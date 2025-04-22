## 📦 Creating an Installer for the Report UI

This section describes how to **bundle your PyQt-based desktop application into an executable installer** for distribution, using `PyInstaller` and `Inno Setup`.

> 🔧 This process is platform-specific and currently supports **Windows**.

---

### 🛠 Prerequisites

Before you start, ensure the following are installed:

- Python 3.10+
- `pip` (Python package manager)
- `PyInstaller` (to package the Python app)
- [Inno Setup](https://jrsoftware.org/isinfo.php) (to create the `.exe` installer for Windows)

Install dependencies:

```bash
pip install pyinstaller
```

Download and install Inno Setup from the official site: https://jrsoftware.org/isinfo.php

---

### 🧱 Step-by-Step Instructions

#### 1. Prepare Your Python App

Make sure your app runs using a single entry point like `main.py`, and includes all resources (e.g., QML files, images).

Your project might look like this:

```
report-manager-ui/
├── main.py
├── main.qml
├── images/
│   └── playas.jpg
```

#### 2. Bundle Your App with PyInstaller

Use PyInstaller to generate a standalone executable:

```bash
pyinstaller --onefile --windowed main.py
```

- `--onefile`: Creates a single `.exe` file
- `--windowed`: Hides the console window (for GUI apps)

This will generate output in a `dist/` directory:

```
dist/
└── main.exe
```

> ⚠️ If your app uses QML or external files, you'll need to copy them manually or customize the `.spec` file to include them.

#### 3. Create an Installer Using Inno Setup

1. Open Inno Setup.
2. Use the *Script Wizard* to create a new installer:
   - Set application name and version.
   - Set `main.exe` (from `dist/`) as the main executable.
   - Include all required resources (e.g., `main.qml`, `images/` folder).
3. Finish and compile the installer script.
4. The output will be a distributable `.exe` installer.

---

### ✅ Final Result

You’ll have a Windows-compatible `.exe` installer that users can run to install your **Report Manager UI** desktop application.

---

### 📌 Notes

- The installer can be configured to add Start Menu entries, desktop shortcuts, and uninstall options.
- For apps with multiple files and folders, you can update the PyInstaller `.spec` file to include all dependencies.

---

### 📚 References

- [PyInstaller Documentation](https://pyinstaller.org/)
- [Inno Setup Documentation](https://jrsoftware.org/isinfo.php)
 