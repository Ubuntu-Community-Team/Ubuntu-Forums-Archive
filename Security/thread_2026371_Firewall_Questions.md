---
title: "Firewall Questions"
date: 2012-07-15
forum: Security
---

### Post by Hungry Man on 2012-07-15
I'm using GUFW and I'm got these rules:

out 53, UDP
out 80, 443 TCP
out 7070 TCP (for IRC)

My question is... if I allow 7070 out what's stopping a program already on the system from using it?

Firefox doesn't need 7070, right? it should be satisfied with 53, 80, and 443. But if it tried to use 7070 wouldn't it be able to?

I'm wondering if there's any way to bind a program to a port specifically and not allow other programs to use that port.

And what if I use Google Voice and Video for Hangouts? I have to enable ports:
19294,19395,19302

Can't Firefox then access those? And wouldn't any program simple be able to access those? Couldn't malware just use them?

And it seems like dnsmasq wants access to all sorts of ports.

---

### Post by Cheesehead on 2012-07-15
> **Hungry Man said:**
> if I allow 7070 out what's stopping a program already on the system from using it?

Firefox doesn't need 7070, right? it should be satisfied with 53, 80, and 443. But if it tried to use 7070 wouldn't it be able to?

I'm wondering if there's any way to bind a program to a port specifically and not allow other programs to use that port.

Allowing data through a firewall port is unrelated to which application is using that port. So nothing except your admin skill prevents an application from seizing and using (or abusing) a port.

Your underlying assumption is that applications are by default opaque, untrustworthy, ignore standards, and require direct supervision by the admin. That's not a valid assumption in this community - you have complete access to the application source code, applications are fully expected to behave politely and adhere to the standards (like port assignments), and users are expected to help make applications more stable and predictable.

Generally, if an application "grabs" port unexpectedly, file a bug report and don't use it - there are well-behaved alternatives.

If you really feel that a port is in danger of being fought over by multiple processes, then kill the undesired process. Or change it's config file to prevent the conflict.

Do you have reason to believe Firefox in behaving badly and stealing ports?

The dnsmasq documentation explains clearly which ports it needs and why. Dnsmasq provides many services...and some of those services require various ports.

---

### Post by CharlesA on 2012-07-15
There is no application-based firewall for linux, but you could try using: 

-m owner --cmd-owner "/path/to/application" 

[http://www.linuxforums.org/forum/networking/41273-iptables-opening-port-certain-application-only.html](http://www.linuxforums.org/forum/networking/41273-iptables-opening-port-certain-application-only.html)

---

### Post by Hungry Man on 2012-07-15
> **Cheesehead said:**
> Allowing data through a firewall port is unrelated to which application is using that port. So nothing except your admin skill prevents an application from seizing and using (or abusing) a port.

Your underlying assumption is that applications are by default opaque, untrustworthy, ignore standards, and require direct supervision by the admin. That's not a valid assumption in this community - you have complete access to the application source code, applications are fully expected to behave politely and adhere to the standards (like port assignments), and users are expected to help make applications more stable and predictable.

Generally, if an application "grabs" port unexpectedly, file a bug report and don't use it - there are well-behaved alternatives.

If you really feel that a port is in danger of being fought over by multiple processes, then kill the undesired process. Or change it's config file to prevent the conflict.

Do you have reason to believe Firefox in behaving badly and stealing ports?

The dnsmasq documentation explains clearly which ports it needs and why. Dnsmasq provides many services...and some of those services require various ports.
If my concerns were limited to what legitimate applications should be doing I wouldn't bother with a Firewall at all. My concerns are with exploited applications doing what they shouldn't.

I'm not saying "Oh, Firefox is so bad" I'm saying that an exploited Firefox would be. If I thought all programs on my system were perfect and would always be perfect and could never behave otherwise I'd have no need for any security procedure at all.

@CHarlesA

I'll have a look at that - thank you.

---

### Post by Cavsfan on 2012-07-15
I found this the other day and set it up like he did in the video, not that I am worried too much about the need for a firewall on Ubuntu.

Uncomplicated Firewall UFW / GUFW Setup Guide for Ubuntu 

[http://youtu.be/zp0tg6popQ0](http://youtu.be/zp0tg6popQ0)

EDIT: Sorry I think I jumped in a bit prematurely. :oops:

---

### Post by Ms. Daisy on 2012-07-15
I think what you're talking about it [stateful packet inspection]("http://en.wikipedia.org/wiki/Stateful_firewall").  I only know about it as a concept, although I hope to implement it at some point. 

From my brief googling, it appears that some firewalls have stateful packet inspection.  I don't know if there are separate implementations or if it needs to be included in a firewall.

---

### Post by Hungry Man on 2012-07-15
I'm just wondering what the point is I guess. No two programs can use the same port at once without some fancy work.

But any program can use an unused port. So if program A, which never needs internet, gets hacked - it can connect out through any open port.

So what's the difference between 1,000 open ports or just a few?

I think I'm actually missing something.

---

### Post by Ms. Daisy on 2012-07-15
AFAIK, that's why we layer security.  The firewall controls which ports, things like apparmor control what calls what.

---

### Post by Hungry Man on 2012-07-15
Sure but it's kind of like if program A can exploit using File B and then you deny access to file B but leave an exact copy of File B in its access.

It can just use the other File B and do what it wants.

---

### Post by emiller12345 on 2012-07-15
> **Ms. Daisy said:**
> I think what you're talking about it [stateful packet inspection]("http://en.wikipedia.org/wiki/Stateful_firewall").  I only know about it as a concept, although I hope to implement it at some point. 


Check this out. You may be surprised to know that you are/might already doing so.
if you have a "-m state --state" command in any of your iptables then your using a very neat part of iptables

[http://en.wikipedia.org/wiki/Netfilter#Connection_Tracking](http://en.wikipedia.org/wiki/Netfilter#Connection_Tracking)

---

### Post by bodhi.zazen on 2012-07-16
> **Hungry Man said:**
> My question is... if I allow 7070 out what's stopping a program already on the system from using it?

Nothing. iptables does not work at the application level.

Best you can do with iptables is to add trusted applications, such as firefox, to a group, net ...

The allow only the group net out

```
sudo iptables -A OUTPUT -m owner --gid-owner net -j ACCEPT
sudo iptables -A OUTPUT -j REJECT
```

For an application firewall, see leopardflower

[http://leopardflower.sourceforge.net/](http://leopardflower.sourceforge.net/)

But honestly you are asking about secondary defense, you already have a cracked system or a cracked applications and IMO selinux/apparmor/grsecurity is a better option.

Problem with apparmor is it does not (yet) confine all applications.

Selinux is closer.

---

### Post by Hungry Man on 2012-07-16
SELinux is definitely closer if only because AppArmor is just unable to deal with something like Truecrypt etc.

The gid thing is really smart. I'm going to try that when I feel motivated.

---

