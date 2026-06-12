---
title: "After unknown technical faults, I've moved from Fedora 21 to Debian 8"
date: 2015-10-09
forum: Ubuntu, Linux and OS Chat
---

### Post by jeff127 on 2015-10-09
I was experiencing some issues with flash drives on F-21. Transfer would take forever, then I'd select "eject" or "power off device" and it'd stall forever claiming it still needed to write data, even when "file transfer operation" had disappeared. I tried to log into terminal using "su" (I wanted to find which process was using the flash drive) ... but the terminal stalled. I was very frustrated so I moved to Debian and I'm pleased with its improvements. A few years ago Debian shipped with the equivalent of Firefox version 4. Now they have Ice Weasel 38.3 - I know I know it's full of security holes, that's why I only use it for trustworthy sites. I steer well away from trash like Tumblr, which is full of viruses, even Chrome has warned me at times that Tumblr pages are trying to download scripts, I reported these accounts as malicious and Tumblr deleted them haha! My bank website doesn't complaint about Ice Weasel 38.3 thank goodness for that, Ice Weasel is now modern enough to meet most website standards!

Anyway side issues aside... Debian 8 is pretty good so far. It shuts down in about two seconds and this version of Ice Weasel is much faster than firefox version 40.x which exists in Fedora.

Linux is still frustrating. I don't understand why we still have issues with flash drives, like the annoying** .Trash** folder that hogs all your drive space. Also I read that you shouldn't format EXT3 and EXT4 onto a flash drive because "journaling" filesystems cause more wear. I might format my flash drives to FAT32 instead. There must be mkfs.fat32 or similar. I just don't care right now, all this Linux is draining my energy, and I've used Linux for 9 years (since around 2006/2007). I hope that Debian will be reliable enough for my high standards.

---

### Post by monkeybrain20122 on 2015-10-09
> **jeff127 said:**
> 
Linux is still frustrating. I don't understand why we still have issues with flash drives, like the annoying** .Trash** folder that hogs all your drive space. Also I read that you shouldn't format EXT3 and EXT4 onto a flash drive because "journaling" filesystems cause more wear. I might format my flash drives to FAT32 instead. There must be mkfs.fat32 or similar. I just don't care right now, all this Linux is draining my energy, and I've used Linux for 9 years (since around 2006/2007). I hope that Debian will be reliable enough for my high standards.

Fedora is kind of buggy sometimes because it is a beta testing distro for Redhat. Mostly it works but sometimes it can be flaky. I have never had problems like those you described on Ubuntu (or fedora for that matter)

---

### Post by jeff127 on 2015-10-09
Thanks for that info, I thought it was a stand-alone product that was properly tested! Just in case I want it again, I have Fedora 22 on DVD, which I can "FedUp" to Fedora 23 if needed, but based on experience: newer equals worse LOL. I had no idea that it was unstable. I used to run the 6-month releases of Ubuntu until I realised what a dumb idea it was. Right now, I have the latest Xubuntu on my netbook and I can't install things like Web (formerly known as Epiphany) because it has dependencies that I can't get on that particular release. We should reject this unstable stuff, it's insanity!

---

### Post by monkeybrain20122 on 2015-10-09
Well I have Fedoea 22 dualbooting with Ubuntu 15.04 at the moment. The graphic driver (intel) is kind of broken on the Fedora side, gnome shell crashes whenever I play video with hardware decoding. Someone has filed a bug and it is claimed to be "fixed", but I doubt that the fix will come to F22. Maybe in F23. IIRC it seems to be a gnome shell bug so if you run other DEs it may be OK.

Debian stable is very stable, but also very old and hardware support may not be that great out of the box (you may have to install a lot of non free stuffs yourself) Some people run Debian unstable, but I find it even more unstable than Fedora, a lot more. So maybe Debian testing is the one to go if you stay with Debian. Software in "testing" is also kind of old, just not as old as in stable :)  I find in Ubuntu the happy balance, where the system is stable but I can also get the latest and greatest software from ppas. I don't know what dependencies you are missing for epiphany. Someone may be able to help you out if you post a thread on the support forums.

---

### Post by buzzingrobot on 2015-10-09
Linux creates a hidden '.trash' folder in the home folder of each user. So, if you run Linux off a USB drive, there will be a .'trash' folder in your home directory.  That how Trash works.  When you click to put something in the Trash, it's moved to that hidden folder, When you empty the trash, the files in that hidden folder are deleted. Trash functions n Windows and OS X work the same way,

If files are deleted rather than moved to Trash, then the size of the .trash folder will not increase. Of course, deleted files are just that... deleted.

---

### Post by buzzingrobot on 2015-10-09
> **monkeybrain20122 said:**
> Well I have Fedoea 22 dualbooting with Ubuntu 15.04 at the moment. The graphic driver (intel) is kind of broken on the Fedora side, gnome shell crashes whenever I play video with hardware decoding.

Gnome on F22 on Haswell and YouTube videos and such were fine here, but, admiittedly, I have no clue if I was using anything with hardware decoding. 

My experience with Fedora has always been that the more I added "foreign" non-FOSS drivers, codecs, and such, the greater the chances for problems. This makes sense to me because Fedora, as a Red Hat project, is FOSS-only.  it's the nature, the purpose, of Fedora to see frequent change and updates, and that increases the odds for problems arising from foreign code that is not keeping pace. I avoid proprietary video drivers and install only the codecs I know I need to support Pithos and Radiotray.  I do create an Adobe repo file and install Flash, and then set it to "Ask to Activate".

I wouldn't recommend Fedora for recent Windows migrants or anyone else who just wants to use a PC without being bothered by frequent updates, potential driver issues, and things like that. Fedora's target audience is obviously not that kind of user.  I would recommend it for someone who knows how Linux works and who wants access to developing, but tested, technology on a fixed release distribution, rather than diving into a rolling release.

Fedora follows a 6-month release cycle, like Ubuntu, without an LTS, unlike Ubuntu. Releases are supported for one month after the release of the second succeeding release, so about 13 months. A conservative approach would see a Fedora user update to the next release in the sequence about a month before the second succeeding release comes out. E.g., Fedora 23 is due for release later this month, so a Fedora 21 user might update to Fedora 22 now.  Then, 6 months later as F24 release approaches, move to F23.

---

### Post by monkeybrain20122 on 2015-10-09
> **buzzingrobot said:**
> Gnome on F22 on Haswell and YouTube videos and such were fine here, but, admiittedly, I have no clue if I was using anything with hardware decoding. 
.

Using vaapi would kill the desktop right the way (vlc,  mpv and gstreamer-vaapi all exhibit same behaviour). It appears to be a gnome shell and/or mesa bug (though I did not experience it in Ubuntu with standard version or Oibaf's ppa) Got Mesa updated last night but haven't booted back to check if it solved the problem. Nowadays I seldom boot into it since the touchpad is not working properly (edge scrolling not working, two finger scrolling is jumpy), the thing is barely usable, some bug in libinput apparently.

Edited:I fixed the touchpad. Turns out synaptic driver is not loaded  because the config file is in wrong location, need to copy it and then  write a script to enable vertical scrolling. But vaapi still kills the desktop.

---

