---
title: "Install stuck at step 3 of  7"
date: 2010-07-04
forum: Ubuntu Moblin Remix
---

### Post by rudizle on 2010-07-04
Have been trying to install both the netbook remix and the regular desktop 32bit version of 10.04 and both get stuck at step 3 of 7 (keyboard layout). I have used the installer from the ubuntu website and unetbootin installer to throw the image into my 4gb stick, both installers same result. The image runs fine from the thumbdrive i can boot from it and do everything just fine but as soon as i try to install it permanently it freezes at step 3. Im trying to install it on a dell inspiron 6000 and on a asus Eee pc and both get stuck at step 3.

Any idea on whats going on? The 9.10 image installs just fine.

---

### Post by camorri on 2010-07-04
Did you run a md5sum check on the .iso image before you put it on the memory stick? Since it fails the same way on two different sets of hardware, I would suspect the download.

---

### Post by rudizle on 2010-07-06
> **camorri said:**
> Did you run a md5sum check on the .iso image before you put it on the memory stick? Since it fails the same way on two different sets of hardware, I would suspect the download.


I have downloaded the ISO over and over, from the ubuntu website plus from other sources and have used different images each time and still the same problem.

---

### Post by camorri on 2010-07-06
I had a look around the forum, and there are many threads like yours. 

For some people, unplugging external drives during the install fixed this type of hang. It seems the installer is out looking through the other drives. So if they are not needed during install, unplug them. 

Not sure if this may apply to you. 

See this thread. 

[http://ubuntuforums.org/showthread.php?t=1112101&highlight=install%2C+keyboard+layout](http://ubuntuforums.org/showthread.php?t=1112101&highlight=install%2C+keyboard+layout)

I also saw threads suggesting to try another keyboard layout. What layout are you choosing?

---

### Post by Memes11 on 2010-07-10
changing the layout did the trick for me. thanks

---

