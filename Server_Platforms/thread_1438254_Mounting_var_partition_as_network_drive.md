---
title: "Mounting /var partition as network drive"
date: 2010-03-24
forum: Server Platforms
---

### Post by Antares784 on 2010-03-24
I'm setting up a server, and someone asked me (after I was done installing and formatting) whether the external hard disk attached to this server (with the /var partition) could also be mounted as a network drive for easy file transfer (i.e. drag-drop file transfer without ssh/scp or sftp). If someone has any ideas on how a pre-formatted (ext4) partition can be simultaneously made available as a network drive readable by a Windows machine, the help would be hugely appreciated.

Thanks!

---

### Post by Antares784 on 2010-03-24
Also, this is Ubuntu 9.04 (Karmic Koala).

---

### Post by Jive Turkey on 2010-03-25
I don't know of a situation where you would want network users writing to /var , but if you did samba would be the way to go for windows clients.

---

### Post by Antares784 on 2010-03-25
This is intended to be a web/file server - I would want people to put files in /var/www/<directory with files> so that they are easily accessible over http as soon as they're posted, rather than having some one person exclusively managing this. Special requirements for a research group - ideally this will be possible; if not, I've to get everyone using ssh or sftp.

Thanks!

---

