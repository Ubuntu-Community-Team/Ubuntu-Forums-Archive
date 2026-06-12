---
title: "HowTo: Sony VPCCW21FX"
date: 2010-05-13
forum: Tutorials
---

### Post by Dark_Stang on 2010-05-13
[CENTER]**I am no longer updating this as of April 2011**[/CENTER]
Sections:
1.Intro
2.What doesn't work
3.What you will need
4.Installation – Briefing
5.Post-Installation – Where you're at
6.Wireless Card
7.Graphics – 256 and 260 drivers covered
8. HDMI Audio
9.Closing notes
10. Link to new kernel image and headers

1.This guide will tell you how to get Ubuntu up and running on a Sony VPCCW21FX laptop. This guide will use Ubuntu 10.04-64bit for installation. There are 2 main problem areas that you are going to run into, and these will be the focus of this guide. If you are looking for step-by-step installation directions, please use some google-foo or look into the absolute beginner forum. There are loads of guides there. It isn't that I don't want to give you step-by-step installation directions, but I don't do normal Ubuntu installs anymore so I do not want to give out half-right statements to any first-time users. 

2. Wireless - The built in AR9285 wireless card drops packets like an armless juggler. If you compile a new kernel, or install the latest wireless drivers, it works a little better but is still far from reliable.
Video stuff - As of the nVidia 256.53 drivers, HDMI works fine. I have not tested VGA. Brightness controls still do not work.

3.What will you need?
1.Alternate or Network Install disc for 10.04 Ubuntu (normal install had no video for me)
2.Network cable (wireless doesn't work very well “out of the box”)
3.Some time – An afternoon to dedicate to this would be nice.

4.As I stated earlier, this isn't a step-by-step guide. Go ahead and install Ubuntu using your alternate or network install disk. Installation is normal (and pretty fast depending on your connection speed) for this laptop. I would recommend keeping your /home partition separate, as you may want to reformat / in the future. I know I will be doing that now that I have everything working.

5.Okay, the installer is done doing it's thing and it's asking you to restart. Go ahead and pop the disc out and reboot your laptop. At this point one of two things is going to happen. You will either have absolutely no video, or you're you'll bad video. If you have no video, read below. If you have bad video, move onto section 6.

No video – Hah, sucks don't it? Okay, reboot again (just hold the power button down to shut it off). Hold the shift key as it starts back up. The GRUB menu will load asking you what OS you wish to start. The default option should be selected, press 'e' to edit the boot lilne. Next to "quiet" add a space and "nomodeset". Then press CTRL + X. (thanks onhafoghefifo) You will have to remember this step until you get the nvidia drivers installed on step 7.

6.At this point your wireless card appears to work. And it does to a point... packet loss plagues this card. If you wish to improve it a little you will want to install a newer kernel (2.6.36.2 kernel at end of this document, or compile your own).

I ended up replacing my wireless card as I stream a lot of media to my PS3 and I like to game on this thing. For normal use you can probably put up with the crap Atheros card. However for best results I highly recommend getting a different one. I went with an Intel WiFi Link 1000 card.


7.Now for video. You may have a desire to simply download the nVidia drivers Ubuntu provides. Just say no to this method, only madness and headaches will follow for the 310m card that's inside this machine. Instead we'll download the latest from nVidia's website. Go to nVidia's site and download some drivers (any 256 driver will work, and 260.19.29 works, other versions may or may not work. After the drivers are downloaded you have to quit X and install them from command line. Pay close attention to where you've saved them (home folder makes things easier).

Press Ctrl+Alt+F1 to be dumped to a terminal. Login. Run the following command to shut down the X server.
```
sudo service gdm stop
```
Now navigate to where you downloaded the nVidia drivers. If you saved them to your home folder, you're already there. For first timers... Use "cd" to change directory. Use "ls" to list the items in your current directory. To mark the nVidia drivers as executable use the following command...
```
chmod +x NameOfNvidiaDrivers
```
To install the nvidia drivers use the "./" command, as follows...
```
./NameOfNvidiaDrivers
```
./ means "Run this file that is in the current directory." Simply typing the files name will attempt to run a file location in /usr/bin rather than the current directory.

Towards the end of the install the drivers will ask if you would like to run nvidia-xconfig. Go ahead and say yes and continue on.

8. HDMI Audio - Doesn't work by default. Below are the steps I took to correct this on my system, I'm not sure if all steps are required.
It looks like the 260 drivers from nVidia (260.19.29 right now) work for video. 

Huge kudos goes to this wiki.
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) 

However in case anything changes, I will post exactly what I've done here.
1. I upgraded my nVidia drivers to 260.19.29
2. I updated my Kernel to 2.6.36.2 - Not sure if this step is needed, but .debs of this are at the end of this post.
3. Added the following line to /etc/pulse/default.pa
```
load-module module-alsa-sink device=hw:1,7
```
4. Make sure your device isn't muted in alsamixer. Run 'alsamixer'. Press F6. Choose HDA NVidia. You can unmute all of them if you want, but it's the 2nd option on our laptops so that's the only one that doesn't need to be muted.
5. Reboot (remember to use 'nomodeset' if you need it)
6. Open up your Sound preferences (System > Preferences > Sound) and choose your new output device (High Definition Audio Controller)

9.That's it. You should be up and running now. Just remember that your wireless card **will** disappoint you until you replace it or Atheros finally fixes the packet loss issue.

As of April 2011 I am no longer updating this guide. Ubuntu has steadily moved away from "bleeding edge but buggy" and more towards "stable but old", and that's not something I want for personal use. I have moved to Debian unstable. Ubuntu, I'll still see you every day at work. I hope we can still be friends and that things won't become awkward.

10. Links to kernel headers and image...
[http://darkstang.com/vpccw21fx/linux-headers-2.6.36.2-ds_2.6.36.2-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-headers-2.6.36.2-ds_2.6.36.2-ds_amd64.deb)
[http://darkstang.com/vpccw21fx/linux-image-2.6.36.2-ds_2.6.36.2-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-image-2.6.36.2-ds_2.6.36.2-ds_amd64.deb)

---

### Post by jjchm on 2010-05-23
Hi, First thanks for excellent post, i buyed this model of laptop VPCCW21FX and i would like my Ubuntu 10.04 work in my laptop, but don't work, i follow your steps, install in alternate mode because normal install dont work, but in the section 5, when i should choose (if i have no video yet) Ubuntu recovery mode, i have no video too, black screen in recovery mode, i can't enter to console for modify the xorg.conf file, same result when i booted in normal mode. Please, i need a help, thanks for your time.
 
Ubuntu Rocks.

---

### Post by Dark_Stang on 2010-05-23
Interesting. There may have been an update to the .iso since I initially installed. I am working on a solution for you.

Edit: Okay, try this out.

Pop the alternate install CD back in and restart the computer with that in it. It should load the main menu of the CD again.
Choose "Rescue a broken system" from the options.
Go through the menus as normal until you get to "Choose Root FileSystem."
Pick your root filesystem and choose "Drop to root shell." If you choose the wrong partition don't worry, you'll just get an error message.
Once you're at a root shell prompt navigate to /etc/X11 .
Now run "nano xorg.conf" .
Make your way down to the Driver option and change it to "vesa".
If there is a module section, delete it.
Now save the file (Ctrl + O) and exit nano(Ctrl + X).
Type "exit" to exit the root shell, then choose reboot the system.

Hopefully it should work for you now... Let me know how it goes.

---

### Post by jjchm on 2010-05-25
Humm i'll try your tip, i can't test now your tips, i'm travelling now, but thanks by your time, i really appreciate your help, we are in contact. Thanks again.

---

### Post by jjchm on 2010-05-29
Hi, i tested your tips, i booted with alternate install cd, and select rescue a broken system and navigate to /etc/X11, but don't have a xorg.conf file, instead i have a xorg.conf.failsafe file, very curious, so i checked the content of that file (xorg.conf.failsafe), and i found the line driver "vesa", so i use the cp command (cp xorg.conf.failsafe xorg.conf), and reboot the system, but same result and normal and recovery mode, black screen, so, i like that shows me your xorg.conf file for compare with my file. I think that my file is incomplete and don't start the graphical mode.  And finally what do you think about that i don't have a xorg.conf file. 

Thanks by your time.

---

### Post by Dark_Stang on 2010-05-29
All right. Go ahead and get back into /etc/X11. Copy the file xorg.conf.failsaif to xorg.conf. To do that just run...
```
cp xorg.conf.failsaif xorg.conf
```
Make sure the driver line reads vesa. Then reboot and see if video is there.

---

### Post by onhafoghefifo on 2010-05-31
Hi, first thanks for the post, surely did help a lot of people, but it didn't work for me. I buyed one VPCCW21FX laptop and would like to use it with ubuntu lucid. Got the same problems, and found how to solve the graphics part on the internet. However never found a way to make my wifi work as it should. I followed all the steps in your tutorial, but never got any far from connecting to my router. Packet loss happens all the time, making it impossible to use. I've tried so far:
* installed the linux-backports-modules-wireless-lucid-generic
* compiling the most recent kernel following your steps: 2.6.34
* compiling it and using the compat-wireless for 2.6.34 kernel
* even tried to activate network boot on BIOS because I read it somewhere that a guy did it and his wifi started to work as it should after installing backports modules
after so much failures I don't know what else to do
my last options as I can see now are trying madwifi and ndiswrapper, but I read that it won't work with the AR9285 wireless card.

Please help me!!!

Thanks in advance

NOTE: my wireless works just fine with windows, so that is not hardware problem

---

### Post by Dark_Stang on 2010-05-31
Did you download and install the kernel that I have posted? How did you solve your graphics issue?

---

### Post by jjchm on 2010-05-31
Onhafoghefifo, How did you solve your graphics problem? Please tell us, i'll go crazy working with windows7.

Thanks by your time,

Ubuntu rocks.

---

### Post by onhafoghefifo on 2010-05-31
I've installed my ubuntu from live cd.
To do so after selecting your language when booting from live cd press F6 and check the "nomodeset" option, and your video card will work.
After installing it restart your pc, and when the grub menu shows up press 'e'. Add next to _quiet_ the word _nomodeset_, and then press CTRL + X.
To make my video work I followed the steps of this post: [http://newyork.ubuntuforums.org/showpost.php?p=9058304&postcount=9](http://newyork.ubuntuforums.org/showpost.php?p=9058304&postcount=9)
But instead of installing nvidia packages from apt-get I used the latest binary package from nvidia site (at the time is 195.36.24): [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Dark_Stang, I've downloaded the kernel version you used, but didn't give it a try yet. Planning to do so this evening. But theoretically shouldn't the newer version work just as fine? I've downloaded also the compat-wireless bleeding edge drivers. If this fails, I don't know what else to do.

jjchm, I'm going crazy to work with windows 7 too. I need my ubuntu working perfect asap. It's such a pain having to manually install all the tools that I could just apt-get in ubuntu.

---

### Post by Dark_Stang on 2010-06-01
First off: Thank you for the solution to the video issue. As long as it get's confirmed I'll edit the first post for that solution.

Second: The wireless issue is a weird one. The 2.6.33 kernel that I have provided uses the stock settings with one exception, I turned on some new debuging features for ath9k. This may have been the fix. Give it a shot and see if it works for you. If you want to track it, I'd say follow these.
[https://bugzilla.kernel.org/show_bug.cgi?id=15313](https://bugzilla.kernel.org/show_bug.cgi?id=15313)
[https://bugs.launchpad.net/linux/+bug/518818](https://bugs.launchpad.net/linux/+bug/518818)

---

### Post by onhafoghefifo on 2010-06-02
I looked at the links you posted and saw that another person had problems with 2.6.34. Maybe you really did the fix =)
I tried to use the kernel packages you provided, but all that I could get after installing the .deb packages was a 'kernel panic'. I will download those again and give it a retry. But if it fails again could you send your kernel config file for me to try it out?

Thanks

---

### Post by Dark_Stang on 2010-06-02
That's weird. You are running a 64 bit system, right? Here is the config I used.
[http://darkstang.com/vpccw21fx/kernel-config](http://darkstang.com/vpccw21fx/kernel-config)
Like I said, the only thing that I really changed was the ath9k debugging, which means some extra things are turned on. But I figured I can always go back and recompile if I want to.

---

### Post by jjchm on 2010-06-04
Onhafoghefifo, i have a question, the nomodeset option should  always be written in the grub menu to avoid the problems with the "blackscreen"???? I ask because without option i have a blackscreen.

Thanks by your time, and your help, i wrote this message with my vaio vpccw21fx running the marvelous Ubuntu 10.04.

---

### Post by onhafoghefifo on 2010-06-05
Dark_Stang, yes I am running a 64 bit version. I've just tried again and again got a kernel panic. Also tried to use your kernel config file, but ended up in the same kernel panic problem.
Is your wifi working flawlessly? I don't know what and if I am doing something wrong.

jjchm, unfortunately yes. I don't remember what I did the first time to get it work without the nomodeset option during boot, but it can happen. I think it was because first of all I tried to install the nvidia driver from apt-get. When I did it, I could boot without the nomodeset option, but I got a really weird screen on startup. It was like my screen was divided in 2 columns and 3 rows, but the last row was missing, the first 2 rows were 1 row below they should be, and the 2 columns were in the wrong position. After that I installed the driver from nvidia site, and it worked as it should, without nomodeset. Is your wifi working flawlessly? I have about 40% packet loss even when pinging my router, like Dark_Stang said in one of those bug tracker sites.

---

### Post by Dark_Stang on 2010-06-05
onhafoghefifo: My wireless is working 100%, as far as I can tell. No packet loss and no crazy high ping times. Torrenting, streaming media to my PS3, playing online games (including WoW through WINE), surfing the web... You name it, and it works. I don't understand why you're getting a kernel panic. And I really don't understand why you'd have a kernel panic if your laptop compiled the kernel. You don't have anything added to your boot lines for grub, do you? Also, you copied over or made the ramdisk image, right? I forget that every time I compile a new kernel.

jjchm: Have you installed the nVidia drivers yet? After you do that you shouldn't need nomodeset in the boot line.

Edit: If either of you are on try hitting me up on gtalk. 
[email]DarkStang@gmail.com[/email]
If I'm at work I won't be able to help you, but I'm always on it.

---

### Post by onhafoghefifo on 2010-06-07
jjchm, any good news from your side? I've tried basically anything and my wireless still the same. Couple of things left to try. Have you managed to make it work?

---

### Post by jjchm on 2010-06-07
Dark_Stang: I'll tell you what i did to run the screen of my vpccw21fx, first install ubuntu in alternate mode (live CD don't work in my vaio) with the nomodeset option activate, when the installation finishes i can boot my ubuntu 10.04 in normal mode but with bad graphics so i install the drivers of de nvidia official site (195 version, i think, the latest), i followed your steps of the first guide, kill the gdm, and i used your xorg.conf, don't use the sonycw.bin, with this i could get working with Ubuntu 10.04 in my vpccw21fx. I need activate the nomodeset activate for working, if this option is desactivated, i got a black screen.

Onhafoghefifo: I have not worked yet with the wireless, in my home i used the internet with UTP, so i can't play with the wireless :), but in my work i'll play with this, i like to try first with the compat-wireless.

Ubuntu rocks, thanks to all.

---

### Post by jjchm on 2010-06-07
Onhafoghefifo: You tried this method?:

[http://wireless.kernel.org/en/users/Download#Selecting_your_driver](http://wireless.kernel.org/en/users/Download#Selecting_your_driver) (Check the part "Getting compat-wireless on Ubuntu")

---

### Post by Dark_Stang on 2010-06-07
> **jjchm said:**
> Dark_Stang: I'll tell you what i did to run the screen of my vpccw21fx, first install ubuntu in alternate mode (live CD don't work in my vaio) with the nomodeset option activate, when the installation finishes i can boot my ubuntu 10.04 in normal mode but with bad graphics so i install the drivers of de nvidia official site (195 version, i think, the latest), i followed your steps of the first guide, kill the gdm, and i used your xorg.conf, don't use the sonycw.bin, with this i could get working with Ubuntu 10.04 in my vpccw21fx. I need activate the nomodeset activate for working, if this option is desactivated, i got a black screen.
So you still have to use nomodeset to get video? I still haven't had to use that option.

---

### Post by onhafoghefifo on 2010-06-09
Yes that's one of the things i've tried. I tried the compat-wireless by downloading its .tar.gz and also by apt-getting the backports module, both unsuccessful. 

Dark_Stang, I think it's because the driver was installed while using this option. I had this problem too. What I think that I did to solve this I said in previous post.

---

### Post by fuligin on 2010-06-09
I tried to install the kernel however now im stuck with a bad kernal at start up and can only boot from generic kernal. any advice?

---

### Post by Dark_Stang on 2010-06-09
> **fuligin said:**
> I tried to install the kernel however now im stuck with a bad kernal at start up and can only boot from generic kernal. any advice?
What error are you getting? What kind of computer do you have? What version of Ubuntu are you running? Is it 64bit or 32 bit?

---

### Post by fuligin on 2010-06-10
> **Dark_Stang said:**
> What error are you getting? What kind of computer do you have? What version of Ubuntu are you running? Is it 64bit or 32 bit?


Im using a Sony Vaio CW Model#VPCCw21FX.
Initially I installed from the alternate 64 as instructed. 
I was able to log in after making the graphics editing. 
However after running the kernel I get a 
1.725011 Kernal Panic  - Not Syncing: VFS Unable to mount root fs on unknown-block (0,0)

Any suggestions? Im actually thinking of reinstalling since I think my ubuntu partion is bigger then I wanted. 

Thanks in advance.
PS: Pls not this is my first attempt at Ubuntu in many years therefore even things like running the install.sh had to be researched. :(

---

### Post by Dark_Stang on 2010-06-11
I would say re-download the package I posted and try it again. onhafoghefifo made me realize I forgot to include the ramdisk image in the original. Sounds like the same problem.

---

### Post by onhafoghefifo on 2010-06-11
Good to know that everybody is making progress. Now we're going to be stuck at the same problem. Hope that someone finds what to do or where i got it wrong :p
I am using ubuntu inside win7 via virtualbox, it was my last option, but i had to do it so to have wireless network access in my ubuntu. Must use it for work.

---

### Post by Mblackwell on 2010-06-12
Has anyone tried custom compiling the kernel (either 2.6.33 or higher) as described in the OP on 32 bit install and seeing if the wireless works better? I'm definitely not loving the speed fluctuations and packet loss...

---

### Post by fuligin on 2010-06-12
> **Dark_Stang said:**
> I would say re-download the package I posted and try it again. onhafoghefifo made me realize I forgot to include the ramdisk image in the original. Sounds like the same problem.

During the install I am always getting this error

cp: cannot stat `initrd.img-2.6.33.3-ds': No such file or directory

obviously im doing something wrong since im the only one complaining :(

---

### Post by jjchm on 2010-06-14
I could finally prove my wireless connection (bought a linksys router) in my vpccw21fx with Ubuntu 10.04 64bits, and i can say i did not have drawbacks, i was online for about two hours and not experience disconnects, i made a ping test to google in the two hours and i got 9% packet loss, honestly i see this behavior normal, well for me is normal :).

All I did was install ubuntu12 (alternate mode with nvidia driver 195) and update to date, after update install nvidia driver again (the new kernel made changes in the nvidia drivers). That's all.

Thanks to all for your help.

---

### Post by onhafoghefifo on 2010-06-16
Mblackwell, neither am i. I've tried to compile kernel 2.6.34 on ubuntu  lucid 32 bits. It didn't solve the problem for me.

fuligin, this  is happening because the cp command at the shell script is trying to  copy a file that doesn't exist in your pc. Try to download again the  package from the first post, and inside of it must have a  'initrd.img-2.6.33.3-ds' file. Dark_Stang forgot to pack this file  before, but he already fixed it.

jjchm, you just installed ubuntu  and did update/upgrade? Wow maybe they finally posted some updates to  fix that \o/

---

### Post by jjchm on 2010-06-17
Onhafoghefifo, Yes, this was what i did:

1) Install Ubuntu 64bits alternate mode with the option nomodeset activate.

2) Install the Nvidia Driver 195.

3) Update the system to date.

4) Install again the nvidia drivers 195.

5) Prove that everything works, specially the wireless :o).

Ubuntu rocks, stay well.

---

### Post by Slayer6 on 2010-06-20
ok ran install then added ramdisk image after with
sudo mkinitramfs -o /boot/initrd.img-2.6.33.3-ds 2.6.33.3-ds
and modified grub

as the one in the download was blank 

still may have malfunctioning wifi

what is the best way to test if all is working well

nvidia works perfect.  thanks for all your help

---

### Post by onhafoghefifo on 2010-06-24
well, the best way to try if your wi-fi is ok is to ping your router
when i try to ping my router i get 40% packet loss
try to ping google.com as well
see how many % you get when doing this

---

### Post by Dark_Stang on 2010-06-28
I've compiled a 2.6.34 kernel, for anybody still having wireless issues this one seems to work for me too. If you don't want to compile, here are the debs to install.

[http://darkstang.com/vpccw21fx/linux-image-2.6.34-ds_2.6.34-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-image-2.6.34-ds_2.6.34-ds_amd64.deb)
[http://darkstang.com/vpccw21fx/linux-headers-2.6.34-ds_2.6.34-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-headers-2.6.34-ds_2.6.34-ds_amd64.deb)

If you want to compile your own kernel, here is what you can do.
Download the 2.6.34 kernel from [http://kernel.org](http://kernel.org).
Here is the link to my config file, I'd recommend starting here and doing as you please to tweak it for you.
[http://darkstang.com/vpccw21fx/2.6.34-config](http://darkstang.com/vpccw21fx/2.6.34-config)

Also, here is a patch that I applied. This doesn't really have anything to do with the wireless, but it fixes an issue with WINE and World of Warcraft... heh. Copy to the source directory if you want to apply it.
[http://darkstang.com/vpccw21fx/wine_patch.patch](http://darkstang.com/vpccw21fx/wine_patch.patch)
This patch comes from the WINE community, link to the bug follows...
[http://bugs.winehq.org/show_bug.cgi?id=23323](http://bugs.winehq.org/show_bug.cgi?id=23323)

Here are the commands that I ran to compile the kernel and make the packages. Be sure to safe my config file as .config in the kernel source directory, if you plan on starting with it and using it.
```
sudo git apply wine_patch.patch
sudo make menuconfig
sudo make kpkg-clean
sudo fakeroot make-kpkg -initrd -append-to-version=-ds kernel_image kernel_headers
```

---

### Post by fuligin on 2010-07-04
Cant seem to get Nvidia to work to save my life. 
Have tried the custom xorg 
It just wont work without the nomodeset
Am updating now to see what happens, 
In the meantime any tips would be appreciated

---

### Post by onhafoghefifo on 2010-07-05
fuligin, maybe this is happening because you did everything with the nomodeset option.
When i installed my ubuntu the first time and managed to make my video work, I did a few steps that maybe made it possible for me to run it without the nomodeset option.
I think it was because first of all I tried to install the nvidia driver  from apt-get. When I did it, I could boot without the nomodeset option,  but I got a really weird screen on startup. After that I installed the driver from nvidia site, and  it worked as it should, without nomodeset. Maybe this nomodeset option is affecting the wireless driver also? jjchm could make it work without doing anything special, and he wasn't using this nomodeset stuff.

---

### Post by fuligin on 2010-07-06
> **onhafoghefifo said:**
> fuligin, maybe this is happening because you did everything with the nomodeset option.
When i installed my ubuntu the first time and managed to make my video work, I did a few steps that maybe made it possible for me to run it without the nomodeset option.
I think it was because first of all I tried to install the nvidia driver  from apt-get. When I did it, I could boot without the nomodeset option,  but I got a really weird screen on startup. After that I installed the driver from nvidia site, and  it worked as it should, without nomodeset. Maybe this nomodeset option is affecting the wireless driver also? jjchm could make it work without doing anything special, and he wasn't using this nomodeset stuff.

onhafoghefifo: Thanks I have formated once again..so I shall try install the driver from apt-get first, and then instal the downloaded NVIDIA driver after I have updated. Something was seriously going wrong because I couldnt even get into the CTRL+Alt+F1 terminal screen.
Will try and update on here.
Thanks again :)

---

### Post by fuligin on 2010-07-06
Ok managed to get everything running without the custom kernel.
Only problem I see right now is that WIFI is very slow & I cant get the CTRL+ALT+F1-6 to work.
Anyone else experiencing this?

---

### Post by Dark_Stang on 2010-07-06
> **fuligin said:**
> Ok managed to get everything running without the custom kernel.
Only problem I see right now is that WIFI is very slow & I cant get the CTRL+ALT+F1-6 to work.
Anyone else experiencing this?

What are your ping times like when pinging your router? Consistent or all over the place?

And for the Ctrl+Alt+F1 thing... I just tried it and it's not working for me either. Wonder when that started. I'm running kernel 2.6.34 now with the 225 nvidia drivers.

---

### Post by fuligin on 2010-07-07
> **Dark_Stang said:**
> What are your ping times like when pinging your router? Consistent or all over the place?

And for the Ctrl+Alt+F1 thing... I just tried it and it's not working for me either. Wonder when that started. I'm running kernel 2.6.34 now with the 225 nvidia drivers.

Im pinging my router and google and its kinda all over the place. for my router it varies from 60%-100% sucessfull packets & for google it varies from 40% to 80%

As mentioned above I am running the latest NVIDIA Driver downloaded from their site. Version 256.35

No clue about the CTl+Alt+F1..it was working before. I read somehwere that it has to do witht he resolution and its common for widescreens. Also I found a post somewhere that lowers resolution of grub and supposedly fixes this problem but have not been able to find it again.

UPdate: In regards to the Ctrl+Alt+F1: the following fixed it for now...I still need to tinker around with the resolution since its huge, but i followed the steps in the following link. 
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by onhafoghefifo on 2010-07-11
well i don't remember experiencing the ctrl + alt + f1 bug
as soon as my vacations starts, in a few days, I'll try again to install ubuntu in my laptop, and report any issues/dificulties here

---

### Post by fuligin on 2010-07-14
> **onhafoghefifo said:**
> well i don't remember experiencing the ctrl + alt + f1 bug
as soon as my vacations starts, in a few days, I'll try again to install ubuntu in my laptop, and report any issues/dificulties here

Would be very nice if you could tell us how things go with you...my installation is a mess :(

---

### Post by Dark_Stang on 2010-07-14
Just a thought, has anybody tried turning bluetooth off and testing?

---

### Post by fuligin on 2010-07-16
> **Dark_Stang said:**
> Just a thought, has anybody tried turning bluetooth off and testing?

Bluetooth is the first thing i turn off when I install..so that's probably not it.

---

### Post by Dark_Stang on 2010-07-16
I am downloading 10.10 to play with tonight. Will test with the liveCD first. If that goes well, or if I feel frisky, I will do a networked install. I'm sorry guys... I have no idea why the wireless works for me 95% (yup, still have the occasional lag issue) of the time. :(

Oh, and on top of that, in case nobody has seen the service alert for our laptops yet...
[http://esupport.sony.com/perl/news-item.pl?news_id=401&template_id=1&region_id=1](http://esupport.sony.com/perl/news-item.pl?news_id=401&template_id=1&region_id=1)

Well that was down right miserable using the stock kernel...
Has anybody seen or tried all these patches yet?

 - Submit July 11 2010
[https://patchwork.kernel.org/patch/111301/](https://patchwork.kernel.org/patch/111301/)
[https://patchwork.kernel.org/patch/111304/](https://patchwork.kernel.org/patch/111304/)
[https://patchwork.kernel.org/patch/111300/](https://patchwork.kernel.org/patch/111300/)
[https://patchwork.kernel.org/patch/111303/](https://patchwork.kernel.org/patch/111303/)
[https://patchwork.kernel.org/patch/111302/](https://patchwork.kernel.org/patch/111302/)
[https://patchwork.kernel.org/patch/111299/](https://patchwork.kernel.org/patch/111299/)
[https://patchwork.kernel.org/patch/111305/](https://patchwork.kernel.org/patch/111305/)

 - Submit July 7 2010
[https://patchwork.kernel.org/patch/110683/](https://patchwork.kernel.org/patch/110683/)
[https://patchwork.kernel.org/patch/110684/](https://patchwork.kernel.org/patch/110684/)

There are loads more...
[https://patchwork.kernel.org/project/linux-wireless/list/?page=1](https://patchwork.kernel.org/project/linux-wireless/list/?page=1)

---

### Post by Dark_Stang on 2010-07-18
Compiled 2.6.35-rc5. Feels the same to me. Surfing the web is fine, everything runs smoothly except for gaming. When I game I have to hardwire.

Edit: Oh, and I still have the Ctrl+Alt+F1 bug. I think it might be the 256 drivers causing it.

---

### Post by fuligin on 2010-07-19
> **Dark_Stang said:**
> Compiled 2.6.35-rc5. Feels the same to me. Surfing the web is fine, everything runs smoothly except for gaming. When I game I have to hardwire.

Edit: Oh, and I still have the Ctrl+Alt+F1 bug. I think it might be the 256 drivers causing it.

I will attempt a reinstallation..since I have messed around too much and for sure have damaged something in my insallation.

The Crtl+Alt+F1 bug is solvable by using the link i have above...only problem is that the terminal font and startup logo become huge....Im convinced that if i play around with the resolution there I may be able to fix it. 
This is very frustrating since im kinda  a Newbie..havent touched linux for a few distros since i got got put off with my last machine not working with it.

---

### Post by Dark_Stang on 2010-07-19
Frustrating for me as well. But I can't blame linux as all the documents I'm reading seem to point out that Atheros basically released several AR9285's with different configurations (of course they're all listed simply as AR9285). A lot of these configurations were broken from the factory and Atheros is trying to fix it with their drivers.

---

### Post by fuligin on 2010-07-19
> **Dark_Stang said:**
> Frustrating for me as well. But I can't blame linux as all the documents I'm reading seem to point out that Atheros basically released several AR9285's with different configurations (of course they're all listed simply as AR9285). A lot of these configurations were broken from the factory and Atheros is trying to fix it with their drivers.

That is news to me and actually it made me look at Ubuntu in a better way! The Artheros AR9285 is a really bad device..hardly any proper or updated drivers for it...and it doesnt play nice with windows 7 either. I had to do a clean install in order to get it to work properly in Windows 7..even now that it is fully functional its range is horrible compared to other Artheros wifi that I have. 
I do thank you for all your help though..it will certainly get me back into Ubuntu :)

---

### Post by Dark_Stang on 2010-07-19
So, after some more diagnostic work I've found that I do have packet loss but my wireless card doesn't know it.

Results from my laptop pinging my router.
```
15 packets transmitted, 15 received, 0% packet loss
```
Results from my router pinging my laptop.
```
15 Packets transmitted, 7 Packets received, 53% Packet loss
```

I've been playing around with the ath9k source code a lot and tweaking things. So far I haven't gotten anywhere good.

---

### Post by Phis on 2010-07-19
have you guys tired this for the wireless [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503&page=4](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503&page=4)  

I installed the newest driver and my internet is blazing ! but i don't know how to verify packet losses.

I still can't get my video to work without the nomodeset, which i have to set every time. I tried jjchm's config but i must be doing something wrong. when I change the nomodeset in grub is there a way i can save it without having to do it each time ? jjchm have you installed the driver with the xorg.conf file that dark_stang has set ?  



> **jjchm said:**
> Onhafoghefifo, Yes, this was what i did:

1) Install Ubuntu 64bits alternate mode with the option nomodeset activate.

2) Install the Nvidia Driver 195.

3) Update the system to date.

4) Install again the nvidia drivers 195.

5) Prove that everything works, specially the wireless :o).

Ubuntu rocks, stay well.

---

### Post by onhafoghefifo on 2010-07-20
Phis, we already tried this. if you look closer at the first post, this is the same package that Dark_Stang played with. i've tried it with kernel 2.6.34 and the compat-wireless for it, and also for other kernel versions, and ended up nowhere
to verify packet losses just open a terminal and enter the command "ping SITE"
when i ping my router i get about 40% packet loss (ping 192.168.0.1) and when i ping google it is even worst (ping [www.google.com](www.google.com))

well for my video card i did the following: [http://ubuntuforums.org/showpost.php?p=9552935&postcount=36](http://ubuntuforums.org/showpost.php?p=9552935&postcount=36)

Dark_Stang, i am having the ctrl+alt+f bug too. In a week i'll try to play with my ubuntu again, to fix things. Sorry for saying that, but in some way it's good to know that you are still having problems with your wifi. I was wondering what could i have possibly done so wrong that i followed your step by step and my wifi is still messed up. Welcome back to the team :D i think you couldn't notice it because you have a decent internet connection, and when the packet can be transmitted it works well. Also, how is it going with ubuntu 10.10?

fuligin, i'll try the link you gave to us. in a couple of days from now i should have an aswer

have anyone tried to use ndiswrapper?

---

### Post by Dark_Stang on 2010-07-21
I've compiled so many kernels in the last few weeks... I don't know why, but for some reason the 2.6.33.3 kernel that I compiled towards the beginning seems to work the best. That doesn't say a whole lot... I appear to have no outgoing packets lost, which is nice. But when pinging my machine from another machine (router, desktop, etc) I still get a no-reply 10-15% of the time. 

Does anybody have BSD on their machine? I'm curious if it's experiencing the same issue.

Ubuntu 10.10 was a nightmare. The newest kernel, or at least the stock Ubuntu one, seems to make the issue worse. Everything else was great though. It kinda bugs me... I thought my problem was fixed, then I started noticing some odd things, and now I notice it all the time. Surfing the web works fine, but any time I try to play WoW it lags hard core. I have to watch what I'm doing on my finance's desktop because my laptop just starts dropping packets like crazy.

---

### Post by fuligin on 2010-07-28
DS: I must say that you are right! I have just reinstalled your first kernel which I have on hand. My speeds are nowhere near perfect though much better then before. 
Back in the day when I was running Ubuntu on my Thinkpad, I used to go to a dedicated forum. I remember there used to be a Vaio forum too which dealt with all these things, however im unable to find it now that I have a Vaio.
Do you know of it ? 
Also is there a way that I dont have to reinstall ubuntu everytime that im trying out new things with it ? This must have been my 10th installation since the new version was out!

I cant get this thing to start up with out the nomodeset ???

---

### Post by Phis on 2010-07-28
the internet is better for web browsing. but it is always disconnecting or fragmented.

I don't know anything about a viao board.


for the video use the nomodeset to log in and then install the drivers from the hardware drivers in system menu once you've updated the system. worked for me

---

### Post by fuligin on 2010-07-29
Sorry to bring this up again!
Im having trouble installing the kernel though I have managed to install it in the past.
Im using the following commands
[I]Sudo sh install.sh
sudo mkinitramfs -o /boot/initrd.img-2.6.33.3-ds 2.6.33.3-ds
sudo grub-mkconfig -o /boot/grub/grub.cfg

sudo reboot[/I]

I just get a black screen at startup.. any help is much appreciated!

---

### Post by Phis on 2010-07-29
you only need to install the kernel which is included in the ubuntu updates.

---

### Post by fuligin on 2010-07-30
> **Phis said:**
> you only need to install the kernel which is included in the ubuntu updates.

Kernel in the updates doesnt play very well with the WiFi driver.
Unless things have changed..
That is one of the key points of this thread!

---

### Post by Dark_Stang on 2010-07-31
> **fuligin said:**
> Sorry to bring this up again!
Im having trouble installing the kernel though I have managed to install it in the past.
Im using the following commands
[I]Sudo sh install.sh
sudo mkinitramfs -o /boot/initrd.img-2.6.33.3-ds 2.6.33.3-ds
sudo grub-mkconfig -o /boot/grub/grub.cfg

sudo reboot[/I]

I just get a black screen at startup.. any help is much appreciated!

You'll need to add "nomodeset" at boot in order to get video. You can manually edit your /boot/grub/grub.cfg file afterwards to make the change permanent.

---

### Post by Dark_Stang on 2010-08-02
I'm feeling pretty agrivated at this point. Surfing is fine but gaming still sucks on this laptop with the 2.6.35-rc6-git6 kernel installed. I feel as though this card is just a plague at this point as it appears to be spreading into many other laptops. I'm strongly considering just buying an Intel wireless card for the laptop so I don't have any more problems.

Edit: The Intel N1000 seems like a very nice (and cheap) solution to this problem.
[http://www.intel.com/network/connectivity/products/wireless/adapters/1000/index.htm](http://www.intel.com/network/connectivity/products/wireless/adapters/1000/index.htm)

---

### Post by GENEius on 2010-08-02
I'm so glad I found this thread, I was about to go and do this install but I'll hold off for a little bit...

---

### Post by Dark_Stang on 2010-08-06
Pulled my AR9285 chip out tonight. Got fed up with it and couldn't hack the ath9k drivers into working at all. Going to see if I can pick up an Intel chip from anybody in town tomorrow. If I can't I'll just order one online. At the moment I'm dragging a 25' (about 8m) network cable around my living room.

If any of you wish to replace your wireless card like I am doing, I say go for it if you know what you're doing. I will not post directions as I don't want to be responsible for somebody frying their motherboard. But if you've ever taken a laptop apart this one is a dream compared to any other laptop that I've had to work on.

I will be editing the first post to reflect that it has wireless issues and to stay away from it until it is fixed.

---

### Post by Dark_Stang on 2010-08-09
Swapped out my wireless card for the Intel WifiLink 1000. Works great at this point, no packet loss pinging out or pinging in. Going to start streaming some media to my PS3 wirelessly to test. And tonight I'll be playing in some dungeons on WoW so it'll get the real test then.

Edit: After a few days of running dungeons in WoW (on linux), streaming media to my PS3, and general use. I must say that I love this Intel wireless card. I don't understand why it didn't come with one in the first place.

---

### Post by onhafoghefifo on 2010-08-24
hey DS which wifi card you bought? and where you bought it from? really wanting to do the same with my laptop. never worked with laptop before (just cleaning), but now it is a good time to learn xD

---

### Post by Dark_Stang on 2010-08-24
The card that I bought was an Intel WiFi Link 1000 card. It's the Mini-PCI-Express Half Card form factor. And I bought mine through Buy.com. Here is the link.
[http://www.buy.com/prod/intel-wifi-link-1000-wireless-adapter-mini-pci-express-300mbps-ieee/q/loc/101/212885539.html](http://www.buy.com/prod/intel-wifi-link-1000-wireless-adapter-mini-pci-express-300mbps-ieee/q/loc/101/212885539.html)

Since you're in Brasil, you may want to find another distributor or shipping might break your bank account. Check out Google shopping.
[http://www.google.com/products?q=Intel+WiFi+Link+1000+mini+pcie+half+card&hl=en&aq=f](http://www.google.com/products?q=Intel+WiFi+Link+1000+mini+pcie+half+card&hl=en&aq=f)

As I said the install was surprisingly easy, especially for a Sony product. Just make sure you're grounded as your hand will be (at most) 2 mm away from the motherboard while replacing the card. At that proximity static electricity is a big concern.

---

### Post by Phis on 2010-09-17
Thank you Dark_Stang. I installed a new wifi card and it works great

---

### Post by reduz on 2010-10-20
Nvidia driver no longer works on 10.10!!!

---

### Post by mrnelson1986 on 2010-10-21
> **reduz said:**
> Nvidia driver no longer works on 10.10!!!

the 260.xx doesn't work, but the 256.53 does, at least on my vpccw27fx/b, which is almost the same as the 21fx i think.  Archive drivers ftw

---

### Post by Dark_Stang on 2010-10-21
> **mrnelson1986 said:**
> the 260.xx doesn't work, but the 256.53 does, at least on my vpccw27fx/b, which is almost the same as the 21fx i think.  Archive drivers ftw
I wasn't even aware that a new driver had come out. I am still using the 256.53 driver.

---

### Post by mrnelson1986 on 2010-10-22
> **Dark_Stang said:**
> I wasn't even aware that a new driver had come out. I am still using the 256.53 driver.

So what is "not working" for you? A bug that exists with the drivers is that _whenever_ there is a kernel update, you have to reinstall the drivers to get picture.  So if your screen goes black when you choose ubuntu at the GRUB menu, then that is your issue, just boot into recovery (possibly editing the boot line with "nomodeset") and reinstall the nvidia drivers, then reboot and try booting again (again editing your boot line with nomodeset)

---

### Post by onhafoghefifo on 2010-10-25
i can't make my video card work on 10.10 either. Tried all the same stuff that i did to make it work under 10.04, but without success. Wondering about regressing back to 10.04 now...

---

### Post by mrnelson1986 on 2010-10-26
> **onhafoghefifo said:**
> i can't make my video card work on 10.10 either. Tried all the same stuff that i did to make it work under 10.04, but without success. Wondering about regressing back to 10.04 now...

Did you follow the tips in my last post? "nomodeset" ALWAYS gets me to a visual GUI...but remember that you have to set nomodeset even on booting into a recovery, for some reason if you don't it tries to load nouveau drivers which are incompatible with sony hardware.

---

### Post by onhafoghefifo on 2010-10-26
actually i followed all the steps we posted before in this thread
i could make ubuntu 10.04 work without the nomodeset option, and it started to use the nvidia driver instead of noveau one
but i couldn't make it work in ubuntu 10.10
i'll try now using another driver version to see what happens

---

### Post by mrnelson1986 on 2010-10-26
> **onhafoghefifo said:**
> actually i followed all the steps we posted before in this thread
i could make ubuntu 10.04 work without the nomodeset option, and it started to use the nvidia driver instead of noveau one
but i couldn't make it work in ubuntu 10.10
i'll try now using another driver version to see what happens

Like I said before for me personally the 260.xx driver does not work, i have to use an archived 256.xx driver for my nvidia 330M gt

---

### Post by Phis on 2010-10-27
I have installed the 256.xxx driver. which works after I start x. Once i restart, without nomodeset, I get the command prompt to log in. When I try to startx I get a failure command. I have to reinstall the driver to be able to startx. Here is the log which I am directed too when X fails to start. Now when I got this particular log I had reinstalled the drivers, not sure if that modifies the log file. 

thank you 

[   193.408] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   193.409] X Protocol Version 11, Revision 0
[   193.409] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   193.409] Current Operating System: Linux ubuntu 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[   193.409] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=002f3c27-c2a6-4657-9bd2-ff4c56a3741f ro quiet splash
[   193.410] Build Date: 16 September 2010  06:18:41PM
[   193.410] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   193.410] Current version of pixman: 0.18.4
[   193.410] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   193.411] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   193.412] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 27 16:31:40 2010
[   193.413] (==) Using config file: "/etc/X11/xorg.conf"
[   193.413] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   193.413] (==) ServerLayout "Layout0"
[   193.413] (**) |-->Screen "Screen0" (0)
[   193.414] (**) |   |-->Monitor "Monitor0"
[   193.414] (**) |   |-->Device "Device0"
[   193.414] (**) |-->Input Device "Keyboard0"
[   193.414] (**) |-->Input Device "Mouse0"
[   193.414] (**) Option "Xinerama" "0"
[   193.414] (==) Automatically adding devices
[   193.414] (==) Automatically enabling devices
[   193.414] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   193.414] 	Entry deleted from font path.
[   193.414] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   193.414] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   193.414] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   193.414] (WW) Disabling Keyboard0
[   193.414] (WW) Disabling Mouse0
[   193.414] (II) Loader magic: 0x7d0200
[   193.414] (II) Module ABI versions:
[   193.414] 	X.Org ANSI C Emulation: 0.4
[   193.414] 	X.Org Video Driver: 8.0
[   193.414] 	X.Org XInput driver : 11.0
[   193.414] 	X.Org Server Extension : 4.0
[   193.416] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9072 rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[   193.416] (II) Open ACPI successful (/var/run/acpid.socket)
[   193.416] (II) LoadModule: "extmod"
[   193.417] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   193.418] (II) Module extmod: vendor="X.Org Foundation"
[   193.418] 	compiled for 1.9.0, module version = 1.0.0
[   193.418] 	Module class: X.Org Server Extension
[   193.418] 	ABI class: X.Org Server Extension, version 4.0
[   193.418] (II) Loading extension MIT-SCREEN-SAVER
[   193.418] (II) Loading extension XFree86-VidModeExtension
[   193.418] (II) Loading extension XFree86-DGA
[   193.418] (II) Loading extension DPMS
[   193.418] (II) Loading extension XVideo
[   193.418] (II) Loading extension XVideo-MotionCompensation
[   193.418] (II) Loading extension X-Resource
[   193.418] (II) LoadModule: "dbe"
[   193.418] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   193.419] (II) Module dbe: vendor="X.Org Foundation"
[   193.419] 	compiled for 1.9.0, module version = 1.0.0
[   193.419] 	Module class: X.Org Server Extension
[   193.419] 	ABI class: X.Org Server Extension, version 4.0
[   193.419] (II) Loading extension DOUBLE-BUFFER
[   193.419] (II) LoadModule: "glx"
[   193.419] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   193.427] (II) Module glx: vendor="NVIDIA Corporation"
[   193.427] 	compiled for 4.0.2, module version = 1.0.0
[   193.427] 	Module class: X.Org Server Extension
[   193.427] (II) NVIDIA GLX Module  256.53  Fri Aug 27 20:50:26 PDT 2010
[   193.427] (II) Loading extension GLX
[   193.427] (II) LoadModule: "record"
[   193.428] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   193.428] (II) Module record: vendor="X.Org Foundation"
[   193.428] 	compiled for 1.9.0, module version = 1.13.0
[   193.428] 	Module class: X.Org Server Extension
[   193.428] 	ABI class: X.Org Server Extension, version 4.0
[   193.428] (II) Loading extension RECORD
[   193.428] (II) LoadModule: "dri"
[   193.428] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   193.428] (II) Module dri: vendor="X.Org Foundation"
[   193.428] 	compiled for 1.9.0, module version = 1.0.0
[   193.428] 	ABI class: X.Org Server Extension, version 4.0
[   193.428] (II) Loading extension XFree86-DRI
[   193.428] (II) LoadModule: "dri2"
[   193.428] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   193.428] (II) Module dri2: vendor="X.Org Foundation"
[   193.428] 	compiled for 1.9.0, module version = 1.2.0
[   193.428] 	ABI class: X.Org Server Extension, version 4.0
[   193.429] (II) Loading extension DRI2
[   193.429] (II) LoadModule: "nvidia"
[   193.429] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   193.429] (II) Module nvidia: vendor="NVIDIA Corporation"
[   193.429] 	compiled for 4.0.2, module version = 1.0.0
[   193.429] 	Module class: X.Org Video Driver
[   193.776] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 20:29:45 PDT 2010
[   193.776] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   193.776] (--) using VT number 7

[   193.796] (II) Loading sub module "fb"
[   193.796] (II) LoadModule: "fb"
[   193.797] (II) Loading /usr/lib/xorg/modules/libfb.so
[   193.797] (II) Module fb: vendor="X.Org Foundation"
[   193.797] 	compiled for 1.9.0, module version = 1.0.0
[   193.797] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   193.797] (II) Loading sub module "wfb"
[   193.797] (II) LoadModule: "wfb"
[   193.798] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   193.798] (II) Module wfb: vendor="X.Org Foundation"
[   193.798] 	compiled for 1.9.0, module version = 1.0.0
[   193.798] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   193.798] (II) Loading sub module "ramdac"
[   193.798] (II) LoadModule: "ramdac"
[   193.798] (II) Module "ramdac" already built-in
[   193.798] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   193.798] (==) NVIDIA(0): RGB weight 888
[   193.798] (==) NVIDIA(0): Default visual is TrueColor
[   193.798] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   193.798] (**) NVIDIA(0): Option "TwinView" "0"
[   193.798] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[   193.799] (**) NVIDIA(0): Enabling RENDER acceleration
[   193.799] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   193.799] (II) NVIDIA(0):     enabled.
[   195.000] (II) NVIDIA(0): NVIDIA GPU GeForce 310M (GT218) at PCI:1:0:0 (GPU-0)
[   195.000] (--) NVIDIA(0): Memory: 262144 kBytes
[   195.000] (--) NVIDIA(0): VideoBIOS: 70.18.35.00.15
[   195.000] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   195.000] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   195.000] (--) NVIDIA(0): Connected display device(s) on GeForce 310M at PCI:1:0:0:
[   195.000] (--) NVIDIA(0):     Sony Nvidia Default Flat Panel (DFP-0)
[   195.000] (--) NVIDIA(0): Sony Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum
[   195.000] (--) NVIDIA(0):     pixel clock
[   195.000] (--) NVIDIA(0): Sony Nvidia Default Flat Panel (DFP-0): Internal Dual Link
[   195.000] (--) NVIDIA(0):     LVDS
[   195.059] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   195.059] (II) NVIDIA(0): Validated modes:
[   195.059] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[   195.059] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[   195.834] (--) NVIDIA(0): DPI set to (111, 114); computed from "UseEdidDpi" X config
[   195.834] (--) NVIDIA(0):     option
[   195.834] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   195.834] (--) Depth 24 pixmap format is 32 bpp
[   195.835] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   195.836] (II) NVIDIA(0): Initialized GPU GART.
[   195.841] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[   195.841] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[   195.841] (WW) NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
[   195.841] (WW) NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
[   195.841] (WW) NVIDIA(0):     respond to ACPI brightness change hotkey events.
[   195.843] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[   196.153] (II) Loading extension NV-GLX
[   196.185] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   196.199] (==) NVIDIA(0): Disabling shared memory pixmaps
[   196.199] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   196.199] (==) NVIDIA(0): Backing store disabled
[   196.199] (==) NVIDIA(0): Silken mouse enabled
[   196.214] (**) NVIDIA(0): DPMS enabled
[   196.214] (II) Loading extension NV-CONTROL
[   196.214] (II) Loading extension XINERAMA
[   196.214] (II) Loading sub module "dri2"
[   196.214] (II) LoadModule: "dri2"
[   196.215] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   196.215] (II) NVIDIA(0): [DRI2] Setup complete
[   196.215] (==) RandR enabled
[   196.215] (II) Initializing built-in extension Generic Event Extension
[   196.215] (II) Initializing built-in extension SHAPE
[   196.215] (II) Initializing built-in extension MIT-SHM
[   196.215] (II) Initializing built-in extension XInputExtension
[   196.215] (II) Initializing built-in extension XTEST
[   196.215] (II) Initializing built-in extension BIG-REQUESTS
[   196.215] (II) Initializing built-in extension SYNC
[   196.215] (II) Initializing built-in extension XKEYBOARD
[   196.215] (II) Initializing built-in extension XC-MISC
[   196.215] (II) Initializing built-in extension SECURITY
[   196.215] (II) Initializing built-in extension XINERAMA
[   196.215] (II) Initializing built-in extension XFIXES
[   196.215] (II) Initializing built-in extension RENDER
[   196.215] (II) Initializing built-in extension RANDR
[   196.215] (II) Initializing built-in extension COMPOSITE
[   196.215] (II) Initializing built-in extension DAMAGE
[   196.215] (II) Initializing built-in extension GESTURE
[   196.216] (II) Initializing extension GLX
[   196.241] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   196.384] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event5)
[   196.384] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[   196.384] (II) LoadModule: "evdev"
[   196.385] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   196.385] (II) Module evdev: vendor="X.Org Foundation"
[   196.385] 	compiled for 1.9.0, module version = 2.3.2
[   196.385] 	Module class: X.Org XInput Driver
[   196.385] 	ABI class: X.Org XInput driver, version 11.0
[   196.385] (**) Sony Vaio Keys: always reports core events
[   196.385] (**) Sony Vaio Keys: Device: "/dev/input/event5"
[   196.432] (II) Sony Vaio Keys: Found keys
[   196.432] (II) Sony Vaio Keys: Configuring as keyboard
[   196.432] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[   196.432] (**) Option "xkb_rules" "evdev"
[   196.432] (**) Option "xkb_model" "pc105"
[   196.432] (**) Option "xkb_layout" "ca"
[   196.432] (**) Option "xkb_variant" "fr-legacy"
[   196.432] (**) Option "xkb_options" "lv3:ralt_switch"
[   196.436] (II) XKB: generating xkmfile /tmp/server-1B5FE174A528F9D0771C4BD29BB630649C2BDA44.xkm
[   196.473] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   196.473] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   196.473] (**) Video Bus: always reports core events
[   196.473] (**) Video Bus: Device: "/dev/input/event4"
[   196.550] (II) Video Bus: Found keys
[   196.550] (II) Video Bus: Configuring as keyboard
[   196.550] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   196.550] (**) Option "xkb_rules" "evdev"
[   196.550] (**) Option "xkb_model" "pc105"
[   196.550] (**) Option "xkb_layout" "ca"
[   196.550] (**) Option "xkb_variant" "fr-legacy"
[   196.550] (**) Option "xkb_options" "lv3:ralt_switch"
[   196.552] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   196.552] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   196.552] (**) Power Button: always reports core events
[   196.552] (**) Power Button: Device: "/dev/input/event1"
[   196.630] (II) Power Button: Found keys
[   196.630] (II) Power Button: Configuring as keyboard
[   196.630] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   196.630] (**) Option "xkb_rules" "evdev"
[   196.630] (**) Option "xkb_model" "pc105"
[   196.630] (**) Option "xkb_layout" "ca"
[   196.630] (**) Option "xkb_variant" "fr-legacy"
[   196.630] (**) Option "xkb_options" "lv3:ralt_switch"
[   196.631] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   196.631] (II) No input driver/identifier specified (ignoring)
[   196.633] (II) config/udev: Adding input device UVC Camera (05ca:18b5) (/dev/input/event7)
[   196.633] (**) UVC Camera (05ca:18b5): Applying InputClass "evdev keyboard catchall"
[   196.633] (**) UVC Camera (05ca:18b5): always reports core events
[   196.633] (**) UVC Camera (05ca:18b5): Device: "/dev/input/event7"
[   196.710] (II) UVC Camera (05ca:18b5): Found keys
[   196.710] (II) UVC Camera (05ca:18b5): Configuring as keyboard
[   196.710] (II) XINPUT: Adding extended input device "UVC Camera (05ca:18b5)" (type: KEYBOARD)
[   196.710] (**) Option "xkb_rules" "evdev"
[   196.710] (**) Option "xkb_model" "pc105"
[   196.710] (**) Option "xkb_layout" "ca"
[   196.710] (**) Option "xkb_variant" "fr-legacy"
[   196.710] (**) Option "xkb_options" "lv3:ralt_switch"
[   196.714] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[   196.714] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[   196.714] (**) USB Optical Mouse: always reports core events
[   196.714] (**) USB Optical Mouse: Device: "/dev/input/event3"
[   196.780] (II) USB Optical Mouse: Found 3 mouse buttons
[   196.780] (II) USB Optical Mouse: Found scroll wheel(s)
[   196.780] (II) USB Optical Mouse: Found relative axes
[   196.780] (II) USB Optical Mouse: Found x and y relative axes
[   196.780] (II) USB Optical Mouse: Configuring as mouse
[   196.780] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[   196.780] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   196.780] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[   196.780] (II) USB Optical Mouse: initialized for relative axes.
[   196.781] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[   196.781] (II) No input driver/identifier specified (ignoring)
[   196.784] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   196.784] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   196.784] (**) AT Translated Set 2 keyboard: always reports core events
[   196.784] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   196.860] (II) AT Translated Set 2 keyboard: Found keys
[   196.860] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   196.860] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   196.860] (**) Option "xkb_rules" "evdev"
[   196.860] (**) Option "xkb_model" "pc105"
[   196.860] (**) Option "xkb_layout" "ca"
[   196.860] (**) Option "xkb_variant" "fr-legacy"
[   196.860] (**) Option "xkb_options" "lv3:ralt_switch"
[   196.861] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[   196.861] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   196.861] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   196.861] (II) LoadModule: "synaptics"
[   196.861] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   196.862] (II) Module synaptics: vendor="X.Org Foundation"
[   196.862] 	compiled for 1.9.0, module version = 1.2.2
[   196.862] 	Module class: X.Org XInput Driver
[   196.862] 	ABI class: X.Org XInput driver, version 11.0
[   196.862] (II) Synaptics touchpad driver version 1.2.2
[   196.862] (**) Option "Device" "/dev/input/event8"
[   197.260] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5534
[   197.260] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4932
[   197.260] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   197.260] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   197.260] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   197.580] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   197.580] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   197.740] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   197.740] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   197.740] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   197.740] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   197.740] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   197.980] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   197.981] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[   197.981] (II) No input driver/identifier specified (ignoring)
[   197.984] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event6)
[   197.985] (II) No input driver/identifier specified (ignoring)
[   197.985] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[   197.985] (II) No input driver/identifier specified (ignoring)

---

### Post by Dark_Stang on 2010-11-05
> **Phis said:**
> Once i restart, without nomodeset
So use nomodeset.

Before anybody else wastes a load of time. The 2.6.36 and 2.6.37 kernels will not work with the 256 nVidia drivers. They work fine with the 260 drivers, but our video cards do not. Don't go past 2.6.35.

---

### Post by Phis on 2010-11-16
Nomodeset doesn't work once I have installed the drivers.

The good news is that I finally have Ubuntu 10.10 working on my VPCCW21FX with my 310m card.

I followed instructions from disappearedng on launchpad
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078)

section 92

Here are the instructions (which I have supplemented with my own steps in red):

*1) Remove all nvidia packages* [COLOR="Red"]( you can do this through synaptic)[/COLOR]
*2) download the files and install this [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973339](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973339).*

[COLOR="Red"](for this step I found a deb on a related forum:[/COLOR] [http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb) and [http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb)  

[COLOR="Red"]Here is the forum link: [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)[/COLOR]

[I]3) This is where I tried something different, I read somewhere that you MUST use linux kernel 2.6.36, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/) (thanks to Artem161 from [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)). Download the appropriate architecture files. I downloaded headers, image and headers-amd64
4) Use the custom EDID option in /etc/X11/xorg.conf
*my edid file is located in /proc/acpi/video... yours might be different.
    Option "ConnectedMonitor" "DPF-0"
    Option "CustomEDID" "DPF-0: /proc/acpi/video/IGPU/LCD0/EDID"
    Option "RegistryDwords" "EnableBrightnessControl=1" # For brightness control[/I]

[COLOR="Red"]This is also from: [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup) [/COLOR]

[COLOR="Red"]before I could add this I had to generate the xorg.conf file with: sudo nvidia-xconfig then opened it with: sudo gedit /etc/X11/xorg.conf
adding the lines under section device. The brighness controls aren't fixed for me but I don't really care, its further discussed in the forums.[/COLOR]

[COLOR="Red"]If the custom path for the edid does not here is a link to another thread discussing another way to obtain with other cards. 
[/COLOR]
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

[I]5) 
   sudo update-alternatives --config gl_conf (I picked manual)
   sudo ldconfig
   sudo nvidia-xconfig
   sudo reboot[/I]

Thank you to every one from all the forums.

I followed these steps on a fresh install using 
Dark_Stang's method

And on a good note, this problem is announced to be fixed in the next version of the nvidia driver, lets cross our fingers ! :) ([http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)) last post

---

### Post by onhafoghefifo on 2010-11-16
one question Phis
how is your wireless card working under 10.10?
same problems as before?

---

### Post by Phis on 2010-11-17
I can not answer that question because I do not have the stock wireless card anymore. I did as Dark_Stang instructed above, I bought a different wireless card. I found one on ebay for 20$. A good deal for perfect wireless.

---

### Post by Dark_Stang on 2010-12-24
It looks like the latest 260 drivers from nVidia (260.19.29 right now) work for video. Can somebody else confirm this so I know I didn't just get lucky?

Audio still doesn't work through HDMI so I'm compiling a new kernel today (2.6.36.2) to see if that fixes it. But since I have three Christmas gatherings in the next 16 hours, I probably won't know until Sunday or Monday.

Edit: Kernel compiled a little early. My sound test works, but I still have no sound from anything else. Will work on this more later.
Edit 2: Rob Zombie is gracing my tv right now. Sound appears to be working 100%.

Huge kudos goes to this wiki.
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) 

However in case anything changes, I will post exactly what I've done here.
1. I upgraded my nVidia drivers to 260.19.29
2. I updated my Kernel to 2.6.36.2 - Not sure if this step is needed, but I will post my .debs after they finish uploading to my web server just in case.
3. Added the following line to /etc/pulse/default.pa
```
load-module module-alsa-sink device=hw:1,7
```
4. Make sure your device isn't muted in alsamixer. Run 'alsamixer'. Press F6. Choose HDA NVidia. You can unmute all of them if you want, but it's the 2nd option on our laptops so that's the only one that doesn't need to be muted.
5. Reboot (remember to use 'nomodeset' if you need it)
6. Open up your Sound preferences (System > Preferences > Sound) and choose your new output device (High Definition Audio Controller)

Links to kernel headers and image...
[http://darkstang.com/vpccw21fx/linux-headers-2.6.36.2-ds_2.6.36.2-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-headers-2.6.36.2-ds_2.6.36.2-ds_amd64.deb)
[http://darkstang.com/vpccw21fx/linux-image-2.6.36.2-ds_2.6.36.2-ds_amd64.deb](http://darkstang.com/vpccw21fx/linux-image-2.6.36.2-ds_2.6.36.2-ds_amd64.deb)

---

### Post by Dark_Stang on 2010-12-26
HDMI video and sound are working flawlessly still. Played a little WoW on my TV.

---

### Post by Slayer6 on 2011-01-07
Thanks for all the tips so far.  Still having trouble with audio in 10.10.  Audio was fine in 10.04 as long as i reloaded alsa after each auto upgrade.  After running 10.10 update i had audio but no mic.  After manual alsa update i have nothing.  I've tried everything here and on the other boards. 
Here is what i'm getting


```
mike@mike-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
mike@mike-laptop:~$ 
mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```[COLOR=Blue]
i don't have asound directory???
cat /proc/asound/version
cat: /proc/asound/version: No such file or directory[/COLOR]
[COLOR=Blue]
here is pulse audio config[/COLOR]


```
mike@mike-laptop:/etc/pulse$ cat default.pa 
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hw:1,7
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
#load-module module-alsa-sink device=hw:1,7
```[COLOR=Blue]
the load-module module-alsa-sink device=hw:1,7 is commented out because this isn't found

thanks again for all the help so far and any yal can give me on this one

[/COLOR]

---

### Post by Dark_Stang on 2011-01-07
> **Slayer6 said:**
>  Still having trouble with audio in 10.10.  Audio was fine in 10.04 as long as i reloaded alsa after each auto upgrade.  After running 10.10 update i had audio but no mic.

If it was me, I would simply reinstall straight to 10.10. I never like to do upgrades because of how easily they break things. The only audio trouble I had with this laptop, was HDMI didn't work until a few days ago.

---

### Post by Slayer6 on 2011-01-19
ok, 
i did reinstall 10.10
still no audio hardware 
then i ran this and it worked

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```i'm sure i did this before.  must have fixed something on the reinstall.

all works including hidef audio

at this point i have newer kernel
2.6.35-24-generic
and nouveau drivers insist on loading even with install of 260
placing nomodeset in grub config prevents this. 

```
gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

sudo update-grub
```
 Correct nvidia drivers load.  
tested hardware acceleration and its all working great

  (of course still no wifi :)

---

### Post by Slayer6 on 2011-01-25
I think i have wifi working with the stock board in 10.10

After messing with ndis and blacklisting stock driver wlan0 would no longer show up.  To fix this and anything else I might have messed up experimenting I recompiled kernel 
2.6.35 
modprobed ath9k.  wireless was up but still terrible.


then installed latest compat-wireless from 1/24
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

I am currently not seeing any packet loss and hulu works at 480p.
Could this really be fixed?  Can I actually do my work at the bar now?

--- google.com ping statistics ---
365 packets transmitted, 365 received, 0% packet loss, time 364445ms
rtt min/avg/max/mdev = 25.534/28.556/79.112/4.318 ms

---

### Post by onhafoghefifo on 2011-05-08
After 3 ubuntu versions (from Lucid to Natty) and 1 year of fighting with my wireless card (yes, I don't give up) I finally got my wifi working as it should. All I did is followed these steps:

Create a new file /etc/modprobe.d/ath9k.conf:

sudo nano /etc/modprobe.d/ath9k.conf

Add the following line to it:
options ath9k nohwcrypt=1

Save and reboot. Your wireless should perform significantly better now.

credits: [http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)

---

### Post by zevictor on 2012-04-27
My webcam doesn't work on 12.04.
Anybody else?

---

