---
title: "LAMP Apache2 starts and stops well but no web site"
date: 2010-11-17
forum: Server Platforms
---

### Post by mansour on 2010-11-17
[FONT=Arial][SIZE=2]I have a small network of an Ubuntu server 10.4 , Debian server, Win XP, and an ubuntu desktop 10.4.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I have configured a DNS server and DHCP server successfully on my ubuntu server, also a slave DNS server on Debian. [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=2]I recently configured apache2 as part of LAMP on ubuntu server, but when I type my ServerName in the URL of my Win XP browser, I get this response:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**The webpage "mansour.net" cannot be found**[/SIZE][/FONT]
**[FONT=Arial][SIZE=2]DNS error occurred. Server cannot be found. The link may be broken.[/SIZE][/FONT]**
 
 
[FONT=Arial][SIZE=2]I have an A Record in my DNS zone file for **mansour.net** and have that as my ServerName in apache2 Definition file, but [/SIZE][/FONT][FONT=Arial][SIZE=2]I don't know why it is not working.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]Could someone please help me to troubleshoot my apache2.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I am trying to learn to install and configure various servers on ubuntu.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]I greatly appreciate your help. [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]Mansour[/SIZE][/FONT]
[FONT=Arial][SIZE=2]from Toronto[/SIZE][/FONT]

---

### Post by SeijiSensei on 2010-11-17
The domain mansour.net is registered at TUCOWS.  When I visit that site I see "This domain name is available for use!" on a page from TUCOWS itself.  Is this really you?  

You could "hijack" the domain for private purposes if all your client machines have DNS resolver configurations that use only DNS servers you maintain with zone files for "mansour.net".  Is that how your machines are configured?

---

### Post by mansour on 2010-11-17
No that's not me. I haven't registered a Domain anywhere yet.
 
And yes, for the time being, it is for private network purpose only. I am not worried about going on internet, and my web site being reached by others on internet right now. That would be future project.(and I will go on internet eventually but not now)
 
Right now I am only trying to see whether my Win XP machine and Ubuntu desktop could open the web page on my apache2 server.
 
With no luck. I can't see what is wrong with apache2 configurations.
 
Mansour

---

### Post by SeijiSensei on 2010-11-17
So the DHCP server tells its clients to use your local DNS server and *only* your local DNS server?

The reason I ask is if they leak any requests to the Internet, they'll be resolved by the existing mansour.net servers.  Any request for something in .net will be handed to the root nameservers which will reply with the nameserver addresses for the requested domain.

The error you post:

The webpage "mansour.net" cannot be found
DNS error occurred. Server cannot be found. The link may be broken.

pretty clearly says it's a DNS error.  I don't think it's an Apache problem.  Can you post the contents of named.conf and the zone file you've created for mansour.net?  Please post them inside [noparse]```

```[/noparse] tags.

Also what do you get if you run "host -t any mansour.net localhost" on the machine with the DNS server running?

---

### Post by mansour on 2010-11-17
> **SeijiSensei said:**
> So the DHCP server tells its clients to use your local DNS server and *only* your local DNS server?
 
[COLOR=blue]Yes. I have disabled my Lynksis router's DHCP and DNS servers. Both DHCP and DNS functions are being provided by my ubuntu server and I also have a slave DNS server which is debian laptop. [/COLOR]
 
The reason I ask is if they leak any requests to the Internet, they'll be resolved by the existing mansour.net servers. Any request for something in .net will be handed to the root nameservers which will reply with the nameserver addresses for the requested domain.
 
[COLOR=blue]Yes, you are right. I never actually though there might be a mansour.net Domain.[/COLOR]
[COLOR=blue]But yes it could happen.[/COLOR]
 
The error you post:
 
The webpage "mansour.net" cannot be found
DNS error occurred. Server cannot be found. The link may be broken.
 
pretty clearly says it's a DNS error. I don't think it's an Apache problem. Can you post the contents of named.conf and the zone file you've created for mansour.net? Please post them inside [noparse]```

```[/noparse] tags.
 
[COLOR=blue]Yes, I'd like to do that, but how could I do that? I mean how could I post those files for you to see. I could upload them to a scp server if I get the address for a scp server, but how could I post them here for you to see?[/COLOR]
 
Also what do you get if you run "host -t any mansour.net localhost" on the machine with the DNS server running?

 
 
[COLOR=blue]:~# host -t ubuntu-server.mansour.net[/COLOR]
[COLOR=blue]host: invalid type: ubuntu-server.mansour.net[/COLOR]

[COLOR=blue]:~# host -t ubuntu-server[/COLOR]
[COLOR=blue]host: invalid type: ubuntu-server[/COLOR]

[COLOR=blue]:~# host -t COMP1[/COLOR]
[COLOR=blue]host: invalid type: COMP1[/COLOR]

[COLOR=#0000ff]COMP1 is my Win XP machine.[/COLOR]

[COLOR=blue]I don't know which one of these commands are correct, or maybe all are. [/COLOR]

---

### Post by Vegan on 2010-11-17
You cannot use an invalid URL and expect it to work. No way for the DNS to route the traffic.

---

### Post by mansour on 2010-11-17
> **Vegan said:**
> You cannot use an invalid URL and expect it to work. No way for the DNS to route the traffic.
 
 
[COLOR=blue]So Vegan what should I do? so as long as I don't have a registered valid Domain, then I can't host a web site?[/COLOR]

[COLOR=blue]But when I run:[/COLOR]

[COLOR=blue]dig ubuntu-server.mansour.net[/COLOR]
[COLOR=blue]dig COMP1.mansour.net [/COLOR]

[COLOR=blue]or even[/COLOR]

[COLOR=blue]dig -x 192.168.1.101[/COLOR]
[COLOR=blue]dig -x 192.168.1.103[/COLOR]

[COLOR=blue]all these commands return a NOERROR response for me.[/COLOR]



[COLOR=#0000ff]Mansour[/COLOR]

---

### Post by SeijiSensei on 2010-11-17
If you just want to run an internal web server that you can see from machines on your local network, then you can use IP address-based URLs like [http://192.168.1.1/](http://192.168.1.1/) and replace the default website files in /var/www.

If you want to use hostnames, you can add names to /etc/hosts on the clients and use those with name-based virtual hosting.

If you want to use a fully-qualified domain name, or you want to make your site available to visitors outside your local network, you'll need to register a domain and set up public DNS records.

Also you really didn't follow my instructions when using the host command:

What do you get if you run **"host -t any mansour.net localhost"** on the machine with the DNS server running?

---

### Post by mansour on 2010-11-17
[FONT=Arial][SIZE=2]> **SeijiSensei said:**
> If you just want to run an internal web server that you can see from machines on your local network, then you can use IP address-based URLs like [/SIZE][/FONT]> **SeijiSensei said:**
> [[FONT=Arial][SIZE=2]http://192.168.1.1/[/SIZE][/FONT]]("http://192.168.1.1/")[FONT=Arial][SIZE=2] and replace the default website files in /var/www.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=blue]Yes, that 's exactly what I am trying to do. An internal web server that serves web pages to local machines for now.[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff]This is /var/www/mansour.net/index.thml the path to that index.html which is a very basic html file. [/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=blue]When I type [/COLOR][[COLOR=blue]http://192.168.1.101/[/COLOR]]("http://192.168.1.101/")[COLOR=blue] in the URL of my Win XP machine this is the response I get.[/COLOR][/SIZE][/FONT]
 
**[FONT=Arial][SIZE=2][COLOR=blue]The webpage "192.168.1.101" cannot be found[/COLOR][/SIZE][/FONT]**
 
**[FONT=Arial][SIZE=2][COLOR=blue]DNS error occurred. Server cannot be found. The link may be broken.[/COLOR][/SIZE][/FONT]**
 
[FONT=Arial][SIZE=2]If you want to use hostnames, you can add names to /etc/hosts on the clients and use those with name-based virtual hosting.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]If you want to use a fully-qualified domain name, or you want to make your site available to visitors outside your local network, you'll need to register a domain and set up public DNS records.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=blue]Yes, But that is for the future. Right now is just for my local machines. This network of 4 machines is just for learning purposes only for now. [/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Also you really didn't follow my instructions when using the host command:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]What do you get if you run **"host -t any mansour.net localhost"** on the machine with the DNS server running?[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=blue]Sorry my apology, this is what I get:[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=blue]# host -t any mansour.net localhost[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]Using domain server:[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]Name: localhost[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]Address: 127.0.0.1#53[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]Aliases:[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]mansour.net has address 192.168.1.101 mansour.net has SOA record ubuntu-server.mansour.net. .....................[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]mansour.net name server debian-laptop.mansour.net.[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]mansour.net name server ubuntu-server.mansour.net.[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]mansour.net mail is handled by 20.mail..............[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]mansour.net mail is handled by ..............[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=blue]root@ubuntu-server[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=blue]:~#[/COLOR][/SIZE][/FONT]

---

