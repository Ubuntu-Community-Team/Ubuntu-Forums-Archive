---
title: "How to change a desktop install into server?"
date: 2006-07-15
forum: Server Platforms
---

### Post by docko on 2006-07-15
i have installed ubuntu desktop, but that box has become my home gateway/firewall/web server, now i don't need gui on it, so i uninstalled gnome, and some packages i knew i wouldn't need (oo2, etc).
is there any simple way to remove all the packages that come with ubuntu desktop and are not needed on a computer without X?

thank you

---

### Post by Swab on 2006-07-15
The ubuntu-desktop package is a meta package for all the gui stuff.

"apt-cache showpkg ubuntu-desktop" will show you all dependencies... you could then remove all those packages... I don't know of any smarter way to do this.

---

### Post by verbatim210 on 2006-07-15
never tried it, but boot straight into console?
hopefully theres a way to bypass the gui

...either that, or fresh install

---

### Post by bikeboy on 2006-07-15
While this isn't removing the packages, it suggests how to customise a runlevel to load Ubuntu without the gui or any other unnecessary things. That should slim down your box a bit.

[http://ubuntuforums.org/showthread.php?t=79058](http://ubuntuforums.org/showthread.php?t=79058)

---

### Post by docko on 2006-07-15
i already load ubuntu without the gui, i just don't want to keep the packages i don't need. 
probably the best way to do it would be as Swab wrote...

---

### Post by verbatim210 on 2006-07-15
correct me if im wrong but linux is nothing like windows
you can install a million packages and it wont necessarily affect your resources, all but hd space as long as your not using them of course

---

### Post by compbrain on 2006-07-16
Perhaps [http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop) is what your looking for?

---

### Post by docko on 2006-07-16
thanks compbrain, this is what i was looking for

---

### Post by uncleclinto on 2006-07-18
Hey kids.

I've got my box up and running with Ubuntu desktop (because I wanted that pretty GUI).  Anyway, I want to install my lamp stack, using aptitude as follows: "apache2 php5-mysql libapache2-mod-php5 mysql-server".  I read the manual.  I read the page [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).  I even read the aptitude survival guide.  When I open the terminal, what do I type at "admin@waltersweb:~$" to install "apache2 php5-mysql libapache2-mod-php5 mysql-server" with aptitude?  Is terminal the right place to do this?  Do I simply write "aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server", or must I begin with some other magic word or command, like "root" or "sudo" or something?

Please help the stupid noob...

---

### Post by az on 2006-07-18
> **uncleclinto said:**
> Do I simply write "aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server", or must I begin with some other magic word or command, like "root" or "sudo" or something?

Please help the stupid noob...

You can use any method:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

You can even use dselect!

There are many different ways to install applications.  The style guide for documentation prefers mentioning to use any menton and refering to the InstallingSoftware documentation instead of having inconsistent command line examples.

---

