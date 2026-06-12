---
title: "Increase Resolution of Ubuntu?"
date: 2010-03-29
forum: Virtualisation
---

### Post by fallenshadow on 2010-03-29
Is there anyway I can expand the resolution of Ubuntu?
Note: I am using Virtualbox 3.1.6 on Ubuntu 8.10 and 9.10 is the Guest OS.

At the moment its running at 800x600 and it should be 1024x768. I have already installed Guest additions but it made no difference.

---

### Post by runix on 2010-03-29
fallenshadow.

I had the same problem. I had to play endless ours with my xorg.conf until I got it somewhat nice look, but then I had some problems while reconfiguring Grub and Uspash. 

I had to switch to VMware. I know that is not open source but until Sun fixes VirtualBox I have to stay with VMaware.

Good Luck

---

### Post by realzippy on 2010-03-29
*VMaware*

...pretty nice typo !!

---

### Post by fallenshadow on 2010-03-29
Whether it is Open source or not does not bother me really but I just want something that works. Its a pity because other than this problem I really like Virtualbox.

Ok I will give VMware a try then. Thanks for the advice! ;)

---

### Post by fallenshadow on 2010-03-29
Hmm... where can I download Vmware?

I find their website really hard to navigate and I don't know what VMware version im looking for.

---

### Post by mkvnmtr on 2010-03-29
You say you installed guest additions: Did you run the installation file? On windows it is offered automaticly bout on all my linux installs I have to find it and run it.

---

### Post by fallenshadow on 2010-03-30
Yes I found the correct one and ran it as root.

---

### Post by codfather on 2010-03-31
Unfortunately to get VMware workstation, you have to buy it, which costs around $150. You can use VMware server version 2.0, but you only have a web interface to manage that , and it can be very fiddly to set up.

As 9.10 doesn't have an xorg.conf by default, you can create one though easily enough.

To do this first exit to the console using the following command:

sudo service gdm stop

Then create an Xorg configuration file with the command below:

sudo Xorg -configure

Then make sure the file created is called xorg.conf and placed in the /etc/X11 directory.

You can then play with the settings there.

If you don't have a specific need for 9.10, you might want to look at Ubuntu 10.04 which I have running fine on a 9.10 host with the latest virtualbox 3.1.6 and those tools installed.

hth

Nick

---

### Post by fallenshadow on 2010-03-31
Here is the Xorg conf it created but I have tried messing with this already and it temporarily broke my installation.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

So how would I go about getting a 1024x678 resolution? Without breaking my install. :D

---

### Post by JustinR on 2010-03-31
Hi,

I've had problems with VirtualBox 3.1.6 and Guest additions for the display resolution in Ubuntu 9.10.

If you haven't already, try reinstalling it.
If that doesn't work, when Ubuntu loads the desktop, while VirtualBox is window-ed (not fullscreen), click Machine > Auto-resize guest display
then click Machine > Fullscreen and it should resize correctly.

---

### Post by codfather on 2010-04-01
Have you tried re-sizing the screen that the VM displays in with your mouse, as this should automatically change the screen resolution, and that works perfectly on my 9.10 host laptop with lucid 10.04 beta 1.

What do you get if you type this into a console?

/etc/init.d/vboxadd status

Nick

---

### Post by fallenshadow on 2010-04-01
The option to "Auto resize guest" is greyed out so I can't click it.

I have tried reinstalling Virtualbox and Ubuntu 9.10 in the virt machine but neither works. I guess its a problem with Virtualbox and 8.10 (my host OS).

--
Tried resizing with mouse... no effect on it.

Here is output of that command: "The VirtualBox Additions are currently running."

---

### Post by codfather on 2010-04-01
Well there are two versions of virtual box. Their is the OSE version which is completely open source, and the version from the Sun/Oracle website which contains certain proprietary drivers for things like USB devices etc.

Which version are you using? I'm using the full version from the Virtualbox site, and I just added the Ubuntu repository to my sources list using the info from that site.

Also, have you added yourself to the vboxusers group? As this will affect being able to use USB devices etc.

Nick

---

### Post by fallenshadow on 2010-04-01
I am using the version of virtualbox from the virtualbox website.

I am already added to vboxusers and USB devices work.

---

### Post by codfather on 2010-04-02
Ok, the log files for your virtualbox virtual machines are in your home directory under:

/home/your-username/.VirtualBox/Machines/virtual-machine-name/Logs

Issue the following command and post anything you find

grep -i error VBox.log

Nick

---

### Post by fallenshadow on 2010-04-02
Ok I found more than just one log file so I did:
```

grep -i error VBox.log
grep -i error VBox.log.1
grep -i error VBox.log.2
grep -i error VBox.log.3

```

Here was the output:
```
00:05:31.628 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:11:08.983 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.772 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.772 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.840 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.845 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.853 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.861 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.877 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.885 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.893 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.901 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.909 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.917 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.925 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.933 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.941 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.949 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false
00:02:56.992 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={7c0f2eae-f92d-498c-b802-e1a3763774dc} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false

```

All seems to do with the mouse I think. When I did it on just the VBox.log I got the same error message once.

---

### Post by Oscar3 on 2010-04-02
Hi all. I am newly on this forum and I stumbled upon your post.
I am running Ubuntu 9.1 under VirtualBox 3.1.6 under Windows 7.
I get the full resolution on Ubuntu. When I run it full screen on a 1920x1200 monitor it does great.
If I reduce it to any size window, the 'monitor size' from within Ubuntu always reflects whatever window I have given it.

What gyrations did I perform to accomplish this? ...(drum roll)...

None!

1. I installed Virtual Box
2. I installed Ubuntu from iso
3. I installed the extensions. 

Before I did the extensions I had 800x600. After that I had whatever window size I gave it.
So, just to let you know that it's possible and that it's not necessary to be mucking around with all those configuration files and stuff. ;)

---

### Post by fallenshadow on 2010-04-03
Yeah I do agree with you Oscar3, I shouldn't have to mess with anything to get it working. With Windows in Virtualbox it works fine at full resolution.

At this stage I think its just something to do with Ubuntu 8.10 because newer Ubuntu releases seem to have no problem going full screen in virtualbox.

Anyway I will mark this thread as solved because when I install 10.04 this problem should be solved... I hope. :D

---

### Post by fallenshadow on 2010-04-24
I know this is mark as solved but its only now that its really solved.

I installed 10.04RC in my virtual machine... installed additions and now I have 10.04 at fullscreen resolution with Compiz working too! :)

I still have 8.10 on the desktop so it wasnt a problem with the host OS. Guess it was just a problem with 9.10...

---

### Post by TheFu on 2010-04-25
I think there's a big difference in controlling the resolution when Linux with X/Windows is the host and when Windows-whatever is the host OS.

BTW, on Windows, if you don't use the OSE, the latest versions are in the 3.1.6 range and offer many, many improvements (performance AND video) over 1.x and 2.x releases.

---

### Post by meenal on 2010-12-14
Thanks.it really helps me :-)

---

