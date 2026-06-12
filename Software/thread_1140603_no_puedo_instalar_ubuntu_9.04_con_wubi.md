---
title: "no puedo instalar ubuntu 9.04 con wubi"
date: 2009-04-27
forum: Software
---

### Post by NICOC77 on 2009-04-27
hola si bien sigo el foro desde hace un tiempo este es mi primer thread. soy nicolás, estudio medicina en tucuman y mi hobbie son las pc. estoy intentando usar linux desde hace un par de versiones de ubuntu pero siempre tengo algun que otro problema.

en este caso es el siguiente: quiero realizar la instalcion de ubuntu 9.04 amd64 dentro de windows mediante wubi, ya que es una pc familiar y el SO principal es windows xp, pero al intentarlo surgieron inconvenientes...

lo primero que hice fue descargar la version antes dicha de la pag de ubuntu, monto la imagen con daemon tools, elijo instalar con wubi y cuando pongo "install" me aparece un error que dice algo como "writelines() argument must be a sequence of strings", sin embargo en "agregar o quitar programas" aparece la instalacion de ubuntu.

buscando encuentro un thread en el foro "Installation & Upgrades" donde recomiendan desinstalarlo y borrar archivos temporales de la instalacion, luego cambiar el idioma del SO a ingles para que funcione wubi. hago todo esto y wubi arranca la instalacion, pero despues de cargar las barras un par de minutos se cierra automaticamente, quedando nuevamente la instalacion fallida.

intente esto varias veces sin resultados, tambien grabe la imagen a un cd para comprobar errores pero no tiene.

caracteristicas de la pc:
. intel core 2 duo e6300 1.86ghz
. 1gb ram ddr2 667
. 250gb sata2
. video intel 946gz integrado :(
. windows xp professional sp3

agradezco cualquier ayuda.

nicolás.

---

### Post by Svensk023 on 2009-04-27
es posible que tu necesitas un otra .iso de Ubuntu. Tu quieres el DVD porque el tiene mas idomas para instalacion, incluyendo espanol. También, no me gusta wubi, este asi asi

lo siente, mi espanol es limitado

---

### Post by clasificado on 2009-04-28
Que error looooooco es que te tira

Si es por aconsejar, te diria que tires al tacho la iso, te bajes [el wubi desde el sitio oficial]("http://wubi-installer.org/") y le des doble click sin mas que el mismo wubi te baja la iso que necesita y lo hace funcionar.

Por otra parte, he usado wubi en varios casos (pcs tímidas y notebooks también tímidas) y tuve siempre buenos resultados en la instalación (después de instalado vamos caso por caso)

clasificado

---

### Post by NICOC77 on 2009-04-28
> **clasificado said:**
> Si es por aconsejar, te diria que tires al tacho la iso, te bajes [el wubi desde el sitio oficial]("http://wubi-installer.org/") y le des doble click sin mas que el mismo wubi te baja la iso que necesita y lo hace funcionar.

hice como vos decis borre la iso y me baje wubi v129 de la pagina oficial, hago doble click y comienza a bajar la iso (ubuntu amd64) pero una vez que termina y comienza a instalar luego de cargar barras durante un tiempo se cierro solo wubi y cuando reinicio no pasa nada, aun asi queda la instalacion fallida en windows.

este reporte queda en la carpeta temp:

```
04-28 14:33 INFO   root: === wubi 9.04 rev129 ===
04-28 14:33 DEBUG  root: Logfile is c:\windows\temp\wubi-9.04-rev129.log
04-28 14:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Nicol\xe1s\\Escritorio\\wubi.exe"']
04-28 14:33 DEBUG  CommonBackend: data_dir=C:\Windows\Temp\pyl24.tmp\data
04-28 14:33 DEBUG  WindowsBackend: 7z=C:\Windows\Temp\pyl24.tmp\bin\7z.exe
04-28 14:33 DEBUG  CommonBackend: Fetching basic info...
04-28 14:33 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Nicolás\Escritorio\wubi.exe
04-28 14:33 DEBUG  CommonBackend: platform=win32
04-28 14:33 DEBUG  CommonBackend: osname=nt
04-28 14:33 DEBUG  CommonBackend: language=es_AR
04-28 14:33 DEBUG  CommonBackend: encoding=cp1252
04-28 14:33 DEBUG  WindowsBackend: arch=amd64
04-28 14:33 DEBUG  CommonBackend: Parsing isolist=C:\Windows\Temp\pyl24.tmp\data\isolist.ini
04-28 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 14:33 DEBUG  WindowsBackend: Fetching host info...
04-28 14:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 14:33 DEBUG  WindowsBackend: windows version=xp
04-28 14:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-28 14:33 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-28 14:33 DEBUG  WindowsBackend: windows_build=2600
04-28 14:33 DEBUG  WindowsBackend: gmt=-3
04-28 14:33 DEBUG  WindowsBackend: country=AR
04-28 14:33 DEBUG  WindowsBackend: timezone=America/Argentina/Buenos_Aires
04-28 14:33 DEBUG  WindowsBackend: windows_username=Nicolás
04-28 14:33 DEBUG  WindowsBackend: user_full_name=Nicolás
04-28 14:33 DEBUG  WindowsBackend: user_directory=Nicolás
04-28 14:33 DEBUG  WindowsBackend: windows_language_code=1034
04-28 14:33 DEBUG  WindowsBackend: windows_language=Spanish
04-28 14:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
04-28 14:33 DEBUG  WindowsBackend: bootloader=xp
04-28 14:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2351.09375 mb free )
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(C: hd 2351.09375 mb free )
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(D: hd 16954.671875 mb free ntfs)
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(F: hd 29455.0117188 mb free ntfs)
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-28 14:33 DEBUG  WindowsBackend: drive=Drive(Q: hd 3095.5390625 mb free ntfs)
04-28 14:33 DEBUG  WindowsBackend: uninstaller_path=None
04-28 14:33 DEBUG  WindowsBackend: previous_target_dir=None
04-28 14:33 DEBUG  WindowsBackend: previous_distro_name=None
04-28 14:33 DEBUG  WindowsBackend: keyboard_id=67765258
04-28 14:33 DEBUG  WindowsBackend: keyboard_layout=ar
04-28 14:33 DEBUG  WindowsBackend: keyboard_variant=
04-28 14:33 DEBUG  CommonBackend: locale=es_AR.UTF-8
04-28 14:33 DEBUG  WindowsBackend: total_memory_mb=1013.39453125
04-28 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 14:33 DEBUG  CommonBackend: Searching for local CDs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 14:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:33 INFO   root: Running the installer...
04-28 14:33 DEBUG  WindowsFrontend: __init__...
04-28 14:33 DEBUG  WindowsFrontend: on_init...
04-28 14:34 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=8000MB, distro_name=Ubuntu, language=Spanish, username=nicolas
04-28 14:34 INFO   root: Received settings
04-28 14:34 DEBUG  TaskList: # Running tasklist...
04-28 14:34 DEBUG  TaskList: ## Running select_target_dir...
04-28 14:34 INFO   WindowsBackend: Installing into F:\ubuntu
04-28 14:34 DEBUG  TaskList: ## Finished select_target_dir
04-28 14:34 DEBUG  TaskList: ## Running create_dir_structure...
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
04-28 14:34 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
04-28 14:34 DEBUG  TaskList: ## Finished create_dir_structure
04-28 14:34 DEBUG  TaskList: ## Running uncompress_target_dir...
04-28 14:34 DEBUG  TaskList: ## Finished uncompress_target_dir
04-28 14:34 DEBUG  TaskList: ## Running create_uninstaller...
04-28 14:34 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Nicolás\Escritorio\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-28 14:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-28 14:34 DEBUG  TaskList: ## Finished create_uninstaller
04-28 14:34 DEBUG  TaskList: ## Running copy_installation_files...
04-28 14:34 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pyl24.tmp\data\custom-installation -> F:\ubuntu\install\custom-installation
04-28 14:34 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pyl24.tmp\winboot -> F:\ubuntu\winboot
04-28 14:34 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pyl24.tmp\data\images\Ubuntu.ico -> F:\ubuntu\Ubuntu.ico
04-28 14:34 DEBUG  TaskList: ## Finished copy_installation_files
04-28 14:34 DEBUG  TaskList: ## Running get_iso...
04-28 14:34 DEBUG  CommonBackend: Searching for local CD
04-28 14:34 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl24.tmp is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl24.tmp\casper\filesystem.squashfs
04-28 14:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 14:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 14:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 14:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 14:34 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 14:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 14:34 DEBUG  CommonBackend: Searching for local ISO
04-28 14:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-28 14:34 DEBUG  TaskList: New task get_metalink
04-28 14:34 DEBUG  TaskList: ### Running get_metalink...
04-28 14:34 DEBUG  downloader: downloading http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink > F:\ubuntu\install
04-28 14:34 DEBUG  downloader: Download start filename=F:\ubuntu\install\ubuntu-9.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink, basename=ubuntu-9.04-desktop-amd64.metalink, length=19580, text=None
04-28 14:34 DEBUG  downloader: download finished (read 19580 bytes)
04-28 14:34 DEBUG  downloader: downloading http://releases.ubuntu.com/9.04/MD5SUMS-metalink > F:\ubuntu\install
04-28 14:34 DEBUG  downloader: Download start filename=F:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-28 14:34 DEBUG  downloader: download finished (read 413 bytes)
04-28 14:34 DEBUG  downloader: downloading http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg > F:\ubuntu\install
04-28 14:34 DEBUG  downloader: Download start filename=F:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-28 14:34 DEBUG  downloader: download finished (read 189 bytes)
04-28 14:34 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-28 14:34 INFO   saplog: Checking block bindings..
04-28 14:34 INFO   saplog: Key verified successfully.
04-28 14:34 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-28 14:34 DEBUG  TaskList: ### Finished get_metalink
04-28 14:34 DEBUG  TaskList: New task download
04-28 14:34 DEBUG  TaskList: ### Running download...
04-28 14:34 DEBUG  downloader: downloading http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso > F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 14:34 DEBUG  downloader: Download start filename=F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso, basename=ubuntu-9.04-desktop-amd64.iso, length=730554368, text=None
04-28 16:02 DEBUG  TaskList: ### Finished download
04-28 16:02 DEBUG  downloader: download finished (read 730554368 bytes)
04-28 16:02 DEBUG  TaskList: New task check_iso
04-28 16:02 DEBUG  TaskList: ### Running check_iso...
04-28 16:02 DEBUG  CommonBackend: Checking F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:02 DEBUG  WindowsBackend:   extracting .disk\info from F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:02 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
04-28 16:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
04-28 16:02 DEBUG  TaskList: New task get_file_md5
04-28 16:02 DEBUG  TaskList: #### Running get_file_md5...
04-28 16:03 DEBUG  TaskList: #### Finished get_file_md5
04-28 16:03 DEBUG  TaskList: ### Finished check_iso
04-28 16:03 DEBUG  TaskList: ## Finished get_iso
04-28 16:03 DEBUG  TaskList: ## Running extract_kernel...
04-28 16:03 DEBUG  CommonBackend: Extracting files from ISO F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:03 DEBUG  WindowsBackend:   extracting md5sum.txt from F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:03 DEBUG  WindowsBackend:   extracting casper\vmlinuz from F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:03 DEBUG  WindowsBackend:   extracting casper\initrd.gz from F:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-28 16:03 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-28 16:03 DEBUG  CommonBackend:   checking F:\ubuntu\install\boot\vmlinuz
04-28 16:03 DEBUG  CommonBackend:   F:\ubuntu\install\boot\vmlinuz md5 = d15243d1203d0aecf187ff969d6764ea == d15243d1203d0aecf187ff969d6764ea
04-28 16:03 DEBUG  CommonBackend:   checking F:\ubuntu\install\boot\initrd.gz
04-28 16:03 DEBUG  CommonBackend:   F:\ubuntu\install\boot\initrd.gz md5 = 090801c7b801aab7d53d11ddfb0fce4a == 090801c7b801aab7d53d11ddfb0fce4a
04-28 16:03 DEBUG  TaskList: ## Finished extract_kernel
04-28 16:03 DEBUG  TaskList: ## Running choose_disk_sizes...
04-28 16:03 DEBUG  WindowsBackend: total size=8000
  root=7744
  swap=256
  home=0
  usr=0
04-28 16:03 DEBUG  TaskList: ## Finished choose_disk_sizes
04-28 16:03 DEBUG  TaskList: ## Running create_preseed...
04-28 16:03 ERROR  TaskList: 'ascii' codec can't decode byte 0xe1 in position 3: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 578, in create_preseed
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 3: ordinal not in range(128)
04-28 16:03 DEBUG  TaskList: # Cancelling tasklist
04-28 16:03 DEBUG  TaskList: # Finished tasklist
04-28 16:03 ERROR  root: 'ascii' codec can't decode byte 0xe1 in position 3: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 3: ordinal not in range(128)
04-28 17:47 INFO   root: === wubi 9.04 rev129 ===
04-28 17:47 DEBUG  root: Logfile is c:\windows\temp\wubi-9.04-rev129.log
04-28 17:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\ubuntu\\uninstall-wubi.exe"']
04-28 17:47 DEBUG  CommonBackend: data_dir=C:\Windows\Temp\pyl33.tmp\data
04-28 17:47 DEBUG  WindowsBackend: 7z=C:\Windows\Temp\pyl33.tmp\bin\7z.exe
04-28 17:47 DEBUG  CommonBackend: Fetching basic info...
04-28 17:47 DEBUG  CommonBackend: original_exe=F:\ubuntu\uninstall-wubi.exe
04-28 17:47 DEBUG  CommonBackend: platform=win32
04-28 17:47 DEBUG  CommonBackend: osname=nt
04-28 17:47 DEBUG  CommonBackend: language=es_AR
04-28 17:47 DEBUG  CommonBackend: encoding=cp1252
04-28 17:47 DEBUG  WindowsBackend: arch=amd64
04-28 17:47 DEBUG  CommonBackend: Parsing isolist=C:\Windows\Temp\pyl33.tmp\data\isolist.ini
04-28 17:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 17:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 17:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 17:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 17:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 17:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 17:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 17:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 17:47 DEBUG  WindowsBackend: Fetching host info...
04-28 17:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 17:47 DEBUG  WindowsBackend: windows version=xp
04-28 17:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-28 17:47 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-28 17:47 DEBUG  WindowsBackend: windows_build=2600
04-28 17:47 DEBUG  WindowsBackend: gmt=-3
04-28 17:47 DEBUG  WindowsBackend: country=AR
04-28 17:47 DEBUG  WindowsBackend: timezone=America/Argentina/Buenos_Aires
04-28 17:47 DEBUG  WindowsBackend: windows_username=Nicolás
04-28 17:47 DEBUG  WindowsBackend: user_full_name=Nicolás
04-28 17:47 DEBUG  WindowsBackend: user_directory=Nicolás
04-28 17:47 DEBUG  WindowsBackend: windows_language_code=1034
04-28 17:47 DEBUG  WindowsBackend: windows_language=Spanish
04-28 17:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
04-28 17:47 DEBUG  WindowsBackend: bootloader=xp
04-28 17:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2341.5078125 mb free )
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(C: hd 2341.5078125 mb free )
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(D: hd 16954.671875 mb free ntfs)
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(F: hd 28745.1835938 mb free ntfs)
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-28 17:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 3095.5390625 mb free ntfs)
04-28 17:47 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
04-28 17:47 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
04-28 17:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-28 17:47 DEBUG  WindowsBackend: keyboard_id=67765258
04-28 17:47 DEBUG  WindowsBackend: keyboard_layout=ar
04-28 17:47 DEBUG  WindowsBackend: keyboard_variant=
04-28 17:47 DEBUG  CommonBackend: locale=es_AR.UTF-8
04-28 17:47 DEBUG  WindowsBackend: total_memory_mb=1013.39453125
04-28 17:47 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 17:47 DEBUG  CommonBackend: Searching for local CDs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether C:\Windows\Temp\pyl33.tmp is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain C:\Windows\Temp\pyl33.tmp\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 17:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 17:47 INFO   root: Running the uninstaller...
04-28 17:47 INFO   CommonBackend: This is the uninstaller running
04-28 17:47 DEBUG  WindowsFrontend: __init__...
04-28 17:47 DEBUG  WindowsFrontend: on_init...
04-28 17:47 INFO   root: Received settings
04-28 17:47 DEBUG  TaskList: # Running tasklist...
04-28 17:47 DEBUG  TaskList: ## Running Backup ISO...
04-28 17:47 DEBUG  TaskList: ## Finished Backup ISO
04-28 17:47 DEBUG  TaskList: ## Running Remove bootloader entry...
04-28 17:47 ERROR  WindowsBackend: Cannot find bcdedit
04-28 17:47 DEBUG  WindowsBackend: undo_bootini C:
04-28 17:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2341.5078125 mb free )
04-28 17:47 DEBUG  WindowsBackend: undo_bootini D:
04-28 17:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 16954.671875 mb free ntfs)
04-28 17:47 DEBUG  WindowsBackend: undo_bootini F:
04-28 17:47 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 28745.1835938 mb free ntfs)
04-28 17:47 DEBUG  WindowsBackend: undo_bootini Q:
04-28 17:47 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 3095.5390625 mb free ntfs)
04-28 17:47 DEBUG  TaskList: ## Finished Remove bootloader entry
04-28 17:47 DEBUG  TaskList: ## Running Remove target dir...
04-28 17:47 DEBUG  CommonBackend: Deleting F:\ubuntu
04-28 17:47 DEBUG  TaskList: ## Finished Remove target dir
04-28 17:47 DEBUG  TaskList: ## Running Remove registry key...
04-28 17:47 DEBUG  TaskList: ## Finished Remove registry key
04-28 17:47 DEBUG  TaskList: # Finished tasklist
04-28 17:47 INFO   root: Almost finished uninstalling
04-28 17:47 INFO   root: Finished uninstallation
04-28 17:47 DEBUG  root: application.quit
04-28 17:47 DEBUG  WindowsFrontend: frontend.quit
04-28 17:47 DEBUG  WindowsFrontend: frontend.on_quit
04-28 17:47 DEBUG  root: application.on_quit
04-28 17:47 INFO   root: sys.exit

```

nicolás.

---

### Post by Tosh78 on 2009-04-28
Hola Nicolas, no se si lo sabias o no, o si ya lo hiciste, pero para que funcione Wubi antes tenes que desfragmentar el disco. Las veces que a mi o a mis amigos les paso algo parecido intentando instalar Ubuntu mediante Wubi, se nos soluciono asi.
Entonces:
1) borra wubi y desinstalalo
2) desfragmenta el disco
3) ejecuta wubi

---

### Post by el_guampiro on 2009-04-28
Hola Nicolás...te recomiendo que , al igual que mis antecesores en este foro, bajes el wubi de la página oficial, y si mal no recuerdo tiene una opción que te permite elegir la fuente de la instalación,es decir, que no hace falta que se ponga a descargar la iso nuevamente..dale la ruta de la iso de ubuntu..y pum! la debería instalar de maravilla....el paso siguiente es que arranques la PC con el CD de ubuntu y que particiones el disco, saludos y éxitos con tu linux!

---

