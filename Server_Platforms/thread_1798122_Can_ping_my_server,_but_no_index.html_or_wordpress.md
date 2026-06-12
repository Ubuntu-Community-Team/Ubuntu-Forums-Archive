---
title: "Can ping my server, but no index.html or wordpress"
date: 2011-07-05
forum: Server Platforms
---

### Post by rileyb76 on 2011-07-05
Guys,
Playing around with Ubuntu Server and trying to get a Wordpress blog up.  I restarted my Ubuntu Server today and now I cannot get the index.html under /var/www to show up, nor my Wordpress blog which was at /var/www/blog.  Does this sound like an apache issue?  

I ran sudo /etc/init.d/apache2 restart    just in case and still nothing.

I can SSH into and even FTP into it.

Thanks for any advice!

---

### Post by gnznt on 2011-07-05
What version # are you using?

---

### Post by rileyb76 on 2011-07-05
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

---

### Post by gnznt on 2011-07-05
you interested in doing a lamp server?
[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
[https://help.ubuntu.com/10.04/serverguide/C/php5.htm]("https://help.ubuntu.com/10.04/serverguide/C/php5.html")[l]("https://help.ubuntu.com/10.04/serverguide/C/php5.html")
[https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)
[]("https://help.ubuntu.com/10.04/serverguide/C/mysql.html")

---

### Post by rileyb76 on 2011-07-05
Yes!

---

### Post by rileyb76 on 2011-07-10
Shameless bump... anyone?  Still the same issues.  Can ssh and ftp into the box, but it seems apache isn't working.  Can't get the "it works" page nor the wordpress blog that was installed.

---

### Post by NZReaction on 2011-07-10
> **rileyb76 said:**
> Shameless bump... anyone?  Still the same issues.  Can ssh and ftp into the box, but it seems apache isn't working.  Can't get the "it works" page nor the wordpress blog that was installed.

Do you have IP tables enabled? Post the results please. ```
iptables -L INPUT
```

---

### Post by rileyb76 on 2011-07-10
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:ACK/ACK 
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED 
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain dpts:1024:65535 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:auth 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
DROP       tcp  --  anywhere             anywhere            tcp dpts:nfs:2050 
DROP       tcp  --  anywhere             anywhere            tcp dpts:x11:6063 
DROP       tcp  --  anywhere             anywhere            tcp dpts:afs3-fileserver:7010 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:1024:65535 
```



thanks for the help!

---

### Post by rileyb76 on 2011-07-10
I also tried to setup a firewall via Webmin and selected "Block all except SSH, IDENT, ping and high ports on interface".  
I'm just trying to run a LAMP server and put this on my DMZ.  No idea if this is correct.

---

### Post by NZReaction on 2011-07-10
Have you checked to see if the files are in the correct location?

```
cd /var/www && dir
```

---

### Post by rileyb76 on 2011-07-10
blog  index.html


THis is correct.

---

### Post by NZReaction on 2011-07-10
> **rileyb76 said:**
> blog  index.html


THis is correct.

So your sure Apache is running and listening on the correct IP address and port? I suggest checking the configs and logs for errors.

---

### Post by rileyb76 on 2011-07-10
Thanks.

I turned off the firewall in Webmin, restarted and the blog and "It Works" page showed up again.  Guess I need to read up on iptables and firewalls.

---

### Post by lisati on 2011-07-11
> **rileyb76 said:**
> I also tried to setup a firewall via Webmin and selected "Block all except SSH, IDENT, ping and high ports on interface".  
I'm just trying to run a LAMP server and put this on my DMZ.  No idea if this is correct.

If you want to do something like this, you'll need to make sure that port 80 (if you're using the "standard" installation of Apache) is NOT blocked.

---

### Post by CharlesA on 2011-07-11
> **lisati said:**
> If you want to do something like this, you'll need to make sure that port 80 (if you're using the "standard" installation of Apache) is NOT blocked.

Yeps.

There's a good tutorial on iptables [here]("http://bodhizazen.net/Tutorials/iptables"). :)

---

### Post by rileyb76 on 2011-07-11
I am a Webmin novice.  I'm guessing "Block all except SSH, IDENT, ping and high ports on interface" for the Firewall setting blocks port 80 traffic? 

Thanks guys.

---

### Post by CharlesA on 2011-07-11
> **rileyb76 said:**
> I am a Webmin novice.  I'm guessing "Block all except SSH, IDENT, ping and high ports on interface" for the Firewall setting blocks port 80 traffic? 

Thanks guys.

Yep.

From what I remember, you can edit the firewall rules manually, but it's been a while since I've used webmin.

---

### Post by gnznt on 2011-07-12
try configuring the apache vhost .conf file.

---

