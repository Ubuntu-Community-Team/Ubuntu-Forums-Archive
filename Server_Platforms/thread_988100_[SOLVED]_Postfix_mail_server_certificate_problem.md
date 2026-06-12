---
title: "[SOLVED] Postfix mail server certificate problem"
date: 2008-11-20
forum: Server Platforms
---

### Post by glasswalkerny on 2008-11-20
Hi,

I've set up a ubuntu server and followed this [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10") tutorial to install a email server.. the server works but when accessed by Thunderbird it always comes up with a message that the certificate is owned by localhost not the ip address of the server. This is my second question.. i'd like to access the server by mail.realmsguard.com (my domain) from inside the network but this never seems to work. i guess what i'm looking to do is associate the certificate with mail.realmsguard.com and be able to access the mail server by that name even on the local network. 

My network looks like this

INTERNET - router/wifi - vonage box (DMZ'd)
[COLOR="White"]........................[/COLOR]|
[COLOR="White"]........................[/COLOR]                       - hub - File Server
[COLOR="White"].................................[/COLOR]                            |
[COLOR="White"].................................[/COLOR]                             - Mail Server (ports for POP3, POP3S, IMAP and IMAPS natted)
[COLOR="White"].................................[/COLOR]                             |
[COLOR="White"].................................[/COLOR]                             - Workstation

let me know if you need anything else to help with this

---

### Post by MJN on 2008-11-20
> **glasswalkerny said:**
> i guess what i'm looking to do is associate the certificate with mail.realmsguard.com and be able to access the mail server by that name even on the local network.Yes - that's exactly what you need to do.
 
So, taking first things first, you need to create another certificate this time with a common name of mail.realmsguard.com. Presumably the HowTo walks you through this in which case I'll move on...
 
I see you've already got DNS configured for the realmsguard.com domain so we need to find out why you're not getting any joy with it internally. So, check these things in order:
 
i. Verify you can resolve the name from the LAN - do this with **host mail.realmsguard.com** - this should hopefully result in a (WAN) IP address
 
ii. Presumably you can access mail.realmsguard.com from outside your network? If so, and you can't access it internally, it is likely that your router doesn't support so-called 'NAT loopback' (amongst other names) i.e. internal LAN clients cannot access other LAN clients via the WAN IP address. There are many solutions to this including adding **<local LAN address> mail.realmsguard.com** to your LAN HOSTS files (/etc/hosts on Linux). Of course, substitute your server's private IP address as required.
 
That'll probably do for now... see how you get on and we can take it from there.
 
Mathew

---

### Post by glasswalkerny on 2008-11-20
ok i found where to change the certificate information that Courier generates on install (why it does so without asking for info i don't know). After deleting the old certificates I had to run a dpkg-reconfigure for courier-imap-ssl and courier-pop3-ssl to get it to generate new certificates... 
So now it identifies properly (although it throws a one time warning about not being able to confirm the cert.. that's ok)

The new problem is that mail.realmsguard.com goes through my hostdime account that i no longer use for email... 

```
root@Nosferatu:/etc/courier# host mail.realmsguard.com
mail.realmsguard.com is an alias for realmsguard.com.
realmsguard.com has address 72.29.72.210
realmsguard.com mail is handled by 0 ravencorp.homelinux.net.

```

so this is now my problem.. i'll have to talk to hostdime about that.

---

### Post by glasswalkerny on 2008-11-21
ok well while using mail.realmsguard.com is still getting grabbed by my hosting services site i can check mail via that by putting in an entry in my host file that points to the internal address.. i haven't tried from outside my network except via webmail which does work so i'll have to work with Hostdime on the issue. I'm hoping to move my web services internal also so i'll just deal with all the routing at that point.

---

### Post by MJN on 2008-11-21
Nice one. As you say, get the DNS reconfigured and you'll be sorted.
 
Mathew

---

