---
title: "Why gksu and gksudo?"
date: 2006-10-28
forum: The Cafe
---

### Post by DaveBorealis on 2006-10-28
What's the advantage of using gksu/gksudo over su/sudo, such as in:
gksu "update-manager -c"

All it seems to is use a dialog box to ask for a password, rather than asking for it in the same terminal that one had to use to launch the gk* command in the first place.

Am I missing something?

Best regards,
Dave

---

### Post by taurus on 2006-10-28
Here you go, from one of the staff members...

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ComplexNumber on 2006-10-28
it only seems to be necessary on ubuntu.

---

### Post by DaveBorealis on 2006-10-28
> **taurus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Ah...I get it now.  su/sudo for CLI commands, and gksu/gksudo for running GUI applications (launched from the command line).

Thanks!
Dave

---

### Post by glotz on 2006-10-29
Now since we got the sudo versus gksudo issue solved, there's a *vaguely similar* relation between su and sudo (and prolly gksu and gksudo), see [https://help.ubuntu.com/community/RootSudo#head-a76e0b38808fca380fa209babb080d60ffe0ec8e](https://help.ubuntu.com/community/RootSudo#head-a76e0b38808fca380fa209babb080d60ffe0ec8e) Bullet 1.

(what a beautiful URL by the way..!)

---

### Post by DaveBorealis on 2006-10-29
> **glotz said:**
> Now since we got the sudo versus gksudo issue solved, there's a *vaguely similar* relation between su and sudo (and prolly gksu and gksudo)

This thread has potential to start a flame war, yet!

---

### Post by glotz on 2006-10-29
:lol: :evil: :lol:

---

### Post by taurus on 2006-10-29
> **DaveBorealis said:**
> This thread has potential to start a flame war, yet!
Don't worry.  We have buckets of water here so it's not going to start and if it does, it's not going to go too far...  :twisted:

---

### Post by aysiu on 2006-10-29
Actually, the page on graphical sudo outlines the differences between *sudo* and *gksudo*, but it doesn't explain the differences between *gksu* and *gksudo*.

Does anyone know the difference between those two?

---

### Post by taurus on 2006-10-29
I always thought that su is a terminal command while gksu is a graphical of su.  On the other hand, sudo is CLI while gksudo is GUI of sudo!!!

---

### Post by DaveBorealis on 2006-10-29
> **taurus said:**
> Don't worry.  We have buckets of water here so it's not going to start and if it does, it's not going to go too far...  :twisted:

Hey just 'cause Dick Cheney says water dunking bad guys is a no brainer...

(Besides...I'm not really bad, just misunderstood!)

---

### Post by wieman01 on 2006-11-15
Actually... One point mentioned on the site is incorrect: You can run...
> sudo kate
...by all means. Doing it all the time. Also the link (...here) on the page is unreachable or broken. 

So far I have not found a sufficient explanation as to why someone should use "gksudo" or "kdesu" rather than "sudo". The explanation given on the site is one step in the right direction, but I cannot confirm that from what I have experienced up to now.

Anything else we should know?

---

### Post by wieman01 on 2006-11-15
By the way... Using common sense, I would think that the difference between "gksu" and "gksudo" is that the first one is the graphical version of "su root", the latter is the graphical tool to run administrative tasks for the current user (if that user has administrative rights). 

Would that make sense?

---

### Post by 23meg on 2006-11-15
> **aysiu said:**
> Actually, the page on graphical sudo outlines the differences between *sudo* and *gksudo*, but it doesn't explain the differences between *gksu* and *gksudo*.

Does anyone know the difference between those two?

Go to apps/gksu in gconf-editor and you'll see that gksu defaults to using sudo in Ubuntu anyway, so there's no difference. If you uncheck the sudo-mode box, you should be able to enter your password only once per session when running administrative graphical apps, if you've enabled the root account.

---

