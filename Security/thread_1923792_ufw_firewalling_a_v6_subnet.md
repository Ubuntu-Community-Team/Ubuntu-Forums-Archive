---
title: "ufw: firewalling a v6 subnet"
date: 2012-02-11
forum: Security
---

### Post by daenney on 2012-02-11
Hey everyone,

I recently got a v6 tunnel from my provider and currently ufw is firewalling the endpoint just fine.

However, with the tunnel came a v6 subnet that radvd is announcing to my network and my clients have picked up on and are using. Some of those clients are laptops and desktops that run their own firewalls and are pretty safe as is, others like phones and tablets I'm not so sure about.

To this end I'd like to use ufw to block incoming connections to the subnet (that don't already have an outgoing connection) in order to shield most of the more "stupid" clients.

Anyone got an idea as to how to decently to this in ufw?

---

### Post by uRock on 2012-02-11
Do you mean IPv6?

---

### Post by daenney on 2012-02-11
Yes. Sorry for the confusion, IPv6 is always shortened to v6 in my head.

---

### Post by kevdog on 2012-02-13
This is kind of going to answer your question -- and kind of not since it deals with iptables directly -- not through ufw.  But to block all ipv6 connections it would be something like this:

IP6TABLES=/sbin/ip6tables

$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

---

### Post by daenney on 2012-02-29
I'm aware of how to do it in iptables but I was rather hoping I could stop using my firewallv6.sh.

It seems ufw doesn't really cater for this right now, I'll see if I can get upstream to do something about that.

Thanks for the reply though :)

---

