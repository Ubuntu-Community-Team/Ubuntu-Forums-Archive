---
title: "Binding an FTP server to use only one interface (VPN)"
date: 2007-11-21
forum: Server Platforms
---

### Post by Cadmus on 2007-11-21
Morning, I've been messing around with OpenVPN and finding it great. I've successfully got a WinXP machine tunelling through to my Feisty-based media centre in my flat and I can access the Samba share.

The problem I've encountered is that folders with a very large number of files (such as my music folder) grind to a halt and time out, as far as I've been able to find it's a problem inherent to the share browser in Windows. One thread I found recommended using an FTP server which would suit me fine. Seeing as I already have the VPN tunnel I was thinking of creating a completely open ftp server but having it only accessible to machines coming in through the VPN.

There's a lot of opinions on FTP servers for Ubuntu so I was hoping for some advice. 

It strikes me that the easiest way to do what I want would be to configure the FTP to only accept connections on a given interface (tun0) but I've been hitting a lot of brick walls in my search.

P.S. First post, please be gentle :)

---

### Post by koenn on 2007-11-21
It might be possible to bind your ftp daemon to a specific interface, but that mostly depends on what ftp server you're using ; the feature should be documented in its documentation or its config file.

Other than that, you can use iptables to set up a rule to only accept ftp traffic on your thun interface. iptables is basically a firewall, and ftp being troublesome when it comes to firewalls, this might require a bit of work to get it going, but itt should be do-able.

---

### Post by Cadmus on 2007-11-21
> **koenn said:**
> It might be possible to bind your ftp daemon to a specific interface, but that mostly depends on what ftp server you're using ;

I suppose part of my question was if anyone knew an ftp server that did that? If not time to roll up my sleeves and try to get to grips with the I'm-sure-it's-not-so-scary-once-you-learn-it iptables.

Thanks for your input.

---

### Post by koenn on 2007-11-21
for the ftp bind to interface, sorry, I'd have to research it myself,
and iptables isn't that hard - the hard part is figuring out what you have to make it do. After that, telling it what to do is rather straightforward.

---

### Post by Cadmus on 2007-11-22
Thanks again for your help

/dives into google for tutorials on iptables

---

