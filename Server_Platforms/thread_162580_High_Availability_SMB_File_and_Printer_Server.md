---
title: "High Availability SMB File and Printer Server"
date: 2006-04-19
forum: Server Platforms
---

### Post by rverrips on 2006-04-19
Hi

I need to create a high-availablity file and printer server for a network of windows 2000/XP workstations (approx 1000 or so) - I have three IBM HS20 (i.e. Xeon based) blade servers and a SAN connected with fibre for the actual storage (approx 1TB)

High-availablity is required 'cause all user files, roaming profiles, etc. are stored on the server, and when the server drops all workstations are unusable.

It's been planned to use a three way Windows 2003 Enterprise Server connecting to the SAN

Anyway Ubuntu+SAMBA solution I could look into as an alternative to this, or is it not quite enterprise ready yet?

Thanks

Roy

---

### Post by xerophyte on 2006-04-19
You can setup but you need reliable shared storage, then cluster any node with heartbeat + AFS (on a reliable storage) 

hope that helps 

some resources 
[http://lcic.org/index.html](http://lcic.org/index.html)
[http://linux-ha.org](http://linux-ha.org)

---

### Post by LordHunter317 on 2006-04-19
What was your specific intended Windows 2003 configurations?  It's hard to advise without details.  If you intended to just run 3 independent blades clustered off the same file-share, it might be able to replace that if you use GFS or OCFSv2.  I don't have a lot of experience there, so it would be something I'd take the time to test first and research.  If you have needs to use Volume Shadow Copy, DFS, or virtually anything else, it's a no-go.

---

