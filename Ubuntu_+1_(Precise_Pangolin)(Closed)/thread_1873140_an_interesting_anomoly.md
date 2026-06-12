---
title: "an interesting anomoly"
date: 2011-10-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ronacc on 2011-10-31
this isn't strictly a precise problem or even an ubuntu only one . Ever since built my test box back during gutsy , when I shutdown the system would shutdown but the box would not turn off and had to be shutdown with the power button . this happened no mater what distro I was running and there have been dozens + every version of ubuntu from gutsy on from the start of dev through release , to keep the story short I thought it was a mobo problem until the other day I installed the dev preview of windows 8 to have a peak at what the enemy is doing and when I shut it down the box turns off just like it should . The mobo is a gigabyte m55plus-s3g . Does anyone have any ideas ?

---

### Post by cariboo on 2011-10-31
Check the power saving settings in the BIOS, I have a couple of P4s I was given, and one won't shutdown, no matter what OS was installed, I changed a power management setting in the BIOS, and now it shuts down running Xubuntu, I haven't tried anything else on it yet.

---

### Post by dino99 on 2011-11-01
report about that issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

---

### Post by ronacc on 2011-11-01
thanks cariboo907 I tried changing any bios setting that looked like it might help but no luck .

@ dino99 thanks for pointing me at that bug , That is not my problem though . for me it is any linux distro not just Ubuntu or even debian , it also exists on rpm based and gentoo based and also 64 or 32 bit and installed or live cd .

---

### Post by dino99 on 2011-11-01
> **ronacc said:**
> 
@ dino99 thanks for pointing me at that bug , That is not my problem though . for me it is any linux distro not just Ubuntu or even debian , it also exists on rpm based and gentoo based and also 64 or 32 bit and installed or live cd .

this report is against the kernel

---

### Post by ronacc on 2011-11-01
I read through the comments on the bug and I don't think that is my problem and I don't want to give them confusing data , all the comments seem to point at late releases and mine dates back 4 years , also they seem to be having real hangs , I am not , the system shuts down normaly all the way to powerdown , it  is just that power to the box does not shut off , also reboots are normal wheater from menu , term or alt>sysreq>b .

edit:  also the problem does not happen on my other 3 desktops ,my netbook or my laptop .

---

### Post by matt_symes on 2011-11-01
Total stab in the dark.....

Windows 8 fixed an issue with the Windows acpi driver ? asl complied using the windows compilier ? buggy aml ?

Have you installed Windows on this PC in the past or is Windows 8 the first time tyou have installed Windows ?

---

### Post by ronacc on 2011-11-01
I never use windows , I just installed the win 8 dev preview to see what MS is up to , and yes I had considered it to be either a hardware problem or an acpi one so the info you just gave points me more tword a buggy acpi . I'll google around and see if this mobo is known for that .

---

### Post by matt_symes on 2011-11-01
You could recompile the dsdt using intels compiler and see what errors it throws out.

---

### Post by effenberg0x0 on 2011-11-01
Hey, I have some notes about workarounds I used for this exact same problem in my old Dell laptop. I thought maybe you could give it a try if you haven't yet tried the same fixes. 

Make sure you really don't have acpi/apm/s3 options in the BIOS you can play with first.

```

sudo nano /etc/default/halt
```Make sure you have only:
```
HALT = poweroff
``````
sudo gedit /etc/modules
apm power_off=1
```Add the following switches to the end of the GRUB_CMDLINE_LINUX_DEFAULT="" line at /etc/default/grub at sudo gedit /etc/default/grub```

GRUB_CMDLINE_LINUX_DEFAULT="WhatEverYouPreviouslyHadHere acpi=force apm=power_off"

```Then sudo update-grub, Reboot and test

If above fail, you can go sysrq (see that we're syncing first, so no harm done)
```
sudo gedit /etc/init.d/halt
```Comment out the following halt line: 
```
# halt -d -f $netdown $poweroff $hddown"
```Add these lines instead:
```
echo s > /proc/sysrq-trigger
sleep 2
echo o > /proc/sysrq-trigger
```

---

### Post by effenberg0x0 on 2011-11-01
As far as I know, Windows **always** forces acpi G2/G3 state and apm 0x07 off, even when it's buggy or unsupported. It disregards unknown / non-existent reply from BIOS.

---

### Post by matt_symes on 2011-11-01
> **effenberg0x0 said:**
> As far as I know, Windows **always** forces acpi G2/G3 state and apm 0x07 off, even when it's buggy or unsupported. It disregards unknown / non-existent reply from BIOS.

That's interesting. Thanks for this info.

---

### Post by ventrical on 2011-11-01
> **ronacc said:**
> I never use windows , I just installed the win 8 dev preview to see what MS is up to , and yes I had considered it to be either a hardware problem or an acpi one so the info you just gave points me more tword a buggy acpi . I'll google around and see if this mobo is known for that .

There is a linux driver for that mobo:

[http://ee.gigabyte.com/products/page/mb/ga-m55plus-s3g_10/](http://ee.gigabyte.com/products/page/mb/ga-m55plus-s3g_10/)

 and also I noticed that the BIOS has Q-Flash and Iv'e had to update a few BIOSes.
 I tend to agree with Caribou .. it is defintley an obscure powersetting in BIOS.. I have a lot of PCs that have the same behaviour .. won't shut off power.. usually older PCs like HPs.&Compaqs.

---

### Post by effenberg0x0 on 2011-11-01
> **ventrical said:**
> There is a linux driver for that mobo:

[http://ee.gigabyte.com/products/page/mb/ga-m55plus-s3g_10/](http://ee.gigabyte.com/products/page/mb/ga-m55plus-s3g_10/)

 and also I noticed that the BISO has Q-Flash and Iv'e had to update a few BIOSes.
 I tend to agree with Caribou .. it is defintley an obscure powersetting in BIOS.. I have a lot of PCs that have the same behaviour .. won't shut off power.. usually older PCs like HPs.&Compaqs.

Add Dell to the list of BIOSes that hide most of the stuff... 
I just had a quick look at GA-M55 manual, it has a Advanced Power Management menu in the BIOS, which is something to check. I believe acpi=force switch will work, since the motherboard specs does mention supporting acpi specs.

---

### Post by ronacc on 2011-11-01
thanks for all the suggestions and info everyone . by googling I found a bunch about editing the dsdt for gigabyte mobos used on osx but nothing specific to linux . 
 
@ effenberg0x0 where would I put that acpi=force switch ? in the boot line ? I'll give that a try , I already tried changing the APM settings one at a time with no help .

---

### Post by mc4man on 2011-11-01
There is a long standing thread on dsdt in the tips forum, but the most relevant to you may be an update edit
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)
> UPDATE: The kernel dev's will no longer use the patch to enable custom DSDT files for Karmic 9.10 and beyond. Jaunty 9.04 is the last version this will work on. You are urged to file a bug report for DSDT errors.

---

### Post by matt_symes on 2011-11-01
> **mc4man said:**
> There is a long standing thread on dsdt in the tips forum, but the most relevant to you may be an update edit
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

Yes. I think you're expected to recompile the kernel with a custom dsdt nowadays. Not good every time you want a new kernel update.

I mentioned it more as the potential problem than the solution.

I read somewhere they removed the dsdt patch because they wanted to fix the dsdt issues at source using quirks i assume.

I have no idea how sucessful they have been though :-\"

---

### Post by effenberg0x0 on 2011-11-01
> **ronacc said:**
> thanks for all the suggestions and info everyone . by googling I found a bunch about editing the dsdt for gigabyte mobos used on osx but nothing specific to linux . 
 
@ effenberg0x0 where would I put that acpi=force switch ? in the boot line ? I'll give that a try , I already tried changing the APM settings one at a time with no help .

I'm sorry, I really wasn't clear in my post. 
You should add those commands to the GRUB_CMDLINE_LINUX_DEFAULT line. I edited the original post #10.

---

### Post by ronacc on 2011-11-01
thanks

---

### Post by ronacc on 2011-11-01
@ effenberg0x0 I applied all the fixes in your post # 10 , sadly they did not do the trick . thanks for all the help I'll just keep pushing the power button to shut the box off after the system halts , I've been doing that for 4 years and havent worn out my finger yet :lolflag:

---

### Post by ventrical on 2011-11-01
> **ronacc said:**
> @ effenberg0x0 I applied all the fixes in your post # 10 , sadly they did not do the trick . thanks for all the help I'll just keep pushing the power button to shut the box off after the system halts , I've been doing that for 4 years and havent worn out my finger yet :lolflag:

Here is how I have my Power management setup:

ACPI Suspend Type [S3(STR)]
Soft-Off by Power_BTTN [OFF]
System After AC Back [OFf]
IRQ [3-7,9-15],NMI [Enabled]
Modem Ring on [dis]
PME Event Wake up [dis]
Power on Keyboard [dis]
Power on Mouse [dis]
Resume by alalrm [dis]
Power Led in S1 State [blinking]


not sure if it will help.

---

### Post by effenberg0x0 on 2011-11-01
> **ronacc said:**
> @ effenberg0x0 I applied all the fixes in your post # 10 , sadly they did not do the trick . thanks for all the help I'll just keep pushing the power button to shut the box off after the system halts , I've been doing that for 4 years and havent worn out my finger yet :lolflag:
Man, I've never seen a hardware resist sysrq! I can only imagine that /etc/init.d/halt is not being invoked? Just so I can let it go, can you do some more small tests, just out of curiosity?

- The results of **ls -lhag /etc/init.d/halt**.  Is it owned by root:root and set to rwxr-xr-x (755)? 
- What happens as you invoke **sudo /sbin/shutdown -P now** ?
- About sysrq: **cat /proc/sys/kernel/sysrq** is 1?
- Still sysrq: Pressing **Alt+PrintScreen+<letter> in this order:r,e,i,s,u,o** doesnt work? Just hold ALt+Printscreen down and press the letters one by one. Save your work first, of course.

**EDIT: **In some laptop keyboards you must hold the "fn" key to be able to use printscreen, so it would be Alt+fn+PrintScreen + each letter.

---

### Post by ronacc on 2011-11-01
@ ventrical that is the way my apm is set except for the IRQ line that is not in the apm module of my bios .

@ effenberg0x0 glad to run any tests you can think of , at least up to the point of using a hammer to shut it down . Its a test box so I'm not worried about losing anything .

the cmds  ```
ron@ron-desktop2:~$  ls -lhag /etc/init.d/halt
-rwxr-xr-x 1 root 1.4K Nov  1 19:32 /etc/init.d/halt
ron@ron-desktop2:~$ 

ron@ron-desktop2:~$ cat /proc/sys/kernel/sysrq
1
```

I have removed quiet splash from my boot line so I see the console through startup and shutdown .
sudo shutdown-p now  ---- the system shuts down but does not poweroff the last line on the console is    power off

alt>sysreq?r e i s u o  same result except the last line is acpi power off

additional info on all shut downs from linux it appears that the mobo stays active to a point ,fans reduce speed but do not stop and power light remains on and video card continues to output the last lines ( or splash screen ) to the monitor until the box is powered down with the switch .

---

### Post by effenberg0x0 on 2011-11-01
> **ronacc said:**
> @ ventrical that is the way my apm is set except for the IRQ line that is not in the apm module of my bios .

@ effenberg0x0 glad to run any tests you can think of , at least up to the point of using a hammer to shut it down . Its a test box so I'm not worried about losing anything .

the cmds  ```
ron@ron-desktop2:~$  ls -lhag /etc/init.d/halt
-rwxr-xr-x 1 root 1.4K Nov  1 19:32 /etc/init.d/halt
ron@ron-desktop2:~$ 

ron@ron-desktop2:~$ cat /proc/sys/kernel/sysrq
1
```I have removed quiet splash from my boot line so I see the console through startup and shutdown .
sudo shutdown-p now  ---- the system shuts down but does not poweroff the last line on the console is    power off

alt>sysreq?r e i s u o  same result except the last line is acpi power off

additional info on all shut downs from linux it appears that the mobo stays active to a point ,fans reduce speed but do not stop and power light remains on and video card continues to output the last lines ( or splash screen ) to the monitor until the box is powered down with the switch .

I could find some reports on the net indicating that the BIOS upgrade is necessary in order to solve some issues with memory on this MB. I'm not sure how it relates, but people report that, without the upgrade, the BIOS reports wrong memory speeds and, in some cases, installing Windows XP and some distros was impossible. I also read a report in which a user managed to make the mobo work by reducing memory speeds in BIOS. There definitely is something wrong with the BIOS version... I'd go for the upgrade.

**EDIT: **Aparently some users also see an ACPI error message on boot when they run dmesg | grep -i acpi. Could be a lead if true.

---

### Post by ronacc on 2011-11-02
sorry I took awhile to get back to you , my last post was just before I shutdown for the night . I also checked the gigabyte site for bios upgrades and there are 15 since my version so that could be it , I would have tried that years ago but this box hasn't got a floppy to flash the bios with , I build my own boxes and haven't installed a floppy in one since the late 90's . I have thought about trying it with a cd but would rather not end up with a door stop .

the only thing interesting I found when I ran dmesg | grep -i acpi  right after boot this morning was "[    0.600169] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found."

---

### Post by ventrical on 2011-11-02
> **effenberg0x0 said:**
> I could find some reports on the net indicating that the BIOS upgrade is necessary in order to solve some issues with memory on this MB. I'm not sure how it relates, but people report that, without the upgrade, the BIOS reports wrong memory speeds and, in some cases, installing Windows XP and some distros was impossible. I also read a report in which a user managed to make the mobo work by reducing memory speeds in BIOS. There definitely is something wrong with the BIOS version... I'd go for the upgrade.

**EDIT: **Aparently some users also see an ACPI error message on boot when they run dmesg | grep -i acpi. Could be a lead if true.


Thats what I did with my GB mobo about 6 months ago.

Q-Flash.

@ronac - yep need floppy.

---

### Post by effenberg0x0 on 2011-11-02
> **ventrical said:**
> Thats what I did with my GB mobo about 6 months ago.

Q-Flash.

@ronac - yep need floppy.

@ronapp @ventrical

My MB (ASUS) sees the BIOS upgrade file when it's placed in a USB drive formated as FAT and connected before power-on. Is it not an option with this Gigabyte?

Another attempt is to update the BIOS with a hot system, running proper software. Many MB brands have win32 software to do that. Download the software, download the BIOS Update, run and reboot. I'm not sure, but maybe this Gigabyte software allows for that?
[http://www.gigabyte.com/MicroSite/121/tech_a_bios.htm](http://www.gigabyte.com/MicroSite/121/tech_a_bios.htm)

EDIT: I just had a quick look on the software PDF, it says it can manage any Gigabyte product, so, it should work for the BIOS update there.

---

### Post by ventrical on 2011-11-02
> **effenberg0x0 said:**
> @ronapp @ventrical

My MB (ASUS) sees the BIOS upgrade file when it's placed in a USB drive formated as FAT and connected before power-on. Is it not an option with this Gigabyte?

Another attempt is to update the BIOS with a hot system, running proper software. Many MB brands have win32 software to do that. Download the software, download the BIOS Update, run and reboot. I'm not sure, but maybe this Gigabyte software allows for that?
[http://www.gigabyte.com/MicroSite/121/tech_a_bios.htm](http://www.gigabyte.com/MicroSite/121/tech_a_bios.htm)

EDIT: I just had a quick look on the software PDF, it says it can manage any Gigabyte product, so, it should work for the BIOS update there.

Yes .. your right .. I remember that but did not choose that option.

@ ronac ...

 If it is any help I have my Frequency/Voltage Control/Linear Frequency Control set to (disabled). My GigaByte mobo has the 2004 Award BIOS.

  It is a 2.20GHz Intel P4 and I can run Miint 11LDXE, Oneiric and most other (ubuntus).


***EDIT***

@effeenberg

 The q-flash has the WINBOND option which  (I assume) can only be run from a floppy (at least with my system).

  I don't recall. at the moment exactly what it is.

---

### Post by ventrical on 2011-11-02
Heres a pic of my q-flash on the GB mobo.

[http://www.youtube.com/watch?v=fR7kLfxgEMc](http://www.youtube.com/watch?v=fR7kLfxgEMc)

---

### Post by ronacc on 2011-11-02
after digging around in my drawer of forgotten parts I came up with a floppy drive and a floppy disk that had escaped the burn barrel and after an hour more of desperate searching came up with a cable for the drive so I'll try a bios flash tomorrow .

---

### Post by effenberg0x0 on 2011-11-02
> **ventrical said:**
> 
@effeenberg

 The q-flash has the WINBOND option which  (I assume) can only be run from a floppy (at least with my system).

  I don't recall. at the moment exactly what it is.

Not sure. Winbond is, as far as I know, a manufacturer of IC, uControllers, PLL, Flash, etc. But since most modern BIOSes provide support for USB ports (for booting from external drives, using USB keyboard, etc) it should be possible to load the BIOS from USB, as long as the embedded BIOS update program has been coded to look for BIOS files at such USB units. It may very well have not been designed to do so, despite the technical capability. But, anyway, the Win32 program I mentioned sounds promissing, if ronacc happen to have a win32 partition. I was looking, this motherboard has *many* BIOS updates... I wonder what went wrong.

---

### Post by ventrical on 2011-11-03
> **effenberg0x0 said:**
> Not sure. Winbond is, as far as I know, a manufacturer of IC, uControllers, PLL, Flash, etc. But since most modern BIOSes provide support for USB ports (for booting from external drives, using USB keyboard, etc) it should be possible to load the BIOS from USB, as long as the embedded BIOS update program has been coded to look for BIOS files at such USB units. It may very well have not been designed to do so, despite the technical capability. But, anyway, the Win32 program I mentioned sounds promissing, if ronacc happen to have a win32 partition. I was looking, this motherboard has *many* BIOS updates... I wonder what went wrong.

Looks like he found a floppy. :)

---

### Post by ventrical on 2011-11-03
> **ronacc said:**
> after digging around in my drawer of forgotten parts I came up with a floppy drive and a floppy disk that had escaped the burn barrel and after an hour more of desperate searching came up with a cable for the drive so I'll try a bios flash tomorrow .


Good luck . take your time.  It wokred here great 6 months ago.

---

### Post by cariboo on 2011-11-03
The last time I looked, many manufacturers, had a floppy image for updating the bios, the last time I had to do I bios update, I burned the floppy image to a CD, and updated it using the the CD. It's a bit of a waste of a CD, but certainly better than using a dodgy floppy drive, or buying a new one.

---

### Post by ronacc on 2011-11-03
I had thought about a cd but wasn't sure it would work , after I extract the zip I'll look at the autoexec.bat file and try to figgure out if I can use a cd .

---

### Post by ronacc on 2011-11-07
just an update to say thanks to all who offered suggestions and help . When I finally managed to get my bios flashed , that corrected the problem . It took a few days because the 2 floppies I had were bad , both linux and windows 8 would see the drive but not read the disk and neither my local wal-mart or office supply store still carries floppies , I had to go to a store over 30 miles away to find any . I did try from a cd but that didn't work , atleast it didn't brick the box . once I got some useable floppies things went smoothly .

---

### Post by ventrical on 2011-11-07
> **ronacc said:**
> just an update to say thanks to all who offered suggestions and help . When I finally managed to get my bios flashed , that corrected the problem . It took a few days because the 2 floppies I had were bad , both linux and windows 8 would see the drive but not read the disk and neither my local wal-mart or office supply store still carries floppies , I had to go to a store over 30 miles away to find any . I did try from a cd but that didn't work , atleast it didn't brick the box . once I got some useable floppies things went smoothly .


 Great to hear !! I always keep floppies on hand .. we never know when we need to go back to the future. :) One of my best IT tools is a Sony USB floppy drive. Using that and PLOP I can get into practically any PC.

---

### Post by effenberg0x0 on 2011-11-07
> **ventrical said:**
> Great to hear !! I always keep floppies on hand .. we never know when we need to go back to the future. :) One of my best IT tools is a Sony USB floppy drive. Using that and PLOP I can get into practically any PC.

I'm looking for one, they are not easy to find here. I have found a scsi zip drive in my drawer a couple days ago lol...Congrats on making it work ronacc!

---

### Post by ventrical on 2011-11-08
> **effenberg0x0 said:**
> I'm looking for one, they are not easy to find here. I have found a scsi zip drive in my drawer a couple days ago lol...Congrats on making it work ronacc!

Sorry to be off topic but my Sony Vaio 3.5" USB floppy is one of my prize hardware  tools (relics).  It was one of those things where I was at the right place at the right time. With the Ubuntu distros and other Linux distros it has proved itself to be worth it's weight in gold, especially any mobos pre 1999. It's a laptop lifesaver.

 Sony PCGA-UFD5

*got the scsi zip drive too.. but it's not the same as a USB :) ie;  I can get a lot older PCs to run puppy or DSL  linix off of a  2GB pendrive using the USB drive with the PLOP loader.. etc..

---

