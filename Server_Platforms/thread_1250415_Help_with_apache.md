---
title: "Help with apache"
date: 2009-08-26
forum: Server Platforms
---

### Post by Insomn1ar on 2009-08-26
I have just installed ubuntu server for the first time, I have installed Php5, MySQL and Apache. I installed Wordpress just to check to see if it runs smooth. I intend in keeping the site under a password so I can just use it for personal use when I am at college. I can view the site fine through LAN, using my LAN IP. But when I browse to the site from a computer outside of my network I get a page that had no images and CSS (or so it seems.)
 
Screenshots;
 
[IMG]http://img440.imageshack.us/img440/2585/lanr.jpg[/IMG]
 
[IMG]http://img22.imageshack.us/img22/944/nolang.jpg[/IMG]
 
Thanks very much to those that offer help :)
 
Edit: Images do work, my mistake. It is only the CSS I guess.

---

### Post by Insomn1ar on 2009-08-26
Alright, been fiddling around and I reinstalled Wordpress using my Iphone through my IP address (out of the network) and now it works on my iphone and displays the CSS. However it doesn't display on my computer in the network and doesn't show the CSS. I am obv doing something wrong. How do I install things so they work with both in and out of the network

---

### Post by DaithiF on 2009-08-27
Hi, from the wordpress admin screen, settings section, what do you have configured as the wordpress url -- is it the external address?  And are you trying to connect from inside your LAN using that external address?  Your router may not allow that, so one option is to add an entry to your /etc/hosts file to map your internal LAN IP address to that external url, so that from inside your LAN you *can* browse to that 'external' address.

---

