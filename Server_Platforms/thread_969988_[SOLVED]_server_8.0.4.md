---
title: "[SOLVED] server 8.0.4"
date: 2008-11-03
forum: Server Platforms
---

### Post by mike010 on 2008-11-03
new to this one i have ubuntu terminal server 8.0.4 installed and i am also needing a file server i guess my question is how do i do that on the same
server just map the drive or do i need to install something?

thank you

---

### Post by cariboo on 2008-11-04
To set up file sharing you will have to install Samba, there is a howto here:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

and this document has helped me a lot:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

Jim

---

### Post by mike010 on 2008-11-04
Great answer and part of what i was looking for but with ltsp installed will it be the same or does the drive need to be partitioned to make room for the file server?

---

### Post by cariboo on 2008-11-05
No extra partitons needed. If you've got the CPU, ram and disk space you can run as many servers as you want.

For example on my server I run Lamp, samba, proftpd, openssh-sever, and probably one or two more that I have forgotten about. :)

My server is a computer I inherited from a previous job. AMD64 1Ghz 512Mb ram 120Gb for /, /home and swap and a 400Gb raid1 array for file storage.

Jim

---

