---
title: "music.raw in my /var/www"
date: 2012-11-18
forum: Security
---

### Post by davidgutu on 2012-11-18
Hi,
I just found a music.raw file in my /var/www folder. I have no idea how it came about. Is there a way to find out what happened? Is this something you have seen before?

Thanks!

---

### Post by samiux on 2012-11-18
> **davidgutu said:**
> Hi,
I just found a music.raw file in my /var/www folder. I have no idea how it came about. Is there a way to find out what happened? Is this something you have seen before?

Thanks!

Hehe, sound like a payload.  Good luck!

Samiux

---

### Post by Lars Noodén on 2012-11-18
What are the permissions on /var/www?

```

 ls -ld /var/www/

```

---

### Post by davidgutu on 2012-11-18
All root - both user and group.

drwxr-xr-x 2 root root 4096 Nov 18 04:57 /var/www/

---

### Post by Ms. Daisy on 2012-11-18
Found these:
[http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-general-questions/368711-music-raw-file.html](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-general-questions/368711-music-raw-file.html)
[http://forums.fedoraforum.org/archive/index.php/t-247203.html](http://forums.fedoraforum.org/archive/index.php/t-247203.html)

In computer-time, those threads are beyond ancient so keep that in mind.  Hopefully they give you a little more information about where a music.raw file would come from.

But if you're concerned about it being malicious you can do a little investigating using [this guide]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned").

---

### Post by samiux on 2012-11-19
> **davidgutu said:**
> Hi,
I just found a music.raw file in my /var/www folder. I have no idea how it came about. Is there a way to find out what happened? Is this something you have seen before?

Thanks!

If nobody can answer your question, you may consider to contact me.  Maybe I can answer your question as I am a certified ethical hacker.

Samiux

---

### Post by Ms. Daisy on 2012-11-19
> **samiux said:**
> If nobody can answer your question, you may consider to contact me.  Maybe I can answer your question as I am a certified ethical hacker. That would be great Samiux. How about you share your knowledge with the whole forum, right here?

---

