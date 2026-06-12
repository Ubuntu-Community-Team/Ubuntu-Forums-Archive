---
title: "samba and a new harddrive"
date: 2007-02-14
forum: Server Platforms
---

### Post by StOnE LiBeRaTiOn on 2007-02-14
I just installed ubuntu server on my one computer I use at home for a server.  I used to run plain debian, but I decided to try out ubuntu.  When I installed ubuntu, I also installed a new 320gig ide hard drive.  I installed ubuntu onto the already existing 40gig drive.  So what I am trying to do now is create a samba file share server for everyone in my house.  (music, movies, pictures, ect...)  I want to basically have the 320 gig hd as pure storage, and use the other harddrive (main) for only running the os, plus a few other services I run. (ventrilo, steam servers, ect...)  So my question is, where do I find the harddrive?  is it already mounted?  Do I have to mount it manually ever time I restart the server?  haha, i'm still pretty new...

thanks

---

### Post by Brazen on 2007-02-14
type this:```
ls /dev/
```
and post the output.

---

### Post by StOnE LiBeRaTiOn on 2007-02-14
it looks like the output fills more than the screen.  ummm im guessing what you're looking for is....

hda
hda1
hda2
hda5
hdb
hdb1
hdd

---

### Post by StOnE LiBeRaTiOn on 2007-02-14
Don't worry... got it figured out... hard drive was in media/hdb1

one more question while I have this thread going... How do i get ssh working?  When i try and connect to my server, it says connection refused.  This never happend with debian.  It's probaly a quick fix, any one know how?

---

### Post by Brazen on 2007-02-15
> **StOnE LiBeRaTiOn said:**
> Don't worry... got it figured out... hard drive was in media/hdb1

one more question while I have this thread going... How do i get ssh working?  When i try and connect to my server, it says connection refused.  This never happend with debian.  It's probaly a quick fix, any one know how?

The harddrive could have been sd* or hd*.  I just figured if you post the output I could help you go through it, but you got it figured out so good.

Have you installed ssh server?  The command is:```
sudo apt-get install openssh-server
```

After it is installed, it should pretty much "just work".

---

