---
title: "Webserver install ?"
date: 2005-04-10
forum: Server Platforms
---

### Post by nervensäge on 2005-04-10
Linux Dau (my first linux) 
I installed kubuntu and would like a Web server now to furnish with php5.0.4 and mysql 4.1.18 (evenly stood for the newest). How can I make that? I would like to furnish my web page local, with windows use I xampp and as go that now here.

---

### Post by Hinko on 2005-04-10
just use kynaptic to install apache, php and MySQL, and basically, you're done then.

---

### Post by nervensäge on 2005-04-10
kynaptic ? what is this ?

---

### Post by shemso on 2005-04-11
GUI for apt-get

---

### Post by bcnstony on 2005-04-13
I don't believe there is a package for PHP5. From the terminal, typing "apt-cache search php4" will get you a lot, but "apt-cache search php5" returns nothing. I believe you will have to compile php5 yourself. Directions can be found here: [http://www.ubuntulinux.org/wiki/PHP5FromSource](http://www.ubuntulinux.org/wiki/PHP5FromSource)
or you could also search for how to do this in debian.

You might just use php4, unless you specifically need php5. I believe you may have to add the Universe to your list of sources. There are several how-to's on Ubuntu wiki if you need to know how to do this.

As for mysql, I believe you are limited to 4.0 if you want an easy install, though you can always compile from source if you have to have the latest.

Synaptic (or kynaptic?) is what you use from the GUI to download and install precompiled packages. The same is accomplised by typing "apt-get install php4" from the command line. 

hope that helps

---

