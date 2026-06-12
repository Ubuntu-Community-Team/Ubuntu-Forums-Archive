---
title: "iptables question"
date: 2009-03-21
forum: Security
---

### Post by Cyked on 2009-03-21
here is my iptables set up.  after setting these I can't connect to any internet site.

```
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere
   18  1508 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www
  204 16176 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:xxxx
11356 1512K DROP       all  --  any    any     anywhere             anywhere

```

Any ideas?  I dug around and wasn't able to find anything.

XXXX is for my SSH port

---

### Post by bodhi.zazen on 2009-03-21
Well, your last line is to drop everything, so your rules are too restrictive.

How did you configure iptables ?

And is that the full output of 

sudo iptables -L -v , or just the INPUT chain ?

---

### Post by Cyked on 2009-03-22
I have only altered input, but can post the rest if you want.  This is what I used as a guide.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I image the entry for "established connections" allows web traffic in the case of the link above?  I think I'm more limited in my knowledge of networking to be able to create an iptables list that will only allow very specific things (and not break my network) than the ability to find a how:to on creating entries for iptables in general.

---

### Post by bodhi.zazen on 2009-03-22
Insert a rule, before your drop all, allowing ESTABLISHED and RELATED connections for port 80 (--sport 80).

See if this helps : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Cyked on 2009-03-22
```
sudo iptables -I INPUT 1 -m state --state ESTABLISHED,RELATED -p tcp --dport 80 -j ACCEPT
```

Is that right?  I tried that and it didn't help.

---

### Post by bodhi.zazen on 2009-03-22
No, you will need to read the link I gave you. If you understand iptables the command is simple. I do not see helping you by writing your rules for you, I prefer to give you a broader understanding via a link.

---

### Post by kevdog on 2009-03-22
Um, to connect to a remote site -- don't you really want the OUTPUT chain rather than the input chain?  And why are you being restrictive on the output chain anyway?  Having problems that you need to block outbound traffic?

---

### Post by Cyked on 2009-03-22
I've only touched input

---

### Post by DGortze380 on 2009-03-22
> **bodhi.zazen said:**
> Well, your last line is to drop everything, so your rules are too restrictive.


I disagree, that essentially creates an implicit deny which is perfectly fine and typically preferred on you main firewall.

---

### Post by bodhi.zazen on 2009-03-22
> **DGortze380 said:**
> I disagree, that essentially creates an implicit deny which is perfectly fine and typically preferred on you main firewall.

I think you mis read the question and answer. The OP wishes to allow traffic, presumably Apcahe.

Sure, a default policy of drop is fine, but the OP is asking how to allow traffic to the web. How else do you allow traffic ? 

I never suggested the OP should change the default policy.

---

### Post by DGortze380 on 2009-03-22
> **bodhi.zazen said:**
> I think you mis read the question and answer. The OP wishes to allow traffic, presumably Apcahe.

Sure, a default policy of drop is fine, but the OP is asking how to allow traffic to the web. How else do you allow traffic ? 

I never suggested the OP should change the default policy.

I understand what you mean, I think your original post was a bit unclear... it appeared as though you were suggesting that a default deny rule was too restrictive, which it clearly is not. The other rules are not permissive enough.

Point taken. Thanks for clarifying.

---

### Post by bodhi.zazen on 2009-03-23
Yes, it was a bit unclear :twisted:

---

### Post by The Cog on 2009-03-23
Assuming that was the INPUT ruled Cyked poster posted, it is a little too restrictive. It makes no provision for reply packets from the DNS server, so you won't be able to connect to anything by name. You need to allow UDP from port 53. If you're being really restrictive, only allow established UDP with a source port 53.

---

