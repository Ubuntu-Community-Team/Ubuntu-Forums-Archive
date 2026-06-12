---
title: "lst Jaunty update killed my VMware, how can i recompile"
date: 2009-07-30
forum: Virtualisation
---

### Post by Ordes on 2009-07-30
After the last update, yesterday 07-30, my vmware is not working properly anymore.

As after every update, vmware toled my to recompile the kernel (click OK). However some parts could not be recompiled this time. So when i start up VMware my eth is not working. --> "cannot open /dev/vmnet/

The basic VMmachine is running though.

Restarting vmware didnt bring up the recompile dialog.

Uninstalling and reinstalling vmware didnt bring up the recompile dialog. So after uninstalling i tried:

$ locate vmware:
/etc/vmware
/etc/init.d/vmware
/etc/rc2.d/K08vmware
/etc/rc2.d/S19vmware
/etc/rc3.d/K08vmware
/etc/rc3.d/S19vmware
/etc/rc5.d/K08vmware
/etc/rc5.d/S19vmware
/etc/vmware/bootstrap
/etc/vmware/components
/etc/vmware/config
/etc/vmware/database
/etc/vmware/networking
/etc/vmware/vmnet1
/etc/vmware/vmnet8
/etc/xdg/menus/applications-merged/vmware-ace-vms.menu
/usr/bin/vmware
/usr/bin/vmware-acetool
/usr/bin/vmware-gksu
/usr/bin/vmware-modconfig
/usr/bin/vmware-mount
/usr/bin/vmware-netcfg
/usr/bin/vmware-networks
/usr/bin/vmware-ping
/usr/bin/vmware-remotemks
/usr/bin/vmware-tray
/usr/bin/vmware-uninstall
/usr/bin/vmware-unity-helper
/usr/bin/vmware-vdiskmanager
/usr/include/vmware-vix
/usr/lib/vmware
/usr/lib/vmware-vix
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/sbin/vmware-authd
/usr/share/app-install/desktop/vmware-user.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/applications/vmware-netcfg.desktop
/usr/share/applications/vmware-player.desktop
/usr/share/applications/vmware-workstation.desktop
/usr/share/bug/xserver-xorg-video-vmware
/usr/share/bug/xserver-xorg-video-vmware/script
/usr/share/desktop-directories/vmware-ace-vms.directory
/usr/share/doc/vmware-player
/usr/share/doc/vmware-vix
/usr/share/doc/vmware-workstation
/usr/share/doc/xserver-xorg-video-vmware
/usr/share/doc/xserver-xorg-video-vmware/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-vmware/changelog.gz
/usr/share/doc/xserver-xorg-video-vmware/copyright
/usr/share/icons/hicolor/16x16/apps/vmware-acevm.png
/usr/share/icons/hicolor/16x16/apps/vmware-netcfg.png
/usr/share/icons/hicolor/16x16/apps/vmware-player.png
/usr/share/icons/hicolor/16x16/apps/vmware-workstation.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-team.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm-clone.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm-legacy.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/24x24/apps/vmware-acevm.png
/usr/share/icons/hicolor/24x24/apps/vmware-netcfg.png
/usr/share/icons/hicolor/24x24/apps/vmware-player.png
/usr/share/icons/hicolor/24x24/apps/vmware-workstation.png
/usr/share/icons/hicolor/24x24/mimetypes/application-x-vmware-vm-clone.png
/usr/share/icons/hicolor/24x24/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/32x32/apps/vmware-player.png
/usr/share/icons/hicolor/32x32/apps/vmware-workstation.png
/usr/share/icons/hicolor/48x48/apps/vmware-acevm.png
/usr/share/icons/hicolor/48x48/apps/vmware-player.png
/usr/share/icons/hicolor/48x48/apps/vmware-workstation.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-snapshot.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-team.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmdisk.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmfoundry.png
/usr/share/icons/hicolor/scalable/apps/vmware-acevm.svg
/usr/share/icons/hicolor/scalable/apps/vmware-player.svg
/usr/share/icons/hicolor/scalable/apps/vmware-workstation.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-snapshot.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-team.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm-clone.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm-legacy.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vmfoundry.svg
/usr/share/man/man1/vmware.1.gz
/usr/share/man/man4/vmware.4.gz
/usr/share/mime/application/x-vmware-snapshot.xml
/usr/share/mime/application/x-vmware-team.xml
/usr/share/mime/application/x-vmware-vm.xml
/usr/share/mime/application/x-vmware-vmdisk.xml
/usr/share/mime/application/x-vmware-vmfoundry.xml
/usr/share/mime/packages/vmware-player.xml
/usr/share/xserver-xorg/pci/vmware.ids
/usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/vmware.h
/usr/src/linux-headers-2.6.28-13/arch/x86/include/asm/vmware.h
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums
/var/log/vmware-installer

so all those files are left.
Shall i manualy delete them? If so which ones? All?

Or how can i just retry the compile process?
Cuz they told me to look at the recomile error log. But i clicked over it, and couldnt find it anymore.

---

### Post by Cheesemill on 2009-07-30
No need to re-install, you just need to do:
```
 
sudo vmware-config.pl -d

```every time you update the kernel (this will recompile the VMware kernel modules).

---

### Post by Ordes on 2009-07-31
do i have to execute this command in a special directoy? because i get "command not found"

all the commands i got under vm* are:

vmnet-bridge                      
vmnet-detect                
vmnet-dhcpd                         
vmnet-natd                  
vmnet-netifup                 
vmnet-sniffer                  
vmplayer                  
vmrun                         
vmstat  
vm-support    
vmware
vmware-acetool
vmware-authd
vmware-gksu
vmware-modconfig
vmware-mount
vmware-netcfg
vmware-networks
vmware-ping
vmware-remotemks
vmware-tray
vmware-uninstall
vmware-unity-helper
vmware-vdiskmanager


also:
i see alot of people saying they have to answer several questions in the terminal when install vmware. For me it always a graphical installer when installling the bundle. Does this make any difference. Or is it just a newer version?

---

### Post by Ordes on 2009-08-01
ok. 

i tried 

$ sudo vmware-modconfig --console --install-all

eveything worked, except: (terminal)

Starting VMware services:
   Virtual machine monitor                       done
   Virtual machine communication interface       done
   Blocking file system                          done
   Virtual ethernet                              failed

when i run the vm, my machine loads up, expect:
i always get "no ethernet- /dev/vmware/eth" cannot be found...

i still tried install - reinstall couple of times without success..

sudo vmware-config.pl -d - is not working for me,, doesnt find command

is there any way to reinstall the virtual ethernet?

---

### Post by ROY.G.BIV on 2009-08-12
delete

---

### Post by Ordes on 2009-10-14
removed Vm-Ware, using Virtual Box, seems to work better

---

### Post by dcstar on 2010-03-06
> **Ordes said:**
> ok. 

i tried 

$ sudo vmware-modconfig --console --install-all

eveything worked, except: (terminal)

Starting VMware services:
   Virtual machine monitor                       done
   Virtual machine communication interface       done
   Blocking file system                          done
   Virtual ethernet                              failed

when i run the vm, my machine loads up, expect:
i always get "no ethernet- /dev/vmware/eth" cannot be found...

i still tried install - reinstall couple of times without success..

sudo vmware-config.pl -d - is not working for me,, doesnt find command

is there any way to reinstall the virtual ethernet?

Old thread, but this should not be left uncorrected.

Do **not** use the "-d" defaults option when there is a problem, you must use the normal *sudo vmware-config.pl* process and manually **fix **the area that is not working.

All "-d" does is re-use the same broken configuration.

---

