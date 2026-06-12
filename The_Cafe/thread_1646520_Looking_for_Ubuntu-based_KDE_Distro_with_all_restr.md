---
title: "Looking for Ubuntu-based KDE Distro with all restricted extras"
date: 2010-12-16
forum: The Cafe
---

### Post by shuttleworthwannabe on 2010-12-16
I want to get my wife to appreciate Linux and thought it would work if I gave a test machine to use for a while with an Ubuntu-based KDE Distro that comes with all the multimedia and other extras. Can u suggest one for me--I was thinking one in the line of Maverick 10.10--Mint is still in LTS version, so not mint.

Thanks

S

---

### Post by Megaptera on 2010-12-16
> **shuttleworthwannabe said:**
> I was thinking one in the line of Maverick 10.10--Mint is still in LTS version, so not mint.S

I'm puzzled why you don't want LTS (long term support)Lucid 10.04 and derivatives  which is supported longer than for instance Maverick 10.10?

But anyway, have you looked at Zorin?

From the website: "Zorin OS is a multi-functional operating system designed specifically for Linux beginners who want to have easy and smooth access to open source software. It is based on Ubuntu which is the most popular Linux operating system in the world.

Zorin OS features the unique Look Changer program which allows users to change the user interface at the touch of a button. Simply click on either the Windows 7, Windows XP or Linux's GNOME interface in Zorin OS Core and Educational and your desktop looks and behaves accordingly."

[http://www.zorin-os.webs.com/](http://www.zorin-os.webs.com/)

---

### Post by akand074 on 2010-12-16
I don't know one off the top of my head. But can't you just install the multimedia and extras on Kubuntu for her? Wouldn't take longer than a matter of minutes. If she was installing it/setting it up herself that would be a different story.

---

### Post by GabrielYYZ on 2010-12-16
Kubuntu is really solid IMHO, you should give it a chance and install all the extra stuff.

as a 2nd (and/or 3rd) option, i'd say open SUSE and/or PCLinuxOS full monty edition, i think they come with a whole lotta stuff right out of the box.

edit: didn't pay attention to the "ubuntu-based" part of the OP, in that case i don't really know.

---

### Post by Ichtyandr on 2010-12-16
Linux Mint KDE edition is probably what you need
Its based on Ubuntu and has multimedia and extras installed
The last version is based on Lucid afaik

---

### Post by Sean Moran on 2010-12-16
> **akand074 said:**
> I don't know one off the top of my head. But can't you just install the multimedia and extras on Kubuntu for her? Wouldn't take longer than a matter of minutes. If she was installing it/setting it up herself that would be a different story.
That's what I was thinking of suggesting.  Also, it wouldn't be too hard to add in a little bash script that anyone could run to apt-get the extras, as in:
```

#! /bin/bash
apt-get install acroread sun-java6-jre flashplugin-installer # anything else ?
apt-get install libavutil49 libschroedinger-1.0-0 libavcodec52 libavformat52 libpostproc51 libswscale0 gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 liba52-0.7.4 libdvdread4 libid3tag0 libmad0 libmpeg2-4 libsidplay1 libtwolame0 gstreamer0.10-plugins-ugly # gstreamer stuff for mp3 files as far as I know.

```I'm not sure if I remember whether  Skype is now part of the partner repos with Maverick, but it's fairly straight forward to just paste the one line - 
```

deb http://download.skype.com/linux/repos/debian/ stable non-free

```into the /etc/apt/sources.list if that's still required as it is on Karmic to go a skyping.

So there you have it!  Ubuntu 10.10 with KDE and lots opf extra goodies, (and a distro with that would take up far less than 1 Gb if it ever needed to morph into .iso form.

---

### Post by ilovelinux33467 on 2010-12-16
If you want Ubuntu based then I say go for Kubuntu. To get the restricted extras in Kubuntu just do:
```
sudo apt-get install kubuntu-restricted-extras
```

Easy :)

---

### Post by marl30 on 2010-12-16
> **Ichtyandr said:**
> Linux Mint KDE edition is probably what you need
Its based on Ubuntu and has multimedia and extras installed
The last version is based on Lucid afaik
This is what I'd recommend too. It's a DVD and a lot softwares will be preinstalled like Wine as well.

---

### Post by WinterMadness on 2010-12-16
Mandriva isnt Ubuntu based, but its the best KDE distro in my opinion.

If you want ubuntu based and KDE, why not just install KDE on ubuntu?

linux mint is another good choice, its pretty much the same as ubuntu, however it comes with a lot of multimedia stuff preinstalled.

---

### Post by shuttleworthwannabe on 2010-12-16
Thanks for all the suggestions--I will go for Kubuntu 10.10 (and will install the restricted stuff before handing over the test machine to her).

---

### Post by DoubleClicker on 2010-12-16
Avoid Zorin, it is nothing like what you are looking for. It's ugly, it's buggy, and uses GNOME, not KDE.

What you are looking for, doesn't exist "out of the box" yet, among any of the well known distributions.   But that doesn't mean you can get what you want, it just means more work. 
 
If you need it based on Maverick, Here are a few of your options.   

1) install linux Mint 9, and wait a month or so for the upgrade to mint 10.  

2) Install linux Mint 10. Then using Synaptic Package Manager, install the KDE desktop. 

3) install Kubuntu 10.10 and using Synaptic, add the media extras.  It really isn't that hard to do.

4) Go to [http://distrowatch.com/search.php?](http://distrowatch.com/search.php?) and do some research to find a minor distribution, that matches your criteria.   

5) Wait till someone, who is familiar with the minor distros, posts a response.  Though its more likely that you'll get mostly replies from people who are just guessing, and giving innaccurate advice.

---

