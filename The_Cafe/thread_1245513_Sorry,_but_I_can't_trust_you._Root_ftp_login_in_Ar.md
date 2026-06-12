---
title: "Sorry, but I can't trust you. Root ftp login in Arch Linux"
date: 2009-08-20
forum: The Cafe
---

### Post by dragos240 on 2009-08-20
Hi there,

Is there a way I can root login on my pure-ftpd server? I have it installed on archlinux..... but when I login as root, it doesn't trust me :(

Help?

---

### Post by Bachstelze on 2009-08-20
This isn't related to programming. Moved to the Cafe.

---

### Post by kk0sse54 on 2009-08-20
The Arch Linux forums exist for a reason, as well as google...


[http://www.google.com/search?q=pure-ftpd+root+login&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=pure-ftpd+root+login&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

---

### Post by bodyharvester on 2009-08-20
is arch linux really that different to ubuntu that the problem cant be solved here? i thought it was just a different interface/applications and slightly modified bits. arch users still come here to chat, someone may know

---

### Post by dragos240 on 2009-08-20
> **HymnToLife said:**
> This isn't related to programming. Moved to the Cafe.

I wasn't sure....

---

### Post by saulgoode on 2009-08-20
There should be an /etc/ftpusers file which contains the names of the users that may ***NOT*** log into the system via the FTP server. If root is listed in that file, delete it or comment it out. (At least, that is how it is done on Slackware.)

---

### Post by dragos240 on 2009-08-20
> **bodyharvester said:**
> is arch linux really that different to ubuntu that the problem cant be solved here? i thought it was just a different interface/applications and slightly modified bits. arch users still come here to chat, someone may know

Very different...... most of the config files are in different places..... and because of that, it's harder to fix.

---

### Post by dragos240 on 2009-08-20
> **saulgoode said:**
> There should be an /etc/ftpusers file which contains the names of the users that may ***NOT*** log into the system via the FTP server. If root is listed in that file, delete it or comment it out. (At least, that is how it is done on Slackware.)


It doesn't seem to exist. Arch's config files are much different than those of other distros.

---

### Post by cariboo on 2009-08-20
Instead of trying to ftp as root, why not just make yourself a member of the group that owns the folder you want to transfer a file to/from?

---

### Post by dragos240 on 2009-08-20
Or I could use SSH...... which is what I'm doing....

---

### Post by cariboo on 2009-08-20
Actually that was my first thought, use sftp, and get rid of the ftp server all together.

---

