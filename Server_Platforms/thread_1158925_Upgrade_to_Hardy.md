---
title: "Upgrade to Hardy"
date: 2009-05-14
forum: Server Platforms
---

### Post by Koybe on 2009-05-14
Hello,

Gutsy sources are no more accessible. Is it still possible to upgrade a server from Gutsy to Hardy and get the long time support version?

Thank you

---

### Post by capleton on 2009-05-14
Couldn't you just go to [http://www.ubuntu.com/getubuntu/download-server]("http://www.ubuntu.com/getubuntu/download-server") and select the LTS version, 8.04?

Or if you prefer bitTorrent, I'm sure you could find it still find it active somewhere. ;)

good luck

---

### Post by Koybe on 2009-05-14
Sorry but my question is about upgrading from an existing system... not installing from a CD.

---

### Post by hansdown on 2009-05-14
Yes you can Koybe.

This tutorial explains it faster than I can.

[http://ubuntu-tutorials.com/2008/04/23/how-to-upgrade-ubuntu-710-to-ubuntu-804/](http://ubuntu-tutorials.com/2008/04/23/how-to-upgrade-ubuntu-710-to-ubuntu-804/)

---

### Post by kaspar128 on 2009-05-14
I have the same question. I'm running a Gutsy-server at my boss his office. It's a file-server that uses samba, rsync(&ssh) to obtain the latest files that my studio produces(animation-footage). I would like to install proftpd&pptpd, so that other 'employees' can work at home. Unfortunately the gutsy-support has ended, so i can't install new software.
I know that it is possible to upgrade an existing system but I am afraid that it will "destroy" settings and other stuff that is installed. I'm looking for a green light on this one, so if anyone can confirm that upgrading works flawlessly(and know the proper commands so i won't have to google :-) then I would be a happy person..

---

### Post by hansdown on 2009-05-14
Hi kaspar128.

Are you able to back up all your data?

Upgrades are not without surprise problems.

If you don't have a seperate home partition, you will lose data.

Please see the link in my post above for a tutorial.

---

### Post by kaspar128 on 2009-05-15
The homedir is on the same disk and contains about 200gb of data. Luckily all of it is backed-up thanks to rsync and will hopefully be restored by it.
Thanks for the reply Handsdown, I now know what to do.. I let it  upgrade and see what remains of all my settings/cronjobs and stuff.
Strange that the process will destroy data in the homedir.

---

### Post by hansdown on 2009-05-15
You should be good to go kaspar128.

---

