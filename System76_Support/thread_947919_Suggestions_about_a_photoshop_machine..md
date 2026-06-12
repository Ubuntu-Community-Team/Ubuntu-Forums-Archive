---
title: "Suggestions about a photoshop machine."
date: 2008-10-14
forum: System76 Support
---

### Post by jeamer on 2008-10-14
Hi, I have a PanV3 and love it. My wife also likes it, and now wants a new machine, as hers was a total ripoff, feels like it is made of raw iron, and is slower than an Amiga. She is a photographer (or "Digital Artist" as she likes to say) and intensely uses Photoshop. She is willing to buy a linux machine, and I better get this right or we've lost her forever! She has only ever used ubuntu on my computer to do basic things like check email etc.

Here's the questions. 

First, what do you suggest in terms of running Photoshop EASILY (stress EASILY) on a ubuntu machine? My three options are Wine, VMware (I have access to an XP disc) or dual boot. Dual boot would not be super ideal, as she would probably not be motivated to use ubuntu and it's secure ways if she had to boot out every time she wanted to use photoshop.

Second, what do I need to look at in terms of budget? Looking at ~1000 -1200 dollar piece of equipment, and everything I read is different. Optimizing photoshop apparently requires a good CPU to someone, lots of RAM to another, and a great graphics card to someone else, or a mixture of all three??!?!? (Sorting though all the &$*&^# people that recommend macs was difficult too).

Ideally looking at an upgraded PanP1, but anyone out there running photoshop on a linux machine want to tell me about it? (Even not a sys76? Also looking at a Dell XPS)

Thanks!


EDIT: BTW hers is an ACER... and I don't hesitate to call it a piece.

---

### Post by thomasaaron on 2008-10-15
I'd get her a Pangolin or a Serval, bump the RAM to a minimum of 2GB (4GB would be better), and bump up the CPU a little.

Then, if all she needs from Windows if Photoshop, I'd use VMware to virtualize XP and just install Photoshop on the VM.

That's what our webmaster does, and it works perfectly.

Just out of curiosity, has she tried the GIMP? My understanding is that it is getting pretty good for anything but the most demanding professional usage.

---

### Post by glacialfury on 2008-10-15
I wouldn't encourage her to use GIMP on a professional basis if she's accustomed to Photoshop; she could start learning it as a hobby, but to jump from one to the other is pretty jarring.  I made that same switch, but it wasn't painless, and to this day I recognize the GIMP as an outstanding program, but Photoshop as a clear superior.

Second of all, as much as I love linux, I don't do so in an evangelical way, and while I prefer opensource, I don't mind commercial software either.  If she is accustomed to Windows and Photoshop, has no problems with that setup and is willing to pay for the software, the best solution might be to let her stay on Windows and use Photoshop.  It sounds like you want her to use Ubuntu/Linux for *your* values, not hers; if she's only using Linux as a shell to boot Windows in VMware, what's the point of even running Linux to begin with? (again, from her perspective - not yours)

Each operating system - even Windows - has its own place, and Linux, just like Windows and any other OS, is not the perfect solution for everyone.  I use Ubuntu now and my wife uses Windows; although I've gotten her to the point where she doesn't revile Linux, *I recognize that she doesn't gain anything by switching.*  I gained the joy of experimenting with a new system and learning new things about computers, and the satisfaction of using opensource software; she doesn't care about any of these things, and thus an OS switch does nothing for her but irritate her.

Linux has a somewhat evangelical community; I would argue that people ought to come to Linux out of curiosity, not be "converted."  So from what you've laid out, I'd say follow the technical suggestions of T.Aaron regarding RAM/processor etc, but stick with Windows.  

Caveats: 
 - VMWare does not use the hardware aspects of your graphics card; so any aspect of photoshop that uses a graphics card will be done by "faking" it on your RAM.
 - You are correct in the dual-boot; there is no incentive to boot the other when you can do everything you want with one OS.
 - Compiz/Fusion can interfere with Photoshop under wine; it will intercept important keyboard shortcuts intended for Photoshop, meaning you'd have to disable all those keystrokes in compiz or shut it down.
 - you *can* get photoshop working reasonably well in wine, at least versions 5 through CS2.  Check the wiki here: [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by jeamer on 2008-10-15
Hey, thanks for the comments.

1. She has used GIMP and is quite familiar with it. Unfortunately, at the level she's at, GIMP is not sufficient. The quality of the final product just can't be at the level she can attain with PS, and it doesn't have anything to do with her knowledge of the program, it is regrettably the program itself. 

2. She wants Linux. I really didn't have to push her in any direction. She's always had windows machines from 98 thru XP and is tired of the 2 year performance shelf life of those distributions. We both find it near impossible to keep a Windows distribution free of crap and protected from more crap without buying expensive Norton software.

Having said that, running XP thru VMWare: will I still need a firewall and A-virus (in the virtual windows)? My understanding is that the machine will still be protected by linux security, but I need to be sure.

---

### Post by thomasaaron on 2008-10-15
Well, if your using the Internet from within the Windows VM, yes. It definitely can catch a virus. It is just as susceptible as installing on hardware.

The beauty of a VM, though, is that you can just minimize the windows vm and do your internet browsing / email from Ubuntu.

---

### Post by wrender on 2008-10-15
In all honesty, professionally gimp does not cut it. Not even close. If she is doing professional work she needs photoshop.

It all comes down to how hard she is going to push photoshop. What is the resolution and the bit depth of the images she is working with?

Cheers, Wren




ps. I have run CS2 under wine with suse 11 and it works pretty good.

---

### Post by glacialfury on 2008-10-16
The way I understand the VMware setup is this:

Yes, you can catch a virus etc on the "virtual" Windows; remember, it's really REALLY Windows, just in a virtual container.  So, anything you can do on regular windows, you can do in the virtual windows.

That being said, the Windows VM is insulated from the Linux host for the most part, so if you do catch a virus, it generally won't cross over.

THAT said, there's no reason not to have a virus scanner on any windows installation, virtual or not - there are plenty of good free ones and they don't interfere significantly in terms of resources.  Install the virus scanner, photoshop, and that's it.

Does anyone else know how much Photoshop uses the actual graphics card for processing?  Because I know that wouldn't work in VM. (You would not want to run a 3D renderer like 3DS Max in VMWare)

---

### Post by wrender on 2008-10-16
CS2 does not use it as far as I know.
CS3 there is an option to enable the 3d acceleration.
CS4 Its probably a requirement.

---

### Post by jeamer on 2008-10-16
So you could set up no network connection capabilities in windows and not worry about viruses. I don't see why you would need it; any downloads (win/PS updates) could be done in Ubuntu and transferred.

Also, if I maxed out the ram (4GB) would I have to worry about no usage of the graphics card if it has ample ram to "fake it" with?

---

### Post by thomasaaron on 2008-10-16
When you set up a VM, you allocate a certain portion of your RAM to it. So, if you had 4GB, it would allow you to allocate more than if you only had 2GB. 

If you are not getting on the Internet with your Windows VM, I don't think you'd really have to worry about viruses. Also, you can shut down the networking bridge between Ubuntu and Windows.

As for running updates, it's somewhat unlikely that this would pose much of a risk.

---

### Post by jeamer on 2008-10-16
Hey, so I thought that if I'm hijacking my own thread then it's not offending anyone :-D

So I'm now trying to get VMware on my Pangolin to try everything out before I commit to more pangolin-ness. Trouble, however, when I try to get it from the repos:

```
After this operation, 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 208047 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So my understanding is that I can't overwrite svg_loader.so because its in another package and probably has dependencies. Any idea what to do? Do I need ia32-libs? What are they for? What is error code (1)? What is the meaning of life? :)

I am using 64bit Ubuntu.

---

### Post by thomasaaron on 2008-10-17
It looks like you didn't do a *complete* uninstall of the old vmware server. See if it is still listed as installed in Synaptic Package Manager, and if it is right-click it and select "Completely Remove."

If not, try removing that package manually. Your new install should replace it.

So...

```
sudo rm /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so
```

You're probably going to run into other modules that weren't completely removed too, like vmnet and vmmon. You'll probably have to use the same technique on them.

---

### Post by jeamer on 2008-10-17
Hey tried this and several other things from the virtualization ubuntu forums, couldn't get a result. Went the way of virtualbox, and had no problems! Anyways, shall see how seamless WinXP in vbox can be and the results will be shown in the possible future purchase of a new pangolin.

---

### Post by glacialfury on 2008-10-17
Sounds good, but double-check first - don't you need the 64bit version of windows to handle more than 2gb ram?  I remember that being a limitation some years ago, not sure if it's still true today.  I remember building a system once with 4gb ram, and it only recognized 2gb due to it being 32 bit OS.

---

### Post by jeamer on 2008-10-18
I think you're right, you need a 64 bit OS to use more than 2 GB of RAM. However windows wouldn't be the host, and I wouldn't allocate more than 2 GB into vbox simply for photoshop to work. All the virtual machine would be for is running photoshop, everything else would be done in 64 bit Ubuntu.

---

### Post by theTOman on 2008-10-25
Running XP in VirtualBox, with the Guest Additions, is the nicest thing ever on a System76 laptop!
If you have enough memory, Photoshop should not be a problem at all!

---

