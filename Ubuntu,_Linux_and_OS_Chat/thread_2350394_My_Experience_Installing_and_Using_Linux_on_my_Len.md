---
title: "My Experience Installing and Using Linux on my Lenovo 110s"
date: 2017-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by matthewj15 on 2017-01-24
(I don't know where exactly to post this, but I felt this was the correct place. Just want to share my pleasant experience.)

 Good day Ubuntu Forums,
 
I love the ease of use of Unity and the customizability of Linux. I wish I could ditch Microsoft products, but programs like Office always pose a major challenge I don’t feel like overcoming at this time. Windows 7 was the last operating system I truly loved Microsoft for, and since then, I have felt disenfranchised by the company’s designers. Mouse and keyboard users should always come first and people shouldn’t worry about popups on their operating system telling them to use a certain web browser.
 
I am using a Lenovo 110s-11IBR, and I have to say, it is an excellent cheap Linux laptop. It is the successor to the Lenovo 100s, which last time I installed Ubuntu, didn’t have good support. But, the 110s has all features working that I have tested. I haven’t tested the Bluetooth, but it is recognized, so I think it works. I had to edit the BIOS settings a bit to get Ubuntu’s GRUB bootloader to be recognized. Besides this small quirk, this sub $200 laptop is excellent for Ubuntu 16.04, and I don’t think I want to return to cluttered Windows 10 on this machine. I have several hours of battery life and it is a very portable, cheap workhorse. Plus, it runs much better on Ubuntu than Windows 10. If you wish to buy this PC, I have instructions below to install Ubuntu on the machine. I have limited knowledge of the OS, and if I make any mistakes, feel free to correct me.

**[SIZE=3]Instructions on Installing Windows on a Lenovo 110s-11IBR[/SIZE]**

**[SIZE=2]What You Need[/SIZE]**

[LIST=1]
[*]Lenovo 110s-11IBR (Make sure you have the right model, old model may not work at all)
[*]USB Wifi Dongle or any other internet connectivity sources
[*]USB drive with 64-bit Ubuntu 16.04 LTS OS
[/LIST]
 
**BIOS Settings**
[LIST=1]
[*]Press F2 repeatedly upon booting the computer.
[*]Go to the ’Configuration Tab’ and make sure the following options are as such:
[LIST=1]
[*]USB Legacy – Enabled
[*]Wireless – Enabled
[*]Hotkey Mode – Selection does not matter, changes FN requirement for functions
[*]Intel Virtual Technology – Selection does not matter, allows VM to run within OS
[*]BIOS Flash Back – Disable (Default selection, May not matter with Install)
[/LIST]

[*]Go to the ‘Security Tab’ and make sure the following options are as such:
[LIST=1]
[*]Intel Platform Trust Technology – Disabled
[/LIST]

[*]Go to the ‘Boot Tab’ and make sure the following options are as such:
[LIST=1]
[*]Boot Mode – Legacy Support
[*]Boot Priority – UEFI First
[*]USB Boot – Enabled (Very Important to Enable)
[*]PXE Boot to Lan – Selection does not matter, allows machine to boot via Networking
[/LIST]

[*]Go to the ‘Exit Tab’ and make sure the following options are as such:
[LIST=1]
[*]OS Optimized Defaults – Disabled
[/LIST]

[*]Press ‘Exit Saving Changes’
[/LIST]
 
**Installing Ubuntu**

[LIST=1]
[*]Once you restart the computer, insert your Ubuntu 16.04 USB Disk and Press F12 repeatedly.
[*]Boot from your USB flash drive and make sure you are in the UEFI enabled Ubuntu installer.
[*]Install Ubuntu as usual wiping the entirety of the drive.
[*]Reboot into Ubuntu and make sure you have the USB Wifi Dongle installed and connect to your network.
[*]Open up a terminal and run ‘sudo apt-get update’ then ‘sudo apt-get upgrade’
[*]Upon restart, the machine should be running perfectly with the integrated Wi-Fi chip working along with all other futures.
[*]Customize Ubuntu and Unity to your desires.
[/LIST]

---

### Post by mörgæs on 2017-01-25
Thanks for posting. 

If you add a brief post to the [compatibility thread]("https://ubuntuforums.org/showthread.php?t=1543006"), possibly linking to this one, there is a better chance that people will find it.

---

### Post by jack rooster on 2017-03-26
Thanks for posting this [[COLOR=#000000]**matthewj15**[/COLOR]]("https://ubuntuforums.org/member.php?u=2056763")! I'm been using Linux as my main OS since 2012 (Linux Mint KDE), with Windows 7 installed in VirtualBox for those rare times I need it. Two days ago I bought an Ideapad 110s. I was thinking about leaving Windows 10 on it to "keep up with the times" but after two days of using it, "It's Linux Time!" I'm traveling right now but will follow your well written instructions as soon as I get home next week with LM Mate. I'll let you know how it went.

---

### Post by jack rooster on 2017-04-07
Worked perfectly! Didn't need to use my USB wi-fi dongle. Ubuntu installed using 10GBs less HDD space than Windows 10 and it uses half the amount of RAM when running.  Thanks again!

---

### Post by jack rooster on 2017-04-07
OOps. Spoke too soon. Neither the touchpad, nor the touchpad buttons are working. I just noticed it. I rarely use it (I'm a mouse guy) so I don't know if it hasn't been working since the installation or if it just recently stopped working. Any ideas?

---

### Post by thomasbu on 2017-06-04
matthewj15,

Thank you so much for your findings. I was having a hard time with the installation, but now it works perfectly. 

Cheers!

---

### Post by bobalu on 2017-07-03
Hi thank you very much for your post, I hesitated to buy a Lenovo 110S (because with a low cost configuration I did not want windows) but with your post I bought it ! So thank you.

I installed with success a Xubuntu 16.04.02 LTS ... but I still have a problem : the bluetooth is unstable when the Wifi connection is activated (the bluetooth is stable is the Wifi connection is not used).

For information, I formatted the ssd drive and I replaced Windows by Ubuntu.

Here my Bios configuration :[INDENT=2]- Wireless : Enabled
        - Hotkey Mode : Enabled
        - Intel Virtual Technology : Enabled
        - BIOS Back Flash : Disabled[/INDENT]
[INDENT]- Security[/INDENT]
[INDENT=2]- Intel Platform Trust Technology : Disabled
        - Secure Boot : Disabled[/INDENT]
[INDENT]- Boot[/INDENT]
[INDENT=2]- Boot Mode : UEFI
        - USB Boot : Enabled
        - PXE Boot to LAN : Disabled[/INDENT]
[INDENT]- Exit[/INDENT]
[INDENT=2]- OS Optimized Defaults : Disable[/INDENT]

I installed using a DVD drive from the ubuntu iso image, but i tried also using a usb key generated using the tool named Unetbooin. And before repairing the Wifi connection I used an usb network adaptor.

After the installation the wifi adaptor wasn't detected automatically, I fixed the problem with these commands :[INDENT]$ rmmod ath10k_pci
        $ rm -r /lib/firmware/ath10k
        $ mkdir /lib/firmware/ath10k
        $ wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.167_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.167_all.deb)
        $ dpkg -i linux-firmware_1.167_all.deb
        $ modprobe ath10k_pci
        $ reboot now[/INDENT]

So after reboot, the wifi connection is up.
But the bluetooth connection still unstable.
[INDENT]$ dmesg | grep error[/INDENT]
[INDENT=2][    5.103365] EXT4-fs (mmcblk0p2): re-mounted. Opts: errors=remount-ro
                   [    6.391298] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:03:00.0.bin failed with error -2
                   [    6.391337] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2[/INDENT]

And sometimes the service bluetoothd crashs.

I identified the adaptor :
[INDENT]$ lspci | grep "Network controller"[/INDENT]
            [INDENT=2]Qualcomm Atheros Device 0042 (rev 31)[/INDENT]

I tried a lot of thread regarding [COLOR=#000000][FONT=&amp]https://github.com/kvalo/ath10k-firmware.git but without success.[/FONT][/COLOR]

Do you have any idea to this issue ?

Thank you in advance !

Best regards

---

### Post by mark.travis on 2017-07-23
Hi Guys,

I am a windows developer and I have played with the Microsoft technology stack for years and to be truthful, I don't mind the direction Microsoft is taking. However, I am aware of the hardware requirements need to for me to do my job, and of course the cost of that hardware. Currently I am finding myself playing with .net core more and more so I thought I would look at what was required to create a minimalist .net core development environment so I started looking at Linux. A second, lesser reason for looking at Linux is that Docker seems to be a little unstable on Windows 10.

I have never played with Linux. I obvious know of it but work has never taken me in that direction. When I cam across this thread, I had just seen the Lenovo 110s in a local computer shop. They were trying to get rid of them because the 32gb drive was just not enough once you ran a significant update so I thought, what the hell, lets give this a shot.

Using bobalu's bios configuration and ubuntu 17.04 desktop for amd 64, I had the OS up and configured in 40 minutes. That is from opening an unsealed box to logging into the OS. I did not pass the windows install and I did not collection $200. That is astonishing. Almost everything just appears to work. The only problem I have is connecting my Logitech MX Anywhare 2 via Bluetooth. I will post again when I figure it out.

@matthewj15, thanks for starting this thread and the steps required to install the OS.

To any other Windows .net core devs out there, this is a viable solution moving forward.

Thanks again guys.

---

### Post by dayvkaos on 2017-08-12
Hello all!

I'd like to share my experience in successfully installing a flavour on my Lenovo Ideapad 110s. 

short version:

Goes to store and buys ethernet over usb dongle.
inserts to usb port on computer, connects ethernet cable to dongle.
Insert created bootable usb (you should have this made prior to doing all this).
In bios (f2 on bootup): Security tab>Secure Boot : Disabled (don't forget to save and exit).
In boot manager (f12 on bootup), select usb with image.
and go through the motions of any normal installation.
Log in, open terminal, sudo apt-get update && sudo apt-get upgrade.
done = happy camper.


Long version:

I first started out by creating a bootable usb from the installed windows. I first tried Debian, ran into the whole "non free driver" deal with wifi, then it didn't even recognize my card. I moved on to Lubuntu. I would go through the motions of connecting to wifi, creating a user name, password, and upon installation, it crashed stating it could not install kernel, boot loader. 
I moved on to ubuntu gnome and to my surprise it installed fully. I logged in then realized that I couldn't update it. My wifi bar appears connected to my network. I disconnect and connect to another, connects successfully but still nothing. Checked the browser, no connection. I was confused. I did some backtracking and noticed that on all my installations it was always to the default location of New York.

Aha moment in place, I then realize it's not really connecting to the internet, no data is coming through even though it appears so. It all started to make sense, especially when debian couldn't even figure out the name of my network card.

Luckily there's an electronics store not too far and picked up an ethernet over usb dongle. Came home, inserted usb to computer, inserted ethernet cable to dongle, power on,f12 to boot manager, selected my flavour and boom, it knows my location upon installation. I knew I was good from here.

---

### Post by noob2this on 2017-10-05
Hi ..Matthew ...can u tell me the process of getting   the ubuntu 16.04 usb disk   the whole process do i have to buy it or is it free...Sorry but this is a first for me to do ..Its been a bit  you might not get this but if anyone else reads this your help will be appreciated thanks

---

### Post by mörgæs on 2017-10-06
Looking over the thread is seems like 17.04 is a better option than 16.04. Installation is easy:

First install the USB creator program Unetbootin. It runs in both GNU/Linux and Windows.

Then download the Ubuntu 17.04 ISO file and transfer the contents of the ISO file to the USB stick using Unetbootin. 

Following the advice above you can now boot from the USB stick.

---

### Post by james-giambrone on 2017-10-16
Hello, very cool post! Just wondering if you are still using 16.04 on your 110s? If so, do you feel the hardware is performing well? 

I've been looking for a very small and light laptop that I can keep with me at all times without having to worry if I lose or damage it. I currently use a Lenovo Edge E530 and it works fantastic with 16.04, I just don't like lugging around a 6Lbs PC along with all my other work items.

I also have an older Acer netbook that's small and light but it's so slow even running Lubuntu it's painful to use. Any additional info regarding the Lenovo 110s and 16.04 would be great.

---

### Post by xmbwd on 2017-12-09
Great OP and supporting posts.  I believe that this post isn't so old that it is dead, so a few questions.

First, why did you wipe the entire hard drive.  I know 32 GB isn't a ton, but I'm curious if you could have shrunk the Windows partition and had a dual boot setup.  That is what I plan to try with the (hopefully similar) Lenovo Ideapad 120s.

Which leads to my second question:  has anyone tried this same install setup on a Lenovo Ideapad 120s?

---

### Post by xmbwd on 2017-12-10
FYIW, I was able to partition the 32 GB hard drive (using EaseUS Partition Tool -- which I'm a little suspicious of given its origins), leaving 10 GB for a linux install.  And I was able to get both Windows 10 and Fedora running on the Ideapad 120s.  That said, this machine only has 2GB and seems to crash every time I use any processor intensive applications (like FireFox).  Still -- the point is that you can run a dual boot system even on this small laptop.

NOTE: I switched to Budgie, and it works flawlessly on this laptop.  Fast and stable.

---

### Post by orlandoscarpa on 2017-12-26
Installed Xubuntu 16.04 on my new  Lenovo 110s-11IBR and everything is running smoothly. Did not need any wifi or ethernet dongle on installation, my connection worked fine throughout the installation process. At first i installed Ubunty Unity 16.04, but found that at times the system lagged a little. Decided to re-install everything using the Xubuntu installer and the machine is noticeably faster. It's my first time using Linux, I have used OSX for about ten years almost exclusively, and now and then use a windows machine at work. So far I am REALLY impressed on how stable and lightweight the whole system is. Decided to leave my main OSX machine for more intense work, and use this for writing, browsing and reading.

Also, I wasn't sure on how big my swap partition should be, so I decided to use 3gb. Is that too much? In case it is, is there some way to safely revert it? With only 32gb storage every Gb counts!

Had two minor issues: wi-fi was unstable after suspend, but found a lot of info on how to fix that and now it works. I was also getting some screen tearing with full screen HD video, but also found a quick fix for it online. I use Libre office, 3 or so tabs open on firefox and a pdf reader at the time without performance getting sluggish. With windows 10 this machine was a nightmare, everything was extremely slow. Also noticed a small improvement on battery life.

---

### Post by paul-onolan on 2018-01-06
FWIW I have installed Linux Mint 18.3 following these instructions. So far everything just works as expected. I was concerned that the trackpad might not but it did, as did the wi-fi and everything else. I have 4Gb RAM on order to replace the 2Gb it came with and have set aside a larger swap partition as result, but I'm not sure I really need it. If I'm not going to use hibernation do I need it at all?

The main issue I had was getting Windows 10 backed up, just in case I ever want to restore the machine to as new condition before passing it on. Windows backup failed, both backing up to my network and to a USB3 drive; and yes, I tried both more than once. I ended up using the free version of AOMEI Backupper, which worked without any issue, and gave me boot ISO volumes as well. Windows 10 then announced that it had a lot of updates for me and I thought I might as well let it update and then backup again. When I clicked INSTALL it then decided to start downloading them all over again, then it ran out of space. By that point I'd had it and I installed Mint. 

I tried Mint XFCE first and didn't like it, so moved on to MATE which I use on another PC. To my surprise MATE yielded more free memory on boot. Performance has been good and will improve once the memory arrives and is installed. 

Of course, I never had any intention of using Windows 10 (never mind dual booting, ugh). Total cost for the computer and memory was &#8364;215, and that's with the Windows tax. All in all, a very nice little machine.

---

### Post by tolebi992 on 2018-01-08
Hello everyone. I also installed Xubuntu 16.04. I did not need Wifi Usb dongle. all was installed itself. My lenovo began to work faster, smoothly and for longer.
Thank you

---

### Post by michael-z-freeman on 2018-01-26
Hi. I just got a Lenova Ideapad 110s and its the best laptop I've ever had for Linux support. Installing Linux is practically mandatory for this device (32gigs) as the preinstalled Windows 10 tries to update to latest Windows and after spending hours installing stuff eventually runs out of space; "10 gigs needed for installation". I followed the instructions at the top of the thread to install Ubuntu 17.10.1. I did not need to use a USB Wifi adapter as setup detected the built in Wifi. I installed using Ubuntu Mate ISO written to USB stick using Rufus, and now I've got Compiz turned on everything runs great! I have Bluetooth as well and all the special function keys work. I'm one happy bunny :)

---

### Post by natek2 on 2018-02-08
Just installed Xubuntu 17.10.1 off a USB drive. As others have noted, no wifi dongle was needed. Smooth install, everything works perfect as far as I can tell, and the system has gone from increasingly sluggish and frustrating to use under Windows 10 to the sleek, lightweight but functional one it was supposed to be all along.

---

### Post by jpilbeam on 2018-03-06
Hi matthewj15,Thanks so much for sharing these instructions! I bought a Lenovo 110s after reading this, I was looking for a lightweight laptop for email, note taking and Web development that I could just throw in my bike bag, instead of lugging around my MacBook Pro. Ubuntu 16 installed with no issues and the performance is great. I'd also add that I don't require a USB Wifi Dongle. I'm incredibly pleased with the laptop and OS :D

---

### Post by ringo-e on 2018-03-14
Can anyone confirm they've managed to get Bluetooth and sound through the headphones working? Bought one of these last week - an 100s-11IBY to be specific - and have had mixed results with Ubuntu 16.04.4, Ubuntu 18.04 Beta 1 and the latest version of Neon (all upgraded to the latest kernel using the script at Linuxium). Haven't managed to get Bluetooth working on any of them. For some strange reason sound through the headphone socket worked with 16.04 running off a USB stick but not once I'd installed it. Everything else works fine, with the possible exception of the untested HDMI. Currently running Neon and planning to stay with it but if anyone can confirm these things are working with a different version (and no more breakages!) I might be tempted to switch.

Even semi-functional it's a great little machine.

---

### Post by kerry_s on 2018-03-14
when you use a blutooth head set, sometimes you have to select it in sound-> output & select the type of sound(a2p,hfs,erc...)

---

### Post by ringo-e on 2018-03-14
You mean in Unity? Don't have it installed at the moment, but I'm fairly sure that even under Unity there was some kind of underlying driver issue with bluetooth before the system could get to the stage of routing sound to headphones or a speaker. As I recall the message I was getting was similar to what I'm seeing now in KDE, "no bluetooth adapters have been found".

---

### Post by ringo-e on 2018-03-14
Just to be clear - the headphone issue is a whole separate thing. It's the headphone socket which isn't working, not a set of bluetooth headphones. Though they wouldn't work either, if I had them. Because I don't have bluetooth working yet.

---

### Post by kerry_s on 2018-03-14
since your os jumping, try elementary os, runs great on those low spec rigs.

my bag, i missed read. i thought it was working but you didn't have sound in the headphones.

---

### Post by ringo-e on 2018-03-14
I might just try elementary tonight. Don't think I've got the patience for a full install right now but it would be interesting to see how it runs, though to be fair KDE is running much better than I'd expected so I don't have any real performance issues for the type of basic stuff I'll be using it for.

---

### Post by kerry_s on 2018-03-14
> **ringo-e said:**
> I might just try elementary tonight. Don't think I've got the patience for a full install right now but it would be interesting to see how it runs, though to be fair KDE is running much better than I'd expected so I don't have any real performance issues for the type of basic stuff I'll be using it for.

i'm just saying the main purpose is to provide more ram towards running netflix in firefox. you been running heavier de's which will leave you very little ram, so it will start swapping which will make things freeze/lag/stutter/etc....

eos is bare bones from the get go. you'll have to install firefox from the app center. 
just a reminder with them everything is opt in when it comes to money, just chose custom, put 0 & download, same go's in there app store you can put 0 & download for free.

if you like it you can always donate later. :) i used for years on my hp mini, it had 2gb's ram, so i donated a few times.

---

### Post by ringo-e on 2018-03-15
Tried elementary last night, off a USB stick. Seemed to work well on this machine but it's not for me, I'm the type who thinks KDE doesn't have quite enough customisation options. Video playback is okay as it stands. I've had no problems watching shorter videos on youtube (five minutes or so). I tried watching one longer video (around fifteen minutes) and it was very choppy, almost unwatchable. But I've got other machines to watch movies on so that doesn't bother me so much, the Lenovo is mainly for reading and writing. And maybe listening to (local, not streaming) music if I can get the bluetooth working!

---

### Post by kerry_s on 2018-03-15
yeah but kde is the heaviest desktop in linux. if you like to tweak stuff ubuntu-mate or xubuntu would be a better choice. any linux can actually be tweaked, some are just easier.
did you try that smtube app? it plays youtube vid in the player of your choice.

---

### Post by ringo-e on 2018-03-15
You're very persuasive! At the risk of going too far off-topic, of the two distros you suggest which is better for tweaking icons, especially app icons? I know it's trivial to most, but I've a bit of an obsession with stripping out as much branding as I can from my desktop. Crazy, possibly, but I can get 60% or 70% of the way there with KDE and I'm reluctant to give that up.

Not tried SMPlayer yet. Looks promising, thanks for the tip.

---

### Post by kerry_s on 2018-03-15
xubuntu then, you can change the menu icon, right click-> properties.
there's plenty of icon themes
all kinds of window themes.

it's smtube, for the video player just use your favorite. i'm using totem for example. you just move the 1 you want to the top of the list, you can even add a player if not listed.
[ATTACH=CONFIG]278950[/ATTACH]

---

### Post by arya-pill on 2018-04-01
Upgraded this machine to bionic 18.4 today. Except sound everything works fine. I tried all the solutions available online but haven't solved the sound issue. Also I was unable to find the alsa driver for bionic. 

Although all my systems have been lenovo and I never faced any issues other than this one, I am regretting buying this machine. I agree price is too low but considering how slow the machine was with all the windows bloatware and the 32 bit bios issue, makes me wonder I made a mistake with this. Ubuntu is fast and efficient as of now, but sound is undeniably a major issue. Hopefully once bionic stable release is available the stability issues will go away.

---

### Post by artem-lenovo-120s-11iap on 2018-09-05
Thanks for your posting, matthewj15 ! It really helped me to install Lubuntu on my brand new Lenovo IdeaPad 120S

---

### Post by parkerl on 2019-02-15
I've got an Ideapad 110 whose drive I'm trying to backup.

I can boot Clonezilla from a DVD, but it doesn't recognize anything plugged into the USB.. which will be used to save the hard drive image to.   

Sounds like Ubuntu/Mint might have working USB drivers for it.. is there a way to install it into Clonezilla... or  alternatively, is there a version of a live Ubuntu distro that can backup a hard drive image onto the usb /  restore a partition from an image file?

---

### Post by Solostian on 2019-07-22
I had the 110S running smoothly for a while until I droppped it from 2 floors. The screen shattered but it kept working with an external monitor.
Ordered a new screen the installed it. While I was at it, I decided to upgrade the Linux version.
In my haste, I deleted the EFI partition during the installation process.
Now, it won't boot from the SSD.
Do any of you know how to get from under that rock?

Cheers,
Solostian

---

