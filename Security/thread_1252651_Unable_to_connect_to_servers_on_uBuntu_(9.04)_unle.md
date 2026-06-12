---
title: "Unable to connect to servers on uBuntu (9.04) unless logged on locally"
date: 2009-08-29
forum: Security
---

### Post by brno223 on 2009-08-29
Until recently I could start the computer on which I run uBuntu 9.04, leave it at the local logon screen, and connect via my LAN to the SSH, Samba and FTP servers. But following recent updates I can't connect to any of the servers on the uBuntu machine unless I have logged onto it locally.

I guess that a way round this is to auto-logon the computer at start-up but I'd rather not do this as it would leave the computer 'open'. Is there any way in which I can re-configure uBuntu so that I can access servers *without* first logging on locally?

I can't identify which update has apparently caused this change in behaviour but I think that it was applied within the last 7-10 days.

TIA,

Steve

---

### Post by slakkie on 2009-08-29
Configure your network via /etc/network/interfaces, rather then relying on a network manager.

---

### Post by Rob_H on 2009-08-29
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1225436](http://ubuntuforums.org/showthread.php?t=1225436)

---

### Post by brno223 on 2009-08-29
> **Rob_H said:**
> Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1225436](http://ubuntuforums.org/showthread.php?t=1225436)

Thanks! The answer was in there: nothing to do with updates, my network connection was not available to all users. I did search for problems similar to mine but missed that thread :redface:

Thanks again.

---

### Post by bodhi.zazen on 2009-08-29
> **brno223 said:**
> Thanks! The answer was in there: nothing to do with updates, my network connection was not available to all users. I did search for problems similar to mine but missed that thread :redface:

Thanks again.

That "trick" is a recent discovery for me in network manager (I do not use network manager much) but it has been a life saver.

---

