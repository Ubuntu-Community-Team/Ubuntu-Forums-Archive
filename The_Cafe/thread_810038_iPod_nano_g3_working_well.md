---
title: "iPod nano g3 working well"
date: 2008-05-27
forum: The Cafe
---

### Post by morticul on 2008-05-27
I've been searching all over the place for a solution to my iPod problem. While in fact it was ridiculous. So I'm just posting this in case it is of any use to anybody. 

The solution is just to add yourself the the "disk" group, logout and login et voilà...

The story goes like this... 

Just bought a new iPod nano G3 and I'm unable to put songs into it. Well I'm able to but when I unplug it, the iPod don't see any song. I noticed that when I "safely remove" it, I get a message telling me that it can unmount but can't eject. Searching the web to see what does "eject" mean, I fall on threads that tells that eject is for cd or dvd and that you don't want to eject your iPod because it could be harmful if you stand in front of it (of course they were not serious). 

Well as they were saying that ejecting an iPod was useless I juste moved on to the next possible problem. Found threads talking about problem with libgpod and iPod G3. I was pretty sure that was the problem... but in fact no... the problem was with libgpod2 and we are now at libgpod3 and the problem is solved...

I finally try sudo eject /dev/sdb1 to realize I was able to properly eject... But still... it took me hours to realize that it was the solution to my problem. So the problem is only a permission problem... playing around, I found out that you just need to add yourself to the "disk" group but don't forget to logout and login.

All this work for a problem as simple as this... hmmmm not really happy ;)

---

### Post by Scalez13 on 2008-05-27
Okay.... how do you go about adding yourself to the "disk" group?

---

### Post by morticul on 2008-05-27
here is a thread that talk about non GUI methods

[http://ubuntuforums.org/showthread.php?t=662961]("http://ubuntuforums.org/showthread.php?t=662961")

In KUbuntu, I use the *kcontrol* GUI and then I select the *user management* pane. In *administrator mode*, I *modify* my user to add *disk* in the *Privileges and Groups* tab

---

### Post by Scalez13 on 2008-05-27
awesome. thanks.

---

