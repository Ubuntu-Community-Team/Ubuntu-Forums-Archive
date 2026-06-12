---
title: "adding web site to exception list in dansguardian"
date: 2011-02-01
forum: Security
---

### Post by toolmania1 on 2011-02-01
[FONT=Calibri]How do you add a website to the exception list in dansguardian?[/FONT]
 
[FONT=Calibri]I was not able toedit the exceptionsitelist file.  I triedto chmod it to 777, but I was informed by Ubuntu that this was notallowed.  No reason was given though.[/FONT]
 
[FONT=Calibri]So, maybe it is assimple as typing the site into the exceptionsitelist file.  But, if I cannot open it becausedansguardian, or something else, is blocking editing the file, then that wouldbe why I cannot add sites to the exception list.  Anyone have any ideas on this?[/FONT]

---

### Post by toolmania1 on 2011-02-01
gksudo gedit /etc/dansguardian/lists/exceptionsitelist

Do I need to use gksudo in front?

( I found that on this page:
[http://ubuntuforums.org/showthread.php?t=1204576](http://ubuntuforums.org/showthread.php?t=1204576)
but for phrase list in that case )

---

### Post by bodhi.zazen on 2011-02-01
> **toolmania1 said:**
> gksudo gedit /etc/dansguardian/lists/exceptionsitelist

Do I need to use gksudo in front?

( I found that on this page:
[http://ubuntuforums.org/showthread.php?t=1204576](http://ubuntuforums.org/showthread.php?t=1204576)
but for phrase list in that case )

Yes, you need to edit system files as root, not change ownership or permissions.

So, for graphical applications such as gedit, use gksu

From a terminal use sudo

```
sudo -e /path/to/file/to/edit
```

---

### Post by toolmania1 on 2011-02-01
Ok, that must have been what I was doing wrong then.  I used sudo, but not on the correct item.  I think I did:

sudo gedit exceptionsitelist

but I need to do:

gksu gedit exceptionsitelist

or 

gksudo gedit exceptionsitelist

Right?

---

### Post by bodhi.zazen on 2011-02-01
> **toolmania1 said:**
> Ok, that must have been what I was doing wrong then.  I used sudo, but not on the correct item.  I think I did:

sudo gedit exceptionsitelist

but I need to do:

gksu gedit exceptionsitelist

or 

gksudo gedit exceptionsitelist

Right?

gksu is a symbolic link to gksudo, so same thing with less typing.

You need to use the full path to exceptionsitelist

---

### Post by toolmania1 on 2011-02-02
cd /etc/dansguardian/lists
 
gksudo gedit exceptionsitelist
 
I added my web site here and saved.  I reloaded the site and dansguardian did not block it.
 
Thanks!

---

