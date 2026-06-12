---
title: "Ubuntu shines :)"
date: 2008-02-15
forum: Testimonials &amp; Experiences
---

### Post by Wolfghar on 2008-02-15
Greetings!  I'm a long time Windows user although I've always been interested in running Linux, I've spent some time a couple years back playing around with Gentoo but in the end I just went back to Windows because of lack of hardware support back then and Gentoo was damn hard to install LOL.

How times have changed...

I recently got myself a new core2 duo system (E6550) with 3 gigs of ram and a ATI Radeon 2600 XT and with that came the urge to try Linux again.  I started reading alot and downloading some live cd's to try and Ubuntu 7.10 was one of the first and I liked it..

I've spent a couple weeks now messing around with it and re-learning allot of the stuff I had forgotten when I used Gentoo, I finally got a dual-boot Ubuntu/Windows XP system up and running and it's awesome (I barely boot into XP anymore, I'll explain shortly.)

After a couple of weeks of trial and error, lots of reading and a couple re-installs I finally have the dual head goodness working and Ubuntu is looking good on my 37" and 22" LCD's :)

I used Envy to install the ATI drivers, getting the dual head working was a pain and I hope I never have to go through that again LOL.  I made an image of my working Ubuntu so if I ever screw it up I can just reformat and put the image back...

So Ubuntu is working good, dual head big desktop is working good, compiz effects are on (cube and stuff) :), I've got remote desktop access to my other Windows XP machine (which I might switch to Ubuntu as well).

I recently discovered the miracle of VirtualBox and decided to give it a go, so I installed it and setup a virtual XP Pro which works better than it did running live...

Some more tweaks and many more hours of reading and I have my virtual XP Pro running in seamless mode along side Ubuntu!!  I still can't get over seeing XP software running on the Ubuntu desktop...  Only one small problem, the virtual XP windows are stuck on whichever monitor I start it in seamless.  It would be nice if I could move them across to the other monitor (any ideas??)

The one other problem I have and it's kinda major, video playback tears very badly and I have yet to find an answer for it...

So at this point, I have to boot into XP to watch movies and play UT3 (I hear there will be a UT3 linux client someday)...

I'm very pleased with Ubuntu, it's slick and good looking and the virtual seamless XP is a nice bonus for the odd time I want to use it...

Ubuntu!!!

Wolfghar

---

### Post by DaveyBaby on 2008-02-15
Hi, I am a new comer to Ubuntu and want to install VirtualBox. Can you provide instructions on how youy did this?  Thanks

---

### Post by CompGeek on 2008-02-15
Hey if anyone is wondering how to install VmWare on ubuntu 7.1 
here is a great LInk

:popcorn:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by Wolfghar on 2008-02-15
> **DaveyBaby said:**
> Hi, I am a new comer to Ubuntu and want to install VirtualBox. Can you provide instructions on how youy did this?  Thanks

I found it in the main menu 'Applications' / 'Add/Remove', look for **InnoTek VirtualBox** then mark for install and apply.  I have 3rd party archive enabled which I'm not sure if it makes a difference..

Wolfghar

---

### Post by MNICY on 2008-02-15
The default virtualbox for Ubuntu is the OSE (open source edition) which does not have USB capabilities.
install by typing:
```
sudo apt-get install virtualbox
```

If you want the full edition, go to [http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads) 

INSTRUCTIONS for Virtualbox:
```
sudo gedit /etc/apt/sources.list
```
add this to the bottom of the list: (depending on your distro)
Gutsy:
```
deb http://www.virtualbox.org/debian gutsy non-free
```
Feisty:
```
deb http://www.virtualbox.org/debian feisty non-free
```

Save this to a folder (like your desktop):
[http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)

In terminal, navigate to where you saved that file
(if it is desktop then this:
```
cd ~/Desktop
```

type this:
```
sudo apt-key add innotek.asc
```

then:

```
sudo apt-get install Virtualbox
```

---

### Post by Wolfghar on 2008-02-15
Thanks for that info MNICY, I went ahead and removed the OSE package and followed your instructions to install the other one.  I was presented with an error that went something like this..

*Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.*

so I did some searching and found the solution.  I had to edit this _/etc/init.d/mountdevsubfs.sh_ file to make it work.  (uncomment these lines)

```
    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb
```

After I did that it worked...  now I just have to figure out how to use my USB hard drive, something to do with permissions. [COLOR="SeaGreen"]EDIT: I just figured that too...  :)[/COLOR]

Wolfghar

---

