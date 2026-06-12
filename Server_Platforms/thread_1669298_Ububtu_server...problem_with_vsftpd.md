---
title: "Ububtu server...problem with vsftpd"
date: 2011-01-17
forum: Server Platforms
---

### Post by alfamuzjak on 2011-01-17
Did anyone know how to add files (and where) for anonymous download. I installed vsftpd and configure /etc/vsftpd.conf file...just few common options like allowing anonymous,download,upload. And now i can login with anonymous.

But i dont know what to do next, i want to try to download and upload files. Can anyone help me with with this?

---

### Post by alfamuzjak on 2011-01-17
PLease help me...I realy need this.

---

### Post by alfamuzjak on 2011-01-17
Please help me...I realy need this.

---

### Post by pipemartinm on 2011-01-17
There's heaps of config guides for vsftpd out there. Try [http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm)

Make sure you unblock port 20 & 21 on your firewall and use a simple ftp client or just your web browser to test it.

---

### Post by alfamuzjak on 2011-01-17
Thanks for that, i will search that one too.
Till now i have seen a lots of tutorials etc, but none have answer where to putt files which can i download for test, or some instruction about upload folders. All i've saw was explanations about options in /etc/vsftpd.conf file which isnt so tricky...
I mean after i config that file

---

### Post by alfamuzjak on 2011-01-18
> **pipemartinm said:**
> There's heaps of config guides for vsftpd out there. Try [http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm)

Make sure you unblock port 20 & 21 on your firewall and use a simple ftp client or just your web browser to test it.

I cant find anything about files which can i putt (where) for download...Cant belive that noone knows

---

### Post by RobbanC on 2011-01-18
Hi

I snooped around [here]("http://www.informit.com/articles/article.aspx?p=378136&seqNum=7")...

Try:
```

anon_root=/your/directory/here

```
Standard value (if you don't enter any own dir.) seem to be /var/ftp

Hope this helps. :)

---

### Post by alfamuzjak on 2011-01-19
I solved download problem after hard googling and lots of luck! Now i just need to check if upload works.
If that is ok too and if someone wants to know how i will post solution here soon.

---

### Post by alfamuzjak on 2011-01-19
.

---

### Post by alfamuzjak on 2011-01-19
.

---

### Post by alfamuzjak on 2011-01-19
.

---

### Post by alfamuzjak on 2011-01-19
.

---

