---
title: "Flameshot: screenshot tool with built-in editing"
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by vasa1 on 2018-02-28
I came across Flameshot here: [https://www.youtube.com/watch?v=XYj_XCgSfHY&t=172s](https://www.youtube.com/watch?v=XYj_XCgSfHY&t=172s)

It's in the Universe repo in 18.04.

Seems decent.

---

### Post by cruzer001 on 2018-02-28
Nice find vasa1

[https://www.omgubuntu.co.uk/2018/01/flameshot-linux-screenshot-tool-annotation](https://www.omgubuntu.co.uk/2018/01/flameshot-linux-screenshot-tool-annotation)

---

### Post by vasa1 on 2018-02-28
Have you found an AppImage link?

BTW, what does "callout" mean in the OMG piece?> take screenshots on Linux and annotate them with arrows, boxes, and callouts &#8212; no external editor required.

---

### Post by again? on 2018-02-28
Looks good vasa1.
I'm a fan of shutter but Flameshot could be a replacement.

I was able to compile and install flameshot in Xubuntu 17.10 from [https://github.com/lupoDharkael/flameshot#installation](https://github.com/lupoDharkael/flameshot#installation)

---

### Post by vasa1 on 2018-02-28
And the developer is working on text annotation: [https://github.com/lupoDharkael/flameshot/issues/11](https://github.com/lupoDharkael/flameshot/issues/11)

---

### Post by cruzer001 on 2018-02-28
> Have you found an AppImage link?
Nope, just this
[https://packages.ubuntu.com/bionic/flameshot](https://packages.ubuntu.com/bionic/flameshot)
> BTW, what does "callout" mean in the OMG piece?
[ATTACH=CONFIG]278720[/ATTACH]

---

### Post by vasa1 on 2018-02-28
@cruzer001, thanks! I browse some sites with images turned off!

---

### Post by corradoventu on 2018-03-01
installed in ubuntu 18.04 from Ubuntu Software, I start it from terminal or the launcher, i see the icon in the top bar, with 'comfiguration, information, quit' but nothing happens 
```
corrado@corrado-p7-bb-0225:~$ apt policy flameshot
flameshot:
  Installed: 0.5.1-2
  Candidate: 0.5.1-2
  Version table:
 *** 0.5.1-2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p7-bb-0225:~$ inxi -SCGx
System:    Host: corrado-p7-bb-0225 Kernel: 4.15.0-10-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.28-1ubuntu3)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.0-rc4 Direct Render: Yes
corrado@corrado-p7-bb-0225:~$
```

---

### Post by vasa1 on 2018-03-01
You don't see three choices? Maybe you pinned the wrong choice to your launcher?

---

### Post by #&amp;thj^% on 2018-03-01
It seems to me that this might be a bit confusing for some with 3 entries for flameshot.
To open flameshot via terminal:
```
flameshot
```
To set Configure Flameshot:
```
flameshot config
```
To Take graphical screenshot:
```
flameshot gui
```
[s]And to me the above is identical to the first "flameshot"[/s] More below
And:
```
flameshot full -p Downloads
```
You can use the "-p" flag for path to save to.
More on:
```
flameshot --help
Usage: flameshot [flameshot-options] [arguments]

Options:
  -h, --help     Displays this help
  -v, --version  Displays version information

Arguments:
  gui            Start a manual capture in GUI mode.
  full           Capture the entire desktop.
  config         Configure flameshot.


```
La mia eredità è dall'Italia

---

### Post by corradoventu on 2018-03-01
1) Sorry for not using 'code' i will remember (i hope)
2) found my error, i used the wrong choice, but i was confused having 3 different entries.

---

### Post by again? on 2018-03-01
> **1fallen said:**
> It seems to me that this might be a bit confusing for some with 3 entries for flameshot.
To open flameshot via terminal:
```
flameshot
```
To set Configure Flameshot:
```
flameshot config
```
To Take graphical screenshot:
```
flameshot gui
```
And to me the above is identical to the first "flameshot"
And:
```
flameshot full -p Downloads
```
You can use the "-p" flag for path to save to.
More on:
```
flameshot --help
Usage: flameshot [flameshot-options] [arguments]

Options:
  -h, --help     Displays this help
  -v, --version  Displays version information

Arguments:
  gui            Start a manual capture in GUI mode.
  full           Capture the entire desktop.
  config         Configure flameshot.


```
La mia eredità è dall'Italia

Here in xfce....
**flameshot** ...starts without the gui to the system tray
**flameshot gui** ...starts with the gui ready to select an area

---

