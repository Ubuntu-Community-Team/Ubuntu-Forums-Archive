---
title: "Dead ubuntu, backing up files permissions"
date: 2009-06-02
forum: Security
---

### Post by lordhaworth on 2009-06-02
Hi all,

I am (was) running ubuntu hardy heron and it recently died. The login screen keeps refrshing itself up to the jungly drum sound which is quite annoying and I cant login.

Anyway I opted to back up my files and start again with intrepid and a fresh install.

To do this  am running ubuntu from a disk and going to copy my important files over to usb. 

THe issue I am having is that the usb is seen as read only and Im not sure how to get around this. I've tried
 
    sudo cp etc....

I get 

    "cannot create regular file" ... "Read-only file system"

Im assuming the issues I am having are because I'm running off a live disk. I could really do with backing a few of these files up!

If anyone can help me change the permissions on the usb stick W would much appreciate it!

---

### Post by lordhaworth on 2009-06-02
Note that I cannot see the permissions in properties

---

### Post by MichaelSammels on 2009-06-02
Try using something like:

```
sudo chmod 777 <filename>
```

Or try this:

```
sudo chown $USER:$USER -R <foldername>
```

to change the folder owner.

---

### Post by lordhaworth on 2009-06-02
Oh yeah!

After a lot of faffing (I had to reformat my pen drive too!)

The first one seems to have worked!!!!!!

Absolute genius!

Ubuntu forums... probably the best on the web

Cheers

---

