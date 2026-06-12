---
title: "Problema al querer instalar por Wubi"
date: 2009-06-06
forum: Software
---

### Post by pablocerg on 2009-06-06
Buenas, intente instalar Ubuntu por Wubi pero me sale este problema

[http://i42.tinypic.com/o72gm1.png](http://i42.tinypic.com/o72gm1.png)


Cuando voy a ese archivo me sale esto
```
06-06 15:56 INFO   root: === wubi 9.04 rev128 ===
06-06 15:56 DEBUG  root: Logfile is c:\windows\temp\wubi-9.04-rev128.log
06-06 15:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
06-06 15:56 DEBUG  CommonBackend: data_dir=C:\Windows\Temp\pylC72.tmp\data
06-06 15:56 DEBUG  WindowsBackend: 7z=C:\Windows\Temp\pylC72.tmp\bin\7z.exe
06-06 15:56 DEBUG  CommonBackend: Fetching basic info...
06-06 15:56 DEBUG  CommonBackend: original_exe=I:\wubi.exe
06-06 15:56 DEBUG  CommonBackend: platform=win32
06-06 15:56 DEBUG  CommonBackend: osname=nt
06-06 15:56 DEBUG  CommonBackend: language=es_ES
06-06 15:56 DEBUG  CommonBackend: encoding=cp1252
06-06 15:56 DEBUG  WindowsBackend: arch=amd64
06-06 15:56 DEBUG  CommonBackend: Parsing isolist=C:\Windows\Temp\pylC72.tmp\data\isolist.ini
06-06 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-06 15:56 DEBUG  WindowsBackend: Fetching host info...
06-06 15:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-06 15:56 DEBUG  WindowsBackend: windows version=xp
06-06 15:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-06 15:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
06-06 15:56 DEBUG  WindowsBackend: windows_build=2600
06-06 15:56 DEBUG  WindowsBackend: gmt=-3
06-06 15:56 DEBUG  WindowsBackend: country=BR
06-06 15:56 DEBUG  WindowsBackend: timezone=America/Fortaleza
06-06 15:56 DEBUG  WindowsBackend: windows_username=Administrador
06-06 15:56 DEBUG  WindowsBackend: user_full_name=Administrador
06-06 15:56 DEBUG  WindowsBackend: user_directory=Administrador
06-06 15:56 DEBUG  WindowsBackend: windows_language_code=1034
06-06 15:56 DEBUG  WindowsBackend: windows_language=Spanish
06-06 15:56 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
06-06 15:56 DEBUG  WindowsBackend: bootloader=xp
06-06 15:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43976.515625 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(C: hd 43976.515625 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(D: hd 58015.6914063 mb free ntfs)
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: uninstaller_path=None
06-06 15:56 DEBUG  WindowsBackend: previous_target_dir=None
06-06 15:56 DEBUG  WindowsBackend: previous_distro_name=None
06-06 15:56 DEBUG  WindowsBackend: keyboard_id=67765258
06-06 15:56 DEBUG  WindowsBackend: keyboard_layout=br
06-06 15:56 DEBUG  WindowsBackend: keyboard_variant=
06-06 15:56 DEBUG  CommonBackend: locale=es_ES.UTF-8
06-06 15:56 DEBUG  WindowsBackend: total_memory_mb=1023.23046875
06-06 15:56 DEBUG  CommonBackend: Searching ISOs on USB devices
06-06 15:56 DEBUG  CommonBackend: Searching for local CDs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC72.tmp is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC72.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-06 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-06 15:56 INFO   Distro: Found a valid CD for Ubuntu: I:\
06-06 15:56 INFO   root: Running the CD menu...
06-06 15:56 DEBUG  WindowsFrontend: __init__...
06-06 15:56 DEBUG  WindowsFrontend: on_init...
06-06 15:56 INFO   WindowsFrontend: Operation cancelled
06-06 15:56 DEBUG  WindowsFrontend: frontend.quit
06-06 15:56 DEBUG  WindowsFrontend: frontend.on_quit
06-06 15:56 DEBUG  root: application.on_quit
06-06 15:56 INFO   root: sys.exit
06-06 15:56 INFO   root: === wubi 9.04 rev128 ===
06-06 15:56 DEBUG  root: Logfile is c:\windows\temp\wubi-9.04-rev128.log
06-06 15:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
06-06 15:56 DEBUG  CommonBackend: data_dir=C:\Windows\Temp\pylC73.tmp\data
06-06 15:56 DEBUG  WindowsBackend: 7z=C:\Windows\Temp\pylC73.tmp\bin\7z.exe
06-06 15:56 DEBUG  CommonBackend: Fetching basic info...
06-06 15:56 DEBUG  CommonBackend: original_exe=I:\wubi.exe
06-06 15:56 DEBUG  CommonBackend: platform=win32
06-06 15:56 DEBUG  CommonBackend: osname=nt
06-06 15:56 DEBUG  CommonBackend: language=es_ES
06-06 15:56 DEBUG  CommonBackend: encoding=cp1252
06-06 15:56 DEBUG  WindowsBackend: arch=amd64
06-06 15:56 DEBUG  CommonBackend: Parsing isolist=C:\Windows\Temp\pylC73.tmp\data\isolist.ini
06-06 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-06 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-06 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-06 15:56 DEBUG  WindowsBackend: Fetching host info...
06-06 15:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-06 15:56 DEBUG  WindowsBackend: windows version=xp
06-06 15:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-06 15:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
06-06 15:56 DEBUG  WindowsBackend: windows_build=2600
06-06 15:56 DEBUG  WindowsBackend: gmt=-3
06-06 15:56 DEBUG  WindowsBackend: country=BR
06-06 15:56 DEBUG  WindowsBackend: timezone=America/Fortaleza
06-06 15:56 DEBUG  WindowsBackend: windows_username=Administrador
06-06 15:56 DEBUG  WindowsBackend: user_full_name=Administrador
06-06 15:56 DEBUG  WindowsBackend: user_directory=Administrador
06-06 15:56 DEBUG  WindowsBackend: windows_language_code=1034
06-06 15:56 DEBUG  WindowsBackend: windows_language=Spanish
06-06 15:56 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
06-06 15:56 DEBUG  WindowsBackend: bootloader=xp
06-06 15:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43969.9804688 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(C: hd 43969.9804688 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(D: hd 58015.6914063 mb free ntfs)
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
06-06 15:56 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
06-06 15:56 DEBUG  WindowsBackend: uninstaller_path=None
06-06 15:56 DEBUG  WindowsBackend: previous_target_dir=None
06-06 15:56 DEBUG  WindowsBackend: previous_distro_name=None
06-06 15:56 DEBUG  WindowsBackend: keyboard_id=67765258
06-06 15:56 DEBUG  WindowsBackend: keyboard_layout=br
06-06 15:56 DEBUG  WindowsBackend: keyboard_variant=
06-06 15:56 DEBUG  CommonBackend: locale=es_ES.UTF-8
06-06 15:56 DEBUG  WindowsBackend: total_memory_mb=1023.23046875
06-06 15:56 DEBUG  CommonBackend: Searching ISOs on USB devices
06-06 15:56 DEBUG  CommonBackend: Searching for local CDs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether C:\Windows\Temp\pylC73.tmp is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain C:\Windows\Temp\pylC73.tmp\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-06 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-06 15:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-06 15:56 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-06 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-06 15:56 INFO   Distro: Found a valid CD for Ubuntu: I:\
06-06 15:56 INFO   root: Running the CD menu...
06-06 15:56 DEBUG  WindowsFrontend: __init__...
06-06 15:56 DEBUG  WindowsFrontend: on_init...
06-06 15:57 INFO   root: CD menu finished
06-06 15:57 INFO   root: Running the installer...
06-06 15:57 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=20000MB, distro_name=Ubuntu, language=Spanish, username=administrador
06-06 15:57 INFO   root: Received settings
06-06 15:57 DEBUG  TaskList: # Running tasklist...
06-06 15:57 DEBUG  TaskList: ## Running select_target_dir...
06-06 15:57 INFO   WindowsBackend: Installing into D:\ubuntu
06-06 15:57 DEBUG  TaskList: ## Finished select_target_dir
06-06 15:57 DEBUG  TaskList: ## Running create_dir_structure...
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-06 15:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-06 15:57 DEBUG  TaskList: ## Finished create_dir_structure
06-06 15:57 DEBUG  TaskList: ## Running uncompress_target_dir...
06-06 15:57 DEBUG  TaskList: ## Finished uncompress_target_dir
06-06 15:57 DEBUG  TaskList: ## Running create_uninstaller...
06-06 15:57 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
06-06 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
06-06 15:57 DEBUG  TaskList: ## Finished create_uninstaller
06-06 15:57 DEBUG  TaskList: ## Running copy_installation_files...
06-06 15:57 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pylC73.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-06 15:57 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pylC73.tmp\winboot -> D:\ubuntu\winboot
06-06 15:57 DEBUG  WindowsBackend: Copying C:\Windows\Temp\pylC73.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-06 15:57 DEBUG  TaskList: ## Finished copy_installation_files
06-06 15:57 DEBUG  TaskList: ## Running get_iso...
06-06 15:57 DEBUG  TaskList: New task copy_file
06-06 15:57 DEBUG  TaskList: ### Running copy_file...
06-06 16:00 DEBUG  TaskList: ### Finished copy_file
06-06 16:00 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
06-06 16:00 DEBUG  TaskList: # Cancelling tasklist
06-06 16:00 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
06-06 16:00 DEBUG  TaskList: New task check_iso
06-06 16:00 DEBUG  CommonBackend: Searching for local ISO
06-06 16:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-06 16:00 DEBUG  TaskList: New task get_metalink
06-06 16:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-06 16:00 DEBUG  TaskList: # Cancelling tasklist
06-06 16:00 DEBUG  TaskList: # Finished tasklist

```

¿Tiene solución? Al cd lo queme bien, lo revise por si tiene errores y no tiene ningúno

---

### Post by luks911 on 2009-06-06
A ver si esto[0] te ayuda. Entiendo que tenés que usar la iso desde tu rígido en lugar de un CD.

[0] [http://ubuntuforums.org/showthread.php?t=1146634](http://ubuntuforums.org/showthread.php?t=1146634)

---

### Post by juancarlospaco on 2009-06-06
*Solo vengo a decir que recomiendo instalarlo directamente en una particion EXT4.*

---

### Post by pablocerg on 2009-06-06
> **juancarlospaco said:**
> *Solo vengo a decir que recomiendo instalarlo directamente en una particion EXT4.*

Gracias, con una partición de 8gb andare bien?

---

### Post by luks911 on 2009-06-06
Me sumo a la recomendación. Con 8gb estás ajustado, pero estás. Si no pretendés hacer nada fuera de lo que hace un usuario doméstico (como yo) podés dividir en dos con 5 para / y 3 para /home.

---

### Post by Hei Ku on 2009-06-06
La unica advertencia sobre ext4 es que es nueva y tiene problemas. Si bien es mas rapida, todavia se esta depurando y yo no la recomendaria para usuarios nuevos.

---

### Post by staar on 2009-06-06
ext4 no tiene problemas para uso común, de escritorio, por lo menos en mi experiencia personal, desde hace un par de meses tengo arch y ubuntu en ext4, cero problemas, y la mejora en velocidad es considerable...

me parece que si no fuera lo suficientemente estable, no hubiera sido liberada como tal...


saludos

---

### Post by Hei Ku on 2009-06-06
Durante la beta, hubo muchos reportes de gente que perdio el disco completo. Y estoy hablando de un par de meses antes de la release final. 

Si pensás que de no ser estable no la hubieran liberado, me limito a poner como ejemplo kde 4.1. ;)

---

### Post by pablo.s on 2009-06-06
Es muy cierto lo que comenta
Hei Ku. Pero como sabemos las
circunstancias de una máquina
pueden no ser las de otra.
El soporte a los file systems se
va mejorando a medida que
pasa el tiempo, como otros
aspectos claves del sistema.
Yo estoy esperando con bastante
ansiedad las alphas de Karmic
que supuestamente traen el
soporte de brtfs en 2.6.30.

---

### Post by pablocerg on 2009-06-06
> **luks911 said:**
> Me sumo a la recomendación. Con 8gb estás ajustado, pero estás. Si no pretendés hacer nada fuera de lo que hace un usuario doméstico (como yo) podés dividir en dos con 5 para / y 3 para /home.

Gracias por el consejo, igualmente soy muy inexperto, solo se usar partition magic, e instalar windows :P
Y por el momento solo quiero probar ubuntu, espero que pueda adaptarme a el y encontrar las altenartivas de soft de mi so actual y en algún momento tener solo ubuntu en mi pc.

---

### Post by pablo.s on 2009-06-06
> **pablocerg said:**
> Y por el momento solo quiero probar ubuntu, espero que pueda adaptarme a el y encontrar las altenartivas de soft de mi so actual y en algún momento tener solo ubuntu en mi pc.

Has probado el LiveCD? Para
probar como vos queres, es
mucho mas util que instalar
desde Wubi.
Por reemplazar tus programas
habituales, no te preocupes,
GNU/Linux en cualquiera de sus
distribuciones tiene un amplio
catalogo de software libre, que
es mucho mejor que el software
de Windows. Tiene algunas 
excepciones en cuanto a ciertos
generos muy especificos, pero
para la gran mayoria de los
usuarios y programadores esta
100% listo para ser un sistema
principal.

---

### Post by pablocerg on 2009-06-06
> **pablo.s said:**
> Has probado el LiveCD? Para
probar como vos queres, es
mucho mas util que instalar
desde Wubi.
Por reemplazar tus programas
habituales, no te preocupes,
GNU/Linux en cualquiera de sus
distribuciones tiene un amplio
catalogo de software libre, que
es mucho mejor que el software
de Windows. Tiene algunas 
excepciones en cuanto a ciertos
generos muy especificos, pero
para la gran mayoria de los
usuarios y programadores esta
100% listo para ser un sistema
principal.

El live cd no puedo hacerlo andar por el problema de mi monitor (OUT OF RANGE) lo que voy a hacer al final es instalar el alternativo y usar la solución que me dieron en mi thread anterior [http://ubuntuforums.org/showthread.php?t=1179778](http://ubuntuforums.org/showthread.php?t=1179778)

---

### Post by staar on 2009-06-06
me acuerdo del mini-revuelo que se armó por esos reportes, pero también creo recordar que no eran culpa del FS, si no de algunas aplicaciones (creo que eran parte de KDE) que no respetaban el estándar en las escrituras a disco...

saludos

EDIT: [http://diegocg.blogspot.com/2009/04/mucho-mucho-ruido-sobre-ext4.html]("http://diegocg.blogspot.com/2009/04/mucho-mucho-ruido-sobre-ext4.html")

---

### Post by juancarlospaco on 2009-06-06
Estas equivocado Hei Ku con un uso adecuado EXT4 no pierde datos.

Ademas tampoco es nueva!, Sabayon la viene usando desde hace años, 
fue la primer distro en soportarlo oficialmente, la probe solo por eso,
andaba muy bien, igual me aburria compilar paquetes de OpenOffice y KDE demoraba demasiado.

*Con un uso inadecuado cualquier Filesystem puede perder datos.*

---

### Post by Hei Ku on 2009-06-06
juan carlos, le estas recomendando ext4 a un usuario nuevo. Estoy de acuerdo que probablemente no tenga problemas con un uso adecuado, pero seamos prudentes en lo que recomendamos a usuarios nuevos. Por un poco de velocidad podes terminar generandole un problema y una mala experiencia.

Fue incluido por primera vez en el kernel anterior, hace menos de 6 meses. Hubo problemas durante la jaunty de beta. Es muy bueno, pero le falta un tiempo natural de pulido.

---

### Post by Tosh78 on 2009-06-06
Volviendo al tema del Wubi, desfragmentaste el disco antes de intentar instalarlo. Si no lo hiciste, hacelo y proba de instalarlo. Es muy comun que si no esta desfragmentado de error.

---

