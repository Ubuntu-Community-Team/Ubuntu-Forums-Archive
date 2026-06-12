---
title: "HOWTO: RX 5700 XT/RX 5700 with open source drivers on Ubuntu 19.04"
date: 2019-08-30
forum: Tutorials
---

### Post by Claritux on 2019-08-30
I just got my brand new RX 5700 XT and had to do a bit of trial and error to get it up and running, as I couldn't find a complete guide on how to do so. This should most definitely work with the regular RX 5700 as well, but I can't test.

*As for 19.10, the firmware files for Navi did not make it into the final release, but they are included with the first linux-firmware patch, so full support will be enabled after your first system update. The default kernel and mesa has built in support, but I would still recommend installing newer kernels and mesa, as the drivers are still a work in progress.*

First of all the kernel needs to be updated to 5.3 or later. You can get kernel debs from [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/") or do as me and install "[Mainline]("https://github.com/aljex/mainline")", a tool for handling custom kernel updates.
```
sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update && sudo apt -y install mainline
```
Open "Ubuntu Mainline" from applications menu and install the latest 5.3 kernel or disable "Hide unstable and RC releases" in settings and install the latest 5.4rc kernel (recommended).

Next we need newer versions of llvm and mesa. Luckily everything is neatly packaged for us in [Oibaf's PPA]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers").
```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt update && sudo apt -y upgrade
```

Finally we download the proprietary [firmware]("https://people.freedesktop.org/~agd5f/radeon_ucode/navi10/") files for Navi 10 and place them in /lib/firmware/amdgpu
```
wget -r -np -R "index.html*" https://people.freedesktop.org/~agd5f/radeon_ucode/navi10/
cd people.freedesktop.org/~agd5f/radeon_ucode/navi10/
sudo cp navi* /lib/firmware/amdgpu
```

**Optional**: If you have an AMD Freesync capable monitor you can enable Freesync in the amdgpu driver. Note that this is very unstable at the moment, at least for 144hz monitors like mine. You can check if your monitor is capable of Freesync by running *xrandr --props* and look for the line that says *vrr_capable: 1*.
This option does unfortunately only work in X on single monitor setups, and not in Wayland.
```
sudo nano /usr/share/X11/xorg.conf.d/10-amdgpu.conf
```
Add the line *Option "VariableRefresh" "true"*, so it looks something like this:
```
Section "OutputClass"
        Identifier "AMDgpu"
        MatchDriver "amdgpu"
        Driver "amdgpu"
        Option "VariableRefresh" "true"
EndSection
```
You can verify that it's enabled (after rebooting) using:
```
grep -w VariableRefresh ~/.local/share/xorg/Xorg.0.log
```
To disable, simply change the VariableRefresh option to *false*.

*Reboot and enjoy!*

**_Uninstall guide:_**
Remove user installed kernels using mainline. You will have to boot an earlier kernel version before doing so.

Remove Oibaf's PPA and downgrade packages.
```
sudo apt install ppa-purge
sudo ppa-purge ppa:oibaf/graphics-drivers
```

Remove firmware files. **This is not recommended for 19.10 onwards**, as the firmware files is now part of Ubuntu's default *linux-firmware* package.
```
sudo rm /lib/firmware/amdgpu/navi*
```

---

### Post by Badouken on 2019-09-01
Can confirm. I ran these steps and now my card is being recognized. Thank you!

---

### Post by montfox on 2019-09-03
I created an account just to note that this absolutely works on my 5700 (not the XT)! Windows 10 was giving me a bluescreen if I had more than one application open, so I decided to download Ubuntu bungie and follow these steps! Although I had issues building mainline with these steps, I just used ukuu (You can still get it free on the git release page)

---

### Post by dlapik on 2019-09-07
The only solution that works for RX 5700XT, thank you! However please be aware that kernel 5.3rc7 doesn't work, only 5.3rc6. rc7 fails to load navi FW and consequently nothing is visible on the screen.

---

### Post by coffeecat on 2019-09-07
Not a request for help.

*Thread moved to **Tutorials**.*

@Claritux, thank you for posting this howto. Please see the [Tutorials Guidelines sticky](https://ubuntuforums.org/showthread.php?t=2143602)

---

### Post by Claritux on 2019-09-09
> **coffeecat said:**
> Not a request for help.

*Thread moved to **Tutorials**.*

@Claritux, thank you for posting this howto. Please see the [Tutorials Guidelines sticky](https://ubuntuforums.org/showthread.php?t=2143602)

Will do! Thanks for moving the thread!

---

### Post by Claritux on 2019-09-09
> **dlapik said:**
> The only solution that works for RX 5700XT, thank you! However please be aware that kernel 5.3rc7 doesn't work, only 5.3rc6. rc7 fails to load navi FW and consequently nothing is visible on the screen.
That's odd. 5.3rc7 works fine with me. 5.3rc8 is out now, maybe give that a go!

---

### Post by Claritux on 2019-09-09
> **montfox said:**
> I created an account just to note that this absolutely works on my 5700 (not the XT)! Windows 10 was giving me a bluescreen if I had more than one application open, so I decided to download Ubuntu bungie and follow these steps! Although I had issues building mainline with these steps, I just used ukuu (You can still get it free on the git release page [https://github.com/teejee2008/ukuu/releases](https://github.com/teejee2008/ukuu/releases)),
I didn't want to include Ukuu in the tutorial, as the original author has discontinued his original project and made it proprietary, but I'm happy you got it to work! :)
Edit: Mainline has a PPA now. I will update the tutorial with that. I recommend switching over, as the GitHub version of Ukuu is unmaintained.

---

### Post by montfox on 2019-09-10
> **Claritux said:**
> I didn't want to include Ukuu in the tutorial, as the original author has discontinued his original project and made it proprietary, but I'm happy you got it to work! :)
Edit: Mainline has a PPA now. I will update the tutorial with that. I recommend switching over, as the GitHub version of Ukuu is unmaintained.

Added to my PPA, but package manager is unable to find mainline

```
Hit:4 http://ppa.launchpad.net/cappelikan/ppa/ubuntu bionic InRelease

sudo apt install mainline
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mainline


 
```

---

### Post by Claritux on 2019-09-11
It seems the PPA had a build failiure for the 18.04 package. You can try running the 19.04 .deb until it's updated:
[https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa/+files/mainline_1.0.1-0~201909030023~ubuntu19.04.1_amd64.deb](https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa/+files/mainline_1.0.1-0~201909030023~ubuntu19.04.1_amd64.deb)

---

### Post by l-beto88 on 2019-09-15
Marry me dude. Thank you

---

### Post by ludo-surfer on 2019-09-16
Thank you man its working perfectly !

---

### Post by jorne66 on 2019-09-20
I tried installing using this tutorial but now my monitor doesn't get detected anymore and when i try to change the resolution i only get a message: unknown display. If i try the tutorial up until the firmware files it does recognize my monitor but then every time i try to open a youtube video or something similar i get a black screen for 2 seconds and a bit of screen tear. is it possible that i need to use other firmware files?

---

### Post by Claritux on 2019-09-21
> **jorne66 said:**
> I tried installing using this tutorial but now my monitor doesn't get detected anymore and when i try to change the resolution i only get a message: unknown display. If i try the tutorial up until the firmware files it does recognize my monitor but then every time i try to open a youtube video or something similar i get a black screen for 2 seconds and a bit of screen tear. is it possible that i need to use other firmware files?

Very hard for me to tell what might be causing that. Those are definitely the firmware files you need if you have a 5700 or 5700 XT. Did you try setting it up in a different way before? I ran into some issues when I tried to use padoka PPA instead of Oibaf's initially. Having both could cause some issues. Did you install the amdgpu-pro driver before trying this? Are you switching from an nvidia card and have the nvidia proprietary driver installed?
Try removing everything: nvidia-driver (sudo apt purge nvidia*), amdgpu-pro (sudo amdgpu-pro-uninstall), padoka PPA (sudo ppa-purge ppa:paulo-miguel-dias/mesa), uninstall all using my uninstall guide and then run the tutorial again from a fresh state.

---

### Post by Claritux on 2019-09-21
> **l-beto88 said:**
> Marry me dude. Thank you

Only if you buy me a top of the line navi12 GPU when that comes out ;)

---

### Post by o462 on 2019-10-05
Works fine with 5700 XT 50th Anniversary ;)

---

### Post by small-pony on 2019-10-08
Hi. I have RX 5700 followed your instructions. Tried to install League Of legends with lutris but running at 2-5 fps.. When I run **glxinfo | grep -i opengl **i get this:
> OpenGL vendor string: X.OrgOpenGL renderer string: AMD NAVI10 (DRM 3.33.0, 5.3.5-050305-generic, LLVM 9.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.3.0-devel (git-6f26eae 2019-10-08 disco-oibaf-ppa)
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5 (Compatibility Profile) Mesa 19.3.0-devel (git-6f26eae 2019-10-08 disco-oibaf-ppa)
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.3.0-devel (git-6f26eae 2019-10-08 disco-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
Can someone help?

---

### Post by Claritux on 2019-10-15
> **small-pony said:**
> Hi. I have RX 5700 followed your instructions. Tried to install League Of legends with lutris but running at 2-5 fps.. When I run **glxinfo | grep -i opengl **i get this:

Can someone help?

I have no experience with running Lutris, but have you tried using d9vk for enabling Vulkan instead of OpenGL? There's also Gallium Nine for running DX9 games practically natively. Drivers are still somewhat unstable so some games might have issues. The 5.4rc kernels has included many fixes for navi/amdgpu, so maybe try that.

---

### Post by lcsavb on 2019-10-17
Claritux,

Thank you so much. I've followed the steps and it's working without any issues.

Lucas

---

