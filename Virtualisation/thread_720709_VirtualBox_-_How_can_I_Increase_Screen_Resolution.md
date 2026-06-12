---
title: "VirtualBox - How can I Increase Screen Resolution??"
date: 2008-03-10
forum: Virtualisation
---

### Post by 449 on 2008-03-10
Is there anyway I can getting better resolution for StarCraft in VirtualBox?

[http://i27.tinypic.com/amsn9.png](http://i27.tinypic.com/amsn9.png)

---

### Post by andy_blah on 2008-03-10
Try pressing RightCtrl+F. That will switch to full screen, still I don`t know if it will show you the guest OS on the whole screen.

---

### Post by 449 on 2008-03-10
> **andy_blah said:**
> Try pressing RightCtrl+F. That will switch to full screen, still I don`t know if it will show you the guest OS on the whole screen.

All that does is increase the window size, not the actual resolution. Here is the resolution of XP, and when I load Starcraft it goes to half size. 

[http://i30.tinypic.com/10h7zpe.png](http://i30.tinypic.com/10h7zpe.png)

---

### Post by dje on 2008-03-10
Have you installed the guest additions? If not try installing it, that should make it fill the entire screen when your press right Ctrl (not left) and F
Have a look [here]("http://fieldyweb.co.uk/blog/?p=465") for guest addition install help

Hope that helps you
dje

---

### Post by 449 on 2008-03-10
> **dje said:**
> Have you installed the guest additions? If not try installing it, that should make it fill the entire screen when your press right Ctrl (not left) and F
Have a look [here]("http://fieldyweb.co.uk/blog/?p=465") for guest addition install help

Hope that helps you
dje

Nothing happens when I click "Install Guest Additions..."

---

### Post by 449 on 2008-03-10
Ok, I followed the other instructions and mounted the guest iso manually, but nothing is different. 

?

---

### Post by lswest on 2008-03-10
have you tried changing the resolution of starcraft itself? i seem to remember it being defaulted at 800x600

---

### Post by linuxlizard on 2008-03-10
I didn't think starcraft resolution could be changed even when running native in windows.

---

### Post by lswest on 2008-03-10
hmm, i seem to remember it being able to go up to 1024 x 768...might be wrong though, never really played it.

---

### Post by Therion on 2008-03-10
> **449 said:**
> 

Nothing happens when I click "Install Guest Additions..." 
I don't know if you simply want to play at full screen, or if you want to increase the display resolution, but I do think you need to install Guest Additions properly (either way).  

To do that select Guest Addtions from the "Devices" menu in your VM.  It nothing happens when you do that, then go to "My Computer" and double-click on the CD icon. This should launch the wizard to install some additional drivers.  Follow the wizard, accept the license, ignore the unsigned driver warnings, etc. At the end, reboot the virtual machine.  Now you can go in and out of the VM with your mouse without it being trapped inside the VM. You can also resize the window, and the VM will automatically adjust the resolution.

---

### Post by 449 on 2008-03-10
> **Therion said:**
> I don't know if you simply want to play at full screen, or if you want to increase the display resolution, but I do think you need to install Guest Additions properly (either way).  

To do that select Guest Addtions from the "Devices" menu in your VM.  It nothing happens when you do that, then go to "My Computer" and double-click on the CD icon. This should launch the wizard to install some additional drivers.  Follow the wizard, accept the license, ignore the unsigned driver warnings, etc. At the end, reboot the virtual machine.  Now you can go in and out of the VM with your mouse without it being trapped inside the VM. You can also resize the window, and the VM will automatically adjust the resolution.

Ok, so I successfully installed the Guest Addon ,but it's still jumping back to the tiny resolution when I try to play Starcraft. 

Any suggestions??

---

### Post by gui3 on 2008-03-11
i'm having the same problem, but running ubuntu as the guest and osx as the host.

i posted this in another thread:

I'm using Vbox on my macbook pro.
i started with a fresh install of 7.10, installed updates, installed builder-essentials and installed guest additions.

i followed all the advice i could find on this forum - booted into recovery mod, did the reconfigure, added 1440x900 resolution, and there is no change.

if i mess with xorg.conf directly, either nothing happens or the video won't boot properly.
when i go to preferences --> screen resolution, the max is still 800x600.
when i go to administration --> screen and graphics, its listed as "plug n play" with max res 800x600.
if i change "plug n play" to "LCD Panel 1440x900", the video goes crazy after reboot.

there's got to be something i'm missing

---

### Post by lswest on 2008-03-11
you'd need the drivers for the card that's in your laptop to get that resolution, but the thing with virtual machines is that they (at least, vmware and virtualbox, not sure about Qemu) use virtual hardware, which is generic, meaning, you get basic fuctionality (probably even using the VESA driver atm) but nothing more.  No compiz, no high resolutions, etc.

---

### Post by gui3 on 2008-03-11
> **lswest said:**
> you'd need the drivers for the card that's in your laptop to get that resolution, but the thing with virtual machines is that they (at least, vmware and virtualbox, not sure about Qemu) use virtual hardware, which is generic, meaning, you get basic fuctionality (probably even using the VESA driver atm) but nothing more.  No compiz, no high resolutions, etc.

i have seen plenty of posts about how people using ubuntu as a guest and are running 1440x900. i've followed all their directions to the letter but i'm getting nowhere!

---

### Post by gui3 on 2008-03-12
can anyone help?

---

### Post by ozz314 on 2008-05-08
I successfully added the screen resolution of 1280x800 to my hardy installation on virtualbox with my macbook as host.

Instructions [here]("http://ozz314.wordpress.com/2008/05/06/ubuntu-resolution-fix-using-virtualbox-on-macbook/").

Anyone get shared folders working with Ubuntu guest and mac host using virtualbox?

---

### Post by Xnyper on 2008-06-07
Once you've installed the guest tools, you can increase the screen resolution just by dragging the outside of the window.  The problem is, regardless of what windows is doing, starcraft runs at 640x480.  If you find a tweak to make starcraft run at a higher resolution, that should do the trick.  If you want to do it by messing with virtualbox... good luck

---

### Post by jmcwb on 2008-06-08
After struggling with increasing Screen Resolution for months, I finally found that ignoring xorg.conf was the best way to go, This is the contents of my xorg.conf:

Section "InputDevice"
        Identifier  "VBoxMouse"
        Driver      "vboxmouse"
        Option      "CorePointer"
EndSection


I'm running with 1280x1024 instead of the default 1024x768 by using the setting in startupmanager.  This adds vga=775 to the kernel line in the /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c9d44d29-9154-49cb-a612-c6fb39dc294c ro quiet splash vga=775

---

### Post by Ubeaut on 2008-06-08
There's a great new simple solution to the screen size problem since the release of VirtualBox version 1.6.2.

It's a new VBoxManage command, explained in the Help Contents/ User Manual at section 9.12 under the heading "Configuring the maximum resolution of guests when using the graphical frontend".

As the default screen resolution option was unsatisfactory for me, I found by trial and error that the perfect resolution for a Guest on my Host's desktop (with a 19 inch LCD) is 1272 x 920. So in my HOST system, I shut down VirtualBox, then opened a terminal and typed:

VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

This worked perfectly. Now when I run any guest machine in Virtualbox, the guest immediately opens to my desired screen size (1272x920) and it works consistently time after time. You can set any screen size you want this way. Absolutely no adjustments are required inside the guest machine's settings.

---

### Post by CRMcMullen on 2008-06-13
Thank you Ubeaut!!  ... the "setextradata" info was exactly what I needed.  That permanently assigned my resolution settings just like I wanted.

---

### Post by axcairns on 2008-06-15
This is doing my head in. I've got a Hardy guest running on a Hardy host and nothing I have tried has provided me any resolution other than 640x480 and 800x600. 

I have tried just about every solution on this forum and outside including MaxGuestResolution, CustomVideoMode1, adding mode lines to xorg.conf and vga= parameters to grub/menu.lst. Guest additions have been installed (my cursor is no longer trapped in the box), but does not appear to have had any impact on screen resolution. Resizing the Virtual Box window and the auto-resize menu option have no impact on the guest resolution.

Is there something obvious I am missing?

Thanks,

Allan

---

### Post by tbenk on 2008-06-17
Hi,

none of the solutions worked for me, but here is my addition:

Go to [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and calculate the Modeline for your desired resolution.

This was Mine:

```
Modeline "1600x1200@60" 176.70 1600 1632 2296 2328 1200 1224 1236 1261
```

Then use xrandr to add the new resolution and activate:

```
xrandr --newmode "1600x1200" 176.70 1600 1632 2296 2328 1200 1224 1236 1261
xrandr --addmode "1600x1200"
xrandr -s "1600x1200"
```

Maybe this helps anyone struggling around.

Greetings,
-timo

---

### Post by Virtua-Touch on 2008-06-20
My host is Windows XP and I'm running 8.04 Hardy Ubuntu and it's stuck at 800x600. I haven't seen anyone asking about this who had Window as the host.

---

### Post by thegreatpretender on 2008-06-22
I got full 1680x1050 resolution working. This is maximum for my lcd-monitor. Here is a summary of how I did it. Hope this can be of help.

System set-up:
Host: Ubuntu Studio 8.04 AMD 64 (Hardy)
Guest: Ubuntu 8.04 x86 (Hardy) - I was not able to run AMD64 versions of Ubuntu as the guest system.


First, setting up the host system: 

1. Before starting, it is always a good idea to download and install all updates from the repositories, including kernel updates. Especially so in this case since we will be compiling kernel modules and this can save you the the work of recompiling again when Ubuntu releases a new kernel version.
2. After updating, restart your computer to load the new kernel, if any.
3. Install the kernel source and some other tools. This is needed because VirtualBox will be compiling kernel modules:

sudo apt-get -s install build-essential linux-headers-`uname -r`

4. Download VirtualBox 1.6.2 binary version (not open source edition) from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads). I selected the Ubuntu 8.04 AMD 64 version.
5. Install VirtualBox by double-clicking on the icon of the downloaded file.
6. Add users that will be using VirtualBox to the group vboxusers. 
7. Do a small fix a needed in Ubuntu to make USB work properly and to prevent an error message from appearing when entering settings for USB in VirtualBox. This is explained in the VirtualBox FAQ. What you have to do is edit the script `/etc/init.d/mountdevsubfs.sh and uncomment the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

sudo /etc/init.d/mountdevsubfs.sh start


Then, setting up the guest system:

1. Start VirtualBox on the host and install the guest OS from an ISO-file og CD.
2. I got a kernel panic when trying to install the guest system. The solution that worked for me was to enable ACPI, IO APIC, VT-x/AMD-V and PAE/NX in settings - general - advanced in VirtualBox, but I am not sure what actually made the magic...
3. Install all updates from the repositories, including kernel updates.
4. Restart the guest OS
5. Install some special drivers to get smoother screen, keyboard and mouse performance: When the guest OS is running, select "Install guest additions" from the Devices menu of VirtualBox. A virtual CD is mounted on your system with the files needed. Start a terminal and do

cd /media/cdrom
sudo bash ./VBoxLinuxAddition.run

Then restart your system and when you log in you should have a full resolution.

Good luck!

---

### Post by kvdbreem on 2008-06-24
This method worked for me.  The trick appears to be in referencing the vboxdriver under the device section.  Thanks for the code snippet.  It was getting cramped working in 800/600.

---

### Post by junkam on 2008-07-01
Here is an easy step by step instructions of [changing resolution for Ubuntu 8.04 running under VirtualBox]("http://www.aviransplace.com/2008/07/01/change-screen-resolution-for-ubuntu-804-running-under-virtualbox/")

---

### Post by TheBuzzSaw on 2009-03-22
> **449 said:**
> Is there anyway I can getting better resolution for StarCraft in VirtualBox?

[http://i27.tinypic.com/amsn9.png](http://i27.tinypic.com/amsn9.png)
I am having this exact same problem.

I have the latest version of VBox. I have properly installed Guest Additions. I am running Full Screen mode. Starcraft still floats in the middle of the screen with black all around it. Is there really no way to make it stretch? Sadly, I have to use WINE to accomplish this, but I don't like doing it that way because I use dual monitors, and I have to disable one monitor, save my xorg file, and do a partial reboot. I have VBox running full screen on just one monitor (just the way I like it), but Starcraft will not stretch!

Are there any modern tricks to making this work? I've read over this thread (and many places found through Google), and nothing seems to help. :(

---

### Post by Armchair on 2009-03-22
Hey BuzzSaw,

I've recently moved from Windoze to Ubuntu 8.10 and ain't going back, except for the need to play the odd game which I figured would be cooool inside a VM. I used VMWare in my day job but am embracing the OpenSource ethos so I'm using VirtualBox.

I found out that no VM product does Direct3D yet, so Dawn of War was out unless I go to WINE, and that's only another VM away. So I figured I'd try to load Starcraft and see how that went. (And I'm glad I'm not the only retro-gamer alive!)

I was pondering this thread for the last couple of hours and realised that VirtualBox doesn't offer a Display differential between the Host Display Setting and the Guest Display Setting. At this point it seems to be an automatic thing without any user selection/configurability.

Now the following isn't clean, but I figured if it's automatic why not set the Host display to 640x480? I'm running an nvidia 8600GT, and through the Nvidia X Server Settings I changed the display to 640x480 (while the Starcraft VM was running), clicked back into the Starcraft VM, Right Ctrl + F, and now windoze is full screen at 640x480, Clicked 'Take me to the pixel death gallery' and Starcraft is now as it was full screen stretched on my 22 in widescreen monitor.

As I said it isn't perfect, but it's simple enough to choose and re-choose the display setting and it sure was nostalgic to hear "Jacked up and ready to go!"

As I learn more there may be a way to automatically resize both Host and Guest when Guest is started, and reset when Guest is closed, or a future development of VirtualBox may be to enhance Guest Additions and split the Host/Guest Display Settings, but only time will tell.

Happy Hunting, Lloyd.

---

### Post by TheBuzzSaw on 2009-03-22
This works, but it still does not solve my dual monitor issue. I'd like one monitor to stay at its full 1280x1024 while the other switches to 640x480.

---

### Post by Armchair on 2009-03-22
Sorry BuzzSaw, I'm too new to the environment to answer that one, and don't have 2 monitors connected to have a play for you.

Do you run the monitors separately out of the video card? (2 separate cables?) Do the Monitors each represent 1 Linux Workspace or is 1 Workspace represented across 2 monitors?

Does the video card allow you to specify the resolution differently for each? What about the user control System-Preferences-Screen Resolution, does that allow you to specify separate screen resolutions?

Cheers, Lloyd.

---

### Post by TheBuzzSaw on 2009-03-24
> **Armchair said:**
> Sorry BuzzSaw, I'm too new to the environment to answer that one, and don't have 2 monitors connected to have a play for you.

Do you run the monitors separately out of the video card? (2 separate cables?) Do the Monitors each represent 1 Linux Workspace or is 1 Workspace represented across 2 monitors?

Does the video card allow you to specify the resolution differently for each? What about the user control System-Preferences-Screen Resolution, does that allow you to specify separate screen resolutions?

Cheers, Lloyd.
The monitors both run out of one NVidia card (one DVI, one VGA). Both monitors constitute a single workspace (essentially a 2560 width display instead of a lonely 1280), but each monitor has a light constraint (I can drag a window over and then have it maximize onto just one monitor).

I have several graphic settings I can tweak. I have no problem getting VBox to fill up one monitor. I just can't get programs *inside* VBox to stretch to fill its window. :(

---

### Post by mister_playboy on 2009-03-27
Starcraft is a tricky one.  On my Sony Vista (now Ubuntu) laptop, full screen would just leave the normal size screen in a sea of black.  My brother's Dell laptop would stretch the screen for fullscreen... neither laptop could be convinced to display the way the other did!  Each option seemed set in stone at the hardware level.

Very confusing.

---

### Post by deepagnv on 2009-04-29
[http://www.aviransplace.com/2008/07/01/change-screen-resolution-for-ubuntu-804-running-under-virtualbox/](http://www.aviransplace.com/2008/07/01/change-screen-resolution-for-ubuntu-804-running-under-virtualbox/)

This is what worked for me after hours of trying out different things. By the way, my host is XP Pro and guest is Ubuntu 9.04

Good luck!:):guitar:

---

### Post by stukpixel on 2009-05-02
I don't see how your suggestion solves the issue of stretching the starcraft window in virtual box.

---

### Post by areskz on 2009-06-26
My topic is close to this, so I will not create a new thread.

I have a Kubuntu 8.04 host, and a Windows XP guest. I'm trying to launch Starcraft in Windows XP. While trying to stretch small starcraft window to fullscreen I changed the resolution in windows for 800x600, and it resulted in this:

[IMG]http://img134.imageshack.us/img134/5933/vbxp.jpg[/IMG]

So, I can't even stretch windows resolution.
Someone has an idea?

---

### Post by TheBuzzSaw on 2009-06-26
That's basically it. VBox does not allow for graphic stretching. I am hoping that changes in an upcoming release.

---

### Post by isaacalves27 on 2010-01-07
> **Ubeaut said:**
> There's a great new simple solution to the screen size problem since the release of VirtualBox version 1.6.2.

It's a new VBoxManage command, explained in the Help Contents/ User Manual at section 9.12 under the heading "Configuring the maximum resolution of guests when using the graphical frontend".

As the default screen resolution option was unsatisfactory for me, I found by trial and error that the perfect resolution for a Guest on my Host's desktop (with a 19 inch LCD) is 1272 x 920. So in my HOST system, I shut down VirtualBox, then opened a terminal and typed:

VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

This worked perfectly. Now when I run any guest machine in Virtualbox, the guest immediately opens to my desired screen size (1272x920) and it works consistently time after time. You can set any screen size you want this way. Absolutely no adjustments are required inside the guest machine's settings.
Hi Ubeaut

I have just updated to the last version of VirtualBox. My host is Ubuntu Hardy and guest is windows 7. when I use the command you have used I get no changes.
VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

I can change the display settings inside the guest but the screen is never stretched to its max..

Any ideas why setextradata isnt performing as it should?

Isaac

---

### Post by lammi02 on 2010-05-08
Just 2 cents from me on ubuntu 10 Lucid Lynx with Win 2k3 std guest.

 -Right click on the windows desktop and select properties
- on the Display properties , select settings tab and click on advanced button
- select the VBOX adapter and select update the driver .

the goal here is to replace the VBOX driver into SVGA adapter and do a reboot .

From here you can select any resolution you wanted.


Gilbert

---

### Post by STEPHANVS on 2010-08-30
Try this:

```
VBoxSDL --detecthostkey
```
Select your hostkey, for me Right CTRL gave 305 128.

```
VBoxSDL --hostkey 305 128 --startvm "Windows XP"
```
Replace 305 128 with the numbers the first command gave you, "Windows XP" with the name of your virtual machine.

Start the game, then press HostKey+F. It will switch the screen resolution when going to fullscreen.

Cheers.

---

### Post by rleck on 2010-10-02
*An update to Ubeaut's excellent advice, from section 9.6.2 of the virtualbox help manual, currently VirtualBox version 3.2.8*

VBoxManage setextradata global GUI/MaxGuestResolution any

*will remove all limits on guest resolutions.*

VBoxManage setextradata global GUI/MaxGuestResolution >width,height<

*manually specifies a maximum resolution.*

VBoxManage setextradata global GUI/MaxGuestResolution auto

*restores the default settings. Note that these settings apply globally to all guest systems, not just to a single machine.*

---

### Post by mcpastor on 2010-12-07
> **Ubeaut said:**
> There's a great new simple solution to the screen size problem since the release of VirtualBox version 1.6.2.

It's a new VBoxManage command, explained in the Help Contents/ User Manual at section 9.12 under the heading "Configuring the maximum resolution of guests when using the graphical frontend".

As the default screen resolution option was unsatisfactory for me, I found by trial and error that the perfect resolution for a Guest on my Host's desktop (with a 19 inch LCD) is 1272 x 920. So in my HOST system, I shut down VirtualBox, then opened a terminal and typed:

VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

This worked perfectly. Now when I run any guest machine in Virtualbox, the guest immediately opens to my desired screen size (1272x920) and it works consistently time after time. You can set any screen size you want this way. Absolutely no adjustments are required inside the guest machine's settings.

Thanks dude. Absolutely perfect!

---

### Post by TheBuzzSaw on 2010-12-07
> **mcpastor said:**
> Thanks dude. Absolutely perfect!

Oh please do not resurrect old threads *just* to thank people. Resurrect old threads when you have something meaningful to add.

---

### Post by KFlannigan5 on 2011-03-25
*Genius...pure genius*

---

### Post by PlanetT on 2011-07-24
> **Ubeaut said:**
> There's a great new simple solution to the screen size problem since the release of VirtualBox version 1.6.2.

It's a new VBoxManage command, explained in the Help Contents/ User Manual at section 9.12 under the heading "Configuring the maximum resolution of guests when using the graphical frontend".

As the default screen resolution option was unsatisfactory for me, I found by trial and error that the perfect resolution for a Guest on my Host's desktop (with a 19 inch LCD) is 1272 x 920. So in my HOST system, I shut down VirtualBox, then opened a terminal and typed:

VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

This worked perfectly. Now when I run any guest machine in Virtualbox, the guest immediately opens to my desired screen size (1272x920) and it works consistently time after time. You can set any screen size you want this way. Absolutely no adjustments are required inside the guest machine's settings.

Thanks dude, this really works!

---

### Post by mcquoidellum on 2011-09-13
> **Ubeaut said:**
> There's a great new simple solution to the screen size problem since the release of VirtualBox version 1.6.2.

It's a new VBoxManage command, explained in the Help Contents/ User Manual at section 9.12 under the heading "Configuring the maximum resolution of guests when using the graphical frontend".

As the default screen resolution option was unsatisfactory for me, I found by trial and error that the perfect resolution for a Guest on my Host's desktop (with a 19 inch LCD) is 1272 x 920. So in my HOST system, I shut down VirtualBox, then opened a terminal and typed:

VBoxManage setextradata global GUI/MaxGuestResolution 1272,920

This worked perfectly. Now when I run any guest machine in Virtualbox, the guest immediately opens to my desired screen size (1272x920) and it works consistently time after time. You can set any screen size you want this way. Absolutely no adjustments are required inside the guest machine's settings.

Totally worked for me, Natty 8,1 Macbook pro, with ubuntu 10.04.3. Thanks!!

---

### Post by thelastbiscuitinthetin on 2011-11-19
> **Xnyper said:**
> Once you've installed the guest tools, you can increase the screen resolution just by dragging the outside of the window.  The problem is, regardless of what windows is doing, starcraft runs at 640x480.  If you find a tweak to make starcraft run at a higher resolution, that should do the trick.  If you want to do it by messing with virtualbox... good luck


I feel like a complete retard. This worked for me after trying so many things. To think it was so easy. I've had my head in a terminal for too many days! Thanks so much. :popcorn:

Edit: I should say the dragging worked for me. I don't play Starcraft, but we'll see how other games do with the dragging solution. Will report back.

---

