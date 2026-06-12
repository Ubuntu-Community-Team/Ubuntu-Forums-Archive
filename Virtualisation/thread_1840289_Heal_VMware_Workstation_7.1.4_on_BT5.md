---
title: "Heal VMware Workstation 7.1.4 on BT5"
date: 2011-09-07
forum: Virtualisation
---

### Post by baligh.bedewi on 2011-09-07
Hello and welcome friends...
I'm working on (**Backtrack 5 R1 kernel 2.6.39.4 KDE 4.5**) based on (**Ubuntu 10.04 Lucid**)
My work depend on Virtual Network, on WIN7 VMware worked perfectly. in BT5 :confused:
I searched over and over [@] backtrack-linux, ubuntuforum, ubuntugeek, linux-question... etc forums but still can't compile module
1- I tried 3 different installation of VMware Workstation **7.1**, **7.1.3** and **7.1.4**
2- After installing trying to prepare the kernel and to unrar patching and re-rar (vmci - vsock - vmnet - vmmon)
3- Compile Module[B][COLOR=#ff6600]
[/COLOR][/B]```
vmware-modconfig --console --install-all
```and this what I get

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201690&stc=1&d=1315396401[/IMG]

If I run Vmware I got this message 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201693&stc=1&d=1315396931[/IMG]

I did Install/Uninstall VMware Workstation, patching and reboot as much as I'm freak of vmware files which I think they are allover my root.

Did I made any wrong require installing fresh copy of BT5 or there is a solution and I'm a dumb ?!
Thanks in Advance

P.S: I'M NEW TO LINUX .

---

### Post by abvinodu2003 on 2011-10-10
[http://weltall.heliohost.org/wordpress/2011/06/26/vmware-7-3-4-guest-modules-fixes-for-linux-2-6-39-and-3-0/](http://weltall.heliohost.org/wordpress/2011/06/26/vmware-7-3-4-guest-modules-fixes-for-linux-2-6-39-and-3-0/)
 

try tis link i think it wil be helpfull to u

and also try tis procedure

How to install VMware Workstation 7.1.4 on Kernel 2.6.39.4, tested on Backtrack 5 R1 KDE (Ubuntu 10.04 Lucid)..
 1- Install VMware Workstation 7.1.4 from vmware.com (DON'T RUN) VMware will not run until you compile 5 module
 2- Download "vmware2.6.39fixed.patch" to compile the module manual (vmnet, vmmon, vmblock, vmci and vmsock)
 3- Copy the 5 module from the vmware installed directory to TMP, unrar,  patch, re-rar and replace them back. Just follow step No. 4
 4- OPEN SHELL and follow to complete compile
 ~mkdir /tmp/vmware && cd /tmp/vmware
 ~cp -R /usr/lib/vmware/modules/source/ .
 ~cd /tmp/vmware/source
 ~for i in ./*.tar; do tar -xf $i; done
 ~for i in ./*.tar; do mv $i $i.orginal; done
 ~patch -t -f -p1 < vmware2.6.39fixed.patch
 ~tar cf vmblock.tar vmblock-only
 ~tar cf vmci.tar vmci-only
 ~tar cf vmmon.tar vmmon-only
 ~tar cf vmnet.tar vmnet-only
 ~tar cf vsock.tar vsock-only
 ~cp -vf *.tar /usr/lib/vmware/modules/source/
 5- Run VMware.. It'll compile and you're ready to GO

---

