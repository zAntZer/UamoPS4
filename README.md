# 🎮 UamoPS4 - Emulador de PS4 para Android (Basado en shadPS4)

¡Bienvenido a **UamoPS4**! Este es un proyecto experimental que busca portar y emular juegos de PlayStation 4 (PS4) en dispositivos Android. Está basado en el núcleo de desarrollo del emulador de PC de código abierto **[shadPS4](https://github.com/shadps4-emu/shadPS4)**.

El objetivo de UamoPS4 es adaptar el potente traductor y renderizador de sombreadores de shadPS4 para la arquitectura ARM64 de los smartphones modernos, ofreciendo una interfaz móvil de alto rendimiento y adaptabilidad.

---

## ✨ Características Principales

*   **📱 Interfaz Moderna e Intuitiva:** Diseñada desde cero con **Jetpack Compose** y Material Design 3, ofreciendo un aspecto visual premium, modo oscuro elegante y transiciones fluidas.
*   **📂 Selector de Archivos Integrado:** Permite buscar y seleccionar fácilmente tus imágenes de juegos de PS4 (como archivos `.pkg` o carpetas volcadas) desde el almacenamiento de tu dispositivo.
*   **⚙️ Panel de Configuraciones por Categorías:**
    *   **Gráficos:** Ajuste del backend de renderizado (soporte nativo de Vulkan), resolución y filtros.
    *   **Audio:** Selección de controladores de audio y volumen del sistema.
    *   **Sistema:** Configuración del idioma de consola, límite de FPS y emulación de CPU.
    *   **Controles:** Mapeo de botones de pantalla táctil y soporte para gamepads externos.
*   **📜 Pestaña de Registro (Logs) en Tiempo Real:** Un visor integrado que muestra los registros internos del emulador y del puente C++. Cuenta con un botón para **copiar el registro** directamente al portapapeles, facilitando el reporte de errores y la optimización continua del emulador.
*   **⚡ Puente Nativo (JNI):** Comunicación de baja latencia entre el frontend en Kotlin/Java y el backend del emulador escrito en C++ (`native-lib.cpp`).

---

## 🛠️ Estructura del Código Fuente

El código fuente está organizado de la siguiente manera para facilitar su navegación y contribución:

*   **`/[root](file:///root/UamoPS4)`**: Directorio raíz del proyecto.
*   **`├── /android`**: Todo el código de la aplicación de Android.
    *   **`├── /app/src/main/java/com/example/uamops4`**:
        *   [`MainActivity.kt`](file:///root/UamoPS4/android/app/src/main/java/com/example/uamops4/MainActivity.kt): Actividad principal que inicializa la interfaz de usuario e invoca los métodos nativos de C++ mediante JNI.
        *   [`ui/main/MainScreen.kt`](file:///root/UamoPS4/android/app/src/main/java/com/example/uamops4/ui/main/MainScreen.kt): Pantalla principal construida en Jetpack Compose que implementa las pestañas de Juegos, Ajustes y Registro.
    *   **`├── /app/src/main/cpp`**:
        *   [`native-lib.cpp`](file:///root/UamoPS4/android/app/src/main/cpp/native-lib.cpp): Puente JNI (C++) que recibe la ruta de los archivos cargados en la interfaz de Android y los transfiere al núcleo del emulador.
        *   [`CMakeLists.txt`](file:///root/UamoPS4/android/app/src/main/cpp/CMakeLists.txt): Configuración de construcción de C++ para compilar el núcleo del emulador con el NDK de Android.
*   **`└── /core`**: Directorio preparado para albergar el núcleo directo de emulación y traducción de CPU/GPU portado de shadPS4.

---

## 📲 Descargar el APK

Actualmente, al tratarse de un proyecto en fase de desarrollo temprano (Alpha experimental), puedes compilar tu propia APK para realizar pruebas directamente:

### Requisitos previos para compilar:
1. Android Studio Jellyfish (o superior) / Android SDK.
2. Android NDK (versión recomendada 25.x o superior) y CMake.
3. JDK 17.

### Pasos para compilar:
1. Clona este repositorio en tu máquina local.
2. Abre una terminal en la carpeta del proyecto y navega al directorio `android`:
   ```bash
   cd android
   ```
3. Genera la APK en modo depuración (Debug) usando Gradle:
   ```bash
   ./gradlew assembleDebug
   ```
4. El archivo APK generado se ubicará en:
   `android/app/build/outputs/apk/debug/app-debug.apk`

*Próximamente se añadirán flujos de CI/CD para compilar versiones automáticamente en la sección de **Releases** de este repositorio.*

---

## ☕ Donaciones y Apoyo al Proyecto

Desarrollar un emulador de PS4 para dispositivos móviles es un desafío técnico inmenso que requiere incontables horas de investigación, ingeniería inversa y depuración. Si deseas apoyar a los desarrolladores de **UamoPS4** para acelerar el desarrollo y mantener el servidor de pruebas activo, puedes realizar una donación voluntaria:

*   **☕ PayPal:** [paypal/@Donate](https://paypal.me/shhkk) (Apóyanos con el valor de un café).

*Cada pequeña contribución ayuda enormemente a mantener viva la motivación y a conseguir hardware de prueba más potente.*

---

## ⚠️ Descargo de Responsabilidad y Licencia

*   **UamoPS4** es una herramienta de emulación con fines puramente educativos y de investigación. No incluye juegos, BIOS, ni archivos protegidos por derechos de autor de Sony Interactive Entertainment. Los usuarios deben poseer copias legales de sus propios juegos para poder emularlos.
*   Este software se distribuye bajo la licencia GNU General Public License v2.0 (GPL-2.0), en concordancia con la licencia del proyecto base *shadPS4*.
