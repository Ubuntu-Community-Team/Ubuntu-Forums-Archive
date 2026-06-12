---
title: "Remmina not working in 13.04?"
date: 2013-02-18
forum: Ubuntu Development Version
---

### Post by laborg on 2013-02-18
Hi!

Since updating to 13.04 I can't connect to a Windows 7 pc anymore (same wifi, rdp). 
* Connections from 12.10 to the windows machine are possible (tried with a different computer).
* Connections via CLI and rdp are also possible.

Could someone confirm this problem I've got with Remmina bevor I report a bug?

EDIT: As a poster mentioned the solution was to delete .freerdp directory!

Thx,
Gerhard

---

### Post by dino99 on 2013-02-18
reconfiguring it or purging then reinstalling it maybe can help; sorry i never use that app.

---

### Post by laborg on 2013-02-18
> **dino99 said:**
> reconfiguring it or purging then reinstalling it maybe can help; sorry i never use that app.
Thx, but I already tried that with no success.

---

### Post by howefield on 2013-02-18
Just tried it, loaded Remmina, connected to my Windows 7 machine and connected straight away.

No issues.

Can't offer any clues other than is your machine fully updated ?

---

### Post by cariboo on 2013-02-18
Seeing as you didn't do a fresh install, there are more than likely some settings files that contain the wrong information. Can you remove the ~/.freerdp/known_hosts file, and try to connect to a Windows 7 system again?

---

### Post by celluloid on 2013-02-18
Weird - are you getting any specific error message?
I use Remmina daily for my job - including the NX plugin and connect to over two dozen RDP & NX clients including RDP through SSH tunnels - with no problems at all.

---

### Post by laborg on 2013-02-19
> **cariboo907 said:**
> Seeing as you didn't do a fresh install, there are more than likely some settings files that contain the wrong information. Can you remove the ~/.freerdp/known_hosts file, and try to connect to a Windows 7 system again?

Thanks, that solved my problem! A proper error message would be nice for such a case.

---

