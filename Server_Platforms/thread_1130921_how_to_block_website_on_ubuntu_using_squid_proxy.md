---
title: "how to block website on ubuntu using squid proxy"
date: 2009-04-20
forum: Server Platforms
---

### Post by salim.madni on 2009-04-20
hello sir/madam/gurus

i am beginner to linux and trying to learn it.

i made 1 testing server of ubuntu 9.04, where i install configure using squid proxy server.

I need to blocked the websites and ips, domains, subdomains. also download.

so i read so many article guideline but i could not success.

can some one guideline step by step how to do it.

i create one file, then block access and acl list define the file also, restart squid. but sites are not getting blocked.

what happend next, how it looks like if the site are blocked.

can some one also guide, if a few number of sites say like  playboy.com,gmail.com to block, and a huge list of sites to block.

kind regards
salim

---

### Post by nandemonai on 2009-04-20
[http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733) is a very good howto on the subject.

---

### Post by salim.madni on 2009-04-21
dear gurus

thanks for support this link

but this is using third party software filter content programs

anyway inside squid proxy where we can blocked ips/websites etc

advise further

regards
salim

---

### Post by salim.madni on 2009-04-21
hello sir

can you advise which file to edit and put below details

# UNCONFIGURED
filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

---

### Post by koenn on 2009-04-21
see here for an example of using whitelists and blacklists
[http://www.screaming-penguin.com/node/3871](http://www.screaming-penguin.com/node/3871)

basically, you need in /etc/squid/squid.conf
```

acl     localnet   src    192.168.1.0/24               #define localnet
acl     blacklist dstdomain "/etc/squid/blacklist"     #define blaclist

http_access deny blacklist
http_access allow localnet

```
in /etc/squid/blacklist, you list the domains you want to block, starting with '.' to include hostnames/subdomains :
```

.plaboy.com
.gmail.com
.microsoft.com
.ubuntuforums.org

```
and so on

Note that filtering through a proxy server only works if the browser is configured to use the proxy, and that direct access to the internet is blocked or the user is prevented from modifying the proxy settings of the browser(s)

---

