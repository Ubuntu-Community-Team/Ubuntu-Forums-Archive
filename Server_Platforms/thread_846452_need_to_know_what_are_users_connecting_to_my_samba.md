---
title: "need to know what are users connecting to my samba server"
date: 2008-07-01
forum: Server Platforms
---

### Post by Mia_tech on 2008-07-01
I have samba running on my ubuntu box, and I would like to know what files users are connected to and for how long, also I'd like to have the ability to disconnect users at the end of the day to do backups... is there any app out there that would let me do something like this?...the equivalent of "share folders" section inside "computer management" in windows xp/2003.

any help appreciated 

thanks

---

### Post by promodus on 2008-07-01
> **Mia_tech said:**
> I have samba running on my ubuntu box, and I would like to know what files users are connected to and for how long, also I'd like to have the ability to disconnect users at the end of the day to do backups... is there any app out there that would let me do something like this?...the equivalent of "share folders" section inside "computer management" in windows xp/2003.

any help appreciated 

thanks

I'm not sure how to get a report on which users, which files, and for how long.

But, I can suggest a way to get the current information. 
```
smbstatus
```
Will tell you which user is connected, what file they are accessing and how long they have accessed that file. If you're wanting a running-tally at the end of the day a script of some sort and a bit of logic could fix that. There may be other ways.

To disconnect users and do a backup? I would think that maybe stopping the samba service would be alright. I'm not sure what type of backup you're planning to do. But stopping the Samba service would ensure that no one is going to access the files while you're backing them up.

---

