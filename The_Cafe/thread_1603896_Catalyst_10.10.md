---
title: "Catalyst 10.10"
date: 2010-10-23
forum: The Cafe
---

### Post by sandyd on 2010-10-23
Is out.
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Hopefully this fixes the random lagging problems.....

---

### Post by Oxwivi on 2010-10-23
Wow, with Ubuntu 10.10, coincidence?

---

### Post by Cam! on 2010-10-23
I can't install this! I get this error message whenever I run it:

[I]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/I]

I set the encoding to UTF-8, and I still get the same error.

---

### Post by alexandari on 2010-10-23
I feel like a boss with this GUI installer

---

### Post by sandyd on 2010-10-23
> **Cam! said:**
> I can't install this! I get this error message whenever I run it:

[I]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/I]

I set the encoding to UTF-8, and I still get the same error.

your supposed to run it in the terminal
i,e,
```

chmod 777 ati*run
sudo ./ati*run
```

---

### Post by Cam! on 2010-10-23
I'm an immense noob at chmod and the terminal. I have the file in my downloads folder. What do I type? :P

---

### Post by alexandari on 2010-10-23
This driver is absolute ****.

---

### Post by Cam! on 2010-10-23
Still, it's better than what I have now. How do I CHMOD to my Downloads folder in the terminal?

---

### Post by sandyd on 2010-10-23
> **alexandari said:**
> This driver is absolute ****.

^^
It stopped the window lagging though, although there IS still a lot of performance problems.

---

### Post by sandyd on 2010-10-23
> **Cam! said:**
> Still, it's better than what I have now. How do I CHMOD to my Downloads folder in the terminal?

switch to a VT (alt+f1)

```

sudo killall kdm
sudo killall gdm
sudo killall X
cd Downloads
chmod 777 ati*run
./ati*run

```

---

### Post by Cam! on 2010-10-23
After I install it, what do I do? It installs an extra ATI Catalyst in addition to the one when I enabled my previous driver by default. Do I disable the driver and re-enable it?

---

### Post by doorknob60 on 2010-10-23
> **Oxwivi said:**
> Wow, with Ubuntu 10.10, coincidence?
They use a similar version numbering system to Ubuntu :P First number is the year, second number is the number of the release of the driver in that year (this is the 10th driver this year. They try to release one once every month, so the second number usually matches the month too).

---

### Post by alexandari on 2010-10-23
I am having huge problems now after I installed it,and I cant revert back to the default driver...

---

### Post by bgilbert on 2010-10-23
Could any of you guys elaborate on your experience with this driver installed? I've got an hd 5730 in my laptop and am experiencing a fair amount of screen tearing and lag with the default driver shipped with Ubuntu 10.10.

I'm trying to evaluate the risk of installing this driver, as I'm a bit nervous about installing it after some of these posts.

Thanks in advance,
Bryan

---

### Post by sandyd on 2010-10-23
> **alexandari said:**
> I am having huge problems now after I installed it,and I cant revert back to the default driver...

```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

```

---

### Post by Dustin2128 on 2010-10-23
here's a 25$ solution for PCIe users:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187108](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187108)
here's a 40$ higher end solution:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814134112](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134112)
here's a 40$ solution for those of you still clinging to your agp cards and steam powered desktop fans:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133328](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133328)

I had an ATI/AMD card and trust me, nvidia's worth it.

---

### Post by bgilbert on 2010-10-23
FYI, for anyone interested. I updated my drivers to the ATI release of catalyst 10.10 and have seen significant improvements with no regressions after the update.

I installed these updates by using the following command:

```

chmod +x ati-driver-installer-10-10-x86.x86_64.run
./ati-driver-installer-10-10-x86.x86_64.run --buildpkg

```

This creates three different deb's which I each installed using the software center. Again, I've had no issues thus far, only improvements...and I figure at worst I can revert these updated packages back to the defaults with 10.10 using synaptic if needed.

Hope this helps somebody.

---

### Post by alexandari on 2010-10-24
> **sandyd said:**
> ```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

```


thanks a lot dude :) thing is,I did those things and still it wasnt alright...but I got it fixed,long and kinda random story...yes it involves the commands on the top xD

---

### Post by sandyd on 2010-10-24
[s]note: don't enable vsync if your using VLC.
enabling it causes heavy lag in video ](*,)](*,)

and for some reason, its only in vlc.[/s]
nvm.
after some tweaks to xorg.conf, its working nicely

---

### Post by wirespot on 2010-10-24
Can you post your xorg.org please? It might help others too. I'm particularly loath to "tweak" it. :(

---

### Post by wirespot on 2010-10-25
Finally, got to try this driver. I think it's this one, I installed from Ubuntu's "Hardware Drivers", it has version 8.783 which is the same as the driver downloaded from AMD.

Indeed, the vsync issues are mostly fixed. No longer get any major tearing of the desktop like before. Flash, movies, Compiz, games all seem to work fine.

There are some minor issues still there though, you get corrupted bits of screen here and there, especially in scrolling text areas in Firefox (happens as I write this), the cursor and letters get momentarily warped as I type, especially in gnome-terminal and so on. But it's bearable, nothing like before when I'd get "runny" slices all over the place.

Here's hoping AMD keeps up the good work. The performance is still not up to par, for instance. The Radeon HD3200 I'm trying is supposed to be on par or better than the NVidia 7600GS but this latest Catalyst gets only 1750 FPS in glxgears whereas the 7600 gets 2800 FPS with the NVidia binary drivers. Not to sound ungrateful but performance is a big thing, we want to use ATI cards for gaming and such, if it was only for Compiz we'd get by with much older or weaker stuff.

---

### Post by blueturtl on 2010-10-26
You may wish to use something other than glxgears as a benchmark. Just saying.

---

### Post by sandyd on 2010-10-26
> **wirespot said:**
> Finally, got to try this driver. I think it's this one, I installed from Ubuntu's "Hardware Drivers", it has version 8.783 which is the same as the driver downloaded from AMD.

Indeed, the vsync issues are mostly fixed. No longer get any major tearing of the desktop like before. Flash, movies, Compiz, games all seem to work fine.

There are some minor issues still there though, you get corrupted bits of screen here and there, especially in scrolling text areas in Firefox (happens as I write this), the cursor and letters get momentarily warped as I type, especially in gnome-terminal and so on. But it's bearable, nothing like before when I'd get "runny" slices all over the place.

Here's hoping AMD keeps up the good work. The performance is still not up to par, for instance. The Radeon HD3200 I'm trying is supposed to be on par or better than the NVidia 7600GS but this latest Catalyst gets only 1750 FPS in glxgears whereas the 7600 gets 2800 FPS with the NVidia binary drivers. Not to sound ungrateful but performance is a big thing, we want to use ATI cards for gaming and such, if it was only for Compiz we'd get by with much older or weaker stuff.

[http://ubuntuforums.org/showthread.php?t=772664](http://ubuntuforums.org/showthread.php?t=772664)
I can get 2000 fps on a mobility 3650 with all the kwin effects on (i.e transparency, cube). but not blur, obviously.

---

### Post by bgilbert on 2010-10-27
Thanks a lot SandyD....this brought huge improvements with my HD 5730 as well!

---

### Post by juancarlospaco on 2010-10-27
*The Perl web framework or the Cisco switches ...?*
:D

---

