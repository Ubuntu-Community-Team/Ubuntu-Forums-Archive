---
title: "My Successful Install of ubuntu netbook 10.04 on a HP Mini 210-1084NR"
date: 2010-08-19
forum: Ubuntu Moblin Remix
---

### Post by triwave on 2010-08-19
I recently ordered a HP Mini 210 Netbook with Windows 7 Starter on it. My intention was to load Ubuntu Netbook 10.04 or maybe an alternate Linux netbook edition. The specific model I ordered was a Mini 210-1084NR which didn't have a lot written on it since it was new, but thought I'd give it a try given the positive reviews of 10.04 and the HP mini series in general. Major difference on this netbook (at least compared to others at the time of ordering) is the wireless card which supports 801.11b/g and N , the newest and fastest version of 802.11 WiFi.

I powered the machine up with the included Windows 7 Starter and was less than impressed. There is so much garbage and bloatware the machine is  sluggish, at least compared to a regular and more powerful Laptop. Try to get to the internet and you'll have virus scanning, windows updates, HP software updates and various free trials popping up. To be fair, once all this stuff is done it does get a bit better, but if you are an occasional user this stuff will happen fairly regular because the updates occur quite regular also. I'm not a Windows fan at the best of times, if I were I may not have bothered to try something else, but trying to be objective I still state the difference in usability of this machine with Win7 and Ubuntu is very different. The Ubuntu system is more responsive, boots faster and is infinitely customizable. It's also cheaper - living with Windows I have to shell out for Anti-virus protection and buy several programs and licenses to be productive plus potentially upgrade the Win7 Starter to something more useful. Your exact use and program needs will of course vary so judge for yourself. On my Ubuntu system I have spent $0. Period.
 
The new card which I couldn't research proved to be the only real issue, but it turned out that was only an issue with the live USB I created. The broadcom drivers need to be downloaded and re-booted, couldn't get that to work on the live USB but when I installed the system to disk the drivers worked like a charm. 

You need a wired Ethernet connection to first to download the updated drivers - so have a connection available to plug-in to when doing the install and wireless setup. I did the install and then checked for system updates (via Ethernet) - there were quite a few updates available so I used Ethernet to download and install all the updates, getting the Broadcom drivers in the process.  After re-boot the wireless worked, I unplugged the ethernet and haven't plugged in it since ...   I've connected to open networks, WEP encrypted networks and WPA2 encrypted networks (both personal and infrastructure) - all have worked as expected. 

What works: Sleep, hibernate, screen resolution, external monitors, extended desktop, wireless, wireless modems (3G Samsung in my case), keyboard, mouse and touchpad. 

What doesn't work: nothing major. In the minor category there is windows network browsing with Gnome. I really don't think this is specific to the HP Mini nor to the netbook re-mix - it seems a fundamental problem in the ubuntu / gnome lineage. All my ubuntu based desktops has similar challenges .... mounting and sharing files is no problem when you know what to mount to. The network browsing utility is supposed to be like windows, just click and the workgroup and browse the different machines on your network. This portion is flakey. A simple work-around is to create bookmarks in the places folder of commonly mounted drives/machines. Clicking the bookmark will immediately mount them without having to use the browse function.

What is different: The F12 wireless on/off button works in Windows, in Ubuntu you turn the wireless on/off via the Network Manager applet.  I noticed that if I work with WiFi off and then put PC to sleep, it comes back on when the computer resumes from sleep.  Nothing major, but I noticed it when I was on an airplane and had to turn it off again. Touchpad seems slightly different in win and ubuntu - neither is great in my opinion - much prefer an external mini-mouse when available. When religated to the touch pad the use in ubuntu is slightly better - the scroll bar works better. In both cases the pad is sensitive to touch and I occasionally select things I didn't intend to. I have not found a way to change this but it's very possible there is a setting buried somewhere.

How I installed it

The Win7 loaded on the system used all four possible primary partitions so It wasn't obvious how to add new partitions for ubuntu and preserve the Win7 for a dual boot configuration. Secondly, there are no windows recovery disks - there is a recovery partition which helps if you bork something, but doesn't help if your harddrive dies. I have no external CD for my unit so the hassle of finding one and making recovery disks was another strike against M$. I ended up making an image of the whole hd as it came from the factory so for a complete re-install (like selling the netbook) I will just re-image the complete drive. 

After having a recovery image I began playing. Working off the live USB I ran GParted and deleted the recovery partition. Then I shrank the Windows System partition freeing up approx 100GB of drive space. I created an extended partition and then three logical partition inside that : one for root (/) , one for user directories (/home) and a SWAP partition. I then installed the system to these partitions (using manual configuration, not automatic configuration) and re-booted. I was greeted with a Grub screen allowing me to select win or ubuntu  :)   After that all was well.

I added a few additional apps I find useful:

• Grsync : a front end for rsync - a universal and solid backup/imaging tool I use to synchronize files on the netbook and my network storage device (via SSH)
• Google Chrome - while I generally like Firefox, I found Chrome much faster on this system. It's very quick, faster than my desktop.
• Skype : works great with built in speakers, webcam and mic ; your PC is like a speaker phone
• VLC : my prefered media player - seems to play anything I can throw at it (even over wireless)
• TrueCrypt : there are probably good Linux encryption tools also, but I like this one because it's cross platform. I have an encrypted USB I need to open on windows machines at work as well as linux machines at home
• Hulu : a little TV in the hotel never hurts
• Last.fm client : easy way to listen to streaming music with your taste  

Overall I'm very happy with this hardware and the OS running on it - what a great combination! Battery life is forever ... honestly, I don't know how to benchmark it but I can use it virtually all day without plugging in. It's light and powerful enough to access your media, websites, etc.

---

### Post by atr_hugo on 2010-08-24
Want to echo those thoughts. I picked up an Asus Eee 1005HAB and was able to load the netbook remix painlessly. Windows 7 Starter is a joke. It's nice to have a decent OS on the machine.

---

### Post by saxophobe on 2010-08-28
I recently installed UNR on the exact HP model that you have and had an extremely similar experience.  I did a custom install and just wiped out the main windows partition and made a / partition and a swap.  

You are right; this system is WAY more responsive on UNR than it was on the Win 7 Starter version it came with.

This is the most pain-free install that I have ever done on a *nix system!

I'm keeping this one!  8-)

---

### Post by Rescue Penguin on 2010-08-28
I just recently got an HP Mini, a week after my wife got an Acer netbook. I happen to like HP products. I ran into the same problem, 4 primary partitions used. I tried to rearrange things only to have an "oops" moment. 

I called HP support, they gave me the option of obtaining a USB drive with the image on it, but recommended that I send it in to have the software reloaded. I was told I would get a call from the department that would handle it.I got the call the next day. The lady insisted that I had to send it in. Every time I mentioned the USB drive, she ignored me. Not wanting to send it in on a regular bases until I got Ubuntu on it, I chose to exercise my retailers 2 week return policy. Before I did, I checked out my wife's Acer for the partition table. I now own an Acer netbook and not an HP. I rarely use Win7, but choose Ubuntu instead.

                Steve

---

### Post by pr1vatepiles on 2010-09-07
got the same hp laptop and like you really didnt like windows 7. brand new to unbuntu and within five minutes was loving it. just going to install the wireless drivers using instructions ive found on here. just brill so so easy :D

---

### Post by tim183 on 2010-09-11
I am currently installing Ubuntu netbook remix on my HP Mini 210.

I want to keep the windows recovery partition just in case I need to ever send the machine back to HP for repairs etc.

There appears to be 4 partitions available.

Which do I keep/where do I install the Ubuntu?

---

### Post by triwave on 2010-09-12
Are you trying to dual boot with Win7 or are you willing to blow that away? If you want to keep Win7 and Dual Boot the recovery partition is the one I blew away to install ubuntu to.

My rational was: a) I made a backup of the whole disk as it came from the factory b) you could probably make a disk image of the restore partition c) you can create recovery disks with an external CD burner  d) you can order recovery disks from HP.   With all those options I chose to blow away the recovery section.  This left me with a small boot partition, the NTFS (Win7) partition, and another small FAT partition windows uses for some diagnostics. If I knew what that one was I'd have considered blowing it away instead but was unsure it's function...

---

### Post by camorri on 2010-09-14
I bought my HP mini, looked at the four primary partitions, and the poor win 7 performance, and decided to blow away win7. I created a primary partition, an extended partition + swap and installed. 

Ubuntu is fast, much faster than I thought it would be on the N450 processor. Makes win 7 look slow. 

As far as returning this machine, I'm not worried. It should run the year for its warranty. After that, I can fix most things, if I can get the parts. As for selling it, don't think I want too. I bought this for a traveling system. It does everything I want, including network testing. 

It took some time to get the touch pad mouse to settle down. I installed gpointing-device-settings and was able to get the touch pad to behave. It is mow useable, although I prefer an external mini mouse. 

Wireless on this system is Antheros, and worked from the day I installed. :D

I run the standard Gnome desktop, not the netbook big icon one. 

Great battery life with the six cell battery. 

This is a keeper. :D

---

### Post by triwave on 2010-09-14
> **camorri said:**
> I bought my HP mini, looked at the four primary partitions, and the poor win 7 performance, and decided to blow away win7. I created a primary partition, an extended partition + swap and installed. 

Ubuntu is fast, much faster than I thought it would be on the N450 processor. Makes win 7 look slow. 

As far as returning this machine, I'm not worried. It should run the year for its warranty. After that, I can fix most things, if I can get the parts. As for selling it, don't think I want too. I bought this for a traveling system. It does everything I want, including network testing. 

It took some time to get the touch pad mouse to settle down. I installed gpointing-device-settings and was able to get the touch pad to behave. It is mow useable, although I prefer an external mini mouse. 

Wireless on this system is Antheros, and worked from the day I installed. :D

I run the standard Gnome desktop, not the netbook big icon one. 

Great battery life with the six cell battery. 

This is a keeper. :D
cammori - just to be clear and maybe help others ... what model mini are you referring to?

Mine definitely has a Broadcom card (b/g/n compatible) and getting those drivers to work is perhaps the only real "out-of-the-box" issue, although easily fixed when updated.

Do you have a different model? 

Also, what driver did you use for the wireless card and did it work "out-of-the-box" ?

---

### Post by camorri on 2010-09-15
My HP Mini is a 210-1000, product number WD269UA#ABC. 

Wireless driver ath9k.

---

### Post by KristinaK on 2010-09-23
how it works on 1920 x 1080 resolution, 24 inch display? external monitor?

Have you tested 10.10?

---

### Post by triwave on 2010-09-23
> **KristinaK said:**
> how it works on 1920 x 1080 resolution, 24 inch display? external monitor?

Have you tested 10.10?

Don't know about 10.10 , but I have used it with an external display that is 1680x1050 20" Monitor , works fine with extended desktop. You can also shut down the laptop monitor, and use the external display as your primary display with a much bigger desktop ...

---

### Post by slycooper on 2010-09-24
Did anyone installed a dual boot system? If yes then can someone post the detailed instructions?
Can I test it via Live USB? 
I have bought HP mini 210 for my wife over last weekend and Windows 7 sucks. Since that system belongs to my wife, i just want to be cautious :)

---

### Post by triwave on 2010-09-24
> **slycooper said:**
> Did anyone installed a dual boot system? If yes then can someone post the detailed instructions?
Can I test it via Live USB? 
I have bought HP mini 210 for my wife over last weekend and Windows 7 sucks. Since that system belongs to my wife, i just want to be cautious :)

My description that started this thread **is** a dual boot system. I didn't write a detail step by step guide but I explained how I did it - you have to give up a windows partition somewhere because they use up all 4 primary slots in the factory install so think about what your willing to do there ... or make restore disks in case you mess up ...

---

### Post by slycooper on 2010-09-25
Sorry for the confusion. My question was specific to installing it in the same partition of Windows 7 i.e. without resizing or creating a new partition. Will it work?

---

### Post by slycooper on 2010-09-25
I managed to install ubuntu netbook 10.04 in the same partition (without partitioning). I used wubi installer and the installation went well. Also I managed to get drivers for all the hardware components including broadcom wireless.

---

### Post by triwave on 2010-09-25
Cool slycooper, now I know what your question was ... I didn't use WUBI because there seems to be a bit of a performace hit with that method, at least on my older laptop, so figured on an Atom system there isn't much to give up either, but it's definitely easier than resizing partitions! After you play a bit please post again on your experience with speed, responsiveness, etc. using WUBI install.

---

### Post by pearlie on 2010-10-01
I removed the HP_Tools partition to get the slot I needed on my Mini 210 so I could repartition & install UNR - there was only one diagnostics file in there, which I backed up to another system... this left the windows recovery partition intact. (The Tools file is also available for download from HP Support... so, not too worried about losing it.)

Don't know why I bothered keeping windows 7, really - I haven't used anything but Ubuntu for years now.

Now I just have to figure out how to tether the little beggar to my Blackberry...

---

### Post by triwave on 2010-10-01
> **pearlie said:**
> I removed the HP_Tools partition to get the slot I needed on my Mini 210 so I could repartition & install UNR - there was only one diagnostics file in there, which I backed up to another system... this left the windows recovery partition intact. (The Tools file is also available for download from HP Support... so, not too worried about losing it.)

Don't know why I bothered keeping windows 7, really - I haven't used anything but Ubuntu for years now.

Now I just have to figure out how to tether the little beggar to my Blackberry...

Cool. I don't know about how the HP_Tools partition works, I never use windows either, but assumed it's disaster recovery of some sort...  Do you know what that partition really does?

As for Blackberry I hope it works OK. I have a 3G Samsung phone (A777 with AT&T) and I was able to tether no problem.  First I did it with a USB cable and that was fine and completely automatic setting it up. Then I tried Bluetooth and that worked just fine too ... so now I just connect via BT if I need to check e-mail , no cables, no wires, no fuss  :)  Hope it works just as easy for your BB.

---

### Post by ultrastevep on 2010-10-07
This is so confusing....I keep getting "No root file system is defined" when I select a partition. In an another dual boot step by step it said that while installing it will choose the next open partition. I guess I have no idea what I'm doing and am afraid of effing up my HP netbook.
What exactly do I do when in the partition screen of the install?

Thanks....

---

### Post by camorri on 2010-10-08
ultrastevep,

You need to open your own thread to get assistance. This thread was a success story. I know you need help, so please open your own thread.

To try and help here, you need to know what partitions you have, and what is on them. It also helps to know the partition types you have. 

How big is the disk in the HP mini? What partitions do you have now, and what do you want to preserve? 

Open a new thread, put in the answers to these questions, as information, and I'm sure you will get help.

---

### Post by codenix on 2010-10-31
> **triwave said:**
> I recently ordered a HP Mini 210 Netbook with Windows 7 Starter on it...

Thank you triwave - your post encouraged me to choose the HP Mini 210 over other options, and my experience exactly matched yours.

I created an Acronis recovery boot image on a USB stick (which is easily done with their product), and used this to first make an image of the factory Win7 installation.

I then loaded the Ubuntu live CD (10.04), onto a USB stick, using the included application via a Windows 7 machine, and used this to install Ubuntu, removing the factory partitions during the installation.

Remembering your post, I plugged in an ethernet cable prior to the install, so when I first logged in I was able to run the updates. The Broadcomm drivers for WiFi were offered via the systray popup, which I accepted, and was then able to join my wireless network after a reboot.

Overall my experience with Ubuntu Netbook edition on this device ***vastly*** improves upon the Windows 7 Starter experience. The OEM build was slow and bloated with HP stuff, and the trackpad was almost unusable. For example, the scroll function didn't seem to work on Win7, but on Ubuntu works fine. There's also more control on Ubuntu, whereas Win7 seemed to jump all over the place (which may have been due to the excessive running processes eating up system memory).

The only issue I had, which was easily resolved, was that Evolution didn't load with the 'opensync-plugin-google-calendar', which is required to use a Google calendar in Evolution. A quick search revealed the problem, and this library was available via the software centre.

Thanks again,

Codenix.

---

