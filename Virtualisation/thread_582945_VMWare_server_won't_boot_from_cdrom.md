---
title: "VMWare server won't boot from cdrom"
date: 2007-10-20
forum: Virtualisation
---

### Post by chrisch on 2007-10-20
I just installed vmware server according to [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) and everything went great.  I created a new virtual machine but when I power up the machine it opens, shows a black screen, and then powers off.  I am assuming because it can't find the cdrom.

So I can't get Windows or PCLinux installed on a virtual machine.

I am running Gutsy.

---

### Post by scottishnarn on 2007-11-07
I've got exactly the same problem. I can't get access to either a real CD or an iso file. I've used 1.0.3 and 1.0.4 with identical results. When I try to boot it, the icon for the CD in the  bottom right corner has a red cross across it.

I'm running Ubuntu 7.10.

---

### Post by koenn on 2007-11-08
check, in the virtual machine's properties, that the checkbox for CD-ROM "connect at power on'"  is checked.

point the virtual cdrom to  device rather than to the folder where you mount your cdroms. I.e use /dev/cdrom or /dev/hdc ( .... )  in stead of /media/cdrom : the mounted filesystem doesn't include the cd-rom's boot sector, and that's what you need to boot from it.

---

### Post by chrisch on 2007-11-14
I solved my problem.  I was trying to install it on an external usb drive and VMWare didn't like it.  Once I took the default location for my Win XP file it worked fine.

---

### Post by halfconscious on 2007-12-18
I'm still struggling with this same problem - I have an external USB
CD on a Dell Latitude D410 and the VM won't boot from it.

I don't understand what your mean by
"Once I took the default location for my Win XP file it worked fine"

It seems to give you the option of booting from an ISO image - but
the dialogs only seem to lead you to the virtual disk of the VM.
I assumed I had to find a way to copy the .iso to the .vmdk - but  I
have not found a way to do it.  I can mount the .vmdk using
vmware-mount - but all I can see is a flat file.

---

### Post by koenn on 2007-12-18
there's a "Browse" button there that lets you browse to any (iso) file on the VM host ...

---

### Post by halfconscious on 2007-12-18
I'm trying to access it with the web interface and the browse just
takes me to what seems to be the virtual disk ... e.g. 'datastore' item and no option to go up through the directory hierarchy.

Things have progressed here ... after upgrading to gutsy ( starting
from 6.06LTS) running vmware-uninstall , deleting /etc/vmware , /var/lib/vmware and re-installing ( running vmware-install.pl ) and
'taking the defaults' for the CD ( i.e. physical device etc. ) windows
setup started.. from the USB CD . Hallelulah .

The web 'console' is a bit cranky for me. It locked my mouse in
- fortunately I thought to try CTRL-ALT-ENTER ( as on vmware workstation ) which actually toggles you to a full screen version
and back - and in so doing seemed to get my mouse back to 
Linux. Hopefully I'm off now.


Incidentally , when I try running 'vmware'  I get the following
#vmware
Try 'man vmware' for more information.
#vmware -v
VMware Server e.x.p build-63231

---

### Post by BLTicklemonster on 2007-12-30
I can't boot from an iso image, or a cd. I've been trying like mad with different distros, and never can get it to work.

I create a new cdrom, set it to boot from iso image, and browse to it, and nothing.

I remove that, then set the originally created cdrom to /dev/cdrom or any other setitng and nothing happens.

I remove the originally created cdrom, create a new one and set it to boot from iso image, browse to it, and nothing happens.

BUT, once or twice, I have gotten it working, but I have no earthly idea how, and it never worked again after that, no matter how much tinkering I did with it.

I'd really like to test new live cds but this is quite crazy.

Is there a step by step How To on booting vmware from an iso image?

---

### Post by oarion7 on 2008-06-14
bump

Having the exact same problem here. But internal drives, on laptop. When I power on the vm, it shows the black screen for about 1 second or 2, then exits back to the main console. During the black screen I see a small cd icon among others with a non sign over it. I've tried several different device locations for my cdrom as well as mount points and even ISO images. Cannot get it to boot from the cd, cannot get it to boot from the iso.

vmware server 1.0.6 on Hardy

Any help?

EDIT: I am also unable to access any kind of BIOS screen while the black screen is up. Tried esc, f2, and del.

---

### Post by oarion7 on 2008-06-15
ok it seems that the bios option is probably obsolete and replaced with the preferences option. so i've gone through there a couple types, set cd to connect at power on, tried a few difference device locations:

/dev/cdrom
/dev/scd0
auto detect
etc...

no luck.

---

### Post by BLTicklemonster on 2008-06-16
I've moved to virtualbox, myself.

---

### Post by oarion7 on 2008-06-16
> **oarion7 said:**
> bump

Having the exact same problem here. But internal drives, on laptop. When I power on the vm, it shows the black screen for about 1 second or 2, then exits back to the main console. During the black screen I see a small cd icon among others with a non sign over it. I've tried several different device locations for my cdrom as well as mount points and even ISO images. Cannot get it to boot from the cd, cannot get it to boot from the iso.

vmware server 1.0.6 on Hardy


Problem solved. Was trying to use a virtual drive on NTFS. Reparitioned a ext3 and it worked great!! am now successfully running Windows 98 with vmware tools in vmware server! internet and everything, got it, worked perfectly.

---

### Post by ojlnx on 2008-06-28
hey, i had the same problem what i did i went into vm configuration, chose power tab and ticked "Enter the BIOS setup screen the next time the virtual machine boots". Then i booted up the machine and changed the boot order in bios. Worked like a magic. ;)

---

### Post by antispin on 2010-01-05
This worked for me as well, although what I did was boot up the VM, hit F2 to enter the BIOS and changed the boot order. Never had this issue when installing other VMs.

If you stumble across this thread, try it -- it only takes a second and it might fix your problem.

---

