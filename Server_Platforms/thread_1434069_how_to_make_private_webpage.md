---
title: "how to make private webpage"
date: 2010-03-19
forum: Server Platforms
---

### Post by blakep2 on 2010-03-19
i want to make a webpage so that only people on my network can see it. how do i do this

---

### Post by km0r3 on 2010-03-20
> **blakep2 said:**
> i want to make a webpage so that only people on my network can see it. how do i do this

Hello blakep2,

We need to know the following things:

[LIST]
[*]Which "network" do you mean?* The Internet, a WAN, your (W-)LAN, your social network, your spider's net-work? ;).*
[*]What kind of "Web Page"? [[Definition of a Web Page]]("http://www.techterms.com/definition/webpage") *(A) HTML-Document(s) (static), a dynamic "Web Page", programmed with PHP, Python, etc...*
[*]What will you be using to serve your "Web Page"? [A LAMP stack?]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") A lonely Web Server for serving static HTML pages, like [Apache]("http://en.wikipedia.org/wiki/Apache_HTTP_Server") (which is a popular choice by the way) ?
[/LIST]
If you simply want to password-protect your "Web Page", then I'd suggest reading what is an [htaccess file]("http://en.wikipedia.org/wiki/Htaccess").

Hope I could help you somehow.

---

### Post by blakep2 on 2010-03-20
I am using apache and a html webpage is fine, and i guess it is wan; i do not want it on the internet.

---

### Post by km0r3 on 2010-03-20
> **blakep2 said:**
> I am using apache and a html webpage is fine, and i guess it is wan; i do not want it on the internet.

OK. Well, maybe the best choice is the htaccess file solution.

[QUOTE=Wikipedia][Authorization]("http://en.wikipedia.org/wiki/Authorization"), [authentication]("http://en.wikipedia.org/wiki/Authentication").htaccess files are often used to specify the security restrictions for the particular directory, hence the filename "access". The .htaccess file is often accompanied by a [.htpasswd]("http://en.wikipedia.org/wiki/.htpasswd") file which stores valid [usernames]("http://en.wikipedia.org/wiki/Username") and their [passwords]("http://en.wikipedia.org/wiki/Password").[[3]]("http://en.wikipedia.org/wiki/Htaccess#cite_note-2")[/QUOTE]

Means, you can set a user and a password really fast to limit access.

You can also restrict access by allowing only specific IP addresses to access Apache or [restricting specific IP addresses]("http://ubuntuforums.org/showthread.php?t=736084").

I suggest using the Forum search will give you valuable results.

---

### Post by era86 on 2010-03-20
I believe there is a XAMPP app in the repos.  You can read more about it here: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

You can also view this thread: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

A little dated, but you might find it useful for deploying "in-house".

---

### Post by blakep2 on 2010-03-20
> **era86 said:**
> I believe there is a XAMPP app in the repos.  You can read more about it here: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

You can also view this thread: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

A little dated, but you might find it useful for deploying "in-house".

i do not understand what does this mean.

---

### Post by soltanis on 2010-03-20
XAMMP is a webserver "stack".

What you are asking us is to basically run a webserver that is accessible to the local network but not to the Internet.

If you are running in a LAN environment behind a router which is performing Network Address Translation (NAT) then you need not do anything beyond run an Apache/Lighttpd webserver. Unless you specifically set port forwarding rules in the router, the site will not be accessible from outside of your network.

If you are not running behind a NAT router, then you are either directly connected to the Internet, or you are in a more complex networking scheme (for example, School or Corporate networks which do assign unique, Internet-accessible IP addresses to each computer which is connected, as opposed to private subnet addresses).

A good way for you to figure out which one of these you are using is to go to the terminal and run ifconfig. Post the output here, and we can tell you if it's a private subnet address (indicating you are in a LAN, behind a NAT router) or a public address (which would indicate a more advanced network setup, and would make this process more complicated).

---

### Post by blakep2 on 2010-03-20
> **soltanis said:**
> XAMMP is a webserver "stack".

What you are asking us is to basically run a webserver that is accessible to the local network but not to the Internet.

If you are running in a LAN environment behind a router which is performing Network Address Translation (NAT) then you need not do anything beyond run an Apache/Lighttpd webserver. Unless you specifically set port forwarding rules in the router, the site will not be accessible from outside of your network.

If you are not running behind a NAT router, then you are either directly connected to the Internet, or you are in a more complex networking scheme (for example, School or Corporate networks which do assign unique, Internet-accessible IP addresses to each computer which is connected, as opposed to private subnet addresses).

A good way for you to figure out which one of these you are using is to go to the terminal and run ifconfig. Post the output here, and we can tell you if it's a private subnet address (indicating you are in a LAN, behind a NAT router) or a public address (which would indicate a more advanced network setup, and would make this process more complicated).

root@petermanserver:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:99:65:fe  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe99:65fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7149511 (7.1 MB)  TX bytes:38679973 (38.6 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15982 (15.9 KB)  TX bytes:15982 (15.9 KB)

---

### Post by Hellkeepa on 2010-03-20
HELLo!

That's a NATed address, the "192.168." bit tells us that. That means that all you have to do, is to set up a web server on your computer. "sudo apt-get install apache2" is the easiest way to do this.
I do recommend reading up on how to configure Apache too, and you'll find the documentation at this address: [http://httpd.apache.org/](http://httpd.apache.org/)

PS: Not exactly a programming question this, as we're just dealing with setting up a server. ;-)

Happy codin'!

---

### Post by blakep2 on 2010-03-20
I already have apache and have a site set up how do i change the domain(I have read the forums and tutorials they are not making any sense to me)  As of right now I have to access the site through the server's ip address i want to change this

---

### Post by Hellkeepa on 2010-03-20
HELLo!

For this you need a domain controller, which is a completely different beast. Or, you can go the easier, but manual, route and edit the "/etc/hosts" file on each of the computers that can connect to it.

Happy codin'!

---

### Post by blakep2 on 2010-03-20
if i was to make a new thread what would i put that under.  Also how hard would that be to do and what does that do.  I am not that experienced don't know what of a lot of the terms mean(fairly new to ubuntu).

---

### Post by lisati on 2010-03-20
(Mrs Lisati is putting my multitasking skills to the test as I type, so this answer isn't quite as good as I'd like)

You might be able to access it already. Try this in the address bar of a browser on a machine other than your serve:
```

<servname>.lan:80

```

---

### Post by blakep2 on 2010-03-20
What do I replace sever name with. the name of my computer is called petermansever i replaced it with that inside the <x> and it did a google search so i guess it is not working?

---

### Post by lisati on 2010-03-20
> **blakep2 said:**
> What do I replace sever name with. the name of my computer is called petermansever i replaced it with that inside the <x> and it did a google search so i guess it is not working?

Sorry about the delay replying, Mrs Lisati managed to grab my attention. It would be the name of your computer which has apache2 on it. As long as it's visible on your home network......

---

### Post by blakep2 on 2010-03-20
it is visible on my home network but when  I enter that address in nothing comes up

---

### Post by emyr42 on 2010-03-20
You need something in your network to turn names into IP addresses. If you post your router model, we can work out if it will run a local DNS server.

---

### Post by blakep2 on 2010-03-21
wrt54gs lynksys cisco version 6

---

### Post by noway2 on 2010-03-21
Taking a quick look through their manual, it doesn't look like this device supports DNS, though you may be able to add a static route to your server.

I would suggest that you look into and consider running DHCP and BIND on your server instead of letting your router assign all the IPs.  You can then link the two so that they are updated together.  This will allow all your LAN devices to be accessible by name rather than just IP address.

---

### Post by blakep2 on 2010-03-21
that is what i am doing now minus the bind server.  I don't know about the dns.

---

### Post by Dunco on 2010-03-26
thanks

---

