---
title: "VirtualBox and Screen Resolution"
date: 2007-11-23
forum: Virtualisation
---

### Post by rayberto on 2007-11-23
I am having a problem adjusting my screen resolution.

I am running a Gateway Laptop, Vista Home Premium, VirtualBox 1.5.2, Ubuntu 7.1.

I am an experienced Windows admin, however I am brand new to Linux, so please dont assume I know anything Linux. If I can copy and paste your commands, that would be best.  Everything is set at default settings.

I installed Ubuntu on my computer using Virtualbox. Just about everything is working correctly, except the video display. It only wants to run at 800x600. I was able to edit the xorg.conf file and add 1024x768 and 1280x800 resolutions. When I change the resolution the screen gets all garbled. I click on cancel and the screen comes back to 800x600. 

I can provide more info if you need it. 

Ray

---

### Post by sstusick on 2007-11-23
It might help to change the amount of Video Ram for the Virtual Machine, and give the VM a bit more RAM, also.

---

### Post by rayberto on 2007-11-23
I moved the video ram all the way to 128mb, I forgot to mention that I installed Guest Addons.

---

### Post by sstusick on 2007-11-23
The video RAM shouldn't need that much...32 MB would suffice, I'd think. The default is 8 MBs.

---

### Post by TravisFix on 2007-11-28
I have a Dell Lattitude D600 and have experianced the same problem. The above solutions didn't help me.  I did found a solution here 

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438) 

I tried to clarify the steps below: 

1. First, make sure your have installed “guest additions” (VirtualBox documentation describes how to do this). This may solve your problem. If not, go on. 
2. To see what resolutions your screen is capable of, on your host machine go to “Preferences” and then “Screen Resolution”. 
3. Create a snapshot of your virtual machine in case the below steps cause you problems. That way you can always revert back to a stable machine. (VirtualBox documentation describes how to do this) 
4. In the terminal type: 

sudo gedit /etc/X11/xorg.conf 
(space after gedit and X11 must be capital X) 

5. You now need to hunt through the text until you see the display resolutions listed. The ones you will be concerned about will be listed under bit depth 24 or bit depth 16 (as these depths are the ones that give you a large amount of colors.) 
6. Next, either replace the existing resolution, or add another listed resolution in the exact same manner. Your resolution must be equal to or less than what the host machine is capable of (see step 2). 
7. Restart the guest machine. Your resolution should be what you have specified or allow it to be changed.

---

### Post by ben2talk on 2007-12-27
I had a similar problem, but I guess I was lucky. I have a HP w1907 monitor which doesn't appear in the list of monitors. I decided on an intelligent solution, and after 30 minutes of trying out monitor settings at random I managed a 1440 by 900 desktop by setting HP D1187A 20-inch display and checking the 'Widescreen Monitor' box. Now my Opera Browser looks rather lovely, and my environment for surfing internet is altogether more human than Vista.

I didn't learn much by doing this, but it worked. If you can't dazzle them with brilliance....

---

### Post by Uncelilo on 2008-01-13
I was having problems just getting it to go to 1024x768 and when I changed the resolution modes using the method TravisFix outlined it would be all messed up. I tried adding more video memory to the machine but that didn't work either. 

To fix it I had to change the bit depth listed from 24 to 16.

---

### Post by billstei on 2008-01-20
FWIW: This is just a log of my experiences getting Ubuntu (Hardy) running inside Virtualbox running inside a Ubuntu (Gutsy) host.

1) Make a copy of the /etc/X11/xorg.conf file.  I called mine xorg.conf-original  If a Bad Thing happens you can log into a failsafe terminal and (sudo) cp this back to xorg.conf and try again.

2) Booting into Hardy I used the VirtualBox menu Devices->Install Guest Additions...  This mounts the CD (virtual image, not a real one) to the Hardy desktop.  DO NOT open that and double click the Linux script.  You need to be root to install it.  Open a terminal and change directory to /media/cdrom

3) Now type:

sudo ./VBoxLinuxAdditions.run

This will build the kernel modules for the video driver (and whatever other Secret Squirrel stuff it does).

4) Reboot.

5) In the rebooted Hardy, go to Ubuntu menu System->Administration->Screens and Graphics.  Under the Graphics Card tab (second one) it should now show vboxvideo (not vesa).  Under the Screen tab I changed the Model of my monitor to Generic->Monitor 1600x1200.  I had no intention of using that much res, but my monitor is capable of 1600x1200 and I could in theory.  Back at the Screen tab I picked Resolution: 1400x1050 (which keeps it reasonably sized on my host 1600x1200 desktop).  There is a Test button, but I found it to be meaningless and/or misleading.  So I eventually learned to just click OK.  Why?  Because I knew it would be.  Your Mileage May Vary.  I was told that I must log out in order to see my nice 1400x1050 choice, which I did, and all was well.

Bill

---

### Post by 23meg on 2008-01-24
I've tried this, but I don't get the "vboxvideo" driver displayed, despite having installed the guest additions.

---

### Post by LeAstrale on 2008-01-24
> **TravisFix said:**
> I have a Dell Lattitude D600 and have experianced the same problem. The above solutions didn't help me.  I did found a solution here 

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438) 

I tried to clarify the steps below: 

1. First, make sure your have installed “guest additions” (VirtualBox documentation describes how to do this). This may solve your problem. If not, go on. 
2. To see what resolutions your screen is capable of, on your host machine go to “Preferences” and then “Screen Resolution”. 
3. Create a snapshot of your virtual machine in case the below steps cause you problems. That way you can always revert back to a stable machine. (VirtualBox documentation describes how to do this) 
4. In the terminal type: 

sudo gedit /etc/X11/xorg.conf 
(space after gedit and X11 must be capital X) 

5. You now need to hunt through the text until you see the display resolutions listed. The ones you will be concerned about will be listed under bit depth 24 or bit depth 16 (as these depths are the ones that give you a large amount of colors.) 
6. Next, either replace the existing resolution, or add another listed resolution in the exact same manner. Your resolution must be equal to or less than what the host machine is capable of (see step 2). 
7. Restart the guest machine. Your resolution should be what you have specified or allow it to be changed.

that worked out nicely with only 8mb gfx ram in Vbox.. ty for the info :)

---

### Post by johnl on 2008-03-21
I also had trouble here.  I finally manged a solution:

Install the guest additions, and reboot as mentioned before.

edit your xorg.conf;  find the section for the video driver.  Mine looked like:

```

Section "Device"
     Identifier "Configured Video Device"
EndSection

```

Change it to specify the vboxvideo driver instead of whatever the default is (vesa?)

```

Section "Device"
     Identifier "Configured Video Device"
     Driver "vboxvideo"
EndSection

```

Save the file, log out, and log back in.  Your VM should now be a much nicer size and you should see additional options under System->Administration->Screen Resolution.

Edit:  The when you log out and log back in the screen should resize to whatever the size of your virtualbox window is.  nice.

---

### Post by MikeBlyth on 2008-04-04
Same problem -- I can't get the vboxvideo driver to work on my virtual Ubuntu system.

I have tried the suggestions in this thread but am stuck. 
[LIST]
[*]There is *no* "Screens and Graphics" entry in the Preferences or Administration menu
[*]The xorg.conf file does not have anything related to a vbox display driver. It only has
[INDENT]Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[/INDENT]
and noting more.
[*]If I add "Driver 'vboxvideo'" to the Device section, the system hangs on rebooting. The only line in Device is "Identifier 'Configured Video Device'"
[/LIST]

I have done fresh installs with Vista and XP as the host, and with Ubuntu 7.something and 8.04 beta as the guest system. I still get the same problem. Every suggestion I've seen about this refers to the "Screens and Graphics" configuration program but mine is missing 

If I run displayconfig-gtk from the command line, it works, but there is no vboxvideo graphics card listed, and nothing by "Innotek", only the usual ones.

vboxvideo_drv.so is listed under /usr/lib/xorg/modules/drivers

Ideas?

---

### Post by Das Oracle on 2008-04-05
> **johnl said:**
> I also had trouble here.  I finally manged a solution:

Install the guest additions, and reboot as mentioned before.

edit your xorg.conf;  find the section for the video driver.  Mine looked like:

```

Section "Device"
     Identifier "Configured Video Device"
EndSection

```

Change it to specify the vboxvideo driver instead of whatever the default is (vesa?)

```

Section "Device"
     Identifier "Configured Video Device"
     Driver "vboxvideo"
EndSection

```

Save the file, log out, and log back in.  Your VM should now be a much nicer size and you should see additional options under System->Administration->Screen Resolution.

Edit:  The when you log out and log back in the screen should resize to whatever the size of your virtualbox window is.  nice.

I just wanted to say that this solution worked perfectly for me, running 8.04 Hardy inside virtualbox, ty

---

### Post by amitk on 2008-04-05
> **Das Oracle said:**
> I just wanted to say that this solution worked perfectly for me, running 8.04 Hardy inside virtualbox, ty

For me too. However, I think I can still get a higher resolution because my screen is not as wide as my laptop can allow. 

Thanks!

---

### Post by vahnx on 2008-04-07
Thanks. The above xorg.conf hack worked for me. (yes I know it's not a hack but it sounds better). Now I'm no longer 800x600 or 640x400 (whatever I was). But mine doesn't auto resize like you peoples say. Running Ubuntu 8.04 Hardy Heron Alpha 6

---

### Post by atcronos on 2008-04-07
You could also try this:

[ubuntuforums.org/showthread.php?t=727503&highlight=xubuntu+seamless]("ubuntuforums.org/showthread.php?t=727503&highlight=xubuntu+seamless")

If you do this you don't have to worry about the VM screen resolution. It works with XP professional, I don't know if it works with vista.

---

### Post by jmckean on 2008-04-15
> **billstei said:**
> FWIW: 

4) Reboot.

5) In the rebooted Hardy, go to Ubuntu menu System->Administration->Screens and Graphics.  

Bill

Tried this withhHardy on VBox with Gutsy host, but there is no "Screens  and Graphics" under Admin.  ??  Checked under Edit Menus to make sure it just wasn't hidden.  "Screen Resolution" under preferences has no useful settings.

If this happens to you, command line to start "Screens and Graphics is 

gksu displayconfig-gtk

---

### Post by RayPioli on 2008-04-26
I am really struggling on this and am new to this ubuntu stuff

I have tried "every" suggested modification of xorg.conf but all to no effect although many users appeared to have gotten them to work.

I am using the new Ubuntu 8.4 with VirtualBox 1.5.6 (with Guest Additions installed).

But Screen/Size Resolution only gives me the option 800x600 and 640x480

Currently my xorg.conf file contains

DefaultDepth 24
	SubSection "Display"
	Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection 
	EndSection

But it does not seem to affect anything.

Also the menu item "Screens and Graphics" does not appear under Administration and I have only just learned that I can use command gksu displayconfig-gtk. 

(Come back Bill Gates most is forgiven)

Greatful for advice as current resolution is close to unworkable

Ray

---

### Post by pi2deatn on 2008-04-26
> **RayPioli said:**
> I am really struggling on this and am new to this ubuntu stuff

I have tried "every" suggested modification of xorg.conf but all to no effect although many users appeared to have gotten them to work.

I am using the new Ubuntu 8.4 with VirtualBox 1.5.6 (with Guest Additions installed).

But Screen/Size Resolution only gives me the option 800x600 and 640x480

Currently my xorg.conf file contains

DefaultDepth 24
	SubSection "Display"
	Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection 
	EndSection

But it does not seem to affect anything.

Also the menu item "Screens and Graphics" does not appear under Administration and I have only just learned that I can use command gksu displayconfig-gtk. 

(Come back Bill Gates most is forgiven)

Greatful for advice as current resolution is close to unworkable

Ray

I'm having the same issue you are having, Ray, except you are the lucky one who has SubSection Modes and screen resolution settings shown.  My xorg.conf hasn't got any of it.

Any ideas?

---

### Post by RayPioli on 2008-04-27
pi2deatn

Id didn't habe them originally I simply cupied and pasted then using into the file
Ray gedit

---

### Post by pi2deatn on 2008-04-27
If it's this hard just to get Ubuntu to run full screen mode in VirtualBox, I'm done hassling.  Dual-boot time.

---

### Post by wilrt on 2008-05-03
Upgrading to VirtualBox 1.6 fixed this for me (as also posted here: [http://ubuntuforums.org/showthread.php?t=779414](http://ubuntuforums.org/showthread.php?t=779414)). The referenced thread poster was using OSX as host with Ubuntu 8.04 as Guest. The same fix worked for me and I'm running WinXP as host and Ubuntu 8.04 as guest. 

Hope this helps.

---

### Post by xtreme35967 on 2008-05-09
I also updated too VB 1.6 and this fixed my problem. Also thanks for posting the command for Screens and Graphics. I just added a button to my menu so I can easily get too it in the future.

---

### Post by muzzamo on 2008-05-17
for me the trick was to install the guest software, then run 

sudo displayconfig-gtk

then use choose a generic model screen that has the same resolution as my screen. Then i can choose whatever i want for the resolution.

---

### Post by Ubeaut on 2008-06-09
There's a new, simple solution to this problem since VirtualBox 1.6.2.

Check out my post at:

[http://ubuntuforums.org/showthread.php?p=5145028#post5145028](http://ubuntuforums.org/showthread.php?p=5145028#post5145028)

.

---

### Post by Etoile on 2008-08-08
Boy howdy, all the stuff in this thread didn't help except for one thing: **SEAMLESS** resolution!  Host+L brings you in and out of it.  It basically fits the resolution of your host machine; it seems to even eliminate the need to pop in and out of the VM all the time!  This is pretty cool. :)

Wait, also: if you don't want to have the two blended, use Host+A to resize the window, and the guest should automatically fit the window size.  Then you can do Host+F for full-screen and it won't look like you're running the host at all! :D

---

### Post by Masoris on 2008-08-11
> **rayberto said:**
> I am having a problem adjusting my screen resolution.

I am running a Gateway Laptop, Vista Home Premium, VirtualBox 1.5.2, Ubuntu 7.1.

I am an experienced Windows admin, however I am brand new to Linux, so please dont assume I know anything Linux. If I can copy and paste your commands, that would be best.  Everything is set at default settings.

I installed Ubuntu on my computer using Virtualbox. Just about everything is working correctly, except the video display. It only wants to run at 800x600. I was able to edit the xorg.conf file and add 1024x768 and 1280x800 resolutions. When I change the resolution the screen gets all garbled. I click on cancel and the screen comes back to 800x600. 

I can provide more info if you need it. 

Ray

That's a bug: [http://www.virtualbox.org/ticket/1689](http://www.virtualbox.org/ticket/1689)

---

### Post by vandorjw on 2008-08-18
try this

sudo dpkg reconfig xorg-xserver

answer all questions and set resultion to **your** native (maximum) resultion

---

### Post by axel206 on 2008-08-18
Well this is an old thread. :P

When I tried installing ubuntu 8.04 on Virtualbox 1.6.2 and 1.6.4 I had no problems with the resolution. Here is some info.

[How to install Ubuntu Linux on Windows using VirtualBox](http://www.my-guides.net/en/content/view/112/26/)

---

### Post by charlie763 on 2008-10-09
I'm running Ubuntu 8.04 as the host system. I have Windows XP as the guest. I had seamless mode working at 1600x1200 in VirtualbBox 1.6. After installing 2.0.0 the best I can get is 1400x1050. Anyone have a solution?

---

### Post by backdoc on 2008-11-08
> **billstei said:**
> 
3) Now type:   sudo ./VBoxLinuxAdditions.run


This is the key.  I was double clicking the icon on the desktop and running it in a console window.  It was failing because of insufficient privileges, but I couldn't see that because the window closed too fast.

---

### Post by miguelreyes98 on 2008-11-21
This is what worked for me:

 Ubuntu in virtual box dynamic resolution

1. Run ubuntu in virtualbox
2. Go to Menu: devices -> Install Guest Additions
3. Cd-rom drive is loaded (it shows on the desktop)
4. Open terminal and run:
    $ cd /media/cdrom
    $ sudo bash ./VBoxLinux*
5. Restart Ubuntu virtual box

Now you can resize the window and it resizes the screen resolution automatically.

/Miguel

---

### Post by miguelreyes98 on 2008-11-21
This is what worked for me:

 Ubuntu in virtual box dynamic resolution

1. Run ubuntu in virtualbox
2. Go to Menu: devices -> Install Guest Additions
3. Cd-rom drive is loaded (it shows on the desktop)
4. Open terminal and run:
    $ cd /media/cdrom
    $ sudo bash ./VBoxLinux*
   Note: There are many VBoxLinux files depending on the Linux version. I just tried with the x64 and it worked.
5. Restart Ubuntu virtual box

Now you can resize the window and it resizes the screen resolution automatically.

/Miguel

---

### Post by LaughingBubba on 2008-12-26
Here's what worked for me (trying to run Ubuntu 8.10 as a VBox image @ 1280x768 resolution on Kubuntu 8.04 with VBox 2.06 ... PS: Native res on my LCD is 1440x900)

Perquisites:
[LIST=1]
[*]VBox guest additions installed on Guest/OS
[*]Correctly configured xorg.con file (post additions)
[/LIST]

Method:
[LIST=1]
[*]Change default ISO for VBox image to point to "VBoxGuestAddions.iso"
[*]Start the VBox image (you should now see the new ISO)
[*]Start the Command Line Interface (CLI) using Applications->Accessories->Terminal
[*]At the the CLI type the following:
[*]sudo /media/cdrom/VBoxLinuxAdditions-x86.run
[*]Note the file name extension based on your architecture (x86) as this may be different based on your cuurent hardware setup
[*]This will install the guest additions (it may ask you to restart but before you do) at the CLI type the following:
[*]sudo gedit /etc/X11/xorg.conf add these lines to the designated sections:
section Device:

   Driver "vboxvideo"

And this to the section Screen:

   DefaultDepth 24
   SubSection "Display"
      Depth 24
      Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubSection
[*]Restart the Guest/OS
[*]When it starts you may find that the Window is bigger than usual.
[*]In the Guest/OS go to System->Preferences->Screen Resolution to chnage your updated preferences
[*]Done
[/LIST]

After I did this I was able to copy/paste between Host and Guest as well as change my resolution.

Sources:
This Post/Thread
This URL for install of guest addition:
[http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/]("http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/")
This URL for th xorg.conf set up:
[https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/30718]("https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/30718")

If this was useful, drop me a line so I can feel validated :)

Cheers.

---

### Post by afecelis on 2009-01-17
LaughingBubba your tip nailed it!  :D

Thanks a lot, works like a charm!

regards,
Alvaro

---

### Post by the2ndfrog on 2009-01-24
Upon installing GuestAdditions, my Ubuntu switched to a "Plug&Play Monitor". I needed to enlarge the VM window to access larger resolutions, apparently Ubuntu takes the VM window size as the maximum screen resolution. 

(If you have never worked with Linux before, the VM manual is of limited help - it should explain where to find the terminal, how to get to the root directory in order to type in the code that the manual contains, how to use "sudo"... no wonder many people give up on it and stay with Windows. I have an ATI Mobility Radeon 3650 for which there is apparently no Linux driver, so i had to use the VM.)

---

### Post by doggystyle on 2009-02-25
Ever tried right ctrl+g? 

Or "Machine" -> "Change guest screen size automatically" in the guest Window?

--
Kisses from Sweden

---

### Post by n3wbi32linux on 2009-03-02
Hi,

Tried what's suggested on this thread in order to be able to change screen resolution on Ubuntu 8.10 running under VirtualBox running on Mac OSX 10.5 however am having no joy in changing the resolution from 800x600.

Any suggestions on how to get up and running would be appreciated.

Thank you.

---

### Post by crownedzero on 2009-09-04
I tinkered with this for a a couple minutes and got it working in part thanks to this thread and another I found.

Make sure you install the 'Guest Additions' from the Sun console. Once this is done you should see a cd image on the desktop, open it and double click the autorun. Mine popped up a terminal and installed. I also added the 'vboxdriver' in the xorg.conf according to this thread.

REBOOT and I was gtg.

---

### Post by welshsteve on 2010-03-22
My problem is the other way round.  I am running Ubuntu 8.10 and have installed Windows XP inside Virtual Box because i wish to use Demand Five on [www.five.tv]("http://www.five.tv"), which doesn't support my operating system.  However, the Windows XP screen is tiny, and I wish to make the screen bigger, but there don't seem to be any options to do so in the VirtualBox menus.  Can anybody help?

---

### Post by keerthi on 2011-03-13
Just installing virtualbox "guest additions" resolved my issue.

This is what I did. (on Ubuntu 10.04)

1. Installed virtualbox-guest-additions on parent/host OS.
2. Then an iso image will be available in /usr/share/virtualbox/
3. In virtual box interface, created Storage Device (CD/DVD) for guest OS with above ISO.
4. Started Guest OS (another ubuntu setup in my case)
5. CD ROM with virtualbox-guest-additions now available in guest os.
6. Open a terminal, change to particular CD rom, and execute

sudo ./VBoxLinuxAdditions-x86.run

7. That's it. Restart the virtual machine :popcorn:

---

