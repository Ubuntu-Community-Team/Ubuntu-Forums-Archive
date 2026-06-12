---
title: "backup to Ubuntu 10.04 file/print server"
date: 2010-09-30
forum: Server Platforms
---

### Post by jquis8411 on 2010-09-30
I recently got an Ubuntu file/print server up and running with a mix of Wins and Ubuntu comps on the network. I have just been backing up all the comps (all laptops) to external disks but I would love to back them up to this central (desktop) server. I have samba going on the server, everything is talking. I was hoping to use luckybackup to accomplish this but I keep getting the following error   p, li { white-space: pre-wrap; } [COLOR=#FF0000]r[/COLOR][COLOR=#FF0000]sync: failed to connect to (host comp): Connection refused (111) rsync error: error in socket IO (code 10) at clientserver.c(122) [sender=3.0.7] [/COLOR]
 [COLOR=#FF00FF]execution of task : [/COLOR][COLOR=#FF00FF]home[/COLOR][COLOR=#FF00FF], finished[/COLOR]
[COLOR=#FF00FF] [COLOR=Black]My attempts at a primitive rsync script yield much less interesting errors and no results so any help would be great. thanks[/COLOR]
[/COLOR]

---

### Post by jquis8411 on 2010-10-01
Never mind I would have sworn open ssh was installed already but it wasn't. oops

---

### Post by mrhhug on 2010-10-01
so you could mark this as solved?

---

