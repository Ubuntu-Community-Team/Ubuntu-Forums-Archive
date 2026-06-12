---
title: "Move a Server to Ubuntu?"
date: 2007-02-05
forum: Server Platforms
---

### Post by markbt on 2007-02-05
I want to replace an existing server with a Ubuntu installation on a different machine, i.e. I want to copy all my config and users and files to my ubuntu box.  Can I just type 
'cp -rf /mnt/old_servers_mounted_home_directories/* /place_on_new_server' ?

Can I also then just copy my passwd file from the old to the new, along with things like Samba configs, or is it actually much more complicated than this?

Thanks,
Mark

---

### Post by jtc on 2007-02-05
If the two servers are simillary setup you should be able to copy most of the files over right away, without too much trouble. At least when it comes to the homedirectories. When it comes to samba-config-files it might very well work, but I guess it could also depend on versions etc.

No matter what, it never hurts to try :-) As long as you keep the original server running until the new one works fine you can always try again if it didn't turn out right the first time.

Regarding the homedirectories I would use *rsync -a* since you that way get to keep fileownerships, timestamps, and pretty much everything else.

---

### Post by markbt on 2007-02-05
Thanks for the reply jtc, I'll give rsync a go :)

Mark

---

### Post by elst on 2007-02-05
Be careful about copying passwd files between distributions, as different distros provide different system accounts, so transplanted files may cause a few issues. It may be better to just copy the lines in /etc/shadow, /etc/passwd and /etc/group that specifically relate to user accounts.

---

### Post by markbt on 2007-02-06
Thanks for the warning, I'll keep an eye out for that pitfall.

Mark

---

