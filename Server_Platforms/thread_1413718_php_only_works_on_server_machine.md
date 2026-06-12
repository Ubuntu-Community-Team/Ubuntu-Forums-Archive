---
title: "php only works on server machine"
date: 2010-02-22
forum: Server Platforms
---

### Post by Cenotaph on 2010-02-22
So, I'm trying to setup a server at home so i can work in a LAMP based web app from a Windows 7 laptop. I downloaded Ubuntu Server 9.10 and installed it on one of my desktop PCs. I also installed phpmyadmin and everything seemed fine (tested with lynx)

I started noticing the problem when I tried to connect from the laptop to the server in the same LAN. when i tried to access http://<server-name>.lan/phpmyadmin the browser kept loading forever and nothing appeared. The default http://<server-name>.lan/index.html "it works" page display just fine

I then created a testing.php file containing just <?php phpinfo() ?> in the /var/www directory and it works on the server, but from the laptop it displays the same hanging behaviour, any php code doesnt seem to be properly executed when apache serves other machines.

Im guessing its some sort of php configuration causing this, and it might be obvious for ppl with more experience with server setups, but i've never setup a server before and Im having a hard time solving this.

Any help is appreciated. Thanks.

---

### Post by Cenotaph on 2010-02-22
hmm... i guess this might be a non-trivial issue. I can't really afford to lose many time on this so ill setup a server on a virtual machine instead, which seems to work flawlessly like i intended. I'd rather have my webapp in a different computer but we dont always get what we want. ;)

still, if someone has an idea of what might be happening let me know.

---

