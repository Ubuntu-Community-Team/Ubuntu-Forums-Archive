---
title: "Automatic security updates- what port does it use?"
date: 2011-08-13
forum: Security
---

### Post by metalix on 2011-08-13
My firewall policy is to DROP everything unless I explicitly decide I want to use it.

I want to be able to download and install automatic security updates. What port is used, for sending the update requests and receiving the updates?

---

### Post by haqking on 2011-08-13
> **metalix said:**
> My firewall policy is to DROP everything unless I explicitly decide I want to use it.

I want to be able to download and install automatic security updates. What port is used, for sending the update requests and receiving the updates?

On your Router or local machine ?
 
I think they use port 80. I believe apt uses HTTP:

---

### Post by metalix on 2011-08-13
Hi,

On my local machine. Isn't port 80 for http?

---

### Post by haqking on 2011-08-13
> **metalix said:**
> Hi,

On my local machine. Isn't port 80 for http?

yes that what i said, it uses port 80 because as far as i know Apt uses HTTP.

if you man sources.list you can see you can change the URI if you wish.

By default it uses http though, if you look the updates come from a http source.

But you could change that to ftp or whatever.

This is what i am assuming based on what i see and read in the man page.

---

### Post by bodhi.zazen on 2011-08-13
> **metalix said:**
> Hi,

On my local machine. Isn't port 80 for http?

No, that is not at all how it works.

You are running a client that is connecting to port 80 on the server. As a client you are going to use a random, high, non-privileged port to connect to port 80 on the server.

You would only be using port 80 if you are running a web server, such as apache, which would then listen (by default) on port 80.

See the introductory section here:

[http://bodhizazen.net/Tutorials/iptables#Basic_Networking_Concepts](http://bodhizazen.net/Tutorials/iptables#Basic_Networking_Concepts)

For most desktop users all you need to do is:

```
sudo ufw enable
```

If you are writing rules for iptables you would use

```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m state --state NEW -j DROP
```

If you are blocking outgoing traffic you will need to allow traffic to at least port 53 (for DNS) and 80 (for apache).

---

