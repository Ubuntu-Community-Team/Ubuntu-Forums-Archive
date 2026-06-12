---
title: "firewire capture"
date: 2006-09-13
forum: System76 Support
---

### Post by newlinux on 2006-09-13
I'm posting this in system76 but I realize this might not be system76 specific.

i have the gazelle and it has a firewire port. I want to capture output from my cable box firewire output, and my HDTV firewire output. I tried kino and dvgrab but was unable to capture anything (I just get a message saying no camera exists in dvgrab, and kino says error reading file /dev/raw1394, but it's chmod 777, so it's not a permission problem). I think these are more made for digital cameras. I tried to make sure I was trying digital unencrypted channels.  I'm pretty sure the box outputs to its firewire port, and I'm sure my tv does.

Any help is greatly appreciated, as I really don't know what I'm doing :)

---

### Post by newlinux on 2006-09-21
I tried using VLC as well just to view the capture and couldn't get that to work either. I'd really like to be able to archive the non-encrypted content from the cable box. I know people with myth do this. Do I need to install myth? Or is there a simple myth module I can install to capture firewire from a cable box?

Thanks.

---

### Post by crichell on 2006-09-21
this is an interesting one - I've never tried capturing video through firewire.  Unfortunantly I don't think I have the equipment to try it out though.

---

### Post by newlinux on 2006-09-21
Yeah, I know on windows there is a program called capDVHS that basically emulates a DVHS player and captures the output of firewire from the cable box. I also know in Myth people seem to be able to configure it to capture non 5c encrypted HD content from the firewire ports of some cable boxes, and even change the channels through the firewire input. All I'm looking for at this point is basically a linux version of capDVHS. I know it has to be out there somewhere :). I think VLC might be able to at least view it. As I have time I think I'll continue to play with it. One day though, I'll probably build/buy a mythbox, and then I will figure out how to do it through myth...

---

### Post by realitygaps on 2006-09-21
not using a system76 laptop (yet) but i found that sudo kino (or any other dv capture program as sudo instead of normal user allowed me to capture video via firewire)

hope this helps

---

### Post by newlinux on 2006-09-21
> **realitygaps said:**
> not using a system76 laptop (yet) but i found that sudo kino (or any other dv capture program as sudo instead of normal user allowed me to capture video via firewire)

hope this helps

It allowed you to capture vidoe from a cable set top box or from a camera/camcorder? If from a set tob box can I ask how (settings, procedures, anything)? I tried using kino and dvgrab with sudo and couldn't get any input from my TV firewire or cable firewire. 

Well, throughout my searches I found out about an old early stage development program called ddr1394 that apparently was discontinued, but I can't find it anywhere... I'll keep searching as time permits.

---

### Post by ddennedy on 2006-09-27
Kino and dvgrab can not capture MPEG2-TS from a cable settop box. You have to get libiec61883 from linux1394.org and compile it yourself. It contains an example utility called test-mpeg2 that can capture it. However, first you might need to tell the box to send the data using another utility it contains called plugctl: e.g.,
plugctl -n 1 oPCR[0].n_p2p_connections=1

In any case, it's all quite tricky and not tidied up into an easy to use application. Your mileage may vary.

---

### Post by newlinux on 2006-09-28
Thanks, given time I'll look into this, or maybe wait for a better solution to be developed.

---

### Post by newlinux on 2007-02-08
In case anyone cares I use mythtv to do this now. Works pretty well. Never did get anything else to work. I still would like to, but it is not as pressing of a need now...

---

### Post by hackmeister on 2007-02-08
I guest hosted Linux Reality a while back and it primarily covered Kino and I talked about getting the firewire port working correctly at the beginning:
[http://media.libsyn.com/media/linuxreality/linuxreality031.ogg](http://media.libsyn.com/media/linuxreality/linuxreality031.ogg)

This is a very good how-to:
[http://www.yourmachines.org/tutorials/kino.html](http://www.yourmachines.org/tutorials/kino.html)

as well as this:
[http://www.linuxjournal.com/article/7615](http://www.linuxjournal.com/article/7615)

As far as capturing and controlling your HDTV cable box via firewire you might want to read this:
[https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire)
[http://www.mythtv.org/wiki/index.php/FireWire](http://www.mythtv.org/wiki/index.php/FireWire)

Hope it helps

---

### Post by ziggykg on 2007-02-08
This may or may not help but I had a Canon camcorder that wasn't being recognised on my standard Edgy installation.  No amount of messing with /dev/raw1394 or similar modules helped ... until I downloaded, compiled and used kernel 2.6.19 (following a tutorial I found in the forum).  Camcorder now works with both Kino and dvgrab.

So you may want to try using that kernel.

---

