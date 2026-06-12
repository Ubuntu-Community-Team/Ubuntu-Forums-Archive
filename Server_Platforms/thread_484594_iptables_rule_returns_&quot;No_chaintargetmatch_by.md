---
title: "iptables rule returns &quot;No chain/target/match by that name&quot;."
date: 2007-06-26
forum: Server Platforms
---

### Post by ddcc on 2007-06-26
Hi, I'm trying to get iptables to block TCP RST packets, state established from port 15779. I've been entering the following command, however, iptables doesn't seem to accept it and tells me "iptables: No chain/target/match by that name." Help would be appreciated. This is on Feisty.

sudo iptables -A DROP -p TCP -m state --state ESTABLISHED tcp --sport 15779 --tcp-flags ALL RST

---

### Post by ddcc on 2007-06-26
Resolved through IRC.

---

### Post by AndEat on 2007-11-29
This thread comes up #1 in a search for 

iptables: No chain/target/match by that name ubuntu

Post the solution?

---

### Post by MJN on 2007-11-29
I don't use iptables myself but from a quick scan of the manual could it be that the 'DROP' chain doesn't exist?
 
Instead, I suspect the following would work:
 
**sudo iptables -A INPUT -p TCP -m state --state ESTABLISHED tcp --sport 15779 --tcp-flags ALL RST -j DROP**
 
This adds the rule to the default INPUT chain, and the responding action for a match is to DROP.
 
Mathew

---

### Post by ddcc on 2007-11-29
Yes, I recall that that should be the solution. I was adding it to an invalid table without specifying the action.

---

### Post by linux__rulez on 2008-05-02
The original problem has come up so high in Google that I could not resist to give some more explanation about what goes wrong.

Here the original problem:

> **ddcc said:**
> Hi, I'm trying to get iptables to block TCP RST packets, state established from port 15779. I've been entering the following command, however, iptables doesn't seem to accept it and tells me "iptables: No chain/target/match by that name." Help would be appreciated. This is on Feisty.

sudo iptables -A DROP -p TCP -m state --state ESTABLISHED tcp --sport 15779 --tcp-flags ALL RST

The above statement tries to add a rule to the table of DROP (which does not exist). Instead it should be for example INPUT. And the target (-j) should be DROP. For example:

sudo iptables -A INPUT (add some rules here) -j DROP

Should save someone time

---

### Post by MJN on 2008-05-02
We'd done that! :)

(Good to hear Ubuntu Forums being high up in the Google results again though!)

---

