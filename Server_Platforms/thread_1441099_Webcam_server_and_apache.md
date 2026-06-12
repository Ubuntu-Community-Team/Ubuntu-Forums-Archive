---
title: "Webcam server and apache"
date: 2010-03-28
forum: Server Platforms
---

### Post by Lou-buntu on 2010-03-28
Hey everyone,

I'm trying to set up a webcam server I can access from outside my home. I'm fairly skilled with computers, but networking and server stuff just kills me. 

I followed this tutorial [http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

So far this is what I've got:
The webcam-server starts fine and browsing to [http://localhost:8888/](http://localhost:8888/) shows the camera feed (and when I refresh as does the image). Then I set up apache2 just as instructed and when I go to [http://localhost/webcam.html](http://localhost/webcam.html) I get the webcam stream. So that seems fine aswell. (my apache stuff is all in the var/www/ file, which I assume is default and the webcam.html is just the file that I created using the tutorial's HTML script)

Now I have no idea how to pull off the next step to enable access from the internet. I have a website through my internet provider Shaw which I normally edit using Dreamweaver and just set the FTP to Shaws (ftp.shaw.ca) and it stays on Shaws servers. Now is it possible to 'link' apache2 to my Shaw website and 'PUT' files like I would in Dreamweaver? If thats not possible, can I use something like dyndns.com and link the IP they give me there to my site?

Thx.

---

### Post by terazen on 2010-03-29
Yeah, you'd need to use some sort of dynamic dns and then on your home router, enable port forwarding for tcp port 8888 and 80 to your home server's ip address.  Get the port forwarding setup first and tested before you start the dns part.

---

### Post by waloshin on 2010-03-30
And if your running a firewall like ufw you would type ufw allow 80, ufw allow 8888.

---

### Post by Lou-buntu on 2010-04-16
Ya I have my router set up to forward the ports as you stated, but I still had no luck. I gave up and used uStream, but I will probably attempt my own server in the future. Thanks for the help though.

---

### Post by Dragonbite on 2010-04-16
So the webcam images are static with each page refresh, or is it streaming real-time?  This sounds pretty cool (and creepy ;) ).

---

