---
title: "I don't have an /etc/apache2/"
date: 2005-10-22
forum: Server Platforms
---

### Post by rach on 2005-10-22
Ok, I wanted to use my laptop as a testing-ground for PHP I'm writing for some-one else's site, and also to host my website to the rest of the network.

I installed "apache", but this seemed different from apache2, so I removed this and installed apache2 (I've no idea whether this was a stupid thing to do). Here comes the silly part:

I then spent ages trying to configure my web server, before finding out that I was editing the config files for the old version of apache (in /etc/apache/ as opposed to /etc/apache2). So to prevent further confusion, I decided to delete /etc/apache. Unfortunately, due to an unfortunate typing reflex I accidentally deleted /etc/apache2 instead. This has predictably stopped apache2 working properly.

I tried uninstalling and re-installing everything I could, but nothing seemed to restore the folder to it's proper state (I currently have a few files like "httpd.conf", but no "apache2.conf"). How can I get it back, preferably with the default set-up (which worked quite well apart from some issues with permissions which was what I was trying to fix in the first place).

Any help on this would be *greatly* appreciated.

--Rach

---

### Post by David Marrs on 2005-10-22
remove *all* of the apache2 packages and then try reinstalling. I still haven't figured out how to remove dependancies in a smart way when uninstalling software so this may be a case of going through and removing each package by hand.

---

### Post by rach on 2005-10-22
I tried that: I uninstalled every package that started with apache (regexp ^apache.* seemed to work for that), and re-installed. That's how I managed to get some of the files back, but not the essential ones.

--R

---

### Post by TomB on 2005-10-22
apache is the 1.3.X version, whereas apache2 is the 2.0.X version.

You should apt-get --purge remove <apache packages>, this will remove all the config files and such, ready for you to reinstall, make sure you backup any web sites in the docroot, usually /var/www

---

### Post by rach on 2005-10-22
Thanks TomB, you're a legend - it works now

--Rach

---

### Post by TomB on 2005-10-22
No problem :)

---

