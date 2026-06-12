---
title: "VirtualBox version 5.  Dark screen."
date: 2015-07-11
forum: Virtualisation
---

### Post by ajgreeny on 2015-07-11
I have just uninstalled VBox 4.3.28 to try the version 5 that I found today on the Oracle site [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) but have been totally unsuccessful as screen brightness is at about 20% of normal.

Everything seems to run and install OK including the updated Guest additions and the VMs all start and run fine, but it leaves them totally unusable as they are far too dark, so I have had to uninstall VBox v5 and go back to 4.3.28.

Anyone else found the this new version and installed it, and if so, has it worked OK for you?

---

### Post by v3.xx on 2015-07-11
I think I'll just lock my version for now and see how this plays out.

Sounds like the same screen brightness you get when pause is used.

---

### Post by ajgreeny on 2015-07-18
Six days on from my original post and just for ther hell of it I tried VBox 5 on an older Compaq CQ70 laptop with dual core Intel CPU and only 2GB ram.  On that machine the exported VM of WinXP from my desktop, where I see that dark screen, is working absolutely correctly.

I assume therefore that the problem must be more to do with a hardware incompatibiltiy rather than a specific VBox 5 problem.  The VBox forum does not give me any clues either so I am not sure what is going on with my desktop machine.

---

### Post by grepster on 2015-08-23
If you are using compton, see [this thread]("https://forums.virtualbox.org/viewtopic.php?f=7&t=68896&p=328269&hilit=full+screen&sid=163fe0f5559c7b48295cb5708a77a0ec#p328269")

grepper

---

### Post by QIII on 2015-08-23
Please don't use URL shorteners like tinyurl.  Use the full URL.  To save space, you can always use the link functionality in the buttons above the text entry box like [this]("http://ubuntuforums.org").

That way people can hover over the link to see what it is without fear of being directed to some random, undesirable destination.

Thanks.

---

### Post by ajgreeny on 2015-08-29
> **grepster said:**
> If you are using compton, see [this thread]("https://forums.virtualbox.org/viewtopic.php?f=7&t=68896&p=328269&hilit=full+screen&sid=163fe0f5559c7b48295cb5708a77a0ec#p328269")

grepper
Oh. WOW!

Thanks so much for that; a bit belated but heartfelt, nonetheless.  I had searched the VBox forum without success.

I had not even considered that it might be something so simple as compton and had not considered that the laptop that I used VBox 5 on with success is using the inbuilt XFCE compositor, not compton, and because I always run my VMs fullscreen I was not even aware that in windowed mode all was as it should be on my desktop as well.

I've just edited my .compton.conf to include that line and updated to a now fully working VBox 5.

I'm a very "happy-chappy" so thanks again for finding that.

---

