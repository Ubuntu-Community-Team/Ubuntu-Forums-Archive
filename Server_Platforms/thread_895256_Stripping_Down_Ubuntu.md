---
title: "Stripping Down Ubuntu"
date: 2008-08-20
forum: Server Platforms
---

### Post by neutrino15 on 2008-08-20
I have an ubuntu install which is full of installed applications. I am repurposing the box as a home server, and therefore I only need the following on it:

LAMP
FTP
rtorrent
SSH

I have about a bajillion packages installed.. How do I get rid of them all?

thanks!

---

### Post by yabbadabbadont on 2008-08-20
The fastest way might be to reinstall using the alternate installation CD.  I believe that it has an option to install a LAMP system.  Then you can add the extra stuff you need.  Of course, backup your /etc and /home directories first.  That should be helpful if you have made any extensive modifications to your configuration files.

Edit: you may want to download the server installation CD.  I'm not sure now, if the alternate install CD includes the LAMP option.  (I know that it used to...)  Anyway, you might also want to read the help topic on LAMP here:

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by cariboo on 2008-08-20
There is a history file in Synaptic you could go through that if you have a lot of time :)

Jim

---

