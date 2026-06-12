---
title: "Mysql guide that works?"
date: 2020-09-15
forum: Server Platforms
---

### Post by math492m on 2020-09-15
hi i am trying to install mysql 5.5.62 on my ubuntu 18.04 server and i cant actually find a guide that works 

anybody got one 

thanks

---

### Post by Tadaen_Sylvermane on 2020-09-15
Is there a reason you need exactly that version? Why not just use the one in the repositories? (Prefer MariaDB myself, screw Oracle!)

```
sudo apt update && sudo apt install -y mysql-server
```

If not then can probably manually compile with the Debian backport instructions although I strongly recommend you stick with the newest stable version. 

```
sudo apt update && [COLOR=black]sudo apt-get install packaging-dev devscripts equivs dirmngr[/COLOR]
```

[COLOR=black]*EDIT* you may or may not need dirmngr. I recall needing it because I've also used this process to build packages from a few PPA's on Debian. It would fail unless I had dirmngr installed.

Do this next part in a dedicated folder to keep it easy to clean up.

(it wasn't accepting code tags properly for the next line)

dget -x [/COLOR]https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/mysql-5.5/5.5.62-0ubuntu0.14.04.1/mysql-5.5_5.5.62-0ubuntu0.14.04.1.dsc




Afterwards follow these instructions [https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation) starting at the Install Build Dependencies section. I also tend to skip the fakeroot part.

I make no guarantees this will work of course. You may need to chase down potentially changed dependency names and such in the Control file. I've used this process in the past to get MergerFS from Ubuntu repos > Debian before it was a standard package there.

---

