---
title: "please test this app"
date: 2017-07-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-07-26
@all,

```

sudo apt-get install vokoscreen

```

Could some of you try to install this app on gnome-shell or gnome-wayland and see if it works for you. I have it only partially working. The app will come up and appear to work but it will not render a recording of the needed video file , yet, it works on xubuntu and unity-session just fine.

Regards..

---

### Post by DogMatix on 2017-07-26
I am having a similar experience to the one you describe. It seems to install and open fine. I recorded a 20s full screen video but then clicking play nothing happened. Eventually I got an 'Application not responding' dialogue and then it crashed. There is a mkv file in my home/videos directory but it was only 15KB in size and will not open.

Ubuntu 17.10 running in VitualBox Gnome (wayland session).

---

### Post by mc4man on 2017-07-26
Works just fine in an ubuntu session (- an actual ubuntu session, not what the [crappy gdm3/gnome-shell  greeter says]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157")...

Will not produce usable video in an ubuntu-wayland session, i.e. the session you're in.

screen shows, 1st 2 are short caps in an ubuntu session, 3rd is in the ubuntu-wayland session. Thumbnails are accurate in that the 3rd one is just black..

---

### Post by mc4man on 2017-07-26
The reason it  doesn't work in wayland is because it's using ffmpeg & x11grab, see screens for in it's code & it's log.
So file a bug with vokoscreen or an issue on it's [github issues page]("https://github.com/vkohaupt/vokoscreen/issues"). (maybe Gnome has a screen recording API... for wayland/mutter

Edit: for instance this recorder - [https://github.com/foss-project/green-recorder](https://github.com/foss-project/green-recorder)

---

### Post by ventrical on 2017-07-27
@dogmatix, mac4man,

Thanks !

My point is that a lot apps that currently work in 16.04 and in 17.10 unity-session will not work in gnome-shell or gnome shell with wayland - which is probably the case for a lot of graphical apps. My second point being that I am trying to get a heads up on the workload that it will take to test all these apps.

regards..

---

### Post by ventrical on 2017-07-27
> **mc4man said:**
> 

Edit: for instance this recorder - [https://github.com/foss-project/green-recorder](https://github.com/foss-project/green-recorder)

I was hoping for something out of the box (non-ppa) but green-recorder seems to fit just fine with wayland.

Thanks mac4man

Regards..

---

### Post by mc4man on 2017-07-27
> **ventrical said:**
> @dogmatix, mac4man,

Thanks !

My point is that a lot apps that currently work in 16.04 and in 17.10 unity-session will not work in gnome-shell or gnome shell with wayland - which is probably the case for a lot of graphical apps. 

regards..
gnome-shell is working just fine in the current default ubuntu session (X11),  in ubuntu-wayland (gnome-wayland) there are atm  significant limitations.

---

### Post by ventrical on 2017-07-27
> **mc4man said:**
> gnome-shell is working just fine in the current default ubuntu session (X11),  in ubuntu-wayland (gnome-wayland) there are atm  significant limitations.

Yes. I stand corrected. I had to log in from the "Ubuntu" in lightdm to get gnome shell using X11. vokoscreen working.

Really appreciate your pointers on this , saving lots of work.

Regards..

---

### Post by amano on 2017-07-27
Ventrical, you can add Micropolis (Sim City) to your list of broken apps under wayland. Only the plain soil is showing and surprisingly the trains. No streets, no trees, no residential zones etc.

Everything shows up as normal in the X session.

---

### Post by mc4man on 2017-07-27
> **ventrical said:**
> Yes. I stand corrected. I had to log in from the "Ubuntu" in lightdm to get gnome shell using X11. vokoscreen working.

You don't need to go to lightdm (even though atm a better experience..

At the gdm greeter one must switch from "ubuntu" to "ubuntu on wayland" then back to "ubuntu" to get an X11 session. At that point subsequent reboots will be to X11.
If later going to a wayland session & rebooting or shutting down the same process must be repeated.

In other words atm the greeter Always shows "ubuntu" even if really going to load a wayland session.

---

### Post by ventrical on 2017-07-27
bug report for vokoscreen

[https://bugs.launchpad.net/ubuntu/+source/vokoscreen/+bug/1706957](https://bugs.launchpad.net/ubuntu/+source/vokoscreen/+bug/1706957)

---

### Post by amano on 2017-07-27
I added the wayland tag. If it is a bug in wayland/weston/xwayland, the wayland tag should be added.

The wayland-session tag is different (added automatically by apport). That just means that you were running a wayland session when you encountered a bug. Even if the bug was totally unrelated and happens on X as well.

---

### Post by ventrical on 2017-07-27
> **amano said:**
> I added the wayland tag. If it is a bug in wayland, the wayland tag should be added.

The wayland-session tag is different (added automatically by apport). That just means that you were running a wayland session when you encountered a bug. Even if the bug was totally unrelated and happens on X as well.

@amano

Yes. Thanks .. I had seen that originally but didn't trim my report.

Thanks again

Regards..

---

### Post by jbicha on 2017-07-27
> **ventrical said:**
> I was hoping for something out of the box

How "out of the box" do you want?

GNOME has basic built-in [screen recording]("https://help.gnome.org/users/gnome-help/stable/screen-shot-record.html#screencast") functionality.

---

### Post by mc4man on 2017-07-27
maybe try the built-in recorder (gnome-shell). (ctrl+alt+shift+r
Not easy to modify settings so use with an extension instead- 
[https://extensions.gnome.org/extension/690/easyscreencast/](https://extensions.gnome.org/extension/690/easyscreencast/)

In a wayland session you could only do, vp8, vp9, ogg

---

### Post by ventrical on 2017-07-27
> **jbicha said:**
> How "out of the box" do you want?

GNOME has basic built-in [screen recording]("https://help.gnome.org/users/gnome-help/stable/screen-shot-record.html#screencast") functionality.

It has problems with wayland.

regards..

---

### Post by ventrical on 2017-07-27
> **jbicha said:**
> How "out of the box" do you want?

GNOME has basic built-in [screen recording]("https://help.gnome.org/users/gnome-help/stable/screen-shot-record.html#screencast") functionality.

It's worse than this one. Does the same thing though.. wont close file .. keeps on recording until break.

[https://ubuntuforums.org/showthread.php?t=2367236](https://ubuntuforums.org/showthread.php?t=2367236)

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> maybe try the built-in recorder (gnome-shell). (ctrl+alt+shift+r
Not easy to modify settings so use with an extension instead- 
[https://extensions.gnome.org/extension/690/easyscreencast/](https://extensions.gnome.org/extension/690/easyscreencast/)

In a wayland session you could only do, vp8, vp9, ogg

I filed that vokoscreen/wayland bug and see where that will go. Vokoscreen works out of the box on the other distros.

Regards..

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> maybe try the built-in recorder (gnome-shell). (ctrl+alt+shift+r
Not easy to modify settings so use with an extension instead- 
[https://extensions.gnome.org/extension/690/easyscreencast/](https://extensions.gnome.org/extension/690/easyscreencast/)

In a wayland session you could only do, vp8, vp9, ogg

Actually they are in webm format.

You have to use dconf-editor to tweak the max-screencast-length. Default is 30 secs.

---

### Post by ventrical on 2017-07-28
As it stands the default recorder has serious playback performance issues. On the other hand green-recorder has good performance but gets choppy after a couple of minutes with animated graphics on wayland.as I said earlier .. vokoscreen has no issues on gnome-shell or other distros .. just wayland

edit:
default recorder also has problems turning off on gnome-shell. it keeps running after ctrl+alt+shift+r

What package do I file a bug against?

---

### Post by mc4man on 2017-07-28
> **ventrical said:**
> As it stands the default recorder has serious playback performance issues. On the other hand green-recorder has good performance but gets choppy after a couple of minutes with animated graphics on wayland.as I said earlier .. vokoscreen has no issues on gnome-shell or other distros .. just wayland

edit:
default recorder also has problems turning off on gnome-shell. it keeps running after ctrl+alt+shift+r

What package do I file a bug against?
I would suspect gnome-shell.
A quick look here shows it (gnome-shell @ high cpu use) running for 7-12 sec. after stopping recording. As nothing additional is recorded then maybe it's catching up on the encoding..

Here i'd prefer ffmpeg for screen recording so X11 is better option. ( and an option that will still exist in 18.04..

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> I would suspect gnome-shell.
A quick look here shows it (gnome-shell @ high cpu use) running for 7-12 sec. after stopping recording. As nothing additional is recorded then maybe it's catching up on the encoding..

Here i'd prefer ffmpeg for screen recording so X11 is better option. ( and an option that will still exist in 18.04..

Here, if you are doing a recording and then stop it and then look at the file properties you can see it is still running after you try to stop it with the macro. So you have to log out and then log back on. I tested extremetux racer 3D game because I wanted to push  and see if wayland would break. Well, it does, sort of, but I can't really tell because I can't get vokoscreen (which is the app which we should be using to test it) to work. Currently have a bug filed against vokoscreen with wayland tag.

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> I would suspect gnome-shell.
A quick look here shows it (gnome-shell @ high cpu use) running for 7-12 sec..

Thanks mac4man,



[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1707217](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1707217)

---

### Post by ventrical on 2017-07-28
I also tested this on nVidia box and it is same broken behaviour as with intel set.

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ inxi -Fxz
System:    Host: ventrical-Precision-WorkStation-T3400 Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: Dell product: Precision WorkStation T3400
           Mobo: Dell model: 0TP412 BIOS: Dell v: A03 date: 01/31/2008
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 19152
           clock speeds: max: 2394 MHz 1: 2394 MHz 2: 2394 MHz 3: 2394 MHz
           4: 2394 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Gallium 0.4 on NVD9
           version: 4.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Broadcom Limited NetXtreme BCM5754 Gigabit Ethernet PCI Express
           driver: tg3 v: 3.137 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 160.0GB (6.0% used)
           ID-1: /dev/sda model: ST3160815AS size: 160.0GB
Partition: ID-1: / size: 74G used: 8.9G (13%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.0C mobo: N/A gpu: 30.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 191 Uptime: 32 min Memory: 1135.8/3883.1MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.25 
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```


regards..

---

### Post by grahammechanical on 2017-08-03
Mir needed a Linux container called Libertine to run certain apps that weren't written for Mir. I would not be surprised if Wayland compositors did not need a similar work around.

System Load Indicator does not work in Gnome 3 shell with or without Wayland. I think that we will find that apps originating from Gnome will work fine, but anything else will be down to luck.

Regards.

---

### Post by P-I H on 2017-08-03
A little off topic.

There are alternatives to System Load Indicator in Gnome. I use the System-monitor extension.
[https://www.dropbox.com/s/eyddb7nluzy6bfc/Screenshot%20from%202017-08-03%2022-07-33.png?dl=0](https://www.dropbox.com/s/eyddb7nluzy6bfc/Screenshot%20from%202017-08-03%2022-07-33.png?dl=0)

---

