---
title: "A primer on lan security with Ubuntu?"
date: 2011-09-05
forum: Security
---

### Post by Retor on 2011-09-05
Hi!

I have a network at home with:
- network modem connected to a 
- wifi router (AEBS) that takes care of IP delegation and
- 4 pc-s running Ubuntu, Lubuntu (x2) and Mint

Lately I've started to play with opening up certain port on the router so I can connect to my network when I'm not at home. 

Can anyone recommend articles/websites/books on Ubuntu and home network security? I don't want to accidentally forget to lock the front door when I'm at work.

---

### Post by haqking on 2011-09-05
> **Retor said:**
> Hi!

I have a network at home with:
- network modem connected to a 
- wifi router (AEBS) that takes care of IP delegation and
- 4 pc-s running Ubuntu, Lubuntu (x2) and Mint

Lately I've started to play with opening up certain port on the router so I can connect to my network when I'm not at home. 

Can anyone recommend articles/websites/books on Ubuntu and home network security? I don't want to accidentally forget to lock the front door when I'm at work.

For security issues in general with Ubuntu i receommend reading the following:

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

and this will give you a good grounding in the security of your system and such like.

---

### Post by Retor on 2011-09-06
Thanks! 

Some very valuable information about SSH. 

I'll just shoot in one question: 

The sticky mentions that all ports are closed by default in Ubuntu, but wont Firefox, chat and email software open some? 

So it's not just a matter of open ports, but also a matter of what's listening to that port and what that listener is authorized to do?

---

### Post by Dangertux on 2011-09-06
> **Retor said:**
> Thanks! 

Some very valuable information about SSH. 

I'll just shoot in one question: 

The sticky mentions that all ports are closed by default in Ubuntu, but wont Firefox, chat and email software open some? 

So it's not just a matter of open ports, but also a matter of what's listening to that port and what that listener is authorized to do?

In my opinion people spend far too much time overthinking "open ports"

You are correct in your assumption that when creating a connection to an outside service Firefox and the like will create connections, many actually. That being said those are going to be listening for traffic from a defined source. Where you can start getting into trouble is where you have services that are listening like this

```

0.0.0.0:22 or *:22

```

Even then, if you need the SSH service or whatever services is listening on all interfaces it's still not the end of the world.  You just have to change your thinking about security at this point. Look at it like a house. If you build a house with no doors or windows, you can't get inside of it without breaking down a wall. Everything in the house is essentially secure. But it's not a home it's a bunker.  If you build a completely secure system you will find it is not very functional.

In my opinion, security is a balance, how much security are you willing to give up for the functionality you desire? Also, how can you best secure the services you want to use. For instance many people run a web server or some other type of server on their home network. This is acceptable, but in order to properly secure this set-up you need to go beyond simple network firewalls, you start getting into things like application level firewalls (apparmor), permissions, and packet filtering. You also begin to understand the need for monitoring things through IDS software such as snort. 

So... Depending on what you want going on your network, security can be as simple as locking down your router reasonably well, using strong passwords and setting up iptables correctly on your machine. Or it can become very complicated. Security imo is a means not an end.

---

### Post by Rob_H on 2011-09-06
> **Retor said:**
> 
The sticky mentions that all ports are closed by default in Ubuntu, but wont Firefox, chat and email software open some? 

So it's not just a matter of open ports, but also a matter of what's listening to that port and what that listener is authorized to do?

Client programs like Firefox and Thunderbird make outgoing connections to remote servers and receive traffic back from those servers on those same connections. The traffic from the remote hosts is **solicited** (i.e. you request some data and it responds).

This is very different from a server program that listens for **unsolicited** traffic from any host on a specific port. When people talk about "open" ports, that's what they mean: ports that are open to **unsolicited** traffic.

---

