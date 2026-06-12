---
title: "Restricted User Access"
date: 2011-03-31
forum: Security
---

### Post by Kaneda on 2011-03-31
I am running a system with a user that I want to be restricted to their home directory.  To do this, I used the following to set their home directory and restrict access:
```
usermod -d /home/username username
usermod --shell /bin/rbash username
```
(I got this from [http://ubuntuforums.org/showthread.php?t=1627240](http://ubuntuforums.org/showthread.php?t=1627240) and [http://www.cyberciti.biz/faq/restrict-linux-users-to-their-home-directories-only/](http://www.cyberciti.biz/faq/restrict-linux-users-to-their-home-directories-only/))

But... it turns out that I need the user to be able to reboot the machine from the command prompt.  This is disabled with the rbash restrictions.  Is there any way to keep access restricted, but still give them the ability to reboot?  Where would the best place to look be for learning to turn on or off certain features?

Thanks a lot!

---

### Post by bodhi.zazen on 2011-03-31
it is rather trivial to break out of rbash, I think you need to use apparmor.

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

