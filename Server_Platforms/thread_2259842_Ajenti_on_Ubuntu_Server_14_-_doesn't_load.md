---
title: "Ajenti on Ubuntu Server 14 - doesn't load"
date: 2015-01-07
forum: Server Platforms
---

### Post by bizres on 2015-01-07
Hello,

I've got this Ubuntu server 14 instance on AWS EC3 and have followed instructions at [http://ubuntuserverguide.com/2013/12/how-to-install-ajenti-in-ubuntu-server-13-10-13-04-12-10-12-04.html](http://ubuntuserverguide.com/2013/12/how-to-install-ajenti-in-ubuntu-server-13-10-13-04-12-10-12-04.html) to setup Ajenti.

However, while the install seems to complete successfully, going to [https://(my-ip-number):8000](https://(my-ip-number):8000) doesn't reveal anything - just stays at "connecting".

Would really appreciate some help on this, pls.

---

### Post by volkswagner on 2015-01-07
I believe Amazon AWS is firewall enabled. 

Did you open port 8000 in your Amazon control panel?

For the least vulnerable firewall hole, I suggest only opening the port to your home ip address if possible.

---

### Post by bizres on 2015-01-08
> **volkswagner said:**
> I believe Amazon AWS is firewall enabled. 

Did you open port 8000 in your Amazon control panel?
Thanks Volkswagner. Re-checked at amazon and noticed I had opened port 800 instead of 8000. Rectified and works well. Thanks.

> **volkswagner said:**
> For the least vulnerable firewall hole, I suggest only opening the port to your home ip address if possible.In my case this wouldn't be possible as I'm behind ISP NAT.

Once again, Thanks very much.

---

### Post by volkswagner on 2015-01-08
If your ISP provider doesn't change your IP often, this should be no problem. Even though you're behind NAT, your AWS instance
will see your public ip, not your private ip. If you have dial up (public ip changes often) or DSL (ip changes occasionally) this setup
may be inconvenient, as you'd have to change the firewall rule often.  In my area with Time Warner Cable, my public ip address
only changes if I replace my router, even though it's considered dynamic. 

I had to search ISP NAT. I assume this means "[Carrier Grade NAT]("http://en.wikipedia.org/wiki/Carrier-grade_NAT")". If
that's the case, all I can say is yuck.  What provider is forcing you into that ugliness?

---

### Post by bizres on 2015-01-08
ISP's in our region are pretty stingy.
They put >100 users behind a singe public IP - all we know as our IP address is 192.168.0.xxx
and they want to charge an arm and a leg for giving a public IP address.

Checking out on "whatismyip.com" is going to reveal what is the same IP number for >100 other user:lolflag:

---

