---
title: "Fiesty 7.04 Server using wireless"
date: 2007-10-10
forum: Server Platforms
---

### Post by baronne on 2007-10-10
howdie doodies.
I am setting up my first home server using 7.04 Feisty Fawn.  What I intend to do is chuck the servers in the garage 'cos they're so damn noisy. I've gone through the install a few times now and the only cards that show up during install are the eth0 and eth1 which I just skipped as I wanted to setup using ra0 which is the D-Link card. I have managed to do this and I get an internet connection, etc. 

The problem I have is that I cannot ping this server from my laptop. It's almost as if there is a firewall or something blocking it. I have installed SSL, Samba and Webmin, but I cannot connect to them using Putty or via browser.

Are there any places I should be looking to see if something is blocking traffic?

---

### Post by James79 on 2007-10-10
I will assume both your server and laptop are connected to the same network via the same access point.

The default server install has no firewall. So unless you enabled one, there should be none. To be sure, what's the output of this command:

```
sudo iptables -L
```

Are you pinging it by IP or by hostname? What happens when you try by IP? Can you ping your laptop from your server (by IP)? What output does this command give you:

```
iwconfig
```

Just some ideas to get us going...

---

### Post by baronne on 2007-10-11
I didn't install any firewall, so I guess that's out the question...
cheers I'll try that this evening when I get back home...

---

