---
title: "Endless apache headaches :("
date: 2015-03-06
forum: Server Platforms
---

### Post by fzaman2 on 2015-03-06
Hey all,

So I have been trying to get Apache2 to work for the last week or so and not getting any closer to it working.  To top it off today I think I broke the whole damn thing when I tried deleting apache2 and doing a fresh install.  I got a bunch of errors when trying to ```
sudo apt-get install apache2
``` 

It looked like for some reason there wasn't an index.html file in ```
/usr/share/spache2/default-site
``` so i just created one in there.

The reason I decided to delete evverything and start over was because I had been messing around so much with the various configuration files that I didn't remember what I had done and hadn't done.

Anyway, all that to say I believe I am now at a point where I have just the original apache2 files and my dummy index.html file loaded on the server.

When I put the domain in my address bar I get nothing...IE says "This page can't be displayed".  It should be noted that his computer is on the same wireless network as the server.  

I also try going to the IP of the server and still get the same results.  I tried from outside my LAN and also am getting the same results.

Previously I has been able to get the default page from outside the LAN using the domain, however, the address bar would switch to the IP address.  Within the lan, I had to use the local IP (192.168.x.x) to get to the default page.

Now I have nothing from anywhere and a giant headache...any help is appreciated.

Thanks.

---

### Post by lisati on 2015-03-06
The proper place for an index place can vary between Ubuntu versions and how you have Apache configured. Up until fairly recently, apache looked in the folder /var/www by default, newer versions look in /var/www/html.

---

### Post by lisati on 2015-03-06
*Thread moved to **Server Platforms**.*

---

### Post by fzaman2 on 2015-03-07
ok so i ended up just reinstalling a fresh image of ubuntu and that solved the problems i had created by making all of the changes...now to start at square 1 again and get a website set up.  Will start a new thread if I have questions

---

