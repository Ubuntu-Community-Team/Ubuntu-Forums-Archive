---
title: "Two websites(servers) from one IP address?"
date: 2011-01-30
forum: Server Platforms
---

### Post by Nova 107 on 2011-01-30
hey guys. Is it possible to run two servers through one ip address? And I don't mean through apache to run virtual servers. Right now my set up is: Cable modem>router>server.

---

### Post by ryannathans on 2011-01-30
Yes, it is perfectly possible.

config files tell apache what files to 'serve' the visiter. I believe they are stored in /etc/apache2/ and folders inside there depending on how you have it set up. 

EG: my server is on 192.168.1.4

i have two sites, 

/var/www/timsworkshop/
/var/www/bobsfuntime/

apache config files would be set up properly to serve [http://192.168.1.4/timsworkshop](http://192.168.1.4/timsworkshop) the files from /var/www/timsworkshop and [http://192.168.1.4/bobsfuntime](http://192.168.1.4/bobsfuntime) to serve files at /var/www/bobsfuntime

or externally, you would use a domain and web forwarding on the DNS settings.

[www.timsworkshop.com]("http://www.timsworkshop.com") would be forwarded to (my exturnal ip/DDNS) EG myhome.selfip.org/timsworkshop or 111.222.111.222/tims workshop

and [www.bobsfuntime.com.au]("http://www.bobsfuntime.com.au") would be forwarded to myhome.selfip.org/bobsfuntime or 111.222.111.222/bobsfuntime 

with port 80 forwarded to 192.168.1.4 on my router.

-Just a quick demo
ryannathans

---

### Post by volkswagner on 2011-01-30
You may find some ideas [here]("http://ubuntuforums.org/showthread.php?t=1642265&highlight=servers+connection"), for running two servers with one ip.

---

### Post by Vegan on 2011-01-30
apache can run 1 million sites if your server can keep up.

search google for apache vhost

---

### Post by koenn on 2011-01-30
> **Nova 107 said:**
> hey guys. Is it possible to run two servers through one ip address? And I don't mean through apache to run virtual servers. Right now my set up is: Cable modem>router>server.

yes, by using NAT (Network Address Translation), aka masquerading

---

### Post by Nova 107 on 2011-01-30
I just want to clarify, i can do this running two separate machines and not virtual servers?

---

### Post by koenn on 2011-01-30
This is an example of NAT :
3 servers - all accessible through the same IP address, 206.86.181.25 (when looking from the 'internet' side of things)

[IMG]http://users.telenet.be/mydotcom/library/network/nat/slide05.png[/IMG]

is that what you mean ?

---

### Post by Nova 107 on 2011-01-30
> **koenn said:**
> This is an example of NAT :
3 servers - all accessible through the same IP address, 206.86.181.25 (when looking from the 'internet' side of things)

[IMG]http://users.telenet.be/mydotcom/library/network/nat/slide05.png[/IMG]

is that what you mean ?

yeah

---

### Post by volkswagner on 2011-01-30
> **Nova 107 said:**
> I just want to clarify, i can do this running two separate machines and not virtual servers?


Did you check any of the links from my post.

I believe you will need a [reverse proxy]("http://www.classhelper.org/articles/reverse-proxy-server-squid-debian/reverse-proxy-introduction.shtml") if you want two machines hosting on port 80 with one external ip address.

What koenn has pointed out will work if you don't want both servers on port 80.

---

### Post by koenn on 2011-01-30
> **Nova 107 said:**
> yeah

you sure ? because you could just run 2 (or more) websites on the same server - each site having it's own name

---

### Post by koenn on 2011-01-30
> **volkswagner said:**
> 
What koenn has pointed out will work if you don't want both servers on port 80.
yeah, that's a problem, you need to be able to distinguish by port number.


I'm still trying to figure out what the OP is trying to do, exactly. 
Going by the 1st post (2 servers, 1 IP address) NAT would make sense.
For websites, a reverse proxy or just plain apache virtual(*)  hosts would make more sense. 
 

(*) note to the OP : 'virtual' here has nothing to do with virtualization, vbox, vmware, or whatever.

---

### Post by Nova 107 on 2011-01-30
> **koenn said:**
> you sure ? because you could just run 2 (or more) websites on the same server - each site having it's own name

it really depends on if I can get this other computer I have to run. I can put two on my current server, but if I can use two instead I'd rather keep them separate

---

### Post by elico on 2011-01-30
so you can use a reverse proxy...
nginx is one of the best !!!
the fastest reverse proxy i have ever seen.
even faster then squid.

you will put it this waY:


INTERNET >>> MACHINE WIHT SQUID\NGINX ON LISTENING ON PORT 80 >>>> REVERSING THE REQUEST BY THE SITE NAME TO WITHER THA SAME MACHINE ON ON OTHER PORT\ INTERNAL (127.0.0.1:81) 
AND BY THE OTHER SITE NAME TO THE OTHER MACHINE ON ANY PORT YOU WANT .

so.. the client..
i want from 2.x.x.x (IP):80 (site:[www.blala.blabla](www.blala.blabla)) ||| reverse proxy (hoo who was holding this site??? haaa 192.168.1.1:80 give me page ... or 192.168.1.20:80 give me )

---

### Post by spynappels on 2011-02-01
Apache has reverse proxying built in and you set up separate vhosts and point one of them to a different physical server using reverse proxy.

---

### Post by Nova 107 on 2011-02-05
Thanks guys! I think I'm going to stick to a virtual host for now until I get my other machine working, but this definitely helped :).

---

