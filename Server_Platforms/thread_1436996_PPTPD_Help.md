---
title: "PPTPD Help ?"
date: 2010-03-23
forum: Server Platforms
---

### Post by yesrno on 2010-03-23
Hello,

A few days ago I was trying to set up my Ubuntu server for VPN uses. I tried to get it working with the pptpd package and followed the following "guide":
[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

I tried playing around with the settings and such to my personal liking but I keep getting the same error. Whenever I test my VPN connection into my internal network, it works good. But when I try to connect to my internet ip it gets stuck at the status of 
"Registering computer on the network". My client is a Windows 7 by the way, but I get the same error when trying with a Xp client.
Here is the error message from my Win7 client. It does however work when I try to connect to the vpn server using the internal ip.

[IMG]http://i42.tinypic.com/167s8ig.png[/IMG]

I was hoping someone here could help me out with my problem.
Thanks in advance,
Peter

---

### Post by EmanresuusernamE on 2010-03-23
Could you post some of your configuration so that we can get a little bit more knowledge of what's happening with your server?

Also, have you thought about trying to use an administrative program such as Webmin? It can't really install a lot of what you might want, but it can configure all sorts of things quite well.  I have PPTPD installed on my system and I configured it with Webmin and it my systems get onto the VPN pretty well.  I don't have forwarding of any sort enabled so I can only really access my server while on the VPN, but I can VPN in.  :)  It was more of a test than anything.

---

### Post by dfxdeimos on 2010-03-23
---

---

### Post by yesrno on 2010-03-23
Yes I have forwarded the port correctly, only port 1723 right ?
Also yes, at this moment I am in the same internal network as the Vpn server. When someone from the outside is trying, it will get the same error back tho.
Like I said when I try to connect with my internal ip just to test the connection, it's working fine but when I change that exact ip to my internet ip. It gets stuck at the Registering part.

Here is a part of the config:
```

# TAG: ppp
#       Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#       Specifies the location of the PPP options file.
#       By default PPP looks in '/etc/ppp/options'
#
option  /etc/ppp/pptpd-options


# TAG: logwtmp
#       Use wtmp(5) to record client connections and disconnections.
#
logwtmp

localip 192.168.1.18
remoteip        192.168.1.1-100

```Deleted most of the commented rules.
1.18 being the Ethernet card on the Vpn server. This card has right access to the Internet.
And I already tried adding my internet ip to the remoteip field, won't do any good.
Hope this is any help!

---

### Post by dfxdeimos on 2010-03-23
---

---

### Post by yesrno on 2010-03-23
Yes I'm sure the result is the same. 
However I modified the remoteip to 192.168.1.50-100 and it seems to work correctly, from intern to my internet ip that is. Tomorrow I will try to connect from the outside to see it myself, thank already! ;)

---

### Post by EmanresuusernamE on 2010-03-23
> **dfxdeimos said:**
> Depending on your router, connecting to a server that is hosted on the same network via your external IP can cause issues and odd behaviors. 

Speaking of routers, did you make sure your router was enabled to allow VPN traffic to pass through? I know that's an option in routers out there, and I also know that a large amount of my customer's have issues with VPN traffic at hotels and such which probably don't have such an option set.

---

### Post by yesrno on 2010-03-24
Okay I just tested it from the outside and it is all working well :)
I changed the 
192.168.1.1-100
to 
192.168.1.50-100
Which did the trick. Thanks for all the help!

---

