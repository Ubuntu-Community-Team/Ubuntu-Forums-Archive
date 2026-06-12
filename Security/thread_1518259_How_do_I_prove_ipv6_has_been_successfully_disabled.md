---
title: "How do I prove ipv6 has been successfully disabled"
date: 2010-06-26
forum: Security
---

### Post by Ulysses_ on 2010-06-26
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro.  Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more.  Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

---

### Post by insane_alien on 2010-06-26
try to ping the home 1pv6 address ( ::1/128 )

---

### Post by Ulysses_ on 2010-06-26
> **insane_alien said:**
> try to ping the home 1pv6 address ( ::1/128 )

You mean the following command?  

ping ::1/128

  It says ''ping: unknown host ::1/128''.    

This is on a default linux mint install.  Is ipv6 likely to be enabled in the default install of ubuntu and derivatives?

---

### Post by teejaybee on 2010-06-26
```
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
```They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

```
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

---

### Post by rookcifer on 2010-06-26
To check if IPv6 is enabled, just simply use netstat:

```
netstat -tlv
```

If you see any "tcp6" entries, then IPv6 is not disabled.

---

### Post by Rubi1200 on 2010-06-27
If someone could answer the following question, I would be very grateful.

What is the implication of ipv6 being enabled? I checked using the commands provided by teejaybee and rookcifer and it appears that it is enabled by default on my computer.

Any insights?

Thanks in advance.

---

### Post by teejaybee on 2010-06-27
One that I can think of, and there is probably more, is that you are usually not looking for ipv6 traffic, so if you have interfaces listening for ipv6 and they are assigned an address (I am not up to speed on the protocol itself, eg. what are reserved private network addresses under ipv6 etc - when I had ipv6 enabled my eth0 had an ipv6 address even though my routers dhcp server wasn't configured to hand one out, whether that address could be communicated with is another matter) there could be either communication happening there without your knowledge or if a machine gets compromised they could use ipv6 to hide whats going on from you... could possibly be a non-issue someone who knows about how ipv6 is implemented under ubuntu may rule this out.

The second part of this theory that doesn't require a tinfoil hat could be that your firewall configuration is only set up for ipv4, so if ipv6 is enabled and someone can somehow communicate via ipv6 to that machine then there is the possibility that any ports, services, etc. you have blocked with your firewall configuration could be left open when using ipv6. This is fixed by blocking all ipv6 traffic on your firewall as part of a default ruleset.

Hopefully there may be some here with a thorough understanding of ipv6 and can chime in...

---

### Post by Rubi1200 on 2010-06-27
Thanks teejaybee.

It seems that cups, the only service listed as listening, is on both ipv4 and ipv6.

If I disable ipv6 via sysctl, as you mentioned above, and I run into problems can I then just remove the entries and be "back to normal"?

My default Desktop installation sits behind a wireless router with firewall enabled. I do not have ufw enabled (if this makes a difference).

By the way, when I run
```
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
```it returns 5 zeros, but your additions to the file only mention 3 things.

Additional question:

I am definitely in the "dark" somewhat about Internet protocols, but a cursory search on Google suggests that ipv6 is not a major issue on Ubuntu UNLESS one is experiencing connectivity issues, in which case it is recommended to disable it. Any thoughts about this?

---

### Post by teejaybee on 2010-06-27
> If I disable ipv6 via sysctl, as you mentioned above, and I run into  problems can I then just remove the entries and be "back to normal"?Yes - and if you don't want to reboot after you've removed the lines from sysctl.conf, simply run sysctl manually for all the correct entries.

If you don't print from that machine, i'd disable CUPS from starting on boot - it has a bad history of vulnerabilities. Since you're behind NAT you should be pretty safe though...

(Edit: didn't see your update)

If you change to /proc/sys/net/ipv6/conf you'll see it lists all your network interfaces there. It will be more or less depending on how many you have.

IPV6 probably isn't going to cause you any problems. You can probably run it safely and never have any issues. I like to run a pretty tight ship on my home gear because I don't want my stuff compromised and someone being able to gather all sorts of information to do stuff against me, whether that is draining my bank accounts or otherwise. You decide whether its going to fit in your overall strategy for securing your own network/machine/whatever. For me, disabling a network feature I don't use is the same as disabling a service I don't use. For example, CUPS :)
[FONT=monospace][/FONT]

---

### Post by Rubi1200 on 2010-06-27
Thanks teejaybee, I appreciate your input and taking time to answer my questions.

:-)

---

### Post by Ulysses_ on 2010-06-27
Thanks. A related question: when ipv6 is enabled, how do I prove it is being used by a web site?

---

### Post by The Cog on 2010-06-27
You almost certainly don't have any IPv6 connectivity out of your home (or work, come to that). You can try it by browsing to [http://ipv6.google.com](http://ipv6.google.com) - that site doesn't have an IPv4 address, so if you can reach it, you have IPv6 connectivity.

I believe that IPv6 is going to come to all, but it is taking a long time and the ISPs are really dragging their feet. Operating systems now all have ipv6 support, so do modern browsers. Home routers generally don't, and ISPs generally don't. 

The only issue you might have with IPv6 being enabled on your PC right now is that a modern browser will try to resolve a URL to an IPv6 address and only when that fails will try to use IPv4. That isn't normally an issue, but some ISPs have broken DNS servers that don't answer queries for IPv6 addresses. If you use one of those broken ISPs, there will be a pause when you try and connect while the IPv6 query from the browser times out. In that instance, disabling IPv6 on the PC will prevent the IPv6 connection attempt and remove the timout delay.

You can check if you have IPv6 support enabled by pinging your loopback address: (**ping6 ::1** will succeed if IPv6 is functioning) or running the command **ifconfig** and looking to see if there are any **inet6 addr** lines.

If you do have IPv6 connectivity and you run a firewall, don't forget to firewall IPv6 as well as IPv4.

---

### Post by axeboy on 2011-03-15
> **Rubi1200 said:**
> Thanks teejaybee, I appreciate your input and taking time to answer my questions.

:-)


how to enable IPV6?
on ubuntu 10.0.4  using lighttpd

---

