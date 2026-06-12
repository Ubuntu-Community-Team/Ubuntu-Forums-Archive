---
title: "An intresting situation(DNS server questions)"
date: 2009-08-22
forum: Server Platforms
---

### Post by munchi3s on 2009-08-22
Well in a previous [post]("http://ubuntuforums.org/showthread.php?t=1245839&highlight=webdav+ubuntu+apache&page=2") I needed help setting up a webserver with webdav I got it all figured out. Well this webserver was for a school lab that I'm "in charge of". I plan to have a Email server, a DNS server, a webserver, a proxy caching server, and a terminal server.
I'm using ubuntu because I feel that it is way more fexible then windows when it comes to servers. Anyways I question is if this is possible. I'm wondering if its possible to set up domain names and a DNS server that services lan IPs. Some of the computers in this lab that I'm "in charge of" will have some ubuntu boxes and some windows XP boxes and with my endevours working with webservers both in windows(IIS 7) and Ubuntu (apache 2) the seperate systems have a hard time seeing eachother. Windows computers will associate windows computer names with their IP but wont associate Ubuntu comptuer names with their IPs this makes things terrible difficult when you need to check the webserver for updates and you have to type in and remember the whole IP. I want to know if its possble to set up the DNS server in a LAN setting so I, on a windows box, can type in "it04netwokring.com" and it take that directly to the computer that is hosting that server which would be 192.168.0.13

I'm hoping that someone can point me to a tutorial that accomplishes this.
Thanks to anyone with any information on this subject:).

---

### Post by munchi3s on 2009-08-22
Now I feel like a total idiot. I realize that I have already set up one of the DNS servers that I wanted and it worked rather well I have able to connect to the domain name that works for LAN. Its really interesting how useful ubuntu really is.

---

### Post by cariboo on 2009-08-22
Depending on the number of computers on the network, you may want to have a look at dnsmasq, it is in the repositories.

---

### Post by Bucky Ball on 2009-08-22
Yes, and how really interesting networking is. Don't forget, Unix thrives in a networking environment; some say it should have been left there as it was never really designed for what we use it for, domestic desktop computing with GUIs!

---

### Post by munchi3s on 2009-08-23
> **cariboo907 said:**
> Depending on the number of computers on the network, you may want to have a look at dnsmasq, it is in the repositories.

I may look at that. There will be about 70 - 90 computers total but only around 30 at any one time. But the DNS/apache webserver I have set up a home is amazing. I'm seeing how many types of servers I can fit onto this machine. The proxy server on here is going to be the most used. The DNS server is only for the webserver with the 1 website other then that it will forward to the normal DNS servers. I also plan to have DHCP on here as well.
I may decide later on to have 2 or even 4 servers for everything, but for right now I'm just testing all of the servers I can set up. I'm working on a squid proxy server right now and then I will be working on DHCP.

---

