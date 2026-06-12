---
title: "Edgy Request: Blender 2.43"
date: 2007-02-19
forum: Repositories &amp; Backports
---

### Post by Statik on 2007-02-19
Hi All,

Blender.org has been updated and version 2.43 has been released! The linux version has ffmpeg compiled in and it is ready to be used for video editing as well as all the other 3D goodness! Can we get it into the repositories? It might make Ubuntu a little more attractive for video edittng and 3d editing. I'm installing it by hand but I remember when I started with Ubuntu, feeling disipointed when Ubuntu didn't have the most recent version of blender.

Statik

---

### Post by Stylee on 2007-02-19
Hi,

I am new to Ubuntu...
Can you explain me how to instal blender 3.43 without the package?

thank you...

---

### Post by carlwh123 on 2007-02-20
> **Stylee said:**
> Hi,

I am new to Ubuntu...
Can you explain me how to instal blender 3.43 without the package?

thank you...


Me too, except its "2".43 and I gather its not really going to work properly until they release the repo right? Because I tried it and I couldn't even get the hotkey reference page to come up.
thanks for any advice.

---

### Post by Joey French on 2007-02-20
I just upgraed and everything works fine. I simply downloaded the file tar.gz, extracted it to my desktop, moved it to /opt/blender and ran it with /opt/blender/blender. Works fine for me. Per the instructions on the site:
> To install Blender, download the appropriate package for your platform to your computer. The Windows version comes with an optional self-extracting installer, for other operating systems you can unpack the compressed file to the location of your choice.  

Provided the Blender binary is in the original extracted directory, Blender will run straight out of the box. No system libraries or system preferences are altered. 
Also, it flies! It's actually shocking how fast it gets up and goes...

---

### Post by Stylee on 2007-02-20
> **Joey French said:**
> I just upgraed and everything works fine. I simply downloaded the file tar.gz, extracted it to my desktop, moved it to /opt/blender and ran it with /opt/blender/blender. Works fine for me. Per the instructions on the site:
 
Also, it flies! It's actually shocking how fast it gets up and goes...

I have the 2.42 version instaled, but but my /opt is empty (I've enabled to see hiden). I have the .blender directory in /home/filip(my usr-name), but there is a diferent layout of files then in blender-2.43-linux-glibc232-py24-i386.tar.bz2...

---

### Post by carlwh123 on 2007-02-20
Yeah, I don't see the blender folder in /opt either - just azureus (and i have hidden files showing).
I did a search for the blender folder and I found a few different ones.

I'm an ex-windows user and I find it anoying how when I right click on launchers in the applications menu I can't find out which file they are linked to.....is their a way to do this?

sorry i'm a total linux n00b.

---

### Post by Statik on 2007-02-20
For those who have 2.42 already installed, what I did was:
1. download the file from blender.org and extract it to a folder in your home directory
2. I checked in Synaptic to see where the 2.42 files were installed. If I remember correctly, the blender and blenderplayer files were in /usr/bin/blender and the rest were in /usr/etc/blender. Check synaptic to be sure.
3. sudo mv blender /usr/bin/blender/blender
 and so on for all the files. You need sudo because of the file protection on the files. Blender is installed through Synaptec for everyone, not just your username. Once all the files and directories are moved, 2.43 works.

NOTE: there is a hidden directory .blender, in the archive. Move it to the same place as the plugins directory.

Statik

---

### Post by Marsan on 2007-02-20
> **Statik said:**
> For those who have 2.42 already installed, what I did was:
1. download the file from blender.org and extract it to a folder in your home directory
2. I checked in Synaptic to see where the 2.42 files were installed. If I remember correctly, the blender and blenderplayer files were in /usr/bin/blender and the rest were in /usr/etc/blender. Check synaptic to be sure.
3. sudo mv blender /usr/bin/blender/blender
 and so on for all the files. You need sudo because of the file protection on the files. Blender is installed through Synaptec for everyone, not just your username. Once all the files and directories are moved, 2.43 works.

NOTE: there is a hidden directory .blender, in the archive. Move it to the same place as the plugins directory.

Statik


Sounds real complicated for a noob user.. i will rather wait untill the 2.43 (hopefully) gets to the repos ...

---

### Post by Stylee on 2007-02-20
Thanke you for your help, I've understand what to do, but I'm still a litlle bit unshure...
I've tried to duble click the executable file named blander in the extrackted arhive, and it works... or this is an unapropriated way?

---

### Post by carlwh123 on 2007-02-20
> **Statik said:**
> For those who have 2.42 already installed, what I did was:
1. download the file from blender.org and extract it to a folder in your home directory
2. I checked in Synaptic to see where the 2.42 files were installed. If I remember correctly, the blender and blenderplayer files were in /usr/bin/blender and the rest were in /usr/etc/blender. Check synaptic to be sure.
3. sudo mv blender /usr/bin/blender/blender
 and so on for all the files. You need sudo because of the file protection on the files. Blender is installed through Synaptec for everyone, not just your username. Once all the files and directories are moved, 2.43 works.

NOTE: there is a hidden directory .blender, in the archive. Move it to the same place as the plugins directory.

Statik

Cheers mate, that worked for me....and also i should point out it can be useful to use "sudo nautilus" which loads up the normal gui where you have root access and can easily copy and paste the files. Its possibly not the safest way but for n00bs its good (I couldn't even figure out how to overwrite the plugins folder using the command shell). :)

---

### Post by moeFinley on 2007-02-21
I have a small file call "blender" and an executable called "blender-bin".  Do I have to re-name the executable that comes in the package?

/usr/bin/blender-bin
/usr/bin/blender
/usr/bin/blenderplayer

:confused:

---

### Post by knn on 2007-02-28
[Here's]("http://people.inf.elte.hu/kovacsn/blender/blender_2.43-0ubuntu1_i386.deb")  a backport of Feisty's 2.43 package to Edgy (i386)

---

### Post by Stylee on 2007-02-28
Thanke you,  this is what I was shearching for :)

---

### Post by gmjs on 2007-03-12
I've tried running Blender 2.43 under Ubuntu 6.10 (gcc 4.1.2 (prerelease)) and have an intermittent fault.  Sometimes it starts with no problems, other times Ubuntu completely locks up and I have to switch off my PC completely and reboot.  I am very new to Linux, so I don't know how to solve this (I tried uninstalling and reinstalling Python after trying to install an older version of gcc (which failed!) and all I managed to do was remove the Gnome Desktop package!  I had to retrieve it by re-installing ubuntu-desktop).  I think I'll wait for Ubuntu 7.04!

---

### Post by gmjs on 2007-04-09
Aha...sorted.  I have (probably rather unfortunately) an ATI Radeon 9200 graphics card.  I have since managed to install the appropriate drivers for the card (the self-extracting installer file will not run using the 'dash' shell - I renamed 'bash' to 'dash' and got it to install successfully).  No problems running Blender 2.43 now.  It runs straight away by double-clicking the binary file after download.  I'm learning (albeit slowly)!

---

### Post by knn on 2007-04-10
> **gmjs said:**
> Aha...sorted.  I have (probably rather unfortunately) an ATI Radeon 9200 graphics card.  I have since managed to install the appropriate drivers for the card (the self-extracting installer file will not run using the 'dash' shell - I renamed 'bash' to 'dash' and got it to install successfully).  No problems running Blender 2.43 now.  It runs straight away by double-clicking the binary file after download.  I'm learning (albeit slowly)!

You should install the driver from the ubuntu restricted repository, to get automatic updates whenever there's a kernel update (otherwise every time there's a kernel update you'll be left without a gui and will have to reinstall the driver)
[How to install binary driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

And another tip: the first line in scripts that specifies which shell program they want to be run with. This is usually /bin/sh. In Ubuntu, /bin/sh is a symbolic link (something like a windows shortcut except it's completely transparent to applications) to /bin/dash. To make it a symbolic link to /bin/bash:
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh



[read more here]("http://www.hmug.org/man/1/ln.php")

---

