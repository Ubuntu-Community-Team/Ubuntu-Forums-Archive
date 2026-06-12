---
title: "nVidia Drivers 304.51"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-09-25
There is a new nVidia graphics driver in Xorg-edgers PPA: 304.51

---

### Post by Harry33 on 2012-09-25
> **VinDSL said:**
> There is a new nVidia graphics driver in Xorg-edgers PPA: 304.51

Right, got it.
This is a new certified release version.
Works pretty well.
Here are the release higlights:

> 

[LIST]
[*]Added       support for the new Quadro Sync board for Quadro Kepler  GPUs. See the  "Configuring Frame Lock and Genlock" chapter in the  README   for details.
[*]Fixed       an X server crash on X.Org xserver 1.13 when it is compiled without support for  DRI2.
[*]Fixed       a regression that broke color controls on older X servers.
[*]Fixed       a bug that sometimes caused the display layout area of  the nvidia-settings  control panel to be laid out incorrectly.
[*]Fixed       a bug that prevented panning from working correctly  after a modeswitch on some X  servers with support for cursor  constraining.
[*]Gamma       ramp and colormap adjustments now apply correctly when  screen transformations such  as rotation and keystone correction are in  use.
[*]Fixed       RandR per-CRTC gamma persistence across modeswitches and VT-switches.
[*]Fixed       a bug that caused the X server to sometimes hang in response to input events.
[*]Fixed       a reduction in rendering performance for core X11  rendering on certain GPUs that  occurred in the 290.series of releases.
[*]Fixed       a bug that prevented PowerMizer from working correctly  on some boards with  GDDR5 memory, such as some GeForce GT 240 SKUs.
[*]Fixed       a bug that caused OpenGL applications to not animate  properly when a rotation or a  transformation was applied on some older X   server versions.
[*]Enabled       FXAA with Unified Back Buffers.
[*]Fixed       a bug that prevented the "Reset Hardware Defaults"  button in the Display Settings page of nvidia-settings from being  activated.
[/LIST]


---

### Post by cecilpierce on 2012-09-25
Hmmm!  X server, X server, X server, no Wayland help yet...Geez -:guitar:

---

### Post by funicorn on 2012-09-25
I wonder whether nvidia driver can work with Wayland.

---

### Post by bird1500 on 2012-09-25
> **funicorn said:**
> I wonder whether nvidia driver can work with Wayland.
No, and Nvidia said it has no plans to do so. For now.

But it will eventually support it when Wayland makes enough progress on the Linux front, which should be within like 2 years.

Nvidia also plans to support EGL (which is a prerequisite for Wayland support) on desktop Linux, so me thinks it will support Wayland within a few years. Phoronix confirmed this [here]("http://www.phoronix.com/scan.php?page=news_item&px=MTE5MTk").

---

### Post by cecilpierce on 2012-09-25
> **funicorn said:**
> I wonder whether nvidia driver can work with Wayland.

It works some what inside of X but not from start and its buggy and slow.
I got an email from nvidia support and they said when it gets some of the bugs out it MIGHT think about support...:p

---

### Post by Dr.Paneas on 2012-09-25
It doesn't change that much. It's pretty much an update version of beta 304.48 in stable branch.

btw, the guide: [http://ubuntuxtreme.com/howto/how-to-install-nnvidia-304-51-drivers-in-ubuntu/](http://ubuntuxtreme.com/howto/how-to-install-nnvidia-304-51-drivers-in-ubuntu/)

---

### Post by VinDSL on 2012-09-25
> **Dr.Paneas said:**
> It doesn't change that much. It's pretty much an update version of beta 304.48 in stable branch.[...]
That said, it runs great on ancient iron (see sig).


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-sep-2012-1.png")[/INDENT]


Lots of stuff running in the background -- Descent times for a GeForce 7600GT -- And, nothing is stumbling... ;)

---

### Post by funicorn on 2012-09-25
They should be careful. Years ago when Nvidia decided to support linux and started development, it took long for them to adapt to linux Xframework and eventually it's proved that's impossible. Now its WayLand. 

> **cecilpierce said:**
> It works some what inside of X but not from start and its buggy and slow.
I got an email from nvidia support and they said when it gets some of the bugs out it MIGHT think about support...:p

---

### Post by MikeCyber on 2012-09-26
Why should we switch to wayland?

Why should I use the ppa? Would I run into problems by simply downloading from nvidia? Simply running the installer should ask for an update of the installed driver.

Thanks

---

### Post by effenberg0x0 on 2012-09-26
> **MikeCyber said:**
> Why should we switch to wayland?

Why should I use the ppa? Would I run into problems by simply downloading from nvidia? Simply running the installer should ask for an update of the installed driver.

Thanks

About Wayland: X is old, 25+ years old actually. Things have changed greatly in this period: Hardware, software, OSs, programming languages, coding style, developers and users expectations and demands. Wayland is supposed to be a step towards modernization. See the [wiki]("http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)").

About xorg-edgers ppa: Read [this]("https://launchpad.net/~xorg-edgers/+archive/ppa"). It's just another resource for testers of new software. If you are involved in testing Ubuntu you may use it or not, depending on your testing preferences. It's up to you. Keep in mind that once you add the PPA to your sources you're using the whole of it (all of it's packages will be available when you update&upgrade). 

Downloading from Nvidia: No, normally you shouldn't run into any problem. The installer will ask you if it's OK to remove the previous version and install the new one. That's the method I use to install and update Nvidia in testing. I prefer to not use alternative sources in my testing installs. If the drivers need (depend) on new releases of other packages (like xorg*), my install will be broken and it's up to me to check for broken depends and fix it. I prefer to work like that.

It all goes down to whether you are testing Ubuntu Development Releases or not. Ordinary users (not testers) that stick to the current releases of Ubuntu and require a stable and reliable machine don't have to worry about any of this. But these topics are hugely relevant to testers. 

Regards,
Effenberg

---

### Post by kyleabaker on 2012-09-26
I can't remember if I've got 304.48 or 304.51 installed at home, but has anyone noticed with a recent update that _the hidden dock does NOT reappear anymore_ when you mouse over to the left edge of the screen? I remember this happening a long while back, but it was fixed since then.

---

### Post by kyleabaker on 2012-09-26
> **kyleabaker said:**
> I can't remember if I've got 304.48 or 304.51 installed at home, but has anyone noticed with a recent update that _the hidden dock does NOT reappear anymore_ when you mouse over to the left edge of the screen? I remember this happening a long while back, but it was fixed since then.

Should I reopen this bug?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/937792](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/937792)

---

### Post by robtygart on 2012-09-26
> **Dr.Paneas said:**
> It doesn't change that much. It's pretty much an update version of beta 304.48 in stable branch.

btw, the guide: [http://ubuntuxtreme.com/howto/how-to-install-nnvidia-304-51-drivers-in-ubuntu/](http://ubuntuxtreme.com/howto/how-to-install-nnvidia-304-51-drivers-in-ubuntu/)

I used this, and choose "beta Proprietary drivers" when it restarted, it came back were I had no effects or use of the keyboard unless I Alt+F2 and I could access the command line.

I just did a reinstall, I am using 304.48 again.

---

### Post by kyleabaker on 2012-10-02
> **kyleabaker said:**
> Should I reopen this bug?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/937792](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/937792)

Quick update. If you're seeing this bug as well, please leave your feedback here...
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1060511](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1060511)

---

