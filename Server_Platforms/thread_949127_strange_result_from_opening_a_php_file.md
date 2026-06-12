---
title: "strange result from opening a php file"
date: 2008-10-15
forum: Server Platforms
---

### Post by glenngds2007 on 2008-10-15
in fact I tried to open index.php and got something like this

You tried to open
which is a PHTML file...

Yes php5 is installed and so is apache2
What have I forgot to install or uninstall????????:confused:

---

### Post by cariboo on 2008-10-15
Have you got libpache2-mod-php5 installed? to check in a terminal type:

```
ocate libapache2-mod-php5
```

If you have it installed the output should look like this:

```

locate libapache2-mod-php5
/usr/share/doc/libapache2-mod-php5
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
```

If this solves your problem please mark this thread solved

Jim

---

### Post by glenngds2007 on 2008-10-16
Actually libapache2-mod-php5 is installed.  The problem was caused by I am not sure.  I just installed apache and php and had not rebooted.  Some updates, including a new kernel, recently was installed and recommended a reboot--anyway when I rebooted everything was just fine.

---

### Post by az on 2008-10-16
> **glenngds2007 said:**
> Actually libapache2-mod-php5 is installed.  The problem was caused by I am not sure.  I just installed apache and php and had not rebooted.  Some updates, including a new kernel, recently was installed and recommended a reboot--anyway when I rebooted everything was just fine.

When testing web deployment, you need to clear your browser cache often.  If Apache doesn't handle php and serves it up as a text file, that file will still be in your browser's cache.  So even if you install the correct packages on your server, then next time you click on the link, your web browser won't even query the server again, but use what it has in it's cache.

In firefox, hitting CTRL-F5 clears the current page's cache and reloads the page.

This may be an explanation for you.

---

