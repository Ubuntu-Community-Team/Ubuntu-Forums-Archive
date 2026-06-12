---
title: "Setting up ufw on with Lighttpd, Varnish, MySQL, etc?"
date: 2013-04-07
forum: Server Platforms
---

### Post by hoppipolla on 2013-04-07
I tried allowing port 22 and port 80 both TCP, and yet it still fails.

It's set to deny all by default incoming and allow all by default for outgoing.

SSH and SFTP still works and SOMETIMES HTTP seems to work but not other times.

What am I doing wrong? :(

As a warning I am using Debian Squeeze not Ubuntu (wish I chose Ubuntu server now though!) but I hope that's ok.


Thanks,

Hoppi ^_^


EDIT -- Oh and to the mods - I made a small mistake in the thread title.. could you remove the "on" before "with"? Thanks :)

---

### Post by darkod on 2013-04-07
If you are still at the beginning of this project I would recommend using iptables directly instead of ufw. The rules will be much more clear, ufw in some cases makes a mess, although it still works.

First of all, you have direct access to the server (not only ssh) so you can't lock yourself out, right?

Also, with iptables you can test rule by rule without even making them permanent. For example, try disabling ufw, flushing the iptables, then setting up DROP policy for incoming traffic and allowing only ssh on port 22:
```
sudo ufw disable
sudo iptables -F
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -A INPUT -i <interface> -p tcp --dport 22 -j ACCEPT
```

If you want you can limit the interface on which the traffic will be allowed with -i, if not remove that from the command. After executing that iptables command you should have ssh access.

For other ports and services it would be similar.

---

### Post by hoppipolla on 2013-04-10
Sorry for my silence! I had other issues on my server that took my attention that's all :)

Also erm, my friend said that closing unneeded services that are listening on ports is the simplest way to achieve this increase in security, as Debian will just ignore packets on closed ports anyway. Is there then no need for a firewall at all? :)

---

### Post by darkod on 2013-04-10
Well, in general there is no danger from ports where no services are listening. And by default there are no services listening on ports unless specifically configured/installed. Wheter you need a firewall or not, only you know. Depending what you want to protect.

For example with iptables you can protect the SSH so that you can only access it from within your home network.

It also depends how is the server connected to the internet. If it goes through a router where you need to forward ports, only the forwarded ports can reach the server anyway, so there is no real point having a firewall. You control everything from the router and its firewall.

Also, if the services you have active on the server are for public access (like port 80 for http), and if you want everyone to access them, there is no much point configuring a firewall since you don't plan to block port 80 anyway, if you want it open to all that's no firewalling.

---

### Post by hoppipolla on 2013-04-10
Agreed yeah.

To be honest... I probably don't need one when all this has been factored in!

I just assumed it was the "done thing" for a server but didn't fully understand why!! I too figured that Debian was probably secure enough anyway due to what we've discussed.

I'll monitor open ports ("netstat -a", right? :) ) and go from there I guess!

---

