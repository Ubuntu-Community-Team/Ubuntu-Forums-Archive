---
title: "Shorewall, worth the time investment?"
date: 2016-02-08
forum: Security
---

### Post by Drenriza on 2016-02-08
As far as i understand, shorewall is a wrapper for iptables. But is it worth it to begin and learn how shorewall works and wrap rules instead
of using iptables directly? Would you deem it more 'secure' because shorewall is a wrapping master that makes complicated rules easy to implement and understand?

If you have experience with shorewall pls share :KS

Thanks on advance
Kind regards

---

### Post by The Cog on 2016-02-08
I have no experience of shorewall. However, I will venture the following opinions:

Most iptables wrappers are intended to make configuring simple-ish firewall requirements easier than doing so with iptables. Implementing simple rules with shorewall will probably be safer than doing it in iptables for a beginner, because of the possibility that an iptables beginner will forget/overlook/misunderstand something.


If you want to know how iptables works in detail, that's a good thing. A very good learning start would be to configure rules you understand with shorewall, then look at the iptables rules it produces. Its produced rules will be much more complicated than a straight-forward iptables implementation would be, because it will be setting up a framework for handing use cases that you don't need. But it will also possibly be doing things that you simply didn't realise were necesssary. Looking at a shorewall configuration (use **sudo iptables-save** or **sudo iptables -nvL** to list the rules) and understanding what it's doing and why will be a good iptables education.

I thought shorewall had stopped development some years ago - perhaps you should check on that. ufw is the recommended iptables wrapper for Ubuntu at the moment.

nftables is the new iptables. iptables commands still work but so do nftables commands. It seems from the little messing that I have done that both exist and can work at the same time, although I guess there is an opportunity for conflict if you try to configure both. The nftables website suggests to me that iptables is now a wrapper round nftables, but I notice that iptables configuration doesn't show up in an nftables rules listing. If you are looking deeply into iptables, you may want to also look at nftables.


You cannot mix a shorewall configuration with hand-written iptables rules without the risk of conflicts. In practice, you need to use either iptables or shorewall (or nftables).

---

### Post by Drenriza on 2016-02-19
Thanks for the reply!

Shorewall is still in development and frequently updated.

I have also read that nftables are going to replace iptables in the long run, but what does that exactly mean.
Is the development for iptables in 2016 stopped or is it still updated and patched? Or is it schedulated for later 2016 / 2017 that iptables no longer will be updated and patched in favor of nftables?

> Most iptables wrappers are intended to make configuring simple-ish  firewall requirements easier than doing so with iptables. Implementing  simple rules with shorewall will probably be safer than doing it in  iptables for a beginner, because of the possibility that an iptables  beginner will forget/overlook/misunderstand something.
And as an advanced iptables admin, would you still consider shorewall or another wrapper the way to go, or would you write the rules directly in iptables?

---

### Post by HermanAB on 2016-02-20
Howdy,

A firewall is mostly a Windows thing.

The last time I checked out Shorewall, it set up many complicated rules to protect a server against kernel network stack bugs that were already fixed a decade before.  

In my experience, if you use a modern kernel, then you can put a server directly on the internet with no iptables rules and it will be perfectly fine until its PSU eventually blows up.

So, you don't need a 'firewall'.  You may need a few routing rules for your server, but routing isn't a firewall.

---

### Post by bashiergui on 2016-02-20
> **HermanAB said:**
> A firewall is mostly a Windows thing.<snip>
So, you don't need a 'firewall'.  You may need a few routing rules for your server, but routing isn't a firewall.Categorically irresponsible misinformation. Sane people run firewalls on internet-facing servers regardless of the operating system. There are way too many automated scans of the internet and brute force attacks going at any given time to just let any old thing connect to every exposed port.

---

### Post by HermanAB on 2016-02-21
Nope.  Sane people do not expose every port.  If you run a server, then you should know exactly which ports have a listener and a firewall will  need to allow those through, so it won't actually do anything useful.

On a Windows server, there are a multitude of listeners, many of them undocumented and with no easy way to disable the listeners.  That is why Windows needs a firewall.

So a firewall is a band-aid used by admins who don't really know what their servers are doing.

---

### Post by kevdog on 2016-02-22
@HermanAB

So you're saying rate limiting an attempted incoming connection isn't a useful activity for a firewall?

---

### Post by Seb_Boffen on 2016-03-28
I have shorewall configured to work with fail2ban from the same blacklist file. Fail2ban add's ip addresses to the blacklist. Shorewall block's unwanted traffic perfectly.

Changed in fail2ban /etc/fail2ban/action.d/iptables-multiport.conf

actionban = iptables -I fail2ban-<name> 1 -s <ip> -j <blocktype>

to:

actionban = iptables -I fail2ban-<name> 1 -s <ip> -j <blocktype>
            # Add offenders to local blacklist, if not already there
            grep -q '<ip>' /etc/fail2ban/ip.blacklist; \
            if [ $? -eq 1 ]; \
            then echo '<ip>' >> /etc/fail2ban/ip.blacklist; \
            fi

So the blacklist only contains ipaddresses, this file can be used by shorewall as blacklist. A symlink /etc/shorewall/blacklist directs to /etc/fail2ban/ip.blacklist

also in /etc/fail2ban/jail.local

set:

 banaction = shorewall

---

