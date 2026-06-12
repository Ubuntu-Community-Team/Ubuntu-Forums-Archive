---
title: "DHCP3 Help Needed: Details Inside."
date: 2011-02-15
forum: Server Platforms
---

### Post by bfh on 2011-02-15
Hello new to server edition of ubuntu but im having some trouble now.


> DHCP3 is running fine, no problems with that.

My problem is what i try typing in a the domain name of the new webpage i made doesnt work, and when i even type in the router address for the website, nothing their.

So under this cercumstance im guessing that dhcp3 doesnt have a folder dedicated to web development. so if any 1 can help me out here lmk:


here is the code for my /etc/dhcp3/dhcpd.conf file.

```


ddns-update-style none;
option domain-name "mySitewashere.ca";
option domain-name-servers 24.153.23.66, 24.153.22.195;
default-lease-time 86400;
max-lease-time 604800;


log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
   range dynamic-bootp 192.168.0.2 192.168.0.75;
   option broadcast-address 192.168.0.255;
   option routers 192.168.0.1;
}

```also not sure what log-facility local7; does or if its really needed ?




So basicly what im wondering is how to set up a folder where my html files are kept, and is that 1 line is really needed ?




>> Edit:

Is dchp even support the web hosting part ? gonna use html files.

or do i need to get a different software ?

if so, lmk links to good straight forward // very noob tutorials :)

would like to keep using dhcp3 though, so merging tutorial would be nice (if needed)

Thanks

>>Edit #2:

Ubuntu 10.04 is version forgot to add that in.

---

### Post by gobbledigook on 2011-02-16
where are you putting the html files? 

they should be in /var/www/

---

### Post by bfh on 2011-02-16
> **gobbledigook said:**
> where are you putting the html files? 

they should be in /var/www/

> Just finished installing lamp so i got the folder now.

>but the webpage still wont load when i type in url.
currently switch over to opendns dns servers
and restarted dhcp, yet no luck.

I can type in my ip address provided by router to get onto the webpage.

any ideas ? am i doing something wrong ?
wondering if i have to somehow link the dhcp file to the webpage folder ?

thanks



OR...

its working fine just that i have to be outside my network to get onto the webpage ?
ei:

cant login to server within my home network using my public ip address instead must use router ip address.

Edit : Just tested outside of network, doesnt work (second part > "OR" section)











Edit#3:

Just remember to add portfowarding // dmz for the server, so added that.

going to test if this helps it out and works now, maby that was my prob.

but question for port forwarding is the program that i should allow connect - Options:

dhcp3
dhcpd
dhcp

For now im leaving dmz open till i can figure which to use also:

tcp
udp

or both ?

Also what ports:

67-80

or 67
or 80 ?

cuz when i run command I get:   grep bootps /etc/services

I get following:
```

bootps          67/tcp                          # BOOTP server
bootps          67/udp


```

---

### Post by bfh on 2011-02-16
Okay well new, most has been setup > might be missing something but not sure what.

If you try to connect itll just hang, itll show u the ip address of my server but no luck
loading webpages.

>Currently Installed:

dhcp3 [http://www.howtoforge.com/dhcp_server_linux_debian_sarge](http://www.howtoforge.com/dhcp_server_linux_debian_sarge)
bind9 [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
apache web server


<< not sure whats wrong, lmk if u can help, tutorials i used are beside the
software i have had installed.

not sure whats wrong but this is the furthest i got so far.

> ip conversion works fine, but failing to load webpages.

Edit:


It Works Fine now

---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
DHCP has nothing to do with URL's or Domain Names, this is all done via DNS, so basically, just purge dhcp3-server.
apt-get purge dhcp3-server
and for configuring DNS - thats a different story, but try this:
[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)

---

