---
title: "virtualbox (dkms issue) not working since upgrade to 16.04"
date: 2016-07-04
forum: Virtualisation
---

### Post by Grummfy on 2016-07-04
Hello,
since I have upgraded to ubuntu 16.04, virtualbox doesn't work anymore.

I have already purged and reinstalled the package (virtualbox & virtualbox-dkms). The linux-headers are installed correctly. They are installed from ubutu repositories.

So here is the sudo dpkg-reconfigure virtualbox-dkms
> 
-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.0.18
Kernel:  4.4.0-28-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 5.0.18
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.0.18 DKMS files...
Building only for 4.4.0-28-generic
Building initial module for 4.4.0-28-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-28-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-28-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-28-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-28-generic/updates/dkms/

depmod....

DKMS: install completed.
Job for virtualbox.service failed because the control process exited with error code. See "systemctl status virtualbox.service" and "journalctl -xe" for details.
invoke-rc.d: initscript virtualbox, action "restart" failed.

When i do a systemctl status virtualbox.service
> virtualbox.service - LSB: VirtualBox Linux kernel module
   Loaded: loaded (/etc/init.d/virtualbox; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since lun 2016-07-04 22:49:01 CEST; 24s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 20190 ExecStart=/etc/init.d/virtualbox start (code=exited, status=1/FAILURE)

jui 04 22:49:01  systemd[1]: Starting LSB: VirtualBox Linux kernel module...
jui 04 22:49:01  virtualbox[20190]:  * Starting VirtualBox kernel modules
jui 04 22:49:01  virtualbox[20190]:  * modprobe vboxdrv failed. Please use 'dmesg' to find out why
jui 04 22:49:01  virtualbox[20190]:    ...fail!
jui 04 22:49:01  systemd[1]: virtualbox.service: Control process exited, code=exited status=1
jui 04 22:49:01  systemd[1]: Failed to start LSB: VirtualBox Linux kernel module.
jui 04 22:49:01  systemd[1]: virtualbox.service: Unit entered failed state.
jui 04 22:49:01  systemd[1]: virtualbox.service: Failed with result 'exit-code'.


the only message in dmesg is
> [12669.861664] capability: warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)


Anyone have a solution?

---

### Post by Grummfy on 2016-07-04
sorry it appears the the bug already exist on launchpad : [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1574300](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1574300)

---

### Post by SeijiSensei on 2016-07-05
Do you have the same problems if you install the version of VirtualBox in Oracle's own repository: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)?

---

### Post by MAFoElffen on 2016-07-05
uninstall & install virtualbox-dkms. I'm out the door, so in a hurry, but there are many threads in the sections with the commands to do that, if you did a search on this section...

---

### Post by Grummfy on 2016-07-05
Thanks.

As I say, I already remove, even purge package and reinstall it. It change absolutely nothing. Each of the treads seems resolved with that but it's not my case, unfortunately.

I have not try yet the oracle repositories.

thanks

---

