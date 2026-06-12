---
title: "Artful has no login option for wayland"
date: 2017-05-31
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-05-31
Has anyone else seen **no option** for a wayland session on fresh install instead of upgrading from a 17.04 install?
To be clear>>>I have no Option for a Wayland session when logging in.
Options shown are: Gnome && Gnome classic>>>Only.
"Ubuntu-GNOME 17.10 "Artful Aardvark" - Alpha amd64 **(20170530)**"
Am I missing something here?
```
apt policy gnome-session-wayland
gnome-session-wayland:
  Installed: 3.24.1-0ubuntu2
  Candidate: 3.24.1-0ubuntu2
  Version table:
 *** 3.24.1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu artful/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu artful/universe i386 Packages
        100 /var/lib/dpkg/status


```

---

### Post by deadflowr on 2017-05-31
i've only ever seen an option for wayland if I switch from lightdm to gdm3.
Not sure if I've ever seen an option for it with lightdm.
fwiw

---

### Post by mc4man on 2017-05-31
If you have nvidia drivers installed then you'd lose wayland option.

---

### Post by #&amp;thj^% on 2017-05-31
> **deadflowr said:**
> i've only ever seen an option for wayland if I switch from lightdm to gdm3.
Not sure if I've ever seen an option for it with lightdm.
fwiw
Pure Ubuntu Gnome install no lightdm here. :)
```
apt policy lightdm
lightdm:
  Installed: (none)
  Candidate: 1.22.0-0ubuntu2
  Version table:
     1.22.0-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages


```

> **mc4man said:**
> If you have nvidia drivers installed then you'd lose wayland option.
No nvidia till just now.
I'll just chalk this this up to a bad iso download
```
cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu Artful Aardvark (development branch)"
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Artful Aardvark (development branch)"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful


```
Thats ok X11 is better anyway...thought they wanted it tested, but??? I can't test if it's not available. :D
X11 all the way Baby... i will miss it.;)
EDIT: Just to show nvidia works with:
```
uname -r
4.12.0-041200rc3-lowlatency

```

---

### Post by #&amp;thj^% on 2017-05-31
OMG!! this is way funny...after installing the nvidia driver, I now have the wayland Option.:lolflag:
```
$ echo $DESKTOP_SESSION
gnome-wayland

```
Used the Prime option for Intel, And Rebooted.
Whatever...all's well that ends well Right?;)
Edit: When I installed the system I had the Nvidia card disabled via Bios.

---

### Post by ventrical on 2017-06-02
> **deadflowr said:**
> i've only ever seen an option for wayland if I switch from lightdm to gdm3.
Not sure if I've ever seen an option for it with lightdm.
fwiw

I upgraded and older system. Just updated. I have wayland option in lightdm but only get blackspace when I try to log on. But I'm off topic already :)

Regards..

---

### Post by rrnbtter on 2017-06-06
Greetings,
Gnome-Wayland login working with this mornings updates.  I am using the 4.12.0-041200rc4 kernel. Could not take a screen shot because of Unity/Gnome software conflict.  Updated with proposed enabled. There are problems but at least it is in the works.

rrnbtter@rrnbtter-110-15ISK:~$ apt policy gnome-session-wayland
gnome-session-wayland:
  Installed: (none)
  Candidate: 3.24.1-0ubuntu2
  Version table:
     3.24.1-0ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe i386 Packages

inxi -Sxx && $DESKTOP_SESSION
System:    Host: rrnbtter-110-15ISK Kernel: 4.12.0-041200rc4-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu1) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
gnome-wayland
rrnbtter@rrnbtter-110-15ISK:~$

---

### Post by rrnbtter on 2017-06-06
Greetings,
Everything working fine now with the Gnome Shell Login.  I switched back to the 4.11 kernel. It seems that my RTL wifi drivers wasn't loaded with the 4.12 kernel and my wifi was dropping. A few more updates and all is well with the Unity/Gnome Wayland/Gnome login.

---

### Post by rrnbtter on 2017-06-07
Greetings,
Based on this morning's updates it appears that Wayland is gearing up and Mir is gearing out.

Edit: Just updated again and its back! .... Mir.

As my uncle Germano said " The moment you think you're out they pull you back in!

---

### Post by rrnbtter on 2017-06-07
Greetings,
Looks like GDM is in and Lightdm plus the Unity Greeteris out.  With that going on I wonder why they are putting up the Mir updates.

---

### Post by ventrical on 2017-06-08
Seems wayland has a little more snap to it.

```

ventrical@ventrical-System-Product-Name:~$ inxi -Sxx && $DESKTOP_SESSION
System:    Host: ventrical-System-Product-Name Kernel: 4.10.0-22-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2) dm: gdm3
           Distro: Ubuntu Artful Aardvark (development branch)
gnome-wayland: command not found
ventrical@ventrical-System-Product-Name:~$ 

```

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.10.0-22-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 driver: N/A
           Resolution: 1440x900@59.75hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 17.1.0 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.10.0-22-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (0.5% used)
           ID-1: /dev/sda model: WDC_WD15EURS size: 1500.3GB
Partition: ID-1: / size: 1.1T used: 6.8G (1%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.5C mobo: 35.0C gpu: 35.0
           Fan Speeds (in rpm): cpu: 4218 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 226 Uptime: 7 min Memory: 1189.1/3005.7MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.8 

```

---

### Post by rrnbtter on 2017-06-08
Greetings,
@Ventrical:  I don't see anything in your data the implies you are using Wayland.  However, I agree that the Gnome Desktop has more snap than Unity, at least on my machine. I can see that you are using the gdm whereas I am still using lightdm but my results still supports the extra performance of the Gnome desktop.

With the exception of my first year on linux, Unity is the only desktop I have used until now (excepting my Puppy Linux).  I was not a fan of the gnome menu driven desktop.  But I'm not disappointed at all with this new direction we seem to be taking. If Gnome adapts a few of the advantages of Unity I don't see why the switch will be that much of a deal. I haven't had Unity back up in three days, and we aren't even where we are going yet with Gnome.

rrnbtter@rrnbtter-110-15ISK:~$ inxi1
inxi -Sxx && $DESKTOP_SESSION
System:    Host: rrnbtter-110-15ISK Kernel: 4.11.0-5-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
gnome-wayland

rrnbtter@rrnbtter-110-15ISK:~$ inxi -Fxz
System:    Host: rrnbtter-110-15ISK Kernel: 4.11.0-5-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: laptop System: LENOVO product: 80UD v: Lenovo ideapad 110-15ISK
           Mobo: LENOVO model: Lenovo ideapad 1 v: SDK0J40700 WIN
           UEFI [Legacy]: LENOVO v: 1TCN19WW(V2.00) date: 08/09/2016
Battery    BAT1: charge: 29.5 Wh 94.1% condition: 31.4/32.0 Wh (98%)
           model: SIMPLO PABAS0241231 status: N/A
CPU:       Dual core Intel Core i3-6100U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9216
           clock speeds: max: 2300 MHz 1: 403 MHz 2: 408 MHz 3: 402 MHz
           4: 442 MHz
Graphics:  Card: Intel HD Graphics 520 bus-ID: 00:02.0
           Display Server: X.Org 1.19.3 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.80hz
           GLX Renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2)
           GLX Version: 3.0 Mesa 17.1.2 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.11.0-5-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 5000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Realtek RTL8821AE 802.11ac PCIe Wireless Network Adapter
           driver: rtl8821ae port: 4000 bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (18.8% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
           ID-2: /dev/mmcblk0 model: N/A size: 7.9GB
Partition: ID-1: / size: 15G used: 5.6G (41%) fs: ext4 dev: /dev/sda5
           ID-2: /home size: 896G used: 165G (20%) fs: ext4 dev: /dev/sda6
           ID-3: /boot size: 842M used: 68M (9%) fs: ext4 dev: /dev/sda3
           ID-4: swap-1 size: 5.24GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 221 Uptime: 8:48 Memory: 1405.2/3823.9MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.8 
rrnbtter@rrnbtter-110-15ISK:~$

---

### Post by ventrical on 2017-06-08
@rrnbtter

 I log on with wayland option. So it's buggy then ?

---

### Post by rrnbtter on 2017-06-08
Greetings,
@Ventrical:  Don't get me wrong, You and plenty of others on the forum know more about the workings of this than I do. But it is a forum and I'm just giving my opinion of your posted data, however I do agree with your result.  I wouldn't use the word buggy.  The "gnome wayland" login is just the name of the link that gets us to the Gnome Desktop of which wayland is a work in progress to come.  No doubt that we will get it and it will come through the updates and at that point we will just have it through no function or our own other than just to run the updates. However your and my posted data show that that we are running "X" and that you are using "gdm" and I am using "lightdm".  If you can get a positive result on "apt policy wayland", I would like to see it. I'm still getting a "no" at this point. 
I am finding some bugs with the Gnome display but nothing that would cause me to dislike it. Even Gnome as the primary Ubuntu display is a work in progress at this point. I'm just as eager to get this going as you seem to be but it will happen when it happens.

Referring back to my original sentence, if I wrong on this so be it. But in another thread you asked us to help with the testing of the Gnome desktop and thats what I'm doing, and posting my results. I hope you can respect that.

---

### Post by #&amp;thj^% on 2017-06-08
How to find if using wayland or x11
```
$ loginctl
   SESSION        UID USER             SEAT             TTY             
         4       1000 me               seat0            /dev/tty2       
        c3        120 gdm              seat0            /dev/tty1       

2 sessions listed.
```
```
me@me-750-417c:~$ loginctl show-session 4 -p Type
_**Type=x11**_
```

"loginctl show-session <YOUR_NUMBER> -p Type"
```
$ loginctl
   SESSION        UID USER             SEAT             TTY             
         2       1000 me               seat0            /dev/tty2       
        c1        120 gdm              seat0            /dev/tty1       

2 sessions listed.
```
```
me@me-750-417c:~$ loginctl show-session 2 -p Type
_**Type=wayland**_
me@me-750-417c:~$ echo $DESKTOP_SESSION
gnome-wayland

```
But I stll find it funny or odd that it did not show up until I installed the Nvidia Drivers

---

### Post by rrnbtter on 2017-06-08
Greetings,

Here's mine!

rrnbtter@rrnbtter-110-15ISK:~$ loginctl
   SESSION        UID USER             SEAT             TTY             
        c2       1000 rrnbtter         seat0                            


1 sessions listed.


rrnbtter@rrnbtter-110-15ISK:~$ loginctl show-session c2 -p Type
Type=wayland


rrnbtter@rrnbtter-110-15ISK:~$ echo $DESKTOP_SESSION
gnome-wayland


I'm on the way to work but I'll look into this more in the morning.  But thanks for the code.

---

### Post by #&amp;thj^% on 2017-06-08
Glad to help:)
Thanks for your contributions here also.

---

### Post by ventrical on 2017-06-08
> **rrnbtter said:**
> Greetings,
@Ventrical:  Don't get me wrong, You and plenty of others on the forum know more about the workings of this than I do. But it is a forum and I'm just giving my opinion of your posted data, however I do agree with your result.  I wouldn't use the word buggy.  The "gnome wayland" login is just the name of the link that gets us to the Gnome Desktop of which wayland is a work in progress to come.  No doubt that we will get it and it will come through the updates and at that point we will just have it through no function or our own other than just to run the updates. However your and my posted data show that that we are running "X" and that you are using "gdm" and I am using "lightdm".  If you can get a positive result on "apt policy wayland", I would like to see it. I'm still getting a "no" at this point. 
I am finding some bugs with the Gnome display but nothing that would cause me to dislike it. Even Gnome as the primary Ubuntu display is a work in progress at this point. I'm just as eager to get this going as you seem to be but it will happen when it happens.

Referring back to my original sentence, if I wrong on this so be it. But in another thread you asked us to help with the testing of the Gnome desktop and thats what I'm doing, and posting my results. I hope you can respect that.

I'm just asking.  Really .. some of it is really new news to me. I respect all the contributions you and others make , the good, the bad and the ugly.  Every little bit adds to the KB. In UDV I have developed a desktop blindness where all of us here , I pressume, are working forward  to try to find resolution for all the bugs on all the  different DEs and crossovers. Really . thank you for your original comment. And now as I see, 1fallen and provided us with further code to authenticate if wayland compositor is running. 

Regards..

---

### Post by ventrical on 2017-06-08
@1fallen

same here but not using nVidia drivers

```

ventrical@ventrical-System-Product-Name:~$ loginctl
   SESSION        UID USER             SEAT             TTY             
        c1        120 gdm              seat0            /dev/tty1       
         2       1000 ventrical        seat0            /dev/tty2       

2 sessions listed.
ventrical@ventrical-System-Product-Name:~$ loginctl show-session 2 -p Type
Type=wayland
ventrical@ventrical-System-Product-Name:~$ echo $DESKTOP_SESSION
gnome-wayland
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by #&amp;thj^% on 2017-06-08
> **ventrical said:**
> @1fallen

same here but not using nVidia drivers

```

ventrical@ventrical-System-Product-Name:~$ loginctl
   SESSION        UID USER             SEAT             TTY             
        c1        120 gdm              seat0            /dev/tty1       
         2       1000 ventrical        seat0            /dev/tty2       

2 sessions listed.
ventrical@ventrical-System-Product-Name:~$ loginctl show-session 2 -p Type
Type=wayland
ventrical@ventrical-System-Product-Name:~$ echo $DESKTOP_SESSION
gnome-wayland
ventrical@ventrical-System-Product-Name:~$ 

```
And a special **Thanks **to you for all your long hours and years and help here in U+1):P

Respectfully

---

### Post by ventrical on 2017-06-08
or..

```

ventrical@ventrical-System-Product-Name:~$ echo $XDG_SESSION_TYPE
wayland
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2017-06-08
I created a little test.

Install htop and you should see /xwayland running.

Highlight that line then kill it and press Enter.

Screen should go blank and bring you back to gdm.

Regards..

---

### Post by #&amp;thj^% on 2017-06-08
> **ventrical said:**
> I created a little test.

Install htop and you should see /xwayland running.

Highlight that line then kill it and press Enter.

Screen should go blank and bring you back to gdm.

Regards..

Yep! here as well.
I also see it in my conky. (xwayland)

---

### Post by ventrical on 2017-06-08
> **1fallen said:**
> Yep! here as well.
I also see it in my conky. (xwayland)

Hey ... thanks for testing that 1fallen. It's kinda goofy but it's fun too:) Gives some insight into it.  I'm kinda of surprised how easy it was to terminate. Wonder if a code could inadvertently do that from non root.

Regards..

edit: I mean I wonder if it could be a security issue. Reading up on it - wayland is suppossed to  be like a container that provides security for apps to run on.

---

### Post by #&amp;thj^% on 2017-06-08
> **ventrical said:**
> Hey ... thanks for testing that 1fallen. It's kinda goofy but it's fun too:) Gives some insight into it.  I'm kinda of surprised how easy it was to terminate. Wonder if a code could inadvertently do that from non root.

Regards..

edit: I mean I wonder if it could be a security issue. Reading up on it - wayland is suppossed to  be like a container that provides security for apps to run on.

Thought this was fun.
[GNOME 3.24] Flatpak Firefox running native on Wayland with NVIDIA \o/
[https://www.youtube.com/watch?v=XEJY3BeSt48](https://www.youtube.com/watch?v=XEJY3BeSt48)

This was very interesting to say the least.
Flatpak vs Snap - Which format is "Better"?
[https://www.youtube.com/watch?v=ixWuE1hhZfw](https://www.youtube.com/watch?v=ixWuE1hhZfw)
Explore differences between Flatpaks and Snaps and decide for yourself which format is better!

---

