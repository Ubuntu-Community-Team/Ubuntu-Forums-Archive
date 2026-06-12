---
title: "good jabber server tutorial?"
date: 2010-05-23
forum: Server Platforms
---

### Post by X1R1 on 2010-05-23
Hi, I have a running samba file server integrated with active directory and I want to expand its uses, can I mount on this same server a jabber service?

I want the employees to be able to chat on the LAN only, and, if possible, through a WAN that connects another office brach.

Where can I find a good tutorial for doing this?

Running ubuntu server 10.04

PS:If what im asking is too specific, then point me out to a good tutorial to setup a jabber server on ubuntu 10.04.

cheers

---

### Post by sylvester_0 on 2010-05-23
I used openfire back in the day; it should integrate well with your existing ware. I'm not sure on the license (don't think it's GPL) but it is free.

---

### Post by X1R1 on 2010-05-24
ok I will check it out, If anyone has some tutorial for doing this on ubuntu server I will be glad :D

ty

---

### Post by HermanAB on 2010-05-24
Maybe you should install Citadel.  It does pretty much everything, including Jabber.

---

### Post by dipeshmehta on 2010-05-24
> **X1R1 said:**
> ok I will check it out, If anyone has some tutorial for doing this on ubuntu server I will be glad :D

ty

Openfire is very easy to setup and deploy.  You may check: [http://www.igniterealtime.org/builds/openfire/docs/latest/documentation/install-guide.html](http://www.igniterealtime.org/builds/openfire/docs/latest/documentation/install-guide.html)

Dipesh

---

### Post by Khufucius on 2010-05-27
I'm starting this project as well.

I'll let you know how it turns out.  The goal right now:

Intra-office chat on the LAN, with possible access from outside for selected accounts.  Although I might just keep it LAN-only and then have external users VPN into the network.  I'm also planning on using pidgin with the Off-The-Record (OTR) plugin.

-Khufu

---

### Post by Khufucius on 2010-05-28
Openfire was extremely easy to install and set up.  I'm using a few of the plugins -- most obviously the "broadcast" (broadcast messages), "monitoring" (see who is logged on, usage stats, etc), and "search" (installed by default).

Right now I am using an integrated database to test openfire; I'll be using a dedicated MySQL Database when we deploy this for the whole office.

I'm still trying to work out a centralized contact management scheme, to avoid forcing a user to manually enter ALL the other employees' usernames to have a complete address-book/buddy-list.  Perhaps this is something I can mess with in a pidgin config file somewhere.

I've tested Spark and Pidgin as clients, and I think I'll be going with pidgin.  I love the OTR (off-the-record) plugin for pidgin, which is a fantastic little tool to handle encryption and integrity.

So:

1. Openfire XMPP Server
-broadcast + monitoring plugins

2. Pidgin
-Off-The-Record Plugin (OTR)

3. Contact management --> ?

I'll keep updating this as I go along.

---

