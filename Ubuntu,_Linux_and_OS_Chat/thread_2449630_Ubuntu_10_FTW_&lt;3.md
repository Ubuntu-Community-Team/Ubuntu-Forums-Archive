---
title: "Ubuntu 10 FTW &lt;3"
date: 2020-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by chilewskirbuu on 2020-08-31
So uh i had this bugged out laptop that wouldnt work with win7 win 8 win10 or ubuntu 20 or ubuntu xfce4 slim, So i got ubuntu 10 New bro cd and the Computer works like a charm no screen glitching anymore :) Enjoy!! lol....
OS: Ubuntu 10 lol....
Cpu i7
3 gb of RAM
Nvidia 250M

---

### Post by mastablasta on 2020-08-31
don't connect it to internet and you will be fine.

---

### Post by chilewskirbuu on 2020-08-31
Hrm but i am connected to internet with Ubuntu 10 lol, why is this a bad thing i felt it was kinda shady but... what is my real concern just a test laptop to destroy fix actually now, will read thru this Thank you, I see something along the lines of firewall lol ..., and the browser doesnt work correctly, I found an alternative i have DUAL Boot ubuntu 10 which works stable with Xubuntu 16 LTS, which is working for now the GUI in ubuntu seems to have major issues with NVidia laptops older then 500 series :)Toshiba Qosmio, I Do and am Extremly Grateful for your post would like to get a mobile OS going with Ubuntu 10 For even older  laptop your info should save me a few hours of searching at least :), Slash pc project ( for tiny movie boxes for futuristic type house i mean why not have TV everywhere :))hobbies <3

---

### Post by QIII on 2020-08-31
It is a bad thing for three reasons:

1.  That release is long past its EOL and it is unsupported.
2.  You will not be able to do any update, or install any software from the repos.
3.  You are exposing yourself to risk of compromise if you access the web.

Your installation is not FTW, but a very dangerous action.

---

### Post by mastablasta on 2020-09-01
yur chip will be using nouveau driver which is reverse engineered opensource driver for nvidia chips. so you need to explore the kernel or driver switches and see fi there is something that needs to be turned on or off.
It says that 250 M is :
> **NV50 family (Tesla)**
[COLOR=#000000][FONT=&amp]Has unified shader architecture, can do GPGPU and [CUDA]("https://github.com/pathscale/pscnv/wiki/nvidia_compute"), has virtual memory, quite different from previous cards.[/FONT][/COLOR]

source: [https://nouveau.freedesktop.org/wiki/](https://nouveau.freedesktop.org/wiki/)

it then also explains you need to select performance level manually for Tesla familly:
> 
[LIST]
[*]Support for manual performance level selection (also known as "reclocking") on [GM10x Maxwell]("https://nouveau.freedesktop.org/wiki/CodeNames/#nv110familymaxwell"), [Kepler]("https://nouveau.freedesktop.org/wiki/CodeNames/#nve0familykepler") and [Tesla G94-GT218]("https://nouveau.freedesktop.org/wiki/CodeNames/#nv50familytesla") GPUs. Available in /sys/kernel/debug/dri/0/pstate
[/LIST]


so increasing performance and decreasing energy savings will help in general feel of the OS. not all GPU features might be available in the nouveau driver, but hopefully enough are available for your chip to make it a better experience for you.

Since old mobile chips had usually really poor performance (the technology just wasn't there yet), i would suggest getting a lighter version of the OS such as Lubuntu. or Xubuntu but make sure to turn off all special desktop effects and select a really simple theme.

there are also a couple of OS that are built especially with old hardware in mind or they use a very light desktop or windows manager by default. some of the easy to use ones are: MX linux, AntiX, Bodhi Linux, Bunsenlabs linux, Puppy Linux,...

You could also try older Debian stable that has older kernel and install some XFCE or LXDE on it. 

Since you are experimenting on old laptop have a look at Slitaz and Tiny Core. Just for fun. another thing you can try is to use netinstall image or minimal install image and then add just what you need to keep system as light as possible and you can add only windows manager to it (e.g. iceWM, Flwm, OPenbox or a tilled one like Awesome or i3).

---

### Post by zebra2 on 2020-09-01
@OP 
Don't know for sure what release you are using but 10.04 Lucid was a very good release, however 10.10 Maverick was an absolute rocket on the system I was using at the time.  11.04 Introduced the Unity Graphical Desktop.

Don't forget to activate the firewall. I doubt you will have a problem

---

