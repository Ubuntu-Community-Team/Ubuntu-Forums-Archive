---
title: "Howto: Setup a DNS server with bind"
date: 2006-08-14
forum: Tutorials
---

### Post by tomtom_in_eire on 2006-08-14
After looking on Ubuntu forum for an easy step-by-step howto for instaling a DNS server, I decided the best idea would probably be to write this howto myself.... So, here it is!

**Step 1**: Install Ubuntu dapper, or use your WORKING installation.

**Step2**: Install bind 9:
```
sudo apt-get install bind9
```
**Step 3**: Configure the main Bind files. Usually, if you install Bind from the source code, you will have to edit the file named.conf. However, Ubuntu provides you with a pre-configured Bind, so we will edit another file:
```
sudo vi /etc/bind/named.conf.local
```
This is where we will insert our zones. By the way, a zone is a domain name that is referenced in the DNS server ;)
Insert this in the named.conf.local file:
```

# This is the zone definition. replace example.com with your domain name
zone "*example.com*" {
        type master;
        file "/etc/bind/zones/*example.com*.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "*0.168.192*.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.*0.168.192*.in-addr.arpa";
};

```
Ok, now, let's edit the options file:
```
sudo vi /etc/bind/named.conf.options
```
We need to modify the forwarder. This is the DNS server to which your own DNS will forward the requests he cannot process.
```

forwarders {
      # Replace the address below with the address of your provider's DNS server
      123.123.123.123;
};

```
Now, let's add the zone definition files (replace *example.com* with your domain name:
```

sudo mkdir /etc/bind/zones
sudo vi /etc/bind/zones/*example.com*.db

```
The zone definition file is where we will put all the addresses / machine names that our DNS server will know. You can take the following example:
```

*// replace example.com with your domain name. do not forget the . after the domain name!*
*// Also, replace ns1 with the name of your DNS server*
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
*// Do not modify the following lines!*
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

[I]// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name[/I]
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mta.example.com.

*// Replace the IP address with the right IP addresses.*
www              IN      A       192.168.0.2
mta              IN      A       192.168.0.3
ns1              IN      A       192.168.0.1

```
Now, let's create the reverse DNS zone file:
```
sudo vi /etc/bind/zones/rev.0.168.192.in-addr.arpa
```
Copy and paste the following text, modify as needed:
```

[I]//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.[/I]
@ IN SOA ns1.example.com. admin.example.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.example.com.
1                    IN    PTR    example.com

```
Ok, now you just need to restart bind:
```
sudo /etc/init.d/bind9 restart
```
We can now test the new DNS server...
Step 4: Modify the file resolv.conf with the following settings:
```
sudo vi /etc/resolv.conf
```
enter the following:
```

*// replace example.com with your domain name, and 192.168.0.1 with the address of your new DNS server.*
search example.com
nameserver 192.168.0.1
```
Now, test your DNS:
```
dig example.com
```

Look at the result.... Enjoy!
Also, this post is not perfect... Do not hesitate to improve it!

---

### Post by larka06 on 2006-08-31
I have setup my hp xg833, 733mhz and 384megs ram, just as you have above.  I have even cut and pasted through putty.  I have then set one of my other machines to go to the dns server to only have it say not able to reach the website I want to reach.  Basically I am using the dns server for the intranet and the internet.  I thought that once it did not find what I was looking for on the intranet it would go to the ISP, which I have set the ip addresses and host, on to the internet. Is this thinking correct?  I am stumped.
Thanks larka06
email at [email]larka51@netscape.net[/email]
I also can meet you on the IRC channel or anywhere you want me to be

---

### Post by hogman23 on 2006-09-13
One more step to get it to work:
You must rename the named.conf.local to named.conf

---

### Post by mekas2024 on 2006-09-18
Nice tutorial , i was working with this and with a tutorial that is in this page [http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm) 

The thing its that im not sure if a did everything well, i dont know how to test this..

y dig mekas.com and this says the terminal:

dantec@ubuntu:~$ dig mekas.com

; <<>> DiG 9.3.2 <<>> mekas.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 9469
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mekas.com.                     IN      A

;; Query time: 12 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Sep 18 00:42:30 2006
;; MSG SIZE  rcvd: 27



if i dig something wrong, i get this:

dantec@ubuntu:~$ dig tadeo.meks.com

; <<>> DiG 9.3.2 <<>> tadeo.meks.com
;; global options:  printcmd
;; connection timed out; no servers could be reached


I think its working, but i need to be sure, please i will apreciate if u help me, im kind of newbie in linux and i need to mount a dns server 4 a class ;)

THX a lot

Regards

MeKaS

---

### Post by subscr on 2006-09-20
When I try and install bnd9, here is what I get..Any ideas ?

 sudo apt-get install bind9
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bind9: Depends: libdns21 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisccfg1 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisc11 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisccc0 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed

---

### Post by mitjab on 2006-09-30
must domain be registered or not?
Can i use no-ip.com domain?

I am using router so which port must o foward for bind server?

www IN A 192.168.1.5
mta IN A 192.168.1.5
ns1 IN A 192.168.1.5

can i use for all three the same ip and the same machine?

---

### Post by garbergs on 2006-10-21
I also had trouble installing bind9, so I tried to write:

apt-get install bind

and that gave me version 8.4.6-1. I'm sure this will suffice for my simple home network.

---

### Post by Bretls on 2006-11-07
Thanks for the tutorial. I have a dynu account and used this as my domain name. I believe dynu is similar to no-ip.com. I installed bind9 with synaptic in edgy, and followed your directions. Works without a problem.

---

### Post by jaywatkins on 2006-11-08
Does this work for Edgy?

I would like to set up a "chrooted" bind server for local traffic and Internet forwarding.  Would this tutorial work?

I was trying to follow on howtoforge.com regarding "A perfect setup" for Edgy 6.10 server, but ran into trouble when I came to setting up bind9.  I understand DNS, just not bind.

Thx

/J

---

### Post by marwell on 2006-11-12
Finaly, what I was looking for. :)
Thanks a lot.

---

### Post by huggy77 on 2006-11-13
in reference to ```

# This is the zone definition. replace example.com with your domain name
zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};

```

the box ip i want visible is: 10.10.10.2, router is 10.10.10.1
would that make my rev. 0.10.10.10????

---

### Post by randomnote1 on 2006-11-16
> **huggy77 said:**
> in reference to ```

# This is the zone definition. replace example.com with your domain name
zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};

```

the box ip i want visible is: 10.10.10.2, router is 10.10.10.1
would that make my rev. 0.10.10.10????
that's correct.....you just need the network address

---

### Post by jo calamine on 2006-11-17
what version of ubuntu has the pre configured bind files?  loaded the latest and it does not.  Is there a version that has bind already loaded or would I still have to load bind?

---

### Post by Coogan on 2006-11-21
I'm getting this error when trying to start Bind:

```
Nov 21 21:59:47 localhost named[10645]: starting BIND 9.3.2 -u bind
Nov 21 21:59:47 localhost named[10645]: found 1 CPU, using 1 worker thread
Nov 21 21:59:47 localhost named[10645]: loading configuration from '/etc/bind/named.conf'
Nov 21 21:59:47 localhost named[10645]: /etc/bind/named.conf:55: unknown option 'forwarders'
Nov 21 21:59:47 localhost named[10645]: loading configuration: failure
Nov 21 21:59:47 localhost named[10645]: exiting (due to fatal error)

```

Here's the forwarders part in named.conf:

```
forwarders {
  205.152.37.23;
  };
```

Any idea what I'm doing wrong?  I'm trying to set up an DNS server that'll act as a local cache (Bellsouth's DNS kinda sucks) and so I set up a few internal websites and servers.

Coog

---

### Post by mikemaggio on 2007-01-14
I've just finished setting this up. When I restart the service I get this error:

 rndc: connect failed: connection refused

Any ideas on what I might have done wrong?

---

### Post by stijn_pol on 2007-01-17
Just wanted to let you guys know: don't use '_' in your server names. For some reason I did this and it wasted hours to find out. Stupid... yes indeed

---

### Post by phormion on 2007-01-17
stijn_pol, underscores in host names are illegal according to RFCs (I can't remember if it was the DNS RFCs or another one, it was explained on the bind-users list). This was checked in older versions of BIND (for example 8.x); BIND 9.2 didn't perform host name checking, but the feature was reimplemented in BIND 9.3 and that's what I think bit you. 

You can work around that using the 'check-names' option, if you're *really* convinced you need underscores in your hostnames. 

For diagnosing problems in your BIND configuration, named-checkconf or named-checkzone are your friends. They are part of the BIND source package, although I don't know in which Ubuntu package they are installed.

---

### Post by velorider on 2007-01-28
To get the dns to updated for dhcp clients I had to add the "allow-update" directive to the zone:

zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        allow-update {192.168.1.0/24;};
};

---

### Post by phormion on 2007-01-28
velorider, BIND doesn't accept zone updates by defaults, which makes sense if you think of the implications of allowing people to update your DNS and redirecting your traffic to who knows what host. Also, 'allow-update' is considered insecure in the BIND 9.3 administrator's manual (see [here](http://www.isc.org/sw/bind/arm93/Bv9ARM.ch07.html#dynamic_update_security)). The best way is to use something like TSIG. Oh, and did you say you allow DHCP clients to update the DNS? That's also not a good idea, how can you trust a client not being hacked, and wreaking havoc on your DNS namespace? 

What I'd recommend is to have the DHCP server send the DNS updates, most servers should support that. 

Also, If you're running a publicly accessible DNS server, I would suggest your configuration with [http://www.dnsreport.com](http://www.dnsreport.com), especially the 'open dns server' item.

---

### Post by CopaceticOpus on 2007-02-27
> **hogman23 said:**
> One more step to get it to work:
You must rename the named.conf.local to named.conf

I want to point out that this isn't correct. The default setup is for named.conf to include named.conf.local. There should be a line at the end of your named.conf which looks like this:

```
include "/etc/bind/named.conf.local";
```

For my setup, I wanted to use BIND to divert all domains ending in ".dev" to a local IP, and to act as a cache for all other requests. This is a nice easy way to set up a local testing environment. Here's how my setup looks:

**named.conf.local:**
```
zone "dev" {
  type master;
  file "/etc/bind/db.dev";
};

zone "1.168.192.in-addr.arpa" {
  type master;
  file "/etc/bind/db.192.168.1";
};
```

**db.dev:**
```
;
; BIND data file for dev sites
;
$TTL    604800
@       IN      SOA     dev. root.dev. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      dev.
@       IN      A       192.168.1.10
*.dev.  14400   IN      A       192.168.1.10

```

**db.192.168.1:**
```
;
; BIND reverse data file for dev domains
;
$TTL    604800
@       IN      SOA     dev. root.dev. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      dev.
10      IN      PTR     dev.

```

In this example, 192.168.1.10 is the computer hosting the ".dev" sites. I'm not an expert in this, but my setup seems to be working well. I think it's unfortunate that the syntax of these files is so obscure, compared to Apache's easy-to-read config files.

---

### Post by CopaceticOpus on 2007-02-27
I must follow up on my above posting. My setup is kind of working, but not exactly. It seems that the first time I try to look up any ".dev" URL from another machine, I get a delayed response. For example, this is the output of two nslookup commands from an XP box which is using my Linux BIND server as its DNS server:

```
C:\>nslookup wahoo.dev
Server:  dev
Address:  192.168.1.10

DNS request timed out.
    timeout was 2 seconds.
Name:    wahoo.dev
Address:  192.168.1.10


C:\>nslookup wahoo.dev
Server:  dev
Address:  192.168.1.10

Name:    wahoo.dev
Address:  192.168.1.10
```

That delay is a big problem. When I try to access a ".dev" URL from the web browser, it works only part of the time, seemingly randomly. Often, I will get a message saying "Firefox can't find the server at whatever.dev." Once this happens, Firefox seems to cache the failed DNS result, because no amount of refreshing will fix the problem.

Does anyone know why I might be getting this delay?

---

### Post by Trackieman on 2007-03-06
> **CopaceticOpus said:**
> the first time I try to look up any ".dev" URL from another machine, I get a delayed response. 

The machine you are doing the lookup from, is it using the DNS server handling your .dev as it's primary DNS nameserver?

You can get really horrible delays if the machine you are browsing from first uses a DNS server that knows nothing about your .dev domain

---

### Post by CopaceticOpus on 2007-03-08
Thanks for the reply... I'm using the local DNS machine as the primary DNS server, with an external public DNS server as the alternate.

I've been getting strange, intermittent behavior. Sometimes it works great and I can load any .dev domain instantly. But just when I think it's working right, I'll try later in the day and I get slow responses and failed lookups. I can't figure it out.

---

### Post by talz13 on 2007-03-12
What does it mean, "replace example.com with your domain name"?  Does that just mean to replace it with my server's hostname?  I don't recall assigning an actual domain name to my machine...

---

### Post by phormion on 2007-03-12
CopaceticOpus , you might want to try dig as a DNS troubleshooting tool, the nslookup program that comes with Windows is far from ideal in that respect. Look up a binary BIND distro for windows on ISC's website ([www.isc.org)](www.isc.org)). The latest is BIND 9.4.0. dig is also part of that, and its output is more verbose and more helpful than the one from nslookup. 

A sniffer (e.g. like wireshark) might also help in troubleshooting.

---

### Post by 2012_ad on 2007-03-14
Okay, here's one for you guys...  

I haven't seen a topic on this or a how-to and will create a new post if you think I should.

I want to setup a DNS server using Ubuntu server.
The server will have to serve as a DHCP/DNS/WINS server for the internal network to resolve internal hostnames and handle requests for the outside (www) as well.  This is a network of about 100 workstations on VLANs, address ranges from 192.158.51.0-192.168.60.0

Here's the catch, some workstations, because of their location and job function, can't have full blown internet access but there are a handful of websites (maybe 10 or so) that they DO need to have access to.  

I am currently accomplishing this by using two Windows 2003 servers, one server (..51.6) is the full blown internet access DNS server with forwarders to our outside DNS.  The other server (..51.8) is the limited DNS server that only knows about a handful of website addresses which I've statically configured the IPs for.

How I'd like this to work:  I'd like to configure either two network cards or one network card with two ip addresses on Ubuntu server.  Any request to ..51.6 will allow access, any request to ..51.8 will DENY access unless it's a site I allow, then it will forward to ..51.6 for resolution.

I need to do this to consolidate the servers and to relieve load on one of the servers. 

I have a base install of Ubuntu server ready to go.  Any help is appreciated.

---

### Post by Abhi Kalyan on 2007-03-16
Been searching for such knowledge,
Am trying to integrate DNS and DHCP so that the DHCp updates the DNS, And what ever is the IP served out by the DHCP the other systems should be able to get the system. But am getting stuck some where and i dont Know Where. Thank you, WIll be reading this post .
Thank you
All the best

---

### Post by jparello on 2007-03-16
Hi,

I went through this setup and then had problems with the comments lines. Sometimes you have // other times you have #

When I was setting up my .db files I cut/paste from the guide above and got errors in the startup. One good thing to do when you restart the bind9 is to tail the daemons.log

any errors in loading the files will show up there.

In mydomain.com.db file I got an error from the // comments and had this in /var/daemons.log

[B]Mar 16 15:56:36 server named[28388]: /etc/bind/zones/mydomain.com.db:1: unknown RR type 'replace'
Mar 16 15:56:36 server named[28388]: zone mydomain.com/IN: loading master file /etc/bind/zones/slytly.com.db: unknown class/type[/B]

Well the first comment line in the file has the word **replace** in it so I removed all the // comments 

That was it. For some reason the // comments were not being processed.

I'm not sure if I had some fat finger error in there or not but it may help you if you tail the daemons.log when you restart bind9 to look for any errors in your .db files.

HTH

---

### Post by phormion on 2007-03-17
jparello, you can also use named-checkconf to check your configuration file (or named-checkzone to check your zone files). They are part of the BIND distribution, and I think they are included in the bind9 Ubuntu package. 

2012_ad, you can accomplish that with a firewall or proxy, it's not absolutely necessary to use DNS. However, if you wish you can configure a root zone on the limited nameserver, and put whatever hosts you want to be accessible. The other nameserver would be a regular caching-only nameserver (I think on Debian/Ubuntu bind comes configured for that out of the box), with forwarders configured if you are positive that you need them. 

Forwarders add another point of failure to your DNS setup - you depend on the provider's DNS servers to be always accessible. Also, maybe your provider's nameservers weren't designed with forwarding in mind. Your nameservers can resolve just fine without forwarding.

---

### Post by whtet on 2007-03-23
I have set up the box following the instruction and it works but with a few glitches.
e.g. If I try to ' dig hostname.mydomain.com' it works but if I 'ping hostname.mydomain.com' it's not working. 
I have to spend some time to solve the issue. 
I also have problems with the reverse look up. 'nslookup xx.xx.xx.xx' is not working. 

Finally I find the problems and they all have to do with the comment type.
I cannot use '//' or '#' in the zone files but ';'.  After I have taken out '//' and '#' from the zone (reverse) files 
'ping hostname.mydomain.com' and 'nslookup xx.xx.xx.xx' is working again. 

I still needs to troubleshoot why 'dig hostname' is not working while 'ping hostname' is working.

---

### Post by papayiya on 2007-03-23
Hi,

Thank you for the tutorial, it worked great.
So now I have my

ns1.xxxx.com
ns2.xxxx.com

I want to set up another domain say abc.com to use my new DNS servers.  I went through the process of registering the domain, setting the DNS servers to the above from GoDaddy, set up a new virtual host in apache, etc..  

My quesiton is, how do I add another domain to my bind configuration?
I'd post what I did so far, but that might just confuse others.
Can you post a general example about what needs to be added in the bind?

Any help would be appreciated..
Thanks
George

---

### Post by CopaceticOpus on 2007-03-26
> **whtet said:**
> I still needs to troubleshoot why 'dig hostname' is not working while 'ping hostname' is working.

I've experienced this intermittently. Most of the time I can ping internal hostnames, but sometimes, some of them just don't work. Then I'll come back later in the day and suddenly they do work.

This is the same basic problem as I'm having with resolving internal hostnames within Firefox on XP. Sometimes they work, sometimes they don't. If it doesn't work in Firefox, then ping will also be broken, so these issues share the same root cause.

Thank you phormion for the link to dig for Windows. Here's the output I see for dig and nslookup. I no longer get the timeout for nslookup (and I'm not sure how I fixed that), but the basic problem still remains.

```

dig zencartdemo.dev

; <<>> DiG 9.4.0 <<>> zencartdemo.dev
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 899
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;zencartdemo.dev.               IN      A

;; ANSWER SECTION:
zencartdemo.dev.        38400   IN      A       192.168.1.10

;; AUTHORITY SECTION:
dev.                    38400   IN      NS      dev.

;; Query time: 0 msec
;; SERVER: 192.168.1.10#53(192.168.1.10)
;; WHEN: Mon Mar 26 12:54:58 2007
;; MSG SIZE  rcvd: 63
```

```

nslookup zencartdemo.dev

Server:         192.168.1.10
Address:        192.168.1.10#53

Name:   zencartdemo.dev
Address: 192.168.1.10
```

---

### Post by dpanacea on 2007-04-21
tomtom_in_eire great tutorial, worked well for me.

Hope you don't mind, I copied your post to the ubuntu wiki manual at [http://http://ubuntuguide.org/wiki/Ubuntu:Feisty/Networking#How_to_Setup_BIND_DNS_Server]("http://http://ubuntuguide.org/wiki/Ubuntu:Feisty/Networking#How_to_Setup_BIND_DNS_Server")

---

### Post by L0rd_Rahl on 2007-04-25
I'm having a similar problem to CopaceticOpus. Name resolution works great when browsing locally from the bind server, but clients on the local network can rarely perform successful lookups. Sometimes it works, sometimes it doesn't. This is the case for both local and global DNS entries. It almost looks like a network connectivity issue, however communication via IP rather than DNS works great all the time. I've looked at my firewall logs (and disabled) - it doesn't seem to be an issue there. I can also consistently telnet into the bind port from a remote machine, even though the actual lookups fail with a timeout.

---

### Post by L0rd_Rahl on 2007-04-28
It was in fact a firewall problem. Everything is working well now...

---

### Post by nasirazizawan on 2007-05-03
hmmm .. all this is helpful .. but wot i was looking for is 

i have a local network or more than 500 computers. working with out any domain or central control. 

I am running a windows base DHCP to serve the IP address to clients. now i want to setup a dns server Ubuntu based , to keep track of the naming of all the computers.


regard,


nasir aziz awan.

---

### Post by phanter on 2007-05-16
GREAT Tutorial It works fine fne i!! Thank's a lot. BTW I'm using  Feisty Fawn. All Perfect. :)

---

### Post by phanter on 2007-05-16
> **Coogan said:**
> I'm getting this error when trying to start Bind:

```
Nov 21 21:59:47 localhost named[10645]: starting BIND 9.3.2 -u bind
Nov 21 21:59:47 localhost named[10645]: found 1 CPU, using 1 worker thread
Nov 21 21:59:47 localhost named[10645]: loading configuration from '/etc/bind/named.conf'
Nov 21 21:59:47 localhost named[10645]: /etc/bind/named.conf:55: unknown option 'forwarders'
Nov 21 21:59:47 localhost named[10645]: loading configuration: failure
Nov 21 21:59:47 localhost named[10645]: exiting (due to fatal error)

```

Here's the forwarders part in named.conf:

```
forwarders {
  205.152.37.23;
  };
```

Any idea what I'm doing wrong?  I'm trying to set up an DNS server that'll act as a local cache (Bellsouth's DNS kinda sucks) and so I set up a few internal websites and servers.

Coog

Well, firts of all 

You should change the location of the option 'forwarders' into the file 'named.conf.options' 
and remove it from the 'named.conf' file.

This because in the named.conf file there is an include section for the 'named.conf.options' file so maybe the problem is around there. And if there is not the include. here's an example:

```

include "/etc/bind/named.conf.options";

```

Hope it works. Any questions or corrections are welcome. :D

---

### Post by dthacker on 2007-06-27
I tried to use this tutorial to build an internal (not internet exposed) dns server on fiesty ubunt-server and it's been a struggle.  bind9 loads, but is not functional.  The named-checkconf is spitting out all kinds of errors.

```
zone localhost/IN: loaded serial 1
zone 127.in-addr.arpa/IN: loaded serial 1
zone 0.in-addr.arpa/IN: loaded serial 1
zone 255.in-addr.arpa/IN: loaded serial 1
dns_rdata_fromtext: /etc/bind/zones/dthacker.org.db:6: near 'dthacker.org.': syntax error
zone dthacker.org/IN: loading master file /etc/bind/zones/dthacker.org.db: syntax error
_default/dthacker.org/IN: syntax error
dns_rdata_fromtext: /etc/bind/zones/rev.1.168.192.in-addr.arpa:6: near eol: unexpected end of input
/etc/bind/zones/rev.1.168.192.in-addr.arpa:9: no TTL specified; zone rejected
/etc/bind/zones/rev.1.168.192.in-addr.arpa:10: no TTL specified; zone rejected
/etc/bind/zones/rev.1.168.192.in-addr.arpa:16: unknown RR type 'example.com'
dns_rdata_fromtext: /etc/bind/zones/rev.1.168.192.in-addr.arpa:22: near eol: unexpected end of input
/etc/bind/zones/rev.1.168.192.in-addr.arpa:25: no TTL specified; zone rejected
/etc/bind/zones/rev.1.168.192.in-addr.arpa:26: no TTL specified; zone rejected
zone 1.168.192.in-addr.arpa/IN: loading master file /etc/bind/zones/rev.1.168.192.in-addr.arpa: unexpected end of input
_default/1.168.192.in-addr.arpa/IN: unexpected end of input

```

I don't understand why bind is complaining about TTL settings, none were specified in the tutorial.  I also can't tell if semicolons are necessary, or just comment indicators.  Here are my zone files.

```
dthacker.org.  IN SOA ns1.dthacker.org. (
                                  2007062602
                                  28800
                                  3600
                                  604800
                                  38400; )

dthacker.org.           IN NS ns1.dthacker.org.

ns1             IN  A  192.168.1.30
buckbeak        IN  A  192.168.1.5
fluffy          IN  A  192.168.1.3

```

```
@ IN SOA ns1.dthacker.org. (
                        2007062602;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     ns1.dthacker.org
30                    IN    PTR   dthacker.org

```

Any help would be appreciated. These eol errors are driving me nuts!

---

### Post by CopaceticOpus on 2007-07-05
**dthacker**: I think your problem is the semicolon in this line:

> 38400; )

The semicolon is the start of a comment in these files, so everything after the semicolon on that line is ignored. This means your closing parentheses is not being recognized.

---

### Post by Nokao on 2007-07-25
Internal dns service seems to work, however:

I didn't understand how to define a certain IP for an EXTERNAL whatever website... and WHERE to do it.

---

### Post by dmfrey on 2007-08-19
I followed this tutorial for my Feisty server.  My clients can all ping/nslookup/dig the dns server, however, they cannot perform any of those commands on other clients on the network.  My network consists of three machines: the dns server, one static ip client, and one dynamic ip client.  Each has the resolve.conf setup to point back to the dns server.  How do i get the name resolutions established for all of the clients on the network automatically?

Thanks for any help.

---

### Post by mark27 on 2007-08-21
Hy i have problem when i am restarting the bind9 
i am having this ouput 
 Stopping domain name service...                                              rndc: connect failed: connection refused
                                                                         [ ok ]
 * Starting domain name service...     .

i would like to know how can i solve the problem, what happen it.

---

### Post by CopaceticOpus on 2007-08-21
I typed "rndc" into Google and the first result describes your error message and a suggested remedy for it:

[http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-bind-rndc.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-bind-rndc.html)

---

### Post by bignose on 2007-08-21
> **CopaceticOpus said:**
> I typed "rndc" into Google and the first result describes your error message and a suggested remedy for it:

[http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-bind-rndc.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-bind-rndc.html)

I'm having the exact same error. Except :

I have a defult LTS install where rndc works just fine and there is not a 'control statement in named.conf...

Then I have another machine that a colo facility installed for me, and rndc just won't go... and the named.conf files do not differ [i ran a diff on them]

CORRECTION : the working machine is LTS, the non working one is Edgy, however teh files still do not differ.

Jeff.

---

### Post by sgla1 on 2007-08-27
> **hogman23 said:**
> One more step to get it to work:
You must rename the named.conf.local to named.conf

If you read all the way to the bottom of named.conf you will see the following line:
```
include "/etc/bind/named.conf.local";
```
You absolutely need named.conf -- if you are foolish enough to rename it (thereby overwriting named.conf--see man mv) you will never have a working dns server.  The only way to eliminate named.conf.local is to paste all of it's contents into named.conf.

I'm sorry if this sounds harsh but unfortunately there is a lot of bad advice in these forums.  People, please test your advice carefully before you post.

---

### Post by sgla1 on 2007-08-27
Please ignore--does not reference OP

---

### Post by stubba on 2007-11-01
> My clients can all ping/nslookup/dig the dns server, however, they cannot perform any of those commands on other clients on the network

I'm having the same issue. Any help greatly appreciated...

---

### Post by lkstamenov on 2007-11-21
Nice! Works! But if you add the following :

1. Remove any comments from the zones files (those in zones directory)
2. Test the domain with 
sudo named-checkzone exampledomain.com

And it works like a dream

---

### Post by iLLiCiTgr on 2007-11-21
Interesting Guide

---

### Post by Gunner_Sr on 2007-12-14
> **phormion said:**
> stijn_pol, underscores in host names are illegal according to RFCs (I can't remember if it was the DNS RFCs or another one, it was explained on the bind-users list). This was checked in older versions of BIND (for example 8.x); BIND 9.2 didn't perform host name checking, but the feature was reimplemented in BIND 9.3 and that's what I think bit you. 

You can work around that using the 'check-names' option, if you're *really* convinced you need underscores in your hostnames. 

For diagnosing problems in your BIND configuration, named-checkconf or named-checkzone are your friends. They are part of the BIND source package, although I don't know in which Ubuntu package they are installed.

The named-checkzone and checkconf fixed it for me!!

Thanks. :popcorn:

-Gunner_Sr

---

### Post by BoltCutter on 2008-01-06
I have this problem at the very beginning of the installation, could some one help me. I'm kinda new at the ubuntu linux
Thanks
Bolt

user@computer:~$ sudo apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bind9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nxserver (2.1.0-22) ...
NX> 704 ERROR: Cannot add user: nx. User: nx already exists.
NX> 704 ERROR: Please try to fix the problem by reinstalling the server.
dpkg: error processing nxserver (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@computer:~$

---

### Post by otake-tux on 2008-01-07
this thread helped me but all was not perfect.  

I advise following every step, then opening another terminal on the box and running

tail -f /var/log/daemons.log


there will be error messages there.  just because bind runs doesn't mean its working.  I fixed accordingly and got everything to work.  good job, OT. :guitar:

---

### Post by cov on 2008-01-09
I have tried to follow the recipe provided here to get my DNS working.

My /etc/bind/named.conf.local:```
zone "iqetd.co.za" {
        type master;
        file "/etc/bind/zones/iqetd.co.za.db";
};
zone "60.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.60.168.192.in-addr.arpa";
};


```
/etc/bind/zones/iqetd.co.za.db```
iqetd.co.za     IN      SOA     Base.iqetd.co.za (
                                2006081401
                                28800
                                3600
                                604800
                                38400
)
iqetd.co.za.    IN      NS      Base.iqetd.co.za
Base            IN      A       192.168.60.254



```

/etc/bind/zones/rev.60.168.192.in-addr.arpa```

@       IN      SOA     Base.iqetd.co.za (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
                        )
@       IN      NS      Base.iqetd.co.za.
254     IN      PTR     iqetd.co.za.


```

'named-checkconf /etc/bind/named.conf' produces no errors.

However, 'named-checkconf -z' produces the following ```

root@Base:~# named-checkconf -z
zone localhost/IN: loaded serial 1
zone 127.in-addr.arpa/IN: loaded serial 1
zone 0.in-addr.arpa/IN: loaded serial 1
zone 255.in-addr.arpa/IN: loaded serial 1
dns_rdata_fromtext: /etc/bind/zones/iqetd.co.za.db:6: near eol: unexpected end of input
/etc/bind/zones/iqetd.co.za.db:8: no TTL specified; zone rejected
/etc/bind/zones/iqetd.co.za.db:9: no TTL specified; zone rejected
zone iqetd.co.za/IN: loading from master file /etc/bind/zones/iqetd.co.za.db failed: unexpected end of input
_default/iqetd.co.za/IN: unexpected end of input
dns_rdata_fromtext: /etc/bind/zones/rev.60.168.192.in-addr.arpa:6: near eol: unexpected end of input
/etc/bind/zones/rev.60.168.192.in-addr.arpa:8: no TTL specified; zone rejected
/etc/bind/zones/rev.60.168.192.in-addr.arpa:9: no TTL specified; zone rejected
zone 60.168.192.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.60.168.192.in-addr.arpa failed: unexpected end of input
_default/60.168.192.in-addr.arpa/IN: unexpected end of input

```

Can anyone help?

---

### Post by dbrower256 on 2008-01-26
What if my dns server is on a separate network than the clients?  For example, my dns server could be at 192.168.100.10 255.255.255.0, while my clients are on network 192.168.20.0 255.255.255.0.  

Daniel

---

### Post by tsumiro on 2008-02-02
do you have to buy a domain name from somewhere like godaddy before you do this?

im a retard. lol.

---

### Post by SimbaSpirit on 2008-02-28
I have a feeling this thread is too old to get a reply lol.

I went through your tutorial and at the end I'm a bit confused.
It says to change resolv.conf.
By change do you mean remove what was there and insert the new?
When I remove what was in there previously, add what the tutorial said, it can't dig my server, when I add the original nameservers below the one the tutorial had me add I can dig it. Is this normal or does it mean the one I added from the tutorial fails so it tries the next one?

TIA,
-SS

---

### Post by joegeek on 2008-03-20
while copy and paste is a wonderful thing sometimes your ssh proggy will continue a line on the next line, and if you dont catch it, it could mess you up.

just remember "named-checkconf" is your friend. you should run it after you edit your dns config files, but befor you restart bind.

---

### Post by blackjackchik on 2008-03-21
[http://forum.ubuntu.ru/index.php?topic=12746.0](http://forum.ubuntu.ru/index.php?topic=12746.0)
[http://forum.ubuntu.ru/index.php?topic=23524.0](http://forum.ubuntu.ru/index.php?topic=23524.0)

---

### Post by ZioNemo on 2008-04-12
Hi,
I have a net with a firewall (IPCop) and two subnets (local and DMZ) with private addresses in the range 192.168.11.xxx and 192.168.56.xxx.
I have a server in DMZ that serves my domain.
I have from my ISP a block of 16 IP addresses I can use how I like and I have a registered domain "mydomain.com" :)
I did set up my dns to serve my zone as defined by my routable addresses.
Now the problem:

I have a lot of hosts on my net that only have non-routable addresses, but I would like to call them (internally) with the same domain name "mydomain.com".

I currently have:
> 
$ttl 38400
mydomain.com.    IN      SOA     ambassador. operator.mydomain.com. (
                        1207724850
                        10800
                        3600
                        604800
                        38400 )
mydomain.com.    IN      NS      ambassador.
[www.mydomain.com](www.mydomain.com).        IN      A       83.xxx.xxx.211
mail.mydomain.com.       IN      A       83.xxx.xxx.211
smtp.mydomain.com.       IN      A       83.xxx.xxx.211
ftp.mydomain.com.        IN      A       83.xxx.xxx.212
ssh.mydomain.com.        IN      A       83.xxx.xxx.212
vpn.mydomain.com.        IN      A       83.xxx.xxx.212
gatekeeper.mydomain.com. IN      A       83.xxx.xxx.213
cisco.mydomain.com.      IN      A       83.xxx.xxx.214
cvs.mydomain.com.        IN      A       83.xxx.xxx.215
svn.mydomain.com.        IN      A       83.xxx.xxx.215
flyspray.mydomain.com.   IN      A       83.xxx.xxx.215
mail.mydomain.com.       IN      MX      1 mail.mydomain.com.
ambassador.mydomain.com. IN      A       192.168.56.10
archiver.mydomain.com.   IN      A       192.168.11.100


which seems to work, but I have no idea how to set up the reverse zone!

Can some kind soul help me?
TiA
ZioNemo

---

### Post by RHAnthony on 2008-04-25
I have my bind setup.

It's setup with one of my domains, and I can dig through 127.0.0.1 and get all the results I want just fine.

I have the domain registered through godaddy.com and it says the name servers are NS1 and NS1.dashin.net (another domain of mine, registered through godaddy, dns hosted there).

NS1.dashin.net pings and digs to the right IP, of my DNS server I just made.

My new domain is set to use it as a DNS server.

Digging the new domain from anywhere other than 127.0.0.1, returns no results and times out.

Any thoughts?

---

### Post by jessmagz on 2008-05-02
hi everyone!

I followed the steps given here (in setting up a DNS server using bind) but I stopped for a while because of the following questions:

About the network address to use in the reverse dns, my server's static IP address is 121.97.152.252, would the line look like this:

file "/etc/bind/zones/rev.252.152.97.121.in-addr.arpa" ?

or

file "/etc/bind/zones/rev.152.97.121.in-addr.arpa" ?


And about the name of the DNS server (to be substituted to "ns1" in the given example) should I use the host name of my computer? My host name is "localhost". I did not change it. Once I tried to change it to "my-ubuntu" but when I run a command with "sudo" an error appeared saying:

postfix: hostname "my-ubuntu" can't be resolved
****enter sudo password: (something like that)

So I changed it back to "localhost" and the error disappeared. 

Is my dns server name "localhost"? Should I change it to something else? How can I resolve it so that postfix will not give an error anymore?

I'm really new to linux and ubuntu... Please bear with my type of questions...

Thanks...

---

### Post by texasjim on 2008-05-03
@ JESSMAGZ

 I am in the middle of this also, but I got past the reverse IPaddr thing. Your entry for 121.97.152.252 should be as your second example:
file "/etc/bind/zones/rev.152.97.121.in-addr.arpa".

---

### Post by texasjim on 2008-05-03
> **jessmagz said:**
> hi everyone!



And about the name of the DNS server (to be substituted to "ns1" in the given example) should I use the host name of my computer? My host name is "localhost". I did not change it. Once I tried to change it to "my-ubuntu" but when I run a command with "sudo" an error appeared saying:

postfix: hostname "my-ubuntu" can't be resolved
****enter sudo password: (something like that)

So I changed it back to "localhost" and the error disappeared. 

Is my dns server name "localhost"? Should I change it to something else? How can I resolve it so that postfix will not give an error anymore?

I'm really new to linux and ubuntu... Please bear with my type of questions...

Thanks...

About your hostname:

Go to System --> Administration --> Network and click on the Hosts tab. Look for a line with address 127.0.1.1, probably the 2nd line in the display. Here's mine :
127.0.1.1  studio studio.homey.tx.org

click on the line starting with 127.0.1.1, click Properties and enter 2 lines into the Aliases box. First line will he your hostname, 2nd is your fully qualified netname you're setting up.

I know this is set up at install time, haven't tried changing it.  If this doesn't work, just put it back the way you found it.

---

### Post by MAO on 2008-05-10
Hi i've got some problems with bind Zones Files:

root@sw:/# tail -f /var/log/daemon.log
May 10 20:05:51 sw named[4705]: command channel listening on ::1#953
[COLOR="DarkRed"]May 10 20:05:51 sw named[4705]: could not open entropy source /dev/random: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: using pre-chroot entropy source /dev/random
May 10 20:05:51 sw named[4705]: zone 0.in-addr.arpa/IN: loaded serial 1
May 10 20:05:51 sw named[4705]: zone 127.in-addr.arpa/IN: loaded serial 1
[COLOR="#8b0000"]May 10 20:05:51 sw named[4705]: zone 22.29.217.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.22.29.217.in-addr.arpa failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone 255.in-addr.arpa/IN: loaded serial 1
[COLOR="DarkRed"]May 10 20:05:51 sw named[4705]: zone software.kg/IN: loading from master file /etc/bind/zones/software.kg.db failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone localhost/IN: loaded serial 2
May 10 20:05:51 sw named[4705]: running

____________________________________

root@sw:/# ls -la /var/lib/named/etc/bind/zones
total 16
drwxr-sr-x 2 bind bind 4096 2008-05-10 19:45 .
drwxr-sr-x 3 bind bind 4096 2008-05-10 19:47 ..
-rwxrwxrwx 1 bind bind  260 2008-05-10 19:45 rev.22.29.217.in-addr.arpa
-rwxrwxrwx 1 bind bind  651 2008-05-10 19:54 software.kg.db

Plz Help me !!!

---

### Post by heperez on 2008-05-13
RHAntony: Do you really check /etc/resolv.conf?.
This archive must contain the complete name of your computer (the dns computer).

And then restart the service. 
sudo /etc/init.d/bind9 restart

---

### Post by heperez on 2008-05-13
jessmagz:
Did you check the file /etc/hostname ?
What did you do, to change the computer name?.

---

### Post by eludlow on 2008-05-19
A question regarding the original post - I'm running a network that has 10 windows machines and one Linux box (my PC!).  I have a windows network working using workgroups and with samba set up to link with the linux box.

When creating my DNS zones, what should I use in place of the domain (example.com in the original guide...)?

Many thanks.

Edit to add, I want to be able to control local DNS records and also (rarely!) be able to add records to redirect external addresses to local IPs.  I know how to get this up and running in Windows, but not Ubuntu...!

---

### Post by Mech13 on 2008-05-21
Please Help me:

I have a domain name registed with GoDaddy.com called [www.rockblogband.com](www.rockblogband.com).
I'm trying to set up BindDNS on my server but i'm having some problums. I want to be able to access my server from anywhere i am, like a normal webpage.
Every time i try to start BIND DNS it works
When i run the test: dig rockblogband.com I get:
```
; <<>> DiG 9.4.2 <<>> rockblogband.com
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 669
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION;;
;rockblogband.com              IN        A

;; Query time: 1 msec
;; SERVER: 192.168.1.8#53(192.168.1.8)
;; MSG SIZE rcvd: 34
```

IP references:
My home static IP is: 65.33.21.85
Server is located on: 192.168.1.8
Ip Address assigned to my domain by Godaddy: 64.202.189.170
Nameservers assigned by godaddy: NS13.DOMAINCONTROL.COM & NS14.DOMAINCONTROL.com
My ISP's DNS Server Ip: Prim: 208.67.222.222; Sec: 208.67.220.220

This is the code that i have set up so far:

In File: /etc/bind/named.conf.local
```
# This is the zone definition. replace example.com with your domain name
zone "rockblogband.com" {
        type master;
        file "/etc/bind/zones/rockblogband.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "170.189.202.64.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.170.189.202.64.in-addr.arpa";
};
```

In File: /etc/bind/named.conf.options
```
options {
	directory "/var/cache/bind";

	forwarders {
	 	208.67.222.222;
		208.67.220.220;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};
```

In File: /etc/bind/zones/rockblogband.com.db
```
rockblogband.com.      IN      SOA     ns1.rockblogband.com. admin.rockblogband.com. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
rockblogband.com.      IN      NS              ns1.rockblogband.com.
rockblogband.com.      IN      MX     10       mta.rockblogband.com.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.0.8
mta              IN      A       192.168.0.8
ns1              IN      A       192.168.0.8
```

In File: /etc/bind/zones/rev.170.189.202.64.in-addr.arpa
```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.rockblogband.com. admin.rockblogband.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.rockblogband.com.
8                    IN    PTR    rockblogband.com
```

In File: /etc/resolv.conf
```
search rockblogband.com
nameserver 192.168.1.8
```

I'm really sorry about the long post! I'm kinda new to this :)

---

### Post by PeterK2003 on 2008-05-27
> **CopaceticOpus said:**
> I must follow up on my above posting. My setup is kind of working, but not exactly. It seems that the first time I try to look up any ".dev" URL from another machine, I get a delayed response. For example, this is the output of two nslookup commands from an XP box which is using my Linux BIND server as its DNS server:

```
C:\>nslookup wahoo.dev
Server:  dev
Address:  192.168.1.10

DNS request timed out.
    timeout was 2 seconds.
Name:    wahoo.dev
Address:  192.168.1.10


C:\>nslookup wahoo.dev
Server:  dev
Address:  192.168.1.10

Name:    wahoo.dev
Address:  192.168.1.10
```

That delay is a big problem. When I try to access a ".dev" URL from the web browser, it works only part of the time, seemingly randomly. Often, I will get a message saying "Firefox can't find the server at whatever.dev." Once this happens, Firefox seems to cache the failed DNS result, because no amount of refreshing will fix the problem.

Does anyone know why I might be getting this delay?

I am having a similar issue.  Any Solutions yet?

---

### Post by mark36ph on 2008-06-16
i am trying to get bind working but when i run "named-checkconf -z" i get the following

```
/etc/bind/zones/m36ph.info.db:1: no TTL specified; using SOA MINTTL instead
zone m36ph.info/IN: loaded serial 2006081401
/etc/bind/zones/rev.0.1.168.192.in-addr.arpa:1: no TTL specified; using SOA MINTTL instead
zone 0.1.168.192.in-addr.arpa/IN: loaded serial 2006081401

```

any clues where I'm wrong?

here are my files.

**named.conf**
```
zone "m36ph.info" {
        type master;
        file "/etc/bind/zones/m36ph.info.db";
        };

zone "0.1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.1.168.192.in-addr.arpa";
};
```

**named.conf.local**
```
zone "m36ph.info" {
        type master;
        file "/etc/bind/zones/m36ph.info.db";
        };

zone "0.1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.1.168.192.in-addr.arpa";
};
```

**named.conf.options**
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	 query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

forwarders {
      # Replace the address below with the address of your provider's DNS server
      93.96.17.146;
};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

**m36ph.info.db** < that is my domain name
```
m36ph.info.      IN      SOA     ns1.m36ph.info. admin.m36ph.info. (
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

m36ph.info.      IN      NS              ns1.m36ph.info.
m36ph.info.      IN      MX     10       mta.m36ph.info.

www              IN      A       192.168.1.71
mta              IN      A       192.168.1.71
ns1              IN      A       192.168.1.71
```


```
rev.0.1.168.192.in-addr.arpa
``` - my local machine ip is 192.168.1.71 (that takes me to my web server)
```
@ IN SOA ns1.m36ph.info. admin.m36ph.info. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.m36ph.info.
71                    IN    PTR    m36ph.info
```


Thanks for any help.

---

### Post by XS-Extreme on 2008-07-06
Hi Guys ...


Thanks for the guide .. but i dont know how should i do it for my own domain ......

Also my problem is that ...
First I give my infos...

I have a router and that give my server an ip. i have allready [B]set the ip of the server on static..  192.168.2.12
and have this domain for example:  test.pe
and a public IP 123.452.33.22 
and want to host my test.pe on the server too .[/B]

[B]
I only want to get something when i put on the browser on firefox [www.test.pe](www.test.pe) and i want get the messages "it works" from apache 
[/B]

------------------------------------
This is what i did.
------------------------------------

1.  sudo apt-get install bind9
2.  sudo vi /etc/bind/named.conf.local

3.
....

# This is the zone definition. replace example.com with your domain name
zone "**test.pe**" {
        type master;
        file "/etc/bind/zones/**test.pe.db"**;
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "**2.168.192.in-addr.arpa**" {
     type master;
     file "/etc/bind/zones/**rev.2.168.192.in-addr.arpa**";
};

4. sudo vi /etc/bind/named.conf.options

5.
.......
forwarders {
      # Replace the address below with the address of your provider's DNS server
      123.123.123.123;
};

6. sudo mkdir /etc/bind/zones
7. sudo vi /etc/bind/zones/**test.pe.db**
8.
......

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
**test.pe. **     IN      SOA     **myserver.test.pe.** **admin.test.pe.** (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
**test.pe. **     IN      NS              [B]myserver.test.pe.
[/B]
// Replace the IP address with the right IP addresses.
www              IN      A       **192.168.2.12**
**myserver**         IN      A       **192.168.2.12**


9. sudo vi /etc/bind/zones/**rev.2.168.192.in-addr.arpa**

10. 
...


//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA **myserver.test.pe.** admin**.test.pe.** (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     **myserver.test.pe.**
1                    IN    PTR    **test.pe**



11. sudo /etc/init.d/bind9 restart
12. sudo vi /etc/resolv.conf
13.
...
// replace example.com with your domain name, and 192.168.0.1 with the address of your new DNS server.
search **test.pe**
nameserver **192.168.2.12**

14.dig **test.pe**


Are these Changes good .. and why i dont get my IP when i put nslookup test.pe

---

### Post by benbowler on 2008-07-07
> **garbergs said:**
> I also had trouble installing bind9, so I tried to write:

apt-get install bind

and that gave me version 8.4.6-1. I'm sure this will suffice for my simple home network.

You could probably fix this by running:

```
apt-get update
```

This would update the package lists as the problem may have been that when you last updated or use apt-get the current version of bind was version 8.4.6-1.

I asume version 8.4.6-1 would work with no problems anyhow just a tip.

---

### Post by mustimasti on 2008-07-15
> **tomtom_in_eire said:**
> After looking on Ubuntu forum for an easy step-by-step howto for instaling a DNS server, I decided the best idea would probably be to write this howto myself.... So, here it is!

**Step 1**: Install Ubuntu dapper, or use your WORKING installation.

**Step2**: Install bind 9:
```
sudo apt-get install bind9
```
**Step 3**: Configure the main Bind files. Usually, if you install Bind from the source code, you will have to edit the file named.conf. However, Ubuntu provides you with a pre-configured Bind, so we will edit another file:
```
sudo vi /etc/bind/named.conf.local
```
This is where we will insert our zones. By the way, a zone is a domain name that is referenced in the DNS server ;)
Insert this in the named.conf.local file:
```

# This is the zone definition. replace example.com with your domain name
zone "*example.com*" {
        type master;
        file "/etc/bind/zones/*example.com*.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "*0.168.192*.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.*0.168.192*.in-addr.arpa";
};

```
Ok, now, let's edit the options file:
```
sudo vi /etc/bind/named.conf.options
```
We need to modify the forwarder. This is the DNS server to which your own DNS will forward the requests he cannot process.
```

forwarders {
      # Replace the address below with the address of your provider's DNS server
      123.123.123.123;
};

```
Now, let's add the zone definition files (replace *example.com* with your domain name:
```

sudo mkdir /etc/bind/zones
sudo vi /etc/bind/zones/*example.com*.db

```
The zone definition file is where we will put all the addresses / machine names that our DNS server will know. You can take the following example:
```

*// replace example.com with your domain name. do not forget the . after the domain name!*
*// Also, replace ns1 with the name of your DNS server*
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
*// Do not modify the following lines!*
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

[I]// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name[/I]
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mta.example.com.

*// Replace the IP address with the right IP addresses.*
www              IN      A       192.168.0.2
mta              IN      A       192.168.0.3
ns1              IN      A       192.168.0.1

```
Now, let's create the reverse DNS zone file:
```
sudo vi /etc/bind/zones/rev.0.168.192.in-addr.arpa
```
Copy and paste the following text, modify as needed:
```

[I]//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.[/I]
@ IN SOA ns1.example.com. admin.example.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.example.com.
1                    IN    PTR    example.com

```
Ok, now you just need to restart bind:
```
sudo /etc/init.d/bind9 restart
```
We can now test the new DNS server...
Step 4: Modify the file resolv.conf with the following settings:
```
sudo vi /etc/resolv.conf
```
enter the following:
```

*// replace example.com with your domain name, and 192.168.0.1 with the address of your new DNS server.*
search example.com
nameserver 192.168.0.1
```
Now, test your DNS:
```
dig example.com
```

Look at the result.... Enjoy!
Also, this post is not perfect... Do not hesitate to improve it!



AFTER DOING THE FOLLOWING STEPS WHEN I RESTART MY BIND9

RNDC: CONNECT FAILED: 127.0.0.1#953: CONNECTION REFUSED
STOPPING DOMAIN NAME SERVICE ......BIND [FAIL]
STARTING DOMAIN NAME SERVICE ......BIND [FAIL]

I AM FACING WITH THIS ISSUE

AND WHEN I DO DIG DOMAINNAME.COM

IT SHOWS BE THIS :

; <<>> Dig 9.4.2 <<>> domainname.com
;; global options:printcmd
;; connection time out; no servers could be reached

PLEASE HELP AS SOON AS POSSIBLE

---

### Post by webweaver on 2008-07-24
Hi there,

I've followed this tutorial and tinkered around with other helpful hints Google showed me, but I still can't get this working properly.

I can ping servername and servername.example.local from the server, and I can ping servername from the client, but for some reason I cannot ping servername.example.local from the client!

And I can also ping clientname from the server, but not clientname.example.local...

What's going on?

Config files below:

**Server's /etc/hosts**
```

127.0.0.1 localhost
127.0.1.1 servername servername.example.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

**Server's /etc/hostname**
```

servername

```

**Server's /etc/resolv.conf**
```

domain example.local
search example.local
nameserver 192.168.1.7
nameserver 192.168.1.254

```

**Client's /etc/hosts**
```

127.0.0.1 localhost
127.0.1.1 clientname clientname.example.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

**Client's /etc/hostname**
```

clientname

```

**Client's /etc/resolv.conf**
```

domain example.local
search example.local
nameserver 192.168.1.7
nameserver 192.168.1.254

```

---

### Post by bad_boy on 2008-08-05
> **XS-Extreme said:**
> Hi Guys ...


Thanks for the guide .. but i dont know how should i do it for my own domain ......

Also my problem is that ...
First I give my infos...

I have a router and that give my server an ip. i have allready [B]set the ip of the server on static..  192.168.2.12
and have this domain for example:  test.pe
and a public IP 123.452.33.22 
and want to host my test.pe on the server too .[/B]

[B]
I only want to get something when i put on the browser on firefox [www.test.pe](www.test.pe) and i want get the messages "it works" from apache 
[/B]


Are these Changes good .. and why i dont get my IP when i put nslookup test.pe

i have same problem, please help me!:(

---

### Post by BrendanP on 2008-08-06
Any idea why I get this?
```
root@hostname:/etc/bind# /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                                                                                                      rndc: connect failed: 127.0.0.1#953: connection refused

 * Starting domain name service... bind
```

---

### Post by sefs on 2008-08-10
how do you jail / chroot a setup like this for security?

---

### Post by poszest16 on 2008-08-20
I had the worst time trying to resolve why the bind9 was not giving out the zone information. nslookup, host and ping were interrupted by the zone entry but no ip was returned. have hours of debugging. I found using "named-checkzone example.com zones/db.example.com" (not my real domain) that something about TTL not specified, zone rejected. So I did so research and updated my zone file like so:

Original first line of example:
example.com.      IN      SOA     ns1.example.com. admin.example.com. (

Replace with:
$TTL 604800
@      IN      SOA     ns1.example.com. admin.example.com. (

Worked like a charm!!!
I am so surprised I could not find this answer anywhere online.

---

### Post by wgregori on 2008-08-20
I would like to setup DNS Resolve Permits list so that I can control who as access to my DNS service.  I would also like to setup DNS Zone Transfer Permits.  Can anyone point me to a good resource?

Thanks,
Wayne

---

### Post by egc52556 on 2008-08-23
Useful debugging tools for DNS issues are:

[INDENT]nslint - Checks for problems in DNS files
dnswalk - Checks dns zone information using nameserver lookups[/INDENT]

Both are available as Ubuntu packages, e.g.:
```
sudo apt-get install nslint
sudo apt-get install dnswalk
```

---

### Post by trickyexpert on 2008-08-25
hi. i don't understand this part. 

Step 3: Configure the main Bind files. Usually, if you install Bind from the source code, you will have to edit the file named.conf. However, Ubuntu provides you with a pre-configured Bind, so we will edit another file:

```
sudo vi /etc/bind/named.conf.local
```

This is where we will insert our zones. By the way, a zone is a domain name that is referenced in the DNS server
Insert this in the named.conf.local file:

```
# This is the zone definition. replace example.com with your domain name
zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};
```

i really don't understand. after i type this ```
sudo vi /etc/bind/named.conf.local
``` in the terminal, i get this:

```
E325: ATTENTION
Found a swap file by the name "/etc/bind/.named.conf.local.swp"
          owned by: root   dated: Sun Aug 24 16:36:39 2008
         file name: /etc/bind/named.conf.local
          modified: YES
         user name: root   host name: ubuntu
        process ID: 7076
While opening file "/etc/bind/named.conf.local"
             dated: Thu Apr 10 03:42:59 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/bind/named.conf.local"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/bind/.named.conf.local.s
wp"
    to avoid this message.
"/etc/bind/named.conf.local" 8 lines, 165 characters
Press ENTER or type command to continue

```

yeah, what's that? by the way, i'm new to this ubuntu server. i need help. ASAP. thanks.

---

### Post by nodoubtd on 2008-08-28
Really is there a good tutorial available?  Does it work with Hardy aka current s/w?  

Summary for Techies:  Those of you with the “open-source personality” that have functional Authoritative DNS servers operating don’t have the time to make a good, and self checked tutorial.  Pick one of these “popular” tutorials – I will complete – Q&A it – then send concise detailed bug reports until the tutorial is truly complete, easy to follow and accurate.  Then I will post with a clear searchable title with links in all forums and tutorial sites listed in this post with ACTIVELY aiding participants CLEARLY noted.  Links to tutorials @ btm of pg.


Detailed Explanation:  I am not looking for someone to try to help me with a particular problem.  Rather I am looking for an accurate, detailed, recent, preferably self tested tutorial on setting up a BIND9 authoritative server.  BIND authoritative AND caching server setup tutorials will be accepted as well; if a strictly authoritative server tutorial is not available YET.?!  I am a windows administrator of 10 years who has not bought into the Open-Source wave until I reached the holy grail of Authoritative DNS servers.  As you all know there is NO way to create an Authoritative DNS server on Windows w/out paying hundreds or thousands of dollars for the NT Server Super Package.  Windows too has an open-source movement and most everything available for pay is available in a free version if you look and are willing to have less user-friendly gui’s. But DNS is held above normal programs of course and no-one but Mara-dns, and SANS has attempted to build an open-source authoritative dns for windows platform.  You all know DNS Authoritative server configuration the key – no website operates without it!!  You know NO top-notch tutorials exist – there is not one tutorial, or discussion on the topic that does not have unanswered problems on it.  As a corporate desktop and website liaison I am clear as to why techies are not too eager to hand over key knowledge, or you can say we all understand you learn best when you figure things out on your own.  Whether I agree with holding knowledge close to the breast or not – Linux and Ubuntu claim to be open-source and eager to have people “participate” in using, developing, and teaching the OS.  I have taught myself Linux enough to run the gnome desktop, network a small lan, and serve a website to the world.  Never have I asked for any knowledge that was not available publicly already, be shared with me – I understood why no tutorials, or manuals were completely accurate and clearly not self-checked.  

I have fully completed, checked, read comments, searched discussions, forums, postings, and visited IRC for all the below tutorials to complete them.  I have become quite familiar with the common problems initially configuring BIND9 on Ubuntu.  Basically I have taken the time to complete these tutorials, carefully researched anomalies I found in each tutorial and made some basic notes on each.  This is how I have come to the conclusion none are complete – not only do none have everything necessary to setup bind, but they often have mistakes, typos, and even contradict manual/other tutorial/publicly released fixes.  How is someone supposed to follow a tutorial that leaves out fixes, and contradicts the manual &#61514;.  Being new to Linux I do not have the knowledge to confidently put together a good tutorial, but I have the ambition and a solid background to make the process easy.  I want to create the one thing Linux still needs to make it truly Open-source to the public.  A free OS with almost competitive word and excel is good, but if you really want to help those in developing areas you need to make the entire food chain to the world Open-source.  My challenge and offer to the Ubuntu Linux Community is this: 
	Demonstrate the definition of Ubuntu and help me help you show the Ubuntu server really is for everyone. Help me create the 1st truly useful BIND tutorial and make Ubuntu the first linux platform to successfully do this (perhaps FreeBSD has won the battle, but Ubuntu can still win the war due to its media popularity) This will take far less time than you all have spent TRYING to trouble shoot the various tutorials created but not refined.  I will post this top-notch tutorial with a clear searchable title and links in all forums and tutorial sites listed in this post with ACTIVELY aiding participants CLEARLY noted.  This is all I should have to offer the “truly open-source community”.  Thank you for your time.

Tutorials on BIND9 DNS:
[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)

[http://www.unix-tutorials.com/go.php?id=917](http://www.unix-tutorials.com/go.php?id=917)

and of course this “tutorial” I am posting to now

There are other tutorials that seem to repeat parts of these listed tutorials, but these seem to be the most complete, and tested available.  Thank you for your time.  Feel free to PM me, post a link to a tutorial EVERYONE has somehow missed, or take me up on what seems like a much needed effort.

---

### Post by Crafty Kisses on 2008-08-28
I've seen a couple goot tutorials on Google somewhere I'll try to get them, but I thought this was a decent one with everyone contributing and what not.

---

### Post by Oceanwatcher on 2008-12-01
I have been looking at this how-to and on this page

[http://www.madboa.com/geek/soho-bind/]("http://www.madboa.com/geek/soho-bind/")

to find out as much as possible how to set up a caching DNS that also resolves my small, local network.

As far as I understand, there is not a lot of information needed to get this running, but one thing that might be an idea for anyone out there that want to help absolute beginner get this right without a lot of hassel, is to make a webpage where you just enter the needed information in a form and get the files ready to be copied.

Here is what I figure is needed:

The model is a small network with a router acting as the gateway, a Ubuntu server and a number of pc's, Linuxboxes or Mac's connected to the lan.

An official domain exists and is hosted on an external webhotel. It is important not to mess up this, so a local subdomain is made - lan1.xyxyxy.com

POP3, IMAP and SMTP servers are available at the webhotel address mail.xyxyxy.com

The DNS server for the small network will of course be this server. It will also be a web server (LAMP) and a file server running SAMBA.

Server name: black
Local domain name: lan1.xyxyxy.com (replace xyxyxy.com with your official domain name)
Server IP address: 10.0.0.10
Netmask: 255.255.255.0
Gateway: 10.0.0.1
DNS1: 208.67.222.222 (Using OpenDNS)
DNS2: 208.67.220.220 (Using OpenDNS)

Additional computers on the lan:

IP: 10.0.0.20 name: blue
IP: 10.0.0.21 name: red
IP: 10.0.0.22 name: green

Do I need anything else to set up the local DNS, or is this information complete?

Anyone out there that would like to make a BIND9 generator for Ubuntu? A webpage that generates the files so beginners can just copy them?

---

### Post by Oceanwatcher on 2008-12-01
In the options file, is it ok to add two DNS'es, each one on a separate line? So it becomes (using OpenDNS)

```
forwarders {
      # Replace the address below with the address of your provider's DNS server
      208.67.222.222;
      208.67.220.220;
};
```

In the zone definition, you have this line:
```

example.com.      IN      SOA     ns1.example.com. admin.example.com. (
```

If your lan is called lan1.xyxyxy.com and your server is called black, would it be correct to have this?
```

lan1.example.com.      IN      SOA     black.lan1.example.com. black.lan1.example.com. (
```

Or do you need to have ns1 and admin? Anyway - what is admin.example.com? Is it a mandatory address?

How do you indicate in the zone file that you have an external mailserver? POP3, IMAP and SMTP are all on the same server - mail.xyxyxy.com

I am in the middle of trying to sort out all this and get it working on my local server... Learning a little every day, but impatient to get it all working :-)

---

### Post by Oceanwatcher on 2008-12-01
Here is another quick question:

I have a laptop that can connect both wired and wireless. If I want to include this laptop in the zonefile, will this be correct?

```
yellow    IN    A    10.0.0.25
yellow    IN    A    10.0.0.35
```

---

### Post by Oceanwatcher on 2008-12-01
Did a test of the setup so far and I am getting an error on the forwarding:

```
/etc/bind/named.conf.options:8: unknown option 'forwarders'
```

I even deleted the commented lines to make sure comments did not mess up the forwarders:

```
options {
        directory "/var/cache/bind";

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

forwarders {
      208.67.222.222;
};
```

After some searching, I found the answer. There is an error in the example - here is what I think the options should look like:

```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

forwarders {
      # Replace the address below with the address of your provider's DNS server
      208.67.222.222;
      208.67.220.220;
	  };
};
```

Notice the bracket and the semicolon that has been moved from the line above "forwarders" and down under the IP addresses. The "forwarders" option needs a closing bracket and it needs to be within the "options" brackets. A bit like div tags :-)

EDIT: Ehrrmm... After checking the first post again, I think the original poster can say his example is correct. I just did not have a clue to where it should go. So I just copied his code at the end of the options file, getting it wrong. I am letting this post remain both as an example of how something can be misunderstood and as a warning to other readers that they really need to know what they are doing... I am wondering what else I missed.

To the OP - maybe it would be a good idea to include the options text in it's entirety so nobody else do what I did?

---

### Post by Maheriano on 2009-02-04
What have I done wrong?

> deemar@Jurassic:/etc/bind$ nslint
nslint: missing "ptr": [www.deemarwebdesign.com](www.deemarwebdesign.com). -> 68.144.96.207
nslint: missing "a": deemarwebdesign.com. -> 68.144.96.207
nslint: missing "ptr": mta.deemarwebdesign.com. -> 68.144.96.207
nslint: missing "ptr": ns1.deemarwebdesign.com. -> 68.144.96.207
nslint: 68.144.96.207 in use by deemarwebdesign.com. and [www.deemarwebdesign.com](www.deemarwebdesign.com).
nslint: 68.144.96.207 in use by mta.deemarwebdesign.com. and deemarwebdesign.com.
nslint: 68.144.96.207 in use by ns1.deemarwebdesign.com. and mta.deemarwebdesign.com.


etc/bind/named.conf
> zone "deemarwebdesign.com" {
        type master;
        file "/etc/bind/zones/deemarwebdesign.com.db";
        };


zone "96.144.68.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.96.144.68.in-addr.arpa";
};


/etc/bind/named.conf.options
> options {
        directory "/var/cache/bind";


         forwarders {
                68.144.96.207;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


/etc/bind/zones/deemarwebdesign.com.db
> deemarwebdesign.com.      IN      SOA     ns1.deemarwebdesign.com. admin.deemar$

                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

deemarwebdesign.com.      IN      NS              ns1.deemarwebdesign.com.
deemarwebdesign.com.      IN      MX     10       mta.deemarwebdesign.com.

www              IN      A       68.144.96.207
mta              IN      A       68.144.96.207
ns1              IN      A       68.144.96.207


/etc/bind/zones/rev.96.144.68.in-addr.arpa
> @ IN SOA ns1.deemarwebdesign.com. admin.deemarwebdesign.com. (
                        2006081401;
                        28800;
                        3600;
                        604800;
                        86400
)

                     IN    NS     ns1.deemarwebdesign.com.
207                    IN    PTR    deemarwebdesign.com.


Then I restarted bind.

/etc/resolv.conf
> search deemarwebdesign.com
nameserver 68.144.96.207


I have no idea what I did wrong.

---

### Post by Maheriano on 2009-02-04
Anyone?

---

### Post by Maheriano on 2009-02-06
I don't know what else I need to do to get help around here, anybody who sets up a webserver on a domain has had to create this before. Is there honesty nobody here to help me? What more do I have to do?

---

### Post by yknivag on 2009-02-06
> **Maheriano said:**
> I don't know what else I need to do to get help around here, anybody who sets up a webserver on a domain has had to create this before. Is there honesty nobody here to help me? What more do I have to do?

You don't need your own DNS server to host a website on your own domain.  All you need to do is point the domain to your static external IP address.  It simply isn't really worth building a DNS server from scratch just to point a single record to yourself.

However, setting up a DNS server is certainly an interesting project, if only in the issues around keeping it secure.

I'm afraid this hasn't really helped your problem in getting it working (I'm no BIND expert) but I'm sure someone will be along who knows more.  Other than that, there are some excellent BIND tutorials out there...

---

### Post by Maheriano on 2009-02-06
> **yknivag said:**
> You don't need your own DNS server to host a website on your own domain.  All you need to do is point the domain to your static external IP address.  It simply isn't really worth building a DNS server from scratch just to point a single record to yourself.

However, setting up a DNS server is certainly an interesting project, if only in the issues around keeping it secure.

I'm afraid this hasn't really helped your problem in getting it working (I'm no BIND expert) but I'm sure someone will be along who knows more.  Other than that, there are some excellent BIND tutorials out there...

For real? I tried entering my IP as the DNS at my registrar but I got an error saying it wasn't a valid format for a DNS entry.

---

### Post by yknivag on 2009-02-06
You don't add your IP as the DNS, you use their DNS but simply create a record to point [www.yourdomain.tld](www.yourdomain.tld) to your IP.

---

### Post by Maheriano on 2009-02-06
> **yknivag said:**
> You don't add your IP as the DNS, you use their DNS but simply create a record to point [www.yourdomain.tld](www.yourdomain.tld) to your IP.

Where do I create this record?

---

### Post by yknivag on 2009-02-06
That will depend on who you registered your domain with.

---

### Post by Maheriano on 2009-02-06
> **yknivag said:**
> That will depend on who you registered your domain with.

[www.hostgo.com](www.hostgo.com)
I think they use a sister service at [www.registergo.com](www.registergo.com) for registrations.

---

### Post by yknivag on 2009-02-07
Ah, they seem only to provide the name itself, most registration companies also do the DNS for you for free.  I'd look to transfer your domain somewhere that offers a better service.

---

### Post by Maheriano on 2009-02-07
Damnit. So I just set up an account with [www.dyndns.com](www.dyndns.com) and can now get to my website via deemar.dyndns.com but I want to get there from the domain I purchased which is deemarwebdesign.com. How do I do that?

---

### Post by yknivag on 2009-02-07
You'll need to find a way of pointing your domain to your dyndns.com entry (assuming your server is on a dynamic IP) or to your IP if you have a static one.

How you do this will depend on your registration company.  Only they can really answer that.

---

### Post by Maheriano on 2009-02-10
Nuts.....I contacted my registrar and they don't do anything with DNS at all. So either I transfer the domain I just paid $15 for or I try and set up bind9 on my machine which is proving impossible with the limited support I'm getting.

---

### Post by alienseer23 on 2009-02-25
i use easydns [http://www.everydns.com/index.php](http://www.everydns.com/index.php) 

it's a free dns service for your domain.

---

### Post by Maheriano on 2009-03-03
> **alienseer23 said:**
> i use easydns [http://www.everydns.com/index.php](http://www.everydns.com/index.php) 

it's a free dns service for your domain.

Cool! So I just set up an A record there and I'm done? I don't see a tutorial on their site anywhere.

---

### Post by QordaZ on 2009-03-16
Very good guide, got me up and running. Thank you

---

### Post by Rufe0 on 2009-03-30
Followed this to the letter, didn't work tried, it other ways still doesn't work, anyway wonder if you lot could sort me out

domain name: choices.hcctraining.uk
forwarder: 91.43.10.50

mailserver: choicesserver@choices 91.43.10.30

severname: choicesproxy
IP: 91.43.20.14

example machine: ccc100 91.40.20.100

---

### Post by Maheriano on 2009-03-30
> **alienseer23 said:**
> i use easydns [http://www.everydns.com/index.php](http://www.everydns.com/index.php) 

it's a free dns service for your domain.

Do this. Worked perfect for me.

---

### Post by Rufe0 on 2009-03-31
Using gbindadmin, seems to be working so far

---

### Post by stevetmlp on 2009-04-03
> **MAO said:**
> Hi i've got some problems with bind Zones Files:

root@sw:/# tail -f /var/log/daemon.log
May 10 20:05:51 sw named[4705]: command channel listening on ::1#953
[COLOR="DarkRed"]May 10 20:05:51 sw named[4705]: could not open entropy source /dev/random: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: using pre-chroot entropy source /dev/random
May 10 20:05:51 sw named[4705]: zone 0.in-addr.arpa/IN: loaded serial 1
May 10 20:05:51 sw named[4705]: zone 127.in-addr.arpa/IN: loaded serial 1
[COLOR="#8b0000"]May 10 20:05:51 sw named[4705]: zone 22.29.217.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.22.29.217.in-addr.arpa failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone 255.in-addr.arpa/IN: loaded serial 1
[COLOR="DarkRed"]May 10 20:05:51 sw named[4705]: zone software.kg/IN: loading from master file /etc/bind/zones/software.kg.db failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone localhost/IN: loaded serial 2
May 10 20:05:51 sw named[4705]: running

____________________________________

root@sw:/# ls -la /var/lib/named/etc/bind/zones
total 16
drwxr-sr-x 2 bind bind 4096 2008-05-10 19:45 .
drwxr-sr-x 3 bind bind 4096 2008-05-10 19:47 ..
-rwxrwxrwx 1 bind bind  260 2008-05-10 19:45 rev.22.29.217.in-addr.arpa
-rwxrwxrwx 1 bind bind  651 2008-05-10 19:54 software.kg.db

Plz Help me !!!

Hi All,

Does anyone know how to resolve the above??? I followed this tutorial "http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind", and it went flawlessly until I ran into the "Loading from master file.....permission denied error"

Thanks

---

### Post by TheFuzz4 on 2009-04-23
I am having some issues getting bind to resolve local hosts.  It will resolve all of the external addresses with no problems.  Thanks in advance for your help with this.

Here is my zone file

/ replace thefuzz4.net with your domain name. do not forget the . after the domain name!                                                                         
// Also, replace ns1 with the name of your DNS server                            
thefuzz4.net.      IN      SOA     ns1.thefuzz4.net. admin.thefuzz4.net. (       
// Do not modify the following lines!                                            
                                                        2009041901               
                                                        28800                    
                                                        3600                     
                                                        604800                   
                                                        38400                    
 )                                                                               

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// thefuzz4.net = domain name
thefuzz4.net.      IN      NS              ns1.thefuzz4.net.
thefuzz4.net.      IN      MX     10       mta.thefuzz4.net.

// Replace the IP address with the right IP addresses.
www              IN      A       208.109.181.20
localhost        IN      A       127.0.0.1
ns1              IN      A       192.168.1.144
thefuzz4-kubuntu-01 IN   A       192.168.1.144
thebeast2linux   IN      A       192.168.1.143
thebeastlaptop   IN      A       192.168.1.140
thebeastjenn     IN      A       192.168.1.146
thebeast         IN      A       192.168.1.141
lexmark          IN      A       192.168.1.250
router           IN      A       192.168.1.129

Here is my named.conf.local file
# This is the zone definition. replace thefuzz4.net with your domain name
zone "thefuzz4.net" IN {
        type master;
        file "/etc/bind/zones/thefuzz4.net.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" IN {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";

and last but not least my named.conf

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

I tried to use the admin tool which is really quite nice and friendly but I could not find any setup guides for this.  When it loads it never actually touches any of the files in /etc/bind/ if anyone can provide some insight on the admin tool as well that would be great.  However at this moment I would just love to have bind resolve my local computers.  Thank you once again for any help you can provide on this.

---

### Post by rey.manic on 2009-04-29
hi, I have follow steep by steep this tutorial, but when try to restart bind9 I get this error:

rndc: connect failed: 127.0.0.1#953: connection refused

and the bind9 don't start just say [fail]

whys is this error ?

---

### Post by ldillon on 2009-05-25
I just wanted to add a quick note that slaves must be set to point to /var/cache/bin in /etc/bind/named.conf.local  or else apparmor will break the updating.

---

### Post by theDaveTheRave on 2009-06-19
Hello all.

I'm hoping that the expertise on this thread will be able to answer my question.

Where I work we use a lot of fixed IP addresses - for local file shares on various pc's etc.

In fact every new team member (with a new pc) has to set their pc to use a fixed IP.

We also get regular visitor, and when they log onto our server sometimes they will "steal" one of the IP's that has been used by a regular team member. When that team member gets back from lunch (or that important meeting ;) ) They can find that our visitor has "stolen" their normal IP address, and they can't get logged on!

Also the fixed IP thing seems to occasionally fail - for no known reason, creating a similar situation to that above.

I have suggested that the IP addressing should somehow be controled by the server, to resolve these issues.

But I would like to say that the server could "give out" IP on a fixed basis, so my terminal (host name "Dartagnon") will always get the same IP when I hook into the local network.

Am I correct that using DHCP / DNS / BIND / LDAP I should be able to set something up that meets these requirements?

Will it also be able to reserve a pool for the "fixed" ip addresses, and a pool for "guests"?

Can anyone give me a idea of where I should look to set this up. I've read a number of tutorials on DHCP / DNS /BIND / LDAP and I get the impression that this solution should be possible, but I have not seen anything specific for fixing host names to IP's (or alternatively MAC addresses - if that is easier).

Also I know that looking at my various wireless routers at home I can use MAC address filtering, and fix an IP from the router. So I guess I can do something similar with a DHCP server?

I'm quite happy to play around with setting this up at home in the first instance, but I would like to know that the support for this set up is available before I make a mess of everything:D

Thanks in advance

David

_______ edit 1 ________

Ok I've found this [page]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server") whic certainly seems to suggest I can set the IP relating to the host name, and MAC address.

but how can I add in a "check" to ensure that if the host name isn't in the dhcpd.conf file it gets a specified IP address??

I guess it should be a simple bit of shell loop programming, but I'm not sure I know how to do this.... although as I say I'm happy to try!

______ edit 2 ________

I've just had an even better thought / question.

If I use LDAP / DNS / DHCP does the server automatically store the host names of the computers?

If so I guess it stores the hostname and IP address in a table  / file somewhere. I get the impression this is partly the purpose of LDAP - or am I not understanding it properly?

If it doesn't can I configure it to do so??

david

---

### Post by Lukas1 on 2009-06-26
Hi all,

I am trying to configure a dns/webserver (still he he) anyways I got my router problem worked out and started trying to get the DNS configured. I registered a domain (globalcapeesh.com) and gave my information. My whois all looks right. I am having trouble setting the alias in my dns. In otherwords, you can visit my skelatal website by visiting ns1.globalcapeesh.com but not by visiting [www.globalcapeesh.com](www.globalcapeesh.com). I was wondering if anyone has any experience with this type of problem. Thank you.

Here is my zones file:

; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for globalcapeesh.com
; Note: The extra "." at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
globalcapeesh.com. IN SOA ns1.globalcapeesh.com. hostmaster.globalcapeesh.com. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that ns1 is the name server on globalcapeesh.com
; MX indicates that ns1 is (also) the mail server on globalcapeesh.com
globalcapeesh.com. IN NS ns1.globalcapeesh.com.
globalcapeesh.com. IN NS ns2.globalcapeesh.com.
globalcapeesh.com. IN MX 10 ns1.globalcapeesh.com.
; Set an alias (canonical name) for ns1
www IN CNAME ns1
; Set the address for localhost.globalcapeesh.com
localhost    IN A 127.0.0.1
; Set the hostnames in alphabetical order
ns1          IN A 10.0.1.2
ns2          IN A 10.0.1.3

---

### Post by xiaomahe on 2009-06-30
hi, i already followed all your steps, but the dig result not showing example.com point to my ip.

ming@ming-laptop:~$ dig example.com

; <<>> DiG 9.5.0-P2 <<>> example.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56470
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		78269	IN	A	208.77.188.166

;; Query time: 13 msec
;; SERVER: 10.0.0.1#53(10.0.0.1)
;; WHEN: Tue Jun 30 19:08:54 2009
;; MSG SIZE  rcvd: 45


or is this correct already?

---

### Post by Lukas1 on 2009-07-02
xaiomahe,

I don't see the authority section in your output. Check to make sure that the zones are properly set up; you need have the start of authority (SOA) to connect them up right.

---

### Post by atag on 2009-07-13
> **mekas2024 said:**
> ; <<>> DiG 9.3.2 <<>> mekas.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 9469

status: SERVFAIL says you have errors, check the syslog for details.
I recommend to remove all comments (// lines) from the zone files

---

### Post by meeces2911 on 2009-07-13
Hey, thanks for the tuts man, its working great... well kind of.

The DNS its self IS working... but i want something like this to work, [http://intranet/](http://intranet/)   ... ranther than [http://xxx.intranet/](http://xxx.intranet/) .

I have tried changing example.com to intranet, but that doesnt quite work. I now have to do this: [http://intranet./](http://intranet./) for the PC to register [http://intranet/](http://intranet/) as a valid DNS destination.

Anyone got this to work with a single domain entry ?

**EDIT:**

Huh, its amazing what a night can do. I guess the dns timed out, and required an update, because i tried my intranet url again this morning, and it now works! Thanks again for the tuts guys :D

**EDIT:**

Maybe not... spoke too soon...
doesn't seem to like single domains, without extentions. :(

---

### Post by GodOnline on 2009-09-19
This tutorial definitely helped me a lot.. Thanks a lot all of you :)

---

### Post by JKyleOKC on 2009-09-27
> **rey.manic said:**
> hi, I have follow steep by steep this tutorial, but when try to restart bind9 I get this error:

rndc: connect failed: 127.0.0.1#953: connection refused

and the bind9 don't start just say [fail]

whys is this error ?
I had the same error, as did several other folk earlier in this thread, but nobody ever seemed to answer. I did some digging through MAN pages and discovered that BIND9 needs an additional configuration file, rndc.conf, in the same directory as named.conf. This file seems to be part of the security features, but it's not created by the setup process. You apparently have to do it by hand, although there's a program called rndcconf located in /sbin that will create a key and show you a sample.

EDIT: I created the two rndc.* files required, made the modification to /etc/bind/named.conf.local as indicated by the sample rndc.conf file, and now have a new error:
```
jim@Mehitabel:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                         [OK]
rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
                                                                         [fail]
 * Starting domain name service... bind                                  [ OK ] 
jim@Mehitabel:~$ 
```
Here's what /var/log/daemon.log shows:
```

Sep 27 10:06:09 Mehitabel named[6024]: invalid command from 127.0.0.1#47130: bad auth

```So the questions now are why did the connection close, and what does "bad auth" mean???:confused:

---

### Post by yknivag on 2009-09-27
> **JKyleOKC said:**
> 
```
jim@Mehitabel:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                         [OK]
rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
[COLOR="Red"]* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.[/COLOR]
                                                                         [fail]
 * Starting domain name service... bind                                  [ OK ] 
jim@Mehitabel:~$ 
```
Here's what /var/log/daemon.log shows:
```

Sep 27 10:06:09 Mehitabel named[6024]: invalid command from 127.0.0.1#47130: [COLOR="Red"]bad auth[/COLOR]

```So the questions now are why did the connection close, and what does "bad auth" mean???:confused:

"bad auth" simply means the authentication has failed.

The key lines are in red above.  Either the clocks are out of synch (the server and terminal must be within 5 minutes for bind to start).  Or your rndc keys are invalid or incorrectly generated/installed.

The output suggests your restarting this on the local host so the timing shouldn't be an issue.  Maybe you could try regenerating the keys.

---

### Post by sheldonnbbaker on 2009-10-13
Thanks for the tutorial, I'm hoping I can get everything working with just a few questions:

I have a web server set up at home with a dynamic IP address from my ISP, and two domain names registered (domain1.name and domain2.ca). I also have a dynamic DNS service with DynDNS (subdomain.dyndns.org).

What I'd like to do is have my DNS server living at domain1.name, which then has zones for my web server, domain2.ca.

The configuration and such for BIND seems to involve only one domain - which one do I use? And then how do I set up ns1.domain1.name, ns2.domain1.name? I'm assuming I just forward port 53 to the Ubuntu machine?

Thanks for your help :)

---

### Post by Oceanwatcher on 2009-10-25
I have set up a small caching DNS at home and made a 3 part blog post about it, both to document it for my own sake, and to be a help for others that might need it.

The thread here has been part of my source for what I have learnt during the process and I added a link back here at the end of the series.

Check it out: [http://www.wisnaes.com/2009/10/25/setting-up-your-own-dns-part-1-getting-started/](http://www.wisnaes.com/2009/10/25/setting-up-your-own-dns-part-1-getting-started/)

---

### Post by yknivag on 2009-10-25
Thanks, Oceanwatcher. Superb blog! I shall bookmark it for when I get my server fully up and running.

---

### Post by Oceanwatcher on 2009-10-25
Thanks for the kind words :-) I hope it will be useful.

---

### Post by NagWolf on 2009-11-03
Hi Ppl;
I followed the instructions to the letter, replacing for instance ns1.example.com with vaalgate.nagwolf.net (vaalgate is the Ubuntu server's name), etc. but not working...

Error I receive when restarting Bind9 is 
rndc: connect failed: 127.0.0.1#953: connection refused

any Ideas please how to address this, and then I was just wondering, purpose of this will be for friends to connect to a VPN server with IP 10.10.10.12/29
The DNS server's IP is 10.10.10.10/29
I've set the IP's allowed to connect to this VPN server to 192.168.10.x and my friends' WAN routers are of IP range 172.17.3.x, although they have Lan IP's behind the router of 192.168.10.x

I hope someone can make sense of this, and tell me if I'm introducing too many IP ranges, which might be the problem as well.

Thank you and I shall now go and start praying that someone can help me make sense

N8

---

### Post by im_an_elf on 2009-11-10
I'm getting the same error.

```
/etc/bind/zones/rev.1.168.192.in-addr.arpa:1: unknown RR type 'example.com'
Nov 10 12:47:22 loadbox2 named[32445]: zone 1.168.192.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.1.168.192.in-addr.arpa failed: unknown class/type
Nov 10 12:47:22 loadbox2 named[32445]: zone 255.in-addr.arpa/IN: loaded serial 1
Nov 10 12:47:22 loadbox2 named[32445]: /etc/bind/zones/*****.com.db:1: unknown RR type 'replace'
Nov 10 12:47:22 hashbox2 named[32445]: zone *****.com/IN: loading from master file /etc/bind/zones/*****.com.db failed: unknown class/type

```

This is a clip from my syslog.

I removed all comments from the files that contain comments with the double slashes.  The server behaved properly and return the 127.0.0.1 localhost

---

### Post by spikoley on 2009-12-13
> **NagWolf said:**
> Hi Ppl;
I followed the instructions to the letter, replacing for instance ns1.example.com with vaalgate.nagwolf.net (vaalgate is the Ubuntu server's name), etc. but not working...

Error I receive when restarting Bind9 is 
rndc: connect failed: 127.0.0.1#953: connection refused

any Ideas please how to address this, and then I was just wondering, purpose of this will be for friends to connect to a VPN server with IP 10.10.10.12/29
The DNS server's IP is 10.10.10.10/29
I've set the IP's allowed to connect to this VPN server to 192.168.10.x and my friends' WAN routers are of IP range 172.17.3.x, although they have Lan IP's behind the router of 192.168.10.x

I hope someone can make sense of this, and tell me if I'm introducing too many IP ranges, which might be the problem as well.

Thank you and I shall now go and start praying that someone can help me make sense

N8

I had that same error with Jaunty.  When I installed it on Karmic it worked.  I think there is a bug in Jaunty and  I recommend running Karmic instead.

---

### Post by virresss on 2009-12-16
hey im a big noob but learning. so far ive configured ubuntu server with  no-ip free domain and i got it to work with apache2 and vhost. my idea was to host 2 online sites and one over only LAN.

before i fixed with vhost i had the lan server  and after vhost i lost the lan. then i read some where that i had to install BIND and make it host the lan dsn for me. but when i read the instructions here but im lost. i dont know if its my dyslexia thats kicking in or that im tired now  mabe both. but if some one can help me? or is there an easy way to do this?  

as i said i want 2 online sites and one lan server only and if possible named "media":)(i got vhost on the 2 online sites working for me)

---

### Post by dtcostelloe on 2010-01-21
Would anyone mind looking over my files here and tell me if you guys see anything obviously wrong here?  I've been working on this for several hours now - following both tutorials to the letter.  I keep getting a SERVFAIL message when I do a "dig" command from the local host machine (the one to be a server).

I am running Ubuntu Server Edition v.9.10 (Karmic, I believe.)
In addition to BIND9, I have XAMPP (LAMPP), SAMBA, and OpenSSH.  All are working fine.  I can ping the server locally and on my LAN without problems using the server IP address.  Windows computers can see the SAMBA stuff without any problems.  I can SSH using PuTTY - as long as I call the server by IP address, rather than host name.  Basically, the server is happily "seeing" the network and Internet, and talking amongst its neighbors - but not by DNS host name.

I've included all my file contents here, and the exact results of a "dig" command launched from the server, and an "ifconfig".

I know this is lengthy, but would you guys mind looking over my stuff and see if there is something that I am just not seeing - give me a "fresh" pair of eyes, so to speak?

My "/etc/resolv.conf":
```

search costelloe.net
nameserver 10.0.0.10

```

My "/etc/hosts" file:
```

127.0.0.1       localhost
10.0.0.10       svr.costelloe.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My "/etc/bind/named.conf" file (still at default settings):
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```

"/etc/bind/named.conf.options" file:
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                64.102.255.44;
                   };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

My "/etc/bind/named.conf.local" file:
```

zone "costelloe.net" {
        type master;
        file "/etc/bind/zones/svr.costelloe.net.db";
        };

zone "0.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.0.10.in-addr.arpa";
        };

```

My "/etc/bind/zones/svr.costelloe.net.db" file:
```

$TTL 1h
svr.costelloe.net.     IN   SOA   svr.costelloe.net. (
        2010012101
        28800
        3600
        604800
        38400
)

svr.costelloe.net.     IN   NS   svr.costelloe.net.

localhost       IN     A         10.0.0.10

svr             IN     A         10.0.0.10

```

My "/etc/bind/zones/rev.0.0.10.in-addr.arpa" file:
```

$TTL 1h
@ IN SOA svr.costelloe.net. (
        2010012101;
        28800;
        604800;
        604800;
        86400
)
        IN      NS      svr.costelloe.net.
10      IN      PTR     svr.costelloe.net.

```

Results of "dig costelloe.net":
```

; <<>> DiG 9.6.1-P2 <<>> costelloe.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 60584
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;costelloe.net.                 IN      A

;; Query time: 0 msec
;; SERVER: 10.0.0.10#53(10.0.0.10)
;; WHEN: Thu Jan 21 01:16:18 2010
;; MSG SIZE  rcvd: 31

```

Results of "dig svr.costelloe.net"
```

; <<>> DiG 9.6.1-P2 <<>> svr.costelloe.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 41969
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;svr.costelloe.net.             IN      A

;; Query time: 0 msec
;; SERVER: 10.0.0.10#53(10.0.0.10)
;; WHEN: Thu Jan 21 01:17:12 2010
;; MSG SIZE  rcvd: 35

```

Results of "ifconfig":
```

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:2b:02:57
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe2b:257/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2193447 (2.1 MB)  TX bytes:2411251 (2.4 MB)
          Interrupt:22 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:68612 (68.6 KB)  TX bytes:68612 (68.6 KB)

```

I really appreciate anyone taking the time to check my stuff here, it's probably something really simple - but for the life of me, I haven't a clue.  I've reconstructed these files completely from scratch (except the default files) about 4 times now, and the errors persist.  Any suggestions, ideas, thoughts?

---

### Post by margemoosh on 2010-05-23
I have a  few questions about bind.
for example ip address for aaa.com is 111.111.111.111 and i want to configure bind in my laptop so when i ping aaa.com or dig aaa.com instead of 111.111.111.111 it gives me 222.222.222.222(222.222.222.222 is not the ip address for aaa.com).
i couldn't do that with bind. request for ip address of aaa.com reaches my laptop bind instead of real dns server but it doesn't return anything!
can anyone help me to do that?

---

### Post by kiwi_nigel on 2010-06-11
Thank You!

I found your post really useful :p

I had been going nuts for a day trying to get my home network to use our Linux server as a DNS cache...the Linux machines were happy! getting the WinXP machine to play nicely was another story!

I also found this article useful (for anyone else who is looking for additional examples) 
[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/)

Cheers

---

### Post by AnRkey on 2010-08-30
> **hogman23 said:**
> One more step to get it to work:
You must rename the named.conf.local to named.conf

Not so, these are two different files and they both exist for a reason.

There are three named.conf files in /etc/

named.conf
named.conf.local
named.conf.options

They are all used, it's just defferent parts of the config that is stored in each.

R 8)

---

### Post by dionp2 on 2010-09-14
Could somebody please help me?

I'm not sure how to trouble shoot this.

I setup bind9 with webmin but gave up on that and tried to edit the files manually.

Now from a root logon on the ubuntu 9.10 server I get

---------------------------------------------
root@ice:/etc/bind/zones# nslookup ice.7rocks.com.
Server:		127.0.0.1
Address:	127.0.0.1#53

** server can't find ice.7rocks.com: SERVFAIL
---------------------------------------------

Checked if bind is up and running
---------------------------------------------
root@ice:/etc/bind/zones# ps -ef|grep [n]amed
bind      4259     1  0 11:04 ?        00:00:00 /usr/sbin/named -u bind
---------------------------------------------

Doing the dig thing I get
---------------------------------------------
root@ice:/etc/bind/zones# dig ice.7rocks.com.

; <<>> DiG 9.6.1-P2 <<>> ice.7rocks.com.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 58059
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ice.7rocks.com.			IN	A

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Sep 15 11:18:24 2010
;; MSG SIZE  rcvd: 32
---------------------------------------------


Contents of /etc/resolve.conf are :
---------------------------------------------
# Generated by NetworkManager
nameserver 127.0.0.1
---------------------------------------------

The contents of 7rocks.com.db
---------------------------------------------
// replace example.com with your domain name. do not forget the . after the dom$
// Also, replace ns1 with the name of your DNS server

7rocks.com.     IN      SOA     ice.7rocks.com. dion.7rocks.com. (
10118 ; Serial
43200 ; Refresh
3600 ; Retry
3600000 ; Expire
2592000 ) ; Minimum

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
7rocks.com.                 IN      NS              ice.7rocks.com.
7rocks.com.                 IN      MX     10       mail.7rocks.com.

// Replace the IP address with the right IP addresses.
7rocks.com.      IN      A       192.168.1.3
ice.7rocks.com.  IN      A       192.168.1.3
[www.7rocks.com](www.7rocks.com). IN      A       192.168.1.3
mail             IN      A       82.98.86.173
ice              IN      A       192.168.1.3

// Aliases
ice              IN      CNAME   ice.7rocks.com.


---------------------------------------------


The contents of rev.1.168.192.in-addr.arpa
---------------------------------------------
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS serve$

@       IN      SOA     ice.7rocks.com. dion.7rocks.com. (
                        2006081402
                        28800
                        604800
                        604800
                        86400 )

        IN      NS      ice.7rocks.com.
3.1.168.192.in-addr.arpa.       IN      PTR     ice.7rocks.com.

---------------------------------------------


Contents of /etc/bind/named.conf
---------------------------------------------
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "7rocks.com" {
        type master;
        file "/etc/bind/zones/7rocks.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your netw$
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

---------------------------------------------

This DNS servers IP address is 192.168.198.3 sitting on an internal network behind an
ADSL modem.
The ADSL modem has an IP address of 192.168.1.1

Anybody got any ideas?

Regards,

D

---

### Post by mikisr on 2010-09-29
after  # dig mysite.com
I get this:
; <> DiG 9.4.2-P2.1 <> mysite.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36531
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
 ;; QUESTION SECTION:
;mysite.com.                   IN      A
 ;; ANSWER SECTION:
mysite.com.            0       IN      A       xx.xxx.xx.xxx
 ;; Query time: 214 msec
;; SERVER: 208.67.220.220#53(208.67.220.220)
;; WHEN: Wed Sep 29 12:58:08 2010
;; MSG SIZE  rcvd: 45


 and after # ping mysite.com
 I get this:
PING mysite.com (ip of my VPS) 56(84) bytes of data.
64 bytes from mysite.com (ip of my VPS): icmp_seq=1 ttl=64 time=0.045 ms


 Those results are shown if I dig and ping from root of my VPS, but  when I ping mysite.com from other machine (any where from internet) I  get "unknown host mysite.com" how can I be shure that my zone files are  correct??? there is about 24h of propagation (if that may be a problem)  but I can't find mysite.com in any table (I was trying with diferent  proxies and diferent tools).

---

### Post by mikisr on 2010-09-29
.

---

### Post by anypundit on 2010-11-03
Deleted

---

### Post by sash11 on 2010-11-21
I have set up bind with hardly any problems. However there is yet one thing that troubles me. I connect to my ISP through aDSL modem. Each time a connection is made resolv.conf file gets modified with providers DNS servers. I have to manually remove the IPs and add my local DNS IP and search order string. Is there a way to fix this?

---

### Post by SeijiSensei on 2010-11-21
> **anypundit said:**
> What, if any, changes should I make to the standard db.anypundit.com to leave the 2LD alone while issuing 3LD names to my network hosts? 

The easiest solution is to replicate the external records for [www.anypundit.com](www.anypundit.com) in your local zone file.  I do this all the time when setting up internal nameservers for clients.  Usually the www host record, and sometimes a "mail" record point to the external server(s) with everything else pointing inside.

> **sash11 said:**
> I have to manually remove the IPs and add my local DNS IP and search order string. Is there a way to fix this?

Edit (with sudo) /etc/dhcp3/dhclient.conf and remove "domain-name-servers" and "domain-search" from the list in the "request" directive.  You can also muck with "prepend" and "supersede" if you like, or you can just create a static resolv.conf and disable the request for domain-name-servers and search list.

---

### Post by anypundit on 2010-11-22
If you have trouble with zone file syntax like I did, try a little script called "hosts2dns".  It will read your HOSTS file and translate those entries into the proper zone files.  Beware and backup, as it will overwrite existing DNS entries.

---

### Post by rededit on 2011-01-07
I have set up my dns server just like the original tutorial in this topic said to do. However, I can not browse to my local webserver using xserv.local or [www.xserv.local]("http://www.xserv.local"). 

So I ran a test:

C:\Users\dx>nslookup xcserv.local
Server:  UnKnown
Address:  192.168.2.20

*** UnKnown can't find xserv.local: Non-existent domain

--------------------------------------------------------------------

ja@serv:~$ dig tgcserv.local

; <<>> DiG 9.7.0-P1 <<>> xserv.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 53932
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;xserv.local.                 IN      A

;; AUTHORITY SECTION:
.                       3436    IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2011010700 1800 900 604800 86400

;; Query time: 46 msec
;; SERVER: 192.168.2.20#53(192.168.2.20)
;; WHEN: Fri Jan  7 16:00:42 2011
;; MSG SIZE  rcvd: 106

-----------------------------------------------------

ja@serv:~$ nslookup ns
Server:         192.168.2.20
Address:        192.168.2.20#53

** server can't find ns: NXDOMAIN


Any help on what file I mis-configured  or what I need to do differently is greatly appreciated.

---

### Post by rededit on 2011-01-10
I fixed my problem. I have my domain running I think. The problem is I cannot browse to the my internal site via the new domain name. 

Here are the results of the tests:

```

ja@x:/etc/apache2$ ping x.local
PING x.local (127.0.1.1) 56(84) bytes of data.
64 bytes from x.local (127.0.1.1): icmp_seq=1 ttl=64 time=0.014 ms
64 bytes from x.local (127.0.1.1): icmp_seq=2 ttl=64 time=0.012 ms
64 bytes from x.local (127.0.1.1): icmp_seq=3 ttl=64 time=0.012 ms
64 bytes from x.local (127.0.1.1): icmp_seq=4 ttl=64 time=0.013 ms
^C
--- x.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.012/0.012/0.014/0.004 ms
ja@x:/etc/apache2$ dig x.local

; <<>> DiG 9.7.0-P1 <<>> x.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64267
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;x.local.                     IN      A

;; AUTHORITY SECTION:
x.local.              38400   IN      SOA     ns1.x.local. admin.x.local. 2010011001 28800 3600 604800 38400

ja@xserv:/etc/apache2$ dig -x 127.0.0.1

; <<>> DiG 9.7.0-P1 <<>> -x 127.0.0.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64924
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; QUESTION SECTION:
;1.0.0.127.in-addr.arpa.                IN      PTR

;; ANSWER SECTION:
1.0.0.127.in-addr.arpa. 604800  IN      PTR     localhost.

;; AUTHORITY SECTION:
127.in-addr.arpa.       604800  IN      NS      localhost.

;; ADDITIONAL SECTION:
localhost.              604800  IN      A       127.0.0.1
localhost.              604800  IN      AAAA    ::1

;; Query time: 0 msec
;; SERVER: 192.168.2.20#53(192.168.2.20)
;; WHEN: Mon Jan 10 20:43:47 2011
;; MSG SIZE  rcvd: 121

ja@xserv:/etc/bind$ named-checkzone x.local /etc/bind/zones/x.local.db
/etc/bind/zones/x.local.db:1: no TTL specified; using SOA MINTTL instead
zone x.local/IN: loaded serial 2010011001
OK


```It seems as though I have everything configured correctly, yet I still cannot browse to the site I have hosted off of the nameserver 192.168.2.20. The router ip is 192.168.2.1.

Here are my files:

named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "x.local" {
        type master;
        file "/etc/bind/zones/x.local.db";
        };


zone "2.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.2.168.192.in-addr.arpa";

```named.conf.options
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

           forwarders {
                192.168.2.1;
           };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```x.local.db
```
x.local.      IN      SOA     ns1.x.local. admin.x.local. (

                                                        2010011001
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 );





x.local.        IN      NS      ns1.x.local.
www              IN      A       192.168.2.20
ns1                IN      A       192.168.2.20
*                   IN      A       192.168.2.20

```rev.2.168.192.in-addr.arpa
```

@ IN SOA ns1.x.local. admin.x.local. (
                        2010011001;
                        28800;
                        604800;
                        604800;
                        86400
)

                      IN    NS     ns1.x.local.
20                    IN    PTR    x.local

```resolv.conf
```

search x.local
nameserver 192.168.2.20

```Any help would be greatly appreciated. I can't seem to figure out what I am doing wrong.

Edit: I can browse to the site by putting in the ip address of the nameserver/webhost into my browser.

---

### Post by mwb173 on 2011-03-28
[SIZE=3]when i try to start bind it says bind9  rmdc:connect failed :127.0.0.1#953: connection refused

where do i start looking to trouble shoot this?  any help is much appreciated 

thanks![/SIZE]

---

### Post by Grakul on 2011-04-30
Hi,

Sorry to be resurrecting a dead thread here, but I cannot get it to work. I cannot resolve my own machine's hostname!

Here are my files:

> **named.conf.local]
zone "communicate.local" {
        type master said:**
> 

[QUOTE=named.conf.options]
options {
	directory "/var/cache/bind";
	forwarders {
	 	192.168.0.1;
	};
	auth-nxdomain no;
	listen-on-v6 { any; };
};


> **communicate.local.db]
communicate.local. IN SOA zeus.communicate.local. admin.communicate.local. (
2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
)
communicate.local. IN NS zeus.communicate.local.
* IN A 192.168.0.2
zeus IN A 192.168.0.2
[/QUOTE]

[QUOTE=rev.0.168.192.in-addr.arpa]
@ IN SOA zeus.communicate.local. admin.communicate.local. (
                        2006081401 said:**
> 

[QUOTE=resolv.conf]
nameserver 192.168.0.2
domain communicate.local
search communicate.local


bind9 starts fine, but when I try nslookup zeus 192.168.0.2, I get:

> 
Server:		192.168.0.2
Address:	192.168.0.2#53

** server can't find zeus: NXDOMAIN


If anybody knows what could be causing my problem, I would appreciate it if you could let me know. By the way, this happens whether I run the nslookup from the zeus itself (the DNS server) or another machine on the network.

Thanks in advance for your help,
Grakul

---

### Post by Grakul on 2011-05-02
Nevermind. I fixed it. I ran the following command: 

```
named-checkzone example.com /etc/bind/db.example.com
```

It basically gave errors on each of the comment lines. I removed all the comments, after which the above line reported "OK."

I restarted bind and was able to resolve zeus and ping communicate.local.

Now to find out how to get my DHCP server to automatically update DNS for the clients.... ;)

Cheers
Grakul

---

### Post by netwokernewbie on 2011-09-18
nice tutorial ! a want to try this ! 
thank's

---

### Post by Delfines on 2011-09-26
so good~;)

---

### Post by rituranjan on 2012-03-06
how to an other domain created with this domain

---

### Post by TeamXlink on 2012-06-13
How would I go about setting up a CNAME record.

Directing users of the DNS Server from:

[www.example.com](www.example.com) to [www.other.com](www.other.com)

I cannot use an A record because the ip address that [www.other.com](www.other.com) is dynamic and not static.


*Note - [www.example.com](www.example.com) and [www.other.com](www.other.com) are just examples.

Thank you.

---

### Post by Yizi on 2013-02-04
Very good tutorials, still having issues, I'm using a live example here and just can't get it to work, here's my configuration so far:

I'm going to use mydomain.com as my domain name here

**named.conf.local**

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mydomain.com" {
	type master;
	file "/etc/bind/db.mydomain.com";
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "201.168.192.in-addr.arpa" {
    	type master;
     	file "/etc/bind/rev.201.168.192.in-addr.arpa";
};

```

**db.mydomain.com**

```
;
; BIND data file for mydomain.com
;
$TTL	604800
mydomain.com.	IN	SOA	ns1.mydomain.com. admin.mydomain.com. (
	84739	; Serial
	604800	; Refresh
	86400	; Retry
	2419200	; Expire
	604800 ); Negative Cache TTL
;
mydomain.com.			IN	NS	ns1.mydomain.com.
mydomain.com.	86400	IN	NS	ns2.mydomain.com.
localhost		14400	IN	A	127.0.0.1
ns1				14400	IN	A	<external server IP>
ns2				14400	IN	A	<external server IP>
@	IN	A	127.0.0.1
@	IN	AAAA	::1

```

Any help would be appreciated.

---

### Post by subco on 2013-09-12
That does not works for me. The file 'example.com.db' contains:
```

example.com.      IN      SOA     ns1.example.com. admin.example.com. (
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )


example.com. IN NS ns1.example.com.
example.com. IN MX 10 mail.example.com.


www     IN      A       ***.***.***.***
mail    IN      A       ***.***.***.***
ns1     IN      A       ***.***.***.***



```

and here is result of *named-checkzone*:
```

# named-checkzone example.com example.com.db
example.com.db:1: no TTL specified; using SOA MINTTL instead
zone example.com/IN: loaded serial 2006081401
OK

```

But dig resolve successfully! What is wrong?

---

### Post by sam_jefferson on 2014-05-15
> **subscr said:**
> When I try and install bnd9, here is what I get..Any ideas ?

 sudo apt-get install bind9
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bind9: Depends: libdns21 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisccfg1 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisc11 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed
         Depends: libisccc0 (= 1:9.3.2-2ubuntu1) but 1:9.3.2-2ubuntu1.1 is to be installed

just simply 
remove all the libraries defined above by the apt-get remove command for example 
apt-get remove libisccfg1 
then simply install the bind9 by the apt-get install bind9 command ;)

---

### Post by Iterhit on 2014-12-07
hello all!
please, help me understand
```

*// replace example.com with your domain name. do not forget the . after the domain name!*
*// Also, replace ns1 with the name of your DNS server*
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
*// Do not modify the following lines!*
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

[I]// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name[/I]
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mta.example.com.

*// Replace the IP address with the right IP addresses.*
www              IN      A       192.168.0.2
mta              IN      A       192.168.0.3
ns1              IN      A       192.168.0.1

```

What is ns1 nameserver?
for what i need other nameserver? if i install bind?

---

### Post by jovemmusico on 2015-07-13
How to make this work with multiple VirtualHost to same ip : port?

```
<VirtualHost *:80>...</VirtualHost>
<VirtualHost *:80>...</VirtualHost>
...
```

---

