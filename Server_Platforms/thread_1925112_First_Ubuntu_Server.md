---
title: "First Ubuntu Server"
date: 2012-02-14
forum: Server Platforms
---

### Post by blackhex666 on 2012-02-14
Oke so i want to make a server that have the following features:

Share music,photos,ect. on LAN and internet - for this i understood that vsftpd is good ...but i want to have multiple account i mean i want to have one account for some folders and other for other folders
But i head also about an app PureFTPd with MySQL witch is better?

I want to have a web server - i read the help on Apache2PHPMySQL but i want to have 2 websites stored with there own domain and i want one to be visible only on LAN

Is good to install a minimal gnome ??
O and i want to download my files using torrents i need a torrent server for this??

---

### Post by tamkt on 2012-02-14
To share on LAN, you can install samba.
You can setup 2 domain on webserver by use virtualhost.
You can install webmin, to create easy virtualhost.

Sorry bad English.

---

### Post by lykwydchykyn on 2012-02-14
There are tons of file sharing protocols available.  FTP is pretty universal, but the security is poor so most people recommend using ssh/sftp/scp for that, all of which is ready to roll if you install openssh-server.  Of course this isn't as universally supported as FTP (e.g., Windows users have to download a 3rd-party client, can't open sftp in a browser, etc).

I've set up PureFTPD and ProFTPD with the mysql backend before, it's pretty cool but there's a whole lot of "roll-your-own" involved and it's not easy for someone who's new to all this stuff.

Samba is a good option for the LAN, but it doesn't work over the internet AFAIK.

As for apache and whatnot, I'll second the recommendation for Webmin.  It makes system administration in general a lot easier, and the Apache module has great support for virtual hosts.

---

### Post by bubylou on 2012-02-14
[Samba]("https://help.ubuntu.com/11.10/serverguide/C/samba-fileserver.html") is the best option for sharing file on a LAN. You could also look into streaming option over your LAN or even the internet.

For a web server just install the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") stack when you install the server or use the tasksel  command if you have already installed Ubuntu. 

For sharing over the internet i don't recommend just standard ftp. It is incredibly insecure. Use either sftp through openssh or ftps via ssl. I personally prefer sftp since openssh is almost a necessity.

I wouldn't bother installing a gui of any kind on a server. It will only take up an unnecessary amount of resources. 

In terms of torrent clients there are a few to choose from depending on your preference. I use [transmission]("http://www.transmissionbt.com/") which has a web front end but you should see whats best for you.

---

### Post by tamkt on 2012-02-14
To share via Internet, you can research WebDAV.

---

