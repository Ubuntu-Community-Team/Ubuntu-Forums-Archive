---
title: "Lightweight distro for picture frame?"
date: 2008-08-29
forum: The Cafe
---

### Post by BetterSense on 2008-08-29
I need a lightweight linux distribution for a picture frame. Its sole purpose in life will be to boot, and run the program feh to show a slideshow of the pictures on the flash drive or possibly from the internet.

Requirement: the program feh.

I would just use Ubuntu because that's what I'm familiar with, but I would have to buy a 4GB compact flash card even for Xubuntu because it requires 2.8GB. I would like to be able to install on a 1GB card, to save money.

I looked at DSL but by default it doesn't have apt-get, so I couldn't install feh. I'm a total linux noob, so I didn't know how else to install it.

---

### Post by LaRoza on 2008-08-29
How about a minimal install of Debian?

---

### Post by BetterSense on 2008-08-29
I don't know how to do that. Is there a 'minimal Debian install' cd? Cause I'm not smart. I only know how to install ubuntu from a live or alternate CD.

---

### Post by Twitch6000 on 2008-08-29
> **BetterSense said:**
> I don't know how to do that. Is there a 'minimal Debian install' cd? Cause I'm not smart. I only know how to install ubuntu from a live or alternate CD.

Yes there is a minimal install of Debian.
You get it on their site.I suggest version stable for what you will be using it for.

---

### Post by init1 on 2008-08-29
Linux for a picture frame? Seems overkill. I'd use FreeDOS. The only problem is that there aren't any good slideshow apps for DOS. There's lxpic, but you can't change the slideshow speed. There's jpgshow, but that only for jpegs. I've tried dozens of DOS picture viewers, but those are the only practical options. If those aren't suitable, I'd run Debian and feh. 
[http://www.freedos.org/](http://www.freedos.org/)
[http://hplx.pgdn.de/](http://hplx.pgdn.de/)
[http://www.pictview.com/showjpg.htm](http://www.pictview.com/showjpg.htm)

---

### Post by LaRoza on 2008-08-29
> **init1 said:**
> Linux for a picture frame? Seems overkill. I'd use FreeDOS. The only problem is that there aren't any good slideshow apps for DOS. There's lxpic, but you can't change the slideshow speed. There's jpgshow, but that only for jpegs. I've tried dozens of DOS picture viewers, but those are the only practical options. If those aren't suitable, I'd run Debian and feh. 

Linux isn't that much bigger, and it is perfectly suited for it. After all, Linux runs on motherboards (part of the hardware) and in routers.

---

### Post by saulgoode on 2008-08-29
> **BetterSense said:**
> I looked at DSL but by default it doesn't have apt-get, so I couldn't install feh. I'm a total linux noob, so I didn't know how else to install it.

You should be able to download the Debian package for 'feh' manually (using a different computer and transferring the file to your DSL machine if necessary) and then use 'dpkg' to install the package. For example,[INDENT]**dpkg -i feh_1.3.4-2_i386.deb**[/INDENT]

I'm not certain this will work as I don't use DSL that much (hardly ever, anymore) but it is worth a try if you still have DSL installed on your picture frame machine.

---

### Post by barbedsaber on 2008-08-29
In DSL, just run apt-get install apt :)

---

### Post by klange on 2008-08-30
> **barbedsaber said:**
> In DSL, just run apt-get install apt :)
DSL comes with apt.

You can't use Deb packages because of what they're compiled for. Heck, DSL is on a 2.4 kernel track with a completely different libc version, etc. etc.

---

### Post by Riffer on 2008-08-30
Here is a HOWTO for a minimal system.  

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Hope it helps

---

### Post by BetterSense on 2008-08-30
> Linux for a picture frame? Seems overkill. I'd use FreeDOS

I don't know anything about DOS or its commands or anything. I have plenty of space for linux, the computer used to have windows NT or 2000 or something on it

> **WindowsSucks said:**
> DSL comes with apt.

You can't use Deb packages because of what they're compiled for. Heck, DSL is on a 2.4 kernel track with a completely different libc version, etc. etc.

Supposedly the DSL apt uses the woody repository, which is old and stuff.

> You should be able to download the Debian package for 'feh' manually (using a different computer and transferring the file to your DSL machine if necessary) and then use 'dpkg' to install the package. For example,

    dpkg -i feh_1.3.4-2_i386.deb
Like that one dude said, I don't know if the packages will work cause it's 2.4 and all. But couldn't I get the feh source code and compile in on the machine? Note: I have no idea how to do that.

---

### Post by saulgoode on 2008-08-30
> **BetterSense said:**
> Like that one dude said, I don't know if the packages will work cause it's 2.4 and all. But couldn't I get the feh source code and compile in on the machine? Note: I have no idea how to do that.

The difficulty with that approach is that your target machine would need to have the necessary development tools available (the C compiler, libraries, and linker), as well as the header files which permit you to compile source code. It is unlikely that DSL includes these (since they are not necessary for typical usage and DSL tries to have a minimal footprint), and having to add all that and then compile 'feh' would probably be more difficult than choosing a different distribution. 

An alternative would be compile 'feh' on a different machine (perhaps your Ubuntu machine) but configure things so that the final result targets your DSL machine. While possible, this is a rather advanced approach and I would not recommend it to someone who is just beginning to become familiar with GNU/Linux.

I would recommend that you post a request on the DSL forums and ask if some kind soul would be willing to create a 'feh' package for your DSL system (be sure to tell them the version your are running and the details of your machine). Some of those people would already have a setup which can accomplish the compilation and packaging for you (since that is how they create DSL :) ) and the task should not be as difficult for them.

Otherwise, look for a different lightweight which either provides a 'feh' package or for which you can find someone to create one for you.

---

### Post by BetterSense on 2008-08-30
Actually, now based on the info that pops up when you run the DSL liveCD, it seems that even a HDD install requires you to configure X and stuff every time you boot. That won't work for this, which has to boot directly into the slideshow because I don't plan on having a keyboard hooked up.

---

### Post by Barrucadu on 2008-08-30
You could try a really minimal Arch, or even LFS, with just the bare minimum required to boot and run feh.

---

### Post by BetterSense on 2008-08-30
well I managed to install and run dsl from the compact flash. The problem I have now, and this really blew my mind, is that the machine doesn't seem to have an ethernet port. 

No ethernet port.

No modem port either.

So I can't even connect this thing to the internet to enable apt! I think it had a docking station originally and the docking station probably had the ethernet port on it. But I don't have the docking station.

I do have a CF-to USB adator, so I could boot from the CF card on my main computer, and somehow compile feh onto there. But I'm not smart.

---

### Post by init1 on 2008-08-30
> **LaRoza said:**
> Linux isn't that much bigger, and it is perfectly suited for it. After all, Linux runs on motherboards (part of the hardware) and in routers.
Yeah, it just seems extreme to use a multitasking, multiuser OS designed after the OS of some of the most power computers of it's day to display pictures. Might be the most practical option though, especially since the OP has said that they don't know DOS.

---

### Post by init1 on 2008-08-30
> **BetterSense said:**
> well I managed to install and run dsl from the compact flash. The problem I have now, and this really blew my mind, is that the machine doesn't seem to have an ethernet port. 

No ethernet port.

No modem port either.

So I can't even connect this thing to the internet to enable apt! I think it had a docking station originally and the docking station probably had the ethernet port on it. But I don't have the docking station.

I do have a CF-to USB adator, so I could boot from the CF card on my main computer, and somehow compile feh onto there. But I'm not smart.
Yeah my old laptop is like that. How much RAM do you have? Perhaps I can think of something for you to use.

---

### Post by BetterSense on 2008-09-01
I gave up on DSL and installed a command-line Hardy system. I used a connected computer and a CF adaptor. I didn't do any stripping down after installing a command line system, then I basically just apt-get'd xorg and feh. Feh runs fine without a window manager.

The problems I have now are that I need it to auto-log me in, because I won't have a keyboard. I did a bit of searching but didn't find much. 

I also need to place my 'startx' command somewhere, I'm not sure where. 

And then, I need a permanent path for my 'start feh' script, but I also need it to be on a flashdrive. So I think I might have to like add a 'mount flashdrive on boot' script in there somewhere or put it in the fstab or something. I'm not sure if I'll be able to remove and reinstall the flashdrive (with updated pictures) with the system up and running, but I would like to.

---

### Post by Reivax22 on 2008-09-04
Hello Better Sense

There is a light linux package created just to show picture on a old computer at this adresse:

[http://mcdpf.wiki.sourceforge.net/](http://mcdpf.wiki.sourceforge.net/)

I hope it will be useful. Let me now if it works properly , because I planned to do this anytime soon !

---

### Post by mikjp on 2008-09-04
> **bettersense said:**
> i looked at dsl but by default it doesn't have apt-get, so i couldn't install feh. I'm a total linux noob, so i didn't know how else to install it.

rtfm.

[http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions](http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions)

The Official Damn Small Linux(R) Book has also a chapter about making a media frame out of an old laptop.

mikko

---

