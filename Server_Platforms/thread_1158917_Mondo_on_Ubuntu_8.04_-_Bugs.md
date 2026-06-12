---
title: "Mondo on Ubuntu 8.04 - Bugs"
date: 2009-05-14
forum: Server Platforms
---

### Post by chrislynch8 on 2009-05-14
Hi,

I have used Mondo successfully on 6.06LTS but so far I have not been able to use it on 8.04LTS. 

Has anyone been able to use it on 8.04?

It gets to 82% of backing up filesystem, then stays at that until I reboot the server ( not good )

Rgds
Chris

---

### Post by jamesr on 2010-01-06
I know that this a long time from your original problem. Have you solved the problem?. I ask because I have had a similar problem which I may have solved, archiving to CDRWs does not work especially when I use verify.

---

### Post by chrislynch8 on 2010-01-08
Hi,

Thanks for the reply. No I still haven't gotten it to work. I will try the No Verify to see if that works, but if I'm backing up and entire production system I would want to verify really, but I guess I could also try to restore the system to see if it has worked

Rgds
Chris

---

### Post by jamesr on 2010-01-08
Hi Chris,

Please let me know how you get on because I will be running some additional tests this weekend.

I was able to archive and verify to an USB external HD, my complete system.  If I need to rebuild, I can burn all of the ISO's on another system to CDRW's. This is the first time recently that I have any success with the archival process.

The problem seems to be related to the /dev/name that Ubuntu has in fstab and what Ubuntu uses to call the active device, also with the way Mondo recalls the name. It did originally work until I did a kernel update. I do not believe that I was not aware of the problem immediately so the last successful backup was greater than 6 months old. This existed until I was able to spend time trying to identify the problem. I think my major clue was when I added an external USB HD box with CDRW in it and the software started talking to new CDRW device instead of the internal CDRW and this was when using gnomebaker not even Mondo.

---

