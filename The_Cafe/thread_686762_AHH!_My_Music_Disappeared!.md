---
title: "AHH! My Music Disappeared!"
date: 2008-02-03
forum: The Cafe
---

### Post by BOBSONATOR on 2008-02-03
Hey guys, i have a WD 500GB External that i host all my music on, and today I turned on MPD, to find out that only there were about 10 songs in there out of 8000+ !!!!!

So I go to thunar, and go to the directory, and its all gone! all the covers are still there, just the mp3's diasapeared! 

So then i boot into windows, to see that its not there either!

What should I do?

Thanks In Advance!

---

### Post by LookTJ on 2008-02-03
Sounds your system was compromised. Did you open a ssh port to the internet?

---

### Post by BOBSONATOR on 2008-02-03
no! i dont do any ssh, i dont leave the computer on for long periods of time, maybe 5 hours the most, its my laptop

---

### Post by diskotek on 2008-02-03
damn! i2m also wondering for solution since i have same WD500GB harddrive with full of documents and music.

---

### Post by BOBSONATOR on 2008-02-03
what does this mean!?

---

### Post by Jimmey on 2008-02-03
Try ```
ls -a /mount/point/
```

If you accidentally deleted those songs, they might still be in a .Trash folder.

Check the filesystem stats on the hard drive. See if there's much space taken up.

Which filesystem is on the drive?

---

### Post by LookTJ on 2008-02-03
Also XFS filesystem can corrupt itself if it lost power.

---

### Post by ~LoKe on 2008-02-03
All your album art is there, and, let me guess, your folders as well?  Did you trash it all with Rhythmbox like I did? :lolflag:

---

### Post by Kingsley on 2008-02-03
> **~LoKe said:**
> All your album art is there, and, let me guess, your folders as well?  Did you trash it all with Rhythmbox like I did? :lolflag:
That or something similar seems like a very probable possibility.

---

### Post by BOBSONATOR on 2008-02-03
> **Kingsley said:**
> That or something similar seems like a very probable possibility.

Yes, but i havent used rythembox in the longest time, I have been constantly redoing an arch install, only using mpd + sonata

---

### Post by BOBSONATOR on 2008-02-03
omg, i just realized i removed all of my songs on songbird in windows, does that mean that it deleted all of the songs from the HD?

---

### Post by ~LoKe on 2008-02-03
> **BOBSONATOR said:**
> omg, i just realized i removed all of my songs on songbird in windows, does that mean that it deleted all of the songs from the HD?

It's probably in the Recycle Bin.

---

### Post by BOBSONATOR on 2008-02-03
nope its not...

---

### Post by Lostincyberspace on 2008-02-03
That is not good they went bye bye I think, I don't know how to recover any information from it then.

---

### Post by michaelzap on 2008-02-04
If you just deleted them, then you should be able to get most if not all of your files back:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by mips on 2008-02-04
> **BOBSONATOR said:**
> omg, i just realized i removed all of my songs on songbird in windows, does that mean that it deleted all of the songs from the HD?

It seems to be the case.

---

### Post by Wiebelhaus on 2008-02-04
Songbird owned.


Anyway....


[Recuva]("http://www.recuva.com/") Can help you restore deleted files that have not been written over , good luck.

---

### Post by az on 2008-02-04
> **sx66gns said:**
> 

[Recuva]("http://www.recuva.com/") Can help you restore deleted files that have not been written over , good luck.

That's proprietary.  You also need to pay for it to actually save your files.  The Ubuntu-Rescue-Remix works just as well and is free.

> **michaelzap said:**
> If you just deleted them, then you should be able to get most if not all of your files back:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If you need data recovery-specific help, you can ask on the ubuntu-rescue-remix help section:

[http://ubuntu-rescue-remix.org/forum](http://ubuntu-rescue-remix.org/forum)

---

