---
title: "Hardening my Firewall"
date: 2010-08-14
forum: Security
---

### Post by Techtronic on 2010-08-14
Hi

I have a VPS (Ubuntu 8.04 server eition) and as such am stuck with using a software firewall.

i currently have UFW installed.

I would ideally like to have my firewall be a little rude, or rather just not polite. I know what i am asking will break the RFC, but i consider this ok due to the security benefits.

I would like to have my firewall
1) ignore (eg drop without responding)all packets that dont start with a syn flag
2)for all other traffic that is currently blocked, have it dropped (again drop it without responding)

If there are any other rules you can think of i would like to know them. I already have only the services i want open and the rest blocked.

Open to comments

Thanks in advance for any help you can offer.

---

### Post by CharlesA on 2010-08-14
Learn how to use [iptables]("http://bodhizazen.net/Tutorials/iptables/") (ufw/gufw is a frontend for them)

DROP will silently drop packets. I know you can drop packets with certain syn/ack flags, but I don't know if it can tell if it's at the beginning or not.

---

### Post by HermanAB on 2010-08-14
You are running Linux?

Relax and enjoy your system.  Most of the network issues of yesteryear are taken care of by default in the modern network stack.

---

### Post by bodhi.zazen on 2010-08-14
I have never seen any credible documentation that DROP is more secure then REJECT and DROP, only opinions.

If the default UFW settings are insufficient, you will need to learn iptables (IMO at least).

Finally, I would add, that by default there are no significant open ports / listening services, so perhaps a better question is - what are you trying to accomplish with a firewall ?

---

### Post by CharlesA on 2010-08-14
The only difference between REJECT and DROP is that REJECT sends a IMCP message that the port is closed.

---

### Post by Techtronic on 2010-08-15
CharlesA, 
I'd like to drop the packet not just reject it.

I am fully aware that security is simply a comfort blanket to its owner, but the mroe layers you put in the more you frustrate script kidies that learnt to use nmap on youtube. I know that if a hacker wanted in, he would get in, i can make it difficult, and my firwall isn't going to help me much. 

Just want to annoy kiddies."its just another layer of the onion that is security"

Herman, I cant relax, i live and breath this stuff daily, i see it every day, i know how easy it is.

Sounds like IP Tables may be the way to go, can i wire ip tables along side UFW?

---

### Post by CharlesA on 2010-08-15
> **Techtronic said:**
> CharlesA, 
I'd like to drop the packet not just reject it.

Then just use DROP instead of REJECT. :)

> Sounds like IP Tables may be the way to go, can i wire ip tables along side UFW?

UFW is just a frontend for iptables. Don't use both at the same time.

Check out this page on iptables: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

It's a pretty good one. :)

The way I have mine set up, is that I created the rules using iptables then use iptables-save to create a file with the rules in it, that I load everytime the machine boots/eth0 comes up.

---

### Post by bodhi.zazen on 2010-08-15
> **Techtronic said:**
> CharlesA, 
I'd like to drop the packet not just reject it.

I am fully aware that security is simply a comfort blanket to its owner, but the mroe layers you put in the more you frustrate script kidies that learnt to use nmap on youtube. I know that if a hacker wanted in, he would get in, i can make it difficult, and my firwall isn't going to help me much. 

Just want to annoy kiddies."its just another layer of the onion that is security"

Herman, I cant relax, i live and breath this stuff daily, i see it every day, i know how easy it is.

Sounds like IP Tables may be the way to go, can i wire ip tables along side UFW?

I understand the deep rooted fear, but, as I indicated DROP is no more or less secure then REJECT.

DROP does NOT do what you think it does.

If you do not believe me, try it. Make a simple rule

```
sudo ufw disable
sudo iptables -F
sudo iptables -A INPUT -j DROP
```

The first two command simply clear (flush) your rules.

The third command DROPs all traffic.

Now scan the box with nmap.

The port is closed with both DROP and REJECT, both are secure, and DROP alone does not hide your box, as you can see :p

If you want to learn more, read up on iptables and nmap.

The bottom line, IMO :

1. By default you have no significant open ports (listening services) so there is not much to be gained with a firewall, less if you are already behind a router.

2. DROP and REJECT are equally secure. Use either one, but do not fool yourself into believing you one is more or less secure then the other.

Linux is not Windows and you can not increase your security by blindly applying windows mentality. To increase security you need to look under the hood, understand how the OS works, and then make adjustments. 

The reason for this is, unlike windows, the defaults are already quite secure, and so there is a steep learning curve if you wish to improve.

See the security sticky and

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

