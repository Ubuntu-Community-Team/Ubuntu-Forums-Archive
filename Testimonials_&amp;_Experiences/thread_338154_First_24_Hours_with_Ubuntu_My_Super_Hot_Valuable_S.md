---
title: "First 24 Hours with Ubuntu: My Super Hot Valuable Sexy Feedback"
date: 2007-01-14
forum: Testimonials &amp; Experiences
---

### Post by jloehrlein on 2007-01-14
I'm a game developer, I've only ever used Windows before, I've been using Ubuntu for about a day and I thought I would list my thoughts on it. 

My two main purposes for using Ubuntu are to see if I can develop games in a general manor so that they can be ported easily(which I can't do in Windows), and to see if I could put this on my parent's computers so that they wouldn't have to worry so much about viruses and other malware.

I used the standard install off the live CD, I figured it would be the easiest.

The disk configuration tool that came on the live CD was very useful, :) much better than Windows. It was annoying to have to create a swap partition, I wish that was optional also the whole thing about mounting a drive as / is really cryptic, It was not something I needed to know. After installing I looked for that drive configuration tool on a menu but couldn't find it.

I find myself wondering why everything has weird names like "GRUB", gparted, and xorg. I wish they would just be named for what they do. :confused: 

Setting up a dual boot system took a while. I was glad Ubuntu came with GRUB :) , much nicer than Windows which comes with "wipe out other OS's". However I had to go into the shell and configure quite a bit before both Linux and Windows were happy. Windows was actaully more resilient during this process because it didn't need hardcoded mounts like Ubuntu. The "kernal" parameter required for Ubuntu is at fault here.

The first thing I noticed on the desktop was that it wasn't using the right resolution. I found the resolution changer quickly, but it wasn't useful as I was already using the highest res it allowed. I guessed I needed to install video drivers so I went the nvidia site and downloaded them to the desktop. Then I double clicked on the icon to install the drivers, it opened them in a text editor, that wasn't so helpful. I went into the terminal and typed the name of the file to run it, but that didn't do anything. Finally I googled "nvidia ubuntu drivers install" and blindly followed some terminal directions. I have no idea what it did but I assumed it worked as the nvidia logo started popping up at login (which I find annoying). However I still couldn't change the resolution any higher than 1024x768. 

I googled "ubuntu desktop resolution" which led me to reconfiguring something called xorg (again using the terminal). I just wanted to add some resolutions but it asked about a bunch of stuff that I really didn't know about. This worked but I was worried about hosing Ubuntu. Finally I was able to change my desktop resolution. If I gave Ubuntu to my parents they will be using 1024x768 on their 1280x1024 LCD which won't look so hot. :( 

Messing around with the desktop settings was actually fun :) , and the default was a bit better than Windows. I noticed the Firefox icon on the top bar and wondered how to add my own links there. Around this time Ubuntu told me to update my software so I did, it took a few hours (91 downloads) but that didn't really bug me as it seemed like I was getting some good stuff.

Next I decided I wanted to see if I had the nvidia drivers installed right. I decided the best way to do this was to download a game. I'm in the independent game development community so it wasn't too hard to find something (I went for the demo of "Tribal Trouble" from garagegames.com). This was much like installing the nvidia drivers in that clicking the downloaded file didn't do squat :mad: . At this point I concluded that if I put this on my parent's computer they couldn't use it day to day because they wouldn't be able to install programs.  I had to go into the console and run it with sh. I still have no idea what sh is, I googled "sh linux" but nothing told me what it was and I couldn't find any help on it.

At this point I tried using the add/remove menu item hoping it would be an easy way to install downloaded packages. While that's not what it does I was thrilled :D to see that it automagically downloads and installs a ton of stuff. This is great, my parents could probably use this to get office apps and games. I was however disappointed for myself because it only works with packages Ubuntu has posted, which is way more restrictive than Windows installers.

Around this time I decided to get my logitech mx1000 laser mouse working properly. Long story short, more console and file editing. I wish there was a gui app that would let me assign function to buttons.

One thing I appreciated was that Ubuntu never stopped working for no reason the way Windows likes to. If it got messed up it was always because of something I did and I could figure out what and fix it. :-k 

Ubuntu's weakest point is the console, None of the things I did should have required it, but almost everything did. Consoles are great for development when your trying to do something new, but when trying to do well established tasks (like setting your desktop resolution or installing a game) a console is a pain in the arse. 

I liked the security of not running as root but I was annoyed when I couldn't edit config files from the desktop. I had to go into the console and use sudo to open the editor. I wish the editors  would ask for my password when I try to save a protected file rather then requiring me to start the editor with sudo.

I like Ubuntu and plan to do some development on it, but I don't want to write apps for an OS where normal people couldn't figure out how to install them.

---

### Post by Extreme Coder on 2007-01-14
Hey jloehrlein,
Nice to see that you liked it a bit in the end. If you want to run a file by double-clicking on it, there is no need to go to the terminal. Right-click on the file, choose properties. In the permisssions tab, Check the "Allow this file to run as a program". THis will allow you to run the nVidia driver, and the Tribal Trouble game, by double clicking only. And I think there's a way to make all scripts executable by default, but I'm not sure.

---

### Post by Grey on 2007-01-14
Installing software in Ubuntu is even easier than it is for Windows actually.  The trick is that the software that you download must be packaged in a proper format.  Much like a Windows installer must be packaged with an installer program in an .exe, Ubuntu software must be packaged in a .deb.  If you download a deb and double click it, it will install on your computer the proper way.

Installing software manually takes a bit more work.  On Windows, any file with a .exe extension is thought to be executable.  On Linux, there's a flag on the file that marks it as executable, and newly downloaded files are generally not marked as executable.  I've never used the nvidia drivers from their site, for fear of tainting the ubuntu package management.  But I would imagine that they come with instructions on how to install them.  Installing them manually is generally a power user thing anyway.  Most people opt for installing the drivers from the repositories.

But this sort of information should really be more clearly presented to new users.  The next release will actually install the nvidia drivers by default, despite licensing issues though, so you might want to try that when it comes out.  It should give you a lot less headache.

---

### Post by PetePete on 2007-01-16
i agree with the console thing, personly i dont mind using it, quite like it actualy! but if ubuntu/linux wants to become more mainstream its got to be designed so the user never has to use the console and theres a GUI for everything .... and not a txt based gui !

it just scares new users and seems primitive to the uneducated ;)

---

### Post by jloehrlein on 2007-01-16
Well let me just update. I really like Ubuntu, and I will continue using it. Just I'll be waiting egarly for a version I can give to non-tech people.

I think a lot of people want "linux for humans" myself included. Ubuntu is still getting some of the core functionality up and running, once that's done it'll be easier to get a smooth user interface.

It's just a matter of time.

---

### Post by Tux Aubrey on 2007-01-16
Welcome!

In your OP you noted: 

> I liked the security of not running as root but I was annoyed when I couldn't edit config files from the desktop. I had to go into the console and use sudo to open the editor. I wish the editors would ask for my password when I try to save a protected file rather then requiring me to start the editor with sudo.

There are a few lovely little scripts (available if you install and [Automatix]("http://www.getautomatix.com")) that give you right-click access to gedit and nautilus as root.  Once you get used to them being there, they become very convenient for editing read-only files.

---

### Post by 3rdalbum on 2007-01-17
Drag and drop editing as root is really easy to accomplish - it's a pity you're not a Mac user, or you'd love this as much as me.

Create a launcher on the desktop, and give it the command:

```

gksudo -m "Enter your password to open the file \"%u\" as root." gnome-open %u

```

Now, whenever you're working in the filesystem and you want to open a file as root, just drag it onto the launcher. You will be prompted for your password, and then the file will open as root.

PetePete, remember that most people chose to use Windows 3.1 and Win 95 over the Macintosh operating system, even though the former depended heavily on the terminal and the Mac didn't even have one. Were you a Macintosh user?

---

### Post by rocknrolf77 on 2007-01-18
And it's also nice to know that you can just hit alt - F2 then you get the run box. Just type ```
gksudo nautilus
``` in it and you can browse all the files as root in nautilus.

---

### Post by galileon on 2007-02-05
Welcome to the Linux World, son. You are now a man.

> **jloehrlein said:**
> I'm a game developer, I've only ever used Windows before, I've been using Ubuntu for about a day and I thought I would list my thoughts on it. 

My two main purposes for using Ubuntu are to see if I can develop games in a general manor so that they can be ported easily(which I can't do in Windows), and to see if I could put this on my parent's computers so that they wouldn't have to worry so much about viruses and other malware.

I used the standard install off the live CD, I figured it would be the easiest.

The disk configuration tool that came on the live CD was very useful, :) much better than Windows. It was annoying to have to create a swap partition, I wish that was optional also the whole thing about mounting a drive as / is really cryptic, It was not something I needed to know. After installing I looked for that drive configuration tool on a menu but couldn't find it.

I find myself wondering why everything has weird names like "GRUB", gparted, and xorg. I wish they would just be named for what they do. :confused: 

Setting up a dual boot system took a while. I was glad Ubuntu came with GRUB :) , much nicer than Windows which comes with "wipe out other OS's". However I had to go into the shell and configure quite a bit before both Linux and Windows were happy. Windows was actaully more resilient during this process because it didn't need hardcoded mounts like Ubuntu. The "kernal" parameter required for Ubuntu is at fault here.

The first thing I noticed on the desktop was that it wasn't using the right resolution. I found the resolution changer quickly, but it wasn't useful as I was already using the highest res it allowed. I guessed I needed to install video drivers so I went the nvidia site and downloaded them to the desktop. Then I double clicked on the icon to install the drivers, it opened them in a text editor, that wasn't so helpful. I went into the terminal and typed the name of the file to run it, but that didn't do anything. Finally I googled "nvidia ubuntu drivers install" and blindly followed some terminal directions. I have no idea what it did but I assumed it worked as the nvidia logo started popping up at login (which I find annoying). However I still couldn't change the resolution any higher than 1024x768. 

I googled "ubuntu desktop resolution" which led me to reconfiguring something called xorg (again using the terminal). I just wanted to add some resolutions but it asked about a bunch of stuff that I really didn't know about. This worked but I was worried about hosing Ubuntu. Finally I was able to change my desktop resolution. If I gave Ubuntu to my parents they will be using 1024x768 on their 1280x1024 LCD which won't look so hot. :( 

Messing around with the desktop settings was actually fun :) , and the default was a bit better than Windows. I noticed the Firefox icon on the top bar and wondered how to add my own links there. Around this time Ubuntu told me to update my software so I did, it took a few hours (91 downloads) but that didn't really bug me as it seemed like I was getting some good stuff.

Next I decided I wanted to see if I had the nvidia drivers installed right. I decided the best way to do this was to download a game. I'm in the independent game development community so it wasn't too hard to find something (I went for the demo of "Tribal Trouble" from garagegames.com). This was much like installing the nvidia drivers in that clicking the downloaded file didn't do squat :mad: . At this point I concluded that if I put this on my parent's computer they couldn't use it day to day because they wouldn't be able to install programs.  I had to go into the console and run it with sh. I still have no idea what sh is, I googled "sh linux" but nothing told me what it was and I couldn't find any help on it.

At this point I tried using the add/remove menu item hoping it would be an easy way to install downloaded packages. While that's not what it does I was thrilled :D to see that it automagically downloads and installs a ton of stuff. This is great, my parents could probably use this to get office apps and games. I was however disappointed for myself because it only works with packages Ubuntu has posted, which is way more restrictive than Windows installers.

Around this time I decided to get my logitech mx1000 laser mouse working properly. Long story short, more console and file editing. I wish there was a gui app that would let me assign function to buttons.

One thing I appreciated was that Ubuntu never stopped working for no reason the way Windows likes to. If it got messed up it was always because of something I did and I could figure out what and fix it. :-k 

Ubuntu's weakest point is the console, None of the things I did should have required it, but almost everything did. Consoles are great for development when your trying to do something new, but when trying to do well established tasks (like setting your desktop resolution or installing a game) a console is a pain in the arse. 

I liked the security of not running as root but I was annoyed when I couldn't edit config files from the desktop. I had to go into the console and use sudo to open the editor. I wish the editors  would ask for my password when I try to save a protected file rather then requiring me to start the editor with sudo.

I like Ubuntu and plan to do some development on it, but I don't want to write apps for an OS where normal people couldn't figure out how to install them.

---

### Post by Peti29 on 2007-02-05
> **jloehrlein said:**
> I don't want to write apps for an OS where normal people couldn't figure out how to install them.
Hmmm. I also think that's a problem. Any solution for this? (As someone new to Linux/Ubuntu I stick to only install apps through Add/Remove or Synaptic)

---

### Post by galileon on 2007-02-05
already been mentioned above - dot-debs

or, alternatively, like aMSN does, the Autopackage system (although it requires Tcl and Tk to be installed from synaptic) - but it's all graphical

there was mention of an installation system that could eat through dot-debs, dot-rpm, dot-tgz etc 

[https://launchpad.net/alien](https://launchpad.net/alien)

---

### Post by marx2k on 2007-02-06
> **Grey said:**
> Installing software in Ubuntu is even easier than it is for Windows actually.  The trick is that the software that you download must be packaged in a proper format.  Much like a Windows installer must be packaged with an installer program in an .exe, Ubuntu software must be packaged in a .deb.  If you download a deb and double click it, it will install on your computer the proper way.

Installing software manually takes a bit more work.  On Windows, any file with a .exe extension is thought to be executable.  On Linux, there's a flag on the file that marks it as executable, and newly downloaded files are generally not marked as executable.  I've never used the nvidia drivers from their site, for fear of tainting the ubuntu package management.  But I would imagine that they come with instructions on how to install them.  Installing them manually is generally a power user thing anyway.  Most people opt for installing the drivers from the repositories.

But this sort of information should really be more clearly presented to new users.  The next release will actually install the nvidia drivers by default, despite licensing issues though, so you might want to try that when it comes out.  It should give you a lot less headache.

What i found to be VERY useful is compiling stuff from source... and once that is done, I use a program called 'checkinstall' which makes a DEB file for you out of the compiled binaries and installs them for you.

In this way you can also make your own packages to whatever program you make, so basically, the end user can just double click on a DEB file and it will install onto their system for them.

(and of course, if your work is pretty good, it can always be included onto the next distribution of Ubuntu in the repositories!)

---

### Post by rev_b on 2007-02-06
> **Peti29 said:**
> Hmmm. I also think that's a problem. Any solution for this? (As someone new to Linux/Ubuntu I stick to only install apps through Add/Remove or Synaptic)

Yes. Not assuming Linux is Windows. I was a all-windows user and I wanted to learn Linux/Ubuntu. When I noticed, I was doing most things the hard way - As a windows user, I had the common misconception that you can't use Linux without some cryptic comands on the terminal. Wrong, no need to get the terminal, cd here and there, ./ or sh, chmod this.

Just right click the game install script -> permissions -> allow executing file as a program.
Then just... double click the icon, confirm that you want it to run, and there you go. Your game installs right away. I installed every Linux game I own this way.

This is just an example how linux is way better designed than windows. Maybe if Windows didn't allow all executable files to run by default, it wouldn't be the virus/trojan/spyware mess it turned out. I still find unbelievable how many "average windows users" double-click on every clickmeimavirus.exe file they got attached on e-mails...

---

### Post by Leipe_Po on 2007-02-19
just try slackware linux and come back and tell us we need gui, linux forces people to know what theyr doing, not to keep them dumb....

i personaly like something i payed for and in controll of, rather then paying for stuff and let microsoft take over...

but thats my opinion

---

### Post by lyceum on 2007-02-19
So, you are going to make games for Linux? What program are you using? (just wondering). If you would like recomendations, here are two:

[blender](http://www.blender.org/) is a 3d rencering program made for games, but normally used for everyhing else 3D.

[Ogre ](http://www.ogre3d.org/) is a free 3D rendering engen, you write in C, if I remember correctly. There are some great how-tos in some back issures of [ LinuxFormat](http://www.linuxformat.co.uk/).

---

### Post by sloggerkhan on 2007-02-19
I must say that as far as making SIMPLE and QUICK models goes, I find wings3d to be rather nifty. I think they have it for windows, too. Of course blender is much better, just has the weirdest UI i've ever met for 3-d. It's powerful, but it takes getting used to. (I came from using Softimage XSI on windows, which was just completely different.)

Almost all the problems I've ever had with linux relate to graphics cards. So far as something your parents can use: If you install it properly for them, they will be able to use it without much trouble. But I'd doubt that they'd want to install it themselves.

Lastly, have you checked out ADD/REMOVE under applications and Synaptic under Administration? In general, you use them to install stuff more than downloading things separetely. Or you add locations to Administration > Software Sources.

---

