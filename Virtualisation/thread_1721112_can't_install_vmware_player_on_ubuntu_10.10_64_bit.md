---
title: "can't install vmware player on ubuntu 10.10 64 bit"
date: 2011-04-04
forum: Virtualisation
---

### Post by hagai_sela on 2011-04-04
Hi,
I am trying to install vmware player 3.1.3 on my ubuntu 10.10 machine. the install script crashes because a python related error (I think). This is the log (/var/log/vmware-installer)

[2011-04-04 10:59:17,253] 
[2011-04-04 10:59:17,254] 
[2011-04-04 10:59:17,254] Installer running.
[2011-04-04 10:59:17,254] Command Line Arguments:
[2011-04-04 10:59:17,254] ['/tmp/vmis.ZGOuEc/install/vmware-installer/vmware-ins
taller.py', '--set-setting', 'vmware-installer', 'libconf', '/tmp/vmis.ZGOuEc/in
stall/vmware-installer/lib/libconf', '--install-component', '/tmp/vmis.ZGOuEc/in
stall/vmware-installer', '--install-bundle', '/home/hagai/Downloads/./VMware-Pla
yer-3.1.3-324285.x86_64.bundle', '']
[2011-04-04 10:59:17,420] Successfully loaded GTK libraries.
[2011-04-04 10:59:17,443] Using UI type gtk
[2011-04-04 10:59:17,460] Uncaught exception in installer:
Traceback (most recent call last):
  File "/tmp/vmis.ZGOuEc/install/vmware-installer/vmware-installer.py", line 613
, in <module>
    main(options)
  File "/tmp/vmis.ZGOuEc/install/vmware-installer/vmware-installer.py", line 292
, in main
    UseNewestInstaller()
  File "/tmp/vmis.ZGOuEc/install/vmware-installer/vmware-installer.py", line 246
, in UseNewestInstaller
    exitCode = os.execv(systemInstaller, args)
OSError: [Errno 2] No such file or directory


Thanks,
Hagai.

---

