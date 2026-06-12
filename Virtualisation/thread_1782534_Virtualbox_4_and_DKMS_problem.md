---
title: "Virtualbox 4 and DKMS problem?"
date: 2011-06-14
forum: Virtualisation
---

### Post by pepsifx357 on 2011-06-14
Can anyone tell me what this means.  I don't know what the DKMS is or does, but I do know that I seem to have a lot of problems with it.

```
ben@DAW:~/Downloads$ sudo dpkg -i virtualbox-4.0_4.0.8-71778~Ubuntu~lucid_i386.deb 
Selecting previously deselected package virtualbox-4.0.
(Reading database ... 194904 files and directories currently installed.)
Unpacking virtualbox-4.0 (from virtualbox-4.0_4.0.8-71778~Ubuntu~lucid_i386.deb) ...
Setting up virtualbox-4.0 (4.0.8-71778~Ubuntu~lucid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
update-rc.d: warning: vboxdrv stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  /usr/bin/sort: line 2: syntax error near unexpected token `('
/usr/bin/sort: line 2: `&#65533;OK&#65533;&#65533; &#65533;1N-+X&#65533;S&#65533;&#65533;d&#65533;&#65533;lU^&#65533;&#65533;&#1726;<L)&#65533;&#1725;&#65533;PN&#65533;&#65533;&#65533;&#65533;TP&#65533;&#1812;&#65533;&#65533;
                                                                       &#841;&#65533;&#65533;&#65533;>7z&#65533;&#65533;nS^&#65533;^&#65533;&#65533;&#65533;q&#946;q&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;W`[&#65533;2&#65533;&#65533;N)$&#65533;&#65533;&#65533;&#65533;{]&#65533;&#958;&#65533;tv&#65533;&#65533;4&#65533;<&#65533;f&#1545;WN&#65533;&#65533;J+]&#65533;&#65533;e&#892;\&#65533;&#65533;&#65533;&#65533;&#65533;Z&#65533;&#65533;n &#65533;91&#65533;&#65533;V&#8762;xE&#65533;4&#65533;Wó&#65533;&#65533;UmZ&#65533;&#65533;&#1651;l&#65533;&#65533;&#65533;&#65533;}lq&#65533;U&#65533;&#65533;&#65533;F&#65533;0yU&#65533;yyq&#65533;&#65533;H&#65533;&#65533;g&#65533;&#1852;&#65533;lW&#65533;&#65533;_t&#65533;2zCA^Np&#65533;&#65533;d&#1037;&#65533;c&#65533;&#65533;+&#960;&#65533;&#65533;&#65533;&#65533;W'&#65533;&#65533;&#65533;&#65533;2[~&#65533;3/R&#685;(&#65533;WQ&#65533;P&#65533;&#65533;LXSX&#65533;W&#65533;W8&#65533;!]X&#65533;&#65533;&#65533;&#65533;&#668;b9=&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;&#65533;&#65533;e&#65533;aV&#65533;&#65533;&#65533;&#65533;2&#65533;qA&#65533;&#65533;&#65533;g&#1653;&#65533;f;&#65533;m&#65533;&#65533;&#65533;\y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;'
/usr/sbin/dkms: line 535: [: : integer expression expected
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.

Error! Bad conf file.
File: /usr/src/vboxhost-4.0.8/dkms.conf
does not represent a valid dkms.conf file.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                 [ OK ] 
 * Starting VirtualBox kernel modules                                           
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why

Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-central ...
Processing triggers for python-support ...

```

I'va recently installed, from PPA, the kernel 2.6.38

```
ben@DAW:~$ uname -a
Linux DAW 2.6.38-1-generic #27~lucid1-Ubuntu SMP Thu Jan 27 10:54:07 UTC 2011 i686 GNU/Linux

```

I got my Nvidia straightened out finally but I can't seem to fix this issue.

Thanks

---

### Post by cometdog on 2011-06-28
Yes, I am seeing a DKMS problem on the latest Virtualbox on Maverick.

DKMS is something which is used so that kernel modules which provide certain functionality can be built separately from kernel releases.  It's used by stuff which requires certain kind of kernel driver support and is great when it works because it means that when you update to a new kernel, you don't have to build a new kernel from scratch to support that software or hardware.

In this case you should try to open a terminal and run virtualbox from the command line.  When I do so I get this:
```
:~$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.35-30-generic-pae) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

```

so I follow the instructions and do 
```
:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for me: 
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxhost/4.0.8/source/dkms.conf does not represent
a valid dkms.conf file.
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                               [ OK ] 
 * Starting VirtualBox kernel modules                                                        [ OK ] 
```

Lo and behold, despite the error messages, virtualbox works now.

HTH

---

