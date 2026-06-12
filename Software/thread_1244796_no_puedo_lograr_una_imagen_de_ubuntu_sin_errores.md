---
title: "no puedo lograr una imagen de ubuntu sin errores"
date: 2009-08-19
forum: Software
---

### Post by nachocuervo on 2009-08-19
Hola! intento instalar Ubuntu, y no puedo!!!!!!!!! bueaaaa!!!!!!!!  
 en reiteradas ocasiones descargue el 8 hardy heron y siempre tube problemas con el archivo "filesystem.squashfs" que daba error con md5summary. Lo descargue en diversas oportunidades y de diversas formas.
Al final logré crear un CD que no me diera errores con md5!!, el LiveCD anda muy bien, pero quiero instalarlo desde windows y me es imposible. Empieza muy bien creando el soporte en la raíz del disco, reinicio y la instalación comienza y siempre da error en algun archivo , no siempre el mismo (de todos modos nunca logre individualizar el archivo en el cd de instalacion). Lo que descubri es q cuando crea la carpeta ubuntu en la raiz del rígido descubri que hace una imagen del disco de instalación "installation.ISO" que tiene el problema de "filesystem.squashfs" (error con md5summary) y por mas que probe de todas formas no puedo hacer que cree una buena imagen. El origen de eso (sería el disco de instalación) es de un CD grabé y NO da error md5 y tambien con un disco virtual (cuya imagen descargue de nuevo de internet por las dudas) que tampoco da error...

Ubuntu Installer
ocurrió un error:
writelines() argument must be a sequence of strings
Para más información vea el archivo de registro: c:/user/impst/temp/wubi-9.04-rev128.log
[IMG]http://picasaweb.google.it/ignacio.vinelli/ProgramacNac?feat=directlink[/IMG]
no se que hacer me vuelvo loco... ?
Ahora pruebo con ubuntu 9... y peor.
Aca voy a describir paso por paso, ya que muy lejos no llego...
Descargue la iso, monto la imagen y apenas arranca el autorun me tira este error:
[IMG]http://picasaweb.google.it/ignacio.vinelli/ProgramacNac?feat=directlink[/IMG]
Este es el log
> 08-19 19:38 INFO   root: === wubi 9.04 rev128 ===
08-19 19:38 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 19:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 19:38 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\data
08-19 19:38 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\bin\7z.exe
08-19 19:38 DEBUG  CommonBackend: Fetching basic info...
08-19 19:38 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 19:38 DEBUG  CommonBackend: platform=win32
08-19 19:38 DEBUG  CommonBackend: osname=nt
08-19 19:38 DEBUG  CommonBackend: language=it_IT
08-19 19:38 DEBUG  CommonBackend: encoding=cp1252
08-19 19:38 DEBUG  WindowsBackend: arch=i386
08-19 19:38 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\data\isolist.ini
08-19 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 19:38 DEBUG  WindowsBackend: Fetching host info...
08-19 19:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 19:38 DEBUG  WindowsBackend: windows version=xp
08-19 19:38 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 19:38 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 19:38 DEBUG  WindowsBackend: windows_build=2600
08-19 19:38 DEBUG  WindowsBackend: gmt=-3
08-19 19:38 DEBUG  WindowsBackend: country=BR
08-19 19:38 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 19:38 DEBUG  WindowsBackend: windows_username=User
08-19 19:38 DEBUG  WindowsBackend: user_full_name=User
08-19 19:38 DEBUG  WindowsBackend: user_directory=User
08-19 19:38 DEBUG  WindowsBackend: windows_language_code=1040
08-19 19:38 DEBUG  WindowsBackend: windows_language=Italian
08-19 19:38 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 19:38 DEBUG  WindowsBackend: bootloader=xp
08-19 19:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 621.30078125 mb free )
08-19 19:38 DEBUG  WindowsBackend: drive=Drive(C: hd 621.30078125 mb free )
08-19 19:38 DEBUG  WindowsBackend: drive=Drive(D: hd 6285.99609375 mb free ntfs)
08-19 19:38 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 19:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 19:38 DEBUG  WindowsBackend: uninstaller_path=None
08-19 19:38 DEBUG  WindowsBackend: previous_target_dir=None
08-19 19:38 DEBUG  WindowsBackend: previous_distro_name=None
08-19 19:38 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 19:38 DEBUG  WindowsBackend: keyboard_layout=br
08-19 19:38 DEBUG  WindowsBackend: keyboard_variant=
08-19 19:38 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 19:38 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 19:38 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 19:38 DEBUG  CommonBackend: Searching for local CDs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Ubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Ubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Kubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Kubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Xubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Xubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Mythbuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp is a valid Mythbuntu CD
08-19 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A2.tmp\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:39 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 19:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 19:39 DEBUG  Distro: wrong arch: i386 != amd64
08-19 19:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 19:39 INFO   root: Running the CD menu...
08-19 19:39 DEBUG  WindowsFrontend: __init__...
08-19 19:39 DEBUG  WindowsFrontend: on_init...
08-19 19:39 INFO   WindowsFrontend: Operation cancelled
08-19 19:39 DEBUG  WindowsFrontend: frontend.quit
08-19 19:39 DEBUG  WindowsFrontend: frontend.on_quit
08-19 19:39 DEBUG  root: application.on_quit
08-19 19:39 INFO   root: sys.exit
08-19 19:50 INFO   root: === wubi 9.04 rev128 ===
08-19 19:50 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 19:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 19:50 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\data
08-19 19:50 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\bin\7z.exe
08-19 19:50 DEBUG  CommonBackend: Fetching basic info...
08-19 19:50 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 19:50 DEBUG  CommonBackend: platform=win32
08-19 19:50 DEBUG  CommonBackend: osname=nt
08-19 19:50 DEBUG  CommonBackend: language=it_IT
08-19 19:50 DEBUG  CommonBackend: encoding=cp1252
08-19 19:50 DEBUG  WindowsBackend: arch=i386
08-19 19:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\data\isolist.ini
08-19 19:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 19:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 19:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 19:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 19:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 19:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 19:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 19:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 19:50 DEBUG  WindowsBackend: Fetching host info...
08-19 19:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 19:50 DEBUG  WindowsBackend: windows version=xp
08-19 19:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 19:50 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 19:50 DEBUG  WindowsBackend: windows_build=2600
08-19 19:50 DEBUG  WindowsBackend: gmt=-3
08-19 19:50 DEBUG  WindowsBackend: country=BR
08-19 19:50 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 19:50 DEBUG  WindowsBackend: windows_username=User
08-19 19:50 DEBUG  WindowsBackend: user_full_name=User
08-19 19:50 DEBUG  WindowsBackend: user_directory=User
08-19 19:50 DEBUG  WindowsBackend: windows_language_code=1040
08-19 19:50 DEBUG  WindowsBackend: windows_language=Italian
08-19 19:50 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 19:50 DEBUG  WindowsBackend: bootloader=xp
08-19 19:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 641.828125 mb free )
08-19 19:50 DEBUG  WindowsBackend: drive=Drive(C: hd 641.828125 mb free )
08-19 19:50 DEBUG  WindowsBackend: drive=Drive(D: hd 6288.99609375 mb free ntfs)
08-19 19:50 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 19:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 19:50 DEBUG  WindowsBackend: uninstaller_path=None
08-19 19:50 DEBUG  WindowsBackend: previous_target_dir=None
08-19 19:50 DEBUG  WindowsBackend: previous_distro_name=None
08-19 19:50 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 19:50 DEBUG  WindowsBackend: keyboard_layout=br
08-19 19:50 DEBUG  WindowsBackend: keyboard_variant=
08-19 19:50 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 19:50 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 19:50 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 19:50 DEBUG  CommonBackend: Searching for local CDs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:50 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 19:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 19:50 DEBUG  Distro: wrong arch: i386 != amd64
08-19 19:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:50 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 19:50 INFO   root: Running the CD menu...
08-19 19:50 DEBUG  WindowsFrontend: __init__...
08-19 19:50 DEBUG  WindowsFrontend: on_init...
08-19 19:50 INFO   root: CD menu finished
08-19 19:50 INFO   root: Running the installer...
08-19 19:51 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=Spanish, username=nacho
08-19 19:51 INFO   root: Received settings
08-19 19:51 DEBUG  TaskList: # Running tasklist...
08-19 19:51 DEBUG  TaskList: ## Running select_target_dir...
08-19 19:51 INFO   WindowsBackend: Installing into D:\ubuntu
08-19 19:51 DEBUG  TaskList: ## Finished select_target_dir
08-19 19:51 DEBUG  TaskList: ## Running create_dir_structure...
08-19 19:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
08-19 19:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
08-19 19:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
08-19 19:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
08-19 19:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
08-19 19:51 DEBUG  TaskList: ## Finished create_dir_structure
08-19 19:51 DEBUG  TaskList: ## Running uncompress_target_dir...
08-19 19:51 DEBUG  TaskList: ## Finished uncompress_target_dir
08-19 19:51 DEBUG  TaskList: ## Running create_uninstaller...
08-19 19:51 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-19 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-19 19:51 DEBUG  TaskList: ## Finished create_uninstaller
08-19 19:51 DEBUG  TaskList: ## Running copy_installation_files...
08-19 19:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
08-19 19:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A3.tmp\winboot -> D:\ubuntu\winboot
08-19 19:51 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 161, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
08-19 19:51 DEBUG  TaskList: # Cancelling tasklist
08-19 19:51 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings
08-19 19:51 DEBUG  TaskList: # Finished tasklist
08-19 19:53 INFO   root: === wubi 9.04 rev128 ===
08-19 19:53 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 19:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 19:53 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\data
08-19 19:53 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\bin\7z.exe
08-19 19:53 DEBUG  CommonBackend: Fetching basic info...
08-19 19:53 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 19:53 DEBUG  CommonBackend: platform=win32
08-19 19:53 DEBUG  CommonBackend: osname=nt
08-19 19:53 DEBUG  CommonBackend: language=it_IT
08-19 19:53 DEBUG  CommonBackend: encoding=cp1252
08-19 19:53 DEBUG  WindowsBackend: arch=i386
08-19 19:53 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\data\isolist.ini
08-19 19:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 19:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 19:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 19:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 19:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 19:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 19:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 19:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 19:53 DEBUG  WindowsBackend: Fetching host info...
08-19 19:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 19:53 DEBUG  WindowsBackend: windows version=xp
08-19 19:53 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 19:53 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 19:53 DEBUG  WindowsBackend: windows_build=2600
08-19 19:53 DEBUG  WindowsBackend: gmt=-3
08-19 19:53 DEBUG  WindowsBackend: country=BR
08-19 19:53 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 19:53 DEBUG  WindowsBackend: windows_username=User
08-19 19:53 DEBUG  WindowsBackend: user_full_name=User
08-19 19:53 DEBUG  WindowsBackend: user_directory=User
08-19 19:53 DEBUG  WindowsBackend: windows_language_code=1040
08-19 19:53 DEBUG  WindowsBackend: windows_language=Italian
08-19 19:53 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 19:53 DEBUG  WindowsBackend: bootloader=xp
08-19 19:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 641.703125 mb free )
08-19 19:53 DEBUG  WindowsBackend: drive=Drive(C: hd 641.703125 mb free )
08-19 19:53 DEBUG  WindowsBackend: drive=Drive(D: hd 6287.11328125 mb free ntfs)
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 19:54 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
08-19 19:54 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
08-19 19:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-19 19:54 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 19:54 DEBUG  WindowsBackend: keyboard_layout=br
08-19 19:54 DEBUG  WindowsBackend: keyboard_variant=
08-19 19:54 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 19:54 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 19:54 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 19:54 DEBUG  CommonBackend: Searching for local CDs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 19:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 19:54 DEBUG  Distro: wrong arch: i386 != amd64
08-19 19:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:54 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 19:54 INFO   root: Running the CD menu...
08-19 19:54 DEBUG  WindowsFrontend: __init__...
08-19 19:54 DEBUG  WindowsFrontend: on_init...
08-19 19:54 INFO   root: CD menu finished
08-19 19:54 INFO   root: Already installed, running the uninstaller...
08-19 19:54 INFO   root: Running the uninstaller...
08-19 19:54 INFO   CommonBackend: This is the uninstaller running
08-19 19:54 INFO   root: Received settings
08-19 19:54 DEBUG  TaskList: # Running tasklist...
08-19 19:54 DEBUG  TaskList: ## Running Backup ISO...
08-19 19:54 DEBUG  TaskList: ## Finished Backup ISO
08-19 19:54 DEBUG  TaskList: ## Running Remove bootloader entry...
08-19 19:54 ERROR  WindowsBackend: Cannot find bcdedit
08-19 19:54 DEBUG  WindowsBackend: undo_bootini C:
08-19 19:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 641.703125 mb free )
08-19 19:54 DEBUG  WindowsBackend: undo_bootini D:
08-19 19:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 6287.11328125 mb free ntfs)
08-19 19:54 DEBUG  WindowsBackend: undo_bootini E:
08-19 19:54 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
08-19 19:54 DEBUG  TaskList: ## Finished Remove bootloader entry
08-19 19:54 DEBUG  TaskList: ## Running Remove target dir...
08-19 19:54 DEBUG  CommonBackend: Deleting D:\ubuntu
08-19 19:54 DEBUG  TaskList: ## Finished Remove target dir
08-19 19:54 DEBUG  TaskList: ## Running Remove registry key...
08-19 19:54 DEBUG  TaskList: ## Finished Remove registry key
08-19 19:54 DEBUG  TaskList: # Finished tasklist
08-19 19:54 INFO   root: Almost finished uninstalling
08-19 19:54 INFO   root: Finished uninstallation
08-19 19:54 DEBUG  CommonBackend: Fetching basic info...
08-19 19:54 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 19:54 DEBUG  CommonBackend: platform=win32
08-19 19:54 DEBUG  CommonBackend: osname=nt
08-19 19:54 DEBUG  CommonBackend: language=it_IT
08-19 19:54 DEBUG  CommonBackend: encoding=cp1252
08-19 19:54 DEBUG  WindowsBackend: arch=i386
08-19 19:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\data\isolist.ini
08-19 19:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 19:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 19:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 19:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 19:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 19:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 19:54 DEBUG  WindowsBackend: Fetching host info...
08-19 19:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 19:54 DEBUG  WindowsBackend: windows version=xp
08-19 19:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 19:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 19:54 DEBUG  WindowsBackend: windows_build=2600
08-19 19:54 DEBUG  WindowsBackend: gmt=-3
08-19 19:54 DEBUG  WindowsBackend: country=BR
08-19 19:54 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 19:54 DEBUG  WindowsBackend: windows_username=User
08-19 19:54 DEBUG  WindowsBackend: user_full_name=User
08-19 19:54 DEBUG  WindowsBackend: user_directory=User
08-19 19:54 DEBUG  WindowsBackend: windows_language_code=1040
08-19 19:54 DEBUG  WindowsBackend: windows_language=Italian
08-19 19:54 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 19:54 DEBUG  WindowsBackend: bootloader=xp
08-19 19:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 641.6171875 mb free )
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(C: hd 641.6171875 mb free )
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(D: hd 6289.00390625 mb free ntfs)
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 19:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 19:54 DEBUG  WindowsBackend: uninstaller_path=None
08-19 19:54 DEBUG  WindowsBackend: previous_target_dir=None
08-19 19:54 DEBUG  WindowsBackend: previous_distro_name=None
08-19 19:54 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 19:54 DEBUG  WindowsBackend: keyboard_layout=br
08-19 19:54 DEBUG  WindowsBackend: keyboard_variant=
08-19 19:54 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 19:54 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 19:54 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 19:54 DEBUG  CommonBackend: Searching for local CDs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 19:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:54 DEBUG  Distro: wrong arch: i386 != amd64
08-19 19:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 19:54 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 19:54 INFO   root: Running the installer...
08-19 19:55 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=Spanish, username=user
08-19 19:55 INFO   root: Received settings
08-19 19:55 DEBUG  TaskList: # Running tasklist...
08-19 19:55 DEBUG  TaskList: ## Running select_target_dir...
08-19 19:55 INFO   WindowsBackend: Installing into D:\ubuntu
08-19 19:55 DEBUG  TaskList: ## Finished select_target_dir
08-19 19:55 DEBUG  TaskList: ## Running create_dir_structure...
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
08-19 19:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
08-19 19:55 DEBUG  TaskList: ## Finished create_dir_structure
08-19 19:55 DEBUG  TaskList: ## Running uncompress_target_dir...
08-19 19:55 DEBUG  TaskList: ## Finished uncompress_target_dir
08-19 19:55 DEBUG  TaskList: ## Running create_uninstaller...
08-19 19:55 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-19 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-19 19:55 DEBUG  TaskList: ## Finished create_uninstaller
08-19 19:55 DEBUG  TaskList: ## Running copy_installation_files...
08-19 19:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
08-19 19:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A4.tmp\winboot -> D:\ubuntu\winboot
08-19 19:55 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 161, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
08-19 19:55 DEBUG  TaskList: # Cancelling tasklist
08-19 19:55 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings
08-19 19:55 DEBUG  TaskList: # Finished tasklist
08-19 20:02 INFO   root: === wubi 9.04 rev128 ===
08-19 20:02 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 20:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 20:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\data
08-19 20:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\bin\7z.exe
08-19 20:02 DEBUG  CommonBackend: Fetching basic info...
08-19 20:02 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 20:02 DEBUG  CommonBackend: platform=win32
08-19 20:02 DEBUG  CommonBackend: osname=nt
08-19 20:02 DEBUG  CommonBackend: language=it_IT
08-19 20:02 DEBUG  CommonBackend: encoding=cp1252
08-19 20:02 DEBUG  WindowsBackend: arch=i386
08-19 20:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\data\isolist.ini
08-19 20:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 20:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 20:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 20:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 20:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 20:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 20:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 20:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 20:02 DEBUG  WindowsBackend: Fetching host info...
08-19 20:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 20:02 DEBUG  WindowsBackend: windows version=xp
08-19 20:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 20:02 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 20:02 DEBUG  WindowsBackend: windows_build=2600
08-19 20:02 DEBUG  WindowsBackend: gmt=-3
08-19 20:02 DEBUG  WindowsBackend: country=BR
08-19 20:02 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 20:02 DEBUG  WindowsBackend: windows_username=User
08-19 20:02 DEBUG  WindowsBackend: user_full_name=User
08-19 20:02 DEBUG  WindowsBackend: user_directory=User
08-19 20:02 DEBUG  WindowsBackend: windows_language_code=1040
08-19 20:02 DEBUG  WindowsBackend: windows_language=Italian
08-19 20:02 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 20:02 DEBUG  WindowsBackend: bootloader=xp
08-19 20:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 641.3671875 mb free )
08-19 20:02 DEBUG  WindowsBackend: drive=Drive(C: hd 641.3671875 mb free )
08-19 20:02 DEBUG  WindowsBackend: drive=Drive(D: hd 6289.00390625 mb free ntfs)
08-19 20:02 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 20:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 20:02 DEBUG  WindowsBackend: uninstaller_path=None
08-19 20:02 DEBUG  WindowsBackend: previous_target_dir=None
08-19 20:02 DEBUG  WindowsBackend: previous_distro_name=None
08-19 20:02 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 20:02 DEBUG  WindowsBackend: keyboard_layout=br
08-19 20:02 DEBUG  WindowsBackend: keyboard_variant=
08-19 20:02 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 20:02 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 20:02 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 20:02 DEBUG  CommonBackend: Searching for local CDs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2A6.tmp\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 20:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 20:02 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 20:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 20:02 DEBUG  Distro: wrong arch: i386 != amd64
08-19 20:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 20:02 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 20:02 INFO   root: Running the CD menu...
08-19 20:02 DEBUG  WindowsFrontend: __init__...
08-19 20:02 DEBUG  WindowsFrontend: on_init...
08-19 20:02 INFO   WindowsFrontend: Operation cancelled
08-19 20:02 DEBUG  WindowsFrontend: frontend.quit
08-19 20:02 DEBUG  WindowsFrontend: frontend.on_quit
08-19 20:02 DEBUG  root: application.on_quit
08-19 20:02 INFO   root: sys.exit
08-19 20:25 INFO   root: === wubi 9.04 rev128 ===
08-19 20:25 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 20:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 20:25 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\data
08-19 20:25 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\bin\7z.exe
08-19 20:25 DEBUG  CommonBackend: Fetching basic info...
08-19 20:25 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 20:25 DEBUG  CommonBackend: platform=win32
08-19 20:25 DEBUG  CommonBackend: osname=nt
08-19 20:25 DEBUG  CommonBackend: language=it_IT
08-19 20:25 DEBUG  CommonBackend: encoding=cp1252
08-19 20:25 DEBUG  WindowsBackend: arch=i386
08-19 20:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\data\isolist.ini
08-19 20:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 20:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 20:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 20:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 20:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 20:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 20:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 20:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 20:25 DEBUG  WindowsBackend: Fetching host info...
08-19 20:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 20:25 DEBUG  WindowsBackend: windows version=xp
08-19 20:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 20:25 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 20:25 DEBUG  WindowsBackend: windows_build=2600
08-19 20:25 DEBUG  WindowsBackend: gmt=-3
08-19 20:25 DEBUG  WindowsBackend: country=BR
08-19 20:25 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 20:25 DEBUG  WindowsBackend: windows_username=User
08-19 20:25 DEBUG  WindowsBackend: user_full_name=User
08-19 20:25 DEBUG  WindowsBackend: user_directory=User
08-19 20:25 DEBUG  WindowsBackend: windows_language_code=1040
08-19 20:25 DEBUG  WindowsBackend: windows_language=Italian
08-19 20:25 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 20:25 DEBUG  WindowsBackend: bootloader=xp
08-19 20:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 639.28515625 mb free )
08-19 20:25 DEBUG  WindowsBackend: drive=Drive(C: hd 639.28515625 mb free )
08-19 20:25 DEBUG  WindowsBackend: drive=Drive(D: hd 6289.00390625 mb free ntfs)
08-19 20:27 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 20:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 20:27 DEBUG  WindowsBackend: uninstaller_path=None
08-19 20:27 DEBUG  WindowsBackend: previous_target_dir=None
08-19 20:27 DEBUG  WindowsBackend: previous_distro_name=None
08-19 20:27 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 20:27 DEBUG  WindowsBackend: keyboard_layout=br
08-19 20:27 DEBUG  WindowsBackend: keyboard_variant=
08-19 20:27 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 20:27 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 20:27 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 20:27 DEBUG  CommonBackend: Searching for local CDs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl2AA.tmp\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 20:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 20:27 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 20:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 20:27 DEBUG  Distro: wrong arch: i386 != amd64
08-19 20:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 20:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 20:27 INFO   root: Running the CD menu...
08-19 20:27 DEBUG  WindowsFrontend: __init__...
08-19 20:27 DEBUG  WindowsFrontend: on_init...
08-19 20:47 INFO   WindowsFrontend: Operation cancelled
08-19 20:47 DEBUG  WindowsFrontend: frontend.quit
08-19 20:47 DEBUG  WindowsFrontend: frontend.on_quit
08-19 20:47 DEBUG  root: application.on_quit
08-19 20:47 INFO   root: sys.exit
08-19 21:13 INFO   root: === wubi 9.04 rev128 ===
08-19 21:13 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 21:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
08-19 21:13 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\data
08-19 21:13 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\bin\7z.exe
08-19 21:13 DEBUG  CommonBackend: Fetching basic info...
08-19 21:13 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-19 21:13 DEBUG  CommonBackend: platform=win32
08-19 21:13 DEBUG  CommonBackend: osname=nt
08-19 21:13 DEBUG  CommonBackend: language=it_IT
08-19 21:13 DEBUG  CommonBackend: encoding=cp1252
08-19 21:13 DEBUG  WindowsBackend: arch=i386
08-19 21:13 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\data\isolist.ini
08-19 21:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 21:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 21:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 21:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 21:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 21:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 21:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 21:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 21:13 DEBUG  WindowsBackend: Fetching host info...
08-19 21:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 21:13 DEBUG  WindowsBackend: windows version=xp
08-19 21:13 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 21:13 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 21:13 DEBUG  WindowsBackend: windows_build=2600
08-19 21:13 DEBUG  WindowsBackend: gmt=-3
08-19 21:13 DEBUG  WindowsBackend: country=BR
08-19 21:13 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 21:13 DEBUG  WindowsBackend: windows_username=User
08-19 21:13 DEBUG  WindowsBackend: user_full_name=User
08-19 21:13 DEBUG  WindowsBackend: user_directory=User
08-19 21:13 DEBUG  WindowsBackend: windows_language_code=1040
08-19 21:13 DEBUG  WindowsBackend: windows_language=Italian
08-19 21:13 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 21:13 DEBUG  WindowsBackend: bootloader=xp
08-19 21:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 869.68359375 mb free )
08-19 21:13 DEBUG  WindowsBackend: drive=Drive(C: hd 869.68359375 mb free )
08-19 21:13 DEBUG  WindowsBackend: drive=Drive(D: hd 6289.00390625 mb free ntfs)
08-19 21:13 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 21:13 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 21:13 DEBUG  WindowsBackend: uninstaller_path=None
08-19 21:13 DEBUG  WindowsBackend: previous_target_dir=None
08-19 21:13 DEBUG  WindowsBackend: previous_distro_name=None
08-19 21:13 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 21:13 DEBUG  WindowsBackend: keyboard_layout=br
08-19 21:13 DEBUG  WindowsBackend: keyboard_variant=
08-19 21:13 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 21:13 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 21:13 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 21:13 DEBUG  CommonBackend: Searching for local CDs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 21:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 21:13 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 21:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 21:13 DEBUG  Distro: wrong arch: i386 != amd64
08-19 21:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 21:13 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 21:13 INFO   root: Running the CD menu...
08-19 21:13 DEBUG  WindowsFrontend: __init__...
08-19 21:13 DEBUG  WindowsFrontend: on_init...
08-19 21:13 INFO   root: CD menu finished
08-19 21:13 INFO   root: Running the installer...
08-19 21:14 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=Spanish, username=nacho
08-19 21:14 INFO   root: Received settings
08-19 21:14 DEBUG  TaskList: # Running tasklist...
08-19 21:14 DEBUG  TaskList: ## Running select_target_dir...
08-19 21:14 INFO   WindowsBackend: Installing into D:\ubuntu
08-19 21:14 DEBUG  TaskList: ## Finished select_target_dir
08-19 21:14 DEBUG  TaskList: ## Running create_dir_structure...
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
08-19 21:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
08-19 21:14 DEBUG  TaskList: ## Finished create_dir_structure
08-19 21:14 DEBUG  TaskList: ## Running uncompress_target_dir...
08-19 21:14 DEBUG  TaskList: ## Finished uncompress_target_dir
08-19 21:14 DEBUG  TaskList: ## Running create_uninstaller...
08-19 21:14 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-19 21:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-19 21:14 DEBUG  TaskList: ## Finished create_uninstaller
08-19 21:14 DEBUG  TaskList: ## Running copy_installation_files...
08-19 21:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
08-19 21:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\User\IMPOST~1\Temp\pyl6.tmp\winboot -> D:\ubuntu\winboot
08-19 21:14 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 161, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
08-19 21:14 DEBUG  TaskList: # Cancelling tasklist
08-19 21:14 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings
08-19 21:14 DEBUG  TaskList: # Finished tasklist
08-19 21:20 INFO   root: === wubi 9.04 rev128 ===
08-19 21:20 DEBUG  root: Logfile is c:\docume~1\user\impost~1\temp\wubi-9.04-rev128.log
08-19 21:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
08-19 21:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\data
08-19 21:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\bin\7z.exe
08-19 21:20 DEBUG  CommonBackend: Fetching basic info...
08-19 21:20 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
08-19 21:20 DEBUG  CommonBackend: platform=win32
08-19 21:20 DEBUG  CommonBackend: osname=nt
08-19 21:20 DEBUG  CommonBackend: language=it_IT
08-19 21:20 DEBUG  CommonBackend: encoding=cp1252
08-19 21:20 DEBUG  WindowsBackend: arch=i386
08-19 21:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\data\isolist.ini
08-19 21:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 21:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 21:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 21:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 21:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 21:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 21:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 21:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 21:20 DEBUG  WindowsBackend: Fetching host info...
08-19 21:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 21:20 DEBUG  WindowsBackend: windows version=xp
08-19 21:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 21:20 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 21:20 DEBUG  WindowsBackend: windows_build=2600
08-19 21:20 DEBUG  WindowsBackend: gmt=-3
08-19 21:20 DEBUG  WindowsBackend: country=BR
08-19 21:20 DEBUG  WindowsBackend: timezone=America/Fortaleza
08-19 21:20 DEBUG  WindowsBackend: windows_username=User
08-19 21:20 DEBUG  WindowsBackend: user_full_name=User
08-19 21:20 DEBUG  WindowsBackend: user_directory=User
08-19 21:20 DEBUG  WindowsBackend: windows_language_code=1040
08-19 21:20 DEBUG  WindowsBackend: windows_language=Italian
08-19 21:20 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
08-19 21:20 DEBUG  WindowsBackend: bootloader=xp
08-19 21:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 865.88671875 mb free )
08-19 21:20 DEBUG  WindowsBackend: drive=Drive(C: hd 865.88671875 mb free )
08-19 21:20 DEBUG  WindowsBackend: drive=Drive(D: hd 6287.09765625 mb free ntfs)
08-19 21:20 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-19 21:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-19 21:20 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
08-19 21:20 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
08-19 21:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-19 21:20 DEBUG  WindowsBackend: keyboard_id=134884362
08-19 21:20 DEBUG  WindowsBackend: keyboard_layout=br
08-19 21:20 DEBUG  WindowsBackend: keyboard_variant=
08-19 21:20 DEBUG  CommonBackend: locale=it_IT.UTF-8
08-19 21:20 DEBUG  WindowsBackend: total_memory_mb=1014.109375
08-19 21:20 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 21:20 DEBUG  CommonBackend: Searching for local CDs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain C:\DOCUME~1\User\IMPOST~1\Temp\pyl8.tmp\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 21:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 21:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 21:20 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 21:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 21:20 DEBUG  Distro: wrong arch: i386 != amd64
08-19 21:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 21:20 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-19 21:20 INFO   root: Running the uninstaller...
08-19 21:20 INFO   CommonBackend: This is the uninstaller running
08-19 21:20 DEBUG  WindowsFrontend: __init__...
08-19 21:20 DEBUG  WindowsFrontend: on_init...
08-19 21:20 INFO   root: Received settings
08-19 21:20 DEBUG  TaskList: # Running tasklist...
08-19 21:20 DEBUG  TaskList: ## Running Backup ISO...
08-19 21:20 DEBUG  TaskList: ## Finished Backup ISO
08-19 21:20 DEBUG  TaskList: ## Running Remove bootloader entry...
08-19 21:20 ERROR  WindowsBackend: Cannot find bcdedit
08-19 21:20 DEBUG  WindowsBackend: undo_bootini C:
08-19 21:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 865.88671875 mb free )
08-19 21:20 DEBUG  WindowsBackend: undo_bootini D:
08-19 21:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 6287.09765625 mb free ntfs)
08-19 21:20 DEBUG  WindowsBackend: undo_bootini E:
08-19 21:20 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
08-19 21:20 DEBUG  TaskList: ## Finished Remove bootloader entry
08-19 21:20 DEBUG  TaskList: ## Running Remove target dir...
08-19 21:20 DEBUG  CommonBackend: Deleting D:\ubuntu
08-19 21:20 DEBUG  TaskList: ## Finished Remove target dir
08-19 21:20 DEBUG  TaskList: ## Running Remove registry key...
08-19 21:20 DEBUG  TaskList: ## Finished Remove registry key
08-19 21:20 DEBUG  TaskList: # Finished tasklist
08-19 21:20 INFO   root: Almost finished uninstalling
08-19 21:20 INFO   root: Finished uninstallation
08-19 21:20 DEBUG  root: application.quit
08-19 21:20 DEBUG  WindowsFrontend: frontend.quit
08-19 21:20 DEBUG  WindowsFrontend: frontend.on_quit
08-19 21:20 DEBUG  root: application.on_quit
08-19 21:20 INFO   root: sys.exitY hasta ahí llego con el 9. 
Con el 8 me va mejor...
llego a la parte de instalación luego de reiniciar, si les parece necesario puedo ponerle los pasos y los errores que saltan.
Estoy en una laptop con 
W XP home SP2, partición C:
Intel Pentium 1.73 Ghz, 
1GB RAM
Intento instalar ubuntu-9.04-desktop-i386.iso en modo wubi en disco D:
falta algo?P ...
saben que puede estar pasando?? seguramente estoy haciendo algo mal, o no sé porque intenté millones de veces descargar el ubuntu-8.04.2-desktop-i386.iso  y a menudo tira error en el archivo "filesystem.squashfs" cuando chekeo con md5summary y aunque conseguí tener uno que no nunca puedo hacerlo instalar, solo liveC, porque al hacer la ISO de "installation.ISO" en la carpeta "ubuntu" esa imágen también da error al descomprimir y chekear con md5.
Bueno, agradezco un monton su ayuda.
Cualquier cosa que necesiten pregunten, si quieren les hago un informe de AIDA32 o el que me digan ustedes.
Saludos
Ignacio

---

### Post by luks911 on 2009-08-20
nachocuervo,

Parece que hay un bug[0] en Wubi bastante curioso. Resulta que si querés instalar Ubuntu en un idioma o zona horaria distintos a los de tu instalación de Win, entonces pasa lo que te pasó a vos. Fijate si es eso y probá de instalar Ubuntu con el mismo idioma que tenés Win. Entiendo que después se puede cambiar. 
Y si no es eso. Avisá.

Saludos

[0] [https://bugs.launchpad.net/wubi/+bug/365642](https://bugs.launchpad.net/wubi/+bug/365642)

---

### Post by nachocuervo on 2009-08-27
tenés toda la razon luks, :popcorn: instalé el ubuntu9 al final en italiano pero ese era el problema sin duda. No logro cambiar de idioma ...

---

