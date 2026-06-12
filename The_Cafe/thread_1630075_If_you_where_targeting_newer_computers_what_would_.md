---
title: "If you where targeting newer computers what would you change about ubuntu"
date: 2010-11-24
forum: The Cafe
---

### Post by nolag on 2010-11-24
This is not my computer, I have a better one then I am describing. I am just saying if ubuntu did not need to support computers that did not have at least the following what would you add/modify by default.
 
1) i686+ processors (maybe i786 if you have something cool for it, just mention it).
 
2) At least 4GB DDR3 RAM.
 
3) At least 256/512MB video RAM (if there is something requireing 512 just mention it)
 
4) at least 250 GB hard drive space (try not to use too much for the OS just saying it is there)
 
Your suggestions could be for preformance, power saving, ease of use, because you feel it would make the distro better.
 
I was thinking:
 
1) move tmp to RAM to increase preformance and reduce power usage (tell firefox and possibly other programs to use that location :P)
2) install compiz (and the manager etc)

---

### Post by grahammechanical on 2010-11-24
The computer you describe is not like my computer either. Only mine is not better. Oh. I do have 1026 MB memory on the graphic card and a 250 GB hard disc. so, I must be 25%  to 75%. 

I did not realize I was holding back the development of Ubuntu.

An OS that requires the very latest CPUs and as much memory as you can afford and then some more. Are you sure you are thinking of Linux and Ubuntu?

Regards.

---

### Post by 3rdalbum on 2010-11-24
Compiz is preinstalled on Ubuntu.

---

### Post by wilee-nilee on 2010-11-24
A built in espresso maker.

---

### Post by nolag on 2010-11-24
> **grahammechanical said:**
> The computer you describe is not like my computer either. Only mine is not better. Oh. I do have 1026 MB memory on the graphic card and a 250 GB hard disc. so, I must be 25%  to 75%. 

I did not realize I was holding back the development of Ubuntu.

An OS that requires the very latest CPUs and as much memory as you can afford and then some more. Are you sure you are thinking of Linux and Ubuntu?

Regards.


I am sorry, I don't mean it like that.  I am sure there are things that are not installed because of the amount of RAM or graphics requirements or hd space.  You are not "holding back" development, no one is.  I just think that people with higher end computers may want extras.    

@3rdalbum: I needed to install something to get the cube?  Or was it just to control it? (I am confused).

---

### Post by hhh on 2010-11-24
> **nolag said:**
> @3rdalbum: I needed to install something to get the cube?  Or was it just to control it? (I am confused).
Just to control it. In Synaptic, look for compizconfig-settings-manager. Then you'll find it under System>Preferences (I think, I'm not on Ubuntu right now). For more plugins, install compiz-fusion-plugins-extra.

---

### Post by thomas144 on 2010-11-24
Yes, I like the idea of moving /tmp to the RAM. My laptop has 3 GB of RAM and I definitely can spare some. Maybe you could have /tmp be a virtual file system in the RAM (like /proc is) and there could be a /tmp.bak on the hard drive and /tmp.bak is updated from /tmp every 10 minutes or something. But, I think this should be automatic (like of you have 2GB of RAM or more, store /tmp in RAM) but the user can ultimately set where he/she wants /tmp (hard drive or RAM) in a configuration file. I like your idea, nolag.

---

### Post by nolag on 2010-11-24
> **thomas144 said:**
> Yes, I like the idea of moving /tmp to the RAM. My laptop has 3 GB of RAM and I definitely can spare some. Maybe you could have /tmp be a virtual file system in the RAM (like /proc is) and there could be a /tmp.bak on the hard drive and /tmp.bak is updated from /tmp every 10 minutes or something. But, I think this should be automatic (like of you have 2GB of RAM or more, store /tmp in RAM) but the user can ultimately set where he/she wants /tmp (hard drive or RAM) in a configuration file. I like your idea, nolag.

Thank you, but I am curious why write it back to the disk at all?  Usually the /tmp is deleted on reboot anyways. Also thanks for the configurable idea, I'll try to work on that!

---

### Post by NightwishFan on 2010-11-24
Some programs store data in /tmp, such as for CD burning or DVD rips etc.. You might end up having over 4gb files in there.

---

### Post by GabrielYYZ on 2010-11-24
> **NightwishFan said:**
> Some programs store data in /tmp, such as for CD burning or DVD rips etc.. You might end up having over 4gb files in there.

couldn't something like: 

```

{
if (/tmp/*.* > 256mb)
          mv  /tmp/*.*/ -t /ram/
   else
               /tmp/*.* / == /dev/hd*/tmp
}

```

be done? i'm not a programmer and i do realise that, if it's possible, it might/will be harder than that but i'm interested to know if that could be done.

---

### Post by NightwishFan on 2010-11-24
I am sure something is possible. Though for simplicities sake I just have /tmp on my hard drive. If I really needed some peak performance and battery over general purpose use I would put it in a ram disk and just worry about any potential space fill-ups when I came around to it.

---

### Post by czr114 on 2010-11-24
/tmp becomes less and less of a bottleneck as more and more systems adopt SSDs for system drives.

The solution to a slow /tmp is a fast drive, not expensive RAM.

As NightwishFan pointed out, /tmp can't now nor in the future be expected to fit in RAM (optical mastering/burning alone prevents this), nor can the average system afford to lose that amount of RAM for temporary storage. Things making heavy use of /tmp are not always bound by access speed, especially once SSDs become more common.

The average user also can't be expected to deal with an overflowing ramdisk at /tmp when he's trying to do something as basic as burn a DVD.

---

### Post by owners4life5 on 2010-11-24
> **wilee-nilee said:**
> a built in espresso maker.

+1

---

### Post by nolag on 2010-11-25
> **czr114 said:**
> /tmp becomes less and less of a bottleneck as more and more systems adopt SSDs for system drives.
 
The solution to a slow /tmp is a fast drive, not expensive RAM.
 
As NightwishFan pointed out, /tmp can't now nor in the future be expected to fit in RAM (optical mastering/burning alone prevents this), nor can the average system afford to lose that amount of RAM for temporary storage. Things making heavy use of /tmp are not always bound by access speed, especially once SSDs become more common.
 
The average user also can't be expected to deal with an overflowing ramdisk at /tmp when he's trying to do something as basic as burn a DVD.
 
Point taken, I guess I can configure firefox and some other light weight applications to use a different file for tmp and move that to RAM.  It would increase preformance for them.  SSDs are not THAT popular yet (and still not RAM fast).  The thing I don't like about SSDs is that they don't last as long and tend to have a fixed maximum number of writes to a location on the disk (also they tend to be smaller).  
 
I do wonder if GabrielYYZ's idea is possible.  That seems even better.
 
Are there any heavy weight applications people would like to see in ubuntu.  Like common thing people with newer/higher end systems like to download or tweaks they tend to make.  This is the question I am really trying to get answered.  I would consider making a customization for this group (if I have time and there is actually people who would like to see it).

---

