---
title: "Apache (un)installation badly corrupted by apt-get"
date: 2009-01-13
forum: Server Platforms
---

### Post by Jesdisciple on 2009-01-13
My Apache2 installation wasn't honoring the APACHE_RUN_* environment variables and therefore not treating directories or PHP pages as they should be, so I fiddled around with apt-get and tasksel for a while, shoving the **apache2** package and the **lamp-server** task back and forth.  After the first uninstallation, Apache stopped working altogether; I should have just tried hard-coding the variables in the first place, except then I might have gotten a bigger surprise later.

Anyhow, when my shoving was accomplishing nothing except the re-creation of four empty directories and one empty file (httpd.conf) in /etc/apache2, I decided to restart my system to get more diagnostic info for this thread.  When I booted back up, the shell complained about problems with **kinit**; the command by that name isn't installed, so I'm clueless.  But those problems crippled Gnome, and I took a crash-course in WeeChat and lynx (which was only useful for reading about WeeChat because it couldn't hold cookies or login).

I finally got someone on the Ubuntu IRC channel to state the obvious (and flattened my forehead a bit more): that I should reinstall the core Gnome components.  I already had **gnome-core**, so I just installed **gnome** for good measure.  One of those dependencies must have been the right one; when I rebooted, I was greeted by the GUI again.

I uninstalled all the packages listed at [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP) and then installed the lamp-server task again.  Now I'm in the same position as before I restarted; Apache can't start because apache2.conf doesn't exist, and even when it did exist something hidden was horribly wrong.  Does anybody have a clue about what's going one?

Thanks!

---

### Post by kmac on 2009-01-14
Would a copy of apache2.conf help at all? i could send you mine

---

### Post by cariboo on 2009-01-14
If you used a gui app to remove apache2, you may have not removed all the configuration files when uninstalling a package use:

```
sudo apt-get purge <packagename>
```

This completely removes the the package and it's configuration files. Then run in the same terinal:

```
sudo apt-get autoremove
```

To remove the dependencies.

I think think someone is leading you down the wrong path, as I have a LAMP server with no gui, and everything works the way it should with no gnome-core installed.

Jim

---

### Post by Jesdisciple on 2009-01-14
kmac, thanks for the offer but there are several other missing files and I don't even know whether they all belong in /etc/apache2/.  apache2.conf is just the first one identified when I try to start the server.

Jim, I don't mean the GUI for Apache but Gnome itself.  I was stuck in the login shell, and that's where lynx and WeeChat came in.

I ran those two lines for **apache2** and then installed it again, but saw no improvement.

---

### Post by Jesdisciple on 2009-01-17
I forgot about this, but... (bump)

---

