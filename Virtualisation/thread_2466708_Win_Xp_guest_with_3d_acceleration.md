---
title: "Win Xp guest with 3d acceleration"
date: 2021-09-03
forum: Virtualisation
---

### Post by demonenero84 on 2021-09-03
Hello,
Is there a way to have a Win xp vm with 3d acceleration using QEMU/KVM? 
I am aware that Vm workstation and virtual box support 3d acceleration for some guests, I was wondering if QEMU/KVM can have a vm with 3d acceleration to play old Win xp games
Thanks in advance:P

---

### Post by TheFu on 2021-09-05
Try using spice.  SPICE is a display protocol that is extremely fast.  It supports opengl.
Use **glxinfo -B** to see the level your box supports.

For example, on my KVM VM host, I see
```
OpenGL version string: 4.6.0 NVIDIA 460.91.03
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 460.91.03
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
```

But inside a 20.04 KVM VM (running on the same physical machine), I see
```
OpenGL version string: 3.1 Mesa 21.0.3
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```
**virt-manager** will setup a SPICE connection by default.  Just need to load the QXL video drivers into WinXP. I don't know if those are on the web anymore (XP support ended a LONG TIME AGO), but that's where I got them.  Inside _Windows Device Manager_, the video driver should say:
**Red Hat QXL GPU** in the Display Adapters section once correctly installed.

Google "spice qxl windows driver"  [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html) ... there are links to Windows QXL binaries.  None are labeled "WinXP", so I haven't any idea if those will work or not.

---

### Post by demonenero84 on 2021-09-06
Thanks a lot for the reply :)
Just a few weeks ago I made a similar vm with a QXL GPU ( following this guide [https://www.youtube.com/watch?v=qsVxjc3leQU](https://www.youtube.com/watch?v=qsVxjc3leQU) ).
To be honest I was not aware about QXL GPU support for 3D acceleration :oops:I did not test any games.
 Have you ever played any games with this type of vm? Is this solution a practical alternative to GPU passthrough to play old win xp games?
Thanks

---

### Post by TheFu on 2021-09-06
I don't game on computers. Sorry.  

I generally run some ATC sims on Android and still use a PS2 with the most popular games from that time - SOCOM, GTA, GT, DDR, Ace Combat 4/5/6.

Inside the VM, I see frame rates limited to the same rate that my monitor can handle - 60Hz.

---

### Post by demonenero84 on 2021-09-07
Thanks, I play a few ps2 games every now and than too:lolflag:, however I use an emulator not real hardware

---

### Post by MAFoElffen on 2021-09-08
One curiosity... What graphics is on your VM Host?

---

### Post by monkeybrain20122 on 2021-09-08
virgl is quite spectacular on Linux guests with great frame rate, its goal is to attain near bare metal performance (beats QXL/Spice hands down), many native Linux games are totally playable. But  it doesn't work on Windows guests. In fact seems that nothing short of GPU pass through works on Windows guests. [https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration](https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration)

Also XP is a rotting corpse that should have been buried deep long ago.

---

### Post by demonenero84 on 2021-09-08
> 
One curiosity... What graphics is on your VM Host?                 

Nvidia [FONT=monospace][FONT=monospace][COLOR=#000000]GeForce GTX 1050
[/COLOR][/FONT][/FONT]> [FONT=monospace][FONT=monospace][COLOR=#000000]virgl is quite spectacular on Linux guests
[/COLOR][/FONT][/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]
I have to try it then :) , I really like the idea of having a safe vm to play around
[/COLOR][/FONT][/FONT]> [FONT=monospace][FONT=monospace][COLOR=#000000]Also XP is a rotting corpse that should have been buried deep long ago
[/COLOR][/FONT][/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][/FONT]For me it is the perfect machine for retrogaming old Windows 98 and Windows Xp games, anyway WINE is really an impressive alternative for old games ( much better than Win 10 )

---

### Post by TheFu on 2021-09-08
Some games don't run well, if at all, on any newer OS than WinXP. Should we just through away our $500 game library? Not an option for us.  I still play some Atari 2600 games from my youth.

I need for my GPU access to VMs to be network agnostic most of the time.  Running on the same physical hardware seldom happens here. I'm probably unusual in that.  The intel iGVT-g stuff that I've seen the last 4+ yrs has always been unstable.  Crashing after just a few minutes.  I had hopes for this for laptop use.

virgl ....
> The project is currently investigating the desktop virtualisation use case only. This use case is where the viewer, host and guest are all running on the same machine (i.e. workstation or laptop).

For virgl, the documentation is terrible and it appears that rebuilding qemu is required.  Cannot tell what releases are supported, which dependencies are necessary, and which hardware should work. Stuff like this is usually tied to specific, high-end, GPUs.  I don't see any mention of GPU hardware.   There is an 18.04 PPA from Stein, but I'm uncomfortable risking all my KVM VMs to just support a single desktop.
Without adding any new software, I attempted to get virt-manager to accept some settings for virgl. Eventually, got passed the errors, but got stuck with
```
$ virsh start regulus
error: Failed to start domain regulus
error: unsupported configuration: This QEMU doesn't support spice OpenGL
```
Which leads to the PPA.

So others who have more time to waste might get farther, faster, in the VM settings
```
Tab: **Display Spice**
 Spice Server
 None
 Unchecked
 Keymap: en-us
 OpenGL: checked (has a [COLOR="#FF0000"]![/COLOR] next to it)
    Auto
Tab: **Channel Spice**
 Device type: spicevmc
 Target type: virtio
 Target name: com.redhat.spice.0
Tab: **Video Virtio**
 Model: Virtio
 RAM - 
 Heads: 1
 3d Accel: [COLOR="#008000"]checked[/COLOR]
```

With the 3d Accel checked, starting the domain returns:
```
$ virsh start regulus
error: Failed to start domain regulus
error: unsupported configuration: virtio 3d acceleration is not supported
```

Just change the driver back to QXL and disable opengl support to get a working setup again - working, but without OpenGL support.

Guess I'll have to make due with 
```
$ glxinfo -b
1336
```
That's the peak FPS under a spice connection over the network.  The average with glxgears is around 200 fps.

---

### Post by monkeybrain20122 on 2021-09-08
> **TheFu said:**
> 

virgl ....


For virgl, the documentation is terrible and it appears that rebuilding qemu is required.  Cannot tell what releases are supported, which dependencies are necessary, and which hardware should work. Stuff like this is usually tied to specific, high-end, GPUs.  I don't see any mention of GPU hardware.   There is an 18.04 PPA from Stein, but I'm uncomfortable risking all my KVM VMs to just support a single desktop.
Without adding any new software, I attempted to get virt-manager to accept some settings for virgl. Eventually, got passed the errors, but got stuck with
.


It appears to depends on your graphic card. For intel no further work is necessary, works out of the box with virt-manager on Ubuntu 20.04. With Nvidia you need to compile qemu from source since apparently the Nvidia driver doesn't play well with gtk so you need sdl2 but qemu from the repo (Debian) for some reason is not built with it. Also I am not able to start the VM with virt-manager (it can probably done if I figure out how to edit the xml but it appears that the option with sdl is not supported at the moment) but with command line it is fine.

I don't have an amd card.

Also the snap works, so save you time for compiling qemu if you don't mind snap (I mind, so I compiled)

BTW glxgears is not reliable. I have glxgears reporting higher fps in vm than the hosts on some machines which is ridiculous, another member on this forum observed the same. Try something else for benchmarking like unigine-heaven. with Spice/QXL I got average of 5~ 6 fps with low quality, with virlgl 80~100 fps with ultra high quality (on bare metal it is ~130fps)

You keep saying it is not for gaming but apparently you haven't tried. On here supertuxkart and some shooting games are definitely very smooth (there is a mouse/touchpad issuue with some OpenGL/sdl games which appear to be Nvidia specific). With QXL/Spice they are like slide shows. I don't know how it is over a network, but that seems to be a very special use case and involves other factors.

---

### Post by monkeybrain20122 on 2021-09-08
@OP

As said, as far as I know nothing short of gpu passthrough would work for Windows guests and for that you need 2 gpus. There are some blogs and tutorials on "single gpu passthrough" but it sounds very risky. Some people report that their their gpu got permanently stolen by the guest and couldn't pass it back to the host, still others report that after passing the gpu around a bit it just got lost in the ether so neither the host nor the guest have any graphic.So unless you are a pro and have a reasonably recent computer to spare (apparently it doesn't work if hardware is too old) you shouldn't try it. I am neither so I haven't.  

Now there is this cheap and easy way to up your windows guest's opengl version by installing mesa on Windows guests. You'll get opengl3 so some applications that wouldn't run because of missing opengl support would. But there is no boost performance wise and there is no hardware acceleration of any kind (it is software rendering)

[https://thomas.inf3.ch/2019-06-12-opengl-kvm-mesa3d/index.html](https://thomas.inf3.ch/2019-06-12-opengl-kvm-mesa3d/index.html)

---

### Post by TheFu on 2021-09-09
Whenever screwing around with GPU stuff, it is a good idea to have sshd running and know how to ssh into the system so you can put things back from a shell interface.

Installed and played a little super tux kart.  Meh.  There definitely was a performance problem, likely due to spice limits, but also since the VM I used was fairly limited.  It is my normal desktop.

---

### Post by demonenero84 on 2021-09-09
> 
Should we just through away our $500 game library? 

Indeed, they expect you to rebuy your games, and this time you are buying a service instead of a product ( you must be online to play you games :( )
> 
  I still play some Atari 2600 games from my youth.

I have an Atari St in the attic :) But I prefer emulation to play those old games

---

### Post by monkeybrain20122 on 2021-09-09
> **TheFu said:**
> Whenever screwing around with GPU stuff, it is a good idea to have sshd running and know how to ssh into the system so you can put things back from a shell interface.
.

I am not sure how virgl screw with gpu. If things got stuck I just do ctrl+F and click close or kill the terminal, that's it.

The purpose is not to play supertuxkart, it is a way of testing how well virlgl works. You don't care for your use case, you are a system admin so you ssh into your VM, got it, but this is your preference and your way of doing things, others may have other interests and preferences.

---

### Post by TheFu on 2021-09-09
> **monkeybrain20122 said:**
> I am not sure how virgl screw with gpu. If things got stuck I just do ctrl+F and click close or kill the terminal, that's it.

The purpose is not to play supertuxkart, it is a way of testing how well virlgl works. You don't care for your use case, you are a system admin so you ssh into your VM, got it, but this is your preference and your way of doing things, others may have other interests and preferences.

Definitely!  

I'm 100% sold that SPICE isn't the graphics solution for gamers. I'm still looking for "easy" solutions for average people.

---

### Post by demonenero84 on 2021-09-19
So in my free time I did a few tests with Vmware player. Vmplayer is free to use but it is not FOSS, I made a Win XP vm with a virtual GPU, most games I tried tend to work with minor problems, anyway those games that I tried run better with WINE, it is rather pointless to setup a vm if games run better with WINE ( perhaps  for windows users it is a useful option )
Let me know if there are other options for playing old games
Bye :)

---

