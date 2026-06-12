---
title: "Domino 8 list errors on the console"
date: 2008-02-12
forum: Server Platforms
---

### Post by Webdawgz on 2008-02-12
[SIZE="3"]Installed Lotus Domino 8 on my ubuntu box successful.
The console ran and gave me an error. i then restarted the Ubuntu box and the Domino console.

The ubuntu box rebooted, but for the life of me i cannot start the Domino console...i tried most of the forum posts no luck.

I attached a picture!!!!

Ubuntu version 7.10/Domino server version 8

Please gents and lady's!!!!![/SIZE]

---

### Post by Webdawgz on 2008-02-14
:mad:Solved the problem!!!!!:lolflag:

I download the package gawk and installed it, that removed the  error on the console.

The domino server started because of the following:

su Notes 

cd directory to /local/notes/data

exec: /opt/lotus/bin/server -jc &
it started in the jconsole view.
The following websites must get props: [http://www.windelen.be](http://www.windelen.be)
the Ubuntu How to section/catergory!!!

C u guys until the next encounter!!!

---

