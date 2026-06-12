---
title: "Can't add new resolution in Xubuntu VM using xrandr, failed to get gamma?"
date: 2016-07-29
forum: Virtualisation
---

### Post by XOIIO on 2016-07-29
Hello all so I have several Xubuntu VM's running, hosted on a server 2012 r2 machine.

I recently added a basic graphics card to improve their graphics performance, with a much better one to be installed once a PCI extension cable and power cables for my server come in.  The problem is, as soon as I enabled the passthrough of the graphics card, the resolution dropped to 800x600, and I can't change it at all. That's the only option, and whenever I try to add a resolution (I'm wanting 1024 x 768, or 1280x800, maybe both), or try to get the display info xrandr gives me the error "failed to get size of gamma for output default"

I'm assuming this is because it doesn't have a real display, so how can I go about fixing this?

---

### Post by Bucky Ball on 2016-07-29
It would help if you let us know what graphics card you are trying to get working. Do you have a third-party driver installed for it or are you using the open-source Nouveau driver or something else?

---

### Post by XOIIO on 2016-07-29
> **Bucky Ball said:**
> It would help if you let us know what graphics card you are trying to get working. Do you have a third-party driver installed for it or are you using the open-source Nouveau driver or something else?

It's just a basic xubuntu install, same issue with my regular ubuntu vm though.

Right now it's a radeon 5450, but I'll be putting a gtx 660 oc in later.

I guess perhaps it's detected the card and sort of gone back to it's default resolution? Haven't messed with linux enough to swap/add graphics cards before, so maybe it just doesn't know what to do with this one? It is odd though as it had a pretty high resolution (1600x something) on the integrated graphics on my server which are pretty **** poor.

---

### Post by Bucky Ball on 2016-07-29
* I thought of this after I'd written everything else, so you should do this first if you haven't already. It dawned on me that the odd thing is, as you are running in Virtualbox, you shouldn't need to install drivers. Should be using the host's. Do you have [Virtualbox Guest Additions]("https://www.virtualbox.org/manual/ch04.html") installed? If not, install it. That should fix things immediately.

It's in one of the drop-down Virtualbox menus on the host side, Devices from memory. The last selection is 'Insert Guest Additions image' or something like that. The method of getting the guest additions varies with OS/flavour. I think all the *buntus are the same, but you might check ...
___

Otherwise:

Check for the Radeon driver in Synaptics. Check on the other machine to see if that is installed and being used. (You can have a look in the terminal with 'sudo lshw -C video' and in the output you will find the card and the driver somewhere).

In Synaptics there is a bunch of xserver-xorg-video-radeon drivers. One of them might be right for you. I do know that some Radeon cards are no longer supported in more modern releases of Ubuntu. You will need to do a bit more research on that.

Xubuntu is not Ubuntu, even though it's based on it, and doesn't install everything Ubuntu does by default. That could be your issue here. I personally use nothing but Xubuntu (well, Xubuntu-core actually). Love it. ;)

* Just remembered. My laptop uses a Radeon card. Here's the output, see details in bold:

```
*-display               
       description: VGA compatible controller
       product: RV710/M92 [**Mobility Radeon HD 4530/4570/545v**]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **driver=radeon** latency=0
       resources: irq:27 memory:c0000000-cfffffff ioport:4000(size=256) memory:d6000000-d600ffff memory:d6020000-d603ffff
```

Checking in Synaptics, I have xserver-xorg-video-radeon installed. I am running Xubuntu-core 16.04 LTS.

---

### Post by XOIIO on 2016-07-29
I'm actually running in Hyper-v, not virtualbox.

As I mentioned I have a couple full ubuntu vm installs, and they have the same issues. I might try doing a fresh install. It would suck to have to do this several times, so I might just wait till I have the good video card in to save some hassle, if it works once time.

---

### Post by MAFoElffen on 2016-07-30
To the OP:


Hyper-V does not do hardware GPU pass-through... like VSphere, KVM or Xen. But if your host is Windows version 8.1 or newer, then after you get to the guest console window, in it's menu select View > Enhanced Session...


In Hyper-V enhanced session mode will give enhanced support for display configuration, audio redirection, printer redirection, full clipboard support (improved over limited prior-generation clipboard support... meaning you can cut-and-paste between the host and guest), smart card support, USB Device redirection, drive redirection, redirection for supported Plug and Play devices, etc.


So, for you, turn on enhanced session mode support, and you should be able set your resolution to something higher.

---

### Post by XOIIO on 2016-07-31
> **MAFoElffen said:**
> To the OP:


Hyper-V does not do hardware GPU pass-through... like VSphere, KVM or Xen. But if your host is Windows version 8.1 or newer, then after you get to the guest console window, in it's menu select View > Enhanced Session...


In Hyper-V enhanced session mode will give enhanced support for display configuration, audio redirection, printer redirection, full clipboard support (improved over limited prior-generation clipboard support... meaning you can cut-and-paste between the host and guest), smart card support, USB Device redirection, drive redirection, redirection for supported Plug and Play devices, etc.


So, for you, turn on enhanced session mode support, and you should be able set your resolution to something higher.

My host is Server 2012 R2, and I'm passing through the GPU with the  RemoteFX GPU adapter. It won't let me enable the enhanced session,  probably because it's a type 1 virtual machine.

Currently reinstalling one of my vm's, and the installer at least started at a much higher resolution, we'll see if it sticks.

It just seems that it can't really handle the sudden change in graphics adapter "hardware", and since it's not real hardware I can't use the ubuntu command line stuff to update all drivers, so I'll just wait for parts I need, slap the good video card in, and then redo the machines.

---

### Post by MAFoElffen on 2016-07-31
> **XOIIO said:**
> [COLOR=#b22222]Currently reinstalling[/COLOR] one of my vm's, and the installer at least started at a much higher resolution, we'll see if it sticks.

It just seems that it can't really handle the sudden change in graphics adapter "hardware", and since it's not real hardware I can't use the ubuntu command line stuff to update all drivers, so I'll just wait for parts I need, slap the good video card in, and then redo the machines.
As, in... as a Gen-2 hyper-v guest?

A couple things I do... and it does involve some commandline:

At the grub2 menu, press <C>, which will drop you into a grub command prompt...
```

vbeinfo

```
That will show you the capabilities of the virtual display. Reboot into the system... After XServer starts, use 
```

xrandr -q
sudo lshw -numeric -class video 

```
to display the characteristics of the virtual display and virtual graphics adapter...

Even if a hypervisor or VM Guest OS does not support enhanced guest graphics, there are ways to get around those to a point. IOld school tip with Linux guests running under a hypervisor... and graphics.. Is that most all support VGA graphics. You can usually VGA resolutions up to 1024x768 or 1280x1027 with not much effort.

Even with a Windows Guest, you can manually add new modes... that would add better graphics, as long as the recognized virtual display can show it.

---

### Post by XOIIO on 2016-07-31
It's the same generation 1 guest, all my machines are gen 1 right now,  reinstalling to see if it would detect the new graphics adapter and then  work at higher resolution, which it is, going all the way up to  1152x864 which is a good size for what I need.

This is the output  on fresh install and the existing install on other machines reports the  same, so it is detecting everything properly from what I can tell, but  xubuntu itself is having an issue.
[img]http://i.imgur.com/2870D0W.jpg[/img]

Something  really strange I just noticed though, a couple of the VM's are also  running at the higher resolution now, without me having done anything,  and the others still running at 800x600 show that as the max resolution  with xrandr. lshw shows the same output on both machines.

Ahh, maybe I can change it in grub itself, I found this that seems like I might be able to do it manually. [http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

---

### Post by XOIIO on 2016-07-31
Nope, that didn't do the trick sadly. Another machine just switched to the higher resolution randomly too, and I have no clue why.

---

### Post by MAFoElffen on 2016-08-01
So how are you trying to change it via xrandr?

Steps are:
- Define the mode in memory
- Add the mode to a port
- Set a port to that mode
Then add add to the .profile script to set it each time it boots and logs a user... like this
```

xrandr --newmode Modeline "1280x1024" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
xrandr --addmode VGA-0 1280x1024
xrandr --output VGA-0 --mode 1280x1024 -rate 60

```
Much easier to do via an /etc/X11/xorg.conf file:
```

## xorg.conf file for a VM Guest
# By MAFoElffen, 2016.07.31
* Tailored for the Resolutions seen by XOIIO

Section "ServerLayout"
  Identifier "Layout0"
  Screen 0 "Screen0" 0 0
EndSection


Section "Device"
  Identifier "Device0"
  VendorName "Virtual Vesa Device"
  BoardName "Configure Vesa Driver"
  Driver "vesa"
  Option "IgnoreEDID" "True"
EndSection


Section "Monitor"
  Identifier      "Monitor0"
  VendorName      "Configured Display"
  ModelName       "Virtual Display"
  Horizsync 30.0-82.0  Vertrefresh 50.0-75.0
  Modeline "1600x1200_60.00" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -HSync +Vsync
  Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
  Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
  Modeline "800x600_60.00" 38.22 800 832 912 1024 600 601 604 622 -HSync +Vsync
  Option "PreferredMode" "1280x1024_60.00"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device     "Device0"
  Monitor    "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Viewport  0 0
    Depth     24
    Modes "1600x1200_60.00"  "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
  EndSubSection
EndSection

```

---

### Post by XOIIO on 2016-08-02
First thing I found before posting here was those steps that you gave, and that gives me the "failed to get gamma" error which is why I posted, because I can't even find out what that means from my searching.

I also don't have the xorg config file in that directory, and I looked around some more and the only xconf files I could find didn't look anything like that. I'm not sure if it's because this is xubuntu or what but all the results I found that are supposed to work don't.

---

### Post by MAFoElffen on 2016-08-02
There is a intermittent challenge with Xrabdr sometimes when it can't read the returned output of the display, to see if it took the mode... To get around that, on the output command, append a gamma option:
```

xrandr --output VGA-0 --mode 1280x1024 -rate 60 --gamma 1:1:1

```
On not finding an /etc/X11/Xorg file... yes, if you have not installed a video driver or even if you have, if there is no xorg.conf file, then XServer uses the default files from /etc/X11/xorg.d/... but it looks for the present of one first. If present, then it uses that as the preferences. (So uses as an override, or as user preferences.

---

