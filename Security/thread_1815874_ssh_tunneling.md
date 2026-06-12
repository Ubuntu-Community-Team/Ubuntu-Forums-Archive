---
title: "ssh tunneling"
date: 2011-08-01
forum: Security
---

### Post by therog726 on 2011-08-01
Hi,

I'm trying to set up ssh tunneling to encrypt my web browsing (for wireless hotspots etc) and I'm just testing it at home at the moment and I'm having some problems. I have a little experience now with linux, I'm mainly just new to the server stuff.

I've followed various guides in setting up a ssh server to tunnel through (like [this one, ]("http://www.searchmarked.com/ubuntu/how-to-surf-anonymously-using-an-ssh-tunnel-and-ubuntu.php")[this one, ]("http://omninoggin.com/blogging/how-to-encrypt-your-internet-traffic/") [or this one.]("http://lifehacker.com/237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy")) and that all seems to be ok.

So now for my questions:

[LIST]
If I tunnel from my laptop connected to my home network to the desktop (also on my home network) does that encrypt my traffic or not? Does the server need to be running on a different network (eg. at a friends place)?
[/LIST]

[LIST]
If I'm out, assuming the desktop running the ssh server is all running fine, how do I connect to it? I know I have to run something similar to:```
ssh -ND 9999 username@<ip address>
```
The ip address is: 192.1681.x but isn't that just the "internal" network address? How do I find out the "external" ip address?? Ie. to access from the outside world?
[/LIST]

That's all I can think of at the moment. Hope it all makes sense!

EDIT: Thought of some more questions:

[LIST]I read that Ubuntu basically has ssh access whenever it's turned on - Is having port 22 (or whatever) open all the time dangerous? If so, how can I make it more secure?
[/LIST]

[LIST]What is actually encrypted when I use an ssh tunnel? Is it all the packets I send via the network or my ip address or what?
[/LIST]

[LIST]My university allows ssh access - could I create a tunnel via that for the same effect? Would the fact that they have some web filtering cause problems?
[/LIST]

Thanks! :KS

---

### Post by Lars Noodén on 2011-08-01
> **therog726 said:**
> 
The ip address is: 192.1681.x but isn't that just the "internal" network address? How do I find out the "external" ip address?? Ie. to access from the outside world?


Yes. It is an internal address.  You'll have to set your router to forward the right port from the external address to the machine with the server.

---

### Post by therog726 on 2011-08-01
> **Lars Noodén said:**
> Yes. It is an internal address.  You'll have to set your router to forward the right port from the external address to the machine with the server.

Ok. And after I've done that, I connect to the ip address of the *router* (ie. my networks external address?) which forwards it to the server right? And I log in using an account on the server not the router?

---

### Post by Lars Noodén on 2011-08-01
> **therog726 said:**
> Ok. And after I've done that, I connect to the ip address of the *router* (ie. my networks external address?) which forwards it to the server right? And I log in using an account on the server not the router?

Yes.

---

### Post by bodhi.zazen on 2011-08-01
> **therog726 said:**
> 
EDIT: Thought of some more questions:

[LIST]I read that Ubuntu basically has ssh access whenever it's turned on - Is having port 22 (or whatever) open all the time dangerous? If so, how can I make it more secure?
[/LIST]

yes, opening a port for ssh is a security risk.

IMO you should use a virtual machine and secure your ssh server. This means use keys and disable passwords.

If you do not know how to secure a ssh server, you need to learn security before you go any further.

> [LIST]What is actually encrypted when I use an ssh tunnel? Is it all the packets I send via the network or my ip address or what?
[/LIST]

All traffic is encrypted.

> [LIST]My university allows ssh access - could I create a tunnel via that for the same effect? Would the fact that they have some web filtering cause problems?
[/LIST]

Thanks! :KS

See : [https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

Also, if you want filtering, use a proxy server such as privoxy or squid.

---

### Post by Lars Noodén on 2011-08-01
> **bodhi.zazen said:**
> yes, opening a port for ssh is a security risk.



Not a big one though, if you disable password authentication and use keys instead.  

Regarding virtualization, at best, that adds complexity:  

> 
"x86 virtualization is about basically placing another nearly full kernel, full of new bugs, on top of a nasty x86 architecture which barely has correct page protection. Then running your operating system on the other side of this brand new pile of ****. You are absolutely deluded, if not stupid, if you think that a worldwide collection of software engineers who can't write operating systems or applications without security holes, can then turn around and suddenly write virtualization layers without security holes."
-- [http://kerneltrap.org/OpenBSD/Virtualization_Security](http://kerneltrap.org/OpenBSD/Virtualization_Security)


---

### Post by bodhi.zazen on 2011-08-01
> **Lars Noodén said:**
> Not a big one though, if you disable password authentication and use keys instead.

Which is what I advised.

> Regarding virtualization, at best, that adds complexity:

Running a server (ssh, squid) is no more or less complex in a virtual machine then a physical machine, and the advantage is that the services are then isolated from the host, and can be isolated from the rest of the network.

IMO the security advantages outweigh the difficulty of setting up a VM.

---

### Post by therog726 on 2011-08-01
> **bodhi.zazen said:**
> yes, opening a port for ssh is a security risk.

If you do not know how to secure a ssh server, you need to learn security before you go any further.


So how would I go about learning security? I've had a look at this: [http://...openssh-server-best-practices]("http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html")
Is there anything else I should know?

> 
Also, if you want filtering, use a proxy server such as privoxy or squid.

Would privoxy do the same (from the end user point of view) as an ssh tunnel? (Ie. Encrypt my traffic?) I'm  basically after a way that I could safely do anything I want (Online banking, checking emails, etc) from a wireless hotspot.


Thanks for your help so far guys! =D>

---

### Post by bodhi.zazen on 2011-08-01
Encryption is manages by ssh and the ssh tunnel.

squid would speed things up a tad as it is a caching proxy. privoxy would add some privacy and some adblock.

---

