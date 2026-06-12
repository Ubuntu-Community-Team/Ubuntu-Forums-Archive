---
title: "Ubuntu 14.04 Boot - plymouth-upstart-bridge Issue"
date: 2014-04-19
forum: Server Platforms
---

### Post by jasonvp on 2014-04-19
Hey folks -

I'm somewhat new to the Ubuntu world, but no stranger to Linux (using it since '92).  My newest install is the server version of 14.04, and upon booting, init spams this to the console:

```

[    5.456439] init: plymouth-upstart-bridge main process (387) terminated with status 1
[    5.457595] init: plymouth-upstart-bridge main process ended, respawning
[    5.460514] init: plymouth-upstart-bridge main process (398) terminated with status 1
[    5.461659] init: plymouth-upstart-bridge main process ended, respawning
.
. (deleted for brevity)
.
[    5.496967] init: plymouth-upstart-bridge respawning too fast, stopped

```

The following step is the kernel loading its swap space.  From there, it freezes.

My "sledgehammer" style fix for this was to remove /etc/init/plymouth-upstart-bridge.conf, which was likely the wrong thing to do.  But, the machine boots reliably every time now, and everything appears to be fine.  Prior to 14.04 server, I'd installed 13.10, and it booted reliably every time.

Any ideas or suggestions?  Should I just leave it as is?

Thanks.

---

### Post by Professor Frink on 2014-04-22
I get the same error on boot but mine boots just fine.  The error does bug me though.

---

### Post by jasonvp on 2014-04-22
> **Professor Frink said:**
> I get the same error on boot but mine boots just fine.  The error does bug me though.

As it turns out, my machine was booting just fine too.  There was another error happening that was confusing me: right after the swap space is enabled, the kernel seems to be kicking over to "graphical" mode.  My machine has an ATI card, and the kernel doesn't seem to like that.  No further boot messages appear on the console after that point but the machine does continue to boot.  I never actually see a login prompt on the console.

So the plymouth-upstart-bridge messages aren't consequential to the apparent console lock-up.

---

### Post by Greg_Vickers on 2014-04-23
Ha, I have this problem as well!  Let me know if you find out how to force the machine to boot to text mode.  I can SSH to my server just fine.

---

### Post by jasonvp on 2014-04-23
> **Greg_Vickers said:**
> Ha, I have this problem as well!  Let me know if you find out how to force the machine to boot to text mode.

It's in the /etc/defaults/grub file.

```

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

```

Uncommenting that line and re-running update-grub afterwards should do it.  Note: I haven't verified because I have yet to reboot my machine.  It's running too many important VMs and I can't take the down time right now.

---

### Post by Jon Hanna on 2014-04-25
Could you please not post illogical solutions involving editing config files for other parts of your system until after you've tried them first? It makes it look like this question has been answered.

---

### Post by Greg_Vickers on 2014-04-27
> **jasonvp said:**
> It's in the /etc/defaults/grub file.

```

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

```

Uncommenting that line and re-running update-grub afterwards should do it.  Note: I haven't verified because I have yet to reboot my machine.  It's running too many important VMs and I can't take the down time right now.I've tried this and the problem still exists.  I'm working around it by booting in rescue mode and going straight to "Resume boot" from the rescue menu.

---

### Post by MetaView on 2014-05-06
> **Greg_Vickers said:**
> I've tried this and the problem still exists.  I'm working around it by booting in rescue mode and going straight to "Resume boot" from the rescue menu.

We had something similar with NVIDIA gfx card and 13.04. It only happend from time to time. disabling plymouth and splash screen in grub:

in file /etc/defaults/grub
set line
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

and run update-grub afterwards.

This plymouth stuff is a pain and should be killed or fixed, just my 2cents.

---

### Post by jasonvp on 2014-05-06
> **MetaView said:**
> We had something similar with NVIDIA gfx card and 13.04. It only happend from time to time. disabling plymouth and splash screen in grub:

Thanks for the suggestion, but unfortunately it didn't work.  My Mac's console still froze up solid after the swap space was enabled.  The PC server sitting next to it did the same thing.  No joy. :-(

---

### Post by ciberwolf010191 on 2014-05-08
Thanks i have the same problem with plymouth... but with your reply can resolved...

---

### Post by jasonvp on 2014-05-09
Marking this as "solved" because it turns out my problem has nothing to do with plymouth.  See a follow-up thread I'm going to make.

---

### Post by MirkoCe on 2014-05-20
Did you guys solve? Because I am having the same issue.

---

### Post by humpty88 on 2014-06-27
> **MirkoCe said:**
> Did you guys solve? Because I am having the same issue.

It's not realy solved. I have it on a fresh install.
I do know it is not GRUB because I boot with EXTLINUX, and it's still there.

---

### Post by Harley_Rumbang on 2014-08-21
I solved it by following this
[http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/](http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/)

credits goes to the original poster.

---

### Post by jared-thomas on 2014-10-09
> **MetaView said:**
> We had something similar with NVIDIA gfx card and 13.04. It only happend from time to time. disabling plymouth and splash screen in grub:  in file /etc/defaults/grub set line GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"  and run update-grub afterwards.  This plymouth stuff is a pain and should be killed or fixed, just my 2cents.  I have been having similar issues with two different Ubuntu 14.04 systems with ATI graphics; crash reporter was popping up on every login. I don't think it was hurting anything, just annoying. Adding "noplymouth" to the default GRUB line definitely fixed the problem. Thanks for the heads-up!

---

### Post by WinEunuchs2Unix on 2014-11-09
> **jasonvp said:**
> Hey folks -

I'm somewhat new to the Ubuntu world, but no stranger to Linux (using it since '92).  My newest install is the server version of 14.04, and upon booting, init spams this to the console:

```

[    5.456439] init: plymouth-upstart-bridge main process (387) terminated with status 1
[    5.457595] init: plymouth-upstart-bridge main process ended, respawning
[    5.460514] init: plymouth-upstart-bridge main process (398) terminated with status 1
[    5.461659] init: plymouth-upstart-bridge main process ended, respawning
.
. (deleted for brevity)
.
[    5.496967] init: plymouth-upstart-bridge respawning too fast, stopped

```

The following step is the kernel loading its swap space.  From there, it freezes.

My "sledgehammer" style fix for this was to remove /etc/init/plymouth-upstart-bridge.conf, which was likely the wrong thing to do.  But, the machine boots reliably every time now, and everything appears to be fine.  Prior to 14.04 server, I'd installed 13.10, and it booted reliably every time.

Any ideas or suggestions?  Should I just leave it as is?

Thanks.

The kernel thinks plymouth is running to fast.  The solution is  using sleep 2 (as per another website) in  /etc/init/plymouth-upstart-bridge.conf:

```

# plymouth-upstart-bridge - Bridge Upstart state changes into Plymouth
#
# This helper process receives Upstart state changes over D-Bus and sends
# corresponding messages to Plymouth.
**# Nov 9, 2014 - Add sleep 2 to prevent respawning error msgs during boot.**

description    "bridge from Upstart state changes to Plymouth"

respawn

start on (startup
          or runlevel [06])
stop on (stopping plymouth
         or stopping plymouth-shutdown)         

console output

exec plymouth-upstart-bridge
**sleep 2**

```

Bold lines are inserts.  Testing on Ubuntu 14.04.1 and Kernel 3.17.1-generic shows it fixes the problem.

Earlier attempts to comment out swap mount in /etc/fstab only shifted the 8 second delay to the mounting of ext4 (root) in the next /var/log/syslog line after plymouth respawning messages.

Althougth solution gets rid of the nagging plymouth respawning messages it doesn't explain the 7 to 8 second delay in syslog messages:

```

Nov  9 12:02:57 Dell kernel: [    2.815625] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Nov  9 12:02:57 Dell kernel: [    3.418797] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 3.0 PMAP PQ: 0 ANSI: 6
Nov  9 12:02:57 Dell kernel: [    3.419035] sd 6:0:0:0: Attached scsi generic sg3 type 0
Nov  9 12:02:57 Dell kernel: [    3.419272] sd 6:0:0:0: [sdc] 122849280 512-byte logical blocks: (62.8 GB/58.5 GiB)
Nov  9 12:02:57 Dell kernel: [    3.419576] sd 6:0:0:0: [sdc] Write Protect is off
Nov  9 12:02:57 Dell kernel: [    3.419579] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 00
Nov  9 12:02:57 Dell kernel: [    3.419872] sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Nov  9 12:02:57 Dell kernel: [    3.792211]  sdc: sdc1 sdc2 sdc3
[B]Nov  9 12:02:57 Dell kernel: [    3.793675] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Nov  9 12:02:57 Dell kernel: [   12.080198] Adding 8243196k swap on /dev/sda6.  Priority:-1 extents:1 across:8243196k FS[/B]
Nov  9 12:02:57 Dell kernel: [   12.262062] systemd-udevd[477]: starting version 204
Nov  9 12:02:57 Dell kernel: [   12.704868] lp: driver loaded but no devices found
Nov  9 12:02:57 Dell kernel: [   12.709270] ppdev: user-space parallel port driver
Nov  9 12:02:57 Dell kernel: [   12.741688] wmi: Mapper loaded

```

Bold lines show the 8 second delay that used to have the Plymouth respawning error messages which are now gone thanks to "sleep 2" code.

EDIT 1 (NOV 10/2014):

The actual processes taking place during the blank 8 seconds are echoed to the boot screen in the form of:
/usr/share/initramfs/scripts/_____:
init-top
init-premount
local-top
loacl-premount
local-bottom
init-bottom

Some fine-tuning of mdadm, lvm or udev might shorten the boot time.

EDIT 2 (DEC 30/2014):

Posts on Dec 29th brought this forgotten thread back to my in-box.  Since Nov 10th EnhanceIO SSD caching of the HDD was elevated from mount time to pre-mount time by inserting into local-top scripts directory.

Subsequent tests reveal the 8 second delay question was not due to LVM or mdadm but rather mounting the file systems which doesn't give step by step reporting.

The SSD caching software moves relevant portions of the 250GB HDD into a super-fast 11 GB SSD cache. The other 19GB caches a Windows 256GB HDD partition for use by Windows 7 Ultimate booting and applications.

The "Sleep 2" code described above was commented out and rebooting now reveals.

[SIZE=5][FONT=arial black]At the 3 second mark:[/FONT][/SIZE]
```

Dec 30 18:31:43 Dell kernel: [    3.785390] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
Dec 30 18:31:43 Dell kernel: [    3.785393] usb 1-1.5: Manufacturer: CN00YCD67248732362B3A00
**Dec 30 18:31:43 Dell kernel: [    3.800018] enhanceio: Cache metadata loaded from disk with 1219220 valid 0 dirty blocks**
**Dec 30 18:31:43 Dell kernel: [    3.800217] enhanceio: Setting mode to write through **
**Dec 30 18:31:43 Dell kernel: [    4.037142] enhanceio_lru: Initialized 11440 sets in LRU**
Dec 30 18:31:43 Dell kernel: [    4.037145] Console: switching to colour frame buffer device 240x67
Dec 30 18:31:43 Dell kernel: [    4.040503] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Dec 30 18:31:43 Dell kernel: [    4.040661] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS

```

Loading enhanceio in ..scripts/local-top/ directory moves about 1 second of time from the formal 10 second mark (which is now gone) to the 3.800 second mark.

As an aside don't work about the webcam being loaded at the 3.785 mark because like all NSA-paranoid-laptops there is paper taped over top of the camera's CCD since 2007.

The Firmware bug at 4.040 second mark I just noticed for the first time which should be a nice time-consuming project.

[SIZE=5][FONT=arial black]At the 5 second mark:[/FONT][/SIZE]
```

Dec 30 18:31:43 Dell kernel: [    4.247590] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 00
Dec 30 18:31:43 Dell kernel: [    4.247896] sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Dec 30 18:31:43 Dell kernel: [    4.575845]  sdc: sdc1 sdc2 sdc3
**Dec 30 18:31:43 Dell kernel: [    4.577166] sd 6:0:0:0: [sdc] Attached SCSI removable disk**
**Dec 30 18:31:43 Dell kernel: [    5.046552] enhanceio: Cache creation failed: Cache already exists.**
**Dec 30 18:31:43 Dell kernel: [    5.062998] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)**
Dec 30 18:31:43 Dell kernel: [    5.619535] init: ureadahead main process (413) terminated with status 5
Dec 30 18:31:43 Dell kernel: [    5.903014] Adding 8243196k swap on /dev/sda6.  Priority:-1 extents:1 across:8243196k FS
Dec 30 18:31:43 Dell kernel: [    6.028033] systemd-udevd[527]: starting version 204
Dec 30 18:31:43 Dell kernel: [    6.329186] lp: driver loaded but no devices found

```

The old 8 second delay to mount the file system is now (5.062 - 4.577) or 0.485 or 1/2 second.  A wonderful time savings to fanatics spending hours reconfiguring and rebooting to save time booting :D

At the 5.046 second mark we see an error message that EnhanceIO cache is already created.  As a persistent (udev rule) linux tries to mount it with everything else.  So we now have one message during the boot's file system mount process.

[SIZE=5][FONT=arial black]At the 9 second mark:[/FONT][/SIZE]
```

Dec 30 18:31:45 Dell accounts-daemon[1378]: started daemon version 0.6.35
Dec 30 18:31:45 Dell dbus[1020]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec 30 18:31:45 Dell acpid: client connected from 1390[0:0]
Dec 30 18:31:45 Dell acpid: 1 client rule loaded
**Dec 30 18:31:45 Dell kernel: [    9.228286] init: plymouth-upstart-bridge main process ended, respawning**
**Dec 30 18:31:45 Dell kernel: [    9.232162] init: plymouth-upstart-bridge main process (1400) terminated with status 1**
**Dec 30 18:31:45 Dell kernel: [    9.232171] init: plymouth-upstart-bridge main process ended, respawning**
Dec 30 18:31:46 Dell NetworkManager[1123]: <info> (eth0): carrier now ON (device state 20)
Dec 30 18:31:46 Dell NetworkManager[1123]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 30 18:31:46 Dell kernel: [    9.913959] r8169 0000:03:00.0 eth0: link up
Dec 30 18:31:46 Dell kernel: [    9.913968] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 30 18:31:46 Dell NetworkManager[1123]: <info> Auto-activating connection 'Wired connection 1'.
Dec

```

Respawning messages are now coming when plymouth is pretty much ending.  There are fewer of them and do not appear to take up any time.  Leaving the "sleep 2" line out means there is no need to redo the code on future installs and one less configuration to document and worry about patching.

A poster on Dec 29/2014 is looking forward to systemd.  That sounds like fun.  Add to that disk caching in btrfs or native Intel Rapid Storage within mdadm / grub boot sound like fun too.  Some are bad mouthing plymouth but I think it's cool especially the earth-sunrise theme with Ubuntu logo.  Still need to hack it to get sunset on reboot.  Another project :D

Apologies in advance to those that fell asleep reading this or went bald scratching their heads :)

---

### Post by Angel_Suarez on 2014-12-29
Hi, i had the same problem but i'm not sure if this could help somebody else (i hope so).

I had tried all the solutions posted here and anothers forums, but nothing fix my problem

I saw the plymouth.conf file and it has this instruction: "start on starting mountall", so i checked my NTFS Disks.

I found that when ubuntu started, it tried to mount my NTFS Disk (i made the changes in fstab, because there, i have my web content, so this disk has to be mounted asap) but, it could not be able to be mounted becase there was some errors trying to mont this disk. 

Some days ago i had installed windows x on this one of my disk, Windows save some files that does HDD boot "faster", well, this files were that don't let ubuntu boot normally.

I run a "ntfsfix" on that disk, and now ubuntu works normally again!!

Regards.

---

### Post by MAFoElffen on 2014-12-29
I know got marked as solved, but wasn't. Then still people pursuing an answer... 

Package plymouth-disabler ([https://launchpad.net/ubuntu/trusty/+package/plymouth-disabler](https://launchpad.net/ubuntu/trusty/+package/plymouth-disabler)), that was a fix for bug#1235231 might be a better idea... I have many servers that have this problem, though they all run just fine. 

I'm going to try this fix for a test tonight. Thinking this will change again when upstart/init is fully replaced by systemd, but until then. I'll post back after that test.

---

### Post by elhoir_220582 on 2015-01-17
hi there,

im now using Ubuntu 14.10, and i have the <snip> plymouth-upstart-bridge ****

But, i have tested every thing you guys posted in this thread, and they do NOT work for me :/

i tested adding "sleep 2" at /etc/init/plymouth-upstart-bridge.conf. Didn´t work. At this point, i even tested commenting out "exec plymouth-upstart-bridge" in the same file, so i have serious doubts about this being a plymouth issue...

i tested adding acpi=off in the Linux kernel parameter line

i tested removing "quiet splash" from the same linux kernel parameter line

None worked for me, and now i can´t boot into Ubuntu.

Could anyone help me please?

thanks in advance!

---

### Post by sivitri on 2015-03-13
Hi,
For those who display text boot, you don't need plymouth (splash screen).
So just disable the start of plymouth-upstart-bridge.
To  do this, rename the file /etc/init/plymouth-upstart-bridge.conf to  /etc/init/plymouth-upstart-bridge.conf.original (for example).
I have no more plymouth-upstart-bridge messages during boot, and all is running fine !

---

### Post by hirameki on 2015-07-18
> **MetaView said:**
> We had something similar with NVIDIA gfx card and 13.04. It only happend from time to time. disabling plymouth and splash screen in grub:

in file /etc/defaults/grub
set line
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

and run update-grub afterwards.

This plymouth stuff is a pain and should be killed or fixed, just my 2cents.

I have same problem. 
your solution worked for me. Thank you.

---

### Post by WinEunuchs2Unix on 2015-07-18
> **sivitri said:**
> Hi,
For those who display text boot, you don't need plymouth (splash screen).
So just disable the start of plymouth-upstart-bridge.
To  do this, rename the file /etc/init/plymouth-upstart-bridge.conf to  /etc/init/plymouth-upstart-bridge.conf.original (for example).
I have no more plymouth-upstart-bridge messages during boot, and all is running fine !

Firstly apologies for typo in my last post (November 2014) I obviously meant my 2 ghz dual core Centrino was "too fast" not "to fast".

Also I agree with the Poster that Plymouth should be avoided by all Linux Neophytes. I avoided Plymouth for many months of my 1 year incarnation (whatever the right word is).

After figuring out much of dmesg and other jazz I ventured into Plymouth and learned how to make a sunrise at boot-up and sunset on shutdown / reboot.

I think it's cool but concur it's not for neophytes.

I don't want to preach that you should use Plymouth I'm only preaching you should ignore those who tell you to not learn.

---

### Post by tessk2 on 2015-07-23
Has this issue been solved? Sorry, I have read the entire thread twice now and i cannot figure out if someone in here has actually found a fix for this issue. I just installed a fresh copy of Ubuntu Server 14.04 on a machine and I am getting this same  error message. The thoughts about the system booting too fast sound plausible, since previous installs of this OS on the same machine never had this problem, until I just upgraded it with an SSD. 

Either way, the machine is basically unusable now due to this. Additionally, it is not clear to me how you all are going about editing these config files when the OS will not boot. Mine does not boot at all after hitting the plymouth snag.

EDIT: This worked. Had to load a LiveCD in order to edit the file.

> **MetaView said:**
> We had something similar with NVIDIA gfx card and 13.04. It only happend from time to time. disabling plymouth and splash screen in grub:

in file /etc/defaults/grub
set line
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

and run update-grub afterwards.

This plymouth stuff is a pain and should be killed or fixed, just my 2cents.

EDIT 2:
So it looks like this does not permanently fix the problem for me. As soon as I restart the computer, the error message comes back. If I start Ubuntu in recovery mode, I am able to boot. But as soon as I do a normal boot the issue comes back. Also it looks like the changes I make to /etc/default/grub as per the above solution are not being saved, even though I am editing the file as root and running update-grub afterwards

---

### Post by WinEunuchs2Unix on 2015-07-24
> **tessk2 said:**
> Has this issue been solved? Sorry, I have read the entire thread twice now and i cannot figure out if someone in here has actually found a fix for this issue. I just installed a fresh copy of Ubuntu Server 14.04 on a machine and I am getting this same  error message. The thoughts about the system booting too fast sound plausible, since previous installs of this OS on the same machine never had this problem, until I just upgraded it with an SSD. 

Either way, the machine is basically unusable now due to this. Additionally, it is not clear to me how you all are going about editing these config files when the OS will not boot. Mine does not boot at all after hitting the plymouth snag.

EDIT: This worked. Had to load a LiveCD in order to edit the file.



EDIT 2:
So it looks like this does not permanently fix the problem for me. As soon as I restart the computer, the error message comes back. If I start Ubuntu in recovery mode, I am able to boot. But as soon as I do a normal boot the issue comes back. Also it looks like the changes I make to /etc/default/grub as per the above solution are not being saved, even though I am editing the file as root and running update-grub afterwards

I quickly browsed the thread and quite frankly can't remember all the technical details at this time.

I'd like to point out that booting from a CD is SLOWWWWW so you would not encounter the "booting too fast issue from SSD".

I'm writing this from Windows 7 Ultimate so cannot verify if I'm still using a 2 second sleep on Plymouth. Caching the HDD to SDD with a LOT of tweaking resulted in a 7 second boot time instead of 45 and now I'd like to research if the 2 second sleep I posted earlier could be reduced to 1.5 seconds or less.

Another poster is correct in that the Plymouth care-takers should recode to have it wait in it's own cycle to spare us the trouble of "kiddy-scripting".

Still the rising sun on boot up and setting sun on shut down that Plymouth provides is cool.

Thought you deserved some kind of answer even though I didn't have the time today to research it thoroughly.

---

### Post by tessk2 on 2015-07-25
Thanks for the update.

I tried the sleep -2 command as listed before. It got my boot past plymouth, but it quickly hit another snag, and halted the boot with a urandom-init command mentioning something about bits of entropy. 

I also started unplugging system devices that I don't need and gave the SSD a dedicated power cable instead of using one that was also connected to the ODD and HDD, but neither made a difference beyond reducing the number of items listed on boot.

Right now I am trying to look through the syslog but honestly I don't know what I am looking for. Also, I am using a LiveUSB to access the logs, still haven't figured out how you are supposed to access the drive contents if its not booting, are you guys all using the recovery console? It seemed to have trouble writing to root protected files when I used it.

Also this machine is going to be running on the command line only, no GUI, so I am not sure that I even need Plymouth at all. I honestly dont understand what its supposed to do anyway, maybe because I never actually use vanilla Ubuntu, only Xubuntu. I've never seen this sunrise/sunset thing you are talking about.. But, with these errors, I am not sure that plymouth is the true culprit or if the problems are a symptom of something else

EDIT: it appears that if I boot into Recovery mode, then Resume normal boot, I can get it to go to the full login screen. It looks like some graphics drivers are not loaded though because the screen resolution is much lower.

EDIT2: Tried installing Xubuntu 14.04, it boots without a single problem. So whatever is causing the issue is present in Ubuntu server 14.04 but not in Xubuntu 14.04. I wanted this machine to be command line only, since I already have a personal desktop. Oh well I might end up sticking with this.

---

### Post by WinEunuchs2Unix on 2015-07-26
> **tessk2 said:**
> Thanks for the update.

I tried the sleep -2 command as listed before. It got my boot past plymouth, but it quickly hit another snag, and halted the boot with a urandom-init command mentioning something about bits of entropy. 

I also started unplugging system devices that I don't need and gave the SSD a dedicated power cable instead of using one that was also connected to the ODD and HDD, but neither made a difference beyond reducing the number of items listed on boot.

Right now I am trying to look through the syslog but honestly I don't know what I am looking for. Also, I am using a LiveUSB to access the logs, still haven't figured out how you are supposed to access the drive contents if its not booting, are you guys all using the recovery console? It seemed to have trouble writing to root protected files when I used it.

Also this machine is going to be running on the command line only, no GUI, so I am not sure that I even need Plymouth at all. I honestly dont understand what its supposed to do anyway, maybe because I never actually use vanilla Ubuntu, only Xubuntu. I've never seen this sunrise/sunset thing you are talking about.. But, with these errors, I am not sure that plymouth is the true culprit or if the problems are a symptom of something else

EDIT: it appears that if I boot into Recovery mode, then Resume normal boot, I can get it to go to the full login screen. It looks like some graphics drivers are not loaded though because the screen resolution is much lower.

EDIT2: Tried installing Xubuntu 14.04, it boots without a single problem. So whatever is causing the issue is present in Ubuntu server 14.04 but not in Xubuntu 14.04. I wanted this machine to be command line only, since I already have a personal desktop. Oh well I might end up sticking with this.

Entropy is used to encrypt data and random bits are stored in /dev/random and /dev/urandom amongst other places. The random bits are needed to create a GPG key and perhaps for encrypting data volumes (ie /home, etc.)

Are you even using file encryption though???

There were bugs with SSD and Kernel versions in May/June 2015 that led to data corruption. It had something to do with the TRIM functions of the SSD and the DISCARD option within Linux. The Kernel version numbers were 4.0.1 through 4.0.4. Mainstream Kernel versions simultaneously maintained in 3.14.xx, 3.18.xx, 3.19.xx, etc would also suffer this data corruption I presume. Check if the file /etc/fstab has the discard option used. If discard is used and your kernel version is a buggy one then remove the discard option.

I've only used the recovery console once or twice and frankly not too familiar with the console at all. In recovery console mode graphics would default to "plain vanilla" and high DPI (dots per inch) screens could look extremely tiny or might revert to old VGA 640 x 480 which could be "big and blocky". Not to sure on this one.

Plymouth is a tool to load graphics early in the boot process before Ubuntu desktop if up and running. For standard Ubutntu you get like a purple screen with a strange looking icon in the middle. The Sunrise / Sunset are optional graphic files you can download from the net to jazz up the screen. There are people offering many different graphic files.

A final suggestion. Since this is no longer a Plymouth problem, create a new thread about the boot problem with Entropy.

---

### Post by tessk2 on 2015-07-27
> **WinEunuchs2Unix said:**
> Entropy is used to encrypt data and random bits are stored in /dev/random and /dev/urandom amongst other places. The random bits are needed to create a GPG key and perhaps for encrypting data volumes (ie /home, etc.)

Are you even using file encryption though???

There were bugs with SSD and Kernel versions in May/June 2015 that led to data corruption. It had something to do with the TRIM functions of the SSD and the DISCARD option within Linux. The Kernel version numbers were 4.0.1 through 4.0.4. Mainstream Kernel versions simultaneously maintained in 3.14.xx, 3.18.xx, 3.19.xx, etc would also suffer this data corruption I presume. Check if the file /etc/fstab has the discard option used. If discard is used and your kernel version is a buggy one then remove the discard option.

I've only used the recovery console once or twice and frankly not too familiar with the console at all. In recovery console mode graphics would default to "plain vanilla" and high DPI (dots per inch) screens could look extremely tiny or might revert to old VGA 640 x 480 which could be "big and blocky". Not to sure on this one.

Plymouth is a tool to load graphics early in the boot process before Ubuntu desktop if up and running. For standard Ubutntu you get like a purple screen with a strange looking icon in the middle. The Sunrise / Sunset are optional graphic files you can download from the net to jazz up the screen. There are people offering many different graphic files.

A final suggestion. Since this is no longer a Plymouth problem, create a new thread about the boot problem with Entropy.


Very interesting. I am indeed using the Discard option on my SSD. I have two partitions on it, a 40GB / partition and a 400GB /home partition. There's also a 1TB /opt partition on the HDD. The SSD partitions are set up with Discard, Noatime, and Nodiratime. It was my understanding that with SSD's, Discard is important for drive health, as per [this]("http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/") old article (maybe this is out of date?). I use these same settings without issue on my 'recreational' desktop PC, which is also running Xubuntu 14,04 with an SSD, and uses kernel version 3.13.0-58-generic. I no longer have Ubuntu server installed on the PC that was giving me the Plymouth / urandom issues, its now running Xubuntu 14.04 as well, though it has kernel version 3.16.0-44-generic, and I just tested it with the noatime, nodiratime, and discard settings in /etc/fstab and it seems to have no issues booting. I do not remember what kernel version was being used when I installed Ubuntu server, and since the machine in question is working fine with Xubuntu, I am hesitant to 'break' it again to find out :/

I am not using any file encryption on either PC. Though I do have a password set for my user account, maybe that could initiating the urandom process? 

I agree with your suggestion about making a new thread. Since the machine is currently working under the listed settings & kernel version in Xubuntu, I may not pursue it further, but if I need to I will make a new thread for it. Thanks a lot for the help and valuable information.

---

### Post by WinEunuchs2Unix on 2015-07-28
> **tessk2 said:**
> Very interesting. I am indeed using the Discard option on my SSD. I have two partitions on it, a 40GB / partition and a 400GB /home partition. There's also a 1TB /opt partition on the HDD. The SSD partitions are set up with Discard, Noatime, and Nodiratime. It was my understanding that with SSD's, Discard is important for drive health, as per [this]("http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/") old article (maybe this is out of date?). I use these same settings without issue on my 'recreational' desktop PC, which is also running Xubuntu 14,04 with an SSD, and uses kernel version 3.13.0-58-generic. I no longer have Ubuntu server installed on the PC that was giving me the Plymouth / urandom issues, its now running Xubuntu 14.04 as well, though it has kernel version 3.16.0-44-generic, and I just tested it with the noatime, nodiratime, and discard settings in /etc/fstab and it seems to have no issues booting. I do not remember what kernel version was being used when I installed Ubuntu server, and since the machine in question is working fine with Xubuntu, I am hesitant to 'break' it again to find out :/

I am not using any file encryption on either PC. Though I do have a password set for my user account, maybe that could initiating the urandom process? 

I agree with your suggestion about making a new thread. Since the machine is currently working under the listed settings & kernel version in Xubuntu, I may not pursue it further, but if I need to I will make a new thread for it. Thanks a lot for the help and valuable information.

Keep in mind the bug is with the Operating System (Linux) and not the Application (Ubuntu / Lubuntu / Xubuntu / Arch / Mint , etc. etc.). The application needs the operating system to work. I guess by extension the operating system needs a computer chip and ram to work.

By simply taking the discard option out of /etc/fstab you can quickly check if you are effected by the bug. It is detailed at: [https://lkml.org/lkml/2015/5/21/102](https://lkml.org/lkml/2015/5/21/102)

It's not the link I researched a couple of months ago but the bug fixer's name (Neil) is in this thread too.

As far as passwords are concerned they probably aren't encrypted using Entropy but I can't confirm this. Just a hunch...

I agree with hesitation to "break" things. Simply type out the version of Linux (the operating system) you are running with the command:

[COLOR=#333333][FONT=Arial]uname -r[/FONT][/COLOR] 

and see if that has the SSD data corruption bug. While you're at it there could be a host of other bugs that might effect your SSD.

FTR my SSD is a "stock" 32 GB mSata PCI that is simply used to cache data from the "stock" 500 GB hard drive so it could die tomorrow and not effect things (they would just be a little slower until I bought a new one).

HTH

---

### Post by lx3r on 2015-09-02
workaround for the impatient:  ctrl-alt-del  sends the TERM signal, which seems to be exactly what this stupid program was waiting for.

---

### Post by WinEunuchs2Unix on 2015-09-02
> **lx3r said:**
> workaround for the impatient:  ctrl-alt-del  sends the TERM signal, which seems to be exactly what this stupid program was waiting for.

Spooky timing with your post because last night I was reading Linux-Lite:

[http://news.softpedia.com/news/linux-lite-2-6-is-out-with-firefox-40-0-3-and-libreoffice-5-0-1-based-on-ubuntu-14-04-3-lts-490564.shtml](http://news.softpedia.com/news/linux-lite-2-6-is-out-with-firefox-40-0-3-and-libreoffice-5-0-1-based-on-ubuntu-14-04-3-lts-490564.shtml)

 would use Ctrl+Alt+Del to bring up the system shut-down / reboot prompt.

When googling to find the link tonight I saw a reference that Ubuntu used to use Ctrl+Alt+Del a long time ago for the same thing.

Anyway sorry I didn't have time to explore a real solution for you.

---

### Post by dominic-timedicer on 2015-09-18
The advice above to disable plymouth by editing a file contained a typo ('defaults' not 'default'), it should read:

in file **/etc/default/grub** set line
```
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```

If there is already such a line in /etc/default/grub, just add the noplymouth parameter e.g.:
```
GRUB_CMDLINE_LINUX_DEFAULT="zswap.enabled=1 noplymouth"
```

---

### Post by jojo9 on 2015-10-16
Hi,

Just my tip (and note for myself) for blank screen and plymout respawning message.
I always finish with a blank screen when the kernel or/and the nvidia drivers updates.

1 - Boot on recovery console and directly resuming lead me to a working desktop with default graphical driver.
2 - using synaptic, I reinstall the nvidia driver (not cuda and other related packages) and reboot.
3 - if it does not work better, I reinstall the least version of the kernel.

Maybe someone who understands better the system could tell if doing 3rd step before the 2nd is better.

---

