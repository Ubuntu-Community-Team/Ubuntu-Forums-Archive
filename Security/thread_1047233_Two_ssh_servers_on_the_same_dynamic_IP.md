---
title: "Two ssh servers on the same dynamic IP"
date: 2009-01-22
forum: Security
---

### Post by pentolino on 2009-01-22
Hello, 
I have two ssh servers on my lan and I would like to reach them from the internet; almost everything is set up ok, I forwarded two different ports on the router so that I can connect to both using one port for each; the IP is resolved through a dynamic dns so that I connect writing:

ssh -p <first_port> [email]username@domain.name[/email] (for the first one)
and 
ssh -p <second_port> [email]username@domain.name[/email] (for the second one).

My problem is that each time I shut down the router I get a new IP so ssh tells me it is adding the public key for server <new_ip>; this brings to a lot of entries in my known_hosts file, all for the same server. Also I am concerned for the fact I might fall into a man in the middle attack because having this message so often lower my alarm threshold.
I tried to let ssh store public keys by server name, but because the two server  have different key once I write the first key the second (of course) fails.
I have two ways of solving this: using the same server-key for both servers (is it advisable security wise?) or access the server through a different name (but I don't know how to let the system resolve something like another.domain.name to domain.name - changing /etc/hosts would not work because the ip changes every time).

Can anyone help?
Thanks a lot
Riccardo

---

### Post by hyper_ch on 2009-01-22
rent a static IP then... that's the only option...

---

### Post by Dr Small on 2009-01-22
You can setup a hostname at DynDNS.org which will point to your IP Address. Then you can configure your router (or one of the computers on the same network) to update the DynDNS IP when it changes. From here, you can just always connect to the hostname instead of the IP address. That may help.

---

### Post by yota on 2009-01-22
Ciao Riccardo,

as Dr Small suggested I'd use an account on dyndns which allows you to create up to 4 domains aliased to the same ip.

Said that you could connect to:

ssh -p port1 [email]username1@your.domain.of.choich[/email]e1

ssh -p port2 [email]username2@your.domain.of.choich[/email]e2

so that, from the ssh perspective, the server found at each domain is always the same, while still keeping the flexibility of using different keys/authentication methods and so on.

Hope it helps!

---

### Post by hyper_ch on 2009-01-22
well, even if you use dyndns the new ips after a change will still be added to the known_hosts...

---

### Post by pentolino on 2009-01-22
Thanks everyone for the replies.

@hyper_ch: I would like not to pay. It is a home server for private use after all, not a business

@dr_small: as hyper_ch pointed out this is the exact setup I am using and it has the problems I mentioned.

@yota: this should do the trick. I have to test it better but first it seems to work. Thank you very much.

Just a note: I posted here because I thought there may have been some "system" way to resolve this (like some setting in ssh server/client and/or dns). If there is such one I would be happy to hear it :-)

---

### Post by Dr Small on 2009-01-22
I guess the only other thing you could do on the client side, is set StrictHostChecking to "no", but you probably don't want to do that.

---

### Post by pentolino on 2009-01-22
I don't think so, becaue that would definitely lead to a possible man in the middle :-) Thanks anyway for your suggestion.
I will let you know if yota suggestion does what I need; I also thought about a script which periodically updates /etc/hosts entries (I can do it beacuse I have root access on the machine I'm connecting from), but I would use it as a last resort.

---

### Post by kevdog on 2009-01-22
Just a stupid question -- but why do you shut down your router?  I never do this, but I'm sure there is a reason for your setup.

---

### Post by pentolino on 2009-01-23
this is not a stupid question :-)
It is just that I don't need it on all the time and I switch it off every time I plan non to use it for several hours. 
I'm for energy saving (or at least not wasting), that's it :-)

---

### Post by kevdog on 2009-01-23
I have several home style routers (Linksys, Belkin) etc.  I wonder how much energy they actually waste?  I never turn them off.  In fact the only way to turn them off is unplugging the cord since no "off" button is supplied.

---

### Post by Dr Small on 2009-01-23
> **kevdog said:**
> I have several home style routers (Linksys, Belkin) etc.  I wonder how much energy they actually waste?  I never turn them off.  In fact the only way to turn them off is unplugging the cord since no "off" button is supplied.
I'm no electrician (My dad is, he's an electrical supervisior), but you can probably run the router through a test cord and use an ampmeter on it to see how many amps it is drawing.

---

### Post by pentolino on 2009-01-23
> **kevdog said:**
> I have several home style routers (Linksys, Belkin) etc.  I wonder how much energy they actually waste?  I never turn them off.  In fact the only way to turn them off is unplugging the cord since no "off" button is supplied.
Well, I have only one in fact and in doesn't have a button to shut it down. I never measured it but I guess it takes around 10 W or so; I know it is far less then an "old stile" lamp (40-60W) but I still think it is a waste to leave it on if not necessary.
I could probably leave it always on but I also have no guarantee that my provider won't ever reset my connection anyway...

---

