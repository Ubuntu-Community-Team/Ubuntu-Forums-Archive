---
title: "Cloud Server/Desktop Client"
date: 2010-01-09
forum: Server Platforms
---

### Post by leejayd on 2010-01-09
I have access to a unmanaged dedicated server on the net.  I am considering loading Ubuntu Server to this for web/mail/ftp serving.  

If I install Ubuntu Desktop to my local machine is it possible for me to administer the server using Ubuntu Desktop (using the GUI) ?  I connect to the net over ADSL.

Also, does anyone know of any guides/advice for setting up Ubuntu as a web/mail/ftp with a key focus on keeping to secure?   I know how to install LAMP but as I have root I need to learn a little more than I did when I was on a shared host.

Regards,

Lee

---

### Post by stlsaint on 2010-01-10
when you say control server from local machine i assume you are referring to [Openssh]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") in which case yes you can. As long as you have direct access to vps to install what you want you can. Something like webmin or directly ssh into vps using [key authentication]("http://www.debuntu.org/ssh-key-based-authentication") and not username/password. (You said you wanted secure)
Now as far as web hosting here are some guidelines assuming you plan on hosting yourself.

1) Make the website
2) Get domain for hosting (i use godaddy) if you want free hosting go through [DynDns]("http://www.dyndns.com")
3) Install apache2 unless you just want the entire LAMP setup but for web hosting apache2 is all you need. Install other stuff for mail, ftp, etc as you see fit.
4) Upload website files to your /var/www dir on server this is where apache will look for files to show on internet
5) Give permissions to folder: in ubuntu terminal on server run: ```
chown -R www-data:www-data /var/www/
``` Again we are working on the bases of key authentication.
6) I dont know how your managing ip address in dealing with your webhosting but if you go thru say godaddy than you need to give them the public ip that you use to connect thru to vps so they can associate 
your domain( [www.whatever.com](www.whatever.com)) to your specified vps ip.


Hope this help! :D

---

