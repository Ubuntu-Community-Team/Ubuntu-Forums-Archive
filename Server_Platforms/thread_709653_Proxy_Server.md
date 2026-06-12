---
title: "Proxy Server"
date: 2008-02-27
forum: Server Platforms
---

### Post by spyke01 on 2008-02-27
Hi Guys,
i have a small network setup at my house, most of the systems are running Ubuntu in various forms and my machine is dual botting. I want to be able to setup another small system to act as a proxy so that when the other computers are using the internet or another application it records the ip of the computer and where they are going on the internet. The whole idea is to be kind of a watchdog over what my children are accessing on the internet. 

Is a proxy right for this? If so can you make any suggestions? Instead of a proxy should i just use a system as a default gateway between the LAN and the router, my only issue with this is that the equipment being used will probably be older.

---

### Post by HermanAB on 2008-02-27
You need Squid-cache with either SquidGuard or Dansguardian.

---

### Post by faulkes on 2008-02-27
> **spyke01 said:**
> Hi Guys,
I want to be able to setup another small system to act as a proxy so that when the other computers are using the internet or another application it records the ip of the computer and where they are going on the internet.


Squid is the generally accepted proxy server of the community, at least IMO.

```

aptitude search squid

```

> 
Is a proxy right for this? 

my only issue with this is that the equipment being used will probably be older.

Yes, a proxy is right for this.  Older hardware is not an issue, I currently
run squid on a g4 350mhz ppc w/ 512 mb of ram, it also acts as a fileserver
and does other tasks.

Squid also allows you to block urls, to limit bandwidth to certain sites and a
host of other features.  I can't say much for the configuration of it, as it is
somewhat cumbersome on the command line (I haven't used any of the 
cgi tools, so that may make life easier for you).

Faulkes

---

### Post by spyke01 on 2008-02-28
thanks guys ill look deeper into it, should i jus hang the proxy off the switch on my lan or position it between the lan and the router?

---

### Post by Cato2 on 2008-02-28
Have a look at [Dan's Guardian]("http://en.wikipedia.org/wiki/Dan's_Guardian") as well which is specifically for parental control/filtering.  However, Squid may be better as it's more about monitoring than control.

On where to put the proxy - what I would do is to set up the firewall so that the kids' PCs have no direct Internet access (simply set a static IP address for the proxy PC and allow only that address onto the Net, disallowing all others in your IP address range - set this up on the broadband router/firewall, not on the PCs).  Anything that is set up on a PC is really very easy for kids to bypass of course.

Once you have that, just configure the kids' PCs to point directly to the proxy.

Also be aware that there are sites out there that are specifically designed to help people get past proxies - e.g. you type in a URL to a web form - and that Google Images is also not really filterable.  

So it's best to have PCs in a shared, public area and just keep an eye on them.

---

### Post by faulkes on 2008-02-28
> **Cato2 said:**
> 
On where to put the proxy - what I would do is to set up the firewall so that the kids' PCs have no direct Internet access (simply set a static IP address for the proxy PC and allow only that address onto the Net, disallowing all others in your IP address range - set this up on the broadband router/firewall, not on the PCs).  Anything that is set up on a PC is really very easy for kids to bypass of course.

Once you have that, just configure the kids' PCs to point directly to the proxy.


In a linux FW NAT -> Router NAT -> Internet situation there are issues which
can arise, especially with port allocation, upnp (if it's used) and if the kids are
gaming.

Next, even with a FW NAT box, you would still need to force all web traffic
to the proxy, which is a bit more complex.

The easier approach would be to lock down the PC's for changing settings,
although it might be a bit more time intensive, think of it as spending time with
the kids ;)

> 
So it's best to have PCs in a shared, public area and just keep an eye on them.

Agreed, software can only do so much, nothing beats active healthy 
monitoring of the kids while they are on the computer.

Faulkes

---

### Post by HermanAB on 2008-02-28
If you set Squid up as a 'transparent proxy' then it is very difficult/impossible to bypass.  Another advantage is that then you don't need to do anything to the setup on any of the PCs.  

The transparency is done with a few iptables rules to forward port 80 to Squid.

---

