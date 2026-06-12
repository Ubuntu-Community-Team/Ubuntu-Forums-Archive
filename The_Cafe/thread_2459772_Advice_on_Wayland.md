---
title: "Advice on Wayland?"
date: 2021-03-25
forum: The Cafe
---

### Post by DuckHook on 2021-03-25
Due to a nasty video breakage that was hard to triage but had something to do with X11, I just made the jump to Wayland. All I can say is, "Wow". So far, everything not only works, but seems snappier and more stable.

I had resisted until now because my Wayland experience on Bionic was not good. In particular, it broke pulseaudio sockets on my LXD containers. But I just tried it this morning and everything works!

Are there hidden issues I should be aware of? Wayland user advice would be welcome and greatly appreciated.

---

### Post by TheFu on 2021-03-25
Hows the remote running of GUI applications been?  Did they fix that?  Last time Wayland was the default, no remote X11-like capabilities worked.  Right now, I have about 15 windows open - 13 of those are running programs on other systems.  Basically, I need an X/Server more than I need fast local graphics.

What about screen recording and capture tools?  
Does ImageMagick "**import**" work?  How about **SimpleScreenRecorder**?  I like to record presentations to re-review later regardless of whether the video-platform supports it.

---

### Post by QIII on 2021-03-25
Have the Wayland developers changed their minds on the "There are things we have decided in our infinite wisdom that users don't need to do so we won't allow them to do so" attitude?

---

### Post by DuckHook on 2021-03-25
> **TheFu said:**
> Hows the remote running of GUI applications been?  Did they fix that?  Last time Wayland was the default, no remote X11-like capabilities worked.  Right now, I have about 15 windows open - 13 of those are running programs on other systems.  Basically, I need an X/Server more than I need fast local graphics.
15 windows. Oooookay… See, that's so far beyond my use case that it feels like it's another universe. I don't even have one remote GUI and don't foresee any future need.
> What about screen recording and capture tools?  
Does ImageMagick "**import**" work?  How about **SimpleScreenRecorder**?  I like to record presentations to re-review later regardless of whether the video-platform supports it.
Haven't done anything remotely like those yet. I just made the jump this morning. Again, those are rather exotic use cases for me, but I can see their utility. If the need arises, I'll be sure to report back on any tests I do.
> **QIII said:**
> Have the Wayland developers changed their minds on the "There are things we have decided in our infinite wisdom that users don't need to do so we won't allow them to do so" attitude?
I wasn't aware of this attitude. Seems quite counter to the whole Linux philosophy. When it comes to Wayland, I'm so new to it that I just fell off the turnip truck. Are some of those limitations what TheFu described above?

---

### Post by DuckHook on 2021-03-25
After my first-day test drive:

[LIST=1]
[*]The motivation for switching was that X11 would drop the video signal to my monitor about 1 in 10 boots. Unplugging&#8209;plugging the video cable would not work. The only recourse was to either ssh into my main box from another (a royal pain) or sysrq (the nuclear option). Wayland has solved that.
[*]My video card is an older one that was the last of the AMD products using the Radeon driver. The combo of card, driver, kernel and X11 was always flaky and maxed out at 30 Hz, which sometimes induced eyestrain and headaches. Wayland is capable of driving the card at 60 Hz which is making a nice difference visually.
[*]Ubuntu's default video player, Totem, was unviewable under X because video would drop out, audio would desync and the output became a trial on the nerves. I worked around it with VLC player, but it's sad to have to resort to such kludges. Under Wayland, Totem runs as smooth as silk.
[/LIST]
So far, I'm highly impressed.

---

### Post by poorguy on 2021-03-26
I've used Wayland with Intel integrated graphics adapters and it seemed to work well.

Does anyone know anything about Wayland working with Nvidia graphics cards.

I have a Asus brand NVIDIA GT218 [GeForce 8400 GS Rev. 3] with the Nvidia 340.108 proprietary driver installed.

---

### Post by TheFu on 2021-03-26
Video drivers are below Wayland/X11.  Shouldn't matter.

---

### Post by grahammechanical on 2021-03-26
I understood Wayland to be a protocol and that a compositing window manager (compositor) would be needed that operates according to the protocol. It seems that Mutter is the Wayland compositor for Gnome 3 shell. So, if there are developer limitations as to what Mutter as the display server/compositor can do it would be down to the Gnome developers themselves.

For those looking for technical information about the Wayland compositor in Ubuntu 20.04 + Gnome 3 shell, then this might help

[https://www.phoronix.com/scan.php?page=article&item=ubuntu-2004-waylandgame&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-2004-waylandgame&num=1)

Regards

---

### Post by DuckHook on 2021-03-26
> **poorguy said:**
> …Does anyone know anything about Wayland working with Nvidia graphics cards…
There were some complaints when Wayland first came out that it did not play well with nVidia, but that was years ago. Since IT years run even faster than dog years, things have probably changed dramatically since then.

It's easy to try it out: just choose Wayland at login (or does that apply only to Gnome?).

---

### Post by poorguy on 2021-03-26
Yeah I read that Wayland needed the 450 / 470 Nvidia driver which isn't even offered for my graphics card.

Yeah I read all of the Nvidia didn't play well with Wayland but I will give it a try over the weekend and report back.

OK guys I appreciate the replies and I just wanted to get some feedback before I gave Wayland and Nvidia a try.


Thanks.

---

### Post by TheFu on 2021-03-26
> **DuckHook said:**
>  It's easy to try it out: just choose Wayland at login (or does that apply only to Gnome?).

I'll try it, but I don't login more than once a week usually - well, not on desktops with GUIs. ;(
Don't even know if Wayland is an option on my systems.  I've always wanted it disabled.

---

### Post by poorguy on 2021-03-26
Well that was easy enough to do and no go.

I don't even have the option to use Wayland as there is no settings gear in the lower right hand corner of my login screen.

Guess my driver and graphics card doesn't meet the requirements of Wayland.

OH well I've got another Ubuntu 20.04 desktop that is all Intel inside and supports Wayland and runs great using Wayland.

I guess that's what I get for being cheap and using computers built from bits and pieces from other users discarded computers.

---

### Post by DuckHook on 2021-03-26
> **TheFu said:**
> I'll try it, but … I've always wanted it disabled.
:lolflag:

Well, there's no ***obligation*** to try it you know. You have every right to ignore it. And given your use case, I doubt it would work for you. It just solves a few problems for little ol' me.

---

### Post by poorguy on 2021-03-26
FWIW.
[https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-470-Wayland-Friendly](https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-470-Wayland-Friendly)

---

### Post by TheFu on 2021-03-26
> **DuckHook said:**
> :lolflag:

Well, there's no ***obligation*** to try it you know. You have every right to ignore it. And given your use case, I doubt it would work for you. It just solves a few problems for little ol' me.

Or it might do everything better. I'll never know without trying. I can fix my ignorance, maybe.

---

### Post by mastablasta on 2021-03-27
> **QIII said:**
> Have the Wayland developers changed their minds on the "There are things we have decided in our infinite wisdom that users don't need to do so we won't allow them to do so" attitude?


don't know about their attitudes, but this is major problem one - not all features and drivers are present or working. one case is synaptics touch pad configuration. it's just not there. as i read, they removed (not yet not implemented?) many other features users normally use. if they can sort of add features most people use in X, but make it faster, then no desktop user will mind the move.

> **poorguy said:**
> 
Does anyone know anything about Wayland working with Nvidia graphics cards.


this is major problem 2. at leats for me, because i have nvidia card. as do many other people. this is not X or Wayland fault, but nvidia not catching up with their driver. i can understand they are in no hurry to support the old chips or that they can't afford to invest into driver upgrades for older components (although they soon might since new ones are getting really hard to come by). but on the other hand they could help nouveau team a bit more so they could reach (at leats on older chip ) on par performance with new models.

EDIT: i appreciate having the fall back option (X). i am not sure why we should burden the environment with fully functioning components that just lost software support.

---

### Post by poorguy on 2021-03-27
[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **poorguy**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=14028510#post14028510")                 
 Does anyone know anything about Wayland working with Nvidia graphics cards.


> **mastablasta said:**
> 

this is major problem 2. at leats for me, because i have nvidia card. as do many other people. this is not X or Wayland fault, but nvidia not catching up with their driver. i can understand they are in no hurry to support the old chips or that they can't afford to invest into driver upgrades for older components (although they soon might since new ones are getting really hard to come by). but on the other hand they could help nouveau team a bit more so they could reach (at leats on older chip ) on par performance with new models.


Nvidia does seem to act as though they lack any interest in getting driver support for Wayland.

That would be great if Nvidia would help with nouveau team more but obviously Nvidia has no interest in doing so.

---

### Post by TheFu on 2021-03-27
Rebooted today.  Didn't see Wayland as an option on the login screen. Guess I was very successful in removing it. It has an nVidia GT 1030 GPU.

I'll go out of my way to see that Wayland is loaded on the laptop that still needs to be rebooted from the patching. Need to hunt down some install instructions. Looks like it may not be possible without using gdm or whatever kde uses.

---

### Post by MartyBuntu on 2021-03-28
> **QIII said:**
> Have the **[FONT=Impact]Wayland[/FONT]** developers changed their minds on the "There are things we have decided in our infinite wisdom that users don't need to do so we won't allow them to do so" attitude?


You spelled GNOME wrong....

---

### Post by tea for one on 2021-03-28
> **DuckHook said:**
> Are there hidden issues I should be aware of? Wayland user advice would be welcome and greatly appreciated.

A couple of years ago, synaptic package manager used to fail in a Wayland session but now it is OK.
[COLOR="#0000FF"]virt-viewer[/COLOR] ( a tool to display the graphical console of a VM) has a similar difficulty.
```
edited@edited:~$ virt-viewer

(virt-viewer:3340): Gdk-CRITICAL **: 19:06:37.643: gdk_wayland_window_set_dbus_properties_libgtk_only: assertion 'GDK_IS_WAYLAND_WINDOW (window)' failed
```

I suspect Wayland will address this in the fullness of time.

---

### Post by kurt18947 on 2021-03-29
I've run into what sounds like the same problem on a Ryzen/AMD/Radeon video box. If running an X session the video will lock up and none of the simple fixes - ctrl alt del or trying different terminals work. So far a hard reboot returns to the session with no data loss. Wayland does not do this.

SWMBO uses Shutter which only runs under X so Wayland is not an option for her. I've tried Shutter alternatives but they lack one function she uses several times a day. She wants to do a screen shot and print the result without pasting the screen shot into another application. Shutter will do this, no other screen shot application I've found will.

---

### Post by VMC on 2021-03-29
> **QIII said:**
> Have the Wayland developers changed their minds on the "There are things we have decided in our infinite wisdom that users don't need to do so we won't allow them to do so" attitude?

What was it, Steve Jobs said "Don't hold it that way". So we have now "Don't use it way".

I tried Gnome and it booted okay, but the dock took several minutes to come up. Haven't tried it in a while. My debian gnome works perfectly.

---

### Post by DuckHook on 2021-03-29
> **kurt18947 said:**
> I've run into what sounds like the same problem on a Ryzen/AMD/Radeon video box. If running an X session the video will lock up and none of the simple fixes - ctrl alt del or trying different terminals work. So far a hard reboot returns to the session with no data loss. Wayland does not do this.
Mine was a different problem. Once running, it didn't lock up. My problem was that, infrequently, X would fail to hand off from GDM to the window manager and just drop the video signal altogether. The OS underneath was still running fine and if I switched to another TTY blindly, going by memory, I could reboot it by logging in, then typing sudo reboot with no video signal. But that's a hairy way to run a production box.
> SWMBO uses Shutter which only runs under X so Wayland is not an option for her. I've tried Shutter alternatives but they lack one function she uses several times a day. She wants to do a screen shot and print the result without pasting the screen shot into another application. Shutter will do this, no other screen shot application I've found will.
Though the Wayland landscape is slowly getting better, there are still a number of areas where it doesn't do too well. It sounds like Shutter is one of them. However, I can attest that xWayland has progressed enough that I can now get sound in LXD containers under Wayland. That was my big bugbear. Now that that's working, I doubt I'll be going back to Xorg. The increased stability alone is sufficient reason for me to make the jump.

---

### Post by mastablasta on 2021-03-30
> **kurt18947 said:**
> I've run into what sounds like the same problem on a Ryzen/AMD/Radeon video box. If running an X session the video will lock up and none of the simple fixes - ctrl alt del or trying different terminals work. So far a hard reboot returns to the session with no data loss. Wayland does not do this.

SWMBO uses Shutter which only runs under X so Wayland is not an option for her. I've tried Shutter alternatives but they lack one function she uses several times a day. She wants to do a screen shot and print the result without pasting the screen shot into another application. Shutter will do this, no other screen shot application I've found will.

i don't have it for now. we had to use iommu=soft switch to avoid strange ryzen GPU chip behaviour

spectacle in KDE also does this. not sure if it is wayland ready.

---

### Post by zebra2 on 2021-04-04
I've been using Wayland since it arose from the primordial ooze without any problems at all.  However, I run a few Linux friendly systems and also being a Linux household I wouldn't know the difference between a problem and normal behavior.

---

### Post by kurt18947 on 2021-04-09
> **poorguy said:**
> Well that was easy enough to do and no go.

I don't even have the option to use Wayland as there is no settings gear in the lower right hand corner of my login screen.

Guess my driver and graphics card doesn't meet the requirements of Wayland.

OH well I've got another Ubuntu 20.04 desktop that is all Intel inside and supports Wayland and runs great using Wayland.

I guess that's what I get for being cheap and using computers built from bits and pieces from other users discarded computers.

If your Nvidia card is discreet you could always replace it with an AMD video card. I've bought AMD video cards off Ebay for $20 -$30 - they're pulls, typically Dell or HP. They seem to work fine on MSI/Gigabyte/Asus boards. My main machine has MSI Ryzen MoBo and AMD 7450 video. I'm not a gamer or video editor so don't demand too much of my video system. This setup works just fine using Wayland. If using X.org eventually - and it may be several days - the video will lock up. The mouse cursor will move but that's all. I've had this happen perhaps a half dozen times. After a hard restart I can restart the program I was in and everything is there as it was when it froze up.

---

### Post by poorguy on 2021-04-11
Hey kurt18947,

I appreciate the advice although I have several computers with Intel integrated graphics that Wayland runs great with.
My whole interest with Nvidia and Wayland was curiosity because Nvidia doesn't seem to have interest in helping opensource.


```


Dell-OptiPlex-XE:~$ inxi -Fxz
System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.7 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Dell product: OptiPlex XE v: N/A serial: <filter> 
           Mobo: Dell model: 0TNXNR v: A01 serial: <filter> BIOS: Dell v: A05 date: 01/09/2013 
CPU:       Topology: Dual Core model: Intel Core2 Duo E7400 bits: 64 type: MCP arch: Penryn rev: A 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx bogomips: 11171 
           Speed: 1596 MHz min/max: 1600/2800 MHz Core speeds (MHz): 1: 1596 2: 1596 
Graphics:  Device-1: Intel 4 Series Integrated Graphics vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Display: wayland server: X.Org 1.20.9 driver: i915 resolution: 1024x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel Q45/Q43 (ELK) v: 2.1 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: Intel 82801JD/DO HD Audio vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.8.0-48-generic 
Network:   Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe vendor: Dell 
           driver: tg3 v: kernel port: 0980 bus ID: 05:00.0 
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Broadcom and subsidiaries NetXtreme BCM5761 Gigabit Ethernet PCIe vendor: Dell 
           driver: tg3 v: kernel port: 0980 bus ID: 06:00.0 
           IF: enp6s0 state: down mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 7.63 GiB (5.1%) 
           ID-1: /dev/sda vendor: Western Digital model: WD1600AAJS-22PSA0 size: 149.05 GiB 
RAID:      Hardware-1: Intel SATA Controller [RAID mode] driver: ahci v: 3.0 bus ID: 00:1f.2 
Partition: ID-1: / size: 145.22 GiB used: 7.63 GiB (5.3%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 31.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 192 Uptime: 21h 50m Memory: 7.68 GiB used: 1014.3 MiB (12.9%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
Dell-OptiPlex-XE:~$


```

---

### Post by kurt18947 on 2021-04-11
> **poorguy said:**
> Hey kurt18947,

I appreciate the advice although I have several computers with Intel integrated graphics that Wayland runs great with.
My whole interest with Nvidia and Wayland was curiosity because Nvidia doesn't seem to have interest in helping opensource.


There's a reason Linux Torvalds isn't one of Nvidia's biggest fans. I have used Nvidia's closed driver and it fixed a suspend/resume problem I had but I think caused a different issue or two, really can't remember. I know I prefer AMD video at this point.

---

### Post by poorguy on 2021-04-11
> **kurt18947 said:**
> There's a reason Linux Torvalds isn't one of Nvidia's biggest fans. I have used Nvidia's closed driver and it fixed a suspend/resume problem I had but I think caused a different issue or two, really can't remember. I know I prefer AMD video at this point.

I used to have good results using Nvidia graphics cards but Ubuntu 20.04 doesn't seem to like some of my Nvidia graphics cards.

The Nouveau graphics driver works OK but sometimes I really need the proprietary Nvidia driver and it doesn't work half of the time even when it installs. 

OH well I stick with my Intel Inside for Ubuntu and Wayland.

---

### Post by poorguy on 2021-04-12
I'm confused because everything I read about Nvidia and Wayland says that a Nvidia proprietary graphics driver is needed to run Wayland with an Nvidia graphics card.

I did try to run Wayland and I was using an Nvidia proprietary graphics driver and I was unable to enable Wayland as the settings gear on my log in screen wasn't available.


Today I decided to reinstall Ubuntu 20.04.2 on the same computer only this time I didn't use the Nvidia proprietary graphics driver and to my surprise I now have the option to use Wayland I am using Wayland and so far it appears to be working well.

Why does the Nouveau open source driver work and since it does work why does anyone need the Nvidia proprietary graphics driver if the Nouveau open source graphics driver works.


Thanks.


```


nelson@hp-pavilion:~$ echo $XDG_SESSION_TYPE
wayland
nelson@hp-pavilion:~$ 


```

```


nelson@hp-pavilion:~$ env | grep -i wayland
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu-wayland:/etc/xdg
DESKTOP_SESSION=ubuntu-wayland
XDG_SESSION_DESKTOP=ubuntu-wayland
XDG_SESSION_TYPE=wayland
XAUTHORITY=/run/user/1000/.mutter-Xwaylandauth.FLUV10
WAYLAND_DISPLAY=wayland-0
XDG_DATA_DIRS=/usr/share/ubuntu-wayland:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
GDMSESSION=ubuntu-wayland
nelson@hp-pavilion:~$ 


```

```


nelson@hp-pavilion:~$ inxi -Fxz
System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.7 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop System: HP-Pavilion product: GN556AA-ABA a6200n v: N/A serial: <filter> 
           Mobo: ECS model: Nettle2 v: 1.0 serial: <filter> BIOS: Phoenix v: 5.12 date: 06/11/2007 
CPU:       Topology: Dual Core model: AMD Athlon 64 X2 5600+ bits: 64 type: MCP arch: K8 rev.F+ 
           rev: 3 L2 cache: 2048 KiB 
           flags: lm nx pae sse sse2 sse3 svm bogomips: 11251 
           Speed: 1000 MHz min/max: 1000/2800 MHz Core speeds (MHz): 1: 1000 2: 1000 
Graphics:  Device-1: NVIDIA GT218 [GeForce 8400 GS Rev. 3] vendor: ASUSTeK driver: nouveau v: kernel 
           bus ID: 02:00.0 
           Display: wayland server: X.Org 1.20.9 driver: nouveau resolution: 1024x768~60Hz 
           OpenGL: renderer: NVA8 v: 3.3 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard 
           driver: snd_hda_intel v: kernel bus ID: 00:05.0 
           Device-2: NVIDIA High Definition Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 02:00.1 
           Sound Server: ALSA v: k5.8.0-48-generic 
Network:   Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard type: network bridge 
           driver: forcedeth v: kernel port: ec00 bus ID: 00:07.0 
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 76.69 GiB used: 8.68 GiB (11.3%) 
           ID-1: /dev/sda vendor: Hitachi model: HDS721680PLAT80 size: 76.69 GiB 
Partition: ID-1: / size: 74.49 GiB used: 8.68 GiB (11.7%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 33.0 C mobo: N/A gpu: nouveau temp: 40 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 200 Uptime: 3m Memory: 5.81 GiB used: 660.5 MiB (11.1%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
nelson@hp-pavilion:~$ 


```

---

### Post by DuckHook on 2021-04-12
> **poorguy said:**
> I'm confused because everything I read about Nvidia and Wayland says that a Nvidia proprietary graphics driver is needed to run Wayland with an Nvidia graphics card.
…
Why does the Nouveau open source driver work and since it does work why does anyone need the Nvidia proprietary graphics driver if the Nouveau open source graphics driver works.
I have a very old nVidia&#8209;based laptop that runs Wayland properly on the FOSS Nouveau driver. Its problem is that Nouveau displays things like video sub-optimally. For smooth video, I must run nVidia's proprietary driver, and that's when the problems start.

It doesn't help that I also run LXD containers and the proprietary drivers won't properly map LXD pulseaudio to the host. At least, I haven't been able to get it to work. I've kept to Nouveau because of this, despite its limitations.

Many prefer the proprietary drivers because they give better performance. But if you are happy with the Nouveau driver, then there's no need to change and your system will likely be stabler.

---

### Post by poorguy on 2021-04-12
I've actually have good results using the Nouveau open source graphics driver vs the Nvidia proprietary graphics driver depends on which Nvidia graphics card I'm using and most of mine are from the Windows Vista days so they're years old.

I usually try and stick with the Nouveau open source graphics driver if it's working without problems because I have had problems with the Nvidia proprietary graphics driver.

I think I'm going to leave it as it is now a well working desktop in its present state and if I start having problems I'll switch from Wayland back to the X11 standard.

I've done a lot of reading about Wayland and there are a lot of mixed feelings about Wayland kinda like Snaps but I think my 2 computers use less system resources using Wayland although I may be wrong.

Anyway I'm slowly learning about stuff I have no clue of and surprisingly somewhat understanding it although trying to learn to much all at once at my old age of 69  confuses me sometimes.



Thanks DuckHook for the reply and the explaining of.

---

### Post by ajgreeny on 2021-04-12
I haven't seen nor used wayland since it became the default back in whichever version it was a few years ago, and immediately stopped using it as there were so many things that did not work well on my hardware.

However, having read this thread I fancy trying again but I can not figure out how to install it on Xubuntu 20.04, or even if it's possible.  Everything seems to point to gnome being needed and gdm3 but I'd prefer not to have gnome which I dislike, nor to change the DM in use.
So is it possible to add wayland to Xubuntu 20.04 and make the choice, Xorg or wayland session, from lightdm which Xubuntu uses?

My machines are all using Intel graphics, no nvidia cards, but I can not find any info on what needs to be installed.

---

### Post by DuckHook on 2021-04-12
> **ajgreeny said:**
> &#8230;is it possible to add wayland to Xubuntu 20.04&#8230;
Hi aj,

I'm pretty sure that XFCE is not Wayland&#8209;capable. Not yet anyway. If you don't like Gnome, perhaps try one of my favourites, Enlightenment. I believe the Enlightenment team have ported their latest few releases to Wayland, so it is both Wayland and X11 capable. You'd have to install the latest directly though. The version in the repos is ancient.

KDE is already Wayland-capable so Kubuntu is an option.

Another option might be Gnome&#8209;flashback, which might be Wayland compatible because it uses GTK3. I've never tried it.

Yet another option is Lubuntu, but you would have to go to Groovy or Hirsute which would take you off LTS.

For sure I would try everything out in a VM first though.

---

### Post by poorguy on 2021-04-12
I ran across this in my searches about Wayland.

[https://www.phoronix.com/scan.php?page=news_item&px=Xfce-4.18-Planning-Begins](https://www.phoronix.com/scan.php?page=news_item&px=Xfce-4.18-Planning-Begins)

---

### Post by ajgreeny on 2021-04-13
Thanks to both of you.

I thought the probability was that Xfce was not waylaid compatible and you seem to have more or less confirmed that.

I may well try a full Ubuntu install again in KVM and see how that goes with wayland but the chances of sticking with gnome are, I'm afraid, just about zero; it just doesn't work for me in the way I want it to.

---

### Post by ajgreeny on 2021-04-13
I have just installed Ubuntu 20.04.2 as a VM in KVM/QEMU simply to try wayland  and at the moment wayland is running it with no difficulties or problems.

Actually I did have one problem; I am so used to using command ***xrandr -s 1920x1080*** to set screen resolution and I did so when using wayland; of course, it doesn't work as it needs an x session.  However, using the settings utility gets the resolution sorted with a GUI system.
I'm sure there will be a terminal command to do this with wayland but have not yet even searched for it.

Using synaptic works by default now without the previous workaround necessary to get GUI applications to work with root permissions, and so far I have not found any disadvantages to wayland compared with Xorg though it is certainly early days so far and there may be many that I've yet to find.

---

### Post by poorguy on 2021-04-14
> **ajgreeny said:**
> 
Actually I did have one problem; I am so used to using command ***xrandr -s 1920x1080*** to set screen resolution and I did so when using wayland; of course, it doesn't work as it needs an x session.  However, using the settings utility gets the resolution sorted with a GUI system.
I'm sure there will be a terminal command to do this with wayland but have not yet even searched for it.


I ran across this link, perhaps it may be of use.

[https://askubuntu.com/questions/973499/wayland-how-to-set-a-custom-resolution](https://askubuntu.com/questions/973499/wayland-how-to-set-a-custom-resolution)

---

