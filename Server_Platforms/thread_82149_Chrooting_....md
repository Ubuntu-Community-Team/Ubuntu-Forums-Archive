---
title: "Chrooting ..."
date: 2005-10-26
forum: Server Platforms
---

### Post by dbee on 2005-10-26
Do you chroot your production server apps ... eg. Apache, Mysql, PHP ?

If not why not ?
If so, why ?

I'm spending alot of time doing it at the moment but I'm not too sure that it's worth my effort in the of the day ...

... also, one question ... what's the easiest way to check whether your app is running from it's chroot environment ?

---

### Post by simon w on 2005-10-26
I don't because I don't know how to (yet)

How do you chroot a user to their home directory when they ssh in? :p

---

### Post by herrpoon on 2005-10-26
Hehe simon, that was pretty much going to be my response too!  Having wiki'ed it I'm still at a loss how to do this :confused:

---

### Post by dbott67 on 2005-10-26
I have not done this either, but would be interested in any tips & caveats people have.

A simple search of Ubuntu forums for "chroot jail" turned up [this.]("http://www.ubuntuforums.org/search.php?searchid=2246163")

One of the posts has an article that leads [here for chrooting Apache]("http://www.linux.com/article.pl?sid=04/05/24/1450203").

If anyone has actually done this, I'd be interested in their thoughts.

Thanks,
Dave

---

### Post by LordHunter317 on 2005-10-26
Depending on your production site goals, chrooting Apache is useless, because the real security concern is the PHP applications you're running.  In which case, PHP as a fastcgi + suExec is what you really want.

MySQL is ok to chroot, as is postfix.  BIND should always be chrooted, no matter what.  

And mod_chroot is probably a better way to run chroot Apache.

---

### Post by Glut on 2005-10-26
One of the non-security related advantages to chrooting is that all of the files relating to one service are easily identifiable and replaceable. For instance, if you chroot your users who login with ssh, then they can run a different version of programs to the one that you run on the base system. Thus much funkiness can be done. The obvious downside is that maintainence becomes hell.

There is a patch for sshd that automatically chroots the user once they log in. It's a sourceforge project and I'm afraid I can't remember the name. It's easy to setup, but has limitations.

As for checking the process, it is often service specific. For ssh above, the easiest way is to log in as a user and check, because the patched server itself does not actually run in the jail.

---

