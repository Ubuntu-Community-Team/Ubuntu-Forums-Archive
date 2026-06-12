---
title: "[SOLVED] Vmware Server 1.0.4 not picking Printer as USB peripheral in Gusty"
date: 2007-10-23
forum: Virtualisation
---

### Post by ashishgoel on 2007-10-23
Hi all,

I upgraded to Ubuntu 7.10 recently from 7.04 and as there is no support from the Ubuntu Community(The program not available in Add/Remove and also not in Automatix) for Vmware Server, I installed latest VMware Server directly. Everything is working fine after some tweaking but the server is not recognizing my attached Canon MP110 printer as USB peripheral because of which I'm not able to use it with the Guest operating system(WinXP). The printer is working fine in the Ubuntu 7.10 installation and had no problem in 7.04 version with Vmware Server 1.0.3.

Please help

Thanx



Solution No.1

SOLVED

Please open the following file: /etc/init.d/mountdevsubfs.sh by following command - gksudo gedit /etc/init.d/mountdevsubfs.sh

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Restart and your usb devices will be recognised


Solution No. 2 (Thanx to Jome2)

The problem with Workstation can be resolved by:
sudo mount -t usbfs none /proc/bus/usb/

---

### Post by empty89 on 2007-10-23
I am having the same problem as u have.. In ubuntu fiesty, i was able to install my printer in my winXP in vmware player 2.0, right now, after doing a fresh install of gutsy my printer is not detected by vmware, so i cant connect my printer directly to my vmware player.. i need to print my document. it is important

---

### Post by stuffer007 on 2007-10-23
your not the only one. Mine is not a printer, but USB thumb drives and my Ipod do not pass through into vmware.

---

### Post by tcdrewiv on 2007-10-24
I had same problem after upgrade. After installing vmware server 1.04  it would not see any usb devices until i uncommented the  4 lines in the file below.  This also worked for virtual box.

/etc/init.d/mountdevsubfs

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

see [http://www.virtualbox.org/ticket/747]("http://www.virtualbox.org/ticket/747")

now vmware will locate any usb connections as before

---

### Post by Dripbagulhos on 2007-10-25
Hi tcdrewiv,

Thank you very much! It does work perfectlly for me. I was using Kubuntu 7.04 + VMWare Server 1.03 where everything worked fine. When I moved to Ubuntu 7.10 + VMWare Server 1.04 I lost all USB devices.

The clue you gave, did the trick, but there is one question... Why these 4 lines wheren't uncomented by default? :-)

---

### Post by tcdrewiv on 2007-10-25
I have no idea.  People a lot smarter than me may have an answer.  I have been an ubuntu user since dapper and I have always been able to find an answer to any problem on these forums.  I was glad to pass the answer along.

---

### Post by ashishgoel on 2007-10-25
i'll be glad if anyone could be little more explainatory on how to do it exactly...

thanx

---

### Post by ashishgoel on 2007-10-25
SOLVED

Please open the following file: /etc/init.d/mountdevsubfs.sh      by following command -     gksudo gedit /etc/init.d/mountdevsubfs.sh

Find the following lines:
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:
   mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb


Restart and your usb devices will be recognised.

---

### Post by jome2 on 2007-11-02
I use vmware workstation 6.0.0 on Ubuntu 7.10 and have this problem as well.
Umark (uncomment) of these lines do nothing.

Earlier I have used vmware workstation 6.0.0-beta on Ubuntu 7.04 and it worked fine.

What can I try more to solve the problem? :confused:

---

### Post by jome2 on 2007-11-06
The problem with Workstation can be resolved by:
sudo mount -t usbfs none /proc/bus/usb/

The resolution from:
[http://communities.vmware.com/message/617688](http://communities.vmware.com/message/617688)
"There is allegations that /proc/bus/usb/ is insecure, but that Vmware refuses to change to the new standard."

---

### Post by cenwesi on 2007-11-07
omg, it worked. This need to be made a sticky! Finally i can make use of my printer again.... :)

The wife will be happy again.

---

### Post by xanderp123 on 2008-04-20
I am having the same problem... The "VM -> Removable Devices -> USB Devices menu is empty". I have uncommented lines 42-45 in gksudo gedit /etc/init.d/mountdevsubfs.sh, and restarted my computer (i.e. host os which is Ubuntu) several times. I have also tried running the command 'sudo mount -t usbfs none /proc/bus/usb/' which is supposed to fix VM Workstation. I have also tried running the "/etc/init.d/mountdevsubfs.sh" manually, but get the following error:

ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists

None of the above actions fixed the problem. The" USB Devices" menu is still empty! (Yes, I am sure I have plugged in my USB devices... I have also tried starting the computer with and without them plugged in). My goal is to get my VTech Skype phone working with Windows XP Pro running on a VMWare virtual machine. I have also tried connecting a USB flash drive and my HP PSC 1315 (usb all-in-one printer, scanner and copier), none of which seem to work.

I am running VMWare Server 1.0.5 build-80187 on Ubuntu 7.10 (Gutsy). I installed VMWare from the tar.gz binary and just accepted all the default settings during installation. Did I miss something perhaps?

Any help or suggestions would be greatly appreciated! I would be happy to provide any technical details about by system that you may need.

---

### Post by ashishgoel on 2008-04-20
what i can suggest u is to remove the current installation and install from Software List of ubuntu or from Automatix...

---

