---
title: "Server + external acces"
date: 2009-08-27
forum: Server Platforms
---

### Post by anneliesdepoorter on 2009-08-27
Hi,

I'm totally new to Ubuntu, so excuse me if I ask stupid questions ;)...

I need to install a server for a small business, so I'm trying out with an old desktop computer.
I already installed ubuntu server 9.04, but now I'm stuck.
I don't know how it's possible to share documents or directories or how users can login to it. I also can't find how to create a static ip...

If this is ok, i need to acces it from external locations also. We have got 2 offices and we need to see all the documents on both locations. The main location has got a fixed IP, so we should be able to acces the server. The only question is how.

I need to forward my port from my router to my server, but I don't know if it's possible to just surf to the location or if I need a vpn connection or something like that.

Can somebody help me?

---

### Post by pi4r0n on 2009-08-27
Hello **anneliesdepoorter**
> [COLOR=Black]
[/COLOR]I don't know how it's possible to share documents or directories or how users can login to it.[COLOR=Black]
[/COLOR][COLOR=Blue][COLOR=Black]The best way to share your files [COLOR=Red]**internal**[/COLOR] is to set up[/COLOR] [COLOR=Navy]**samba** **server**[/COLOR][/COLOR]. See this [_*[COLOR=Navy]**link**[/COLOR]*_]("https://help.ubuntu.com/community/SettingUpSamba") for more info

In order to share your files [COLOR=Red]**externally**[/COLOR] set up [COLOR=Navy]**ftp sever**[/COLOR]. See this [***_[COLOR=Navy]link[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server") for more info

> If this is ok, i need to acces it from external locations also. We have got 2 offices and we need to see all the documents on both locations. The main location has got a fixed IP, so we should be able to acces the server. The only question is how.
With regards to IP addresses they best way to do this is to set up IP filtering to only allow these IP addresses and there is few ways of doing it.

[LIST=1]
[*]Allow IP addresses on your firewall
[*]Allow IP addresses on iptable
[*]Allow IP addresses on your software firewall
[/LIST]
> 
I need to forward my port from my router to my server, but I don't know if it's possible to just surf to the location or if I need a vpn connection or something like that.With regards to port number allowance again you do this on your firewall.

If you have any other questions let us know.

Cheers

pi4r0n

---

### Post by tarps87 on 2009-08-27
Static ip:
```
sudo nano /etc/network/interfaces
```

add the lines

iface **eth0** inet static
address **192.168.1.5**
netmask **255.255.255.0**
gateway **192.168.1.254**

**eth0** = the interface, discoverable by ifconfig

(You may need to change the values in bold)

address = ip add
netmask = subnet

---

### Post by anneliesdepoorter on 2009-08-28
Thank you!

---

