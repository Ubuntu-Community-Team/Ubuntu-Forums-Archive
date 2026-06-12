---
title: "how to by pass a proxy server?"
date: 2009-03-17
forum: Server Platforms
---

### Post by machinakias on 2009-03-17
hi all...
i need your help with this: i have set up an ubuntu 8.10 server,
it gets ip from dhcp (that's ok..) and there's also a proxy server with ip 192.168.10.1

i tried to get my server to the internet by adding the proxy's ip during the installation (like this: 192.168.10.1:8080)

the problem is that i can't get on the internet at all..

where was i go wrong? any help please?

a first-timer ubuntu (wannabe) admin.....;)

---

### Post by askreet on 2009-03-17
What are you trying to do through the proxy?  Browse the web?  Updating packages?

Are you behind a firewall that won't allow you to go outboound on your own, i.e. forced to use the proxy?

---

### Post by machinakias on 2009-03-17
> **askreet said:**
> What are you trying to do through the proxy?  Browse the web?  Updating packages?

Are you behind a firewall that won't allow you to go outboound on your own, i.e. forced to use the proxy?
well,as far as i know there is a proxy server in 192.168.10.1 that we use to access the internet.(i tried it with a live cd...added this proxy in firefox's settings and then i got internet access)

there 's also a firewall (named fortigate i think..maybe i can find out more about it..the old IT left and i have no clue what's going on..) but i 'm not sure if it cuts me off...

i tried to set static ip with settings from another machine that has full access to the web (as an admin of the company)but no luck..

i dont know what i'm doing wrong..maybe i have to add the settings somewhere else except the /etc/network/interfaces

i need access to update my server packages (mainly) and maybe just browse the web for a while..

got any ideas?

(sorry for being so long....) ;)

---

### Post by machinakias on 2009-03-20
noone knows folks? :(

i cant find any clue....

---

### Post by hellrabbit on 2009-03-20
Let me start by saying most folks in corporate IT field / domain administrators do not take kindly to foreign objects. I just feel compelled to give you a heads up, people get fired for stuff like that.

With that said, I think your proxy may be challenging your request to web surf, download packages, etc.

Meaning you may need to add your domain credentials.

example http_proxy=http://username:password@host:port/
example (if using installer) [http://username:password@host:port](http://username:password@host:port)


I'm no expert, and I don't pretend to be. Just trying to help.

---

### Post by bapoumba on 2009-03-20
Is this on your private network or on a corporate network?

---

### Post by Almighty on 2009-03-20
> **bapoumba said:**
> Is this on your private network or on a corporate network?

This is the most important question in the thread.

I would first inspect the browser config before anything else.

---

### Post by EdObie on 2009-04-10
[QUOTE=hellrabbit;6928670]
example http_proxy=http://username:password@host:port/
example (if using installer) [http://username:password@host:port](http://username:password@host:port)
[QUOTE]


Simply run this from the Terminal

export http_proxy=http://username:password@host:port/

It worked for me.

---

