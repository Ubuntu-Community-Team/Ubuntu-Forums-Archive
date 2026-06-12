---
title: "apache, how to browse files + share folders and get phpmyadmin"
date: 2005-03-06
forum: Server Platforms
---

### Post by Wicez on 2005-03-06
Hi there. 

I just installed ubuntu on my server. (i've never tried anything but windows before). 

I have installed apache, php4 and mysql on my server, and now i would like to:

 - **Install phpmyadmin.**

 - **Share the http-conf folder on the lan-network.**

 - **Know how i can access + edit the files on my apache server .**


I have had an apache server on windows, so i know the basics about apache.

---

### Post by Xanthous on 2005-06-04
[QUOTE=Wicez]Hi there. 

I just installed ubuntu on my server. (i've never tried anything but windows before). 

I have installed apache, php4 and mysql on my server, and now i would like to:

 - **Install phpmyadmin.**

 - **Share the http-conf folder on the lan-network.**

 - **Know how i can access + edit the files on my apache server .**


I have had an apache server on windows, so i know the basics about apache.[/QUOTE]


I have the same question....

---

### Post by Gandalf on 2005-06-04
first you have to make sure that you have all necessary packages so,
sudo apt-get install apache2 apache2-common libapache2-mod-php4 php4
now go and grab phpmyadmin from [http://phpmyadmin.sourceforge.net](http://phpmyadmin.sourceforge.net) extract it /var/www
for example tar -xzvf phpmyadmin.tar.gz -C /var/www
chown -R www-data:www-data /var/www/phpmyadmin_dir (or else you'll get access denied)


please explain the last 2 questions

---

### Post by LordHunter317 on 2005-06-04
There is a phpmyadmin package in universe, and you should use that unless it's too old for your needs (I'm not certain how recent it is).  

You do **NOT** want to share /etc/apache over the network.  Instead, say  what you want to be able to do and someone will suggest an alternate solution.

Assuming you want remote access to edit files and adminster your server, I recommend you install ssh and use that.  It gives you a secure, encrypted shell you can access from anywhere.

Exporting your webroot (i.e., /var/www) via something like NFS or Samba would be ok though, if you want remote file access.  But SFTP (which you get for free with SSH) is probably sufficent.

[quote=gandalf]chown -R www-data:www-data /var/www/phpmyadmin_dir (or else you'll get access denied)[/quote]Nope, this is bad advice.  It's rare you want the Apache user to own the files it serves.  In a system compromise, that means the attacker can change files at their will.

---

### Post by Gandalf on 2005-06-04
[QUOTE=LordHunter317]There is a phpmyadmin package in universe, and you should use that unless it's too old for your needs (I'm not certain how recent it is).  

You do **NOT** want to share /etc/apache over the network.  Instead, say  what you want to be able to do and someone will suggest an alternate solution.

Assuming you want remote access to edit files and adminster your server, I recommend you install ssh and use that.  It gives you a secure, encrypted shell you can access from anywhere.

Exporting your webroot (i.e., /var/www) via something like NFS or Samba would be ok though, if you want remote file access.  But SFTP (which you get for free with SSH) is probably sufficent.

Nope, this is bad advice.  It's rare you want the Apache user to own the files it serves.  In a system compromise, that means the attacker can change files at their will.[/QUOTE]
 are you sure? because i can't access non www-data files (at least group)

---

### Post by LordHunter317 on 2005-06-04
You can, if you give them world-access.  Which is generally what you do.  Configuration files being a noticable exception (they sohuld be owned root:www-data, with perms no wider than 640).  

The right way to do things is to have whatever user will be editing the files (or root if no one) own the files.  Meaning if bob will be editing the content under /var/www, he should own /var/www and it's contents.   You then give world read access to allow the webserver to server the content.

---

