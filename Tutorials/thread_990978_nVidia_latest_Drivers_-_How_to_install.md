---
title: "nVidia latest Drivers - How to install"
date: 2008-11-23
forum: Tutorials
---

### Post by Kosimo on 2008-11-23
*Edit September 1 2010*: Latest nVidia 256.xx (STABLE) **[COLOR="Red"]256.53[/COLOR]** Drivers:  [ 32 Bit ]("http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html") . [64 Bit]("http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html")

*Edit September 9 2010*: Latest nVidia 260.xx (BETA) **[COLOR="Red"]260.19.04[/COLOR]** Drivers:  [ 32 Bit ]("ftp://download.nvidia.com/XFree86/Linux-x86/260.19.04/") . [64 Bit]("ftp://download.nvidia.com/XFree86/Linux-x86_64/260.19.04/")

*Edit March 18 2010*: Latest nVidia 195.xx **OpenGL 3.3** (STABLE) **[COLOR="Red"]195.36.07.03[/COLOR]** Drivers:  [ 32 Bit ]("http://developer.download.nvidia.com/opengl/3.3/linux/NVIDIA-Linux-x86-195.36.07.03-pkg1.run") . [64 Bit]("http://developer.download.nvidia.com/opengl/3.3/linux/NVIDIA-Linux-x86_64-195.36.07.03-pkg2.run")




_**How to install nVidia drivers in Ubuntu:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR="Red"]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR="Red"]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR="Red"]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR="Red"]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```

**[COLOR="Red"]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```

**[COLOR="Red"]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR="Red"]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR="Red"]7[/COLOR])** Then restart your computer   ```
sudo reboot
```

**[COLOR="Red"]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: ```
sudo sh ./Nxxx --uninstall
```
or
```
sudo nvidia-uninstall
```

**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


**[COLOR="Red"]If you want to have an automated procedure, that keeps you updated with the latest version, you can use the X-Updates.[/COLOR]**

[HERE]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")


_**Legacy Drivers**_


GeForce 5 series GPUs **[COLOR="Red"]173.14.25 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_173.14.25.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_173.14.25.html")


GeForce 2 through GeForce 4 series **[COLOR="Red"]96.43.16 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_96.43.16.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_96.43.16.html")


Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR="Red"]71.86.13 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_71.86.13.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_71.86.13.html")


*note*: Legacy drivers are being updated as well. (Latest update: February 15, 2010)


Good luck ;)

---

### Post by Pogeymanz on 2008-11-23
What card are you using? How was 2D performance affected?

---

### Post by Kosimo on 2008-11-23
> **Pogeymanz said:**
> What card are you using? How was 2D performance affected?

GeForce 8400m GT 128MB
2D performance has a big boost compared to 177.

---

### Post by xravexheavenx on 2008-11-23
> **Kosimo said:**
> GeForce 8400m GT 128MB
2D performance has a big boost compared to 177.

Agreed.

---

### Post by graabein on 2008-11-23
My graphics are all screwed up. Starting in low-res each time. Hope this driver fixes that. I've got a GeForce 6600 GT card. Anyone else had any problems with that card?

---

### Post by kevin11951 on 2008-11-23
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. 
Now, it's been almost a week that I've installed latest BETA drivers 180.06 from nvidia witch includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability. Compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues also with compiz. In one word. IMPRESSIVE.
I hope that this is not the final step but only the first step of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance.   I would like to ask you guys if anyone else is using 180.06 and know how you feel with them.

where exactly do you get this driver?

EDIT: Nevermind, i found it here: [http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by Kosimo on 2008-11-23
> **kevin11951 said:**
> where exactly do you get this driver?

From nVidia official webpage. Follow this [link]("http://www.nvidia.com/object/linux_display_ia32_180.06.html")

---

### Post by Kosimo on 2008-11-23
> **graabein said:**
> My graphics are all screwed up. Starting in low-res each time. Hope this driver fixes that. I've got a GeForce 6600 GT card. Anyone else had any problems with that card?

I don't have this card... Which Drivers version are you currently using?

---

### Post by Polygon on 2008-11-23
the 180 series of drivers are great for me in linux (9800gtx).....but cause very frequent bsod's for me in windows. Irony anyone?

---

### Post by Valok on 2008-11-23
Quick question, is there a way I can find out what video card I'm using within Ubuntu?  I know its some 8800 but I don't remember if its GT, GTS, or some other crappy naming system Nvidia came out with.

---

### Post by Kosimo on 2008-11-23
> **Valok said:**
> Quick question, is there a way I can find out what video card I'm using within Ubuntu?  I know its some 8800 but I don't remember if its GT, GTS, or some other crappy naming system Nvidia came out with.

Actually if you have any nVidia drivers, just go to the settings-manager and it'll tell you exactly witch card are you currently using.

---

### Post by RATM_Owns on 2008-11-23
Mine says GeForce 6150SE nForce 430

And there's a GeForce driver and a nForce driver. :P

EDIT: Nevar mind. :P

---

### Post by steveneddy on 2008-11-23
> **Kosimo said:**
> I don't have this card... [COLOR=Blue]**Witch**[/COLOR] Drivers version are you currently using?

[COLOR=Blue]**which**[/COLOR] drivers

witch is an ugly old woman that eats children.

---

### Post by Kosimo on 2008-11-23
> **steveneddy said:**
> [COLOR=Blue]**which**[/COLOR] drivers

witch is an ugly old woman that eats children.

Sorry dude... English is not my native language and I'm trying to do my best...

---

### Post by bapoumba on 2008-11-23
> **Kosimo said:**
> Sorry dude... English is not my native language and I'm trying to do my best...

I can relate to that :)

A smiley would have been appreciated, steveneddy..

---

### Post by Valok on 2008-11-23
> **Kosimo said:**
> Actually if you have any nVidia drivers, just go to the settings-manager and it'll tell you exactly witch card are you currently using.

Where is the settings manager?  Tried typing it into a terminal but it said 'command not found'

---

### Post by eragon100 on 2008-11-23
Just so you now, 180.08 is already available. It adds openGL 3.0 support.

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.08/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.08/) (64-bit)

[ftp://download.nvidia.com/XFree86/Linux-x86/180.08/](ftp://download.nvidia.com/XFree86/Linux-x86/180.08/) (32-bit)

---

### Post by Ub1476 on 2008-11-23
> **Valok said:**
> Where is the settings manager?  Tried typing it into a terminal but it said 'command not found'

You need to install it from Synaptic. "nvidia-settings" or something. However, typing "lspci | grep VGA" should do the trick too. :)

Hm, gotta install this driver now. Hope it's improvments for KDE 4 too.. By the way, what's the difference between 2d and 3d?

---

### Post by Kosimo on 2008-11-23
> **Ub1476 said:**
> You need to install it from Synaptic. "nvidia-settings" or something. However, typing "lspci | grep VGA" should do the trick too. :)

Hm, gotta install this driver now. Hope it's improvments for KDE 4 too.. By the way, what's the difference between 2d and 3d?

Are you serious?

3D applications, google earth, 3D Games, etc etc...

2D, Compiz, video, etc...

---

### Post by oedipuss on 2008-11-23
> **Kosimo said:**
>  which includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability. Compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues also with compiz. 


What video player are you using? I thought there wasn't any that implemented purevideo yet.

---

### Post by eragon100 on 2008-11-23
> **Kosimo said:**
> Are you serious?

3D applications, google earth, 3D Games, etc etc...

2D, Compiz, video, etc...

Compiz was still a **3d** application last time I checked :wink:

That's also why Compiz doesn't work with the nv driver.

---

### Post by Kosimo on 2008-11-23
> **oedipuss said:**
> What video player are you using? I thought there wasn't any that implemented purevideo yet.

Actually if you want to use PureVideo Hardware accelerated you need to do some tweaks. There is a topic that talks about that:  [Here]("http://ubuntuforums.org/showthread.php?t=984198&highlight=180.06")

---

### Post by Kosimo on 2008-11-23
> **eragon100 said:**
> Compiz was still a **3d** application last time I checked :wink:

That's also why Compiz doesn't work with the nv driver.

It have 3D effects, but I like to consider it a 2D window management. When I'm talking about 2D performance I mean how my videocard manages to minimise, move, resize windows when compiz enabled.

---

### Post by eragon100 on 2008-11-23
> **Kosimo said:**
> It have 3D effects, but I like to consider it a 2D window management. When I'm talking about 2D performance I mean how my videocard manages to minimise, move, resize windows when compiz enabled.

Well from what I have heard the speed problems with KDE4, and 2d in general, have been (almost) resolved :wink:

---

### Post by Martje_001 on 2008-11-23
> **Valok said:**
> Where is the settings manager?  Tried typing it into a terminal but it said 'command not found'
sudo lshw -C video xD

---

### Post by lzfy on 2008-11-23
> **eragon100 said:**
> Well from what I have heard the speed problems with KDE4, and 2d in general, have been (almost) resolved :wink:

I can confirm this :) KDE works great with the new beta drivers.

---

### Post by aktiwers on 2008-11-23
Can I use it with my 9800GTX ?

---

### Post by Kosimo on 2008-11-23
> **aktiwers said:**
> Can I use it with my 9800GTX ?

yes

---

### Post by aktiwers on 2008-11-23
> **Kosimo said:**
> yes
Thanks, because I couldn't last time I checked.. gonna install it now :P

---

### Post by Ub1476 on 2008-11-23
> **Kosimo said:**
> Are you serious?

3D applications, google earth, 3D Games, etc etc...

2D, Compiz, video, etc...

Yep, we all learn it someday. :)

It's just that Compiz looks so 3D that I just needed a clarification.

---

### Post by aktiwers on 2008-11-23
Runs great! Thanks!

Here is a small HOWTO install it.

Download the driver.
[http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html) (64bit)
[http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html) (32bit)

Open terminal and type:
```
sudo chmod +x NVIDIADRIVER
```Where NVIDIADRIVER is the name of the driver file.

Hit CTRL+ALT+F1
Login

type:
```
sudo /etc/init.d/gdm stop
```To stop GDM and run the installer:
```
sudo sh NVIDIADRIVER
```Again where NVIDIADRIVER is the file name of the driver.

When done, Reboot:
```
sudo reboot
```

---

### Post by happysmileman on 2008-11-23
I'm using the 96.43.09 driver and not so happy with it.

Performance wise it's fine, but on KDE4 I can only use the desktop effects with XRender, not OpenGL, since I've come to intrepid and used this driver. While the speed is ok on XRender for the small amount of settings I use, some effects don't work at all and some have serious bugs.

For example "Mouse Marks" doesn't work at all for me, and with Desktop effects enabled with XRender the nicklist and statusbar in Konversation go completely blank (apparently rendering issue in the new drivers with QT3 applications)

---

### Post by Kosimo on 2008-11-23
> **aktiwers said:**
> Runs great! Thanks!

Here is a small HOWTO install it.

Download the driver.
[http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html) (64bit)
[http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html) (32bit)

Open terminal and type:
```
sudo chmod +x NVIDIADRIVER
```Where NVIDIADRIVER is the name of the driver file.

Hit CTRL+ALT+F1
Login




type:
```
sudo /etc/init.d/gdm stop
```To stop GDM and run the installer:
```
sudo sh NVIDIADRIVER
```Again where NVIDIADRIVER is the file name of the driver.

When done, Reboot:
```
sudo reboot
```


Looking forward for your small review about performance and stability ;)

---

### Post by Mr. Picklesworth on 2008-11-23
Can anyone confirm whether NVidia's installer there sorts out the DKMS stuff? I would be sad if I confused it :(

---

### Post by Valok on 2008-11-23
For some reason (and this happens to me all the time) when I type in 'sudo chmod +x NAME OF DRIVER FILE' it returns that it cannot find the file or that such a file doesn't exist.  

I know I typed it in right because I copy pasted the name right from the properties.  How come this is still giving me this error?

And when I follow the directions on the Nvidia page I get an error saying that it cannot open the .run file.

---

### Post by aktiwers on 2008-11-23
> **Valok said:**
> For some reason (and this happens to me all the time) when I type in 'sudo chmod +x NAME OF DRIVER FILE' it returns that it cannot find the file or that such a file doesn't exist.  

I know I typed it in right because I copy pasted the name right from the properties.  How come this is still giving me this error?

And when I follow the directions on the Nvidia page I get an error saying that it cannot open the .run file.

Did you download the file to your Desktop?
Then remember to go there first.
```
cd Desktop
```Then type:
```
sudo chmod +x NVIDIA<hit tab key here>
```And it should autocomplete the driver name.

Edit: Remember that the Terminal is CaSeSenSitiVe

---

### Post by pelle.k on 2008-11-23
```
sudo chmod +x NVIDIA<hit tab key here>
```
Just "sh" it! (no need to chmod it first)

```
sudo sh NVIDIA<hit tab key here>
```

Also, you'be wise to uninstall "nvidia-glx-177" and "nvidia-settings" first.
You need to have "build-essential" and "libx11-dev" and "linux-headers-generic" installed as well.

Lastly, when you're done testing, uninstall the nvidia driver with appending "--uninstall" on the nvidia binary installer.

---

### Post by eragon100 on 2008-11-23
> **happysmileman said:**
> I'm using the 96.43.09 driver and not so happy with it.



That driver is ancient. Really ancient. Download the **180.08** driver that I mentioned above, it's about 1.5 years newer :wink:

---

### Post by FuturePilot on 2008-11-23
> **eragon100 said:**
> That driver is ancient. Really ancient. Download the **180.08** driver that I mentioned above, it's about 1.5 years newer :wink:

That might not be an option if they have an older card. 180.08 will not support it.

---

### Post by eragon100 on 2008-11-23
> **FuturePilot said:**
> That might not be an option if they have an older card. 180.08 will not support it.

You are right, but the legacy driver gets updates too.
The 180.X series dropped support for GeForce fx cards, so you need to have a geforce 6 series card or newer to install said driver :(

(I have a 512 MB GeForce 8 8600 GT and the driver, and card, works fine.)

---

### Post by Kosimo on 2008-11-23
> **eragon100 said:**
> That driver is ancient. Really ancient. Download the **180.08** driver that I mentioned above, it's about 1.5 years newer :wink:

that driver you mentioned 180.08 has two .run  Which one do I have to download? 

Thanks

---

### Post by eragon100 on 2008-11-23
> **Kosimo said:**
> that driver you mentioned 180.08 has two .run  Which one do I have to download? 

Thanks

The one with the highest number on the end, because it has the most extra features. For example, on a 64-bit system, you should *not* install the pkg0 drivers, because they don't contain 32-bit open-gl compatibility libraries, meaning that 32-bit 3d games wouldn't run on your 64-bit system.

---

### Post by Kosimo on 2008-11-23
> **eragon100 said:**
> The one with the highest number on the end, because it has the most extra features. For example, on a 64-bit system, you should *not* install the pkg0 drivers, because they don't contain 32-bit open-gl compatibility libraries, meaning that 32-bit 3d games wouldn't run on your 64-bit system.

How about if I'm using 32bit os?

---

### Post by Kosimo on 2008-11-23
After reading [this post]("http://forums.nvidia.com/index.php?showtopic=82194") I guess that now it's better to keep using 180.06 as 180.08 are not CUDA compatible and not even public.

---

### Post by eragon100 on 2008-11-23
> **Kosimo said:**
> How about if I'm using 32bit os?

Like I said, the one with the highest number on the end (should be pkg1.run) .

---

### Post by Mr. Picklesworth on 2008-11-23
Okay I got it going. It was a teeny bit troublesome, but after the fact I guess it is kind of cool that a whole new graphics driver magically kicked in without a full reboot :)

Anyhow... first impressions:

OMG the ugly artifacting is gone! The expanding semi-transparent effect on panel launchers actually looks right, GNOME-Do's popup doesn't flicker when it appears, menus feel right and everything feels smooth now. Nice work, Nvidia :)

Is that a super subtle fading effect I see on popup menus now, with Metacity in compositing mode?
Edit: Nope, I'm just crazy.

---

### Post by zmjjmz on 2008-11-23
Nice to hear this, but they're still not OSS right?

---

### Post by eragon100 on 2008-11-23
> **zmjjmz said:**
> Nice to hear this, but they're still not OSS right?

No they aren't. It's *terrible* :rolleyes:

---

### Post by happysmileman on 2008-11-23
> **eragon100 said:**
> That driver is ancient. Really ancient. Download the **180.08** driver that I mentioned above, it's about 1.5 years newer :wink:

It's not ancient, it was released last month, it's just for much older cards than the 180.08.

It's the newest driver for the GeForce4 series AFAIK.

---

### Post by mips on 2008-11-23
> **Kosimo said:**
> After reading [this post]("http://forums.nvidia.com/index.php?showtopic=82194") I guess that now it's better to keep using 180.06 as 180.08 are not CUDA compatible and not even public.

Do you actually use CUDA? I do not think there is more than 0.01% in this forum that would use CUDA.

CUDA is a C language environment/compiler to program GPUs to in effect perform the functions of a CPU.

[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

---

### Post by blithen on 2008-11-23
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. 
Now, it's been almost a week that I've installed latest BETA drivers 180.06 from nvidia which includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability. Compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues also with compiz. In one word. IMPRESSIVE.
I hope that this is not the final step but only the first step of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance.   I would like to ask you guys if anyone else is using 180.06 and know how you feel with them.

Welp...I'm gonna try it. here's hoping to no crash!
EDIT: I should really know this by now, by how on earth do I kill the X Server?

---

### Post by mips on 2008-11-23
> **eragon100 said:**
> That driver is ancient. Really ancient. Download the **180.08** driver that I mentioned above, it's about 1.5 years newer :wink:

He has a NVidia GeForce 440 MX which does not work with 180.xx drivers.

---

### Post by Yes on 2008-11-23
> **blithen said:**
> Welp...I'm gonna try it. here's hoping to no crash!
EDIT: I should really know this by now, by how on earth do I kill the X Server?

ctrl+alt+backspace

---

### Post by eragon100 on 2008-11-23
> **Yes said:**
> ctrl+alt+backspace

that restarts the x-server.

You must:

1: press ctrl-alt-F1

2: login at the prompt

3: type "sudo /etc/init.d/gdm stop"

4: type in your password.

That will kill the x-server, be sure to save any documents or stuff you have open in gnome first :wink: .

---

### Post by aktiwers on 2008-11-23
Actually after using it for a couple of hours I think its a little choppy. 
It runs great for 10-20 mins then gives a small chop that even stops my musik for 1 sec. Then it goes back to normal. 

I am already thinking about going back to 177 again.

Somehow reloading and switching between tabs in firefox has become a lot slower too after I install the driver.

EDIT: Okay just installed the 08 version and it seams to run a lot better (only tried it for 5 mins though)

---

### Post by CholericKoala on 2008-11-23
Installed, seems to work well.  Smoothish.

---

### Post by Vadi on 2008-11-23
Don't suppose anyone have a .deb for this?

If I isntall the driver from nvidia, next time ubuntu upgrades the driver, this will all break.

---

### Post by Kosimo on 2008-11-23
> **Vadi said:**
> Don't suppose anyone have a .deb for this?

If I isntall the driver from nvidia, next time ubuntu upgrades the driver, this will all break.

That doesn't happen anymore  (if you use intrepid) :)
You can install those drivers, and even if kernel gets an update you'll still be able to boot

---

### Post by ad_267 on 2008-11-23
> **lzfy said:**
> I can confirm this :) KDE works great with the new beta drivers.

Does this fix the bug where OpenOffice would make everything go crazy? This one: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/226833](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/226833)

KDE was useless to me because of that.

---

### Post by Vadi on 2008-11-23
> **Kosimo said:**
> That doesn't happen anymore  (if you use intrepid) :)
You can install those drivers, and even if kernel gets an update you'll still be able to boot

Oh? Well thank you then, I will give them a try.

---

### Post by FuturePilot on 2008-11-23
> **Vadi said:**
> Don't suppose anyone have a .deb for this?

If I isntall the driver from nvidia, next time ubuntu upgrades the driver, this will all break.

> **Kosimo said:**
> That doesn't happen anymore  (if you use intrepid) :)
You can install those drivers, and even if kernel gets an update you'll still be able to boot

Not quite. Next time Ubuntu updates the kernel it won't break. But next time Ubuntu updates the driver it will most likely break. The Ubuntu driver package places some libraries and files in different places than the Nvidia installer does. Installing the driver using the Nvidia installer and then updating it with the Ubuntu package will probably break something.

---

### Post by Kosimo on 2008-11-23
> **FuturePilot said:**
> Not quite. Next time Ubuntu updates the kernel it won't break. But next time Ubuntu updates the driver it will most likely break. The Ubuntu driver package places some libraries and files in different places than the Nvidia installer does. Installing the driver using the Nvidia installer and then updating it with the Ubuntu package will probably break something.

From ubuntu 8.10 release notes:

> DKMS

DKMS (by Dell) is included in Ubuntu 8.10, allowing kernel drivers to be automatically rebuilt when new kernels are released. This makes it possible for kernel package updates to be made available immediately without waiting for rebuilds of driver packages, and without third-party driver packages becoming out of date when installing these kernel updates. 

---

### Post by FuturePilot on 2008-11-23
> **Kosimo said:**
> From ubuntu 8.10 release notes:

Yes, DKMS only deals with the kernel modules. It doesn't do anything with the driver libraries. You are correct that updating the **kernel** won't break anything, but updating the **driver** from two different sources, Nvidia installer and the Ubuntu package, can cause breakage.

---

### Post by Vadi on 2008-11-23
Oh yeah. So it's the same thing then.

I'll wait :|

---

### Post by Kosimo on 2008-11-23
> **FuturePilot said:**
> Yes, DKMS only deals with the kernel modules. It doesn't do anything with the driver libraries. You are correct that updating the **kernel** won't break anything, but updating the **driver** from two different sources, Nvidia installer and the Ubuntu package, can cause breakage.

So we're talking in a scenario where the user have nvidia drivers installed (manually) and then it also installs drivers from an update?

---

### Post by liquidfunk on 2008-11-23
Does this add anything to games running within Wine?

---

### Post by Kosimo on 2008-11-23
> **liquidfunk said:**
> Does this add anything to games running within Wine?

Wine uses OpenGL which is managed by the videocard using it's drivers.
So the answer is yes. Totally.

---

### Post by FuturePilot on 2008-11-23
> **Kosimo said:**
> So we're talking in a scenario where the user have nvidia drivers installed (manually) and then it also installs drivers from an update?

Yes. For example, someone install the driver manually but then later decides to go back to the Ubuntu package, that could possibly cause problems. The Ubuntu driver packages has certain symlinks that the Nvidia installer can break.

---

### Post by Kosimo on 2008-11-23
> **FuturePilot said:**
> Yes. For example, someone install the driver manually but then later decides to go back to the Ubuntu package, that could possibly cause problems. The Ubuntu driver packages has certain symlinks that the Nvidia installer can break.

Ok, now I understand you.
Well.. In that case the only thing he needs to do is uninstalling the current version and then everything is fine.

---

### Post by Mr. Picklesworth on 2008-11-23
> **Kosimo said:**
> Ok, now I understand you.
Well.. In that case the only thing he needs to do is uninstalling the current version and then everything is fine.

...and just so you don't end up using the same driver version for eternity, subscribe to this bug report to find out when / how the future nvidia drivers are released "officially" into Ubuntu:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/)

Also, hold on to the install script for that driver as there is an option to uninstall when the time comes.

---

### Post by Changturkey on 2008-11-23
Great, just got a new laptop with intel gfx, could have got nvidia. :(

---

### Post by Kosimo on 2008-11-23
> **Changturkey said:**
> Great, just got a new laptop with intel gfx, could have got nvidia. :(

At least you are using open source drivers, that should be enough satisfaction for now, isn't it :P

---

### Post by zmjjmz on 2008-11-23
> **Changturkey said:**
> Great, just got a new laptop with intel gfx, could have got nvidia. :(

I feel your pain. By a lot.

---

### Post by wd5gnr on 2008-11-23
I tried 180.06 and had a strange "breakage". It would start up ok, but tabs and keyboard stuff didn't work so it was useless and I reverted to 177.x. However, I tried 180.08 and this time remembered to turn off the overclocking in my Autostart (nvidia-settings lines). That did the trick. Turning on the overclocking that worked in 177.x caused a similar failure. 

However, I have noticed lately that in a Konsole window, "more" doesn't show the first page (no overclock). This did not happen before. Not sure if it is a Konsole issue, a Compiz issue, or a driver issue. Will investigate more.

Oh yeah, I remembered the issue seems sensitive to the scrollback buffer setting but never had a problem in 177.

Update: Compiz seems to be the culprit.

---

### Post by Kosimo on 2008-11-24
any other review so far?

---

### Post by Vadi on 2008-11-24
Well I uninstalled ubuntu driver and the intalled nvidia. tried running a benchmark, no difference in fps :\

---

### Post by Kosimo on 2008-11-24
> **Vadi said:**
> Well I uninstalled ubuntu driver and the intalled nvidia. tried running a benchmark, no difference in fps :\

Are you running compiz?

---

### Post by Vadi on 2008-11-24
Yeah. I don't feel like messing up my window arrangement so I always play with it on.

For games that can properly do fullscreen, it doesn't matter anyway, because compiz goes out of the way for them ("unredirect fullscreen windows" option I think. Anyway 0 diff in fps)

---

### Post by graabein on 2008-11-24
> **Kosimo said:**
> I don't have this card... Witch Drivers version are you currently using?

Version 177 I think. From within the driver management thingy in Ubuntu 8.10. Had it going okay but tried to change boot resolution because of the *unidentified video mode number 31f error* and now it's all messed up. Going back and forth between low res, reconfigure, restart and repeat. ](*,)

(Nvidia GeForce 6600 GT card.)

---

### Post by Kosimo on 2008-11-24
> **graabein said:**
> Version 177 I think. From within the driver management thingy in Ubuntu 8.10. Had it going okay but tried to change boot resolution because of the *unidentified video mode number 31f error* and now it's all messed up. Going back and forth between low res, reconfigure, restart and repeat. ](*,)

(Nvidia GeForce 6600 GT card.)

You should give it a try to this version.

There are several bugfixes

---

### Post by Amorget on 2008-11-24
I installed .06 on Friday and was very impressed.  My card is a 8600GT in a Sony Vaio laptop.  It fixed a problem with Skype where the text wouldn't appear on the chat window until I clicked somewhere on the window.  It is also incredibly faster.  However, I noticed that I am getting a weird "highlighting" error in Gnome.  Basically when I browse the Menus (Application, Places, System) it seems to keep things highlighted even after my mouse leaves them.  I am going to install .08 and see what that fixes.

I am not sure why anyone waits for the Ubuntu drivers, it really isn't very hard to install the nVidia ones, imho.

---

### Post by Kosimo on 2008-11-27
after that last kernel update we had everything brake down... I don't know then why they say that it won't happen

---

### Post by Paqman on 2008-11-27
So this is going into backports? That's good news.

---

### Post by wd5gnr on 2008-11-28
> **Amorget said:**
>  However, I noticed that I am getting a weird "highlighting" error in Gnome.  Basically when I browse the Menus (Application, Places, System) it seems to keep things highlighted even after my mouse leaves them.  .

Are you running Compiz/Emerald? Turning those OFF in Kbuntu solved a similar problem for me. Actually turning Compiz off did it, but made things slow. I don't think Kwin and Emerald like to play together, at least with the new drivers.

---

### Post by Vadi on 2008-11-28
> **Kosimo said:**
> after that last kernel update we had everything brake down... I don't know then why they say that it won't happen

Because you upgraded the drivers manually?

People who didn't got everything fine.

---

### Post by rakan_dr on 2008-11-28
I have nvidia 8500GT 512, and i'll install that driver to test it. I have plenty problems with my graphics card. I hope that driver fixes everything.

By the way, does anybody used that driver with 8500GT??

---

### Post by Kosimo on 2008-11-28
> **Vadi said:**
> Because you upgraded the drivers manually?

People who didn't got everything fine.

We're talking about 180.06, there is a "non manual" way to install them? :D

---

### Post by Luke has no name on 2008-11-28
Card: 8800M GTS
I uninstalled the 177 drivers manually, disabled compiz, killed gdm, ran the script, and my 2D performance is noticeably more responsive.

---

### Post by Cheap Webcam on 2008-11-28
wholesale [cheap card](http://www.agoodic.com/viewproduct.asp?/SD-card.htm) [cheap webcam](http://www.agoodic.com/viewproduct.asp?/webcam_kitty.htm) in [agoodic](http://www.agoodic.com/viewproduct.asp?/webcam_kitty.htm)

---

### Post by doorknob60 on 2008-11-29
I wanna install, but I can't think of a good way to install them in Arch without casuing missing dependencies on all my apps that require libgl (provided by nvidia-utils, which needs to be uninstalled to manually install the drivers). Meh, this is the one drawback of Arch, although there's probably pretty easy ways around it, but whenever I mess with my drivers my lib32-nvidia-utils stops working and breaks Wine, so I'll just not mess with it I guess. Nothing wrong with the 177 drivers right now.

---

### Post by pissedoffdude on 2008-11-29
> **Kosimo said:**
> after that last kernel update we had everything brake down... I don't know then why they say that it won't happen

Yeah, but that's something you should be aware of when you install the drivers manually.  Whenever there's a kernel upgrade, they're definitely gonna break.  But it's not hard to fix.  Just reinstall the drivers from the .run

---

### Post by EdThaSlayer on 2008-11-29
Too bad they don't support my laptops 512 mb Geforce 9500m GS...yet. :(
Can't wait till the final drivers come out(they organized it in a pretty neat way!).

---

### Post by BigSilly on 2008-11-29
I'm thrilled to bits that Nvidia are giving Linux users improved drivers, don't get me wrong, but wouldn't we be better off if they opened them up now? I'm no expert, but if the community could improve these drivers, it'd be much better for the end user, no?

---

### Post by Half-Left on 2008-11-29
> **BigSilly said:**
> I'm thrilled to bits that Nvidia are giving Linux users improved drivers, don't get me wrong, but wouldn't we be better off if they opened them up now? I'm no expert, but if the community could improve these drivers, it'd be much better for the end user, no?

They just can't open them up if they wanted because their licence says no, as I heard some of that code dont even belong to them.

---

### Post by mips on 2008-11-29
> **doorknob60 said:**
> I wanna install, but I can't think of a good way to install them in Arch without casuing missing dependencies on all my apps that require libgl (provided by nvidia-utils, which needs to be uninstalled to manually install the drivers). Meh, this is the one drawback of Arch, although there's probably pretty easy ways around it, but whenever I mess with my drivers my lib32-nvidia-utils stops working and breaks Wine, so I'll just not mess with it I guess. Nothing wrong with the 177 drivers right now.

What are you talking about? Why do you want to install the drivers manually? You have to update the nvidia-utils to the same version as the driver else it will NOT work.

yaourt -S nvidia-beta
yaourt -S nvidia-utils-beta

The above will do it all for you, enjoy.

---

### Post by mips on 2008-11-29
> **Half-Left said:**
> as I heard some of that code dont even belong to them.

True, one of the reasons.

---

### Post by BigSilly on 2008-11-29
> **Half-Left said:**
> They just can't open them up if they wanted because their licence says no, as I heard some of that code dont even belong to them.

> **mips said:**
> True, one of the reasons.

Ah right. Shame that.

---

### Post by Vadi on 2008-11-29
That and video drivers are a one complex thing... amount of people wanting & being actually able to contribute wouldn't be high.

---

### Post by Mazza558 on 2008-11-29
Just installed these after removing nvidia-glx-new.

Now it defaults to Vesa at 800x600.

Great. 

Right, going to try a dpkg-reconfigure.

EDIT: That didn't work. I'm at my original resolution, but no shiny new drivers.

---

### Post by aktiwers on 2008-11-29
Try running:
```
sudo nvidia-xconfig
```

---

### Post by Polygon on 2008-11-29
> **Vadi said:**
> That and video drivers are a one complex thing... amount of people wanting & being actually able to contribute wouldn't be high.

well im sure all the people who work on the mesa vesa and the nv/nouvou (however thats spelled) drivers know a thing or two about them, and could contribute

---

### Post by MikeTheC on 2008-11-30
Don't know what you guys are looking at, but when I go to the nVidia search page (as per the link above) and I tell it I've got an nForce 405 / 6100, it tells me there were no search results for the driver.

I'm not panicking over this, of course, because I've had (knock on wood) absolutely no problems with any of the various nVidia drivers I've used so far. Perhaps my graphics card doesn't fall into a gray area for performance or stability?

---

### Post by mips on 2008-11-30
> **MikeTheC said:**
> Don't know what you guys are looking at, but when I go to the nVidia search page (as per the link above) and I tell it I've got an nForce 405 / 6100, it tells me there were no search results for the driver.


[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us) Pick your card and select Beta under "**Recommended/Beta:**"

32bit: [http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)
64bit: [http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html)

---

### Post by pelle.k on 2008-11-30
Just to remind people that 180.08 is way more stable than the 180.06 BETA.
I speak for myself, of course, but i imagine it's rather universal.

---

### Post by Vadi on 2008-11-30
On a certain webpage, I had my screen completely freeze and start flickering. No smashing on the keyboard helped.

Today when opening a flash chart, my screen went black for a second but thankfully came back.

So, just know what you're getting into... this is a real beta, not a google beta.

---

### Post by Kosimo on 2008-11-30
> **Vadi said:**
> On a certain webpage, I had my screen completely freeze and start flickering. No smashing on the keyboard helped.

Today when opening a flash chart, my screen went black for a second but thankfully came back.

So, just know what you're getting into... this is a real beta, not a google beta.

I'm not having any of this problems.

---

### Post by kfrancart on 2008-12-03
Woohoo! Thanks to all for the insights. I was having some real issues with the 177 driver and KDE. Same story as many here. Worked in 8.04, busted in 8.10. 
I fiddled with the settings to get 8.10 working but it never worked with OpenOffice always had flickering and black screens, etc. 
Now KDE seems rock solid - after install reboot and test of open office no more flickering! Thanks to aktiwers for the code. Only had to change to: 
sudo /etc/init.d/gdm stop 
to
sudo /etc/init.d/kdm stop

since it's KDE) out of his HOWTO. The drivers did have to rebuild parts of the kernal, but all went without a hitch.

---

### Post by MikeTheC on 2008-12-03
I chose the provided link for x86 32 bit. I still cannot find anything using their search system, no matter what I try.

EDIT: Ok, so now I have the file via the link (as mentioned above), but it keeps telling me I have to quit X first. Um... not sure why I should have to do this (let alone how), so I'm thinking maybe it's wiser to wait for Ubuntu to officially put this out.

---

### Post by pelle.k on 2008-12-04
180.11 now released.
[ftp://download.nvidia.com/XFree86/Linux-x86/180.11/NVIDIA-Linux-x86-180.11-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.11/NVIDIA-Linux-x86-180.11-pkg1.run)

---

### Post by kfrancart on 2008-12-04
> **MikeTheC said:**
> I chose the provided link for x86 32 bit. I still cannot find anything using their search system, no matter what I try.

EDIT: Ok, so now I have the file via the link (as mentioned above), but it keeps telling me I have to quit X first. Um... not sure why I should have to do this (let alone how), so I'm thinking maybe it's wiser to wait for Ubuntu to officially put this out.

MikeTheC, I followed post #31 found at the top of page 4 of this thread almost verbatim to get mine to work (I changed gdm to kdm due to Kubuntu). The reason for stopping X is because you are replacing the video drivers. The how is in aktiwers post as stated earlier.

I was apprehensive at first as well, I've only been using Linux for a short time. After many tests on my system I've found this new beta driver to fix all of the issues I was having with the latest release of 8.10. If you are not having any issues with your video card/screen then there is no reason to replace your current drivers. Hope this helps.

---

### Post by ingalex on 2008-12-04
If you want to update nvidia driver and you don't know how you can see [this ]("http://www.ingalex.helloweb.eu//index.php?option=com_content&task=view&id=152&Itemid=1")tutorial. ):P

---

### Post by Kosimo on 2008-12-04
> **pelle.k said:**
> 180.11 now released.
[ftp://download.nvidia.com/XFree86/Linux-x86/180.11/NVIDIA-Linux-x86-180.11-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.11/NVIDIA-Linux-x86-180.11-pkg1.run)

Thanks for the heads up! ;)

---

### Post by Kosimo on 2008-12-04
Good good good
WIth 180.08 I wasn't able to run Google earth for some memory bug, 
Now with 180.11 problem is solved and it perfectly works again.

---

### Post by Kosimo on 2008-12-04
By the way, if any admin reads this:

Can you please change this topic title from 180.06 to 180.xx? As it can become a recurrent discussion to talk about this particular driver series

---

### Post by piousp on 2008-12-04
Sweet! I'm gonna try em with my GTX260 :p

---

### Post by waapwoop1 on 2008-12-04
Will this work with an nvidia 8500 GT 512MB?

---

### Post by Kosimo on 2008-12-04
> **waapwoop1 said:**
> Will this work with an nvidia 8500 GT 512MB?

yeps

---

### Post by chris4585 on 2008-12-04
so if i install intrepid on my laptop which has a GeForce 8400M GS card, which before I got not 3D and install the 180.08 driver I should have 3D acceleration back?

and what about my GeForce 6150SE nForce 430 card on my desktop?

---

### Post by MikeTheC on 2008-12-04
Hmm... as far as I *know*, the 180.06 drive installed successfully. I rebooted and came back up and nothing seemed to be improved or changed.

So then, as I'm getting ready to write this very reply, I thought I'd check the System > Administration > Hardware Drivers status, and it still shows I'm using driver version 177[color=red]*[/color].

Anyone here have a clue what may be going on?

[color=red]*[/color] Please note that the 180-series driver does [color=red]*NOT*[/color] appear in Hardware Drivers, only version 96, version 173, and version 177 (which specifically shows as "activated".)

---

### Post by Perfect Storm on 2008-12-04
Did you try unistall the previous driver first?

---

### Post by MikeTheC on 2008-12-04
> **Artificial Intelligence said:**
> Did you try unistall the previous driver first?

No. I wasn't aware that I needed to. However, is it "safe" to do now that I've sort of tampered with things?

---

### Post by Perfect Storm on 2008-12-04
If it's the default driver from the repo, remove it from "Hardware Drivers" applications. It should set it back to nv driver. Then try again.

---

### Post by MikeTheC on 2008-12-05
Interesting...

Ok, so I deactivated the 177 driver, then uninstalled all of the nVidia driver-related items in Synaptic. After that, I killed gdm, re-ran the 180 installer.

Upon rebooting, I checked and Applications > System Tools > NVIDIA X Server Settings clearly shows that 180.06 is up and running. *However*... System > Administration > Hardware Drivers now is blank, showing no "non-free" drivers at all.

I had Compiz enabled before I began this process, and it's still enabled now, and all 3D acceleration seems to work as before. Unfortunately, I'm still getting the video freezing I was before.

So my question is, given that all I've got is an nVidia mobo with an on-board n405/6100, am I simply beating a dead horse here? Because if that's all this is, then for the moment I can easily disable Compiz (which then solves the whole video freeze issue) and when I am able to budget it, I'll upgrade the PSU and put in a decent graphics card.

Thoughts or opinions?

---

### Post by Perfect Storm on 2008-12-05
Did you check if your card is actually affected of the changes in 180 driver?

> Upon rebooting, I checked and Applications > System Tools > NVIDIA X Server Settings clearly shows that 180.06 is up and running. However... System > Administration > Hardware Drivers now is blank, showing no "non-free" drivers at all.

It shouldn't. Only the driver from Ubuntu official will be listed. So it's fine.

---

### Post by mhh91 on 2008-12-05
they didn't release that driver for 6200??

i know it's old,but why??

---

### Post by Perfect Storm on 2008-12-05
You have to ask at nvidia...

---

### Post by eternalnewbee on 2008-12-05
Hi there. Here to hijack.
I've searched this thread for my graphic card (Geforce 7300GT), but it's not mentioned.
Does anyone know nVidia 180.06 is compatible with my card?
EDIT: Forgot the smily. Here it is: (I'm smiling)
EDIT: Never mind. Not compatible. I just checked at the nvidia site.

---

### Post by FuturePilot on 2008-12-05
> **eternalnewbee said:**
> Hi there. Here to hijack.
I've searched this thread for my graphic card (Geforce 7300GT), but it's not mentioned.
Does anyone know nVidia 180.06 is compatible with my card?

It should be. The 180 drivers should work with the 6 series and higher.

---

### Post by mips on 2008-12-05
> **chris4585 said:**
> so if i install intrepid on my laptop which has a GeForce 8400M GS card, which before I got not 3D and install the 180.08 driver I should have 3D acceleration back?

and what about my GeForce 6150SE nForce 430 card on my desktop?


> **mhh91 said:**
> they didn't release that driver for 6200??

i know it's old,but why??

[COLOR=Red]**Now before any more people ask, check their website!**[/COLOR][COLOR=Black] 

Anyway here goes for v180.06 supported cards are:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[/COLOR]> **GeForce Products:**
         GeForce 9800 GX2
     0x0604
           GeForce 9800 GTX
     0x0612
           GeForce 9600 GT
     0x0622
           GeForce 9500M GS
     0x0405
           GeForce 8800M GTX
     0x060C
           GeForce 8800M GTS
     0x0609
           GeForce 8800 Ultra
     0x0194
           GeForce 8800 GTX
     0x0191
           GeForce 8800 GTS 512
     0x0600
           GeForce 8800 GTS
     0x0193
           GeForce 8800 GT
     0x0602
           GeForce 8800 GT
     0x0611
           GeForce 8800 GS
     0x0606
           GeForce 8800 GS
     0x060D
           GeForce 8700M GT
     0x0409
           GeForce 8600M GT
     0x0407
           GeForce 8600M GS
     0x0425
           GeForce 8600 GTS
     0x0400
           GeForce 8600 GT
     0x0401
           GeForce 8600 GT
     0x0402
           GeForce 8500 GT
     0x0421
           GeForce 8400M GT
     0x0426
           GeForce 8400M GS
     0x0427
           GeForce 8400M G
     0x0428
           GeForce 8400 SE
     0x0420
           GeForce 8400 GS
     0x0404
           GeForce 8400 GS
     0x0422
           GeForce 8400 GS
     0x0424
           GeForce 8400 GS
     0x06E4
           GeForce 8300 GS
     0x0423
           GeForce 8300
     0x0848
           GeForce 8200/ nForce 730a
     0x084A
           GeForce 8200
     0x0849
           GeForce 8200
     0x084B
           GeForce 8100 / nForce 720a
     0x084F
           GeForce 7950 GX2
     0x0293
           GeForce 7950 GX2
     0x0294
           GeForce 7950 GT
     0x0295
           GeForce 7950 GT
     0x02E4
           GeForce 7900 GTX
     0x0290
           GeForce 7900 GT/GTO
     0x0291
           GeForce 7900 GS
     0x0292
           GeForce 7900 GS
     0x02E3
           GeForce 7800 SLI
     0x0095
           GeForce 7800 GTX
     0x0090
           GeForce 7800 GTX
     0x0091
           GeForce 7800 GT
     0x0092
           GeForce 7800 GS
     0x0093
           GeForce 7800 GS
     0x00F5
           GeForce 7650 GS
     0x0390
           GeForce 7600 LE
     0x0394
           GeForce 7600 GT
     0x02E0
           GeForce 7600 GT
     0x0391
           GeForce 7600 GS
     0x02E1
           GeForce 7600 GS
     0x0392
           GeForce 7500 LE
     0x01DD
           GeForce 7350 LE
     0x01D0
           GeForce 7300 SE/7200 GS
     0x01D3
           GeForce 7300 LE
     0x01D1
           GeForce 7300 GT
     0x0393
           GeForce 7300 GT
     0x0395
           GeForce 7300 GS
     0x01DF
           GeForce 7150M / nForce 630M
     0x0531
           GeForce 7150 / NVIDIA nForce 630i
     0x07E0
           GeForce 7100 GS
     0x016A
           GeForce 7100 / NVIDIA nForce 630i
     0x07E1
           GeForce 7050 PV / NVIDIA nForce 630a
     0x053A
           GeForce 7050 PV / NVIDIA nForce 630a
     0x053B
           GeForce 7050 / NVIDIA nForce 610i
     0x07E3
           GeForce 7025 / NVIDIA nForce 630a
     0x053E
           GeForce 7000M / nForce 610M
     0x0533
           GeForce 6800 XT
     0x0044
           GeForce 6800 XT
     0x0048
           GeForce 6800 XT
     0x00C3
           GeForce 6800 XT
     0x0218
           GeForce 6800 XE
     0x0043
           GeForce 6800 Ultra
     0x0040
           GeForce 6800 Ultra
     0x00F9
           GeForce 6800 LE
     0x0042
           GeForce 6800 LE
     0x00C2
           GeForce 6800 LE
     0x0212
           GeForce 6800 GT
     0x0045
           GeForce 6800 GT
     0x0046
           GeForce 6800 GT
     0x0215
           GeForce 6800 GS
     0x0047
           GeForce 6800 GS
     0x00C0
           GeForce 6800 GS
     0x00F6
           GeForce 6800
     0x0041
           GeForce 6800
     0x00C1
           GeForce 6800
     0x00F0
           GeForce 6800
     0x0211
           GeForce 6700 XL
     0x0147
           GeForce 6610 XL
     0x0145
           GeForce 6600 VE
     0x0143
           GeForce 6600 LE
     0x00F4
           GeForce 6600 LE
     0x0142
           GeForce 6600 GT
     0x00F1
           GeForce 6600 GT
     0x0140
           GeForce 6600
     0x00F2
           GeForce 6600
     0x0141
           GeForce 6500
     0x0160
           GeForce 6250
     0x0169
           GeForce 6200SE TurboCache(TM)
     0x0162
           GeForce 6200 TurboCache(TM)
     0x0161
           GeForce 6200 LE
     0x0163
           GeForce 6200 A-LE
     0x0222
           GeForce 6200
     0x00F3
           GeForce 6200
     0x014F
           GeForce 6200
     0x0221
           GeForce 6150SE nForce 430
     0x03D0
           GeForce 6150 LE
     0x0241
           GeForce 6150
     0x0240
           GeForce 6100 nForce 420
     0x03D5
           GeForce 6100 nForce 405
     0x03D1
           GeForce 6100 nForce 400
     0x03D2
           GeForce 6100
     0x0242
           GeForce PCX 5900
     0x00FB
           GeForce PCX 5750
     0x00FA
           GeForce PCX 5300
     0x00FC
           GeForce Go 7950 GTX
     0x0297
           GeForce Go 7900 GTX
     0x0299
           GeForce Go 7900 GS
     0x0298
           GeForce Go 7800 GTX
     0x0099
           GeForce Go 7800
     0x0098
           GeForce Go 7600 GT
     0x0399
           GeForce Go 7600
     0x0398
           GeForce Go 7400
     0x01D8
           GeForce Go 7300
     0x01D7
           GeForce Go 7200
     0x01D6
           GeForce Go 6800 Ultra
     0x00C9
           GeForce Go 6800
     0x00C8
           GeForce Go 6600 TE/6200 TE
     0x0146
           GeForce Go 6600 GT
     0x0149
           GeForce Go 6600
     0x0144
           GeForce Go 6600
     0x0148
           GeForce Go 6400
     0x0166
           GeForce Go 6400
     0x0168
           GeForce Go 6200
     0x0164
           GeForce Go 6200
     0x0167
           GeForce Go 6150
     0x0244
           GeForce Go 6100
     0x0247
           GeForce FX Go5700
     0x0347
           GeForce FX Go5700
     0x0348
           GeForce FX Go5650
     0x031B
           GeForce FX Go5600
     0x031A
           GeForce FX Go53xx
     0x032C
           GeForce FX Go5250
     0x0325
           GeForce FX Go5200 32M/64M
     0x0328
           GeForce FX Go5200
     0x0324
           GeForce FX Go5100
     0x032D
           GeForce FX 5950 Ultra
     0x0333
           GeForce FX 5900ZT
     0x0334
           GeForce FX 5900XT
     0x0332
           GeForce FX 5900 Ultra
     0x0330
           GeForce FX 5900
     0x0331
           GeForce FX 5800 Ultra
     0x0301
           GeForce FX 5800
     0x0302
           GeForce FX 5700VE
     0x0344
           GeForce FX 5700LE
     0x0343
           GeForce FX 5700 Ultra
     0x0341
           GeForce FX 5700
     0x0342
           GeForce FX 5600XT
     0x0314
           GeForce FX 5600 Ultra
     0x0311
           GeForce FX 5600
     0x0312
           GeForce FX 5500
     0x0326
           GeForce FX 5200LE
     0x0323
           GeForce FX 5200 Ultra
     0x0321
           GeForce FX 5200
     0x0320
           GeForce FX 5200
     0x0322
           GeForce FX 5100
     0x0327
     **Tesla Products:**
         Tesla C870
     0x0197
     **Quadro Products:**
         Quadro FX 1000
     0x0309
           Quadro FX 1100
     0x034E
           Quadro FX 1300
     0x00FE
           Quadro FX 1400
     0x00CE
           Quadro FX 1500
     0x029E
           Quadro FX 1500M
     0x029B
           Quadro FX 1600M
     0x040D
           Quadro FX 1700
     0x040F
           Quadro FX 2000
     0x0308
           Quadro FX 2500M
     0x029A
           Quadro FX 3000
     0x0338
           Quadro FX 330
     0x00FC
           Quadro FX 3450/4000 SDI
     0x00CD
           Quadro FX 350
     0x01DE
           Quadro FX 3500
     0x029D
           Quadro FX 350M
     0x01DC
           Quadro FX 3600M
     0x061C
           Quadro FX 360M
     0x042D
           Quadro FX 370
     0x040A
           Quadro FX 3700
     0x061A
           Quadro FX 4000
     0x004E
           Quadro FX 4400/Quadro FX 3400
     0x00F8
           Quadro FX 4500
     0x009D
           Quadro FX 4500 X2
     0x029F
           Quadro FX 4600
     0x019E
           Quadro FX 500/FX 600
     0x032B
           Quadro FX 540
     0x014E
           Quadro FX 540M
     0x014C
           Quadro FX 550
     0x014D
           Quadro FX 5500
     0x029C
           Quadro FX 560
     0x039E
           Quadro FX 5600
     0x019D
           Quadro FX 570
     0x040E
           Quadro FX 570M
     0x040C
           Quadro FX 700
     0x033F
           Quadro FX Go1000
     0x034C
           Quadro FX Go1400
     0x00CC
           Quadro FX Go700
     0x031C
           Quadro NVS 110M
     0x01D7
           Quadro NVS 110M
     0x01DA
           Quadro NVS 120M
     0x01DB
           Quadro NVS 130M
     0x042A
           Quadro NVS 135M
     0x042B
           Quadro NVS 140M
     0x0429
           Quadro NVS 210S / NVIDIA GeForce 6150LE
     0x0245
           Quadro NVS 280 PCI-E/Quadro FX 330
     0x00FD
           Quadro NVS 285
     0x0165
           Quadro NVS 290
     0x042F
           Quadro NVS 320M
     0x040B
           Quadro NVS 440
     0x014A
           Quadro NVS 55/280 PCI
     0x032A



---

### Post by eternalnewbee on 2008-12-05
If it is, it's not mentioned here:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
EDIT: Found it under Beta

---

### Post by mhh91 on 2008-12-05
> **mips said:**
> [COLOR=Red]**Now before any more people ask, check their website!**[/COLOR][COLOR=Black] 

Anyway here goes for v180.06 supported cards are:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[/COLOR]


okay,can you send me a link of the driver for my card please?


it's Geforce 6200,i can't find it,really

---

### Post by mips on 2008-12-05
> **mhh91 said:**
> okay,can you send me a link of the driver for my card please?


it's Geforce 6200,i can't find it,really

See post #102

What I do not understand is how you cannot find the driver?

---

### Post by eternalnewbee on 2008-12-05
> What I do not understand is how you cannot find the driver?
Relax mips. Has it never happened to you, that you're looking for something that's right in front of you?;)

---

### Post by eternalnewbee on 2008-12-05
> 
okay,can you send me a link of the driver for my card please?


it's Geforce 6200,i can't find it,really
You can find it here mhh91:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
Just fill in the form, and under Recommended/Beta choose Beta.

---

### Post by mips on 2008-12-05
> **eternalnewbee said:**
> Relax mips. Has it never happened to you, that you're looking for something that's right in front of you?;)

I'm relaxed. The thing is he is not the first person that cannot find the driver and I'm wondering why. Is he inputting the right info into the fields etc?

Yes I have stared at a web page before and not seen what is right in front of me.

---

### Post by fjf on 2008-12-05
Easy install of 180.11 from repos:

[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

---

### Post by MikeTheC on 2008-12-05
> **mips said:**
> See post #102

What I do not understand is how you cannot find the driver?

> **eternalnewbee said:**
> Relax mips. Has it never happened to you, that you're looking for something that's right in front of you?;)

> **mips said:**
> I'm relaxed. The thing is he is not the first person that cannot find the driver and I'm wondering why. Is he inputting the right info into the fields etc?
I was and still am having the "can't find it on nVidia's site" problem. When I put in what hardware I have, it returns the message of no search results. Whether I pick the release driver option, the beta driver option, or the All option, and whether I pick for x86 32 bit or 64 bit, it makes absolutely no difference.

The *only* way I can get it to give me the driver is to pick some much higher-end, much newer card, and then technically it's a "hope" that the driver supports the older hardware. Now, it happens to be the case that the 180 series *does* support the hardware, but that's not the point.

If I didn't know any better (which of course, I do) I would have to surmise that the card no longer has driver support from nVidia. The problem is, of course, that you can still go out and buy new 6200 series (which is relatively close to my card in the grand scheme of things) at the local Wal-Mart, so what gives?

Clearly, whomever is maintaining the database which back-ends the driver download portion of their site isn't doing so in a way which properly reflects the actual support by nVidia for their products. Whether this is due to company policy or incompetence is, of course, an unknown.

---

### Post by MikeTheC on 2008-12-05
To Wit:

[IMG]http://img99.imageshack.us/img99/3682/nodriversfromnvidianq5.png[/IMG]

---

### Post by Bou on 2008-12-05
> **Kosimo said:**
> In one word. IMPRESSIVE.

Agreed. I tried it today and the difference in performance is spectacular.

---

### Post by Kosimo on 2008-12-05
> **Bou said:**
> Agreed. I tried it today and the difference in performance is spectacular.

Hope that development doesn't stop here anyway ;)

ps: El fary? Visca el frikisme.

---

### Post by chris4585 on 2008-12-05
> **mips said:**
> [COLOR=Red]**Now before any more people ask, check their website!**[/COLOR][COLOR=Black] 

Anyway here goes for v180.06 supported cards are:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[/COLOR]

uhm.. I didn't ask if they had the driver I needed, I asked if I'd have 3D acceleration if I used the driver, sorry if it wasn't worded that way :P

---

### Post by NTolerance on 2008-12-05
> **Changturkey said:**
> Great, just got a new laptop with intel gfx, could have got nvidia. :(

Consider yourself lucky.  Seriously.  My laptop has an NVidia 7400GO.  I've had nothing but trouble with NVidia's Linux drivers.  Compiz flickers due to Powermizer bugs, titlebars turn into artifacts, guest session fails due to libGL crashes, the list goes on.  

I thought I might want to play games on this laptop every now and then but I actually never do.  I would be much better off with an Intel graphics chip that has usable Linux drivers.

---

### Post by MikeTheC on 2008-12-06
[indent][font=courier]**Ubuntulog:** *Stardate 20081205.5*

We're on an errand of computing mercy to Xanth Colony 5. Initial pre-approach scans revealed variable and largely inconclusive evidence of GPUs habitating near one of their technology population centers. Science Officer M'Self and I beamed down to one of these and entered one of the rehabilitated CompUSA installations, still online and operational after their multiple-year war with several other technological powers. Very soon thereafter, we detected the presence of GPUs and, curiously, several suspiciously nearby PSUs.

Immediately suspecting a treacherously SLIppery situation, I headed towards the GPUs while M'Self approached the PSUs. Almost immediately, we encountered some of the native CompUSAian tribesmen who agreed to serve as our guides and go-betweens, which was fortunate because, by then, our framerates had dropped precipitously. M'Self had cautioned prior to beam-down this was possible owing to localized RAMDAC field effects, as well as possible Brownian Emotion. I had mixed feelings about that, but decided to pursue the matter further anyhow.

Ultimately, M'Self was able to track down and retrieve one of the Thermaltake 500 watt PSUs (after several unsuccessful attempts to wrestle it to the ground, he wound up cardboard boxing it into submission), having narrowly avoided harm from it's electrified tendrils of Molex power. It took some further time and effort on my part, but I was able to isolate an [url=http://www.compusa.com/applications/searchtools/item-details.asp?EdpNo=4128445&SRCCODE=CNETCMPUSA&cm_mmc_o=2mHCjC2WHaCjCVqHCjCdwwp
]XFX 9600 GSO/768[/url], at a reasonable cost to life and liberty of only 80 standard credits.

Shortly thereafter, we beamed back up with the two specimens and hope this will aid in driver-se areas of compatibility and overall system resource utilization.[/font][/indent]

Alright, folks, so I'm hoping this takes care of all the issues I have been expressing up-thread. :)

---

### Post by mips on 2008-12-06
> **MikeTheC said:**
> 
Clearly, whomever is maintaining the database which back-ends the driver download portion of their site isn't doing so in a way which properly reflects the actual support by nVidia for their products. Whether this is due to company policy or incompetence is, of course, an unknown.

From the screenshot below your post I would say the way you are searching is wrong. Firstly you are searching for nForce drivers which are actually your MB chipset drivers and for linux that support is included in the kernel, you should be searching for GeForce drivers. Secondly you are searching in the wrong place, the area you are searching in does not include beta drivers.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[IMG]http://img71.imageshack.us/my.php?image=nv1as2.png[/IMG][IMG]http://img399.imageshack.us/img399/653/nv1wa8.png[/IMG]



Then you will have something like this
[IMG]http://img212.imageshack.us/my.php?image=nv2xf4.png[/IMG][IMG]http://img383.imageshack.us/img383/8395/nv2vy5.png[/IMG]


Hope this helps.

The following link says it is for Hardy so i dunno if it works in Intrepid etc, [http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

.

---

### Post by mips on 2008-12-06
> **chris4585 said:**
> uhm.. I didn't ask if they had the driver I needed, I asked if I'd have 3D acceleration if I used the driver, sorry if it wasn't worded that way :P

I don't see why the driver would not provide you with 3D acceleration unless you have specific issues.

---

### Post by MikeTheC on 2008-12-06
> **mips said:**
> From the screenshot below your post I would say the way you are searching is wrong. Firstly you are searching for nForce drivers which are actually your MB chipset drivers and for linux that support is included in the kernel, you should be searching for GeForce drivers. Secondly you are searching in the wrong place, the area you are searching in does not include beta drivers.

<snip>

Hope this helps.

The following link says it is for Hardy so i dunno if it works in Intrepid etc, [http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

.

Thanks, Mips! I'm rather strangely relieved to know it was me and not nVidia who was being the idiot here... :p

Although, to be fair, since what I have *is* an nForce card (the on-board one, not the new one I just bought), why is how I was searching fundamentally wrong? ;)

---

### Post by chris4585 on 2008-12-06
> **mips said:**
> I don't see why the driver would not provide you with 3D acceleration unless you have specific issues.

Ok thanks, also thanks for understanding

---

### Post by mhh91 on 2008-12-06
i found it,thanks peeps :)

---

### Post by ellalan on 2008-12-06
I have installed the nVidia180.08 driver and when I looked in Hardware Drivers nothing in there not the new driver, old driver169.12 removed by me prior to installation of this new driver. Could someone help me please. I have already done a reinstall of my Hardy due to using the Jaunty Repo method(but that was before reading etternalnewbe's post).
Hardy Heron 8.04
GeForce6150SE nForce430

---

### Post by 3rdalbum on 2008-12-06
> **ellalan said:**
> I have installed the nVidia180.08 driver and when I looked in Hardware Drivers nothing in there not the new driver, old driver169.12 removed by me prior to installation of this new driver. Could someone help me please. I have already done a reinstall of my Hardy due to using the Jaunty Repo method(but that was before reading etternalnewbe's post).
Hardy Heron 8.04
GeForce6150SE nForce430

The Hardware Drivers program doesn't know about the new driver, but as long as it's installed and you're getting 3D acceleration, everything is working as it should.

If you aren't having problems with the old driver, I would recommend not upgrading.

---

### Post by mips on 2008-12-07
> **ellalan said:**
> I have installed the nVidia180.08 driver and when I looked in Hardware Drivers nothing in there not the new driver, old driver169.12 removed by me prior to installation of this new driver. Could someone help me please. I have already done a reinstall of my Hardy due to using the Jaunty Repo method(but that was before reading etternalnewbe's post).
Hardy Heron 8.04
GeForce6150SE nForce430

Install the latest nvidia-utils to match your driver version. When you open nvidia-utils it should tell you the driver version you are using amongst other things.

---

### Post by eternalnewbee on 2008-12-07
That's correct. See screenshot

---

### Post by ellalan on 2008-12-07
Thank you Guys,
I have managed to install v 173.12 using EnvyNG and I may try the 180.11 later on. I wanted the new driver because my display was a bit untidy and its a lot better now. Thanks again to all.

---

### Post by FokkerCharlie on 2008-12-07
Hi All- I have run into a bit of a snag here:

While the 180 driver did give me a bit of a performance boost, unfortunately it also stops suspend from working properly (in fact, my laptop won't wake up at all), so I have been trying to go back to the 173 driver (seems to work better here than 177).

I tried both the binary driver from nvidia 180.06, then installed the 180.11 from the Jaunty repos, all as expected.  I then tried to revert to 173 using envy, didn't work.  I have run the --uninstall option with the nvidia driver, which looked OK, and have uninstalled the 180 using apt-get.

Now, I'm trying to re-install 173 using apt-get, and here's the output:
```

sudo apt-get install -f nvidia-glx-173
[sudo] password for charlie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  nvidia-glx-173
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7695kB of archives.
After this operation, 23.0MB of additional disk space will be used.
(Reading database ... 212214 files and directories currently installed.)
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

With or without the -f, doesn't seem to make a difference.  Any suggestions?  I am without my compiz effects entirely at the mo!

Charlie

---

### Post by aktiwers on 2008-12-07
I had this happend to me too. Did you install using Jaunty repos?

The only way I could fix this problem was to enable the Jaunty repos again, completely purge, remove and autoremove the 180 driver. Then disable Jaunty repos again.

Then remove all other installed Nvidia drivers. Delete all the conflicting libs manually, and reboot. 
Again I tried installing the driver through ubuntu 8.10 repos but it gave me errors, so I downloaded the stable 177 driver from Nvidia and it took care of the problem.

I would not recomment installing the drivers via. the Jaunty repositories..  Install manually instead to save yourself from lots of trouble.

---

### Post by Redrazor39 on 2008-12-07
hey I have a geforce go 7400 ubuntu 8.10 and I can't find the right driver. Could someone point to a link for me and some really helpful instructions (noob here)?

---

### Post by FokkerCharlie on 2008-12-07
Hi, aktiwers

Sadly, that didn't work for me.  I have re-enabled jaunty repo, uninstalled/purged the 180 driver, removed the repo again, but I'm still struggling.  I still get all the same errors- any more ideas, anyone?

I am stuck with a 800x600 display for the moment!

Charlie

---

### Post by aktiwers on 2008-12-07
> **FokkerCharlie said:**
> Hi, aktiwers

Sadly, that didn't work for me.  I have re-enabled jaunty repo, uninstalled/purged the 180 driver, removed the repo again, but I'm still struggling.  I still get all the same errors- any more ideas, anyone?

I am stuck with a 800x600 display for the moment!

Charlie
 
Did you try downloading the stable driver from Nvidia and install it manually after removing the 180?

---

### Post by mips on 2008-12-08
> **Redrazor39 said:**
> hey I have a geforce go 7400 ubuntu 8.10 and I can't find the right driver. Could someone point to a link for me and some really helpful instructions (noob here)?

See post #102 & #143

---

### Post by FokkerCharlie on 2008-12-08
OK- I restored my setup to full 3D glory, after removing the 180 driver from the Jaunty repo.  This caused major problems for me, I would not recommend anyone else try it!

Charlie

---

### Post by barbedsaber on 2008-12-08
man, I can't wait to try this.
(thinks about previous times I tried to install pre release software)
(remeber hours spent trying to configure, editing config files, Reading the ******* manual and then trying to get things back to the way they were, just to get a working PC again)
might wait until it hits official repos eh. :)

---

### Post by ellalan on 2008-12-08
> **FokkerCharlie said:**
> Hi, aktiwers

Sadly, that didn't work for me.  I have re-enabled jaunty repo, uninstalled/purged the 180 driver, removed the repo again, but I'm still struggling.  I still get all the same errors- any more ideas, anyone?

I am stuck with a 800x600 display for the moment!

Charlie

Hi,
Uninstall everything begins with "nvidia" in synaptics.
Download the driver to your Desktop,
1.Ctrl+Alt+F1
2.sudo /etc/init.d/gdm stop
3.cd Desktop
4.sudo sh NVIDIA<Tab>
5.sudo reboot

I had same troubles as you had with Jaunty repo method. I found this method very easy. HTH.

---

### Post by FokkerCharlie on 2008-12-09
Cool, thanks- fixed it my end.  Had to do some serious tampering with uninstalling the kernel headers and re-installing them, and then the same with xorg-xserver.  Back to 173 driver now!

Charlie

---

### Post by Paqman on 2008-12-09
Looks like 180.11 will be going into intrepid-proposed very shortly:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/)

---

### Post by pelle.k on 2008-12-09
Hell must have frozen over. I've never seen an SRU like that?!

---

### Post by Insane_Homer on 2008-12-09
Great thanks for the post and all the help!

Just installed then and must say very noticeable improvements in the Gnome 2D environment, 3D seem better too, AWN was much faster launching and without the usually twitchiness before it settles down. Firefox seems more responsive too. Celestia seems much smoother too. Even the Gimp felt more responsive.

[CENTER][IMG]http://4.bp.blogspot.com/_71IvjB-RAis/ST7xZvgV8aI/AAAAAAAABpA/dGJOKjfhMA0/s1600/Screenshot-NVIDIA%2BX%2BServer%2BSettings.png[/IMG][/CENTER]

---

### Post by fillintheblanks on 2008-12-09
I am using nvidia-glx-new.

how are these drivers different?

---

### Post by Kosimo on 2008-12-10
Anybody tried to play Prey (Linux Native) with this drivers? I've been playing the official demo that I've download yesterday and performance was almost the same than in Windows. We're on the right way guys!

---

### Post by Mr. Picklesworth on 2008-12-10
> **pelle.k said:**
> Hell must have frozen over. I've never seen an SRU like that?!

I hope it happens more often in the future with this as a precedent. Drivers are always quite backwards compatible, and any new release is just an improvement on existing expected functionality. It's completely transparent, yet the fixes can really be felt :)

In this case, it certainly makes sense to push an SRU since the new driver reportedly fixes poor performance in KDE 4.

---

### Post by waapwoop1 on 2008-12-10
> **Paqman said:**
> Looks like 180.11 will be going into intrepid-proposed very shortly:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/)

I don't want to have to go through the process of installing it, I haven't got time. 
Will we see this update happen automatically in Ubuntu 8.10
Is that what you mean by this.

---

### Post by Polygon on 2008-12-10
how come i dont see any other beta drivers besides 180.06? i downloaded the .08 drivers using some link, but when i go to nivida's website i only see 180.06

[[IMG]http://img408.imageshack.us/img408/5095/screenshot1hc7.th.png[/IMG]](http://img408.imageshack.us/img408/5095/screenshot1hc7.png)

---

### Post by Kosimo on 2008-12-10
> **Polygon said:**
> how come i dont see any other beta drivers besides 180.06? i downloaded the .08 drivers using some link, but when i go to nivida's website i only see 180.06

[[IMG]http://img408.imageshack.us/img408/5095/screenshot1hc7.th.png[/IMG]](http://img408.imageshack.us/img408/5095/screenshot1hc7.png)

I recommend you to forget about the main webpage and just follow this nVidia official topics on nvidia linux forums:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by Insane_Homer on 2008-12-11
> **Polygon said:**
> how come i dont see any other beta drivers besides 180.06? i downloaded the .08 drivers using some link, but when i go to nivida's website i only see 180.06


Try here...
[ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/)

---

### Post by Paqman on 2008-12-11
> **waapwoop1 said:**
> I don't want to have to go through the process of installing it, I haven't got time. 
Will we see this update happen automatically in Ubuntu 8.10
Is that what you mean by this.

Yes, but only if you're connecting to the intrepid-proposed repo. That would include a lot of other stuff in the update that may or may not be stable or desirable.

Best thing to do, once it is released: open Synaptic, add intrepid-proposed, update, select just the nvidia 180.11 driver, install, then remove intrepid-proposed and update. That will grab just this driver out of intrepid-proposed.

---

### Post by pelle.k on 2008-12-11
First of all, "proposed" is where updates is kept until they are "released". So by defenition, they should end up in "updates" or "backports" repo. Unless i'm mistaken? But yes, if you want to install something before they are properly "released" then "proposed" it is.
Second, this will probably not replace the 177 series, but rather be another alternative. e.g. the "180 series". If so, it will not replace an existing "177.80" installation, but be available should one want to install it through the "restricted drivers" manager i guess. Unless it's distributed using envyNG.
I've not seen anything official on this though.

---

### Post by AaronP_ on 2008-12-12
> **mips said:**
> 
[QUOTE=MikeTheC;6314049]I was and still am having the "can't find it on nVidia's site" problem. When I put in what hardware I have, it returns the message of no search results. Whether I pick the release driver option, the beta driver option, or the All option, and whether I pick for x86 32 bit or 64 bit, it makes absolutely no difference.

From the screenshot below your post I would say the way you are searching is wrong. Firstly you are searching for nForce drivers which are actually your MB chipset drivers and for linux that support is included in the kernel, you should be searching for GeForce drivers. Secondly you are searching in the wrong place, the area you are searching in does not include beta drivers.[/quote]
I know I'm late to the party, but I filed a request with the web team to clarify this and make it more obvious that there's a difference between GeForce and nForce drivers.

---

### Post by Insane_Homer on 2008-12-13
180.16 released (Beta)

[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)

[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html)

> The NVIDIA driver follows a Unified Architecture Model in which a single graphics driver is used for all supported NVIDIA GPU products (see Appendix A, Supported NVIDIA GPU Products for a list of supported GPUs). The burden of selecting the correct driver is removed from the user, and the graphics driver is downloaded as a single file named

    **NVIDIA-Linux-x86-180.16-pkg1.run**

The package suffix (-pkg#) is used to distinguish between packages containing the same driver, but with different precompiled kernel interfaces. The file with the highest package number is suitable for most installations.

:guitar:

---

### Post by Kosimo on 2008-12-13
> **Insane_Homer said:**
> 180.16 released (Beta)

[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)

[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html)



:guitar:

Thanks for the heads up!

---

### Post by FokkerCharlie on 2008-12-13
Still won't resume from stanby, sadly!

Charlie

---

### Post by Kosimo on 2008-12-13
There are much more cards supported by the new version 180.16


Here the changelog:

> Release Highlights:

    * Added support for the following GPUs:
          o Quadro FX 2700M
          o GeForce 9400M G
          o GeForce 9800 GT
          o GeForce 9800 GT
          o GeForce 8200M G
          o GeForce Go 7700
          o GeForce 9800M GTX
          o GeForce 9800M GT
          o GeForce 9800M GS
          o GeForce 9500 GT
          o GeForce 9700M GT
          o GeForce 9650M GT
          o GeForce 9500 GT
    * Fixed a problem with the SDI sync skew controls in nvidia-settings.
    * Fixed a problem that caused some SDI applications to hang or crash.
    * Fixed an nvidia-settings crash when xorg.conf contains Device and Screen sections but no ServerLayout section.
    * Fixed a problem that caused the Linux OpenGL library to crash when used inside FreeBSD's Linux emulation layer.
    * Updated VDPAU:
          o VdpDecoderCreate API has changed incompatibly. All client applications must be rebuilt because of this change.
          o For H.264, require the application to tell VDPAU how many reference frames to allow. This allows the application to request more than 4 reference frames. VDPAU should now support level 4.1 reference frame limits on all GPUs (or very close to this limit). The application now has control over this aspect of VDPAU's memory usage.
          o Fix corruption decoding some H.264 streams on some GPUs.
          o Fix a bug that prevented VC-1/WMV3 decode from being allowed on some GPUs.
          o Documentation enhancements and cleanups to vdpau.h.
          o Don't paint the color key to presentation queue targets until the first frame is presented. This should reduce or remove the time the key is displayed before the presented frame is visible.


Just installed on my system, everything seems to work ok.

---

### Post by pelle.k on 2008-12-13
Just a quick update, 180.16 BETA released
[http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1)

32bit - [ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)
64bit - [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/)

These guys are really pushing out new beta releases, and fast!

---

### Post by Kosimo on 2008-12-13
> **pelle.k said:**
> Just a quick update, 180.16 BETA released
[http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1)

32bit - [ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)
64bit - [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/)

These guys are really pushing out new beta releases, and fast!

We've been talking about this early this morning already ;)

Yes, looks like nVidia is really pushing on Linux Drivers. Good! :guitar:

---

### Post by cmat on 2008-12-13
Support for the 8200 M? I can finally get rid of Vista!

---

### Post by mips on 2008-12-13
Will wait for it to appear in AUR which should be real soon or maybe I should just edit the package build for the 180.11 version, hmmm.

---

### Post by Shagg on 2008-12-13
Just tried 180.16 on intrepid 32bits  with a GeForce 7000m card, without any luck:

Installation went OK, and once I rebooted, the login screen worked with the right resolution. But as soon as I loged in, the screen went totally black, although the sound keeps on normally.

Any thoughts would be appreciated :p

---

### Post by Kosimo on 2008-12-14
I just made an easy how-to for new users in the first comment.

Hope it helps.

---

### Post by Phat Phreddy on 2008-12-15
> **Kosimo said:**
> I just made an easy how-to for new users in the first comment.

Hope it helps.

Just signed up to say thanks.. I have spent all yesterday trying EnvyNG, and all many of ways to put that on, all the other instructions looked highly intimidating. 

That solution was trivial.. And on reboot almost all my AWN problems have vanished !! 

Thanks from a noob.

---

### Post by MikeTheC on 2008-12-16
Any idea yet when Ubuntu will put this thing into the repos?

---

### Post by gardara on 2008-12-16
Does EnvyNG support 180 drivers?

---

### Post by cmat on 2008-12-16
> **gardara said:**
> Does EnvyNG support 180 drivers?

Not yet but I'm delaying my installation until it is.

---

### Post by chris4585 on 2008-12-16
I downloaded and installed the 180.16 beta driver successfully on 8.10, works beautifully, I'm happy

I run a nvidia 8400? I don't remember the exact model

---

### Post by gardara on 2008-12-16
> **cmat said:**
> Not yet but I'm delaying my installation until it is.

I think I'll do the same...
Has anyone heard from the developer? About ETA...

---

### Post by Trail on 2008-12-16
Hmm, I installed the latest beta (180.16 iirc) on a friend's PC on a new installation I performed for him, and while the drivers seemed to work (decent glxgears speed, glxinfo seemed to return normally), compositing would not be supported :| So I could not enable kde4-Kwin's compositing. Still the PC worked quite fine so I left it at that.

Any ideas, though? I'm just curious.

---

### Post by Kosimo on 2008-12-16
> **Phat Phreddy said:**
> Just signed up to say thanks.. I have spent all yesterday trying EnvyNG, and all many of ways to put that on, all the other instructions looked highly intimidating. 

That solution was trivial.. And on reboot almost all my AWN problems have vanished !! 

Thanks from a noob.

Nice to know that at least I could help someone ;) Looks difficult but is not :KS

By the way if you ever want to uninstall them, (for example when you want to install a newer version) just follow the same steps but when running the installer, add this line at the end ```
--uninstall 
``` it will remove everything. (you need to have the old installer)

---

### Post by Redrazor39 on 2008-12-16
Hey I've got the Geforce Go 7400 335MB card and I can't find this driver for that card. Could someone post a link to that for me?

---

### Post by Kosimo on 2008-12-16
> **Redrazor39 said:**
> Hey I've got the Geforce Go 7400 335MB card and I can't find this driver for that card. Could someone post a link to that for me?

GeForce 7xxx should be supported by the latest driver: 180.16

Did you try to install it?

---

### Post by AaronP_ on 2008-12-16
> **Kosimo said:**
> Nice to know that at least I could help someone ;) Looks difficult but is not :KS

By the way if you ever want to uninstall them, (for example when you want to install a newer version) just follow the same steps but when running the installer, add this line at the end ```
--uninstall 
``` it will remove everything. (you need to have the old installer)
You don't need the .run package for that, you can just run (as root)
```
nvidia-installer --uninstall
```
or starting with recent beta drivers, the convenience symlink
```
nvidia-uninstall
```

---

### Post by Kosimo on 2008-12-16
> **AaronP_ said:**
> You don't need the .run package for that, you can just run (as root)
```
nvidia-installer --uninstall
```
or starting with recent beta drivers, the convenience symlink
```
nvidia-uninstall
```

Right :)
Thanks for the clarification!

---

### Post by atorch on 2008-12-16
Will 180.* be added to intrepid-proposed?

---

### Post by wiebeest on 2008-12-16
> **atorch said:**
> Will 180.* be added to intrepid-proposed?
 
I wonder the same. 
Or will we have to wait untill Jaunty...?

---

### Post by FokkerCharlie on 2008-12-16
There's a decent chance, I think that we will have to wait until it's (at least more) stable!

In particular, many users are having a problem resuming from standby mode.  Until that's fixed, I see no reason to allow an unfinished driver into the repos!

Charlie

---

### Post by Paqman on 2008-12-16
> **atorch said:**
> Will 180.* be added to intrepid-proposed?

[Launchpad says yes]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/")

---

### Post by Kosimo on 2008-12-16
> **atorch said:**
> Will 180.* be added to intrepid-proposed?



Why don't you install the drivers by yourself? It is very easy, just follow the steps on the first post :p

---

### Post by Vadi on 2008-12-17
Don't bother. See benchmarks: [http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1)

---

### Post by FuturePilot on 2008-12-17
> **Vadi said:**
> Don't bother. See benchmarks: [http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1)

WOW :guitar:

---

### Post by Paqman on 2008-12-17
> **Vadi said:**
> Don't bother. See benchmarks: [http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1)

Er, that's a very positive review dude. Looks like it's well worth installing. Xrender performance is a huge improvement.

---

### Post by atorch on 2008-12-17
> **Kosimo said:**
> Why don't you install the drivers by yourself? It is very easy, just follow the steps on the first post :p

You were right, thanks for calling me out on that.

I've installed them (180.16 on 64 bit), and I immediately noticed a performance improvement.  This is great!  Now, I'm almost afraid to try suspend & resume since I've been hearing that they're broken.

// Edit:  Resume is broken:  the screen stays black & I'm forced to do an ugly reboot (hold the power button until my laptop shuts down).

// Another Edit:  But Hibernate works, which is nice.

I'd suggest that System > Hardware Drivers list the 180.* drivers (ie users have the option to install, but are not forced) as soon as the resume issue is fixed.  What do you guys think?

---

### Post by jespdj on 2008-12-17
> **Vadi said:**
> Don't bother. See benchmarks: [http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1)

Did you read the conclusion? Sounds like the 180 series driver is great!

> There were a few OpenGL tests where the performance of NVIDIA's binary Linux drivers had improved this year, but the main area of improvement when it comes to performance was with the 2D / X Render support. In both GtkPerf and QGears2 there was dramatically better performance in the more recent driver releases thanks to many optimizations from this Santa Clara company. The only area there was major performance regressions worth noting were in a few of the WINE tests.

Aside from the performance, this year the NVIDIA Linux driver has most notably picked up support for the Video Decode and Presentation API for Unix, which is terrific for offloading the video decoding process and related tasks to the GPU instead of the CPU. Using a $20 processor and $30 graphics card we were even able to watch HD videos on Linux. There weren't many new features made available this year in the NVIDIA Linux driver when compared to AMD, but of course NVIDIA has already had CoolBits, Scalable Link Interface, and other features in all of their drivers for quite a while. What we still have yet to see from NVIDIA, however, is any open-source strategy.

---

### Post by c4rson on 2008-12-17
I am a super newbe to Ubuntu (messed with suse over the years a little). new to Ubuntu (love it) how do i find my installer code. nvidia geforce 440go. thanks n sorry if this is a dumb question.

---

### Post by Kosimo on 2008-12-17
> **c4rson said:**
> I am a super newbe to Ubuntu (messed with suse over the years a little). new to Ubuntu (love it) how do i find my installer code. nvidia geforce 440go. thanks n sorry if this is a dumb question.

Your card shouldn't be supported with this latest version.
I recommend you to install the proprietary drivers you can find in your system. Are you using Ubuntu Intrepid Ibex 8.10? 

Then just go to System-Administration-Hardware Drivers.

Ubuntu will do everything for you ;)

---

### Post by Polygon on 2008-12-17
> **Vadi said:**
> Don't bother. See benchmarks: [http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ayir_2008&num=1&single=1)

aka INSTALL THEM NOW ,2d rendering performance doubled!

---

### Post by mips on 2008-12-18
> **jespdj said:**
> Did you read the conclusion? Sounds like the 180 series driver is great!

+1

Unfortunately some people only look at performance. For a lot of benchmarks they kinda stayed the same. The more important thing for me is all the glitches they have fixed with the new drivers plus they added VDPAU support wich is really cool.

Stabality is probably more important to me in a video driver than major performace boosts.

---

### Post by Vadi on 2008-12-18
Are you kidding me?

This is -2D-. Not -3D-. Unless you're seeing your Metacity draw windows sloooowly, this won't affect you at all. This isn't 1980 where 2D improvements were "woah".

(VDPAU is useless for you unless you're using patched versions of software that supports it, too - and are on a $20-$30 card.)

---

### Post by Paqman on 2008-12-18
> **Vadi said:**
> 
This is -2D-. Not -3D-. Unless you're seeing your Metacity draw windows sloooowly, this won't affect you at all. This isn't 1980 where 2D improvements were "woah".


Unless you're a gamer 2D performance is a lot more useful than 3D.

---

### Post by Polygon on 2008-12-18
> **Vadi said:**
> Are you kidding me?

This is -2D-. Not -3D-. Unless you're seeing your Metacity draw windows sloooowly, this won't affect you at all. This isn't 1980 where 2D improvements were "woah".

(VDPAU is useless for you unless you're using patched versions of software that supports it, too - and are on a $20-$30 card.)

there was an entire thread that got locked i think on how crappy nvidia's 2d support was when you were not using compiz (which used 3d acceleration)....so 2d acceleration improvements are much needed with the nvidia linux drivers. 

not to mention they most likely fix bugs, so its generally a good idea to be at the latest version =P

---

### Post by Kosimo on 2008-12-18
At the moment... I'm 90% of the time using only 2D (No compiz) So, for me 2D improvements and stability + bugfixes is much more important than having 3fps more in quake wars.

---

### Post by Hells_Dark on 2008-12-18
The 3D was working well before (for a long time yet).
All i was waiting was good 2D !!!
Thanks nvidia ! I can resize and move my windows smoothly ! FINALLY !

(and i use compiz btw..)

---

### Post by Vadi on 2008-12-18
Most likely, your 2d fps is already 500fps+. I don't see how having 100 more would make any difference!

---

### Post by obsrv on 2008-12-18
This is what I get in log:


   [ 1207.556500] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
   [ 1582.203365] mtrr: no more MTRRs available
   [ 1582.203396] mtrr: no more MTRRs available
   [ 1795.082821] nvidia: disagrees about version of symbol struct_module
   [ 1839.203689] mtrr: no more MTRRs available
   [ 1839.203721] mtrr: no more MTRRs available
   [ 1972.610758] nvidia: disagrees about version of symbol struct_module
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
obsrv@pirate:~$ 

Kernel-source is available and symlinked, precompiled interfaces on nvidia ftp not found and so on. What info I should provide more?

---

### Post by obsrv on 2008-12-19
I managed to run the driver, but I get a lot of glitches in Compiz-Fusion.

---

### Post by Paqman on 2008-12-19
> **Vadi said:**
> Most likely, your 2d fps is already 500fps+. I don't see how having 100 more would make any difference!

Xrender performance was notoriously bad on the 170-series drivers. I believe there was also problems with artifacts in window decoration on KDE4. There's been a flood of reports that this driver sorts both.

---

### Post by mips on 2008-12-19
> **Paqman said:**
> Xrender performance was notoriously bad on the 170-series drivers. I believe there was also problems with artifacts in window decoration on KDE4. There's been a flood of reports that this driver sorts both.

Vadi does not care about that, he only sees performance and thats it.

---

### Post by Vadi on 2008-12-19
> **Paqman said:**
> Xrender performance was notoriously bad on the 170-series drivers. I believe there was also problems with artifacts in window decoration on KDE4. There's been a flood of reports that this driver sorts both.

That's understandable then, valid reason if you're actually negative affected by the current recommended drivers.

---

### Post by Insane_Homer on 2008-12-23
[180.18]("ftp://download.nvidia.com/XFree86/Linux-x86/180.18/") release 19th Dec 

Install Instructions on [Page 4]("http://ubuntuforums.org/showthread.php?t=990978&page=4") of this thread.

EDIT:**[COLOR="Red"] WARNING [/COLOR]**180.18 broke my X (Sorry, I should have posted after attempting the install). I've reverted back to 180.16 for the moment.

---

### Post by MikeTheC on 2008-12-23
My answer remains the same...

I'll wait until the Ubuntu maintainers have gotten through beating on it and release it to the masses...

---

### Post by FokkerCharlie on 2008-12-23
Has anyone successfully suspended and resumed with this driver yet?

Charlie

---

### Post by wieman01 on 2008-12-23
I have trouble with my NVIDIA legacy adapter, a GeForce FX 5900XT.

Does anybody know if this driver will also take care of legacy hardware? If not, where will I get the drivers from?

This issue keeps me from upgrading to 8.10.

---

### Post by wieman01 on 2008-12-23
I have trouble with my NVIDIA legacy adapter, a GeForce FX 5900XT.

Does anybody know if this driver will also take care of legacy hardware? If not, where will I get the drivers from?

This issue keeps me from upgrading to 8.10.

---

### Post by mips on 2008-12-23
[COLOR=Red][B]Apologies, I did a CTRL-F to search the model and found it not realising the text to the top says it is only supported by legacy driver!

Please ignore my post below.
[/B][/COLOR]
> **wieman01 said:**
> I have trouble with my NVIDIA legacy adapter, a GeForce FX 5900XT.

Does anybody know if this driver will also take care of legacy hardware? If not, where will I get the drivers from?

This issue keeps me from upgrading to 8.10.

The FX 5900XT is supported, see post #128 or [ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html)

The latest driver 180.18 can be found here 

[ftp://download.nvidia.com/XFree86/Linux-x86/180.18/](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/)
[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/)
[ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/index.html)

---

### Post by wieman01 on 2008-12-23
Thank you, Mips. Great news.

---

### Post by mips on 2008-12-23
> **wieman01 said:**
> Thank you, Mips. Great news.

Good luck, let us know how it goes.

---

### Post by gissi on 2008-12-23
Just a hint, the Nvidia FX 5900XT card is NOT supported on 180.x, only the cards on series 6 or above. The driver for FX 5900XT is 173.14.

---

### Post by mips on 2008-12-23
> **gissi said:**
> Just a hint, the Nvidia FX 5900XT card is NOT supported on 180.x, only the cards on series 6 or above. The driver for FX 5900XT is 173.14.

If that is the case then nVidia must be straight out lying their asses off! 

According to this it is supported, [ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html)

---

### Post by AaronP_ on 2008-12-23
> **mips said:**
> If that is the case then nVidia must be straight out lying their asses off! 

According to this it is supported, [ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/README/appendix-a.html)
[quote=Appendix A]
[...]
The 173.14.xx driver supports the following set of GPUs:
[...]
GeForce FX 5900XT 	0x0332
[/quote]
.

---

### Post by zim2dive on 2008-12-23
I had installed 177.82 manually (needed for HDMI audio) and now appear to have removed TOO much (per the threads at nvnews and a few mentions here).

When I run pkg1 for 180.18 I get an error saying it can;t find the kernel-source .. what do I need to (re)install to get it to work?

thanks,
Mike

---

### Post by pelle.k on 2008-12-23
> I had installed 177.82 manually (needed for HDMI audio) and now appear to have removed TOO much (per the threads at nvnews and a few mentions here).

What you need to install the nvidia drivers are;
linux-headers-generic build-essential libx11-dev

---

### Post by zim2dive on 2008-12-23
has anyone gotten 180.18 installed?  if so, please list the steps you used.  I currently have 177.82 installed (by hand upgrade from the default 177.80 in Intrepid).

the steps I normally use do not seem to be sufficient for 180.18, works just fine for 180.16 (tho 180.16 is terribly unstable for me and causing massive crashing)

---

### Post by Vadi on 2008-12-23
> **AaronP_ said:**
> .

Welcome to the forums, Aaron!

---

### Post by ushimitsudoki on 2008-12-23
> **zim2dive said:**
> has anyone gotten 180.18 installed?  if so, please list the steps you used.  I currently have 177.82 installed (by hand upgrade from the default 177.80 in Intrepid).

the steps I normally use do not seem to be sufficient for 180.18, works just fine for 180.16 (tho 180.16 is terribly unstable for me and causing massive crashing)

I installed 180.18 just like normal (read: downloaded them from the NVIDIA FTP site, killed X, and ran the installer). No problems there, but I did see someone on the NVIDIA forums was having trouble installing them.

---

### Post by zim2dive on 2008-12-23
> **ushimitsudoki said:**
> I installed 180.18 just like normal (read: downloaded them from the NVIDIA FTP site, killed X, and ran the installer). No problems there, but I did see someone on the NVIDIA forums was having trouble installing them.

Not working for me at all.... just posted details to nvnews... [http://www.nvnews.net/vbulletin/showpost.php?p=1883895&postcount=27](http://www.nvnews.net/vbulletin/showpost.php?p=1883895&postcount=27)

---

### Post by mips on 2008-12-24
> **AaronP_ said:**
>  					Originally Posted by **Appendix A** 					 				
 				[I][...]
The 173.14.xx driver supports the following set of GPUs:
[...]
GeForce FX 5900XT 	0x0332[/I]



:redface: My bad, I just did a CTRL-F to search and found the model not seeing that section above it.

---

### Post by mips on 2008-12-24
> **wieman01 said:**
> Thank you, Mips. Great news.

Sorry to get you all excited but I made a mistake by not scrolling up and reading the text. Your card is not supported by the new driver.

---

### Post by AaronP_ on 2008-12-24
> **mips said:**
> :redface: My bad, I just did a CTRL-F to search and found the model not seeing that section above it.
Don't feel bad, you're definitely not the first person to do that.  I'll see about getting the layout changed to make it more obvious.

---

### Post by mips on 2008-12-25
> **AaronP_ said:**
> Don't feel bad, you're definitely not the first person to do that.  I'll see about getting the layout changed to make it more obvious.

I don't see the logic of even listing the legacy cards. If it's not there it's not supported and don't mention it. Those lists are so long you have no option but to ctrl-f to do a search and in the process you miss out information like I did.

---

### Post by wieman01 on 2008-12-25
> **mips said:**
> Sorry to get you all excited but I made a mistake by not scrolling up and reading the text. Your card is not supported by the new driver.
Oh man... yes, I do see it now as well. Oh well, not your fault. Guess I need new hardware at one point in time anyway.

Thanks for your support, dude!

_**EDIT:**_
I will try the other version though. Maybe I get around upgrading my hardware, who knows.

---

### Post by mips on 2008-12-25
> **wieman01 said:**
> .... Oh well, not your fault. Guess I need new hardware at one point in time anyway.

Thanks for your support, dude!

_**EDIT:**_
.... Maybe I get around upgrading my hardware, who knows.


The XFX 9600GT is a one cool card if you consider upgrading and have a PCI-E slot+PSU to match ;)

---

### Post by Kosimo on 2008-12-25
WoW guys... I've been playing Unreal Tournament 2004... I'm impressed with the overall performance, (even using Antialiasing 4x and Anisotropic 2x) in a "normal" Geforce Mobile 8400.

---

### Post by cb34 on 2008-12-27
glxgears was screwed up with 180.18 drivers, getting nly 4-5 fps..
and i was getting some errors on system boot and in xservererrors somethin about xgl not loading..(everything seemed to be working besides that).. went back to 170.82 drivers, and glxgears is back to normal getting 4000+ fps and no errors anymore.. also glxgears would only run as root, now its normal, no sudo needed.. was some file /dev/nvidiactl that has wrong permissions, and even after modifying permissions, nvidia changes that file all the time.

sometething was funky for me with my 8800GT and 180.18 drivers.
so now i'm using 170.82 and everything seems fine..

was tricky going back and forth between drivers, kernel module problems, but i think that was just me and the way i did things, now all is good after a good purging of all nvidia packages and files and a reinstall.

180.18 didn't work so well for me.

i suggest for anyone to open a terminal and try glxgears and see if all is fine.
and to check in their home dir the log file .xsession-errors for any nvidia errors, i had a few hiding in there.

peace.

---

### Post by Kosimo on 2008-12-28
> **cb34 said:**
> glxgears was screwed up with 180.18 drivers, getting nly 4-5 fps..
and i was getting some errors on system boot and in xservererrors somethin about xgl not loading..(everything seemed to be working besides that).. went back to 170.82 drivers, and glxgears is back to normal getting 4000+ fps and no errors anymore.. also glxgears would only run as root, now its normal, no sudo needed.. was some file /dev/nvidiactl that has wrong permissions, and even after modifying permissions, nvidia changes that file all the time.

sometething was funky for me with my 8800GT and 180.18 drivers.
so now i'm using 170.82 and everything seems fine..

was tricky going back and forth between drivers, kernel module problems, but i think that was just me and the way i did things, now all is good after a good purging of all nvidia packages and files and a reinstall.

180.18 didn't work so well for me.

i suggest for anyone to open a terminal and try glxgears and see if all is fine.
and to check in their home dir the log file .xsession-errors for any nvidia errors, i had a few hiding in there.

peace.

glxgears works perfectly for me and 180.18. Where you using compiz?

---

### Post by Vadi on 2008-12-28
Even if he were, disabling compiz shouldn't be the solution.

---

### Post by shadylookin on 2008-12-28
The 180.xx is the only one that I was able to get working with the new kernel 2.6.28

---

### Post by hotweiss on 2008-12-28
Installing 180 drivers over the Nvidia drivers installed by Envy will create a nightmare. Installing the 180 drivers after a clean install is a painless process. Mind you, I didn't see any performance improvements between the 177 and 180 drivers.

---

### Post by cb34 on 2008-12-28
> **Kosimo said:**
> glxgears works perfectly for me and 180.18. Where you using compiz?yes i did have compiz on and running.. everything else seemed smooth, that's why it was wierd, glxgears needed sudo to run without error, and then with sudo glxgears, it wasn't movin.. like 4fps..haha.. purged all nvidia, re-installed 177.82, back to ~5000fps... ?????
but everything else did seem normal.. like spinning the 3d cube for instance, was working all normal and smooth.

---

### Post by Kosimo on 2008-12-28
> **cb34 said:**
> yes i did have compiz on and running.. everything else seemed smooth, that's why it was wierd, glxgears needed sudo to run without error, and then with sudo glxgears, it wasn't movin.. like 4fps..haha.. purged all nvidia, re-installed 177.82, back to ~5000fps... ?????
but everything else did seem normal.. like spinning the 3d cube for instance, was working all normal and smooth.

Strange... It can be a glxgears bug maybe? Anyway if everything else is working fine... I strongly recommend you to use 180.18. It has a much better performance and stability than 177.xx

ps: unless you're a glxgears freak ;)

---

### Post by NTolerance on 2008-12-29
I installed the 180 drivers from the Jaunty repo.  It fixed my issues with window border artifacts but re-introduced a libGL.so crash when switching to the guest session.  This causes gnome-settings-daemon to crash and makes the desktop unusable.  This is with a 7400 GO card.

:(

---

### Post by Vadi on 2008-12-29
> **Kosimo said:**
> Strange... It can be a glxgears bug maybe? Anyway if everything else is working fine... I strongly recommend you to use 180.18. It has a much better performance and stability than 177.xx

You're recommending people to use beta drivers even as it breaks stuff for them and others report on difference in speed a few posts above?

---

### Post by BGFG on 2008-12-29
Just installed, as per the instruction for the OP, but on attempt to restart GDM i get a message saying that 177 is loaded in the kernel but it doesn't matchthe 180 driver.
Which is obvious.
As such, x is saying 'no x screen found'. How can i remedy this guys ?
Thank god for the live cd :)

---

### Post by wd5gnr on 2008-12-29
BGFG: in your /etc/X11/xorg.conf does it say Driver "nv" or Driver "nvidia"? Should be "nvidia"

---

### Post by zim2dive on 2008-12-29
Has anyone gotten 180.18 installed on a machine with the nVidia 8200 and Intrepid?

I can install .11 and .16 (both very unstable for me), but not .18

---

### Post by BGFG on 2008-12-29
> **wd5gnr said:**
> BGFG: in your /etc/X11/xorg.conf does it say Driver "nv" or Driver "nvidia"? Should be "nvidia"

Thanks for the quick response :) Back up and running now:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Although when i go to system>>Admin>>Hardware Drivers, Nvidia 177 is not in use but i do not see 180. How can i tell that 180 is in use for sure ?

180.18 Didn't work. Got 180.17 on though....

---

### Post by josephpmh on 2008-12-29
I just tried to install the 180.18 (and .17) but I ended with an error msg:

ERROR: API mismatch: the NVIDIA kernel module has version 169.12 but NVIDIA driver companent has 180.18 (or .17).

I have GeForce 7100/nforce 630i with U-8.04

I'm about to revert to 169.12 and will check back to see about how I can tell the kernel mode to switch to 180.xx

Ta.  This looks promising.  I may even upgrade to Intrepid Ibex if this works.

---

### Post by Kosimo on 2008-12-29
> **Vadi said:**
> You're recommending people to use beta drivers even as it breaks stuff for them and others report on difference in speed a few posts above?

Yes.

---

### Post by fizban9 on 2008-12-29
Alright, I've read all 27 pages and I think I'm ready to ask my question.  I'm looking to upgrade my video card, I'm having issues (read: stutters) playing hidef content from sights like hulu and youtube.  Right now I'm running a geforce 7900gt with the 169.12 nvidia drivers on Hardy.

I'm thinking of buying an 8800gts from newegg.  Yesterday I read another forum, as long as this one, about how the 8/9k nvidia cards suck at xrender.  Now i've read this forum that says it's fixed?

On top of that I use compiz, so theres a chance it doesn't even matter for me because compiz is 3d?  

Can anyone shed some light on the matter? :confused:

---

### Post by andamaru on 2008-12-29
> **fizban9 said:**
> Alright, I've read all 27 pages and I think I'm ready to ask my question.  I'm looking to upgrade my video card, I'm having issues (read: stutters) playing hidef content from sights like hulu and youtube.  Right now I'm running a geforce 7900gt with the 169.12 nvidia drivers on Hardy.

I'm thinking of buying an 8800gts from newegg.  Yesterday I read another forum, as long as this one, about how the 8/9k nvidia cards suck at xrender.  Now i've read this forum that says it's fixed?

On top of that I use compiz, so theres a chance it doesn't even matter for me because compiz is 3d?  

Can anyone shed some light on the matter? :confused:

Which version of flash are you running? I believe flash versions less than 10 don't have video card(GPU) acceleration.

---

### Post by pelle.k on 2008-12-30
> Now i've read this forum that says it's fixed?
I don't know if you can call it "fixed" since from what i understand, the nvidia developers use some workarounds in the driver replacing some functionality of xorg (which is why we have flicker free Xrender, Xvideo and openGL, when ATI does not, well at least not until xorg server 1.6 and DRI2), but the downside is that 2D and xrender is apparently not apparently rendering as fast ATI does it. However, there is clearly an improvement over the 177 series driver, but don't know if that means it really "fixed".
Please, correct me on the technical details.

---

### Post by cb34 on 2008-12-30
> **Kosimo said:**
> Strange... It can be a glxgears bug maybe? Anyway if everything else is working fine... I strongly recommend you to use 180.18. It has a much better performance and stability than 177.xx

ps: unless you're a glxgears freak ;)nah, i'm not a glxgear freak..LoL i dont really care about that, it just shows that something is not perfect with the driver for me, and i know my beast of a vid card is not the problem, so even if everything 'seems' to be working, that's not enough for me when it comes to the main nvidia drivers.

p.s. i've even tried it all over again installing the 180.18 drivers, and what i did notice what really bothered me was, my GPU temp was up by 3 degrees, i'dling at 49 with an idle computer, and with the 177.82 drivers temps are sitting at 46 stable, all the time.. i made sure all variables are the same for many hours.. i know my card temps.

so there's somethin goin on i don't like.

---

### Post by fizban9 on 2008-12-30
> **andamaru said:**
> Which version of flash are you running? I believe flash versions less than 10 don't have video card(GPU) acceleration.

My flash is version 10,0,12,36

---

### Post by zeronothing on 2008-12-30
yea, this driver works really well. I'm not having the awkward window manager problems. plus it seems to have boosted the acceleration quite a bit. I'm only using a 6800 XT. that should say something..

---

### Post by josephpmh on 2008-12-30
OK, I am having all sorts of problems since trying to switch and even switch back to my original driver.  Now Ubuntu doesn't recognize my nvidia GeForce 7100/nforce 630i.  When I have to start in  low grafix mode, I have to reinstall the Nvidia driver, which then sez I gotta reboot, which I do, which takes me back to no recognized 7100/630i. After doing this several times, and reverting to the 169.12 driver, I'm at my wit's end and need to seek the help of a higher power (the forum). 

I have a dell 1504fp screen.  I built the pc, run 8.04 on it.  HDD is 500GB. Intel Core Duo 7200; 2GB RAM (being read as 1762 MiB RAM).  

I would love to have the 180.18 or .17 working, but, at this point, I'd be happy if I can get the 169.12 working.

---

### Post by jespdj on 2008-12-30
> **fizban9 said:**
> Alright, I've read all 27 pages and I think I'm ready to ask my question.  I'm looking to upgrade my video card, I'm having issues (read: stutters) playing hidef content from sights like hulu and youtube.  Right now I'm running a geforce 7900gt with the 169.12 nvidia drivers on Hardy.
Are you sure this is because the video card is not powerful enough? Can you play video locally (not streamed from Internet, but from your harddisk, or a DVD for example) without stuttering?

An nVidia 7900GT is not a bad video card, so I highly doubt that the problem is your video card; getting a new video card might not solve your problem.

---

### Post by zim2dive on 2008-12-30
> **jespdj said:**
> Are you sure this is because the video card is not powerful enough? Can you play video locally (not streamed from Internet, but from your harddisk, or a DVD for example) without stuttering?

An nVidia 7900GT is not a bad video card, so I highly doubt that the problem is your video card; getting a new video card might not solve your problem.

Given the issues I've had with my 8200 (and having to go backwards in drivers to 173 to get any success), I can't say I'm surprised.  For me the issue was Flash content from hulu HD and The Daily Show.  YouTube was ok.  Under 177 _and_ 180, life was miserable.  Going back to 173 (the non-recommended option in Intrepid) solved my video, but killed my HDMI audio.. so for now I will live with the 6-channel analog outputs.  Crazy stuff.  mplayer/vlc was fine with all the drivers, Flash was the only video that seemed to vary drastically based on which nvidia driver I used.

---

### Post by mips on 2008-12-30
> **jespdj said:**
> 
An nVidia 7900GT is not a bad video card, so I highly doubt that the problem is your video card; getting a new video card might not solve your problem.

+1 My 6600 played all videos just fine.

---

### Post by HunterK on 2008-12-30
WOW.  

I just fresh installed 8.10 yesterday and was using 177 for a little while and I something just didnt feel right.  

Since I used envyng to install 177, I used it to remove it as well. I then proceeded to use the instructions on Page 4 to install the 180.18 drivers.  Upon reboot, compiz was already enabled and things just felt so fast!  I can definitely tell a difference by just clicking around in Firefox.  Not to mention the greatly improved responsiveness of the entire GUI.

---

### Post by andamaru on 2008-12-31
> **fizban9 said:**
> My flash is version 10,0,12,36

then it should get some acceleration from your card, do you have a sample hi-def flash video for use to use. I've only seen one, and it was on my desktop so I'm not sure if the card was the problem.

---

### Post by TheAL76 on 2009-01-05
Hey guys,

I have a GeForce 8600GT. I'm considering upgrading the driver from the 177.80 that Ibex provides to 180.18. 

Couple of questions:

1. If 180.18 doesn't work, how do I restore the original 177.80 driver?
2. When kernel updates come through, will I have to re-run the nvidia driver installation?
3. Do I need to disable the 177.80 driver in the restricted drivers menu before installing 180.18?

Thanks,

TheAL76

---

### Post by Vadi on 2009-01-05
> **TheAL76 said:**
> 1. If 180.18 doesn't work, how do I restore the original 177.80 driver?
2. When kernel updates come through, will I have to re-run the nvidia driver installation?
3. Do I need to disable the 177.80 driver in the restricted drivers menu before installing 180.18?


1) Depends on how did you install it. If from a package, then just going to the Hardware Driver and enabling the 177.80 one should work. If from nvidia's installed, and you *firstly* uninstalled current driver, then you uninstall nvidia, and install driver back. If you used nvidia's installed with 177.80 installed and overwrote things, it'll get screwed and you're pretty much stuck with nvidia drivers until a reinstall unless you can fix the files.
2) Yeah. Nvidia drivers will break.
3) It's recommended, see above.

---

### Post by TheAL76 on 2009-01-05
> **Vadi said:**
> 1) Depends on how did you install it. If from a package, then just going to the Hardware Driver and enabling the 177.80 one should work. If from nvidia's installed, and you *firstly* uninstalled current driver, then you uninstall nvidia, and install driver back. If you used nvidia's installed with 177.80 installed and overwrote things, it'll get screwed and you're pretty much stuck with nvidia drivers until a reinstall unless you can fix the files.
2) Yeah. Nvidia drivers will break.
3) It's recommended, see above.

Thanks Vadi!:D

I will disable 177.80 in the restricted menu first, then install 180.18. 

Am I right in assuming the highest numbered pkg file is the correct one? I see pkg2 on the FTP site.

Sorry for all the questions, nvidia driver installations make me nervous!

---

### Post by Vadi on 2009-01-05
Yeah, use pkg2. I don't know why do they put multiple versions, but pkg2 is what I was told to use.

---

### Post by TheAL76 on 2009-01-05
Excellent. I'm looking forward to trying it when I get home, and will post about my experience.

Thanks again,

TheAL76

---

### Post by TheAL76 on 2009-01-05
Great success so far...thanks!

Deactivated the 177.80 driver in the Restricted Drivers menu, then followed the directions, it installed effortlessly.

Cheers,

TheAL76

---

### Post by Aries K on 2009-01-07
Here is an easier and safer way to install the driver. Doing it this way gives you the modaliases too. :D

[http://www.nvnews.net/vbulletin/showthread.php?p=1894313](http://www.nvnews.net/vbulletin/showthread.php?p=1894313)

(See ThomasC's posts)

---

### Post by zim2dive on 2009-01-07
> **Aries K said:**
> Here is an easier and safer way to install the driver. Doing it this way gives you the modaliases too. :D

[http://www.nvnews.net/vbulletin/showthread.php?p=1894313](http://www.nvnews.net/vbulletin/showthread.php?p=1894313)

(See ThomasC's posts)

Will 180.18 show up as a choice in the hardware driver panel when you use his PPA?  (making it easy to switch back up/down to 173/177)

---

### Post by TheAL76 on 2009-01-07
Damn, now I wish I'd waited a day to try 180.18, and used the method Aries K posted.

Is it difficult to uninstall the driver I installed manually? How do I uninstall it?

Edit: OK, looks like all I need to do is rerun the installer with the --uninstall flag. Easy enough.

---

### Post by forrestcupp on 2009-01-07
> **TheAL76 said:**
> Damn, now I wish I'd waited a day to try 180.18, and used the method Aries K posted.

Is it difficult to uninstall the driver I installed manually? How do I uninstall it?

Edit: OK, looks like all I need to do is rerun the installer with the --uninstall flag. Easy enough.

or
```
sudo apt-get remove --purge nvidia*
```

---

### Post by Aries K on 2009-01-07
> **zim2dive said:**
> Will 180.18 show up as a choice in the hardware driver panel when you use his PPA?  (making it easy to switch back up/down to 173/177)

Yep, it will show up just like it is an official driver in the panel giving you the ability to switch back to 173/177 if you have any problems with it or when the final driver gets released in the repos. :)

---

### Post by zim2dive on 2009-01-08
> **Aries K said:**
> Yep, it will show up just like it is an official driver in the panel giving you the ability to switch back to 173/177 if you have any problems with it or when the final driver gets released in the repos. :)

When I try to add via aptitude I get
```
The following packages will be REMOVED:
  gnash-common{u} kdelibs-data{u} kdelibs4c2a{u} libarts1c2a{u} libavahi-qt3-1{u} libboost-date-time1.34.1{u} 
  libboost-thread1.34.1{u} libifp4{u} liblua50{u} liblualib50{u} libnjb5{u} libqt3-mt{u} libruby1.8{u} libtunepimp5{u} 
  libxcb-shape0{u} libxcb-shm0{u} libxcb-xv0{u} libxine1{u} libxine1-console{u} libxine1-misc-plugins{u} libxine1-x{u} 
  nvidia-173-kernel-source{a} nvidia-glx-173{a} ruby{u} ruby1.8{u}
```

I don't know that I care about most of those, but I dont think I want any of 173 to be removed??? ie. I want it to be there so I can easily switch back to it. Also why is 173 removed but not 177 (both are listed in my Hardware drivers panel, 173 is the current active one)

thanks,
Mike

---

### Post by forrestcupp on 2009-01-08
> **zim2dive said:**
> When I try to add via aptitude I get
```
The following packages will be REMOVED:
  gnash-common{u} kdelibs-data{u} kdelibs4c2a{u} libarts1c2a{u} libavahi-qt3-1{u} libboost-date-time1.34.1{u} 
  libboost-thread1.34.1{u} libifp4{u} liblua50{u} liblualib50{u} libnjb5{u} libqt3-mt{u} libruby1.8{u} libtunepimp5{u} 
  libxcb-shape0{u} libxcb-shm0{u} libxcb-xv0{u} libxine1{u} libxine1-console{u} libxine1-misc-plugins{u} libxine1-x{u} 
  nvidia-173-kernel-source{a} nvidia-glx-173{a} ruby{u} ruby1.8{u}
```

I don't know that I care about most of those, but I dont think I want any of 173 to be removed??? ie. I want it to be there so I can easily switch back to it. Also why is 173 removed but not 177 (both are listed in my Hardware drivers panel, 173 is the current active one)

thanks,
Mike
173 is removed because that's the one you installed.  You can only have one installed at a time.  Removing it doesn't mean you won't be able to reinstall it.  It *has* to be removed to be able to install the new one.  You never had 177 installed, you just had the capability to install it.

---

### Post by anxiousdog on 2009-01-08
I have successfully installed 180.18 and my Compiz still isn't working. I keep getting:

> 
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size


---

### Post by cb34 on 2009-01-08
just to test.. (i already posted in here my experience with installing 180.18 driver in case you're wondering what im talkin about)

on a brand new install of debian, i installed the 180.18 driver, and like i said before, my GPU temp went up a few degrees doing nothing just idling, it idles at a higher temp, and also glxgears will not run for a regular user, it needs sudo, which is not normal. so it had nothing to do with maybe some tweaks i had in my setup or something before.

i properly uninstalled using the nvidia script, then installed my usual 177.82 driver, temps are back down a few degrees, glxgears runs fine without root access, and with no compiz i get about 9000-9500fps, with compiz on, half that, about 4000-4500, which is ok.. just saying.

so 180.18 doesn't work for me and my 8800GT.
177.82 works perfectly. :)

edit-> also i tried Arch Linux for a few dayz, and the exact same situation, GPU temp up and things didn't seem right.. 177.82 everything was fine.

peace.

---

### Post by akiratheoni on 2009-01-08
Can anyone confirm if this nvidia driver works with the nVidia Geforce 9500 GT?

I always had resolution issues with Ubuntu 8.10. I really want 8.10 but I'm stuck at 8.04... so if anyone can tell me if either xorg or the new nvidia driver works with it, that would be great.

---

### Post by Bachstelze on 2009-01-08
> **akiratheoni said:**
> Can anyone confirm if this nvidia driver works with the nVidia Geforce 9500 GT?

I always had resolution issues with Ubuntu 8.10. I really want 8.10 but I'm stuck at 8.04... so if anyone can tell me if either xorg or the new nvidia driver works with it, that would be great.

Which version of the driver did you try? Version 180.18 supports your GPU.

---

### Post by Kosimo on 2009-01-08
Finally a stable release!!!

Ladies and gentelman... Her the 180.22 (STABLE)
[URL="http://www.nvidia.com/object/linux_display_ia32_180.22.html"]
Download nVidia Linux 180.22[/URL]

---

### Post by Kosimo on 2009-01-08
Finally a stable release!!!

Ladies and gentleman... Her the 180.22 (STABLE)
[URL="http://www.nvidia.com/object/linux_display_ia32_180.22.html"]
Download nVidia Linux 180.22[/URL]

---

### Post by Kosimo on 2009-01-08
Guys, finally a stable release of the 180.xx series!


[Download the STABLE 180.22 release!]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by Kosimo on 2009-01-08
Guys, finally a stable release of the 180.xx series!  


[Download the STABLE 180.22 release!]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by Kosimo on 2009-01-08
Guys, finally a stable release of the 180.xx series!     


180.22

[Download the STABLE 180.22 release!]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by Kosimo on 2009-01-08
Guys, finally a stable release of the 180.xx series!     


180.22
  
[Download the STABLE 180.22 release!]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by Kosimo on 2009-01-08
Guys, finally a stable release of the 180.xx series!


[Download the STABLE 180.22 release!]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by Kosimo on 2009-01-08
Hey!
180.22 are FINALLY stable!!!   

[Download them]("http://www.nvidia.com/object/linux_display_ia32_180.22.html") from the official 180.22 nvidia webpage

---

### Post by Kosimo on 2009-01-08
Hey!    
180.22 are FINALLY stable!!!   

[Download them]("http://www.nvidia.com/object/linux_display_ia32_180.22.html") from the official 180.22 nvidia webpage

---

### Post by hugmenot on 2009-01-08
relax, man.

---

### Post by Kosimo on 2009-01-08
Guys, finally a STABLE version.  180.22 
[URL="http://www.nvidia.com/object/linux_display_ia32_180.22.html"]
Download them![/URL]

---

### Post by Kosimo on 2009-01-08
Guys, finally a STABLE version 180.22 

[Download]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

---

### Post by pelle.k on 2009-01-08
I think it's the forum acting up. Kosimo usually behaves.
Anyways, thanks for the news!

---

### Post by zim2dive on 2009-01-08
180.22 is out

[http://www.nvnews.net/vbulletin/showthread.php?t=125903](http://www.nvnews.net/vbulletin/showthread.php?t=125903)

---

### Post by Vadi on 2009-01-08
The 180 driver is in the ubuntu repositories now I think, intrepid-update

---

### Post by Kosimo on 2009-01-08
Holly sh!!!!!!   Sorry guys, ubuntuforums were in trouble, and so I...

I apologise for this hyper repeated post.

---

### Post by Rocket2DMn on 2009-01-08
I deleted the duplicate posts, we know the forum was acting today.  Thanks for the report, let us know of any more massive dups.

---

### Post by Kosimo on 2009-01-08
> **Rocket2DMn said:**
> I deleted the duplicate posts, we know the forum was acting today.  Thanks for the report, let us know of any more massive dups.

Thank you ;) I swear it wasn't on propose!

About 180.22. I'm testing them using Unreal Tournament 2004 and I felt some little performance regression compared to 180.18. I need some more time to check it out. Apart from that, everything else works as a charm.

---

### Post by zim2dive on 2009-01-08
I didn;t try 180.22 yet, but I can confirm that 180.18 does nothing to help full-screen flash on the 8200.. still chokes and dies on The Daily show and hulu HD (reverting to 173 fixes performance)

---

### Post by pelle.k on 2009-01-08
The suspend issue isn't fixed with 180.22 (release) yet, but they have confirmed the problem and responded that they are working on it. Some people on 2.6.28 say the have suspend working with the 180 series. The nvidia devs said there was a deadline on 180.22, but that they still continue work on unresolved issues (and probably fix it in a point release).

---

### Post by pt123 on 2009-01-08
> **Vadi said:**
> The 180 driver is in the ubuntu repositories now I think, intrepid-update

would they have it in Hardy?

---

### Post by Vadi on 2009-01-08
> **pt123 said:**
> would they have it in Hardy?

I'm not sure.

---

### Post by zim2dive on 2009-01-09
> **Vadi said:**
> The 180 driver is in the ubuntu repositories now I think, intrepid-update

I saw 180.18, but not 180.22 ? (just confirming)

---

### Post by pt123 on 2009-01-09
> **zim2dive said:**
> I saw 180.18, but not 180.22 ? (just confirming)

under what package name I searched for 180 and couldn't find it.

---

### Post by FuturePilot on 2009-01-09
> **zim2dive said:**
> I saw 180.18, but not 180.22 ? (just confirming)

> **pt123 said:**
> under what package name I searched for 180 and couldn't find it.

I only see 180.11
```
 apt-cache policy nvidia-glx-180
nvidia-glx-180:
  Installed: 180.11-0ubuntu1~intrepid1
  Candidate: 180.11-0ubuntu1~intrepid1
  Version table:
 *** 180.11-0ubuntu1~intrepid1 0
        500 http://us.archive.ubuntu.com intrepid-updates/restricted Packages
        100 /var/lib/dpkg/status

```

---

### Post by zim2dive on 2009-01-09
> **FuturePilot said:**
> I only see 180.11
```
 apt-cache policy nvidia-glx-180
nvidia-glx-180:
  Installed: 180.11-0ubuntu1~intrepid1
  Candidate: 180.11-0ubuntu1~intrepid1
  Version table:
 *** 180.11-0ubuntu1~intrepid1 0
        500 http://us.archive.ubuntu.com intrepid-updates/restricted Packages
        100 /var/lib/dpkg/status

```

I think it was in intrepid-proposed (I don't have access to my machine right now), or possible intrepid-backports (new to Ubuntu and still puzzling why its not more obvious to get to these for those that want to risk newer, less-test pkgs)

---

### Post by Bachstelze on 2009-01-09
> **zim2dive said:**
> I think it was in intrepid-proposed (I don't have access to my machine right now), or possible intrepid-backports (new to Ubuntu and still puzzling why its not more obvious to get to these for those that want to risk newer, less-test pkgs)

Because it's assumed that if you want to use the bleeding edge stuff, you have enough knowledge to install it yourself. And anyway, if you don't, you definitely should stick with the well-tested packages, because if the bleeding-edge ones break, you'll be in trouble.

---

### Post by bobbocanfly on 2009-01-09
I tried out 180.22 last night on my brand new 8600 GTS (Overclocking edition from MSI) and was pretty disappointed. It tanked my 3D framerate and I had massive stability issued when overclocking, which was disappointing seeing as the card I have is underclocked by default and is *designed* to be overclocked. I reverted to 177.82 and have had no problems since.

---

### Post by zim2dive on 2009-01-09
> **HymnToLife said:**
> Because it's assumed that if you want to use the bleeding edge stuff, you have enough knowledge to install it yourself. And anyway, if you don't, you definitely should stick with the well-tested packages, because if the bleeding-edge ones break, you'll be in trouble.

For most stuff I might agree.. the 180.18 and 180.22 (presumably) seems to cause more difficulty than usual for manual installs.. so being able to use a pkg was an especially big benefit.. also (and yes I'm new to this), I hadn't had much/any luck being able to roll back (via the Hardware driver panel or even by hand) to 173/177 after I did an upgrade by hand (to 180.x).. which became an expensive price to pay for being willing to test a beta driver.

The hardware driver panel (and how items get in to it or not) adds an additional layer of complexity, at least to those new to Ubuntu.

---

### Post by Bachstelze on 2009-01-09
> **zim2dive said:**
> 
The hardware driver panel (and how items get in to it or not) adds an additional layer of complexity, at least to those new to Ubuntu.

That's the price to pay for non-free drivers. Because they are non-free, they cannot be fully integrated into Ubuntu, which means Ubuntu has to resort to workarounds like this one. I fully agree with you when you say the driver manager adds a layer of complexity, and that's why I never use it and prefer to use the installers provided by nvidia (it is, after all, the way they're meant to be installed ;)).

---

### Post by hotweiss on 2009-01-09
180.22 drivers are working great for me...

---

### Post by pt123 on 2009-01-09
> **FuturePilot said:**
> I only see 180.11

Thanks installed 180.11 but why doesn't it appear in the Hardware Drivers section

---

### Post by Bachstelze on 2009-01-09
> **pt123 said:**
> Thanks installed 180.11 but why doesn't it appear in the Hardware Drivers section

How did you install them?

---

### Post by rajeev1204 on 2009-01-10
Do these drivers increase performance in games ?

I mean, the windows driver page always lists the percentage increase application wise, but in linux all it says is some bug fixes and support for newer cards.

I just installed windows 180 drivers jan 8 2009 and it lists a lot of increase in games upto 15 percent even.

Wonder what the linux version really does.Driver 177 crashes my desktop all the  time. I use 173.... something.

Also i never noticed any difference in performance from when i was using the older feisty drivers.


Oops --- forgot, linux is not for gaming.

---

### Post by user11 on 2009-01-10
Just goes into low graphics mode for me.

"(EE) Failed to load module "type1"(module does not exist, 0)"

Xubuntu 8.10
e-Geforce 6200 DDR2 256MB

I saved a log file somewhere if anyone is interested.:(

---

### Post by Vadi on 2009-01-10
> **rajeev1204 said:**
> Do these drivers increase performance in games ?

There was a diff between 173 and 177, but otherwise not by whole heaps. It's the same hardware after all :popcorn:

---

### Post by FuturePilot on 2009-01-10
> **pt123 said:**
> Thanks installed 180.11 but why doesn't it appear in the Hardware Drivers section

It's not going to. I think they've purposely prevented it from showing up in there due to it being a Beta driver.

---

### Post by zim2dive on 2009-01-10
> **Vadi said:**
> There was a diff between 173 and 177, but otherwise not by whole heaps. It's the same hardware after all :popcorn:

Unless you have an 8200.. in which case the "advance" from 173 to 177 (or 180) created a massive decrease in performance (at least for Full-screen Flash on hulu HD) :(

---

### Post by rajeev1204 on 2009-01-10
> **Vadi said:**
> There was a diff between 173 and 177, but otherwise not by whole heaps. It's the same hardware after all :popcorn:


I could never get 177 to work,right now iam using 173 version.177 just crashed my desktop when i launched Quake 4.

---

### Post by pt123 on 2009-01-10
> **HymnToLife said:**
> How did you install them?

using synaptic

> **FuturePilot said:**
> It's not going to. I think they've purposely prevented it from showing up in there due to it being a Beta driver.
Ok, Thanks

---

### Post by HunterK on 2009-01-11
I was running the 180.18 drivers flawlessly and decided to get the 180.22 stable.  I used the --uninstall option on the 180.18, and followed the same exact steps as before to install the 180.22 drivers.  Something is wrong.  Compiz and everything do work, but it is extremely sluggish.  Firefox pages scroll unbelievably slow. I am going to try going back to the .18 drivers again.

Ubuntu 8.10 32bit
GeForece 6800GT

---

### Post by fizban9 on 2009-01-11
> **jespdj said:**
> Are you sure this is because the video card is not powerful enough? Can you play video locally (not streamed from Internet, but from your harddisk, or a DVD for example) without stuttering?

I have the same trouble with hi-def videos playing from my own system as I do from the internet.  I'm starting to wonder if it's my Pentium-D thats bottlenecking my system.

I upgraded to Intrepid just to see if anything would get better.  It didn't, but nothing is worse.

---

### Post by OffHand on 2009-01-11
> **HunterK said:**
> I was running the 180.18 drivers flawlessly and decided to get the 180.22 stable.  I used the --uninstall option on the 180.18, and followed the same exact steps as before to install the 180.22 drivers.  Something is wrong.  Compiz and everything do work, but it is extremely sluggish.  Firefox pages scroll unbelievably slow. I am going to try going back to the .18 drivers again.

Ubuntu 8.10 32bit
GeForece 6800GT

I can't get .22 working at all on my machine. No user error, I know this stuff.

---

### Post by HunterK on 2009-01-11
> **OffHand said:**
> I can't get .22 working at all on my machine. No user error, I know this stuff.

That's good to know.  What card do you have?

EDIT:

Man, even, with compiz disabled, 2D performance is bad with the .22 drivers. Will revert back to .18 and see how things are.

---

### Post by Montblanc_Kupo on 2009-01-11
I installed the 180.22 driver after having used the 177 driver with My nvidia 6800. 177 worked pretty well, but had some occasional issues and caused some problems while playing certain games. 180.22 seems pretty stable, although I haven't really noticed any major improvement other than stability. No speed increase in rendering or anything. 

I did notice that now My GL screen savers (the ones that were preinstalled with Ubuntu 8.10) don't seem to work anymore. I can play games that use OpenGL and they're fine... but the previously working screensavers aren't. This isn't a huge problem, although I would like them back instead of just a blank screen, but I'm worried that it's indicative of some larger issue. I noticed when I looked in the nvidia manager that it doesn't identify My card type anymore where as 177 told Me it was a 6800.

Any ideas? I'm fairly new to linux so I'm not entirely sure where to check for things. I followed the basic installation instructions in this thread as well as checked for the prerequisites that were listed on the nvidia driver download page for ubuntu.

I'm going to try installing this on someone else's machine with a 7 series nvidia later to rectify some issues they're having hopefully... we'll see how that goes.

---

### Post by HunterK on 2009-01-11
> **Montblanc_Kupo said:**
> I installed the 180.22 driver  No speed increase in rendering or anything. 

it was a 6800.


I can definitely say for sure that 180.18 work MUCH better for me than the 180.22.  Everything is much more responsive on the desktop.  Compiz is smooth, videos don't shear, everything is snappy.  I have a 6800GT card as well, maybe you should try the 180.18 drivers?

32bit: [ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run)

64bit: [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run)

---

### Post by Montblanc_Kupo on 2009-01-12
> I can definitely say for sure that 180.18 work MUCH better for me than the 180.22. Everything is much more responsive on the desktop. Compiz is smooth, videos don't shear, everything is snappy. I have a 6800GT card as well, maybe you should try the 180.18 drivers?

After finding that simple gl objects in the desktop (like glxgears) were running at 5 fps, I removed the 180.22 driver and reverted to the 177. It's running like it was before... although it refuses to identify the card in the nvidia-xconfig for some reason and it used to have no issue ... not sure why.

Thanks for the link for the 180.18 drivers, I'll give those a try tomorrow when I'm more awake lol. :)

---

### Post by pelle.k on 2009-01-12
> I'm going to try installing this on someone else's machine with a 7 series nvidia later to rectify some issues they're having hopefully... we'll see how that goes.
You mind sharing what those problems are? Installing a BETA driver (even 180.22 should, at least according to me, be considered BETA) may end up causing more problems than the 177 driver.
I cant say i have had very many problems with the 177 other than the performance of it. So, what is the problem you are experiencing with 177.XX?
> I'm fairly new to linux
Another reason you should tell us about your problem. It may be something else causing your problem.

---

### Post by zim2dive on 2009-01-12
> **HunterK said:**
> That's good to know.  What card do you have?

EDIT:

Man, even, with compiz disabled, 2D performance is bad with the .22 drivers. Will revert back to .18 and see how things are.

Is setting Desktop effects to None the same thing as disabling compiz (or is there more that needs to be done to disable compiz?)

thanks,
Mike

---

### Post by ingvildr on 2009-01-12
With the 177.82 driver in ubuntu and my 9800 gt i cant get above 60 refresh and i was hoping the 180.22 would solve that but no, is anyone else with this card having the same problem?

---

### Post by AaronP_ on 2009-01-12
> **ingvildr said:**
> With the 177.82 driver in ubuntu and my 9800 gt i cant get above 60 refresh and i was hoping the 180.22 would solve that but no, is anyone else with this card having the same problem?
Sounds like your monitor is requesting a 60 Hz limit.  Try starting X with "startx -- -logverbose 6" and then check the mode validation log in /var/log/Xorg.0.log.  Look for the VertRefresh range and where it came from.  There's also a special flag for "60 Hz only".  You may need some of the options documented in the README; in particular, the "AllowNon60HzDFPModes" mode validation override.  Please note that many flat panels expect to be driven at exactly 60 Hz, and driving them at higher refreshes will result in suboptimal quality.

---

### Post by HunterK on 2009-01-12
> **zim2dive said:**
> Is setting Desktop effects to None the same thing as disabling compiz (or is there more that needs to be done to disable compiz?)

thanks,
Mike

I thought setting it to "None" would suffice.  Does it not?  That is the setting that you have when you do not have 3D drivers installed, so I am just assuming it is enough.

---

### Post by zim2dive on 2009-01-12
> **HunterK said:**
> I thought setting it to "None" would suffice.  Does it not?  That is the setting that you have when you do not have 3D drivers installed, so I am just assuming it is enough.

 had some folks telling to me disable compiz over at the nvnews forums (debugging the disproportionately poor full-screen flash on the 8200 vs. the other nvidia GPUs).. I thought this was accomplishing that, but I wanted to be sure I was testing as asked.

EDIT: by default, my Intrepid install had the effects turned on.  When I changed it to none I got a good boost in Flash performance, but not enough to get me back to the levels I saw with 173 (which was a good 15+ fps on hulu HD, vs the 1-2, and then 0 I get with 177/180)

---

### Post by Montblanc_Kupo on 2009-01-12
> **pelle.k said:**
> You mind sharing what those problems are? Installing a BETA driver (even 180.22 should, at least according to me, be considered BETA) may end up causing more problems than the 177 driver.

Two things mainly that I'm hoping to fix are:

1. Tearing / vanishing window menubars. This is a problem specifically listed as a known issue that is fixed by the 180 driver.

2. Can't access all of the resolutions capable for the monitor. Was running at 1400x1050 under windows, linux only sees 1280x1024 as the highest resolution and it keeps reverting to 1024x768 on reboot. 

Tried the 173 and 177 drivers through hardware devices (Ubuntu 8.10) and no dice, so I figured I would give 180 a shot.

> Another reason you should tell us about your problem. It may be something else causing your problem.

I'm new to being a full time linux user, but I'm spending a lot of time reading and tweaking... and I have been using computers for a long long long time heh. I do appreciate the great community for ubuntu though... even though My first question on the forums never got even close to answered hehe.

---

### Post by cb34 on 2009-01-12
about the resolution, you should try using nvidia-settings to set the resolution or look into modifying your xorg.conf to add the resolutions you want in there. using the built in ubuntu screen resolution tab under preferences never worked for me, so i dont use it.

---

### Post by pelle.k on 2009-01-12
> 2. Can't access all of the resolutions capable for the monitor. Was running at 1400x1050 under windows, linux only sees 1280x1024 as the highest resolution and it keeps reverting to 1024x768 on reboot.
I can't help you with the first one, but i might know how to fix the second problem.

Add a "monitor" section to xorg.conf, like this;
```
Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1400x1050_60.00"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync
EndSection

```

And, put this *inside* the "screen" section;
```
        Subsection "Display"
                Depth       24
                Modes       "1400x1050_60.00" "1024x768" "800x600" "640x480"
                ViewPort    0 0
        EndSubsection

```

IMPORTANT, i created the modeline with "gtf", which is a command line tool to calculate these things, but i don't know if this (as in *my* result) is universal, so you might want to double check that it is the same for you, on your laptop.

**Sorry for the OT guys...**

---

### Post by lyceum on 2009-01-12
I have to agree. When I first started using Kubuntu I was happy with the way my nVidia card worked, but now, everything looks just amazing.

---

### Post by jkratze1 on 2009-01-12
> **user11 said:**
> Just goes into low graphics mode for me.

"(EE) Failed to load module "type1"(module does not exist, 0)"

Xubuntu 8.10
e-Geforce 6200 DDR2 256MB

I saved a log file somewhere if anyone is interested.:(

I get this error with 180.22 version driver on my 9600M GT.  Going back to 180.17 which works fine.

---

### Post by cb34 on 2009-01-12
i've alwayz had that type1 doesn't exist warning also, from day 1, and it never caused any problems.

---

### Post by adamlau on 2009-01-12
For those of you on minimal installs, you will need to:

```
sudo apt-get linux-headers-generic
```

In order to compile the NVIDIA drivers against your kernel.

---

### Post by Montblanc_Kupo on 2009-01-14
> **adamlau said:**
> For those of you on minimal installs, you will need to:

```
sudo apt-get linux-headers-generic
```

In order to compile the NVIDIA drivers against your kernel.

Shouldn't that be:

```
sudo apt-get install linux-headers-generic
```

[quote="cb34"]about the resolution, you should try using nvidia-settings to set the resolution or look into modifying your xorg.conf to add the resolutions you want in there. using the built in ubuntu screen resolution tab under preferences never worked for me, so i dont use it.[/quote]

Yeah... the built in doesn't work very well heh... I only use the nvidia manager for it.

[quote="pelle.k"]I can't help you with the first one, but i might know how to fix the second problem.

Add a "monitor" section to xorg.conf, like this.......[/quote]

That's terrifying... ... I'll do it! hehe Kinda figured it was something like that... I'll give it a shot later... just been waiting until I had the energy to mess with it heh.

--- edit ---

Tried the xorg.conf edit... made My own string from gtf... input those values into the section in xorg... even rebooted... no dice... doesn't show up in screen resolution OR nvidia settings...

---

### Post by adamlau on 2009-01-14
Yeah, I caught my typo after the post was submitted, but the forums went down immediately afterwards and stayed down for what seemed like hours and hours :( .

---

### Post by Montblanc_Kupo on 2009-01-14
> **adamlau said:**
> Yeah, I caught my typo after the post was submitted, but the forums went down immediately afterwards and stayed down for what seemed like hours and hours :( .

Heh... yeah... that was fun right in the middle of troubleshooting issues wasn't it? hehe Truth be told, I forget the "install" half the time I type it in the terminal... which is the only reason I caught it when you missed it. ;)

---

### Post by speed32219 on 2009-01-14
Can anyone tell me how the playback is with 1080i or 1080p video?
(Last one I used was 180.11 I believe)

Is it still choppy?  (Pans/scans)

And how is CPU utilization?  With the earlier driver it was high.

---

### Post by Kosimo on 2009-01-14
> **speed32219 said:**
> Can anyone tell me how the playback is with 1080i or 1080p video?
(Last one I used was 180.11 I believe)

Is it still choppy?  (Pans/scans)

And how is CPU utilization?  With the earlier driver it was high.

If you can compile mPlayer with nVidia patches... Then is going to work perfectly no matter what cpu you're currently using as the videocard is going to do all the decoding by hardware.

---

### Post by sofasurfer on 2009-01-14
I have lost 3D/advanced desktop effects ever since I went from 8.04 up to 8.10. 

I am using Geforce 7200 GS card. 177 driver recommended by Ubuntu does not enable advanced effects. Tried to get 180.22 working but so far no luck. Will try tutorial from this site now. Hope I have better luck.

By the way...
What is "pure video"?
What is the differance between 2D and 3D? Is it just a speed and processing power issue?

EDIT::
Can someone verify that 180.22 is the driver for my Geforce 7200 GS?

---

### Post by sofasurfer on 2009-01-14
I just installed 180.22. When it asked if I wanted it to build a kernel module I said yes. Then I restrted 'x'. I ended up with a blank, black screen just like when I tried this earlier.

I don't know how much longer I can go on like this. I have been able to figure out most things with Ubuntu but getting the proper graphics driver running is sapping my patience.

Would someone please help me?

---

### Post by pelle.k on 2009-01-14
> When it asked if I wanted it to build a kernel module I said yes. Then I restrted 'x'. I ended up with a blank, black screen just like when I tried this earlier.
Try the recommended
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
and make sure you run
```
sudo nvidia xconfig
```
afterwards, just to be on safe side.

You did try rebooting after installing the new driver?
Be sure to paste a copy of **/var/log/Xorg.0.log** after X fails (copy it to the desktop before you start up X with another driver).

---

### Post by sofasurfer on 2009-01-15
Thanks pelle.k
I'll probably try this out tomorrow.

Edit::
I just reinstalled. Instead of setting up my full system I will use a basic system with the only additional packages being those installed by the "Comprehensive Multimedia & Video Howto". If you have any other recommendations please state them.

Thanks again.

---

### Post by pelle.k on 2009-01-15
> I will use a basic system with the only additional packages being those installed by the "Comprehensive Multimedia & Video Howto"
OMG, that howto is totally crazy!. I usually enable medibuntu and install "ubuntu-restricted-extras" and thats it as far as codecs and stuff go. Never had a problem with watching/listening to any file really. But i'm sure it's a very good howto :)
Good luck with your new setup!

---

### Post by EdThaSlayer on 2009-01-15
I love these drivers, my pc looks awesome now with the desktop effects!
Haven't tried the hardware rendering of the videos though(as in, your cpu doesn't do much of the rendering).Luckily the support for my gpu 9500m is perfect! Rarely, and not sure whether this is the fault of compiz or Nvidia my screen goes a bit crazy and everything ceases to work. But that only happens 1 in 100 or so bootups.

---

### Post by fissionmailed on 2009-01-16
I upgraded to 8.10 from 8.04. Even after upgrading the drives(wouldn't work at all before) in envyng I couldn't even use opengl in mplayer.  Now it works perfectly.

---

### Post by sofasurfer on 2009-01-16
I have a GeForce 7200 GS in an Intrepid system. I have not found information that this card is supported, but I have not found information that it is NOT supported either.

After scouring this thread for information I have performed the following...

1) sudo apt-get remove --purge nvidia*
2) sudo aptitude install nvidia-glx-180
3) sudo /etc/init.d/dkms_autoinstaller start ( I do not understand this at all )
4) reboot
5) try to enable 'extra desktop effects'. 'desktop effects could not be enabled'
6) pelle.k...you stated...

   Try the recommended
   Code:
   sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
   sudo dpkg-reconfigure -phigh xserver-xorg

   and make sure you run
   Code:
   sudo nvidia xconfig

Do you mean I should do these steps AFTER I perform the above steps?

7) Is there anything else I need to do?

---

### Post by pelle.k on 2009-01-17
> Do you mean I should do these steps AFTER I perform the above steps?
I said that because you told us you had a blank screen when restarting X. I you've got past that step, then no, dont bother. My "recommendation" was based on the assumption that the nvidia driver didn't even bring up a working X, but it seems you've succeeded with that. Sorry you can't enable a "composite" desktop though. I have no solution for that.

---

### Post by macadavy on 2009-01-17
Valok:  just type 'lspci' in a terminal and you should get a list of all your cards, including a line like this (from my computer): 
 > 01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)

---

### Post by Eddie Wilson on 2009-01-17
When will these drivers go open source?

---

### Post by macadavy on 2009-01-17
> **Eddie Wilson said:**
> When will these drivers go open source?

Ask nVidia, the answer will probably be: "When we no longer make a profit or Hell freezes over, whichever comes first!" ;)

---

### Post by jyaan on 2009-01-18
I'll probably just wait until it's stable in Ubuntu before I change mine. Everything works perfectly, aside from some fullscreen annoyances with TwinView. However, if I knew there were TwinView improvements, it might be a different story. I have 9800gt btw.

And Pelle.k watch the language in your sig.

---

### Post by Swagman on 2009-01-18
Indeed. I am waiting for these to enter standard updates.

I'm sick of the audio glitches I am getting when "doing *Anything*" on the web.

---

### Post by Polygon on 2009-01-18
180.22 working flawlessly for me with my nvidia 9800 gtx =)

---

### Post by geezerone on 2009-01-19
What steps are needed to get this driver to work with 6600 as tried installing (first page of this thread) but get warning of Ubuntu running in low graphics mode.

Do I need to uninstall the repository packages (169.12 nvidia-glx-new)? If so, what is the best way?

I have to 'fix xserver' in recovery mode to get x working again.

---

### Post by Fingel on 2009-01-19
I was using the 180 series for a while but my laptop would not suspend using them.
You can always find the latest version here:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Just noticed, 180.x has gone from unstable to stable, when did that happen?

---

### Post by shaolinmilk on 2009-01-19
How exactly do I uninstall it?

Do I just do

sudo apt-get remove --purge nvidia*

EDIT:

I just did that and all of my hardware drivers for Nvidia are gone. Is this right?

---

### Post by jespdj on 2009-01-20
After having used the 180.22 driver for a while, I am not so convinced anymore that it rocks... :(

I get corrputed graphics sometimes, and sometimes parts of the screen do not redraw properly (for example the menus in Firefox). And my laptop doesn't wake up anymore from suspend. After digging around on the web (for example on nvnews.net) I discovered that I'm not the only one who has problems like this with the 180.xx drivers.

So I got an 173.xx version from nVidia's download archives, which works without these problems.

Waiting for nVidia to fix the issues... :(

@shaolinmilk: That command is to uninstall the drivers that come from the Ubuntu repository. If you want to uninstall a manually installed nVidia driver, switch to a text console (Ctrl+Alt+F1), and do:
```
sudo /etc/init.d/gdm stop
sudo nvidia-uninstall
```

---

### Post by lamborghiniwang on 2009-01-20
> **jespdj said:**
> After having used the 180.22 driver for a while, I am not so convinced anymore that it rocks... :(

I get corrputed graphics sometimes, and sometimes parts of the screen do not redraw properly (for example the menus in Firefox). And my laptop doesn't wake up anymore from suspend. After digging around on the web (for example on nvnews.net) I discovered that I'm not the only one who has problems like this with the 180.xx drivers.

So I got an 173.xx version from nVidia's download archives, which works without these problems.

Waiting for nVidia to fix the issues... :(

@shaolinmilk: That command is to uninstall the drivers that come from the Ubuntu repository. If you want to uninstall a manually installed nVidia driver, switch to a text console (Ctrl+Alt+F1), and do:
```
sudo /etc/init.d/gdm stop
sudo nvidia-uninstall
```

Same problem here, 180.22 driver, Hardy 64-bit. Everything works fine except suspend.

---

### Post by SeePU on 2009-01-20
> **shaolinmilk said:**
> How exactly do I uninstall it?

Do I just do

sudo apt-get remove --purge nvidia*

EDIT:

I just did that and all of my hardware drivers for Nvidia are gone. Is this right?
I believe that is correct, shaolinmilk.  I didn't read through the entire thread but I think the OP left out that requirement.  Does Ubuntu automatically sort out the conflicts and module-building?  I've always read a lot of steps when installing the latest Nvidia driver.

But, one common theme throughout is you need to remove/purge (whatever you do, you get rid of them) the previous nvidia driver info whether it's packages, modules or anything that is related to the kernel that specifies nvidia.  Did you check Synaptic to see that the nvidia packages are gone?  I discovered that you can have some 'generic' nvidia info left and the Nvidia Installer will sort that out but ANY package/module/driver from the previous driver will conflict and you will be left with the black screen (no kdm or gdm) as a result.  Furthermore, it is often the case (always the case) that some modules and kernel headers/images have to be matched up.  That is, the correct ones.  Also, the lib (gcc versions) need to match up.  Usually, the Installer can deal with the gcc disparities but previous Nvidia driver or modules that are installed cannot (e.g. nvidia-glx-173.14 module is installed when you are trying to install ver. 180.xx).  

I hope some of that makes sense.

P.S. I guess some people here have said you can use the Installer to uninstall the latest driver if you have a problem.  The driver will install even if you don't get kdm or gdm working.  It won't be installed correctly and xorg will be screwed up.  The OS will boot up into a screen console terminal and give messages about the X Server and/or the gdm/kdm running but some problem.  

You can also solve it by editing xorg.conf (xorg config file - which should have been backed up anyway) or using the backup file.  You edit the xorg.conf file by changing the driver from 'nvidia' to 'nv' which usually restore the desktop/gdm/kdm to a VGA resolution.  At least, you can boot up then and try again.

---

### Post by Wanas on 2009-01-23
I pressed alt control f1 and loged in, typed sudo /etc/init.d/gdm stop
sudo sh NVDIAxxxx
but I have this message 

Unable to find the kernel source tree for the currently running kernel.
Please make sure you have installed the kernel source files for your
kernel and that they are properly configured; on Red Hat Linux systems,
for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
installed. If you know the correct kernel source files are installed,
you may specify the kernel source path with the '--kernel-source-path'
command line option.

---

### Post by Kosimo on 2009-01-23
> **Wanas said:**
> I pressed alt control f1 and loged in, typed sudo /etc/init.d/gdm stop
sudo sh NVDIAxxxx
but I have this message 

Unable to find the kernel source tree for the currently running kernel.
Please make sure you have installed the kernel source files for your
kernel and that they are properly configured; on Red Hat Linux systems,
for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
installed. If you know the correct kernel source files are installed,
you may specify the kernel source path with the '--kernel-source-path'
command line option.


You're may missing build-essential files, (please anyone correct me if I'm mistaken) 

Just get them by typing: sudo apt-get install build-essential 

Then install the NVIDIA-Drivers again

Hope it helps.

---

### Post by macadavy on 2009-01-24
I followed the instructions in post #1 to install the Nvidia module 180.22 (stable) to support the GeForce 9500 GT card but received the following error messages on restarting X.org server:

 > (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 24 12:51:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

So here I sit in 800x600 low-res mode - no joy in Mudville tonight! :(
Now where are those uninstall instructions?  Ah yes: "nvidia-uninstall"
Lesson learned:  get a vidcard supported by modules already in the repos, or wait (approx. 3-4 months) for Ubuntu tailored modules to appear there...

---

### Post by speed32219 on 2009-01-24
Currently I have 5.1 digital audio over hdmi using the Nvidia and Alsa drivers.  I want to use the head phones as well as get the analog outputs working also (Gigabyte GA-M78SM-S2H MOBO).  I need a config for the asound.conf as well as .asoundrc I think to get everything working.

Can someone post your .asoundrc as well as your .asound.conf files if you have both digital hdmi as well as the analog working.

Thanks

Got it working!

The performance with the 180.22 dirvers has greatly improved.  The 8200 chipset is working great now with acceleration. I installed everything from the command prompt including the soundgraph LCD/IR/Volume knob in my Antec case. I am a happy camper once again, except for NM which I installed wicd instead thanks to a prior posted recommendation.

---

### Post by lamborghiniwang on 2009-01-27
The latest 180.25 driver has fixed the suspend/resume problem. :D

---

### Post by pelle.k on 2009-01-27
> The latest 180.25 driver has fixed the suspend/resume problem.
I can confirm that (GF8600M GS). Good work Aaron and co.! :)

---

### Post by Casper Hansen on 2009-01-27
Thanks! Just going to work with my desktop a while to feel the changes. The installation went flawless (nVidia GeForce 8600 GT 256 MB).

---

### Post by Unitas on 2009-01-28
The 180 drivers installed from the .run file borked my system. I checked all the fixes, none worked. I had to reinstall ubuntu. I got the drivers again from synaptics, same deal only this time it randomly freezes the system. Looks like I'll have to do yet another reinstall... :(

For those of you who got them to work, grats.

For those who value their time and sanity, wondering if they'll work, avoid them like the plague. 177 ain't so bad. I wish I never attempted to upgrade.

---

### Post by FokkerCharlie on 2009-01-28
Sorry to hear that, Unitas

It all works perfectly (well, as far as I would expect) here- including working suspend/resume.

BUT A NOTE OF WARNING TO ANYONE PLANNING TO INSTALL THIS DRIVER:

Make sure that you uninstall all the Nvidia modules with synaptic, first!

Cheers

Charlie

---

### Post by mips on 2009-01-28
> **Unitas said:**
> Looks like I'll have to do yet another reinstall... :(


Why do need to keep reinstalling, it would drive me nuts. Can't you just fix/uninstall?

---

### Post by Vadi on 2009-01-28
You can now just get the 180.11 driver by clicking [here]("apt:nvidia-glx-180") (this will install them from ubuntu directly).

This is way less error-prone and confusing to newbies - since as you see, some have attempted the complicated way and borked their systems.

---

### Post by -jay- on 2009-01-28
> **Vadi said:**
> You can now just get the 180.11 driver by clicking [here]("apt:nvidia-glx-180") (this will install them from ubuntu directly).

This is way less error-prone and confusing to newbies - since as you see, some have attempted the complicated way and borked their systems.

thank you that link worked uninstalled old installed new without any headaches

---

### Post by swoll1980 on 2009-01-28
Downloading now. Thanks for the heads up

---

### Post by CraigPaleo on 2009-01-28
I found 180.11 in the repositories and desktop effects do work more smoothly. I wonder why this upgrade wasn't automatic. 

Even after installation, it doesn't show up at all under hardware drivers but does under NVIDIA X Server Settings.

Nvidia's site wouldn't show me any drivers for my Geforce 6100/nforce 405, even using the advanced search for betas. This made me doubt whether it was really supported or not so, I found this list of supported cards: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/180.11-0ubuntu1~intrepid1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/180.11-0ubuntu1~intrepid1)

---

### Post by FuturePilot on 2009-01-28
> **CraigPaleo said:**
> I found 180.11 in the repositories and desktop effects do work more smoothly. I wonder why this upgrade wasn't automatic.
Because that is a beta version and by now a very old beta version.

> **CraigPaleo said:**
> Even after installation, it doesn't show up at all under hardware drivers but does under NVIDIA X Server Settings.


See above.

---

### Post by CraigPaleo on 2009-01-28
> **FuturePilot said:**
> Because that is a beta version and by now a very old beta version.



See above.

I don't think it is. Canonical provides critical updates for it up till 2010. I don't think they do that for beta software.

Anyway, the reason it wasn't showing up under Hardware Drivers was because I neglected to install nvidia-180-modaliases. I've just done that and everything is showing up as it should. It's even showing 180.11 as recommended. Surely they wouldn't recommend a beta.

---

### Post by zim2dive on 2009-01-28
> **CraigPaleo said:**
> I don't think it is. Canonical provides critical updates for it up till 2010. I don't think they do that for beta software.

Anyway, the reason it wasn't showing up under Hardware Drivers was because I neglected to install nvidia-180-modaliases. I've just done that and everything is showing up as it should. It's even showing 180.11 as recommended. Surely they wouldn't recommend a beta.

Would be nice if newer betas were more readily available via the package distribution method.. too may folks end up bonking their system installing at the command line.. 

even if they weren't "recommended" drivers.. for those of us who NEED the new drivers (my 8200 is currently under bug fix from nvidia), the Restricted Driver system almost hurts more than it helps.

---

### Post by Vadi on 2009-01-28
180.11 isn't considered a beta anymore, it's in intrepid-updates. People are fine to use it.

---

### Post by zim2dive on 2009-01-28
> **Vadi said:**
> 180.11 isn't considered a beta anymore, it's in intrepid-updates. People are fine to use it.

180.11 was always beta to nvidia.. 180.22 was the 1st 180.xx that they released as "stable".  Supposedly 173 was never upgraded to .15 or .16 b/c it still had "beta" status according to nvidia.

So not clear to me how the decision is made..

---

### Post by CraigPaleo on 2009-01-28
> **zim2dive said:**
> Would be nice if newer betas were more readily available via the package distribution method.. too may folks end up bonking their system installing at the command line.. 

even if they weren't "recommended" drivers.. for those of us who NEED the new drivers (my 8200 is currently under bug fix from nvidia), the Restricted Driver system almost hurts more than it helps.

Debian packages would probably be better as they would show up in Synaptic and be easier to remove. There are some here (not beta but for 180.22): [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/) 

For i386,you need to install: 
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.22-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.22-0ubuntu2_i386.deb)
then
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.22-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.22-0ubuntu2_i386.deb)
and then 
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.22-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.22-0ubuntu2_i386.deb)

For AMD64 :
 [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.22-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.22-0ubuntu2_amd64.deb) 
then 
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.22-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.22-0ubuntu2_amd64.deb)
and then

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.22-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.22-0ubuntu2_amd64.deb)

---

### Post by rajeev1204 on 2009-01-28
> **Vadi said:**
> 180.11 isn't considered a beta anymore, it's in intrepid-updates. People are fine to use it.



Where? Iam completely updated and i dont see it.

---

### Post by FuturePilot on 2009-01-28
> **Vadi said:**
> 180.11 isn't considered a beta anymore, it's in intrepid-updates. People are fine to use it.

It is beta. If you have the Nvidia splash screen enabled you will see it says Beta on it. 180.22 was the first stable release of the 180.xx driver.

---

### Post by CraigPaleo on 2009-01-28
> **rajeev1204 said:**
> Where? Iam completely updated and i dont see it.

Open Synaptic and search for "nvidia-glx-180"

---

### Post by Twitch6000 on 2009-01-28
> **zim2dive said:**
> Would be nice if newer betas were more readily available via the package distribution method.. too may folks end up bonking their system installing at the command line.. 

even if they weren't "recommended" drivers.. for those of us who NEED the new drivers (my 8200 is currently under bug fix from nvidia), the Restricted Driver system almost hurts more than it helps.

Question, what bugs for nvidia 8200 are being fixed? I ask this because as of the latest version of the nvidia drivers my bugs have now been fixed.

However I think a new bug has appeared,which is where certain buttons refuse to work when clicked on(and this on any distro).

I know this is a driver issue because with the other driver 1.77 it works fine.

---

### Post by CraigPaleo on 2009-01-28
> **zim2dive said:**
> 180.11 was always beta to nvidia.. 180.22 was the 1st 180.xx that they released as "stable".  Supposedly 173 was never upgraded to .15 or .16 b/c it still had "beta" status according to nvidia.

So not clear to me how the decision is made..

I just now upgraded to 180.22 and after restarting, most of the icons on the right side of the top panel didn't become visible until I passed my mouse pointer over them. Perhaps it's just a one time glitch or maybe it's a bug that caused the devs to keep 180.11. I don't know.

---

### Post by Vadi on 2009-01-28
It is not a beta for Ubuntu users, see [https://bugs.launchpad.net/bugs/297543](https://bugs.launchpad.net/bugs/297543) before pointing out that it's a beta for nVidia.

[IMG]http://www.ubuntu-pics.de/bild/8941/screenshot_100_335__U24LnO.png[/IMG]

If you want to install it, either [click here]("apt:nvidia-glx-180"), or install the "nvidia-glx-180" package manually. The Hardware Drivers updater is a bit wonky - but then again I disabled the automatic driver check in it. It did however show the 180 drivers fine and as "recommended" after I installed them.

---

### Post by ghostandmachine on 2009-01-28
I'm having major problems. I followed the directions in post #1 and when the nVidia installer was working everything seemed to go by just fine.

After reboot, I had "Fatal Error: No Screens Found" now the only way I can get gnome to run is by running in recovery mode. Even then I can only get a 800 x 600.

I can't even reinstall an older version of the driver because I get an error that says the version of the driver doesn't match the version number of the nVidia kernel. 

I have a Geforce 6150 LE onboard chip.

:(

---

### Post by CraigPaleo on 2009-01-28
> **Vadi said:**
> 

[click here]("apt:nvidia-glx-180"), 

I was going to ask how you did that but in this reply I can see the code. Cool!

---

### Post by Vadi on 2009-01-28
> **CraigPaleo said:**
> I was going to ask how you did that but in this reply I can see the code. Cool!

[https://wiki.ubuntu.com/AptUrl](https://wiki.ubuntu.com/AptUrl)

---

### Post by CraigPaleo on 2009-01-28
> **ghostandmachine said:**
> I'm having major problems. I followed the directions in post #1 and when the nVidia installer was working everything seemed to go by just fine.

After reboot, I had "Fatal Error: No Screens Found" now the only way I can get gnome to run is by running in recovery mode. Even then I can only get a 800 x 600.

I can't even reinstall an older version of the driver because I get an error that says the version of the driver doesn't match the version number of the nVidia kernel. 

I have a Geforce 6150 LE onboard chip.

:(

If you click the "apt link" that Vadi posted above, it should install the dependencies you need. The first post is old.

---

### Post by Vadi on 2009-01-28
> **ghostandmachine said:**
> I'm having major problems. I followed the directions in post #1 and when the nVidia installer was working everything seemed to go by just fine.

After reboot, I had "Fatal Error: No Screens Found" now the only way I can get gnome to run is by running in recovery mode. Even then I can only get a 800 x 600.

I can't even reinstall an older version of the driver because I get an error that says the version of the driver doesn't match the version number of the nVidia kernel. 

I have a Geforce 6150 LE onboard chip.

:(


I feel sorry for you, but blame it on the OP for recommending this hard way of installing which already broke several machines in this thread: [http://ubuntuforums.org/showpost.php?p=6458598&postcount=261](http://ubuntuforums.org/showpost.php?p=6458598&postcount=261)

Now you need to manually uninstall the drivers (get access to the terminal - so boot up, get the error msg, and do ctrl+alt+f1, login, and "sudo nvidia-uninstall", reboot, make ubuntu use the default settings - and then just install the drivers again from Hardware Drivers).

And remember - just because some random person recommends it, doesn't mean they know what they're doing.

---

### Post by ghostandmachine on 2009-01-28
> **CraigPaleo said:**
> If you click the "apt link" that Vadi posted above, it should install the dependencies you need. The first post is old.

i get an error that says firefox doesn't know what to do with the extension

---

### Post by Vadi on 2009-01-28
> **ghostandmachine said:**
> i get an error that says firefox doesn't know what to do with the extension

Ah, that might mean that your Ubuntu install is old - possibly 7.04.

You'd want to upgrade to 8.10 (which is 7.04, then 7.10, 8.04, and 8.10 - can't skip) or just install 8.10. [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Kosimo on 2009-01-28
> **Vadi said:**
> I feel sorry for you, but blame it on the OP for recommending this hard way of installing which already broke several machines in this thread: [http://ubuntuforums.org/showpost.php?p=6458598&postcount=261](http://ubuntuforums.org/showpost.php?p=6458598&postcount=261)

Now you need to manually uninstall the drivers (get access to the terminal - so boot up, get the error msg, and do ctrl+alt+f1, login, and "sudo nvidia-uninstall", reboot, make ubuntu use the default settings - and then just install the drivers again from Hardware Drivers).

And remember - just because some random person recommends it, doesn't mean they know what they're doing.

Does this even deserve an answer? 
I didn't' want to answer your flame, trying to ignore you as much as I could, but after this I got to say a few things to you.

1st, the only reason why I put that how-to in the first post is because I think it works, and it could help others as well. In fact I'm always doing that way with no issues at all. I like keep doing things the old manual way. You don't like it? Say it. But always respecting the others ideas.

2nd, That link you've just posted shows you a different point of view about how usable or recommended are beta drivers that just work for some users, and don't for others. This is the typical discussion between stable and cutting edge, you'll always have pros and cons. But you know what? I don't want to discuss this with you.

3rd, SO, from now on I recommend you to stop blaming on anything that is different about how you see it, and try to discuss and talk about how to make things better for everyone. I wouldn't mind to make the 1st post more usable, or warning users about possible issues. But with those answers, the only thing you do is totally the opposite.

---

### Post by swoll1980 on 2009-01-28
> **Kosimo said:**
> 

1st, the only reason what I put that how-to in the first post is because I think it works, and it could help others as well. In fact I'm always doing that way with no issues at all. I like keep doing things the old manual way. You don't like it? Say it. But always respecting the others ideas.



I have always done it this way as well, never had any issues although this time with a fresh install I had to manually edit xorg.conf for some reason. I think there's something wrong with the xorg configuration tool in the nvidia.run script this problem wouldn't affect someone that had an xorg.conf already configured to use a "nividia" driver, but if they didn't it will use there old driver. I'm not understanding how it would bork something though. Maybe they(the posters with the bad luck) tried tinkering with it to get it to work? seems more likely to me

---

### Post by zim2dive on 2009-01-28
> **swoll1980 said:**
> I have always done it this way as well, never had any issues although this time with a fresh install I had to manually edit xorg.conf for some reason. I think there's something wrong with the xorg configuration tool in the nvidia.run script this problem wouldn't affect someone that had an xorg.conf already configured to use a "nividia" driver, but if they didn't it will use there old driver. I'm not understanding how it would bork something though. Maybe they(the posters with the bad luck) tried tinkering with it to get it to work? seems more likely to me

*IF* you have installed 173/177 via the restricted panel in Intrepid, the 1st post works for 177.82, 180.06, and 180.11.. it broke for 180.16 and 180.22 according to most postings I saw (I have not tried the newest yet).  It may have been as simple as doing a --uninstall via the nvidia installer.  But something got more complicated after 180.11.  Folks should be made aware simple may not work..

If you've always installed by hand, the simple method may still work (dunno).

---

### Post by TheAL76 on 2009-01-28
> **Kosimo said:**
> Does this even deserve an answer? 
I didn't' want to answer your flame, trying to ignore you as much as I could, but after this I got to say a few things to you.

1st, the only reason why I put that how-to in the first post is because I think it works, and it could help others as well. In fact I'm always doing that way with no issues at all. I like keep doing things the old manual way. You don't like it? Say it. But always respecting the others ideas.

2nd, That link you've just posted shows you a different point of view about how usable or recommended are beta drivers that just work for some users, and don't for others. This is the typical discussion between stable and cutting edge, you'll always have pros and cons. But you know what? I don't want to discuss this with you.

3rd, SO, from now on I recommend you to stop blaming on anything that is different about how you see it, and try to discuss and talk about how to make things better for everyone. I wouldn't mind to make the 1st post more usable, or warning users about possible issues. But with those answers, the only thing you do is totally the opposite.

I for one appreciated this thread. 180.22 is running like a champ for me.

---

### Post by Vadi on 2009-01-28
Here is the issue:

"It is very easy and you can do it just following this steps."

You are assuming that it is easy for everybody - even complete newbies to Linux - to follow the terminal commands, which are really strings that either a) need to be memorized or b) written down or c) printed out. First two methods are error prone.

At the end you also say "Easy, isn't it? " - so anybody who got it wrong or is having diffulties with it, now feels like an idiot, because you claim it so be so easy.

That, and you're completely screwing over Ubuntu's image of stability by recommending people install bleeding-edge and **vital** software such as graphics drivers. Ubuntu gets borked because people mess up / bleeding-edge software is buggy - people think Ubuntu sucks. Ubuntu developers have a *delay* and *launchpad workflows* for this for a reason - and not because they don't want people using the best software available.

---

### Post by swoll1980 on 2009-01-28
> **TheAL76 said:**
> I for one appreciated this thread. 180.22 is running like a champ for me.

And that's the point. It wasn't bad advice. If 2 out of 1000 people have a problem with something oh well. It's not the owner of the threads fault. He was just trying to help, and did not deserve the treatment he received from one very condescending poster. Ubuntu doesn't work for every one either, should we start jumping down the Devs' throats, blaming them? SILLYNESS!!

---

### Post by Vadi on 2009-01-28
If he wanted to help, he would use Launchpad, work with Ubuntu developers on testing this. Not recommending clueless users to install bleeding-edge drivers like on archlinux :) (and even they have a week or so delay, I heard... this guy posts them up as soon as they appear on FTP).

---

### Post by swoll1980 on 2009-01-28
> **Vadi said:**
> If he wanted to help, he would use Launchpad, work with Ubuntu developers on testing this. Not recommending clueless users to install bleeding-edge drivers like on archlinux :) (and even they have a week or so delay, I heard... this guy posts them up as soon as they appear on FTP).

In a way I can see your point, but firstly you could have been a little nicer about it. Secondly users of any software should know the risk evolved with installing anything, especially at the OS level, on the recommendation of one person that they don't know. I for one am grateful because I had no idea new drivers were available, and I had to disable my nvidia card because of an issue I was having with the old drivers, and my window borders flickering like crazy which the new drivers completely fixed

add: And I had some problems with it as well, but knew the risk, and was ready to deal with any complications the arose.

---

### Post by swoll1980 on 2009-01-28
> **stuv132 said:**
> A college football lineman married one of the team's cheerleaders. The coach said, "You're such a big guy--why did you marry such a petite woman? She's no bigger than your hand.""That's right, Coach," replied the lineman, "but she's much better!" ............................................................................................................................................[**wow gold**](http://www.mmoinn.com/)|[**cheap wow gold**](http://www.mmoinn.com/)  [http://www.mmoinn.com](http://www.mmoinn.com)

That's a good one

---

### Post by HunterK on 2009-01-28
I'm just wondering if anyone else is having some serious performance problems with 180.22 and 180.25 drivers whereas 180.18 work great?

Yeah yeah, if it works, why upgrade? Honestly, I dont even know if going from 180.18 to 180.22 / 25 would even benefit a GeForce 6800GT? Its the principal of it, though.

FireFox is especially sluggish. When I click the titlebar to drag it (compiz on) it pauses a half second to do who knows what. Oh well, back to 180.18.

---

### Post by zim2dive on 2009-01-28
> **Vadi said:**
> If he wanted to help, he would use Launchpad, work with Ubuntu developers on testing this. Not recommending clueless users to install bleeding-edge drivers like on archlinux :) (and even they have a week or so delay, I heard... this guy posts them up as soon as they appear on FTP).

What it needs are the 2-3? extra steps that make it bulletproof... ie. if you look on nvnews there are a good hanful of folks, mostly Ubuntu users, who all had trouble _after_ 180.11.. so the "easy" steps worked great up til then.. then something in the nvidia install process changed, and some/few/many started seeing the "easy" steps stop working.

ie. when the nvidia installer says it can't find the kernel headers, post how to fix that, etc...

its not a bad set of instructions, its just not complete.  As someone that is new to Ubuntu, but old to unix (20 years daily *enduser* experience (but not admin experience), the unpreditctability of the nvidia driver installs has been a nightmare (I'm installing the new driver as I can to help debug a recently acknowledged bug with the 8200 support, so yes I do have a reason, but no I don't have the process down 100% yet).

Edit: and/or let say one does install by hand.. how does one get back to being able to use the restricted driver panel.. and/or how does one ADD their newly installed driver to the panel so they can switch back and forth... THAT would be a great thing to know.

---

### Post by CraigPaleo on 2009-01-29
> **Vadi said:**
> If he wanted to help, he would use Launchpad, work with Ubuntu developers on testing this. Not recommending clueless users to install bleeding-edge drivers like on archlinux :) (and even they have a week or so delay, I heard... this guy posts them up as soon as they appear on FTP).

+1! 

Glad you were here, Vadi!

---

### Post by rajeev1204 on 2009-01-29
nvm

---

### Post by CraigPaleo on 2009-01-29
> **rajeev1204 said:**
> Dont forget, This is a thread in the community cafe.Its not a how to.Thread title says 'nvidia 180 rocks' , not nvidia 180 installation procedure.OP wanted us to know how he did it and arent we glad he did.

After 400 posts, the OP should re-write the first post to reflect the fact that it's NOT a simple how-to!

> Most users who want bleeding edge are the only ones who are going to follow this. And as far as new users are concerned,its a learning curve for them getting used to which sections of the forum are for questions.

I don't think so at all! New users reading the Community Cafe? I think not!

> And who says only the ubuntu devs can test a piece of software?

No one says that ONLY the Ubuntu devs can test any piece of software but, good for us, they DO!


 >  These forums have always been an effective way of testing and giving advice to a lot of people.I still havent installed this 180... driver but iam sure users who need something new or something which will help with their display issues are  always eager to try something new.

It has been but I've witnessed many more instances of cleaning up "bleeding edge" suggestions than not. 



> The mods are well aware that this is bleeding edge,or this would have been a how to by now.

I hope they ARE aware and I certainly hope this DOESN'T become a stickied "how-to."

---

### Post by rajeev1204 on 2009-01-29
nvm

---

### Post by CraigPaleo on 2009-01-29
> **rajeev1204 said:**
> Lets get back to the Topic.All points noted and taken.But personal remarks are never a good thing in the forums and vadi did do it.


Case closed please.Dont want to ruin the thread.

Pardon me for correcting your English but don't you mean, "I don't want to ***HAVE RUINED*** the thread"? 

Closed or not, you have!

---

### Post by ghostandmachine on 2009-01-29
alright. so I updated my 8.04 LT to 8.10 which installed the nvidia 177 driver. Log in was fine but after that my monitor gave me the "Cannot Detect Display 1680x1050 60Hz". So I went to the xfix in recovery uninstalled all of the 177 driver files through synaptic and installed every file that said nvidia-180. 

When I went to restart it hung on a black screen with the text "acpid: exiting" and I had to hard reboot. 

After loading ubuntu I got pushed to the root login because it said it couldn't connect to the x server. So I reinstalled nvidia-177 (through synaptic) and now I can't get any higher than 800x600.

So many problems to fix a video driver. But I'm determined to get it to work. And I thank those already who have already helped. I feel like I'm that close.

Edit: With the 180 driver running, under Hardware Drivers it says that I'm running the 180 driver but my res is still only 800x600

---

### Post by copperfish on 2009-01-29
Just FYI, the new 180.27 driver suspends and resumes correctly on my T61 with an NV140M.  This is the first 180.x series driver that has worked.  I've tried every release, but I've kept going back to the 177.x series to have suspend and hibernate which for me is a must.

The usual hassles apply with installation:

Completely remove all Nvidia drivers and bits with Synaptic.
Edit /etc/X11/xorg.conf back to the open "nv" driver.
Reboot.
Follow the standard Nvidia install process i.e. Ctrl-Alt-F1, sudo killall gdm, sh nvidiainstaller

The 180.27 release seems to be worth it.

---

### Post by lamborghiniwang on 2009-01-29
> **copperfish said:**
> Just FYI, the new 180.27 driver suspends and resumes correctly on my T61 with an NV140M.  This is the first 180.x series driver that has worked.  I've tried every release, but I've kept going back to the 177.x series to have suspend and hibernate which for me is a must.

The usual hassles apply with installation:

Completely remove all Nvidia drivers and bits with Synaptic.
Edit /etc/X11/xorg.conf back to the open "nv" driver.
Reboot.
Follow the standard Nvidia install process i.e. Ctrl-Alt-F1, sudo killall gdm, sh nvidiainstaller

The 180.27 release seems to be worth it.

Actually, the suspend/resume has been working since the 180.25 driver, which was released one day before the 180.27. :)

---

### Post by shrndegruv on 2009-01-29
I followed this advice to go from 177.xx to the 180.xx.  I started with a completely up to date ubuntu install.  After I had followed the instructions, and rebooted, x wouldn't start because of API mismatch error (the kernel is 177 and the driver is 180, or something like that).  I recovered by uninstalling the new driver.  Has anyone else encountered this and know how to fix it?  I want to see if the newer driver speeds up kde 4.2 at all...

---

### Post by zim2dive on 2009-01-29
> **shrndegruv said:**
> I followed this advice to go from 177.xx to the 180.xx.  I started with a completely up to date ubuntu install.  After I had followed the instructions, and rebooted, x wouldn't start because of API mismatch error (the kernel is 177 and the driver is 180, or something like that).  I recovered by uninstalling the new driver.  Has anyone else encountered this and know how to fix it?  I want to see if the newer driver speeds up kde 4.2 at all...

This is exactly the type of situation that I wish was covered in the how-to.  I've yet to find any good (and thorough) set of instructions for when the easy way does not work.

---

### Post by aktiwers on 2009-01-29
I guess 180.22 is stable, at least its in Nvidia's official driver download page.
You could uninstall 177 via the Hardware Drivers app.. and then go for a manual install of that driver.

The manual installation is explained here by me and others on page 1 or 2 (cant remember)

---

### Post by ghostandmachine on 2009-01-29
Well now I can't even reach my desktop (had to boot into my m$ partition) Even when I go through the recovery mode and do a xfix I still only get a black screen.

I fear that I will have to reinstall ubuntu :(

---

### Post by swoll1980 on 2009-01-29
> **ghostandmachine said:**
> Well now I can't even reach my desktop (had to boot into my m$ partition) Even when I go through the recovery mode and do a xfix I still only get a black screen.

I fear that I will have to reinstall ubuntu :(

```
sudo nvidia-uninstall
```
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

This should return xserver back it's default settings on your machine

---

### Post by KhaaL on 2009-01-29
Kosimo, i think it might be neccesarly to remove all the nvidia-* packages through synaptic first? I've just followed your howto and i've ran into **major** problems getting my display to work.

its sleep time for me now though, so i'll resume the troubleshooting tomorrow...

EDIT: isn't just easier to install nvidia-glx-180 through synaptic?

---

### Post by Vadi on 2009-01-29
> **KhaaL said:**
> EDIT: isn't just easier to install nvidia-glx-180 through synaptic?

That's my point. [Click]("apt:nvidia-glx-180") and done.

---

### Post by jespdj on 2009-01-30
But nvidia-glx-180 is only available for Intrepid. If you are running Hardy for example, you'll have to download it from the nVidia website.

> **aktiwers said:**
> I guess 180.22 is stable, at least its in Nvidia's official driver download page.
But unfortunately that doesn't mean it's bugfree. nVidia admitted in a topic in the [nvnews forums](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) (can't find the topic there now) that with the 180-series drivers, wakeup from suspend is broken with some Linux kernel versions.

---

### Post by KhaaL on 2009-01-30
> **jespdj said:**
> But nvidia-glx-180 is only available for Intrepid. If you are running Hardy for example, you'll have to download it from the nVidia website.


But unfortunately that doesn't mean it's bugfree. nVidia admitted in a topic in the [nvnews forums](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) (can't find the topic there now) that with the 180-series drivers, wakeup from suspend is broken with some Linux kernel versions.

Ah, thats barely noticable since suspend rarely works anyway :lolflag:

---

### Post by shrndegruv on 2009-01-30
Originally Posted by KhaaL  View Post
EDIT: isn't just easier to install nvidia-glx-180 through synaptic?
That's my point. Click and done.

wait -- is it possible to get the 180 series via synaptic?

---

### Post by blazemore on 2009-01-30
Are these going to be pushed by the Hardware Drivers tool in Jaunty?

---

### Post by KhaaL on 2009-01-30
> **shrndegruv said:**
> 

wait -- is it possible to get the 180 series via synaptic?

Yes, i just did it and it saved me from gaining more grey hair strays.

---

### Post by shrndegruv on 2009-01-30
thats awesome -- i think its supposed to make kde 4 go faster.  and i can revert back to the 177 if 180 breaks my suspend?

---

### Post by KhaaL on 2009-01-30
I heard that too but havent tried it yet. If you need to revert, just reinstall the 177 package...

---

### Post by shrndegruv on 2009-01-30
i can't wait to get home and try this.  i just read a blog post that implies if i go to 180 series all the problems im having with kde should go away (busted plasmoids, some slow performance, etc).

---

### Post by zim2dive on 2009-01-30
> **Vadi said:**
> That's my point. [Click]("apt:nvidia-glx-180") and done.

Assuming Synaptic deigns to include the version you want.

ie. how long has 177.82 been out?  I needed that for 5.1 sound over HDMI audio, but Synaptic only installs 177.80, and the early 180.x were frightfully unstable on the 8200.

---

### Post by s1300045 on 2009-01-30
I have been using 180.22 for over a week now and I have to tell everyone how awesome it is! I run a kubuntu 8.10 box with kde4.2 installed, and the kwin performance problem is like it never happened before! Though I have to follow the instruction and disable direct rendering. Now kwin only runs 5% and below when active, and I can even play Warcraft III TFT in wine without switch off compositing effect first!

---

### Post by FuturePilot on 2009-01-30
> **zim2dive said:**
> Assuming Synaptic deigns to include the version you want.

ie. how long has 177.82 been out?  I needed that for 5.1 sound over HDMI audio, but Synaptic only installs 177.80, and the early 180.x were frightfully unstable on the 8200.

177.82 has been in the repos for a while. It's what I'm currently using.
```
apt-cache policy nvidia-glx-177
nvidia-glx-177:
  Installed: 177.82-0ubuntu0.1
  Candidate: 177.82-0ubuntu0.1
  Version table:
 *** 177.82-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com intrepid-updates/restricted Packages
        100 /var/lib/dpkg/status
     177.80-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/restricted Packages

```

---

### Post by piousp on 2009-01-30
> **KhaaL said:**
> Yes, i just did it and it saved me from gaining more grey hair strays.


How you did it?? I mean, what you typed 'cuz i cant find the right package (Maybe i'm so excited that i cant type well :p )

---

### Post by Neural oD on 2009-01-30
i'll have to give 180. a spin - sounds good

---

### Post by Vadi on 2009-01-30
> **piousp said:**
> How you did it?? I mean, what you typed 'cuz i cant find the right package (Maybe i'm so excited that i cant type well :p )

Are you on Ubuntu 8.10? if yes, just [click here]("apt:nvidia-glx-180") to install it (it installs from ubuntu repos, not a 3rd party site)

---

### Post by piousp on 2009-01-30
> **Vadi said:**
> Are you on Ubuntu 8.10? if yes, just [click here]("apt:nvidia-glx-180") to install it (it installs from ubuntu repos, not a 3rd party site)

Nice!! Does it uninstalls 177? Or should i do it first?

---

### Post by Montblanc_Kupo on 2009-01-30
The repositories only install 180.11 though... or is there some way to get the latest version through them?

---

### Post by Vadi on 2009-01-30
It automatically uninstalls 177

---

### Post by Npl on 2009-01-30
> **Montblanc_Kupo said:**
> The repositories only install 180.11 though... or is there some way to get the latest version through them?Not through the repos, but you should be able use the 180.22 packages from jaunty without messing the package-manager up:
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)
[http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source](http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source)

---

### Post by piousp on 2009-01-30
> **Vadi said:**
> It automatically uninstalls 177

Excellent, gonna do it as soon as I get home.

---

### Post by ghostandmachine on 2009-01-30
so i followed the link to install 180 and did a restart. but under hardware drivers it only show 177.

Edit: it's weird when i go to services>about ubuntu it doesn't tell me what version of ubuntu I'm running.

it just says Thank you for your interest in Ubuntu - the  - released in . apparently that's just a bug. haha

Edit: Okay, so 180 is installed and running I found out that there was still a 177 file "nvidia-177-modaliases" so I uninstalled that one and installed the 180-modaliases.

But nvidia-settings still says that I don't have a nvidia driver installed. Although it's active in hardware drivers.

Edit: Okay, I'm sorry for all the edits but I keep trying different things to get it to work. So I ran nvidia-xconfig in the terminal and did a restart. Got to the login screen at a great resolution (i think 1680x1050 or something) anyway I log in and my monitor goes black with the "Cannot Detect Display" error. So I did a restart, recovery, xfix, and i'm stuck at 800x600.

---

### Post by ghostandmachine on 2009-01-31
just thought it would help to have my xorf.conf file to see if I'm missing something. 

I was thinking that maybe if I manually entered my screen res on my xorg.conf file it might stop the "Cannot display video mode" but I have no idea how to do that. 

anyways...

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Nov  4 14:07:17 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Vadi on 2009-01-31
I'd delete the xorg.conf - use the "rm xorg.conf" command to, and restart - it'll then have a screen asking you to go back to the default configuration, which hopefully will give you the proper res to reinstall the driver.

---

### Post by ghostandmachine on 2009-01-31
> **Vadi said:**
> I'd delete the xorg.conf - use the "rm xorg.conf" command to, and restart - it'll then have a screen asking you to go back to the default configuration, which hopefully will give you the proper res to reinstall the driver.


removing the xorg.conf file did nothing.

---

### Post by Yoshiman007 on 2009-01-31
I feel like an idiot, but can someone tell me the best way to get the nvidia drivers working with a *clean* install of Intrepid? I can get the system up initially, but it seems with any nvidia drivers installed, X throws the "no screen found" error upon rebooting. I've already made my Hardy install inoperable (same X error) due to this error when I decided to upgrade to Intrepid.

So what's the best way to get nvidia drivers working in a clean install of Intrepid, **OR** what is the best way to get my Hardy install working again (command line only)? Any help would be greatly appreciated.

If it helps:
64-bit Hardy/Intrepid
2GB Ram, 2x Nvidia 7900 GT
AMD X2 5000

Duly noted to move, please help here: [New thread]("http://ubuntuforums.org/showthread.php?p=6654540#post6654540")

Via witchcraft, I have fixed it. Explanation is here ----^

---

### Post by pelle.k on 2009-01-31
> So what's the best way to get nvidia drivers working in a clean install of Intrepid, OR what is the best way to get my Hardy install working again (command line only)? Any help would be greatly appreciated.

What driver (nv or the propreitary one)? This isn't a generic help thread you know. We're discussing the new 180 series driver. I'm guessing you're using the "built in" 177 series driver? Set up a new thread about it and link to it here if you want help.
Oh, and be more specific (if you can) when describing the problem.

---

### Post by jamlc on 2009-02-01
Hi everyone, I can confirm huge speed improvement with the 180 drivers, KDE4 is now actually usable. 

Just a quick question. Is is safe to upgrade linux-header, linux-image and some nvidia modaliases on a machine that has the 180.22 drivers installed not through synaptic, but from the nvidia package? 

Also, what is the safest way of upgrading to 180.27, should I uninstall the 180.22 driver? Cheers

---

### Post by Montblanc_Kupo on 2009-02-01
Okay... I was testing the 180.27 drivers from the repositories and thought they were working (installed and was running fine) but had the same random weirdness as with 180.22. After a short time... all 3D functions come to a crunching halt and everything starts going hella slow.

So I wanted to revert back to something that worked (180.11 worked great, 177 worked fine too).

I went to deactivate in the hardware drivers and then ended up just removing ALL the drivers from synaptic. SO right now I should have no nvidia drivers installed... this is evident because when I rebooted... ubuntu insisted that I go into "low graphics mode" becauase there was some problem with the display. 

When I try to install either 177 or 180.11 from synaptic I get this error after install starts:
```
/var/cache/apt/archives/nvidia-glx-180_180.11-0ubuntu1~intrepid1_i386.deb: subprocess pre-installation script returned error exit status 2
```

I tried doing an autoremove, purge, clean whatever to make sure that there wasn't any residual junk left from a previous install... but there's obviously something tweaky going on. 

Any clue as to how I can get back up and running with 180.11?

[b]--edit - solved--

I'm not sure what fixed it... but it's fixed. I uninstalled EVERYTHING that said nvidia on it from synaptic. Then added ONLY the 177 modalalias file... then let the hardware driver app activate it for Me. Restarted and it was working. So from there I went back and added the 180.11 modalalias and kernel files and it applied them and they're going again. Black magic is afoot... heh[/b]

---

### Post by drdos2006 on 2009-02-02
I'm glad everyone is having good results with the 180 driver. I am not.
Have Ubuntu 8.10 64bit version on Gigabyte motherboard ( GA-G33M-S2) and had a GeForce 7600 GT OC PCIe video card. Upgraded to 180 drivers using apt_get install and it blew my video card.
Unable to see video in BIOS, changed BIOS to read on-board video first, found a CRT with VGA connector, tried again. Remove video card, use on-board video, all OK, but Ubuntu loads in low graphics. Removed anything to do with nVidia drivers, video card still blown, still not seen in BIOS, blank screen.
Purchase new video card ( 8400 GS ) after checking that this video card is supported by nVidia in Ubuntu. ( Thanks to this forum ).

Any advice to restore 7600 to original glory would be appreciated before I load 180 drivers into 8400 GS.

regards to any who respond.

---

### Post by FokkerCharlie on 2009-02-02
Can anyone tell me which repo the 180.27 driver is in?  I can only see 180.11 in Intrepid backports.

Cheers!
Charlie

---

### Post by shrndegruv on 2009-02-02
> **FokkerCharlie said:**
> Can anyone tell me which repo the 180.27 driver is in?  I can only see 180.11 in Intrepid backports.

Cheers!
Charlie


I don't think 180.27 is in a repo -- you need to get the installer form nvidia.

If you go to the jaunty repo you can get 180.22.  On my quadro 160m all the features work (suspend, hibernate) and performance is improved (in KDE4.2 although some things like dropshadows aren't working-- could be kde or the driver i dont know).  

I got the 180.22 version from jaunty.  all I had to do was install prevu, which is a utility that allows you to try packages for other ubuntu releases.  

DO THE FOLLOWING AT YOUR OWN RISK!

The process is something like this:

1) google for 'prevu wiki' and familiarize yourself with the instructions.  
2)  Follow the wiki.  The init step took a good hour to run.  
3)  After init, if you completely followed the wiki, any jaunty packages you install will be viewable in synaptic.  
4)  from the wiki, do prevu package-you-want. prevu will pull down the source, compile the package.  It wont be installed, but you can see it in synaptic.  Then install normally from synaptic.
5)  So based on number 4, the package you want is at 

[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

if you look to the right, you will see the source package is 
nvidia-graphics-drivers-180

so 

prevu nvidia-graphics-drivers-180

should do it.

then just go to synaptic and install the new version.  since intrepid also has a glx-180, you will see that you can upgrade your existing package....

---

### Post by Montblanc_Kupo on 2009-02-02
The jaunty repo has 180.27 now.

---

### Post by TheAL76 on 2009-02-02
> **jamlc said:**
> Hi everyone, I can confirm huge speed improvement with the 180 drivers, KDE4 is now actually usable. 

Just a quick question. Is is safe to upgrade linux-header, linux-image and some nvidia modaliases on a machine that has the 180.22 drivers installed not through synaptic, but from the nvidia package? 

Also, what is the safest way of upgrading to 180.27, should I uninstall the 180.22 driver? Cheers

You can update the linux image, but you need to re-run the nvidia installer afterward.

For upgrading to 180.27, I think you can run nvidia --uninstall, then run the 180.27 installer.

---

### Post by FokkerCharlie on 2009-02-02
Kupo- Which Jaunty repo?  Do you have the apt-line?

Charlie

---

### Post by former_warper on 2009-02-02
I just went from the 177 to the 180.11 driver.  I see a huge difference, especially in slide show tif images. The 177 driver produced irritating ghost bands that are gone with the 180 driver. I even tried gnome hearts - big difference!

---

### Post by Montblanc_Kupo on 2009-02-02
> **FokkerCharlie said:**
> Kupo- Which Jaunty repo?  Do you have the apt-line?

```
## nvidia
deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
```

I believe that's where I got it from. I was thinking it was in the official repos, but apparently it was in the PPA here.

---

### Post by Shaya on 2009-02-03
Anyone experiencing lower refresh rate and highlighting errors while hovering mouse over items in menus?
I manually installed 180.22 version hours ago and I have these problems. Another thing is that my "Hardware Drivers" list is empty.
What should I do to solve those problems? :D
I'm on Ubuntu Hardy, Kernel 2.6.24-23 . . .

---

### Post by shrndegruv on 2009-02-03
> **Montblanc_Kupo said:**
> The jaunty repo has 180.27 now.

ah yes.  kde 4.2 really is much faster with these drivers.

---

### Post by Polygon on 2009-02-04
i get no 3d acceleration with 180.27. just throwing that out there. Programs are saying that 'opengl 2.1 is not available" when my card SHOULD support 2 (maybe 3, its a nvidia 9800 gtx)

---

### Post by wingnux on 2009-02-05
I've just installed 180.25 here and KDE4 is way faster! Ok, not as fast as Gnome but at least now it's useable! =)

---

### Post by Twitch6000 on 2009-02-05
Uhmm the main post says the latest prerelease is 180.25 when it is truly 180.27 >.>

link - [http://www.nvnews.net/vbulletin/showthread.php?p=1916380](http://www.nvnews.net/vbulletin/showthread.php?p=1916380)

---

### Post by Mr. Picklesworth on 2009-02-07
So has anyone noticed improvements to the dynamicness of Twinview stuff in the newer versions? I am running 180.11 from the official repository, and I decided that enough cruft was enough so spent the morning making my system super tidy. This involved wiping out the xorg.conf stuff and starting fresh (and installing gdm-new, which makes me happy).

Anyhow, the result with my wiping out xorg.conf is that my hard display settings were removed. Makes sense for a laptop; the only display that should be in static configuration is the one firmly attached to the computer, even if I do use an external one fairly often.

I remember that I originally had to get tis stuff set up on xorg.conf because nvidia-settings required changing the virtual screen size (to fit both monitors) before it could enable twinview. This time, however, GDM was happily outputting to just the one automatically detected display (which is fine). I logged in, opened nvidia-settings and enabled my second monitor with TwinView and it Just Worked within my session without the need to escalate privileges or anything. No extra steps required and no junk lying around in xorg.conf. Cool!
So has this been improved lately, or am I imagining things?

And if they've improved that, is there some way for it to automatically detect and temporarily configure displays as soon as they are plugged in / unplugged rather than needing to dig through nvidia-settings every time?


Edit:
I swear, ever since I installed gdm-new everything has worked better. Just noticed my wacom tablet works with hotplugging now...

---

### Post by Kosimo on 2009-02-09
180.29 STABLE are out

Release Highlights:

    * Added support for the following GPUs:
          o GeForce GTX 295
          o GeForce GTX 285
          o GeForce 9300 GE
          o Quadro NVS 420
    * Added support for OpenGL 3.0 for GeForce 8 series and newer GPUs.
    * Fixed a bug that caused VDPAU to display a green screen when using the overlay-based presentation queue with interlaced modes.
    * Fixed a bug that prevented VDPAU from working correctly after X server restarts on some GPUs.
    * Improved VDPAU's handling of mode switches; eliminated a crash in its mode switch recovery code and a hang in the blit-based presentation queue.
    * Fixed a bug that caused VDPAU to crash when using DisplayPort devices.
    * Fixed a potential hang in VDPAU when using the blit-based presentation queue on systems with multiple GPUs not in SLI mode.
    * Implemented missing error checking of layer data in VDPAU's VdpVideoMixerRender function.
    * Improved VDPAU's handling of setups with multiple GPUs, if a subset of the GPUs cannot be supported due to resource limitations.
    * Improved GPU video memory management coordination between the NVIDIA X driver and VDPAU.
    * Fix potential hang in VDPAU when the overlay is already in use.
    * Improved workstation OpenGL performance.
    * Fixed an X driver acceleration bug that resulted in Xid errors on GeForce 6 and 7 series GPUs.
    * Updated the X driver to consider GPUs it does not recognize supported, allowing it to drive some GPUs it previously ignored.
    * Added the ability to run distribution provided pre- and post- installation hooks to 'nvidia-installer'; please see the 'nvidia-installer' manual page for details.
    * Updated the X driver's metamode parser to allow mode names with periods (i.e. '.'s).
    * Fixed a problem in VDPAU that prevented the overlay-based presentation queue from being used on displays connected by component video.
    * Fixed various problems in VDPAU that caused visual corruption when decoding certain MPEG-2 video streams.
    * Fixed a crash in VDPAU caused by certain invalid MPEG-2 streams, in 64-bit drivers for some GPUs.
    * Fixed an X driver performance problem on integrated GPUs.
    * Fixed a stability problem with OpenGL applications using FSAA.
    * Fixed an initialization problem that caused some AGP GPUs to be used in PCI compatibility mode.
    * Fixed a bug that could result in stability problems after changing clock settings via the Coolbits interface.
    * Fixed a problem with hotkey switching on some recent mobile GPUs.
    * Worked around a power management regression in and improved compatibility with recent Linux 2.6 kernels.

---

### Post by Hells_Dark on 2009-02-09
I don't understand why there is several .run. 
Anyone ?

---

### Post by Npl on 2009-02-09
> **Hells_Dark said:**
> I don't understand why there is several .run. 
Anyone ?Explained in the readme, all contain the same driver, same kernel-source. Th eonly difference is that higher ?run`s have more/newer precompiled kernel-modules (which you usually dont need anyway)

---

### Post by Hells_Dark on 2009-02-09
> **Npl said:**
> Explained in the readme, all contain the same driver, same kernel-source. Th eonly difference is that higher ?run`s have more/newer precompiled kernel-modules (which you usually dont need anyway)

Ha okay. I took a look at the README, but didn't find the answer (maybe didn't undestand because english is not my mother tongue).

Anyway, thanks.

I just installed them, They work great :)

---

### Post by lightsout565 on 2009-02-09
I appreciate the excellent guide but when I type "startx" I get an error saying that it couldnt load the Nvidia Device and that it is running in low graphics mode. NOTE: I am using Wubi. I have heard tons of other people saying about when they install ATI/Nvidia drivers they get the same error.If you reboot, i't usually gets stuck at "Check Battery State"

---

### Post by Montblanc_Kupo on 2009-02-10
> **lightsout565 said:**
> I appreciate the excellent guide but when I type "startx" I get an error saying that it couldnt load the Nvidia Device and that it is running in low graphics mode. NOTE: I am using Wubi. I have heard tons of other people saying about when they install ATI/Nvidia drivers they get the same error.If you reboot, i't usually gets stuck at "Check Battery State"

I know I had serious issues with just restarting X. I do a full reboot after install and it seems to work.

---

### Post by lightsout565 on 2009-02-10
> **lightsout565 said:**
> I appreciate the excellent guide but when I type "startx" I get an error saying that it couldnt load the Nvidia Device and that it is running in low graphics mode. NOTE: I am using Wubi. I have heard tons of other people saying about when they install ATI/Nvidia drivers they get the same error.If you reboot, i't usually gets stuck at "Check Battery State"
In addition, I uploaded the logs of the errors I get.

[ATTACH]102895[/ATTACH]

---

### Post by neilevan814 on 2009-02-11
I think you type in lspci in terminal and that will give you a lot of internal specs for your computer.

---

### Post by crazyfuturamanoob on 2009-02-11
The new driver is great but it didn't fix the weird background with toribash:
[[IMG]http://img502.imageshack.us/img502/455/toribashbug11kn4.th.png[/IMG]](http://img502.imageshack.us/my.php?image=toribashbug11kn4.png)

---

### Post by zim2dive on 2009-02-11
180.29 looks like it fixes the horrendous performance of the 8200/8300 (in particular with full-screen Flash)

---

### Post by crjackson on 2009-02-13
> **Vadi said:**
> You can now just get the 180.11 driver by clicking [here]("apt:nvidia-glx-180") (this will install them from ubuntu directly).

This is way less error-prone and confusing to newbies - since as you see, some have attempted the complicated way and borked their systems.

Is there an update link for 180.29, or is there some particular reason we should stick with 180.11?

---

### Post by lightsout565 on 2009-02-13
> **crjackson said:**
> Is there an update link for 180.29, or is there some particular reason we should stick with 180.11?
I used the link to install the drivers. I reboot and I don't get any errors that ubuntu is running in low graphics mode. Everything is fine so far. I wanted to use the desktop effects and it gave me an error saying they couldn't be enabled. I check the nvidia x server settings and it said that it wasn't running the Nvidia X driver. I typed "sudo nvidia-xconfig" in the terminal and it gave me a error. I check the new xorg.conf and see that its been updated. So, I reboot the x server by pressing CTRL+ALT+BACKSPACE. It goes to the command line stuck at checking battery state and I get a error message that says that ubuntu is running in low graphics mode.
```
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

xorg.conf before sudo nvidia-xconfig
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

xorg.conf after running sudo nvidia-xconfig
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Xorg.O.log
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 13 20:05:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8600 GT rev 161, Mem @ 0xfa000000/0, 0xd0000000/0, 0xf8000000/0, I/O @ 0x0000df00/0, BIOS @ 0x????????/131072
(--) PCI: (0@2:4:0) Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xe8000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:23:16 PST 2008
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 11:00:06 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

:O.log
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 13 20:05:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8600 GT rev 161, Mem @ 0xfa000000/0, 0xd0000000/0, 0xf8000000/0, I/O @ 0x0000df00/0, BIOS @ 0x????????/131072
(--) PCI: (0@2:4:0) Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xe8000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:23:16 PST 2008
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 11:00:06 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by lightsout565 on 2009-02-14
Bump

---

### Post by xX-Felipao-Xx on 2009-02-14
Hi all, I tryied to install the 180.x drivers (because my 2D performance with Firefox was really bad -slow tab changing, notification bar appears in slowmotion, etc-) following the 1st post's instructions but I messed it up (it won't get installed since I don't have the exactly matching version of gcc compiler, but mainly because I don't have the kernel source files it needs, i searched in Synaptics, installed the nvidia-kernel-source for 180.x but it didn't work).

Now I uninstalled everything starting with nvidia in Synaptic but I couldn't install it neither. I have a FX 5200, old indeed, so, this driver fits to me? if not, which one would you recommend to me? And please, how to install it, because now I'm without drivers at all... so without compiz, so sad :(

---

### Post by Rumbl3 on 2009-02-14
yeah i went from 177 to these (i'm new to linux) and these drivers imo were awesome compared to the 177's.

---

### Post by emtjr928 on 2009-02-14
I am using 177 ver. drivers with a 6600le 256 pcie on intrepid. Will the new 180 series driver break my system if installed through synaptic? I checked and it wants to remove the 177 ver.
Thanks Ed

---

### Post by crjackson on 2009-02-14
I first used the apt link to install the 180.11 drivers and it went perfect. Driver was great..

I then backed up my drive to an image in case the next move borked my system.

I enabled a jaunty ppa with the 180.29 driver (and other files). I unchecked all packages except the 3 nVidia driver modules. I accepted and applied the updates as normal.

All went without a hitch. Then I edited my sources list and removed the jaunty ppa.

Then I rebooted to a perfectly running Intrepid 32 bit system with driver version 180.29.

I have the video card listed in my sig... I knew it was risky but it worked out perfectly for me. I don't know what went wrong on your system..

That's all I got...

---

### Post by xX-Felipao-Xx on 2009-02-15
I'm having the issue with the kernel source files, when I'm trying to install the drivers it wont install because it can't find those files.

What can I do? Help please !

I have already tryied downloading nvidia-kernel-source for 180.x version, and I read that i need the linux-headers and kernel-source matching with my current version, but those aren't in Synaptic, there aren't for my version (2.6.24-21-generic)
My video card is a FX5200

---

### Post by JPorter on 2009-02-15
> **xX-Felipao-Xx said:**
> I'm having the issue with the kernel source files, when I'm trying to install the drivers it wont install because it can't find those files.

What can I do? Help please !

I have already tryied downloading nvidia-kernel-source for 180.x version, and I read that i need the linux-headers and kernel-source matching with my current version, but those aren't in Synaptic, there aren't for my version (2.6.24-21-generic)
My video card is a FX5200

Why are you using such an old kernel?

---

### Post by Paqman on 2009-02-15
Don't know if it's been mentioned yet in this thread but you can get a 180 series driver out of the proposed repo on Intrepid. You'll only need to follow the instructions in the first post if you want the absolute latest one.

---

### Post by seicean on 2009-02-15
Thanks for the effort, but the 180 RUINED my X Server. I had to prepare for a fresh install after I hit ENTER at the end of the driver installation. 

I have a GeForce 9300M GS, 256MB (Laptop) witch worked very well with the recommended 177. 

And to spare a few replyes:

1. After driver update/reboot Ubuntu 8.10 was booting in "init 3" text mode
2. Switching manually to graphical mode, the mouse pointer appeared on the screen freezing. A dizzy image in backgrnd=...dead
3. The Xorg.conf was reset to a VESA Default 640x480.
4. Backups not usable.
5. Reinstall 2 times... same scenes 

I'm fine now with the good ol' 177 :)

---

### Post by walkerk on 2009-02-15
I wasn't too successful w/ 180.29. I can install the driver w/o problems and run pekwm flawlessly. 

My problem comes if I try to run Compiz... the screen just goes black and I have to restart X. Anyone having this same problem? Oh and compiz-check comes back w/o issues...

GeForce Go 7150M

---

### Post by xX-Felipao-Xx on 2009-02-15
> **JPorter said:**
> Why are you using such an old kernel?

Ok, I've recently updated it to 2.6.27-11-generic
I'll try again,...

---

### Post by xX-Felipao-Xx on 2009-02-15
Guys, I've have successfully installed the drivers and then, when I rebooted, the "Start in low-graphics mode" dialog appeared. I chose to re-configure and then, it was OK the resolution, but again, I don't have graphics acceleration and in Hardware Drivers there's NOTHING! 

Even my webcam driver is lost... what's happening? :S

---

### Post by seicean on 2009-02-16
I know. Somehow the Backed-up X configuration cannot be accessed after the 180 install. I tried reconfiguring it manually, but didn't worked 100% and the acceleration was lost. 

I would recommend to stick with the 177, until the 180 is OFFICIALLY in the repos.

---

### Post by MasterProg on 2009-02-16
My X broke after installing driver version 180.29 (Ubuntu 8.10 i386). Still sticking with 177.

---

### Post by MasterProg on 2009-02-16
Just installed 180.11 from the repos and everything is fine so far. But I kind of still want to try the newest version out.

---

### Post by PythonPower on 2009-02-16
I haven't noticed any speed-ups but then again everything always seemed snappy before. I'm guessing the improvements are very variable depending on setup.

---

### Post by darco on 2009-02-16
I installed 180.29 and everything seems ok.The nvdia x-server settings reports everything is fine too. Compiz is fine...I do notice under Administration/Hardware Drivers that it says that I do not have any proprietary drives installed. Is that right?

darco

---

### Post by xX-Felipao-Xx on 2009-02-16
Ok people, I BEG for help.

After uninstalling everything to do with nvidia in Synaptics, I could install the package (180.11), but It doesn't work properly (low-graphics) and with no acceleration (so no compiz).

Then, I installed envy again and installed 173, and everything went OK, I rebooted, low graphics again but I still needed to activate the drivers in "Hardware Drivers", then, I activate them, reboot, and...

Still the same, good resolution now but no acceleration, so I can't enable Desktop Effects..

What is lacking? What should I have to enable acceleration?!?!?

---

### Post by darco on 2009-02-16
> **xX-Felipao-Xx said:**
> Ok people, I BEG for help.

After uninstalling everything to do with nvidia in Synaptics, I could install the package (180.11), but It doesn't work properly (low-graphics) and with no acceleration (so no compiz).

Then, I installed envy again and installed 173, and everything went OK, I rebooted, low graphics again but I still needed to activate the drivers in "Hardware Drivers", then, I activate them, reboot, and...

Still the same, good resolution now but no acceleration, so I can't enable Desktop Effects..

What is lacking? What should I have to enable acceleration?!?!?

Check out this link, not sure if this will help for acceleration issue but re installing may help.
[http://ubuntuforums.org/showthread.php?t=1071283](http://ubuntuforums.org/showthread.php?t=1071283)

darco

---

### Post by xX-Felipao-Xx on 2009-02-17
> **darco said:**
> Check out this link, not sure if this will help for acceleration issue but re installing may help.
[http://ubuntuforums.org/showthread.php?t=1071283](http://ubuntuforums.org/showthread.php?t=1071283)

darco

I have just tryied it, and I get the Gnome low-graphics again...

grrrrrrrrrrrrrr

I don't know what the hell is happening hereee!! :(

---

### Post by Sealbhach on 2009-02-17
> **darco said:**
> I do notice under Administration/Hardware Drivers that it says that I do not have any proprietary drives installed. Is that right?

darco

Yes that's right. You should have an Nvidia Menu option, in System/Admnistration which will display the correct driver version.


.

---

### Post by itisbasi on 2009-02-17
The simplest way to install it is via the synaptic.
I have a 6600GTS and didn't notice any major difference after installing this driver....

---

### Post by TalioGladius on 2009-02-19
Everything is working for me with 177, and I have a wonky dual monitor setup.  It's not broken, so I'm not dicking with it....yet.

---

### Post by patchoro on 2009-02-19
Exellent thread! My Geforce 8200M was 3D wise already pretty snappy with the 173 drivers, but firefox just felt.. cumbersome and slow. With the 180 drivers all is peachy! Hi-res youtube provides no more problems and I have yet to encounter any kind of screen corruption. Wine games are now as they should be, racing along! 

Kudos to Nvidia for coming through for the OS community.

---

### Post by stefangr1 on 2009-02-20
I notice some random noise / horizontal artifacts when using mplayer-vdpau, especially in scenes with fast movement or a moving camera. Strange thing is that when I make a print screen when I see it, I don't seem to capture it (could be a coincident). Strange... I hope it will be fixed soon.

Then another point: does anyone know if there's a way to automate opening files with mplayer-vdpau? Maybe trough some configuration in the mplayer config file that detects the format and selects the right vdpau codec or something?

---

### Post by stefangr1 on 2009-02-21
> **stefangr1 said:**
> I notice some random noise / horizontal artifacts when using mplayer-vdpau, especially in scenes with fast movement or a moving camera. Strange thing is that when I make a print screen when I see it, I don't seem to capture it (could be a coincident). Strange... I hope it will be fixed soon.

Then another point: does anyone know if there's a way to automate opening files with mplayer-vdpau? Maybe trough some configuration in the mplayer config file that detects the format and selects the right vdpau codec or something?

Apparently the horizontal lines are no longer present after executing:

sudo nvidia-xconfig --no-composite

and restarting X.

Still interested though in ways to automize the use of vdpau in mplayer.

---

### Post by Hells_Dark on 2009-02-21
> **stefangr1 said:**
> 
Still interested though in ways to automize the use of vdpau in mplayer.

What is vdpau ?

---

### Post by stefangr1 on 2009-02-21
vdpau is a patch for mplayer, made by nvidia. You can use it to decode movies on a nvidia GPU of the 7 and 8 series, if you have the 180.xx driver installed.

This gives a HUGE performance advantage: a 1080p h264 encoded movie that couldn't play on my E6750 with the cpu at 100% now plays perfectly at only 2%. It appears that with the newest drivers (180.29) and newest version of vdpau almost all issues are solved, and >90% of the movies I have play with it. 

Only trouble is that if I configure the use of vdpau in my mplayer config, mplayer will just crash with the other 10% of the movies, whereas if I don't configure it there, about 2 lines of configuration in a terminal are needed just to start a movie which isn't to convenient for a media center. So thats why I'm hoping someone knows a way to make this right.

---

### Post by thegreenblob on 2009-02-21
Oh man the 180.29 drivers work awesome with intrepid 64 bit with my NVIDIA GeForce 7100.

Much better that the 177 drivers :)

Savage 2 was REALLY laggy with the 177 ones and now it runs flawlessly. And there's also no more static under my window boarders in compiz.

---

### Post by BGFG on 2009-02-21
You guys make me wish i had a video card. I'm running on-board with the 180.29 so i don't see the HUGE performance gains. My graphics ARE very crisp though and i get great 2D performance....

---

### Post by mips on 2009-02-21
> **BGFG said:**
> I'm running on-board with the 180.29 so i don't see the HUGE performance gains.

The evils of shared slow ram...

---

### Post by Polygon on 2009-02-21
> **stefangr1 said:**
> vdpau is a patch for mplayer, made by nvidia. You can use it to decode movies on a nvidia GPU of the 7 and 8 series, if you have the 180.xx driver installed.

This gives a HUGE performance advantage: a 1080p h264 encoded movie that couldn't play on my E6750 with the cpu at 100% now plays perfectly at only 2%. It appears that with the newest drivers (180.29) and newest version of vdpau almost all issues are solved, and >90% of the movies I have play with it. 

Only trouble is that if I configure the use of vdpau in my mplayer config, mplayer will just crash with the other 10% of the movies, whereas if I don't configure it there, about 2 lines of configuration in a terminal are needed just to start a movie which isn't to convenient for a media center. So thats why I'm hoping someone knows a way to make this right.

its not a patch for mplayer, its just a interface to allow ANY program to use the videocard to decode video. Its just that mplayer is one of the first programs to use it. Soon there will be a bunch of players that support it (on windows and linux)

---

### Post by Hells_Dark on 2009-02-21
Thanks.
Interesting :)

---

### Post by BGFG on 2009-02-21
> **mips said:**
> The evils of shared slow ram...

Tell me about it. ooog...:(

---

### Post by Montblanc_Kupo on 2009-02-22
So there's something I noticed with the 180 versions. I can install them... and they might work okay at first... but slowly the system gets less and less responsive over time (time like... over the course of 20 minutes or so). Things will run better than 177.xx at first... then slowly get slower. Applications will continue to run okay, but when the video card kicks into 3D mode... it takes a second to do it... and it runs slowly. So anything from rotating the compiz desktop cube to glxgears ... anything using the 3D seems affected. Uninstall 180.xx and reinstalled 177.xx and it's back to normal... runs all day without slowdown.

I have a geforce 6800XT 256mb card.

Any ideas?

---

### Post by AaronP_ on 2009-02-23
> **stefangr1 said:**
> You can use it to decode movies on a nvidia GPU of the 7 and 8 series, if you have the 180.xx driver installed.
VDPAU requires GeForce 8 or higher.  See mips's post below for more details.

> **Polygon said:**
> Soon there will be a bunch of players that support it (on windows and linux)
VDPAU is the Video Decode and Presentation API for **UNIX**.  Windows already has similar APIs so I doubt anyone is going to bother to port it.

---

### Post by mips on 2009-02-23
> **AaronP_ said:**
> VDPAU requires GeForce 8 or higher.


Not all 8xxx series models are supported either, ie. 8800GTS 320/640MB & 8800GTX.

Not all chipsets have support for all the decoders either:
[ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/appendix-h.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/appendix-h.html)
> 
**VdpDecoder**

    In all cases, VdpDecoder objects solely support 8-bit 4:2:0 streams, and only support writing to VDP_CHROMA_TYPE_420 surfaces.
 [COLOR=Red]**The exact set of supported VdpDecoderProfile values depends on the hardware model in use.**[/COLOR]
     **G84, G86, G92, G94, G96, GT200**

 
 
 
 These chips support the following VdpDecoderProfile values:
  
[LIST]
[*] VDP_DECODER_PROFILE_MPEG1, VDP_DECODER_PROFILE_MPEG2_SIMPLE, VDP_DECODER_PROFILE_MPEG2_MAIN:
[LIST]
[*] Partial acceleration.
[*] Minimum width or height: 3 macroblocks (48 pixels).
[*] Maximum width or height: 128 macroblocks (2048 pixels).
[*] Maximum macroblocks: 8192
[/LIST]
 
[*] VDP_DECODER_PROFILE_H264_MAIN, VDP_DECODER_PROFILE_H264_HIGH:
[LIST]
[*] Complete acceleration.
[*] Minimum width or height: 3 macroblocks (48 pixels).
[*] Maximum width or height: 128 macroblocks (2048 pixels).
[*] Maximum macroblocks: 8192
[/LIST]
 
 
[/LIST]
 
  
     **G98, MCP77, MCP78, MCP79, MCP7A**

 
 
 
 These chips support the following VdpDecoderProfile values:
  
[LIST]
[*] VDP_DECODER_PROFILE_MPEG1, VDP_DECODER_PROFILE_MPEG2_SIMPLE, VDP_DECODER_PROFILE_MPEG2_MAIN:
[LIST]
[*] Complete acceleration.
[*] Minimum width or height: 3 macroblocks (48 pixels).
[*] Maximum width or height: 128 macroblocks (2048 pixels).
[*] Maximum macroblocks: 8192
[/LIST]
 
[*] VDP_DECODER_PROFILE_H264_MAIN, VDP_DECODER_PROFILE_H264_HIGH:
[LIST]
[*] Complete acceleration.
[*] Minimum width or height: 3 macroblocks (48 pixels).
[*] Maximum width: 127 macroblocks (2032 pixels).
[*] Maximum height: 128 macroblocks (2048 pixels).
[*] Maximum macroblocks: 8190
[*] Unsupported widths: 49, 54, 59, 64, 113, 118, 123 macroblocks (784, 864, 944, 1024, 1808, 1888 pixels).
[/LIST]
 
[/LIST]





---

### Post by Rawit on 2009-02-23
Not some power-saving mode that get's enabled after a while? I can vaguely remember reading something about that with past drivers... Power saving mode kicking in, lower clockspeed of the gpu, and the desktop with visual effects becoming slow.

I think at the nvidia-settings panel you can read the current state of the gpu (power, speed).

> **Montblanc_Kupo said:**
> So there's something I noticed with the 180 versions. I can install them... and they might work okay at first... but slowly the system gets less and less responsive over time (time like... over the course of 20 minutes or so). Things will run better than 177.xx at first... then slowly get slower. Applications will continue to run okay, but when the video card kicks into 3D mode... it takes a second to do it... and it runs slowly. So anything from rotating the compiz desktop cube to glxgears ... anything using the 3D seems affected. Uninstall 180.xx and reinstalled 177.xx and it's back to normal... runs all day without slowdown.

I have a geforce 6800XT 256mb card.

Any ideas?

---

### Post by Slim Odds on 2009-02-23
> **xX-Felipao-Xx said:**
> My video card is a FX5200

The FX5200 is not supported by the 180 driver.

It uses the 173 driver.......

---

### Post by crjackson on 2009-02-23
> **walkerk said:**
> I wasn't too successful w/ 180.29. I can install the driver w/o problems and run pekwm flawlessly. 

My problem comes if I try to run Compiz... the screen just goes black and I have to restart X. Anyone having this same problem? Oh and compiz-check comes back w/o issues...

GeForce Go 7150M

Did you resolve the issue. Could it have been something other than the 180's vs Compiz issue?

My brother has that card and was considering the update due to current problems with compiz / 177 drivers.

---

### Post by Reklov on 2009-02-24
Ok, the buggy 177.xx drivers really bothered me since I installed Intrepid about 2 weeks ago. I had to install it 6 times because I experimeted a lot until I had a system that was usable ;) ... (Manual install of current drivers, trying different distros and so on.)

The main problem I had with both drivers, the 173 and the 177, was that the CPU permanently ran at 98% up to 100%. That's not tolerable of course, and I didn't want the old 800 res with no 3D.

The first thing I found out was that I had to lower the screen refresh rate from 85 Hz to 75 Hz at 1600x1200. I don't know hy that helped, but it did. So I now have about 3% or 4% CPU load. I used the latest 177 driver until tonight.

I had another problem with the 173 and 177 drivers: The window title bars went gray all the time, and there were a few other graphic bugs as well.

So tonight I decided to find a working solution. And I think I did, partly with the help of this thread. 


The following will only work with Intrepid Ibex!!!

This is what I did ...

1) Install the latest 177 driver using System->Administration->Hardware Drivers
2) Start **System->Synaptic** and search for *nvidia*
3) Find the package '*nvidia-180-modaliases*', check it and install it.
4) Reboot your computer and log back in
5) Run **System->Administration->Hardware Drivers** and activate the new 180 driver. Wait untill it is fully installed, Hit **Close** and reboot again.

You now have the 180.11 driver installed and running. Check it in System->Administration->NVIDIA X Server Settings

The 180.11 driver might be sufficient for you, so only go further if you want the latest driver (180.29 which is considered stable by NVIDIA).

I do not give any guaranties that the following will work or that I didn't forget a step.

The harder part now ...
6) Go to **System->Administration->Software Sources**.
7) Press the **Third Party Software** tab and hit the **Add** button.
8) Copy the line below and paste it into the APT line:
[FONT="Courier New"]deb [http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu) intrepid main[/FONT]
9) Press **Add Source**
10) Back in the Third Party Software window, press **Add** again
11) Copy the line below and paste it into the APT line:
[FONT="Courier New"]deb-src [http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu) intrepid main[/FONT]
12) Press **Add Source** and then click **Close** to save your changes.
13) You will be notified that the information about available software is out-of-date. Press **Reload**.
14) Now you need a GPG key for the new repositories. You get the key from here: [http://keyserver.ubuntu.com:11371/pks/lookup?search=0x026491A5DD081BDC6CDFC0DE6298AD34413576CB&op=get]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x026491A5DD081BDC6CDFC0DE6298AD34413576CB&op=get")
15) Open your editor then copy all the text beginning with ----- to the end and paste it into the editor. Then save it to a location of your choice. Remember where you save it.
16) Import the key by selecting the **Authentication** tab, clicking on **Import Key File**, and then selecting the file you saved in the previous step to be imported.
17) **Close** the Software Sources window.
18) Launch the **Update Manager** from **System->Administration**.
19) **Check** for new updates
20) You will now see a list of NIVIDIA drivers that want to be updated. Do the update then reboot your computer and log back in.
21) Finally, check System->Administration->NVIDIA X Server Setttings for the latest driver being installed and running.

If anything went wrong, you can easily get back the 177 driver from **System->Administration->Hardware Drivers**

If you don't want to get frequently updated Ubuntu beta drivers, you should uncheck the two new repositories in **System->Administration->Software Sources** and the tab **Third Party Software**. If there is a newer driver available you're interested in, just check the entries again and run an update in the Update Manager.

I hope this helps :)

Regards

---

### Post by Reklov on 2009-02-24
A few more tips and hints if you got stuck at some point when installing a NVIDIA driver ...

[LIST]
[*]Always make a backup of your */etc/X11/xorg.conf* as there is no easy way reparing it after it is broken!
[*]If you don't see NVIDIA drivers in the **Hardware Drivers** manager, you can try to install all 'NVIDIA-###-modaliases' packages. Make sure the package 'nvidia-common' is installed as well. Then reboot your computer, log back in and check **Hardware Drivers** for NVIDIA are available now.
[*]Do never uninstall all NVIDIA packages! Even if someone says so. It will break your system and X won't be able to start properly. At least the packages 'nvidia-common', 'xserver-xorg-video-nv' and 'NVIDIA-###-modaliases' must remain installed.
[*]If you have successfully installed an NVIDIA driver and you do not have **System->Administration->NVIDIA X Server Settings**, install the package 'nvidia-settings'.
[*]If you don't see NVIDIA drivers in **System->Administration->Hardware Drivers**, even if you have installed the packages 'nvidia-common' and 'nvidia-###-modaliases', or you don't have the **Hardware Drivers** at all, you may need to install the packages mentioned and 'jockey-common' and 'jockey-gtk' (for Gnome) or 'jockey-kde' (for KDE).
[/LIST]

EDIT: Another one: After a fresh install of Ubuntu, first do the updates, then reboot and then install NVIDIA drivers. This is very important!

I hope that helps someone.

Regards

---

### Post by Montblanc_Kupo on 2009-02-24
> **Rawit said:**
> Not some power-saving mode that get's enabled after a while? I can vaguely remember reading something about that with past drivers... Power saving mode kicking in, lower clockspeed of the gpu, and the desktop with visual effects becoming slow.

I think at the nvidia-settings panel you can read the current state of the gpu (power, speed).

I hadn't checked on that... doesn't make much sense if it is though. Seems like 177 would do the same thing too... and it doesn't. It feels more like a memory leak though because it will get progressively worse after a while until anything 3D is just not gonna work right.

There are no settable parameters in the powermizer section of the nvidia server control... it will tell you the speed and such but doesn't have any place to set timeouts or even say that it is.

Dunno... but the 180.xx drivers are the only ones that do it. 173 and 177 both run without the slowdown issue.

---

### Post by Bart_D on 2009-02-24
> **Slim Odds said:**
> The FX5200 is not supported by the 180 driver.

It uses the 173 driver.......

How do you know this?  Is there a list?

---

### Post by Slim Odds on 2009-02-24
> **Bart_D said:**
> How do you know this?  Is there a list?

They are listed on the nvidia website.

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

---

### Post by mips on 2009-02-25
> **Bart_D said:**
> How do you know this?  Is there a list?

The list is on the website as mentioned above. The easy answer is that the 180.xx drivers only support the 6xxx series cards and above.

---

### Post by Kosimo on 2009-02-25
Guys, 180.35 are here! :)

Changelog
>     *  Added support for the following GPUs:
          o GeForce GT 120
          o GeForce G100
          o Quadro FX 3700M
    * Fixed a bug that caused Maya to freeze when overlays are enabled.
    * Fixed an interaction problem with some applications that use memory tracking libraries.
    * Added support for RG renderbuffers in OpenGL 3.0.
    * Added support for OpenGL 3.0 floating-point depth buffers.
    * Fixed a problem that caused Valgrind to crash when tracing a program that uses OpenGL.
    * VDPAU updates:
          o VDPAU now supports VC-1/WMV acceleration on all GPUs supported by VDPAU; see the README for details.
          o Expand the documentation of VDPAU's VdpVideoMixer, in particular regarding how to use the deinterlacing algorithms. Explicitly document "half rate" deinterlacing, which should allow the advanced algorithms to run on more low-end systems. See vdpau.h.
          o Implement a "skip chroma deinterlace" option in VDPAU, which should allow the advanced deinterlacing algorithms to run on more low-end systems. See vdpau.h.
          o Enhance VDPAU to correctly handle some forms of corrupt/invalid MPEG streams on some GPUs.
          o Fix VDPAU to prevent some cases of "display preemption" in the face of missing H.264 reference frames on some GPUs.
          o Fix VDPAU to correctly handle VC-1 skipped pictures with missing start codes on some GPUs.
          o Fix VDPAU to correctly handle WMV "range reduction" on some GPUs. A minor backwards-compatible API change was made for this; see vdpau.h's documentation for structure field VdpPictureInfoVC1.rangered.
          o Fix VDPAU wrapper library to print dlerror() messages when problems occur, which will simplify debugging of driver loading issues.

The 180.35 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 180.35 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86-64 is available for download via FTP.

---

### Post by Kosimo on 2009-02-25
The biggest news in this release is:

VDPAU now supports VC-1/WMV acceleration on all GPUs supported by VDPAU; see the README for details. 
:guitar:

---

### Post by Kosimo on 2009-02-26
I didn't have time to test 180.35, anyone here did?

---

### Post by TheAL76 on 2009-02-26
> **Kosimo said:**
> I didn't have time to test 180.35, anyone here did?


I installed it, but didn't test it extensively. From the little bit I did see, I didn't notice much difference. But, at least nothing broke!

Can someone explain VDPAU in simple terms, and discuss how I can make use of it? I have an 8600GT, and I believe that is one of the supported cards.

---

### Post by Kosimo on 2009-02-26
> **TheAL76 said:**
> I installed it, but didn't test it extensively. From the little bit I did see, I didn't notice much difference. But, at least nothing broke!

Can someone explain VDPAU in simple terms, and discuss how I can make use of it? I have an 8600GT, and I believe that is one of the supported cards.

Thanks! I'll give them a try tonight once back home ;)

VDPAU is what "pure video" is for Windows. That means that Video will be full GPU hardware accelerated. This will reduce the CPU utilization when watching videos and will assure a very good performance when using high def videos.
In order to use VDPAU you neew trhee things: 
[LIST=1]
[*]a VDPAU supported videocard
[*]VDPAU enabled divers
[*]a specially compiled player (Yes you need to compile your own player with VDPAU patches that you can get from nvidia linux forum)
[/LIST]

Hope it helps.

---

### Post by TheAL76 on 2009-02-26
> **Kosimo said:**
> Thanks! I'll give them a try tonight once back home ;)

VDPAU is what "pure video" is for Windows. That means that Video will be full GPU hardware accelerated. This will reduce the CPU utilization when watching videos and will assure a very good performance when using high def videos.
In order to use VDPAU you neew trhee things: 
[LIST=1]
[*]a VDPAU supported videocard
[*]VDPAU enabled divers
[*]a specially compiled player (Yes you need to compile your own player with VDPAU patches that you can get from nvidia linux forum)
[/LIST]

Hope it helps.

Yes, very much so. So I guess I have the first 2; is there a good guide for doing step number 3? And can I compile the patches with any video player (Totem, VLC) or is there some specific one I have to use?

Thanks!

---

### Post by Polygon on 2009-02-26
i think only mplayer has patches at the moment, im sure future updates of all players will eventually include vdpau support

---

### Post by PsychedelicWonders on 2009-02-28
Do I want to download all 3 packages?:

NVIDIA-Linux-x86_64-180.35-pkg0.run	RUN	13890 KB	02/24/2009 02:34:00 AM
NVIDIA-Linux-x86_64-180.35-pkg1.run	RUN	13893 KB	02/24/2009 02:34:00 AM
NVIDIA-Linux-x86_64-180.35-pkg2.run	RUN	20956 KB	02/24/2009 02:34:00 AM

Or just one of these?

---

### Post by Danny Dubya on 2009-02-28
Just one... pkg2 is probably your safest bet.

---

### Post by PsychedelicWonders on 2009-02-28
hmm alright.

What is the difference between all 3?

So I dont get it, when I run all the code on the 1st page of this walk thru, it will shut down everything but the terminal?

I cant remember all of those different codes you have to do... do I really have to write them down on a piece of paper?

I'm not that good with Ubuntu yet to memorize the codes.

I can work the terminal however.

I assume as I enter in each code, it will prompt me for the next thing to do?

---

### Post by PsychedelicWonders on 2009-02-28
When I try to download from here:

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/)

My browser doesnt download anything, just loads up a GIANT read me file.

What do I do?

I'm getting a 2nd Asus video card in a few days, should I wait till its installed to run this new driver walk-thru?

Or will I just have to do it all over again when I get it?

---

### Post by Kosimo on 2009-03-01
> **PsychedelicWonders said:**
> When I try to download from here:

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/)

My browser doesnt download anything, just loads up a GIANT read me file.

What do I do?

I'm getting a 2nd Asus video card in a few days, should I wait till its installed to run this new driver walk-thru?

Or will I just have to do it all over again when I get it?

Instead of clicking to the file, just hit (right button, save as)
then you can save it in your desktop

---

### Post by Spif on 2009-03-01
Any reliable way to install 180.35 on Hardy?

A .deb package would be great.

---

### Post by mad_max0204 on 2009-03-01
Why would you need deb package ?

Dont be so lazy. Download driver, kill gdm, run installer and run gdm again. 2 minutes of work and it always works.

---

### Post by PsychedelicWonders on 2009-03-01
> 2) Enter in a real terminal mode: CONTROL + ALT + F1 (don't do it now as you wouldn't be able to keep reading)

So if I cant keep the webpage open, and I'm not familary enough with Ubuntu to remember all of these codes, what application can I open and save these in for visual reference as I'm entering them?

Wordpad?

Or will that close also?

I can do this, as long as I can still visually see the directions.

But with out them, I'm completely lost.

> 3) Turn off x.org: 
Code:
sudo /etc/init.d/gdm stop
4) Go to your desktop: 
Code:
cd Desktop
5) Run the installer: 
Code:
sudo sh ./Nxxx.run
(If you hit TAB after the first N the rest of the filename it will automatically appear) 
Don't forget to choose x.org automatic configuration at the last step inside the installation program.

6) Then restart your computer and you're done

---

### Post by Perfect Storm on 2009-03-01
Print it or write it down. Note; you still need headers for the kernel to do it.

---

### Post by PsychedelicWonders on 2009-03-01
> **Artificial Intelligence said:**
> Print it or write it down. Note; you still need headers for the kernel to do it.

Well I dont have a printer, so I guess writing it down is the only option.

Why does that first code completely shut everything down?

What do you mean it still needs headers for the kernal to do it?

---

### Post by Slim Odds on 2009-03-01
> **PsychedelicWonders said:**
> Well I dont have a printer, so I guess writing it down is the only option.

Well.... that's what we did before printers..... :P

> Why does that first code completely shut everything down?It shuts down the GUI (graphical interface).

> What do you mean it still needs headers for the kernal to do it?The driver has to build some files that need the info about the kernel (which is in the headers).

---

### Post by PsychedelicWonders on 2009-03-01
> **Slim Odds said:**
> 
The driver has to build some files that need the info about the kernel (which is in the headers).

Is this a step that happens automatically when I go through all of those codes?

Or is this an addtional step that I have to do?

I honestly have no idea what you even mean, so I hope it happpens automatically.

---

### Post by Danny Dubya on 2009-03-01
> **mad_max0204 said:**
> Why would you need deb package ?

Dont be so lazy.
The poster did not even once say they didn't feel like installing the .run file or refuse to, and only requested additional information, so I'm curious as to where this response came from.

---

### Post by mips on 2009-03-01
> **Artificial Intelligence said:**
> Print it or write it down. Note; you still need headers for the kernel to do it.

Even better, save it as a text file that you can access from the console. Less labour intensive ;)

---

### Post by darco on 2009-03-01
Dont want to make things more confusing but I did post these steps and few pages back...

system > administration > hardware > disable any nvidia drivers if any are enabled

run: sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
run: sudo apt-get autoremove

test: ctrl + atl + backspace : reconfigure display - after gdm restart no gfx drivers should be in use

stop gdm: sudo /etc/init.d/gdm stop

login with normal account

sudo sh /<driver location>/NVIDIA-Linux-x86_64-180.29-pkg2.run

start gdm: sudo /etc/init.d/gdm start

I will upgrade to .35 following these steps and get back to you all w/results.

darco

p.s. ok, so I tried the above and after stopping gdm, it hangs at Checking Battery state:ok
Tried Recovery mode and though I can install the driver, the installer doesnt recommend it installing at root level.
p.s.s ok, in recovery mode I chose Fix x server, rebooted, than ran above and .35 installed

---

### Post by Montblanc_Kupo on 2009-03-02
> **mad_max0204 said:**
> Why would you need deb package ?

Dont be so lazy. Download driver, kill gdm, run installer and run gdm again. 2 minutes of work and it always works.

Well... maybe it's the teeny tiny fact that it DOESN'T always work.

Don't be such a jackass.

---

### Post by cmat on 2009-03-02
> **Montblanc_Kupo said:**
> Well... maybe it's the teeny tiny fact that it DOESN'T always work.

Don't be such a jackass.

Who's to say that the *.deb will work? 

Using Envy made it much more difficult to install the vanilla driver later on. It's best either to wait for the official repo release or do it yourself. Unless you have a hacked kernel it's almost certain that it will install correctly. I did it on many machines without incident. Just print out the guide posted above and try it out, something goes wrong, XFIX in recovery console and use the repo version.

Anyways, I don't think one is available yet. I think there is one in the Jaunty repo though.

Tried it out on Quake Wars but the performance is still not up to par with windows. FPS is the same but fluctuates more wildly on Ubuntu.

---

### Post by FraggedLocust on 2009-03-02
I'm eager to get this installed so I can use the default human/DarkRoom themes without the titles messing up. But everytime I try installing them, I break X.
- nVidia GeForce 750m (currently using 177)

---

### Post by mips on 2009-03-02
> **FraggedLocust said:**
> 
- nVidia GeForce 750m

750m, is that correct?

---

### Post by FraggedLocust on 2009-03-02
Sorry, I believe that must be the chipset.
GeForce Go 7200

---

### Post by erolinux on 2009-03-02
I spent so many hours fixing nvidia driver bugs, that I wont spend a dime ont this product again.

I have Nvidia 7300GT

[LIST]on windows, screen freezing "stuck in device loop"[/LIST]
[LIST]on linux, screen 800 x 600 at each new kernel release, with blinking refresh rate[/LIST]

Nvidia NEVER repairs the bugged drivers, they want us to install the new ones, but these dont support older cards.

Now I am tired of installing new drivers for a material which never satisfied me. Buy once, instal 2349 times and get no support?

So have fun with 180.xx, you are a lucky person :-)

---

### Post by pol666 on 2009-03-02
i'm using on Kubuntu 8.10, Quite stable and fixes some KDE issues.

---

### Post by jocheem67 on 2009-03-03
Got the latest driver on 7600Go...
Had some install issues, but no biggy...however I had to do new install of nvidia x server settings.

Now I'm fiidling around with setting up a dual monitor, connected to my dell insp. 9400 through DVI..
Hmmm....never done this before, but it seems to work alright. I've got separate x-screens, atm rhythmbox is filling my notebookscreen and I'm typing this on my philips lcd...
Very nice:popcorn:

One thingy: screensavers, however very beautiful and complementary over the two monitors, require a ctrl -- alt -- backspace..
Leaving a "black screen" as protection works though.

---

### Post by FraggedLocust on 2009-03-03
Got it to work on mine. Only problem I'm having is that the desktop doesn't show until I enter and exit a terminal.

---

### Post by PsychedelicWonders on 2009-03-03
> **Slim Odds said:**
> 
The driver has to build some files that need the info about the kernel (which is in the headers).

Is this a step that happens automatically when I go through all of those codes?

Or is this an addtional step that I have to do?

I honestly have no idea what you even mean, so I hope it happpens automatically.

---

### Post by Shagg on 2009-03-03
> **FraggedLocust said:**
> Got it to work on mine. Only problem I'm having is that the desktop doesn't show until I enter and exit a terminal.

Yeah, the same thing here (GeForce 7000M, Ubuntu 8.10). As a workaround, you can try hibernating instead of turning off, at least it works for me.


Anyway, does anybody have a clue on how to fix this? I just wouldn't know where to start looking.

---

### Post by PsychedelicWonders on 2009-03-06
Can someone help explain the walk thru a little better to me?

I guess I'm nervous about this because it shuts down the GUI

Quote:
Originally Posted by Slim Odds  
The driver has to build some files that need the info about the kernel (which is in the headers). 

Is this a step that happens automatically when I go through all of those codes?

Or is this an addtional step that I have to do?

I honestly have no idea what you even mean, so I hope it happpens automatically.

---

### Post by Kareeser on 2009-03-06
Walk-through... the installation?

---

### Post by jocheem67 on 2009-03-06
Shutting down the GUI may seem like a big step, but in fact you're just using a terminal....
Rebooting always gives you back your GUI, however if something went wrong it'll be low resolution.....

Just follow the steps....

Or, if you feel uncomfortable with this whole thing, just don't try it.

I believe you can install one of the 180.* drivers from synaptic....this might need adjusting your sources though ( backports? proposed? )

---

### Post by Slim Odds on 2009-03-06
> **PsychedelicWonders said:**
> 
Quote:
Originally Posted by Slim Odds  
The driver has to build some files that need the info about the kernel (which is in the headers). 

Is this a step that happens automatically when I go through all of those codes?

Or is this an addtional step that I have to do?

When you install via the .run file, then it's automatically part of the process......

---

### Post by NoranaC on 2009-03-06
I tried installing nVidia 180 and when I restarted all I got was a blank screen.  I uninstalled it and tried an earlier version and still - blank screen.  Anyone else having these problems with the new driver?

---

### Post by mips on 2009-03-06
I suspect this is not the easiest thing to do in ubuntu compared to some other distros.

---

### Post by Kosimo on 2009-03-07
I wish some day nVidia will publish nice .deb's on their website.

[wishmode: on]
nVidia presented the new 230.10 drivers! Download them here! nVidia230.10.deb 
   [wishmode: off]

Some day guys, some day...

---

### Post by Kosimo on 2009-03-07
Guys:   180.37 released!


Changelog: 

>     *  Fixed a problem that caused signals to be blocked in some applications.
    * Fixed a problem that could cause Xid errors and display corruption in certain cases when OpenGL is used to render to redirected windows, for example when Java2D is used with the -Dsun.java2d.opengl=true option.
    * glGetStringi(GL_EXTENSIONS, i) no longer returns NULL in OpenGL 3.0 preview contexts.
    * Fixed a problem that caused the screen to flicker momentarily when OpenGL applications exit unexpectedly on GeForce 6 and 7 series GPUs.
    * Fixed an X server crash when an X client attempts to draw trapezoids and RenderAccel is disabled.
    * Improved recovery from certain types of errors.
    * VDPAU updates:
          o Fixed corruption on some H.264 clips.
          o Update documentation.
          o Fixed VC-1 decoding on 64-bit platforms.
          o Improved handling of invalid H.264 streams.
          o Fixed a problem that caused surfaces to be marked as visible too early when the blit presentation queue is in use.


Get them [here]("http://www.nvnews.net/vbulletin/showthread.php?p=1951107")

---

### Post by Mazza558 on 2009-03-08
I'm about to upgrade to Jaunty Alpha, will I need to reinstall the Nvidia driver beforehand (due to kernel updates etc)?

---

### Post by Twitch6000 on 2009-03-08
> **Mazza558 said:**
> I'm about to upgrade to Jaunty Alpha, will I need to reinstall the Nvidia driver beforehand (due to kernel updates etc)?

After you upgrade you will have to install the Nvidia driver for the new kernel.

---

### Post by Twitch6000 on 2009-03-08
> **Kosimo said:**
> I wish some day nVidia will publish nice .deb's on their website.

[wishmode: on]
nVidia presented the new 230.10 drivers! Download them here! nVidia230.10.deb 
   [wishmode: off]

Some day guys, some day...

Well I find these .run files easy enough to run and since they run on any distro... wouldn't that be better then them having to make a .deb for each main distro and a .rpm for each main distro?

If only their .run file wasn't so complex we had to be in CLI mode lol.

---

### Post by simtaalo on 2009-03-08
> **Twitch6000 said:**
> Well I find these .run fi;es easy enough to run and since they run on any distro... wouldn't that be better then them having to make a .deb for each main distro and a .rpm for each main distro?


i dunno, there's a user over on fedora forums who always makes rpm's of the new nvidia drivers, so why not someone making debs for here.

---

### Post by Twitch6000 on 2009-03-08
> **simtaalo said:**
> i dunno, there's a user over on fedora forums who always makes rpm's of the new nvidia drivers, so why not someone making debs for here.

Maybe so,but even with that one .rpm it cannot be guaranteed to work on every distro that uses .rpm's .(even though I have oddly never had trouble doing this...)


Also look at what you said too it is someone from the fedora forums make the .rpms not some from the nvidia team . So unless someone has enough free time to make a .deb then I do not see it happening.

---

### Post by walkerk on 2009-03-08
> **crjackson said:**
> Did you resolve the issue. Could it have been something other than the 180's vs Compiz issue?

My brother has that card and was considering the update due to current problems with compiz / 177 drivers.

No fix with 180.29 but I am happy to say 180.37, from [[COLOR="DarkOrange"]this post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6854318&postcount=565"), works great.

---

### Post by djungelmums on 2009-03-09
Is 9800 GT supported or just 9800 GTX?

---

### Post by Kosimo on 2009-03-09
> **djungelmums said:**
> Is 9800 GT supported or just 9800 GTX?

Both of them should be supported.

---

### Post by Roasted on 2009-03-09
Is there an easy way to install 180 yet? I installed them the hard way with the "official guide" here on forums and it broke my sytem.

---

### Post by bhoth on 2009-03-09
> **walkerk said:**
> No fix with 180.29 but I am happy to say 180.37, from [[COLOR="DarkOrange"]this post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6854318&postcount=565"), works great.

Whats the difference between package 0 and package 1?

---

### Post by Sockerdrickan on 2009-03-09
nothing really, just more pre compiled versions.

---

### Post by Christopher on 2009-03-09
Now theres a package 2?  :D

---

### Post by Sockerdrickan on 2009-03-09
Yeah they keep updating them.

---

### Post by The Bright Side on 2009-03-09
Hi guys... I just tried installing this and when I turn off X Server, my PC hangs at "Checking Battery State". Any ideas? I so want these drivers :-(

---

### Post by crjackson on 2009-03-10
> **Christopher said:**
> Now theres a package 2?  :D

Really? I only see 0 & 1, do you have a link to package 2?

---

### Post by Mazza558 on 2009-03-10
The 180.29 drivers are working great for me, but there is one big problem: there are 2 websites which I frequent which seem to scroll abnormally slow, and only with Nvidia + Linux. They are:

[The Student Room]("http://www.thestudentroom.co.uk/")
Facebook. 

Does anyone else have problems with these websites?

---

### Post by djungelmums on 2009-03-10
What packages do i have to install before?
What packages do i have to uninstall before? (Ive got drivers installed from "Hardware Drivers")

---

### Post by The Bright Side on 2009-03-10
Try this:

"To see nvidia 180 driver in hardware drivers, install nvidia-180-modaliases.
To do this you can type in terminal sudo apt-get install nvidia-180-modaliases . Or you can use synaptic."

This quote is from here:
[http://ubuntuforums.org/showthread.php?t=993788&page=4](http://ubuntuforums.org/showthread.php?t=993788&page=4)

Worked like a charm for me! After doing that, you'll have it available in your System -- Adminístration -- Hardware Drivers menu. I got 180.11 this way and am very happy with it. It's not the latest either, but close :-)

---

### Post by MCMcButtah on 2009-03-12
> **Mazza558 said:**
> The 180.29 drivers are working great for me, but there is one big problem: there are 2 websites which I frequent which seem to scroll abnormally slow, and only with Nvidia + Linux. They are:

[The Student Room]("http://www.thestudentroom.co.uk/")
Facebook. 

Does anyone else have problems with these websites?


I can tell you that out of no where a few months ago firefox started to become super slow when scrolling on certain sites.
After i turned off flash, scrolling was fast again. Since not using flash really isn't an option I installed FF 2 and that works great with flash and all the performance problems I had went away. Made me realize the thing that happened a few months ago was an upgrade from FF2 to FF3.

As a side note I also noticed that Opera was almost as slow on the problem sites with scrolling as FF3. Konqueror did not have this scrolling problem on these sites.

---

### Post by TheAL76 on 2009-03-14
185.13 has been posted. It is a beta, so keep that in mind.

---

### Post by Kosimo on 2009-03-14
> **TheAL76 said:**
> 185.13 has been posted. It is a beta, so keep that in mind.

Thanks for the heads up! :KS

The only thing I'm missing is a complete changelog list.
Nothing is mentioned here:
[http://www.nvnews.net/vbulletin/showthread.php?p=1957328](http://www.nvnews.net/vbulletin/showthread.php?p=1957328)

---

### Post by TheAL76 on 2009-03-14
So far, so good with 185.13 and an 8600GT.

Anyone else try it yet?

---

### Post by Polygon on 2009-03-14
what the heck? how is the linux driver now ahead of the windows one?

the latest one i see for windows vista is 182.08 while we are now on 185.13 O.o

---

### Post by Kareeser on 2009-03-14
*shrugs* Why's that such a surprise? Perhaps it's easier to develop drivers for Linux.

---

### Post by Twitch6000 on 2009-03-14
> **Kareeser said:**
> *shrugs* Why's that such a surprise? Perhaps it's easier to develop drivers for Linux.

Or perhaps they are saying sorry in a way for their crappy 177 drivers <.<?

---

### Post by Kosimo on 2009-03-14
> **TheAL76 said:**
> So far, so good with 185.13 and an 8600GT.

Anyone else try it yet?

How about Compiz and VDPAU performance?

---

### Post by cmat on 2009-03-14
Possibly they aren't related but have release numbers that are very close, IDK.

---

### Post by cmat on 2009-03-14
> **Mazza558 said:**
> The 180.29 drivers are working great for me, but there is one big problem: there are 2 websites which I frequent which seem to scroll abnormally slow, and only with Nvidia + Linux. They are:

[The Student Room]("http://www.thestudentroom.co.uk/")
Facebook. 

Does anyone else have problems with these websites?

I'm currently on my laptop with Vista. Those sites do scroll slowly with FF3. Facebook isn't that bad though. There are also issues with GTK apps having slow scroll speeds. Do you have a GeForce *200 M?

---

### Post by The Bright Side on 2009-03-14
I installed the new 185 driver according to the instructions on the front page. It installed without any problems, I was so happy that this worked, but then I restarted and Ubuntu went into low graphics mode, telling me some kernel or something wasn't available or correct, idk.

And there I was thinking something would finally work here. Can anybody give me suggestions about what went wrong? Like I said, installation worked w/o any problems at all, but then it went to low graphics mode :-(

---

### Post by Kosimo on 2009-03-14
> **The Bright Side said:**
> I installed the new 185 driver according to the instructions on the front page. It installed without any problems, I was so happy that this worked, but then I restarted and Ubuntu went into low graphics mode, telling me some kernel or something wasn't available or correct, idk.

And there I was thinking something would finally work here. Can anybody give me suggestions about what went wrong? Like I said, installation worked w/o any problems at all, but then it went to low graphics mode :-(

What graphics card are you currently using?
What Ubuntu version are you using?
did you choose automatic x.org configuration at the last step inside the installation program?

---

### Post by keiichidono on 2009-03-14
I wonder if I should install 180.37 or 185.13. I'm pretty fine with 180.29 but I kind wanna see if I can better performance in MPlayer and with Compiz. Can anyone give me some feedback on these two drivers?

---

### Post by The Bright Side on 2009-03-15
It's Ubuntu 8.10 64 bit, Graphics card is Nvidia 6150SE nForce 430. I think I did choose the automatic configuration...

I now installed 180.11 from Synaptics, but even with that installed correctly I cannot turn on Desktop Effects or anything. Here's what I get when I type "compiz" in the terminal:


Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 


That stuff used to work before I re-installed my entire system this morning because many other programs didn't work. Now I can't even get the drivers to work anymore, I don't even want to try to get to the other programs :-(

Thanks anyway! Any advice is appreciated.

---

### Post by Kareeser on 2009-03-15
Sounds like a bug... you should copy that error message and create a new bug report on Launchpad for compiz...

---

### Post by keiichidono on 2009-03-15
> **The Bright Side said:**
> It's Ubuntu 8.10 64 bit, Graphics card is Nvidia 6150SE nForce 430. I think I did choose the automatic configuration...

I now installed 180.11 from Synaptics, but even with that installed correctly I cannot turn on Desktop Effects or anything. Here's what I get when I type "compiz" in the terminal:


Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 


That stuff used to work before I re-installed my entire system this morning because many other programs didn't work. Now I can't even get the drivers to work anymore, I don't even want to try to get to the other programs :-(

Thanks anyway! Any advice is appreciated.

Install this driver? [http://www.nvidia.com/object/linux_display_amd64_180.29.html](http://www.nvidia.com/object/linux_display_amd64_180.29.html)

---

### Post by jespdj on 2009-03-15
With driver 185.13 (beta) I still have the problem that parts of the screen do not redraw properly, for example menus. See the attached screenshot.

I've had this problem with every 180.xx or newer driver. The problem is not there with driver 177.xx. Using Ubuntu 8.04.2, 64-bit on my Dell XPS M1530 with 8600M GT.

:(

Is this a bug in the driver or in Compiz Fusion? It looks like it doesn't happen if I switch desktop effects off, so maybe it's a bug in Compiz Fusion.

---

### Post by Kosimo on 2009-03-15
> **jespdj said:**
> With driver 185.13 (beta) I still have the problem that parts of the screen do not redraw properly, for example menus. See the attached screenshot.

I've had this problem with every 180.xx or newer driver. The problem is not there with driver 177.xx. Using Ubuntu 8.04.2, 64-bit on my Dell XPS M1530 with 8600M GT.

:(

Is this a bug in the driver or in Compiz Fusion?

Curious bug... You should may ask something in official nvidia forums. Maybe you can find some answers there.

---

### Post by The Bright Side on 2009-03-15
Hey, I re-installed the second most recent pkg (180.37), and now everything works splendidly! Thanks again fellas! :-)

I have one more question: when installing the thing from the command line, it told me it would now uninstall an old version and that that was probably installed by other means then the Nvidia installer, e.g. Synaptic (smart little bugger). Generally, it seems like the Nvidia installer will uninstall any old drivers it finds automatically before installing itself, right?

So for the future, is that the way to go whenever I want to update? Or should I try to remove old Nvidia drivers myself before installing a pkg of a new release?

---

### Post by Kareeser on 2009-03-15
If it works properly, I wouldn't see why not... :)

---

### Post by AaronP_ on 2009-03-16
> **jespdj said:**
> Is this a bug in the driver or in Compiz Fusion? It looks like it doesn't happen if I switch desktop effects off, so maybe it's a bug in Compiz Fusion.
It's not a bug, it's a design flaw in the Damage extension.  The gist of it is that the X server tells Compiz that a window has been damaged before the damage actually happens, and Compiz wins the race and redraws the screen first.

---

### Post by jespdj on 2009-03-16
Do you know if there is a fix or workaround for this problem in a newer version of Compiz or the X server?

---

### Post by Kosimo on 2009-03-16
Trying 185.16 So far so good ;)

---

### Post by TheAL76 on 2009-03-16
> **Kosimo said:**
> Trying 185.16 So far so good ;)

Geez! Slow down, Nvidia :P

---

### Post by cmat on 2009-03-16
It's like I'm installing a new driver every other week. It's not like I mind though. ;)

Maybe I can finally dual-boot this Compaq CQ50. Video and power management were the only serious issues it has.

---

### Post by gersoid on 2009-03-16
Errr.my experience is that 180.xx certainly DOESN'T rock when trying to use Bibble 5 (Digital photo RAW processor) on my Dell inspiron 1520 + 8600M GT + ubuntu 8.10 / 2.6.27.13. 
I had to manually install 180.29 to get the rid of the blank-screen-on-startup when I was upgraded to kernel 2.6.27.13 (thanks Ubuntu...). Everything seemed to run fine, but Bibble 5 (preview version) won't start. This is a problem for Ubuntu users of Bibble (but apparently not for RH users); it's not just my machine. It matters because Bibble 5 is the best RAW processor for Linux (IMHO) and I don't reallywant to switch to RedHat just to use it...
has anyone out there tried 185.xx with Bibble 5? Bibble 4 works btw.

---

### Post by AaronP_ on 2009-03-16
> **gersoid said:**
> Everything seemed to run fine, but Bibble 5 (preview version) won't start.
What error do you get?  I'm going to take a wild guess and suggest adding Option "AllowSHMPixmaps" to xorg.conf.  If that helps, then this is a bug in Bibble 5.

---

### Post by gersoid on 2009-03-16
thks will check this out

---

### Post by pelle.k on 2009-03-16
185.13 working just fine, including suspend and whatnot. Nvidia 8600M GS on a LG R500 (Notebook) running intrepid.
I installed from thefirstM's PPA (intrepid and jaunty), [http://ubuntuforums.org/showpost.php?p=6894986&postcount=4](http://ubuntuforums.org/showpost.php?p=6894986&postcount=4)
Thankyou, thefirstM. Thankyou AaronP_ and co.

---

### Post by airtonix on 2009-03-16
> **steveneddy said:**
> [COLOR=Blue]**which**[/COLOR] drivers

witch is an ugly old woman that eats children.
lulz, only if you believe fairy tales created by the grimm brothers

---

### Post by devolute on 2009-03-17
I tried to install 180 from Synaptec but now everything has gone wrong. I don't have any working drivers and I can't even go back to 177. Every time I activate the drivers and re-install I get Xorg nagging me and then the screen appears garbled.

I think my xorg.conf is screwed. I can't run Compiz and I can't run NVidiaX Server Settings.

After 100 restarts, I think I need someone to tell me step by step how to clean this mess up. I'm happy to go back to 177 if needs be. It may be slow but at least it worked!

---

### Post by jocheem67 on 2009-03-17
You can still get into your graphical desktop ( x-server ) ?
Go into synaptic then and check for nvidia....
Uncheck all nvidia related packages, except the "modaliases" and the "nv" driver, and "nvidia-settings" 

Make sure you've got all sources enabled ( backports and proposed ) and select the 180 driver there.( nvidia-glx-180 )
Then try again.

---

### Post by simtaalo on 2009-03-17
just installed 185.13 + it works beautifully, fixed a few bugs that i've had during the 180.xx series.

---

### Post by devolute on 2009-03-17
> **jocheem67 said:**
> You can still get into your graphical desktop ( x-server ) ?
Go into synaptic then and check for nvidia....
Uncheck all nvidia related packages, except the "modaliases" and the "nv" driver, and "nvidia-settings" 

Make sure you've got all sources enabled ( backports and proposed ) and select the 180 driver there.( nvidia-glx-180 )
Then try again.

I can do that, thanks.  Before I do though; when I restart and I'm asking to create a new configuration or use a generic one or whatever; what option should I choose?

---

### Post by jocheem67 on 2009-03-17
The new one, it's the driver runfile that wants to write a new xorg.conf...
If you don't the new driver won't be loaded.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Mar  5 18:47:52 PST 2009

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips 190S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

The first part of my xorg.conf is interesting, you can see that it's generated by the nvidia-installer....don't mind the rest. It's a two monitor configuration...

I hope you succeed, it _can_ be a pain.

---

### Post by simtaalo on 2009-03-17
tbh if your really having trouble install them from this repo
[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by devolute on 2009-03-17
Tried both methods.  Have installed from the .debs as well.

Still refuses to active the nvidia drivers in 'Hardware Drivers'. How do I go back to 177? Everything worked perfectly back then!

---

### Post by jocheem67 on 2009-03-17
Don't mind the hardware drivers tab too much...can you post your xorg. conf?

> cat /etc/X11/xorg.conf

---

### Post by devolute on 2009-03-17
Currently:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@crested)  Thu Jun 26 06:23:58 UTC 2008

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       28.0 - 33.0
	VertRefresh     43.0 - 72.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	Driver	"nv"
EndSection

```

[edit]
I removed everything from synaptec manually and then followed these instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers)

It's all good again now, although 'Hardware Drivers' doesn't show anything. Should I be worried?

---

### Post by pelle.k on 2009-03-17
Heh, you're running the "nv" driver. Of course everything works :)
Rememeber to backup important config files before experimenting with your system.
This is a plain "ubuntu" xorg.conf for an nvidia card (it's from jaunty, but that shouldn't matter);
```
# xorg.conf (X.Org X Window System server configuration file)
#                                                            
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.                                         
#                                                                           
# Edit this file with caution, and see the xorg.conf manual page.           
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```
To reinstall the old driver, just
```
sudo apt-get install nvidia-glx-177
```

---

### Post by devolute on 2009-03-17
It now reads nvidia in the config. Still nothing 'Hardware Drivers'.

Thanks for your help everyone. First Ubuntu request for help. I've managed to get HL2 in Wine, Fireworks, all my music and video moved from NTFS, Boxee... I don't want to go back to Windows!

---

### Post by pelle.k on 2009-03-17
I never said anything about hardware drivers (that gui thing). I never use that anyway. All that matters is that you've got nvidia-glx-177 installed, and the "driver" component says "nvidia" in xorg.conf and you should be good.
Save that reinstall for jaunty (April 23).

---

### Post by jocheem67 on 2009-03-18
You can run 

> glxgears

to see if your rendering is okay. In the terminal that is....

---

### Post by devolute on 2009-03-18
My rendering is totally okay.  Nice work guys.

---

### Post by Kosimo on 2009-03-21
New prerelease: 180.41

Changelog 
> Release Highlights:

    * Added support for the following GPUs:
          o Quadro FX 3800
          o Quadro FX 1800
          o Quadro FX 580
          o Quadro FX 380
    * Fixed OpenGL crashes while running KDE4's Plasma.
    * Fixed OpenGL crashes when using a large number of texture objects.
    * Fixed the timestamp reporting in the GL_NV_present_video extension on SDI II with Quadro FX 4800 and 5800.
    * Improved power management support on some systems, such as Hewlett-Packard xw4600 workstations.
    * Fixed an X server crash when an X client attempts to draw trapezoids and RenderAccel is disabled.


---

### Post by Kosimo on 2009-03-21
anyone is trying this last version?

---

### Post by verlyn13 on 2009-03-21
This thread is huge! I'm a linux newb so I apologize in advance for my ignorance, but I haven't been able to find a real solution to this problem.

I am running 8.10 and have a 9800GTX card in my system and I have wasted too much of my life getting the latest drivers (180.xx) to install properly.

Each time a new version (180.xx) comes out I end up having to reinstall my entire system to get it to work.  Can someone point me to a systematic way to install the latest drivers in 8.10 without getting some type of conflict with an older version? (since the installation program clearly doesn't do it properly)
 
- Yes, I've read the instructions and I don't get any error messages during the installation.
- I run "uninstall" on the previous drivers before installing the new ones.
- Typically what happens after I install the new drivers and restart X, I try to get back into gnome and it goes into an infinite cycle of script each titled with [zen], very annoying.

thanks in advance

---

### Post by BGFG on 2009-03-21
Just installed the Jaunty dailybuild of yesterday. On activation of the restricted drivers I was suprised to see 180.37 installed. And here I was afraid to try the .35 driver i have sitting on my desktop.

---

### Post by mermshaus on 2009-03-25
Edit: Seems to work fine in Jaunty (Flash videos and 3D games). Finally.

Hi.

Has somebody been able to get the card below to work with a driver version newer than the one in the Intrepid repositories (> 180.11)?

```
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8100 / nForce 720a (rev a2)
```

I don't feel brave enough to [install the driver packages by hand](http://ubuntuforums.org/showpost.php?p=6789121&postcount=7). But I'd like to know whether it's worth waiting for the update in Jaunty. Otherwise, the only real option would be to [buy a separate PCI card](http://ubuntuforums.org/showpost.php?p=6575252&postcount=6) because of the 8100's abysmal performance.

BTW: Is it possible (and a good idea) to install nothing but the updated driver package (180.37, I guess) from the Jaunty repositories to my Intrepid system?

Thanks, Marc

---

### Post by BigSilly on 2009-03-27
> **pelle.k said:**
> 185.13 working just fine, including suspend and whatnot. Nvidia 8600M GS on a LG R500 (Notebook) running intrepid.
I installed from thefirstM's PPA (intrepid and jaunty), [http://ubuntuforums.org/showpost.php?p=6894986&postcount=4](http://ubuntuforums.org/showpost.php?p=6894986&postcount=4)
Thankyou, thefirstM. Thankyou AaronP_ and co.

Just wanted to add my thanks to TheFirstM too. Whoever you are and wherever you are, you have totally saved my life today with your PPA! I tried to install the driver manually, and while it all seemed to go well and I followed the instructions fine, on the reboot it just didn't seem to work. I could only get low graphics mode, and whatever commands I tried to to fix just wouldn't change. I just kept getting into a spiral of resetting the xorg.conf, then trying again, it not working, then returning to the first step ad infinitum.

By a stroke of luck I found this post on this thread, and am now running beautifully with the very latest 185 driver! Absolutely thrilled. Thanks again to you FirstM!

:guitar:

---

### Post by TheAL76 on 2009-03-27
I installed 185.13 about 1-2 weeks ago, but yesterday I had an issue with compiz not working. I ended up re-installing 185.13, but it gave an error message about some file not being a symbolic link.

I ran the 180.41 installer and it worked fine, compiz is working again.

Any ideas on if my compiz issue was related to using 185.13? I know it is a beta, and lot less documented than the 180 series, but I was just curious if anyone else has seen issues with compiz.

---

### Post by Kosimo on 2009-03-29
I've just added the links for download all nVidia legacy drivers in the first post.

---

### Post by danieljuh on 2009-03-30
Problem: Good lord! No CUDA and VDPAU in Jaunty! :(

No 180.41 since the package from [http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/) doesn't work with jaunty. Conflicts and wants to eat xorg.

Solved by: 
- Uninstalling all nvidia packages i could find through synaptic. 
- The instructions at first post in this thread (thx mate), (downloaded 64bit 180.41 through link at: [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) ).
- Boinc versions from [http://getdeb.net/](http://getdeb.net/) (64bit intrepid).(Look here otherwise:[http://www.gpugrid.net/forum_thread.php?id=592](http://www.gpugrid.net/forum_thread.php?id=592))
- Install mplayer libx264 nvidia-180-libvdpau (180.41) from the avenard rep above.

After reboot boinc/GPUGRID complains that is misses one cuda/co-processor.
a "sudo /etc/init.d/boinc-client restart" 

Then boinc finds the cuda/co-processor and plays nice work horse for Gpugrid and all is well again, rainbows, pony's,joy, dancing,kittens and smiles all around. :D

---

### Post by Kosimo on 2009-03-30
Guys, a new official release is here!
180.44

 >  	Linux Display Driver - x86

Version: 180.44
Operating System: Linux x86
Release Date: March 30, 2009

Release Highlights

    * Added support for the following GPUs:
          o Quadro FX 3800
          o Quadro FX 3700M
          o Quadro FX 1800
          o Quadro FX 580
          o Quadro FX 380
          o Quadro NVS 295
          o GeForce GT 120
          o GeForce G100
    * Fixed a problem that could cause Xid errors and display corruption in certain cases when OpenGL is used to render to redirected windows, for example when Java2D is used with the -Dsun.java2d.opengl=true option.
    * Updated glGetStringi(GL_EXTENSIONS, i) to no longer return NULL in OpenGL 3.0 preview contexts.
    * Fixed OpenGL crashes while running KDE4's Plasma.
    * Fixed OpenGL crashes when using a large number of texture objects.
    * Fixed the timestamp reporting in the GL_NV_present_video extension on SDI II with Quadro FX 4800 and 5800.
    * Improved power management support on some systems, such as Hewlett-Packard xw4600 workstations.
    * Fixed a problem that caused the screen to flicker momentarily when OpenGL applications exit unexpectedly on GeForce 6 and 7 series GPUs.
    * Fixed an X server crash when an X client attempts to draw trapezoids and RenderAccel is disabled.
    * Improved recovery from certain types of errors.
    * Fixed a bug that caused Autodesk Maya to freeze when overlays are enabled.
    * Fixed an interaction problem between OpenGL and memory tracking libraries such as MicroQuill SmartHeap.
    * Added support for RG renderbuffers in OpenGL 3.0.
    * Added support for OpenGL 3.0 floating-point depth buffers.
    * Fixed a problem that caused Valgrind to crash when tracing a program that uses OpenGL.
    * Updated VDPAU to support VC-1/WMV acceleration on all GPUs supported by VDPAU; see the README for details.
    * Fixed VDPAU corruption on some H.264 clips.
    * Updated VDPAU documentation in the README and in vdpau.h, in particular regarding how to use the deinterlacing algorithms in the VdpVideoMixer object. Explicitly documented "half rate" deinterlacing, which should allow the advanced algorithms to run on more low-end systems.
    * Implemented a "skip chroma deinterlace" option in VDPAU, which should allow the advanced deinterlacing algorithms to run on more low-end systems. See vdpau.h.
    * Fixed VDPAU VC-1 decoding on 64-bit platforms.
    * Updated the VDPAU wrapper library to print dlerror() messages when driver loading problems occur.
    * Improved VDPAU's handling of some corrupt H.264 streams, and some corrupt/invalid MPEG streams on some GPUs.
    * Fixed VDPAU to correctly handle WMV "range reduction" on some GPUs. A minor backwards-compatible API change was made for this; see vdpau.h's documentation for structure field VdpPictureInfoVC1.rangered.
    * Fixed a problem that caused surfaces to be marked as visible too early when the blit presentation queue is in use.
    * Fixed VDPAU to prevent some cases of "display preemption" in the face of missing H.264 reference frames on some GPUs.


---

### Post by crjackson on 2009-03-30
Great. I'll be playing with this in a day or two. Thanks for your work on the 1st post. It should be a sticky. I have machines with video cards from all generations and it's a good reference for the various nVidia drivers.

---

### Post by klopus on 2009-03-30
Sorry guys for probably asking same thing but I tried to wade thru this huge thread but probably missed some messages.Also I'm pretty familiar as a developer with RedHat server but quite new to desktop and Ubuntu so please bear with me.

I'm installing Kubuntu 8.10 using wubi on my HP 8100m Vista desktop. It has an onboard Nvidia 5100se or something to this effect. My monitor is 22" wide screen Samsung LCD. 

Install finishes fine. On booting Kubuntu it initially goes fine showing low res Kubuntu boot screen and mouse pointer but when I guess it tries to start gdm screen first turns into what seems to be a fancy grayish textured background but then immediately starts to fade away in blotches until screen goes blank. Pressing Ctrl-Backspace apparently restarts X but leads to same results.

So I restarted in recovery mode and got to busybox prompt. Installed via apt-get nvidia-glx-180.1 (as I can recall) drivers. Rebooted. Same thing. So are you saying that using latest Nvidia drivers (185.x?) solves the problem? Should I use deb package or tarball? What's the best source?

Thanks!

---

### Post by PC_load_letter on 2009-03-31
**Reporting failure!** On Hardy 64bit with the 180.44 driver. Here is what happened if anyone is interested.

- I downloaded the driver from Nvidia for my 8400GS mobile (file name: NVIDIA-Linux-x86_64-180.44-pkg2.run) 
- Followed the instructions on the 1st post to the semicolon.
- As the script was running, it said that "there is no available module for my current kernel" (2.6.24-23), "would you like to search the NVIDIA ftp server?" which I answered yes.
- Came back with "Nothing available for your kernel on the ftp server, will have to compile the kernel module", which went successfully. 
- Then later "Would you like to install 32-bit openGL libs?" to which I said yes.
- "Checking for any conflicts w/ existing openGL libs."
- "Configure X automatically? Old file will be backed up", said yes.
- Restarted, but X failed, and the error message was something like "fatal error".

So, I uninstalled the 180.44 driver as mentioned in 1st post, then had to reboot into recovery mode, use xfix, and now I'm back to square one.

Any ideas why things went wrong?

Thanks.

---

### Post by crjackson on 2009-03-31
Just ran the guide on page one and glad to say all is well. This time it didn't pick-up the highest refresh rate (it normally does) and a simple change of the refresh with the settings applet fixed this.

I wish they would include a "nologo" option in the nvidia-settings applet. I wouldn't have to edit xorg.conf at all then.

**[SIZE="4"]Is there any way to make this driver show active in the hardware drivers applet?[/SIZE]**

I just updated a second system with the 180.44 driver and it's working well so far. With the second system I didn't have to add the "nologo" option like the first.  Odd!

---

### Post by Hells_Dark on 2009-03-31
All works great here with the last 180.44 (Intrepid).

---

### Post by RaZoR1394 on 2009-03-31
180.44 works ok for me. I'm using a 720P x264 file with XBMC and CPU stays low on my old processor. I get a lot of tearing however.

I'm going to try 185.13 from thefirstm ppa.

---

### Post by hotweiss on 2009-03-31
> **PC_load_letter said:**
> **Reporting failure!** On Hardy 64bit with the 180.44 driver. Here is what happened if anyone is interested.

- I downloaded the driver from Nvidia for my 8400GS mobile (file name: NVIDIA-Linux-x86_64-180.44-pkg2.run) 
- Followed the instructions on the 1st post to the semicolon.
- As the script was running, it said that "there is no available module for my current kernel" (2.6.24-23), "would you like to search the NVIDIA ftp server?" which I answered yes.
- Came back with "Nothing available for your kernel on the ftp server, will have to compile the kernel module", which went successfully. 
- Then later "Would you like to install 32-bit openGL libs?" to which I said yes.
- "Checking for any conflicts w/ existing openGL libs."
- "Configure X automatically? Old file will be backed up", said yes.
- Restarted, but X failed, and the error message was something like "fatal error".

So, I uninstalled the 180.44 driver as mentioned in 1st post, then had to reboot into recovery mode, use xfix, and now I'm back to square one.

Any ideas why things went wrong?

Thanks.

1. > sudo apt-get remove Nvidia*

2. install the driver again

---

### Post by |Porsche on 2009-03-31
Wow, everything looks sharper.

---

### Post by crjackson on 2009-04-01
If anyone knows how to make this driver work with "Hardware Drivers" applet, let me know please.

---

### Post by crjackson on 2009-04-01
Wow, I'm getting really strange behaviour with the 180.44 drivers on 2 different systems. This one tends to go all pink, and the other one tends to go all white.

I'll be backing out on these drivers.

---

### Post by Swagman on 2009-04-01
Driver 180 came in with the last but one update automatically. I can't tell any difference though... 

Sound still glitches when scrolling on the net

Google earth still bombs on initialisation

etc

8:10 with 2 gb Ram and a 512mb GT8800 here.

---

### Post by Swagman on 2009-04-01
Oh...

And a Cerise screen .. which is starting to pee me off now.

---

### Post by crjackson on 2009-04-01
> **Swagman said:**
> Oh...

And a Cerise screen .. which is starting to pee me off now.

Now this is getting really strange.  I wiped out my Ubuntu drive and restored from a backup that's running the 180.29 driver.  I'm still getting the Cerise screen on Ubuntu Forums. If I keep hitting refresh a few times it will return to normal.

Could this be an issue with the Forums and not the driver at all.  Poor little driver, I may have executed it without warrant. There's just no justice in this world. Not even for a video card driver. ;)

**Me thinks an April Fool's Day Joke is afoot...**

---

### Post by Kosimo on 2009-04-01
> **crjackson said:**
> Now this is getting really strange.  I wiped out my Ubuntu drive and restored from a backup that's running the 180.29 driver.  I'm still getting the Cerise screen on Ubuntu Forums. If I keep hitting refresh a few times it will return to normal.

Could this be an issue with the Forums and not the driver at all.  Poor little driver, I may have executed it without warrant. There's just no justice in this world. Not even for a video card driver. ;)

**Me thinks an April Fool's Day Joke is afoot...**

ahahah

Guys...
is 1St of April!!!!!!!!

---

### Post by crjackson on 2009-04-01
> **Kosimo said:**
> ahahah

Guys...
is 1St of April!!!!!!!!

Yeah, not a cool trick for this old man. I reinstalled my whole system because of this trick.... #-o

---

### Post by Kosimo on 2009-04-01
> **crjackson said:**
> Yeah, not a cool trick for this old man. I reinstalled my whole system because of this trick.... #-o

Sorry dude, but you deserve this big loooooooooooooooooooooool :KS

---

### Post by crjackson on 2009-04-01
> **Kosimo said:**
> Sorry dude, but you deserve this big loooooooooooooooooooooool :KS

Really not that big of a big deal. I use Acronis True Image and it only took about 8 minutes to restore my latest backup.

---

### Post by JPorter on 2009-04-01
> **danieljuh said:**
> Problem: Good lord! No CUDA and VDPAU in Jaunty! :(
Just to be clear... VDPAU is in the Jaunty repos, it's listed as[FONT="Courier New"] nvidia-180-libvdpau[/FONT].

---

### Post by JPorter on 2009-04-01
> **crjackson said:**
> If anyone knows how to make this driver work with "Hardware Drivers" applet, let me know please.

I assume you mean the 180 driver in general?

Make sure that[FONT="Courier New"] nvidia-180-modaliases [/FONT]is installed, and the 180 driver should show up in the Hardware Drivers panel.  Currently it installs 180.37, and note that VDPAU support is available in a separate package which is installable through Synaptic.

---

### Post by crjackson on 2009-04-01
> **JPorter said:**
> I assume you mean the 180 driver in general?

Make sure that[FONT="Courier New"] nvidia-180-modaliases [/FONT]is installed, and the 180 driver should show up in the Hardware Drivers panel.  Currently it installs 180.37, and note that VDPAU support is available in a separate package which is installable through Synaptic.

I'm talking about the 180.44 specifically.

modealiases is installed but it's only showing the older versions of the driver. Keep in mind this is an intrepid install I'm refering to. I already did away with the *.44 driver due to problems in caused on the jaunty machine.

With the driver installed, nothing shows active in the "Hardware Drivers" applet.

---

### Post by aptperson on 2009-04-02
Is there any other way to enter a "real" terminal apart from the control + alt + F1 command, which does not seem to work on my computer?

Thanks

---

### Post by bvanaerde on 2009-04-02
> **aptperson said:**
> Is there any other way to enter a "real" terminal apart from the control + alt + F1 command, which does not seem to work on my computer?

In the menu:
Applications > Accessories > Terminal
But you won't be able to install the nVidia drivers this way...

So what you can do, is reboot, and take the "recovery mode" at the grub menu. This way, you can get into the terminal without starting your x-server.

---

### Post by Trail on 2009-04-02
So, I was kinda bored one day, and decided to upgrade to the latest openSUSE factory. Then I also upgraded the nvidia drivers. Then after a while I played a 1080p video. Then I noticed my laptop's fan was surprisingly silent. Then I checked the CPU usage.

VDPAU is very nice. Having it work unexpectedly is also very nice. I was following the progress for quite a while, but I couldn't be assed to compile mplayer from svn. Lazy approach ftw?

---

### Post by aptperson on 2009-04-02
> **bvanaerde said:**
> 
So what you can do, is reboot, and take the "recovery mode" at the grub menu. This way, you can get into the terminal without starting your x-server.

Thanks, worked perfectly.

---

### Post by Daremo_06 on 2009-04-02
I just got my new 9400GT in the other day and started with a fresh install of 8.10 64bit on my machine last night.  Loaded everything from Nvidia, then when I went to enable the Nvidia driver in the hardware drivers section, it screwed everything up.  

My configuration is a pair of LCD monitors that I want to dual display on and the aformentioned 9400GT.  This is a brand new install, so I don't mind having to redo things till I get it right.  What is the correct way to fully install drivers for this card so that I can run things like Compiz and make my desktop into a cube and spin it around and other silly things ;).

There are so many threads and links out there, if someone has a known and accurate thread/link and _current_ to a guide for installing the 180.44 driver (thats the newest on NVIDIA's page), that would be really awesome.  

Thanks!

---

### Post by crjackson on 2009-04-02
> **Daremo_06 said:**
> I just got my new 9400GT in the other day and started with a fresh install of 8.10 64bit on my machine last night.  Loaded everything from Nvidia, then when I went to enable the Nvidia driver in the hardware drivers section, it screwed everything up.  

My configuration is a pair of LCD monitors that I want to dual display on and the aformentioned 9400GT.  This is a brand new install, so I don't mind having to redo things till I get it right.  What is the correct way to fully install drivers for this card so that I can run things like Compiz and make my desktop into a cube and spin it around and other silly things ;).

There are so many threads and links out there, if someone has a known and accurate thread/link and _current_ to a guide for installing the 180.44 driver (thats the newest on NVIDIA's page), that would be really awesome.  

Thanks!

Follow the instructions on the 1st post of this thread. Read the whole thing and do exactly as it says. That should do the trick.

---

### Post by wingnux on 2009-04-02
Can anyone please help me with an issue I'm having after manualy installing those drivers? 
I was using the ones from the hardware manager just fine but then I uninstalled them, rebooted and installed the beta one just fine, everything worked great but whenever I tried to launch any fullscreen game that used a resolution different from the one I was using on my desktop (1152x864@62) the X server would restart and go back to the login screen. For instance, when I tried to run zsnes wich was set to 1024x768, the X server restarted so I had to manualy edit the zsnes config in order to make it launch fullscreen @ 1152x864.
I've tried the official driver (not the beta one) and had the same problem, I've also tried replacing the xorg.conf with the one I was previously using with the repo drivers and nothing helped =/

Any ideas? I really do want to use those drivers because I got a very nice speed boost (about 12fps) on my games.

---

### Post by FraggedLocust on 2009-04-03
bah. the new 180 drivers won't let me do compiz. It seems every time I try to update the 180 drivers I break X configuration somehow, so I have to remove and fall back to the default 180. and even that won't let compiz work. the 177 was better, but I don't see it on hardware Devices now for some reason.

---

### Post by Kosimo on 2009-04-03
> **FraggedLocust said:**
> bah. the new 180 drivers won't let me do compiz. It seems every time I try to update the 180 drivers I break X configuration somehow, so I have to remove and fall back to the default 180. and even that won't let compiz work. the 177 was better, but I don't see it on hardware Devices now for some reason.

What videocard are you currently using when trying to install this drivers? How do you install them?

---

### Post by FraggedLocust on 2009-04-03
nvidia GeForce 7200. i download the drivers in .run format and install from terminal using 

.... gdm stop

sudo sh NVIDIA-....

.... gdm start

it installs fine, but when i restart X it says the configuration is broken. i got the driver again. I think I'll try one last time soon.

---

### Post by Kosimo on 2009-04-04
> **FraggedLocust said:**
> nvidia GeForce 7200. i download the drivers in .run format and install from terminal using 

.... gdm stop

sudo sh NVIDIA-....

.... gdm start

it installs fine, but when i restart X it says the configuration is broken. i got the driver again. I think I'll try one last time soon.

Remember to uninstall any previous version and disable the hardware propietary drivers tool if you'reusing it

---

### Post by ticket on 2009-04-05
180.44 doesn't wanna play on my rig.

Running 2.6.27-11-generic (8.1 Intrepid) with a PCI 6200 card.

I had the 177 driver worked fine. I installed directly using the nvidia installer, using nvidia's advice about cleaning the system first.
Compiz worked, but the performance was poor, so I want to upgrade to the 180 drivers.

So I removed the 177 (sudo sh NVIDIA-.. -- uninstall) and then installed the 180 by the usual

.... gdm stop

sudo sh NVIDIA-....

.... gdm start

The driver builds and installs fine. But after a reboot:


[COLOR="Blue"](**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.[/COLOR]

So I end up in low resolution mode.

A similar situation encountered by others.

I tried both deleting my xorg.conf and let the installer rebuild it - no luck.

sudo dpkg-reconfigure -phigh xserver-xorg just produces a bare bones xorg.conf - again, no luck.


The packages I have installed are:
nvidia-settings           177.78-0ubuntu2.1
nvidia-177-kernel-source  177.78-0ubuntu0.1
nvidia-kernel-common
nvidia-common
nvidia-***-modaliases  (for 177, 180, etc)
xserver-xorg-video-nv

I do not have nvidia-glx-180 installed as I believe(?) these glx's conflict with the nvidia installer. For example, I didn't have nvidia-glx-177 installed when I used the 177 driver, and the 177 driver installed and worked fine.

Should I try removing nvidia-177-kernel-source?
I don't see why - the 180 driver builds fine anyway. similarly, should I install nvidia-180-kernel-source? 

Finally, I tried inserting a 
   BusID "PCI:2:7:0" 
into the xorg.conf (as suggested by some threads) - again, no luck.

It looks to me like the xorg.conf might have been broken for 180, as the error is a failure to initialise the nvidi.ko module rather than in creating it.


I don't want to revert to loading the Ubuntu 180 package - that is not so flexible - and should not be necessary anyway.

HELP!!

---

### Post by Kosimo on 2009-04-07
Guys, 185.19 BETA has been released today.

Here the change log: 

>     *  Added support for the following new GPUs:
          o Quadro FX 3800
          o Quadro FX 1800
          o Quadro FX 380
          o Quadro FX 580
          o GeForce GTS 250
          o GeForce GT 140
          o GeForce GT 130
          o GeForce 9600 GSO 512
    * Fixed SDI presentation time queries returning unexpected values.
    * Removed the 'AllowDFPStereo' X config file option, which is now enabled by default.
    * Fixed a bug that caused certain programs to hang when multiple threads call functions in libdl at the same time.
    * Fixed a driver crash when OpenGL applications use an extremely large number of textures.
    * Text rendering to PseudoColor windows with the glyph cache enabled no longer causes GPU errors.
    * The X driver now allows pixmaps smaller than 32x32 pixels to be placed in video memory.
    * Fix a problem that prevented the driver from retraining a DisplayPort link after a device is hotplugged.
    * nvidia-bug-report.sh now automatically gzips the resulting log file.
    * Fix VDPAU to eliminate some cases of GPU hangs when decoding H.264 video on G84, G86, G92, G94, G96, or GT200 GPUs, and supplying a DPB missing some reference frames.
    * The VDPAU presentation queue now syncs to VBLANK in the blit path. The environment variable VDPAU_NVIDIA_SYNC_DISPLAY_DEVICE selects which display to sync to when TwinView is enabled; see the README for details.
    * On systems using integrated graphics, VDPAU now uses system RAM instead of video RAM for many purposes. This should prevent "out of resources" problems in most cases, even when the video RAM carve-out is configured as low as 128M.
    * Added support for Quad-Buffered Stereo in the main plane simultaneously with the Color Index Overlay; i.e., both Stereo GLX FBConfigs and Color Index Overlay FBConfigs can be advertised and used at the same time, though no single GLX FBConfig contains both Stereo and Overlay capabilities.


---

### Post by MartinEve on 2009-04-08
I know this comment doesn't add much, but: performance on 180 is amazing compared to the 177 I was running previously!

---

### Post by Kosimo on 2009-04-08
> **MartinEve said:**
> I know this comment doesn't add much, but: performance on 180 is amazing compared to the 177 I was running previously!

This is what all this 3rd is a talking about :D  

Now is time to check if 185.xx are another step forward

---

### Post by kamitsukai on 2009-04-08
Can I install this on 8.10 64bit?

---

### Post by Kosimo on 2009-04-08
> **kamitsukai said:**
> Can I install this on 8.10 64bit?

Sure you can. Just make sure you get the 64 bit version. 
Same steps are valid for 32 and 64 bits on the first post.

---

### Post by thehipho on 2009-04-08
OK, nice looks like coolbits! is in 185.19!, I noticed Clock-Freq. are available and need enabled and set (at your own risk!!). 
Great performance improvement tweaks, thanks to the how-to in this post!

---

### Post by ticket on 2009-04-10
> **ticket said:**
> 180.44 doesn't wanna play on my rig.

Running 2.6.27-11-generic (8.1 Intrepid) with a PCI 6200 card.

I had the 177 driver worked fine. I installed directly using the nvidia installer, using nvidia's advice about cleaning the system first.
Compiz worked, but the performance was poor, so I want to upgrade to the 180 drivers.

So I removed the 177 (sudo sh NVIDIA-.. -- uninstall) and then installed the 180 by the usual

.... gdm stop

sudo sh NVIDIA-....

.... gdm start

The driver builds and installs fine. But after a reboot:


[COLOR="Blue"](**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.[/COLOR]

So I end up in low resolution mode.

A similar situation encountered by others.

I tried both deleting my xorg.conf and let the installer rebuild it - no luck.

sudo dpkg-reconfigure -phigh xserver-xorg just produces a bare bones xorg.conf - again, no luck.


The packages I have installed are:
nvidia-settings           177.78-0ubuntu2.1
nvidia-177-kernel-source  177.78-0ubuntu0.1
nvidia-kernel-common
nvidia-common
nvidia-***-modaliases  (for 177, 180, etc)
xserver-xorg-video-nv

I do not have nvidia-glx-180 installed as I believe(?) these glx's conflict with the nvidia installer. For example, I didn't have nvidia-glx-177 installed when I used the 177 driver, and the 177 driver installed and worked fine.

Should I try removing nvidia-177-kernel-source?
I don't see why - the 180 driver builds fine anyway. similarly, should I install nvidia-180-kernel-source? 

Finally, I tried inserting a 
   BusID "PCI:2:7:0" 
into the xorg.conf (as suggested by some threads) - again, no luck.

It looks to me like the xorg.conf might have been broken for 180, as the error is a failure to initialise the nvidi.ko module rather than in creating it.


I don't want to revert to loading the Ubuntu 180 package - that is not so flexible - and should not be necessary anyway.

HELP!!

I tried removing the nvidia-177-kernel-source package, so all I have installed now are:

nvidia-settings        177.78-0ubuntu2.1
nvidia-kernel-common
nvidia-common
nvidia-***-modaliases  (for 177, 180, etc)
xserver-xorg-video-nv

Again, the 180.44 driver builds ok, but fails to initialise on reboot (same error as before).  I tried again with the new 2.6.27-11-generic headers that appeared in recent updates - still fails.  

I also tried the build with the nvidia-xconfig package installed, and un-installed. The compilation phase muttered something about a different nvidia-xconfig signature, but still completed the driver build ok. Still get the driver initialisation failure.

I see no reason why the _install_ works for the 177 and 180 drivers, but the 180 driver fails to initialise on reboot (and thence low res graphics). Possibilities:

[LIST=1]
[*]The 180.44 driver doesn't like to coexist with compiz modules? (this was reported earlier as a possible source of conflict. If this is so, the 180.44 driver is useless for compiz users).

[*]Maybe the 6200 and the 180.44 driver conflict? (but documentation says 6200 is supported).

[*]Is there an issue in having an old nvidia-settings package. The latest one available appears to be for the 177 driver series. Does a 180 version exist?
[/LIST]

Really fed up with this. It should work but doesn't. How come others have succeeded on Intrepid 8.1?  What packages did they have installed?

---

### Post by inobe on 2009-04-10
> **ticket said:**
> I tried removing the nvidia-177-kernel-source package, so all I have installed now are:

nvidia-settings        177.78-0ubuntu2.1
nvidia-kernel-common
nvidia-common
nvidia-***-modaliases  (for 177, 180, etc)
xserver-xorg-video-nv



Really fed up with this. It should work but doesn't. How come others have succeeded on Intrepid 8.1?  What packages did they have installed?

[IMG]http://www.itsyourpc.org/duane/files/nvidia_180_44.jpg[/IMG]

i never removed anything, when i selected the packages the old packages were auto removed.

packages i have selected

nvidia-libvdpau
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180


once selected i restarted and the driver appeared in "hardware drivers" i then activated it.

---

### Post by inobe on 2009-04-10
if anyones having trouble with the 180.44's not being in package management you could add a source to synaptic [http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

the site responsible for the source [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

you will always get the very latest nvidia driver...

at least this way when you get a linux kernel image update you won't need to reinstall your nvidia driver manually !


edit: **warning** this only works on 9.04 if upgraded from 8.10, this repo is incompatible with a 9.04 fresh install !

it will remove your desktop for whatever reason.................

---

### Post by Kareeser on 2009-04-10
Nuh-uh, the driver works perfectly on my 9.04 64-bit system with Compiz, so that rules out #1.

---

### Post by Kosimo on 2009-04-10
> **Kareeser said:**
> Nuh-uh, the driver works perfectly on my 9.04 64-bit system with Compiz, so that rules out #1.

Here as well, Jaunty 64bit and 180.44  ( I am using 2.6.29 kernel by the way)

---

### Post by ticket on 2009-04-10
> **inobe said:**
> 

i never removed anything, when i selected the packages the old packages were auto removed.

packages i have selected

nvidia-libvdpau
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180


once selected i restarted and the driver appeared in "hardware drivers" i then activated it.

Hi inobe,

Looks like you are not using the nvidia-installer, just installing from the Ubuntu repositories.  But I see you got the 180.44 installed!! Does that mean the Ubuntu repositories now support the 180.44 driver? (it used to just support an earlier and more buggy version, 180.12 or something). 
I am avoiding going back to a repository-based install as my system is currently 'cleaned' for using the nvidia-installer, but I may have to reconsider that.  I note you are using 64 bit - I am still 32 bit - I wonder if that's an issue.

---

### Post by inobe on 2009-04-10
> **ticket said:**
> Hi inobe,

Looks like you are not using the nvidia-installer, just installing from the Ubuntu repositories.  But I see you got the 180.44 installed!! Does that mean the Ubuntu repositories now support the 180.44 driver? (it used to just support an earlier and more buggy version, 180.12 or something). 
I am avoiding going back to a repository-based install as my system is currently 'cleaned' for using the nvidia-installer, but I may have to reconsider that.  I note you are using 64 bit - I am still 32 bit - I wonder if that's an issue.


i did use the installer in the past.....

that repo i posted back there is what i am using now, if you want to use it be sure to add the stable source.

[http://ubuntuforums.org/showpost.php?p=7049521&postcount=678](http://ubuntuforums.org/showpost.php?p=7049521&postcount=678)

you will be able to install the 180.44 driver.

don't worry about 32 or 64bit drivers, synaptic will grab the correct driver version from the source.

also that is not an ubuntu supported repo, but if you want the latest driver without manual installation this is the way to go.

---

### Post by ticket on 2009-04-10
> **Kareeser said:**
> Nuh-uh, the driver works perfectly on my 9.04 64-bit system with Compiz, so that rules out #1.

> **Kosimo said:**
> Here as well, Jaunty 64bit and 180.44  ( I am using 2.6.29 kernel by the way)

Hmmm, you guys are using 64 bit as well ... could that be it?

Also, both of you are using a later kernel than me (9.04 and 2.6.29, versus my 8.1 / 2.6.27-11-generic, the current formal release).  I thought earlier in this thread I saw people have success with 8.1. Do I need to get the beta kernel to get this to work?

Also, did you both use the nvidia-installer method?

Thanks for your responses, looks like I am getting some more clues ...

I am trying to install NVIDIA-Linux-x86-180.44-pkg1.run

---

### Post by inobe on 2009-04-10
my kernel

```
-desktop:~$ uname -r
2.6.27-11-generic

```

edited: this is my ubuntu desktop with the 180.44

this is a 32bit os using the same procedure with that repo.

---

### Post by ticket on 2009-04-10
> **inobe said:**
> if anyones having trouble with the 180.44's not being in package management you could add a source to synaptic [http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

the site responsible for the source [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

you will always get the very latest nvidia driver...

at least this way when you get a linux kernel image update you won't need to reinstall your nvidia driver manually !

inobe, that looks promising!  
So the 180.44 release is therefore not an official package release yet.
I need a little helping hand though, in getting this unofficial package installed. 

The web site says:
[HTML]To use this repository, first add the signing key[/HTML]

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && **rm ubuntu-repos.key** 
```

but I am a little nervous about the "rm ubuntu-repos.key" bit.

Looking further, can I simply just download and extract this file:

     nvidia-graphics-drivers-180_180.44-0ubuntu1.tar.gz 

which I guess will produce a .deb package, and simply install that (by double clicking on it?)

---

### Post by inobe on 2009-04-10
> **ticket said:**
> 
but I am a little nervous about the "rm ubuntu-repos.key" bit.

Looking further, can I simply just download and extract this file:

     nvidia-graphics-drivers-180_180.44-0ubuntu1.tar.gz 

which I guess will produce a .deb package, and simply install that (by double clicking on it?)

i added the key and didn't suffer for it.


i suppose you can dl the .debs, i never tried that but **i think** it will cause some problems.

---

### Post by inobe on 2009-04-10
the site is pretty reputable, i seriously doubt there would be a breach of any kind with the instructions.

the site googled

[http://www.google.com/search?q=http%3A%2F%2Fwww.avenard.org%2Ffiles%2Fubuntu-repos%2F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=http%3A%2F%2Fwww.avenard.org%2Ffiles%2Fubuntu-repos%2F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

edit: ubuntu doesn't support any proprietary driver "including" nvidia

---

### Post by ticket on 2009-04-11
Hi inobe,

Well I successfully installed 180.44 following the instructions at 
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)
as you recommended. Thanks!

This does however compound the mystery as to why the nvidia installer that produced the nvidia.ko fails to run.  

When I installed 180.44 via the 'avenard' method, I didn't even have to change xorg.conf.  So that wasn't the problem, and neither was using 32 bit or having a GeForce 6200 PCI card.

Looking at the log for the successfully installed 180.44 driver:

```
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
**(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:2:7:0 (GPU-0)**
```

The nvidia-installer method would fail at the bold line - maybe it needed to be told the PCI address in xorg.conf  (I did try that once, but it still failed - maybe I got the syntax wrong).  That's the only thing I can think of that could have stopped the nvidia-installer method working. 

Anyway, now I have 180.44 installed. Was it worth it?  Not really. Before 180.44 I was using the 177.80 driver, which had the following issues:

177.80 issues:
_Flash in Firefox_
Using Metacity:  
     ok in normal window, stuttering when maximised. 
     HD is a slideshow in a normal window (& unusable in maximised window)
    
Using Compiz:
     ok in a normal window, badly stuttering when maximised. But using
     zoom on a normal window (to fill the screen) gives a smooth,
     watchable result.
     HD is unwatchable no matter what you do.

_DVD playing - totem / GStreamer_
Using Metacity:
     Frequent but small stuttering - kinda grates on the viewing
     experience

Using Compiz:
     Frequent, more noticeable stuttering 

_DVD playing - Vlc_
Using Metacity:
     Occasional bad stutter, smooth in-between them.

Using Compiz:
     More frequent bad stutters, smooth in-between them.

The above is using the 2D performance settings:

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```
and having 
```
    Option "PixmapCacheSize" "1000000"
    Option "AllowSHMPixmaps" "0"
```
in the xorg.conf.

And the difference when switching to 180.44?  Sorry, but no significant difference as far as I can tell.  Exactly the same 2D performance problems as before. To watch DVDs I have to switch compiz off. To watch flash video in full screen I have to switch compiz on and use the compiz zoom feature.

Perhaps I am expecting too much from my NV44 6200?  Pity, because this card is really the last option for PCs with only PCI slots. The card is still on sale, filling the need for older PCs.  Mine is a 1.5Ghz P4 with 512Mb RAM (a machine of that spec will play DVDs perfectly under Windows...)

For me, 180.44 doesn't rock. Neither did 177.80.

The only benefit I get from the 180.44 is the window title bar corruption, seen when using compiz, seems to have gone.

Overall, rather disappointing.  Is 9.04 going to help?

Anyway, thanks to inobe for pointing me to the avenard site.

---

### Post by ticket on 2009-04-11
> **ticket said:**
> 
Overall, rather disappointing.  Is 9.04 going to help?

Maybe not:

[http://forums.adobe.com/thread/199736;jsessionid=2500E8126BDA8ACF3CCD9CBA7E784370.node0?tstart=0](http://forums.adobe.com/thread/199736;jsessionid=2500E8126BDA8ACF3CCD9CBA7E784370.node0?tstart=0)

---

### Post by inobe on 2009-04-11
it's much easier installing from package management......


i have a slow machine next to me that runs xubuntu, it's light weight with an Xfce desktop, the computer does a lot better with Xfce, gnome and kde would drag that machine in the ground.

[http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)

there are other light weight alternatives.

---

### Post by robgue on 2009-04-12
Inobe thanks for pointing us to that repo. I've got the new driver installed easily now. The other method I got    errors on reboot.
I enabled the testing and bleeding repo but I can't find the beta 185 driver? How can I install that using the repo? Thanks for your help.

---

### Post by zhangmaster12 on 2009-04-13
when i type sudo /ect/init.d/gdm stop

all i get is an invalid command. Im on 8.10 HALP!

---

### Post by ticket on 2009-04-13
> **zhangmaster12 said:**
> when i type sudo /ect/init.d/gdm stop

all i get is an invalid command. Im on 8.10 HALP!

Did you mean to type

  sudo /_etc_/init.d/gdm stop

---

### Post by crjackson on 2009-04-16
Anybody tried the [180.50's]("ftp://download.nvidia.com/XFree86/Linux-x86/180.50/") yet. I'm at work so I can't do it right now.

---

### Post by Kosimo on 2009-04-16
> **crjackson said:**
> Anybody tried the [180.50's]("ftp://download.nvidia.com/XFree86/Linux-x86/180.50/") yet. I'm at work so I can't do it right now.

Thanks for the heads up!

I'm going to update the firs post right now and then try this version :KS

---

### Post by Kosimo on 2009-04-16
Changelog in 180.50

>     *  Added support for the following GPUs:
          o GeForce 9600 GSO 512
          o GeForce 9400 GT
          o GeForce GTS 250
          o GeForce GT 130
          o GeForce GT 140
    * Updated nvidia-bug-report.sh to compress its log file; running `nvidia-bug-report.sh` now produces "nvidia-bug-report.log.gz".
    * Addressed a problem that could lead to intermittent hangs and system crashes on some GeForce 9 and later GPUs.
    * Fixed an X server crash when viewing the website [www.tim.it](www.tim.it).
    * Fixed a DisplayPort interaction problem with power management suspend/resume events.
    * Fixed rendering corruption in the OpenGL 16-bit RGB Workstation Overlay.
    * Fixed a recent VDPAU regression that caused aborted playback and hangs when decoding some H.264 clips on G84, G86, G92, G94, G96, and GT200 GPUs.
    * Fixed occasional X driver memory management performance problems when a composite manager is running.
    * Improved compatibility with recent Linux kernels.
    * Reduced CPU usage of nvidia-smi utility for reporting Quadro Plex information.
    * Fixed compatibility problem with LandMark GeoProbe.


---

### Post by OutOfReach on 2009-04-16
> **Kosimo said:**
> Changelog in 180.50
[QUOTE=Changelog]
* Fixed an X server crash when viewing the website [www.tim.it](www.tim.it).
[/QUOTE]

O_O I wasn't actually expecting that website to crash X, but out of curiousity I visited it and of course...X crashed

BTW thanks for the 180.50 heads up

---

### Post by inobe on 2009-04-16
> **robgue said:**
> 
I enabled the testing and bleeding repo but I can't find the beta 185 driver? How can I install that using the repo? Thanks for your help.

i was wrong robgue, you can remove the bleeding repo.


the the post with the bad information will get edited.

---

### Post by Kosimo on 2009-04-16
> **OutOfReach said:**
> O_O I wasn't actually expecting that website to crash X, but out of curiousity I visited it and of course...X crashed

BTW thanks for the 180.50 heads up

I've tried with 180.44 and didn't crash for me.
Now I am with 180.50 and so far so good ;)

---

### Post by AaronP_ on 2009-04-16
> **Kosimo said:**
> Thanks for the heads up!

I'm going to update the firs post right now and then try this version :KS
Don't try it on a GeForce 6 or 7-series GPU.  It's got a pretty nasty regression that causes Xid errors and corrupts the screen.  A fixed driver should be out soon.

---

### Post by Kosimo on 2009-04-16
> **AaronP_ said:**
> Don't try it on a GeForce 6 or 7-series GPU.  It's got a pretty nasty regression that causes Xid errors and corrupts the screen.  A fixed driver should be out soon.

What's your current configuration?

---

### Post by SnowRider on 2009-04-16
I have an acer 5520 GeForce 7000M/nForce610M. Dual booting JJ 9.04 & II 8.10. Both OS's running NVIDIA 185.19 BETA drivers since their release. Was running 185.13 before that.Have had no problems yet. They work great for me.(64 bit)

---

### Post by AaronP_ on 2009-04-17
> **AaronP_ said:**
> Don't try it on a GeForce 6 or 7-series GPU.  It's got a pretty nasty regression that causes Xid errors and corrupts the screen.  A fixed driver should be out soon.
Fixed in 180.51.

---

### Post by Mazza558 on 2009-04-17
I'm not quite sure I believe my eyes. 

But, I have got Guild Wars running in WINE, on Dirext 9.0c (YES, 9.0c, not 8.1), running flawlessly with a drop in fps of only 5-10 over Windows. I get around 40 fps on Ubuntu and 50 on Windows.

Not bowled over? This is an INCREDIBLE moment for Ubuntu's credibility as a gaming platform. NVIDIA really have gone all out (as have WINE) to make Windows games runnable. 

Amazing stuff!

---

### Post by Kosimo on 2009-04-18
Differences between 180.50 and 180.51

> 180.51 additions:

    * Fixed an interaction problem that could corrupt the EDID of the Fujitsu Technology Solutions Celsius H270 notebook's internal flatpanel.
    * Fixed a bug that could interfere with the detection of display devices attached to secondary GPUs when first starting X after cold boots.
    * Fixed a problem that could result in temporary stalls when moving OpenGL application windows on GeForce 8 and later GPUs.
    * Fixed a bug that prevented VGA fonts from being saved/restored correctly on GeForce 8 and later GPUs.


---

### Post by crjackson on 2009-04-18
> **Kosimo said:**
> Differences between 180.50 and 180.51

kosimo - From your experience is it good enough to replace the 180.44 driver on a production machine?

---

### Post by Kosimo on 2009-04-19
> **crjackson said:**
> kosimo - From your experience is it good enough to replace the 180.44 driver on a production machine?

For me, PRE releases has been always very stable and rock solid. In fact I am now using 180.51 driver without any issue at all. Sometimes I had some performance regressions in BETA driver but lately looks like even BETA are stable enough. But definitely PRE releases are in my opinion as good and stable than STABLE releases.

---

### Post by crjackson on 2009-04-19
cool, I'll be moving some machines to that driver today. I'll back-up and try that script we talked about. Have you messed with it yet?

---

### Post by The Bright Side on 2009-04-19
Just wanted to say that this thread and the instructions on the first page are AWESOME. Many thanks to Kosimo for maintaining and updating this, YOU DA MAN.

---

### Post by donaldt on 2009-04-19
Greetings,

I have a problem with Nvidia in Ubuntu 8.10.  The Nvidia X server is apparently installed but does not function normally.  Driver is 180.44-pkg1.

When I try to use the X server to add my second monitor, it accepts the inputs but never  activates the second screen, an LG 19” monitor.  Here is what I get when I try to configure “separate x-screen”

After activating the second monitor and placing it in the correct location, I click apply and get the following:  Cannot Apply (plus five reasons why, such as you changed xinerama etc.)  When I click apply what is possible, nothing happens.

When I try to save to x configuration file, here is the message that appears;
“Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.”  When I try to manually delete the file, it says I am denied that privilege.

When I shut down and re-boot all of the changes have reverted back to the single screen with the second one displayed, but shown as inactive once again.  No information about the LG monitor is shown.  It says unknown on all the resolutions.  

At one time the second monitor was working properly, but did not survive a re-boot of Ubunutu.

I am enjoying the Ubuntu experience and have become a fan of the linux operating system.  The support of the community has been excellent, for which I am grateful.  Perhaps someone can point me in the right direction on this issue.

Thanks!

donaldt

---

### Post by hotweiss on 2009-04-20
Here's an Adobe Flash solution for playing full screen videos with Compiz enabled:

1. sudo mkdir /etc/adobe

2. sudo nano /etc/adobe/mms.cfg

3. Paste "OverrideGPUValidation=true"

4. Restart Firefox.

---

### Post by crjackson on 2009-04-20
kosimo,

I installed the 180.51 drivers... As you say, so-far, so-good...

Sadly the custom script didn't work.

Do you know of anyway to force the Hardware Drivers applet to indicate that this driver is installed?

---

### Post by Kosimo on 2009-04-20
> **crjackson said:**
> kosimo,

I installed the 180.51 drivers... As you say, so-far, so-good...

Sadly the custom script didn't work.

Do you know of anyway to force the Hardware Drivers applet to indicate that this driver is installed?


Hey, didn't work? :-k
Would be interesting to go deep into it and find out what is missing and rewrite it. I actually couldn't try it yet as I'm travelling, once back home I'll definitely give it a try as I still believe is a good idea, but I was wondering as well how to automate the choice of the internal options. Any idea?

About the hardware drivers, I guess that it would never realise that is installed, as it has nothing to do with the official .deb released for ubuntu, this means that the drivers are directly installed in the kernel instead of follow the debian installation process (which I think is the one that looks into it)  Please guys, correct me if I'm mistaken


Keep in touch!

---

### Post by Kosimo on 2009-04-20
> **The Bright Side said:**
> Just wanted to say that this thread and the instructions on the first page are AWESOME. Many thanks to Kosimo for maintaining and updating this, YOU DA MAN.

Thanks!
In fact, I just try to put together all information that can be found elsewhere anway :KS

---

### Post by OutOfReach on 2009-04-20
hmm after installing 180.51 KDE's Plasma and KWin have been crashing every once in a while. I don't know if this is a coincidence or the fault of the driver

---

### Post by ticket on 2009-04-22
> **inobe said:**
> if anyones having trouble with the 180.44's not being in package management you could add a source to synaptic [http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

the site responsible for the source [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

you will always get the very latest nvidia driver...

at least this way when you get a linux kernel image update you won't need to reinstall your nvidia driver manually !

Today the Avenard repository auto-updated me to 180.51.  No problems - it works fine.  

However, I was wondering if having the Avanard repos enabled will interfere with official Ubuntu driver releases (e.g. with the looming Ubuntu 9.04).

If Ubuntu also releases a 180.51 driver, which one will get installed?

---

### Post by DDM on 2009-04-22
Trying to update from 180.44 to 180.51 on Jaunty x64 using the Avenard repo. For some reason, nvidia-glx-180 wants to remove xorg, xserver-xorg and a bunch of xorg-related stuff.

---

### Post by inobe on 2009-04-22
Avenard updated me to 180.51 last night, no problems, i applied the update and restarted with 180.51 loaded.

---

### Post by crjackson on 2009-04-22
Kosimo - 180.51 is now posted as nvidia's latest RELEASE version.

---

### Post by Kosimo on 2009-04-23
> **crjackson said:**
> Kosimo - 180.51 is now posted as nvidia's latest RELEASE version.

Thanks for the heads up!

Information has been updated, 

Changelog for 180.53

> Fixed stability problems with some GeForce 6200/7200/7300 GPUs on multi-core/SMP systems.

---

### Post by ffixcollector on 2009-04-23
I used to have trouble with video lag, screen rip, and I could only play 720p videos. 
Now I have no issues and I can play 1080i videos, with minimal to no processor usage. 
I couldn't be happier with the 180.xx/vdpau drivers.

---

### Post by devolute on 2009-04-24
After a very nasty upgrade to 9.04 where I lost my desktop (new driver removed xorg-core!?) I'm finally back to a working, fast visual effects desktop.

Only one problem; no open GL in Wine so no Fireworks CS3 and no HL2.  They were both fine before.  Any suggestions?

---

### Post by Kosimo on 2009-04-24
Guys, is amazing how many releases do we get PER WEEK! :)

Now we've got a new BETA driver: [185.18.4]("http://www.nvnews.net/vbulletin/showthread.php?p=1990290") (which is newer than the 185.19)

Here the changelog: 

>     *  Worked around a bug in a RedHat patch applied to the X server in RHEL 5 that caused screen resolution changes to corrupt the screen.
    * Fixed occasional X driver memory management performance problems when a composite manager is running.
    * Improved compatibility with recent Linux kernels.
    * Fixed a DisplayPort interaction problem with power management suspend/resume events.


---

### Post by crjackson on 2009-04-24
> **ticket said:**
> Today the Avenard repository auto-updated me to 180.51.  No problems - it works fine.  

However, I was wondering if having the Avanard repos enabled will interfere with official Ubuntu driver releases (e.g. with the looming Ubuntu 9.04).

If Ubuntu also releases a 180.51 driver, which one will get installed?

I advise against using this repos for Jaunty. I hosed my system with it. Using the method on page 1 is the best I've found.

---

### Post by hoodaman on 2009-04-26
I have a problem. I got the drivers from the specified location and followed the directions in the original post and when I reboot all I get is a command prompt.

I have 2x BFG Geforce 9600GTs.

Could it be getting confused because I have 2 cards installed?

---

### Post by ticket on 2009-04-26
> **crjackson said:**
> I advise against using this repos for Jaunty. I hosed my system with it. Using the method on page 1 is the best I've found.

Ok, in prep for eventual installation of 9.04 I tried removing the 180.5 driver installed via the Avenard repo.

This didn't go as smoothly as I hoped.

I disabled the current 185 driver using the System->Administration->Hardware Drivers.  Did not reboot at this point (wasn't asked to)

I then un-ticked the Avenard repository using System->Administration->Software Sources

I then tried enabling the 180 driver again using the hardware drivers tool.
Didn't work, so in apt I ended up messing around un-installing refs to the 180.5 packages and installing the 180 glx package.  In the process I lost mplayer and tovid, presumably because it used the vdpau package that was somehow linked to the 185 driver.  Eventually I got back to the 180 driver (180.11) provided by Ubuntu in Intrepid 8.1 and restored the lost packages.

I hope there is an easier path than this!!

So I am back to the 180 series. After the dust settles, I will try the 9.04 distribution.  No 185 for me for now, as I failed to get the nvidia driver to install per this thread's instructions (and I tried real hard!).  

Does the 9.04 distribution provide a 185 Ubuntu driver package?

---

### Post by hanzomon4 on 2009-04-26
Well with dkms it should recompile it's self with each new kernel.

---

### Post by huntzire on 2009-04-27
I have been running x86_64-185.19 for a bit now with my linux kernel 2.6.29, i think the biggest improvement I have had was xorg update. It improved how smooth my gui works and AlienArena works alot better now, even though i just have a onboard chip heheh

---

### Post by northwestuntu on 2009-05-01
> Important note: After a kernel upgrade you won't be able to load x.org, that means that have to be configured again.

so to break it down to a newbie.  that means your screen won't come back up after a ubuntu kernel upgrade and you need to reinstall the nvidia driver manually again?

just checking.

---

### Post by Kosimo on 2009-05-01
> **northwestuntu said:**
> so to break it down to a newbie.  that means your screen won't come back up after a ubuntu kernel upgrade and you need to reinstall the nvidia driver manually again?

just checking.

Yes.

Then you have several options. This are the easiest ones:

1) You save a copy of the driver in your home folder, so if you can't load x.org, the only thing you do is CONTROL + F1, and uninstall the drivers:  sudo sh ./Nxxx --uninstall  after that you just need to install them again.   Problem solved.


2) Follow sdennie instructions to upgrade the kernel drivers automatically: [here]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by northwestuntu on 2009-05-01
great.  thanks for the confirmation on that and the extra info :)

---

### Post by drubdrub on 2009-05-01
> **Valok said:**
> Quick question, is there a way I can find out what video card I'm using within Ubuntu?  I know its some 8800 but I don't remember if its GT, GTS, or some other crappy naming system Nvidia came out with.

Howdy.  Give this a try:

lspci | grep -i nvidia

Best to you!

---

### Post by inobe on 2009-05-02
> **crjackson said:**
> I advise against using this repos for Jaunty. I hosed my system with it. Using the method on page 1 is the best I've found.


the repo being incompatible will remove gnome-desktop.

i edited my initial post for the avenard repo, apparently it's incompatible with a fresh install of 9.04' however there is minor corruption upgrading from 8.10..........



example of the corruption.

[http://ubuntuforums.org/showthread.php?t=1143504](http://ubuntuforums.org/showthread.php?t=1143504)

if you ended up in a server ui due to the repo' simply run

```
sudo dpkg-reconfigure xserver-xorg
```

if you get an error saying xserver isn't installed' do

```
sudo apt-get install ubuntu-desktop
```

if you get an nvidia error' do

```
sudo apt-get remove nvidia-glx
```

then run the ubuntu-desktop command....

after that you will need to manually remove the driver from the repo in synaptic, you can review the link for that information.

note: the person upgraded in the link' and is why he was able to continue using the repo.

---

### Post by macabro22 on 2009-05-02
Doodes,

I would like to report that using drivers 180.53 in SLI mode might slowdown ubuntu and cause Kernel Panics.

Can you guys confirm that?

---

### Post by Kosimo on 2009-05-02
> **macabro22 said:**
> Doodes,

I would like to report that using drivers 180.53 in SLI mode might slowdown ubuntu and cause Kernel Panics.

Can you guys confirm that?

I can't confirm it as I don't have an SLI configuration. You could give it a try to latest BETA drivers, it will may work better, or going to nvnews forum (linux section) and ask for help or create a bug.

---

### Post by inobe on 2009-05-03
figured out the avenard repo issue and why it was removing desktops.

**for jaunty 9.04**


the repo must be added in terminal.

first the key

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

then the repo

```
echo "deb http://www.avenard.org/files/ubuntu-repos jaunty release" | sudo tee /etc/apt/sources.list.d/avenard.list



```

i installed kubuntu 9.04 x64 bit, i did the system updates, activated thew 180.44 driver then added the 9.04 jaunty repo, i then received the update notification, applied updates and rebooted to a desktop running 180.51 driver.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

that page appears to be recently updated or i completely missed seeing it.

---

### Post by Roasted on 2009-05-03
I have nVidia 180 drivers with a 9600GT 512mb, yet I still have video tearing. Everyone made it sound like it was an Intrepid thing and Jaunty would fix it - but uh - still got tearing.

---

### Post by inobe on 2009-05-03
> **Roasted said:**
> I have nVidia 180 drivers with a 9600GT 512mb, yet I still have video tearing. Everyone made it sound like it was an Intrepid thing and Jaunty would fix it - but uh - still got tearing.

what application are you using that you notice tearing in ?

---

### Post by dearmrdear on 2009-05-03
Well, It's not Rockin for me. I've clean installed 9.04 (4) times. Twice from from the popup on install, once as described at the begining of this thread and I even tried 173 for laughs but none work they all freeze-up at "Checking battery state". Any ideas?

---

### Post by Roasted on 2009-05-04
> **inobe said:**
> what application are you using that you notice tearing in ?

VLC, if I recall properly. I'll try it tomorrow and verify.

---

### Post by inobe on 2009-05-04
> **Roasted said:**
> VLC, if I recall properly. I'll try it tomorrow and verify.

heres the thing, vlc has vdpau support, do you have the components for vdpau ?

i use mplayer+ffmpeg+vdpau


run this in terminal

```
ffmpeg -formats | grep vdpau
```

i get and you should also have accelleration.

```
box:~$ ffmpeg -formats | grep vdpau
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU

```


that's with the latest stable 180.51 using avenard repo, side not: i didn't manually compile anything, all settings and apps were automatic via synaptic.

---

### Post by Kosimo on 2009-05-04
Does VLC already have VDPAU support!??!?!!?!?


> **inobe said:**
> heres the thing, vlc has vdpau support, do you have the components for vdpau ?

i use mplayer+ffmpeg+vdpau


run this in terminal

```
ffmpeg -formats | grep vdpau
```

i get and you should also have accelleration.

```
box:~$ ffmpeg -formats | grep vdpau
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU

```


that's with the latest stable 180.51 using avenard repo, side not: i didn't manually compile anything, all settings and apps were automatic via synaptic.

---

### Post by inobe on 2009-05-04
> **Kosimo said:**
> Does VLC already have VDPAU support!??!?!!?!?

yes

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

---

### Post by Kosimo on 2009-05-05
Guys, new BETA drivers.
185.18.08

Release notes:

> #  Fixed stability problems with some GeForce 6200/7200/7300 GPUs on multi-core/SMP systems.
# Improved recovery from certain types of errors.
# Fixed a problem that caused DisplayPort monitors to never light up or lose sync intermittently on some Quadro GPUs.
# Fixed a bug that caused some performance levels to be disabled on certain GeForce 9 series notebooks.
# Fixed a problem that could result in temporary stalls when moving OpenGL application windows on GeForce 8 and later GPUs.
# Fixed a bug that could interfere with the detection of display devices attached to secondary GPUs when first starting X after cold boots.
# Fixed a bug that prevented VGA fonts from being saved/restored correctly on GeForce 8 and later GPUs.
# Loaded the NVIDIA kernel module earlier in the X driver's initialization path to facilitate more graceful fallbacks if the kernel module cannot be loaded. Removed the LoadKernelModule X configuration option.
# Fixed a bug that caused kernel crashes when attempting to initialize NvAGP on Linux/x86-64 kernels built with the CONFIG_GART_IOMMU kernel 

Links in the first page

---

### Post by skibota on 2009-05-05
Hi,
do you know something about the Hybrid SLI support on Linux Driver?
I have an Nvidia solution with a 9400M + 9200 on my Dell Studio XPS and i would know if it's possible to use the Hybrid SLI support on ubuntu or if it's possible to disable one of the cards (9200) to reduce the power consumption (under ubuntu I have 1 hour less of battery life respect Windows Vista where i can disable one card).
Thanks

---

### Post by Kosimo on 2009-05-05
> **skibota said:**
> Hi,
do you know something about the Hybrid SLI support on Linux Driver?
I have an Nvidia solution with a 9400M + 9200 on my Dell Studio XPS and i would know if it's possible to use the Hybrid SLI support on ubuntu or if it's possible to disable one of the cards (9200) to reduce the power consumption (under ubuntu I have 1 hour less of battery life respect Windows Vista where i can disable one card).
Thanks


Have a look here and try to find your laptop:

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by LightB on 2009-05-05
Well I bought a new middle ground nvidia card, a geforce 9600 I believe. I was going to get one anyways because the old ati I have sucked and support was dropped in fglrx to add insult to injury. 

I wonder if the linux nvidia driver supports the hdmi output, though. I have a 1080p hdtv, but I've never used it for PC. Do any of you use that setup, and if so, is it a feasible alternative to a monitor?

---

### Post by Kosimo on 2009-05-05
> **LightB said:**
> Well I bought a new middle ground nvidia card, a geforce 9600 I believe. I was going to get one anyways because the old ati I have sucked and support was dropped in fglrx to add insult to injury. 

I wonder if the linux nvidia driver supports the hdmi output, though. I have a 1080p hdtv, but I've never used it for PC. Do any of you use that setup, and if so, is it a feasible alternative to a monitor?


Yes it supports HDMI external monitors. (Be aware that you will only get video and not audio)

---

### Post by Kosimo on 2009-05-05
More updates guys:
nVidia released a new BETA Driver: 180.37.05  This is the latest OpenGL 3.1 driver available.

Links at the first page.

*180.37.05 Release notes*


> You need one of the following graphics cards to get access to the OpenGL 3.1 and GLSL 1.40 functionality:
Desktop

    * Quadro FX 370, 570, 1700, 3700, 4600, 4700x2, 4800, 5600, 5800, Quadro VX200, Quadro CX
    * GeForce 8000 series or higher; Geforce G100, GT120, 130, GTS 150, Geforce GTS 250, GeForce GTX 260, 280, 285 and 295, any ION based products.

Notebook

    * Quadro FX 360M, 370M, 570M, 770M, 1600M, 1700M, 2700M, 3600M, 3700M
    * GeForce 8000 series or higher

This driver now implements all of GLSL 1.30 and all of OpenGL 3.0, and all of OpenGL 3.1 and GLSL 1.40

This driver exposes the following new extensions:
OpenGL 2.1 extensions:

    * ARB_vertex_array_object
    * ARB_framebuffer_object
    * ARB_half_float_vertex

OpenGL 3.0 extensions:

    * WGL_create_context
    * GLX_create_context
    * ARB_draw_instanced
    * ARB_geometry_shader4
    * ARB_texture_buffer_object

OpenGL 3.1 extensions:

    * ARB_compatibility
    * ARB_copy_buffer

The OpenGL 3.1 and GLSL 1.40 specifications, as well as the extension specifications, can be downloaded here: [http://www.opengl.org/registry/](http://www.opengl.org/registry/)

For any bugs or issues, please file a bug through the developer website: [https://nvdeveloper.nvidia.com/](https://nvdeveloper.nvidia.com/)

---

### Post by Raguster on 2009-05-05
I've tried the 180.xx, 185.xx, and 173.xx with my 8600gts. I have a dual monitor setup and I keep getting black screensafter the ubuntu loading screen. Can anyone offer me any adivce (I'm a nooB)

---

### Post by calvinps on 2009-05-05
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. 
Now, it's been almost a week that I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 


*Edit April 17 2009*: Latest nVidia 180.xx (STABLE) drivers: **[COLOR=Red]180.51[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?p=1985816")


*Edit April 23 2009*: Latest nVidia 180.xx (PRE) Drivers: **[COLOR=Red]180.53[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?t=131874")


*Edit May 05 2009*: Latest nVidia 185.xx (BETA) Drivers: **[COLOR=Red]185.18.08[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?p=1997862")


*Edit May 05 2009*: Latest nVidia _OpenGL 3.1 _180.xx (BETA) Drivers: **[COLOR=Red]180.37.05[/COLOR]**  [ Download]("http://developer.nvidia.com/object/opengl_3_driver.html")



_**How to install nVidia drivers in Linux:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR=Red]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```**[COLOR=Red]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```**[COLOR=Red]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR=Red]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR=Red]7[/COLOR])** Then restart your computer   ```
sudo reboot
```**[COLOR=Red]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: 


**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.




Legacy releases for GeForce 5 series GPUs **[COLOR=Red]173.14.18[/COLOR]** [32 Bits, ]("http://www.nvidia.com/object/linux_display_ia32_173.14.18.html") / [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_173.14.18.html")

Legacy releases for GeForce 2 through GeForce 4 series **[COLOR=Red]96.43.11[/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_x86_96.43.11.html") , [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_96.43.11.html")

Legacy releases for Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR=Red]71.86.09[/COLOR]** [32 Bits]("http://www.nvidia.com/object/linux_display_x86_71.86.09.html"), [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_71.86.09.html")

*note*: Legacy drivers are being updated as well.

Good luck ;)

**tl;dr :|**

---

### Post by djungelmums on 2009-05-06
Anyone else having problems with the new 185.18.08?

Im getting logged out whenever i start a game like warcraft 3. Although i can benchmark with glxgears and glmark08 without problems.

---

### Post by Kosimo on 2009-05-06
> **djungelmums said:**
> Anyone else having problems with the new 185.18.08?

Im getting logged out whenever i start a game like warcraft 3. Although i can benchmark with glxgears and glmark08 without problems.

Remember that Warcraft III and the newest patch 1.23 isn't working properly under Wine, There is a bug in winehq webpage. You can also find some patches that can "partially" solve the problem in Battle.net 2.0

---

### Post by VastOne on 2009-05-06
> **CraigPaleo said:**
> Pardon me for correcting your English but don't you mean, "I don't want to ***HAVE RUINED*** the thread"? 

Closed or not, you have!

Lame...:sad:

And what an **** :P it is to assume that everyone that uses these forums first language is English

---

### Post by djungelmums on 2009-05-07
> **Kosimo said:**
> Remember that Warcraft III and the newest patch 1.23 isn't working properly under Wine, There is a bug in winehq webpage. You can also find some patches that can "partially" solve the problem in Battle.net 2.0

Thats true but with 185.18.04 it starts and i can play, although it crashes sometimes (but thats a war3 + wine bug, not nvidia-drivers).

I have the same problem with counter-strike in 185.18.08 so its not a war3 bug.

---

### Post by LightB on 2009-05-08
Finally installed the card. Better than ati card for 2d but it still crashed with compiz + games, but at least it can recover unlike ati fglrx. I think it's best to forget about compiz being capable of being active all the time any time soon.

---

### Post by mastergunner on 2009-05-10
Need help with coolbits. Where do I get it and how do I install it.

---

### Post by crjackson on 2009-05-10
> **mastergunner said:**
> Need help with coolbits. Where do I get it and how do I install it.

If you are using the proprietary nvidia driver, coolbits is built in.

Just edit your /etc/X11/xorg.conf

In the **_Device section for the NVIDIA graphics card_**, one additional line needs to be appended to the configuration. A line that reads **_Option “Coolbits” “1”_** should be added to the section. After restarting the computer and entering run-level 5, the CoolBits page should appear in nvidia-settings.

---

### Post by LightB on 2009-05-10
Yes, vdpau is pretty amazing. You can watch full HD video on fairly old machines like mine. I tried it in 180.x stable but vdpau was not vsync, the current beta driver 185.x does although it seems to have compiz bugs. If you don't care much for compiz and watch HD videos I'd use the beta driver already.

---

### Post by djungelmums on 2009-05-10
> **LightB said:**
> Yes, vdpau is pretty amazing. You can watch full HD video on fairly old machines like mine. I tried it in 180.x stable but vdpau was not vsync, the current beta driver 185.x does although it seems to have compiz bugs. If you don't care much for compiz and watch HD videos I'd use the beta driver already.

How did you activate it?

---

### Post by LightB on 2009-05-10
> **djungelmums said:**
> How did you activate it?

Once the driver is installed, the only thing I know of that can use it right now is a custom mplayer build, mplayer source with [some patches](ftp://download.nvidia.com/XFree86/vdpau/). On fedora, I found some rpms that can replace mplayer/mencoder and they seem to work fine. There must be some deb packages for Ubuntu somewhere.

---

### Post by Pasdar on 2009-05-10
After installing 185.18.08, it ruined my system. I had to purge everything nvidia* from my system an after much trouble managed to install the stable drivers from 'hardware drivers' again. Its now installed and enabled, however Compiz will not start and I can not enable effects, keeps saying, "Desktop effects could not be enabled"...

compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity

any help? :(

---

### Post by LightB on 2009-05-10
you probably should have uninstalled and disabled the repo drivers first.

---

### Post by Pasdar on 2009-05-10
it seems you were right. I removed repo drivers and installed 185.18.08 drivers and everything works again.

---

### Post by ukblacknight on 2009-05-11
I installed the 180.53 driver last night, vast improvement over the driver that came shipped with Jaunty!  Flash is better and things like Docky are even smoother :)

---

### Post by Kosimo on 2009-05-11
> **ukblacknight said:**
> I installed the 180.53 driver last night, vast improvement over the driver that came shipped with Jaunty!  Flash is better and things like Docky are even smoother :)



Docky is just amazing :)

---

### Post by Drokles on 2009-05-13
> **graabein said:**
> My graphics are all screwed up. Starting in low-res each time. Hope this driver fixes that. I've got a GeForce 6600 GT card. Anyone else had any problems with that card?
 
I also have that problem, although I use 7200, but the driver doesn't fix that.
It seems like theres no "good" way around it. If there is though I'd like to know.

---

### Post by Kosimo on 2009-05-13
> **Drokles said:**
> I also have that problem, although I use 7200, but the driver doesn't fix that.
It seems like theres no "good" way around it. If there is though I'd like to know.

Did you uninstall the Ubuntu Hardware Proprietary drivers before manually install the new ones?

---

### Post by Kosimo on 2009-05-14
Guys:

New PRE drivers: 180.60

Changelog:

>     *  Fixed VGA console restoration on some laptop GPUs.
    * Fixed a bug that caused kernel crashes when attempting to initialize NvAGP on Linux/x86-64 kernels built with the CONFIG_GART_IOMMU kernel option.
    * Fixed a bug that caused some performance levels to be disabled on certain GeForce 9 series notebooks.
    * Fixed crashes in Bibble 5.



Links in the first page.

---

### Post by stelmed on 2009-05-14
Hello everybody.
I have installed the latest 180.60 driver and after 5 hours of testing I haven't had a crash yet. That was not the case with the previous driver. Hopefully that this extremely annoying bug is fixed now.

---

### Post by Polygon on 2009-05-14
what the heck is bibble 5? :?:

---

### Post by Kosimo on 2009-05-14
> **Polygon said:**
> what the heck is bibble 5? :?:

I was asking the same question....

---

### Post by Gemnoc on 2009-05-14
Ever heard of Google? ;)

[http://bibblelabs.com/products/bibble5/](http://bibblelabs.com/products/bibble5/)

---

### Post by Kosimo on 2009-05-14
> **Gemnoc said:**
> Ever heard of Google? ;)

[http://bibblelabs.com/products/bibble5/](http://bibblelabs.com/products/bibble5/)

I'm too lazy lately... Anyway thanks for the link

---

### Post by Tim_Olaguna on 2009-05-14
> **Kosimo said:**
> Did you uninstall the Ubuntu Hardware Proprietary drivers before manually install the new ones?

Kosimo, I have a really dumb newbie kind of question: How does one do what you advise here?  How do I identify the "Ubuntu Hardware Proprietary drivers" for sure?

I know how to use the Synaptic Package Manager somewhat.  I have used it to search on the term "nvidia" and found a bunch of stuff.  I have used it to un-install those items named "nvidia-glx-###" as those were clearly described as an "NVIDIA binary Xorg driver".  

(None of those seemed to work for me at all under Ubuntu 9.04 anyway.  Every time I specified one of them and attempted to reboot that reboot would fail until I accepted the option of using a generic driver.)

Are those the "Ubuntu Hardware Proprietary drivers"?  Or have I miss-identified them?

---

### Post by Gemnoc on 2009-05-14
Hi Tim,

[QUOTE="Tim_Olaguna"]Kosimo, I have a really dumb newbie kind of question: How does one do what you advise here? How do I identify the "Ubuntu Hardware Proprietary drivers" for sure?[/QUOTE]
Ok, I'm not sure of the exact wording in English, as I have a French OS.

You have to go to the menu System/Administration/Hardware Proprietary Drivers. That last one may be worded differently. It will give you a window that lists the proprietary drivers available on your system, and you can activate/deactivate them there.

---

### Post by sherl0k on 2009-05-15
Gnome likes to restart when I switch between Compiz and Metacity using the fusion-icon. This never happened before I upgraded. Anyone else get this?

---

### Post by Tim_Olaguna on 2009-05-15
> **Gemnoc said:**
> Hi Tim,


Ok, I'm not sure of the exact wording in English, as I have a French OS.

You have to go to the menu System/Administration/Hardware Proprietary Drivers. That last one may be worded differently. It will give you a window that lists the proprietary drivers available on your system, and you can activate/deactivate them there.

Thank you, Gemnoc.  Your directions worked great for me.  The response I get is that I have no proprietary drivers installed.  So I guess I don't have to worry about un-installing anything.

Thank you for your help and "Hello!" from just outside Sacramento, California, USA.  Today it is sunny and 91 degrees F.

---

### Post by Gemnoc on 2009-05-15
Glad I could help Tim,

> "Hello!" from just outside Sacramento, California, USA. Today it is sunny and 91 degrees F.

Well "Hello back!" from up north. :) We had a nice sunny day today, but it didn't get warmer than 61ºF (which is normal for this time of year). I guess it's better than shoveling twelve inches of snow! :p

---

### Post by Arup on 2009-05-16
A few tips to this thread from my personal experience if I may, since my early SuSE days, I have always installed nvidia or ati drivers from their site. I feel its best to keep current when it comes to video drivers as new features and older bugs are cleared up but sometimes newer bugs get introduced as well but then thats a risk to take with any software or OS.

The script method of installing works out the best however with one caveat which I have discovered after hours or installing, formatting and re-installing Jaunty and Hardy. The included Googleearth package from medibuntu works fine only with drivers from repos. If you do a clean install of Ubuntu and then install nvidia drivers, everything works fine except for google earth. No matter what I tried, it would segfault in Hardy x64 and Jaunty x64 with nvidia drivers installed and open gl enabled. The only workaround to this is to install the nvidia drivers via hardware drivers first, reboot and install google earth, execute it and let it run. Then uninstall the nvidia drivers via the hardware drivers applet, do a sudo apt-get autoremove to remove the unwanted packages left behind, then its very important to do a sudo apt-get install build-essentials as the nvidia installed would need that to compile the driver against your kernel. After that reboot and enjoy the nvidia driver of your choice with Ubuntu, googleearth works fine as well.

---

### Post by Kosimo on 2009-05-17
> **Arup said:**
> A few tips to this thread from my personal experience if I may, since my early SuSE days, I have always installed nvidia or ati drivers from their site. I feel its best to keep current when it comes to video drivers as new features and older bugs are cleared up but sometimes newer bugs get introduced as well but then thats a risk to take with any software or OS.

The script method of installing works out the best however with one caveat which I have discovered after hours or installing, formatting and re-installing Jaunty and Hardy. The included Googleearth package from medibuntu works fine only with drivers from repos. If you do a clean install of Ubuntu and then install nvidia drivers, everything works fine except for google earth. No matter what I tried, it would segfault in Hardy x64 and Jaunty x64 with nvidia drivers installed and open gl enabled. The only workaround to this is to install the nvidia drivers via hardware drivers first, reboot and install google earth, execute it and let it run. Then uninstall the nvidia drivers via the hardware drivers applet, do a sudo apt-get autoremove to remove the unwanted packages left behind, then its very important to do a sudo apt-get install build-essentials as the nvidia installed would need that to compile the driver against your kernel. After that reboot and enjoy the nvidia driver of your choice with Ubuntu, googleearth works fine as well.

I've been always using google earth installed from medibuntu, and haven't had an issue at all after installing nVidia drivers manually

---

### Post by Arup on 2009-05-17
> **Kosimo said:**
> I've been always using google earth installed from medibuntu, and haven't had an issue at all after installing nVidia drivers manually

Neither do I but only after I install drivers from repository first and then remove then and install the nvidia drivers via .sh

---

### Post by djungelmums on 2009-05-17
> **sherl0k said:**
> Gnome likes to restart when I switch between Compiz and Metacity using the fusion-icon. This never happened before I upgraded. Anyone else get this?

Yes i had this problem with the .08 (newest) beta driver. I couldnt play games as well, then gnome restarted. So i switched back to the .04 driver.

---

### Post by northwestuntu on 2009-05-18
i have a overscan problem on my hdtv using the jaunty nvidia driver.  you think if i installed one of the latest drivers right from nvidia it will solve my overscan?

---

### Post by Kosimo on 2009-05-18
> **northwestuntu said:**
> i have a overscan problem on my hdtv using the jaunty nvidia driver.  you think if i installed one of the latest drivers right from nvidia it will solve my overscan?

Not guaranteed, but you can give it a try with newer versions. Just make sure you uninstall the previous version before compiling.

---

### Post by Kosimo on 2009-05-18
Net BETA 185.18.10 Has just been released!

>     *  Moved kernel module loading earlier in the X driver's initialization, to facilitate more graceful fallbacks if the kernel module cannot be loaded. Removed the LoadKernelModule X configuration option.
    * Add support for new horizontal interlaced and checkerboard passive stereo modes.
    * Fixed occasional X server crashes when running an OpenGL-based composite manager.
    * Fixed crashes in Bibble 5.



Links at the first page, like always ;)

---

### Post by ren4rd on 2009-05-19
I installed the beta drivers 185.18.10 with 180.11 because I had bugs in Blender. My 3d view turns black when I point my mouse in the window buttons or on the header window when AA is enabled.

I am not alone in this case and it did not change my problem.

Who could help me solve this problem ?

---

### Post by Arup on 2009-05-21
The latest beta 185.18.10 works quite well on my system with occasional xorg CPU spikes. The full screen movie playback has drastically improved over 180.51 stable. Earlier I would have to turn compiz off to watch a movie in full screen, now its no longer necessary. This is with a cheap nvidia 8400GS card with 512mb of memory.

---

### Post by Buschbarber on 2009-05-23
I just built a new PC.
Asus P5Q mobo
Core2Quad Q9400 2.66Ghz Processor
4Gb Corsair memory
Nvidia Gforce 9800GTX+ 512Mb Ram PCI-e
WinTV-HVR-1600 PCI card

I have been using Windows 7 64bit, with my 50" Sony HDTV as the monitor, connected via DVI to HDMI at 1900x1080. The Windwos 7 Nvidia Control Panel lets me shrink the Overscan so that the Desktop fits nicely inside the frame of the HDTV screen

I just installed Ubuntu 9.04 64bit in a Dual Boot. I installed the Nvidia 180 drivers using the Hardware Drivers choice and the Admin Menu. I installed Nvidia Settings. There does not seem be anything in the Control Panel to shrink the Ubuntu Desktop to fit the HDTV frame.

Any ideas on how to do this? The Overscan places the Menus off the top of the display

---

### Post by northwestuntu on 2009-05-23
yeah i have the same problem.  i've read a lot of options to solve overscan but nothing seems to work.  in the windows nvidia software there is tools for the overscan problem, not in linux though.

---

### Post by Buschbarber on 2009-05-23
> **northwestuntu said:**
> yeah i have the same problem.  i've read a lot of options to solve overscan but nothing seems to work.  in the windows nvidia software there is tools for the overscan problem, not in linux though.
Thanks!!

---

### Post by jppinto on 2009-05-23
Sorry to be the black sheep but I cant seem to install the nvidia drivers properly!

I am running ubuntu 8.10 and I have a NVIDIA GeForce 9300M GS (hp dv3560ep), and before trying to update the NVIDIA driver everything was working perfectly with 3D acceleration. The only problem that led me to update was a hue setting that was not correct.

I start by uninstalling everything related to NVIDIA, then open a terminal and stop gdm. Navigate to NVIDIA-linux-x86_64-180.51-pkg2.run and execute as sudo.

All goes smooth with no errors being reported and I end up back with the terminal prompt.

Then I start gdm. See some flashes of a NVIDIA picture filling the whole screen. And the After the flashes, the monitor shows some noise lines on top, and somehow the screen seems divided in 2. The left part of the screen shows the right part of what should be in the screen! and vice-versa. (however if I do a printscreen, the image is correct!)

At this point an error message appears saying:

"Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) failed to load module "type1" (module does not exist,0)
(EE) failed to load /usr/lib/xorg/modules/libwfb.so
(EE) failed to load module "wfb" (loader failed,7)
(EE) NVIDIA(0): Need libwfb but wfbScreenInit not found"

Similar errors occur when I try to install via the provided restricted drivers applet.

if I uninstall NVIDIA drivers "sudo sh NVI** --uninstall" then I get the screen correct again but low-graphics again.

I've tried numerous "solutions" like envyng and others but with no success.

Can someone help me?

J

---

### Post by itreius on 2009-05-23
Are you sure you followed this instruction?
[U]**Choose x.org automatic configuration at the last step inside the installation program**.
[/U]
Also, did you reboot the PC? Don't just start the GDM manually.

---

### Post by jppinto on 2009-05-23
I just redid all the work and in the end instead of starting gdm, I did "sudo reboot". (thanks for the suggestion)

The error stayed exactly the same!

After that and folloing a recomendation from other site, I commented the line involving "type1" under "modules" in /etc/X11/xorg.conf

After this change the initial error became:

"Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) failed to load /usr/lib/xorg/modules/libwfb.so
(EE) failed to load module "wfb" (loader failed,7)
(EE) NVIDIA(0): Need libwfb but wfbScreenInit not found"

The screen still has the same problem showing the screen shifted.

J

---

### Post by Kosimo on 2009-05-23
> **jppinto said:**
> Sorry to be the black sheep but I cant seem to install the nvidia drivers properly!

I am running ubuntu 8.10 and I have a NVIDIA GeForce 9300M GS (hp dv3560ep), and before trying to update the NVIDIA driver everything was working perfectly with 3D acceleration. The only problem that led me to update was a hue setting that was not correct.

I start by uninstalling everything related to NVIDIA, then open a terminal and stop gdm. Navigate to NVIDIA-linux-x86_64-180.51-pkg2.run and execute as sudo.

All goes smooth with no errors being reported and I end up back with the terminal prompt.

Then I start gdm. See some flashes of a NVIDIA picture filling the whole screen. And the After the flashes, the monitor shows some noise lines on top, and somehow the screen seems divided in 2. The left part of the screen shows the right part of what should be in the screen! and vice-versa. (however if I do a printscreen, the image is correct!)

At this point an error message appears saying:

"Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) failed to load module "type1" (module does not exist,0)
(EE) failed to load /usr/lib/xorg/modules/libwfb.so
(EE) failed to load module "wfb" (loader failed,7)
(EE) NVIDIA(0): Need libwfb but wfbScreenInit not found"

Similar errors occur when I try to install via the provided restricted drivers applet.

if I uninstall NVIDIA drivers "sudo sh NVI** --uninstall" then I get the screen correct again but low-graphics again.

I've tried numerous "solutions" like envyng and others but with no success.

Can someone help me?

J

It can be bug of this specific version. Did you give a try to the 180.61 PRE drivers? Or BETA?

If you keep having this problems, I recommend you to go post a bug on nvnews forums.

---

### Post by jppinto on 2009-05-23
Just installed 185.18.04 and the problem is exactly the same.

When I installed version 177.x using envyng or the restricted driver applet I had the same error.

I don't know if this is a clue for the problem, but:

* after I uninstall the NVIDIA driver "sudo sh NVID* --uninstall" and reboot "sudo reboot", the screen is no longer shifter, BUT I see the following error:

"Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.
(EE) failed to load module "glx" (module does not exist,0)
(EE) failed to load module "nvidia" (module does not exist,0)
(EE) No drivers available.

J

---

### Post by jppinto on 2009-05-23
I just opened a thread on "nvnews forums" "http://www.nvnews.net/vbulletin/showthread.php?t=133391" but I am afraid that from what I saw there, the linux related posts get 0 replies!

---

### Post by Kosimo on 2009-05-23
> **jppinto said:**
> I just opened a thread on "nvnews forums" "http://www.nvnews.net/vbulletin/showthread.php?t=133391" but I am afraid that from what I saw there, the linux related posts get 0 replies!

You should post it in the linux section! 

[http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14)

---

### Post by jppinto on 2009-05-23
Thanks. Will do. :)

---

### Post by jppinto on 2009-05-24
Problem SOLVED!

In the NVIDIA forumn, AaronP suggested to reinstall all xserver related packages. I did that and everything went smooth as silk.

as he said and I quote:
"libwfb.so is supposed to come from your distribution's X server package. It sounds like it's missing or corrupt. I would recommend reinstalling the X package."

J

p.s. here is the link to that forum: [http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951](http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951)

---

### Post by Kosimo on 2009-05-24
> **jppinto said:**
> Problem SOLVED!

In the NVIDIA forumn, AaronP suggested to reinstall all xserver related packages. I did that and everything went smooth as silk.

as he said and I quote:
"libwfb.so is supposed to come from your distribution's X server package. It sounds like it's missing or corrupt. I would recommend reinstalling the X package."

J

p.s. here is the link to that forum: [http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951](http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951)

Cool! 

Nice to know that you could finally find the answer for your problem! ;)

---

### Post by Kosimo on 2009-05-28
Latest news:

185.18.14 becomes PRE-Relase

Changelog:

>     *  Fixed a Xinerama drawable resource management problem that can cause GLXBadDrawable errors in certain cases, such as when Wine applications are run.
    * Fixed XineramaQueryScreens to return 0 screens instead of 1 screen with the geometry of screen 0 when XineramaIsActive returns false. This conforms to the Xinerama manual page and fixes an interaction problem with Compiz when there is more than one X screen.
    * Moved kernel module loading earlier in the X driver's initialization, to facilitate more graceful fallbacks if the kernel module cannot be loaded. Removed the LoadKernelModule X configuration option.
    * Added support for new horizontal interlaced and checkerboard passive stereo modes.
    * Fixed an OpenGL driver crash while running Bibble 5.
    * Fixed a DisplayPort interaction problem with power management suspend/resume events.
    * Fixed occasional X driver memory management performance problems when a composite manager is running.
    * Fixed a bug with VT-switching or mode-switching while using Compiz; the bug could lead to a corrupted desktop (e.g., a white screen) or in the worst case an X server crash.
    * Fixed a bug that could cause GPU errors in some cases while driving Quadro SDI products.
    * Fixed a several second hang when VT-switching while OpenGL stereo applications were running on pre-G80 Quadro GPUs.
    * Added support for multiple swap group members on G80 and later Quadro GPUs.
    * Fixed the behavior of the NV_CTRL_FRAMELOCK_SYNC_DELAY NV-CONTROL attribute on Quadro G-Sync II.
    * Fixed a problem with Quadro SDI where transitioning from "clone mode" to "OpenGL mode" would fail.
    * Fixed VDPAU to eliminate some cases of corruption when decoding H.264 video containing field-coded reference frames on G84, G86, G92, G94, G96, or GT200 GPUs. Such streams are commonly found in DVB broadcasts.
    * Slightly improved the performance of the VDPAU noise reduction algorithm.
    * Enhanced VDPAU to validate whether overlay usage is supported by the current hardware configuration, and to automatically fall back to the blit-based presentation queue if required.
    * Fixed error checking in VdpVideoMixerRender, to reject calls that specify more layers than the VdpMixer was created with.
    * Modified VDPAU's VDPAU_DEBUG code to emit a complete backtrace on all platforms, not just on 32-bit Linux.
    * Improved interaction between VDPAU and PowerMizer; appropriate performance levels should now be chosen for video playback of all standard resolutions on all supported GPUs.
    * Fixed a bug in VDPAU that sometimes caused "display preemption" when the VdpDecoderCreate function failed.
    * Fixed a potential segfault in the VDPAU trace library, triggered by a multi-threaded application creating a new VdpDevice in one thread, at the same time that another thread detected "display preemption".
    * Improved compatibility with recent Linux kernels.



As always, links in the first page

---

### Post by Kosimo on 2009-05-28
Texting using 185.18.14!

No particular issues here. Something new is that we've got a new NV-Control, which is now 1.18

---

### Post by Arup on 2009-05-29
Same here, runs nice and smooth, the drivers are getting better day by day.

---

### Post by randyklein99 on 2009-05-29
> **Kosimo said:**
> Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR="Red"]THIS IS MANDATORY![/COLOR]_**

Just wanted to say thanks.  This worked real well once I actually followed the above mandatory step.

Also, can we move this to a more appropriate forum - maybe the Tutorials section.

---

### Post by kranny on 2009-05-31
> **jppinto said:**
> Problem SOLVED!

In the NVIDIA forumn, AaronP suggested to reinstall all xserver related packages. I did that and everything went smooth as silk.

as he said and I quote:
"libwfb.so is supposed to come from your distribution's X server package. It sounds like it's missing or corrupt. I would recommend reinstalling the X package."

J

p.s. here is the link to that forum: [http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951](http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951)

Do i need to reinstall xserver-xorg-core and try running the nvidia installer??

---

### Post by UKRoman on 2009-05-31
Hi there,

Im trying to install the latest NVIDIA drivers, but when I issue the 'gdm stop' command to stop X Server i get a message saying 'Stopping Firestarter Firewall' and the machine then hangs. I then have to reboot and so end up back with the GUI desktop. Any ideas how to overcome this so that I can continue with installing the new drivers?

Thanks, UKRoman

---

### Post by Kosimo on 2009-05-31
> **UKRoman said:**
> Hi there,

Im trying to install the latest NVIDIA drivers, but when I issue the 'gdm stop' command to stop X Server i get a message saying 'Stopping Firestarter Firewall' and the machine then hangs. I then have to reboot and so end up back with the GUI desktop. Any ideas how to overcome this so that I can continue with installing the new drivers?

Thanks, UKRoman

For some reason looks like firestarter needs to be closed when stopping GDM. If you are unable to continue you can try to hit CONTROL + ALT + F1 before entering in your system (on the logging screen). 
Maybe firestarer won't be load yet so you can continue. 

Le me know if this works for you ;)

---

### Post by Polygon on 2009-05-31
how do you uninstall the custom installed nvidia drivers? As in the ones downloaded from nvidia.com? is there some command line argument to the install that will uninstall it or do i just use the restricted driver manager?

---

### Post by Kosimo on 2009-05-31
> **Polygon said:**
> how do you uninstall the custom installed nvidia drivers? As in the ones downloaded from nvidia.com? is there some command line argument to the install that will uninstall it or do i just use the restricted driver manager?

What I use to do in order to uninstall the manually installed drivers is: Using the same driver file (which includes an uninstaller). 

```
sudo sh ./NVIDIAxxx --uninstall
```

---

### Post by Arup on 2009-06-01
Place the driver you installed in your home folder, hit ctrl+alt+F1 login and do a sudo /etc/init.d/gdm stop

then type sh NVidiaxxxxxxxx --unistall

After its done do a sudo reboot.

---

### Post by AaronP_ on 2009-06-01
> **Arup said:**
> Place the driver you installed in your home folder, hit ctrl+alt+F1 login and do a sudo /etc/init.d/gdm stop

then type sh NVidiaxxxxxxxx --unistall

After its done do a sudo reboot.
You don't need the installer for that, just run
```

nvidia-installer --uninstall

```
or for more recent drivers, just
```

nvidia-uninstall

```
(nvidia-uninstall is a symlink to nvidia-installer that invokes the --uninstall option).

---

### Post by Arup on 2009-06-01
> **AaronP_ said:**
> You don't need the installer for that, just run
```

nvidia-installer --uninstall

```
or for more recent drivers, just
```

nvidia-uninstall

```
(nvidia-uninstall is a symlink to nvidia-installer that invokes the --uninstall option).

Thanks, makes it even easier.:D

---

### Post by Kosimo on 2009-06-01
> **AaronP_ said:**
> You don't need the installer for that, just run
```

nvidia-installer --uninstall

```
or for more recent drivers, just
```

nvidia-uninstall

```
(nvidia-uninstall is a symlink to nvidia-installer that invokes the --uninstall option).

Thanks, this is the best way.

---

### Post by shid007 on 2009-06-02
Sorry to post it here, but I didn't wanted to create a new thread for this... 

Is there a way to set a resolution that isn't listed in MetaModes shown by nvidia-settings? I have Thinkpad R61 with Quadro NVS140 and 1680x1050 lcd panel and I cant set 1024x768 nor 1280x800 resolution which is really pain in the a... since most of the projectors that I connect to notebook when I present something have this resolution (1024x768) working with it is really unconfortable...


Thanks for every answer.:popcorn:

---

### Post by jppinto on 2009-06-02
> **kranny said:**
> Do i need to reinstall xserver-xorg-core and try running the nvidia installer??

What I did was:

0- uninstall NVIDIA using "sudo sh NVI** --uninstall"
1- go to System-Admin-Synaptic
2- search for xserver
3- re-install all xserver installed packages (or if you know what you are doing, try to pin-point only relevant packages)
4- install NVIDIA using "sudo sh NVI**"

Did it help? :)

---

### Post by Kosimo on 2009-06-02
Guys:

180.60 Becomes stable.

Links at the first page.

---

### Post by Polygon on 2009-06-02
so, with 185.19 or whatever version i am running now, compiz works,and glxinfo says i have direct rendering, but i cant play any games that require the library libGL.so.1 ....anyone know whats wrong? should i try the ubuntu standard driver?

---

### Post by Kosimo on 2009-06-03
> **Polygon said:**
> so, with 185.19 or whatever version i am running now, compiz works,and glxinfo says i have direct rendering, but i cant play any games that require the library libGL.so.1 ....anyone know whats wrong? should i try the ubuntu standard driver?

How did you install this drivers?

---

### Post by Mattaus on 2009-06-04
Damnit the problems have started earlier for me than I had hoped...

I used to use Ubuntu a lot with ATI cards but I have not touched Linux for a year and a bit now and I'm starting fresh on a HTPC using an on board Nvidia 8200.

This will show how totally backwards I have gone but when I kill X.org it goes to text mode and does nothing...it just sits there and wont respond to any key commands what so ever. I let it sit for a good 5mins and it still did nothing.

What the? Am I doing something wrong here?

EDIT: I am an idiot. Problem solved. It seems I've been out too long lol.

---

### Post by biker3 on 2009-06-04
> **Polygon said:**
> so, with 185.19 or whatever version i am running now, compiz works,and glxinfo says i have direct rendering, but i cant play any games that require the library libGL.so.1 ....anyone know whats wrong? should i try the ubuntu standard driver?
I have the same problem:(
> **Kosimo said:**
> How did you install this drivers?

I did...
[LIST]
[*]uninstall the old drivers removing nvidia Debian packets.
[*]reboot
[*]chmod +x NVIDIA*
[*]./NVIDIA-Linux-x86_64-185.18.14-pkg0.run
[*]make module and condigure xorg with the installer
[*]and reboot
[/LIST]

with glxinfo I obtain direct rendering at yes, but in Quake 4 I obtain>
> --------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

My card is a GeForce 6800 512 MB. Before with 173.14.09 Quake 4 was slowly and for this I have tried the new drivers:oops:

---

### Post by biker3 on 2009-06-04
> ./NVIDIA-Linux-x86_64-185.18.14-pkg**2**.run
Problem solved! There is that install the high number of "run" files. In my situation is the #2 and not the #0:oops:

---

### Post by Kosimo on 2009-06-04
> **biker3 said:**
> Problem solved! There is that install the high number of "run" files. In my situation is the #2 and not the #0:oops:

Glad that you could find a solution. Usually try to get the highest number.

---

### Post by capinredbeard on 2009-06-04
I have tried installing the drivers by doing the following:

[LIST=1]
[*]At the login screen, pressing Ctrl+Alt+F2 to login into the console.
[*]/etc/init.d/gdm stop
[*]cd'ing to the folder (Desktop)
[*]sudo sh NVIDIA-Linux-x86_64-180.29-pkg2.run
[/LIST]
When the file runs, it gives the same error message (It appears that you are running X-Server ...)

I have searched through this thread, but didn't find any similar comment.  My apologies if I missed it.

This is my first hour with Ubuntu\Linux so be gentle :)

---

### Post by Mattaus on 2009-06-04
> At the login screen, pressing Ctrl+Alt+F2 to login into the console.

I could be completely wrong/been overly picky here (or you just have a typo) but should it not be Ctrl+Alt+F1?

---

### Post by bvanaerde on 2009-06-05
> **Mattaus said:**
> I could be completely wrong/been overly picky here (or you just have a typo) but should it not be Ctrl+Alt+F1?

You're both right :D
I think you can go to F6, and Ctrl+Alt+F7 brings you back to GDM. Not sure about the numbers though... it's been a while since I needed this. Just try it out ;)

---

### Post by pbrane on 2009-06-05
Like bvanaerde said above, Ctrl-Alt-F1 thru F6 will take you to a console (tty1-6). Ctrl-Alt-F7 will take you to the GUI, whether it is GDM or whatever. F1 console (tty1) is usually the console that is used for bootup output. Also if you're already in a tty you can simply do Alt-F7 to get back to the GUI, or go to another tty. You don't need the Ctrl key.

---

### Post by Kosimo on 2009-06-05
Guys:

185.18.14 Becomes stable

Links on the first page

---

### Post by Spif on 2009-06-05
I am trying to install the latest drivers on Ubuntu 8.04 LTS. It says I am missing a precompiled interface.

I do have the kernel-headers installed. What am I missing here?

---

### Post by Spif on 2009-06-05
Installed the driver and told it to compile it for me. Worked fine.

---

### Post by northwestuntu on 2009-06-05
they need to add a resize tool for hdtvs.

---

### Post by TetonsGulf on 2009-06-05
Just installed Nvidia Linux Display Driver - x86 Version 185.18.14, released 6/5 for a GeForce 6100 nforce 405 running Ubuntu Jaunty with kernel 2.26.28-11.

Everything works perfectly!

---

### Post by Spif on 2009-06-06
Well, this is strange. I installed the new stable driver, compiled the new kernel module during installation. I use nvidia-xconfig. X starts fine, everything is well.

I reboot and the kernel module is not loaded. It said something about a mismatch. It seemed to me that it was loading the module for the driver in the Ubuntu repo. Just to make it clear > I did not install the Ubuntu nvidia driver at any point, whatsoever.

---

### Post by Spif on 2009-06-06
Solved it by editing /etc/default/linux-restricted-modules-common and setting DISABLED_MODULES="" to DISABLED_MODULES="nv nvidia_new".

I honestly wasn't expecting Ubuntu's restricted hardware tool to interfere when I hadn't even used it. Ah well. Lesson learned.

---

### Post by crjackson on 2009-06-07
I'm thinking of installing the 185.18.14, are there any particular issues I should look out for on my MSI 8800GT OC

---

### Post by Kosimo on 2009-06-08
> **crjackson said:**
> I'm thinking of installing the 185.18.14, are there any particular issues I should look out for on my MSI 8800GT OC

I'm using them, and I had some strange issue with video colors, which was corrected by doing nothing (...) suddenly! 

A part from that, performance is excellent.

---

### Post by crjackson on 2009-06-08
> **Kosimo said:**
> I'm using them, and I had some strange issue with video colors, which was corrected by doing nothing (...) suddenly! 

A part from that, performance is excellent.

I'll guess I'll try it on for size after I do a full backup this weekend.  Thanks

---

### Post by Arup on 2009-06-09
185.18.14 is final release driver from nvidia now. Its on their website download page.

---

### Post by ratcheer on 2009-06-09
Kosimo, thank you very much. I just followed your instructions to upgrade from 180.something to 185.18.14. No problems at all.  My card is a 9400GT with 1024 MB.

Tim

---

### Post by Kosimo on 2009-06-09
> **ratcheer said:**
> Kosimo, thank you very much. I just followed your instructions to upgrade from 180.something to 185.18.14. No problems at all.  My card is a 9400GT with 1024 MB.

Tim

You're welcome ;)  It's nice to know that this post can help some people :KS

---

### Post by FokkerCharlie on 2009-06-11
Oh dear!

I have just removed the nvidia package from the Hardware Drivers manager, restarted and installed the new driver as described, but I now have a system that won't boot into the GDM at all!

The system boots, usplash OK, but then I am into a text-only screen, no error messages.  I can log in fine, switch terminals (ctrl+alt+fn) but even f7 / f8 don't work out.  I tried typing 'sudo /etc/init.d/gdm start', which reports that the Gnome Display Manager is starting, but then nothing happens!

Any ideas on how to proceed?

Cheers!
Charlie

---

### Post by hotweiss on 2009-06-11
> **FokkerCharlie said:**
> Oh dear!

I have just removed the nvidia package from the Hardware Drivers manager, restarted and installed the new driver as described, but I now have a system that won't boot into the GDM at all!

The system boots, usplash OK, but then I am into a text-only screen, no error messages.  I can log in fine, switch terminals (ctrl+alt+fn) but even f7 / f8 don't work out.  I tried typing 'sudo /etc/init.d/gdm start', which reports that the Gnome Display Manager is starting, but then nothing happens!

Any ideas on how to proceed?

Cheers!
Charlie

> sudo apt-get remove Nvidia*

and then reinstall your drivers

---

### Post by hotweiss on 2009-06-11
> **Arup said:**
> 185.18.14 is final release driver from nvidia now. Its on their website download page.

These drivers are great, Nvidia has come a long way.

---

### Post by FokkerCharlie on 2009-06-11
Thanks, hotweiss.

unfortunately, that didn't work.  It seems that X is not starting properly somehow.  After login to the text screen, I can ctrl+alt+f8 and see:

* Checking battery state...
/dev/sda:
 Setting Advanced Power Management level to 0xfe (254)     [OK]

And then nothing... no prompt, no error message.

If I try dpkg-reconfigure, it reports that it is not properly installed.

Help!
Charlie

---

### Post by hotweiss on 2009-06-11
> **FokkerCharlie said:**
> Thanks, hotweiss.

unfortunately, that didn't work.  It seems that X is not starting properly somehow.  After login to the text screen, I can ctrl+alt+f8 and see:

* Checking battery state...
/dev/sda:
 Setting Advanced Power Management level to 0xfe (254)     [OK]

And then nothing... no prompt, no error message.

If I try dpkg-reconfigure, it reports that it is not properly installed.

Help!
Charlie

Did you follow my steps in recovery mode?

---

### Post by Arup on 2009-06-12
> **hotweiss said:**
> These drivers are great, Nvidia has come a long way.

Fully agreed, mplayer vdpau performance as well as overall windows draw etc. have greatly improved. System response is snappier as well. ATI better catch up or most in Linux world will wave goodbye like I have.

---

### Post by FokkerCharlie on 2009-06-12
Hi Hotweiss

I followed your advice in recovery mode, to no avail.  X still doesn't seem to be starting.

I tried sudo dpkg-reconfigure xserver-xorg, which returned:
xserver-xorg is broken or not fully installed.

I can't get connected to the network via the terminal here, so I can't reinstall it!  Is it possible to download the packages to some other media or something?  Aaaargh!

Charlie

---

### Post by vreemde eend on 2009-06-12
I had an issue with the default nvidia driver and dual screen setup ([http://ubuntuforums.org/showthread.php?p=7444172#post7444172](http://ubuntuforums.org/showthread.php?p=7444172#post7444172)). Installing the latest stable driver solved my problem at last.

thanks a lot!!

pieter

---

### Post by ticket on 2009-06-12
> **Spif said:**
> Solved it by editing /etc/default/linux-restricted-modules-common and setting DISABLED_MODULES="" to DISABLED_MODULES="nv nvidia_new".

I honestly wasn't expecting Ubuntu's restricted hardware tool to interfere when I hadn't even used it. Ah well. Lesson learned.

Should this be part of the "How to" ?

---

### Post by rainwalker on 2009-06-12
I just got a ThinkPad W700 with a Quadro card in it; should I go with the v185 driver or is it true that Quadro cards use special drivers? The Nvidia site (after selecting my hardware) gives me the page to download the v169.12 driver, is this what I need?

UPDATE: I went ahead and installed the 185.18.14 driver and it seems the same as the regular 180 on in the Restricted Drivers Manager. However, I get some noticeable tearing (more than I had on my old laptop with an ATI card) when moving wobbly windows sideways; is this normal? I'm still tempted to try the 169.12 version that the Nvidia site gave me when I selected my hardware; should I? If I do, how do I go about uninstalling these drivers?

---

### Post by Arup on 2009-06-13
If nvidia is recommending 169 series drivers, then thats what you need to use. The 180 and 185 is for series 6x and up.

---

### Post by Spif on 2009-06-13
> **ticket said:**
> Should this be part of the "How to" ?

It should, if you ask me. At least for 8.04 LTS. Not sure if the issue is the same on newer releases.

---

### Post by rainwalker on 2009-06-14
> **Arup said:**
> If nvidia is recommending 169 series drivers, then thats what you need to use. The 180 and 185 is for series 6x and up.

Hm...everything seems to work fine, should I leave it with the v185 driver?

---

### Post by Arup on 2009-06-14
> **rainwalker said:**
> Hm...everything seems to work fine, should I leave it with the v185 driver?

If you have 3d support, leave it as it is.

---

### Post by rainwalker on 2009-06-14
> **Arup said:**
> If you have 3d support, leave it as it is.

Alright, I do so I'll leave it.
You don't think it would make a difference, performance-wise? I'm not going to be doing anything professional in Ubuntu, but I'd still like to get the most out of this card.

---

### Post by Arup on 2009-06-14
> **rainwalker said:**
> Alright, I do so I'll leave it.
You don't think it would make a difference, performance-wise? I'm not going to be doing anything professional in Ubuntu, but I'd still like to get the most out of this card.

If you wish to benchmark, then you can install gtkperf which is in the repos and do so. Don't worry, Ubuntu handles professional work far better than the other paid OS, in fact compiling on multi core PCs is a dream. Blender also runs quite good in Ubuntu.

---

### Post by ratcheer on 2009-06-21
Weird happening. I just ran Ubuntu Update Manager and quite a few packages were updated, as I have been on vacation for a week. When I rebooted, it threw me into reduced mode graphics, saying it could not find an installed driver. So, I had to go through the process on the OP of this thread and install v 185, again. It had been working perfectly until I ran Update Manager.

Is this just a fluke occurrence, or will I have to re-install nVidia every time I need to update the Ubuntu packages?

Thanks, Tim

---

### Post by Kosimo on 2009-06-21
> **ratcheer said:**
> Weird happening. I just ran Ubuntu Update Manager and quite a few packages were updated, as I have been on vacation for a week. When I rebooted, it threw me into reduced mode graphics, saying it could not find an installed driver. So, I had to go through the process on the OP of this thread and install v 185, again. It had been working perfectly until I ran Update Manager.

Is this just a fluke occurrence, or will I have to re-install nVidia every time I need to update the Ubuntu packages?

Thanks, Tim

When you update your kernel, driver must be recompiled again. 

If you don't want to do that you have two options:

1St, using the Hardware Proprietary Drivers tool included in Ubuntu (with older drivers)

2nd, Following the automated guide made by Sdennie mentioned in the first page to autocompile the drivers in each new kernel upgrade. Follow this [link]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by ratcheer on 2009-06-21
Thanks, Kosimo. I understand.

Tim

---

### Post by zubrick on 2009-06-23
Hello,

I have a GeForce 8400 GS, and when I install the nvidia driver (tried different versions) there is no audio in X (only in X, works in console mode).

If I use the opensource drivers the audio is ok but the video performance is really bad, so I really would like to use de nvidia drivers.

Have someone seen this problem before?

---

### Post by vreemde eend on 2009-06-23
I didn't have audio after I had to remove and recompile the drivers due to a kernel update. Solved by selecting a different device in Preferences -> Sound (I'm guessing, Os X right now). Might not be ideal, but seems to work for me.

---

### Post by zubrick on 2009-06-23
It didn't work. I really think the nvidia driver has a problem. I tested with another soundcard other desktop environments, and still no audio.
All the levels are ok in alsamixer, nothing is muted.

The strange part is that as soon as X is displayed on the screen there is no sound. For example, if I start a movie while in X, I only have the video and if I type ctrl+alt+F1 to switch to the console, I can ear the sound from the movie. It's the same if I play a song through ssh, as soon as X is on the screen, there is no sound.
It looks like something else is using alsa and preventing other sounds to be played.
For the moment I switched to an ATI card, the video quality is not as good as the one obtained with the nvidia drivers (even with the proprietary drivers) but at least I have sound and it's better than th default nv drivers.

If someone has a solution for my nvidia card, I would be happy to test it.

---

### Post by Arup on 2009-06-24
> **zubrick said:**
> Hello,

I have a GeForce 8400 GS, and when I install the nvidia driver (tried different versions) there is no audio in X (only in X, works in console mode).

If I use the opensource drivers the audio is ok but the video performance is really bad, so I really would like to use de nvidia drivers.

Have someone seen this problem before?

When you installed latest drivers from nvidia, did you remove previous drivers and also linux restricted modules and linux restricted modules common they have to be purged. Also you need to do a sudo apt-get install build-essential

---

### Post by mattwilkes512 on 2009-06-24
Has anyone in this thread installed the 185.xx drivers with PPA for use with a dell dimension 2400 PNY PCI 8400gs 512mb card?  I would like to know if this works before I buy-sound and video.

---

### Post by Kosimo on 2009-06-24
Guys: **[COLOR="Red"]190.09[/COLOR]** Leaked from a russian webpage

EXTREMELY UNOFFICIAL.  Use it at your own risk. 

Some words about this version from phoronix:

> The latest stable NVIDIA Linux driver release is in the 185.xx series, but NVIDIA developers have been hard at work on the forthcoming 190.xx driver series. Among other features, this next major driver update is expected to bring their talked about OpenCL support.

It will probably be some weeks still before NVIDIA even publicly releases a Linux driver in the 190.xx series, but currently for those that are under NDA with NVIDIA, they have early access as a registered developer. However, a beta NVIDIA Linux x86/x86_64 driver in the 190.xx series has leaked onto the Internet via a Russian web-site.

Among the official changes in this leaked NVIDIA driver include Compiz bug-fixes, improved H.264 and VC-1 video decoding with G98 and MCP97 cores, improved broken bytes processing in H.264 on cores G84, G86, G92, G94, G96, and GT200, fixing an X Server collapse on console switching, and improved VDPAU compatibility detection. Beyond that there are also some likely changes not mentioned in these brief release notes. This NVIDIA Linux driver is at version 190.09.

As this driver is not officially sanctioned by NVIDIA for general usage, use at your own risk -- and let us know in the forums what great things you run into!


Links at the first page

---

### Post by Kosimo on 2009-06-24
Here a screenshot using 190.09

---

### Post by Mazza558 on 2009-06-24
> **Kosimo said:**
> Guys: **[COLOR="Red"]190.09[/COLOR]** Leaked from a russian webpage

EXTREMELY UNOFFICIAL.  Use it at your own risk. 

Some words about this version from phoronix:




Links at the first page

I'll try it out and give some feedback if it works.

---

### Post by Mazza558 on 2009-06-24
Well I'm running them now, they seem to be snappier in both 2D and 3D but this might just be the placebo effect. No bugs as of yet, unlike some drivers (like the 180 drivers which leave artifacts everywhere).

There's a noticeable improvement in Firefox especially - scrolling half-loaded pages is better.

---

### Post by mgsfan on 2009-06-24
tried running 190.09 in karmic and it fails..so went back to 185's..though I used a ppa 
Did a manual install and now they are working correctly

---

### Post by Kosimo on 2009-06-24
> **mgsfan said:**
> tried running 190.09 in karmic and it fails..so went back to 185's..though I used a ppa  [https://launchpad.net/~brandonsnider/+archive/ppato](https://launchpad.net/~brandonsnider/+archive/ppato) install them

Did a manual install and now they are working correctly


Did yo uninstall the previous version before trying to install the new one?


190.09 works perfectly so far

---

### Post by mgsfan on 2009-06-24
yep I always uninstall whatever version I have before updating to a newer one..just would'nt work with this version from the ppa...I'll try later if if gets updated..er oops this the correct link to the ppa
[https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

---

### Post by master_kernel on 2009-06-24
Woohoo! 190 drivers!

---

### Post by NightwishFan on 2009-06-24
Do the 190 drivers support the 6 series?

---

### Post by Kosimo on 2009-06-24
> **NightwishFan said:**
> Do the 190 drivers support the 6 series?

The 6 series should be supported

---

### Post by mattwilkes512 on 2009-06-24
I have a PNY PCI 8400gs 512mb graphics card.  If i install with the 185.xx or 190.xx sereis drives does that support audio on this card or do I need a seperate sound card for that.  I ask because I have onboard graphics and sound and am not sure if both are disabled when I put a new graphics card in.  Also on a recent fresh install of Ubuntu 9.04 compiz was disabled becuase my graphics card was not supported (low graphics mode) but I also had no sound-both worked out of the box for 8.04 and prior.  Thanks.  Cant wait to set it all up and give these drivers a try!

---

### Post by ticket on 2009-06-24
Oh er, according to Avenard, the latest 185 stable driver breaks some machines:


> Wednesday, 10 June 2009
Well, the 185.18.14 drivers are sh*t... They completely hang my PC at least once a day now...

So I’m reverting back to 180.60.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

Ouch!

---

### Post by NightwishFan on 2009-06-24
185 installed correctly, but crashed Wine. So I will still use 180 from the repos.

---

### Post by el-mar01 on 2009-06-25
Installed the 190.x driver from the PPA but the kernel module failed to load so back to 185.x for me.

---

### Post by mgsfan on 2009-06-25
190.09 drivers in the ppa got updated 2 hours ago and install correctly now

---

### Post by xalaros on 2009-06-26
well i tried installing from ppa on x64 but got dkms kernel module build failure.
When i tried make module manually i got an error about unable to make kernel/bounds.c and then nvidia.ko failed to build.
Anybody tried this on x64 and has it working??

by the way i am on Jaunty x64 2.6.28.13

---

### Post by Saladyn on 2009-06-26
My Jaunty Jackalope x64 crashes with the same bug above mentioned!!! There are also  problems with broken dependencies &#8594; a new libvdpau doesn't match libxine and digikam...,

---

### Post by Dougie187 on 2009-06-26
Unfortunately, I get the same error.

---

### Post by Kosimo on 2009-06-26
> **Dougie187 said:**
> Unfortunately, I get the same error.

Guys... How about building it yourself?

---

### Post by Dougie187 on 2009-06-26
That is a possibility. I mean, it's not hard, it's just more convienent to remove later if it's from a PPA.

---

### Post by Kosimo on 2009-06-26
> **Dougie187 said:**
> That is a possibility. I mean, it's not hard, it's just more convienent to remove later if it's from a PPA.

If you want to remove a "manually" installed nvidia drivers just type: ```
sudo nvidia-uninstall
```

:KS

---

### Post by Dougie187 on 2009-06-26
Ok cool, I might give it a shot later. Right now I'm back to using 180, just because I had to get some stuff done.

---

### Post by mattwilkes512 on 2009-06-26
> **Kosimo said:**
> Guys... How about building it yourself?

How would I do that?  Are those the instructions at the beginning of the thread?  I'm still learning here.  Thanks.

---

### Post by NightwishFan on 2009-06-27
When I built it myself, Wine did not work. I will try the 185 debs again though.

---

### Post by dragos240 on 2009-06-27
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. 
Now, it's been almost a week that I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 


*Edit June 05 2009*: Latest nVidia 185.xx (STABLE) drivers: **[COLOR=Red]185.18.14[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?p=2016740")


*Edit May 05 2009*: Latest nVidia 180.xx (BETA) _OpenGL 3.1_  Drivers: **[COLOR=Red]180.37.05[/COLOR]**  [ Download]("http://developer.nvidia.com/object/opengl_3_driver.html")


*Edit June 24 2009*: [COLOR=Red]**EXTREMELY UNOFICIAL**[/COLOR] **[COLOR=Red]190.09[/COLOR]**  Drivers:  [ Download]("http://pavlinux.ru/190.09.html")


_**How to install nVidia drivers in Linux:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR=Red]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```**[COLOR=Red]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```**[COLOR=Red]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR=Red]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR=Red]7[/COLOR])** Then restart your computer   ```
sudo reboot
```**[COLOR=Red]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: ```
sudo sh ./Nxxx --uninstall
```or
```
sudo nvidia-uninstall
```**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.



_**Legacy Drivers**_

GeForce 5 series GPUs **[COLOR=Red]173.14.18[/COLOR]** [32 Bits ]("http://www.nvidia.com/object/linux_display_ia32_173.14.18.html") / [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_173.14.18.html")

GeForce 2 through GeForce 4 series **[COLOR=Red]96.43.11[/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_x86_96.43.11.html") , [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_96.43.11.html")

Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR=Red]71.86.09[/COLOR]** [32 Bits]("http://www.nvidia.com/object/linux_display_x86_71.86.09.html"), [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_71.86.09.html")


*note*: Legacy drivers are being updated as well.


Good luck ;)


A few of your links seem to be borked.

---

### Post by Kosimo on 2009-06-27
> **dragos240 said:**
> A few of your links seem to be borked.

which one?
all of them are working

---

### Post by dragos240 on 2009-06-27
> **Kosimo said:**
> which one?
all of them are working

I guess the server on the nvnews site was down.... nevermind back up.

---

### Post by Kosimo on 2009-06-28
Guys, a bunch of new legacy drivers are fresh available in the first page. A lot of work has been done, and changelog is big. Give them a try!

---

### Post by stanley82 on 2009-06-29
I downloaded and installed the driver okay.  Problem how do I change from 640 x 480 pixels.  That's in ubuntu Jaunty Jackalope 64 bit AMD set up Geforce 8500 GT.  Hope there is a way to get back into high resolution.

---

### Post by Kosimo on 2009-06-30
> **stanley82 said:**
> I downloaded and installed the driver okay.  Problem how do I change from 640 x 480 pixels.  That's in ubuntu Jaunty Jackalope 64 bit AMD set up Geforce 8500 GT.  Hope there is a way to get back into high resolution.

How did yo install the driver? Which driver did you download?

---

### Post by stanley82 on 2009-06-30
NVIDIA-Linux-x86_64-185.18.14-pkg1.run and I took all the defaults.  It said I needed a kernel, could not find one and re-compiled mine.  Preferences/Nvidia settings gives me a panel that tells me all sorts of complicated stuff but no way to change the 640 x 480.  I can only click detect monitor that changes nothing.  This is the most annoying screen that I have ever had.  Seems to pan all over and I fail to understand how to control what I'm seeing.  Maybe I should have downloaded pkg2 or 0 in place of pkg1?  Any help would be greatly appreciated.  Oh yes, I've just upgraded hardy to jaunty after my share of hicks tha last one being my screen moved 3cm to the left provoking my driver update.  Regards Ian

---

### Post by Kosimo on 2009-06-30
> **stanley82 said:**
> NVIDIA-Linux-x86_64-185.18.14-pkg1.run and I took all the defaults.  It said I needed a kernel, could not find one and re-compiled mine.  Preferences/Nvidia settings gives me a panel that tells me all sorts of complicated stuff but no way to change the 640 x 480.  I can only click detect monitor that changes nothing.  This is the most annoying screen that I have ever had.  Seems to pan all over and I fail to understand how to control what I'm seeing.  Maybe I should have downloaded pkg2 or 0 in place of pkg1?  Any help would be greatly appreciated.  Oh yes, I've just upgraded hardy to jaunty after my share of hicks tha last one being my screen moved 3cm to the left provoking my driver update.  Regards Ian

You should get the pkg2. 
One question: Did you use any previous drivers before? If yes, did you uninstall them correctly?

---

### Post by Kosimo on 2009-06-30
> **stanley82 said:**
> NVIDIA-Linux-x86_64-185.18.14-pkg1.run and I took all the defaults.  It said I needed a kernel, could not find one and re-compiled mine.  Preferences/Nvidia settings gives me a panel that tells me all sorts of complicated stuff but no way to change the 640 x 480.  I can only click detect monitor that changes nothing.  This is the most annoying screen that I have ever had.  Seems to pan all over and I fail to understand how to control what I'm seeing.  Maybe I should have downloaded pkg2 or 0 in place of pkg1?  Any help would be greatly appreciated.  Oh yes, I've just upgraded hardy to jaunty after my share of hicks tha last one being my screen moved 3cm to the left provoking my driver update.  Regards Ian

Try to get the pkg2, uninstall the previous version (sudo nvidia-uninstall) and start over again

---

### Post by stanley82 on 2009-06-30
From Ian.
I loaded pkg2 and did the rest of the stuff.  Looks the same and the NVDIA server settings (system/preferences) looks the same.  I see no way to change from 640 x 480.  That's what I need to do.  I can only see a portion of the display in great detail.  It looks like windows in safe mode.  Thanks Ian.

---

### Post by stanley82 on 2009-06-30
I restored to as before this driver and got back to the screen shifted 3cm to the left.  Back to try synaptic again envying.qt on the repository seems to be up again so here goes.  No change so reboot pain not having system/quit.  System/admin/HW drivers and it say I need a driver click to activate and it's still downloading and activating driver.  This release of ubuntu seems to have a few nasties stuck in it.  I'm not able to cancel the download popup.  So it's timed out with the jockey backend crashed.  I'm wasting my energy on this stuff ... all paths lead to nothing.  Thanks for trying to help.  Regards Ian.

---

### Post by VastOne on 2009-07-02
I have one system with a 940 Deneb that seems to dislike the 190 drivers.

I have setup mine to automagically pull in the latest drivers with dpkg.

Now that I am dead in the water and only a black screen, my question is, can I just go in with a Live boot CD and apt-get purge uninstall nvidia and get back to square one?  

I cannot even get to a screen with a safe mode boot and selecting the X repair option.  All I ever see is the modealias (sp?) message that dpkg is setting up the 190 drivers and I go dead.

Any and all help is greatly appreciated

---

### Post by NightwishFan on 2009-07-02
The GRUB screen is before the kernel (90% sure), so your Nvidia kernel module should not be an issue.

---

### Post by mattwilkes512 on 2009-07-02
> **mattwilkes512 said:**
> I have a PNY PCI 8400gs 512mb graphics card.  If i install with the 185.xx or 190.xx sereis drives does that support audio on this card or do I need a seperate sound card for that.  I ask because I have onboard graphics and sound and am not sure if both are disabled when I put a new graphics card in.  Also on a recent fresh install of Ubuntu 9.04 compiz was disabled becuase my graphics card was not supported (low graphics mode) but I also had no sound-both worked out of the box for 8.04 and prior.  Thanks.  Cant wait to set it all up and give these drivers a try!

So I followed the instructions at the beginning of the post and installed the 185.xx driver however I still cannot use compiz!  Do I need to blacklist my onboard graphics? How do I do that?
Here is the lspci
ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:05.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:05.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:05.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:06.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
ubuntu@ubuntu-desktop:~$ 


and here is my blacklist file
ubuntu@ubuntu-desktop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for ubuntu: 

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

I would very much appreciate anyone's help in getting this working.  Thanks!!!

Matt

---

### Post by stanley82 on 2009-07-02
I do not know, but in the boot process you should grub should give you the 3 seconds (if you did not disable it) to select a different kernel err like an older one.  You could try that if this is not your first install, even at that there should be a backup.  Regards  Ian.

---

### Post by thekonofman on 2009-07-02
Thing is, if you install the nVidia drivers from synaptic, they should work... they worked for me.  Only trouble with me is that my box starts up with a very low resolution.  I have to manually go to 

system > preferences > display

and then it says the default drivers aren't working... it asks whether or not to use the new drivers.

I choose yes, and then have to manually set the resolution.

Every single time I boot.

Any ideas?

---

### Post by thekonofman on 2009-07-02
> So I followed the instructions at the beginning of the post and installed the 185.xx driver however I still cannot use compiz! Do I need to blacklist my onboard graphics? How do I do that?Have you tried installing any other drivers?  As in a basic display drivers pack?

Sometimes the simplest solutions work the best.

---

### Post by mattwilkes512 on 2009-07-02
> **stanley82 said:**
> I do not know, but in the boot process you should grub should give you the 3 seconds (if you did not disable it) to select a different kernel err like an older one.  You could try that if this is not your first install, even at that there should be a backup.  Regards  Ian.

Yeah I did have an older kernal-selected it and was forced into low graphics mode.  No luck with that method but if you have any more ideas I'm open to em'?
thanks.

---

### Post by mattwilkes512 on 2009-07-02
> **thekonofman said:**
> Have you tried installing any other drivers?  As in a basic display drivers pack?

Sometimes the simplest solutions work the best.

I tried installing the 180 driver that is in restricted drivers and got the same result I have now with the 185.xx driver I installed by the instructions in this post.  On a separate matter I was able to get the sound back...just had to enable in BIOS. lol
The 185.xx installation went smooth. No errors but still cant enable compiz!  Attached is a pic of the nvidia manager showing installed driver.
Help anyone??
thanks

---

### Post by jocheem67 on 2009-07-05
Well, I've been installing the beta's on several occasions but ran into trouble lately as I kind of forgot the steps to take:

Appeared that I forgot to uninstall older driver(s)..a simple "sudo nvidia-uninstall" did the trick and I'm now happily running the 185.18.14...
It was a kernel update that forced me to install/update the drivers actually..

As it didn't work to do it manually, I was thankfully able to use the synaptic 180's...uninstalled those later, uninstalled the 185 remains through "nvivia-uninstall" .... and did a clean 185 install through the usual method of page 1 of the thread.

Maybe this helps someone.

---

### Post by VastOne on 2009-07-06
> **VastOne said:**
> I have one system with a 940 Deneb that seems to dislike the 190 drivers.

I have setup mine to automagically pull in the latest drivers with dpkg.

Now that I am dead in the water and only a black screen, my question is, can I just go in with a Live boot CD and apt-get purge uninstall nvidia and get back to square one?  

I cannot even get to a screen with a safe mode boot and selecting the X repair option.  All I ever see is the modealias (sp?) message that dpkg is setting up the 190 drivers and I go dead.

Any and all help is greatly appreciated

Bump

---

### Post by tommsen77 on 2009-07-06
damn, i don't get it working. Tried all approaches install/uninstall/install pkg1 manually, also tried to use a version from a repository...it doesn't work. I always get this " you do not appear to be using the nvidia x drive" when i try to use nvidia-settings.
Is it possible, that it doesn't work via a freeNX session (which i use if im not at home)?
I had it working when i first setup my machine, but now it does't work :(

any ideas?

---

### Post by darco on 2009-07-07
I just upgraded my kernel from 28.11 to .30 and decided to d/l and install the latest drivers. I tried before w/the older kernel and got a black screen so I was hoping the new kernel would work. It did.....

I posted this awhile ago in this thread on how I install new drivers..

system > administration > hardware > disable any nvidia drivers if any are enabled
run: sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
run: sudo apt-get autoremove
reboot back to desktop
then crtl+alt+f1
stop gdm: sudo /etc/init.d/gdm stop
login with normal account
sudo sh /<driver location>/NVIDIA-xxx.run
start gdm: sudo /etc/init.d/gdm start

If you get a low resolution screen, reboot into recovery mode and choose Fix x server, reboot. You may have to re-run the steps above if the driver didnt take...

good luck
darco

---

### Post by molder on 2009-07-07
I was hoping that upgrading to the nvidia 185 driver would give me an easy fix to the over scan issue I have with my tv but to my disappointment it did not.  Anyione have any suggestions for correcting this?

---

### Post by molder on 2009-07-07
Also for those trying install the 185.xx driver, in addition to running sudo /etc/init.d/gdm stop in tty2 I had to open a terminal window in GNOME and use the same command to get the installer to comply.

---

### Post by GeekGirl1 on 2009-07-07
Darco - Thank you very much for the install instructions. I somehow have managed to get the kernel sources mixed up. The shell scripts by NVidia (/usr/bin/nvidia-uninstall or /NV*.run --uninstall) to remove the drivers stated that all was OK, but subsequent driver installations were failing due to mismatched kernels.

I installed 180.51 (it's what I had), and got into the low-res mode. Then, I ran System --> Administration --> Hardware drivers and enabled the NVidia driver. It installed a driver. After rebooting, I am now running 180.44 and in a very nice 1920 x 1200 resolution.

From /var/log, it's incomplete:
> Jul  7 17:13:30 ubuntu kernel: [  555.765054] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul  7 17:13:30 ubuntu kernel: [  555.787214] NVRM: API mismatch: the client has the version 185.18.14, but
Jul  7 17:13:30 ubuntu kernel: [  555.787216] NVRM: this kernel module has the version 180.44.  Please
Jul  7 17:13:30 ubuntu kernel: [  555.787217] NVRM: make sure that this kernel module and all NVIDIA driver
Jul  7 17:13:30 ubuntu kernel: [  555.787217] NVRM: components have the same version.I'm not sure how to clean the NVidia kernel sources to get the correct "matched" versions.

I'd like to update to 185.14, but I don't know where the kernel sources are. The Open-GL server is not running, but I'm stuck at this version until I get the source versions aligned with the driver.

FWIW- There was a post from someone who could never read the text with the default driver because it was too small. I have had the same problem over several years with different cards. No idea why. I have always had to use the text-based OS installer because no graphics modes were usable. This is a problem, which I see occasionally when I have driver problems.

---

### Post by darco on 2009-07-07
> **GeekGirl1 said:**
> Darco - Thank you very much for the install instructions. I somehow have managed to get the kernel sources mixed up. The shell scripts by NVidia (/usr/bin/nvidia-uninstall or /NV*.run --uninstall) to remove the drivers stated that all was OK, but subsequent driver installations were failing due to mismatched kernels.

I installed 180.51 (it's what I had), and got into the low-res mode. Then, I ran System --> Administration --> Hardware drivers and enabled the NVidia driver. It installed a driver. After rebooting, I am now running 180.44 and in a very nice 1920 x 1200 resolution.

From /var/log, it's incomplete:
I'm not sure how to clean the NVidia kernel sources to get the correct "matched" versions.

I'd like to update to 185.14, but I don't know where the kernel sources are. The Open-GL server is not running, but I'm stuck at this version until I get the source versions aligned with the driver.

FWIW- There was a post from someone who could never read the text with the default driver because it was too small. I have had the same problem over several years with different cards. No idea why. I have always had to use the text-based OS installer because no graphics modes were usable. This is a problem, which I see occasionally when I have driver problems.

I know its a pain but I would re run the purge command, reboot and see if there are any traces of the nvdia driver. It sure looks like there was when you activated the restricted driver. What I noticed again when installing  a new driver, the xorg.conf gets dumped in the /root folder rather than in the X11 folder. After install it all seemed fine but I noticed the /root xorg.conf was more detailed (picked up my gaming mouse) than what I was running. I copied it over to the proper folder, rebooted, and it looks great.
Dont give up

darco

---

### Post by GeekGirl1 on 2009-07-08
That wasn't it. The 2nd time I purged, apt reported everything was OK (no modules installed).

I even thought there was a problem with the symbolic link in /usr/lib/xorg/modules/extensions/libglx.so, as the NVidia installer reported that it could not read this file. When I manually updated the link to be the actual file, the installer complained and put the link back.

I have a folder called /usr/src/nvidia-180.44, which is at the same level as the kernel source files.

A dump of /var/log/nvidia-installer.log. The kernel mismatch was also echoed /var/log/kern.log. Notice where it jumps from 185.18.14 to 180.44 during the load process. It looks like a dependency is mismatched, not the compile. Is there some sort of modprobe or depmod that I should be doing to clear this out? The install script is doing a 'depmod -aq' at the end. I'm not sure on how to resolve this.

I'm thinking that since the System --> Administrative --> Hardware Settings can install 180.44 correctly, it's probably a configuration / dependency problem. But, the Ubuntu script knows how to fix it.```
-> Kernel module compilation complete.
-> Kernel messages:
   [  915.076333] nvidia 0000:01:00.0: setting latency timer to 64
   [  915.076582] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14 
   Wed May 27 01:23:47 PDT 2009
   [ 1085.622718] nvidia 0000:01:00.0: setting latency timer to 64
   [ 1085.623233] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14 
   Wed May 27 01:23:47 PDT 2009
   [ 1312.537920] nvidia 0000:01:00.0: setting latency timer to 64
   [ 1312.538433] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14 
   Wed May 27 01:23:47 PDT 2009
   [ 1390.536720] nvidia 0000:01:00.0: setting latency timer to 64
   [ 1390.537236] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue
   Mar 24 05:46:32 PST 2009
   [ 1390.568402] NVRM: API mismatch: the client has the version 185.18.14, but
   [ 1390.568403] NVRM: this kernel module has the version 180.44.  Please
   [ 1390.568404] NVRM: make sure that this kernel module and all NVIDIA driver
   [ 1390.568404] NVRM: components have the same version.
   [ 1393.670873] NVRM: API mismatch: the client has the version 185.18.14, but
   [ 1393.670875] NVRM: this kernel module has the version 180.44.  Please
   [ 1393.670876] NVRM: make sure that this kernel module and all NVIDIA driver
   [ 1393.670876] NVRM: components have the same version.
   [ 1396.775437] NVRM: API mismatch: the client has the version 185.18.14, but
   [ 1396.775438] NVRM: this kernel module has the version 180.44.  Please
   [ 1396.775439] NVRM: make sure that this kernel module and all NVIDIA driver
   [ 1396.775440] NVRM: components have the same version.
   [ 1403.313209] mtrr: base(0xf5000000) is not aligned on a size(0xe00000)
   boundary
   [ 1422.740660] mtrr: no MTRR for f5000000,e00000 found
   [ 1428.258541] mtrr: base(0xf5000000) is not aligned on a size(0xe00000)
   boundary
   [ 1681.537821] nvidia 0000:01:00.0: setting latency timer to 64
   [ 1681.538344] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14 
   Wed May 27 01:23:47 PDT 2009
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: No)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (185.18.14):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
```I'm not giving up, as I can always recover with the 180.44 driver.

Update: More info. Could it be a problem with dkms? You can see it using 180.44, but I don't know how to fix it.```
~> locate nvidia.ko
/lib/modules/2.6.28-13-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.28-13-generic/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/180.44/2.6.28-13-generic/x86_64/module/nvidia.ko
/var/lib/dkms/nvidia/180.44/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/180.44/build/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.28-11-generic/x86_64/collisions/kernel/drivers/video/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.28-11-generic/x86_64/collisions/kernel/drivers/video/nvidia/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.28-13-generic/x86_64/nvidia.ko
~> lsmod | grep nvidia
nvidia               8123768  0 
```

---

### Post by GeekGirl1 on 2009-07-09
It's working! Open GL is up and running! How? The Ubuntu X repository has prebuilt 185.18.14 packages ready to go. No need to do this manually. Let Synaptic do the work for you. 

I knew that my kernel mismatch was due to a configuration problem with dkms, but I didn't know how to fix it. Synaptic took care of everything. It removed all the dkms modules then reinstalled what it needed using the 185.18.14 driver. It just worked.

See this thread: [Proprietary drivers not working, nvidia](http://ubuntuforums.org/showthread.php?p=7590694#post7590694)

_Start here:_
From the [Ubuntu X repository](https://edge.launchpad.net/~ubuntu-x-swat), go to the X Updates page: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

_Do the next 2 steps in any order:_
- Signing key: Select "What is this?" and follow the instructions to add the pgp key. This step uses a terminal command line. 
- Install packages: Select "Read about installing" and follow the instructions. You'll add the 2 lines noted below "Display sources.list entries". This step uses System --> Administration --> Software Sources

_Uninstall the current NVidia driver:_
-- Open a terminal, cd to to your NVidia driver file and run the command below. Hit the TAB key to complete the filename after NVIDIA (at the *):
```
sudo sh ./NVIDIA* --uninstall
```

_Use Synaptic to install the new drivers:_
-- Open System --> Administration --> Synaptic Package Manager
-- In the Quick Search box, type "nvidia"
-- nvidia-glx-180 should appear somewhere in the selection choices. Note that the installed version is your current version (180.44), but the "Latest Version" is 185.18.14. The Ubuntu X repository has replaced the NVidia drivers with the latest version. You can also see a lot of files listed as 185.18.14. This is good.
-- Mark nvidia-glx-180 for installation. It will add a lot more files that it needs to build the driver.
-- Select "Apply" and watch the details as it goes to work.
-- Reboot and you are done.

---

### Post by VastOne on 2009-07-11
> **VastOne said:**
> Bump

bump again

---

### Post by VastOne on 2009-07-11
> **VastOne said:**
> I have one system with a 940 Deneb that seems to dislike the 190 drivers.

I have setup mine to automagically pull in the latest drivers with dpkg.

Now that I am dead in the water and only a black screen, my question is, can I just go in with a Live boot CD and apt-get purge uninstall nvidia and get back to square one?  

I cannot even get to a screen with a safe mode boot and selecting the X repair option.  All I ever see is the modealias (sp?) message that dpkg is setting up the 190 drivers and I go dead.

Any and all help is greatly appreciated

bumped again

---

### Post by heyyy on 2009-07-11
since a later stable version is out why its not available through the hardware driver manager?

---

### Post by GeekGirl1 on 2009-07-11
VastOne - Have you tried to reboot with the "Recovery" option? Your boot menu should give you a "recovery" or "failsafe" mode. Try doing that first.

185.xx is not that stable. It's up to the Ubuntu team to decide when it's "stable enough". You can get it through an "unofficial repository" as I described above or in this thread:[http://ubuntuforums.org/showthread.php?t=1206998&page=5](http://ubuntuforums.org/showthread.php?t=1206998&page=5)

---

### Post by VastOne on 2009-07-11
> **GeekGirl1 said:**
> VastOne - Have you tried to reboot with the "Recovery" option? Your boot menu should give you a "recovery" or "failsafe" mode. Try doing that first.

185.xx is not that stable. It's up to the Ubuntu team to decide when it's "stable enough". You can get it through an "unofficial repository" as I described above or in this thread:[http://ubuntuforums.org/showthread.php?t=1206998&page=5](http://ubuntuforums.org/showthread.php?t=1206998&page=5)

I have been using 185 forever on several machines with out issue. It is the 190 drivers I am fighting with. 

Yes I have done the recovery option but all I get is a black screen because the 190 drivers are failing before X even starts.

What I need is to uninstall 190.X and reinstall 185.xx and I am trying to find that process to do it correctly

Thanks

---

### Post by macabro22 on 2009-07-12
> **heyyy said:**
> since a later stable version is out why its not available through the hardware driver manager?

It is available here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

---

### Post by mattwilkes512 on 2009-07-14
> **mattwilkes512 said:**
> I have a PNY PCI 8400gs 512mb graphics card.  If i install with the 185.xx or 190.xx sereis drives does that support audio on this card or do I need a seperate sound card for that.  I ask because I have onboard graphics and sound and am not sure if both are disabled when I put a new graphics card in.  Also on a recent fresh install of Ubuntu 9.04 compiz was disabled becuase my graphics card was not supported (low graphics mode) but I also had no sound-both worked out of the box for 8.04 and prior.  Thanks.  Cant wait to set it all up and give these drivers a try!

Well I finally got 8.10 working on my dell dimension 2400.  What I did was 
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
( [http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html) )
to get the nvidia card to be recognized and then before restart I installed the 185.xx driver as described on page one of this post.  I think the problem was with the onboard graphics and Intel's i845GV chipset.  Sound was enabled by just turning it back on in the bios after 8.10 and 185.xx install.

---

### Post by Riffer on 2009-07-14
Try the 185 driver and everything works well .. except quicktime in firefox.  its like its missing one of the colour channels (red), any fix for this.  Everything else works fine.

---

### Post by FirstByté on 2009-07-15
**[I dropped in here to help solve a friend's 3year-old '*no support found*' Asus F3 [sample image link]("http://www.notebookreview.com/assets/16079.jpg")) blessed with nVidia GeForce 8400m G/ 128MB]**

Apologies if I'm duplicating posts. I tried to read the first 5 pages of post and the last 8pages of post, but didn't find someone with similar challenge as mine; that's why I'm writing this. I wrote this about a week ago, but couldn't post it 'cause I didn't have all the necessary details upfront.

I've been trying to work on fixing/installing NVIDIA driver version **185.18.14.** with no head ways. Honestly I have barely more than a year old experience with Ubuntu/Linux.

The Device Details:
```

- Asus F3 Series Laptop
- nVidia GeForce 8400m G
- Centrino Duo Core 2
- 512MB RAM

```

```

ubuntu@ubuntu:~$ lspci -nn |grep -i VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M G [10de:0428] (rev a1)

```

I was a fresh installation of Ubuntu 8.10 [same happened with fresh installation of Ubuntu 9.04 too] but only the versa (800x600) resolution worked.

At first I tried the restricted installer from the "Hardware Drivers Manager" it takes forever and later does nothing... so I opted for the manual installation of the 180.18.14.pk... but it's ftp fails (well, I wasn't able to get _**iwconfig, ifdown, ifup**_ to help me in the tty console). It opted to compile the nVidia Kernel interface instead. After a while it reports a series of errors.

I tried all these:
```

sudo apt-get update; sudo apt-get upgrade 
sudo apt-get install linux-kernel-hearders
sudo apt-get install linux-headers-generic
sudo apt-get install build-essential

```

then retried the nVidia installation manually.. it still fell short of compilation or even installing.

I have since tried some legacy drivers with it.. it didn't work either. 

I have appended the card ID 'cause, my friend told me he bought it about 3year ago, and has since been trying to use Ubuntu on it with no success.

I have the "**[nvidia-installer.log]("http://docs.google.com/Edit?docid=dchm3mct_1gjhc9cg3")**" <=LOG but can not attach it here 'cause the size is 56kb so I saved it on Google Docs

I'll greatly appreciate any help that can be given. and also cooperate to any extent possible to get his Ubuntu working.. *cause he is one die-hard lover of Ubuntu*.

NOTE: He said, OpenSolaris works OOTB for him! But the Ubuntu way, he 
prefers to tread.



***- Firstbyté***

---

### Post by GeekGirl1 on 2009-07-15
> **Riffer said:**
> Try the 185 driver and everything works well .. except quicktime in firefox.  its like its missing one of the colour channels (red), any fix for this.  Everything else works fine.Interesting. Now that you mention it, I think I have the same problem with Totem (Movie Player). 

See if you can reproduce this: In FF, go to NASA's public TV site, [http://www.nasa.gov/multimedia/nasatv/index.html](http://www.nasa.gov/multimedia/nasatv/index.html). Right-click to "Open in Movie Player" and watch the live feed. You should be in Totem. The Red channel is missing.

Open the System --> Administration --> NVidia X Server Settings. Select a 2nd display (if you have one) and enable it. The color is restored in Totem, which is playing on my primary display. Totem is using a Windows Media 9 video codec to display the stream.

I think something needs to be reset and changing the display configuration fixes it. If you think it's Quicktime and I think it's the video codec, perhaps it really is the NVidia driver.

Update: The Totem video stream lost the red channel again. It came back as soon as I started the NVidia X Server Settings.

---

### Post by GeekGirl1 on 2009-07-15
> **FirstByté said:**
> [I dropped in here to help solve a friend's 3year-old '*no support found*' Asus F3 [sample image link]("http://www.notebookreview.com/assets/16079.jpg")) blessed with nVidia GeForce 8400m G/ 128MB]Have you tried the technique I used, which is to utilize the 185.18.14 packages available from the PPA repositories?

In this thread here: [http://ubuntuforums.org/showpost.php?p=7590748&postcount=917](http://ubuntuforums.org/showpost.php?p=7590748&postcount=917)

Which has more information in this thread: [http://ubuntuforums.org/showthread.php?p=7590694#post7590694](http://ubuntuforums.org/showthread.php?p=7590694#post7590694)

The point is to use the already built packages instead of a generic shell script. The package manager will manage everything correctly.

If that doesn't work you can try this script, which worked when I had 8.10: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) It should be current, but I can not verify if it works on 9.04.

---

### Post by FirstByté on 2009-07-16
> **GeekGirl1 said:**
> 
Have you tried the technique I used, which is to utilize the 185.18.14 packages available from the PPA repositories?

In this thread here: [http://ubuntuforums.org/showpost.php...&postcount=917](http://ubuntuforums.org/showpost.php...&postcount=917)

Which has more information in this thread: [http://ubuntuforums.org/showthread.p...94#post7590694](http://ubuntuforums.org/showthread.p...94#post7590694)


Thanks for the swift response. I'll have to try it from a LiveCD on his system first and return with results/updates. This time I hope it's fix and final! ;)





Sorry for the delayed post... Forgot to click "Submit Reply":P

---

### Post by Kosimo on 2009-07-21
Folks, 190.16 beta drivers released

Here the changelog: 

>     *  Added GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
          o GL_ARB_draw_buffers
          o GL_EXT_Cg_shader
          o GL_EXT_gpu_program_parameters
          o GL_NV_fragment_program
          o GL_NV_gpu_program4
          o GL_NV_register_combiners
          o GL_NV_vertex_program1_1
          o GL_NV_vertex_program2
    * Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
          o GL_ARB_geometry_shader4
          o GL_ARB_shader_objects
          o GL_ARB_texture_buffer_object
          o GL_ARB_vertex_buffer_object
          o GL_ARB_vertex_shader
          o GL_EXT_bindable_uniform
          o GL_EXT_compiled_vertex_array
          o GL_EXT_geometry_shader4
          o GL_EXT_gpu_shader4
          o GL_EXT_texture_buffer_object
          o GL_NV_geometry_program4
          o GL_NV_vertex_program
          o GL_NV_parameter_buffer_object
          o GL_NV_vertex_program4
      GLX protocol for GL_EXT_vertex_array was also updated to incorporate rendering using GL_ARB_vertex_buffer_object. Use of these extensions with GLX indirect rendering requires the AllowUnofficialGLXProtocol X configuration option and the __GL_ALLOW_UNOFFICIAL_PROTOCOL environment variable.
    * Fixed a bug that caused glXGetVideoSyncSGI, glXWaitVideoSyncSGI, and glXGetRefreshRateSGI to operate on the wrong screen when there are multiple X screens.
    * Fixed glXQueryVersion to report GLX version 1.4. NVIDIA's GLX version has been 1.4 for several releases, and was already reported as 1.4 in the GLX client and GLX server version strings.
    * Fixed a problem that caused window border corruption when the screen is rotated.
    * Fixed a bug that causes corruption or GPU errors when an application paints a redirected window whose background is set to ParentRelative on X.Org servers older than 1.5. This was typically triggered by running Kopete while using Compiz or Beryl.
    * Added support for configuring the GPU PowerMizer Mode on GeForce 8 or later GPUs with multiple performance levels via nvidia-settings and NV-CONTROL.
    * Fixed a bug in VDPAU that could cause visible corruption when decoding H.264 clips with alternating frame/field coded reference pictures, and a video surface is concurrently removed from the DPB, and re-used as the decode target, in a single decode operation. This affected all GPUs supported by VDPAU.
    * Fixed a bug in VDPAU that could cause visible corruption near the bottom edge of the picture when decoding VC-1 advanced profile clips whose heights are not exact multiples of 16 pixels, on G98 and MCP7x (IGP) GPUs.
    * Enhanced VDPAU to better handle corrupt/invalid H.264 bitstreams on G84, G86, G92, G94, G96, or GT200 GPUs. This should prevent most cases of "display preemption" that are caused by bitstream errors.
    * Fixed an X server crash when using the VDPAU overlay-based presentation queue and VT-switching away from the X server.
    * Enhanced VDPAU's detection of the GPU's video decode capabilities.
    * Fixed a bug in VDPAU that could cause ghosting/flashing issues when decoding H.264 clips, in certain full DPB scenarios, on G98 and MCP7x.
    * Fixed VDPAU to detect an attempt to destroy the VdpDevice object when other device-owned objects still exist. VDPAU now triggers "display preemption", and returns an error, when this occurs.
    * Enhanced VDPAU's error handling and resource management in presentation queue creation and operation. This change correctly propagates all errors back to the client application, and avoids some resource leaks.


Links at the first page

---

### Post by mastergunner on 2009-07-21
Where can I get the beta drivers?

---

### Post by Kosimo on 2009-07-21
> **mastergunner said:**
> Where can I get the beta drivers?

Have a look at the first page of this thread

---

### Post by 0pul3nce on 2009-07-21
"I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them"

I ABSOLUTELY HATE IT. I'm running a 64 bit system and my graphics in simple flash videos are glitchy. When i have numerous flash video's open...even with all stoped bar one...i get an unbearable stop start video. I can't TAKE IT ANYMORE. Please someone fix the problem.

---

### Post by heyyy on 2009-07-21
has anyone encountered serious problems 185 drivers
im about to install but im not sure

---

### Post by Arup on 2009-07-21
190.16 are officially availalbe with nvidia as beta, they work fine on Jaunty here.

---

### Post by Kosimo on 2009-07-22
> **Arup said:**
> 190.16 are officially availalbe with nvidia as beta, they work fine on Jaunty here.

I couldn't boot my Jaunty after installing them, so I'm back to 185 :(

---

### Post by j7%&lt;RmUg on 2009-07-22
Im using an 8500GT 512mb PCIE DDR2 card and the 180 drivers and its close to excellent in jaunty. I think im going to wait until karmic before i install the 190 drivers, the beta seems a little unstable.

---

### Post by Arup on 2009-07-22
Been running 190 since yesterday, put it through battery of tests, no surprises yet.

---

### Post by ratcheer on 2009-07-22
I am using 185 with Jaunty and 9400GT card. Everything is fine.

Tim

---

### Post by Kosimo on 2009-07-23
Just want to mention that latest 190.16 drivers are OpenGl 3.2 compatible :KS  nVidia is really pushing one step forward Linux drivers.

---

### Post by fly360 on 2009-07-23
Installed 190.16 driver IAW post #1. Using an Axle Geforce 6200A 512mb AGP, and it works like a champ on this computer.

---

### Post by drbee on 2009-07-25
Tried to download but page not found on nvidia site.  Anybody knows a mirror? Thx


EDIT: I actually found this [ftp://*download](ftp://*download)*.nvidia.com/XFree86/  with 190.18 version

---

### Post by Kosimo on 2009-07-28
190.18 Drivers has been released fixing some minor bugs:


Changes since 190.16

>     *  Fixed an initialization problem on some mobile GPUs.
    * Worked around X.Org X server Bugzilla bug #22804. This bug allows X clients to send invalid XGetImage requests to the hardware, leading to screen corruption or hangs. This was most commonly triggered by running JDownloader in KDE 4.
    * Fixed a crash in nvidia-settings displaying GPU information when in Xinerama.


---

### Post by Kosimo on 2009-07-28
nVidia have just released a new Stable Driver

185.18.29


Changelog:

> #  Added code to forcibly terminate long-running CUDA kernels when Ctrl-C is pressed.
# Fixed a bug that could cause occasional memory corruption problems or segmentation faults when running OpenGL applications on Quadro GPUs.
# Fixed a deadlock in the OpenGL library that could be triggered in certain rare circumstances on Quadro GPUs.
# Fixed an interaction problem between PowerMizer and CUDA applications that caused the performance level to be reduced while the CUDA kernel is running.
# Made CUDA compute-exclusive mode persistent across GPU resets.
# Fixed the order of outputs in the GPUScaling nvidia-settings property.
# Fixed a bug that caused graphics corruption in some OpenGL applications when the Unified Back Buffer is enabled the application window is moved.
# Fixed a bug that caused glXGetVideoSyncSGI, glXWaitVideoSyncSGI, and glXGetRefreshRateSGI to operate on the wrong screen when there are multiple X screens.
# Fixed a bug that causes corruption or GPU errors when an application paints a redirected window whose background is set to ParentRelative on X.Org servers older than 1.5. This was typically triggered by running Kopete while using Compiz or Beryl.
# Fixed a bug in VDPAU that could cause visible corruption when decoding H.264 clips with alternating frame/field coded reference pictures, and a video surface is concurrently removed from the DPB, and re-used as the decode target, in a single decode operation. This affected all GPUs supported by VDPAU.
# Fixed a bug in VDPAU that could cause visible corruption near the bottom edge of the picture when decoding VC-1 advanced profile clips whose heights are not exact multiples of 16 pixels, on G98 and MCP7x (IGP) GPUs.
# Enhanced VDPAU to better handle corrupt/invalid H.264 bitstreams on G84, G86, G92, G94, G96, or GT200 GPUs. This should prevent most cases of "display preemption" that are caused by bitstream errors.
# Fixed an X server crash when using the VDPAU overlay-based presentation queue and VT-switching away from the X server.
# Enhanced VDPAU's detection of the GPU's video decode capabilities.
# Fixed a bug in VDPAU that could cause ghosting/flashing issues when decoding H.264 clips, in certain full DPB scenarios, on G98 and MCP7x.
# Fixed VDPAU to detect an attempt to destroy the VdpDevice object when other device-owned objects still exist. VDPAU now triggers "display preemption", and returns an error, when this occurs.
# Enhanced VDPAU's error handling and resource management in presentation queue creation and operation. This change correctly propagates all errors back to the client application, and avoids some resource leaks.


Links in the first page of this thread.

---

### Post by rainwalker on 2009-07-28
> **Kosimo said:**
> nVidia have just released a new Stable Driver

185.18.29

Links in the first page of this thread.

I'd like to try this, but I'd like to confirm something first. I'm using the 185.18.14 driver at the moment, so I'd need to uninstall that first, right? Also, I thought I remembered someone posting a script somewhere in this thread that would automatically update this driver at bootup or something...I don't quite remember what, and obviously it's a lot to look through. I guess it's not a huge deal, but does a script like this ring a bell? I think it involved recompiling something automatically.

---

### Post by Kosimo on 2009-07-29
> **rainwalker said:**
> I'd like to try this, but I'd like to confirm something first. I'm using the 185.18.14 driver at the moment, so I'd need to uninstall that first, right? Also, I thought I remembered someone posting a script somewhere in this thread that would automatically update this driver at bootup or something...I don't quite remember what, and obviously it's a lot to look through. I guess it's not a huge deal, but does a script like this ring a bell? I think it involved recompiling something automatically.

If you want to install the new ones you have to uninstall the previous ones first. 

It's easy:

Get the new drivers and put them wherever you want. 

Then go to real terminal CONTROL + ALT + F1 

Turn off GDM

```
sudo /etc/init.d/gdm stop
```

and type

```
sudo nvidia-uninstall
```

now you can easily excecute the installer for the new drivers

sudo sh ./NVxxxx

---

### Post by rainwalker on 2009-07-29
> **Kosimo said:**
> If you want to install the new ones you have to uninstall the previous ones first. 

It's easy:

Get the new drivers and put them wherever you want. 

Then go to real terminal CONTROL + ALT + F1 

Turn off GDM

```
sudo /etc/init.d/gdm stop
```

and type

```
sudo nvidia-uninstall
```

now you can easily excecute the installer for the new drivers

sudo sh ./NVxxxx

Okay, thanks :)
Wow, I just re-read your first post and the script I was wondering about it mentioned there already, oops :?

---

### Post by rainwalker on 2009-07-29
Alright, so the 185.18.29 driver didn't work out. I got it installed and everything, but when I rebooted my screen would go black at the login screen. Any ideas? 185.18.14 works perfectly as far as I can tell (there may be issues that I just don't know are caused by it) but I'd still like to use newer drivers.

---

### Post by Kosimo on 2009-07-29
> **rainwalker said:**
> Alright, so the 185.18.29 driver didn't work out. I got it installed and everything, but when I rebooted my screen would go black at the login screen. Any ideas? 185.18.14 works perfectly as far as I can tell (there may be issues that I just don't know are caused by it) but I'd still like to use newer drivers.

How did you install the previous ones? Manually? 

If keeps not working why don't you give a try to the latest 190 version? I had no problems at all with them so far.

---

### Post by Sockerdrickan on 2009-07-29
OpenGL 3.2 here we go :D where are the headers already Khronos... ;)

---

### Post by devolute on 2009-07-29
The 190 beta drivers magically made my Open GL work again. The result is HL2 works again through Wine and it runs a lot faster that it used to.

Hopefully it will stop the horrid screen corruption problem I had with a 185 'stable'.

---

### Post by Buschbarber on 2009-07-29
I have an Nvidia 9800GTX+ and output from my PC using DVI to HDMI to a Sony 50" KDS50A2020 Rear Projection HDTV. I have been using the 185 drivers with UE2.3, but I suffered from Overscan. 

The easiest solution, which is a BandAid, was to enter the Service Menu, on the HDTV, and set the Overscan to Zero.

I dual boot with Windows 7 and the 185 drivers in Windows 7 have Scroll Handles that let me Resize the Display.

Do these 190 Beta drivers, for Linux, give me that option, yet?

For now, I am just losing a tad on either side and a tad on the bottom, but nothing I can't live with until there is a better solution.

The only other option is a complicated redo of my xorg.conf, using modelines, etc.

---

### Post by pcgstudio on 2009-07-29
I have a problem with it, i installed the 185....29 one and it built the kernel whilst installing, however after i restarted, i think the kernel is missing, so it loads in low graphics mode, how can i resolve this?

---

### Post by darco on 2009-07-29
> **Kosimo said:**
> If you want to install the new ones you have to uninstall the previous ones first. 

It's easy:

Get the new drivers and put them wherever you want. 

Then go to real terminal CONTROL + ALT + F1 

Turn off GDM

```
sudo /etc/init.d/gdm stop
```

and type

```
sudo nvidia-uninstall
```

now you can easily excecute the installer for the new drivers

sudo sh ./NVxxxx

I always get a little nervous when updating my drivers...this time your instructions worked fine!...it failed at first because I did not read that my gcc was incompaitable , so I said no instead of yes and all went smooth...
thxs
darco

---

### Post by Ericj1186 on 2009-07-29
> **rainwalker said:**
> Alright, so the 185.18.29 driver didn't work out. I got it installed and everything, but when I rebooted my screen would go black at the login screen. Any ideas? 185.18.14 works perfectly as far as I can tell (there may be issues that I just don't know are caused by it) but I'd still like to use newer drivers.

What card are you running?

For months, I had that issue, and I am running two GTS 250s in SLi, so the problem was eventually fixed by editing xorg.conf.  I can provide the stuff I did it fix it, but my solution is pretty limited to SLi.

With that said, I doubt I will upgrade until I experience any troubles.  It was too much of a headache to do it, and I'm not sure if there even are any new SLi driver updates.

---

### Post by rainwalker on 2009-07-29
> **Kosimo said:**
> How did you install the previous ones? Manually? 

If keeps not working why don't you give a try to the latest 190 version? I had no problems at all with them so far.

Yeah, I installed both of them manually, both using your instructions in the first post.

I might try the 190 driver, 185 is working just fine for right now though. Oh, I do have one question, though: when uninstalling the old driver before installing the new one, do I have to reboot after uninstalling? Or can I uninstall and then install the newer one without rebooting?

---

### Post by darco on 2009-07-29
No need to reboot...

d

---

### Post by rainwalker on 2009-07-30
> **darco said:**
> No need to reboot...

d

In that case, yes, the latest 185 drivers don't work for me :(

---

### Post by Buschbarber on 2009-07-30
Since this thread is about How to Install Nvidia drivers, could someone give me some feedback on my previously posted Reply to this thread?

Thanks!!!

> **Buschbarber said:**
> I have an Nvidia 9800GTX+ and output from my PC using DVI to HDMI to a Sony 50" KDS50A2020 Rear Projection HDTV. I have been using the 185 drivers with UE2.3, but I suffered from Overscan. 

The easiest solution, which is a BandAid, was to enter the Service Menu, on the HDTV, and set the Overscan to Zero.

I dual boot with Windows 7 and the 185 drivers in Windows 7 have Scroll Handles that let me Resize the Display.

Do these 190 Beta drivers, for Linux, give me that option, yet?

For now, I am just losing a tad on either side and a tad on the bottom, but nothing I can't live with until there is a better solution.

The only other option is a complicated redo of my xorg.conf, using modelines, etc.

---

### Post by sawbuck on 2009-07-31
I'm a newbie so bear with me.
 
I had a Fedora installatiion with MythTV that had a H/W crash and when I rebuilt I couldn't find the same version (Fedora 8) so - long story short - rebuilt a system with MYTHBUNTU 9.04.
 
I have an EVGA 6200 in this new system that runs Windows 7 (RC) fine but doesn't load with the mythbuntu system.  I've tried all the recommended drivers which go to 179 (I think) then spent a lot of time trying 180.06 as described in this thread, using the steps as described.  In the process it compiled a kernel for NVIDIA (that normal?) but still didn't work.  Since, I've tried the 185.29 stable set with same lack of result.
 
Is it the mythbuntu or ???  Any help appreciated...

---

### Post by Buschbarber on 2009-07-31
I do not know if this is a similar situation, but before I built my new Quad Core system, I had an HP Media Center Edition P4 system with an Nvidia Gforce 6200 card. It also had an Integrated Intel graphics adapter.

I had no problems running Windows XP MCE, XP pro, or even Windows 7, but any version of Linux would crash, even if I was booting with the LiveCD, unless I set the BIOS to Onboard (instead of PCI) and connected the monitor to the Intel adapter. It got worse when I switched to the Gforce 8400.

I still use it with Windows 7, but there must be a hardware issue that keeps me from being able to switch the BIOS to PCI and running with the Nvidia card. I spent many hours on forums like this trying to find a work around. Most suggestions were to build another PC, so I did.

---

### Post by sawbuck on 2009-07-31
> **Buschbarber said:**
> I do not know if this is a similar situation, but before I built my new Quad Core system, I had an HP Media Center Edition P4 system with an Nvidia Gforce 6200 card. It also had an Integrated Intel graphics adapter.

I had no problems running Windows XP MCE, XP pro, or even Windows 7, but any version of Linux would crash, even if I was booting with the LiveCD, unless I set the BIOS to Onboard (instead of PCI) and connected the monitor to the Intel adapter. It got worse when I switched to the Gforce 8400.

I still use it with Windows 7, but there must be a hardware issue that keeps me from being able to switch the BIOS to PCI and running with the Nvidia card. I spent many hours on forums like this trying to find a work around. Most suggestions were to build another PC, so I did.


I guess the similarity is with Nvidia 6200 PCI card.  However, poster MOOKIE60, back on May 31, '09, posted a hardware table in  the "**Please post your Functional/Non Functional Hardware" **with[B]:
(Partial list)
[/B][INDENT]Video Card:  nvidia geforce 6200

Tuners:  Hauppauge 1600 (analog & digital tuners)

Mythbuntu Version: 9.04

[/INDENT]that seemed to play acceptably.  If you read this thread, MOOKIE60, please post what drivers you used for the video card.  My setup has those 3 items.

With std VGA in linux, I am able to get functionality and video as long as it isn't graphics intensive - like a live TV show and certainly not in HD.  Since I am still setting up and experimenting I don't have a lot of data but plan to post my H/W list when I have something worthwhile to show.  I have neither cable nor dish but get great looking ASTC HD from broadcast - but VERY choppy with the std low graphic vga.  Standard DTV seems to be reasonable but I don't know any way of telling the card to convert HD to STD.

Any advice would be appreciated,  I really don't wnat to go back to Windows MCE if I can avoid it.  MYTH TV was just too comfortable....

Will keep plugging and researching a solution, for now,

---

### Post by Buschbarber on 2009-07-31
I am still asking the question regarding whether or not the 190 Nvidia drivers, for Ubuntu, allow you to Resize the Display, to compensate for Overscan? I don't want to install the 190 drivers unless there is a significant difference over the 185.18 drivers.

---

### Post by bngguy on 2009-07-31
> **pcgstudio said:**
> I have a problem with it, i installed the 185....29 one and it built the kernel whilst installing, however after i restarted, i think the kernel is missing, so it loads in low graphics mode, how can i resolve this?

Did u try uninstalling the driver, reboot and then do a fresh install???

---

### Post by coldReactive on 2009-08-01
New Stable Driver: 185.18.31

---

### Post by Kosimo on 2009-08-01
> **coldReactive said:**
> New Stable Driver: 185.18.31

Thanks for the heads up!


185.18.31 Release changelog:

> Fixed a crash on certain mobile GPUs.

Links on the first page, as always

---

### Post by ratcheer on 2009-08-01
Dern! I just installed the new 185.18.31 driver. When I rebooted, Software Manager informed me of all the kernel updates. So I installed the new kernel and rebooted. Of course, then my new video driver was gone, so I had to install it again. Whew!  Tim

---

### Post by coldReactive on 2009-08-01
> **Kosimo said:**
> Thanks for the heads up!

This time it's pkg2 though. ;)

---

### Post by Ericj1186 on 2009-08-02
[s]So, despite my early apprehension,  I went a head an updated my video card - Biggest mistake ever.

Evidently, during installation, it updated my kernel (although uname -r still yields 2.6.28-13), and now, I have no sound (as was my issue with kernel 2.6.28-13), I have no shut down or restart button under the top right power button (just suspend, logout, and hiberate), and my computer is considerably slower. 

Any way I can fix this?  I am most upset about the lack of sound.[/s]

Magically, after a second restart, the computer is fine.

How can I tell what version of the driver am I using to see if this even worked?

---

### Post by Buschbarber on 2009-08-02
Applications/System Tools/Sysinfo/Nvidia gave me the driver version in UE2.3

---

### Post by tralston on 2009-08-02
> **bngguy said:**
> Did u try uninstalling the driver, reboot and then do a fresh install???

I just (today) got the new 185.18.31 driver working. Interestingly enough, it was the first time that I didn't uninstall the **old** driver. I just thought I'd install it again. Here were my steps for the process

```
# sudo /etc/init.d/gdm stop
# sudo sh ~/Downloads/NVIDIA-Linux-x86-185.18.31-pkg1.run **-x**
# cd NVIDIA-Linux-x86-185.18.31-pkg1
# sudo ./nvidia-installer

```It did the normal license agreement, blah blah. But this time it said "oh, I see you've already installed the 185.18.31 driver. We will remove that for you before installing the new one..." (even though it was the same version....). But I'm glad the installer did, because it put a fresh new one on. I did run into some errors and it said stuff about rolling back the changes and uninstalling the new driver I just put on. I said OK, because I didn't have a choice. Then I did,

```
# sudo /etc/init.d/gdm start
```and then, are you ready for the magic command that changed my life?

```
# nvidia-xconfig
```I had never done that before. Now I found the 1920x1200 resolution listed in both nVidia's display manager and the native Ubuntu display manager. I relogged in a few times just to test if the settings stuck. If you do change the resolution, use the native display manager, or the settings won't be permanent next time you log in. Woohoo, I love my beautiful native resolution! :KS

---

### Post by rainwalker on 2009-08-02
> **tralston said:**
> I just (today) got the new 185.18.31 driver working. Interestingly enough, it was the first time that I didn't uninstall the **old** driver. I just thought I'd install it again. Here were my steps for the process

```
# sudo /etc/init.d/gdm stop
# sudo sh ~/Downloads/NVIDIA-Linux-x86-185.18.31-pkg1.run **-x**
# cd NVIDIA-Linux-x86-185.18.31-pkg1
# sudo ./nvidia-installer

```It did the normal license agreement, blah blah. But this time it said "oh, I see you've already installed the 185.18.31 driver. We will remove that for you before installing the new one..." (even though it was the same version....). But I'm glad the installer did, because it put a fresh new one on. I did run into some errors and it said stuff about rolling back the changes and uninstalling the new driver I just put on. I said OK, because I didn't have a choice. Then I did,

```
# sudo /etc/init.d/gdm start
```and then, are you ready for the magic command that changed my life?

```
# nvidia-xconfig
```I had never done that before. Now I found the 1920x1200 resolution listed in both nVidia's display manager and the native Ubuntu display manager. I relogged in a few times just to test if the settings stuck. If you do change the resolution, use the native display manager, or the settings won't be permanent next time you log in. Woohoo, I love my beautiful native resolution! :KS

What does the "-x" do?
I, again, had no luck with the latest 185 driver. I uninstalled the 185.18.14 one and then ran the installer for the 185.18.31 driver and got no errors, yet my screen still blacks out after usplash.

---

### Post by darco on 2009-08-02
I know awhile back when I was having the black screen issue, it was that the new xorg.conf was being dumped into the /root folder rather than the x11 folder. I just moved it over and all was well.
good luck

darco

---

### Post by tralston on 2009-08-02
> **rainwalker said:**
> What does the "-x" do?
I, again, had no luck with the latest 185 driver. I uninstalled the 185.18.14 one and then ran the installer for the 185.18.31 driver and got no errors, yet my screen still blacks out after usplash.

The -x term (as far as I know) outputs the contents of the .run package to a subdirectory of where you're executing the **sh **command. Go into that directory and you'll see the different folders and the **nvidia-installer** script. It's just a little easier to work with the package once it's "extracted", just in case you need to look at the source really quick or something.

darco's right. Check to see if your **xorg.conf** file is located in /etc/X11 where it's supposed to be. If not, look in your root folder. Again, I emphasize that my xorg.conf file didn't really do me that much good until I ran the **nvidia-xconfig** command, which customizes that config file especially for your nvidia card's settings. Good luck.

---

### Post by tralston on 2009-08-02
And apparently, my bean count is still 0 even though i just posted three times....:popcorn:

---

### Post by darco on 2009-08-02
> **tralston said:**
> And apparently, my bean count is still 0 even though i just posted three times....:popcorn:

Beans arent counted when you post in the Community forums

darco

---

### Post by rainwalker on 2009-08-02
Alright, let me see if I'm understanding you correctly;

1. Uninstall the old driver (or not, because apparently it will see that it's installed?)
2. Install the new driver like I did before. During the process it asks if it should automatically run the nvidia-xconfig utility, and I say yes
3. Once finished, instead of rebooting, check that the xorg file is in /etc/X11, and if not, copy it from the root folder

I have these three questions:
1. Is there a specific xorg file to look for in /etc/X11, or will it be the usual "xorg.conf" filename?
2. If there's no xorg file there, what exactly is the "/root" directory? If I had to guess, I would assume that's the lowest filesystem directory, the one with my home folder and everything in it, right? At the moment there is a file called "xorg.conf.new" in that directory, but I haven't compared it to my current one and it's from all the way back on June 20.
3. Should I run the "nvidia-xconfig" command after the driver has finished installing before I check if the xorg file is in /etc/X11?

---

### Post by darco on 2009-08-02
Bingo!   xorg.conf.new!!!!.....
Boot your machine, go into recovery and rename the .new to xorg.conf and then move it to the x11 folder...

darco

---

### Post by rainwalker on 2009-08-02
> **darco said:**
> Bingo!   xorg.conf.new!!!!.....
Boot your machine, go into recovery and rename the .new to xorg.conf and then move it to the x11 folder...

darco

That xorg.conf.new file is from June 20, I'm guessing a new one will be made if I install the 185.18.31 driver? I didn't have this black screen problem till 185.18.29, which I know I tried later than June 20, which would mean that file was probably created when I installed the 185.18.14 driver waaayyy back.

---

### Post by darco on 2009-08-02
I do not know the consequences if you were to move that xorg file to the x11 folder if it wasnt generated by the latest driver...
A few post above Kosimo posted how to uninstall and install new driver, it worked perfectly for me...rename the xorg.old.new, and see if the new install dumps another one in the root folder.

darco

---

### Post by rainwalker on 2009-08-02
> **darco said:**
> I do not know the consequences if you were to move that xorg file to the x11 folder if it wasnt generated by the latest driver...
A few post above Kosimo posted how to uninstall and install new driver, it worked perfectly for me...rename the xorg.old.new, and see if the new install dumps another one in the root folder.

darco

Well I re-did things twice, with no success. The first time I uninstalled the driver, then installed the new one, then checked to see if there was an "xorg.conf" anywhere other than in /etc/X11 and there wasn't. I even ran "nvidia-xconfig" to see if it mattered if I ran it a second time and it put the "xorg.conf" file in the right place.
The second time, after reinstalling the 185.18.14 driver, I didn't uninstall it and instead let the installer for the 185.18.31 driver do it, which didn't seem to make a difference. I also tried to start gdm again before running "nvidia-xconfig" again like tralston did, but of course starting gdm blacked-out my screen.
Long story short: Something changed between the 185.18.14 driver and the 185.18.29 driver that broke compatibility with my card, a Quadro FX 3700 (a pretty new card).

---

### Post by bngguy on 2009-08-03
Hello All,
           I just installed the latest nvidia driver (185.18.31)for my GEForce Go 7400 graphic card, whenever i attempt to launch an application by clicking on the shortcut placed on the top panel, the Desktop kinda jumps and the window crashes, does anybody know how to fix this, also before i installed this driver i uninstalled compiz-fusion completely.I look forward to your replies.

---

### Post by Ericj1186 on 2009-08-03
Uhh... ignore this.

---

### Post by Kosimo on 2009-08-03
190.18.03 OpenGL 3.2 Has finally been released!

Changelog since 190.18

>     *  Support for OpenGL 3.2 on certain GPUs. Please see the driver download page for a list of GPUs that support OpenGL 3.2.



Links @ the first page.

---

### Post by Kosimo on 2009-08-03
Here the Khronos Press release for OpenGL 3.2 (now totally supported by NVIDIA-Linux users ;)


[http://www.khronos.org/news/press/releases/khronos-releases-opengl-3.2-third-major-opengl-release-within-twelve-months/](http://www.khronos.org/news/press/releases/khronos-releases-opengl-3.2-third-major-opengl-release-within-twelve-months/)

---

### Post by darco on 2009-08-03
Updated!!!...
I'm losing my fear on updating drivers..went smooth as silk
Now to see if these drivers are worth it...

darco

---

### Post by Kosimo on 2009-08-03
> **darco said:**
> Updated!!!...
I'm losing my fear on updating drivers..went smooth as silk
Now to see if these drivers are worth it...

darco

Welcome to the often-drivers-updaters family ;)

---

### Post by NightwishFan on 2009-08-04
Perhaps I should post this in another thread but it seems relevant enough. OpenGL 3.2 should only be available for compliant applications correct? So it will be used in future releases of OpenGL applications, and the later Nvidia driver will include support for it. Or am I wrong, in that case what is going on with it?

---

### Post by Kosimo on 2009-08-05
Another news that shows how seriously is nVidia taking the development of Linux drivers


From Phoronix.com


**NVIDIA Shows Linux Compatible Ray-Tracing Engine**

> Yesterday there was the major announcement of the OpenGL 3.2 release, but the news coming out of today from New Orleans during SIGGRAPH is OptiX, which comes from the folks at NVIDIA. OptiX is a ray-tracing engine developed by NVIDIA to run on Quadro FX graphics cards and uses their CUDA architecture. Later on this year NVIDIA will then release an interactive ray-trace renderer that uses OptiX within their SceniX engine.

Information on the NVIDIA OptiX Application Acceleration Engine is available at NVIDIA.com. NVIDIA also lists four ray-tracing engine examples and do mention Linux for them, but the links are not currently available. These ray-tracing demos will still require Quadro FX hardware and also a NVIDIA 190.xx driver release or newer.

On the developer page they mention that the NVIDIA OptiX engine is Linux x86 compatible.

---

### Post by Sockerdrickan on 2009-08-05
> **Kosimo said:**
> 190.18.03 OpenGL 3.2 Has finally been released!

Changelog since 190.18




Links @ the first page.
what do you mean by "finally"? It was in like 5 months.

---

### Post by Kosimo on 2009-08-05
> **Tux0r said:**
> what do you mean by "finally"? It was in like 5 months.

It wasn't "officially" released.

---

### Post by Buschbarber on 2009-08-05
It is still in Beta on the Nvidia web site.

---

### Post by Sockerdrickan on 2009-08-05
> **Kosimo said:**
> It wasn't "officially" released.
I thought you were referring to OpenGL 3.2

---

### Post by Hells_Dark on 2009-08-05
> **Buschbarber said:**
> It is still in Beta on the Nvidia web site.

Yes, but it's officially a beta release ;)

---

### Post by Askar450 on 2009-08-07
Hello, My wine has been crashing alot for some odd reason I get a

=>0 0x7d58f5f8 in libglcore.so.1 (+0x8ba5f8) (0x7c5cdd74)

In the Ubuntu forum they told me this is a driver issue that either it wasn't installed properly or there's a file conflicting with something I know this is off with the treads topic but anyone know how to correctly install the drivers? I've tried both 185.xx and 190.xx drivers and get the same error.

---

### Post by Askar450 on 2009-08-07
Not Ubuntu forum I meant WineHQ forum.

---

### Post by Kosimo on 2009-08-07
> **Askar450 said:**
> Hello, My wine has been crashing alot for some odd reason I get a

=>0 0x7d58f5f8 in libglcore.so.1 (+0x8ba5f8) (0x7c5cdd74)

In the Ubuntu forum they told me this is a driver issue that either it wasn't installed properly or there's a file conflicting with something I know this is off with the treads topic but anyone know how to correctly install the drivers? I've tried both 185.xx and 190.xx drivers and get the same error.

How did you install the driver? What is your graphics card?

---

### Post by NightwishFan on 2009-08-07
You can try disabling OpenGL related settings in the wine registry. (such as UseGLSL)

Here is a link on how, some values actually need to be created before they can be changed.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Utsukushii Tsubasa on 2009-08-07
alright, i got the driver to install properly, but when i went to update, and went to reboot, it said there was an error, and could not display properly, so i ran the recovery mode and fixed graphical issues, and it turned back to the 800x600 resolution and will not allow me to run the Nvidia config client. im not sure wich update is causing this, but i need help. anyone?

---

### Post by Askar450 on 2009-08-08
For NightwishFan and Kosimo I have a NVIDIA GeForce 8800M GTS (notebook card) and I installed them the manual way, the whole gdm + stop, sh NVIDIA-xxx and let it do roll on its own.

---

### Post by Askar450 on 2009-08-08
I've disabled GLSL and OpenGL but the problem is that If I switch OpenGL to like pbuffer or backbuffer anything with wine is choopy, GLSL disabled = missing parts on game/character.

---

### Post by Jonathan_m84 on 2009-08-08
I just installed the x86_64.185.18.31 drivers and when i reboot i get the error, linux running in low-resolution... he doesnt detect the drivers or something... i installed the drivers by clicking yes on every question, because im not an expert... 

i had the 180 installed with the envyng program.. which work perfectly btw (maybe updating to 185 is unnessecary?)

any help please? is there something with the opengl or so that i should now?

i have an acer 5738 laptop with t6400 duo core and Nvidia GeForce G105M  videocart..

---

### Post by Jonathan_m84 on 2009-08-08
When i install drivers and do a reboot i get the following error:

"failed to initialize the NVIDIA kernel module ........ screen(0) found, but none have a usable configuration.. "

---

### Post by Askar450 on 2009-08-08
I don't know this is the same or not but I was told that before updating your drivers you need to first sudo apt-get install build-essential linux-headers-`uname -r`
then remove the current drivers by sudo sh NVIDIA-xxx.run --uninstall, it will tell you it will do its best to uninstall the drivers. Go ahead and press ctrl+alt+F1 and log in, once that is done type sudo /etc/init.d/gdm stop now just do the samething you did before and they should work.

---

### Post by NightwishFan on 2009-08-08
I successfully installed the driver without build essential. I found that to be very odd, is it possible without it? (I am just curious, I usually use debs anyway but I tested the Nvidia sh installer.)

---

### Post by ratcheer on 2009-08-08
> **Askar450 said:**
> For NightwishFan and Kosimo I have a NVIDIA GeForce 8800M GTS (notebook card) and I installed them the manual way, the whole gdm + stop, sh NVIDIA-xxx and let it do roll on its own.

I have found that way to be reliable. It may not be the easiest way, but so far, it has always worked.

Tim

---

### Post by Jonathan_m84 on 2009-08-08
> **Askar450 said:**
> I don't know this is the same or not but I was told that before updating your drivers you need to first sudo apt-get install build-essential linux-headers-`uname -r`
then remove the current drivers by sudo sh NVIDIA-xxx.run --uninstall, it will tell you it will do its best to uninstall the drivers. Go ahead and press ctrl+alt+F1 and log in, once that is done type sudo /etc/init.d/gdm stop now just do the samething you did before and they should work.

I have the latest linux headers, now my question is, how do I uninstall the current drivers, because I dont have the NVIDIA-xxx.run file for the current drivers, since I installed them using envyNG...

some help? :)

edit: can I just open my synoptics package manager and uninstall everything with nvidia in it??

---

### Post by Jonathan_m84 on 2009-08-08
> **Jonathan_m84 said:**
> 
edit: can I just open my synoptics package manager and uninstall everything with nvidia in it??

I did the following:

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove

 and then reinstalled the drivers with some weird errors I ignored and thought now it's all wrong, but then rebooted and it finally works :)

---

### Post by Askar450 on 2009-08-08
So does anyone have a solution to my problem? I've already got workarounds for it but they don't fix my problem. My really question is what is "libglcore.so.1" and this output mean.

Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7d3195f8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d3195f8 ESP:0033e214 EBP:7c487d74 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7beb0990 ECX:000000ad EDX:00000000
 ESI:00000000 EDI:00000000

then I get 

Backtrace:
=>0 0x7d3195f8 in libglcore.so.1 (+0x8ba5f8) (0x7c487d74)
  1 0x00000405 (0x00000000)

---

### Post by molder on 2009-08-11
Trouble Trouble.  I installed the nvidia binary NVIDIA-Linux-x86-185.18.14-pkg1 it worked so great when NVIDIA-Linux-x86-185.18.29-pkg1 came I was estastic to upgrade.  After a day or two use I got white snow dots all over my display.  I blamed the new driver.  So I uninstalled the newsest driver and reinstalled the older NVIDIA-Linux-x86-185.18.1-pkg1.  After a couple of days I noticed that xorg was consuming quite of bit of resources and not allowing me to watch HD programing.  I took it upon my to added Avenard's testing repository and try to install his version of the NVIDIA 185 drivers and now I have no playback and no I idea on what I have do to maybe take a course of remedying my beloved mythbox.  I have trying using apt pinning to revert to the Ubuntu version but it doesn't seem to work.


```
  nvidia-glx-190: Depends: nvidia-190-libvdpau (>= 190.18) but it is not going to be installed
```

---

### Post by vbundi on 2009-08-12
> **Jonathan_m84 said:**
> When i install drivers and do a reboot i get the following error:

"failed to initialize the NVIDIA kernel module ........ screen(0) found, but none have a usable configuration.. "

I also had that problem and fixed it the same way...
Remove the drivers that were previously installed BEFORE trying to install the new driver.

apt-get remove nvidia-180-****.... (there were 4 or 5 packages likes this)

After installing the 190.18 driver, I notice that the tearing I was getting after using mplayer compiled with VDPAU support was GONE!!

Also, 3D performance of compiz is improved.

Seems as though they fixed all their issues fairly quickly.

Everything seems to be running perfectly, running 9800GT gpu.

---

### Post by ricardo_78 on 2009-08-12
What are you running.. I am having a few probs with the 180 Drivers, therefore tempted to upgrade to 190.18 beta...

---

### Post by molder on 2009-08-12
I used sudo apt-get remove nvidia-glx-* and about 4 programs were uninstalled.  I rebooted and then installed nvidia-glx-190.  During the removal MythTV was also remove (just the program not my settings) so no big deal I can reinstall.  But I can because now I have unresolved dependency issues with the 190.14 NVidia driver installed.  So reinstall nvidia-glx-180.  Now MythTV will not play videos.  When I try to upgrade I get this message:
```

The following packages have unmet dependencies:
  nvidia-glx-185: Depends: nvidia-185-libvdpau (>= 185.18.14) but it is not going to be installed
E: Broken packages
```

---

### Post by vreemde eend on 2009-08-19
> **rainwalker said:**
> Well I re-did things twice, with no success. The first time I uninstalled the driver, then installed the new one, then checked to see if there was an "xorg.conf" anywhere other than in /etc/X11 and there wasn't. I even ran "nvidia-xconfig" to see if it mattered if I ran it a second time and it put the "xorg.conf" file in the right place.
The second time, after reinstalling the 185.18.14 driver, I didn't uninstall it and instead let the installer for the 185.18.31 driver do it, which didn't seem to make a difference. I also tried to start gdm again before running "nvidia-xconfig" again like tralston did, but of course starting gdm blacked-out my screen.
Long story short: Something changed between the 185.18.14 driver and the 185.18.29 driver that broke compatibility with my card, a Quadro FX 3700 (a pretty new card).

I've got the same problem. Tried several things, but reverted to the old driver for now. (Quadro NVS 140M)

---

### Post by rainwalker on 2009-08-19
> **vreemde eend said:**
> I've got the same problem. Tried several things, but reverted to the old driver for now. (Quadro NVS 140M)

What driver are you using? I'm wondering if it's something with drivers newer than 185.18.14 that messes up with Quadro cards...
Is anyone else using the newer drivers successfully with a Quadro?

---

### Post by vreemde eend on 2009-08-21
> **rainwalker said:**
> What driver are you using? I'm wondering if it's something with drivers newer than 185.18.14 that messes up with Quadro cards...
Is anyone else using the newer drivers successfully with a Quadro?

I'm using the 185.18.14 driver.

---

### Post by Buschbarber on 2009-08-21
I just switched to the 185.18.31, from 185.18.14, when the latest Ubuntu Updates included a Kernel update that killed X on my system.

I have a 9800GTX+

---

### Post by tidewatcher on 2009-08-21
NVIDIA-Linux-x86-185.18.31 doesn't work. It simply turns off the light and hangs. No error messages or anything suspicious in the logs. Reverting to the ubuntu-packaged nvidia-glx-180, which works but crashes several times every day.

Quadro FX 360M (rev a1) in Dell Precision m4300

---

### Post by rainwalker on 2009-08-21
> **Buschbarber said:**
> I just switched to the 185.18.31, from 185.18.14, when the latest Ubuntu Updates included a Kernel update that killed X on my system.

I have a 9800GTX+

You need to recompile the driver, or see the auto-recompile script in the first post of the thread

> **tidewatcher said:**
> NVIDIA-Linux-x86-185.18.31 doesn't work. It simply turns off the light and hangs. No error messages or anything suspicious in the logs. Reverting to the ubuntu-packaged nvidia-glx-180, which works but crashes several times every day.

Quadro FX 360M (rev a1) in Dell Precision m4300

I guess the newer drivers do have issues with Quadro cards :?

---

### Post by tidewatcher on 2009-08-23
> **rainwalker said:**
> 
I guess the newer drivers do have issues with Quadro cards :?

A funny bunch of user names here :)

The *newest* driver (190) doesn't seem to have issues with these cards any longer. They are not even mentioned among the supported ones. My machine is only 1.5 years old; I guess that's too five minutes ago for Nvidia, or otherwise Dell purchased the already obsolete scraps.

Correction to my previous post: I was finally able to install the driver package from a ppa yesterday and it hasn't failed so far. I forgot to mention that it was Nvidia's own shell-based installation, NVIDIA-Linux-x86-185.18.31-pkg1.run, that gave me a dead Xorg. Here's the one that is working:

```
apt-cache policy nvidia-glx-180
nvidia-glx-180:
  Installed: 185.18.14-0ubuntu1
  Candidate: 185.18.14-0ubuntu1
  Version table:
 *** 185.18.14-0ubuntu1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
        100 /var/lib/dpkg/status
     180.44-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
```

The reason I didn't try it first was because I probably didn't see it in my apt sources. It's name tag is confusing: it is listed as nvidia-glx-180, but its version is 185.18.14-0ubuntu1.

So now I don't know whether success or failure is determined by the difference in the minor version (18.14 vs. 18.31), or because Nvidia's installer did something weird. I guess the easiest way to find out is to sit and wait.

So, 180.18.14-0ubuntu1 seems to work on my 360M, if one day is long enough for a test. I'll make noise if it fails.

---

### Post by rainwalker on 2009-08-23
> **tidewatcher said:**
> A funny bunch of user names here :)

The *newest* driver (190) doesn't seem to have issues with these cards any longer. They are not even mentioned among the supported ones. My machine is only 1.5 years old; I guess that's too five minutes ago for Nvidia, or otherwise Dell purchased the already obsolete scraps.

Correction to my previous post: I was finally able to install the driver package from a ppa yesterday and it hasn't failed so far. I forgot to mention that it was Nvidia's own shell-based installation, NVIDIA-Linux-x86-185.18.31-pkg1.run, that gave me a dead Xorg. Here's the one that is working:

```
apt-cache policy nvidia-glx-180
nvidia-glx-180:
  Installed: 185.18.14-0ubuntu1
  Candidate: 185.18.14-0ubuntu1
  Version table:
 *** 185.18.14-0ubuntu1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
        100 /var/lib/dpkg/status
     180.44-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
```

The reason I didn't try it first was because I probably didn't see it in my apt sources. It's name tag is confusing: it is listed as nvidia-glx-180, but its version is 185.18.14-0ubuntu1.

So now I don't know whether success or failure is determined by the difference in the minor version (18.14 vs. 18.31), or because Nvidia's installer did something weird. I guess the easiest way to find out is to sit and wait.

So, 180.18.14-0ubuntu1 seems to work on my 360M, if one day is long enough for a test. I'll make noise if it fails.

185.18.14 is two versions older than the newest, 185.18.31, and is the version I'm using as well (compiled with Nvidia's .run package). 185.18.29 and 185.18.31 are the two newer versions that I've had no success with, but I haven't tried any of the 190.xx drivers.

---

### Post by crjackson on 2009-08-23
New Driver Today...

---

### Post by Kosimo on 2009-08-25
> **crjackson said:**
> New Driver Today...

Thanks for the heads up.

Links at the first page

---

### Post by Kosimo on 2009-08-25
190.25 changelog:


>     *  Added code to reject screen modes based on available DisplayPort link bandwidth. Fixes display corruption caused by allowing high bandwidth modes on display devices that can't handle them, such as certain DisplayPort-to-VGA adapters that only support 2 DisplayPort lanes.
    * Fixed an initialization problem on some mobile GPUs.
    * Worked around X.Org X server Bugzilla bug #22804. This bug allows X clients to send invalid XGetImage requests to the hardware, leading to screen corruption or hangs. This was most commonly triggered by running JDownloader in KDE 4.
    * Fixed a crash in nvidia-settings displaying GPU information when in Xinerama.


---

### Post by Buschbarber on 2009-08-25
I just went to the Nvidia site and even the Beta drivers, for Linux, have not been released for 190.25. Where did you get yours?

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by Kosimo on 2009-08-25
> **Buschbarber said:**
> I just went to the Nvidia site and even the Beta drivers, for Linux, have not been released for 190.25. Where did you get yours?

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

You'll find the links in the first page of this thread.

---

### Post by Wheelgunner on 2009-09-02
Hello,

I'm new to Ubuntu and have a problem. The screen flashes black for a few tenths of a seconds at random intervals. In an archived thread I read that this may have something to do with the nVidia drivers, but there was no solutions yet at that time.

I'm running the 180 version of the nVidia driver that had the label recommended, my card is a GeForce Go 7300 in a Toshiba Satellite A200.

Is this a familiar problem? Is there a fix by now?

---

### Post by NightwishFan on 2009-09-02
> **Wheelgunner said:**
> Hello,

I'm new to Ubuntu and have a problem. The screen flashes black for a few tenths of a seconds at random intervals. In an archived thread I read that this may have something to do with the nVidia drivers, but there was no solutions yet at that time.

I'm running the 180 version of the nVidia driver that had the label recommended, my card is a GeForce Go 7300 in a Toshiba Satellite A200.

Is this a familiar problem? Is there a fix by now?

You should probably start a new thread related to this issue. Create a similar post there and ask for assistance.

---

### Post by Kosimo on 2009-09-04
Guys, nVidia have just published a new beta version:

**190.32**


Changelog:

>     *  Added support for IgnoreEDIDChecksum X configuration option, which can be used to force the X driver to accept the EDID of a display device even when the checksum is invalid. Please see the README IgnoreEDIDChecksum description for a caution and details of use.
    * Added support for configuring the GPU's fan speed; see the "Coolbits" X configuration option in the README.
    * Fixed a bug in VDPAU that could cause visible corruption near the bottom edge of the picture when decoding VC-1 simple/main profile clips whose heights are not exact multiples of 16 pixels, on GPUs with VDPAU feature set A.
    * On GPUs with VDPAU feature set C, VDPAU now supports decoding MPEG-4 Part 2, DivX 4, and DivX 5 video. The VDPAU API has been enhanced to expose this feature.
    * On GPUs with VDPAU feature set C, VDPAU now supports a higher quality video scaling algorithm. The VDPAU API has been enhanced to expose this feature.



Links in the first page of this thread

---

### Post by darco on 2009-09-04
heh..I JUST install .25 ....oh well
thxs

darco

---

### Post by Kosimo on 2009-09-04
> **darco said:**
> heh..I JUST install .25 ....oh well
thxs

darco

Come on, I'm sure you enjoy compiling your own drivers ;)


What I can say is that I've been testing the latest 190.35 and so far so good :KS  I couldn't run any test like phoronix test, but I will if I can.

Something bad I can say about this drivers is that they still lack full support for the upcomming 2.6.31 kernel, but they still work.

---

### Post by nyonet on 2009-09-09
Where can I see if the geforce gt 130m is compatible with this last beta driver?

thanks

edit: yes..it's compatible...i've installed it, and i can see video, but no sound.... continue working :p

---

### Post by demeter on 2009-09-11
hi there, I followed the how to on installing the driver for my Riva TNT2 graphic card and all that was lacking during the installation was that x.org automatic configuration step. Also during the process it said that it had to build a kernel, after the installation process it said something about the x.org config file (cant really understand what does it mean:(),anyway, rebooted the system and no changes whatsoever, i mean the drivers arent present in the hardware driver list and still cant change my screen resolution...any help would be greatly appreciated....thanks...

---

### Post by nikio on 2009-09-13
Little problem here: I can't even download  the file!
I've tried the both 185 and the 190 download but with no success.
When I come to the download page and click the "Agree & Download" button, a smaller window appears, offering "Cancel" and "Save File" if I click on Save nothing happens :confused:
Does someone know if there is an other way to download the file (or how to fix firefox, of course :D)?

---

### Post by Mi*6d@# on 2009-09-13
Thank you very much for this guide! Last time I tried to install drivers manually it ended up in Ubuntu reinstallation...

---

### Post by Old Marcus on 2009-09-13
> **nikio said:**
> Little problem here: I can't even download  the file!
I've tried the both 185 and the 190 download but with no success.
When I come to the download page and click the "Agree & Download" button, a smaller window appears, offering "Cancel" and "Save File" if I click on Save nothing happens :confused:
Does someone know if there is an other way to download the file (or how to fix firefox, of course :D)?
Right click, Save file as?

---

### Post by Skip Da Shu on 2009-09-22
> **mips said:**
> Do you actually use CUDA? I do not think there is more than 0.01% in this forum that would use CUDA.

CUDA is a C language environment/compiler to program GPUs to in effect perform the functions of a CPU.

[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

Required for BOINC GPUgrid and other CUDA based GPU number crunching.

---

### Post by Skip Da Shu on 2009-09-22
One of the BOINC projects (GPUgrid) has upgraded their applications to use Cuda v2.2 which will require all the Linux crunchers to upgrade to 185.xx drivers.  

Suspect you'll see some increase in activity around this.

I tried last night but get the 'low-res' message at reboot.  Will go thru it again using 1st post instructions.  IF I remember you said to un-enable the existing 180.44 driver first... how would u recommend doing that prior to running the Nvidia .run installer?

I'll post the Nvidia kernel errors if I get it again.

Kernel 2.6.28, 64b Jaunty

---

### Post by Skip Da Shu on 2009-09-22
After disabling the 180.44 driver and running the 185-...pkg2.run install:

```
Sep 22 17:15:48 c17-desktop avahi-daemon[3321]: Server startup complete. Host name is c17-desktop.local. Local service cookie is 2274955198.
Sep 22 17:15:48 c17-desktop kernel: [   17.607019] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 22 17:15:48 c17-desktop kernel: [   17.607026] nvidia 0000:01:00.0: setting latency timer to 64
Sep 22 17:15:48 c17-desktop kernel: [   17.607169] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Sep 22 17:15:48 c17-desktop anacron[3448]: Normal exit (0 jobs run)
Sep 22 17:15:48 c17-desktop /usr/sbin/cron[3492]: (CRON) INFO (pidfile fd = 3)
Sep 22 17:15:48 c17-desktop /usr/sbin/cron[3493]: (CRON) STARTUP (fork ok)
Sep 22 17:15:48 c17-desktop kernel: [   17.695658] NVRM: API mismatch: the client has the version 185.18.36, but
Sep 22 17:15:48 c17-desktop kernel: [   17.695659] NVRM: this kernel module has the version 180.44.  Please
Sep 22 17:15:48 c17-desktop kernel: [   17.695659] NVRM: make sure that this kernel module and all NVIDIA driver
Sep 22 17:15:48 c17-desktop kernel: [   17.695660] NVRM: components have the same version.
Sep 22 17:15:48 c17-desktop /usr/sbin/cron[3493]: (CRON) INFO (Running @reboot jobs)
Sep 22 17:15:49 c17-desktop kernel: [   18.315167] NVRM: API mismatch: the client has the version 185.18.36, but
Sep 22 17:15:49 c17-desktop kernel: [   18.315168] NVRM: this kernel module has the version 180.44.  Please
Sep 22 17:15:49 c17-desktop kernel: [   18.315168] NVRM: make sure that this kernel module and all NVIDIA driver
Sep 22 17:15:49 c17-desktop kernel: [   18.315169] NVRM: components have the same version.
Sep 22 17:15:51 c17-desktop acpid: client 3182[0:0] has disconnected 
Sep 22 17:15:51 c17-desktop acpid: client connected from 3570[0:0] 
Sep 22 17:15:51 c17-desktop kernel: [   20.786084] NVRM: API mismatch: the client has the version 185.18.36, but
Sep 22 17:15:51 c17-desktop kernel: [   20.786085] NVRM: this kernel module has the version 180.44.  Please
Sep 22 17:15:51 c17-desktop kernel: [   20.786086] NVRM: make sure that this kernel module and all NVIDIA driver
Sep 22 17:15:51 c17-desktop kernel: [   20.786086] NVRM: components have the same version.
Sep 22 17:15:51 c17-desktop ntpdate[3259]: adjust time server 206.212.242.132 offset -0.213516 sec
Sep 22 17:15:51 c17-desktop ntpd[3609]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:10:45 UTC 2009 (1)
Sep 22 17:15:51 c17-desktop ntpd[3610]: precision = 1.000 usec
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #1 wildcard, ::#123 Disabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #2 lo, ::1#123 Enabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #3 eth1, fe80::21f:d0ff:fed4:8037#123 Enabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: Listening on interface #5 eth1, 192.168.218.17#123 Enabled
Sep 22 17:15:51 c17-desktop ntpd[3610]: kernel time sync status 0040
Sep 22 17:15:51 c17-desktop ntpd[3610]: frequency initialized -27.498 PPM from /var/lib/ntp/ntp.drift
Sep 22 17:15:53 c17-desktop kernel: [   22.977509] eth1: no IPv6 routers present
Sep 22 17:15:54 c17-desktop acpid: client 3570[0:0] has disconnected 
Sep 22 17:15:54 c17-desktop acpid: client connected from 3614[0:0] 
Sep 22 17:15:54 c17-desktop kernel: [   23.879093] NVRM: API mismatch: the client has the version 185.18.36, but
Sep 22 17:15:54 c17-desktop kernel: [   23.879094] NVRM: this kernel module has the version 180.44.  Please
Sep 22 17:15:54 c17-desktop kernel: [   23.879094] NVRM: make sure that this kernel module and all NVIDIA driver
Sep 22 17:15:54 c17-desktop kernel: [   23.879095] NVRM: components have the same version.
Sep 22 17:15:54 c17-desktop gdm[3174]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Sep 22 17:15:57 c17-desktop acpid: client 3614[0:0] has disconnected 
Sep 22 17:15:57 c17-desktop acpid: client connected from 3670[0:0] 
Sep 22 17:16:03 c17-desktop kernel: [   32.713652] mtrr: base(0xe5000000) is not aligned on a size(0xe00000) boundary
Sep 22 17:16:57 c17-desktop console-kit-daemon[2947]: WARNING: Couldn't read /proc/2946/environ: Failed to open file '/proc/2946/environ': No such file or directory 
Sep 22 17:17:01 c17-desktop /USR/SBIN/CRON[3900]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 22 17:17:33 c17-desktop init: tty4 main process (2547) killed by TERM signal
Sep 22 17:17:33 c17-desktop init: tty5 main process (2548) killed by TERM signal
Sep 22 17:17:33 c17-desktop init: tty1 main process (3557) killed by TERM signal
Sep 22 17:17:33 c17-desktop init: tty2 main process (2551) killed by TERM signal
Sep 22 17:17:33 c17-desktop init: tty3 main process (2553) killed by TERM signal
Sep 22 17:17:33 c17-desktop init: tty6 main process (2555) killed by TERM signal
Sep 22 17:17:33 c17-desktop console-kit-daemon[2947]: WARNING: Unable to activate console: No such device or address 
Sep 22 17:17:52 c17-desktop exiting on signal 15
```

After running the --uninstall

```
Sep 22 17:20:44 c17-desktop kernel: [   10.570330] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 22 17:20:44 c17-desktop kernel: [   10.570336] nvidia 0000:01:00.0: setting latency timer to 64
Sep 22 17:20:44 c17-desktop kernel: [   10.570560] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
```

Obviously I'm still loading 180.44 someplace.  Any suggestions as to what step I missed?  Any chance that I need to update GRUB to point to a different kernel after doing this?

PS:  Oh looks like **my bad**... It does say disable existing kernel, then restart, then start the install... I'm not SURE I did that... lemme try again.
PPS:  Yup, It was the disable the 180.44 THEN RESTART before starting the nvidia install (have 190.32 running now).

---

### Post by Kosimo on 2009-09-25
New Beta release:

190.36  

Changelog:

>     *  Added support for X.Org xserver 1.6.99.901 (also known as 1.7 RC1) and 1.6.99.902 (1.7 RC2).
    * Add a new OverscanCompensation NV-CONTROL attribute, available on GeForce 8 and higher. This option specifies the amount of overscan compensation to apply to the current mode. It is measured in raster pixels, i.e. pixels as specified in the current mode's backend timings.
    * Updated nvidia-installer to detect newer Debian distributions that use /usr/lib32 instead of /emul/ia32-linux as the 32-bit library path.


---

### Post by Arup on 2009-09-25
On it right now since six hours, no crashes, have watched vdpau movies full screen, played some Tux Racer, absolutely no issues.

---

### Post by Kosimo on 2009-09-25
> **Arup said:**
> On it right now since six hours, no crashes, have watched vdpau movies full screen, played some Tux Racer, absolutely no issues.

Which drivers are you currently using?

---

### Post by steev182 on 2009-09-25
Hi,

I tried installing the earlier 190. drivers yesterday on an amd64 version of karmic.

It gave errors for creating 32 bit extensions, but it succeeded in the kernel module.

When I came to restart, it wouldn't go into x, so I boot from USB and move my xorg.conf to xorg.conf.old and restart. I then run the installer package with --uninstall and restart, then I try the ubuntu provided restricted 185 driver, but this also doesn't work. It seems to load the nvidia module OK, but gives this error in xorg.0.log:

```
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
```

What am I doing wrong to make the drivers not work for me?

nVidia 8400GS PCI-e (with an onboard ATi ES1000 which isn't being used, but can't be disabled in bios)

---

### Post by AaronP_ on 2009-09-25
> **steev182 said:**
> ```
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short

```
That indicates that libglx.so got corrupted somehow, e.g. if there's filesystem corruption or the installer got killed partway through writing that file.  I'd suggest reinstalling the driver.

---

### Post by Buschbarber on 2009-09-25
> **Kosimo said:**
> New Beta release:

190.36  

Changelog:

I only see 190.32 beta for Linux. Where are you getting the 190.36?

---

### Post by darco on 2009-09-25
> **Kosimo said:**
> New Beta release:

190.36  

Changelog:

Hows it looking on the .31 kernel?

darco

---

### Post by Buschbarber on 2009-09-25
I just installed 190.36 on my UE2.3 machine. I have an Nvidia 9800GTX+ card and I have had to deal with an Overscan problem for some time. There is a Slider, in this new driver, that allows me to Shrink the Desktop to fit the display on my 50" HDTV. I output DVI to HDMI on the HDTV at a res of 1920x1080.

---

### Post by Kosimo on 2009-09-26
> **Buschbarber said:**
> I only see 190.32 beta for Linux. Where are you getting the 190.36?

Links at the first page of this thread

---

### Post by Kosimo on 2009-09-26
> **darco said:**
> Hows it looking on the .31 kernel?

darco

Didn't try yet. Somebody?

---

### Post by Buschbarber on 2009-09-26
I just noticed that 190.18.05 references OpenGL and 190.36 does not. Does 190.36 support OpenGL?

---

### Post by keiichidono on 2009-09-26
Yeah but not the unreleased OpenGL 3.2 if I recall correctly.

---

### Post by droidsys on 2009-09-29
None of the above worked for me. This did.

[INDENT]ctrl-alt-f1
[/INDENT]
if you're using KDE
[INDENT]pkill kdm
[/INDENT].. on Gnome use
[INDENT]pkill gdm
[/INDENT]
Then...
[INDENT]pkill Xorg
[/INDENT]
install drivers

[INDENT]startx
[/INDENT]

Done

---

### Post by darco on 2009-09-30
What the heck is OpenCL?

[http://www.beyond3d.com/content/news/735](http://www.beyond3d.com/content/news/735)

The link talks about 190.29 being the latest...Im running 190.32 but no mention of OpenCL in these drivers.....

darco

---

### Post by Buschbarber on 2009-09-30
> **darco said:**
> What the heck is OpenCL?

[http://www.beyond3d.com/content/news/735](http://www.beyond3d.com/content/news/735)

The link talks about 190.29 being the latest...Im running 190.32 but no mention of OpenCL in these drivers.....

darco

[http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)

---

### Post by darco on 2009-09-30
> **Buschbarber said:**
> [http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)

that explains everything (not!)

darco

---

### Post by Buschbarber on 2009-09-30
> **darco said:**
> that explains everything (not!)

darco

I did not really understand it either but I thought someone else could translate it into layman's terms.

---

### Post by Buschbarber on 2009-09-30
> **darco said:**
> that explains everything (not!)

darco

I asked an IT friend of mine to explain, in laymen's terms, the purpose of OpenCL.

This was his response:

OpenCL seems to allow programs to tell the the GPU rather than the CPU to do cryptographic tasks which generally would chew a lot of CPU but GPU's are actually mor efficient at than CPU's.

---

### Post by orlox on 2009-09-30
> **Buschbarber said:**
> I asked an IT friend of mine to explain, in laymen's terms, the purpose of OpenCL.

This was his response:

OpenCL seems to allow programs to tell the the GPU rather than the CPU to do cryptographic tasks which generally would chew a lot of CPU but GPU's are actually mor efficient at than CPU's.

As far as I know, it's not exclusively meant to be used in cryptographic tasks. It allows to use GPUs as additional processors for general tasks. I've seen some interesting videos on youtube, where openCL is used to perform real-time complex fluid simulations on not-so-high-end machines.

It seems it could become a very useful tool to perform scientific simulations on (relatively) low cost hardware.

---

### Post by NightwishFan on 2009-10-01
You cannot exceed your hardware. Only try to take advantage of it.

---

### Post by cschoonover on 2009-10-18
I went into ctrl+alt+f1 
used the command CD DESKTOP
So that I could install 
but it gave me and error as NO SUCH DIRECTORY EXISTS?

What did I do wrong... My screen freezes and I am hoping this new driver will work to fix the problem

---

### Post by OpenGuard on 2009-10-18
> **cschoonover said:**
> I went into ctrl+alt+f1 
used the command CD DESKTOP
So that I could install 
but it gave me and error as NO SUCH DIRECTORY EXISTS?

What did I do wrong... My screen freezes and I am hoping this new driver will work to fix the problem

```
cd $HOME/Desktop
```

---

### Post by Skip Da Shu on 2009-10-18
> **cschoonover said:**
> I went into ctrl+alt+f1 
used the command CD DESKTOP
So that I could install 
but it gave me and error as NO SUCH DIRECTORY EXISTS?

What did I do wrong... My screen freezes and I am hoping this new driver will work to fix the problem

It's 
```

cd Desktop
```

or 
```
cd /home/your-user-id-here/Desktop
```

IF you placed the NVIDIA~.sh file on your desktop.  You can also just place it in your home directory and that's what you should default to when you do the Ctrl-Alt-F1.

---

### Post by denis6902 on 2009-10-19
Hello,

I got a Zotac Mini Itx N330 ION too and i just cant install nvidia drivers on it. 

I installed a fresh jaunty 32bit 2 times already, and nothing.

After running updates, i go to harware drivers, and doesnt seem that i have a graphic card as i shows nothing in there. 

I tried following the tutorial over XBMC forums on setting up this, and when it gets to login screen is asks for usrname and password as usual then i get the following message:

```

XBMC needs hardware accelerated OpenGL rendering
install an appropriate graphics driver.

Please consult xbmc wiki for supported hardware
[http://xbmc.org/wiki/?title+Supported_hardware](http://xbmc.org/wiki/?title+Supported_hardware)

```I tried entering the commands on the post above me and it didnt install the beta 190 driver either.

How can i download this driver from (CRT+ALT+F1) because i cant get to graphical mode as it fails to log in. 

And i dont want to have to re-reintall it all again.

Best Regards

Denis



edit:
here is my error:
[B]
(~/.xsession-errors file)

[/B]```

/etc/gdm/Xsession: Beginnin session setup...
Setting IM through im-switch for locale=en=US
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput/xinput.d/default.
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
Error: cound't find RGB GLX visual or fbconfig
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
Segmentation fault
```
What did i do wrong? I tried installing the ([http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run)) and i still get the same error then the one above.


NOTE: Running 4GB or DDR2 / ubuntu32bit jaunty main

---

### Post by darco on 2009-10-19
Kosimo, 190.40 (release candidate) for Linux x86/x86_64 released 10/16
I d/l and check them out on my Karmic OS (2.6.31.14)

darco

**edit** just finish playing about 10 mins of QuakeLive and these drivers are awesome...very responsive and good IQ

---

### Post by Brackenn on 2009-10-23
Hi. I followed the instructions as best I could, but when I restarted I get the error:
"Ubuntu running in low graphics mode.
the following error was encountered.
You may need to update your configuration to solve this.
(EE)NVIDIA(0):Failed to initialize the nvidia Kernel Module. Please see the system's kernel log for additional error messages and consult the NVIDIA readme for details
                           ***Aborting***
(EE)Screens found, but none have a usable configuration."
In running Jaunty, And I'm trying to install a Gforce 9500gt. I downloaded the 185.18.36 from here===>[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)
Any ideas?
---Brackenn.

---

### Post by Skip Da Shu on 2009-10-23
> **Brackenn said:**
> Hi. I followed the instructions as best I could, but when I restarted I get the error:
"Ubuntu running in low graphics mode.
the following error was encountered.
You may need to update your configuration to solve this.
(EE)NVIDIA(0):Failed to initialize the nvidia Kernel Module. Please see the system's kernel log for additional error messages and consult the NVIDIA readme for details
                           ***Aborting***
(EE)Screens found, but none have a usable configuration."
In running Jaunty, And I'm trying to install a Gforce 9500gt. I downloaded the 185.18.36 from here===>[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)
Any ideas?
---Brackenn.

If you're not doing CUDA number crunching on it why go with these drivers instead of the 180.44 drivers from the repository?  The only reason I'm using 19x.xx drivers is for CUDA 2.2 support.  Otherwise 180.44 in Ubuntu worked fine.

---

### Post by Vorlander on 2009-10-24
I've tried:
185.18.36 ( Karmic 9.10 default)
190.32
190.36
190.40
190.42 RC

None of them has worked for me on kernel 2.6.31.14 (Karmic Default)

always the Black Screen (Monitor power save mode) after initial white ubuntu loading Logo.

My only working combination right now is the prehistoric 173.14.20 on default Karmic kernel installed with envy tool

:(:(:(:(:(

---

### Post by Buschbarber on 2009-10-24
> **Vorlander said:**
> I've tried:
185.18.36 ( Karmic 9.10 default)
190.32
190.36
190.40
190.42 RC

None of them has worked for me on kernel 2.6.31.14 (Karmic Default)

always the Black Screen (Monitor power save mode) after initial white ubuntu loading Logo.

My only working combination right now is the prehistoric 173.14.20 on default Karmic kernel installed with envy tool

:(:(:(:(:(

I just installed Ubuntu 9.10. I then installed 190.36. It works fine with my 9800GTX+

---

### Post by Vorlander on 2009-10-24
> **Buschbarber said:**
> I just installed Ubuntu 9.10. I then installed 190.36. It works fine with my 9800GTX+

Well....maybe is my Nvidia card , it's a 8600GTS......but I don't think so.....

---

### Post by Buschbarber on 2009-10-24
> **Vorlander said:**
> Well....maybe is my Nvidia card , it's a 8600GTS......but I don't think so.....

I stopped gdm and then did a sudo sh ./NVIDIA......run before rebooting.

---

### Post by darco on 2009-10-24
I used to have problems installing nvidia drivers but the key is to uninstall the original  nvidia kernel, files first...since then, installing new drivers is a breeze. You dont have to uninstall for every new driver, just this one time...

system > administration > hardware > disable any nvidia drivers if any are enabled

run: sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
run: sudo apt-get autoremove

crtl+alt+F1

login with normal account

stop gdm: sudo /etc/init.d/gdm stop

sudo sh ./<driver location>/NVIDIA-Linux-xxxx-pkg2.run

start gdm: sudo /etc/init.d/gdm start

darco

---

### Post by Kosimo on 2009-10-24
Folks, 190.42 Stable RC Released!

Here the Changelog:

> Release highlights since 190.40:

    * Fixed a bug in the nvidia-settings disclaimer window for the GPU Clock Frequencies Coolbits page, such that the "Accept" button is selectable when the desktop is so tall that the entire disclaimer can be viewed without scrolling.
    * Fixed a recent regression that caused the Xinerama option to not be set properly in the X configuration file when saving and merging from the nvidia-settings X Server Display Configuration page.
    * Fixed a resource leak in VDPAU's blit-based presentation queue. This bug limited the number of presentation queue objects that could be created and destroyed in a single application instance, and hence could limit the number of streams that could be displayed and/or the number of iterations of "loop" playback.
    * Fixed a power management regression that prevented some notebooks and systems with integrated GeForce 8 and 9 series GPUs from suspending.
    * Fixed a regression that caused TV-OUT controls to be unavailable on some GeForce 6 and 7 series GPUs.

Release highlights since 190.36:

    * Added support for OpenGL 3.2.
    * Added support for NVIDIA Quadro SDI Capture, part of the Quadro Digital Video Pipeline.
    * Added support for the following GPUs:
          o GeForce G102M
          o GeForce GT 220
          o GeForce G210
          o GeForce G210M
          o GeForce GT 230M
          o GeForce GT 240M
          o GeForce GTS 250M
          o GeForce GTS 260M
    * Updated the NVIDIA X driver to allow, on GeForce 8 or greater GPUs, more modes to validate on digital display devices whose EDIDs report very constrained HorizSync or VertRefresh ranges.
    * Fixed a randomly occuring X server crash caused by the PixmapCache option.
    * Increased the allowed amount of overscan compensation from 100 to 200.
    * On GPUs with VDPAU feature set B, VDPAU's handling of some corrupted or incorrectly formatted H.264 and MPEG streams has been improved.
    * Fixed a memory allocation problem with pre-GeForce 8 GPUs that caused GLX_EXT_texture_from_pixmap clients (e.g., Compiz, KDE 4) to display incorrect contents.



Links at the first page.

---

### Post by Vorlander on 2009-10-24
> **darco said:**
> I used to have problems installing nvidia drivers but the key is to uninstall the original  nvidia kernel, files first...since then, installing new drivers is a breeze. You dont have to uninstall for every new driver, just this one time...

system > administration > hardware > disable any nvidia drivers if any are enabled

run: sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
run: sudo apt-get autoremove

crtl+alt+F1

login with normal account

stop gdm: sudo /etc/init.d/gdm stop

sudo sh ./<driver location>/NVIDIA-Linux-xxxx-pkg2.run

start gdm: sudo /etc/init.d/gdm start

darco

I tried this way alkready without luck.....

I can't understand what is happening here :confused::confused::confused:

---

### Post by darco on 2009-10-24
Are you saying YES to each step in the nvidia installer?
Also check the nvidia installer log..Administration\Log File Viewer
for any dupe entries...


darco

---

### Post by Vorlander on 2009-10-24
> **darco said:**
> Are you saying YES to each step in the nvidia installer?
Also check the nvidia installer log..Administration\Log File Viewer
for any dupe entries...


darco

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Oct 24 05:31:48 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : true
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> There is no NVIDIA driver currently installed.

```

This is when I uninstall every NVidia driver, and then use envyng tools to install the only driver that works for me right now:
173.14.20

---

### Post by Kosimo on 2009-10-30
Folks:

190.42 has become Stable.  Links at the first page.

---

### Post by Buschbarber on 2009-10-30
> **Kosimo said:**
> Folks:

190.42 has become Stable.  Links at the first page.

I just installed Karmic Koala 9.10 Final and the Nvidia 190.42 seems to be working fine.

---

### Post by Vorlander on 2009-10-30
Ihave still the same problem.
If I cahnge my Nvidia 173.xx to any other drivers , the everything works Ok (I can login to terminal or by SSH and see all is running) except for the X....my monitor goes black and in Power Save mode :(:(

---

### Post by darco on 2009-10-30
> **Vorlander said:**
> Ihave still the same problem.
If I cahnge my Nvidia 173.xx to any other drivers , the everything works Ok (I can login to terminal or by SSH and see all is running) except for the X....my monitor goes black and in Power Save mode :(:(

Check to see if your xorg.conf is being dumped into the / (root) folder. That happened to me once and using a live-cd, I moved it to the proper folder, rebooted and all was good.

good luck

darco

---

### Post by Skip Da Shu on 2009-10-30
> **Kosimo said:**
> Folks:

190.42 has become Stable.  Links at the first page.
Thanx Much!

---

### Post by klemperal on 2009-11-04
Since I updated to the latest Nvidia drivers using this thread (great guide by the way) I can no longer drag launchers to my second x screen--I used to be able to do this without xinerama enabled.  Is there some way around this without having to enable xinerama or use twinview?

---

### Post by Keymone on 2009-11-06
i did everything as stated in the first post previously getting rid of all nvidia stuff that was already installed but instead of kdm i'm logged into console whith black screen flashing sometimes(it's probably kdm trying to start but fails)

after i remove xorg.conf everything works fine(but without nvidia drivers loaded of course)

can somebody help?

---

### Post by Skip Da Shu on 2009-11-06
> **Keymone said:**
> i did everything as stated in the first post previously getting rid of all nvidia stuff that was already installed but instead of kdm i'm logged into console whith black screen flashing sometimes(it's probably kdm trying to start but fails)

after i remove xorg.conf everything works fine(but without nvidia drivers loaded of course)

can somebody help?  It sounds like you are at the point where you would ctrl-alt-F1 and sudo sh  NVIDIA-.....sh to install the current drivers with the option of letting the script build you an xorg.conf.

---

### Post by cubdukat on 2009-11-09
Do these steps apply to Mythbuntu as well? I would like to install the 185 driver so that it can take advantage of the VDPAU features, but the last time I tried it by enabling the restricted driver, I ended up with it flashing incessantly at login without me being able to stop it. In short, I had to reinstall everything, and I would really like to avoid this, seeing as it took me eight reinstalls to get the system to work properly.

I am really losing patience with both NVidia and Ubuntu with these issues. I realize that all distros seem to have issues with NVidia drivers, but it seems to me that Ubuntu has a disproportionate share of them. The only reason I'm not using a different Myth distro is that they're even worse. 

If I could dump NVidia I would, but sadly, ATI doesn't make a card that can play games really fast and only take up one slot. I need a card like that because of the mobo's layout; I need to have both x1 PCI-e slots free.

I have been a Ubuntu user for years, but they're starting to slip a bit.

---

### Post by Buschbarber on 2009-11-09
> **cubdukat said:**
> Do these steps apply to Mythbuntu as well? I would like to install the 185 driver so that it can take advantage of the VDPAU features, but the last time I tried it by enabling the restricted driver, I ended up with it flashing incessantly at login without me being able to stop it. In short, I had to reinstall everything, and I would really like to avoid this, seeing as it took me eight reinstalls to get the system to work properly.

I am really losing patience with both NVidia and Ubuntu with these issues. I realize that all distros seem to have issues with NVidia drivers, but it seems to me that Ubuntu has a disproportionate share of them. The only reason I'm not using a different Myth distro is that they're even worse. 

If I could dump NVidia I would, but sadly, ATI doesn't make a card that can play games really fast and only take up one slot. I need a card like that because of the mobo's layout; I need to have both x1 PCI-e slots free.

I have been a Ubuntu user for years, but they're starting to slip a bit.

Have you tried installing Ubuntu on another drive and then immediately installing the Nvidia drivers before you do anything else? At least that would help you rule out other factors that might be preventing the Nvidia drivers from working properly.

I went through a similar experience to yours and I was finally able to get the drivers to install properly. I have a 9800GTx+ PCIe card on an ASUS P5Q mobo.

I have an HP MCE 7060n 3Ghz P4 that has an Onboard Intel video adapter and an Nvidia 8400GS PCI card. I have never been able to get the Nvidia drivers to install because I cannot get Ubuntu to boot unless the BIOS is set to Onboard, for the video. I cannot choose PCI in the BIOS. I have finally given up on that PC and built my new one.

---

### Post by NightwishFan on 2009-11-09
This is not really important, since I do not rely on the new drivers, however I have an issue.

When I install the AMD64 version of the driver, everything works well. The option to install 32-bit compatibility drivers, which I believe I need for wine, says that a 32-bit library did not pass the check, but the installation worked. 32 games in Wine crash, however.

---

### Post by Arup on 2009-11-10
> **NightwishFan said:**
> This is not really important, since I do not rely on the new drivers, however I have an issue.

When I install the AMD64 version of the driver, everything works well. The option to install 32-bit compatibility drivers, which I believe I need for wine, says that a 32-bit library did not pass the check, but the installation worked. 32 games in Wine crash, however.

That warning is normal for ncurses based nvidia driver. However bear in mind, some apps after install will need a removal and re-install of drivers to get the correct symbolic link for the x32 drivers.

---

### Post by coldReactive on 2009-11-11
By the way, this howto won't work for Hardy Heron and the nvidia GTS 250, the nvidia propietary driver just boots you into low graphics.

Edit: I had to install ia32-libs for the 32-bit opengl compat. then I had to do nvidia-xconfig again after reinstalling.

---

### Post by mocha on 2009-11-14
> **cubdukat said:**
> Do these steps apply to Mythbuntu as well? I would like to install the 185 driver so that it can take advantage of the VDPAU features, but the last time I tried it by enabling the restricted driver, I ended up with it flashing incessantly at login without me being able to stop it. 

Are you installing the 185 driver from the official repo and upgrading from a previous kernel?  This is a known bug that should be fixed soon.  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917")

---

### Post by sledge73 on 2009-11-14
Gotta mark this thread so I don't loose it again. Thanks made it all work correctly!!

---

### Post by Kosimo on 2009-11-14
> **sledge73 said:**
> Gotta mark this thread so I don't loose it again. Thanks made it all work correctly!!

Nice to know that this thread can still help somebody! ;)

---

### Post by Buschbarber on 2009-11-14
I just installed Ubuntu Ultimate 2.4 based upon Ubuntu 9.10. Once again, the Nvidia 190.42 drivers installed without a hitch and are working perfectly.

---

### Post by Kosimo on 2009-11-16
Folks

New Legacy drivers with X.Org 1.7 support have been released

 **173.14.22** (legacy,prerelease) for Linux x86/x86-64 released
Release highlights:

    * Added support for X.Org xserver 1.7.
    * Updated nvidia-installer to detect newer Debian distributions that use /usr/lib32 instead of /emul/ia32-linux as the 32-bit library path.


 **96.43.14** (legacy,prerelease) for Linux x86/x86-64 released
Release highlights:

    * Added support for X.Org xserver 1.7.
    * Updated nvidia-installer to detect newer Debian distributions that use /usr/lib32 instead of /emul/ia32-linux as the 32-bit library path.





Links at the first page.

---

### Post by Buschbarber on 2009-11-16
I downloaded 190.42 on Oct 24, before it was Certified on Oct 31. Is there any difference between the file I downloaded then and the one available on the Nvidia site Now?

---

### Post by AaronP_ on 2009-11-16
> **Buschbarber said:**
> I downloaded 190.42 on Oct 24, before it was Certified on Oct 31. Is there any difference between the file I downloaded then and the one available on the Nvidia site Now?
No.

---

### Post by Buschbarber on 2009-11-16
> **AaronP_ said:**
> No.

Thank you for the quick reply!!

---

### Post by rprenen on 2009-11-17
I had trouble stopping the GDM display manager. Rebooted pc and went for the recovery mode in the grub menu. Installed run package from NVIDIA from the prompt (I had changed the file-mode in 'runnable' earlier in GNOME'S file manager). Worked also..

---

### Post by blackened07 on 2009-11-17
Ubuntu 9.10, 9.04 can't install properly nvidia 190.xx driver
hello guys, i'm having this little problem, I just bought this sony laptop
VPCCW17FX, thath comes with nvidia 210m chipset

I tried adding to the /etc/apt/sources.list and installing the driver from the terminal and everything seems to work fine, until y reboot and goes to my log in screen, the screen goes totally to black, like turned off, anyway I tried from system/administration/hardware drivers and enabling the 185, and the 190 driver will do the same thing.

I also tried downloading the driver from de nvidia webpage, and installed, but the same thing, the screen goes totally black, I can log on in my ubuntu, but I can't see a thing.

I'm running ubuntu 9.10 amd 64, ( I also tried in 9.04 i386 ) but the same thing, I don't know how to look for info, since I can't find too many on the net, Obviuously I'm missing sth, but don't have a clue what it is, any help, or tip would be really appreciated

Thanks in advance.

---

### Post by darco on 2009-11-20
Running Mint 7 x64 w/190.42 drivers. When I make a change in the X server settings (contrast/brightness), it saves but on the next reboot it goes back to the default settings. As soon as I re-open Nvidia X server settings, the change kicks in?
How do I go about saving the settings on reboot w/o having to open nvidia x server?

thxs

darco

*edit...nm...figured it out...*

---

### Post by singedwings on 2009-11-20
I am having the same problems as blackened07. I have a sli setup and always had problems with previous versions of ubuntu and nvidia installs. However in the past I was always able to solve the problems by adding the Busid of the first graphics card to xorg.conf. This time no joy any help appreciated.


I was wrong, putting the Busid in did work. My replacement motherboard numbers the PCI slots in reverse and now that I have worked that out it works.

---

### Post by ratcheer on 2009-11-23
I have defeated myself with my own foresight. I found a new Linux kernel in Update Manager. So, I remembered all the times I installed a new Kernel and lost the video driver and I thought, "If I unstall the driver before I install the new kernel, I won't have that problem". So, I uninstalled it.

So now, I needed to go back to the GUI to re-run Update Manager. So, I tried to restart gdm and, boo!, I am back at the dreaded blinking login prompt.

I thought that with the nVidia driver uninstalled, it would default to the standard VGA driver. Obviously, I am mistaken. How is this supposed to work? What is the correct workflow to install a new kernel when using a 3rd party video driver?

Thanks,
Tim

---

### Post by ratcheer on 2009-11-23
I always panic a little when I cannot log in. But, I calmed down and thought my way through it. I rebooted in Recovery Mode. Then I ran "sudo apt-get upgrade" from the command prompt. This upgraded all but 5 packages. Then I reinstalled nVidia 190.42 and, finally, rebooted normally. I am back in business.

But, with one small problem - the five packages that did not upgrade were the new kernel and associated updates. So, I am back where I started, except for the other updates that were successfully installed.

Should I just install the new kernel from Update Manager and reinstall nVidia when it craps out? I would like to have a clean, smooth process.

Tim

---

### Post by Kosimo on 2009-11-25
Guys!  


**[COLOR="Red"]195.22[/COLOR]** has been released!!

Here the changelog: 

>     *  Enhanced the VDPAU blit-based presentation queue to provide values of "first_presentation_time" that have less jitter.
    * Add support for R16F and RG32F GLXFBConfigs when using GeForce 8 series and higher GPUs.
    * Added support for NVIDIA 3D Vision Stereo on Linux with Quadro GPUs. See the "Stereo" X configuration documentation in the README for details.
    * Added support for A2BGR10 32-bit GLX visuals on 30-bit X screens. These allow some level of window transparency when using 30-bit visuals with GLX and Composite, but they may cause problems with older X servers and/or applications. ARGB GLX visuals can be disabled by adding:

          Option "AddARGBGLXVisuals" "False"

      to the X configuration file.
    * Fixed a problem that caused DisplayPort devices to behave incorrectly when DPMS power saving mode was triggered.
    * Updated VDPAU to improve thread concurrency. See the README for details.
    * Altered NVIDIA X driver behavior in the case that no display devices are connected to the GPU. Previously, in this case, the NVIDIA X driver would pretend a CRT was connected to the GPU. Now, the NVIDIA X driver will not automatically pretend that any CRTs are connected. If the X driver does not detect any connected display devices, the X server will fail to start.

      To restore the old behavior, use the ConnectedMonitor X configuration option; e.g.,

          Option "ConnectedMonitor" "CRT"

      Alternatively, if display is not desired, Quadro and Tesla GPU users can enable "NoScanout" mode, which bypasses any mode timing validation or use of display devices; this is configured with:

          Option "UseDisplayDevice" "none"

    * Disabled software cursors when the driver is operating in "no scanout" (UseDisplayDevice "none") mode. The software cursor image is not visible in remote desktop applications or screenshots anyway, so having software cursor enabled was unnecessary.
    * Changed glXSwapBuffers() behavior for a pixmap such that it is now a no-op in the direct rendering case in order to match the indirect case and comply with the GLX spec. Previously, calling glXSwapBuffers() on pixmaps in the direct case would swap the pixmap's buffers if the pixmap was double buffered.
    * Modified the installation location and names of internal VDPAU libraries to conform to conventions and Debian packaging guidelines. New versions of libvdpau expect this layout. Compatibility with old versions of libvdpau is maintained with symlinks.
    * Fixed a bug that could cause errors in graphical applications run after a previous application using VDPAU and OpenGL. This behaviour was observed when running Gwenole Beauchesne's hwdecode-demos application.
    * Modified vdpau.h to increment VDPAU_VERSION, to reflect the fact that new features have been added in the past. Also, add the new define VDPAU_INTERFACE_VERSION.
    * Fixed a periodic temporary hang in the VDPAU blit-based presentation queue.
    * Fixed a problem that caused resolution limitations or corruption on certain DisplayPort devices such as the Apple 24" Cinema display or some DisplayPort to VGA adapters.
    * Disabled the UseEvents option for GeForce 8 series and higher GPUs due to a problem that causes occasional short hangs. It will be re-enabled when that bug has been tracked down and fixed.
    * VDPAU now allows multiple streams to be decoded at once, without the need to set any environment variables.





Links at the first page of this thread. 

Good luck!

---

### Post by Buschbarber on 2009-11-25
I ran into my first install issue in quite some time, with 195.22. I was running 190.42. After installing 195.22, it rebooted into a blinking TTY Login Prompt and was not accurately accepting Input. I rebooted into the Recovery Mode, ran sudo nvidia-uninstall and then reinstalled 195.22. Now, it is working perfectly.

---

### Post by WildeBeest on 2009-11-25
This has worked for me every time I tried a new version.

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=command+line](http://ubuntuforums.org/showthread.php?t=1125400&highlight=command+line)

---

### Post by gspat on 2009-11-27
how does upgrading to 195 affect nvidia-glx? I was having issues with stuff not working (logon prompt only) after I installed, so i followed examples and installed the 190 driver, but programs running opengl would error out with an error about not starting and missing a .so file.

I installed nvidia-glx-185 and things work better now, but there was a warning about a driver number mismatch

there is no nvidia-glx-190, or nvidia-glx-195... should I be overly concerned?

---

### Post by mocha on 2009-11-29
> **gspat said:**
> programs running opengl would error out with an error about not starting and missing a .so file.


There is a little something missing from all these nvidia HOWTOs.  Sometimes after xserver package updates OpenGL stuff stops working.  This is becuase the symlink /usr/lib/xorg/modules/extensions/libglx.so gets broken for some reason, probably becuase the package manger doesn't see the nvidia binary driver installed.

If you have OpenGL problems just check the directory /usr/lib/xorg/modules/extensions/ and make sure there is a file called libglx.so symlinked to libglx.so.190.42, or whatever driver you have installed (libglx.so.195.xx, etc...)

---

### Post by toupeiro on 2009-11-29
Sorry if this was mentioned earlier in this thread, but How well is DKM at addressing these beta drivers when kernel updates are done?  In the beginning, it was pretty raw..  I would like to recommend to some people I casually support to use a beta driver for some video issues they are having, but I'm not up to doing so if its going to break their update/upgrade processes.

---

### Post by LWJ on 2009-11-30
Help...  I am new to Linux.  I have a dell poweredge machine with the ATI graphics card on the system board.  I installed a Nvidia 6200 to run windows.  When I attempted to install Ubuntu while the Nvidia card was in the machine, it would hang up.  So I installed it using only the ATI graphics and the Nvidia card removed.  The boot loader comes up ok with the ATI graphics and will load Ubuntu or Windows, but Windows does not do well with ATI.  If I install the Nvidia card Ubuntu will not boot, I have to power the machine off and start over.  I have read the procedure to install Nvidia drivers, but those procedures assumes the Nvidia card is installed when trying to install.  anyone have any suggestions?

---

### Post by Buschbarber on 2009-11-30
> **LWJ said:**
> Help...  I am new to Linux.  I have a dell poweredge machine with the ATI graphics card on the system board.  I installed a Nvidia 6200 to run windows.  When I attempted to install Ubuntu while the Nvidia card was in the machine, it would hang up.  So I installed it using only the ATI graphics and the Nvidia card removed.  The boot loader comes up ok with the ATI graphics and will load Ubuntu or Windows, but Windows does not do well with ATI.  If I install the Nvidia card Ubuntu will not boot, I have to power the machine off and start over.  I have read the procedure to install Nvidia drivers, but those procedures assumes the Nvidia card is installed when trying to install.  anyone have any suggestions?

This may have nothing to do with your problem, but I have an HP m7060n P4 MCE machine that came with an Onboard Integrated Intel graphics adapter. I put in an Nvidia 6200 and later replaced it with an Nvidia 8400. Ubuntu would not boot if I set the Graphics Option, in the Bios, to PCI. It would only boot if the Graphics Option, in the Bios, were set to Onboard. I tried several distros of Ubuntu and Mandriva. They did not like a PC mobo with Onboard Graphics.

---

### Post by LWJ on 2009-11-30
> **Buschbarber said:**
> This may have nothing to do with your problem, but I have an HP m7060n P4 MCE machine that came with an Onboard Integrated Intel graphics adapter. I put in an Nvidia 6200 and later replaced it with an Nvidia 8400. Ubuntu would not boot if I set the Graphics Option, in the Bios, to PCI. It would only boot if the Graphics Option, in the Bios, were set to Onboard. I tried several distros of Ubuntu and Mandriva. They did not like a PC mobo with Onboard Graphics.


Unfortunately I am not able to disable the pci port in the bios of this machine.  So I have to remove the card to get it to boot.

---

### Post by Buschbarber on 2009-11-30
> **LWJ said:**
> Unfortunately I am not able to disable the pci port in the bios of this machine.  So I have to remove the card to get it to boot.

Windows would boot with the Nvidia driver no matter what Bios setting I chose, however, I could not access the Grub Menu unless I plugged a monitor into the Onboard Intel Graphics Adapter.

With the 6200 card, I was able to install the Nvidia Restricted drivers and even though the Bios was set to Onboard, half way through the Boot sequence, the Ubuntu Nvidia driver kicked in and Ubuntu would load with the Nvidia driver. 

When Ubuntu version 9 came out, I could not do that anymore so I built a Newer, Faster, Quad Core machine with an Asus P5Q mobo and Ubuntu boots perfectly.

---

### Post by Skip Da Shu on 2009-11-30
> **LWJ said:**
> Help...  I am new to Linux.  I have a dell poweredge machine with the ATI graphics card on the system board.  I installed a Nvidia 6200 to run windows.  When I attempted to install Ubuntu while the Nvidia card was in the machine, it would hang up.  So I installed it using only the ATI graphics and the Nvidia card removed.  The boot loader comes up ok with the ATI graphics and will load Ubuntu or Windows, but Windows does not do well with ATI.  If I install the Nvidia card Ubuntu will not boot, I have to power the machine off and start over.  I have read the procedure to install Nvidia drivers, but those procedures assumes the Nvidia card is installed when trying to install.  anyone have any suggestions?

I didn't believe this when I first read it but just happen to have a PowerEdge 600sc on my bench.  I put a Nvidia FX5200 in the PCI slot and rebooted... just black screens and never comes up.  Off to do some googling on this.  No options in BIOS that I see around turning on-board off so I have to assume there's a conflict of some sort.

Ubuntu v9.10

UPDATE:  take a look a [this]("http://www.scheerfun.org/techie/dell600sc/").

---

### Post by ratcheer on 2009-12-02
I went to the nVidia web site and they still have 190.42 as the Linux version. Is 195.22 a beta or something?

Tim

---

### Post by Vadi on 2009-12-02
> **ratcheer said:**
> I went to the nVidia web site and they still have 190.42 as the Linux version. Is 195.22 a beta or something?

Tim

yep

---

### Post by Buschbarber on 2009-12-02
> **ratcheer said:**
> I went to the nVidia web site and they still have 190.42 as the Linux version. Is 195.22 a beta or something?

Tim

If you go to the first page of this thread, it is usually updated with the latest driver links (Beta and Released)

---

### Post by ratcheer on 2009-12-02
Thanks, Vadi and Buschbarber. I will stick with the release version. The post where it was first mentioned said, "195.22 has been released". To me, that is different from saying it is a new beta version.

Tim

---

### Post by The Bright Side on 2009-12-04
Hey guys,

I just installed Karmic on my laptop and am trying to install the 190 driver, but when I try to disable GDM using "sudo /etc/init.d/gdm stop", I get an error message:

> Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm

Well none of these work. How can I stop gdm now? It used to work splendidly in 9.04...

Thanks!



EDIT: Never mind, worked!!

---

### Post by ratcheer on 2009-12-05
I messed around a bit based on that message, too. What I finally figured out was that the gdm was actually stopped by the init.d command and it was just suggesting a new, "improved" way to stop it. So, it was more of a warning than an error, but they make it sound like an error.

Tim

---

### Post by The Bright Side on 2009-12-05
Yeah that's the same thing I found! Thanks for confirming.

---

### Post by Buschbarber on 2009-12-05
I was prompted, today, by Update Manager, to install a number of Security Updates as well as other Updates, including GDM. I am running UE 2.4. After Reboot, it came up in Low Graphics Mode. I exited to the tty Login prompt and stopped GDM. I tried to reinstall Nvidia 195.22 but I was informed that the X Server was still running. I thought that stopping GDM would allow me to install new or existing drivers. I rebooted again and this time went to the tty Login prompt, directly. I was able to reinstall the 190.22 drivers successfully and Login normally.

Is this the process I will have to use each time certain types of Updates are applied? If so, which ones should I be looking for?

---

### Post by nardis_Miles1 on 2009-12-05
I have been looking for a good thread on which to ask a general question. I am using an nvidia graphics card (GeForce 8400 GS) on an athlon 64 5000+ dual core box. I am using an application that takes advantage of 3-d acceleration. At this point, the speed is just bearable. I am thinking of upgrading the graphics card and I'd like to know if I would see a significant difference in speed on the same box. That is, with the same OS, machine, and driver, does a better card (greater graphics memory, higher clock speeds, different software) actually perform better? Does anyone have experience with this?

Art Edwards

---

### Post by l-x-l on 2009-12-05
> **Buschbarber said:**
> I was prompted, today, by Update Manager, to install a number of Security Updates as well as other Updates, including GDM. I am running UE 2.4. After Reboot, it came up in Low Graphics Mode. I exited to the tty Login prompt and stopped GDM. I tried to reinstall Nvidia 195.22 but I was informed that the X Server was still running. I thought that stopping GDM would allow me to install new or existing drivers. I rebooted again and this time went to the tty Login prompt, directly. I was able to reinstall the 190.22 drivers successfully and Login normally.

Is this the process I will have to use each time certain types of Updates are applied? If so, which ones should I be looking for?

The same thing happened to me today. I thought I broke Ubuntu ;) (again). BTW... has anyone else noticed that after installing ver 190.xxx that it doesn't show up on the GUI Hardware Drivers prompt? It works fine though.

---

### Post by ratcheer on 2009-12-05
> **l-x-l said:**
> The same thing happened to me today. I thought I broke Ubuntu ;) (again). BTW... has anyone else noticed that after installing ver 190.xxx that it doesn't show up on the GUI Hardware Drivers prompt? It works fine though.

Ever since upgrading to 9.10, I have not been able to see my nVidia driver in the Hardware Drivers GUI. The GUI does show some older drivers, but not the one I am successfully using. I am using 190.42, but it shows 173 and 185.

Tim

---

### Post by Buschbarber on 2009-12-06
> **ratcheer said:**
> Ever since upgrading to 9.10, I have not been able to see my nVidia driver in the Hardware Drivers GUI. The GUI does show some older drivers, but not the one I am successfully using. I am using 190.42, but it shows 173 and 185.

Tim

That is normal. Ever since I started using drivers that I downloaded and installed, they never show up there. There is a reason why that is, but it escapes me at the moment.

---

### Post by ratcheer on 2009-12-06
> **Buschbarber said:**
> That is normal. Ever since I started using drivers that I downloaded and installed, they never show up there. There is a reason why that is, but it escapes me at the moment.

They did show up there in 9.04.

Tim

---

### Post by northwestuntu on 2009-12-06
finally they added the overscan option :D

---

### Post by bigfootnmd on 2009-12-08
I have two desktops running 9.10.  Both have the Geoforce 8400 graphics card.  On my system which was upgraded from 9.04 I have the Ubuntu restricted Nvida drivers on my machine. However, on they are not present at all on the other machine.  

With my House-mate's PC I had issues with the 9.10 image (which I posted about on this forum).  I found the solution on this site and installed 9.04 and then upgraded from 9.04 to 9.10.  After the upgrade was completed the machine booted to a flashing command prompt.  Searches on this site led me to the solution of copying the xorg.conf.failsafe file to the xorg.conf.
So that is where this machine stands now.  Mind you my House-mate seems happy with his system (although he does miss all the real arcade games that he bought and download, he is playing some on line).  

So, the question here is two fold.  1.  Should I even try to install the NVidia drivers at all?  And 2,  if I do what approach to take?

Thank you in advance.

---

### Post by Kralnor on 2009-12-09
> **Askar450 said:**
> I don't know this is the same or not but I was told that before updating your drivers you need to first sudo apt-get install build-essential linux-headers-`uname -r`
then remove the current drivers by sudo sh NVIDIA-xxx.run --uninstall, it will tell you it will do its best to uninstall the drivers. Go ahead and press ctrl+alt+F1 and log in, once that is done type sudo /etc/init.d/gdm stop now just do the samething you did before and they should work.

Thanks. I had trouble installing the latest nVidia drivers because of missing linux-headers. Running ```
sudo apt-get install linux-headers-$(uname -r)
``` before invoking ```
sudo sh ./NVIDIA-xxx.run
``` fixed the problem.

---

### Post by Kosimo on 2009-12-14
Folks: 

195.53 Pre-Release is here!

Changelog: 

>     *  Modified the installation location and names of internal VDPAU libraries to conform to conventions and Debian packaging guidelines. New versions of libvdpau expect this layout. Compatibility with old versions of libvdpau is maintained with symlinks.
    * Fixed a bug that could cause errors in graphical applications run after a previous application using VDPAU and OpenGL. This behaviour was observed when running Gwenole Beauchesne's hwdecode-demos application.
    * Modified vdpau.h to increment VDPAU_VERSION, to reflect the fact that new features have been added in the past. Also, add the new define VDPAU_INTERFACE_VERSION.
    * Fixed a periodic temporary hang in the VDPAU blit-based presentation queue.
    * Fixed a problem that caused resolution limitations or corruption on certain DisplayPort devices such as the Apple 24" Cinema display or some DisplayPort to VGA adapters.
    * Disabled the UseEvents option for GeForce 8 series and higher GPUs due to a problem that causes occasional short hangs. It will be re-enabled when that bug has been tracked down and fixed.
    * VDPAU now allows multiple streams to be decoded at once, without the need to set any environment variables.



Links in the first page of this thread. 

Good luck!

---

### Post by Janneman27 on 2009-12-15
Great! It works perfectly!

I also notice a quick Nvidia splash screen after GRUB loads...is it possible to turn that of somewhere?

---

### Post by Buschbarber on 2009-12-15
> **Janneman27 said:**
> Great! It works perfectly!

I also notice a quick Nvidia splash screen after GRUB loads...is it possible to turn that of somewhere?

I have seen references, in this thread, to procedures for blocking the Nvidia Splash Screen.

---

### Post by Janneman27 on 2009-12-17
Thanx

---

### Post by Slikgman on 2009-12-24
> **Buschbarber said:**
> If you go to the first page of this thread, it is usually updated with the latest driver links (Beta and Released)
 
There is a new certified release 190.53 on Nvidia home page Dated 12-16-2009 for 64bit.  Someone should check on updating the 1st page.
 
Great work on updating this Thread, I am bookmarking it for future updates!  :)

---

### Post by BDPNA on 2009-12-25
> **Buschbarber said:**
> I was prompted, today, by Update Manager, to install a number of Security Updates as well as other Updates, including GDM. I am running UE 2.4. After Reboot, it came up in Low Graphics Mode. I exited to the tty Login prompt and stopped GDM. I tried to reinstall Nvidia 195.22 but I was informed that the X Server was still running. I thought that stopping GDM would allow me to install new or existing drivers. I rebooted again and this time went to the tty Login prompt, directly. I was able to reinstall the 190.22 drivers successfully and Login normally.

Is this the process I will have to use each time certain types of Updates are applied? If so, which ones should I be looking for?

I actually had to do this same thing to get 190.53 to install on my system.  However, although it looked like the install worked, now when I reboot, I am getting just a blank screen.  Nothing more.  It looks like my monitor is getting a signal since it's not going into sleep mode, but I just see a blank screen.  Can anyone help?  Anything I can do/check or grep in a log if I boot into the recovery console that might shed some light?

Thanks for any help.  First time I ever had to do this when upgrading the drivers.

---

### Post by Buschbarber on 2009-12-25
If I boot Ubuntu 9.10 and the X server has been hosed, I usually do an Ctrl-Alt-F1, login, do a sudo service gdm stop, and reinstall the video driver.

A couple of times, lately, I was not able to Reinstall the video driver or it would boot up with a box containing a white backround and four radio buttons. I was able to boot into the recovery console and install the video driver from there. Next time a booted everything was OK, video wise.

I have not had to Uninstall the old video driver before installing the new one.

---

### Post by BDPNA on 2009-12-25
> **Buschbarber said:**
> If I boot Ubuntu 9.10 and the X server has been hosed, I usually do an Ctrl-Alt-F1, login, do a sudo service gdm stop, and reinstall the video driver.

A couple of times, lately, I was not able to Reinstall the video driver or it would boot up with a box containing a white backround and four radio buttons. I was able to boot into the recovery console and install the video driver from there. Next time a booted everything was OK, video wise.

I have not had to Uninstall the old video driver before installing the new one.

Hmmm, sounds a little different than what I am experiencing.  I was getting that box about low graphics mode before I hand-upgraded the driver...Now if I try to boot into a non-recovery console (any kernel) I don't even get that far.  Can't even get a picture.  Screen goes black a few seconds after I select my kernel and that's that.

I'm doing this on a hacked mac mini, which could be part of the problem.  The weirdest thing is I just tried to force-boot it from a Karmic installation CD and it's doing the same thing.  Really weird now.

---

### Post by jonnyg01 on 2009-12-27
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. It's been almost a week since I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 

_**How to install nVidia drivers in Linux:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR=Red]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```[SIZE=5]**[COLOR=Red]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```[/SIZE]


this is where it is now stuck and reads 
"rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm gdm stop/waiting"

ps. im on the internet on a laptop right now waiting and looking at my desktop screen while it shows this...

Many Thanks. Happy Holidays.
Jonny G

---

### Post by ratcheer on 2009-12-27
But, it still worked to stop your gdm. It is just recommending that you do it differently, in the future.

Tim

---

### Post by jonnyg01 on 2009-12-27
Thank you Tim. It's installing right now!!!

---

### Post by jonnyg01 on 2009-12-27
so i had reboot my computer, all seemed well, but now it's saying things i've never read on it before about USB devices not accepting addresses and $h1t....I'm getting too frustrated...

any way,

---

### Post by jonnyg01 on 2009-12-27
afternthat happened i was able to type "reboot" [enter] and it did just that, went past BIOS and went black..not shiny off black, but terminal black.

---

### Post by jonnyg01 on 2009-12-27
Okay. Sorry about that one...I kicked the key board and woke up...
But it's stuck on 
"BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)"

Where the normal (i dont know what its called but it shows up with your name when you start terminal you know??), it reads
"(initramfs) [(blinking underscore)]

and I think it's blinking pretty fast.

---

### Post by ratcheer on 2009-12-27
This is all too weird, jonnyg. The fast blinking cursor makes me think the video driver is not installed, properly, but I can't be sure.

If you are running grub2, reboot and try holding the Shift key just as grub is starting. This should bring you to the grub menu, where you can choose to boot in recovery mode. If you can get to that point, reinstall the video driver. Make sure that when it asks, you choose to automatically configure xorg. Then, when the installation completes, reboot, normally.

I hope this helps.

Tim

---

### Post by philip5 on 2010-01-01
If anyone is interested in newer Nvidia drivers (especially for Karmic) I have packages ready for both the 190-series and the new 195-beta series on my repo at Launchpad. Look for the packages named nvidia-glx-190 (at the moment 190.42) and nvidia-glx-195 (at the moment 195.30). There are also a bunch of other goodies on my repo.

Check it out at: [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

If you install updated Nvidia drivers like this the easiest way to get all the libs and drivers to reload is making a reboot after updating. 

Regards,

Philip

---

### Post by VastOne on 2010-01-01
> **philip5 said:**
> If anyone is interested in newer Nvidia drivers (especially for Karmic) I have packages ready for both the 190-series and the new 195-beta series on my repo at Launchpad. Look for the packages named nvidia-glx-190 (at the moment 190.42) and nvidia-glx-195 (at the moment 195.30). There are also a bunch of other goodies on my repo.

Check it out at: [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

If you install updated Nvidia drivers like this the easiest way to get all the libs and drivers to reload is making a reboot after updating. 

Regards,

Philip

Are you saying I can load the nvidia-glx-195-dev drivers from Synaptic, reboot and be done or are you saying that once I dload and run the 195.run I will have everything I need so that it will install the kernel support?

---

### Post by tad1073 on 2010-01-01
can't install nvidia-settings

using 195.30 w/9.10 64 bit

```
$ sudo apt-get install nvidia-settings
[sudo] password for thomas: 
Sorry, try again.
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-settings: Depends: libatk1.0-0 (>= 1.29.3) but 1.28.0-0ubuntu1 is to be installed
E: Broken packages

```

---

### Post by philip5 on 2010-01-01
> **VastOne said:**
> Are you saying I can load the nvidia-glx-195-dev drivers from Synaptic, reboot and be done or are you saying that once I dload and run the 195.run I will have everything I need so that it will install the kernel support?
I'm saying that if you use my repo (which have a bunch of other stuff besides nvidia drivers) and add it as source you can from i.e synaptic install nvidia-glx-195 and after that reboot. Then you will have working nvidia 195.30 drivers on your system if you run Karmic. All the compiling and setting up the drivers are done by the package. Also handles it self if you update your kernel etc. This is as my packages use dkms in the same way as the nvidia drivers in ubuntu have done since Intrepid. (you don't need the -dev packages of you don't have to build some source code yourself that need nvidia driver headers)

You might also want to install nvidia-195-libvdpau if you want vdpau support that beside the software in it self need hardware from nvidia 8800 series or newer to de facto work otherwise there is no benefit.

Just remember that the nvidia 195.xx drivers are still beta but so far works great for me.

If you use my packages then you don't need any bin.run-files from nvidia that also have to be re-run everytime you get a kernel update which my packages handle for you.

---

### Post by VastOne on 2010-01-01
> **philip5 said:**
> I'm saying that if you use my repo (which have a bunch of other stuff besides nvidia drivers) and add it as source you can from i.e synaptic install nvidia-glx-195 and after that reboot. Then you will have working nvidia 195.30 drivers on your system if you run Karmic. All the compiling and setting up the drivers are done by the package. Also handles it self if you update your kernel etc. This is as my packages use dkms in the same way as the nvidia drivers in ubuntu have done since Intrepid. (you don't need the -dev packages of you don't have to build some source code yourself that need nvidia driver headers)

You might also want to install nvidia-195-libvdpau if you want vdpau support that beside the software in it self need hardware from nvidia 8800 series or newer to de facto work otherwise there is no benefit.

Just remember that the nvidia 195.xx drivers are still beta but so far works great for me.

I see it now...

I loaded your repo and the first time through after reloading it did not show all of the 195.xx drivers, only the -dev ones.

They are there now and I will give it a try

Thanks

---

### Post by Nixie Pixel on 2010-01-02
First I wanted to thank you. This guide is very valuable and helped me quite a bit!

I have been having a problem with the Nvidia drivers - it seems that they are giving me problems with color switching during video playback. Blues look green/yellow, browns look blue, and so on. Viewing images is fine, it just happens on certain videos.

When I run mplayer with -vo x11, colors show up properly, so I believe it is the driver that is the problem, is this correct? (I can create a new thread if this isn't the place to ask about that)

Thanks!

---

### Post by Kosimo on 2010-01-02
> **Nixie Pixel said:**
> First I wanted to thank you. This guide is very valuable and helped me quite a bit!

I have been having a problem with the Nvidia drivers - it seems that they are giving me problems with color switching during video playback. Blues look green/yellow, browns look blue, and so on. Viewing images is fine, it just happens on certain videos.

When I run mplayer with -vo x11, colors show up properly, so I believe it is the driver that is the problem, is this correct? (I can create a new thread if this isn't the place to ask about that)

Thanks!

Is good to see that this guide still helps people :D

What current configuration are you using? Graphics card, driver version, etc...

Thanks!

---

### Post by AaronP_ on 2010-01-02
> **Nixie Pixel said:**
> I have been having a problem with the Nvidia drivers - it seems that they are giving me problems with color switching during video playback. Blues look green/yellow, browns look blue, and so on. Viewing images is fine, it just happens on certain videos.

When I run mplayer with -vo x11, colors show up properly, so I believe it is the driver that is the problem, is this correct? (I can create a new thread if this isn't the place to ask about that)
This is a common problem with some video players that set the XVideo hue adjustment option to 180 degrees from what it should be.  You should be able to open the player's control panel and reset the hue slider.  Alternatively, you can open up nvidia-settings, change to the "X Server XVideo Settings" tab, and hit "Reset Hardware Defaults".

Hope that helps!

---

### Post by neslot on 2010-01-07
> **cschoonover said:**
> I went into ctrl+alt+f1 
used the command CD DESKTOP
So that I could install 
but it gave me and error as NO SUCH DIRECTORY EXISTS?

What did I do wrong... My screen freezes and I am hoping this new driver will work to fix the problem


Try cd /home/(your login name)/Desktop

space after cd.  you can hit tab after /ho to complete, and after the first 2 or 3 letters of your login name  then /De  be sure to use an upper case D in desktop
hitting tab after each double or triple letter entry to auto complete keeps you on the correct path..
Tony

---

### Post by infestor on 2010-01-07
administration>hardware drivers still show that i use 185, but nvidia settings show 195.22. i take it 195.22 is in use?

---

### Post by ratcheer on 2010-01-08
> **infestor said:**
> administration>hardware drivers still show that i use 185, but nvidia settings show 195.22. i take it 195.22 is in use?

That sounds right to me. On my system, nothing above 185 has ever shown up in the Hardware Drivers applet.

Tim

---

### Post by llawwehttam on 2010-01-08
Just a little worry. When I install the drivers ubuntu offers me in the Hardware drivers menu I lose my display and have had to resort to reinstalling. Are the drivers from the website the same ie will they cause me trouble or should they be fine.

I want to get a laptop card, a GT130M Hybrid Hotswap working to be precise.

Any advice?

---

### Post by GeekGirl1 on 2010-01-08
> **philip5 said:**
> If anyone is interested in newer Nvidia drivers (especially for Karmic) I have packages ready for both the 190-series and the new 195-beta series on my repo at Launchpad. Look for the packages named nvidia-glx-190 (at the moment 190.42) and nvidia-glx-195 (at the moment 195.30). There are also a bunch of other goodies on my repo.

Check it out at: [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

If you install updated Nvidia drivers like this the easiest way to get all the libs and drivers to reload is making a reboot after updating.Thank you! The 195-beta series installed perfectly with no errors. Synaptic removed nearly all of the previous versions, but some files remain. Can I remove files with versions 173, 180, 185, and 96 as shown below?

Should the package manager remove these files automatically (perhaps this information will help you)?
```
~> dpkg --get-selections | grep nvidia
nvidia-173-modaliases				install
nvidia-180-modaliases				install
nvidia-185-modaliases				install
nvidia-195-kernel-source			install
nvidia-195-libvdpau				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-glx-195					install
nvidia-glx-195-dev				install
nvidia-settings					install
```

Update: I removed files marked for deinstall with [Ubuntu Tweak](http://ubuntu-tweak.com/).

---

### Post by AnyMation on 2010-01-08
Thanks a LOT for this thread.

I am a COMPLETE newby on Ubuntu (this is my first post/reply). I only installed it this week, but I am amazed by it. It totally blew my expectations. Everything went a lot smoother than I expected.

However...  the graphics has been giving me the most problems. Although this was the first page that actually helped me, I still have a few problems.

So, without having read the 105 pages of this thread:
[COLOR=Blue]Some of my settings on the NVidia X Server settings app are greyed out - and I need to be able to adjust them, e.g.:
[/COLOR]
[LIST]
[*][COLOR=Blue]The screen resolution of the secondary display. The resolutions it allows me are a lot lower than I need, which is 1280 X 1024. (Under Windoze, I am able to set it a lot higher than what is available in the settings - with no deterioration)[/COLOR]
[*][COLOR=Blue]The refresh rate of the secondary screen (a CRT). It is totally greyed out - I cannot adjust it at all. The 60Hz drives me MAD!
[/COLOR]
[/LIST]
[COLOR=Blue][COLOR=Black]I doubt whether it is a driver limitation. Is it perhaps merely a matter of changing the settings in a file somewhere?

[/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue]I also do not seem to be able to save the configuration file (/etc/X11/xorg.conf) settings - and I therefore have to tell it that I have a second monitor every time.[/COLOR]

Can anyone help me out with this? Forgive such mundane questions from a newby!

Thanks.
[/COLOR][/COLOR]

---

### Post by philip5 on 2010-01-08
> **GeekGirl1 said:**
> Thank you! The 195-beta series installed perfectly with no errors. Synaptic removed nearly all of the previous versions, but some files remain. Can I remove files with versions 173, 180, 185, and 96 as shown below?

Should the package manager remove these files automatically (perhaps this information will help you)?
```
~> dpkg --get-selections | grep nvidia
nvidia-173-modaliases				install
nvidia-180-modaliases				install
nvidia-185-modaliases				install
nvidia-195-kernel-source			install
nvidia-195-libvdpau				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-glx-195					install
nvidia-glx-195-dev				install
nvidia-settings					install
```

Update: I removed files marked for deinstall with [Ubuntu Tweak](http://ubuntu-tweak.com/).

The only packages you need is nvidia-195-kernel-source, nvidia-195-modaliases and nvidia-glx-195. If you want vpdau support then you also need nvidia-195-libvdpau. nvidia-glx-195-dev is of course only needed if you have to compile stuff yourself against the nvidia 195 libs. nvidia-settings	is of course also handy. The rest is not needed (maybe I should be more strict to remove even them by setting them to conflict but at the same time they do no real harm).

Speaking about libvdpau there are some changes comming up there with how it will be packaged and mainly because it's now a spinn off open source project that nvidia have broken out from the rest of the nvidia drivers (some more nvidia parts will be truly open source this way, yeay!). There will be a non-nvidia-specific-package series for called libvpdau1 comming up (as can be found in debian sid recently) but they still only work with nvidia hardware as before. I'm looking over this for karmic when I have time so it doesn't break anything by pulling it out in the debian sid way compatible with karmic that will be the future.

---

### Post by llawwehttam on 2010-01-08
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. It's been almost a week since I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 




*Edit November 25 2009*: Latest nVidia 195.xx (BETA) Open GL 3.2 **[COLOR=Red]195.22[/COLOR]** Drivers:  [ 32 Bit ]("ftp://download.nvidia.com/XFree86/Linux-x86/195.22/") [64 Bit]("ftp://download.nvidia.com/XFree86/Linux-x86_64/195.22/")



*Edit December 11 2009*: Latest nVidia 195.xx (PRE-Release) Open GL 3.2 **[COLOR=Red]195.53[/COLOR]** Drivers:  [ 32 Bit ]("ftp://download.nvidia.com/XFree86/Linux-x86/190.53/") [64 Bit]("ftp://download.nvidia.com/XFree86/Linux-x86_64/190.53//")



*Edit October 30 2009*: Latest nVidia 190.xx (STABLE) Open GL 3.2 **[COLOR=Red]190.42[/COLOR]** Drivers:  [ 32 Bit ]("http://www.nvidia.com/object/linux_display_ia32_190.42.html")   [64 Bit]("http://www.nvidia.com/object/linux_display_amd64_190.42.html")




_**How to install nVidia drivers in Linux:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR=Red]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```**[COLOR=Red]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```**[COLOR=Red]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR=Red]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR=Red]7[/COLOR])** Then restart your computer   ```
sudo reboot
```**[COLOR=Red]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: ```
sudo sh ./Nxxx --uninstall
```or
```
sudo nvidia-uninstall
```**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.



_**Legacy Drivers**_


GeForce 5 series GPUs **[COLOR=Red]173.14.20 [/COLOR]** [32 bits]("ftp://download.nvidia.com/XFree86/Linux-x86/173.14.20/") , [64 bits]("ftp://download.nvidia.com/XFree86/Linux-x86_64/173.14.20/")

GeForce 5 series GPUs **[COLOR=Red]173.14.22 Pre-release [/COLOR]** [32 bits]("ftp://download.nvidia.com/XFree86/Linux-x86/173.14.22/") , [64 bits]("ftp://download.nvidia.com/XFree86/Linux-x86_64/173.14.22/")

GeForce 2 through GeForce 4 series **[COLOR=Red]96.43.13 [/COLOR]** [32 bits]("ftp://download.nvidia.com/XFree86/Linux-x86/96.43.13/") , [64 bits]("ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.13/")

GeForce 2 through GeForce 4 series **[COLOR=Red]96.43.14 Pre-release [/COLOR]** [32 bits]("ftp://download.nvidia.com/XFree86/Linux-x86/96.43.14/") , [64 bits]("ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.14/")

Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR=Red]71.86.11 [/COLOR]** [32 bits]("ftp://download.nvidia.com/XFree86/Linux-x86/71.86.11/") , [64 bits]("ftp://download.nvidia.com/XFree86/Linux-x86_64/71.86.11/")


*note*: Legacy drivers are being updated as well.


Good luck ;)

I can't thank you enough for that post. I have never got graphics drivers working so easily or so well in ubuntu. I have managed it before in debian but never ubuntu and I have been using various linux distros for over 7 years now!

Thank you again for that extremely easy to follow guide.

---

### Post by Buschbarber on 2010-01-08
Every time I receive a new Kernel revision, via Update Mgr, I am forced to go to Terminal Mode, at Boot, and I have to reinstall the Nvidia drivers. I am currently using Ubuntu Ultimate 2.5 64bit and Nvidia driver 195.22, but this has been true with any Nvidia driver I have been using.

Is that normal?

---

### Post by ratcheer on 2010-01-08
> **Buschbarber said:**
> Every time I receive a new Kernel revision, via Update Mgr, I am forced to go to Terminal Mode, at Boot, and I have to reinstall the Nvidia drivers. I am currently using Ubuntu Ultimate 2.5 64bit and Nvidia driver 195.22, but this has been true with any Nvidia driver I have been using.

Is that normal?

It is, for me. Someone told me I shouldn't have to, but I do. I think it has something to do with how we install it. If you install the binaries, manually, you have to reinstall them for each kernel update. But, I am told that if you install a package someone has put in their PPA, you don't have to reinstall.

I still prefer to get the binaries directly from nVidia.

Tim

---

### Post by AnyMation on 2010-01-09
> **AnyMation said:**
> Thanks a LOT for this thread.

I am a COMPLETE newby on Ubuntu (this is my first post/reply). I only installed it this week, but I am amazed by it. It totally blew my expectations. Everything went a lot smoother than I expected.

However...  the graphics has been giving me the most problems. Although this was the first page that actually helped me, I still have a few problems.

So, without having read the 105 pages of this thread:
[COLOR=Blue]Some of my settings on the NVidia X Server settings app are greyed out - and I need to be able to adjust them, e.g.:
[/COLOR]
[LIST]
[*][COLOR=Blue]The screen resolution of the secondary display. The resolutions it allows me are a lot lower than I need, which is 1280 X 1024. (Under Windoze, I am able to set it a lot higher than what is available in the settings - with no deterioration)[/COLOR]
[*][COLOR=Blue]The refresh rate of the secondary screen (a CRT). It is totally greyed out - I cannot adjust it at all. The 60Hz drives me MAD!
[/COLOR]
[/LIST]
[COLOR=Blue][COLOR=Black]I doubt whether it is a driver limitation. Is it perhaps merely a matter of changing the settings in a file somewhere?

[/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue]I also do not seem to be able to save the configuration file (/etc/X11/xorg.conf) settings - and I therefore have to tell it that I have a second monitor every time.[/COLOR]

Can anyone help me out with this? Forgive such mundane questions from a newbie!

Thanks.
[/COLOR][/COLOR]

After some searching and trying I got it resolved. I eventually had to edit the xorg.conf file... deep end stuff for a newbie! But, now I can venture into deeper waters... no swimming yet -> just to my knees :-)

---

### Post by Kosimo on 2010-01-09
> **llawwehttam said:**
> I can't thank you enough for that post. I have never got graphics drivers working so easily or so well in ubuntu. I have managed it before in debian but never ubuntu and I have been using various linux distros for over 7 years now!

Thank you again for that extremely easy to follow guide.


You're much more than welcome ;)

---

### Post by Kosimo on 2010-01-09
> **Buschbarber said:**
> Every time I receive a new Kernel revision, via Update Mgr, I am forced to go to Terminal Mode, at Boot, and I have to reinstall the Nvidia drivers. I am currently using Ubuntu Ultimate 2.5 64bit and Nvidia driver 195.22, but this has been true with any Nvidia driver I have been using.

Is that normal?


Yes, it is normal. As at every kernel upgrade you need to rebuild the drivers. If you read the first page of this thread you'll find a link to a post where teaches you how to create a script that will do this for you automatically at every single kernel upgrade.

Good luck,

---

### Post by darco on 2010-01-09
> **Kosimo said:**
> Yes, it is normal. As at every kernel upgrade you need to rebuild the drivers. If you read the first page of this thread you'll find a link to a post where teaches you how to create a script that will do this for you automatically at every single kernel upgrade.

Good luck,

That script is awesome...its rare that my nvidia drivers are not rebuilt after a kernel update.

---

### Post by Buschbarber on 2010-01-09
> **Kosimo said:**
> Yes, it is normal. As at every kernel upgrade you need to rebuild the drivers. If you read the first page of this thread you'll find a link to a post where teaches you how to create a script that will do this for you automatically at every single kernel upgrade.

Good luck,

Thank you very much!!

---

### Post by zucche on 2010-01-09
> **AaronP_ said:**
> Alternatively, you can open up nvidia-settings, change to the "X Server XVideo Settings" tab, and hit "Reset Hardware Defaults".

Hope that helps!

THANKS for that

---

### Post by Kosimo on 2010-01-10
Folks, 

I have just updated the drivers links to the latest official (190.53) and BETA (195.30) releases. Have a look at the first page if interested. 

Good luck ;)

---

### Post by mackjb on 2010-01-12
Hey folks,

My name is JB and I'm a Linux noob.

Just installed Ubuntu 9.10 and have been attempting to update my nvidia drivers by following the instructions here, but I'm running into some snags and was hoping for some help.

I can access terminal from Applications but every time I try to CTRL+ALT+1 my screen just scrambles and I have to come back to the gui. If I try to run the commands for installing the 190.53 drivers listed on the first page of this thread I get 'can't open blah, blah, blah' error. Obviously something is wrong and yes, I know a lot of it is me, but...

I'm confused and angered and close to pummeling my computer, can anyone advise?

Not sure if you need system specs, but briefly I'm running dual GTS 250's in SLI and Asus P6T mobo with Intel Core i7 920(slightly OC'd).

I surely will love you forever if you can help me out here. And thanks in advance.

JB

---

### Post by Kosimo on 2010-01-12
> **mackjb said:**
> Hey folks,

My name is JB and I'm a Linux noob.

Just installed Ubuntu 9.10 and have been attempting to update my nvidia drivers by following the instructions here, but I'm running into some snags and was hoping for some help.

I can access terminal from Applications but every time I try to CTRL+ALT+1 my screen just scrambles and I have to come back to the gui. If I try to run the commands for installing the 190.53 drivers listed on the first page of this thread I get 'can't open blah, blah, blah' error. Obviously something is wrong and yes, I know a lot of it is me, but...

I'm confused and angered and close to pummeling my computer, can anyone advise?

Not sure if you need system specs, but briefly I'm running dual GTS 250's in SLI and Asus P6T mobo with Intel Core i7 920(slightly OC'd).

I surely will love you forever if you can help me out here. And thanks in advance.

JB

Just a quick answer, you have to type **control + alt + F1  ** Not control + alt + 1

---

### Post by mackjb on 2010-01-12
> **Kosimo said:**
> Just a quick answer, you have to type **control + alt + F1  ** Not control + alt + 1

I know, just a typo, sorry about that.

JB

---

### Post by Tweak42 on 2010-01-13
> **mackjb said:**
> Hey folks,

My name is JB and I'm a Linux noob.

Just installed Ubuntu 9.10 and have been attempting to update my nvidia drivers by following the instructions here, but I'm running into some snags and was hoping for some help.

I can access terminal from Applications but every time I try to CTRL+ALT+1 my screen just scrambles and I have to come back to the gui. If I try to run the commands for installing the 190.53 drivers listed on the first page of this thread I get 'can't open blah, blah, blah' error. Obviously something is wrong and yes, I know a lot of it is me, but...

I'm confused and angered and close to pummeling my computer, can anyone advise?

Not sure if you need system specs, but briefly I'm running dual GTS 250's in SLI and Asus P6T mobo with Intel Core i7 920(slightly OC'd).

I surely will love you forever if you can help me out here. And thanks in advance.

JB

I've never used a SLI setup, but is it possible when you CTRL+ALT+F1 to terminal that it is being outputted to a different DVI/VGA port than your monitor is plugged into?

Along those lines, you can also try pulling 1 of the vid cards and doing a single card install then adding the SLI card back in.

---

### Post by VastOne on 2010-01-13
> **mackjb said:**
> I know, just a typo, sorry about that.

JB

Do you see the same behavior if you do ctrl + alt + f2 or f3 or f4 or f5 or f6?

---

### Post by mackjb on 2010-01-13
> **VastOne said:**
> Do you see the same behavior if you do ctrl + alt + f2 or f3 or f4 or f5 or f6?
  
Yes, same behavior. Something I haven't tried yet, but what if I were to boot into recovery mode and install the driver? would that work when rebooting?

JB

---

### Post by VastOne on 2010-01-13
> **mackjb said:**
> Yes, same behavior. Something I haven't tried yet, but what if I were to boot into recovery mode and install the driver? would that work when rebooting?

JB

Yes you can do this. Every time there is a kernel update I update nVidia this way.  Just make sure you have the driver on your pc and that you have the instructions on what to do.

---

### Post by giovanni420 on 2010-01-13
I have a GeForce 8200M. What are the drivers right for me? 190.53?

---

### Post by VastOne on 2010-01-13
> **giovanni420 said:**
> I have a GeForce 8200M. What are the drivers right for me? 190.53?

I have a 9500 and have 190.42 loaded and they are great

Edit

After seeing your post that 190.53 is now the stable release I have loaded it and it is great too

---

### Post by Kosimo on 2010-01-14
> **VastOne said:**
> I have a 9500 and have 190.42 loaded and they are great

Edit

After seeing your post that 190.53 is now the stable release I have loaded it and it is great too

I try to keep the first page of this thread always updated with the latest releases, so you can have a look every once in a while.

---

### Post by VastOne on 2010-01-14
> **Kosimo said:**
> I try to keep the first page of this thread always updated with the latest releases, so you can have a look every once in a while.

Indeed...I look everyday and somehow missed it, I also have instant notification for this thread on for your updates and still missed it..

Appreciate all you do here Kosimo...Thanks
:D

---

### Post by mackjb on 2010-01-14
Update on my situation

I finally got the driver to install as per the instructions on the first page of this post(thank you for those by the way), however, I get a black screen and lockup right after GRUB boot selection. Also, the recommended driver from the Hardware Drivers menu gives the same result so I'm convinced it has something to do with my SLI config. I'm giving up on this for the time being, I'll just have to do without all the graphical bells and whistles until I learn a little more. 

If someone could give me the command for uninstalling a driver that would be great; I really don't want to reinstall.

I'm very discouraged, I mean it's just a video driver, I feel it shouldn't be this complicated, but like I said, I'm a complete noob when it comes to Linux. I'm going to back off a bit, maybe buy a book or something before I tackle this again. I want to thank everyone for their help, and I'm sure I'll have other questions on less advanced issues in the very near future.

JB

---

### Post by Kosimo on 2010-01-14
> **mackjb said:**
> Update on my situation

I finally got the driver to install as per the instructions on the first page of this post(thank you for those by the way), however, I get a black screen and lockup right after GRUB boot selection. Also, the recommended driver from the Hardware Drivers menu gives the same result so I'm convinced it has something to do with my SLI config. I'm giving up on this for the time being, I'll just have to do without all the graphical bells and whistles until I learn a little more. 

If someone could give me the command for uninstalling a driver that would be great; I really don't want to reinstall.

I'm very discouraged, I mean it's just a video driver, I feel it shouldn't be this complicated, but like I said, I'm a complete noob when it comes to Linux. I'm going to back off a bit, maybe buy a book or something before I tackle this again. I want to thank everyone for their help, and I'm sure I'll have other questions on less advanced issues in the very near future.

JB



Bad to know that you give up ;)

if you want to uninstall the drivers just type:


```
sudo nvidia-uninstall
```

---

### Post by VastOne on 2010-01-14
> **mackjb said:**
> Update on my situation

I finally got the driver to install as per the instructions on the first page of this post(thank you for those by the way), however, I get a black screen and lockup right after GRUB boot selection. Also, the recommended driver from the Hardware Drivers menu gives the same result so I'm convinced it has something to do with my SLI config. I'm giving up on this for the time being, I'll just have to do without all the graphical bells and whistles until I learn a little more. 

If someone could give me the command for uninstalling a driver that would be great; I really don't want to reinstall.

I'm very discouraged, I mean it's just a video driver, I feel it shouldn't be this complicated, but like I said, I'm a complete noob when it comes to Linux. I'm going to back off a bit, maybe buy a book or something before I tackle this again. I want to thank everyone for their help, and I'm sure I'll have other questions on less advanced issues in the very near future.

JB

```
sudo apt-get --purge remove nvidia*

```

Don't be too discouraged.  When I first started I was in a similar situation, and I incorrectly assumed that the answer would come to via a guru in 10 seconds flat.

The answer is here, or google.  Just be patient and research it to the detail. 

I would search google with Ubuntu + SLI + nVidia + your specific card + any other variable that is specific to yours

This one shows several people using your card on Ubuntu, perhaps they can help

[http://ubuntuforums.org/showthread.php?t=1378602](http://ubuntuforums.org/showthread.php?t=1378602)

and here at the nVidia site is detailed instruction specific to Linux

[http://ubuntuforums.org/showthread.php?t=1378602](http://ubuntuforums.org/showthread.php?t=1378602)

Good luck

---

### Post by Colinchocolate on 2010-01-16
I went to try to install the driver for my nVidia GeForce 6200, and it says that it can't run ./Nxxx. I followed the instructions to the note.

---

### Post by VastOne on 2010-01-17
> **Colinchocolate said:**
> I went to try to install the driver for my nVidia GeForce 6200, and it says that it can't run ./Nxxx. I followed the instructions to the note.

Which driver did you try to install?

You may want to check out this thread

[http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

---

### Post by Kosimo on 2010-01-19
> **Colinchocolate said:**
> I went to try to install the driver for my nVidia GeForce 6200, and it says that it can't run ./Nxxx. I followed the instructions to the note.

Are you writting ./Nxxx?

the x's are examples, you have to write the entire filename, (which can automatically be done if you hit TAB after writting the first cap N)

---

### Post by howcanireachthesekids on 2010-01-21
Just installed the latest Nvidia Accelerated Graphics driver for my 9200M GS card on my HP Pavilion DV6-1020el following the guide on OP's post. Everything went fine and smooth. In less then 2 minutes work :) Feels good man :popcorn:

---

### Post by VastOne on 2010-01-22
Information post

I was happily using 190.53 for several days when on a reboot I was unable to enable Visual Effects which in turn disable compiz 

I put 190.42 back on and everything went back to normal.  I will retry 190.53 later to see if I can run it again and post the results

---

### Post by knighthaq on 2010-01-30
your instructions worked but i had to do it from boot up i cant get cntrl+alt+f1 to work garbles my screen all up with lots of colors am i missing something?

---

### Post by PureRumble on 2010-01-31
Guys, are you aware of these instructions:

[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

?

I followed them and they worked flawlessly on my laptop. Just install a launchpad ppa and get the drivers as you get any packages.

Any reason why you should do it manually? :)

---

### Post by the-penguin on 2010-01-31
hey guys...

ok im sorry for the noobie intro but i've been wondering if any of could help me with the issue that im having with my graphics card.
i have a NVIDIA GeForce 7100 / nForce 620i ( i know no the best one) and when i install my drive the display will not work... i have been working on this issue for the past week with no victory.
my desktop currently runs in low graphics mode because the "device" is not found ( according to the log).
I did make it to the login screen before but once i logged in it said that the imput is not supported.
[im running on 9.10 by the way]

could you help me out?
regards,:???:
the-penguin

---

### Post by knighthaq on 2010-01-31
yeah it gives you and older driver and it just wouldnt work on my pc, i did try them. but manually worked best for me after i figured out how to do the permissions to save my settings

---

### Post by Caps18 on 2010-02-01
If I am upgrading my motherboard/GPU from a 6200 to a built-in 8800, do I need to uninstall the old driver before I can install the new one?

The second issue is that I do not have gcc installed on my machine, is there some way to get pre-compiled drivers?  I am running 7.10 still, and it won't let me download any updates or use apt-get since it can't connect to the IP address it has.  I think this is where I left off and got stuck at.


Thanks!

---

### Post by NoaHall on 2010-02-01
> **Caps18 said:**
> If I am upgrading my motherboard/GPU from a 6200 to a built-in 8800, do I need to uninstall the old driver before I can install the new one?

The second issue is that I do not have gcc installed on my machine, is there some way to get pre-compiled drivers?  I am running 7.10 still, and it won't let me download any updates or use apt-get since it can't connect to the IP address it has.  I think this is where I left off and got stuck at.


Thanks!

Yes.

---

### Post by markinf on 2010-02-01
Isn't this way to recompile the driver with the an updated kernel outdated??

---

### Post by Kosimo on 2010-02-05
Folks

New 195.36.03 BETA drivers has been released.


Here the changelog:

>     *  Fixed a regression that made the "TVStandard" X configuration option cause system hangs with products from the GeForce 6 and 7 series.
    * Worked around a bug in some AUO laptop flat panels where the native mode in the EDID is invalid, leading to a 640x480 desktop repeated six times across the screen.
    * Increased the maximum number of slices supported by VDPAU for MPEG-2 streams, in order to cope with the region 1 DVD "A Christmas Story".
    * Added unofficial preliminary support for xorg-server video driver ABI version 7, including xorg-server-1.7.99.2.
    * Fix the soname of libvdpau_nvidia.so.1 and libvdpau_trace.so.1 to match their filenames.



Download links at the first page of this thread.

Good luck.

---

### Post by dBuster on 2010-02-05
Anyone else running Jaunty with the latest kernel update as of this morning???  

The latest kernel totally hosed my nvidia and now I have hours of trying to get the nvidia re-installed to work with that kernel!

---

### Post by LazKapitaL on 2010-02-06
There are 3 .run file on beta driver list. 2 of them is 24mb and last one is 40 mb. Which one should be installed?

---

### Post by Amorget on 2010-02-06
> **LazKapitaL said:**
> There are 3 .run file on beta driver list. 2 of them is 24mb and last one is 40 mb. Which one should be installed?

For the 64 bit OS I know you use the 3rd, which includes the 32 bit binaries (or something like that).

---

### Post by sdowney717 on 2010-02-06
> The latest kernel totally hosed my nvidia and now I have hours of trying to get the nvidia re-installed to work with that kernel!

Yes, it did for me too.
But it took less than 10 minutes

I keep a copy of the Nvidia driver 195.30.
I rename it to something simple
Boot it into recovery mode
login
navigate to the directory with the file
run it like this 
sudo ./nvidia19530.run
sudo reboot

It does not complain about run levels and it sets up easy.
reboot and it is up and running in X

---

### Post by eival on 2010-02-07
okay quick question, im on a fresh 8.04 and never installed the proprietary NVIDIA 3D drivers so i assume there was nothing to uninstall as stated in the guide, if im wrong please tell me if i can fix it now...

anyways i just installed the latest 190.50 driver after running into an issue of not having the libc development package isntalled(which shows how fresh my install was since it wasnt stated in the guide :p), but once everything was done and i rebooted, it started in Low Graphics Mode.:popcorn:

so i brought up the terminal an 

[HTML]sudo nvidia-uninstall[/HTML]

then attempted to reinstall again, how ever this time i simply restarted gdm and its fine as i type this, now the only time i ever restart my laptop is when system updates mandate it, like the kernal update a few days ago, those updates are the best:)

so needless to say im weary of restarting just for the hell of it to see if it boots into low graphics mode again. but what exactly CAUSES that to happen in the first place?

and one last note, did anyone else notice the 190.53 driver take especially longer to install than previous versions?

it seemed to hang on almost every step.

---

### Post by shane2peru on 2010-02-08
Thanks for how-to, worked like a charm.  I didn't realize Nvidia was so far ahead of the Ubuntu restricted drivers.  I have the Nvidia Geoforce 9500 GT card.  

Shane

---

### Post by crjackson on 2010-02-08
Could my video driver cause my Webcam to stop working properly?

---

### Post by Kosimo on 2010-02-09
> **crjackson said:**
> Could my video driver cause my Webcam to stop working properly?

Yes, it happened to me as well...  Unfortunately I really have no clue why this is happening.   Something releated with x.org maybe?

---

### Post by crjackson on 2010-02-09
> **Kosimo said:**
> Yes, it happened to me as well...  Unfortunately I really have no clue why this is happening.   Something releated with x.org maybe?

I suspected as much.  Hopefully it will clear up with the next driver update.  It sure is annoying.

---

### Post by dBuster on 2010-02-10
> **eival said:**
> okay quick question, im on a fresh 8.04 and never installed the proprietary NVIDIA 3D drivers so i assume there was nothing to uninstall as stated in the guide, if im wrong please tell me if i can fix it now...

anyways i just installed the latest 190.50 driver after running into an issue of not having the libc development package isntalled(which shows how fresh my install was since it wasnt stated in the guide :p), but once everything was done and i rebooted, it started in Low Graphics Mode.:popcorn:

so i brought up the terminal an 

[HTML]sudo nvidia-uninstall[/HTML]

then attempted to reinstall again, how ever this time i simply restarted gdm and its fine as i type this, now the only time i ever restart my laptop is when system updates mandate it, like the kernal update a few days ago, those updates are the best:)

so needless to say im weary of restarting just for the hell of it to see if it boots into low graphics mode again. but what exactly CAUSES that to happen in the first place?

and one last note, did anyone else notice the 190.53 driver take especially longer to install than previous versions?

it seemed to hang on almost every step.

Check my thread out:  [http://ubuntuforums.org/showthread.php?t=1399279]("http://ubuntuforums.org/showthread.php?t=1399279")

I had a similar issue with the low graphics mode...  What I mentioned in my post worked to correct my issues with the low graphics...

---

### Post by eival on 2010-02-10
okay the issue is when the boot loader gets to "running local boot scripts" it had a location but i forgot to write it down, if its important i can do that if someone asks.

it just hangs there, the screen goes black about 3 times then low graphics mode starts.

i went as far to actually uninstall every display driver from Synaptic to force it to use the manual Nvidia card, but when i restarted it just hanged on "running local boot scripts" so i used crtl+alt+f1 to bring up the command line then just installed the manual driver and restarted gdm and its working fine.

so im not an expert but im willing to be theres something in the local boot script that needs to be changed to fix this issue, how ever i dont know anything about that, so hopefully someone can figure it out:popcorn:

---

### Post by zero7404 on 2010-02-10
my battle with getting my hardware to function properly in ubuntu 9.10 has been, well, a battle.

after a fresh install of 9.10 and ensuing updates via update manager, restarted the computer and proceeded to install nvidia's latest driver package (190.53) for my hardware (Dell XPS M1730, 8800M GTX SLI). i installed the package properly, got no errors.

after a few restarts I began to get a fuzzy desktop after logging in, fuzzy as in the screen lines in some locations start to play horizontally.

so i stopped xserver and restarted it and the fuzziness goes away.
but then it happens again on a subsequent reboot. so i tried enabling sli with the command:

sudo nvidia-xconfig --sli=auto

then restarted the computer. now the display won't even get to the login, it remains off (completely dark), after the white ubuntu logo disappears (after startup).

now i'm at a loss to figure out why it's behaving this way, but would like to proceed with uninstalling the nvidia driver completely, then maybe trying to install it again. or if there is a fix for this ? or if my safest bet is to use the recommended restricted driver by ubuntu (185) ?

---

### Post by eival on 2010-02-10
i figured out the issue!

[http://ubuntuforums.org/showthread.php?t=1088985](http://ubuntuforums.org/showthread.php?t=1088985)

i had to remove a few more linux-restricted-modules

and now it runs the manual nvidia driver on reboot

---

### Post by zero7404 on 2010-02-10
is there anyone that can help me out with fixing this problem i've got so i can get ubuntu back up and running ?
i have so far reinstalled ubuntu several times in the past year due to misc problems and issues with updates and display driver problems. i am getting tired of configuring the OS to the way I like it, then getting shot in the foot with this display driver problem. back when i was using 8.10 i had no issues with my sli setup and the system ran fine.....

---

### Post by eival on 2010-02-10
> **zero7404 said:**
> is there anyone that can help me out with fixing this problem i've got so i can get ubuntu back up and running ?
i have so far reinstalled ubuntu several times in the past year due to misc problems and issues with updates and display driver problems. i am getting tired of configuring the OS to the way I like it, then getting shot in the foot with this display driver problem. back when i was using 8.10 i had no issues with my sli setup and the system ran fine.....

did you check the thread i posted?

your issue is prolly caused by the other preinstalled drivers still on your system, delete all those files and your manual driver will work fine

---

### Post by Kosimo on 2010-02-15
Folks:

Legacy drivers 173.14.25, 96.43.16, and 71.86.13 has been updated

compatibility with newer kernels and x.org with other minor changes.

Download links at the first page of this thread. 


Good luck

---

### Post by chalewa on 2010-02-16
i just did a fresh install of 9.10 as I just bought a new nvidia card... geforce 210 for use with htpc, however, i seem to be struggling with the drivers. 

i installed 190.53 and the install seemed to work well, but the quality of the picture is terrible. i have the card hooked up to a 46 hdtv with a native resolution of 1920x1080. first i had to adjust the overscan compensation as the picture was too big for the screen, and video playback is still terrible. i feel like i am missing something. 

does anyone have any ideas?

thanks

---

### Post by Objekt on 2010-02-17
It would help to know how you're hooking things up.  Are you using an HDMI cable to connect to the TV?  DVI?  Old fashioned VGA cable?  Please also mention the brand and model of your TV.

I don't have an HDTV, but I do have an LCD monitor of HDTV resolution (Acer P244Wbd) that I use as a second monitor, with the Nvidia 190.53 drivers.  My video card is a GeForce 9800 GTX+, with two DVI outputs and no HDMI, so I use a DVI cable to hook up the monitor.  I have no problems with this setup.

---

### Post by eival on 2010-02-19
> **chalewa said:**
> i just did a fresh install of 9.10 as I just bought a new nvidia card... geforce 210 for use with htpc, however, i seem to be struggling with the drivers. 

i installed 190.53 and the install seemed to work well, but the quality of the picture is terrible. i have the card hooked up to a 46 hdtv with a native resolution of 1920x1080. first i had to adjust the overscan compensation as the picture was too big for the screen, and video playback is still terrible. i feel like i am missing something. 

does anyone have any ideas?

thanks

my GeForce Go 6150 only lets me output up to 1050 thru VGA in a 4:3 format, even tho its going to a widescreen 1080p capable tv, so i have to either downgrade it to 768 which is the next lowset wide screen setting, or i use a combination of 1050 4:3, then set my tv to stretch mode and when i drag VLC to it, i expand it to fit the screen then change the video's aspect ratio to 4:3 an it looks proper..

but after i bought a WD Live player i just use that to watch movies now

---

### Post by cdekter on 2010-02-21
> **chalewa said:**
> i just did a fresh install of 9.10 as I just bought a new nvidia card... geforce 210 for use with htpc, however, i seem to be struggling with the drivers. 

i installed 190.53 and the install seemed to work well, but the quality of the picture is terrible. i have the card hooked up to a 46 hdtv with a native resolution of 1920x1080. first i had to adjust the overscan compensation as the picture was too big for the screen, and video playback is still terrible. i feel like i am missing something. 

does anyone have any ideas?

thanks

Try the latest beta drivers (195.30). I have a 310 (very similar to 210) and had all kinds of problems with 190.53.

---

### Post by Kosimo on 2010-02-27
Good morning Folks..
nVidia has just released a brand new Stable Driver which replaces the current BETA.

**195.36.08**

Changelog: 

>     *  Added support for the following GPUs:
          o Quadro FX 880M
          o GeForce GTS 350M
          o GeForce GTS 360M
    * Fixed a bug that caused screen corruption after an application released a GLX_NV_present_video device.
    * Fixed an X server crash caused by starting nvidia-settings while X was not on the active VT.
    * Fixed brightness control hotkeys on some laptops.
    * Fixed an nvidia-settings bug that produced many "Bad argument" warning messages when running nvidia-settings --query all.
    * Fixed an installer bug that produced the following message:
      Code:

      WARNING: Unable to perform the runtime configuration check for library
      'libGL.so.1' ('/usr/lib/libGL.so.195.36.03'); assuming successful installation.

    * Fixed a bug that caused G-Sync stereo synchronization to fail sometimes when enabling frame lock.
    * Fixed a bug that caused OpenGL applications to occasionally crash with "double free or corruption" messages when exiting.
    * On GPUs with VDPAU feature set A, enhanced VDPAU's handling of some corrupted or incorrectly formatted MPEG-1/2 streams. This solves a reported issue with "0testbad.mpg".
    * Fixed a bug in the VDPAU video mixer that caused chroma aberrations, and corruption in the right-hand few columns of pixels, when post- processing video surfaces with widths not an exact multiple of 4 pixels.
    * Fixed a bug that prevented the GPUFanControlState attribute from being set on the nvidia-settings command line.



Download links at the first page of this thread.

Enjoy!

---

### Post by warped6 on 2010-03-04
Thank you!

After loading on the latest kernel updates, my Nvidia card was all wonky. After following your HOWTO I'm now back up and running on the latest drivers.

Thank you. Thank you. Thank you. :guitar:

---

### Post by Kosimo on 2010-03-04
> **warped6 said:**
> Thank you!

After loading on the latest kernel updates, my Nvidia card was all wonky. After following your HOWTO I'm now back up and running on the latest drivers.

Thank you. Thank you. Thank you. :guitar:


Nice to know that this thread still helps people ! 

:popcorn:

---

### Post by ratcheer on 2010-03-05
**WARNING:** nVidia seems to be having some trouble with some drivers they have released. If you go to their main download page, they are only talking about 196.175 WHQL driver, but several other drivers have also been removed from their download site. For example, if you go to page 1 of this thread and click the link for the 195.36 driver, you will find that it is not currently available.

The issue has to do with the latest drivers severely overheating video cards, often to the point of failure.

I am wondering if I should revert to the 190 driver? I am currently running 195.36.08. Does anyone have further info?

Tim

---

### Post by AaronP_ on 2010-03-05
> **ratcheer said:**
> 
I am wondering if I should revert to the 190 driver? I am currently running 195.36.08. Does anyone have further info?


See the announcement here: [http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

---

### Post by MC707 on 2010-03-05
When I click on the first link for 64 bit > Edit February 27 2010: Latest nVidia 195.xx (STABLE) 195.36.08 Drivers:  32 Bit  . 64 Bit
I get a > 550 /XFree86/Linux-x86_64/195.36.08/: No such file or directoryerror.

Regards

EDIT:
> See the announcement here: [http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

Oh now I see.

---

### Post by Kosimo on 2010-03-06
Folks, thanks for the heads up. 

First page links have been corrected. Let's wait 'till a new official nVidia announcement is made so we can go back to the latest release.

---

### Post by BudworthTDog on 2010-03-07
Okay so I installed a new graphics card to my computer. nVIDIA GeForce 210. Everything with my on board video card was working fine I just put it in to ease up on the system ram and such. When watching movies, avi youtube ect there are two problems that arise. One is an intermitant horizontal distorted line that rolls down the screen. To best describe the "line" its as if the top and bottom layers shift sideways opposite of eachother slightly and then roll down the screen. The other is when a movie changes cameras the shift is rough, kind of like the movie "blinks" this also often triggers the "rolling line"

At first it was very consistant but that was before I installed the nVIDIA proprietary drivers, this improved the problem it was still there. Upon further research I discovered this thread.

[http://ubuntuforums.org/showthread.p...ia+geforce+210]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+geforce+210")

I installed driver 190.53. This improved the problem even further but its till there. I tried both the hdmi and vga input and they both have the same issue. At this point I belive its just a configuration in the NVIDIA X server settings. Does anyone know the best settings.

---My main use for this computer is to watch movies and tv shows, no real gaming involved and 3d isnt all that important (i think)
---It is hooked up to a 40" samsung 60mhz tv
---hooked up hdmi
---nvidia geforce 210 graphics card
---using vcd player (same problem with other players) 

Forgive me if this all is a dumb question, I'm new to all this.

---

### Post by cdekter on 2010-03-09
This sounds like a vsync issue to me. Are you using compositing/Compiz at all? If so, currently the nVidia drivers don't seem to be able to vsync videos if compositing is turned on. Disable it and your problem will probably go away.

As for youtube, this can't be fixed as Flash on Linux is garbage (or just garbage all round) and cannot be made to play video smoothly or with vsync.

---

### Post by BudworthTDog on 2010-03-10
> **cdekter said:**
> This sounds like a vsync issue to me. Are you using compositing/Compiz at all? If so, currently the nVidia drivers don't seem to be able to vsync videos if compositing is turned on. Disable it and your problem will probably go away.

As for youtube, this can't be fixed as Flash on Linux is garbage (or just garbage all round) and cannot be made to play video smoothly or with vsync.


Awesome it worked like a charm. It took me a while to figure out how to do it, I didnt have compiz, I didnt even know what it was. After some research I couldnt seem to find a concreat answer on how to disable compositing. The jist I got from it was it had to do with special desktop effects. I just decided to poke around and ended up going to System--->Preference--->Apperance--->Visual effects--->None (normal is what was selected when I first opened it up) I've watched several videos that I know were doing it before and they all look much better. If you know of anything more I should do to further disable it let me know but I believe I am set.

---

### Post by danjp2000 on 2010-03-10
Hello, I am having difficulty in trying to get the nvidia drivers installed since I upgraded to the 2.6.32 kernel. Specifically I am using the PAE kernel with the 195 version driver. I upgraded the kernel and tried to reinstall the nvidia driver via synaptic (from [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu)) and while it looks like it installs ok it is not loading and I can only login using the default vesa driver. This driver works fine in the 2.6.31 kernels. I have tried removing and reinstalling the kernel and the driver multiple times with no luck. Also, when I do a ctrl-alt-F1 to try a manual install using the driver from the nvidia site, I only get a blank screen. The system is still active so if I blindly login and do a reboot the system starts. Als, I can not get to the recovery terminal as the screen hangs up. Any ideas on what I can do to sort this out would be greatly appreciated.

---

### Post by Jake2500 on 2010-03-11
Hi, ive been reading through as many pages as i can (120+ is a small book)
and can't seem to find a solution to my problem. I have a XFX Geforce 9600 GSO and ive decided to install the NVIDIA-Linux-x86-190.53-pkg1.run driver but when i do dgm loads to a solid blue screen (not no signal the gfx card is outputting solid blue) i can use ctrl+alt+backspace to get to terminal and sudo cp failsafe xorg.conf but i can't get the nvidia generated xorg.conf to work

xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Tue Dec  8 21:04:28 PST 2009

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "1440x900_60.00"
    EndSubSection
EndSection

```

---

### Post by Kosimo on 2010-03-17
Folks, finally 195.xx drivers with the fan control bug solved!

195.36.15

Changelog: 

>     *  Fixed a bug that caused the X server to crash when rendering occurred while the X server was not on the active VT.
    * Fixed a regression that caused the driver to fail to properly adjust the GPU fan speed on some GPUs.
    * Fixed a bug that prevented performance level transitions on recent GPUs with SDDR3 and GDDR5 memory.


Download links at the first page of this thread. 

Good luck! ;)

---

### Post by ratcheer on 2010-03-17
I have been using 195.36.15 since yesterday morning. It seems to be fine, no problems at all.

Tim

---

### Post by Kosimo on 2010-03-18
195.36.07.03 STABLE **[COLOR="Red"]OpenGL 3.3[/COLOR]** Available!


Download links at the first page of this thread.

Good luck!

---

### Post by brenosabino on 2010-03-18
I'm using Ubuntu 9.10 with a Geforce 9600GT and 190.53 drivers, should i update to 195.36.07.03?

---

### Post by Buschbarber on 2010-03-18
> **brenosabino said:**
> I'm using Ubuntu 9.10 with a Geforce 9600GT and 190.53 drivers, should i update to 195.36.07.03?

I am using Ubuntu 9.10 with a 9800GTX+ and 195.36.15, without any problems.

---

### Post by Kosimo on 2010-03-18
> **brenosabino said:**
> I'm using Ubuntu 9.10 with a Geforce 9600GT and 190.53 drivers, should i update to 195.36.07.03?

If you are not a developer that specifically needs to use OpenGL 3.3 I wouldn't recommend you to upgrade to 195.36.07.03. 

But, I would certainly suggest you to move to the latest pre-release of 195.xx which contains a bunch of bug-fixes and performance increases.

---

### Post by 5735guy on 2010-03-20
How To Install Nvidia 185.xx, 190.xx and 195.xx Drivers In Ubuntu, From A Launchpad Repository
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

### Post by Kosimo on 2010-03-22
Guys, latest driver 195.36.15 pre-release have been promoted to the current Stable Release.


Links af the first page of this thread.

Good luck!

---

### Post by cdekter on 2010-03-22
> **Kosimo said:**
> Guys, latest driver 195.36.15 pre-release have been promoted to the current Stable Release.


Links af the first page of this thread.

Good luck!

On my G310M the 196.36.15 drivers have worse OpenGL performance than 195.30 (at least under Kwin).

---

### Post by fatality_uk on 2010-03-23
My performance has dropped slightly, but I get less gfx artifacts, so a light trade off. I am now getting avg 80 fps in ETQW with all settings on high @ 1280x1024. Previously I was getting 140fps avg

---

### Post by Kosimo on 2010-03-23
> **fatality_uk said:**
> My performance has dropped slightly, but I get less gfx artifacts, so a light trade off. I am now getting avg 80 fps in ETQW with all settings on high @ 1280x1024. Previously I was getting 140fps avg

So I understand that you still get artifacts?

---

### Post by fatality_uk on 2010-03-23
I'll grab a screenshot this evening when I get home to show. I have noticed a great imporvement but I dont have AA on.

---

### Post by Jason Peters on 2010-03-24
> **Kosimo said:**
> If you are not a developer that specifically needs to use OpenGL 3.3 I wouldn't recommend you to upgrade to 195.36.07.03. 

But, I would certainly suggest you to move to the latest pre-release of 195.xx which contains a bunch of bug-fixes and performance increases.
I finally successfully installed the 195.36.15 drivers using your instructions on the first page of this thread.

I'm a major Linux noob, so please this possibly redundant question.  To clarify, you're saying that non-developers do NOT need to install the 195.36.07.03 OpenGL drivers?

Also, I noticed after the reboot that Hardware Drivers states "No proprietary drivers in use on this system."  Is this to be expected?

Thanks in advance.

---

### Post by cdekter on 2010-03-24
> **Jason Peters said:**
> I finally successfully installed the 195.36.15 drivers using your instructions on the first page of this thread.

I'm a major Linux noob, so please this possibly redundant question.  To clarify, you're saying that non-developers do NOT need to install the 195.36.07.03 OpenGL drivers?

Also, I noticed after the reboot that Hardware Drivers states "No proprietary drivers in use on this system."  Is this to be expected?

Thanks in advance.

I think what he was saying was that 195.30 is fine for most users. Since then 196.36.15 have been promoted to stable, so it's probably safe to use them now. Having said that, the 195.30 have significantly better 3D perforamnce.

The proprietary driver doodad only works if you install the drivers through it's interface - it won't detect the nVidia drivers you installed manually using the nVidia installer.

---

### Post by AaronP_ on 2010-03-24
cdekter, what do you mean by "significantly better 3D performance"?  Can you please attach nvidia-bug-report.log.gz files from both 195.36.15 and 190.53, and describe exactly what you're doing to measure the performance?

---

### Post by Jason Peters on 2010-03-24
> **cdekter said:**
> I think what he was saying was that 195.30 is fine for most users. Since then 196.36.15 have been promoted to stable, so it's probably safe to use them now. Having said that, the 195.30 have significantly better 3D perforamnce.

The proprietary driver doodad only works if you install the drivers through it's interface - it won't detect the nVidia drivers you installed manually using the nVidia installer.
There are two links on the first page, though, one for drivers and one for OpenGL drivers.  I'm wondering if it is necessary to install the OpenGL in addition to the main drivers.

That makes sense about the installer.  How does one properly uninstall  drivers installed with the nvidia installer when it comes time to upgrade?

---

### Post by Kosimo on 2010-03-25
> **Jason Peters said:**
> There are two links on the first page, though, one for drivers and one for OpenGL drivers.  I'm wondering if it is necessary to install the OpenGL in addition to the main drivers.

That makes sense about the installer.  How does one properly uninstall  drivers installed with the nvidia installer when it comes time to upgrade?

Jason.

The other ones aren't "opengl" drivers.  Open GL is a 3d standard that has just arrived to the version 3.3 which that specific version supports. But for now, there are NO SCENARIOS where you'll need this support as the are no OpenGL 3.3 apps. So by using the latest stable drivers you are much more than safe and covered, having of course OpenGL support as well, but not for the version 3.3.

And as have been said, when you install the proprietary drivers manually you won't see them in the "proprietary drivers tool" instead you'll be able to open nVIDIa x server settings, in proprieties. 


Just keep in mind, that when you'll have a kernel upgrade you won't be able to load x.org. If you want to be "safe" , keep a copy of the installed driver, so in the event that you can't load x.org, you can uninstall the driver and install it again in the console, or, follow the alternative process to let the system automatically compile the driver for the new kernel as explained in the first page. 

Good luck.

---

### Post by AaronP_ on 2010-03-25
> **Jason Peters said:**
> How does one properly uninstall  drivers installed with the nvidia installer when it comes time to upgrade?

nvidia-uninstall

(or old drivers, nvidia-installer --uninstall)

---

### Post by cdekter on 2010-03-25
> **AaronP_ said:**
> cdekter, what do you mean by "significantly better 3D performance"?  Can you please attach nvidia-bug-report.log.gz files from both 195.36.15 and 190.53, and describe exactly what you're doing to measure the performance?

I mean that the framerate for Kwin effects is drastically lower with the newer driver. When I get home tonight I'll turn on the framerate counter to get an exact measurement and post that here (and get the logs if I have time).

---

### Post by static_hf on 2010-03-26
I got a problem using this method.

After i do sudo sh ./Nxxx a new window appears with following note : It appears that you are using X server. Driver could not be installed.

What should i do? Sorry if you already replied to this problem cause i can't read all 100 pages of replies.:KS

---

### Post by TheNessus on 2010-03-26
> **static_hf said:**
> I got a problem using this method.

After i do sudo sh ./Nxxx a new window appears with following note : It appears that you are using X server. Driver could not be installed.

What should i do? Sorry if you already replied to this problem cause i can't read all 100 pages of replies.:KS
you should kill gdm or kdm, whichever one you're running at the moment. (GNOME or KDE, gdm/kdm)

```
sudo /etc/init.d/gdm stop
```

After installing, "startx".

---

### Post by Kosimo on 2010-03-26
> **TheNessus said:**
> you should kill gdm or kdm, whichever one you're running at the moment. (GNOME or KDE, gdm/kdm)

```
sudo /etc/init.d/gdm stop
```

After installing, "startx".



just for the record:

If keeps not working even after doing this, try to go back to your previous ttl (control +F7) and make sure that there are no windows poping up asking to run in low graphics mode.

Good luck

---

### Post by HunterZ on 2010-03-27
I'm running 196.36.15 on Ubuntu 9.10 x64 on my Dell M1730 laptop with nVidia 8700M GT SLI video and a 1920x1200 (16:10) screen. I have 2 issues:

1. When running Baldur's Gate 1 full-screen in Wine, the 640x480 resolution is stretched to fill the screen even when I have aspect ratio scaling set in the nvidia settings app. The only way to make it work correctly is to change the value of the "force full GPU scaling" setting at least once after every time I boot up my laptop. The actual state of "force full GPU scaling" is irrelevant - it just needs to be changed in order for the driver to apply the chosen GPU scaling method setting.

2. When I try to use SLI, I get terrible flickering in OpenGL 3D apps. It's an improvement from some previous drivers I've tried which wouldn't even boot with SLI enabled, but it's still effectively unusable.

---

### Post by static_hf on 2010-03-28
Ok so there is a problem.

I have Asus g1 sn series with Nvidia 9500M GS graphic card.

I followed the method and it succefully installed the driver yet my graphic is like windows 95.( i installed the driver from Nvidia 195.xxx which includes my graphic card inside)
what should i do ? :(c

---

### Post by anthonyk1978 on 2010-03-28
Hi all!! Very good info BUT...... I am using a pos Celeron computer with PNY Nvidia Geforce 8400GS 512mb PCI. I used the recommended driver which is version 185 and i can get my dual monitors to work but not visual graphics. I then followed these instructions using the version 195 driver and everything installed correctly and still NO visuals. What do i have to do just to get this running properly??!!!

---

### Post by Dark Bishop on 2010-03-29
im also getting the error saying the x server is still running after stopping gdm.

im trying to install 195.36.15 32-bit on a fresh install of ubuntu 9.04.

thanks for any help.

---

### Post by wizarddrummer on 2010-03-29
> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. It's been almost a week since I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 



*Edit March 22 2010*: Latest nVidia 195.xx (STABLE) **[COLOR=Red]195.36.15[/COLOR]** Drivers:  [ 32 Bit ]("ftp://download.nvidia.com/XFree86/Linux-x86/195.36.15/") . [64 Bit]("ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/")


*Edit March 18 2010*: Latest nVidia 195.xx **OpenGL 3.3** (STABLE) **[COLOR=Red]195.36.07.03[/COLOR]** Drivers:  [ 32 Bit ]("http://developer.download.nvidia.com/opengl/3.3/linux/NVIDIA-Linux-x86-195.36.07.03-pkg1.run") . [64 Bit]("http://developer.download.nvidia.com/opengl/3.3/linux/NVIDIA-Linux-x86_64-195.36.07.03-pkg2.run")




_**How to install nVidia drivers in Linux:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR=Red]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```**[COLOR=Red]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```**[COLOR=Red]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR=Red]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR=Red]7[/COLOR])** Then restart your computer   ```
sudo reboot
```**[COLOR=Red]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: ```
sudo sh ./Nxxx --uninstall
```or
```
sudo nvidia-uninstall
```**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.



_**Legacy Drivers**_


GeForce 5 series GPUs **[COLOR=Red]173.14.25 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_173.14.25.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_173.14.25.html")


GeForce 2 through GeForce 4 series **[COLOR=Red]96.43.16 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_96.43.16.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_96.43.16.html")


Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR=Red]71.86.13 [/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_ia32_71.86.13.html") , [64 bits]("http://www.nvidia.com/object/linux_display_amd64_71.86.13.html")


*note*: Legacy drivers are being updated as well. (Latest update: February 15, 2010)


Good luck ;)

Great Post!
My system 2.6.31-14-generic
Having read about 400 posts on this topic I've seen lots of diversity in methods.
Do I need to issue any of these commands prior to this installation process.
I have a new install and I have NOT installed the drivers yet.
sudo apt-get install linux-headers-rt
sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)

EDIT1
Or this command?
sudo nvidia-xconfig --nvagp=1

Thanks,

---

### Post by 0pul3nce on 2010-04-02
Looks like this threads died down a bit. I take it that people are happy with the information provided about drivers here?

---

### Post by ratcheer on 2010-04-02
> **0pul3nce said:**
> Looks like this threads died down a bit. I take it that people are happy with the information provided about drivers here?

For the record, I have been very happy with this thread, for months. I hope the methodology for installing nvidia drivers does not change too much with Lucid, but I am afraid it will.

Tim

---

### Post by sdowney717 on 2010-04-02
With Lucid I basically did post number 1255
Except I just used the recovery mode console window.
I did not do the stop gdm command.
I am still running 195.30 driver downloaded direct from Nvidia site

---

### Post by alex_o on 2010-04-02
i finally got the 195 driver working :D thx

---

### Post by Kosimo on 2010-04-03
> **0pul3nce said:**
> Looks like this threads died down a bit. I take it that people are happy with the information provided about drivers here?

Why should it be dead?

At the moment it includes direct links to the latest drivers releases for all cards, including OpenGL betas and legacy, 32 and 64 bits. 

The how-to is still perfectly valid, and yes, it kills GDM (Karmic tells you that in the future you should use a new command, but it still works) I will get specific commands for Lucid Lynx in the event that current ones won't work. 


Hope it helps. 

Kosimo

---

### Post by essexboyracer on 2010-04-05
I second that, the instructions from the first post worked for my 9700M GT on Karmic on an Asus G71v. In Karmic you can also use the command 'gdm stop' (or similar, it will tell you anyway) Keep it alive.

---

### Post by Dugger5688 on 2010-04-06
Just did this, how do I remove the driver and get back to the drivers that come with ubuntu (not the closed source ones), the ones that ubuntu boots into when first started are the ones I'm after. Tried the sudo nvidia-uninstall but got low graphics mode.

---

### Post by shane2peru on 2010-04-13
Ok, here is some new excitement for the thread!  My install failed.  I installed lucid, and ran through the procedure as I have done before and this time it failed.  Attached is the log file.  I was trying to install the 192.36.15 driver that I used on Karmic.  I have the nVidia Corporation G96 [GeForce 9500 GT] card in my box.  Any help would be appreciated.  The last part of the error log says this:

```

-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   21.117800] CPU0 attaching NULL sched-domain.
   [   21.117805] CPU1 attaching NULL sched-domain.
   [   21.170085] CPU0 attaching sched-domain:
   [   21.170089]  domain 0: span 0-1 level MC
   [   21.170092]   groups: 0 1
   [   21.170099] CPU1 attaching sched-domain:
   [   21.170102]  domain 0: span 0-1 level MC
   [   21.170105]   groups: 1 0
   [   24.720187] eth0: no IPv6 routers present
   [ 5284.598467] end_request: I/O error, dev fd0, sector 0
   [ 5296.700119] end_request: I/O error, dev fd0, sector 0
   [ 5942.473487] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [ 5965.927768] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
   [ 5965.932520] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc:
   initialised FIFO 2
   [ 5977.558138] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [ 6049.705018] nvidia: module license 'NVIDIA' taints kernel.
   [ 6049.705024] Disabling lock debugging due to kernel taint
   [ 6050.460319] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [ 6050.460323] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [ 6050.460324] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [ 6050.460326] NVRM: device(s).
   [ 6050.460329] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [ 6050.460330] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [ 6050.460331] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [ 6050.460334] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

That is probably the relevant part.

Shane

---

### Post by Tweak42 on 2010-04-14
I updated to Lucid and got the same errors using same drivers.

---

### Post by Gemnoc on 2010-04-14
Are you talking about the drivers from nVidia's website?

Here's part of the [Lucid Beta2 Known Issues]("http://www.ubuntu.com/testing/lucid/beta2#Known%20issues"):
> Because of the new alternatives system used for nvidia driver packages, **the nvidia installer from NVIDIA's website currently doesn't work**.

---

### Post by Tweak42 on 2010-04-15
Ah yep.  Serves me right for not reading the beta notes to closely. :(


> **Gemnoc said:**
> Are you talking about the drivers from nVidia's website?

Here's part of the [Lucid Beta2 Known Issues]("http://www.ubuntu.com/testing/lucid/beta2#Known%20issues"):

---

### Post by shane2peru on 2010-04-15
Lol, I guess me too!  I hope they are able to get that fixed!  :)  Thanks for pointing out the obvious to us.  

Shane

---

### Post by MockY on 2010-04-17
> **Dugger5688 said:**
> Just did this, how do I remove the driver and get back to the drivers that come with ubuntu (not the closed source ones), the ones that ubuntu boots into when first started are the ones I'm after. Tried the sudo nvidia-uninstall but got low graphics mode.

do a CTRL-ALT-F2 and go in to the directory you have the driver installation file. After you kill GDM, type the following:
```
sudo sh ./Nxxx.run --uinstall
```

---

### Post by AaronP_ on 2010-04-17
> **MockY said:**
> do a CTRL-ALT-F2 and go in to the directory you have the driver installation file. After you kill GDM, type the following:
```
sudo sh ./Nxxx.run --uinstall
```
It's --uninstall, not --uinstall.  Also, you don't need the original .run file, you can just run nvidia-uninstall (or nvidia-installer --uninstall for old drivers).

---

### Post by Linuxforall on 2010-04-19
sudo nvidia-uninstall will do after sudo service gdm stop in terminal.

---

### Post by Kosimo on 2010-04-24
Guys, 195.36.24 Pre-Release is here

Changelog:

>     *  Added support for the following GPUs:
          o GeForce GTX 480
          o GeForce GTX 470
          o Tesla C2050
    * Fixed a problem that caused occasional red flashes in XVideo frames.
    * Added official support for xserver 1.8. The -ignoreABI option is no longer required with this version of the server.
    * Updated the "Supported NVIDIA GPU Products" list to include various supported GPUs that were missing previously.



Links in the first page

Good luck!

---

### Post by zim2dive on 2010-04-26
> **Kosimo said:**
> Guys, 195.36.24 Pre-Release is here


anyone know why the PPA ([https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=)) hasn't gotten upgraded?  Its been 3-4 days since the release.

---

### Post by Kosimo on 2010-04-27
> **zim2dive said:**
> anyone know why the PPA ([https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=)) hasn't gotten upgraded?  Its been 3-4 days since the release.

That's one of the many reasons why I always prefer to compile my own drivers.

---

### Post by zim2dive on 2010-04-28
> **Kosimo said:**
> That's one of the many reasons why I always prefer to compile my own drivers.

and on the flip side, I've borked my system multiple times, following the same instructions as in post #1, hence my preference for PPA.  

I think the issue is once you've installed/used from synaptic, one must do more before simply following those instructions (else the low-graphics that I got multiple times).. but I don't see those steps documented.

---

### Post by Kosimo on 2010-04-30
195.36.24 was promoted to official release status, replacing 195.36.15.

---

### Post by ratcheer on 2010-04-30
Has anyone tried the installation procedures on page 1 with Lucid, yet? The official Lucid release notes still say you shouldn't do it.

> **Incompatibility   with nVidia upstream driver installer**

  
 Ubuntu 10.04 LTS includes  improved integration for nVidia binary driver packages.  Unfortunately,  this comes at the expense of compatibility with the installer provided  upstream on the nVidia website.  Users who wish to use the nVidia binary  video drivers with 10.04 LTS should install them using the Ubuntu  packages, as made available under System -> Administration -> Hardware Drivers.  
 [B]
[/B]



[http://www.ubuntu.com/getubuntu/releasenotes/1004#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](http://www.ubuntu.com/getubuntu/releasenotes/1004#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

Tim

---

### Post by standingwave on 2010-04-30
> **ratcheer said:**
>  Users who wish to use the nVidia binary  video drivers with 10.04 LTS  should install them using the Ubuntu  packages, as made available under  System -> Administration -> Hardware Drivers.   Yeah, the driver it recommended (and I installed) isn't working for me. I have no visual effects. I expect to dig into it more this weekend but it's annoying and a step backwards from Karmic on my system.

---

### Post by Nimless on 2010-04-30
nvidia-current package has vdpau acceleration broken, at least for me.
I've been able to install the latest driver from Nvidia site, but I had to remove nouveau.

---

### Post by 23dornot23d on 2010-05-02
After using the latest 195.36.15 source drivers from setting up the PPA here .... 

[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa?field.series_filter=")

My GeForce Nvidia  9300M GS is working properly in Desktop Mode ....

My kernel is .... 2.6.32-21-generic


[http://i40.tinypic.com/2ez61ch.jpg](http://i40.tinypic.com/2ez61ch.jpg)

When switching into console mode on initial boot was ok ..... but now just a black screen with a flashing white cursor top left ....
 in console mode only ...... not sure why
this just happened though after a second restart and no other changes done ..... will update if it rectifies itself with any updates.

[IMG]http://i43.tinypic.com/2r2tdth.jpg[/IMG]

The Desktop Display is still ok though ........ and 3D works ..... well

Console is ok too now

---

### Post by Dr_Krullivan on 2010-05-02
Thank you for this, hopefully the latest drivers will fix my dilemma with X and the nvidia drivers ubuntu uses as current.

---

### Post by zim2dive on 2010-05-02
So if we've installed by hand, do we have to uninstall and re-install an older version via PPA before upgrading to Lynx?

---

### Post by ratcheer on 2010-05-03
> **zim2dive said:**
> So if we've installed by hand, do we have to uninstall and re-install an older version via PPA before upgrading to Lynx?

I can say that I did not have to do that, but I see people all over these forums who are having tons of trouble with their nVidia drivers in Lucid. They are trying to follow everything everybody is telling them, and nothing is working.

Tim

---

### Post by 23dornot23d on 2010-05-03
I always try to play it safe ..... but while all the work on grub is going on and I cannot find a schematic or flowchart for 
to tell anybody how the system is setting everything up - it is difficult to work out what is the safest way any more ..... 

Other than having a separate USB boot drive with all your Data on that cannot possibly be touched or altered in any way .....

[CENTER]______________________________________________________
[/CENTER]

So ...... to the safest way I know .....

This is how I do my upgrades after all my problems that I had with 9.10 ..... 

I learned not to play Russian Roulette with my System anymore  ,,,

Set up a separate partition and do a clean install of 10.4 Lucid Lynx to it ..... work out any issues that you may have with it if you can ....... and find solutions. 

If you do not find solutions just reformat the partition and life goes on as normal using your previous System ....
once you plug in your main USB drive again .... and boot from it ......

[CENTER]_________________________________________________________
[/CENTER]

If all goes well then you can do the upgrade with a little more confidence ..... which is what I did ..... 
but I did not remove the graphics drivers  .... until after I did the upgrade - which was when I found that they did not work properly .......

Then I looked for this solution ....... so removed any existing graphics drivers ...... added the PPA ..... 
made sure my System was up to date and then downloaded the source files for the latest graphics drivers that suited my spec ..... 195.36 .....

[Nvidia Drivers ]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run&lang=us&type=GeForce")

(add **sudo** in front of each of these lines if you do not run as root user ...)

apt-get install nvidia-kernel-common

( information - [Nvidia-kernel-common]("https://launchpad.net/ubuntu/lucid/+source/nvidia-kernel-common") )

apt-get update
apt-get upgrade
nvidia-xconfig


Check this thread too [Detailed Info if you still have problems]("http://ubuntuforums.org/showthread.php?t=1467074")

On rebuild of the Kernel it picked up the latest driver and all went well for me .....

[IMG]http://i43.tinypic.com/2r2tdth.jpg[/IMG]

I know from the past that everybody has slightly different set ups and problems.

But if you do this the way I have explained .... you may reduce your problems or find out early enough 
if there are any things that may stop you using this version ...... and if there are just continue to use the
last release .......

Some more info and how to get to see the log files .....
( Interesting - [FEB TESTING]("http://www.webupd8.org/2010/02/ubuntu-1004-lucid-lynx-testing-nouveau.html") ) 


Use this to see your log or go to your Log files and find it .... System Administration - Log File Viewer
gedit /var/log/Xorg.0.log

That's the best way I can explain what I do at this moment in time ....... I hope it helps ...... 

If you are [[COLOR=Red]worried[/COLOR]]("http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug") at all using any other graphic drivers than the ones in the normal 
Lucid repository keep checking the Thermal settings while doing things graphic intensive in 3D - 
( rendering a big scene or using Compiz with the cube, playing 3D games etc .... )

[Good Link for more Information on 195.36]("http://text.broadbandreports.com/forum/r23897122-Nvidia-GeForce-Driver-1953608-released-for-LinuxUnix")
________________________________________________________________

How did you do yours Tim ..... or did it all install ok on the Upgrade .........

---

### Post by Fenris_rising on 2010-05-06
Hi there

I have just used the OP to upgrade to the latest Nvidia driver. Everything went perfectly I am glad to say. So cheers for that :KS

I am running Karmic at the moment. Not quite ready to brave lucid yet =D

BUT, there had to be one =D, Setting up my dual screen using the Nvidia config proved to be a pig..........again.

The xorg file it creates just doesn't equate to me setting up for dual screens. Infact a reboot gives me one screen the other is once again disabled in the nvidia config.

Luckily I had saved the original Xorg that was made when I setup the 185 driver which had all the right data to run my dual screens ONLY because I had to dig through the forum to guess at who's xorg files, as listed for help on this forum, looked like they had bits I needed. So I just swapped them over and all is well.

But why am I having this issue of Nvidia config not being able to set up my xorg to suit my needs? A little light on this would be great please!

regards

Fenris

---

### Post by Buschbarber on 2010-05-10
I have been using Ubuntu for over a year and I have been pleased with the success I have had in getting the Nvidia drivers, for my Gforce 9800GTX+, to work with various distros of Ubuntu. I have updated the drivers using the instructions on this thread and all has worked fine.

I was previously runing 9.01. Now, I have installed 10.04 and cannot get the same drivers that worked in 9.01, to install under 10.04. I get errors when I try to run sh ./NVIDIA-Linux-xxxxx. I tried to install 195.36.24 64bit. Failed. I tried to install 195.36.15, using Synaptic, and it failed. I tried installing Version 173, using System/Administration/Hardware Drivers. It appears to install, but when I boot, I get the box that says I am booting in the Low Res mode. I choose Start X and it brings up the Desktop, but I cannot run Nvidia Settings, so the 3D driver is not working.

What is the exact procedure to get a compatible 3D driver installed, especially the latest ones? I cannot use Google Earth and other apps that use the newer Nvidia drivers.

---

### Post by Gemnoc on 2010-05-10
@ Buschbarber

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](http://www.ubuntu.com/getubuntu/releasenotes/1004#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

I mentioned it a couple pages back. I'm unsure wether this issue has been resolved or not since.

You may find a compiled deb package in a PPA, I think someone gave a link in a previous post.

---

### Post by Buschbarber on 2010-05-10
I was advised that I should Boot the Kernel 21, not 22, and then run sudo sh ./NVIDIA-Linux-xxxxx, for the 64bit install and then Reboot into the same Kernel 21. I did so, and although I got an error message that the Script had failed, and did I want to continue, I said OK and the driver 24 is installed and seems to be working.

If I try to boot into Kernel 22, I receive the box that refers to the Low Res Graphics Mode.

Since I use an HDTV as my monitor, I need the newer drivers so I can adjust for Overscan,

---

### Post by ratcheer on 2010-05-11
Buschbarber, yes, fixing one kernel will not fix a different one. The driver is linked in to each individual kernel by the installation process.

Tim

---

### Post by Kosimo on 2010-05-23
Folks, great news. 

nVdia has just released the first beta of the 256.x Series,    

[COLOR="Red"]**256.25**[/COLOR]


Change log: 

> 
Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
GL_ARB_blend_func_extended
GL_ARB_draw_buffers_blend
GL_ARB_sample_shading
GL_ARB_timer_query
GL_EXT_draw_buffers2
GL_EXT_separate_shader_objects
GL_NV_explicit_multisample
GL_NV_transform_feedback
Improved Thermal Settings reporting in nvidia-settings to accurately reflect hardware configurations with multiple thermal sensors.
Fixed an interaction problem between Compiz and 'screen-scraping' VNC servers like x11vnc and vino that caused the screen to stop updating. Fixes Launchpad bug #353126.
Enhanced VDPAU to add basic support for Xinerama. VDPAU will now operate on a single physical X screen under Xinerama. See the README for more details.
Enhanced VDPAU's handling of corrupt clips of all formats on GPUs with VDPAU feature set C to be at least as good as on GPUs with VDPAU feature set B. This significantly improves various clips provided by nvnews.net user eamiller.
Fixed a bug in Xv attribute handling that caused hue, saturation, brightness, and contrast values to be misapplied when using an Xv overlay adaptor.
Fixed a bug in the XvMC driver that prevented it from working on systems with AGP graphics cards.
Enhanced VDPAU to clear all VdpVideoSurfaces to black when allocated. This provides more consistent results when using a surface as a reference when no prior decode operation has written to that surface. In turn, this improves the results of decoding some corrupt streams, such as "p_only_no_play" from ffmpeg bug 1124.
Implemented new APIs to allow sharing VDPAU surfaces with OpenGL and CUDA. The OpenGL extension is GL_NV_vdpau_interop. For CUDA, please see the documentation in the CUDA toolkit for details.
Worked around a bug where the combination of a GPU with VDPAU feature set A together with specific motherboard chipsets could cause visible corruption when decoding some MPEG-2 streams.
Fixed a bug that prevented the VDPAU overlay-based presentation queue from being used more than a few hundred times per X server invocation.
Renamed the driver file libGLcore.so.VERSION to libnvidia-glcore.so.VERSION, as a small step towards reducing the filename collisions between NVIDIA's and Mesa's OpenGL implementations. This driver file is used by NVIDIA's libGL.so and libglx.so, and should never be used directly by applications.
Changed the SONAME of libnvidia-glcore.so.VERSION, libnvidia-tls.so.VERSION, and libnvidia-compiler.so.VERSION to be ".so.VERSION", rather than ".so.1". These driver files are only used by other NVIDIA driver components, and are only intended to be used by components of the matching NVIDIA driver version.
Removed the "-pkg#" suffix from the NVIDIA Linux .run files. The packages are now simply named "NVIDIA-Linux-ARCH-VERSION.run". On Linux-x86_64, a package which omits the 32-bit compatibility libraries is also available: "NVIDIA-Linux-x86_64-VERSION-no-compat32.run"
Simplified the directory structure of the Linux extracted package; most driver files are now just contained within the top level directory of the package. Pass the '--list' option to the .run file for details.
Removed precompiled kernel interfaces from the NVIDIA Linux-x86 .run file; these were ancient and had not been updated in years. Going forward, NVIDIA does not plan to provide precompiled kernel interfaces with the Linux .run files. However, nvidia-installer and the .run file will retain the ability for users to add their own precompiled kernel interfaces via the '--add-this-kernel' .run file option.
Compressed the nvidia-settings, nvidia-installer, and nvidia-xconfig tarballs with bzip2, rather than gzip.


download links in the first page of this thread. 

Good luck

---

### Post by Gemnoc on 2010-05-23
There's no mention that these drivers are now compatible with Lucid...

[Incompatibility with nVidia upstream driver installer]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer")

I'd be interested to know if it now safe to install the nVidia upstream driver in Lucid.

---

### Post by Kosimo on 2010-05-23
> **Gemnoc said:**
> There's no mention that these drivers are now compatible with Lucid...

[Incompatibility with nVidia upstream driver installer]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer")

I'd be interested to know if it now safe to install the nVidia upstream driver in Lucid.

Good question. 


I do not have any pc with a nVidia card right now, so I can't test. 

Anybody can please confirm that it works?

Thanks

---

### Post by cdekter on 2010-05-23
I've installed the 195.30 drivers in Lucid with total success. You have to make sure you remove the existing driver packages first. I just ignored the warning about the 'distribution-provided pre-install script' failing. I also had to blacklist nouveau.

Be warned though, YMMV and I have occasional boot problems (X doesn't start successfully first time, but it does eventually get going).

---

### Post by Kosimo on 2010-05-24
> **cdekter said:**
> I've installed the 195.30 drivers in Lucid with total success. You have to make sure you remove the existing driver packages first. I just ignored the warning about the 'distribution-provided pre-install script' failing. I also had to blacklist nouveau.

Be warned though, YMMV and I have occasional boot problems (X doesn't start successfully first time, but it does eventually get going).



Did you had a chance to install the new 256.x drivers?

---

### Post by wolfe on 2010-05-24
I have installed the 256.25 drivers and they appear to work well on my 2 gtx470s.  However now when I open boinc the computer becomes completely unresponsive unless I 'kill -9' the boinc process.  I use these cards to crunch on gpugrid.  

Does anyone know of a ppa that still has 195.36.24 available in it?  All the ones I know of have replaced that with this beta driver and I really need to downgrade until this issue gets sorted out.

---

### Post by ratcheer on 2010-05-24
> **wolfe said:**
> 
Does anyone know of a ppa that still has 195.36.24 available in it?  All the ones I know of have replaced that with this beta driver and I really need to downgrade until this issue gets sorted out.

It is in the maverick restricted ppa.

Tim

---

### Post by JohnnyC35 on 2010-05-24
The new 256 drivers seem to work fine with my Lucid. Sadly, still can't play 1080 Blu-ray files via XBMC but 720 still play flawlessly :)

---

### Post by wolfe on 2010-05-24
> **ratcheer said:**
> It is in the maverick restricted ppa.

Tim

Hate to be a noob, but could you post a link to that ppa?  Can't seem to find it

---

### Post by gnomeuser on 2010-05-24
The 265 update is available in the ubuntu x swat (x updates) PPA:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by ratcheer on 2010-05-24
> **wolfe said:**
> Hate to be a noob, but could you post a link to that ppa?  Can't seem to find it

It is the same as the lucid restricted repository except for the characters "maverick" instead of "lucid". If you do decide to use it, make sure you get only what you want and remove it from your software sources once you have gotten it. Personally, I would not try it, but you asked where you could get it.

Tim

---

### Post by zim2dive on 2010-05-24
> **Gemnoc said:**
> There's no mention that these drivers are now compatible with Lucid...

[Incompatibility with nVidia upstream driver installer]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer")

I'd be interested to know if it now safe to install the nVidia upstream driver in Lucid.

Agreed.. waiting for the dust to settle on Lucid vs. pkg file situation.. in the meantime, they are in PPA: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

---

### Post by Amorget on 2010-06-05
I just installed the new Beta drivers on my 9.10 x64 setup.

I can now play HD videos without glitch, which before would have massive frame drop.  Huge difference after the install, I am very happy!

---

### Post by Buschbarber on 2010-06-05
I was able to install 195.36.24 or 256.25, both 64bit, in Lucid 64bit, but only kernel 21, not 22.

Is there any way, yet, that I can successfully install either of these drivers in kernel 22?

---

### Post by randyklein99 on 2010-06-05
I was able to install 256 with kernel 22, but I did it by installing nvidia-current and choosing lucid-proposed repository.

---

### Post by Linuxforall on 2010-06-05
> **randyklein99 said:**
> I was able to install 256 with kernel 22, but I did it by installing nvidia-current and choosing lucid-proposed repository.

Why even bother with that when ppa for x has latest beta within hours of its release and best of all, it comes with the newer mesa dri file so performance is far better.

---

### Post by Buschbarber on 2010-06-05
I updated my Software Sources and added the new ppa, but I do not know how to proceed from there. The 256 drivers do not appear in Synaptic. Aren't they supposed to after you add the ppa and then run Update?

---

### Post by Linuxforall on 2010-06-05
> **Buschbarber said:**
> I updated my Software Sources and added the new ppa, but I do not know how to proceed from there. The 256 drivers do not appear in Synaptic. Aren't they supposed to after you add the ppa and then run Update?

In terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 

sudo apt-get update and then fire up update manager and you will see the updates listed, apply and reboot and you will have latest nvidia beta 265xx drivers.

---

### Post by Buschbarber on 2010-06-06
I booted into kernel 22, in the low graphics mode, and followed your instructions to the letter. When I run Update Mgr, it says my system is up to date.

I have to reboot into kernel 21 and reinstall the 265 drivers in order to get 3d support.

---

### Post by kamina on 2010-06-08
I'm running a minimal server installation with xbmc on 10.4. The system is an Asus EB1501 with ion. I was having problems with the stock nvidia drivers and decided to install the latest beta (256.xx) but they would not install... 

I found an article advising to blacklist the following modules:
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```
After doing it the driver installs, but the system runs fsck for all drives on every reboot... Any idea what's going on?

It seems to be somehow connected to an external e-sata disk I use, if I remove the line from fstab it will boot fine. If I disconnect the drive (and don't remove the line) the errors will come.

```

# LABEL=ext_backup	/mnt/backup	ext3	defaults	0	2

```

edit:

lspci -v

```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: 66MHz, fast devsel, IRQ 14
	I/O ports at 2900 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f9f80000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: nvidia
	Kernel modules: nvidia

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at f9f7e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9f7fc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=00a0
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f9f7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f9f7f800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=00a0
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 8376
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9f78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: [b8] Subsystem: ASUSTeK Computer Inc. Device 83e9

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
	I/O ports at d080 [size=8]
	I/O ports at d000 [size=4]
	I/O ports at cc00 [size=8]
	I/O ports at c880 [size=4]
	I/O ports at c800 [size=16]
	Memory at f9f76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
	Capabilities: [8c] SATA HBA <?>
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
	Kernel driver in use: ahci
	Kernel modules: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-fbefffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f7ffffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 83e9
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 83e9
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 83e9
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport
	Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 83e9
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fbee0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, nouveau

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1089
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

---

### Post by Guilden_NL on 2010-06-09
> **Linuxforall said:**
> In terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 

sudo apt-get update and then fire up update manager and you will see the updates listed, apply and reboot and you will have latest nvidia beta 265xx drivers.

Nope.  Same old 173 that refuses to load under Lucid.

*(deleted non-relevant crud)*
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Joop@Joop-Office:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]              
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US           
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [6,946B]
Fetched 64.5kB in 1s (38.9kB/s)   
Reading package lists... Done
Joop@Joop-Office:~$ 

I tried tracking down the addy and it looks correct, but no updates are coming forth.

---

### Post by Buschbarber on 2010-06-09
Since reinstalling UE 2.7, based upon Ubuntu 10.04, I cannot install the Nvidia drivers 195.36.24 or 256.25 64bit drivers. All I get is an error Distribution Pre-Install Script Failed, Unable to load Kernel Module nvidia.ko.

Attached is nvidia-installer log

---

### Post by Buschbarber on 2010-06-09
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun  9 16:38:42 2010
installer version: 256.25

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.25.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-22-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-22-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.32-22-generic/b
   uild SYSOUT=/lib/modules/2.6.32-22-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.tmp_versions ; r
   m -f /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.2
   5/kernel
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nv.o.d  -nos
   tdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/us
   r/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/linu
   x/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototype
   s -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-
   declaration -Wno-format-security -fno-delete-n
   ull-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fu
   nit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -Wsig
   n-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSIO
   N_STRING=\"256.25\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.2
   5/kernel/.tmp_nv.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nv.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nv_gvi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz844
   4/NVIDIA-Linux-x86_64-256.
   25/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -D
   MODULE -DNVRM -DNV_VERSION_STRING=\"256.25\" -mcmodel=kernel -mno-red-zone -
   UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/.tmp_nv_gvi.o /tmp/selfgz8444/NVIDIA-
   Linux-x86_64-256.25/kernel/nv_gvi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nv-vm.o.d  -
   nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format
   -security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-z
   one -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-prot
   ector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compa
   re -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -W
   frame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -
   pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno
   -dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.2
   5/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"256.25\" -mcmodel=kernel -mno-red-zone -U
   DEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz84
   44/NVIDIA-Linux-x86_64-256.25/kernel/.tmp_nv-vm.o /tmp/selfgz8444/NVIDIA-Lin
   ux-x86_64-256.25/kernel/nv-vm.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.os-agp.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/
   selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -Wsign-compare -Wno-c
   ast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.2
   5\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)"  -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.t
   mp_os-agp.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/os-agp.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.os-interface
   .o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror
   -implicit-function-declaration -Wno-format-security -fno-delete-null-pointer
   -checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-ti
   me -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I
   /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -Wsign-compare -
   Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"
   256.25\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -
   D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.2
   5/kernel/.tmp_os-interface.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kern
   el/os-interface.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.os-registry.
   o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclu
   de  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O
   2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccum
   ulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGN
   AL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse 
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-poi
   nter-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/s
   elfgz8444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.25
   \" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUI
   LD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME
   =KBUILD_STR(nvidia)"  -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kerne
   l/.tmp_os-registry.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/os-re
   gistry.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nv-i2c.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ 
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -Werror-implicit-function-declaration -Wno-format-security -fno-delete
   -null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -
   funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=102
   4 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-afte
   r-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fcon
   serve-stack -I/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -W
   sign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VER
   SION_STRING=\"256.25\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_
   64-256.25/kernel/.tmp_nv-i2c.o /tmp/
   selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nv-i2c.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nvacpi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optim
   ize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz8444/NVIDIA
   -Linux-x86_64-256.25/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-err
   or -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.25\" -mcmodel=kern
   el -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.tmp_nvacpi.o /tmp/s
   elfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nvacpi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   8444/NVIDIA-Linux-x86_64-256.25/kernel/nvacpi.o";
     ld -m elf_x86_64   -r -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel
   /nvidia.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nv-kernel.o /tmp
   /selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nv.o /tmp/selfgz8444/NVIDIA-Li
   nux-x86_64-256.25/kernel/nv_gvi.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25
   /kernel/nv-vm.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/os-agp.o /
   tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/os-interface.o /tmp/selfgz8
   444/NVIDIA-Linux-x86_64-256.25/kernel/os-registry.o /tmp/selfgz8444/NVIDIA-L
   inux-x86_64-256.25/kernel/nv-i2c.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.2
   5/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/ker
   nel/nvidia.ko;) > /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/modules.
   order
   make -f /usr/src/linux-headers-2.6.32-22-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-22-generic/Modu
   le.symvers -I /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/Module.symve
   rs  -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/Module.symvers -S -
   w  -s
   WARNING: could not find /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.n
   v-kernel.o.cmd for /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nv-kern
   el.o
     cc -Wp,-MD,/tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/.nvidia.mod.o
   .d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2
   -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumul
   ate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL
   _FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -m
   no-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer
   -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-s
   ign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz8
   444/NVIDIA-Linux-x86_64-256.25/kernel -Wall -MD -Wsign-compare -Wno-cast-qua
   l -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"256.25\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG 
   -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz8444/NVIDIA-
   Linux-x86_64-256.25/kernel/nvidia.mod.o /tmp/selfgz8444/NVIDIA-Linux-x86_64-
   256.25/kernel/nvidia.mod.c
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-22-generic/scripts/mo
   dule-common.lds --build-id -o /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/ker
   nel/nvidia.ko /tmp/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nvidia.o /tm
   p/selfgz8444/NVIDIA-Linux-x86_64-256.25/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1
   No such device
-> Kernel messages:
   [   16.108180] Bluetooth: SCO socket layer initialized
   [   16.157684] ppdev: user-space parallel port driver
   [   16.220953] Bluetooth: RFCOMM TTY layer initialized
   [   16.220958] Bluetooth: RFCOMM socket layer initialized
   [   16.220960] Bluetooth: RFCOMM ver 1.11
   [   24.853639] eth0: no IPv6 routers present
   [   29.837063] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
   [   29.838272] input: Logitech MX5000 Keyboard as
   /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.0/bluetooth/hci0/hci
   0:11/input7
   [   29.838364] generic-bluetooth 0005:046D:B305.0002: input,hidraw1:
   BLUETOOTH HID v45.03 Keyboard [Logitech MX5000 Keyboard] on
   00:07:61:A3:68:84
   [   55.120062] end_request: I/O error, dev fd0, sector 0
   [   67.220934] end_request: I/O error, dev fd0, sector 0
   [   80.663354] input: Logitech MX1000 mouse as
   /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.0/bluetooth/hci0/hci
   0:12/input8
   [   80.663468] generic-bluetooth 0005:046D:B003.0003: input,hidraw2:
   BLUETOOTH HID v43.20 Mouse [Logitech MX1000 mouse] on 00:07:61:A3:68:84
   [  589.532717] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  697.396006] nvidia: module license 'NVIDIA' taints kernel.
   [  697.396010] Disabling lock debugging due to kernel taint
   [  697.988515] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  697.988518] NVRM: This can occur when a driver such as nouveau, rivafb,
   [  697.988520] NVRM: nvidiafb, or rivatv was loaded and obtained ownership
   of
   [  697.988521] NVRM: the NVIDIA device(s).
   [  697.988523] NVRM: Try unloading the conflicting kernel module (and/or
   [  697.988524] NVRM: reconfigure your kernel without the conflicting
   [  697.988525] NVRM: driver(s)), then try loading the NVIDIA kernel module
   [  697.988526] NVRM: again.
   [  697.988528] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
```

---

### Post by Buschbarber on 2010-06-10
Well, no matter what I would do, the Nvidia drivers would not install for Lucid kernel 21 or 22. I even tried reinstalling Ultimate Edition 2.7 and immediately installing the Nvidia drivers. I tried Purging all the Nvidia stuff, rebooting, and reinstalling the drivers, but they kept failing to install.

I would reboot, login, hit Ctrl/Alt/F1, login, and then run the following:

sudo service gdm stop
sudo sh ./NVIDIA-Linux-x86_64-195.36.24-pkg2.run

I would get an error referring to nvidia.ko.

Finally, I saw a thread that suggested the following code:

sudo sh ./NVIDIA-Linux-x86_64-195.36.24.run -k $(uname -r)

The drivers installed without error, for kernel 21 and when I rebooted, the Nvidia logo appeared as I was booting up. I switched to kernel 22 and the drivers also installed there, as well. Nvidia Settings does not appear in the System/Preferences menu so I thought the drivers were still not installed, but when I clicked on System/Preferences/Monitors, I get the following box?

It appears that your Graphics Driver does not support the necessary extensions to support this tool. Do you want to use your Graphics Driver's tool?

When I say Yes, the Nvidia Settings box comes up.

Any idea what is going on here?

---

### Post by randyklein99 on 2010-06-10
I think if you run this:

sudo sh ./NVIDIA-Linux-x86_64-195.36.24.run -k $(uname -r)

you should be in the kernel you want to use.  Otherwise you'll have to specifically call out the kernel instead of using $(uname -r).  Not sure though.

That command worked for me as well.

---

### Post by darco on 2010-06-13
> **Linuxforall said:**
> In terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 

sudo apt-get update and then fire up update manager and you will see the updates listed, apply and reboot and you will have latest nvidia beta 265xx drivers.

thxs...this worked perfectly on .21....

---

### Post by Linuxforall on 2010-06-13
> **darco said:**
> thxs...this worked perfectly on .21....

You are welcome. :)

---

### Post by eGelor on 2010-06-13
hi, 
i'm trying over one month to fix my nvidia drivers without any success.
my laptop is a HP Presario Cq60 and my nvidia Gforce 9200GS.

Please help.

---

### Post by Kosimo on 2010-06-13
> **eGelor said:**
> hi, 
i'm trying over one month to fix my nvidia drivers without any success.
my laptop is a HP Presario Cq60 and my nvidia Gforce 9200GS.

Please help.

What is actually happening? Could you give us more information about your distro, drivers you're trying to install (if any) and how?

---

### Post by Rorohiko on 2010-06-14
Hi to everybody!

I'm using a nVidia GT230 with the news driver 'NVIDIA-Linux-x86-256.29-0ubuntu1~xup~lucid'. It works fine in general, but the problem is when ever I reboot my computer, it had forgotten the settings. So I had to go to 'System / Settings / gnome-appearance-properties' and there to the register: 'visual effects'. It is always pointed to 'no' when I start on this register and after I click with the mouse to 'extra' it always looks up for new available driver and installs it and after that the question comes up, if it should stay in extra mode and where I click to yes. With the extra-mode it comes the frames around the windows, which is missing when the computer starts up.

Does anyone know, were I can save the settings, so that it starts always with the ones I prefer?

Thanks for help!
Rorohiko

---

### Post by eGelor on 2010-06-14
> What is actually happening? Could you give us more information about your distro, drivers you're trying to install (if any) and how?

2.6.32.22 generic
2.6.32.22 pae
2.6.31.14 generic

first i install from synaptic :
nvidia-settings
nvidia-current
nvidia-common

i want to Hardware device and test 173 and then current drivers.
no result.

remove all nvidia-drivers and test from nvidia site 193.x.x.x
manual install with 
xserver-xorg-video-all , nouveau  removed.
and blacklist 
sudo /etc/modprobe.d/blacklist.conf
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

i take a black screen at start up.

---

### Post by The Bright Side on 2010-06-20
Hey guys,

today, I ran the update manager with the latest updates - several pieces of software, but no new kernel. Yet, after reboot, all my cool compiz effects were gone, and when I tried to re-enable them, I was told that they couldn't be enabled.

Nvidia-Settings still reports the latest stable driver (195.36.24) as installed and I can fully configure it, but actually have 3D effects? Hellz no.

So I tried to boot into the console, and fancy that: my screen stays black when trying to use the console. I tried Recovery mode, typing "sudo service gdm stop" into the Gnome terminal, or hitting CTRL-ALT-F1 or CTRL-ALT-BACKSPACE in Gnome. Everything leads to a black screen - my computer can no longer display the console.

This blows... Any ideas what's going on? Everything used to work flawlessly, but since Canonical decided to implant that crappy unfinished Nouveau into Ubuntu, it's all messy.

Graphics card: GeForce 6150SE nForce 430
Ubuntu: Lucid Lynx 64

Thanks!
M.

---

### Post by JPorter on 2010-06-21
Serious question:

Why would anyone feel the need to install using the Nvidia low-level installer, rather than using the conveniently packaged (and perfectly operational) Nvidia drivers in the Ubuntu repos?  

There's even an Nvidia PPA for those who want to run the latest-and-greatest immediately when it becomes available.

I just don't understand the folks in this thread who are hand-wringing over the Nvidia installer not working. Why does it matter?   This is Ubuntu in 2010 folks, not Red Hat in 1997.  They package this stuff, and it works.

---

### Post by JPorter on 2010-06-21
> **Fenris_rising said:**
> Hi there

I have just used the OP to upgrade to the latest Nvidia driver. Everything went perfectly I am glad to say. So cheers for that :KS

I am running Karmic at the moment. Not quite ready to brave lucid yet =D

BUT, there had to be one =D, Setting up my dual screen using the Nvidia config proved to be a pig..........again.

The xorg file it creates just doesn't equate to me setting up for dual screens. Infact a reboot gives me one screen the other is once again disabled in the nvidia config.

Luckily I had saved the original Xorg that was made when I setup the 185 driver which had all the right data to run my dual screens ONLY because I had to dig through the forum to guess at who's xorg files, as listed for help on this forum, looked like they had bits I needed. So I just swapped them over and all is well.

But why am I having this issue of Nvidia config not being able to set up my xorg to suit my needs? A little light on this would be great please!

regards

Fenris

Use [FONT="Courier New"]sudo nvidia-xconfig[/FONT] from a terminal, it will parse and merge your existing xorg.conf with the entries it needs.

---

### Post by K.Mandla on 2010-06-21
Moved to Tutorials and Tips. Why it was in the Cafe, I may never know. ...

---

### Post by Kosimo on 2010-06-21
> **K.Mandla said:**
> Moved to Tutorials and Tips. Why it was in the Cafe, I may never know. ...

Thanks for moving it. I was asking that for ages. Thing is that when I first wrote this topic I didn't include any guide. This mini "how to" was added several days later and I've been updating it since 2008. 

Would it be possible to change the title and remove any mention to drivers version?

Thank you again.

---

### Post by Kosimo on 2010-06-21
nvidia published new stable and beta drivers.

Stable drivers updated to 195.36.31:

Changelog: 

> Fixed a problem with SLI SFR, AFR, and SLIAA modes with GeForce GTX 480 and GeForce GTX 470 and high-resolution display modes.

Beta updated to 256.35

Changelog: 
> Fixed a regression in 256.29 where Performance Level clock frequencies were reported incorrectly in nvidia-settings.
Fixed a 3D Vision Stereo bug that caused the stereo glasses to not toggle when the flat panel was not running at its native mode timings.
Fixed a bug that caused nvidia-settings to crash when rendering its thermal gauge widget if the range of valid values for the thermal sensor was empty.


Download links at the first page like always.

Good luck

---

### Post by K.Mandla on 2010-06-21
> **Kosimo said:**
> Thanks for moving it. I was asking that for ages. Thing is that when I first wrote this topic I didn't include any guide. This mini "how to" was added several days later and I've been updating it since 2008. 

Would it be possible to change the title and remove any mention to drivers version?

Thank you again.
You're welcome, and I edited the title for you. Cheers! ;)

---

### Post by ahso4271 on 2010-06-22
Doesn't work. something at the install end was not found, installed the default Ubuntu drivers...not that old anyway.

Performance is better than on Win:
[http://www.phoronix.com/scan.php?page=article&item=linux_windows_part1&num=9/](http://www.phoronix.com/scan.php?page=article&item=linux_windows_part1&num=9/)

---

### Post by Linuxforall on 2010-06-22
> **ahso4271 said:**
> Doesn't work. something at the install end was not found, installed the default Ubuntu drivers...not that old anyway.

Performance is better than on Win:
[http://www.phoronix.com/scan.php?page=article&item=linux_windows_part1&num=9/](http://www.phoronix.com/scan.php?page=article&item=linux_windows_part1&num=9/)

It works fine here, as for performance, Linux is not yet a gaming platform but its getting there, however I was surprised to see that some of the benchmarks really had very little perceptible difference, there was no slaughter of Ubuntu by Win7.

---

### Post by Kosimo on 2010-06-22
> **k.mandla said:**
> you're welcome, and i edited the title for you. Cheers! ;)

&#12393;&#12358;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12290;

:)

---

### Post by Kosimo on 2010-06-23
Folks, 

nVidia has just promoted 256.35 to stable release!

Good luck

---

### Post by ahso4271 on 2010-06-24
> **Linuxforall said:**
> It works fine here, as for performance, Linux is not yet a gaming platform but its getting there, however I was surprised to see that some of the benchmarks really had very little perceptible difference, there was no slaughter of Ubuntu by Win7.

Yea on newer hardware is slightly faster but even for ages. I've played state of the art ID games around 9-4 years ago. Hoping for Rage though. Gaming platform? Well FSX on Wine would be really cool...I don't play Tomb Raider and all other stuff anymore so I'd be fine with ID, FSX and X-Plane. ( and Xmame :-)

Now could someone explain on how to install the latest 25* Nvidia drivers without messing up my 10.04 with default drivers?
Many thanks

---

### Post by Linuxforall on 2010-06-24
> **ahso4271 said:**
> Yea on newer hardware is slightly faster but even for ages. I've played state of the art ID games around 9-4 years ago. Hoping for Rage though. Gaming platform? Well FSX on Wine would be really cool...I don't play Tomb Raider and all other stuff anymore so I'd be fine with ID, FSX and X-Plane. ( and Xmame :-)

Now could someone explain on how to install the latest 25* Nvidia drivers without messing up my 10.04 with default drivers?
Many thanks

Go to terminal, paste sudo add-apt-repository  ppa:ubuntu-x-swat/x-updates

sudo apt-get update

Go to update manager and click on all updates listed. Enable nvidia driver via hardware drivers if you haven't done so already. The xswat ppa updates drivers within days of official release by nvidia. Best of all it doesn't break anything in Ubuntu, no need for any hacks to make it boot or work. Also when kernel gets updated, it fixes itself via dkms so save yourself all the hassle in case you don't wish to go through the routine of manual install for now.

---

### Post by ahso4271 on 2010-06-25
Thanks. I'll try that tomorrow.

---

### Post by saejin on 2010-06-25
I am posting this in the hopes it saves others time, and leads to a solution:

Problem:
I have been having  huge problems with nvidia drivers for my GeForce 6200. Using clean installs, I tried pretty much everyones recommendations, and tried pretty much every version of driver  I could lay my hands on.   I have a Dell 27 inch monitor that should easily support 1200 x 1600 but none of the install options offer a resolution higher than 1024 x 768 and many of them come up with less than that.  I messed with Grub2, X11-Config and most everything I could think of, each time doing a clean install.

Cause:
I use an older KVM switch.  When I took the KVM switch out of the picture and installs worked, I got full resolution.   
It appears that the software is automatically asking the hardware for capabilities, but when the KVM is in the picture the answers are wrong.

Want:
I would like to be able to do installs and boots without removing and reinstalling my KVM switch.  It would seem pretty reasonable that the driver should simply offer every possible resolution regardless of rather the monitor supports the resolution, allowing the user to choose the resolution incorrectly (like windows) and recover.

Question:
Does anyone know of a way to modify things such that the install and boot do not check display hardware, but instead give a fixed set of options that include most of the options above 1024 x768?

---

### Post by Linuxforall on 2010-06-25
Don't know if this will work, alt+F2 gksudo nvidia-settings select your resolution and save to X and reboot.

---

### Post by Jugador on 2010-06-27
I just installed Ubuntu 10.04.  My resolution was great until I was prompted to use the nVidia proprietary driver.  I installed and rebooted.  Now my resolution is wrong.  I should be at 1680x1050, but am at 1024x768.  When I go to the nVidia X Server Settings screen, there is no resolution option greater than 1360x768.

After reading some of the other posts in this an other threads, I ran "sudo nvidia-xconfig" and got this message:
```

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

If anyone could help get to the proper resolution of 1680x1050, I'd greatly appreciate it.

Thanks!

---

### Post by Jugador on 2010-06-27
I got it working finally.  I found another post on another board and used its xorg.conf settings.  Basically I changed this:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

to this:

```

Section "Monitor"
# HorizSync source: xconfig, VertRefresh source: xconfig
Identifier "Monitor0"
VendorName "Westinghouse"
ModelName "LCD Panel 1680x1050"
HorizSync 30.0 - 82.0
VertRefresh 60.0
DisplaySize 1680 1050
Option "DPMS"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "TwinViewXineramaInfoOrder" "CRT-0"
Option "metamodes" "1680x1050 +0+0"
	SubSection "Display"
	Depth 24
	Modes "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

I hope that doesn't screw anything else up, but so far so good.

---

### Post by dwpbike on 2010-06-28
"how to install"?  not.  small items such as "which driver do i need?" and sending me a page that shows ftp without telling me how to make that happen just doesn't help.

i'm trying to make the jump from redhat/fedora (since '03) to ubuntu.  a video driver for nvidia geforce go 7600 graphics card should not be the sticking point.

---

### Post by Kosimo on 2010-06-28
> **dwpbike said:**
> "how to install"?  not.  small items such as "which driver do i need?" and sending me a page that shows ftp without telling me how to make that happen just doesn't help.

i'm trying to make the jump from redhat/fedora (since '03) to ubuntu.  a video driver for nvidia geforce go 7600 graphics card should not be the sticking point.



If you really want a smooth transition, just install Ubuntu and let the system make all the work for you by using the automatic driver detection. No efforts needed. It just works. That's it. 

If you want to manually install the really "cutting edge" drivers, because you're interested and you want to spend some time tweaking your system, and you don't mind to take some risks, read the how-to again and you'll find specific instructions about how to choose the appropriate driver and how to install it.   If you still have questions, ask in this same thread and we'll be pleased to help you.   This would be way better than just complaining for something that was created with the only intention of helping people.

Good luck.

---

### Post by abedepaul81 on 2010-06-29
I have an issue....

I download the 173.14.25 ....32 bit file
stop gdm
sh the .run file
installation starts well...then a warning:

"you do not appear to have an nvidia gpu supported by the 173.14.25......"

then it lets me continue and accept the terms of conditions agreement and looks like its installing then says an error that it cant install the driver....(if you need the actual error then I guess I can duplicate it and write it all down)
and it takes me back to the terminal.

hope anyone has some indo to help me use this card on my favorite system

---

### Post by saejin on 2010-06-30
Much of what is posted here works only for old versions, and does not work for version 10.4 Lucid Lynx. If you go want to go with the flow (which is not as smooth as it should be, but we can all blame ourselves for buying invidia :evil:  which refuses to go with the flow and be open source)here is what works for 10.4 Lucid Lynx.

:guitar:
Go here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Fill out what hardware you have and let it select which driver you should down load.
For me it downloaded NVIDIA-Linux-x86-256.35.run and put it in my Download directory.

Next I had to remove my KVM Switch so the X software could get automatic replies from my monitor.

Next, You can not change X server while you are running on X server.
Do not type the part after the #, those are comments!  :lolflag:


CTRL ALT F1    #get to console
sudo init 1        #so the X server will NOT start at boot
sudo reboot

                       #Log back in
cd Download    #change directory to where you down loaded the latest driver
sudo sh NVIDIA-Linux-x86-195.36.31.pkg1.run #installs the driver
sudo init 3        #so the X server WILL start at boot
sudo reboot

                       #log back in
CTRL ALT F1    #get to console
sudo /usr/bin/nvidia-settings #run as root so you can save the config file
                       #set the X Server Display Configuration
                       #save the X Configuration File
sudo reboot

---

### Post by ratcheer on 2010-06-30
saejin, if that works it will be a great thing for everyone who has been struggling with this. Your instructions are clear and consise. Thank you.

Tim

---

### Post by ratcheer on 2010-06-30
No, I couldn't get it to work. At the second step, "sudo init 1", it threw up a plymouth purple screen and wouldn't let me do anything else. When I rebooted, it came back up in normal X mode. :confused:

Tim

---

### Post by Sairin_Lote on 2010-07-01
> **ratcheer said:**
> No, I couldn't get it to work. At the second step, "sudo init 1", it threw up a plymouth purple screen and wouldn't let me do anything else. When I rebooted, it came back up in normal X mode. :confused:

Tim

it won't work for me either. same problem

---

### Post by Kosimo on 2010-07-01
Can anyone confirm that the instructions posted in the first topic aren't working on Ludic Lynx?

---

### Post by Turbis on 2010-07-01
Hi, I just did a clean install of Ubuntu 10.04 and following the guide gave me errors in the installer.
It told me it failed to run the pre-script something, is there anything I need to do on a clean Ubuntu 10.04 install prior to following the guide in the opening post?

I went on with the install even though the pre-install script failed, here is the log that was generated.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jul  1 18:36:12 2010
installer version: 256.35

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.35.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-21-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-21-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.32-21-generic/b
   uild SYSOUT=/lib/modules/2.6.32-21-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.tmp_versions ; r
   m -f /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.3
   5/kernel
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nv.o.d  -nos
   tdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/us
   r/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/linu
   x/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototype
   s -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-
   declaration -Wno-format-security -fno-delete-n
   ull-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fu
   nit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -Wsig
   n-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSIO
   N_STRING=\"256.35\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.3
   5/kernel/.tmp_nv.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nv.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nv_gvi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz334
   7/NVIDIA-Linux-x86_64-256.
   35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -D
   MODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -mcmodel=kernel -mno-red-zone -
   UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/.tmp_nv_gvi.o /tmp/selfgz3347/NVIDIA-
   Linux-x86_64-256.35/kernel/nv_gvi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nv-vm.o.d  -
   nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format
   -security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-z
   one -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-prot
   ector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compa
   re -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -W
   frame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -
   pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno
   -dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.3
   5/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -mcmodel=kernel -mno-red-zone -U
   DEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz33
   47/NVIDIA-Linux-x86_64-256.35/kernel/.tmp_nv-vm.o /tmp/selfgz3347/NVIDIA-Lin
   ux-x86_64-256.35/kernel/nv-vm.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.os-agp.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/
   selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -Wsign-compare -Wno-c
   ast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.3
   5\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)"  -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.t
   mp_os-agp.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/os-agp.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.os-interface
   .o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror
   -implicit-function-declaration -Wno-format-security -fno-delete-null-pointer
   -checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-ti
   me -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I
   /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -Wsign-compare -
   Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"
   256.35\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -
   D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.3
   5/kernel/.tmp_os-interface.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kern
   el/os-interface.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.os-registry.
   o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclu
   de  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O
   2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccum
   ulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGN
   AL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse 
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-poi
   nter-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/s
   elfgz3347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35
   \" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUI
   LD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME
   =KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kerne
   l/.tmp_os-registry.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/os-re
   gistry.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nv-i2c.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ 
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -Werror-implicit-function-declaration -Wno-format-security -fno-delete
   -null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -
   funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=102
   4 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-afte
   r-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fcon
   serve-stack -I/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -W
   sign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VER
   SION_STRING=\"256.35\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_
   64-256.35/kernel/.tmp_nv-i2c.o /tmp/
   selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nv-i2c.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nvacpi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optim
   ize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz3347/NVIDIA
   -Linux-x86_64-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-err
   or -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -mcmodel=kern
   el -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.tmp_nvacpi.o /tmp/s
   elfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nvacpi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   3347/NVIDIA-Linux-x86_64-256.35/kernel/nvacpi.o";
     ld -m elf_x86_64   -r -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel
   /nvidia.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nv-kernel.o /tmp
   /selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nv.o /tmp/selfgz3347/NVIDIA-Li
   nux-x86_64-256.35/kernel/nv_gvi.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35
   /kernel/nv-vm.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/os-agp.o /
   tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/os-interface.o /tmp/selfgz3
   347/NVIDIA-Linux-x86_64-256.35/kernel/os-registry.o /tmp/selfgz3347/NVIDIA-L
   inux-x86_64-256.35/kernel/nv-i2c.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.3
   5/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/ker
   nel/nvidia.ko;) > /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/modules.
   order
   make -f /usr/src/linux-headers-2.6.32-21-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-21-generic/Modu
   le.symvers -I /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/Module.symve
   rs  -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/Module.symvers -S -
   w  -s
   WARNING: could not find /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.n
   v-kernel.o.cmd for /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nv-kern
   el.o
     cc -Wp,-MD,/tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/.nvidia.mod.o
   .d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2
   -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumul
   ate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL
   _FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -m
   no-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer
   -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-s
   ign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz3
   347/NVIDIA-Linux-x86_64-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qua
   l -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"256.35\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG 
   -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz3347/NVIDIA-
   Linux-x86_64-256.35/kernel/nvidia.mod.o /tmp/selfgz3347/NVIDIA-Linux-x86_64-
   256.35/kernel/nvidia.mod.c
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-21-generic/scripts/mo
   dule-common.lds --build-id -o /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/ker
   nel/nvidia.ko /tmp/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nvidia.o /tm
   p/selfgz3347/NVIDIA-Linux-x86_64-256.35/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1
   No such device
-> Kernel messages:
   [   59.208322] end_request: I/O error, dev fd0, sector 0
   [  274.514752] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  309.363489] nvidia: module license 'NVIDIA' taints kernel.
   [  309.363492] Disabling lock debugging due to kernel taint
   [  309.876936] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  309.876938] NVRM: This can occur when a driver such as nouveau, rivafb,
   [  309.876939] NVRM: nvidiafb, or rivatv was loaded and obtained ownership
   of
   [  309.876940] NVRM: the NVIDIA device(s).
   [  309.876941] NVRM: Try unloading the conflicting kernel module (and/or
   [  309.876941] NVRM: reconfigure your kernel without the conflicting
   [  309.876942] NVRM: driver(s)), then try loading the NVIDIA kernel module
   [  309.876943] NVRM: again.
   [  309.876944] NVRM: No NVIDIA graphics adapter probed!
   [  351.131466] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
   [  351.134567] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc:
   initialised FIFO 2
   [  722.717865] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [ 1066.711046] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [ 1066.711049] NVRM: This can occur when a driver such as nouveau, rivafb,
   [ 1066.711049] NVRM: nvidiafb, or rivatv was loaded and obtained ownership
   of
   [ 1066.711050] NVRM: the NVIDIA device(s).
   [ 1066.711052] NVRM: Try unloading the conflicting kernel module (and/or
   [ 1066.711052] NVRM: reconfigure your kernel without the conflicting
   [ 1066.711053] NVRM: driver(s)), then try loading the NVIDIA kernel module
   [ 1066.711053] NVRM: again.
   [ 1066.711055] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by AaronP_ on 2010-07-01
[quote="Turbis"]
It told me it failed to run the pre-script something
[/quote]
Ubuntu installs a pre-install script that purposely fails, specifically to cause that error:
[quote="/usr/lib/nvidia/pre-install"]

#!/bin/sh

# Trigger an error exit status to prevent the installer from overwriting
# Ubuntu's nvidia packages.

exit 1
[/quote]
You can still install the driver through the .run package, you just have to tell it to continue anyway, or pass the --no-distro-scripts option to the installer.

The intention is to make it clear to people that they'll have better luck using the Ubuntu packages instead of trying to use nvidia-installer.

---

### Post by Turbis on 2010-07-01
Hey I got it working with a little help from *[This guide](http://jeffhoogland.blogspot.com/2010/04/installing-nvidia-driver-in-ubuntu-1004.html)*.

---

### Post by ratcheer on 2010-07-01
> **Kosimo said:**
> Can anyone confirm that the instructions posted in the first topic aren't working on Ludic Lynx?

I just tried it. I removed the current nVidia proprietary driver and rebooted. It successfully used the open source driver.

Then, when I did Ctrl-Alt-F1, it took me to a wild black screen with flashing bright turquoise vertical bars. I could do nothing else. I rebooted and it still looks good with the open source 
driver.

I tried Ctrl-Alt-F1 again with the same result. So, no, the procedure on Post 1 is not working for me, either.

Tim

---

### Post by ratcheer on 2010-07-02
See post 1349. Can anyone help me get to a usable console screen?

Thanks,
Tim

---

### Post by ratcheer on 2010-07-02
> **ratcheer said:**
> See post 1349. Can anyone help me get to a usable console screen?


Never mind. I got there by booting to single-user mode, then "telinit 3".

I still couldn't install the latest nVidia driver, though. It failed due to something about my header libraries. I ran aptitude and found them and they appear to be installed. What a pain.

Tim

---

### Post by Kosimo on 2010-07-03
> **ratcheer said:**
> Never mind. I got there by booting to single-user mode, then "telinit 3".

I still couldn't install the latest nVidia driver, though. It failed due to something about my header libraries. I ran aptitude and found them and they appear to be installed. What a pain.

Tim

Hello.


Here some further information taken from nvidia website: 

> Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:
* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:
DISABLED_MODULES="nv nvidia_new"
Additionally, delete the following file if it exists:
/lib/linux-restricted-modules/.nvidia_new_installed

Hope it helps.

---

### Post by JPorter on 2010-07-08
I'm still not really following the point of this thread.  The packaged Nvidia drivers work very well.  What is the purpose of instructing users to ignore the packaged version and instead (rather laboriously) install the Nvidia binaries from scratch?  I don't get it.

Even for users that want to jump ahead of the standard repo versions, there are better options.  For example, the very-often-updated (and quite convenient) packages on the [X-Swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

Seriously... is there any demonstrable advantage whatsoever to doing a fully manual install of the Nvidia driver on an Ubuntu desktop system?


AT THE VERY LEAST could Kosimo please edit Post #1 to put a note across the top telling people that this procedure isn't necessary for general installation of the proprietary Nvidia drivers, and certainly not for the average user?  Many people here forget that users who are new to Ubuntu (or new to linux in general) will read a thread called "nVidia latest Drivers - How to install" and automatically assume that this is the required process to get an Nvidia card working well under Ubuntu.  That's not correct, and yet clearly we have new users making that exact error many times in this thread.  Why not just solve the issue up front with a big warning and a note that none of this is necessary?

---

### Post by saejin on 2010-07-08
JPorter,
Clearly, if the packaged Nvidia driver simply installed, worked, and gave full resolution, for every given set of hardware, this thread would not exist,as there would be no problems.

Of course this is not the case, and the manual work around was not obvious to many people, especially those people that came from windows, and have no clue outside of a gui.

If we want to keep everyone on board, rather than having them give up on Ubuntu because off the shelf distro did not deliver for them, then we must show them the work around.

If you have a problem with that lets meet behind the school at recess :-)

---

### Post by VastOne on 2010-07-08
> **saejin said:**
> JPorter,
Clearly, if the packaged Nvidia driver simply installed, worked, and gave full resolution, for every given set of hardware, this thread would not exist,as there would be no problems.

Of course this is not the case, and the manual work around was not obvious to many people, especially those people that came from windows, and have no clue outside of a gui.

If we want to keep everyone on board, rather than having them give up on Ubuntu because off the shelf distro did not deliver for them, then we must show them the work around.

If you have a problem with that lets meet behind the school at recess :-)

I have to agree with JPorter on this one 100%

When I came in to Ubuntu 2.5 years ago this was one of the threads that taught me an incredible amount...

Having said that, over the last 4-5 months I have had tremendous amount of issues running any update under these instructions, more to do with Ubuntu than nVidia (kernel issues)

Since I found Xorg-edgers PPA and XSwat PPA I have never looked back and have had zero issues, even living on the edge of daily kernel rebuilds and the development side. 

And with ppa-purge, it is even that much easier.  

I have appreciated every thing Kosimo has done and I cannot imagine the work put into this.  I have always admired this thread and those who respond to it.

This is all IMHO

):P

---

### Post by Kosimo on 2010-07-09
> **VastOne said:**
> I have to agree with JPorter on this one 100%

When I came in to Ubuntu 2.5 years ago this was one of the threads that taught me an incredible amount...

Having said that, over the last 4-5 months I have had tremendous amount of issues running any update under these instructions, more to do with Ubuntu than nVidia (kernel issues)

Since I found Xorg-edgers PPA and XSwat PPA I have never looked back and have had zero issues, even living on the edge of daily kernel rebuilds and the development side. 

And with ppa-purge, it is even that much easier.  

I have appreciated every thing Kosimo has done and I cannot imagine the work put into this.  I have always admired this thread and those who respond to it.

This is all IMHO

):P



I really appreciate your post, it really made my day better after all this years updating this thread. :)

Having said that, it is true that many users like you are having serious issues with the manual installation process in Ubuntu 10.04  and it is my intention to find out why this is happening, and update the first page "how-to" in order to get the drivers installed properly and have smooth kernel updates.  

If anyone wants to help me with those instructions and find out what is actually happening  in order to help many people that still wants to install their nVidia drivers manually I would really appreciate it. 

Kosimo.

---

### Post by moxxx on 2010-07-09
> **saejin said:**
> Much of what is posted here works only for old versions, and does not work for version 10.4 Lucid Lynx. If you go want to go with the flow (which is not as smooth as it should be, but we can all blame ourselves for buying invidia :evil:  which refuses to go with the flow and be open source)here is what works for 10.4 Lucid Lynx.

:guitar:
Go here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Fill out what hardware you have and let it select which driver you should down load.
For me it downloaded NVIDIA-Linux-x86-256.35.run and put it in my Download directory.

Next I had to remove my KVM Switch so the X software could get automatic replies from my monitor.

Next, You can not change X server while you are running on X server.
Do not type the part after the #, those are comments!  :lolflag:


CTRL ALT F1    #get to console
sudo init 1        #so the X server will NOT start at boot
sudo reboot

                       #Log back in
cd Download    #change directory to where you down loaded the latest driver
sudo sh NVIDIA-Linux-x86-195.36.31.pkg1.run #installs the driver
sudo init 3        #so the X server WILL start at boot
sudo reboot

                       #log back in
CTRL ALT F1    #get to console
sudo /usr/bin/nvidia-settings #run as root so you can save the config file
                       #set the X Server Display Configuration
                       #save the X Configuration File
sudo reboot

Guys, I'm trying to do this but after the first step, "sudo init 1", it automatically tries to reboot (I assume that's what it's doing) but gets stuck on an Ubuntu screen with loading dots. I have to force a reboot and when I do and try to install it says the X server is still running.

Any ideas? New jack, sorry. I'm trying.

---

### Post by ratcheer on 2010-07-09
I must admit that, after being a dedicated manual installer ever since I started using Ubuntu, today I finally got the x-swat ppa properly configured and got the 256.35 driver installed in Lucid (and Maverick) without a hitch.

I added both the binary and source ppa's as instructed on the launchpad page. Then I ran "sudo aptitude update", "sudo aptitude safe-upgrade", and rebooted. That was all there was to it. I did not even remove the 195 driver, first. (In Maverick, I was still on nouveau after a fresh reinstallation, so I just ran "sudo aptitude install nvidia-current".)

I tried very hard to do this manually, about a week ago (see some of my recent posts in this thread. Everything failed for one reason or another. The ppa was a breeze.

I am losing confidence in myself as a result. :redface: :cry:

Tim

---

### Post by artisan on 2010-07-27
[QUOTE=JPorter]I'm still not really following the point of this thread.  The packaged Nvidia drivers work very well.  What is the purpose of instructing users to ignore the packaged version and instead (rather laboriously) install the Nvidia binaries from scratch?  I don't get it.

[/QUOTE]

There have been 269,835 hits on this thread as of 27/07/2010.
Maybe thats a hint that the packaged drivers still do not work for everyone.
.

[QUOTE=JPorter]
Seriously... is there any demonstrable advantage whatsoever to doing a fully manual install of the Nvidia driver on an Ubuntu desktop system?
[/QUOTE]
What you mean to say is.
The drivers work for me.
What's everyone elses problem?


[QUOTE=JPorter]
AT THE VERY LEAST could Kosimo please edit Post #1 to put a note across the top telling people that this procedure isn't necessary for general installation of the proprietary Nvidia drivers, 
[/QUOTE]
You are making no sense.
"Oh I have just down loaded Ubuntu for the first time burnt it to cd and installed it. I know I will look in the forums for a thread called Nvidai drivers and see if I should install different drivers"
Is most probably NOT the first reaction from some one who has just moved from Windoze.


How about the packaged drivers are STILL borked.
I have just had to download and install a fresh edition of 10.4 and I can assure everyone that the Nvidia drivers are still NOT correct.
I have been using Ubuntu for a couple of years.
Have installed VMware, run Windoze inside that.
Installed and used the server edition of Ubuntu.
So would not describe myself a a noob.
Not 100% computer literate but, can use a standard desktop and can safely say to the Nvidia drivers are still borked.
I can report that my machine shuts down after 5 minutes on the first boot of the day.
I tracked this down to the video drivers but, had a slight run in with an automatic update that took down my printer which meant a total re install, which means that I now have to track down the problem again.

Like I say. 269,835 views to date.

---

### Post by VastOne on 2010-07-27
> **artisan said:**
>  Like I say. 269,835 views to date.

No one here has diminished the value of this thread at all, in fact more have praised it than anyone.  I am pretty sure JPorter, like a lot of us have had issues with the manual installs and have found other means.

If you as a seasoned user, or any noob, simply look up xorg-edgers or x-swat on this forum or google, and follow the instructions, including the very very effective ppa-purge tool, you will see a totally new way of implementing nVidia drivers and xorg tools.  

Like Ratcheer said, on both Lucid and Alpha 2 of Maverick, where there are daily changes, there is 0 problems using xorg-edgers.

That is saying something...new nVidia, new xorg on the latest and kernel and OS with no issues. 

Again, a bazillion thanks to Kosimo who has _A Legend_ status in my book!

---

### Post by jokerrain on 2010-07-27
> **moxxx said:**
> Guys, I'm trying to do this but after the first step, "sudo init 1", it automatically tries to reboot (I assume that's what it's doing) but gets stuck on an Ubuntu screen with loading dots. I have to force a reboot and when I do and try to install it says the X server is still running.

Any ideas? New jack, sorry. I'm trying.


I'm getting the same problem any fix to this or any way of killing x server. I've tried Google and its no help lol so any help would be greatly appreciated. 


edit: nevermind i figured it out i just login inthe terminal as root typed gdm stop and it appered to work it stopped the x server so i can load the lastest drivers


edit 2: ok driver starts then it says 

ERROR: unable to load the kernel module 'nvidia.ko'  what does that mean? sorry very new to all of this

---

### Post by george051685 on 2010-07-28
ok i need some help im new to the linux os i am still trying to learn it and im trying to install a 9800gt nvidia graphics card on my ubuuntu i have been reading forums for the last 5 days and still no luck i managed to do a install and it is giving me the following errors

distribution pre install script failed

install failed /var/log/nvidia-installer.log

unable to load kernal module 'nvidia,ko,

any help to get this issue fixed would be much appreciated i am trying to run compiz

---

### Post by Gemnoc on 2010-07-28
Hi george051685,

if you are new to Linux, why are you taking the hard way ?

I have the same card, and I use the Nvidia drivers from the Ubuntu repositories, Compiz runs mighty fine with those ! Even though I'm following this thread, I've never needed to install the drivers that way.

You just need to go to System > Administration > Hardware Drivers and install/activate the proprietary Nvidia drivers.

Although you will need to remove anything you have done so far, and I can't help you with that.

---

### Post by Kosimo on 2010-08-03
Folks, 

nVidia has just released a new "Pre-Release" driver: **[COLOR="Red"]256.44[/COLOR]**


Here the changelog: 

> Added support for Quadro 4000, Quadro 5000, and Quadro 6000.
Added support for GeForce GTX 460.
Updated nvidia-installer to detect the nouveau kernel module and fail with an appropriate error message.
Added information to the NVIDIA driver README on how to disable the nouveau driver.
Fixed VDPAU to not print a debug error message when calling VdpVideoMixerQueryFeatureSupport with an unsupported or unknown VdpVideoMixerFeature.
Removed the requirement that in TwinView passive stereo, MetaModes must have identical viewports on each monitor.
Removed the requirement that in active stereo, all monitors must use identical modetimings.
Enhanced VDPAU to better report certain kinds of initialization error.
Fixed a regression that caused Xv to return BadAlloc errors on AGP systems when using the AGP GART driver contained in the NVIDIA driver. This fixes the problem reported in nvnews.net thread 151199.


Download links at the first page of this thread, like always. 

Good luck

---

### Post by ratcheer on 2010-08-03
> **Kosimo said:**
> Folks, 

nVidia has just released a new "Pre-Release" driver: **[COLOR=Red]256.44[/COLOR]**




Got it. Thanks. It is running well on Lucid and Maverick, for me.

Tim

---

### Post by Kosimo on 2010-08-10
256.44 has been promoted to Stable.

Links at the first page of this thread. 

Good luck.

---

### Post by kva on 2010-08-10
I just installed latest NVIDIA driver 256.44, i follow what is instructed on 

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

and then directly install the driver from terminal as instructed on

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Compiz works great..

Thanks folk..

NB:Any previously proprietary driver installed must be removed first..

---

### Post by JPorter on 2010-08-11
> **artisan said:**
> There have been 269,835 hits on this thread as of 27/07/2010.
Maybe thats a hint that the packaged drivers still do not work for everyone.
If the packaged drivers do not work, the proper response is to file a bug report on Launchpad and involve the developers and package maintainers directly in the resolution of the problem.  Manual workarounds are fine in individual cases, but they should only be used (and described) as temporary workarounds, not as "fixes".

> **artisan said:**
> What you mean to say is.
The drivers work for me.
What's everyone elses problem?
I said nothing like that. I personally use the proprietary Nvidia drivers on 5 significantly different platforms at the moment, and I've had my share of small configuration issues, but generally speaking there was usually an actual solution to the problem that didn't involve breaking the Ubuntu user interface paradigm by dropping runlevels to manually install a driver. 

It's worth searching the forums on Phoronix for discussion of driver issues that aren't related to Canonical's packaging, by the way... the Nvidia developers participate there.

> **artisan said:**
> You are making no sense.
"Oh I have just down loaded Ubuntu for the first time burnt it to cd and installed it. I know I will look in the forums for a thread called Nvidai drivers and see if I should install different drivers"
Is most probably NOT the first reaction from some one who has just moved from Windoze.
I disagree. One of the first things that many new users do when they have a question about something is to search a forum (in this case, Ubuntuforums) for the "community answer".  Users that aren't yet familiar with the package system tend to immediately search for "ubuntu nvidia drivers" or similar and then unthinkingly execute the first credible-looking instructions that they find. On Ubuntuforums, that tends to be this thread.

It's a great thread, don't get me wrong! The information here is excellent... it's just not *recommended* unless the standard methods to install and use the proprietary drivers have already failed.

> **artisan said:**
> How about the packaged drivers are STILL borked.
I have just had to download and install a fresh edition of 10.4 and I can assure everyone that the Nvidia drivers are still NOT correct.
I have been using Ubuntu for a couple of years.
Have installed VMware, run Windoze inside that.
Installed and used the server edition of Ubuntu.
So would not describe myself a a noob.
Not 100% computer literate but, can use a standard desktop and can safely say to the Nvidia drivers are still borked.
I can report that my machine shuts down after 5 minutes on the first boot of the day.
I tracked this down to the video drivers but, had a slight run in with an automatic update that took down my printer which meant a total re install, which means that I now have to track down the problem again.
Are you using an unusual Nvidia product? There are many reasons why you may be having difficulty, and only a few of them are actually related to the driver itself.  Quite possibly, the driver may be exposing a bug in another package.  That's what bug reports via Launchpad are for, to consolidate community feedback on errors and maximize the amount of information available to developers so that they can fix these issues at the root cause.

> **artisan said:**
> Like I say. 269,835 views to date.
That figure could be used as proof of your point or of mine, they're both valid.

---

### Post by JPorter on 2010-08-11
> **kva said:**
> I just installed latest NVIDIA driver 256.44, i follow what is instructed on 

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

and then directly install the driver from terminal as instructed on

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Compiz works great..

Thanks folk..

NB:Any previously proprietary driver installed must be removed first..

I'm using 256.44 as well, I installed it by running System -> Administration -> Update Manager and clicking the Install Updates button.

It's in the Ubuntu X Updates PPA:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Caironater on 2010-08-24
> **Kosimo said:**
> *Edit August 10 2010*: Latest nVidia 256.xx (STABLE) **[COLOR=Red]256.44[/COLOR]** 
**[COLOR=Red]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR=Red]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)


Can i get the package straight from tty?
EDIT: sorry usb i meant

---

### Post by Kosimo on 2010-08-25
> **Caironater said:**
> Can i get the package straight from tty?
EDIT: sorry usb i meant

Let me try to understand what your question is.    You want to get the driver directly from a usb device?  If yes, you should mount the unit first, and then run it from the unit itself.

---

### Post by Caironater on 2010-08-25
> **Kosimo said:**
> Let me try to understand what your question is. You want to get the driver directly from a usb device? If yes, you should mount the unit first, and then run it from the unit itself.
 
But how do I do that?

---

### Post by mtech84 on 2010-08-27
please help i am using ubuntu 9.04 and i have onboard graphics that is nvidia geforce 8100 / nforce 720a and i tried uninstalling and reinstalling the driver recommended by ubuntu (180.44 driver)itself but it is not picking up the highest resoltion supported by my lcd screen . in windows it is good is working on 1680x1052 @59hz so i am trying to get this back on ubuntu. previously it was there but when i removed the hard disk and put it back it lost it after putting the harddisk back. 

irony is i can enable the normal appearance efffect and it works too on low resolution but why the hell its not even showing the highest resoultion. the max is showing in display settings is 1320x768 

please help me..

thx a lot

---

### Post by GeekGirl1 on 2010-08-27
> **JPorter said:**
> I'm using 256.44 as well, I installed it by running System -> Administration -> Update Manager and clicking the Install Updates button.

It's in the Ubuntu X Updates PPA:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)Thank you. Works fine. Just reboot to restart the X-server.

---

### Post by mtech84 on 2010-08-28
> **mtech84 said:**
> please help i am using ubuntu 9.04 and i have onboard graphics that is nvidia geforce 8100 / nforce 720a and i tried uninstalling and reinstalling the driver recommended by ubuntu (180.44 driver)itself but it is not picking up the highest resoltion supported by my lcd screen . in windows it is good is working on 1680x1052 @59hz so i am trying to get this back on ubuntu. previously it was there but when i removed the hard disk and put it back it lost it after putting the harddisk back. 

irony is i can enable the normal appearance efffect and it works too on low resolution but why the hell its not even showing the highest resoultion. the max is showing in display settings is 1320x768 

please help me..

thx a lot

it is working now. what a silly thing... 1st uninstall it using hardware drivers and remove shutdown and wait for some time or else if you have windows installed go to windows and wait that is necessary. now after prolong time go back and install it same way you removed it and thats it restart and voila you have it.

thx again...

---

### Post by Caironater on 2010-08-29
> **mtech84 said:**
> it is working now. what a silly thing... 1st uninstall it using hardware drivers and remove shutdown and wait for some time or else if you have windows installed go to windows and wait that is necessary. now after prolong time go back and install it same way you removed it and thats it restart and voila you have it.
 
thx again...
 
How do you know that you need to wait?

---

### Post by Kosimo on 2010-09-01
Hi guys, here a new driver release:   256.53

Changelog: 

> Fixed a bug that prevented XvMC from initializing in most cases.
Added support for xorg-server video driver ABI version 8, which will be included in the xorg-server-1.9 series of releases.
Fixed a bug that caused extremely slow rendering of OpenGL applications on X screens other than screen 0 when using a compositing manager.
Fixed a regression introduced after 256.35 that caused stability problems on GPUs such as GeForce GT 240.
Fixed a slow kernel virtual address space leak observed when starting and stopping OpenGL, CUDA, or VDPAU applications.
Fixed a bug that left the system susceptible to hangs when running two or more VDPAU applications simultaneously.

Download links at the first page of this thread, like always.

Good luck!

---

### Post by mantaor on 2010-09-07
Hi Kosimo,
I'm sorry for my bad english. I'm not a long term user of ubuntu and for this reason, I really appreciate your initial procedure about installation of nvidia driver.
Then, my question:
If I perform a clean installation of ubuntu, I'd start with nouveau driver. Can I install 256.53 driver from System->Administration->Driver hardware or I must follow your procedure to minimize the risk to have problems of any kind? 

Thank you in advance

PS in the next weeks, I wish to buy a gainward GT240 1GB ddr5

---

### Post by Kosimo on 2010-09-09
> **mantaor said:**
> Hi Kosimo,
I'm sorry for my bad english. I'm not a long term user of ubuntu and for this reason, I really appreciate your initial procedure about installation of nvidia driver.
Then, my question:
If I perform a clean installation of ubuntu, I'd start with nouveau driver. Can I install 256.53 driver from System->Administration->Driver hardware or I must follow your procedure to minimize the risk to have problems of any kind? 

Thank you in advance

PS in the next weeks, I wish to buy a gainward GT240 1GB ddr5


Hello Mantaor. 

If you want to reduce the risk as much as possible, you shouldn't manually install nVidia drivers as it always gives you some risks if you didn't do it properly (especially after a kernel upgrade). 

In this case the safest procedure is to get Ubuntu to install the proprietary drivers for you. This drivers aren't updated to the latest version, (I don't remember which version comes with 10.4, but certainly not the latest one) But they are definitely stable, safe and if you're not affected by any particular bug is the best thing to do (in order to be extremely safe).


There are some PPA's that will help you to automatically install the latest drivers without having to manually compile anything. (like X Updates) This of course puts you in the hands of the development team that is maintaining this PPA. But, after some months, many users in this thread said that everything works quite well for them. You can have a look here: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And if you really want to take the total control of your system you can always try to manually compile and install the latest drivers by yourself (this is my favorite way) by just following the instructions I wrote in the first page of this thread. Just be careful to do it from a clean install, and be sure that you use the script that will automatically compile the drivers again after a kernel upgrade, (something that you can also do it each time you get a kernel upgrade and you can't start X). 

I hope this instructions can help you. 


Best regards.

---

### Post by Kosimo on 2010-09-09
Folks, a new **[COLOR="Red"]BETA[/COLOR]** series is here. 

nVidia has just released **[COLOR="red"]260.19.04[/COLOR]** with so many change logs, here the complete list: 


> Added support for the nvcuvid API.

nvcuvid provides a mechanism for decoding video and exposing the surfaces to CUDA, allowing applications to perform custom processing of the video. nvcuvid is primarily targeted at transcoding and video- processing applications. nvcuvid was already available on other platforms.

By default, nvidia-installer places the nvcuvid library in /usr/lib/libnvcuvid.so, or in the appropriate library path for your system. The nvcuvid header files can be retrieved from the CUDA toolkit package.
Stopped packaging and installing OpenGL, VDPAU, CUDA, and OpenCL header files with the driver. Those interested in these files can get them from their Linux distributions' packages, where available, or upstream:
OpenGL header files (gl.h, glext.h glx.h, glxext.h)
VDPAU header files (vdpau.h and vdpau_x11.h)
CUDA and OpenCL header files (cuda.h, cudaGL.h, cudaVDPAU.h, cl.h, cl_gl.h, cl_platform.h)

Note that while libvdpau.so is still included in 260.xx drivers, it will be removed from a future release series in early 2011. Distributors are encouraged to package libvdpau.so from [http://freedesktop.org/wiki/Software/VDPAU](http://freedesktop.org/wiki/Software/VDPAU)
Fixed a bug in VDPAU that could cause a "display preemption" when toggling MPlayer to full-screen the first time.
Added OpenGL 4.1 support for Quadro Fermi, GeForce GTX 4xx, and later GPUs.
Enhanced VDPAU to fully support Xinerama.
Fixed a bug in the X driver that prevented operation of Xinerama when using multiple NVIDIA GPUs from different major hardware generations on X with ABI 4 or greater.
Fixed a bug in the OpenGL driver's Xinerama support.

Rendering should have ocurred to all physical X screens driven by an NVIDIA GPU compatible with the NVIDIA GPU driving physical X screen 0. However, if some physical X screen did not satisfy that requirement, then not only would that physical X screen not be rendered to (as expected), but also all physical X screens with a higher number would not be rendered to (which was unexpected).
Added GPU "Processor Clock" reporting to the nvidia-settings PowerMizer page.
Implemented support for SLI Mosaic Mode on Quadro FX 5800 and Quadro Fermi and newer Quadro GPUs.
Enhanced the VDPAU overlay-based presentation queue to allow it to be used when SLI is active, and in some cases when the X Composite extension is enabled. See the README for further details.
Added support for configuring the dithering mode used when driving a flat panel with a GeForce 8 family or Quadro 4600/5600 or newer GPU. See the "Dithering Controls" in the Flat Panel page in nvidia-settings.
Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
GL_EXT_texture_integer
GL_ARB_stencil_two_side
GL_EXT_transform_feedback2
GL_NV_transform_feedback2
GL_NV_conditional_render
Added GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
GL_NV_point_sprite
GL_EXT_stencil_two_side
GL_EXT_point_parameters
GL_ARB_transpose_matrix
GL_EXT_framebuffer_blit
GL_EXT_framebuffer_multisample
GLX protocol for the following OpenGL extension is promoted from unofficial GLX ptotocol to ARB approved GLX protocol:
GL_EXT_geometry_shader4
GL_ARB_shader_objects
GL_ARB_vertex_shader
GL_ARB_fragment_shader
Added support for configuring individual displays as any eye in passive stereo mode "4" when using TwinView or SLI Mosaic through extensions to the MetaMode syntax.
Added ColorSpace and ColorRange features for HDMI. These give the ability to output YUV over HDMI and select full/reduced color range on RGB over HDMI. ColorSpace and ColorRange are X Configuration options and can be changed dynamically through nvidia-settings.

As always, downlaod links at the first page of this thread. 


Good luck!

---

### Post by Caironater on 2010-09-13
How do I uninstall a previous version from TTY?

---

### Post by Kosimo on 2010-09-14
> **Caironater said:**
> How do I uninstall a previous version from TTY?


Important note: In some instances, after a kernel upgrade you won't be able to load x.org. "sdennie" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look here

ps: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type:

> sudo sh ./Nxxx --uninstall
or

> sudo nvidia-uninstall

---

### Post by Caironater on 2010-09-14
And you can do this from any directory?

---

### Post by Linuxforall on 2010-09-14
> **Caironater said:**
> And you can do this from any directory?

Home is the easiest way as bash defaults to it.

---

### Post by toffuuu on 2010-09-16
i followed the instructions to the T, and yet it still says im running xserver..    here is the copy from the nvidia log thingy....

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Sep 16 01:12:15 2010
installer version: 256.53

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1230'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

now i did do the sudo /etc/init.d/gdm stop  and  it still gave me this error??   I really need some help here tho  so I hope someone here will help me figure this out...

---

### Post by alzie on 2010-09-17
Thanks Kosimo!!!

I did get an **"out of frequency error"** at reboot.

I used recovery mode to get to the console and manually reset my horizontal and vertical frequencies back to 30-70 (using nano) and now all is good.

Thanks again!

---

### Post by FUJIM0 on 2010-09-19
i'm running a GeForce FX 5500 and Ubuntu 10.04.1 any one forsee any issues with these installation instructions?


Fuji...

---

### Post by xenton on 2010-09-22
> **JPorter said:**
> I'm using 256.44 as well, I installed it by running System -> Administration -> Update Manager and clicking the Install Updates button.

It's in the Ubuntu X Updates PPA:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Thank you so much JPorter, adding the x Updates PPA took about seconds and I'm now on the latest driver for my graphics card.

I mean no disrespect to the OP but this method should be up on the first page as the 1st thing to try, it seems to get the latest driver for most people without the need for manual install.

---

### Post by Kosimo on 2010-09-24
> **xenton said:**
> Thank you so much JPorter, adding the x Updates PPA took about seconds and I'm now on the latest driver for my graphics card.

I mean no disrespect to the OP but this method should be up on the first page as the 1st thing to try, it seems to get the latest driver for most people without the need for manual install.

Following your suggestion, I've just added the info in the first page.

---

### Post by toffuuu on 2010-09-24
finally i got it too work like the way it says on the 1st post here, but after doing  this sudo /etc/init.d/gdm stop,  then the next step without a sudo reboot, it did not work so then i thought how bout rebooting it, so i did that, then I did the sudo sh ./NVIDIA_XXX.run    and it installed..   might vary between all of you,  but  just is a bit weird at times  lol  but it works for me now..  :guitar:

---

### Post by Kosimo on 2010-09-24
> **toffuuu said:**
> finally i got it too work like the way it says on the 1st post here, but after doing  this sudo /etc/init.d/gdm stop,  then the next step without a sudo reboot, it did not work so then i thought how bout rebooting it, so i did that, then I did the sudo sh ./NVIDIA_XXX.run    and it installed..   might vary between all of you,  but  just is a bit weird at times  lol  but it works for me now..  :guitar:

Welcome to the club then ;)

---

### Post by Aitaix on 2010-09-25
just wanted to thank Kosimo for finally!!!! helping me to get** any** version of Ubuntuto work with my crappy Dell Latitude E6510 display to work. 

Now for wireless. Grrr I don't like this laptop at all. but it was free so who am I to complain?

---

### Post by ze3rax on 2010-10-03
Hello Kosimo,

I've tried to install latest drivers as guided but when I type this

```
sudo /etc/init.d/gdm stop
```additional information is given where is explained that /etc/init.d/ was changed to the common "service gdm stop", that's why I'm not sure if this is being stopped. When I start the installation with sudo sh , in the new window Nouveau is being disabled by the installer (I confirmed to disable it) [ location: -> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf ]

Here the real problem is: in the process of installing it ends with the following error:

* The distribution-provided pre-install script failed *


I'm including the log file in case it's needed for resolving the issue.

[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct  4 02:03:36 2010
installer version: 260.19.04

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 260.19.04.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
ERROR: The Nouveau kernel driver is currently in use by your system.  This
       driver is incompatible with the NVIDIA driver, and must be disabled
       before proceeding.  Please consult the NVIDIA driver README and your
       Linux distribution's documentation for details on how to correctly
       disable the Nouveau kernel driver.
-> For some distributions, Nouveau can be disabled by adding a file in the modp
   robe configuration directory.  Would you like nvidia-installer to attempt to
   create this modprobe file for you? (Answer: Yes)
-> The modprobe configuration file to disable Nouveau,
   /etc/modprobe.d/nvidia-installer-disable-nouveau.conf, has been written. 
   For some distributions, this may be sufficient to disable Nouveau; other
   distributions may require modification of the initial ramdisk.  Please
   reboot your system and attempt NVIDIA driver installation again.  Note if
   you later wish to reenable Nouveau, you will need to delete the file
   /etc/modprobe.d/nvidia-installer-disable-nouveau.conf.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.[/HTML]

P.S. Ubuntu 10.04 and 256, 260 versions tried - same error

---

### Post by Linuxforall on 2010-10-03
> **ze3rax said:**
> Hello Kosimo,

I've tried to install latest drivers as guided but when I type this

```
sudo /etc/init.d/gdm stop
```additional information is given where is explained that /etc/init.d/ was changed to the common "service gdm stop", that's why I'm not sure if this is being stopped. When I start the installation with sudo sh , in the new window Nouveau is being disabled by the installer (I confirmed to disable it) [ location: -> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf ]

Here the real problem is: in the process of installing it ends with the following error:

* The distribution-provided pre-install script failed *


I'm including the log file in case it's needed for resolving the issue.

[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct  4 02:03:36 2010
installer version: 260.19.04

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 260.19.04.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
ERROR: The Nouveau kernel driver is currently in use by your system.  This
       driver is incompatible with the NVIDIA driver, and must be disabled
       before proceeding.  Please consult the NVIDIA driver README and your
       Linux distribution's documentation for details on how to correctly
       disable the Nouveau kernel driver.
-> For some distributions, Nouveau can be disabled by adding a file in the modp
   robe configuration directory.  Would you like nvidia-installer to attempt to
   create this modprobe file for you? (Answer: Yes)
-> The modprobe configuration file to disable Nouveau,
   /etc/modprobe.d/nvidia-installer-disable-nouveau.conf, has been written. 
   For some distributions, this may be sufficient to disable Nouveau; other
   distributions may require modification of the initial ramdisk.  Please
   reboot your system and attempt NVIDIA driver installation again.  Note if
   you later wish to reenable Nouveau, you will need to delete the file
   /etc/modprobe.d/nvidia-installer-disable-nouveau.conf.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.[/HTML]

P.S. Ubuntu 10.04 and 256, 260 versions tried - same error

Looks like you didn't do the blacklisting correct or remove nouveau driver, also did you install build-essential, new or first time users should try Ubuntu x-swat ppa which has latest drivers and automatically installs the without any hassle.

---

### Post by ze3rax on 2010-10-04
Hello,

Don't know what build-essential is but will read about it when I got back from work.

---

### Post by ze3rax on 2010-10-04
Allright, here what I found and what I tried:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
 sudo aptitude update
 sudo aptitude install 260.19.06-0ubuntu1~xup1~lucid


```Nothing happens after that. Any advices ?

---

### Post by beew on 2010-10-04
You have to run ```
sudo nvidia-xconfig
``` in the terminal and restart the computer.

---

### Post by ze3rax on 2010-10-04
Strange but nothing happens:

"sudo: nvidia-xconfig: command not found"

---

### Post by beew on 2010-10-04
Ok, go to System > Administration and you should find the icon "Nvidia X server Setting". Click it and do what it tells you to do.

---

### Post by ze3rax on 2010-10-04
Obviously I've missed something because there's no such thing ( I've seen the icon from screenshots over the net only :) )

---

### Post by realzippy on 2010-10-04
After adding xswat you only made an apt update,you need also a upgrade.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```
not sure if you need also:
```
sudo ldconfig
```

...then the driver available in System/Administration/Hardwaredrivers (nvidia current) should be the one from xswat.

---

### Post by beew on 2010-10-04
I am not sure which version your Nvidia card is. Unless I am mistaken I think packages in the X-Swat ppa (and the  Vdpau ppa) only have drivers for newer Nvidia cards so you may have got the wrong drivers. Go to System > Hardware Drivers and run it and install the drivers from there, also check the driver version. You may want to remove whatever you have installed from the PPAs if the version don't match.

If the installation is successful you only need to reboot and it should work.

---

### Post by ze3rax on 2010-10-04
Thank you realzippy and beew. Drivers installed ~

---

### Post by milton888 on 2010-10-12
Just would like to say thank you for the help... I finally managed to install the latest nvidia graphic driver for my 8600GT.

:D

---

### Post by realzippy on 2010-10-12
@milton

Welcome to the forum!

---

### Post by uzzo2 on 2010-10-12
I tried the install from the OP and got this error.
The Nouveau kernel driver is currently in use by your system. This driver is incompatible with the NVIDIA driver and must be disabled before proceeding. Please consult the NVIDIA driver README and your linux distributions documentation for details on how to correctly disable the Nouveau kernel driver.

---

### Post by realzippy on 2010-10-13
*Please consult the NVIDIA driver README and your linux distributions documentation for details on how to correctly disable the Nouveau kernel drive*

...inside the README of your driver are [instructions how to disable nouveau]("http://de.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/commonproblems.html#nouveau").

Why not installing via jockey (post #1401 e.g.)?
Manual install has to be done again after every kernel update.

---

### Post by uzzo2 on 2010-10-13
> **realzippy said:**
> *Please consult the NVIDIA driver README and your linux distributions documentation for details on how to correctly disable the Nouveau kernel drive*

...inside the README of your driver are [instructions how to disable nouveau]("http://de.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/commonproblems.html#nouveau").

Why not installing via jockey (post #1401 e.g.)?
Manual install has to be done again after every kernel update.
I wish I'd read those instructions instead of taking it upon myself to go into Synaptec and uninstall nouveau. That was a bad idea, it pretty much wiped off everything. So I am starting all over again with a fresh install of Ubuntu 10.04 instead of Mint 9. Maybe I won't have these graphics issues with the fresh install.:-(

---

### Post by Kosimo on 2010-10-13
> **uzzo2 said:**
> I wish I'd read those instructions instead of taking it upon myself to go into Synaptec and uninstall nouveau. That was a bad idea, it pretty much wiped off everything. So I am starting all over again with a fresh install of Ubuntu 10.04 instead of Mint 9. Maybe I won't have these graphics issues with the fresh install.:-(

I strongly recommend you to try the new 10.10, which by the way comes by default with the latest stable nVidia driver.

---

### Post by uzzo2 on 2010-10-13
> **Kosimo said:**
> I strongly recommend you to try the new 10.10, which by the way comes by default with the latest stable nVidia driver.
Can I do that without losing everything again? I was up until about 2AM downloading drivers for my printer, etc... Back at it again now trying to get all of my software packages reinstalled. I know that when I switched from 8.04 to Mint 9 the same thing happened, I had to start all over again. It's a pain in the ****, but I guess it's good experience.

---

### Post by ratcheer on 2010-10-13
> **uzzo2 said:**
> Can I do that without losing everything again? I was up until about 2AM downloading drivers for my printer, etc... Back at it again now trying to get all of my software packages reinstalled. I know that when I switched from 8.04 to Mint 9 the same thing happened, I had to start all over again. It's a pain in the ****, but I guess it's good experience.

Since you apparently just installed 10.04, yes, you can just upgrade it to 10.10 without losing anything. I also recommend 10.10, it is the best OS i've ever used on a home PC.

Tim

---

### Post by uzzo2 on 2010-10-13
> **ratcheer said:**
> Since you apparently just installed 10.04, yes, you can just upgrade it to 10.10 without losing anything. I also recommend 10.10, it is the best OS i've ever used on a home PC.

Tim
Thanks Tim, What do I need to do? Just download and burn it to a CD and just stick it in one of my optical drives and it'll take care of itself?

---

### Post by ratcheer on 2010-10-13
> **uzzo2 said:**
> Thanks Tim, What do I need to do? Just download and burn it to a CD and just stick it in one of my optical drives and it'll take care of itself?

You don't even need to do that. Just run "sudo update-manager -d".

Tim

---

### Post by gatorbrit on 2010-10-13
Hi I wanted to add a comment on this thread.   I haven't followed the manual install route yet, although I might try it tomorrow.  

There was talk a little while back about the fact that most users shouldn't need to manually install these drivers.  I don't know about this but I bet my case is similar to many.

I am running an older gforce card that requires the nvidia-96 driver.  I also run dual monitors.  When I installed 10.04, clicking on the hardware driver item in the admin menu prompted me to install the right nvidia driver and all was well.

But now I tried upgrading to 10.10.  First of all the wrong driver is loaded - I can tell this because xorg uses about 99% of my processor most of the time.  I try using the driver menu item (which has changed names) and also I try nvidia-xconfig etc.  I basically go round in circles.

Now I know this is not a specific question.  My point is that even in 10.10, things that used to work don't work out of the box.  Its frustrating, but I think this motivates the need for these manual work arounds.

Incidentally, prior to 10.04 I used to use Envy to get my drivers to work.  This is something that I battle at every upgrade, and frankly makes me think I should just keep this box running 10.04.

---

### Post by 1Dagars1 on 2010-10-14
First i wanted to thank everyone for their posts and contributions to this thread. I am having some trouble with the driver install.

I followed the instructions. I am doing this in Ubuntu 10.10. I downloaded the latest driver for my graphics card (Nvidia GeForce 310m on a Sony Vaio VPCCW21FX). Next i Ctrl+Alt+F1, cd Desktop, turned off xorg and ran the installer.

However the procedure did not work. I received the following notices. I am following this procedure in 10.10.

"Rather than invoking init scripts through /etc/init.d, use the service (8 ) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the stop(8 ) utility, e.g. stop gpm"

After running "sudo sh ./N... <tab>" I received the following message:

"error in check sums 1928700180 3543351320"

I am not sure where i went wrong but I would appreciate any help that can be provided. Basically i was running 10.04 with no problem. I was not able to utilize the higher graphics utilities but at least i did not have to use an external monitor which is the only way i can see or do anything at the moment. And as this is a notebook it would be nice to not be tethered to an external monitor.

Thank you very much.

---

### Post by uzzo2 on 2010-10-14
I updated to 10.10 last night, I didn't use it any after the upgrade. My wife has and reported firefox crashes. I haven't experienced it yet, I guess when I do I'll post a thread about that.

---

### Post by typos1 on 2010-10-15
Just put in a graphics card and the screen is covered in masses of commas, so many that I can barley read it, when its on the boot menu, then nice neat little rows of commas when on the booting page (which is usually a black screen and a flashing underscore), then the 10.10 purple back ground appears for a fraction of a second, then "no signal" from the monitor and the picture goes. 

I m trying to work out whether the card is broken or whether I need the latest drivers, thing is I was expecting to add the card-be able to boot and THEN install the drivers.
Anyone got any ideas?

---

### Post by cariboo on 2010-10-15
You more than likely have a defective video card, as the drivers aren't loaded until after you select an os to boot into.

---

### Post by FokkerCharlie on 2010-10-17
Hmmmmmm.....

I have run into a bit of an issue here, perhaps someone could help?

I recently upgraded to Maverick, and installed the 260 driver via jockey, which was all fine.  Unfortunately, I have been seeing some problems after resuming from suspend, so I decided to try reverting to the 258 driver which had worked well for me on Lucid.  This involved inhibiting the nouveau driver via GRUB.

Unfortunately, the different driver did not solve the issues, so I wanted to revert back to 260, mainly to avoid issues when installing new kernel headers etc.

So, I uninstalled the driver from the command line and rebooted.  Sadly, I now have the following situation:

I can leave the GRUB setup so that Nouveau is inhibited, which takes me to a terminal login.  It seems that gdm and/or X is not getting loaded.  If I allow Nouvea to load, I see a nice splash, which then freezes at about the time that I expect to see the login screen.  I can press the power button, which works, but that's it!

From a command line, I can sudo apt-get install nvidia-current, which seems to work OK, but on reboot doesn't seem to have had any effect.

Any suggestions on how to get back to being able to install the driver via jockey / synaptic?

Thanks in advance!
Charlie

---

### Post by Caironater on 2010-10-21
I get an error when I try to install my correct driver which says that the driver does not match my kernel build or something.
Does anyone know how I could fix this problem?
The installation log is here [http://paste.ubuntu.com/517286/](http://paste.ubuntu.com/517286/)
I am trying to install the 96.43.18 driver for a GeForce4 TI 4400 graphics card.

---

### Post by fillintheblanks on 2010-10-23
Finally I managed to enable fastwrite in Ubuntu 10.10 Nvidia 260.19.06

I make file named 'nvidia' in /etc/modprobe.d with the following :

> options nvidia-current NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

then reboot and voila :

> $ cat /proc/driver/nvidia/agp/status

Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Enabled
SBA: 		 Enabled


---

### Post by sir4taye on 2010-10-24
> **Kosimo said:**
> I strongly recommend you to try the new 10.10, which by the way comes by default with the latest stable nVidia driver.

My 10.10 comes with nouveau. And nvidia is being problematic to setup on my geforce 8200.

---

### Post by cocopuffz on 2010-10-24
Did you figure it out? Instead of killing gdm the old way, you can go "sudo service gdm stop"

cd to the files directory, chmod +x Nvidia-blahlah.run and execute it "sudo sh Nvidia-blahbalh.run"

If that doesn't work, you may need to drop to run level 1, type "init 1" , then go up to run level 3 , type "telinit 3"

and then try to run the installer again.

---

### Post by claven123 on 2010-10-24
I followed the instructions in post #1.

I attempted to install, however I got the kernel does not match error...  ie nouveau or device mismatch..

So, I stopped nouveau with this command.
Well, it didn't work.  I now have  a  blank black screen.  I will attempt to reinstall nouveau.  I might have to go back to windows... I can't get the darn drivers to work.  Quite frustrated with this!

sudo apt-get --purge remove xserver-xorg-video-nouveau

---

### Post by claven123 on 2010-10-24
Any ideas on how I get nouveau drivers back?  With those at least I have something.

Thanks

---

### Post by Hells_Dark on 2010-11-17
Hi,
I have a nvidia driver 190.53 running.
Is it worth the upgrade to a newer driver ?
Have the nvidia driver performance been improved recently ?

---

### Post by HandeH on 2010-12-11
How to get other non-free/restricted drivers back into use and into the list of Jockey after completed uninstallation of manually installed driver? 

[https://help.ubuntu.com/community/NvidiaManual#Disable%20Conflicting%20Software](https://help.ubuntu.com/community/NvidiaManual#Disable%20Conflicting%20Software)
There is a warning but no instructions on how to deal with the situation. 

I have linux-firmware-nonfree installed, but it is not shown in Jockey and not working.

---

### Post by w_barnes on 2010-12-12
> **Kosimo said:**
> Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_**


Please explain further. I'm stuck with 640x480 resolution and can't fix. I've gone to System>Preferences>Monitors and apparently this is the highest resolution available.

I have a GeForce FX 5200 video card and I think a NVidia driver is installed but I have no Idea what version.

Please explain how I can identify my driver (regardless of what it is) including version and release date and name and location of all driver related files using the terminal, not the GUI, and how I can restore Ubuntu back to the default driver. From there I'll try following the instructions provided to get my NVidia card working properly.

Thanks!

---

### Post by ratcheer on 2010-12-12
> **w_barnes said:**
> 

Please explain how I can identify my driver (regardless of what it is) including version and release date and name and location of all driver related files using the terminal, not the GUI, and how I can restore Ubuntu back to the default driver. From there I'll try following the instructions provided to get my NVidia card working properly.

Thanks!

View file  /var/log/Xorg.0.log. Search for string "nvidia". You should find something like the following, if you are running the nvidia driver:

```
[    22.919] (II) LoadModule: "nvidia"
[    22.919] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    23.220] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.228]    compiled for 4.0.2, module version = 1.0.0
[    23.228]    Module class: X.Org Video Driver
[    23.229] (II) NVIDIA dlloader X Driver  260.19.26  Sun Nov 28 22:39:42 PST 2010
[    23.229] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

```

If you are not running an nvidia driver, search repeatedly for "LoadModule:" until you find the one that shows what video driver you are using.

Tim

---

### Post by tzi0 on 2010-12-16
Hi guys. Can anybody explain me the following one: after ive installed a latest stable driver from nvidia, is nouveau still in my system or its  not? And if it is, so, how and where it blocked? Can I safely remove it and how?  Thanks!
ps i used PPA to install the driver

---

### Post by ratcheer on 2010-12-16
> **tzi0 said:**
> Hi guys. Can anybody explain me the following one: after ive installed a latest stable driver from nvidia, is nouveau still in my system or its  not? And if it is, so, how and where it blocked? Can I safely remove it and how?  Thanks!
ps i used PPA to install the driver

I wouldn't mess with it.

Tim

---

### Post by Chris Psycho on 2011-02-02
Hey, I'm pretty new to ubuntu so...

I tried ubuntu but now I'm on Linux Mint (which is meant to be based off ubuntu?), anyway.

I downloaded the lastest Nvidia Drivers for my 7900gt (had a 8500gt maybe a week ago), so I tried running gdm stop service and running the run file, but the whole process goes like this:


'The distribution-provided pre-install script failed. Continue install anyway?'
Yes
'Error: The nouveau kernal driver is currently in use by your system. This driver is incompatible with the Nvidia driver and must be disabled beforfe preceeding. Please consult the nividia diver readme and your linux distribution's documentatin for details on how to correctly disable the nouvuea kernal driver. 

For some distro, nouvuea can be disabled by adding a file in the modprobe configuration directory. Would you like the nvidia-installer to attempt to create this modprobe file for you?

Yes.

After this it pretty much 'crashed'.

I restarted, tried again but said something along the lines of the script failing and can't continue?.


Any idea haha?... Have a small bandwidth contract so yeah that's the reason for installing it like so.  And think it would be quite benaficial to myself to learn how so...

Thanks for reading.

---

### Post by Tweak42 on 2011-02-02
Chris, not to turn you away, but have you searched the Linux Mint forums?  I found this thread there that sounds similar to the problem you are having.
[http://forums.linuxmint.com/viewtopic.php?f=59&t=58990](http://forums.linuxmint.com/viewtopic.php?f=59&t=58990)

It would help if you can give a clear description of the script error you are getting now.

---

### Post by rotary12 on 2011-02-02
> **Chris Psycho said:**
> Hey, I'm pretty new to ubuntu so...

I tried ubuntu but now I'm on Linux Mint (which is meant to be based off ubuntu?), anyway.

I downloaded the lastest Nvidia Drivers for my 7900gt (had a 8500gt maybe a week ago), so I tried running gdm stop service and running the run file, but the whole process goes like this:


'The distribution-provided pre-install script failed. Continue install anyway?'
Yes
'Error: The nouveau kernal driver is currently in use by your system. This driver is incompatible with the Nvidia driver and must be disabled beforfe preceeding. Please consult the nividia diver readme and your linux distribution's documentatin for details on how to correctly disable the nouvuea kernal driver. 

For some distro, nouvuea can be disabled by adding a file in the modprobe configuration directory. Would you like the nvidia-installer to attempt to create this modprobe file for you?

Yes.

After this it pretty much 'crashed'.

I restarted, tried again but said something along the lines of the script failing and can't continue?.


Any idea haha?... Have a small bandwidth contract so yeah that's the reason for installing it like so.  And think it would be quite benaficial to myself to learn how so...

Thanks for reading.

i have Nvidia driver 270.18.i use ubuntu fist go to system administration and remove the driver reboot then
use ubuntu tweak,go to their web and download the .deb file,install it (go to applications - system tools) select source center and look for X UPDATES (its at the end) select it and follow instructions, you should get the latest driver.

---

### Post by kitcat on 2011-02-09
Dear Ubuntu experts,
 

 As an absolute newcomer to Linux and Ubuntu, much of this thread makes little sense to me, but I hope someone can help with the following question.
 

 Yesterday, I completed my first successful installation of Ubuntu 10.10 after several false starts.  Everything seemed OK &#8211; I even received notification that my Video driver was incorrect and it gave a suggested driver which I duly installed.  I now have an &#8220;NVIDIA X Server Settings&#8221; option under my System &#8211; Admin menu and this claims I have driver 260.19.06 installed.
 

 However,  the maximum screen resolution that works for me is 1024*768 and on many applications any font or font size I try comes out rather blurred and hard on the eyes &#8211;  even with windows full sized it is difficult to read some web sites .    In comparison, windows XP with its default drivers can drive my card/monitor at a resolution of 1280*1024 with crystal clear fonts and room to open several windows on the same screen.
 

 My questions are :  
 

 Do I have the correct driver installed?
 Are the symptoms described typical?
 Is there anything I can do to improve my display &#8211; and if so, how, bearing in mind I am a complete novice?
 

 Thanks very much for anyone who can help,

---

### Post by Tweak42 on 2011-02-10
Kitcat, it sounds like the drivers installed ok, but the monitor was not detected correctly, hence the resolution is distorted.  In the Nvidia X Server Settings tool, have you tried running "Detect Displays"?  What model monitor is listed on the Display tab?  Are you using a vga or dvi cable to connect your monitor to your computer?

You are running the latest release driver, however there is a beta 270.18.  It's mainly to support the latest video cards and not likely to fix your current predicament with your older card.  If possible use a dvi cable because the resolution detection should detect without any trouble, where as vga can go funny sometimes.

The easiest way to update and stay current with drivers is to add the X Updates repository to your Software Sources.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

First timer users will usually get tripped up getting the drivers installed, and no issues with monitor detection, so you are already past the 1st hurtle.  Hang in there alittle further and you should have a complete working system. :popcorn:

---

### Post by mockingbird on 2011-02-10
I am having a problem installing this driver in Debian Squeeze.  I managed to get the repository working and hacked a little to get all the dependencies in Debian, but the installation fails witht he part where it compiles the modules.

I went to var/lib/dkms/nvidia-current/270.18/build to try and compile it manually.

So:
"sudo make IGNORE_CC_MISMATCH=1 module"

But I get an error that "scripts/basic/Makefile: No such file or directory".

That file shouldn't be there, it's in the root of linux-headers-2.6.32-5-common but not in the /scripts/basic folder.  I tried making a symlink to it but that sent the compilation in some sort of infinite loop.

Anyone have any idea?

If you want, I can display the entire error, but I'm having trouble with my tee syntax trying to output the operation to a text file.  I've tried "sudo make IGNORE_CC_MISMATCH=1 module && sudo tee output.txt, but the output is not verbose, it only shows me the commands the makefile is trying.

---

### Post by kitcat on 2011-02-11
Hi Tweak42.
Thank you for your very helpful reply.
Of course, you are right.  I had been using a VGA cable because my DVI cable did not seem to work - so the monitor was only being detected as "CRT-1".
I have now tested the cable out by connecting to the HDMI input on the TV - and that works fine so I have to conclude that my monitor itself is at fault.
Still very strange that XP works fine through the VGA cable but never mind.
Thank you once again.

---

### Post by Statik on 2011-02-11
I was looking to enable OpenCL with my GeForce9100M G videocard. I have the latest driver from Ubuntu installed, which is 270.18, It does not seem to have OpenCL with it. I tried to install the latest nvidia driver, from their site, but it is listed as: 260.19.36, which seems like it should be older.

When I tried to install the drivers using this guide, I found that the neuveau drivers were in the way. While I am still looking through this thread for instructions on removing neauveau, can anyone tell me if there is an easier way to enable OpenCL?

Thanks!

Statik

---

### Post by ratcheer on 2011-02-11
270.18 should support OpenCL. I was just looking at the nVidia driver features this morning and I remember seeing it.

Tim

---

### Post by psnegi on 2011-02-12
In Ubuntu 10.1 it automatically asked to download the driver for nvidia card. Min is 9600 gt. It downloaded and installed automatically after I clicked yes for installation.

---

### Post by mockingbird on 2011-02-13
> **mockingbird said:**
> I am having a problem installing this driver in Debian Squeeze.  I managed to get the repository working and hacked a little to get all the dependencies in Debian, but the installation fails witht he part where it compiles the modules.

I went to var/lib/dkms/nvidia-current/270.18/build to try and compile it manually.

So:
"sudo make IGNORE_CC_MISMATCH=1 module"

But I get an error that "scripts/basic/Makefile: No such file or directory".

That file shouldn't be there, it's in the root of linux-headers-2.6.32-5-common but not in the /scripts/basic folder.  I tried making a symlink to it but that sent the compilation in some sort of infinite loop.

Anyone have any idea?

If you want, I can display the entire error, but I'm having trouble with my tee syntax trying to output the operation to a text file.  I've tried "sudo make IGNORE_CC_MISMATCH=1 module && sudo tee output.txt, but the output is not verbose, it only shows me the commands the makefile is trying.

Oddly, when I run make module from var/lib/dkms/nvidia-current/270.18/build as root, as opposed to running "sudo" it works great and I can proceed to run make install.  No dreaded "Makefile.build:44" error.

Rebooted, and the driver is there, works great AFAIK.  So what would cause this behavior in Debian Squeeze with kernel-headers-2.6.32-5-common?  There have been several bug reports about it but some British bufoon at Debian keeps closing the bugs without addressing them.

---

### Post by omicron37 on 2012-07-16
installed ubuntu 12.04, I also have 3 570 gtx nvidia graphic cards (sli) which nvidia driver will I need for my system to recognize all 3 cards

---

### Post by jaithehulk on 2012-09-10
I have a Nvidia geforce 610m(optimus)on my laptop and I have upgraded to kernel 3.5. How do I make sure that my graphics card is detected and is being used by the OS?

---

### Post by Gemnoc on 2012-09-10
If you have Nvidia Optimus hybrid graphics, I think you should look into Bumblebee which allows graphics switching on Linux.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Do a search on the forums here you might find existing topics.

Or the Ubuntu wiki: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

