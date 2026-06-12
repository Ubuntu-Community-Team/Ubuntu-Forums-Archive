---
title: "Ubuntu v6.06 Dapper Drake Main Repository 2006-08-10"
date: 2006-08-29
forum: Repositories &amp; Backports
---

### Post by sekcon on 2006-08-29
hey i downloaded this
[http://files.bigpond.com/library/index.php?go=details&id=23865]("http://files.bigpond.com/library/index.php?go=details&id=23865")
can someone explain how im suposed to install apps from it..
thanks.

---

### Post by mssever on 2006-08-29
> **sekcon said:**
> hey i downloaded this
[http://files.bigpond.com/library/index.php?go=details&id=23865](http://files.bigpond.com/library/index.php?go=details&id=23865)
can someone explain how im suposed to install apps from it..
thanks.

This is only for if you want to run your own repository. If you just want to install apps, see this link: [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by sekcon on 2006-08-29
i just want to install apps without having to download them everytime, i plan on installing ubuntu on several computers and want to be able to install alot of the main apps from a cd (such as opera, dvdripper as well as codecs and stuff) without wasting a crap load of bandwidth. could someone explain the best way for me to do this? 

also could you explain what a repository is then? ive had a look around but have found no straight answer..](*,) 

thanks for any help guys, i know a bit but am fairly new to linux and have just made a complete transfer from windows to ubuntu. 4 desktops, and 4 servers.. all ex-windows boxes (rip microsoft) :)

---

### Post by mssever on 2006-08-29
A repository is a central source where apps live until they're downloaded. I have no idea, though, how to set up a repository. And installing your own would require a lot of disk space.

However, if you use the normal methods of installing on one machine, the .deb files will be saved in /var/cache/apt/archives. You can then copy those debs to your other machines and install them--either double-click on the icon or do sudo dpkg -i package_name.

---

