---
title: "How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)"
date: 2011-10-22
forum: Tutorials
---

### Post by Pay87 on 2011-10-22
The information in this thread has been moved to [https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062090#post12062090](http://ubuntuforums.org/showthread.php?p=12062090#post12062090)

Thread closed.



**Contents:**
1. ..Introduction
2. ..Installation
3. ..Tweaks and Fixes
3.1 ...Fix "Fn brightness keys"
3.2 ...Fix battery drain
3.3 ...Update BIOS without windows

**1. Introduction:**
Lenovo's EFI implantation seems to be not perfect on some newer Lenovo notebooks. After successfully installing Ubuntu the notebook is not able to load the bootloader by default. It seems to be a problem with GPT partition tables and non windows bootloaders.
It took me a hole day to figure out, how to get Ubuntu still working.

So lets start getting Ubuntu on your Lenovo! ;)

UPDATE: evil_hog found out how to install Ubuntu with GPT partition table! Here now the updated guide.
(tested on S205, B570)

**2. Installation**

**Installation - Step 1 - Booting up a Live CD of your favorite Ubuntu:**
Simply boot from your Live CD or a USB Stick.
I prefer the USB Stick because everything will go faster.

**Installation - Step 2 (optional) - Fixing WLAN temporary for the live session:**
Once the system is loaded I was trying to fix my WLAN connection because Ubuntu was not able to start it by default.
Be sure that your hardware switch (if any) is activated.

The following commands will make it possible that your wlan adapter will work temporary on your live session, but since we have no acer wlan adapter the connection can get unstable, especially on N networks.

We will fix the wlan adapter after the installation, this workaround is still useful if you want to access a wifi network over a live session quickly.

Open a terminal and type in the following:
```

sudo modprobe acer_wmi
#Be sure your WLAN is activated by the hardware keys
sudo modprobe -r acer_wmi

```

Your WLAN adapter should now be ready to connect :)

**Installation - Step 3 - Installing Ubuntu with GPT partition table**
Launch the Ubuntu installer.
You can let the installer load updates during the installation if you are connected to the internet.

When it comes to the partition you have to use the "manual mode" so that you can select the partition layout. Don't use any predefined partition layouts.

The first partition has to be the EFI partition, it will be formatted as fat16 afterwards.
I gave the EFI partition 50 MB.

Then I created a ext4 partition for "/" and a swap partition.

That's all! No need to downgrade grub anymore.. :-) 

**Installation - Step 4 - Lets permanently fix the WLAN**
After we booted into our installed Ubuntu system, it is time to fix the WLAN the right way.

There are restricted drivers available for most of our wlan adapters.
So we can install them with the restricted driver installer.

Check after a reboot if you are able to connect.
If you still cannot connect you might have to blacklist some modules.

```
lsmod | grep "b43\|ssb\|bcma\|wl"
```

Your output should be something like this:
```

wl                   2568210  0 
lib80211               14991  2 lib80211_crypt_tkip,wl

```

If b43, ssb, bcma is loaded you have to blacklist them in:
> /etc/modprobe.d/blacklist.conf

I also had to blacklist acer_wmi in order to get network-manager working.

After editing the file, save it and reboot.
You should finally see the wireless networks.

When you come to the point that you still cannot connect, try wicd as network manager:

```
sudo apt-get install wicd && sudo apt-get remove network-manager*
```

After a reboot you should see the wicd icon in the panel and the available wireless networks.

Enjoy Ubuntu on your Lenovo! :popcorn:

**3. Tweaks and Fixes**

**3.1 Fix "Fn brightness keys"**
After successfully installing Ubuntu you might come to the point that your "Fn brightness keys" are not working.
I found a simple solution using "xbacklight" for it.

Be sure xbacklight is installed:
```

sudo apt-get install xbacklight

```

Now you can start a terminal window and type in:
```

xbacklight - 20

```
Your screen should dim by 20%.

If you want to make it brighter again just type:
```

xbacklight + 20

```

This way you can easily change your brightness through the terminal.
If you want to use your hardware "Fn" keys simply set the xbacklight commands as hotkeys in the keyboard settings.

**3.2 Fix battery drain (tested on Intel Sandy Bridge systems like B570)**
When you switch from Windows based systems you might detect a faster battery drain on your Linux system.
The problem is that some kernel parameters are disabled by default which put the VGA into a energy saving mode.
Some people had random system freezes with this great Sandy Bridge feature enabled, however there are a lot of people like me who don't have problems at all. I will recommend you the tweaks which fixed the main battery drain for me.

You have to add the following boot parameters to the grub2 configuration section GRUB_CMDLINE_LINUX_DEFAULT located here /boot/grub/grub.cfg:

1.) Activates the RC6 mode of the Intel GPU
```

i915.i915_enable_rc6=1

```

2.) Activates PCIe Active State Power Management
```

pcie_aspm=force

```

Don't forget to:
```
sudo update-grub
```

**TLP:**

If you don't use the "laptop-mode-tools" package or other energy scripts, you can also have a look on TLP.
TLP will extend the energy modes on your laptop and power save features.

There is a PPA available for TLP:
[https://launchpad.net/~linrunner/+archive/tlp/+packages](https://launchpad.net/~linrunner/+archive/tlp/+packages)
**(external repos can damage the system - be aware)**

```

sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update

```

Now you can install TLP and some usefull tools:

smartmontools (main) - show SMART data with tlp-stat.
ethtool (main) - allows to disable Wake On LAN
powertop (main) - helps monitoring power consumption

```

sudo apt-get install --no-install-recommends tlp smartmontools ethtool powertop

```

**3.3 Update BIOS without windows**
There was a new BIOS available for my Lenovo B570 and I wanted to update it. Lenovo only provides the WinFlash tool to do the updates directly in Windows, but I found a workaround to do it with a bootable USB Stick.

Step 1: Download your BIOS on the [Lenovo Consumer site]("http://consumersupport.lenovo.com").

Step 2: Open the *.exe file with your archive manager and extract the containing *.zip file.
In my case inside the 44CN43WW.exe update file, was the 44CN43WW.zip.
Extract now the content of the *.zip to a folder e.g. "lenovo-bios".

Step 3: Now build yourself a bootable USB stick with FreeDos. I used the image of the Ultimate BootCD as source for my USB Stick because FreeDos is already built in.
Copy the extracted "lenovo-bios" folder to the usb stick.
Now boot into FreeDos.

Step 4: cd into your "lenovo-"bios" folder.
Before running the update be sure that your battery is full or better you are on A/C.

To start the update we need to run Pflash.exe with the BIOS filename, which is the *.rom file.
E.g.: Pflash.exe 44CN43WW.ROM

Step 5: After flashing the image do a reboot. If the tool is not able to reboot your Lenovo you might have to hold the power button for 10sek. to shut it down manually. Do this only when the flashing process finished succesfully!

Step 6: Go into the bios and load the default settings, to clear the CMOS. Save and Reboot.

Sources:
WLAN Fix: [http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/](http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/)
TLP (German): [http://thinkpad-wiki.org/TLP_-_Linux_Stromsparen](http://thinkpad-wiki.org/TLP_-_Linux_Stromsparen)

---

### Post by nitroguy on 2011-11-07
Thank you kindly for this wonderful guide! I am having troubles with my new S205, perhaps you can help me. I followed your instructions (and many others i have pieced together to the same effect) but they all have a similar error.

once I edit the partitions, get it all set up, and run the installer it begins copying files. it says 'Almost finished copying files' and then does one of two things. A) crashes the installer, leaving behind a blank desktop with buttons that are unreactive, or B) gives 'Errno 5' that talks about my install CD being scratched (not possible given my USB stick). yes, I've run the check disk option at liveCD boot, and it says my install disk is just fine. 

do you have any advice for me? I want to love Ubuntu, but am having a hard time doing so with an unbootable computer.

additional details:

I previously had a working install of Ubuntu 11.10 on this very computer. no idea how I did it, but booting from mg USB stick, replaced widows and it just worked. I attemped to reinstall ubuntu to fix some wireless woes, but ended up in this predicament. so I know it is possible, I just don't know the magic combo.

I can successfully install windows to the computer, as I have done it, twice. both times in an effort to replicate the magical time that it worked, but to no avail.

any help is not only appreciated, but will earn you my gratitude for life. :-) 

thanks.

---

### Post by Pay87 on 2011-11-07
> **nitroguy said:**
> Thank you kindly for this wonderful guide! I am having troubles with my new S205, perhaps you can help me. I followed your instructions (and many others i have pieced together to the same effect) but they all have a similar error.

once I edit the partitions, get it all set up, and run the installer it begins copying files. it says 'Almost finished copying files' and then does one of two things. A) crashes the installer, leaving behind a blank desktop with buttons that are unreactive, or B) gives 'Errno 5' that talks about my install CD being scratched (not possible given my USB stick). yes, I've run the check disk option at liveCD boot, and it says my install disk is just fine. 

do you have any advice for me? I want to love Ubuntu, but am having a hard time doing so with an unbootable computer.

additional details:

I previously had a working install of Ubuntu 11.10 on this very computer. no idea how I did it, but booting from mg USB stick, replaced widows and it just worked. I attemped to reinstall ubuntu to fix some wireless woes, but ended up in this predicament. so I know it is possible, I just don't know the magic combo.

I can successfully install windows to the computer, as I have done it, twice. both times in an effort to replicate the magical time that it worked, but to no avail.

any help is not only appreciated, but will earn you my gratitude for life. :-) 

thanks.

How did you create the "LiveStick" ?
I prefer UnetBootin. Also did you try reloading the iso from the server?
Btw can you checksum your downloaded file?

---

### Post by nitroguy on 2011-11-07
Wow, thanks for the quick reply! 

I created my "liveStick" using my other Ubuntu laptop and the "Startup Disk Creator" utility. I downloaded the iso fresh off the ubuntu.com website - it doesn't even ask me to "Update this Installer" when I run the installer from the Live Desktop. (as it sometimes does when I don't use the latest iso, or when I used Windows to create my USB stick).

I do apologize, you'll have to break it down a bit for me, how do I do a checksum? I'm eager to learn, but don't quite know all the ins-and-outs of Ubuntu just yet.

Also, when Googling what Errno 5 is, it seems it is possibly related to a bad hard drive sector. I feel that is a bit hard to believe (it's a *Brand New* laptop, but I suppose anything's possible. I'll run a quick hard drive sector check (googling how to do that now...) and post back the results.

Thanks! I do hope to get to the bottom of this!

---

### Post by Pay87 on 2011-11-08
> **nitroguy said:**
> Wow, thanks for the quick reply! 

I created my "liveStick" using my other Ubuntu laptop and the "Startup Disk Creator" utility. I downloaded the iso fresh off the ubuntu.com website - it doesn't even ask me to "Update this Installer" when I run the installer from the Live Desktop. (as it sometimes does when I don't use the latest iso, or when I used Windows to create my USB stick).

I do apologize, you'll have to break it down a bit for me, how do I do a checksum? I'm eager to learn, but don't quite know all the ins-and-outs of Ubuntu just yet.

Also, when Googling what Errno 5 is, it seems it is possibly related to a bad hard drive sector. I feel that is a bit hard to believe (it's a *Brand New* laptop, but I suppose anything's possible. I'll run a quick hard drive sector check (googling how to do that now...) and post back the results.

Thanks! I do hope to get to the bottom of this!

You could try to check your hdd for bad sectors (takes some hours) or maybe your usb stick has bad sectors.
If you have a optical drive, try burning the ISO to a CD and use this instead. At this point I don't really think this is Lenovo related. ;)

Here is a link how to check the md5 checksum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by moteprime on 2011-11-10
Hi Pay87
A bit off topic, but I'm curious. Are your wlan operating at full speed? There's a bunch of people that has a really hard time making it work.

---

### Post by ivanmmj on 2011-11-14
I followed this guide and it worked out great. I have kubuntu booting smoothly. I didn't even have to play around with the brightness controls as they worked out of the box. My question is this:
What type of issues would I have had if I had tried to boot with grub2?

Also, have you tried using Burg as a bootloader? It might be better with uefi than grub2, even though it's based off of grub2. I would love to get rid of the ugly grub screen. With grub2, you can at least run it at a higher res mode.

As a side note, I also got Chromium OS booting alongside Kubuntu (installed in the harddrive and booting from grub.) Unfortunately, there is currently a bug in it that causes it to not see the battery life and thus it only works while on AC power.

---

### Post by ivanmmj on 2011-11-14
Update: I installed Burg and I have it working fine. I haven't had any issues, yet. I've even themed it to match my current theme for plymouth, KDM, and KDE's Plasma (and icons).

---

### Post by moteprime on 2011-11-15
I am using Grub 2, in dual boot with win7. It works fine, and looks better during boot up and shutvdown.

---

### Post by Pay87 on 2011-11-15
Thanks for the information. Since I had a lot of troubles with grub2, I explain how to use grub instead. Of course everyone can try after successfully installing the system to boot with grub2.

I added some energy tweaks in the tutorial, because I had terrible battery drain without it on my Lenovo.

---

### Post by Pay87 on 2011-11-15
> **moteprime said:**
> Hi Pay87
A bit off topic, but I'm curious. Are your wlan operating at full speed? There's a bunch of people that has a really hard time making it work.

I only use my WiFi for the internet connection and there it works fine. I can do a test on my local network later and post some results if I find something strange.. :)

---

### Post by v923z on 2011-11-15
Hi All,

From the original post, it is not clear to me, whether this is the 32-bit, or the 64-bit version. I am trying to install the 64-bit version, but I don't even get to the end of the installation process. For a while, everything seems to go fine, I can choose the log-on picture and so on, and after that, the screen becomes black, there is some CD activity from time to time, but nothing seems to happen. Any ideas as to what might be wrong, or what I should do differently?
Cheers,
Zoltán

---

### Post by Pay87 on 2011-11-15
> **v923z said:**
> Hi All,

From the original post, it is not clear to me, whether this is the 32-bit, or the 64-bit version. I am trying to install the 64-bit version, but I don't even get to the end of the installation process. For a while, everything seems to go fine, I can choose the log-on picture and so on, and after that, the screen becomes black, there is some CD activity from time to time, but nothing seems to happen. Any ideas as to what might be wrong, or what I should do differently?
Cheers,
Zoltán

Can you tell us on which installation point you get the black screen or is it always random? Which Lenovo do you have?
Guide tested on x64.

---

### Post by v923z on 2011-11-15
Sorry, I forgot to say that this all happens on a lenovo b570. I got past the black screen now, but at the end of the installation process, the only option I have is reboot. I cannot get into the system at this point.
Zoltán

---

### Post by ivanmmj on 2011-11-15
Here are a few more energy tweaks:
i915.lvds_downclock=1
i915.i915_enable_fbc=1
And the options you mentioned already. I'm actually using a kernel patched to properly work with aspm, so the force isn't necessary with this kernel. I'm hoping the patch will be officially pushed into Ubuntu's repo's soon.
I'm getting 3.5-4 hours of battery life in Kubuntu.

---

### Post by v923z on 2011-11-15
Well, this is really a Catch-22 now. I managed to get to the console, and then I tried to do everything written at the beginning of this post. But there are still problems. I could not chroot, because I got a 
```

chroot: failed to run command bin/bash no such file or directory

```
error. Then I decided to go ahead regardless, but then apt-get complained that it cannot read from the cdrom. So, I took the sources.list, and commented out the cdrom as a source. At this point, apt-get did not complain any more, but when I tried to install grub, it returned an error. And of course, the bootloader is not installed properly. Is there a way to choose the bootloader during the installation? It is really annoying that there is no "official" solution for such a fundamental problem. 
Cheers,
Zoltán

---

### Post by v923z on 2011-11-15
Well, I have finally managed to boot into ubuntu. I had to boot from the livecd first, and then remove grub2, and install grub from there. Before that I had to chroot, so that I could operate on the installed system. The steps detailed in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) were of great help. I also had to install boot-repair, but I could not use it. However, even if it did not run, iit made possible that I could produce the menu list for grub.
I hope the information here will be helpful to someone. 
Cheers,
Zoltán

---

### Post by vkmaheshbhat on 2011-11-16
Hi,
How did you get it to dual boot. I have installed win7 64 bit already and try how I may, can't get Linux to boot. It always goes directly to Windows bootloader. Please help me out with step-by-step instructions on what you did to get it to dual boot.
Thanks a lot in advance.
Cheers,
Mahesh
P.S.: I am quite desperate as to what to do. Please help me!

---

### Post by moteprime on 2011-11-16
vkmaheshbhat
Are you installing 11.10 64-bit on a s205?

---

### Post by v923z on 2011-11-16
> **vkmaheshbhat said:**
> Hi,
How did you get it to dual boot. I have installed win7 64 bit already and try how I may, can't get Linux to boot. It always goes directly to Windows bootloader. Please help me out with step-by-step instructions on what you did to get it to dual boot.

I haven't yet got the dual boot up, but I am sure I can do that with some tweaking of the grub menu file. What I really wanted to have is linux, and that I have now. As I said in my previous post, you have to install linux from the disc, and if after the installation the bootloader is not set properly (i.e., your computer always ends up in windows) then you have to insert the CD again, but at this time, instead of installing ubuntu, you should choose the "Try ubuntu without installing" option. Once the computer boots from the CD, you can mount the system on the hard disc, chroot, and then remove grub2, and install grub instead. As I pointed out, you might have to install boot-repair, and run it (it returned with an error for me, but that didn't really matter). After that you can do something like grub install /dev/sda3 or something similar, wherever your linux is installed. Once you installed linux in grub, you have to generate the menu (grub-update), and then you can reboot. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) was really useful. You should read the section on how to remove grub2, and you should then be OK. 
Cheers,
Zoltán

---

### Post by vkmaheshbhat on 2011-11-16
@moteprime,
I am installing Ubuntu 11.10 on B570. Core i3-2330 (Sandy Bridge), 4GB RAM, 500GB HDD. I have the first 3 non-EFI partitions (roughly 100GB) each formatted into ntfs and the first of them has Win7 64 bit. I wish to install ubuntu on the remaining free space.

@Zoltán,
I will try your suggestions for sure and report back.

Thanks a lot both of you. moteprime, I am looking to see what you did exactly to get it to work.

Cheers,
Mahesh
P.S.: Do you guys think it will help if I move the /boot partition of Linux earlier, like the 3rd or 4th partition on the disk? I know it shouldn't matter in GPT, but just a thought.

---

### Post by moteprime on 2011-11-16
Hi.
As i se it the problem seems be be that the Lenovo guys make the Bios to look for a windows boot loader, when ubuntu installs the grub bootloader, the bios finds a backup windows loader instead of grub.
The second problem is that the Ubuntu installer detects a efi bios and installs a efi version of grub. We need Grub2 (grub-pc)
On this blog [http://helms-deep.cable.nu/~rwh/blog/?p=177]("http://helms-deep.cable.nu/~rwh/blog/?p=177") rwh writes about how to get dual boot working with 10.10 and grub legacy.
I wrote there as "mote" [http://helms-deep.cable.nu/~rwh/blog/?p=177&cpage=1#comment-26658]("http://helms-deep.cable.nu/~rwh/blog/?p=177&cpage=1#comment-26658") How to get Grub2 installed instead of grub legacy. 
I'm a bit busy now, and haven't time to write a guide before later tomorrow. (But I will do it, if anybody need it, no problem)
Follow the necessary steps 4, 5 as rwh describes and then use my steps instead of 6.
> I followed your, 4. and 5. But in step 6. instead of installing GRUB Legacy i installed GRUB-PC.
apt-get update
apt-get install grub-pc
Picking “/dev/sda6&#8243; in the GRUB installation menu, despite complaints and errors.
after that i booted win7 and in EasyBCD added a new entry with GRUB2.
Be very aware of the partition numbers!!
I wrote this a bit fast, so don't try it if you don't know what you are doing. I will make a proper guide later if anybody wants it.

---

### Post by vkmaheshbhat on 2011-11-16
Thanks a lot moteprime. Will try it now and post results here asap.

---

### Post by ivanmmj on 2011-11-16
I removed the GPT partitioning scheme all together in mine.

On another note: Does anyone else notice that the volume on this laptop is VERY low? (I'm not dual booting so I don't know if it's louder in Windows.) It seems to work fine through headsets.

---

### Post by ivanmmj on 2011-11-21
Has anyone had any issues with the wifi stalling when downloading something off bittorrent? Trying to download an Ubuntu ISO runs fine for a while then stalls the wifi. I have to turn off the wifi for a few seconds then turn it back on for it to work. Sometimes it can take up to a minute to reconnect.

---

### Post by moteprime on 2011-11-22
ivanmmj.
If you have a s205 or another computer with RT3090, then you might want to take a look here:
[http://ubuntuforums.org/showthread.php?t=1849602](http://ubuntuforums.org/showthread.php?t=1849602)
and here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659)

---

### Post by Pay87 on 2011-11-22
I updated the tutorial, to show how to update the Lenovo BIOS without windows using Pflash :P

Just tried it out and it worked without problems! :)

---

### Post by ivanmmj on 2011-11-23
> **Pay87 said:**
> I updated the tutorial, to show how to update the Lenovo BIOS without windows using Pflash :P

Just tried it out and it worked without problems! :)

Speaking of BIOS's, I'm thinking of trying:
[http://www.bios-mods.com/forum/Thread-Dupe-Lenovo-B570-1068A8U-Whitelist-Mod-Request](http://www.bios-mods.com/forum/Thread-Dupe-Lenovo-B570-1068A8U-Whitelist-Mod-Request)
extracting the bios from:
[http://dl.dropbox.com/u/45117524/bios-mods.com/44CN43WW_NWL_DOS_ByCamiloml.exe](http://dl.dropbox.com/u/45117524/bios-mods.com/44CN43WW_NWL_DOS_ByCamiloml.exe)
and switching out the wireless card with one that has better Linux support and that is more stable. While trying to download Kubuntu through bittorrent, I had to turn off my wifi and turn it back on around 50 times...

Anyone think it'd be safe to flash that?

EDIT: I forgot to add... I've got a Broadcom 4312 lying around. Anyone know if the situation would be any better with that?

---

### Post by Pay87 on 2011-11-23
> **ivanmmj said:**
> Speaking of BIOS's, I'm thinking of trying:
[http://www.bios-mods.com/forum/Thread-Dupe-Lenovo-B570-1068A8U-Whitelist-Mod-Request](http://www.bios-mods.com/forum/Thread-Dupe-Lenovo-B570-1068A8U-Whitelist-Mod-Request)
extracting the bios from:
[http://dl.dropbox.com/u/45117524/bios-mods.com/44CN43WW_NWL_DOS_ByCamiloml.exe](http://dl.dropbox.com/u/45117524/bios-mods.com/44CN43WW_NWL_DOS_ByCamiloml.exe)
and switching out the wireless card with one that has better Linux support and that is more stable. While trying to download Kubuntu through bittorrent, I had to turn off my wifi and turn it back on around 50 times...

Anyone think it'd be safe to flash that?

EDIT: I forgot to add... I've got a Broadcom 4312 lying around. Anyone know if the situation would be any better with that?

You can give it a try but might brick your laptop :)
I would only use official BIOS files.
Is it really that bad with wireless?
I have no probs at all with my B570..

Except fingerprint not working (yet).

---

### Post by ivanmmj on 2011-11-29
> **Pay87 said:**
> You can give it a try but might brick your laptop :)
I would only use official BIOS files.
Is it really that bad with wireless?
I have no probs at all with my B570..

Except fingerprint not working (yet).

My wireless just froze again while I was trying to sync the git sources for Android. (Used 16 simultaneous streams.) >.<

EDIT: Pay87, can you dd an img of your bios updating usb drive? (Don't forget to remove any personal files. :p )
I'm having issues making one. >.<

---

### Post by parovelb on 2011-12-01
> **Pay87 said:**
> **Contents:**
```

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1
sudo mount --bind /sys ./sys
sudo mount --bind /proc ./proc
sudo mount --bind /dev ./dev
sudo chroot .

#We are now in our fresh installed Ubuntu

sudo apt-get update
sudo apt-get install grub
sudo update-grub #say yes when generating menu.lst
sudo grub-install /dev/sda
sudo grub-install /dev/sda1
```



Hello!

I have a s205 and I would like to install the x64 version. I created the bootable usb key with pendrivelinux and later with unetbootin using winxp. The download, usb check and iso file are ok. 

Every time I have tried to install and after to boot from the disk, it ended in a infinite rebooting loop. Like there is no disk nor system to boot from. As I expect it could be grub2 and I decided to use this method.

My wlan is ok. I am stuck on step 5. My partition table is:
```
/dev/sda1/boot
/dev/sda5/linux-swap
/dev/sda6/
/dev/sda7/home

```

Executing the command 
```
sudo mount --bind /sys ./sys
```
gives me the error
```
mount: mount point ./sys does not exist
```

What should a beginner like me do next?

---

### Post by ivanmmj on 2011-12-04
You also have to mount /boot. I have a similar set up from yours and I had a similar issue.

---

### Post by evil_hog on 2011-12-08
After upgrading BIOS I managed to install and boot Kubuntu with fully automatic installation process in GPT on Lenovo Z570. I'm at work so I couldn't provide more accurate data for now. The installer split my 7650GB drive to the following partitions:

Yes, it's GPT!
1. 20mb fat16 (flagged as boot)
2. ~700GB ext4 (this is root partition)
3. 6GB (this is swap partition)

As I noted before, the system is able to boot. But I don't like default partitioning because filesystems starts from sector 34, so 4k alignment isn't respected. Also, I want to separate /home . So I installed gparted, wiped out all partitions and made new ones:
1. 20MB fat16 partition, marked as boot and started from sector 2048
2. 50GB ext4 root partition
3. 8GB linux-swap
4. about 640GB left for /home , which is ext4 either

In graphical installer I chose device /dev/sda to install GRUB. AFAIK installer downloaded grub-efi package via internet and installed it.

After reboot there was 'ubuntu' in uefi boot menu (i'm not sure, maybe it left from previous correct installation of kubuntu). But system doesn't boot, it just get skipped to next boot device in list. I tried to manualy select ubuntu or ATA HDD, but it didn't help.

The question is: what I did wrong? I have two opinions on it:
1. probably, I should have left bootable partition as is, started from 34 sector and adjust alignmnent of the following it partitions?
2. which device should i choose for grub installation? /dev/sda1 (which is bootable partition and marked as 'efi') or /dev/sda in GUI installer?


--Edited:
According to [this](http://ubuntuforums.org/showpost.php?p=11406511&postcount=5) post the EFI partition should have at least 100mb (maybe default installer made it 200mb instead of 20, as I mentioned before?) and GRUB should be installed into EFI partition. Is this accurate?

---

### Post by evil_hog on 2011-12-08
I managed to succesfully install Kubuntu x86_64 on Lenovo z570 on the GPT partition table using EFI. Will post details later

---

### Post by oldfred on 2011-12-08
Someone actually got UEFI to work.:)

Post this just to see what you have:

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

There are several bugs which may relate to your install.
UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by evil_hog on 2011-12-09
> **oldfred said:**
> Someone actually got UEFI to work.:)

Post this just to see what you have:

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

It was semi-automatic installation.

Step 1: prepare hardware.
[LIST]
[*]Z570 has buggy "BIOS" so you want to upgrade it at least to 1st November 2011 version (see the very 1st post for details)
[*]Prepare media (11.10 for semi-automatic install). I was using standard DVD with Kubuntu x86-64 (had some problems with apt on USB stick, probably damaged ISO or the drive itself)
[*]AFAIK the standard distributions doesn't include grub-efi, so you will need an internet connection, otherwise installed system wont boot.
[/LIST]

Step 2. Prepare installation.
(If you are happy with default partitioning and don't want to align filesystems to 4k sectors just press Install and let it use the whole drive. Skip next steps)
[LIST]
[*]Chose "Try Kubuntu" in installers prompt
[*]When system loads, open terminal (konsole) and update packages tree
```
sudo apt-get update
```
[*]Install gparted (ofcourse, if you don't mind calculating you could just use parted instead)
```
sudo apt-get install gparted
```
[*]Run gparted and prepare partitions
```
sudo gparted
```
I'm not planning to have dual boot, so in my case  I created new GPT table and added following partitions on it:
[LIST=1]
[*]200MB fat16, flagged as "boot" (even if you create fat32, installer is going to format it back to fat16)
[*]ext4 root partition
[*]swap partition
[*]ext4 for /home
[/LIST]
Now we have properly aligned partitions due to gparted.
[*]Quit parted and launch installer from your desktop
[*]Choose "Manual" in drive partitioning window and let the installer know which partitions you'd like to use. In my case:
[LIST=1]
[*]/dev/sda1: efi partition (IMPORTANT)
[*]/dev/sda2: root 
[*]/dev/sda3: swap
[*]/dev/sda4: /home
[/LIST]

Below this windows you'll see an option to choose target for GRUB. The default value should be the drive itself (like /dev/sda, not /dev/sda1 or something like this)
[*]I advice you to select "Auto login" option in user configuration window. Most likely you will see black screen after installation. Actually its not black, its very dark (like at minimal brightness). Its still possible to see login window at some angles, but I prefer auto login untill we find the solution. Its impossible to change brightness at login screen with functinal keys, but after login the brightness returns to normal level and functional keys works.
[*]Follow the instructions to finish installation and reboot your PC. You should see 'ubuntu' in boot order menu in bios or by hitting F12. The installer puts ubuntu at the top of this list, so after reboot you will get to newly installed system.
[/LIST]

Manual grub installation.
I think it should be done in following steps:
1. Boot from livecd/usbstick
2. Install grub-efi package
3. Mount the neccesary partitions (like root, boot and efi)
4. Issue grub-install with aproriate flags
5. Run grub-update or efibootmgr to add ubuntu to EFI menu list.

I'll post dmesg and parted output bit later, have to go for now

PS: sorry for misspells! This touchpad is killing me. Sometimes it triggers when I hover a finger over touchpad without actually touching it.


```
$ dmesg |grep EFI
[    0.000000] EFI v2.00 by Phoenix Technologies Ltd.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x0000000000054000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000054000-0x0000000000055000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000055000-0x000000000008f000) (0MB)
[    0.000000] EFI: mem04: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
[    0.000000] EFI: mem05: type=3, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x000000000056d000) (4MB)
[    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x000000000056d000-0x0000000000c00000) (6MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[0x0000000000c00000-0x0000000001000000) (4MB)
[    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x0000000001000000-0x00000000359f6000) (841MB)
[    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x00000000359f6000-0x0000000036cf3000) (18MB)
[    0.000000] EFI: mem11: type=7, attr=0xf, range=[0x0000000036cf3000-0x000000008632e000) (1270MB)
[    0.000000] EFI: mem12: type=2, attr=0xf, range=[0x000000008632e000-0x00000000b3e58000) (731MB)
[    0.000000] EFI: mem13: type=4, attr=0xf, range=[0x00000000b3e58000-0x00000000b3e78000) (0MB)
[    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x00000000b3e78000-0x00000000b6305000) (36MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x00000000b6305000-0x00000000b6e48000) (11MB)
[    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x00000000b6e48000-0x00000000b6f27000) (0MB)
[    0.000000] EFI: mem17: type=1, attr=0xf, range=[0x00000000b6f27000-0x00000000b6f47000) (0MB)
[    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x00000000b6f47000-0x00000000b784c000) (9MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x00000000b784c000-0x00000000b8685000) (14MB)
[    0.000000] EFI: mem20: type=7, attr=0xf, range=[0x00000000b8685000-0x00000000b8688000) (0MB)
[    0.000000] EFI: mem21: type=4, attr=0xf, range=[0x00000000b8688000-0x00000000b9255000) (11MB)
[    0.000000] EFI: mem22: type=7, attr=0xf, range=[0x00000000b9255000-0x00000000b92d7000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x00000000b92d7000-0x00000000b92db000) (0MB)
[    0.000000] EFI: mem24: type=7, attr=0xf, range=[0x00000000b92db000-0x00000000b92dc000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x00000000b92dc000-0x00000000b92dd000) (0MB)
[    0.000000] EFI: mem26: type=7, attr=0xf, range=[0x00000000b92dd000-0x00000000b92de000) (0MB)
[    0.000000] EFI: mem27: type=4, attr=0xf, range=[0x00000000b92de000-0x00000000b92df000) (0MB)
[    0.000000] EFI: mem28: type=7, attr=0xf, range=[0x00000000b92df000-0x00000000b92e0000) (0MB)
[    0.000000] EFI: mem29: type=4, attr=0xf, range=[0x00000000b92e0000-0x00000000b956f000) (2MB)
[    0.000000] EFI: mem30: type=7, attr=0xf, range=[0x00000000b956f000-0x00000000b9570000) (0MB)
[    0.000000] EFI: mem31: type=4, attr=0xf, range=[0x00000000b9570000-0x00000000b958a000) (0MB)
[    0.000000] EFI: mem32: type=7, attr=0xf, range=[0x00000000b958a000-0x00000000b9598000) (0MB)
[    0.000000] EFI: mem33: type=4, attr=0xf, range=[0x00000000b9598000-0x00000000ba5a7000) (16MB)
[    0.000000] EFI: mem34: type=7, attr=0xf, range=[0x00000000ba5a7000-0x00000000ba9f2000) (4MB)
[    0.000000] EFI: mem35: type=2, attr=0xf, range=[0x00000000ba9f2000-0x00000000ba9f8000) (0MB)
[    0.000000] EFI: mem36: type=3, attr=0xf, range=[0x00000000ba9f8000-0x00000000bac87000) (2MB)
[    0.000000] EFI: mem37: type=5, attr=0x800000000000000f, range=[0x00000000bac87000-0x00000000bace7000) (0MB)
[    0.000000] EFI: mem38: type=5, attr=0x800000000000000f, range=[0x00000000bace7000-0x00000000bad87000) (0MB)
[    0.000000] EFI: mem39: type=6, attr=0x800000000000000f, range=[0x00000000bad87000-0x00000000badc0000) (0MB)
[    0.000000] EFI: mem40: type=10, attr=0xf, range=[0x00000000badc0000-0x00000000badc9000) (0MB)
[    0.000000] EFI: mem41: type=6, attr=0x800000000000000f, range=[0x00000000badc9000-0x00000000bae87000) (0MB)
[    0.000000] EFI: mem42: type=0, attr=0xf, range=[0x00000000bae87000-0x00000000baeff000) (0MB)
[    0.000000] EFI: mem43: type=10, attr=0xf, range=[0x00000000baeff000-0x00000000baf9f000) (0MB)
[    0.000000] EFI: mem44: type=9, attr=0xf, range=[0x00000000baf9f000-0x00000000bafe5000) (0MB)
[    0.000000] EFI: mem45: type=9, attr=0xf, range=[0x00000000bafe5000-0x00000000bafff000) (0MB)
[    0.000000] EFI: mem46: type=4, attr=0xf, range=[0x00000000bafff000-0x00000000bb000000) (0MB)
[    0.000000] EFI: mem47: type=7, attr=0xf, range=[0x0000000100000000-0x00000001bfe00000) (3070MB)
[    0.000000] EFI: mem48: type=11, attr=0x8000000000000001, range=[0x00000000f80f8000-0x00000000f80f9000) (0MB)
[    0.000000] EFI: mem49: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] ACPI: UEFI 00000000bafe7000 0003E (v01 LENOVO CB-01    00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafe5000 00256 (v01 LENOVO CB-01    00000001 PTL  00000001)
[    0.515353] fb0: EFI VGA frame buffer device
[    0.741544] EFI Variables Facility v0.08 2004-May-17
[    1.873307] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

```

```
$ find /boot/efi -iname "*efi*"
/boot/efi
/boot/efi/EFI
/boot/efi/EFI/ubuntu/grubx64.efi
```

```
$ sudo efibootmgr 
[sudo] password for user: 
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0008,0003,0004,0005,0006,0002,0007
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:
Boot0003* ATA HDD: WDC WD7500BPVT-24HXZT1                  
Boot0004* ATAPI CD: MATSHITADVD-RAM UJ8B1AS                 
Boot0005* USB HDD:
Boot0006* USB CD:
Boot0007* PCI LAN: Realtek PXE B04 D00
Boot0008* ubuntu
```

---

### Post by hornedfiend on 2011-12-19
You rule dude. i haven't been sleeping because of this. 
Hat's off to you. Thanks a million!

It seems that, in my case (11.10 x64) grub-efi is already installed. The only weird thing is that I can't access the bios settings or boot manager and ubuntu starts loading almost instantly (I only see the lenovo screen for 2-3 seconds).

I've fixed the wifi too, by blacklisting the acer module and installed ironhide for optimus functionality (I can't really tell if it's working or not, since I haven't used this for too many things, yet).

All and all it looks cool, but incomplete (since i can't access bios settings & stuff).

---

### Post by oldfred on 2011-12-21
To any with a working or almost working grub efi system.

We are testing a newer version of bootinfoscript that should also parse the efi partitions and show the grub files.

From terminal command line download & run script then copy & paste results.txt to here, please put in code tags (# in edit panel) to make it easier to read:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript

sudo bash bootinfoscript

 gksu gedit results.txt

```

If it is your first run of bootinfoscript, it will be results.txt or else it adds a digit for each additional run. result1.txt etc.

When I down loaded the script it did not appear in Nautilus immediately? but terminal shows files ok.

Thank you.

---

### Post by hornedfiend on 2011-12-23
@oldfred: I will run this today and post the results.txt here.

1. Does anyone know how to solve the monitor turn off feature? Whenever the power management module turns off my monitor, I end up with a laptop unable to resume its previous state. 
The only workaround for this is to close the lid, so that the system goes into sleep mode and just re-open the lid again for it to resume correctly.

2. Ironhide is a nasty workaround but at least it works. Still needs a lot of work and it seems that the performance isn't that great. I'm just curious: how can I force certain applications to use the nvidia card and how do I check which card is in usage (when needed)?

---

### Post by teufelsdroch on 2011-12-23
Wow, well I followed these instructions on the b570--which, by the way, I picked up for a screamin' $240 with a display coupon at best buy!

But, I had the following problems:

1) grub legacy loaded ubuntu fine, but didn't load windows 7
2) chroot couldn't find an internet connection

Luckily, it turns out grub2 works fine, so long as you convince is to form a master boot record.

First, you connect to the net just as OP suggests, but add

```
cp /etc/resolv.conf /mnt/sda#/etc/resolv.conf
```

so that chroot jail has a line out. Then after 

```
sudo chroot . 
```

you should be root and you purge the old stuff with (no 'sudo' needed!)

```
apt-get purge grub grub-pc grub-common
```

and then reset the list with

```
apt-get install grub-common grub-pc
update-grub 
```

You have to pick the boot partition with space, bizarrely...

Eureka! Win 7, Ubuntu, and the repair partition all pop up--and I suspect that grub2 will do a better job of resisting being written over by win7 updates. Remains to be seen...

---

### Post by sideffects on 2011-12-25
Wait, so to my understanding, I am supposed to create a partition table, thereby completely wiping my harddrive? I don't want to get rid of windows 7, I want to dualboot

---

### Post by moteprime on 2011-12-25
@sideffects. I got a dualboot system with Ubuntu and Windows on a Lenovo s205.
Se my post #22
[http://ubuntuforums.org/showpost.php?p=11462117&postcount=22](http://ubuntuforums.org/showpost.php?p=11462117&postcount=22)

---

### Post by oldfred on 2011-12-25
Creating partition table does not necessarily delete Windows. But if you convert from MBR to gpt or vice-versa it will, but then you are also changing how you are booting from BIOS to UEFI.

Windows only works on UEFI if you have a gpt partition table. You still can shrink the Windows partition and create new partitions for Ubuntu (all gpt parititons are primary). I know with MBR it is best to use the Windows tools for shrinking the Windows partition, but not so sure about gpt.

If Windows is on a MBR partitioned table, you are booting with BIOS and it becomes just like any dual boot instructions. Use Windows to shrink the Windows partition and use gparted to create extended & logical partitons.

---

### Post by sideffects on 2011-12-25
I'm kinda scared to screw anything up with all of this partitioning, so let me clarify a couple of things...
[[IMG]http://img833.imageshack.us/img833/3505/partfz.th.png[/IMG]](http://imageshack.us/photo/my-images/833/partfz.png/)

This is what my partitions look like. I all ready have 3 primary partitions (came that way), and I'm not really sure what Lenovo was trying to do here. :) So, if I'm understanding correctly, the best thing to do would be to create some space (in Windows) on my C: and then use GParted to set up my Linux partition? Do I need to set it as a boot partition, and do I need Linux-swap?

---

### Post by oldfred on 2011-12-26
You are fortunate that Lennovo created D: as a logical. When you shrink c: with Windows it will create unallocated space between c: & d: . Then with gparted you can extend the extended partition left to include the unallocated and create / (root) and swap partitions as logical partitions. You already have a shared NTFS (d:) for data and may not need a separate /home since most data you should save into the shared partition.  Then /home is small and easily backed up for a new install.

---

### Post by sideffects on 2011-12-26
> **oldfred said:**
> You are fortunate that Lennovo created D: as a logical. When you shrink c: with Windows it will create unallocated space between c: & d: . Then with gparted you can extend the extended partition left to include the unallocated and create / (root) and swap partitions as logical partitions. You already have a shared NTFS (d:) for data and may not need a separate /home since most data you should save into the shared partition.  Then /home is small and easily backed up for a new install.

I appreciate the help! Got it all working. Thanks!

---

### Post by evil_hog on 2011-12-29
> **hornedfiend said:**
> It seems that, in my case (11.10 x64) grub-efi is already installed.
Maybe they've updated distributives or something? I had an error telling me that grub-efi not found before I plugged network cable in.

> **hornedfiend said:**
> The only weird thing is that I can't access the bios settings or boot manager and ubuntu starts loading almost instantly (I only see the lenovo screen for 2-3 seconds).
I had no problem with this. To bring configuration window on screen I'm tapping F2 after reboot. Or Del button, can't remember which one.

---

### Post by oldfred on 2011-12-29
Back in post #38, I asked if anyone could run the test version of bootinfoscript to see if it works with an efi install. Has anyone got a working UEFI & grub efi system?

---

### Post by yannoo on 2011-12-30
Hi all,

After a long series of attempts at installing 11.10 on my recently bought B570, I could get it to  boot successfully with burg. No particular setup, just installed burg.

Before that, I had tried grub, grub2 and grub-efi to no avail.

Thanks a million to the person who reported the burg choice.
The only thing I'm missing is the i915 and the aspm stuff, which I don't know where to put in burg since there's no menu.lst.

Also, setting up the acer_wmi in /etc/rc.local effectively fixed the wireless problem.

Thank you for that to the original poster!

---

### Post by sideffects on 2011-12-30
> 
**3.2 Fix battery drain (tested on Intel Sandy Bridge systems like B570)**
When you switch from Windows based systems you might detect a faster battery drain on your Linux system.
The problem is that some kernel parameters are disabled by default which put the VGA into a energy saving mode.
Some people had random system freezes with this great Sandy Bridge feature enabled, however there are a lot of people like me who don't have problems at all. I will recommend you the tweaks which fixed the main battery drain for me.

You have to add the following boot parameters to the grub menu.lst located in /boot/grub:

1.) Activates the RC6 mode of the Intel GPU
```

i915.i915_enable_rc6=1

```

2.) Activates PCIe Active State Power Management
```

pcie_aspm=force

```


I'm using GRUB 2 and I'm under the impression that GRUB 2 doesn't have a menu.lst file. If so, where do I put in this code. My battery drain is pretty quick. A lot quicker than Windows.

---

### Post by oldfred on 2011-12-31
I do not know burg but I thought it was based on grub2 which uses grub.cfg. Does it copy from grub.cfg or have its own burg.cfg or something similar?

For grub you would do this:
gksudo gedit /etc/default/grub
sudo update grub

---

### Post by sideffects on 2012-01-01
> **oldfred said:**
> I do not know burg but I thought it was based on grub2 which uses grub.cfg. Does it copy from grub.cfg or have its own burg.cfg or something similar?

For grub you would do this:
gksudo gedit /etc/default/grub
sudo update grub

This is what I get when I try to update GRUB: 
```
/etc/default/grub: 37: i915.i915_enable_rc6=1: not found
```

---

### Post by oldfred on 2012-01-02
What do you get if you run this, mine does not have that option but my system is older:

```
fred@fred-LT-A105:~$ sudo grep -H '' /sys/module/i915/parameters/*
[sudo] password for fred: 
/sys/module/i915/parameters/fbpercrtc:0
/sys/module/i915/parameters/lvds_downclock:0
/sys/module/i915/parameters/modeset:-1
/sys/module/i915/parameters/powersave:0
fred@fred-LT-A105:~$ 

```

And are you loading the i915 driver?
 sudo lshw -c display

---

### Post by sideffects on 2012-01-02
This is the result:

```
/sys/module/i915/parameters/fbpercrtc:0
/sys/module/i915/parameters/i915_enable_fbc:0
/sys/module/i915/parameters/i915_enable_rc6:0
/sys/module/i915/parameters/lvds_downclock:0
/sys/module/i915/parameters/lvds_use_ssc:1
/sys/module/i915/parameters/modeset:-1
/sys/module/i915/parameters/panel_ignore_lid:0
/sys/module/i915/parameters/powersave:1
/sys/module/i915/parameters/reset:Y
/sys/module/i915/parameters/semaphores:0
/sys/module/i915/parameters/vbt_sdvo_panel_type:-1
```

And for the next one:

```
riley@riley-laptop:~$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)

```

---

### Post by oldfred on 2012-01-02
It does show you have the parameter, I just do not know correct way to specify it.
> 
/sys/module/i915/parameters/i915_enable_rc6:0

Is it something that works in grub but then is not supported by burg?

---

### Post by coversnail on 2012-01-03
> **oldfred said:**
> s it something that works in grub but then is not supported by burg?

Sorry if this is a very noobish comment, but I thought sideffects said he was using Grub2 not burg.

I installed 11.10 64 bit Ubuntu and wanted to dual boot into Windows 7, but when restarting the computer would just immediately boot into Windows 7, this I fixed by using these instructions: [http://ubuntuforums.org/showpost.php?p=11415354&postcount=8](http://ubuntuforums.org/showpost.php?p=11415354&postcount=8) and creating a SuperGrub Live CD and then using the automatic repair Grub2 option. Now I have Grub2 running and it successfully can boot into either Windows or Ubuntu, but I don't know how to apply the power saving tweaks from the first post which mentions editing the menu.lst file, which is not used by Grub2. Any help would be very welcome.

---

### Post by sideffects on 2012-01-03
I thought I was using Grub2 as well, I thought I installed grub2, but maybe I did it wrong.

EDIT: This could be my problem
```
grub-install (GNU GRUB 0.97)
```

---

### Post by oldfred on 2012-01-03
Post this to see what is where, grub legacy has not been maintained for years, Ubuntu added some features to its copy of grub  .97 to work with ext4. You may have to uninstall grub & grub2 and cleanly install grub2:

Edit:
Or better run test versions I posted in post #38 as it now has some improvements:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by coversnail on 2012-01-03
Pretty sure you weren't actually asking me to run the script but these are my results. :D

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   294,863,660   294,452,013   7 NTFS / exFAT / HPFS
/dev/sda3         294,864,894   945,829,887   650,964,994   f W95 Extended (LBA)
/dev/sda5         885,022,720   945,829,887    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda6         294,864,896   876,810,239   581,945,344  83 Linux
/dev/sda7         876,812,288   885,020,671     8,208,384  82 Linux swap / Solaris
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7CD8BDF9D8BDB1AE                       ntfs       
/dev/sda2        3C34DEF334DEAF60                       ntfs       
/dev/sda4        14542661542645B8                       ntfs       LENOVO_PART
/dev/sda5        38285A5F285A1C66                       ntfs       LENOVO
/dev/sda6        86b1bc33-1581-4c99-afd1-5229bc581847   ext4       
/dev/sda7        4bf0dee5-a21c-4c42-92e0-4ffe428f6078   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=86b1bc33-1581-4c99-afd1-5229bc581847 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=86b1bc33-1581-4c99-afd1-5229bc581847 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=86b1bc33-1581-4c99-afd1-5229bc581847 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=86b1bc33-1581-4c99-afd1-5229bc581847 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 86b1bc33-1581-4c99-afd1-5229bc581847
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7CD8BDF9D8BDB1AE
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 14542661542645B8
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=86b1bc33-1581-4c99-afd1-5229bc581847 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4bf0dee5-a21c-4c42-92e0-4ffe428f6078 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 352.735569000 = 378.746933248  boot/grub/core.img                             1
 216.727676392 = 232.709570560  boot/grub/grub.cfg                             1
 142.797851562 = 153.328025600  boot/initrd.img-3.0.0-12-generic               2
 142.857543945 = 153.392119808  boot/initrd.img-3.0.0-14-generic               2
 352.735542297 = 378.746904576  boot/vmlinuz-3.0.0-12-generic                  1
 141.798286438 = 152.254750720  boot/vmlinuz-3.0.0-14-generic                  1
 142.857543945 = 153.392119808  initrd.img                                     2
 142.797851562 = 153.328025600  initrd.img.old                                 2
 141.798286438 = 152.254750720  vmlinuz                                        1
 352.735542297 = 378.746904576  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by sideffects on 2012-01-03
> **oldfred said:**
> Post this to see what is where, grub legacy has not been maintained for years, Ubuntu added some features to its copy of grub  .97 to work with ext4. You may have to uninstall grub & grub2 and cleanly install grub2:

Edit:
Or better run test versions I posted in post #38 as it now has some improvements:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Okay, here are the results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30926575 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648 1,274,219,131 1,273,807,484   7 NTFS / exFAT / HPFS
/dev/sda3       1,274,220,542 1,434,222,591   160,002,050   f W95 Extended (LBA)
/dev/sda5       1,373,403,136 1,434,222,591    60,819,456   7 NTFS / exFAT / HPFS
/dev/sda6       1,274,220,544 1,356,804,095    82,583,552  83 Linux
/dev/sda7       1,356,806,144 1,373,403,135    16,596,992  82 Linux swap / Solaris
/dev/sda4       1,434,222,592 1,465,149,167    30,926,576  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        566409BB64099F3D                       ntfs       
/dev/sda2        52100B63100B4E03                       ntfs       
/dev/sda4        7264104264100C0B                       ntfs       LENOVO_PART
/dev/sda5        94981D8E981D6FCA                       ntfs       LENOVO
/dev/sda6        9bbc7546-d362-48df-bb92-0bac45ff9150   ext4       
/dev/sda7        15948faf-277a-4174-a0a6-b5c08bed7a65   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4        /media/sda4              fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9bbc7546-d362-48df-bb92-0bac45ff9150

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-14-generic
uuid		9bbc7546-d362-48df-bb92-0bac45ff9150
kernel		/boot/vmlinuz-3.0.0-14-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-14-generic

title		Ubuntu 11.10, kernel 3.0.0-14-generic (recovery mode)
uuid		9bbc7546-d362-48df-bb92-0bac45ff9150
kernel		/boot/vmlinuz-3.0.0-14-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro  single
initrd		/boot/initrd.img-3.0.0-14-generic

title		Chainload into GRUB 2
root		9bbc7546-d362-48df-bb92-0bac45ff9150
kernel		/boot/grub/core.img

title		Ubuntu 11.10, memtest86+
uuid		9bbc7546-d362-48df-bb92-0bac45ff9150
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro i8042.nopnp  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro recovery nomodeset i8042.nopnp
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro i8042.nopnp  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=9bbc7546-d362-48df-bb92-0bac45ff9150 ro recovery nomodeset i8042.nopnp
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9bbc7546-d362-48df-bb92-0bac45ff9150
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 566409BB64099F3D
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 7264104264100C0B
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda6 during installation
UUID=9bbc7546-d362-48df-bb92-0bac45ff9150  /            ext4  errors=remount-ro           0  1  
# swap was on /dev/sda7 during installation
UUID=15948faf-277a-4174-a0a6-b5c08bed7a65  none         swap  sw                          0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults                    0  0  
/dev/sda4                                  /media/sda4  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults                    0  0  
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2012-01-03
@sideffects

These seem to be your parameters
```
ro i8042.nopnp  quiet splash vt.handoff=7
```

You have grub2 in the MBR, but do have a grub legacy menu.lst. Are you showing that you are trying to boot with grub legacy?

#versions:
```
grub-install -v
uname -a
```

#To edit grub parameters:
gksudo gedit /etc/default/grub
# Then:
sudo update-grub

---

### Post by sideffects on 2012-01-03
> **oldfred said:**
> @sideffects

These seem to be your parameters
```
ro i8042.nopnp  quiet splash vt.handoff=7
```

You have grub2 in the MBR, but do have a grub legacy menu.lst. Are you showing that you are trying to boot with grub legacy?

#versions:
```
grub-install -v
uname -a
```

#To edit grub parameters:
gksudo gedit /etc/default/grub
# Then:
sudo update-grub

I'm sorry, I'm not clear on how I am supposed to change the parameters/

---

### Post by iqtedar on 2012-01-04
I was able to install Ubuntu 11.10 on my Lenovo B570 using the GUID Partition Table by creating the first partition as an EFI System Partition which automatically formats this as FAT16. Otherwise, if you just create a boot partition the computer fails to boot. If you let the installer do the partitioning, it will automatically create this. My other partitions are Ext4 formatted. Also, there was no need to replace Grub2 with v1. There was an issue with the screen being unable to turn back on easily following a default turnoff after 10 minutes. Initially, I used Fn+F1 which puts the computer to sleep and then pressed any key to wake but this disconnected all my network connections. Then I realised Fn+Up arrow does the job which increases the screen brightness without getting disconnected.

---

### Post by coversnail on 2012-01-04
> **sideffects said:**
> I'm sorry, I'm not clear on how I am supposed to change the parameters/

I asked this question in a new thread and was answered: [http://ubuntuforums.org/showthread.php?t=1904374](http://ubuntuforums.org/showthread.php?t=1904374)

Haven't tried it myself yet though

---

### Post by BigBaka on 2012-01-09
> ```

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1
sudo mount --bind /sys ./sys
sudo mount --bind /proc ./proc
sudo mount --bind /dev ./dev
sudo chroot .

#We are now in our fresh installed Ubuntu

sudo apt-get update
sudo apt-get install grub
sudo update-grub #say yes when generating menu.lst
sudo grub-install /dev/sda
sudo grub-install /dev/sda1
```


Have been following this guide to install 64bit on Lenovo S205 but got stuck here:

```
ubuntu@ubuntu:/mnt/sda1$ sudo mount --bind /sys ./sys
mount: mount point ./sys does not exist
```

What am I doing wrong?

Regards,
BB

---

### Post by BigBaka on 2012-01-09
Actually I couldn't run most of that script. The chroot also returned an error 

ubuntu@ubuntu:/mnt/sda1$ sudo chroot .
chroot: failed to run command `/bin/bash': No such file or directory


as did the following

ubuntu@ubuntu:/mnt/sda1$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/mnt/sda1$ sudo grub-install /dev/sda1
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/mnt/sda1$ 

Any advice appreciated
Thanks
BB

---

### Post by moteprime on 2012-01-09
BigBaka
I had some weird errors following that guide, it took me some time to find out that there was something going wrong during copy/paste, so that my terminal got the wrong characters. It looked right but it did not work. I then tried to type in the commands instead of copy/paste them, and it worked fine.
I don't know if that's what is going wrong for you, but it did for me.

---

### Post by BigBaka on 2012-01-09
Thanks for the tip, but alas no difference when typing commands into terminal

---

### Post by oldfred on 2012-01-09
There should not be the extra . in your commands like
sudo mount --bind /sys ./sys

Several other instructions on chroot:
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by BigBaka on 2012-01-09
Thanks will check that out. By the way if it makes a difference, following is my hard disk readout

ubuntu@ubuntu:/mnt/sda1$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x75e90800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    6  FAT16
/dev/sda2          411648    82331647    40960000   83  Linux
/dev/sda3        82331648    88475647     3072000   82  Linux swap / Solaris
/dev/sda4        88475648   976773119   444148736   83  Linux

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031497

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7821311     3910640    b  W95 FAT32

---

### Post by Trenchbroom on 2012-01-22
> **teufelsdroch said:**
> Wow, well I followed these instructions on the b570--which, by the way, I picked up for a screamin' $240 with a display coupon at best buy!

But, I had the following problems:

1) grub legacy loaded ubuntu fine, but didn't load windows 7
2) chroot couldn't find an internet connection

Luckily, it turns out grub2 works fine, so long as you convince is to form a master boot record.

First, you connect to the net just as OP suggests, but add

```
cp /etc/resolv.conf /mnt/sda#/etc/resolv.conf
```

so that chroot jail has a line out. Then after 

```
sudo chroot . 
```

you should be root and you purge the old stuff with (no 'sudo' needed!)

```
apt-get purge grub grub-pc grub-common
```

and then reset the list with

```
apt-get install grub-common grub-pc
update-grub 
```

You have to pick the boot partition with space, bizarrely...

Eureka! Win 7, Ubuntu, and the repair partition all pop up--and I suspect that grub2 will do a better job of resisting being written over by win7 updates. Remains to be seen...

Thank you teufelsdroch!  I was able to finally get GRUB2 to work using your instructions for Win 7/ Kubuntu dual boot on a friend's Lenovo B570, only slightly different:

1.  Installed fresh Win 7 64 bit install using GParted to setup MS-DOS partition table (note: I could not install Win 7 with MS-DOS table until I updated to the latest BIOS).  Split the hard drive into two partitions (unformatted), let Win 7 setup its own partitions using the first unformatted partition.  Windows set the EFI boot partition as the first on the drive automatically.

2.  Installed Kubuntu 64-bit into the second unformatted partition.  Reboot and it boots right into Win 7. 

3.  Used Super Grub2 disk to boot into Kubuntu.  Got the wireless working.

4.  Purged all GRUB items as you instructed, then reinstalled.  Put the new GRUB in the EFI boot partition that Win 7 set up.

5.  Raise your hands to the sky like Andy Dufresne in Shawshank Redemption!  DONE!!

---

### Post by Pay87 on 2012-02-04
Thanks for all feedback. Since we are now able to install Ubuntu with GPT table and grub2 easily, I updated the guide on the first page.

Also I updated the WLAN fixing part, because the restricted drivers are working fine now and there is no need for the unstable acer workaround. 

The network manager seems to be broken that is why I suggest using wicd instead which fixes the problem. :)

---

### Post by sideffects on 2012-02-04
> **Pay87 said:**
> Thanks for all feedback. Since we are now able to install Ubuntu with GPT table and grub2 easily, I updated the guide on the first page.

Also I updated the WLAN fixing part, because the restricted drivers are working fine now and there is no need for the unstable acer workaround. 

The network manager seems to be broken that is why I suggest using wicd instead which fixes the problem. :)

So, what do I do if I've installed it the old way?

EDIT: Can I change it, or am I stuck?

---

### Post by Pay87 on 2012-02-04
> **sideffects said:**
> So, what do I do if I've installed it the old way?

EDIT: Can I change it, or am I stuck?

What do you want to change?
The old way is also okay, or do you mean the fix for the wlan adapter?

If yes, just install the restricted drivers and wicd (see first post howto).
And remove the lines added to /etc/rc.local before.

---

### Post by sideffects on 2012-02-04
> **Pay87 said:**
> What do you want to change?
The old way is also okay, or do you mean the fix for the wlan adapter?

If yes, just install the restricted drivers and wicd.
And remove the lines added to /etc/rc.local

Sorry, I know it's not a big deal, but Is it possible to update my GRUB now?

---

### Post by Pay87 on 2012-02-04
> **sideffects said:**
> Sorry, I know it's not a big deal, but Is it possible to update my GRUB now?

If you want to do it the new way with Grub2 you need a EFI partition and a GPT table instead MBR.

But there is nothing wrong with Grub.
I would suggest you keep Grub and if you come to the point that you need to reinstall Ubuntu someday then you do it the "new way."

The wlan fix does not depend on Grub2. Its just another boot manager and I don't see any advantages if you have a running system.

It is now just easier when you do a fresh installation for users who don't got Ubuntu running yet.

---

### Post by OxKing on 2012-02-08
What was changed that it is now possible to install it normal?
Was it an Grub2 update which is downloaded during the installation?

For WLAN, i still use the "old" method:
> Just add the following code to /etc/rc.local before the line "exit 0" 

Code:
sudo rfkill unblock wifi
sudo rfkill unblock all
sudo modprobe -r acer_wmi

Uhh, and the i915 rc6 stuff is to put in /etc/default/grub for grub2:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash XXX"
```
(at the XXX) and then sudo update-grub after saving the file.


The backlight keys worked for me out off the box anyway...

---

### Post by Ph1b on 2012-02-09
I'm resetting my system now and try the new way. But on my S205 I am not able to find the drivers in the propritary-driver-program. So you should leave the part with acer_wmi in the tutorial for the s205'er. Or am I doing sth wrong?

---

### Post by moteprime on 2012-02-09
Yesterday i made a new installation just for testing (other stuff), but the Wicd approach does not work for me, it runs with maximum of 60-70 Kb/sec network speed. The solution that works the best for me (every time) are still to download and install this specific driver from Markus Heberling on launchpad 
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

add rt3090sta to /etc/modules
"blacklist acer_wmi" in /etc/modprobe.d/blacklist.conf
And reboot.

It also seems to work in Precise.

The conflict with acer_wmi has been solved.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659)

---

### Post by sideffects on 2012-02-13
I had my battery lasting for a long time, but now it's back to lasting for an hour and a half. I was looking at my grub files, and this is what I have on my /etc/default/grub file.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm i915.i915_enable_rc6=1 i915.lvds_downclock=1 pcie_aspm=force"
```

---

### Post by Pay87 on 2012-02-14
After a kernel update I had to blacklist some WLAN modules. I updated the first post how to do this and get Wifi working again.. :D

---

### Post by Pay87 on 2012-02-18
Something new again:
We can use network-manager if we also blacklist acer_wmi.
So we just have to install the restricted drivers. Blacklist modules (see first post). Reboot. Done :popcorn:

No need for Wicd.

---

### Post by ivanmmj on 2012-02-18
Just in case anyone has had the same issue:
After a few months of fighting with my wifi card (the Broadcom BCM4313) where all wireless connections would just drop out randomly and I had to disable then reenable the card (this was across multiple installs and multipe distros)) I finally gave up on it and picked up an Atheros AR9285. Unfortunately, this AR9285 was not compatible with the B570. I didn't feel like getting another one and thus I flashed a BIOS with the Wifi Whitelist removed. I've now had the AR9285 for a week and it hasn't dropped ONCE since.

On a somewhat unrelated note: Does anyone know if there any higher resolution LCD's compatible with with this laptop that I can swap in place of the current one?

---

### Post by Ph1b on 2012-02-22
As said, there is no restricted driver available for the S205. Also with the new method after a suspend/hibernate you have to reboot the computer properly. Otherwise there is now wifi at all.

---

### Post by brulien on 2012-02-24
Hi all,

I just discover this discussion, I read all the posts but I did not find the solution to my problem.

I just buy a Lenovo B570e and try to install ubuntu in the whole harddirve (erasing windows). I followed the tutorial at the beginning of the discussion, and for me it does not work ... :(
There is nothing booting.

I also tried [http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi) (second answer), without success ...

Help !!

---

### Post by oldfred on 2012-02-24
Welcome to the forums. It may be better to start your own thread, if you want to post boot info script. You can download into liveCd or USB.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

or:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by VoiDeR on 2012-02-29
Hi I just bought this laptop yesterday and have everything setup and working. Question though what kind of battery life is everyone getting? I got it at best buy and they say 5 hours 36 mins, but the battery status in ubuntu is only say alittle over 3 hours.

---

### Post by sideffects on 2012-02-29
> **VoiDeR said:**
> Hi I just bought this laptop yesterday and have everything setup and working. Question though what kind of battery life is everyone getting? I got it at best buy and they say 5 hours 36 mins, but the battery status in ubuntu is only say alittle over 3 hours.

I think this is a pretty common issue with 11.04 & 11.10. Supposedly, they are fixing some power consumption issues for 12.04. Section 3.2 on the very first post in this thread addresses some of your issues.

---

### Post by moteprime on 2012-03-01
I get 2½ hours from my Ideapad s205.

---

### Post by VoiDeR on 2012-03-01
I did the battery drain fix after I installed. Is there a chance that the battery status is inaccurate? This laptop is awesome so I guess I can live with 3.5 hours.

---

### Post by ivanmmj on 2012-03-06
> **VoiDeR said:**
> I did the battery drain fix after I installed. Is there a chance that the battery status is inaccurate? This laptop is awesome so I guess I can live with 3.5 hours.

Was the battery life much better in Windows? I never used the Windows that came with it and I bought this laptop to go UP to the current 3.5 hours. ;) My last laptop would only get 30 minutes if I was lucky. :p

---

### Post by VoiDeR on 2012-03-06
I cringe every time i see the windows entry in grub so no i haven't tested in windows yet. I suppose I should, but i can live with 3.5.

---

### Post by nobarte on 2012-03-24
I’m trying to update my Lenovo BIOS. The update is described on the  first post  ([http://ubuntuforums.org/showpost.php?p=11381428&postcount=1](http://ubuntuforums.org/showpost.php?p=11381428&postcount=1)).  Unfortunately I can not cope.

> Now build yourself a bootable USB stick with FreeDos. I used the  image of the Ultimate BootCD as source for my USB Stick because FreeDos  is already built in.I've done it.
> Copy the extracted "lenovo-bios" folder to the usb stick.After build a bootable USB stick, I've  copied "lenovo-bios" folder to USB root directory. Is it correct?
> Now boot into FreeDos.Yes, I can do that.
> cd into your "lenovo-bios" folder. I've stuck here. I do not know how to cd into the folder on my usb stick.

I will be grateful for your help. Thanks.

---

### Post by oldfred on 2012-03-24
That is in DOS and it has been many years. :)

But cd is still the same in Dos as Linux. But if you have folders the slash is backslash or is it the other way around. I never knew which was which. Linux is / and Dos is \.

cd lenovo-bios

---

### Post by nobarte on 2012-04-09
[COLOR=#000000][FONT=Arial]In my case, FreeDos boots onto A: drive. To get to C: drive, simply type "C:". Then you can type "dir" to see the files.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I'd like to share how I built a USB stick.[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]Delete all partitions on your stick[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Create one primary partition and mark it as active[/FONT][/COLOR]
[LIST]
[*][COLOR=#3c3c3c][FONT=Arial]The [/FONT][/COLOR][COLOR=#3c3c3c][FONT=Arial]**boot flag**[/FONT][/COLOR][COLOR=#3c3c3c][FONT=Arial] indicates the partition is [/FONT][/COLOR][COLOR=#3c3c3c][FONT=Arial]**active**[/FONT][/COLOR][COLOR=#3c3c3c][FONT=Arial] or bootable. Only one partition on a disk device can be active.[/FONT][/COLOR]
[/LIST]
 
[*][COLOR=#000000][FONT=Arial]Format that partition using FAT32 (or FAT16)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Install UNetbootin [/FONT][/COLOR][COLOR=#000000][FONT=Arial]in your system[/FONT][/COLOR][COLOR=#000000][FONT=Arial].[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Insert your blank USB drive into one of your USB ports first. You can launch UNetbootin on Ubuntu through the menu at [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**Applications&#8594;System Tools&#8594;UNetbootin**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. You can also launch from the command line with the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]*unetbootin*[/FONT][/COLOR][COLOR=#000000][FONT=Arial] command. You may get prompted to enter your password. UNetbootin should detect your USB drive automatically and select it.[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]Click the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**Select Distribution**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] button and choose [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**FreeDOS**[/FONT][/COLOR][COLOR=#000000][FONT=Arial].[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]UNetbootin will begin downloading FreeDOS for you and install it to your flash drive.[/FONT][/COLOR]
[/LIST]
 
[*][COLOR=#000000][FONT=Arial]The rest, as described on [#1 post]("http://ubuntuforums.org/showpost.php?p=11381428&postcount=1")...[/FONT][/COLOR]
[/LIST]

---

### Post by zapperlot on 2012-04-24
Hello,
 
the guide in the OP doesnt work for me. I made 4 partitions, one 200 MB EFI, 8GB Swap and EXT4root/home with 25 and ~460GB. Installation complete, reboot -> no OS found on the HDD. So I ran the live version again, used the same partitioning and formatted both EXT4 partitions -> still not bootable.
 
Whether I choose /dev/sda (the HDD) or dev/sda1 (the EFI partition) for the boot loader doesn't matter. So why doenst it work for me when it works for everyone else, I dont get it. 
 
Ubunu32 will run right? Maybe I should try to install that instead. But I have 8GB RAM so I need a 64bit OS to make use of that right? :(

---

### Post by oldfred on 2012-04-24
When you boot to install are you in UEFI mode? Or did you select efi to boot not BIOS mode or AHCI?

If you end up installing in BIOS mode it will not install the efi files to the efi partition. You may be able to manually do that after the fact. But in BIOS with gpt partitioning you need a small 1MB bios-grub partition to get grub2's boot loader to install correctly to the gpt protective MBR.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

---

### Post by Lovegain on 2012-04-27
Hello.

I followed the instructions in the first post with my new S205. But the installed system wouldn't boot.

Instead, I found [the guide on Roblog]("http://helms-deep.cable.nu/%7Erwh/blog/?p=177") more helpful. Except I used the newly stable-released Precise Pangolin 12.04 version. So, basically, this is how I did:

[LIST=1]
[*]I started off with a system marked from several previously failed installation attempts:
[LIST]
[*]The default Windows partitions had been erased, except forwhat seems like a recovery partition in the end.
[*]sda1 contained an EFI syslinux bootloader created by an Arch installation (which was performed by a friend to help troubleshoot the installation process).
[/LIST]
 
[*]Initiating the installer, I checked the option about online upgrades, but not the one about proprietary software.
[*]I did partitioning manually: 230 MB /boot ext2, 8 GB swap, and / ext4 for the rest of available space.
[*]The rest of the installation proceeded successfully.
[*](This step will probably not affect anyone else :)) At reboot, the Arch created syslinux bootloader was started. So I rebooted into the LiveUSB again, and simply removed that partition through GParted (after taking a backup).
[*]After rebooting, the installed system went up nicely.
[/LIST]
So how about the system now? Many seem to have problems with wireless networking. For me, on 12.04, I could immediately connect to my WPA home network. However I can't record sound so I guess some (missing) driver is at fault - perhaps because I unchecked that installation option. Playing sound is fine though sound quality is kind of meh. But maybe that's just cheap hardware?

Good luck!

---

### Post by moteprime on 2012-04-28
@Lovegain
Glad to hear that it works well for you. :-)
There seems to be 5-6 different hardware versions of the s205 and they have different WiFi problems. The one problem that most have are not to get WiFi connected, but getting a stable network speed higher that 70-80Kb/sec.

---

### Post by scorptig on 2012-04-30
OK for those of you getting error :

```
prefix error not set
```

That's while attempting to install any 64 bit Linux installation & then upon reboot you get this error :

```
error: invalid arch independent ELF magic.
```

Previous issues without this EFI partition :

```
missing firmware : iwlwifi-1000-6.ucode
```
during install process.

This thread How to **Install on a Lenovo (U)EFI system**

[http://ubuntuforums.org/showthread.php?t=1959458]("http://ubuntuforums.org/showthread.php?t=1959458")

In my case with a [COLOR="Blue"]Lenovo Z570[/COLOR] i5 CPU, the solution worked well.

However I did following :

Using a live Partition Magic disk and GParted, I created the first logical partition 50 megs FAT 16 and Gparted gave me option to designate as EFI.
As well in my installation I was able to make more partitions.

**terminal df-h output**

```

/dev/sda2        12G  580M   11G   5% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  868K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  152K  3.9G   1% /run/shm
/dev/sda1        50M  120K   50M   1% /boot/efi
/dev/sda7        12G  310M   12G   3% /tmp
/dev/sda3        15G  3.3G   11G  23% /usr
/dev/sda6        10G  280M  9.2G   3% /opt
/dev/sda9       639G   11G  597G   2% /home
/dev/sda5       8.0G  1.2G  6.5G  15% /var

```

Thank you for post, this solved my 64 bit installation issue, note I tried alternate disk, did not work, however the Desktop edition of Ubuntu 12.04 booted into desktop without issues..and permitted installation.

Additional note, in my case, Network, Brightness, no issues, all worked without any other steps, latest BIOS 38 installed for Z570 i5-2410

---

### Post by oldfred on 2012-04-30
UEFI needs gpt and with gpt you do not have an extended/logical partitions. The UEFI specification calls out FAT32 for hard drives (bug in Ubuntu did use FAT16). FAT16 is allowed and should work, but it is really for floppy drives and other really old devices that did not support FAT32.

Also most desktops only have to have / (root) and maybe swap. Often a separate /home is also suggested or other data partitions but you do not need to have separate partitions for all of the system folders. That goes back to old Linux servers. (I did that 15years ago with Redhat 5 & 7).

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Psyrus on 2012-05-16
Hi, I'm also struggling to get Ubuntu running on my B570. I haven't tried every solution yet...just wanted to find out if it is necessary to update the BIOS? I'm a little cautious when it comes to that.

---

### Post by Psyrus on 2012-05-17
So, finally got 12.04 64-bit installed. I think my DVD drive may be faulty...was "timing out" on reading the discs I think, so I could never even load the live version. I then tried with a USB, which got me to the live desktop. From there I tried to install, creating my partitions manually, and installing to disk. Thereafter I followed all the suggestions from this thread, and other fora, about getting Ubuntu to run from the installation. Nothing worked. Out of frustration I decided to give Ubuntu complete control of the install (using whole disk, creating partitions, etc). Voila! Installed perfectly (except for the wireless, but I fixed that). The only issue is that I now have only a / & a swap partition. Not the way I wanted it, but at least I can work with the machine!:guitar:

---

### Post by ivanmmj on 2012-06-22
> **Psyrus said:**
> Hi, I'm also struggling to get Ubuntu running on my B570. I haven't tried every solution yet...just wanted to find out if it is necessary to update the BIOS? I'm a little cautious when it comes to that.

I also had problems with GRUB even with the partitioning scheme they suggested. I ended up using the older instructions they had for installing GRUB1 (it's quoted by someone in the first few pages) but replaced GRUB with BURG. It worked beautifully. (I also had to change it so that BURG was called whenever a grub update was needed.)

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012416](http://ubuntuforums.org/showthread.php?t=2012416)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

