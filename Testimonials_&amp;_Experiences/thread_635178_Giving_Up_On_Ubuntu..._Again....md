---
title: "Giving Up On Ubuntu... Again..."
date: 2007-12-08
forum: Testimonials &amp; Experiences
---

### Post by eob on 2007-12-08
I'm a huge Linux and open-source software fan. Seriously. I got hooked a few months ago by installing Linux Puppy on a PC that wouldn't run Windows Me, let alone XP, and was absolutely amazed by the product so set about making a triple-boot PC with Ubuntu/Puppy and Windows.

I'm no stranger to GRUB files, etc, so have no issues mucking about with GRUB and making sure it all works nicely, but, no matter how hard I try, Ubuntu has this built in desire to mess with both GRUB and the MBR of discs that it isn't even installed on :D

It's hillarious. I've heard so many quips from Linux fans about how XP is 'designed' to mess with your Linux install but here's my experience:

1. After a bit of mucking about with GRUB, I successfully get it to boot Puppy/XP and Ubuntu from boot. 
2. A little icon pops up in Ubuntu asking me to update the software, ah, I think, great, it'll be just like Windows update (how wrong I was :D)
3. Ubuntu updates... oh.. wait, what's this, on reboot it goes straight to Ubuntu.. where's GRUB gone?
4. ...actually... what the hell, it just removed Puppy too?
5. ...and the MBR of my second HDD with XP installed has been messed with too.. Oh no, I haven't backed up my email in Outlook and I have some important customer emails in there. Shi..
6. I know, I'll reinstall Ubuntu. 
7. *much mucking around with GRUB*
8. *some more mucking around with GRUB*
9. Ah, I know...
10. *reaches into PC case, unplugs Ubuntu primary HDD*

:D

Linux has a long, long, long way to go.

---

### Post by lavinog on 2007-12-08
when you do a kernel update...grub automatically updates itself based on the settings in the menu.lst file

what is the timeout setting in your menu.lst?

I wouldn't worry about your emails on your xp drive...they are still there.
if ubuntu boots up just fine then why don't you use it to backup your emails?

---

### Post by lswest on 2007-12-08
just change the settings in /boot/grub/menu.lst to what you need (e.g. XP entries and Puppy Linux entries, timeout, and default choice)

---

### Post by rsambuca on 2007-12-08
I am afraid you don't know as much about grub as you seem to think.  It will only install to places where the menu.lst and device map direct it to go.  If you have those set improperly, then you will have problems.  

Anyways, good luck.

---

### Post by eob on 2007-12-08
I used an old Knoppix boot CD to get in the last time and tweak my GRUB file til it worked, but hillariously, Ubuntu loves to muck with the MBR of my SECOND HDD which hasn't even got Ubuntu installed on it, to the point that it manages to set the Dell Diagnostics programmes on a hidden partition to boot by default :D Just when you expect to see Windows XP loading... It's a nice surprise :D

My XP install is fine, using it to post this, tell you what... I'll boot from CD using Puppy3 and cut & paste my menu.lst and give it one more shot. Already wasted a day on this :D

PS. Is it a given that you have to manually update menu.lst after every Ubuntu update?

---

### Post by rsambuca on 2007-12-08
> **eob said:**
> PS. Is it a given that you have to manually update menu.lst after every Ubuntu update?
Nope.  If the kernel is updated, then Ubuntu is set to automatically update grub as well.

---

### Post by eob on 2007-12-08
Ah... I don't mean to ask a question that might offend some, but... Is it designed to target other operating systems like Puppy and XP and remove them?

Here's my GRUB config, something about an error 17?

Please don't waste too much time on this people, I gave up after a wasted day of resorting to a Knoppix boot CD and /fixmbr in XP's Rescue CD to save my bacon. I'm presuming that, considering I can't update Ubuntu without it declaring Blitzkreig on my other OS's :(

It's a total shame because Ubuntu has come a long, long way since Red Hat but by golly there be tweaking to be done me-hearties, arr harr :)

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/red white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e636bcf5-5eb5-40ad-ac40-290c1e8f4857 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Windows XP 11
rootnoverify 	(hd1,1) 
makeactive
chainloader	+1

title		Windows XP 10
rootnoverify 	(hd1,0)
makeactive
chainloader	+1

title		Windows XP 12
rootnoverify 	(hd1,2)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other such bad *** operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Linux Puppy Woof Woof
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 ro vga=normal 
savedefault
boot



---

### Post by eob on 2007-12-08
PS. Just so you know, it's giving me a GRUB error of 17.

---

