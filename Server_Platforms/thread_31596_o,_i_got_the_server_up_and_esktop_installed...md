---
title: "o, i got the server up and esktop installed.."
date: 2005-05-03
forum: Server Platforms
---

### Post by jayd36108 on 2005-05-03
now that i have that going, is there an easy walkthrough of how to setup the server tools i need to get a website running?

something for us simple folks like myself wo may be a tad on the slow side.

---

### Post by Trickyphillips on 2005-05-04
[QUOTE=jayd36108]now that i have that going, is there an easy walkthrough of how to setup the server tools i need to get a website running?

something for us simple folks like myself wo may be a tad on the slow side.[/QUOTE]
 Some packages that you might be interested in:

**apache** - HTTP server. Will allow you to host files (such as HTML) that can be accessed via a web browser.[B]
proftpd[/B] - FTP server. FTP stands for "File Transfer Protocol". Will allow you to upload, download, and delete files from your server, from a remote location.
**php4** - This package adds PHP support to Apache. Search google, for more information on PHP.
**mysql** - Allows you to create databases. These message boards use MySQL to store all posts made on the boards, as well as user names, profiles, etc.
**phpmyadmin** - I really suggest installing this, if you have MySQL. It's a web-based interface, that allows you to manage your SQL databases. You can accessing by pointing your browser to [www.yourip.com/phpmyadmin](www.yourip.com/phpmyadmin). I suggest changing the default password, which is blank, with the username "root".
**ircd** - A decent IRC server. I've used it a couple times, but haven't gotten too excited over it.
**ssh-server** - Will allow you to completely access your computer remotely, using the login and password that you supplied during installation. (You can even install packages from another computer, using this, if you'd like.)
**telnetd** - Like SSH, but much less secure. Only use this if you're unable to download Putty (ssh client) onto the machine you plan on veiwing the computer from.

---

### Post by jayd36108 on 2005-05-04
great thanks!

is there an apt get sudo command to easily install this stuff? i'm still new to all this and not quite sure how to install on a linux server compared to on my windows pc

---

### Post by s0c0 on 2005-05-04
Just search synaptic for these packages or if you don't have a GUI installed use the aptitude command to bring a commandline version of synaptic.

---

### Post by Trickyphillips on 2005-05-04
[QUOTE=jayd36108]great thanks!

is there an apt get sudo command to easily install this stuff? i'm still new to all this and not quite sure how to install on a linux server compared to on my windows pc[/QUOTE]

Yes. You can just use  "sudo apt-get install **package-name**". :)

---

### Post by firefly2442 on 2005-05-04
Webmin is another great program to manage your server and computer, even remotely. :)

---

### Post by jayd36108 on 2005-05-05
ok, i have webmin and i seem to have everything up and running, i am just stuck on on how to setup the ftp server so i can ftp files from one computer to the server.

can anyone explain this to me/walk me through it

if need to, my yahoo screen name is bama_media_mafia

---

