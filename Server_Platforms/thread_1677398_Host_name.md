---
title: "Host name"
date: 2011-01-28
forum: Server Platforms
---

### Post by webdirector on 2011-01-28
Hello,

I have a problem understanding the naming convention. I have a ubuntu server at home and a fix IP. I have several domains that I point at my home IP address and I got it to work that each domain name is pointed at the virtual server for each domain.

The Ubuntu machine I called server1.server1 ( I mean when I type in hostname in the terminal window).  I also noticed when I type in my fix IP the server is connects to I get an empty website.

So my question is should I name my server by one of my internet domains ? or what should I call it ?

I just do not know what to search for as I do not understand this naming concept

Thanks for help ( or pointing my in the right direction )

---

### Post by arrrghhh on 2011-01-28
Is something not working?  If you have all your domains correctly pointed... then what's the problem?

If you don't like how it looks, you can certainly change it.  Since I don't know your exact setup, I don't know if it'll cause any issues - based on your description, it shouldn't.

---

### Post by redmk2 on 2011-01-28
> **webdirector said:**
> Hello,

I have a problem understanding the naming convention. I have a ubuntu server at home and a fix IP. I have several domains that I point at my home IP address and I got it to work that each domain name is pointed at the virtual server for each domain.

The Ubuntu machine I called server1.server1 ( I mean when I type in hostname in the terminal window).  I also noticed when I type in my fix IP the server is connects to I get an empty website.

So my question is should I name my server by one of my internet domains ? or what should I call it ?

I just do not know what to search for as I do not understand this naming concept

Thanks for help ( or pointing my in the right direction )

There are several concepts at play here.  The hostname is exactly that; the name of the individual host.  The domain name is the DNS name that you purchase that can include multiple hosts.

An example of this could be```
hostname = oak
domain name (DNS) = trees.com
```

You can have multiple hosts in the trees.com domain if you wish and you can refer to them locally by just their hostname or Internet wide by the combination of their hostname and DNS domain.  Like these examples```
hostname = oak
hostname = pine
hostname = maple
hostname = birch

domain name = trees.com

oak.trees.com
pine.trees.com
maple.trees.com
birch.trees.com
```

DNS is for mapping your IP address to the Domain and ultimately an individual host.

Hosts (as in /etc/hostname or /etc/hosts) predates DNS and is for naming and mapping to IP addresses of individual hosts ***locally ***.  So this would only work on your LAN```
ping birch
```This would work across the internet or locally (if the proper internal configuration is setup)```
ping birch.trees.com
```

you can search on DNS or Domain Name System or hostname or  /etc/hosts.  All will give you great information.

This is what [URL="http://en.wikipedia.org/wiki/Domain_Name_System"][B][U]
[COLOR="DarkSlateGray"]Wikipedia [/COLOR][/U][/B][/URL]says.

---

### Post by webdirector on 2011-01-29
Thank you [redmk2]("http://ubuntuforums.org/member.php?u=624368") for the great explanation.

Best regards

---

