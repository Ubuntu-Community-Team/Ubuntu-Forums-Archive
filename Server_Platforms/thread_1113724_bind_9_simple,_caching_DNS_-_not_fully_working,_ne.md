---
title: "bind 9 simple, caching DNS - not fully working, need expert help"
date: 2009-04-01
forum: Server Platforms
---

### Post by Oceanwatcher on 2009-04-01
I have spent countless hours searching, reading, communicating about bind9 and DNS'es.

At home, I have a pc set up with Ubuntu server 8.10, no GUI. It is running Apache, php, MySQL, Samba, Cups and bind9 to mention a few things. It is just for development and it does not get a lot of traffic as there is no connections to it from the internet.

I want it to have a bind9 based caching DNS that works as the main DNS for us here at home, and forward all requests it can not resolve itself to OpenDNS.

On the domain side of things, I have a domain called wisnaes.com and as far as I understand, it should be possible to use lan1.wisnaes.com as the domain for our local network at home without making any mess.

Do anyone know of a DNS file generator on the internet? As most of the job setting up the various files is formatting, it should be possible to make a website that take a list of information and output the various textfiles that is needed, ready to be copied.

Here is my info. I have generalized the IP addresses a little so they will be useful for others.

Server name: zebra
Server IP: 192.168.0.10
Gateway: 192.168.0.1
External DNS 1: 208.67.222.222
External DNS 2: 208.67.220.220
Local domain: lan1.mydomain.com

I want the server to come up if I type [www.lan1.mydomain.com](www.lan1.mydomain.com) in the browser as well as if I type [http://zebra](http://zebra)

What is the list of files that need to be edited?

Another thing - before I installed bind9, the server already had a name and an IP address and some other network specific information. Should any of these files be edited/checked in case they interfere with the bind9 setup? If so, what files?

As it is today, the server works half way as a DNS. I can enter the IP adress of the server as the only DNS for a Windows computer and it will get online.

BUT - if I try to enter [www.lan1.mydomain.com](www.lan1.mydomain.com) I get a "Page not found" message. And if I try to enter [http://zebra](http://zebra) it will go to the internet and search for a site there instead of giving me apache on my server.

If I use the IP address of the server, I do get the webpages. But in order to do the development I want to do, I need this DNS to work perfect.

I can not understand why this has to be so difficult. And I wish there was a tool available that made it much easier...

If you give me the list of files that is needed, I can post the files i have now and you can tell me what I am doing wrong.

---

### Post by tensai_999 on 2009-04-02
Can you give some info regarding your network setup?
Like are you using a router or software based kind of gateway (a pc running a gateway services)? Is the port forwarding has been enabled?
Is your external DNS a free services or did you pay for its services?

---

### Post by primaxx on 2009-04-02
Hello, 

I am absolutely not an expert on Bind, in fact I find it the most difficult of all to configure, but I am (pretty) sure about this:

You need to add a line in your server's /etc/hosts that looks like this:```

192.168.0.10	test.no
```where the ip-address is your server's internal ip-address.

Then it's the zone-files...
Here's Ubuntu's Bind-howto by the way: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Here is my example of a bind-file /etc/bind/db.test.no:```
;
; BIND data file for test.no
;
$TTL    604800
@       IN      SOA     mail.test.no. webmaster.test.no. (
                         2009032502         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      mail
        IN      MX      10 mail
        IN      A       192.168.0.10
mail    IN      A       192.168.0.10
```
The challenge for you is that my bind-file only is about mail, so you must add some information to it, whithout me knowing what.

The configuration given over makes 192.168.0.10 believe test.no is on 192.168.0.10. 
What I am *not* sure of is if this also will trick the rest of your computers...

My /etc/resolv.conf on the server looks like this, but this one I am not sure will work for you!:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

My /etc/nsswitch.conf```
# /etc/nsswitch.conf
passwd:         compat
group:          compat
shadow:         compat

hosts:	files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```:

My /etc/hosts.conf:```
order hosts,bind
multi on
```

Another thing to remember is that you must always change the line in the db.test.no to a higher number after every change you make. If not the Bind-server will not recognize your changes when you restart it.

I don't think this solves your problem, but maybe it helps you just a little bit?
(For all I know, my response to you gives you more trouble rather than less, in that case, please forgive me!)

Good luck! :-)

---

### Post by Oceanwatcher on 2009-04-02
I thought I just gave some information about my network. :-) Of course, I might have forgotten something, so if you see anything particular missing, feel free to let me know.

Oh - I know one thing I forgot. Netmask is 255.255.255.0

If you do not know what OpenDNS is, check out [www.opendns.com](www.opendns.com) . Nothing fancy, nothing you have to pay for. Just a free and open dns.

Why would I need port forwarding??? I think I mentioned that there is no contact from internet to the server. And there will not be any. It is local.

The DNS will serve the few PC's we have in our house, cache the results and in the case it do not have the answers, it will ask the OpenDNS servers.

DHCP is taken care of and will not be done by the Ubuntu server.

It is supposed to be a very simple setup, but somehow I have not got it completely right.

I think a very good starting point is to list all files that need to be edited. That limits the task.

---

### Post by Oceanwatcher on 2009-04-02
primaxx - Absolutely helpful. There were a couple of files on that list I had not remebered to check.

And I had no idea about the number. I guess you are talking about the serial number?

---

### Post by primaxx on 2009-04-02
> **Oceanwatcher said:**
> primaxx - Absolutely helpful. There were a couple of files on that list I had not remebered to check.

And I had no idea about the number. I guess you are talking about the serial number?
I was in a hurry for work, so I forgot a few words there... Yes, I ment the serial-number. :-)

---

### Post by primaxx on 2009-04-02
Oceanwatcher,

as I assume you are Norwegian, you should also try the forum at linux1.no. The response may not be as fast as here, but some of the people there really know what they are talking about! :-)

---

