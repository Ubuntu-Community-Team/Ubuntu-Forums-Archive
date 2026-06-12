---
title: "Unable to admin CUPS remotely - 'Unable to Connect'"
date: 2006-08-18
forum: Server Platforms
---

### Post by SparkyFlooner on 2006-08-18
I'm trying to figure out how to admin CUPS remotely.  I installed cupsys, tinkered with the cupsd.conf to allow remote administration, but all I ever see when I try to log on is:

"Unable to connect"

I'm a noob, so --> ](*,)

---

### Post by bluefrog on 2006-08-18
cupsys need to be added to the shadow group and restart cupsys after doing so.

sudo adduser cupsys shadow
or
sudo vi /etc/group and add cupsys manually at the end of the shadow line.

restart cuspsys.

Drawback: if memory serves there will be no more authentication but I won't be 100% sure on that one (if so it will be dangerous as anybody could access it)

James

---

### Post by SparkyFlooner on 2006-08-18
I did that.  cupsys was added to shadow group, I restarted cups, but still am unable to connect.

...what is the shadow group, btw?

(After doing a 'man shadow'...I'm guessing a member of shadow group can authorize users.)

---

### Post by SparkyFlooner on 2006-08-18
bluefrog - 

When I installed Ubuntu as a desktop, adding cupsys to shadow wouldn't keep you from having to enter a password when trying to admin CUPS remotely.  You had to assign root a password and log in as root.  But it's http, so the password is probably being sent cleartext across the network...whi

Now I've got it installed as a pure server with no X.....

So I'm still here --> ](*,)

---

### Post by SparkyFlooner on 2006-08-19
Ok, this seems like a simple issue to resolve.  In both Fedora and Desktop Ubuntu installs I've been able to remote admin CUPS via the web page.  Fedora worked right out of the box, but Ubuntu I had to do the trick of adding cupsys to the 'shadow' group...but it still worked.

I do the same cupsys->shadow trick for my server install of Ubuntu, but I still can't admin CUPS via the web page.

Anyone?  I shouldn't need apache, the cupsd is actively listening on 631.  What DO I need to do?

---

### Post by jnoreiko on 2006-08-26
> **bluefrog said:**
> 
restart cuspsys.


how do you do that?

EDIT: never mind, this thread explains it:
[http://www.ubuntuforums.org/showthread.php?t=189525](http://www.ubuntuforums.org/showthread.php?t=189525)

---

