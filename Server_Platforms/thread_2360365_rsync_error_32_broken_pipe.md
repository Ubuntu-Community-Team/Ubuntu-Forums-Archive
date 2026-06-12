---
title: "rsync error 32 broken pipe??"
date: 2017-05-03
forum: Server Platforms
---

### Post by bosscheesemo on 2017-05-03
Hello Everyone! I need some help. I'm setting up my Ubuntu Server to sync my mp3 files over a network. I need it to pull files from my laptop and store them on my external hard drive. However the sync keeps failing with an error and I can't figure out why. The remote drive is a 'My Book' external drive with a shared file on it.

Here is the sync code that I am running:

<rsync -arsvzPn  josh@192.168.1.101:'/home/josh/Music/Sync\ Test\ Local/' /media/josh/My\ Book/My\ Network\ Storage/SyncTestRemote>

Here is the error that I'm getting:

<receiving incremental file list
rsync: change_dir "/home/josh/Music/Sync\ Test\ Local" failed: No such file or directory (2)

sent 8 bytes  received 106 bytes  76.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1655) [Receiver=3.1.1]
rsync: [Receiver] write error: Broken pipe (32)>

What am I doing wrong, or what am I not seeing? Thank you very much for your time.

---

### Post by wildmanne39 on 2017-05-03
*Thread moved to **Server Platforms**.*

---

### Post by dragonfly41 on 2017-05-04
I'm not a frequent user of rsync commands but I'm guessing that the command should look like this ..

```
[COLOR=#000000]<rsync -arsvzPn [/COLOR]**[COLOR=#ff0000]'[/COLOR]**[COLOR=#000000]josh@192.168.1.101:/home/josh/Music/Sync\ Test\ Local/' [/COLOR]**[COLOR=#FF0000]'[/COLOR]**[COLOR=#000000]/media/josh/My\ Book/My\ Network\ Storage/SyncTestRemote[/COLOR]**[COLOR=#FF0000]'[/COLOR]**[COLOR=#000000]>
```

note where the single quotes are placed ..

Why not use Grsync (gui) in dry run mode to test your commands?


[/COLOR]

---

### Post by bosscheesemo on 2017-05-07
I figured out what was wrong. No quotes are needed at all.

correct syntax is as follows:

[COLOR=#000000]rsync -arsvzPn [/COLOR][COLOR=#000000]josh@192.168.1.101:/home/josh/Music/Sync\ Test\ Local/ [/COLOR][COLOR=#000000]/media/josh/My\ Book/My\ Network\ Storage/SyncTestRemote[/COLOR]

---

