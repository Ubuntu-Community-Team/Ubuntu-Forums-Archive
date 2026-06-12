---
title: "No encrypted DVD playback... Hardware issue?"
date: 2009-05-03
forum: System76 Support
---

### Post by matthekc on 2009-05-03
I have had my system 76 for less than a year when I was running linux Mint 8.04 it just stopped playing encrypted DVD's. I have tried several distros including Ubuntu with medibuntu repos. 
    I believe that the DVD drive may be at fault.  I haven't found my receipt but I was hoping perhaps I could send it in for warranty work.

---

### Post by Lee_Machine on 2009-05-03
Make sure libdvdread4 is installed via Synaptic, also have you tried using VLC?

I find VLC the best program for watching CSS encrypted DVDs. 

If you can use your optical drive for everything else, then that rules out hardware.

---

### Post by matthekc on 2009-05-03
Linux Mint does have all the software for playing dvd's out of the box.  I have tried Vlc and several other players. My machine did play encrypted dvd roms then in the middle of an install it just quit. I have another machine much older with the same software that does play dvds. 
I have done every test I can think of short of buying an external dvd rom player.  I know it sounds crazy for hardware to fail like this I wouldn't even have believed it possible before but I think it is what happened

---

### Post by Lee_Machine on 2009-05-03
I personally would purge and re-installed libdvdread, along with VLC.

Are you trying more than one DVD?

In the middle of an install? Like System updates? Installing an App?

---

### Post by matthekc on 2009-05-03
:) You know the part where the Dell support guy in India asks you to make sure the machine is plugged in...

> I personally would purge and re-installed libdvdread, along with VLC.

Are you trying more than one DVD?

In the middle of an install? Like System updates? Installing an App? 

Yes I have done more than one install I configured Ubuntu and Debian to play DVD's on this machine.  Tried several versions of Linux mint Uninstalled and reinstalled libdvdcss2, libdvdread 3 and 4, VLC, some other players, etc.

I have encrypted dvds that won't work a lot of them and a few unencrypted ones that do work like a SNL disk of Adam Sandler.

I though maybe it was an updates thing at first to but I've tried too many distros and configurations to think that anymore.

I suppose I could get an external cdrom dvdrom to test with my sister needs one anyway. I could give it to her when I'm done testing but I would prefer not to.

---

### Post by jdb on 2009-05-03
> **matthekc said:**
> :) You know the part where the Dell support guy in India asks you to make sure the machine is plugged in...



Yes I have done more than one install I configured Ubuntu and Debian to play DVD's on this machine.  Tried several versions of Linux mint Uninstalled and reinstalled libdvdcss2, libdvdread 3 and 4, VLC, some other players, etc.

I have encrypted dvds that won't work a lot of them and a few unencrypted ones that do work like a SNL disk of Adam Sandler.

I though maybe it was an updates thing at first to but I've tried too many distros and configurations to think that anymore.

I suppose I could get an external cdrom dvdrom to test with my sister needs one anyway. I could give it to her when I'm done testing but I would prefer not to.

This post talks about a region that is set in the drive's firmware.

[http://bbs.archlinux.org/viewtopic.php?id=68280](http://bbs.archlinux.org/viewtopic.php?id=68280)

Be careful, it warns that:

"Most drives only allow you to change the region code 5 times before it is locked forever, so be cautious when changing your region code."


jdb

---

### Post by matthekc on 2009-05-03
Thanks jdb that was it...
I knew it wasn't my Linux config but I would never thought to check my region setting.  I thought it would be a cooked chip in the drive.

How does a firmware setting like that just change because it was right at one time?

---

### Post by jml on 2009-05-04
I believe that if you insert a DVD from another region, the computer will "offer" to change the DVD drive to support that region.  (That's what I did when I dedicated an old laptop to playing Region 2 DVD's for my daughter.)  Can't say for certain that that is what happened, though.  Glad you got your drive back.

Joe

---

