---
title: "Question about setting up web server"
date: 2013-01-16
forum: Server Platforms
---

### Post by nightfly13 on 2013-01-16
Dear frinds...
 
I'm very new to linux, and on the last days i try to setup an web server to with ubuntu 12.04 to host my sites to development proposes...
 
I have the instalation done and working properly (I Think !!!) :) and i use the tutorial on the link [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3) , i already setup an account on no-IP.com and i already forward my http connection on router to my server.... Now, outside of my network i call [http://my-server-example.no-ip.info]("http://my-server-example.no-ip.info/") on the browser and i can found the squirrel mail on my server as default page....
 
I setup an static IP 192.168.1.80 
 
So, what is the problem????
 
I had 3 purchased domains
 
[www.my-eplace.com]("http://www.my-eplace.com")
[www.buddysface.com]("http://www.buddysface.com")
[www.kartunes-online.com]("http://www.kartunes-online.com")
 
and i'd like to host on my own server to development proposes
 
On the company where i purchase the domains to set up the name servers, i need to add on NS1 the hostname and the IP, and for the NS2 i need to setup also the Hostame and the IP, so one of my questions is, witch hostname and ip i must place there????? I already had installed on my server the ISPConfig3, Webmin with Bind9... I setup an static IP 192.168.1.80 and to access to Webmin or ISPConfig3 i need type [https://192.168.1.8080](https://192.168.1.8080) and [https://192.168.1.80:10000](https://192.168.1.80:10000) for webmin.... 
 
I pretend to host this 3 sites on my own server, with ftp access and email, so, anyone have or know any completed and detailed tutorial to archive this... Anyone can help me with this???????
 
Best Regards
João

---

### Post by chadk5utc on 2013-01-16
If your simply setting up web services for development/testing and email you can do this with Apache2 and Postfix, Not sure why you would want ISPconfig as this is intended more for a provider. If you must have any type of "GUI" then I guess webmin is good as any although "GUI" on servers is not recommended. I use dedicated servers without additional domains so I cant assist with multiples, but Im sure their are a few here that can help.

---

### Post by nightfly13 on 2013-01-16
I install ISPConfig3 because i follow the tutorial :) Like i told, i'm very new to linux... I setup everithing but now i'm stucked on DNS's.... The company where i phurcase my domains it's asking to fill
 
NS1: Host & IP Address
NS2: Host & IP Address
 
I Don't whant become a provider, i'm using an local home DLS cable internet connection with dinamic IP's, that is the reason why i setup an account on no-IP.com... 
 
The objective of this, is learn, and setup one webhosting, only for me, not to sell hostings plans :)
 
I try allot of thinks, a read allot of tutorials, but until now with no sucess... The biggest problem for me is, witch Host and IP Address i must fill on the company where i phurcase my domains to poins the Domain for my own server, like i describe above...
 
Best Regards
João

---

### Post by spynappels on 2013-01-16
You can point the domain seller's DNS to your no-IP.com URL and set up virtualhosts on the server, this means that a request for [www.sitea.com](www.sitea.com) gets sent to your current Dynamic IP through no-IP, then is forwarded through your router to your server and the server serves the correct page based on the domain requested. A request to [www.siteb.com](www.siteb.com) would take the same path but would be served a different page by your server.

Having said this, if this is for you to learn on, I'd be very wary of opening it up to the Internet at large until you have had some experience securing and managing a web host. You can still access the sites inside your LAN, but allowing access from the Internet might cause headaches later, until you are comfortable securing it.

---

### Post by SeijiSensei on 2013-01-16
> **nightfly13 said:**
> The company where i phurcase my domains it's asking to fill
 
NS1: Host & IP Address
NS2: Host & IP Address
 
I Don't whant become a provider

Most DNS registrars will also host your nameservice records.  See if yours offers this service.

---

### Post by d4m1r on 2013-01-16
Did you setup your own DNS servers? Are they internal only (LAN) or live on the internet as well?

It sounds like you are trying to specify custom name servers for your domain so YOU become the host. I don't think this is what you want. Instead, do NOT change the name servers (ns1, ns2, etc), so it will use your domain registrars name servers. Instead just put an A-record on your domain to point to your IP. Google "domain A-record" and see if that is what you want...

---

### Post by brent1975 on 2013-01-16
Looks like you are just wanting to set up a basic web server at home that you can develope your websites. All these added extra things that you are trying to do such as ISPconfig really is not necessary unless you plan on doing a client base webhosting.  

I personally have been where you are and feel the pains. If it wasn’t for [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") and some of the others to hold my hand and help me along the way I would still be using Windows (cough)  

So this is what I have got from you. You want a web server that you can host a few websites and play around with developing them. Sure easy enough.  I actually created a little tutorial on How I set up a web server with Apache2 Mysql PHP and phpmyadmin that I use when I build a server from scratch.  [http://forums.iso-world.com/index.php?/topic/25-setting-up-a-lamp-server/](http://forums.iso-world.com/index.php?/topic/25-setting-up-a-lamp-server/)  Actually my little forums is used just for reference. 

as far as the noip.com deal have you looked into other options that don't require added software to run on your computer to stay up to date? I personally use zoneedit.com Its free for a hand full of domains and sub-domains.  I am the type of person that I don't want added crap on my computer that I don't need. With zoneedit  you would have to manually go to the site and change the IP to the new one if it changes. As of today I am with TWC I have yet to have my IP change in almost 2 years. So works for me. If you are DSL or with a cable provider that does automatic mandatory releases then perhaps what you are looking at is the choice you want to use. Just throwing out other options. 

Im sure having bind (DNS) has its advantages but for home use I really don't see the need. Keep it simple to start with. Don't get overwhelmed with all the other added mess.  I have a few decent things that you can use for basic home set up at my forums that I use alot.  [http://forums.iso-world.com](http://forums.iso-world.com). Remember these are just my personal notes and in no way professional looking haha

---

### Post by nightfly13 on 2013-01-17
Thank you all for your replys's
 
Let me place here some questions, nut please, don't laugh at me :) :)
 
[FONT=Arial][SIZE=3][COLOR=black]**_To setup DNS & Name Servers i need to do this..._**[/COLOR][/SIZE][/FONT]
[COLOR=#7f7f7f][FONT=Calibri][FONT=Courier New]
[FONT=Calibri]
[SIZE=1][COLOR=#7f7f7f][FONT=Courier New]cd /etc/bind[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=#7f7f7f][FONT=Courier New]mkdir -p zones/master[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=#7f7f7f][FONT=Courier New]cd zones/master/[/FONT][/COLOR][/SIZE]
[/FONT][/FONT]
 

[FONT=Courier New][FONT=Arial][SIZE=4][COLOR=black]**_Create one file_**[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Courier New][COLOR=#000000];[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000];BIND data file for my-eplace.com[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]; [/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]$TTL 3h[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]@ IN SOA ns1.my-eplace.com. admin.my-eplace.com. ([/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1 ; Serial[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]3h ; Refresh after 3 hours[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1h ; Retry after 1 hour[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1w ; Expire after 1 week[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1h ) ; Negative caching TTL of 1 day[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000];[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]@ IN NS ns1.my-eplace.com.[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]@ IN NS ns2.my-eplace.com.[/COLOR][/FONT]
 
[FONT=Courier New][COLOR=#000000]my-eplace.com. IN MX 10 mail.my-eplace.com.[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]my-eplace.com. IN A 192.168.1.10[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]ns1 IN A 192.168.1.10[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]ns2 IN A 192.168.1.11[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]www IN CNAME my-eplace.com.[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]mail IN A 192.168.1.10[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]ftp IN CNAME my-eplace.com.[/COLOR][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]**_Create another file_**[/COLOR][/SIZE][/FONT]
[FONT=Courier New][COLOR=#000000];[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000];BIND reverse data file for 1.168.192.in-addr.arpa[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]; [/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]$TTL 604800[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1.168.192.in-addr.arpa. IN SOA ns1.my-eplace.com. admin.my-eplace.com. ([/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1 ; Serial[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]3h ; Refresh after 3 hours[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1h ; Retry after 1 hour[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1w ; Expire after 1 week[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1h ) ; Negative caching TTL of 1 day[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]; [/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1.168.192.in-addr.arpa. IN NS ns1.my-eplace.com.[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]1.168.192.in-addr.arpa. IN NS ns2.my-eplace.com.[/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000]10.1.168.192.in-addr.arpa. IN PTR my-eplace.com.[/COLOR][/FONT]
 
**[FONT=Arial][SIZE=4][COLOR=black]_And on_[/COLOR][/SIZE][/FONT]** 
[FONT=Calibri][COLOR=#000000][FONT=Calibri]vim /etc/bind/named.conf.local [/FONT][/COLOR][/FONT]
 
[FONT=Calibri][FONT=Arial][SIZE=4][COLOR=black]**_Add_**[/COLOR][/SIZE][/FONT][/FONT]

[FONT=Calibri][FONT=Calibri][COLOR=#000000]zone "my-eplace.com" {[/COLOR][/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][COLOR=#000000]type master;[/COLOR][/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][COLOR=#000000]file "/etc/bind/zones/master/db.my-eplace.com";[/COLOR][/FONT][/FONT]
 
 
[FONT=Calibri][FONT=Calibri][COLOR=#000000]};[/COLOR][/FONT][/FONT]

[FONT=Calibri][FONT=Calibri][COLOR=#000000]zone "1.168.192.in-addr.arpa" {[/COLOR][/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][COLOR=#000000]type master;[/COLOR][/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][COLOR=#000000]file "/etc/bind/zones/master/db.192.168.1";[/COLOR][/FONT][/FONT]
 
 
[FONT=Calibri][COLOR=#000000][FONT=Calibri]};[/FONT][/COLOR][/FONT]

[FONT=Arial][SIZE=2][COLOR=#000000]_1st Question...._[/COLOR][/SIZE][/FONT]
[FONT=Arial][COLOR=#000000]Where i have my-eplace.com must be a registered domains, must be the domain registerd on no-IP or can be any name????[/COLOR][/FONT][/FONT]

[FONT=Courier New]_[FONT=Arial][SIZE=2][COLOR=#000000]2nd Question....[/COLOR][/SIZE][/FONT]_[/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]The IP's 192.168.1.10 and 192.168.1.11 must be local IP Address????[/COLOR][/SIZE][/FONT][/FONT]

[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]Sorry for this question, maybe this is easy for you, but not for me and i would like clarify some doubts...[/COLOR][/SIZE][/FONT][/FONT]

[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]**_[COLOR=black]On etc/network/interfaces i had[/COLOR]_**[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Courier New]
[/FONT][FONT=Courier New][FONT=Arial] 
[SIZE=2][COLOR=#000000]***[COLOR=#333333][FONT=Courier New]# This file describes the network interfaces available on your system[/FONT][/COLOR]***[/COLOR][/SIZE][COLOR=#000000]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]# and how to activate them. For more information, see interfaces(5).[/FONT][/COLOR]***[/SIZE]
 
[SIZE=2]***[COLOR=#333333][FONT=Courier New]# The loopback network interface[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]auto lo # Try with &#8220;eth0&#8221;[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]iface lo inet loopback[/FONT][/COLOR]***[/SIZE]
 
[SIZE=2]***[COLOR=#333333][FONT=Courier New]# The primary network interface[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]auto eth0[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]iface eth0 inet static[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]address 192.168.1.80[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]netmask 255.255.255.0[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]network 192.168.1.0[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]broadcast 192.168.1.255[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]gateway 192.168.1.254[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=black][FONT=Courier New]dns-nameservers 8.8.8.8 8.8.4.4[/FONT][/COLOR]***[/SIZE]
 
[SIZE=2]***[COLOR=black][FONT=Courier New]It's missing something or i must place something else on this file????[/FONT][/COLOR]***[/SIZE][/COLOR][/FONT][/FONT]

[FONT=Courier New][FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]**_[COLOR=black]On etc/hosts i had[/COLOR]_**[/COLOR][/SIZE][/FONT][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][COLOR=#000000][SIZE=2]***[COLOR=#333333][FONT=Courier New]127.0.0.1 localhost.localdomain localhost[/FONT][/COLOR]***[/SIZE]
[SIZE=2][COLOR=red]***[COLOR=#333333][FONT=Courier New]192.168.1.80 server1.[/FONT][/COLOR]******[COLOR=#575757][FONT=Courier New]my-server.no-ip.info [/FONT][/COLOR]******[COLOR=#333333][FONT=Courier New]server1[/FONT][/COLOR]***[/COLOR][/SIZE]
 
[SIZE=2]***[COLOR=#333333][FONT=Courier New]# The following lines are desirable for IPv6 capable hosts[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]::1 ip6-localhost ip6-loopback[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]fe00::0 ip6-localnet[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]ff00::0 ip6-mcastprefix[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]ff02::1 ip6-allnodes[/FONT][/COLOR]***[/SIZE]
[SIZE=2]***[COLOR=#333333][FONT=Courier New]ff02::2 ip6-allrouters[/FONT][/COLOR]***[/SIZE]
 
[SIZE=2]on my static IP, on this file i can set any, i must set any registerd domain or i can place ther any name????[/SIZE][/COLOR][/FONT][/FONT]

[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]Best Regards[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=#000000]João[/COLOR][/SIZE][/FONT][/FONT][/FONT][/COLOR]

---

