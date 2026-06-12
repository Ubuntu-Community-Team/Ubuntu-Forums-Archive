---
title: "vsftpd users storage symlinks"
date: 2010-03-27
forum: Server Platforms
---

### Post by Artanis.ro on 2010-03-27
I have some questions about the vsfptd program for ftp on ubuntu. I think this topic will be helpful for other ppl too as I saw it's intensely searched on google. 
My first problem is that when I installed vsftpd (using this [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html guide)]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html") none of my users from my machine got a "ftp" directory in their home folder. The ftp folder was "/srv/ftp" directly into root. Can someone tell what setting must I do to get a "ftp" folder inside each user's home folder?

My second problem is about the users. How can I set a user to have access only to the "ftp" folder inside his home directory. Or if this program uses "srv/ftp" as main storage directory how can I set a user to have access only to that folder (an authenticated user)? I am asking this because I know that by default vsftpd doesn't virtualise any user apart from the default anonymous who uses as storage "/srv/ftp". I know that local system users can log on to the ftp and have access everywhere, or they can be jailed and have access only to their home directory, but can they be "jailed" even more to one directory?

My third question is about symlinks to aditional storage. If I want to add an additional storage directory to a user's ftp directory can this be done somehow using symlinks? I have tried this and if the additional storage directory or partition is outside the user's home directory it can't be accessed (505 error.....).

Thank you very much

---

### Post by inphektion on 2010-03-27
that's a poor guide really.  if you don't get any good responses by monday i'll post you mine.  will answer most of your questions.

---

### Post by Artanis.ro on 2010-03-29
> **inphektion said:**
> that's a poor guide really.  if you don't get any good responses by monday i'll post you mine.  will answer most of your questions.

ok, thank you

---

