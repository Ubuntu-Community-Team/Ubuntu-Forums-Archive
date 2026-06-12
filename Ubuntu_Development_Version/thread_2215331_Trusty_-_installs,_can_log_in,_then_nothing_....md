---
title: "Trusty - installs, can log in, then nothing ..."
date: 2014-04-06
forum: Ubuntu Development Version
---

### Post by cwmoser on 2014-04-06
The last few versions of Trusty just do not work with my configuration.
It installs, I can log in, then the desktop is blank.

I installed Trusty by not selecting to install updates during the installation process.
Will though retry doing that and post back here.

I selected "Something Else" and installed root to /dev/sda1, and home to /dev/sdb1.
Checked to format both partitions as EXT4.

Earlier when I installed Trusty Alpha 1, it worked with only one exception - that there was an issue
with workspaces on a dual monitor configuration.

I am getting concerned that the released Trusty will not work with my hardware configuration:
- AMD Athlon 64 6400+
- 8 GB RAM
- nVidia GeForce 7300 - driving 2 monitors
- Solid state drive on /dev/sda
- Sata drives on /dev/sdb, sdc, sdd

Carl

---

### Post by buzzingrobot on 2014-04-06
Regular updates are essential for alpha/beta releases.  No updates, no fixes.  

Do a "sudo apt-get update", then "sudo apt-get upgrade" (and "sudo apt-get dist-upgrade" if you see anything "held back", as you likely will, including kernels.  Try that before installing again.

---

### Post by grahammechanical on 2014-04-06
When you say "the desktop is blank" do you mean a black screen or just the wallpaper without the top panel or launcher? If we install with the "Install third party software" box ticked then we get a proprietary video driver. That can cause problems.

If you get a wallpaper then right click the wallpaper and select Change Desktop Background. That will open System Settings. From there we can get to Software and Updates>Additional Drivers tab and experiment with drivers.

If you cannot do that and Ctrl+Alt+T does not bring up a terminal then try Ctrl+Alt+F2. That should bring up a Linux command line. Log in and run

```
dconf reset -f /org/compiz
setsid unity
```

The first command resets Compiz and the second resets Unity. Then Ctrl+Alt+F7 to switch back to the desktop.

Regards.

---

### Post by cwmoser on 2014-04-07
OK, I had to enter Recovery mode and run Fail Safe Graphics to get Trusty to allow me to log in.
Then dropped to the command prompt and ran the 3 apt-get commands.

I can log in and get Unity in Fail Safe Graphics - but still cannot do a normal login.
Could it be something to do with the nVidia driver that Trusty is installing????

At one point I did see this message ...  
[DRM] GPU lockup - switching to software fbcon
... but still the desktop was unresponsive.

The mouse cursor would move initially then freeze.  No icons showing.
The background color was light brown.

Carl

---

### Post by cwmoser on 2014-04-07
Tried the dconf reset -f /org/compiz and the setsid unity commands -- still get a frozen desktop after logging in.

Carl

---

### Post by zika on 2014-04-07
As I've mentioned numerous times, did You try using ```
radeon.dpm=0
``` as kernel-boot-line option?

---

### Post by cwmoser on 2014-04-07
Tried adding that Kernel-boot-line option and no help.
Hope I did it correctly ... selected e to edit options, went down to the linux line and
appended radeon.dpm=0 then F10.  On next boot the edit was not there.
Didn't see a save command.

In any case, I have an nVidia card - not an ATI Radeon card.

Carl

---

### Post by zika on 2014-04-07
> **cwmoser said:**
> In any case, I have an nVidia card - not an ATI Radeon card.
CarlMea culpa, I've seen AMD in Your first message, not recognized it meant processor not a graphic card... Being old and do reading in a hurry is not a good combination... ;)

---

### Post by ventrical on 2014-04-07
> **cwmoser said:**
> The last few versions of Trusty just do not work with my configuration.
It installs, I can log in, then the desktop is blank.

I installed Trusty by not selecting to install updates during the installation process.
Will though retry doing that and post back here.

I selected "Something Else" and installed root to /dev/sda1, and home to /dev/sdb1.
Checked to format both partitions as EXT4.

Earlier when I installed Trusty Alpha 1, it worked with only one exception - that there was an issue
with workspaces on a dual monitor configuration.

I am getting concerned that the released Trusty will not work with my hardware configuration:
- AMD Athlon 64 6400+
- 8 GB RAM
- nVidia GeForce 7300 - driving 2 monitors
- Solid state drive on /dev/sda
- Sata drives on /dev/sdb, sdc, sdd

Carl

[s] I just updated my Trusty overclocking box with GeForce 7300 GS (128MB) and it killed the install basically. Those cards (I assume) are obsoleted now most likley because of Mir and Unity.  Unity needs more RAM than what the 7300 has to offer (elst it will default to llvmpipe also). However, I can put in my PCIe GeForce 210/218 and it will work no prob. [/s]

Regards..

edit:

btw ... what worked for  while is that I installed the lubuntu-alternate iso and then downloaded ubuntu-desktop on top of that. It worked great for a long time until todays update and now it defaults into llvmpipe (really crappy graphics). [s] This is usally an indication that the adapter card is no longer being supported by the drivers, however, I have nVidia Control Center installed so perhaps nouveau might work.[/s]

---

### Post by Castea_Min on 2014-04-07
@[COLOR=#000000][B][U]cwmoser
[/U][/B][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I also have the similar problem, cannot login to ubuntu 14.04 after upgrade from 13.10, but now I have succeed to login ^_^. Check my answer at askubuntu below. hope it will help u.[/FONT][/COLOR][COLOR=#000000]****[/COLOR][http://askubuntu.com/questions/423725/ubuntu-12-04-32bit-cant-login/439472#439472](http://askubuntu.com/questions/423725/ubuntu-12-04-32bit-cant-login/439472#439472)

---

### Post by cwmoser on 2014-04-07
> **Castea_Min said:**
> @[COLOR=#000000][B][U]cwmoser
[/U][/B][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I also have the similar problem, cannot login to ubuntu 14.04 after upgrade from 13.10, but now I have succeed to login ^_^. Check my answer at askubuntu below. hope it will help u.[/FONT][/COLOR][COLOR=#000000]****[/COLOR][http://askubuntu.com/questions/423725/ubuntu-12-04-32bit-cant-login/439472#439472](http://askubuntu.com/questions/423725/ubuntu-12-04-32bit-cant-login/439472#439472)

Thanks.  I tried editing /var/lib/Accounts/Service/users/<username>
changing XSession=gnome

That change kept the desktop from freezing ... but could not do anything as
there was no menus or icons.  In addition, the mouse cursor seemed kinda sluggish.

Carl

---

### Post by cwmoser on 2014-04-07
Is Trusty trying to tell me that Ubuntu does not want to support my hardware configuration anymore?

Ubuntu 12.04 runs just fine.

Carl

---

### Post by mc4man on 2014-04-08
> **cwmoser said:**
> Is Trusty trying to tell me that Ubuntu does not want to support my hardware configuration anymore?

maybe ask it - 
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by cwmoser on 2014-04-08
> **mc4man said:**
> maybe ask it - 
```
/usr/lib/nux/unity_support_test -p
```


I get a passing grade that it is still supported by Ubuntu:

```

$ ./unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 LE/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

---

### Post by ventrical on 2014-04-08
> **cwmoser said:**
> Is Trusty trying to tell me that Ubuntu does not want to support my hardware configuration anymore?

Ubuntu 12.04 runs just fine.

Carl

On the machine I had mentioned with  the above mentioned nVIDIA graphics adapter I decided to drop down to:

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-8-generic #27-Ubuntu SMP Fri Feb 7 01:59:38 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 

```

and it works just great. I have all desktops back and nVidia x-server Settings is working again with no llvmpipe.

[s] .. so it appears that the kernel update (3.13.0-23) threw it's pointers to llvmpipe and knocked the network out. It goes to show how a kernel upgrade can make a system appear to be borked is some fashion or another.[/s]

```
ventrical@ventrical-Asus-Overclock:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 GS/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.117

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
ventrical@ventrical-Asus-Overclock:~$ 

```


Regards..

---

### Post by ventrical on 2014-04-08
> **cwmoser said:**
> I get a passing grade that it is still supported by Ubuntu:

```

$ ./unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 LE/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```


Just noticed that I have version 304.117. Wonder if that makes a difference ?

---

### Post by ventrical on 2014-04-08
> **ventrical said:**
> On the machine I had mentioned with  the above mentioned nVIDIA graphics adapter I decided to drop down to:

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-8-generic #27-Ubuntu SMP Fri Feb 7 01:59:38 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 

```

and it works just great. I have all desktops back and nVidia x-server Settings is working again with no llvmpipe.

.. so it appears that the kernel update (3.13.0-23) threw it's pointers to llvmpipe and knocked the network out. It goes to show how a kernel upgrade can make a system appear to be borked is some fashion or another.

```
ventrical@ventrical-Asus-Overclock:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 GS/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.117

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
ventrical@ventrical-Asus-Overclock:~$ 

```


Regards..

as per the above: I was able to use synaptic and reload/apply and somehow it re-installed the kernels correctly and now I have all the ubuntu desktop working with no llvmpipe.

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-23-generic #45-Ubuntu SMP Fri Apr 4 07:01:54 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 


```

---

### Post by cwmoser on 2014-04-10
I THINK I FIGURED IT OUT!!

Downloaded the 10April2014 beta of Trusty and like before desktop froze.
Reset my PC and selected advanced options from Grub menu and entered Recovery.
In Recovery I selected Fail Safe Graphics and logged in to to Trusty desktop.

Then I dropped to command prompt (Ctrl+Alt+T) and issued this command:
**sudo dpkg -l nvidia***
and noted that only one nvidia record.

So, I then issued these commands:
[B]sudo apt-get purge nvidia*
sudo apt-get install nvidia-current[/B]

Restarted PC and now I can log in to Trusty with full resolution and no freeze.

Carl

---

