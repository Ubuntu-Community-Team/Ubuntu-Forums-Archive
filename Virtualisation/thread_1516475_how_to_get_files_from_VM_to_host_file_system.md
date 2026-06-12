---
title: "how to get files from VM to host file system?"
date: 2010-06-23
forum: Virtualisation
---

### Post by schwim on 2010-06-23
Hi there everyone,

I've installed VirtualBox OSE on my Ubu 10.04 machine and installed Win XP(sp3) on it with plans to install iTunes so I can get a few albums that aren't available elsewhere.  I'm going to try following[ this wiki]("http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux") in an effort to convert the iTunes songs into mp3's.

I've got XP installed(and iTunes), but before I purchase any music, I wanted to make sure I could easily get the files from the xp vm to the host file system.  Searching isn't netting me anything, I suppose because I'm missing something that's incredibly simple.

Any help would be greatly appreciated.

thanks,
json

---

### Post by VinoFuriaRoja on 2010-06-23
Im in the same boat...not to hijack your thread!  But I want to know how to access the files from the C Drive on my virtualized Windows OS (using Virtualbox) from my Host OS (10.04).  Any help would be appreciated!

---

### Post by schwim on 2010-06-23
Hehe, I don't mind the hijack if it gets us an answer :)

As a temporary fix, I used ftp to put the files on a remote server and then downloaded them in the host system... way crappy, but works until I figure out how to handle it properly.

---

### Post by VinoFuriaRoja on 2010-06-24
I suppose dropping the files in to a cloud storage system like Dropbox might work too. Still searching for an answer....

---

### Post by VinoFuriaRoja on 2010-06-24
bumping this...can someone please help?

---

### Post by schwim on 2010-06-24
Hi there Vino,

It looks like you and I are on our own(happens a lot to me :) ).  Luckily, I fumbled around enough to get it working.

Surprisingly(to me anyway), there is no way to simply pull files from the vm.  It's it's own OS, and it acts like it in all respects.  What they want you to do is to set up a network share.  The virtualbox dudes have really simplified it, however.  Following [this tutorial]("http://www.tomshardware.com/reviews/xp-mode-ubuntu,2434-6.html"), I was transferring files between the two operating systems in under 5 minutes.

Something he doesn't tell you to do before you start this:  Create a folder and share it under your home in Ubuntu and then create the share under "Devices" at the top of the window housing your VM install.  You'll use it later.

The part where he says to follow the links he clicks exactly is good advice.  My menu was slightly different, so I was having problems finding the shared folder I had crated in my Ubu install.

After finding the shared folder in the network places, I mapped it as a drive and set it to connect at startup.  This way, I can just drag files to drive z:.

I hope this gets you up and running.

thanks,
json

---

### Post by VinoFuriaRoja on 2010-06-24
Thanks alot for the direction.  I actually found a simpler way, and I dont know why I didnt think of this before.  

I created a "Share" file in my "Home" on Ubuntu.  Then I started up the Windows OS in VB and went to "My Computer on the Start button.  I right clicked on "My Computer" and selected "Map Network Drive".  Then I selected Browse and went to the Virtual Box Shared Folders and clicked on that.  

Then I clicked on   \\Vboxsvr, then \\Vboxsvr\Share, and then OK.  Then I clicked FINISH and voila!  The share on \\Vboxsvr showed up under Network drives.  Piece of cake! But thanks for putting my head in the right direction.  Again, I don't know why I didn't think of this before. 


Probably should put this as SOLVED

Vino

---

