---
title: "php HELP"
date: 2009-01-15
forum: Server Platforms
---

### Post by Lori700698 on 2009-01-15
I have a php file that is called popup.php, this file works when I access it from within my network, but when I jump out on the net it won't work, it says "The requested URL /jinzora2/popup.php was not found on this server."  Now it's there, I just don't know what to do to make it work.  Is it an Apache issue, or does the file need to be somewhere else?  I just don't understand and there is no directions on Webmin on how to set up Apache for php so I can't tell what I'm supposed to do.  And I already went crazy and gave everything read & write permissions and that didn't solve a thing.
HELP????

---

### Post by spiderbatdad on 2009-01-15
this file is in the same directory as your DocRoot or a sud-directory?
so you access it as: your.domain.com/jinzora2/popup.php

possibly add the local ip to /etc/hosts

192.xxx.xx.xxx your.domain.com

---

### Post by Lori700698 on 2009-01-15
Thanks for answering me, I think I'm in over my head at this point and need to read up on the whole Apache thing!  I can't get access to my site outside of my home network, I thought it was working and had a friend try and still it's a no go!  The php would probably work if I had the thing set up correctly, so this is probably my fault.  I looked at that file and was a bit freaked out by the other two host files that allow and deny access, they are both blank with ##documenting so I don't know if this needs to be changed or what.

---

### Post by spiderbatdad on 2009-01-15
ok good luck. It isn't too hard, but learning as much as you can is a good thing. Of course if you have a router, you will have to forward port 80 to your local machine for apache to be accessed outside your lan.

There are loads of good apache how-tos on the web.

---

### Post by hockey97 on 2009-01-16
dude... go on google and search what is my external ip address.

have your friend type that ip address in the browser and after the ip do the /popup.php 

so it would be like 207.215.1.23/popup.php 

it should work if not then your apache server is not config right.

but it should work if your server is config right and you don't have a domain name then your external ip will be the one to respond.

hope this helps.


it depends on how you config your apache server.

now if you have a domain name then the url would be like this...

[www.mydomain.com/popup.php](www.mydomain.com/popup.php) 

hope this helps any.


oh and also you need to have apache know what folder is your default area for each website.

like you can make a folder named  domain.com  and then have that as default.

so any files in that foldr would be accessed by using the url like  [www.mydomain.com/yourfile](www.mydomain.com/yourfile) here.


now lets say in the folder domain.com you add another folder called ads, and another one that is called photos.

so if you want to get a photo from the photo folder your url will be like:

[www.mydomain.com/photos/man.jpg](www.mydomain.com/photos/man.jpg)  

it would look something like that.

without a domain name it would be your external ip address you would use instead of a domain name.

looks something like:  207.94.13.63/photos/man.jpg

hope this helps.

---

### Post by Lori700698 on 2009-01-16
Thank you!  It was my own fault, I had was using the actual server IP (behind the router one) instead of my honest IP from my internet provider.  I went to DyDNS.com and checked it there and tried the one it actually showed and that was the whole problem.  Pointed my DyDNS to the correct IP and jammed to my jinzora music server all day at work, what a nice day I had!  I have many more questions about the Apache web server.  My next project will be how to FTP files over, although now I can do it very easily at home with Webmin, but sometimes I need to do it from other places.  Webmin is so stinken easy it almost makes me feel like I'm cheating learning this stuff!  I'm going to look at the email thing too, don't know how useful it will be for an actual home server but I'd like to know how anyway!  The php file does work correctly on the *80 port, but it didn't work right when I tried to open *85 port so something wasn't right, just not sure what.  I opened and forwarded all kinds of ports trying to make this work, now I need to go close them up!

---

### Post by hockey97 on 2009-01-17
well, web server stuff supposed to be on port 80 or 88.

that is default stuff.

just want to warn you ahead of time with the mail server that it's complex.

I want to tell you that you can't send e-mails to aol,msn,yahoo without having a static ip address and a reverse host lookup. else your e-mails will get blocked.

just saying cause I am currently have that problem so I changed my internet to get a static ip address. So I can have my own mail server.

---

### Post by Lori700698 on 2009-01-17
Thanks for the info!  My IP is static so that's one less thing I will need to tackle.  As for the port thing, I didn't realize that you couldn't use what you wanted, I always knew *80 was for web, but I thought you could use others optionally.  I'm just glad it's working, if you wouldn't have mentioned external IP I would have probably still been sleepless trying to figure it out!

---

### Post by Barrucadu on 2009-01-17
You can use other ports, you just have to ensure that they're forwarded in your router, not blocked by any firewalls or something, and that the application knows to listen on that port.

---

