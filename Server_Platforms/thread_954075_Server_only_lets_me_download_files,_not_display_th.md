---
title: "Server only lets me download files, not display them?"
date: 2008-10-20
forum: Server Platforms
---

### Post by ajwak95 on 2008-10-20
I just installed Ubuntu Server, and got my LAMP server working. So now I go to my blog folder, and I can only download a file. Please help.

---

### Post by lykwydchykyn on 2008-10-20
What file extension do your pages use?  
What this means is that Apache has not been given a file handler for that file extension.

---

### Post by ajwak95 on 2008-10-21
php extensions.

---

### Post by lykwydchykyn on 2008-10-21
Make sure php is installed properly:
```

sudo aptitude install php5 libapache2-mod-php5

```

If that command installs no packages, let us know.  Otherwise that'd be the source of the problem.

---

### Post by krcabrer on 2009-04-12
Hi, I got the same problem with firefox,
and when I type

sudo aptitude install php5 libapache2-mod-php5

It anwers me that I have them already installed.

I clean the cache, cookies on firefox, but
stills the problem, also I deactivate the
download status bar plugin, but it have the same
problem..

The page I am traying to open is:

[http://wxmaxima.sourceforge.net/wiki/index.php/Main_Page](http://wxmaxima.sourceforge.net/wiki/index.php/Main_Page)

And it do not work when I try the "Public forum" link.

Thank you for your help.

Kenneth

---

