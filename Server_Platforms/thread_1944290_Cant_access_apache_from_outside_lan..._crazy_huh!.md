---
title: "Cant access apache from outside lan... crazy huh!"
date: 2012-03-21
forum: Server Platforms
---

### Post by kjphilips on 2012-03-21
Hello and thank you for reading this!

I am clueless as to what is going on!

Installed apache, mySQL, and PHP via apt-get and had it configured so that anyone can access it on the LAN IP address 192.168.3.xx

I installed eGroupware set up and configured it and had it running correctly. Everyone on LAN can access it and work in it.

Boss says "hey I want to work on it... from home!" so...

I log in and set up port forwarding to point traffic on port 80 to 192.168.3.xx I use a web browser and type in static ip address assigned by ISP 127.52.xxx.xxx and I get access. cool, so I skype boss ip address to connect from home... blank white screen! I move to another computer in the LAN open web browser and type in 127.52.xxx.xxx and sure enough my Boss is right blank white page. I scratch my head and think what the! 

I continue to work on this slowly going mad!

So far...
Ubuntu 11.10 running apache 2.x.x (just downloaded yesterday 3/2012) Latest PHP 5 and MySQL 5

I did sudo ufw disable

router has port forwarding to correct IP Address 

no firewall on router

ISP does not block port 80 

apache configured to listen on both port 80 and port 8080

I have restarted service every time i have made a change sudo service apache2 restart

and if i try to connect to it through a browser window I can connect to both the default inex.html page and the eGroupware installation.

again when I try to access it from another machine on the lan through the LAN address in a browser it works fine but when i try to access it from outside the LAN I get a blank page, and sometimes server not found.

Is this crazy or what. I am kinda new to Ubuntu. I am kinda new to configuring LAMP but use a local development server a ton.

Anyways please help me out on this one as I really need it!

Thanks
K

---

### Post by volkswagner on 2012-03-21
Navigate to canyouseeme.org
Check port 80.
Take notice of the external ip address, does this match the ip you are trying?

Can you ping your WAN ip from outside the LAN?

Do you have allow from all listed in your vhost file for web root directory?

I did not think you could have Apache listen on port 80 and 8080.  Have you tried adding 8080 to the port forward? 

Have you tried to add the port to the end of the url when accessing outside lan?

---

### Post by kjphilips on 2012-03-21
Hello Volks,

Thanks for replying, I appreciate it!

I had checked the ports on canyouseeme.org prior to writing the OP. Both  ports 80 and 8080 are open and the external IP address matched what I  was typing.

I cannot say for sure what my vhost file says it is at work and I am at  home now. I will check that when i get back to work in the AM.

Regarding Apache listening on port 80 and 8080 I added another line to the ports file in /etc/apache/ 
virtualhost * port 80 (I think this is right) I added another line  exactly the same but added 8080 however since I posted I changed it back  due to the results on the open ports.

I have tried to ad the port to the end of the ip 127.54.xx.xxx:80 but  when I try it the :80 disappears and it just goes back to 127.54.xxx.xxx  displaying a white page. 

in the final half hour I spent going crazy I did get the white page to  stop showing up and actually got the server not found page from another  computer on the LAN. on the local machine however it still opens and  works.

I will check out the vlan file in the /var/www directory I also wonder  if I need to change my permisions on the www directory I did chmod 766  but when I ran a command to find out ownership it was not root:www not  sure if that matters or how to go about that.

I also plan on running my wamp server and configuring the port forward  to that computer on the LAN to rule out any issues with reaching a  destination in my LAN.

So what do you think? Am I on the right path?

---

### Post by spynappels on 2012-03-21
Hi kj,

How are you trying to access the site externally? Through ADSL or 3G Mobile? What browser are you using?

You can check whether the request is reaching your server by taking a t-shark trace on the server on port 80, if you see incoming requests, the rest of the inbound network path is fine, if you see data going out there may be a problem with the outbound network path. If you don't see any incoming requests, you need to check the inbound network path.

I also saw that you disabled UFW, can you just paste the output from ```
sudo iptables -vL
``` to check there is no problem with the firewall rules.

---

### Post by kjphilips on 2012-03-21
Hello and thank you for your reply.

I am back at the office now looking at Ubuntu and this forum it is 8.30am and If I were at home now I would be having a beer, I am in Asia so I suppose I cant complain to much!

Not sure how to do a t shark but I am reading about it now! I will have to get back to you on that.

here is the output of the code you asked me to run  >>> sudo iptables -vL <<< 

Chain INPUT (policy ACCEPT 604 packets, 537K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 594 packets, 89047 bytes)
 pkts bytes target     prot opt in     out     source               destination 

I have a suspicion that this is something simple.

---

### Post by kjphilips on 2012-03-21
One more thing... i did an ifconfig eth0 and it looks like my bcast address is different from my inet does that make i difference? What is bcast?

---

### Post by kjphilips on 2012-03-21
Finally figured it out...

I needed to add some direction to my apache2.conf files 

at the end of apahce2.conf i added theses lines

NameVirtualHost 192.168.xxx.xxx
NameVirtualHost 122.52.xxx.xxx

<VirtualHost 192.168.xxx.xxx 122.52.xxx.xxx>
DocumentRoot /var/www
ServerAlias aasi-intranet
</VirtualHost> 

Now all is working very well! 

Thank you volkswagner and spynappels for your input both of you got me thinking in the right direction!

The reference material which helped me out was [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

