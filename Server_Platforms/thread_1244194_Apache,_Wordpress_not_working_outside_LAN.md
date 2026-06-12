---
title: "Apache, Wordpress not working outside LAN"
date: 2009-08-19
forum: Server Platforms
---

### Post by mahalos on 2009-08-19
So here's my problem.....

I have a LAMP server running 8.10. I mainly use it for backups and a personal blog(wordpress) but i also have Zoneminder installed and have recently installed Gallery2. 
 
So to cut to the point i'm using a default apache setup with everything in /var/www. I have my server on a static ip of 192.168.1.100 and all webpages (wordpress, zoneminder, gallery2) work fine when being viewed within my LAN. Now the problem i have is i am unable to view my Wordpress or my Gallery2 page outside of my lan. I have port forwarding on the router setup fine as i can see my default apache page and i can see my zoneminder page. When i try to access Wordpress or Gallery2 i get a "Network timed out" page after about 3mins or so.

I have had a look in the apache error log, but all i have is an error about ```
[Tue Aug 18 13:04:04 2009] [error] [client 202.37.117.175] File does not exist: /var/www/favicon.ico 
```

I've been doing plenty of reading and my head is about to explode....but i have not managed to find a solution...any help is appreciated

---

### Post by Kolipoki on 2009-08-19
My first step would be asking my ISP to know if they are blocking port 80. Good luck!

---

### Post by DaithiF on 2009-08-19
are your wordpress / gallery running as virtual hosts ?  if so then maybe the servername directives aren't matching when coming in from externally.

---

### Post by mahalos on 2009-08-19
> **Kolipoki said:**
> My first step would be asking my ISP to know if they are blocking port 80. Good luck!

I know for sure they don't block port 80, but in saying that i use a different port number anyway. Thanks

> are your wordpress / gallery running as virtual hosts ? if so then maybe the servername directives aren't matching when coming in from externally.

I don't think so......but then i'm not too sure to be honest. When accessing Wordpress from inside the Lan i use 192.168.1.100/wordpress and it's all good. Both Wordpress and Gallery2 have there own folders that sit in my /var/www folder.

---

### Post by DaithiF on 2009-08-19
hang on, you say you're using a different port to 80, and yet you access wordpress on the LAN as
[http://localhost/wordpress](http://localhost/wordpress)
I don't understand, if you're running apache on a different port shouldn't you have to specify that port in your browser:
[http://localhost:xxxx/wordpress](http://localhost:xxxx/wordpress)

what port is apache listening on?

---

### Post by mahalos on 2009-08-19
> **DaithiF said:**
> hang on, you say you're using a different port to 80, and yet you access wordpress on the LAN as
[http://localhost/wordpress](http://localhost/wordpress)
I don't understand, if you're running apache on a different port shouldn't you have to specify that port in your browser:
[http://localhost:xxxx/wordpress](http://localhost:xxxx/wordpress)

what port is apache listening on?


Sorry about that, I guess i should have been clearer in my explanation. My router is set to listen to port 1980, all requests on that port are forwarded to port 80 on the server. So Apache still runs on port 80.
Connecting to it from inside the LAN is use [http://192.168.1.100/wordpress](http://192.168.1.100/wordpress) and externally i use [http://www.example.net:1980/wordpress](http://www.example.net:1980/wordpress)

hope that makes things a bit clearer.:)

---

### Post by DaithiF on 2009-08-19
ok, i see.

what URI did you set for Wordpress in its config (admin page)?  If its [http://localhost/wordpress](http://localhost/wordpress) then I think that may explain why a request coming from externally to [http://www.example.com](http://www.example.com) doesn't get served.

I think you should try setting the external address as the URI in wordpresses config, and then add an entry to your hosts file to map that address to your internal IP address, and then access the blog inside your LAN as [http://www.example.com](http://www.example.com), ie same address as externally.

---

### Post by mahalos on 2009-08-19
To my surprise I understand exactly what you are saying.....yay me!!

The URI wordpress config did confuse me a bit and I do believe it is set as 192.168.1.100/wordpress. I'm stuck at work for the next 5 hours and I can't seem to find the file that contains the URI setting via ssh,so i'll have wait until I get home to try it...

thanks for your help, hopefully this solves my problem

---

### Post by DaithiF on 2009-08-19
yes, you won't find the siteurl in the wordpress directory, its stored in the database...wp_options table.  Best to edit it via the admin page.
good luck
d

---

### Post by mahalos on 2009-08-19
Well I had it:)....and then I broke it:(

I added these lines to my wp-config.php
```
define('WP_HOME','http://example.com:1980');
define('WP_SITEURL','http://example.com:1980/wordpress');
```

and all was good. I logged into the admin page to re-enable the NextGenGallery and the NextGen Flash-Viewer plugins (I had disabled to see if they were causing problems) and now the blog won't load again!!  

Best I have a closer look when I get home. 

On a side note I've also managed to fix my Gallery2 page, editing it's config and replacing the local address with the external one....sweet

Thanks again:D

---

### Post by Raphaff on 2010-11-26
Thank you.

I was asking myself why.
I run apache on port 80 and 1690 for external access.

---

