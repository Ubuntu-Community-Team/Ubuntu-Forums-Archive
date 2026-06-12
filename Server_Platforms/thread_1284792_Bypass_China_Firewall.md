---
title: "Bypass China Firewall?"
date: 2009-10-07
forum: Server Platforms
---

### Post by tjhart85 on 2009-10-07
OK,

Here's what I'm trying to do.  If anyone has a guide or anything they can point me at, that would be great!

A friend of mine is in China on a study-abroad program.  He's been using TOR to bypass the firewall so he can access facebook & stuff, but they recently blocked that as well.

What I would like to do is set up a proxy for him, so he can access these pages using my internet connection.

I have created a user on my Ubuntu 9.04 Server for him and he can SSH in, unfortunately, I'm kind of stumped.

I have previously attempted to set up a squid proxy, but it didn't work (I'm unsure what went wrong), I just uninstalled it since I obviously hadn't set it up properly.

What I attempted to do was have him access my server and forward port 3128 through it (via putty) & have Firefox use that as a SOCKS proxy on port 3128.  

It didn't work.

As I said, anyone got a guide to do this?  I'm sure it's gotta be asked for a lot (most likely people trying to get around their work firewall), but I cannot find anything that functions as a guide.

---

### Post by ShapeShiftme on 2009-10-07
The idea you have is a kinda good one. However there are may ways to do this. 

Is your fried using windows or linux. And im agthering you are using ubuntu.

Well without wrtitng a tuturial you where on the right track with the squid proxy. But you probebly didnt have the correct routing rules. assigned.

I have set up many firewall (I persoannly use Shorewall) With that i run squid. Using shorewall i set up the routing to squid for access.

But remember the problem with this setup unless you lock down the interface for connection. Youwill allow "anybody" to use your proxy. 


And that would not be your best solution.
Please let me know if you want to know more on this setup then ill try help where i can
Regards

---

### Post by dragos2 on 2009-10-07
Try varnish, maybe you'll have better luck. Also enable encryption on the tunnel.

Also Dante [http://www.inet.no/dante/](http://www.inet.no/dante/)

---

### Post by alex.burlacu on 2009-10-07
Or maybe it will be a good chance to setup a vpn for him on your computer, so he can access it over ppoe without having any operating system related issues.

---

### Post by tjhart85 on 2009-10-07
He is Windows.

Hm...I was under the impression that he would have to SSH into the Ubuntu server and forward ports through it using a tunnel in order to be able to access the proxy.  You're saying that this isn't the case?

Is there any way to allow only a certain MAC address in?  Or password protect it?

I'll look into Shorewall, Varnish & Dante.  Thanks for the help guys!

---

### Post by koenn on 2009-10-07
if you're running a squid proxy, all he'd have to do is configure his browser to use that proxy. Squid listens on port 3128 by default, but you can change that if need be (eg to port 80 to make his traffic look like ordinary web traffic)

This, of course, requires that your proxy is accessible from the internet. Assuming you use a router with NAT (s most people do), you'd have to configure "portforwarding" on that router. 

As ShapeShiftme mentions, you'd probably also want to limit access to your proxy, or you'll end up proxying for half of the world. You can do that with firewalls, or access control in squid. a.o.

You and your friend should also find out about the legalities regarding bypassing the Great Firewall.

---

### Post by Jekshadow on 2009-10-09
The nice thing is that ssh-server can act like a socks proxy server without anything else.

Install ssh-server on the proxy box then set him up an account (adduser [username]) and tell him to use: 
```
ssh -D 7070 [his username]@[your ip address]
```
on a *nix terminal.

If it does not work, go to 192.168.1.1 or 10.0.0.1 to get to your router's control panel. 

Now find your router and follow the instructions here to forward port 22 to your server box. [http://portforward.com/](http://portforward.com/)

If it did work, tell him to open up Firefox and have his computer use the socks proxy localhost:7070. He will only be able to connect when he is signed into your server via the above command. And only people who have an account will be able to do this.

---

### Post by koenn on 2009-10-09
> **Jekshadow said:**
> ..  and tell him to use: 
```
ssh -D 7070 [his username]@[your ip address]
```
on a *nix terminal.
.... and have his computer use the socks proxy localhost:7070 
... 
That would work, but you left out the instructions on how to set this up on a Windows system, eg through putty

---

### Post by ugm6hr on 2009-10-09
I have temporarily closed this thread while I get clarification regarding the forum stance on bypassing the China firewall.

---

