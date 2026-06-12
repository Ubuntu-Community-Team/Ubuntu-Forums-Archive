---
title: "virtualbox 4.o cant load kernel, 3.2 does load ok"
date: 2010-12-28
forum: Virtualisation
---

### Post by sdowney717 on 2010-12-28
I would like to have this working as I want USB to work
[http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/](http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/)
site says dont use the one in the repos, so I followed but of course having issues.

> scott@scott-desktop:~$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.35-23-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

any steps on how to recompile the module?

---

### Post by gordintoronto on 2010-12-29
I've used VirtualBox with USB support, and I've never compiled anything. I went to the VirtualBox web site, downloaded the appropriate .deb from here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) 
and double-clicked on it.

But first, remove whatever you have been trying to run.

---

### Post by b0b138 on 2010-12-29
run the command that the message said
```
sudo /etc/init.d/vboxdrv setup
```
This has to be done if you had a kernel update as kernel modules have to be redone for the new kernel. If you have DKMS installed this should happen automatically.

Also, with VBox 4, you now have to download and install a seperate "Extension Pack" which can be found on the main downloads page.

---

### Post by sdowney717 on 2010-12-29
> sudo /etc/init.d/vboxdrv setup

does nothing at all, not easy to make this work. Unless you know the secret apparently.

> scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for scott: 
sudo: /etc/init.d/vboxdrv: command not found
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2010-12-29
I looked in that folder and that file does not exist. I downloaded 4.0 deb from virtualbox.org

dkms is already installed, so what is going on you think?

> scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for scott: 
sudo: /etc/init.d/vboxdrv: command not found
scott@scott-desktop:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2010-12-29
reinstalled still nothing

where can I download the vboxdrv file??

> scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for scott: 
sudo: /etc/init.d/vboxdrv: command not found
scott@scott-desktop:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2010-12-29
vboxdrv.dpkg-bak
vboxdrv.dpkg-dist

are the only related files in the folder, vboxdrv file does not exist!

> scott@scott-desktop:~$ ls /etc/init.d/
acpid                       plymouth
acpi-support                plymouth-log
alsa-mixer-save             plymouth-splash
anacron                     plymouth-stop
apparmor                    policykit
apport                      postfix
atd                         pppd-dns
avahi-daemon                procps
binfmt-support              pulseaudio
bluetooth                   qemu-kvm
bootlogd                    rc
bridge-network-interface    rc.local
brltty                      rcS
console-setup               README
couchdb                     reboot
cron                        rsync
cups                        rsyslog
dbus                        saned
dmesg                       screen-cleanup
dns-clean                   sendsigs
dnsmasq                     sensord
etc-setserial               setserial
failsafe-x                  single
fancontrol                  skeleton
gdm                         smbd
gpsd                        speech-dispatcher
grub-common                 stop-bootlogd
halt                        stop-bootlogd-single
hostname                    sudo
hwclock                     sysfsutils
hwclock-save                udev
irqbalance                  udev-finish
kerneloops                  udevmonitor
killprocs                   udevtrigger
libvirt-bin                 ufw
lirc                        uml-utilities
llink                       umountfs
llink~                      umountnfs.sh
lm-sensors                  umountroot
logmein-hamachi             unattended-upgrades
mbmon                       urandom
mediatomb                   ushare
module-init-tools           vboxdrv.dpkg-bak
networking                  vboxdrv.dpkg-dist
network-interface           vboxweb-service
network-interface-security  vdr
network-manager             vdradmin-am
nmbd                        virtualbox-ose
ntop                        virtualbox-ose-guest-utils
ntp                         vmware
nvidia-kernel               webmin
ondemand                    x11-common
pcmciautils


---

### Post by sdowney717 on 2010-12-29
ok found it, but they dont call it the same file anymore
new file name is vboxdrv.dpkg-bak


> scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv.dpkg-bak setup
[sudo] password for scott: 
scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv.dpkg-dist setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
scott@scott-desktop:~$ 



---

### Post by sdowney717 on 2010-12-29
almost started but giving usb errors

where do I get this extension pack?

---

### Post by sdowney717 on 2010-12-29
[http://www.oracle.cc/2010/12/oracle-vm-virtualbox-4-0-extension-packs/](http://www.oracle.cc/2010/12/oracle-vm-virtualbox-4-0-extension-packs/)
no download link
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

ok foundit
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

different error and it is still broken for usb
they make it very hard dont they?
CAN IT BE DUE TO RESTORING A SAVED STAT OF THE VM???
if so, how do i unsave and do a startup of the vm??

---

### Post by sdowney717 on 2010-12-29
well, I made a new machine, tied it to the same vdi file and it starts, but for some reason it is missing sp3 and all the changes I had made to the saved one that wont start

---

### Post by sdowney717 on 2010-12-29
LOL, now it tells me it is not available for this PC!

I think I got it by uninstalling ver4, reinstalling vbox ose, restoring the machine state, stopping the machine, uninstalling vbox-ose, reinstalling ver 4, redoing the kernel modules

---

### Post by sdowney717 on 2010-12-29
OK, big question.

why did making a new machine using the xppro32.vdi file from the machine where sp3 and google chrome and avast were installed NOT repeat NOT show these as installed in the new virtual machine?
the new machine simply showed it as I had originally had it setup without these other programs added in. But it was using the xppro32.vdi file from the old machine which does have them installed.

---

### Post by b0b138 on 2010-12-29
lol Well I'm glad you got it. I didn't have any issues installing but I uninstalled the old version first and made new machines.  Thats always seemed like a safe option to me, especialy with major version revisions.

As far as sp3 and chrome and avast? I have no idea lol.  Theres is absolutly no reason that should happen. I would have to guess it was using a different vdi than you thought.  Check through the hidden ~/.VirtualBox folder or do a search for vdi files.

---

### Post by b0b138 on 2010-12-29
or you restored the machine state with the wrong/old snapshot?

---

### Post by b0b138 on 2010-12-29
or you restored the machine state with the wrong/old snapshot?

---

### Post by b0b138 on 2010-12-29
or you restored the machine state with the wrong/old snapshot?

---

### Post by sdowney717 on 2010-12-29
> or you restored the machine state with the wrong/old snapshot?

yeah, maybe so.
I did save a snapshot before adding in that sp3.
How does the snapshot interelate to the vdi file?
I thought the vdi file was the VM.
Where is the snapshot?

So how would you back up the VM if it has a snapshot which somehow keeps the added in windows programs separated?

---

### Post by sdowney717 on 2010-12-29
For some reason, I always go thru the ringer with odd weird software issues when I try to do things. I learn a lot, but wish I did not have to!:p

---

