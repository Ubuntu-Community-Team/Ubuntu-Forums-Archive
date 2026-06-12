---
title: "I Have a Router and Two Computers.  What Geeky, Fun Things are Possible?"
date: 2006-11-12
forum: The Cafe
---

### Post by SendDerek on 2006-11-12
Just like the title says...

I have a router and two computers and I want to know how to take full advantage of them.  If there are any fun, geeky things I can do with them besides hook two computers up to a network to share files and internet access, please let me know!

What setups are possible?
Anything to make 'em faster?
How to make things more reliable?
What is port forwarding?
Is there any way to get around websense blocking?

Anything...

If you know of a trick and tips for owning a router, please share!

(BTW: I own a Linksys WRT54GC and have no static IP address)

---

### Post by DaveBorealis on 2006-11-12
If you have static IP addresses and can get a spare one, setting one up as a web server (apache, mysql, jsp, php, cgi, etc.) will keep you playing for decades to come!

Even if the IP's are assigned with DHCP, if they don't change often and you can get an extra, you can still set up a web server.

Either way, you won't be able to list it in DNS, you'll just have to have people use the IP address to reach it.

This should be a fun thread to follow!
Dave

---

### Post by deepwave on 2006-11-12
If its geeky you want.  Then setup a two node Beowulf cluster. ;-)

Pretty much anything you can do with a router can do without.  Except networking two computers together.

I assume websence is some sort of proxy.  You can fool the proxy (don't try this at work though) by tunneling data from one port through another.  Couple that with ssh, and you bypass the proxy.  Not sure of how to do it exactly.

Web port forwarding means making a different port number communicate traffic for the original port.  Example lets say I have a game server that normally runs on 2345 but for whatever reason I want it to use 5432 instead.  I can make port 5432 behave like 2345.

---

### Post by Dual Cortex on 2006-11-12
> **DaveBorealis said:**
> If you have static IP addresses and can get a spare one, setting one up as a web server (apache, mysql, jsp, php, cgi, etc.) will keep you playing for decades to come!

Even if the IP's are assigned with DHCP, if they don't change often and you can get an extra, you can still set up a web server.

Either way, you won't be able to list it in DNS, you'll just have to have people use the IP address to reach it.

This should be a fun thread to follow!
Dave

:confused: 
He could use No-IP's Linux client.

---

### Post by DaveBorealis on 2006-11-12
> **Dual Cortex said:**
> :confused: 
He could use No-IP's Linux client.

Hello,

I just took a look at their site, but it was a quick peek.  How will this allow someone with a DHCP-assigned IP to link it via DNS to a domain name?  What happens when the IP changes?

Dave

---

### Post by Peepsalot on 2006-11-12
If each computer has it's own monitor and they are in the same room, synergy could be a nice thing to play with.
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)
I've never had a use for it though since I share a single monitor over KVM.

---

### Post by Dual Cortex on 2006-11-12
> **DaveBorealis said:**
> Hello,

I just took a look at their site, but it was a quick peek.  How will this allow someone with a DHCP-assigned IP to link it via DNS to a domain name?  What happens when the IP changes?

Dave

You sign up for their DNS service, the No-IP client detects any IP changes and updates it to their system - result is you can access your computer anytime through an adress like johnsmith.no-ip.info (or you could use your own domain name)

---

### Post by Sam on 2006-11-12
Some ideas...
[list][*]Web server
[*]Mail server (if you own a domain name)
[*]mldonkey (for 24/24 downloads)
[*]file server (stores your movie/music collection to get it available on your LAN)[/list]

---

### Post by aeon on 2006-11-12
> **DaveBorealis said:**
> If you have static IP addresses and can get a spare one, setting one up as a web server (apache, mysql, jsp, php, cgi, etc.) will keep you playing for decades to come!

Even if the IP's are assigned with DHCP, if they don't change often and you can get an extra, you can still set up a web server.

Either way, you won't be able to list it in DNS, you'll just have to have people use the IP address to reach it.

This should be a fun thread to follow!
Dave

Try [DynDNS]("http://www.dyndns.com") , they have a lot of free domains you can use.. I use it myself and use ddclient to automagically update my IP when it changes. (a script checks the ip every n seconds and updates it to the dyndns server if it changes)

I currently have one box set upp as a router/webserver/fileserver and my main box sitting behind that one, nothin fancy though, the setup is pretty straightforward.. ;)

---

### Post by deanlinkous on 2006-11-12
simple one.
vnc from A to B and while in that session open a vnc connection from B back to A...

---

### Post by SendDerek on 2006-11-12
> **Dual Cortex said:**
> :confused: 
He could use No-IP's Linux client.

I'm checking out [http://www.no-ip.com services]("http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html") and this sounds like pretty cools stuff here.  Remote login is something I have ALWAYS wanted and I'd be more than interested to get something like this setup.

I've registered an account and I'll have to do some more reading to figure out what exactly it is I'm doing. :D 


Thanks for all the replys!  This is great... I'm learning lots already.

Keep 'em comming!

---

### Post by DaveBorealis on 2006-11-12
> **SendDerek said:**
> I've registered an account and I'll have to do some more reading to figure out what exactly it is I'm doing.

Did you also see this on their site?  Looks like a nice short but good intro.
[http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html]("http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html")

---

### Post by SendDerek on 2006-11-12
> **DaveBorealis said:**
> Did you also see this on their site?  Looks like a nice short but good intro.
[http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html]("http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html")

Yeah, actually that was the first page I found. lol.  I tried to follow it, but I found out that no-ip is included in the repositories, so I installed it that way and tried this command:

sudo no-ip -C

but I'm getting this error message:

Connect to dynupdate.no-ip.com timed out
Network must be operational to create configfile. Ending!

I'm not sure what to do now, so I'm reading up on any information to get it resolved.

---

### Post by SendDerek on 2006-11-12
Thanks to some of your suggestions, I was able to complete something geeky tonight!  Setting up Remote Desktop with VNC and Dyndns.  I tried no-ip, but it was easier with dyndns.

This stuff is cool!  Keep the ideas comming!

BTW:  I found a suggestion to remote login to 127.0.0.1 using vnc viewer... what a trip! lol

---

### Post by dbbolton on 2006-11-12
> **SendDerek said:**
> Just like the title says...

I have a router and two computers and I want to know how to take full advantage of them.  If there are any fun, geeky things I can do with them besides hook two computers up to a network to share files and internet access, please let me know!

What setups are possible?
Anything to make 'em faster?
How to make things more reliable?
What is port forwarding?
Is there any way to get around websense blocking?

Anything...

If you know of a trick and tips for owning a router, please share!

(BTW: I own a Linksys WRT54GC and have no static IP address)
same here. and it's pretty nice that i don't have out of bed to tell my brother to do something for me.

as far as being nerdy (not pathetic, like me) goes, i think you can type in your router's default IP address in a browser and change the administrative settings (eg, make it static). i have the same router. it gave me a hell of a time with installation.

---

### Post by SendDerek on 2006-11-14
Welp, now I'm having issues getting remotely connected.  I don't think I have port forwarding setup properly.  I have opened another thread on that one though [here]("http://www.ubuntuforums.org/showthread.php?t=299608")

Any other fun geeky things to do?

---

