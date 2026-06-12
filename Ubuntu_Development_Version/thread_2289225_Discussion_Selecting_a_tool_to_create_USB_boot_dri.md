---
title: "Discussion: Selecting a tool to create USB boot drives from ISO files"
date: 2015-08-02
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-08-02
[SIZE=4]I suggest that we discuss tools to create USB boot drives from ISO files.[/SIZE]

***General questions***

- What should the tool do? And what can be skipped?
. is a convenient tool OK, if it does not offer persistence?
. how important is it that the tool can download iso files?

- What should it look like?
. graphics mode ...
. text mode ...

- How to balance convenience and safety?

- Where is the limit for bugs?
. how patient can we be with the Startup Disk Creator (particularly usb-creator-gtk, I think usb-creator-kde is better)?

- Does it work in UEFI?

- Simple tools, that should be recommended to beginners. I think we should ask Canonical to replace the Startup Disk Creator.

- Advanced or specialized tools and methods, that should be recommended to experienced users.


***Specific tools***

- What about the tools mentioned at the official Ubuntu web page
[create-a-usb-stick-on-ubuntu: Startup Disk Creator](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
[create-a-usb-stick-on-windows: Pendrivelinux](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
[create-a-usb-stick-on-mac-osx: cli method](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

- What about Disks and mkusb - that copy/clone/flash content without modifications?

- What about the Startup Disk Creator?

- What about Unetbootin?

- What other tools should be mentioned?

***Tools to be run in Windows***

***Tools to be run in Mac***

***Links***

The discussion started [here](http://ubuntuforums.org/showthread.php?t=2288582&p=13329585#post13329585) and continued [there](http://ubuntuforums.org/showthread.php?t=1958073&page=5&p=13330002#post13330002).

See also the following link [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by dino99 on 2015-08-02
what i'm using smoothly: "multisystem" from "liveusb.info"
it can load most of all iso around

all the other tools are painfull or not usable

---

### Post by sudodus on 2015-08-02
> **dino99 said:**
> what i'm using smoothly: "multisystem" from "liveusb.info"
it can load most of all iso around

all the other tools are painfull or not usable

I tried multisystem some years ago. And it worked for me too. Does the current version work in UEFI mode?

---

### Post by dino99 on 2015-08-02
> **sudodus said:**
> I tried multisystem some years ago. And it worked for me too. Does the current version work in UEFI mode?

i cant test that myself; i suppose there is a changelog available (not checked, but it has been upgraded recently)

Explanations for using with uefi
[http://doc.ubuntu-fr.org/multisystem](http://doc.ubuntu-fr.org/multisystem)

It is possible to use Multisystem for a UEFI system. But if you prepare your key on a host system 1) UEFI, you can only start your UEFI key. By cons, if your host system is legacy 2) you can boot into both UEFI and legacy.

---

### Post by oldfred on 2015-08-02
I now have many flash drives booting various versions.
I did start before any of the scripts were available and had learned grub2, so have exclusively used grub2.

But I think it need to be what purpose the flash drive for. 
With flash drives now inexpensive, it is possible to have several. And size of flash drive also tends to make it better for some uses than others. Using a 64GB as just one ISO installer is a waste. But putting a full install in 8GB is tight but doable. Full Ubuntu vs. other lighter weight flavors may make smaller flash better. USB3 may work better for full install where USB2 is fine for installer or lightweight flavors.

I have one as a pure installer, one with many ISO for installs, one as a repair with mostly Linux ISO that can be used for repairs. I managed to also create a Windows/Linux repair system, but could not get Windows repair ISO to install directly from Ubuntu. I had to create CD, use CD to create Windows repair flash drive. But it only used 2 or 300MB on 4GB  flash drive. So I installed grub, added partitions and got it to boot Windows & the ISO. 
I do not have any with persistence as I either have full installs and larger data partitions or just pure install or repair flash drives.

So what intent or use does a user want. And with all the variety of needs it can get a bit complicated. 

Also then UEFI/BIOS make it a bit more complex now also. I have just kept a couple of flash drives as BIOS to boot my laptop and newer one's as UEFI to boot new desktop. But Ubuntu installer in FAT32 uses syslinux for BIOS & grub2 for UEFI, so it can boot either way.

And if you only want UEFI, you can just use any extraction tool to put ISO on FAT32 partition with boot flag. The FAT32 with boot flag will be seen as the ESP - efi boot partition and the efi boot files will be found. No actual install required.

---

### Post by sudodus on 2015-08-02
I think we are doing similar things Oldfred.

> But I think it need to be what purpose the flash drive for. 

And I think our discussion should consider that too:

- simple tools, that should be recommended to beginners. I think we should ask Canonical to replace the Startup Disk Creator.

- advanced or specialized tools and methods, that should be recommended to experienced users.

---

### Post by Chazall1 on 2015-08-02
Unetbootin works very good. Been using it for years.

---

### Post by cariboo on 2015-08-02
I use Disks->Restore Disk Image

---

### Post by sudodus on 2015-08-02
@  Chazall1:

Which version of Unetbootin are you using? From the Ubuntu repositories, or from the developer's PPA or a version installed from a downloaded deb file?

My experience is that the current version from the developer's PPA is a good alternative. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin).

---

### Post by sudodus on 2015-08-02
> **cariboo said:**
> I use Disks->Restore Disk Image

***Disks*** is simple and reliable, but the dialogue is not intuitive for a beginner. The disk image in the ISO file is new, so it is funny to say 'restore'. I would rather say 'install' or 'clone', 'copy' or 'flash'. I think ***Disks*** would be a good replacement of the Startup Disk Creator with an improved dialogue for this purpose - like what I'm trying to do with ***mkusb***.

---

### Post by kansasnoob on 2015-08-02
> **Chazall1 said:**
> Unetbootin works very good. Been using it for years.

+1!

The UI could use some polishing though. If using a downloaded iso the path_to_iso UI is rather confusing for a noob, and maximum free space for live persistence is not automatically calculated. Other than that it's pretty darn great!

---

### Post by kansasnoob on 2015-08-02
Both persistence and the ability for amd64 iso's to boot in either BIOS or UEFI mode are must haves.

Aside from SDC being badly borked one of the most annoying design flaws has always been the 10 minute timeout for installing the bootloader. I'm sure I'm not the only one that multi-tasks constantly, and not just at the desk. Watching and waiting for SDC to ask if you want to install the bootloader is about like watching paint dry ............... but if you get distracted for more than 10 minutes after SDC asks about bootloader installation you have to start all over again :mad:

---

### Post by ventrical on 2015-08-02
> **kansasnoob said:**
> Both persistence and the ability for amd64 iso's to boot in either BIOS or UEFI mode are must haves.

Aside from SDC being badly borked one of the most annoying design flaws has always been the 10 minute timeout for installing the bootloader. I'm sure I'm not the only one that multi-tasks constantly, and not just at the desk. Watching and waiting for SDC to ask if you want to install the bootloader is about like watching paint dry ............... but if you get distracted for more than 10 minutes after SDC asks about bootloader installation you have to start all over again :mad:

Yep. You got to be right there at the terminal to push it along as soon as that windows pops up. Ya know .. I haven't tried it in a while. I am going to try in in wily Unity desktop.

edit:

Complete fail. It actually rendered my Nextech 8GB USB dongle undetectable in either trusty or wily on various machines. However .. mkusb was able to detect and copy image to it.

---

### Post by ventrical on 2015-08-02
> **cariboo said:**
> I use Disks->Restore Disk Image

Easiest, fastest way with no fails. Even with wily.

---

### Post by sudodus on 2015-08-03
> **ventrical said:**
> [QUOTE=cariboo;13331878]I use Disks->Restore Disk Image

Easiest, fastest way with no fails. Even with wily.[/QUOTE]

But no persistence can be stored in the target device (at least I don't know how to get it.) How important is it to be able to create persistence by  the standard tool?

---

### Post by sudodus on 2015-08-03
> **kansasnoob said:**
> Both persistence and the ability for amd64 iso's to boot in either BIOS or UEFI mode are must haves.


I think there are different opinions about the ability to create persistence - ***@ everybody:*** please tell us what you think :-)

I think we all agree about the ability for amd64 iso's to boot in either BIOS or UEFI mode.
> 
Aside from SDC being badly borked one of the most annoying design flaws has always been the 10 minute timeout for installing the bootloader. I'm sure I'm not the only one that multi-tasks constantly, and not just at the desk. Watching and waiting for SDC to ask if you want to install the bootloader is about like watching paint dry ............... but if you get distracted for more than 10 minutes after SDC asks about bootloader installation you have to start all over again :mad:

I didn't know about this design flaw - either I haven't been distracted for more than 10 minutes - or maybe I have, but not understood what happened :-P

---

### Post by ventrical on 2015-08-03
> **sudodus said:**
> But no persistence can be stored in the target device (at least I don't know how to get it.) How important is it to be able to create persistence by  the standard tool?

What I do is remove all hdds and then use a 16GB usb drive as the target drive. I used to be able to use SDC for this in earlier version of ubuntu. I would make install  USB , say , of maveric meerkat and then install it to USB drive. (It treated the USB drive as if it were a hard drive). and voila' I am still running the same USB drives of Lucid Linyx 10.04  bootable on almost any machine. This drives are almost 5 years old. Thats not bad for persistence don't you think? As far as using the 'persistive' drive technique that was offered by SDC (even in early days) it was always much slower that with the method I used.

Btw .. I did my experiment with 15.10 ubuntu-desktop and SDC is a complete fail. Will now try with trusty on another machine.

Regards..

---

### Post by ventrical on 2015-08-03
After assuming SDC destroyed my Nextech USB flash I tried it on another stable machine - rebooted .. etc.. but would not detect USB. I loaded mkusb and voila'....Now it is detected on other machines.

---

### Post by ventrical on 2015-08-03
SDC is behaving like malware, It is a security hazard and needs to be seriously adressed.

Regards..

---

### Post by sudodus on 2015-08-03
@ ventrical: So you skip 'persistent live' and make an 'installed system' if you want persistence on a USB pendrive.

1. clone the iso file to the first pendrive
2. boot from the first pendrive
3. run the standard installer (ubiquity) and make an 'installed system' in the second pendrive
4. install the bootloader to the head of the second pendrive (either by removing all other drives or by using 'Something else')
5. add the mount option noatime to /etc/fstab to avoid excessive wear

It makes a good system, but is definitely more complicated than to create a persistent live system with for example Unetbootin.

-o-

@ everybody: Debian is recommending the naked cloning method without any safety belt, See [https://www.debian.org/CD/faq/#write-usb](https://www.debian.org/CD/faq/#write-usb).
> "cp":
```
cp <file> <device>
```
or "dd":
```
dd if=<file> of=<device> bs=4M; sync
```

I got that page in Swedish, so I translated to <file> and <device>. Simple is beautiful, but I would recommend a tool with a safety belt ;-)

Debian is recommending ***Win32 Disk Imager*** to clone from Windows. I agree, I even made a [tutorial](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) for it.

---

### Post by Beren Camlost on 2015-08-03
I've never been able to boot off a USB drive created with ***Startup Disk Creator***, ever. It may or may not be the fault of ***Startup Disk Creator*** itself, but I never had any luck with it.

Then I tried ***mkusb*** and has worked every time so far.

---

### Post by mc4man on 2015-08-03
s-d-c can either work or fails in so many different ways or reasons that it seems impossible to maintain & should be redone or abandoned.
As far as unetbootin the Debian/Ubuntu packages are seriously outdated & contain a real flaw that can cause users issues if not careful
(the .iso file browser has both root permissions & DnD capabilities

The above issue was finally fixed but not in any version except from the ppa build. (bug wasn't addressed until I filed a new one requesting unetbootin be removed from repo, that caught the dev's attention

However the new ppa builds don't recommend  gksu, users will get a pop suggesting 'sudo /usr/bin/unetbootin' or 'su --c '/usr/bin/unetbootin', not sure if that's a good idea or not. 
(may be fine..?, note it will use gksu if gksu is installed

---

### Post by sudodus on 2015-08-03
> **mc4man said:**
> s-d-c can either work or fails in so many different ways or reasons that it seems impossible to maintain & should be redone or abandoned.
As far as unetbootin the Debian/Ubuntu packages are seriously outdated & contain a real flaw that can cause users issues if not careful
(the .iso file browser has both root permissions & DnD capabilities

The above issue was finally fixed but not in any version except from the ppa build. (bug wasn't addressed until I filed a new one requesting unetbootin be removed from repo, that caught the dev's attention

However the new ppa builds don't recommend  gksu, users will get a pop suggesting 'sudo /usr/bin/unetbootin' or 'su --c '/usr/bin/unetbootin', not sure if that's a good idea or not. 
(may be fine..?, note it will use gksu if gksu is installed

Interesting details :-)

Please also tell us what tool you use, and what you would suggest as a replacement of the s-d-c (unless it is redone)!

---

### Post by mc4man on 2015-08-03
> **sudodus said:**
> Interesting details :-)

Please also tell us what tool you use, and what you would suggest as a replacement of the s-d-c (unless it is redone)!
I use unetbootin, typically I'll format the usb before using as it's became a habit with s-d-c-'s off/on issue with formatting.
For the latest ppa builds I do install gksu as it also has some value with gdebi.

I haven't tried the ppa version without root, you get the warning but then it does open.
For some you'd need to be very careful with unetbootin, ex. here
Currently running Ubuntu from a usb3 ssd, unetbootin defaults to picking that usb drive to install to, not the usb flash drive. In contrast s-d-c usually never even offers that drive, when it does it's red marked. 

s-d-c worked ok here on 14.04.1 but fails now on installing bootloader with 14.04.2/3. s-d-c does currently work in 15.10 (trying to create  14.04.3 image

---

### Post by sudodus on 2015-08-03
Thanks for those details, mc4man,

What do you think of tools that are reliable, but do not offer persistence, for example Disks and mkusb?

And what about the 'grub-n-iso' method: booting via grub2 and the iso file (stored as a file on the pendrive)? The grub-n-iso method can manage persistence, and works in both BIOS and UEFI.

---

### Post by ventrical on 2015-08-03
> **sudodus said:**
> @ ventrical: So you skip 'persistent live' and make an 'installed system' if you want persistence on a USB pendrive.

1. clone the iso file to the first pendrive
2. boot from the first pendrive
3. run the standard installer (ubiquity) and make an 'installed system' in the second pendrive
4. install the bootloader to the head of the second pendrive (either by removing all other drives or by using 'Something else')
5. add the mount option noatime to /etc/fstab to avoid excessive wear

It makes a good system, but is definitely more complicated than to create a persistent live system with for example Unetbootin.

-o-

@ everybody: Debian is recommending the naked cloning method without any safety belt, See [https://www.debian.org/CD/faq/#write-usb](https://www.debian.org/CD/faq/#write-usb).


I got that page in Swedish, so I translated to <file> and <device>. Simple is beautiful, but I would recommend a tool with a safety belt ;-)

Debian is recommending ***Win32 Disk Imager*** to clone from Windows. I agree, I even made a [tutorial]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") for it.


 I do not use (or need ) step 4. and 5.  Ubiquity just installs it flawlessly. Some choose not to remove hdd. It is not complicated for me. I  have 10 working towers on physical kvm hardware and an abundance of SATA hdds and flash drive. It may not work for everyone.

Regards..

> **mc4man said:**
> s-d-c can either work or fails in so many different ways or reasons that it seems impossible to maintain & should be redone or abandoned.
As far as unetbootin the Debian/Ubuntu packages are seriously outdated & contain a real flaw that can cause users issues if not careful
(the .iso file browser has both root permissions & DnD capabilities

The above issue was finally fixed but not in any version except from the ppa build. (bug wasn't addressed until I filed a new one requesting unetbootin be removed from repo, that caught the dev's attention


How do we catch the devs attention about SDC.? I can use it in maveric meerkat but thats about it. (yes I still have a frozen chosen 10.10 install that runs SDC just fine.)

Regards..

Creation of successful persistent xubuntu 15.04.iso using SDC from ubuntu MM 10.10

> **ventrical said:**
> Creation of successful persistent xubuntu 15.04.iso using SDC from ubuntu MM 10.10

So it works fine in 10.10. Maybe the devs need to backstep?

edit:  and boots awesomely in both UEFI and BIOS.

Regards..

---

### Post by mc4man on 2015-08-03
> **sudodus said:**
> Thanks for those details, mc4man,

What do you think of tools that are reliable, but do not offer persistence, for example  mkusb?

Well in this set up either mkusb can't work or i'm missing something. It goes into a loop > select image - can't find target device, > select
target device > action on image (install) > can't find target device
terminal reports - 
Booted from: /dev/sdd
/dev/sdc is busy; in fstab
/dev/sdd is busy; in fstab

sdc (sdc1) is the flash device, not busy, not in fstab...

---

### Post by C.S.Cameron on 2015-08-03
I used **MultiBootUSB** to make a grub2 iso booting flash drive five years ago.
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
I occasionally update the various iso's and edit grub.cfg on this drive by hand.
It is only a 4GB drive so a casper-rw file is sufficient. 
For a larger drive I would probably use casper-rw and home-rw partitions.
I now only run the Ubuntu iso as persistent.
Sharing the persistence file with other 'buntu iso's does not go smoothly.
It is also best to use a fresh casper-rw file/partition when upgrading.
A home-rw file/partition can be recycled.
I had puppy on the drive and it's version of persistence worked ok.
I recall once having Fedora working persistently on this drive also.
To make a 'buntu based O/S persistent using grub2, you just need to add " persistent" to grub.cfg.

---

### Post by VinDSL on 2015-08-03
> **sudodus said:**
> And I think our discussion should consider that too:

- simple tools, that should be recommended to beginners. I think we should ask Canonical to replace the Startup Disk Creator.

We're using the [mintStick]("https://github.com/linuxmint/mintstick") twins in Peppermint 6 - doesn't get any simpler than that...  ;)

---

### Post by sudodus on 2015-08-04
> **mc4man said:**
> Well in this set up either mkusb can't work or i'm missing something. It goes into a loop > select image - can't find target device, > select
target device > action on image (install) > can't find target device
terminal reports - 
Booted from: /dev/sdd
/dev/sdc is busy; in fstab
/dev/sdd is busy; in fstab

sdc (sdc1) is the flash device, not busy, not in fstab...

Probably you have found a bug. mkusb should display the hotkey **q** (quit) instead of a digit, when a partition on the device is mounted and not possible to unmount. But please double-check: that the device is not busy - some program might occupy it somehow, for example a terminal window!

My attached screenshot shows a case with three busy internal drives and one busy pendrive /dev/sdd (locked by a terminal window that has its current directory on /dev/sdd1 mounted at **/mnt**). In this case only the second pendrive /dev/sde is available as a target (hotkey **5**).

I want to debug your problem. Please tell me which operating system and version you run! There might be a variation of the output of the tool that works behind the curtain of the zenity window. Or maybe I have already fixed the bug in mkusb version 9.2.3 that is available via the unstable PPA.

```
sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install mkusb
```

-o-

I suggest that we discuss the further debugging in this thread: [Howto make USB boot drives](http://ubuntuforums.org/showthread.php?t=1958073)

***Edit:*** I noticed that you seem to be testing Ubuntu 14.04.3 LTS - so I tested mkusb 9.2.3 in Lubuntu 14.04.3 LTS, and it works for me. See screenshot #2.

---

### Post by mc4man on 2015-08-04
tried mkusb on a 14.04.3 install I have - works great. 
(- the issue on my 14.04 install must be local, the thumb drive is always seen as busy by mkusb so 99% sure it's not an mkusb issue, the install is old & quite experimented on. 
The only thing I find odd with mkusb is the 'root' owned "selected" file created & left in Home dir. I can rename, delete, ect. so don't get the reported permissions.

---

### Post by sudodus on 2015-08-04
I save the file **selected** locally, so if you have iso files or (other) compressed image files in several directories, you can start mkusb locally and save the selection for each particular directory.

Examples:

```
cd ~/Downloads/trusty
sudo -H mkusb

cd ~/Downloads/wily
sudo -H mkusb
```

will use different local files (selected). But you are used to the command line and might prefer

```
sudo -H mkusb trusty-desktop-i386.iso 
```

which is faster because it skips some windows, or even

```
sudo mkusb-nox trusty-desktop-i386.iso 
```

with the muscles, but without bells and whistles.

-o-

I do not quite understand: Do you suggest that I change the permissions to write for 'everybody' of that file, or is it OK as it is?

---

### Post by VMC on 2015-08-04
> **mc4man said:**
> Well in this set up either mkusb can't work or i'm missing something. It goes into a loop > select image - can't find target device, > select
target device > action on image (install) > can't find target device
terminal reports - 
Booted from: /dev/sdd
/dev/sdc is busy; in fstab
/dev/sdd is busy; in fstab

sdc (sdc1) is the flash device, not busy, not in fstab...

That "Scan_Cruzer" , is it the u3 variety?
 I just spent the better part of the day with my u3 until I realized, 
It's only worth is the use u3_tools and remove the protected partition and then use it solely as a storage device.

---

### Post by sudodus on 2015-08-04
@ VMC,

Interesting question about U3. I bought one of those pendrives some years ago. mkusb can see it. See the attached files.

-o-

Please tell us what tool do you prefer for creating USB boot drives, and why :-)

---

### Post by VMC on 2015-08-04
I don't create usb flash boot drives all that much. I use loop from grub to install my ubuntu os's. Since ubuntu iso are now all hybrid, I 'dd' them to usb flash. Also grub4dos works quite well as a multi-boot, but the contiguous file errors can be a pain to work out. Also, when I feel adventurous, I will create one using syslinux.

---

### Post by mc4man on 2015-08-04
> **VMC said:**
> That "Scan_Cruzer" , is it the u3 variety?
 I just spent the better part of the day with my u3 until I realized, 
It's only worth is the use u3_tools and remove the protected partition and then use it solely as a storage device.
Nah, that one (now)  is just a run of the mill usb2 cruzer, definitely something I've done to this install which I'll dump at some point. Then i'll try again as this install will be the 14.04.1 image.
(if it came with any of the Sandisk U3 stuff it's long gone...

---

### Post by mc4man on 2015-08-04
> **sudodus said:**
> 
-o-

I do not quite understand: Do you suggest that I change the permissions to write for 'everybody' of that file, or is it OK as it is?
Forget what I said -  I 'forgot' that it's normal to be able to do anything to a root owned file in $HOME except, in this case, edit the file.. which there is no need to.

From here (my other installs) mkusb seems easy to use & does the job. 
(- even a 'fixed' unetbootin is a bit of a chore because it always opens the file browser at / & defaults to all files shown. I'd think the majority of users don't need persistence, they just want a live usb to install, try or for repair work.

---

### Post by ventrical on 2015-08-05
> **mc4man said:**
> I'd think the majority of users don't need persistence, they just want a live usb to install, try or for repair work.

+1

---

### Post by sudodus on 2015-08-05
> **ventrical said:**
> [QUOTE=mc4man;13333112]I'd think the majority of users don't need persistence, they just want a live usb to install, try or for repair work.

+1[/QUOTE]

+1

---

### Post by kansasnoob on 2015-08-05
I'd always use a tool that creates persistence at the time I'm creating the live USB. Why?

(1) Allow Firefox to keep it's history or even bookmarks.

(2) Retain downloaded apps like Boot-Repair.

(3) Why would I want to spend additional time creating persistence myself when a tool can do it for me?

---

### Post by sudodus on 2015-08-05
It's great to get a real discussion :-)

> **kansasnoob said:**
> I'd always use a tool that creates persistence at the time I'm creating the live USB. Why?

(1) Allow Firefox to keep it's history or even bookmarks.

(2) Retain downloaded apps like Boot-Repair.
(1) and (2) :

I see your point, but I doubt that most users do that. (For example, most of the time I don't want persistence.)
> 
(3) Why would I want to spend additional time creating persistence myself when a tool can do it for me?

(3) :

If there is a good enough tool, easy to use and reliable, that offers persistence, I certainly agree with you. I understand that you like Unetbootin, or at least think it is good enough and 'would vote for' ***Unetbootin*** to replace the Startup Disk Creator.

Otherwise (if/when/because there is ***not*** a good enough tool that offers persistence), I would spend additional time creating persistence myself*), or use ***'the advanced tool'*** when I want persistence, but most of the time use an easy to use and reliable tool,*** 'the basic tool'***.
[HR]Edit: *)[/HR]
For example, it is possible to have ***a separate USB 3 pendrive with a casper-rw partition*** (and use that to get persistence in cloned systems (by Disks, mkusb, dd, Win32 Disk Imager ...). That 'casper-rw' pendrive can contain your bookmarks for Firefox, and it should survive a whole development cycle, where you are isotesting daily images. You can even have ***a  home-rw partition on that second pendrive***, which increases the chances for you bookmarks to survive (even if the casper-rw partition is borked).

---

### Post by ventrical on 2015-08-05
> **kansasnoob said:**
> I'd always use a tool that creates persistence at the time I'm creating the live USB. Why?

(1) Allow Firefox to keep it's history or even bookmarks.

(2) Retain downloaded apps like Boot-Repair.

(3) Why would I want to spend additional time creating persistence myself when a tool can do it for me?

I have done this many times in the past but I never keep them up. The cycles develop so fast around here that the previous peristent drives are obsoleted... but I agree that they can come in handy to remember bookmarks so they can be a good realtime test library.

Regards..

 I think my SSD cards have spoiled me:) They are so fast .. that .. well .. you know :)

---

### Post by sudodus on 2015-08-06
'Bump'

[COLOR="#696969"]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)

---

### Post by mörgæs on 2015-08-06
> **mc4man said:**
> s-d-c can either work or fails in so many different ways or reasons that it seems impossible to maintain & should be redone or abandoned.
As far as unetbootin the Debian/Ubuntu packages are seriously outdated & contain a real flaw that can cause users issues if not careful
(the .iso file browser has both root permissions & DnD capabilities

The above issue was finally fixed but not in any version except from the ppa build. (bug wasn't addressed until I filed a new one requesting unetbootin be removed from repo, that caught the dev's attention

However the new ppa builds don't recommend  gksu, users will get a pop suggesting 'sudo /usr/bin/unetbootin' or 'su --c '/usr/bin/unetbootin', not sure if that's a good idea or not. 
(may be fine..?, note it will use gksu if gksu is installed

Thanks for pushing the fix. 

Do you know if the old browsing-as-root-bug is also fixed in the PPA version? I am not on Buntu right now so I can't check.

[https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/468050](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/468050)

---

### Post by flocculant on 2015-08-06
> **sudodus said:**
> 'Bump'

There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet,please tell us what ***you*** use and why you prefer that tool :-)

Sometimes I'll use SDC - if I'm not too worried about tabbing and giving it a command to run, never use persistence.

Sometimes I'll use the gnome disk utility.

Sometimes I'll use dd. 

> **mc4man said:**
> ... I'd think the majority of users don't need persistence, they just want a live usb to install, try or for repair work.

> **mc4man said:**
> s-d-c can either work or fails in so many different ways or reasons that it seems impossible to maintain & should be redone or abandoned...

I'd agree with both of those.

---

### Post by sudodus on 2015-08-08
TheFu replied the following in another thread. I asked and he let me quote it here, because I think it will add to the discussion this thread.

> **TheFu said:**
> If you need to build the install/try USB flash drive from Windows, I've found **yumi** to be the easiest for multi-boot stuff. It is nice to have 1, 2, 5, 10, 20 different Linux ISOs there, ready to boot off a single flash drive. yumi is available at the unetbootin website too.

If you need to build the install/try USB flash drive from Linux (or any Unix), you can just use **dd** to shove the ISO onto any flash drive. It isn't pretty, but you don't need any special tools. It will effectively wipe the flash drive.  The other downside to using dd is it is not multi-boot. Only one ISO at a time.

The tool you use to build a bootable flash drive really isn't that important.  You should also be aware that some flash drives and some PCs just are not compatible for booting. I haven't figured out any way to know if one will work with the other or not. Sometimes new drives don't work, sometimes they do. Sometimes old drives dont' work, sometimes they do. I dunno. Cheap/expensive ... doesn't seem to matter either.

> Hi TheFu,

We are discussing tools to make pendrives in this thread: [Discussion: Selecting a tool to create USB boot drives from ISO files](http://ubuntuforums.org/showthread.php?t=2289225)

1. You are very welcome to post [something like what you posted today] in that link and take part in the discussion. I think it would add in a positive way to the discussion :-) because you are suggesting several tools, but none of the two GUI tools that come with the Ubuntu flavours (the 'Startup Disk Creator' and 'Disks'), and I hope that we can find and suggest a good tool to replace the 'Startup Disk Creator'.

2. If you won't bother to post in that thread, is it OK if I quote your post (like above)? I will only post it if you think it is OK.

Best regards
sudodus

[QUOTE=TheFu]... Copy away, if you think it helps.
Please provide consideration for Server users - not everyone has a GUI or wants to load a large GUI tool for something like this.

As to Yumi - Tried the Linux version and it NEVER worked for me.  OTOH, the Windows version has never failed me. Have a few flash drives here with 5+ different ISO boots on them - usually a "save my butt" distro is what it is used.
 
I've never seen "Disks" and have never tried to have any persistent data on a boot-flash drive.[/QUOTE]

---

### Post by sudodus on 2015-08-08
So far I think there is only the debian recommendation without safety belt (see post [#20](http://ubuntuforums.org/showthread.php?t=2289225&p=13332147#post13332147)) in text mode, suitable for server users. I would like to add [mkusb-nox](https://help.ubuntu.com/community/mkusb/v7) for this purpose. It wraps security around dd just like mkusb, but without the GUI bells and whistles.

The 'first time' dialogue:
```
$ [COLOR="#0000FF"]sudo mkusb-nox ubuntu-14.04.1-server-amd64.iso[/COLOR]
[sudo] password for sudodus: 
The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
mount: block device /media/multimed-2/CD/ubuntu/14.04/ubuntu-14.04.1-server-amd64.iso is write-protected, mounting read-only
disk_name_type=desktop
Ubuntu-Server 14.04.1 LTS "Trusty Tahr" - Release amd64 _found_ in iso-file
Ubuntu-Server 14.04.1 LTS "Trusty Tahr" - Release amd64 _not_ in USB device
Do you want to make a new one? (y/n)
[COLOR="#0000FF"]**y**[/COLOR]
[COLOR="#B22222"]***  WARNING: the device will be completely overwritten      ***
***  quit with (q)                                           ***[/COLOR]
***  Unmount the device if mounted  ****************************
 
Name: ata-SAMSUNG_HD322HJ        Dev: /dev/sda  Size: 320GB
Name: ata-OCZ-AGILITY3           Dev: /dev/sdb  Size: 60GB
Name: ata-WDC_WD1003FBYZ-010FB0  Dev: /dev/sdc  Size: 1000GB
Name: usb-SanDisk_Cruzer_Blade   Dev: /dev/sdd  Size: 4005MB
Live drive: /dev/sdb
 
[color="#B22222"]---> 1: install to USB: SanDisk_Cruzer_Blade Dev: /dev/sdd Size: 4005MB[/COLOR]
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
[COLOR="#0000FF"]**g**[/COLOR]
1: source: ubuntu-14.04.1-server-amd64.iso
   target: USB: SanDisk_Cruzer_Blade   Dev: /dev/sdd  Size: 4005MB
[color="#B22222"] Final checkpoint [/COLOR]
Please check again that it is the correct target device! (y/n)
[COLOR="#0000FF"]**y**[/COLOR]
 
Installing ubuntu-14.04.1-server-amd64.iso to /dev/sdd ...
 
< "ubuntu-14.04.1-server-amd64.iso" pv -s 599785472 | dd bs=4096  of=/dev/sdd
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
 572MB 0:01:42 [5.58MB/s] [==================================>] 100%            
146432+0 records in
146432+0 records out
599785472 bytes (600 MB) copied, 117.426 s, 5.1 MB/s
Syncing the device ...
Done :-)
$ 
```

The simplified 'next time' alias 'isotesting' dialogue:
```
$ [COLOR="#0000FF"]sudo mkusb-nox ubuntu-14.04.1-server-amd64.iso[/COLOR]
The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
mount: block device /media/multimed-2/CD/ubuntu/14.04/ubuntu-14.04.1-server-amd64.iso is write-protected, mounting read-only
disk_name_type=desktop
Ubuntu-Server 14.04.1 LTS "Trusty Tahr" - Release amd64 _found_ in iso-file
Ubuntu-Server 14.04.1 LTS "Trusty Tahr" - Release amd64 _found_ in /dev/sdd
[color="#B22222"] Final checkpoint [/COLOR]
Install to /dev/sdd? (y/n)
[COLOR="#0000FF"]**y**[/COLOR]
pv "ubuntu-14.04.1-server-amd64.iso"| dd of=/dev/sdd bs=4096 ...
 572MB 0:01:42 [5.57MB/s] [==================================>] 100%            
146432+0 records in
146432+0 records out
599785472 bytes (600 MB) copied, 116.76 s, 5.1 MB/s
syncing the drive ...
The Ubuntu-Server 14.04.1 LTS "Trusty Tahr" - Release amd64 USB device is re-cloned  :-)
$ 
```

---

### Post by PJs Ronin on 2015-08-08
I feel a little out of place posting in a thread with a lot of red usernames, but here's my two penneth.

I tried SDC once, and it had a hernia.   My impression is that for novices like me, once something takes a dump we don't go back to it at a later time and I haven't been back to SDC... I just don't trust the damn thing.   I have used Unetbootin and sort of like it.   This is where I first came across persistence and while I appreciate some folks might want/need it, I don't.   Unfortunately, Unetbootin seems to have a mind of it's own when it comes to recognizing (my) flash drives.   Sometime it sees them, sometimes not so much.   I understand (a little) what dd does... but I just can't be bothered using it.   I'm a GUI guy.

Finally, some time ago I saw a post hereabouts mentioning you could make a bootable iso with the Disks program.   Tried it, never failed, loved it, say no more.

---

### Post by SuperFreak on 2015-08-08
I use [Easy2Boot]("http://www.easy2boot.com/") it works great allows me to load Windows and Linux ISOs onnto single USB Stick. I haven't tried persisitence but that is possible also

---

### Post by jerrylamos on 2015-08-08
> **sudodus said:**
> 'Bump'

[COLOR="#696969"]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)

Much of the time I resort to the dangerous dd.  Achtung, can wipe out a hard drive if "of" is the wrong /dev/sdc so know what you're doing.

cd to the folder that has the .iso, example here Wily

dd if=wily-desktop-amd64.iso of=/dev/sdc bs=4M; sync

Last time I used this dd was for a Win 10 peview .iso.  Worked fine.

Sometimes Disk Image will work with Ubuntu .iso,  More safeguards

Download the ISO
With File Manager navigate to the .iso 
Right button select
Select Open With
Select Disk Image Writer
Insert your USB stick in the knowledge that it’s going to get wiped
Choose “Restore Disk Image”
Select the USB.  For whatever reason many times Ubuntu doesn't want to.
Click “Start restoring”
Wait
Boot and select “Try Ubuntu….”
Done *

I find Brasero very cranky has worked one time out of many tries.  
Disk Image Creator over the years fails for me most of the time.

I also boot the .iso directly from the hard disk to do installs to whatever partition.  Writing usb is a bit simpler and slower.

BTW, this is a quintuple boot.  On the hard drive dual boots Win 7 and Win 10, on usb ssd triple boots 3 partitions, wily, a previous wily, 14.04-3 LTS

I have used persistence in the past lately I just pick out my least used usb ssd partition and install to that.

Why Win anything?  When I pass this desktop on it will have a hard drive that boots to something people expect.
                                 I don't much care for Win anything, however my wife uses some windows specific applications to support a couple web sites and sometimes we both work on problems.

Grub is a major gripe for me.  Grub is always desperately trying to over write the boot on the /dev/sda hard drive I've had to recover the Win boot loader several times on two test pc's.

---

### Post by drfox on 2015-08-10
> **sudodus said:**
> I tried multisystem some years ago. And it worked for me too. Does the current version work in UEFI mode?

I use Multisystem and it works fine with UEFI. You can also choose which iso(s) to be made persistent.

Larry

---

### Post by QDR06VV9 on 2015-08-10
> **drfox said:**
> I use Multisystem and it works fine with UEFI. You can also choose which iso(s) to be made persistent.

Larry
+1
 I have used it for about 8 months now the only error's I have had have been Arch, some Gentoo spins, and windows 10
Plus it has a few tools like Plop boot and others. 
More info [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
I have yet to find a single app that works for everything.
Regards

---

### Post by ventrical on 2015-08-10
> **runrickus said:**
> +1
 I have used it for about 8 months now the only error's I have had have been Arch, some Gentoo spins, and windows 10
Plus it has a few tools like Plop boot and others. 
More info [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
I have yet to find a single app that works for everything.
Regards

I first started out with Plop using it on CDs and 1.44 floppies. It would get difficult machines to boot from USB and therefore install Ubuntu. I still use it.

Regards..

---

### Post by sudodus on 2015-08-11
Great that ***Multisystem*** works in UEFI mode too :-)

And yes, I have used ***Plop*** too. Some really old computers need chainloading and Plop's driver to boot from USB :-P

---

### Post by ventrical on 2015-08-12
> **sudodus said:**
> Great that ***Multisystem*** works in UEFI mode too :-)

And yes, I have used ***Plop*** too. Some really old computers need chainloading and Plop's driver to boot from USB :-P

Actually I have a Sony USB 1.44 floppy floppy drive that is a carry-a-round (used for more legacy laptops) and the Plop  1.44 image will boot most any machine that has USB ports. Using Plop is good to boot ubuntu images  from USB sticks on really old machines and if not USB then CD Rom or DVD.  On consultations  - do not leave home without Plop and Sony USB 1.44! 

 A little off topic .. but may be interesting to see how newer wily kernels would load on older hardware.

Regards..

---

### Post by sudodus on 2015-08-12
> **ventrical said:**
> Actually I have a Sony USB 1.44 floppy floppy drive that is a carry-a-round (used for more legacy laptops) and the Plop  1.44 image will boot most any machine that has USB ports. Using Plop is good to boot ubuntu images  from USB sticks on really old machines and if not USB then CD Rom or DVD.  On consultations  - do not leave home without Plop and Sony USB 1.44! 

 A little off topic .. but may be interesting to see how newer wily kernels would load on older hardware.

Regards..

It is interesting to learn about tools that work 'everywhere' :-)

I have been able to boot ToriOS with an old Ubuntu 12.04 LTS non-pae kernel (not forcepae, not fake-pae, really non-pae) in UEFI mode. I did it with ***mkusb version 10 with a modified grub-n-iso installer*** added to create persistent live USB drives. This system does not boot directly from grub and an iso file, but from a copy of the iso file cloned into partition #2. Partition #1 is the boot partition (and EFI partition). Partition #3 is a casper-rw partition. ***The idea is to add persistence and make it a more complete tool for the Ubuntu family and some community re-spins with similar boot structure.*** Booting via grub from a cloned copy of the iso file into partition #2 makes it work with some re-spins that do not boot from an iso file (at least I cannot do it).

The version of mkusb is [s]still not tested by anyone except me[/s] tested by *ventrical* and me. It needs testing before even getting into the unstable PPA, and you find the way to get it via this link: [ Re: Howto make USB boot drives post #120](http://ubuntuforums.org/showthread.php?t=1958073&page=6&p=13337410#post13337410)

---

### Post by sudodus on 2015-08-18
'Bump'

[COLOR="#696969"]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)

---

### Post by QDR06VV9 on 2015-08-18
> **ventrical said:**
> Actually I have a Sony USB 1.44 floppy floppy drive that is a carry-a-round (used for more legacy laptops) and the Plop  1.44 image will boot most any machine that has USB ports. Using Plop is good to boot ubuntu images  from USB sticks on really old machines and if not USB then CD Rom or DVD.  ***On consultations  - do not leave home without Plop and Sony USB 1.44!*** 

 Regards..
He He Same here. Just works. Maybe a little more info for those unfamiliar with Plop.
[http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot](http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot)

> **sudodus said:**
> 'Bump'

[COLOR=#696969]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)
Have to admit I have not tried your method yet, But I will in a couple days.(Forgive me a little busy ATM)
But Hats off to you for your efforts! And ventrical he is great at stepping up and testing most anything.:D
So far I use 1.Multi-system, 2.Unetbootin(When it will work), and 3.DD(if it don't eat my USB Drive :D) and sometimes i have to resort to using K3B to burn Disk.:p
I too would have thought more would have gotten involved on this thread?
Thanks and Regards

---

### Post by ventrical on 2015-08-18
> **runrickus said:**
> He He Same here. Just works. Maybe a little more info for those unfamiliar with Plop.
[http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot](http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot)


Have to admit I have not tried your method yet, But I will in a couple days.(Forgive me a little busy ATM)
But Hats off to you for your efforts! And ventrical he is great at stepping up and testing most anything.:D
So far I use 1.Multi-system, 2.Unetbootin(When it will work), and 3.DD(if it don't eat my USB Drive :D) and sometimes i have to resort to using K3B to burn Disk.:p
I too would have thought more would have gotten involved on this thread?
Thanks and Regards

Thanks for the link and the kudos ;)

mkusb is (10.xx) very efficient at creating persistent USB drives for UEFi and BIOS boot-ups and even presents you with a selection option to boot the 'live' image or persistent image - so it is a very well crafted script. Thing is I am always tearing and ripping burns of different distros (and their subsequent upgrades) to do 'live' test and hard installs <so not using persistence for ubuntu testing>. In all honesty (as mentioned  before) ubuntu-disks is the most reliable for this kind of testing. You're in and out and you do you're test at qa and your done. So it's just a downtime saver to use 'disk'. mkusb is more versatile in the sense that is has more toggles and more options can be executed to do custom install and it efficeintly utilizes USB flash drives in a fuller potential.

Regards...

---

### Post by ventrical on 2015-08-18
For specialty installs - don't leave home without PLOP;)

---

### Post by QDR06VV9 on 2015-08-18
> **ventrical said:**
> For specialty installs - don't leave home without PLOP;)

+2 That would be like a mechanic going to work with no tools IMHO:o
nooooooooooo!
That is why I use multisystem already there and a live environment to chase problems.
Thanks Vent!

---

### Post by ventrical on 2015-08-18
What is link for multisystem?

Thnxs !:)

---

### Post by sudodus on 2015-08-18
> **runrickus said:**
> He He Same here. Just works. Maybe a little more info for those unfamiliar with Plop.
[http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot](http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot)


Have to admit I have not tried your method yet, But I will in a couple days.(Forgive me a little busy ATM)
But Hats off to you for your efforts! And ventrical he is great at stepping up and testing most anything.:D
So far I use 1.Multi-system, 2.Unetbootin(When it will work), and 3.DD(if it don't eat my USB Drive :D) and sometimes i have to resort to using K3B to burn Disk.:p
I too would have thought more would have gotten involved on this thread?
Thanks and Regards

Thanks for the kudos, and thanks for telling us what tools you use :-)

I use k3b too, when I need to burn optical disks.

---

### Post by sudodus on 2015-08-18
> **ventrical said:**
> What is link for multisystem?

Thnxs !:)

I think this link works: [pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by cariboo on 2015-08-19
[Multisystem]("http://sourceforge.net/projects/multisystem/")? 

**Note:** Ublock, blocks Sourceforge by default.

---

### Post by ventrical on 2015-08-19
Thanks for the links . Looked them over. Will try a test later in the development.

Regards..

---

### Post by dino99 on 2015-08-19
> **ventrical said:**
> What is link for multisystem?

Thnxs !:)

donwload & update, from 'synaptic':
[HTML]http://liveusb.info/multisystem/depot all main[/HTML]

---

### Post by ventrical on 2015-08-19
This one here ?
edit: apologies: off topic.

---

### Post by QDR06VV9 on 2015-08-19
> **ventrical said:**
> This one here ?
edit: apologies: off topic.


Yes Sir.
Forgot to mention that you need xterm installed, to run the installer.
For clarification by live environment  I was speaking of any ISOs related like Boot Repair or Windows Tools for chasing problems.
But I think you got my drift:D
Regards

---

### Post by ventrical on 2015-08-20
Downloaded , extracted, got this : now what ?

---

### Post by dino99 on 2015-08-20
> **ventrical said:**
> Downloaded , extracted, got this : now what ?

you can get the deb installed directly while updating/upgrading with the link i've given some posts above

---

### Post by ventrical on 2015-08-20
> **dino99 said:**
> you can get the deb installed directly while updating/upgrading with the link i've given some posts above

Yes .. I had seen that  but I must admit that I am having a complete brain cramp here. I opened synaptic .. etc.. you sent me html code (html url code will not work in firefox) .. etc... not sure exactly how to do this, how to insert html code into repository settings?

Do I have to use 'get' ?

Regards..

---

### Post by ventrical on 2015-08-20
> **runrickus said:**
> Yes Sir.
Forgot to mention that you need xterm installed, to run the installer.
For clarification by live environment  I was speaking of any ISOs related like Boot Repair or Windows Tools for chasing problems.
But I think you got my drift:D
Regards

Sorry ... I am having one of my Homer Simpson moments :)

regards..

---

### Post by ventrical on 2015-08-20
Ok .. got it:

```

deb http://liveusb.info/multisystem/depot all main

```

edit : whoops

---

### Post by ventrical on 2015-08-20
So is the standard to ignore?

---

### Post by QDR06VV9 on 2015-08-20
> **ventrical said:**
> Downloaded , extracted, got this : now what ?

Right click change permissions and make executable, run  in terminal and xterm will pop-up password and Ta Da
your very own multisystem:D Depending on what DE you will find it under Application>Accessories
Opps did not see your last post never have i seen that before. I had scrolled down to your post's and did not see dino's posts above
Do you still have the .tar.gz?
Regards

---

### Post by dino99 on 2015-08-20
> **ventrical said:**
> Ok .. got it:

```

deb http://liveusb.info/multisystem/depot all main

```

edit : whoops

To fix the 'no_pubkey'  ):P
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  4E940D7F

---

### Post by ventrical on 2015-08-20
> **dino99 said:**
> To fix the 'no_pubkey'  ):P

nope! Didn't work....

```

ventrical@ventrical-luntiy-betatest:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E940D7F 
[sudo] password for ventrical: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.SnMoidE73n --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4E940D7F
gpg: requesting key 4E940D7F from hkp server keyserver.ubuntu.com
gpgkeys: key 4E940D7F not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

but I will install it anyways :)

---

### Post by QDR06VV9 on 2015-08-20
This should work for the Key
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E940D7FDD7FB8CC
```
Got enough cooks going on here LOL
Regards

---

### Post by dino99 on 2015-08-20
> **ventrical said:**
> nope! Didn't work....

```

ventrical@ventrical-luntiy-betatest:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E940D7F 
[sudo] password for ventrical: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.SnMoidE73n --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4E940D7F
gpg: requesting key 4E940D7F from hkp server keyserver.ubuntu.com
gpgkeys: key 4E940D7F not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

but I will install it anyways :)

adding the port 80 might help

sudo apt-key adv --keyserver keyserver.ubuntu.com:80 --recv-keys 4E940D7F

( code = the first 8 alphanum of the returned code error) (hopes i've recopied the right ones)
if that does not work to receive the key, then it could be that the multysystem server delivering the key is down (it often happen), so retry some days later.
you can accept the upgrade without that key authentification.

---

### Post by ventrical on 2015-08-20
Completely destroyed unity desktop. I tried to install razorqt and get total white space. I'll install fvwm-crystal DE to see if I can see what the hades went wrong. :)

maybe I should mention that I am using wiley install of ubuntu-desktop.

Regards..

---

### Post by ventrical on 2015-08-20
Rebooted and razorqt DE came up Multisystem also is installed.  I am a little disappointed that it blew out unity. I'll try to recover.

Thanks and regards..

---

### Post by QDR06VV9 on 2015-08-20
I was assuming you were on Wily.
That is why I use the .tar.bz 
But I still could be second guessing Due the fact No Unity here.
But every other DE has been flawless.
Regards

---

### Post by ventrical on 2015-08-20
> **runrickus said:**
> I was assuming you were on Wily.
That is why I use the .tar.bz 
But I still could be second guessing Due the fact No Unity here.
But every other DE has been flawless.
Regards

Thanks. Good to know that there is more than one option :) Actually I am glad  now that I lost unity because I would not of seen how razorqt DE is really coming along!

Regards..

---

### Post by ventrical on 2015-08-20
Ok.. I recovered unity7 desktop. Whew! (the most excitement yet this cycle) :)
During upgrade/install and opening of multisystem it removed some compiz files.
Program works ok . Ready to test bootable drive.

---

### Post by ventrical on 2015-08-20
> **runrickus said:**
> I was assuming you were on Wily.
That is why I use the .tar.bz 
But I still could be second guessing Due the fact No Unity here.
But every other DE has been flawless.
Regards

It's a real 'wow' experience. That thing loaded the USB up with all sorts of  little bootable goodies, syslinux, plop bootloader etc...

Really cleverly written. Somebody burned the midnight oil on that one. ;)

Regards..

btw - works fine on unity.

---

### Post by sudodus on 2015-08-21
> **ventrical said:**
> [QUOTE=runrickus;13341971]I was assuming you were on Wily.
That is why I use the .tar.bz 
But I still could be second guessing Due the fact No Unity here.
But every other DE has been flawless.
Regards

It's a real 'wow' experience. That thing loaded the USB up with all sorts of  little bootable goodies, syslinux, plop bootloader etc...

Really cleverly written. Somebody burned the midnight oil on that one. ;)

Regards..

btw - works fine on unity.[/QUOTE]

Do you mean that Multisystem installed via the tarball (.tar.bz file) brings all those goodies?

---

### Post by QDR06VV9 on 2015-08-21
> **ventrical said:**
> It's a real 'wow' experience. That thing loaded the USB up with all sorts of  little bootable goodies, syslinux, plop bootloader etc...

Really cleverly written. Somebody burned the midnight oil on that one. ;)

Regards..

btw - works fine on unity.
I am happy you recorvered Unity:D
Had a hunch you would like it.
With the right ISO's loaded, Well it turns into a nice little portable toolbox.

> **sudodus said:**
> Do you mean that Multisystem installed via the tarball (.tar.bz file) brings all those goodies?

Yes Sir!:D
I think the ppa is added with the installer.
Don't forget the installer needs "xterm" installed.
Kind Regards

---

### Post by sudodus on 2015-08-21
I used Multisystem for a year or so some years ago. I think the ppa disappeared when I installed precise in my 'work-horse'. And I never refreshed it, I guess I didn't need it.

I'm glad that Multisystem is still going strong :-)

But it should ask for xterm during the installation. mkusb asks for xterm, zenity (depends), and pv, wmctrl (recommends).

---

### Post by ventrical on 2015-08-21
> **sudodus said:**
> Do you mean that Multisystem installed via the tarball (.tar.bz file) brings all those goodies?

Actually it brings up a menu where multisystem will <search> for those isos. They are not loaded by default. It is a good tool to use in the sense where I only have to use one USB drive to boot mutiple flavour .ISOs for ubuntu so I can take a 32GB USB flash drive and even put alternate .ISOs on there for older machines so one USB drive will fit all PCs sort of.

 I think mkusb does this also ?

Regards..

---

### Post by QDR06VV9 on 2015-08-21
Finally Got around to to giving mkusb a whirl, And Glad I did!;)
Nicely Done. Another tool I will make good use out of.
For me it was the first **usb tool **that would make a boot able installer for Arch.:o
Regards

---

### Post by sudodus on 2015-08-21
@ ventrical:

***mkusb*** installs only one operating system each time.

But I made [another kind of installers, that uses the 'grub-n-iso' method](http://ubuntuforums.org/showthread.php?t=2259682) and they can manage booting from either of several iso files. They can even boot 32-bit systems in UEFI mode. These 'grub-n-iso' systems are limited to systems that can run live sessions, so do not work with the Ubuntu mini.iso, Ubuntu Server and Lubuntu alternate iso with debian installers.

Can ***Multisystem*** boot from iso files with debian installers? Try if you haven't done it yet :-P

---

### Post by sudodus on 2015-08-21
> **runrickus said:**
> Finally Got around to to giving mkusb a whirl, And Glad I did!;)
Nicely Done. Another tool I will make good use out of.
For me it was the first **usb tool **that would make a boot able installer for Arch.:o
Regards

I'm glad you like it. I made it and keep improving it to help booting and installing linux :-)

---

### Post by ventrical on 2015-08-21
> **sudodus said:**
> @ ventrical:

***mkusb*** installs only one operating system each time.

But I made [another kind of installers, that uses the 'grub-n-iso' method]("http://ubuntuforums.org/showthread.php?t=2259682") and they can manage booting from either of several iso files. They can even boot 32-bit systems in UEFI mode. These 'grub-n-iso' systems are limited to systems that can run live sessions, so do not work with the Ubuntu mini.iso, Ubuntu Server and Lubuntu alternate iso with debian installers.

Can ***Multisystem*** boot from iso files with debian installers? Try if you haven't done it yet :-P

Ok.. I had put precise-alternate on there yesterday but did not try to boot it. I had also put a Windows 8 or 10 release .iso but it will not boot up. I am working on that.

edit:

Installing currently with no problems. I will wait for full reboot  before I report a success with Debian. This is good discussion. A discussion that needs to be brought up to Canonical to see what they are going to do about SDC and/or alternate method of installing ISOs to USBs.

Regards..

edit:

Rebooted to hdd  ok . Some problems with video driver (not Debian install related).

---

### Post by QDR06VV9 on 2015-08-21
> **ventrical said:**
> Ok..
Installing currently with no problems. I will wait for full reboot  before I report a success with Debian. This is good discussion. _**A discussion that needs to be brought up to Canonical to see what they are going to do about SDC and/or alternate method of installing ISOs to USBs.**_

Regards..



Rebooted to hdd  ok . Some problems with video driver (not Debian install related).
+1;)
How did you do with windows 8 or 10, Still working on it i'll bet.
Here is what I get for now. Had to reformat USB to fat32 but still wont boot to installer
but seems to be ok for upgrade method.(setup exe.)

Post back if you have success with 8 or 10.
And as always Thanks and Kind Regards

---

### Post by sudodus on 2015-08-21
> **runrickus said:**
> [quote=ventrical;13342543]ok..
Installing currently with no problems. I will wait for full reboot  before i report a success with debian. This is good discussion. _**a discussion that needs to be brought up to canonical to see what they are going to do about sdc and/or alternate method of installing isos to usbs.**_

regards..

Edit:

Rebooted to hdd  ok . Some problems with video driver (not debian install related).
+1 ;)[/quote]

+1 :-)

I sent a mail to *Nicholas Skaggs* just ten minutes before reading your posts here. I think he knows which is the right forum at Canonical to discuss replacing the Startup Disk Creator. (Some year ago he was involved in an attempt to replace it.)

***Edit:*** Nicholas replied in a mail:

[QUOTE=Nicholas Skaggs]The proper place to have this discussion is on the ubuntu-desktop mailing list.

[email]ubuntu-desktop@lists.ubuntu.com[/email]

You'll have to make a case for changing the default software on that list.[/QUOTE]

After further discussion in this thread, I think it will be time to 'make a case' at that mailing list. I guess there are corresponding forums for the Ubuntu flavours too.

---

### Post by SuperFreak on 2015-08-21
Easy2Boot will load an extensive list of Linux and Windows ISOs dependent mainly on the size of the USB stick[http://www.easy2boot.com/add-payload-files/list-of-tested-payload-files/]("http://www.easy2boot.com/add-payload-files/list-of-tested-payload-files/")

---

### Post by QDR06VV9 on 2015-08-21
> **sudodus said:**
> +1 :-)

I sent a mail to *Nicholas Skaggs* just ten minutes before reading your posts here. I think he knows which is the right forum at Canonical to discuss replacing the Startup Disk Creator. (Some year ago he was involved in an attempt to replace it.)

***Edit:*** Nicholas replied in a mail:



After further discussion in this thread, I think it will be time to 'make a case' at that mailing list. I guess there are corresponding forums for the Ubuntu flavours too.
Nice, Got the ball rolling at least let us know how we can help.
Kind Regards

---

### Post by sudodus on 2015-08-21
> **runrickus said:**
> Nice, Got the ball rolling at least let us know how we can help.
Kind Regards

The best way to help is to think in a general way - what is best for the users of Ubuntu (and Kubuntu, Lubuntu, Ubuntu MATE, Xubuntu, ...). Which tool should be included in the iso file and why? I tried to list some aspects to think of in the opening post. So do not only think what is best for you, but what would be best also for people with more or less experience of installing linux. It is particularly important that it works for beginners :-)

-o-

And, of course, write it in a post in this thread :-D

---

### Post by ventrical on 2015-08-22
> **runrickus said:**
> +1;)
How did you do with windows 8 or 10, Still working on it i'll bet.
Here is what I get for now. Had to reformat USB to fat32 but still wont boot to installer
but seems to be ok for upgrade method.(setup exe.)

Post back if you have success with 8 or 10.
And as always Thanks and Kind Regards

I am working two projects with  the latest Win products. The first is getting Win 8/10 to be nice to ubuntu in a side by side install in UEFI mode on a >2TB hdd. I had some success with the latest lubuntu alpha 2 but Windows is just so terribly slow - even on newer machine with 16GB ddr3. Secondly  I want to see if I can install Windows 8 or 10 from the USB using multisystem. I tired to do with with mkusb but will not work. (Will try again). It does work with multisystem but it boots into a recovery session and tells me that I need to repair Windows .. etc.. and thats not what I want. I think I have to download  the win10 free version again. I'll be on this and see what happens.
As always .. thanks for your input and motivation ;)

regards..

---

### Post by jerrylamos on 2015-08-22
Success here with a .iso of Win 10 received as part of the Win 10 preview.
Formatted USB to FAT32 with gparted
made sure it was /dev/sdc
(a mistake on the of could be a disaster) 
sudo dd if=filename.iso of=/dev/sdc bs=4M; sync

I run Ubuntu on a USB SSD, with USB first on boot sequence and usually booting Ubuntu
Win 10 on the internal hard drive occasionally for updates, security of course Microsoft has lots of security updates
Remove USB to boot Win 10, update, play around, whatever
My wife has one web site application which only works with Win & Microsoft Word 2010
Re-insert USB to boot Ubuntu
Achtung!  Win 10 re-orders boot sequence and have to do F1, F12, and even go into bios to get the boot order restored on Lenovo M59p.
Not as much trouble with this Acer 5253 laptop.

Another reason for Win is every few years I find a bargain on recon pc and want to pass the old one on, with Win for subsequent user.

---

### Post by sudodus on 2015-08-22
@ jerrylamos:

The same method (via mkusb, but it is dd under the hood) does *not* work for me with the following windows 10 preview iso file. But it works from DVD.

```
ls -l
-rw-rw-rw- 1 nio nio 4100497408 okt  6  2014 WindowsTechnicalPreview-x64-EN-US.iso

md5sum
9005dce26734bcde7f912c2c51ab1127  WindowsTechnicalPreview-x64-EN-US.iso
```

What version of windows 10 preview are you using? Is it treated with isohybrid or some corresponding tool?

---

### Post by sudodus on 2015-08-22
By the way jerrylamos, sorry for getting back to the topic of this thread: Maybe you would recommend a safer tool (not dd) for beginners. Please tell us (what you would recommend and maybe see in a future version of Ubuntu) :-)

---

### Post by dino99 on 2015-08-22
yeah, i'm not a 'dd' user, i find it too 'brute force' for most non techies people, and is not following the ubuntu spirit 'ubuntu is for humans'

---

### Post by sudodus on 2015-08-22
I was curious and browsed the internet about making pendrives for Windows 10. It seems you have to do more than just clone an iso file (for burning to a DVD disk). I think *jerrylamos* has found a special iso file, that is prepared for USB.


1. AskUbuntu refers to a [PPA for making boot pendrives with Windows](https://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

```
sudo add-apt-repository ppa:colingille/freshlight
sudo apt-get update
sudo apt-get install winusb
```

***winusb*** works with previous versions, but it does not work with Windows Technical Preview 10.  The pendrive boots in BIOS mode but complains that a file has a bad signature. *Edit:* Setting the internal clock in the computer to January 2015 made it work, so the problem is that the Technical Preview has passed end of life, now that Windows 10 is released. It seems that ***winusb*** works with Windows 10 but I cannot test it because I haven't got it.


2. Rufus is recommended by more than one web-site. It is a Windows program, not a tool to run in linux.

[http://rufus.akeo.ie/](http://rufus.akeo.ie/)


3. The following link describes three methods, that should work. If I understand it correctly, they all use tools that run in Windows.

[USB Flash Drive - Create to Install Windows 10 ](http://www.tenforums.com/tutorials/2376-usb-flash-drive-create-install-windows-10-a.html)

---

### Post by jerrylamos on 2015-08-22
When it works, I much prefer Files > navigate to folder with .iso >right click .iso > open with > Disk Image Writer

That didn't work for the Win 10 preview .iso

---

### Post by QDR06VV9 on 2015-08-22
> **sudodus said:**
> I was curious and browsed the internet about making pendrives for Windows 10. It seems you have to do more than just clone an iso file (for burning to a DVD disk). I think *jerrylamos* has found a special iso file, that is prepared for USB.   1. AskUbuntu refers to a [PPA for making boot pendrives with Windows]("https://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu")  ```
sudo add-apt-repository ppa:colingille/freshlight sudo apt-get update sudo apt-get install winusb
```  It works with previous versions, but it does not work with Windows 10. The pendrive boots but complains that a file has a bad signature. Maybe it will be updated.   2. Rufus is recommended by more than one web-site. It is a Windows program, not a tool to run in linux.  [http://rufus.akeo.ie/](http://rufus.akeo.ie/)   3. The following link describes three methods, that should work. If I understand it correctly, they all use tools that run in Windows.  [USB Flash Drive - Create to Install Windows 10 ]("http://www.tenforums.com/tutorials/2376-usb-flash-drive-create-install-windows-10-a.html") I was going to try to stay strictly Linux native tools,  But like you I turned up the same results Rufus winusb etc etc. How ever I got the Windows 10 iso to boot using 2 USB sticks one with Plop and the other had the win 10 ISO(RTM) that was burned with unetbootin. This was done on a LenovoB570 Lappy UEFI
Edit: Multisystem will boot to windows10 installer but I did not start to see if it would complete.

---

### Post by sudodus on 2015-08-22
I found that there were problems to boot from the DVD disk too. So I started to think about EOL for the Technical Preview. And yes, when I set the internal clock of my computer to January 2015 it works OK, also ***winusb*** by colingille. It does not halt with the message that a file has a bad signature (I haven't tried it all the way to installing and testing that the installed system works.)

---

### Post by jerrylamos on 2015-08-22
> **sudodus said:**
> @ jerrylamos:

What version of windows 10 preview are you using? Is it treated with isohybrid or some corresponding tool?

Mid June I got onto the Win 10 preview program, wrote DVD to get started.  
Gparted to resize Win 7 smaller created a NTFS partition and installed Win 10 preview to that.  Dual boot Win 7 and Win 10 preview.

There were several updates up to July 13 when I got

Windows10_InsiderPreview_x64_EN-US_10162.iso

which by happenstance appeared to be about the last date they issued.  Used dd to write usb flash drive.

Usual fuss about finding a "product key" that worked.  Much help from the internet.

Updated that several times then a couple days before July 29 got a - massive - update which subsequently found it was release level Win 10 enterprise.

There's internet warnings about counterfeit Win 10 iso's available.

I've gone on to update a Win 7 home to Win 10 home and Win 7 pro to Win 10 pro.  No problems other than usual fuss about updates.
The desktop dual boots Win 10 home from update and Win 10 enterprise from the Preview.  The laptop boots Win 10 pro.
I run mostly ubuntu from usb hard drive.  After booting Win 10, to boot ubuntu some fuss with F1 and F12 and even re-writing bios boot sequence to get going again.  Win 10 is not a good neighbor for me.  Mostly I run ubuntu so it's not a big deal.

---

### Post by sudodus on 2015-08-22
> **jerrylamos said:**
> When it works, I much prefer Files > navigate to folder with .iso >right click .iso > open with > Disk Image Writer

That didn't work for the Win 10 preview .iso

[s]/ Did you clone the iso file to the device /dev/sdx or to the FAT32 partition /dev/sdx1, and did you install or re-use some bootloader, when you succeeded to make a working pendrive with Windows 10? .../[/s]

Edit 1: I see, you had another (newer) iso file, that obviously works when cloned :-)

I understand what you mean by 'Win 10 is not a good neighbour'. I have [had] similar problems, that it is hard to get into Ubuntu again after running Windows 10 Technical Preview.

-o-

Edit 2: I tried with rufus and had the same problem as with winusb, when I continued with the Windows installer from USB: it lacks a driver, maybe for USB, and halts. Maybe it would work better in another computer or with another USB pendrive, but both (the computer and the pendrive) are more than one year old, so older than this version of Windows.

I installed Windows from DVD, this time in BIOS mode, and it seems stable. I can switch between the Lubuntu and Windows. There is no fuss with F1 and F12 and BIOS boot sequence to get going again. So I think those problems are related to UEFI.

---

### Post by ventrical on 2015-08-22
> **sudodus said:**
> I found that there were problems to boot from the DVD disk too. So I started to think about EOL for the Technical Preview. And yes, when I set the internal clock of my computer to January 2015 it works OK, also ***winusb*** by colingille. It does not halt with the message that a file has a bad signature (I haven't tried it all the way to installing and testing that the installed system works.)

THIS is exactly what I suspected !!!! The same thing happened here.   I hit <enter or F8 and it just recycles back to bad signature blue-screen. [s]Am downloading July 28th Free windows 10 enterprise x64 and see if that works.[/s]

Regards..

aborted dl. Will try again later.

---

### Post by jerrylamos on 2015-08-22
[s> **sudodus said:**
> [s]/  I tried with rufus and had the same problem as with winusb, when I continued with the Windows installer from USB: it lacks a driver, maybe for USB, and halts. Maybe it would work better in another computer or with another USB pendrive, but both (the computer and the pendrive) are more than one year old, so older than this version of Windows.

I installed Windows from DVD, this time in BIOS mode, and it seems stable. I can switch between the Lubuntu and Windows. There is no fuss with F1 and F12 and BIOS boot sequence to get going again. So I think those problems are related to UEFI.

My opinion, based on one trial of booting a Windows 7 from usb, Microsoft does NOT want Windows to be run from anything but an installed hard drive screwed into the same pc it was originally installed or manufactured with.

I had a pc break that had a Win 7 dual booted with ubuntu, grub of course.   Put the hard drive from the busted pc into a usb case tried booting on a working pc and got some horrible messages about disastrous configuration change.  Conclusion, don't do that.

Of course I can take ubuntu usb and switch it into another pc, maybe have to change display resolution, and away I go.

---

### Post by QDR06VV9 on 2015-08-22
> **ventrical said:**
> THIS is exactly what I suspected !!!! The same thing happened here.   I hit <enter or F8 and it just recycles back to bad signature blue-screen. [s]Am downloading July 28th Free windows 10 enterprise x64 and see if that works.[/s]

Regards..

aborted dl. Will try again later.
So far the only thing that has worked for me was Multisystem but I pulled the bootmanager && setup.exe out of the folders multisystem had them in && put them in the opening file(IE Open USB Multisystem)
And I did not need Plop this time. Ran the Install and Ta Da It worked a treat!:D
Bios enabled EFI, Although I never tried EFI disabled.(Just info)
So Far Mkusb && Muulitisystem has my Nomination for add to Distro.
Regards

---

### Post by sudodus on 2015-08-23
> **sudodus said:**
> 'Bump'

[COLOR="#696969"]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)

> **sudodus said:**
> The best way to help is to think in a general way - what is best for the users of Ubuntu (and Kubuntu, Lubuntu, Ubuntu MATE, Xubuntu, ...). Which tool should be included in the iso file and why? I tried to list some aspects to think of in the opening post. So do not only think what is best for you, but what would be best also for people with more or less experience of installing linux. It is particularly important that it works for beginners :-)

-o-

And, of course, write it in a post in this thread :-D

Bump

---

### Post by flocculant on 2015-08-23
Given you've got half a dozen people responding - even if you do bump it - mightn't a thread in one of the Chat forums be a sensible thing to try :p

---

### Post by kansasnoob on 2015-08-23
> **flocculant said:**
> Given you've got half a dozen people responding - even if you do bump it - mightn't a thread in one of the Chat forums be a sensible thing to try :p

Maybe start a poll in OS chat? List all available options, eg:

(1) Just fix usb-creator (aka; s-d-c)
(2) Unetbootin
(3) MkUSB
etc, etc, etc.

But I'd include even the most obscure options, including the dreaded dd method.

The thing is before usb-creator ended up so broken my only complaint was the 10 minute time-out for installing the bootloader. Internal alarm clock needed unless you want to sit and watch usb-creator do its thing which is about like watching paint dry.

---

### Post by sgage on 2015-08-23
I usually have good luck with UnetBootin in Linux, wrt Ubuntu. The most reliable of all the ISO to USB tools for me has been a Windows program - LinuxLive USB, aka LiLi. It maintains a database of zillions of distros/rescue images/etc. that seems to be quite regularly updated. I have burned USB keys of all sorts of oddball stuff using LiLo, and it almost always just works.

[http://linuxliveusb.com/](http://linuxliveusb.com/)

---

### Post by sudodus on 2015-08-24
> **flocculant said:**
> Given you've got half a dozen people responding - even if you do bump it - mightn't a thread in one of the Chat forums be a sensible thing to try :p

> **kansasnoob said:**
> Maybe start a poll in OS chat? List all available options, eg:

(1) Just fix usb-creator (aka; s-d-c)
(2) Unetbootin
(3) MkUSB
etc, etc, etc.

But I'd include even the most obscure options, including the dreaded dd method.

The thing is before usb-creator ended up so broken my only complaint was the 10 minute time-out for installing the bootloader. Internal alarm clock needed unless you want to sit and watch usb-creator do its thing which is about like watching paint dry.

You are right, I'll prepare a poll :-)

---

### Post by sudodus on 2015-08-24
Here is a link to the poll:

[Poll: Selecting a tool to create USB boot drives from ISO files](http://ubuntuforums.org/showthread.php?t=2291946)

---

### Post by sudodus on 2015-08-28
Bump :-)

> **sudodus said:**
> 'Bump'

[COLOR="#696969"]There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator).

If you haven't replied yet, [/COLOR]please tell us what ***you*** use and why you prefer that tool :-)

> **sudodus said:**
> Here is a link to the poll:

[Poll: Selecting a tool to create USB boot drives from ISO files](http://ubuntuforums.org/showthread.php?t=2291946)

---

### Post by OGpmpdog on 2015-08-28
Hi!!

I used to like USB Creator, but it's SLOWWWWW, and nowhere near as reliable as it used to be. 

Gnome Disks works!! Last night, I used it to install Fedora 23; it took about 3 minutes to burn to USB (and about 10 minutes to install)!!!!!! 

+1 for Gnome Disks :)

---

### Post by OlafO on 2015-09-14
I have a 2009 17" MacBookPro5,2 that has the Nvidia 9600M video. I've never been able to create bootable USB Flash drives created using any GUI program on a PC (unetbootin, ubuntu's create install media from currently running ubuntu, etc.).

The only method I've used that works (rEFInd or holding down option key during boot) is using the command line dd program on my MacBookPro from a downloaded iso.

Using the steps as a guide from here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx), I created the following sccript I call create-usb-flash-linux.bash that I run in a terminal on my MacBookPro:

```
#!/bin/bash


if [ -z $1 ]; then
    echo ""
    isosfound=$(find . -maxdepth 1 -name "*.iso")
    if [ "$isosfound" == "" ]; then
        echo "** NO iso file given as arg & NO ISO files found, exiting "
        exit 1
    else
        echo "** NO iso file given as arg, but ISO file(s) found :"
        i=0;for f in $isosfound;do isos[$i]=$f;echo "$i: $f";let "i++";done
        echo ""
        echo -n "Enter number of iso file to use from above info [0] "
        read fn
        if [ "$fn" == "" ]; then
            fn=0
        else
            re='^[0-9]+$'
            if ! [[ $fn =~ $re ]] ; then
               echo "** ERROR: \"$fn\" is NOT a number, exiting" >&2; exit 1
            fi
        fi
        if [ $fn -ge 0 ]&&[ $fn -lt $i ]; then
            echo "You've chosen iso file $fn: ${isos[$fn]}"
            iso=${isos[$fn]}
        else
            echo "** ERROR: must enter valid number from above list, exiting"
            exit 1
        fi
    fi
else
    iso=$1
fi
if [ ! -e $iso ]; then
    echo "** ERROR: file \"$iso\" NOT found, exiting"
    exit 1


fi


echo ""
echo "Now running diskutil list ..."
echo ""
cmds="diskutil list"
$cmds
echo ""
echo -n "Enter number 'X' of USB Flash Drive /dev/diskX given above info : "
read X
disk="/dev/disk${X}"
rdisk="/dev/rdisk${X}"
cmds="$cmds $disk"
tmpo=$($cmds)
tmpo=$(echo $tmpo | grep -o "Could not find disk")
if [ "$tmpo" != "" ]; then
    echo "** ERROR: couldn't find $disk from your \"$X\" entry. Bye."
    exit 1
fi
img="${iso%.*}.img"
dmg="${img}.dmg"


echo ""
echo "NOTE: For some linux distros, a conversion from iso to img format needs"
echo "to be done prior to using dd command. Test with original unconverted iso"
echo "first. If that doesn't work, rerun this script and answer \"y\" to"
echo "use iso to img format conversion."
echo ""
echo -n "Given above, convert $iso to .img format ? [n] "
read answer
case "$answer" in
y|Y)
    use_img=1
    echo "OK, converting $iso to .img format, please wait ..."
    cmds="hdiutil convert -format UDRW -o $img $iso"
    echo $cmds; $cmds
    if [ -e $dmg ]; then
        cmds="mv $dmg $img"
        echo $cmds; $cmds
    fi
    echo "Done converting."
    ;;
n|N|"")
    use_img=0
    echo ""
    echo "OK, using original $iso (not converted to .img)."
    ;;
*)
    echo "** ERROR: uncrecognized option \"$answer\" - bye."
    exit 1;
    ;;
esac


echo "Unmounting USB flash drive: $disk prior to dd command ..."
cmds="diskutil unmountDisk $disk"
echo $cmds; $cmds


if [ $use_img -eq 1 ]; then
    cmds="sudo dd if=${img} of=${rdisk} bs=1m"
else
    cmds="sudo dd if=${iso} of=${rdisk} bs=1m"
fi
echo ""
echo "*** About to run dd DESTRUCTIVE COMMAND AS FOLLOWS:"
echo "*** $cmds"
echo -n "*** PROCEED? [y] "
read answer
case "$answer" in
y|Y|"")
    echo "OK, running dd command, please wait (takes a while) ..."
    echo ""
    echo "####################################################################"
    echo "IF WARNING POPS UP THAT COMPUTER CAN'T READ DISK, HIT \"Ignore\"."
    echo "####################################################################"
    echo ""
    echo $cmds; $cmds
    echo "Done."
    ;;
n|N)
    echo "OK, not running dd command, bye."
    exit 0
    ;;
*)
    echo "** ERROR: uncrecognized option \"$answer\" - bye."
    exit 1;
    ;;
esac


echo "Ejecting USB flash drive: $disk, after which you can physically remove..."
cmds="diskutil eject $disk"
echo $cmds; $cmds
echo ""
echo "Done."
echo ""
echo "REMOVE USB flash drive: $disk."
echo ""
```

This worked for me on my MacBookPro to create bootable USB Flash drives for Ubuntu 14.04.3 LTS & Linx Mint MATE 17.2, and allowed to me to install both on my system so that I now have a functioning quadruple-boot Mac that runs:
1. Mavericks (OSX 10.9.x) (on SSD, first hard drive)
2. Linux Mint MATE 17.2 (on SSD, first hard drive)
3. Windows 7 (via Bootcamp on SSD, first hard drive)
4. Ubuntu 14.04.3 (on sATA, second hard drive)

I have no need for persistence, but I understand why others may need that.

OlafO

P.S. Off-topic, but it would be nice if the Ubuntu & Linux Mint developers would use the "nomodeset" instead of "quiet splash" kernel parameters as default, or at least determine that it's a Mac with nvidia video & use "nomodeset" - would save a lot of us Mac folks a LOT of headaches with having to manually edit this when booting install media, and then modifying /etc/default/grub and running update-grub after install. Just a thought.

---

### Post by sudodus on 2015-09-14
Welcome to the Ubuntu Forums *OlafO*, and thanks for sharing this method, that works for you :-)

I read your post and the script (but I did not read or test the script in any great detail). It seems to do the same thing (copy/clone/flash with ***dd***) as the tool [mkusb](https://help.ubuntu.com/community/mkusb), that I have developed. There might be some differences that are critical for Mac computers, but it might be worthwhile for you to try mkusb. (I have no Mac computer.)

-o-

The developers, who decide about things like which boot options to supply as default, seldom read these forums. But some of us here can try to reach them once in a while. For example, the intention of this thread is to collect information, that can be useful when we approach the forums that can decide about changing the tool to create USB boot drives.

If you have not yet voted in [the poll about this issue](http://ubuntuforums.org/showthread.php?t=2291946), please do now :-)

---

### Post by sudodus on 2015-09-20
A dialogue at the ubuntu-quality mailing list is continuing and improving.
 
Now what do you think of this idea: [to make the Ubuntu Startup Disk Creator reliable by removing its ability to create persistent live drives?](http://ubuntuforums.org/showthread.php?t=2291946&page=3&p=13359278#post13359278)

---

