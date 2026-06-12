---
title: "Apache not recognizing 3TB disk"
date: 2012-01-15
forum: Server Platforms
---

### Post by DukeBoxer on 2012-01-15
Just a quick question to see if anyone knows the answer. I built a desktop/server box. I serve the website of our business from an internal 1TB hard disk (seagate) and on another port I have a password protected media server on an external 1TB hard drive. On the media server I sym-linked a folder from my internal 1TB disk that has all the series' on it. I then tried to sym-link a folder from an internal 3TB (WD Caviar Green) that I formatted ext4 but didn't use a partition table and the link would not show up from the browser so I removed everything from the disk and formatted it with a GUID partition table thinking that may have been the problem. It wasn't. No sym-link from that disk shows up in the browser so I created a new site, served it on a new port with that disk as the root, enabled the site, added the new port to the ports.conf file and typed in "localhost:8180" in the browser and nothing. Then I typed in "192.168.1.85:8180" and again nothing. Does anyone know why Apache wouldn't recognize this disk and serve from it? It's not encrypted, which is another reason I found that Apache won't work, but with an encrypted disk, at least it throws an "Access Denied". This just shows that the website can't be found. Any ideas...??

---

### Post by CharlesA on 2012-01-15
Apache doesn't follow symlinks by default.

[http://httpd.apache.org/docs/2.0/sections.html](http://httpd.apache.org/docs/2.0/sections.html)

---

### Post by DukeBoxer on 2012-01-15
> **CharlesA said:**
> Apache doesn't follow symlinks by default.

[http://httpd.apache.org/docs/2.0/sections.html](http://httpd.apache.org/docs/2.0/sections.html)

It follows the sym-link fine to the 1TB internal drive. I would read all that but even using that drive (the 3TB) as the document root doesn't work.

---

### Post by CharlesA on 2012-01-15
Make sure you have the permissions set correctly.

Check /var/log/apache2/access.log for errors.

---

### Post by DukeBoxer on 2012-01-15
oh good idea...didn't think of that

---

### Post by DukeBoxer on 2012-01-15
Nada....Oh well

Did chmod -R 777 Games/ (the directory I'm testing with) and still nothing. I checked the other folders, the media is 777 belonging to me (owner and group), the web site is 755 with me as the owner and www-data as the group

---

### Post by CharlesA on 2012-01-15
Did the access.log show anything?

---

### Post by DukeBoxer on 2012-01-15
No, nothing out of the ordinary, baidu spider bot, me looking at the media server on 8080...weird

---

### Post by CharlesA on 2012-01-15
Hrm, I am kinda stumped on this.

If apache couldn't read something, it should have thrown a 403 error.

---

### Post by DukeBoxer on 2012-01-16
Exactly what I was thinking. It's like the disk isn't even there. I want to see now if I can share the disk with nfs or not. I'll get back

---

### Post by CharlesA on 2012-01-16
Hope it helps troubleshooting.

---

### Post by DukeBoxer on 2012-01-16
ok, I'll mark this one as solved, it was a permission issue. The NFS share did help to troubleshoot. I defined it in /etc/exports and tried mounting it on another computer. It mounted fine but when I tried to open it up it said I didn't have permission to, so I went back and checked the permissions of the drive itself in /media and it was only read/write for myself so I changed it to read for everyone and voila...perfect! Before I was just looking at the permissions of the folder I wanted to sym-link to the server, not of the disk itself

---

### Post by CharlesA on 2012-01-16
Awesome. Glad you got it working!

---

