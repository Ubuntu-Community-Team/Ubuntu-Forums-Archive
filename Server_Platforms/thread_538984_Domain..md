---
title: "Domain."
date: 2007-08-30
forum: Server Platforms
---

### Post by hockey97 on 2007-08-30
Hi I bought a Domain name, now I am having problems getting ti up, I followed their instructions it's registered and has 3 records 2 A's and 1 mx records.

I have webmin and also apache, and bind9 installed and running on ubuntu 7.04.

all are newest editions.

I need help on how to config apache or  bind9 so that I can have my website up with a domain name that I bought.

I  have a router also and I am port forwarding 80 and also 53.

SO I need help on what do I need to do so I can make a folder on my server to be connected to my domain name so when someone types the domain name, it would take them to the website main site file doc.

like website.html or something.

---

### Post by hockey97 on 2007-08-30
I don't know the whole proccess on getting the domain name up and running.

I have 1 registered domain name and it's up.

 I have apache2, and bind9 installed already,
I don't know what IP addresses I need and how to config those programs, so my domain name would direct the request to my server.
 I know my internal ip and also external ip addres, I have a router and I  done port forward.

my router has 3 empty places where I can assing a static dns ip, don't know how to use it.

but I  also have webmin so I use that to add the configs.

but I just don't know what I need in bind9 and apache to get my domain name to send the request's to my server to get the webdocs for that one website.

I need help on configuring bind9 and apache so it could recive requests that go to my domain name.

I would need to know what I need to do in the router, and if I need to use my external or internal ip address or should I use the static dns ip address that I could create on my router.

my router is a linksys .

---

### Post by wirelessmonkey on 2007-08-30
1) Use the IP address of your router, unless your server has a static IP address from your ISP.
2) You don't need bind, bind is for running your own DNS server, the company who registered your domain should take care of this automatically.
3) Read the apache documentation.  You need to set up hosts and/or Virtual Hosts in your apache configuration.

---

### Post by hockey97 on 2007-08-30
OH ok, so if I used Bind I could of hosted my own domain name right?

but that requires a internet backbone connection to use bind9 to host domain names on the internet?

what do you mean the IP address of the router??
Is that  the internal ip address like 192.168.5.4 or external like 69.45.23.1 .

I know the external ip address.

so I just need to config apache and my mail server to have a domain name and also use a domain name for the e-mail ect??

---

### Post by southernman on 2007-08-31
Setting up a Domain Naming Server is much more complicated than you need to deal with now... aka *bind9* 

You would still have to buy the domain name from an accredited ICANN registrar such as you did.

Here is a guide to at least get you up to speed on some of this stuff. I strongly suggest that you think about this again though. Still reading? Ok... you asked for it! ;)

[http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/]("http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/")

That ought to keep you busy for the next couple of weeks. ;) It has me!

---

### Post by hockey97 on 2007-08-31
nice, I added it to my fav.
plan to read it later.

right now I  have a domain name bought, and they handel all of the dns stuff.

so I don't think I need bind9.

on their site I made the domain name, and 2 A records and one Mx record meaning the record address for e-mail ect.

I have apahce2 the latest version, I made a virtuial host with my domain name in it.

and the ip address of my router.

but when I type the domain name in, it dosen't work, I get the error cannont find host.

I right now just want to know what I need to do to connect that domain name to my apache server well the virtual host.

I have a folder for the website.

it's been 2 day's since I paid it and yet can't use it.

lol
and I also have college so time is limited.

today and sunday I only have to work on this stuff.

---

### Post by hockey97 on 2007-08-31
how to config the apache server to attach the domain name to it??

---

### Post by hockey97 on 2007-09-03
HI I got the domain name registered, and using bind 9 and apache webserver. 

I am using webmin to config them.

But I tried to do it, and can't get my server to be attached to the domain name.

also what does it mean when your domain is parked?? does it mean it's reserved?

well I tried config it in webmin but no luck, 

I need s tutorial or some tips or guide line help, like how to go abouts on doing this.

I know the ip address of the domain name and my external ip address, I have only one internet line.

so one external ip address and a router to route them.

---

### Post by OldGaf on 2007-09-03
You need to go to the registrar where you registered you domain name and see if they have a DNS Service that will allow you to enter your external IP address. I have some of my domain names at a registrar that offers this for $9.95 a year.

However, if this is a home server, you could go to:
> [Dyndns]("http://www.dyndns.com/")
and get a domain name for free and point it to your external IP. They will let you have up to 5 free domain names and point them all to the same IP if you want to setup virtual hosts on Apache. This is very easy to do with webmin. I have 3 on my little home server now.

Anyway, the key is to go to where ever you get your domain name and enter your external IP address there. As long as apache is up and running, it will "just work" once the domain name resolves (usually a few days). 

Oh, if you are behind a router, make sure you forward port 80 to the internal IP of your server. If you want ssh, FTP etc, you will need to forward those ports as well.

---

### Post by hockey97 on 2007-09-03
well my registar, they are asking for a name server.

I don't understand what info they want??

I made in bind 9 , 1 name server, one was ns1.mydomainname.com
 my register,  they have an area called dns host's , I put ns1.mydomainname.com and my external ip address.

they said it will take 4 to 8 hour's to complete the proccess, and be able to see the results.

should I keep the computer with the ns server on?? 

well I hope I get it up and running spent a whole day on it.

---

### Post by hockey97 on 2007-09-04
I did port forward port 80,53,25 
that's what I have so far.

my domain provider, they have 2 name servers, and I setup my own, 
with bind 9.

they told me it takes 24 hours.

but do you think this mean's that if I shutdown my computer, and then start it back up, that it will tkae 24 hour's to grab the info of my server??

but the provide seen my name server, it see's it , so now I got 3 ns assinged to my domain, 2 are theirs and 1 is mine.

do I have to put the ns info in apache2 ??

---

### Post by hockey97 on 2007-09-04
look's like I done it right.

check it out, [www.demonicproductions.com](www.demonicproductions.com)

and tell me if you see it.

also what is the url address of the apache zones??

to me I think the website what I done was to connect to just the default apache server zone.

I don't know if I the one you see, is the server zone.

also how can I view it?? on my computer?  Like to me I get a red error, which is from my router.

I went on vtunnel.com and tried it and it works.

any idea how I could see the site, from my computer, which has the servers.

---

