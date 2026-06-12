---
title: "openvpn and other server questions?"
date: 2010-02-13
forum: Server Platforms
---

### Post by bone2006 on 2010-02-13
In a small office I was planning on installing the Ubuntu server with LAMP.  I was hoping to control the box with ssh remotely.

My question is that I've never used openvpn and I was wondering if there's a tutorial out there?  There's a few window computers in the office that are connected to a printer.   We wanted to use openvpn to be able to print to the printer while not at the office.  Any help would be greatly appreciated.

Also is there an easy way using SSH or VPN for a few years to mount a drive letter on your windows machine?

I'm hoping to us this one box for SSH, OpenVPN, Apache...etc

Thanks in advance

---

### Post by dipeshmehta on 2010-02-15
You may please check [http://www.openvpn.net/index.php/open-source/documentation/howto.html](http://www.openvpn.net/index.php/open-source/documentation/howto.html) There is good howto.

To enable shares between windows & linux, please check Samba.

If you feel any difficulty come back here.

Dipesh

---

### Post by Iowan on 2010-02-15
You can search for **help.ubuntu.com vpn** Here is a bit of what I found:
[https://help.ubuntu.com/community/VPNClient]("https://help.ubuntu.com/community/VPNClient")
[https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN")
[https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")
[https://wiki.ubuntu.com/VPN]("https://wiki.ubuntu.com/VPN")

---

### Post by noway2 on 2010-02-16
In addition to the posts by Iowan (btw there is very good documentation in the ubuntu system already), there is one that I found to be key to getting openVPN to work well: [http://ubuntuforums.org/archive/index.php/t-1021592.html](http://ubuntuforums.org/archive/index.php/t-1021592.html).

On the client side you will need or want a means to connect to the remote server.  As far as I was able to determine there is a bug in network manager that makes connecting to this type of VPN difficult.  Instead, you can use gopen to create a little VPN button on your launcher bar.  I use it (am using it right now) and it couldn't be simpler.  You just click it to connect to your server, wait a few seconds and when it turns green, your good to go.

One other important thing to keep in mind when setting up the office server.  The office and the remote locations need distinct IP address ranges.  This means that you can't have the small office and homes using 192.168.0.x.

---

