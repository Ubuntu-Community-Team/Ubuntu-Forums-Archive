---
title: "Automatic Hard Drive Backup"
date: 2009-09-09
forum: Server Platforms
---

### Post by android6011 on 2009-09-09
I have a small home server that I was running with freenas for a while, but freenas had some serious performance issues. I switched to ubuntu server now here I am.

I have 2 1TB hard drives. I have looked into doing a raid before, but I just don't know if its for me. I kind of like the idea of having the data on 1 of the drives being a little older in case I delete something on accident.

What I did on freenas is a local rsync from one drive to the other every 12 hours, or manually if I know for sure data i was adding needed to be backed up immediately. 

Is rsync on ubuntu server my best bet? I think my motherboard only supports software raid anyway and I've read some not so great things about software raid. 

Any suggestions or info would be appreciated. Thanks

---

### Post by cariboo on 2009-09-09
Set up a cron job using rsync exactly the way you did when you were running Freenas

---

