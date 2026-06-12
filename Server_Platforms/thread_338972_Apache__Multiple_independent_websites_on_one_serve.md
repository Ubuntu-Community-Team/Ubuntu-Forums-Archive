---
title: "Apache : Multiple independent websites on one server?"
date: 2007-01-15
forum: Server Platforms
---

### Post by Littleweseth on 2007-01-15
G'day;

I'm currently working on several web development projects, and I'm looking for a way to separate all of my projects out of /var/www. The goal is to have each project in it's own folder, believing that its root folder is the project folder (not /var/www) for the purposes of PHP includes and so forth.

There is probably a moronic solution to this, but if memory serves, in the typical [http://server/~user](http://server/~user) setup, a PHP page referring to '/' will still get [http://server/](http://server/), not [http://server/~user](http://server/~user). Please correct me if i'm wrong (this would be a very nice solution.)

Also, is there a better way to get my files onto my local, private webserver than ftp? FTP tends to be finicky, delicate, and quanta has already nuked one project off my hard drive via a slight misconfiguration (inspired, of course, by the crappy error messages quanta gives and having nothing at all to do with me or the time of night :) )

NFS strikes me as a nice solution (transparent, no separate 'upload' stage) but i'm not sure how to rig the permissions on /var/www to make it all work.

Thanks;
-lws

---

### Post by TSMJ on 2007-01-15
SSH server comes with an SFTP server built in which you could access through a GUI such as WinSCP. Otherwise look at Samba for Windows type SMB network sharing. You have to set permissions on the folder and when you enable the share too.

There are 2 ways to host multiple sites, UserDirs like you mentioned and VirtualHosts, which might be what you're looking for. VirtualHosts allow you to set up multiple virtual servers on the one Apache server, each with seperate configs. For this you'll either need multiple IP's (Public ones for Internet use) or at least one domain name (and use whateveryoulike.domain.com for each). You can also run them on different ports if you've only got one IP.

Hope that give you some ideas.

---

### Post by Littleweseth on 2007-01-16
Virtualhosts sound like The Way Forwards. What are some good spare ports to use? I was thinking along the lines of 8081, 8082, etc.

In my experience, samba is even worse and badder than ftp for configuration woes :) I think NFS really is /the/ solution, so i might tinker around with permissions until i can bash it into working.

---

### Post by tr333 on 2007-01-16
> **Littleweseth said:**
> Also, is there a better way to get my files onto my local, private webserver than ftp? FTP tends to be finicky, delicate, and quanta has already nuked one project off my hard drive via a slight misconfiguration (inspired, of course, by the crappy error messages quanta gives and having nothing at all to do with me or the time of night :) )
have you considered using rsync?  i just set this up yesterday on my mac so i have a single command to sync a whole directory onto a server on my lan.
```
rsync -av localwebdir/ user@server:/var/www/
```
rsync also has the benefit of only transferring files that have modified, so if you have 100+ web pages/images/etc and you only update 2 or 3 pages, then only those 2 pages get sent to the server.

one thing to note with this is that the /var/www/ directory and subdirectories must be owned by the user that is logging in via rsync.  since rsync uses ssh for its connection, you can use public/private key login with ssh from your local box and not have to type a password when updating the web folders on the server!

read "man rsync" for more info on the exact syntax of the command.

---

### Post by Littleweseth on 2007-01-16
tr333 : do you have a passwordless ssh setup guide to hand? It'd be useful for more than this, since there are many ssh server i connect to on a regular basis.

and i'm off, because my dialup is about to expire :)

-lws

---

### Post by Wim Sturkenboom on 2007-01-16
You can either use name-based virtual hostig or ip-based virtual hosting. The first one will not work if you use https.

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

PS There is no need for the use of different ports

---

### Post by Littleweseth on 2007-01-16
> PS There is no need for the use of different ports

Actually, there is - this server is a single, local machine with only one IP, and I don't want to set up a bunch of redundant names for it in my /etc/hosts :)

RE passwordless SSH; I have that set up now, and it was very easy :) Here;s the link I used;[http://www.ece.uci.edu/~chou/ssh-key.html](http://www.ece.uci.edu/~chou/ssh-key.html) - about three steps.

---

### Post by Brazen on 2007-01-16
> **Littleweseth said:**
> > PS There is no need for the use of different ports

Actually, there is - this server is a single, local machine with only one IP, and I don't want to set up a bunch of redundant names for it in my /etc/hosts :)

RE passwordless SSH; I have that set up now, and it was very easy :) Here;s the link I used;[http://www.ece.uci.edu/~chou/ssh-key.html](http://www.ece.uci.edu/~chou/ssh-key.html) - about three steps.

The names don't go in /etc/hosts, the names go on your dns server.  What is the reason for wanting each application to think it is in the website's root?  You might just be able to Alias all the applications into a single website.

---

### Post by armware on 2007-01-16
i did this once with apache. it required some editing of apache conf files and what have you, but once i figured it all out, i had  6 web sites running locally as 127.0.0.1, 127.0.0.2, 127.0.0.3... and all was well.
i'd love to tell you how i did it, but i can't remember at all and have since reinstalled kubuntu without apache, so my conf files are gone. if you want some help setting it up, i'm sure it'll come back to me rather quick.

---

### Post by Wim Sturkenboom on 2007-01-16
> **Littleweseth said:**
> > PS There is no need for the use of different ports

Actually, there is - this server is a single, local machine with only one IP, and I don't want to set up a bunch of redundant names for it in my /etc/hosts :)

As far as I understand, you have to specify the port in the URL (I've never used this). If that's the case, it's your call; adding to either DNS or /etc/hosts is a one time job. Entering a port number in the URL has to happen everytime. And in your webpages you have to add the port number each time as well.
And if the pages get published on the internet you probably have to change all URLs in your pages back to port 80 (although with PHP this can be done quite easily).

---

### Post by Littleweseth on 2007-01-17
> And if the pages get published on the internet you probably have to change all URLs in your pages back to port 80 (although with PHP this can be done quite easily).

eep!

Still, it stands that i'm on a home-type local area network - that is, it's all either DHCP or 192.168.0.nnn static IP's. I wouldn't know how to set up DNS services anyway (and it'd probably interfere with my internet sharing.)

> i had 6 web sites running locally as 127.0.0.1, 127.0.0.2, 127.0.0.3...
> and all was well.i'd love to tell you how i did it, but i can't remember
> at all and have since reinstalled kubuntu without apache, so my conf
> files are gone. if you want some help setting it up, i'm sure it'll come
> back to me rather quick.

This is the kind of thing that would be cool :) If you can remember (or if someone else knows) how to replicate this, that would be sweet.

tyvm;
-lws

---

### Post by Mike'sHardLinux on 2007-01-17
Am I missing something?

One of my servers only has 1 IP address, and runs several Virtualhosts, Name-based hosting AND I use HTTPS. I don't have to specify multiple redundant names in DNS or /etc/hosts or whatever. I don't have to open any special ports, or add IP addresses. Every time I set up a new VirtualHost, I just add a few lines in the Apache config file, and point the new domain at my public IP.

I use the /home/*/public_html method to host all my virtual sites. This allows a lot of flexibility, because you can have multiple users, and give each one access to their virtual site; you can chroot the whole virtual "home" with Jailkit to separate the FTP/SFTP users from your main system, and you CAN use HTTPS with name-based hosting, it's just that it's limited, mostly because you're only running 1 IP address, but you can use the same HTTPS for all your virtual sites.

---

### Post by Littleweseth on 2007-01-17
>  	Am I missing something?

The bet's that you have it right and that _i_ am missing something :)

In your method, if a user references /index.htm as a href in a webpage, does that take them back to the Real Webroot, or the root of their own little chroot jail?

---

### Post by Wim Sturkenboom on 2007-01-17
> **Mike'sHardLinux said:**
> Am I missing something?I think you are missing something (unless you have only one https site). Have you ever checked the certificate that is shown by your browser for the different sites. It will tell you that it does not belong to the site (except for one).

---

### Post by Mike'sHardLinux on 2007-01-17
> **Wim Sturkenboom said:**
> I think you are missing something (unless you have only one https site). Have you ever checked the certificate that is shown by your browser for the different sites. It will tell you that it does not belong to the site (except for one).

I only have 1 true HTTPS site with a cert, BUT, a LOT of web hosts do this with their hosting packages which don't include a dedicated certificate, and it actually works pretty well when you're using a bona fide signed cert, like from Verisign or Comodo, etc....  So I am not missing anything in that respect :) 

I was referring more to the overall suggestions that have been made, ie, specifiying a ton of different "localhost" IP addresses, opening different ports for each site, etc. Those all seem like a pain to implement, and being able to use a url vs. only an IP addy seems more user friendly.

Maybe, one downside to this technique is that you have to specify a different domain for each virtual host, as opposed to website.net/~user, but often this is what the user wants.

---

### Post by Mike'sHardLinux on 2007-01-17
> **Littleweseth said:**
> >  	Am I missing something?

The bet's that you have it right and that _i_ am missing something :)

In your method, if a user references /index.htm as a href in a webpage, does that take them back to the Real Webroot, or the root of their own little chroot jail?

index.htm, or even just specifying the url without an index page will take them to the root of **that** specific site. You see, each virtual host has its own webroot. This isn't an unusual setup. As far as I know, it's a standard setup for virtualhosts. I can post a sample apache2.conf/httpd.conf. It'sprobably  simpler than you think.

---

### Post by Brazen on 2007-01-17
I'm still wondering why you are wanting to set up multiple sites?  You say this is for web apps that you want to think are in the root of the web site, right?

If this is just to satisfy a limitation with the web app, you could use proxy requests within the local machine.  You would have one site that is accessible from the world, and multiple sites accessible only from the local machine which you'll get to through proxy requests, ie:```
<VirtualHost 192.168.0.10>
   ProxyPass /app1 http://localhost:81
   ProxyPassReverse /app1 http://localhost:81

   ProxyPass /app2 http://localhost:82
   ProxyPassReverse /app2 http://localhost:82
</VirtualHost>

<VirtualHost localhost:81>
   ...
</VirtualHost>

<VirtualHost localhost:82>
   ...
</VirtualHost>
```

This way you can access them both through the same server name and address, but the apps will think they are running in the root of their own virtual hosts.  You would just access the apps through [http://server/app1](http://server/app1) and [http://server/app2](http://server/app2).

---

### Post by Littleweseth on 2007-01-18
Brazen, you are my hero. Thankyou, that's *exactly* what I needed to be done.

I'll try it out and see how it works.

---

