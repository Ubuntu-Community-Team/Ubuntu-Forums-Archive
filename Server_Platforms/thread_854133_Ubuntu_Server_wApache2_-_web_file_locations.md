---
title: "Ubuntu Server w/Apache2 - web file locations"
date: 2008-07-09
forum: Server Platforms
---

### Post by philtrim on 2008-07-09
I am new and experimenting with the latest Ubuntu server edition with Apache2.  I have the default web site working ok.  I can even hit it from outside my lan (using DynDNS).  My biggest problem is knowing where the web files are stored.  I can find the default Index.htm in the /var/www folder.  But, when I browse FTP (say from inside the lan from a Windows box - [ftp://servername/](ftp://servername/))  It shows a completely different location. (I don't see this folder or above mentioned Index.htm file.) I have checked the apache2.conf file, it it only references /var/www folder, this is driving me crazy.  I have also searched in other Apache2 config files, and see NO reference to any other webroot, directory etc...

Please advise...I am getting a bit frustated...
(but, I admit I enjoy the challenges (and they are many) of the
Linux world.)

Thanks.
:confused:

---

### Post by windependence on 2008-07-09
The web files ARe in /var/www. If you have anb ftp server running, we would have to know what ftp server you are running to know where the files are stored.

-Tim

---

### Post by philtrim on 2008-07-09
Thanks windependence.

Does the default Ubuntu LAMP install include a default FTP server?

If not, what would you recommend for an FTP package.

I tried to install the Proftpd, but recd an error that it could not find (or something similar)

Thanks

---

### Post by windependence on 2008-07-09
vsftp, but if you are only uploading your web files you don't need an ftp server at all. You can just use WinSCP from a Windoze machine or Nautilus or Konqueror from a Linux box.

-Tim

---

### Post by Kolipoki on 2008-07-09
Philtrim, I've been using WinSCP for over 3 weeks now and it's great. If I'm not wrong, from a LAN you won't need the "ftp://" path. Just put in the server (host) name + user + pw and you should be good to go. I hope this helps.

---

### Post by philtrim on 2008-07-09
I noticed the webfiles default is /var/www, but i also noticed
that my files are somehow tied to /home/username, and I did not see ANY reference to this /home/user in any Apache2 config files.

Furthermore,  if I was designing a web site, is it best to leave it in the /var/www or should I CHANGE the Directory/webroot to point to this /home/username folder?  (I only found it was pointing to this latter directory by connecting from a Windows box w/Wise FTP, and when I connected to the hostname (servername) it automatically takes me to this /home/username (as opposed to the /var/www)  hence my original question....
(Does this do this becasue I authenicated to FTP (with my user name, perhaps?)  Maybe I am beginning to catch on...

Thanks
(dazed, and confused, but loving a new challenge)

Philtrim

---

### Post by windependence on 2008-07-09
I think you are still a bit confused. You must have an ftp server running if you are connecting via ftp. One has nothing to do with the other. Apache and ftp are two separate applications. Your *ftp server* is pointing at the user's home directory. That is the default for most ftp servers out there.

-Tim

---

