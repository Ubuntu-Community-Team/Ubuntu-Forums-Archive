---
title: "I cant block any website by using squis server on ubuntu throw webmin"
date: 2010-11-09
forum: Server Platforms
---

### Post by sipetron on 2010-11-09
Dear All please help 
I need ro know how to block sites using squid server on ubuntu with webmin please help I. Need it toooooo much

---

### Post by Vishal Agarwal on 2010-11-09
Do u have squid module installed in webmin ?

---

### Post by sipetron on 2010-11-10
yes i have and i can control by it but i cant block any site

---

### Post by viperce on 2010-11-10
if you go into webmin click on squid proxy server then click on access control..under access control lists select URL Regexp from the drop down menu then click create new ACL
under ACL name give it a name blocked select Separate file set path /etc/squid3/blocked then click save

click proxy restrictions, click add proxy restrictions, in the left hand column click the name you gave it blocked or whatever then click deny and click save

on the right hand side of the proxy restrictions list u will see arrows pointing UP nexto the restriction u just added

move the restriction up the list untill it is above your client addresses (ip range) that should work
if you want to add sites to the blocked list just go to access control click on the blocked acl u created & add the address to the list apply & it will block the site.

---

### Post by sipetron on 2010-11-11
its didnt work my friend 
do u have other way to do it ??

---

### Post by viperce on 2010-11-11
are your clients connecting to your squid proxy server? if you stop the squid proxy server are they still able to access the internet?

---

### Post by sipetron on 2010-11-11
yes of course , they cant browsing if i stop it

---

### Post by viperce on 2010-11-11
[IMG]file:///C:/Users/ADMINI%7E1/AppData/Local/Temp/1/moz-screenshot.png[/IMG]Acl List
[IMG]http://img593.imageshack.us/img593/1782/acllist.jpg[/IMG]
your proxy restriction you added should look like this
[IMG]http://img169.imageshack.us/img169/9046/blockedx.jpg[/IMG]



and your proxy restriction should be around here in the list

[IMG]http://img183.imageshack.us/img183/9655/proxyrestrictions.jpg[/IMG]

---

### Post by sipetron on 2010-11-12
That's what I did. But the virison that am using its 2.7 .is that make any deferant

---

### Post by viperce on 2010-11-12
no it shouldn't make a difference, but Im using squid3 & created that server yesterday to check & it worked first time.

Can you post screen shots of your Access control list & proxy restrictions??? 
then maybe i could help u.

---

### Post by sipetron on 2010-11-13
i make an virtual server and its worked but i have something if u can help me with it 

can i make it if the adders had any word of the listed block it ???
like if i make 'tube' for example block every thing content this word

---

### Post by viperce on 2010-11-15
if u add a word to ur blocked acl squid will block it for you.

[IMG]http://img254.imageshack.us/img254/4892/blockedlst.jpg[/IMG]

---

### Post by viperce on 2010-11-15
just keep in this in mind if you add words to your blocked list any site containing that word will be blocked so if you add the word sex to your blocked list, sites like 
[www.sussex.ac.uk](www.sussex.ac.uk)

will not be accessible you would need to create another ACL called "safe_sites" 
or whatever you would like to call it and set the proxy restriction to allow. 
Then move it up your proxy restrictions list above your blocked list. 
So if you have sites you would like them to access you add
the site to the "safe_sites" list

---

### Post by sipetron on 2010-11-15
thank you for helping me.  It was very useful 
I have one more thing 
How to block all messengers??

---

### Post by s1nch4n on 2010-11-15
> **sipetron said:**
> thank you for helping me.  It was very useful 
I have one more thing 
How to block all messengers??
if you set squid as transparent proxy, you can block all IM client incoming traffic thru' your linux machine with iptables... and only allow localhost for incoming traffic to squid port... 

if your squid not in transparent proxy, you need to block IM server with squid ACL [more easier in my opinion]... or use dansguardian, squidguard or OpenDNS... or use iptables [need more effort]...

---

### Post by sipetron on 2010-11-15
I'll tray it and I'll tell you if it work or not
Thank you to every thing

---

