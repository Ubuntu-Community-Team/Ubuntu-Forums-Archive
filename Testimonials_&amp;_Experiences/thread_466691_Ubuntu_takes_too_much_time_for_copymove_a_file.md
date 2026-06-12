---
title: "Ubuntu takes too much time for copy/move a file?"
date: 2007-06-07
forum: Testimonials &amp; Experiences
---

### Post by sanothay on 2007-06-07
Hi all,
I don't know if some of you experienced the same thing I am at the moment. I have some .iso files sizes are about 3~4.5 GB. I have Ubuntu dualboot with win xp.
Now, for some reason I personally found it better to burn multi-sessions CD/DVD using nero on windows, but I have all of those big files on Ubuntu, therefore I have to move all those files to C:\ drive where windows could access it.
I started to move a single 4.5 BG .iso file at 10.20 AM and it is now nearly 2.00 PM but the process is still not completed!!!!
Does anyone have similar experience with ubuntu?
Best,
Cookie

---

### Post by Mazza558 on 2007-06-07
It's cos Ubuntu and XP use different filesystems. It would be the same way if you copied files from XP to Ubuntu.

---

### Post by Paul820 on 2007-06-07
It can't take all that time to move a 4.5GB file, can it? It seems a rather long time to me. There must be something wrong somewhere.

---

### Post by BlackEdder on 2007-06-07
> **Paul820 said:**
> It can't take all that time to move a 4.5GB file, can it? It seems a rather long time to me. There must be something wrong somewhere.It is probably because NTFS write support is _very_ slow. You will probably be better off if you find a linux solution (try k3b), or use a fat32 partition to transfer files, although fat32 might have a 2gb file limit (not sure about that, google will probably tell you).

---

### Post by Epilonsama on 2007-06-07
> **BlackEdder said:**
>  You will probably be better off if you find a linux solution (try k3b).

Im using right now Kubuntu and k3b is a great cd/dvd burner, it work better than Nero so sanothay try using k3b like BlackEdder said.

---

### Post by hysteresis on 2007-06-07
or you can try this program:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sanothay on 2007-06-08
Hi all,
Thanks for all your respsonses!
It is the second day now that I let Ubuntu continuously doing the move of a 4.5 GB file, and it has not finished though reached 4.4 GB already! With this, I also thought that there must be something wrong somewhere that I don't really know.
I used to try the k3b as well as the CD/DVD Creator feature embedded in nautilus on my Ubuntu, but had problem with multi-sessions disk, there was no option which I could select for the multi-sessions disk.
I have just "ctrl+c" the move of that big file and will try this: [http://www.fs-driver.org/](http://www.fs-driver.org/)
instead, hope this will work well.
Thanks,

---

### Post by 3rdalbum on 2007-06-08
There's something definately wrong - if your destination disk is NTFS, that would explain it.

Fat32 has a filesize limit of 4 gigabytes, so unfortunately your file is just a bit too big.

---

