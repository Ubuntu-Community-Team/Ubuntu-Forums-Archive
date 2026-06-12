---
title: "Streaming and Samba help"
date: 2013-09-08
forum: Server Platforms
---

### Post by Henry_Sinclair on 2013-09-08
Ok so i have samba for file share in my house but it only works on my MacBook Pro and not my parents MacBooks. How do if fix that, btw i uninstalled samba. Also I would like to stream video to my Xbox and to stream over the internet for our computers (same with music). Is any of this possible?

Server specs:
AMD Athlon x64 2.2GHz
4GB RAM
1TB HDD
56MBPS internet

---

### Post by TheFu on 2013-09-09
Yes, it is possible, however, I don't know anything about xbox limitations. Doesn't it only support very specific video formats? To playback almost anything, a transcoder is needed. Something like ps3mediaserver, I should think.

You'll need to provide more details about the network and software setup if you'd like any help.  For the Mac-side, I'd suggest that you ask on Mac-specific forums. My last use of a Mac was about 18 months ago. At the time, there was a bug in their smb/cifs protocol, so it was impossible to connect to samba shares. After two weeks on "linux-lite" and driving myself crazy with all the differences, I gave the Mac away.

---

### Post by SeijiSensei on 2013-09-10
Adding support for the deprecated [AppleTalk](https://help.ubuntu.com/community/AppleTalk) protocol may help with your parents' machines.

---

