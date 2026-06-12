---
title: "Debugging a new apache2 installation"
date: 2006-12-03
forum: Server Platforms
---

### Post by RLB South on 2006-12-03
I've recently installed apache2 on a fresh Ubuntu Desktop 6.10 using the Ubuntu Server CD. Everything seems to be in the right place, but I cannot get apache to answer external HTTP requests for my domain.

The steps I have taken so far:
1) created zone records with my domain registrar to associate my domain (nsymbol.com) to the IP address of my cable modem (note that I also have a router between the cable modem and my Ubuntu machine, and it has a different IP address than the cable modem)
2) modify /etc/apache2/sites-available/default to set DocumentRoot to a directory under my home folder
3) created an index.html file in this directory
4) started apache in etc/init.d using "sudo apache2 -k start"

I get an error saying "Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

I then test the localhost connection using: [http://localhost](http://localhost) and get the index.html I wanted to display. So far so good.

However when I try to browse to the site using Firefox with [http://www.nsymbol.com/](http://www.nsymbol.com/) the browser times out after a few minutes. I've tried to find an answer in the docs and Google but have come up empty.

Am I missing a step in the configuration process, or are there any good ways to debug this problem? Any pointers or links to useful information would be most appreciated.

Thanks

---

### Post by mssever on 2006-12-03
> **RLB South said:**
> I've recently installed apache2 on a fresh Ubuntu Desktop 6.10 using the Ubuntu Server CD. Everything seems to be in the right place, but I cannot get apache to answer external HTTP requests for my domain.

The steps I have taken so far:
1) created zone records with my domain registrar to associate my domain (nsymbol.com) to the IP address of my cable modem (note that I also have a router between the cable modem and my Ubuntu machine, and it has a different IP address than the cable modem)
2) modify /etc/apache2/sites-available/default to set DocumentRoot to a directory under my home folder
3) created an index.html file in this directory
4) started apache in etc/init.d using "sudo apache2 -k start"

I get an error saying "Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

I then test the localhost connection using: [http://localhost](http://localhost) and get the index.html I wanted to display. So far so good.

However when I try to browse to the site using Firefox with [http://www.nsymbol.com/](http://www.nsymbol.com/) the browser times out after a few minutes. I've tried to find an answer in the docs and Google but have come up empty.

Am I missing a step in the configuration process, or are there any good ways to debug this problem? Any pointers or links to useful information would be most appreciated.

Thanks
First, I would make sure that nslookup returns the correct external IP address. I got 68.148.104.37. Is this correct?

Next, check your router's settings. You normally have to explicitly tell routers to allow port 80 through. I suspect that this is your problem.

Failing all that, try to browse to your site using your internal IP (192.168.1.100 or whatever it is--not localhost or 127.0.0.1).

The fully qualified domain name isn't serious, but you can set it in /etc/hosts.  Find the line that begins 127.0.0.1 and make the first entry your FQDN. Separate multiple entries with a space. Note that you need to keep localhost as one of the entries or you could experience breakage.

---

### Post by tturrisi on 2006-12-04
Use your router port-forwarding to forward port 80 to the private ip address of the server: 192.168.x.x.
If no joy, then your isp may filter port 80 (disallow it) and you will then have to confif apache to listen on a different port in /etc/apache2/ports.conf, such as 81 or 8080.  Then reset port-forwarding.

---

### Post by RLB South on 2006-12-05
Thanks guys

Short story: port forwarding worked.

Longer story for anyone else trying to solve this:
1) gathered info using (System/Administration/Network Tools)
 - static IP from Traceroute tab
 - mask from Netstat tab, Routing Table Info, Netmask
 - gateway from Netstat tab, Routing Table Info, Gateway
2) set a static IP address in Ubuntu (System/Administration/Networking)
 - on the Connections tab select the Wired connection and view properties
 - set a static IP using the info gathered above
3) could not log in to my router so I reset to factory defaults using a paper clip
4) set the Virtual Server settings of my DI-604 router to always forward the private & public port 80 to my static IP
5) successful test!

Of course I left out the part about screwing up the wireless router that was connected to my wired router (once I reset the wired router to factory defaults it's IP changed). Still need to fix this...

If anyone sees a mistake in how I gathered the info listed above, or has any other suggestions, please jump in.

Lots more to learn, but at least I got my "Hello world" moment! As a long-term Windows user (who is now switching), I can say Ubuntu is a very impressive system and I can't imagine going back.

Thanks again for the help.

---

