---
title: "Assistance Needed With BIND9"
date: 2011-11-21
forum: Server Platforms
---

### Post by jlacroix on 2011-11-21
Hello everyone. I set up a server a few days ago and installed Ubuntu Server 11.10 on it. It's actually just a really old Desktop PC, and it's only purpose in life is to allow me to try things and learn. It has nothing important on it so if I break it and have to reinstall Ubuntu Server, so be it.

Short explanation:
I went through setting up BIND9, but it isn't resolving anything. The config files are attached.

Long explanation:
My mission right now is to learn DNS/BIND and how the configuration files work. To accomplish this, I'm just playing with it by using it to resolve local computers on my home LAN. Or at least I'm trying to, it's not working or resolving anything.

Note: If I add any of my LAN computers to /etc/hosts, they resolve and reply to pings. For the sake of testing, I've removed the other computers from /etc/hosts so they only way they'll respond is if BIND responds. But after following [this]("http://www.madboa.com/geek/soho-bind/") tutorial, I'm unable to get it to work. And yes, I did configure my local workstation to check the server with BIND9 on it first, by setting it as the primary DNS server.

I attached the configuration files to this post.

---

### Post by nyu2007 on 2011-11-21
Hi,

This [Link]("http://systeminteg.wordpress.com/") should be help you.

---

### Post by jlacroix on 2011-11-21
> **nyu2007 said:**
> Hi,

This [Link]("http://systeminteg.wordpress.com/") should be help you.
Which am I looking for in particular?

I'm hoping that I just made a simple mistake somewhere, something I overlooked, like last time.

---

### Post by Doug S on 2011-11-21
Your bind files have a mixture of schroder.net and localnet. They need to be consistant. Which are you trying to do?
There is a CNAME record for www, it needs to be an A record (I realize that your tutorial link had a CNAME record, but I am saying that is incorrect).
saturn is not declared in net.localnet.
I am not sure if it matters, but my rev file has an @ at the start of the NS line, your does not. Simiarly for the "IN {" on your zone "localnet" line in named.conf.local, mine doesn't have the "IN" part (again, I don't know if it maters or not).
In your system "cerf" and "stallman" do not exist, so those CNAME records should be corrected or deleted (the www one needs to change anyhow, as mentioned above).
I can try to give you a better reply tomorrow (it is late now), including edited version of your files, once I know what full names you are trying to create.
I would also suggest to look at the DNS section Ubuntu server 11.10 guide.

---

### Post by jlacroix on 2011-11-21
> **Doug S said:**
> Your bind files have a mixture of schroder.net and localnet. They need to be consistant. Which are you trying to do?
There is a CNAME record for www, it needs to be an A record (I realize that your tutorial link had a CNAME record, but I am saying that is incorrect).
saturn is not declared in net.localnet.
I am not sure if it matters, but my rev file has an @ at the start of the NS line, your does not. Simiarly for the "IN {" on your zone "localnet" line in named.conf.local, mine doesn't have the "IN" part (again, I don't know if it maters or not).
In your system "cerf" and "stallman" do not exist, so those CNAME records should be corrected or deleted (the www one needs to change anyhow, as mentioned above).
I can try to give you a better reply tomorrow (it is late now), including edited version of your files, once I know what full names you are trying to create.
I would also suggest to look at the DNS section Ubuntu server 11.10 guide.
Thanks for your help. Schroder.net came from the tutorial I linked to, and wouldn't be correct. I went with "localnet" because I've heard from somewhere that's a typical name for a zone if it's just for local machines. Do I need the www thing in the file? Not sure what that does. Here are the ONLY machines I have, any others are invalid:


ares            172.16.254.15
athena          172.16.254.13
hermes          172.16.254.5
neptune         172.16.254.16
pasithea        172.16.254.18
phoebe          172.16.254.17
phoenix         172.16.254.14
polaris         172.16.254.11
saturn          172.16.254.10

Edit: I went through the config files and I removed the things that weren't supposed to be there, and I've attached the updated files to this message. (It still doesn't work, though).

---

### Post by Doug S on 2011-11-21
The serial number needs to be increased between edits. That might explain some of your remaining troubles. Also, there is still some confusion as to if you are wanting, for example, hermes.localnet or hermes.local.net as your full computer name. I have assumed hermes.local.net
You don't need the www part, if you don't want. It helps with making your web server respond to either [www.local.net]("http://www.local.net") and local.net
Below are my edited versions of your files (note the bumped serial numbers):
net.localnet (includes a www A record and a CNAME record)(hmmm... my formatting seems to have not copied over...):
>  
;
; dns zone for for local.net
;
$ORIGIN local.net.
$TTL 1D
; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day
@ IN SOA local.net hostmaster.local.net (
201111210 ; serial
8H ; refresh
4H ; retry 
4W ; expire 
1D ) ; minimum 
;
@ NS hermes
hermes A 172.16.254.5
www A 172.16.254.5
bla CNAME hermes
ares A 172.16.254.15
athena A 172.16.254.13
neptune A 172.16.254.16
pasithea A 172.16.254.18
phoebe A 172.16.254.17
phoenix A 172.16.254.14
polaris A 172.16.254.11
saturn A 172.16.254.10
 

revp..172.254:
>  
;
; reverse pointers for 172.16.254.0 subnet
;
$ORIGIN 254.16.172.in-addr.arpa.
$TTL 1D
@ IN SOA hermes.local.net. hostmaster.local.net. (
201111210 ; serial
28800 ; refresh (8 hours)
14400 ; retry (4 hours)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
; define the authoritative name server
@ NS hermes.local.net.
; our hosts, in numeric order
5 PTR hermes.local.net.
10 PTR saturn.local.net.
11 PTR polaris.local.net.
13 PTR athena.local.net.
14 PTR phoenix.local.net
15 PTR ares.local.net.
16 PTR neptune.local.net
17 PTR phoebe.local.net
18 PTR pasithea.local.net
 

named.local.conf:
>  
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "local.net" {type master; file "/etc/bind/zone.net.localnet"; };
zone "254.16.172.in-appr.arpa" {type master; notify no; file "/etc/bind/revp.172.16.254"; };
 


---

### Post by jlacroix on 2011-11-21
> **Doug S said:**
> The serial number needs to be increased between edits. That might explain some of your remaining troubles. Also, there is still some confusion as to if you are wanting, for example, hermes.localnet or hermes.local.net as your full computer name. I have assumed hermes.local.net
You don't need the www part, if you don't want. It helps with making your web server respond to either [www.local.net]("http://www.local.net") and local.net
Below are my edited versions of your files (note the bumped serial numbers):
net.localnet (includes a www A record and a CNAME record)(hmmm... my formatting seems to have not copied over...):

revp..172.254:

named.local.conf:
Thank you SO MUCH for taking the time to help me!!!

Anyway, sorry for the confusion. Anywhere you see local.net is a mistake, I chose localnet.

You make a good point about bumping the version numbers. I totally forgot about that. I made a bunch of changes, and then bumped the version numbers. Attached is the latest changes. But if I try to ping athena, athena., or athena.localnet for example, I get no response still. (Even after restarting bind9).

I did set hermes (the computer that is hosting bind9) as the only DNS provider for the workstation I'm using right now, and I am able to get out to the Internet so at least part of bind9 is working properly, so I think we're close!

Edit: To avoid confusion, I'm not going to touch these files for a while unless told to.

---

### Post by Doug S on 2011-11-21
O.K. so I guessed wrong. You have to be careful with these files as the syntax sometimes requires a period after stuff. One of your latest files had some random line that shouldn't be there. Are you getting any errors reported in the log files when you restart bind9? Anyway, your system seems very similar to mine, so we should be able to get this sorted out (If we continue to have trouobles, I might send you my bind files in a PM for you do do the work of comparing). Below is my edit of your most recent files (I wonder if I can preserve the formatting this time?)
 
revp.172.16.254
> 
;
; reverse pointers for 172.16.254.0 subnet
;
$TTL 1D
@ IN SOA hermes.localnet. hostmaster.localnet. (
201111213 ; serial
28800 ; refresh (8 hours)
14400 ; retry (4 hours)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
;
@ NS hermes.localnet.
5 PTR hermes.localnet.
10 PTR saturn.localnet.
11 PTR polaris.localnet.
13 PTR athena.localnet.
14 PTR phoenix.localnet
15 PTR ares.localnet.
16 PTR neptune.localnet
17 PTR phoebe.localnet
18 PTR pasithea.localnet

 
net.localnet
> 
;
; dns zone for for localnet
;
$TTL 1D
; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day
@ IN SOA localnet. hostmaster.localnet. (
201111214 ; serial
8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum
IN A 172.16.254.5
;
@ IN NS hermes.localnet.
hermes IN A 172.16.254.5
www IN A 172.16.254.5
bla IN CNAME hermes
ares IN A 172.16.254.15
athena IN A 172.16.254.13
neptune IN A 172.16.254.16
pasithea IN A 172.16.254.18
phoebe IN A 172.16.254.17
phoenix IN A 172.16.254.14
polaris IN A 172.16.254.11
saturn IN A 172.16.254.10

 
named.conf.local
> 
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "localnet" IN { type master; file "/etc/bind/net.localnet"; };
zone "254.16.172.in-appr.arpa" { type master; notify no; file "/etc/bind/revp.172.16.254"; };

Since internet is working for you, we can ssume your forwarders are setup correctly in named.conf.options. I also assume that named.conf has the include statements to include the other named.conf.XXX files (i.e. is the default file)

---

### Post by jlacroix on 2011-11-21
> **Doug S said:**
> O.K. so I guessed wrong. You have to be careful with these files as the syntax sometimes requires a period after stuff. One of your latest files had some random line that shouldn't be there. Are you getting any errors reported in the log files when you restart bind9? Anyway, your system seems very similar to mine, so we should be able to get this sorted out (If we continue to have trouobles, I might send you my bind files in a PM for you do do the work of comparing). Below is my edit of your most recent files (I wonder if I can preserve the formatting this time?)
 
revp.172.16.254

 
net.localnet

 
named.conf.local

Since internet is working for you, we can ssume your forwarders are setup correctly in named.conf.options. I also assume that named.conf has the include statements to include the other named.conf.XXX files (i.e. is the default file)
That did it! I can now ping a computer if I put .localnet at the end. Is there a way to make ping respond to saturn instead of saturn.localnet for example? If not I won't be choosy. This is the furthest I've ever been!

I will mark this solved, since the original reason I posted this is solved now. But I do have the following questions in regards to the net.localnet file. I know this may be a pain, but the whole point is for me to learn, and I think these are the only things I don't understand.

1.) In net.localnet, what is the following line:
bla             IN      CNAME   hermes

2.) Also in net.localnet, what does this line do:
www             IN      A       172.16.254.5

3.) I am also curious about the below group of lines.
8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum

4.) Finally, what is the point of zones? Can't you just throw everything in one text file, or are zones intended for organizational purposes when you have a boatload of DNS records to maintain?

---

### Post by Doug S on 2011-11-21
I'm glad it works now, and thanks for reporting back to this thread. So many times we try to help and never hear back anything. Often we want to also know if it worked or not.
 
Sorry for not being clear about a couple of things. They were similar to previous posts, so I did not describe.> 1.) In net.localnet, what is the following line:
bla IN CNAME hermesThat was just an example of a proper CNAME record entry. You can delete it, but first try this:```
nslookup bla.localnet
nslookup 172.16.254.5
```You should get 172.16.254.5 and hermes.localnet.
 
> 2.) Also in net.localnet, what does this line do:
www IN A 172.16.254.5That is just an example of the proper way to do www, with an A record. You can delete it. (I assumed your web server is on hermes).
> 3.) I am also curious about the below group of lines.
8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum
That stuff is all related to the DNS records and how often they should update and expire and such. 8 hours, 4 hours, 4 weeks, 1 day. You can use seconds also.
I am not sure about your other questions, but I think you would have to make entries in the various hosts files to be able to use abbreviated computer names. I tend to use the full names on my system.
Now that you have things working, it might be an idea to add the RFC1918 zones to your named.conf.local file. (I am so out of time right now, but could follow up with you later on this subject).
 
Edit: Somehow I didn't see your question 4: Zones is a complicated subject going well beyond your local area network to the entire internet (I think). Maybe someone else can give an actual and better answer.

---

### Post by jlacroix on 2011-11-21
> **Doug S said:**
> I'm glad it works now, and thanks for reporting back to this thread. So many times we try to help and never hear back anything. Often we want to also know if it worked or not.
 
Sorry for not being clear about a couple of things. They were similar to previous posts, so I did not describe.That was just an example of a proper CNAME record entry. You can delete it, but first try this:```
nslookup bla.localnet
nslookup 172.16.254.5
```You should get 172.16.254.5 and hermes.localnet.
 
That is just an example of the proper way to do www, with an A record. You can delete it. (I assumed your web server is on hermes).

That stuff is all related to the DNS records and how often they should update and expire and such. 8 hours, 4 hours, 4 weeks, 1 day. You can use seconds also.
I am not sure about your other questions, but I think you would have to make entries in the various hosts files to be able to use abbreviated computer names. I tend to use the full names on my system.
Now that you have things working, it might be an idea to add the RFC1918 zones to your named.conf.local file. (I am so out of time right now, but could follow up with you later on this subject).
 
Edit: Somehow I didn't see your question 4: Zones is a complicated subject going well beyond your local area network to the entire internet (I think). Maybe someone else can give an actual and better answer.
When I run nslookup, I get this:
```
Server:         172.16.254.5
Address:        172.16.254.5#53

bla.localnet    canonical name = hermes.localnet.
Name:   hermes.localnet
Address: 172.16.254.5
```

As far as RFC1918, I have no idea what that its. I'll look it up and see if it makes sense.

As for the www line, based on what you said, am I correct to assume it's necessary if I were to run Apache on this box?

---

### Post by Doug S on 2011-11-21
> As far as RFC1918, I have no idea what that its. I'll look it up and see if it makes sense.
RFC1918 ip addresses are those that are reserved for local area network use only and are not routable over the world wide web. I.E. 10.X.X.X and 192.168.X.X and ... If your DNS deals with those type of lookups locally, it just saves wasted stuff on internet, in this case from forwarded useless requests. Maybe you don't need to worry about it, but you said your purpose was to learn stuff. 
You should see a file /etc/bind/zones.rfc1918 (I am still using server version 10.10, but hopefully 11.10 is the same for this). You can just cut and paste the contents into your named.conf.local file. However, be sure not to copy the line the applies to the RFC1918 sub-net you are actually using, i.e. the 172.16 line (well, it will be in reverse so I mean the 16.172 line).
Your named.conf.local would become:
> //
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "localnet" IN { type master; file "/etc/bind/net.localnet"; };
zone "254.16.172.in-appr.arpa" { type master; notify no; file "/etc/bind/revp.172.16.254"; };
zone "10.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "17.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "18.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "19.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "20.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "21.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "22.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "23.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "24.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "25.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "26.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "27.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "28.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "29.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "30.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "31.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "168.192.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
> As for the www line, based on what you said, am I correct to assume it's necessary if I were to run Apache on this box? 
If you want to use [www.localnet]("http://www.localnet") as the web addres, then yes.

---

### Post by jlacroix on 2011-11-22
> **Doug S said:**
> RFC1918 ip addresses are those that are reserved for local area network use only and are not routable over the world wide web. I.E. 10.X.X.X and 192.168.X.X and ... If your DNS deals with those type of lookups locally, it just saves wasted stuff on internet, in this case from forwarded useless requests. Maybe you don't need to worry about it, but you said your purpose was to learn stuff. 
You should see a file /etc/bind/zones.rfc1918 (I am still using server version 10.10, but hopefully 11.10 is the same for this). You can just cut and paste the contents into your named.conf.local file. However, be sure not to copy the line the applies to the RFC1918 sub-net you are actually using, i.e. the 172.16 line (well, it will be in reverse so I mean the 16.172 line).
Your named.conf.local would become:


If you want to use [www.localnet]("http://www.localnet") as the web addres, then yes.
Thank you so much for your help. I think that concludes everything. I appreciate it :)

---

### Post by offCourse2007 on 2011-11-25
Hi

One question about DNS and BIND.

If I setup BIND to manage DNS in my server, what does that mean regarding my domain and how it is managed?

Will I have to simply point the domain in the registrar to my server as NAMESERVER address? Is that what BIND picks up from?

Thank you

---

### Post by Doug S on 2011-11-25
> **offCourse2007 said:**
> Hi
 
One question about DNS and BIND.
 
If I setup BIND to manage DNS in my server, what does that mean regarding my domain and how it is managed?
 
Will I have to simply point the domain in the registrar to my server as NAMESERVER address? Is that what BIND picks up from?
 
Thank you
Most of us that implement our own DNS do so for our internal network only. Generally, it is not recommended to have it externally facing. I'm sure there are a few threads on this subject, but here is one: [http://ubuntuforums.org/showthread.php?t=1787730](http://ubuntuforums.org/showthread.php?t=1787730)
To actually answer your question, you wouldn't change anything at your registrar. Externally, things should remain the same as they were. See also this thread: [http://ubuntuforums.org/showthread.php?t=1855739](http://ubuntuforums.org/showthread.php?t=1855739) 
For example: my domain via external lookup:
```

C:>nslookup smythies.com
Server: ns2.dns.telus.com
Address: 75.153.176.9
Non-authoritative answer:
Name: smythies.com
Address: 209.121.28.192

```
and my domain via internal lookup:
```
 
C:\Users\Doug\C>nslookup smythies.com
Server:  ns1.smythies.com
Address:  192.168.111.1
Name:    smythies.com
Address:  192.168.111.1

```
I hope this helps.

---

### Post by offCourse2007 on 2011-11-25
Thank you for your reply.

What I am trying to do is to setup a mail server, to send my newsletters myself without using an SMTP account in any hosting company.

This means I need to configure an MTA, etc. 

The tool I am using has a tutorial with performance improvements and they say this:

"Setup your own DNS server.  Then configure sendmail to use your new DNS server to resolve MX and A records."

Although I want to use postfix instead of sendmail, I'd like to understand how to do this DNS stuff properly.

My domain is managed on bluehost, which is where I create my A records, CNAME and MX.

What kind of configuration do I need to do in both servers, then? Create an MX record in Bluehost pointing to my Ubuntu server? What do I do with BIND, if anything?

Thanks again

---

### Post by Doug S on 2011-11-25
You might want to start a new thread for your question, since this one was marked "solved" some of the other forum readers might not be looking at it anymore (it was a total accident that I saw your post earlier).
 
I have a mail server running fine (postfix, by the way, although I used to use sendmail). I don't have any MX record on my internal DNS, and only rely on the one at my ISP DNS. But then we don't e-mail in my local area network amongst ourselves.
It sounds as though you are looking for a MUA (Mail User Agent) as well as perhaps an MTA (Mail Transport Agent). I am not an e-mail expert, and will defer to input from others.

---

### Post by Doug S on 2011-12-01
> **Doug S said:**
> RFC1918 ip addresses are those that are reserved for local area network use only and are not routable over the world wide web. I.E. 10.X.X.X and 192.168.X.X and ... If your DNS deals with those type of lookups locally, it just saves wasted stuff on internet, in this case from forwarded useless requests. Maybe you don't need to worry about it, but you said your purpose was to learn stuff. 
You should see a file /etc/bind/zones.rfc1918 (I am still using server version 10.10, but hopefully 11.10 is the same for this). You can just cut and paste the contents into your named.conf.local file. [COLOR=red]However, be sure not to copy the line the applies to the RFC1918 sub-net you are actually using, i.e. the 172.16 line (well, it will be in reverse so I mean the 16.172 line).[/COLOR]
Your named.conf.local would become:
 
 
If you want to use [www.localnet]("http://www.localnet") as the web addres, then yes.
I want to make a correction: The sentence in [COLOR=red]RED[/COLOR] above is incorrect. That line needs to be left in, otherwise there will be a gap in coverage of all RFC 1918 addresses. What I did not know was that you can have, what appears to be, double coverage of the 172.16.254 sub-net and it seems to work fine. 
I only just discovered this same flaw in my own bind9 configuration, for my 192.168.111.XXX sub-net when vmware on my windows vista LapTop started doing DNS lookups for 192.168.171.255, which is a sub-net it created, and the request was being forwarded upstream. Sorry for giving incorrect information.

---

### Post by acc61287 on 2011-12-01
> **offCourse2007 said:**
> Hi

One question about DNS and BIND.

If I setup BIND to manage DNS in my server, what does that mean regarding my domain and how it is managed?

Will I have to simply point the domain in the registrar to my server as NAMESERVER address? Is that what BIND picks up from?

Thank you

Are you planning to host your own website?
check this out [http://www.dslwebserver.com](http://www.dslwebserver.com)
and also this [http://mysql-apache-php.com/dns-server-tutorial.htm](http://mysql-apache-php.com/dns-server-tutorial.htm)

after you read it post your question

---

