---
title: "Hostname, Hosts, ServerName... in a production server"
date: 2008-08-21
forum: Server Platforms
---

### Post by ngmachado on 2008-08-21
Hi, 

I've read a lot about hostname, hosts and apache servername and everyone seems to have a different idea about them.

What I have:

3 domains:
[B]   myname.com
   mycompany.com 
   mypet.com[/B]

1 static IP address provided by my VPS company:
    **123.456.789.000**

I'll host all the 3 domains/sites on my VPS and my registrar will be responsible to manage the DNS stuff (no DNS server). 

I want my server to be called:
   **ServerOne**

Now my questions:

1.What should I write in /etc/hostname?

2.What should I write in /etc/hosts?

3.Where and what should I write to prevent the "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" message after installed Apache?

4.In my development server, I can open a browser to check if "localhost" (apache) is working correctly. What CLI utility should I use through SSH to "ping" "localhost"? Wget? Is there anything simpler?

I hope you can enlight me on that. Thank you very much.

---

### Post by Titan8990 on 2008-08-21
Your machine isn't behind a router, firewall, or another server?

---

### Post by windependence on 2008-08-21
Fully qualified domain name:

```
SeverOne.myname.com
```

Hostname:

```
ServerOne
```

/etc/hosts is for defining aliases of the OTHER computers on your network so that the server can identify them by name instead of IP address. Example entry below:

```
192.168.2.5   somethercomputer.myname.com   someothercomputer
```

For number 4. you clearly are a bit fuzzy on some of this stuff yet. "localhost" is the same as the box you are currently logged on, so....if you are logged on to ServerOne, then that box is ServerOne, it is also localhost, it is also ServerOne.myname.com and it is also xxx.xxx.xxx.xxx (It's IP address on the LAN)

-Tim

---

### Post by Iowan on 2008-08-21
#3. [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")> If you get this error: 

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName 

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file, 

sudo nano /etc/apache2/conf.d/fqdnor 

gksu "gedit /etc/apache2/conf.d/fqdn"then add 

ServerName localhostto the file and save. This can all be done in a single command with the following: 

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

---

### Post by ngmachado on 2008-08-24
Thank you windependence and Iowan. You've answered my questions 1, 3 and 4. :) I really appreciated your help.

I've still some doubts regarding /etc/hosts. 

Here is my /etc/host file (for IPv4):

```

127.0.0.1       localhost
127.0.1.1       ServerOne  SeverOne.myname.com

```

From what I understood, given that I don't have other computers in my network and that 127.0.1.1 is a loopback address (it refers to the local machine), it is OK to have the /etc/hosts like this. Am I right?

Thanks again.

---

### Post by inphektion on 2008-08-24
yes in fact when I had the apache prob mentioned above all I did was had the names in /etc/hosts.  I did this for any name I used in the virutal hosts file for apache.  However my domain name was always the same but for example if I have server1.mycompany.com but it is hosting virtual web sites for myapp.mycompany.com and webshare.mycompany.com and the local host IP is 192.168.16.5 then my /etc/hosts has:
```
192.168.16.5 server1.mycompany.com server1 myapp.mycompany.com myapp webshare.mycompany.com webshare
```

Then my apache restart fine.  My loopback in /etc/hosts just has server1.

---

### Post by bab1 on 2008-08-24
> **ngmachado said:**
> 
I've still some doubts regarding /etc/hosts... 

...From what I understood, given that I don't have other computers in my network and that 127.0.1.1 is a loopback address (it refers to the local machine), it is OK to have the /etc/hosts like this. Am I right?


Sort of;  You can use the 127.0.0.x numbers in a one host network, but you are not using the Ethernet interface of the network card.  In the future if you add another host to the network you will have to  redo your hosts file.  I would do it correctly (using your eth0 IP address).  See the man pages for "host"

Apache can be setup to resolve by domains or by IP address.

---

