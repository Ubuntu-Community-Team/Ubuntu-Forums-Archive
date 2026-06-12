---
title: "Desktop icons now enormous"
date: 2015-12-06
forum: Ubuntu Development Version
---

### Post by ubername on 2015-12-06
Hi
Just downloaded today's 16.04 updates and now all my desktop icons are twice (or so) normal size. I can resize them to a bit smaller, but is their an easy way to do this for all of them, rather than one at a time?

---

### Post by tista on 2015-12-06
@ubername,

Please check your gsettings via:
```
gsettings get org.gnome.desktop.interface scaling-factor
```
If it answered **uint32 0** (auto-scaling mode), just try to set it as **uint32 1** (native screen resolution):
```
gsettings set org.gnome.desktop.interface scaling-factor 'uint32 1'
```

Regards,
Tista

---

### Post by mc4man on 2015-12-06
By default scaling-factor should be uint32 1
gnome has decided nautilus should only get 3 options for icon size - small, standard, large. small is still slightly larger than the previous default of 100% so that's likely your best choice.
```
gsettings set org.gnome.nautilus.icon-view default-zoom-level 'small'
```

If you don't like that there's nothing less than small then file a bug specific to that in upstream gnome, this one is just on that there is no user visible means to adjust
(though if Ubuntu keeps this unfortunate nautilus-3.18 in 16.04 then they should default to small rather than standard
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1523015](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1523015)

---

### Post by MikeMecanic on 2015-12-07
> **ubername said:**
> Hi
Just downloaded today's 16.04 updates and now all my desktop icons are twice (or so) normal size. I can resize them to a bit smaller, but is their an easy way to do this for all of them, rather than one at a time?

Mine were ten times larger (in desktop) when I upgrade to Kernel 4.3.  Now they remain twice bigger then they should be.  In Nautilus there OK now. Because I like them small, I open a bug report there:
```
xenial3@hp:~$ apt-cache policy unity
unity:
  Installed: 7.4.0+16.04.20151102-0ubuntu2
  Candidate: 7.4.0+16.04.20151102-0ubuntu2
  Version table:
 *** 7.4.0+16.04.20151102-0ubuntu2 500
        500 http://mirror.clibre.uqam.ca/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
xenial3@hp:~$ 

```[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1523387](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1523387)

---

### Post by ventrical on 2015-12-07
unity is working just awesomely here of both Intel and nVidia graphics.

There seems to be a new feature with 'enable workspaces'. There is now a definitive graphical divider between the workspaces which gives it a sort of three dimensional crispness to it.

Regards..

---

### Post by MikeMecanic on 2015-12-07
Have a second bug: Not able to create a new document .txt file.  The pop-up won't show up (under the main one) when I right click on the desktop.  Plus it seems to contain no information.  Plus its too large.  Not able to do a screenshot.

---

### Post by ventrical on 2015-12-07
> **MikeMecanic said:**
> Have a second bug: Not able to create a new document .txt file.  The pop-up won't show up (under the main one) when I right click on the desktop.  Plus it seems to contain no information.  Plus its too large.  Not able to do a screenshot.

Looks as if you are missing some parts here.

1. Could you please try:

```

sudo -i dpkg --configure -a

```

and could you send up results from running inxi (if you can) . What is your graphics adapter?

Regards..

---

### Post by grahammechanical on 2015-12-07
Finally found the slider in Nautilus 3.18.2 that adjusts the size of the icons in Nautilus & on the desktop. Yes, it could do with reducing them further. 

Right click desktop New Document and Empty Document slides out on the right or the left depending on how close the dialog is to the screen edge. At least it does here.

Perhaps, this thread should be retitled Nautilus 3.18.

Regards.

---

### Post by QDR06VV9 on 2015-12-07
> **grahammechanical said:**
> Finally found the slider in Nautilus 3.18.2 that adjusts the size of the icons in Nautilus & on the desktop. Yes, it could do with reducing them further. 

Right click desktop New Document and Empty Document slides out on the right or the left depending on how close the dialog is to the screen edge. At least it does here.

**Perhaps, this thread should be retitled Nautilus 3.18.**

Regards.
+1

---

### Post by MikeMecanic on 2015-12-07
> **ventrical said:**
> Looks as if you are missing some parts here.

1. Could you please try:
```

sudo -i dpkg --configure -a

```
and could you send up results from running inxi (if you can) . What is your graphics adapter?
Regards..

The command line didn't do much.  Here's the info:
```
xenial3@hp:~$ sudo -i dpkg --configure -a
[sudo] password for xenial3: 
xenial3@hp:~$ inxi
CPU~Dual core Intel Core i3-2100 (-HT-MCP-) speed/max~1642/3100 MHz Kernel~4.4.0-040400rc4-generic x86_64 Up~1:41 Mem~1118.9/3862.4MB HDD~750.2GB(1.5% used) Procs~228 Client~Shell inxi~2.2.28  
xenial3@hp:~$   inxi [-AbCdDfFGhHiIlmMnNopPrRsSuw] [-c NUMBER] [-v NUMBER]
CPU~Dual core Intel Core i3-2100 (-HT-MCP-) speed/max~1599/3100 MHz Kernel~4.4.0-040400rc4-generic x86_64 Up~1:56 Mem~1229.6/3862.4MB HDD~750.2GB(1.5% used) Procs~230 Client~Shell inxi~2.2.28  
xenial3@hp:~$  inxi  [-t (c or m or cm or mc NUMBER)] [-x -OPTION(s)] [-xx -OPTION(s)]
bash: syntax error near unexpected token `('
xenial3@hp:~$        [-xxx -OPTION(s)]
bash: syntax error near unexpected token `('
xenial3@hp:~$  inxi [--help] [--recommends] [--version] [-@ NUMBER]
CPU~Dual core Intel Core i3-2100 (-HT-MCP-) speed/max~1643/3100 MHz Kernel~4.4.0-040400rc4-generic x86_64 Up~1:57 Mem~1231.6/3862.4MB HDD~750.2GB(1.5% used) Procs~229 Client~Shell inxi~2.2.28  
xenial3@hp:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


```

Nautilus is fully back to normal./ Intel Sandy Bridge

---

### Post by MikeMecanic on 2015-12-07
This one gives a better picture:

```
xenial3@hp:~$ inxi -b
System:    Host: hp Kernel: 4.4.0-040400rc4-generic x86_64 (64 bit)
           Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: 610-1130f
           Mobo: Quanta model: 2ABB v: 101
           Bios: AMI v: ING_715 date: 03/01/2012
CPU:       Dual core Intel Core i3-2100 (-HT-MCP-) speed/max: 1599/3100 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel Sandybridge Desktop
           GLX Version: 3.0 Mesa 11.0.6
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 750.2GB (1.5% used)
Info:      Processes: 229 Uptime: 2:12 Memory: 1176.1/3862.4MB
           Client: Shell (bash) inxi: 2.2.28 
xenial3@hp:~$exit
```
BIOS is up to date

---

### Post by ventrical on 2015-12-07
Does it help if you roll back to a previous kernel?

Edit:Oh .. look slike it is fixed.

---

### Post by mc4man on 2015-12-07
> **ventrical said:**
> Does it help if you roll back to a previous kernel?

Edit:Oh .. look slike it is fixed.

Nohing to do with the kernel & certainly not fixed. The current sizes in px, default is Standard- 
#define NAUTILUS_CANVAS_ICON_SIZE_SMALL 64
#define NAUTILUS_CANVAS_ICON_SIZE_STANDARD 96
#define NAUTILUS_CANVAS_ICON_SIZE_LARGE 128

Launchpad bug - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316)
upstream nonsense report, if one wastes some time reading it appears gnome devs are clueless to actual desktop use. - [https://bugzilla.gnome.org/show_bug.cgi?id=748441](https://bugzilla.gnome.org/show_bug.cgi?id=748441)

---

### Post by ventrical on 2015-12-07
I see how they re-engineered it. At least it is ok with those who need assistive tech help at this stage of the game. Ok.. in the larger sense, across the board ... you're right . It still needs fixing.

Regards..

---

