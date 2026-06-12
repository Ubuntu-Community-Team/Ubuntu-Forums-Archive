---
title: "Gparted doesn't recognize unallocated space"
date: 2011-08-02
forum: Virtualisation
---

### Post by Ginzell on 2011-08-02
Hi all,

I have a VM on Ubuntu 11.04.  It's a XP guest and after installing iTunes I realized that I didn't allot enough HD space when I first created the VM.  So I used vboxmanage and resized the VDI. 
It seemed to work and looking at the VB settings for XP, it does show that the VDI has expanded to the size I requested. However, when I boot to HBCD and use Gparted to allocate the extra space, it still shows the original size. I've rebooted my physical machine to no avail.  
Does anyone know why this is happening and how I can fix it?  

Thanks in advance,

---

### Post by lmarmisa on 2011-08-02
I do not know HBCD. I recommend to boot your VM into an Ubuntu 11.04 Live CD (iso image), open Gparted, take a snapshot (Applications -> Accesories -> Take Screenshot) and post the image here.

I have not used vboxmanage for expanding a virtual disk. I have used [Clonezilla Live]("http://www.clonezilla.org/") (iso image) for cloning a small virtual disk into a bigger one. Finally I used Gparted to expand the NTFS partition to the new size. This method has no risk because the source disk is not modified.

Best regards,

Luis

---

### Post by Ginzell on 2011-08-03
Hi, 
I attached the SS of gparted in Ubuntu.  It's the same as it was with the HBCD (Hiren's BootCD.14.0.iso - very very handy iso to have, includes a bunch of helpful little programs all in one and I would list them here but it's way too much. Thanks to Varun for showing it to me:
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/) )

When I was researching the best way to expand my VDI, I did come across the cloning, but when I saw a second way- where I could just type in a command and expand it, that looked easier for my situation.  I have come across another piece of info on it (a little late), they say don't have Snapshots of your VM BEFORE you do the vboxmanage cmd - something about it acting "wonky" etc.  
I did have a snapshot before and didn't know it would wonky out on me, but I tried to go ahead and delete it thinking that might unwonky it :D , however after having already expanded the VDI, it gave me an error.  So I'm thinking this may be the whole reason I cannot get the extra allotted space to show up in Gparted. I've been researching how to get that Snapshot off of there now.

---

### Post by Ginzell on 2011-08-03
Ok, I fixed it.  Finally..after messing with it all night.  It was an easy fix once I got it.

To sum it up:
Gparted wasn't recognizing the extra space because of the snapshot. You cannot resize the VDI when there is a snapshot, and after I had resized using the vboxmanage cmd, I was unable to delete the snapshot. So what I did was went back in and restored the VM from that "pre-modifyhd" snapshot.  (Thank goodness I didn't delete it from the outside in Nautilus &trash) Then booted to make sure all was good.  It was, then went back and deleted that darn snapshot.
Went into Gparted and there was the extra space! Yay! :D
I resized my main partition to use that unallocated space and then rebooted.  XP booted and went through it's little check disk thing that it does and now I have my VDI expanded! 
Also, I didn't have to resize again because it kept the bigger size, and it was nice because it also kept the iTunes backup that I had made - after the snapshot - and I had deleted so much stuff trying to grab extra space that I deleted things I really needed, (like QuickTime and bon something or another - I didn't know you needed that to run iTunes ha!) but upon restore - it was all back.  It was like - Linux knew what I was trying to do.  Makes me love it all the more! 
All that just because of a silly snapshot! 

So, to easily add space to your VM VDI in the current version of Sun VirtualBox using the vboxmanage cmds:
DELETE SNAPSHOTS!!
On host terminal :
```

vboxmanage modifyhd "VirtualBox VMs"/WinXP/WinXP.vdi --resize 40000 
```(VirtualBox VMs should be the dir your vdi is in) 
To add 5GB to your 10GB VDI, code would be: --resize 15000.

Now I can get on with it!!

---

### Post by varunendra on 2011-08-06
Nice description! Looks like you're on your way towards writing 'linux/VBox tutorials' ;)
By the way, don't forget to create another snapshot as it is very useful at times - especially for a test VM. I also use to just make a compressed backup of the entire VM folder when the VM is fresh and complete with stuff I need to have in it (only software, not user-data). Typically, a 2GB XP VM (complete with essential software) gets compressed to approx 380-400 MB in size (in 7zip format). A fresh VM - just in case I need one! :)

Thanks for sharing your experience, much appreciated!

---

### Post by Ginzell on 2011-08-06
I just hope that maybe this post can help someone else out that might end up in the situation I was.  It took a LOT of research to find out all this stuff, maybe I was just looking in the wrong spot but it was in no way easy to find.  That's why I gave so much detail of my experience.  There are some things I've been thinking about putting up on YouTube - short tutorials.  Now that I've fixed my webcam I may just do that!  :D

Thanks for the info, I'm going to go and compress several things because I'm beginning to run out space on my physical hard drive.  And if I decide to do videos - I will definitely need some room for it.  Or...maybe I'll just grab an external hard drive.

---

### Post by hosk on 2011-08-11
Hey Liz,

Wanted to let you know your post helped me. I couldn't get GParted to see the extra space I had free'd up in the VDI. I suspected it might be the snapshot but your post confirmed it, thanks!

edit: for posterity, the answer was probably somewhere in

[http://forums.virtualbox.org/viewtopic.php?p=29276](http://forums.virtualbox.org/viewtopic.php?p=29276)

but i didn't read very thoroughly

---

