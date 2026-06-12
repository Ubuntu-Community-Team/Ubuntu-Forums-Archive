---
title: "VirtualBox and shared folders"
date: 2011-01-01
forum: Virtualisation
---

### Post by graphikeye on 2011-01-01
Hi,
I've set up virtualbox successfully and it works well. 
However, when it comes to setting up shared folders, I am at a lost. I've tried everything in the documentation but nothing seems to work. 

My host: Ubuntu 10.10
Guest: Windows 7

I've added a shared folder in Vbox called FANTOM.
However, when I try to mount it in DOS using: 

net use x:\\VBOXSVR\FANTOM

it says unable to connect to network. I'm not sure how to determine what the drive letter should be (maybe it's not 'x').

Any help would be appreciated. Thanks in advance.

---

### Post by karthick87 on 2011-01-01
Have you installed Guest Additions?

[http://ubuntu-tutorials.com/2010/09/08/install-guest-additions-on-ubuntu-10-10-beta-workaround/](http://ubuntu-tutorials.com/2010/09/08/install-guest-additions-on-ubuntu-10-10-beta-workaround/)

---

### Post by graphikeye on 2011-01-01
I figured out a workaround. I had set up network sharing using samba from UBuntu host. The Windows guest was able to see the folder, but whenever I tried to open it it would ask for a guest and password on the VBOX-PC domain. I had no clue what that meant and nothing I tried worked. Finally, I gave root a shot and lo and behold, all my files appeared. So thanks.

---

### Post by b0b138 on 2011-01-01
you need to have a space between the drive letter and share name
```
net use x: \\VBOXSVR\FANTOM
```

---

### Post by graphikeye on 2011-01-01
hey that worked! Thanks! I'll have to read up on how 'net use' works.

Thanks!

---

### Post by karthick87 on 2011-01-02
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

