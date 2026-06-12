---
title: "[SOLVED] XAMPP Crippled by KDE?"
date: 2008-08-05
forum: Server Platforms
---

### Post by Jesdisciple on 2008-08-05
By installing KDE ([http://ubuntuforums.org/showthread.php?t=876801](http://ubuntuforums.org/showthread.php?t=876801)) I apparently crippled XAMPP and now the only localhost URL I can access directly is / (root), which ultimately (and ironically), after a complex process of META refreshing, PHP redirecting, and I don't know what else, prints a simple page:```
<html><body><h1>It works!</h1></body></html>
```

The behavior is identical in both GNOME and KDE.  How can I begin to diagnose this?  Thanks!

---

### Post by Jesdisciple on 2008-08-06
(bump)

I just noticed that, of the items on the XAMPP Control Panel (Apache, MySQL, ProFTPD), only ProFTPD is running; the rest are stopped.  Why would that be?

---

### Post by Jesdisciple on 2008-08-07
(bump)

Hello?

---

### Post by StickyStyle on 2008-08-07
I think your lack of responses lends me to believe that most people install/use the built-in LAMP stack, rather than a third party one.  Perhaps there is a XAMMP forum?

---

### Post by Jesdisciple on 2008-08-07
Yes, but it's German.  I actually just posted a message there after supposedly making it bilingual with Google Translate.

---

### Post by Jesdisciple on 2008-08-07
OK, I got an answer from Apache Friends:  Other MySQL and server daemons were installed with KDE.  What would those be?

---

### Post by StickyStyle on 2008-08-08
I can't see why KDE would have a dependancy on MySQL, but lets see...
Post the output of this, 
```
dpkg -l mysql-server
```

If I may be so bold to ask, why are you using XAMPP and not the built-in LAMP?  You wouldn't have these kinds of strange issues and you would be getting security updates on the packages from ubuntu-security.

---

### Post by Jesdisciple on 2008-08-08
I'm sorry; I should have updated this thread with the other.  The answer to both questions is (sort of) at [http://ubuntuforums.org/showthread.php?t=873145]("http://ubuntuforums.org/showthread.php?t=873145").

---

