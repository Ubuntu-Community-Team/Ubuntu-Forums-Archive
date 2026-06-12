---
title: "Encrypted backup to a NAS server"
date: 2009-05-08
forum: Security
---

### Post by modmadmike on 2009-05-08
I need to backup my files to a NAS unit [A netgear ReadyNAS which runs linux and I can ssh into]. I plan to use rsync. On the host I have Full-Disk-Encryption to keep people [ie: my dad] out of my files. Can I setup a  encrypted folder on the share using ssh and then backup to there? Is it even worth it with the fact that rsync is not encrypted? Can I tunnel the rsync job through ssh?

---

### Post by wirelessmonkey on 2009-05-08
Yes, you can tunnel rsync through ssh.

---

