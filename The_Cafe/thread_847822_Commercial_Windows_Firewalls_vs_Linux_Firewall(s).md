---
title: "Commercial Windows Firewalls vs Linux Firewall(s)"
date: 2008-07-02
forum: The Cafe
---

### Post by kenweill on 2008-07-02
whats the difference between the two?

as i have noticed in linux firewalls, its more about on IP/port blocking.

but with commercial windows firewalls, there are alot of features.
trojan blocking capabilities, worm blocking capabilities, host intrusion detection/prevention, program/application controls, and much much more.

does that mean that those commercial windows firewalls works better than the one found on linux?

or exactly, whats the difference?
and also there's stealth mode..

---

### Post by pferpaddy on 2008-07-02
yeah but....linux dosnt need most of those features now im not saying that there no need for security because there is but if u like all thos features....run it in wine :P

---

### Post by Koori23 on 2008-07-02
It's sort of against the philosophy."Do one thing, do it well" is the UNIX/Linux philosophy. A firewall's purpose is to monitor and route network traffic. So, any of the GUI front ends you have in Linux merely configure IPTables, I would go as far as to say it's more efficent.

You have programs like chrootkit, rkhunter, clamav etc.. to check for nasties on your system.

I think of it this way. Say you're building a battleship. You have all sorts of flashy long range weapons and neat, easy to use push button navigation systems. Unfortunately, the hull is made out of tin foil. You can destroy targets from 200 miles out with pinpoint accuracy but somebody can swim up to the ship with a No.2 pencil and poke a hole in it and sink the whole damn thing. That's Windows.

Linux would rather fix the root of a problem than rely on third party apps to fix fundamental flaws. Besides, half that crap you listed as a "feature" won't work anyway initially. You'd have to see it in the wild first, create a signature to detect it, user's would have to update for it.. Then and only then would you be able to protect yourself.

Me personally, I'd rather save my 20-30 meg of resident ram doing something useful. I'll check my logs in firestarter on occasion, run chrootkit, "sudo aptitude update" once a day.. A much simplier process in my mind.

Rant over.

---

### Post by stmiller on 2008-07-02
Software firewalls are only as safe as the operating system they are running on. So if there is a security hole in the windows OS (which is ongoing of course) then you are vulnerable.

The dedicated hardware firewalls you can get are actually just a small dedicated Linux box running iptables, for the most part.

I'm skeptical of these 'commercial' software firewalls you are reading about for Windows. Sounds like a lot of carefully worded marketing.

---

### Post by pferpaddy on 2008-07-02
I'm skeptical of these 'commercial' software firewalls you are reading about for Windows. Sounds like a lot of carefully worded marketing.[/QUOTE]

i second that commercial software vendors are in it for one thing and one thing only...money

---

### Post by original_jamingrit on 2008-07-03
A firewall is a firewall is a firewall.  Any additional features are just probably more for working around universal plug and play.  Universal plug and play, in general, is not cool for the security-minded computer user.   Besides, any additional features a "firewall" has could potentially become an attack vector.  In general, a NAT router should be good, although there are things to be said about a software firewall that can monitor and alert you to outbound traffic as well.

---

### Post by macogw on 2008-07-03
> **original_jamingrit said:**
> In general, a NAT router should be good,[quote]
Myth.  Jumping NAT isn't all that hard.
[quote]although there are things to be said about a software firewall that can monitor and alert you to outbound traffic as well.
Yes, blocking outbound is good.  No phoning home.  No letting software you accidentally OK'd that you shouldn't have try to spread itself or send back spy info or anything like that.

---

### Post by LaRoza on 2008-07-03
> **kenweill said:**
> whats the difference between the two?

as i have noticed in linux firewalls, its more about on IP/port blocking.

but with commercial windows firewalls, there are alot of features.
trojan blocking capabilities, worm blocking capabilities, host intrusion detection/prevention, program/application controls, and much much more.

does that mean that those commercial windows firewalls works better than the one found on linux?


Windows has open ports, a weak security model, and will just about broadcast anything on the internet.

Linux is designed differently, with networking in mind, of course there are differences in tools.

---

### Post by kevdog on 2008-07-03
Windows has open ports, but by default so does Linux -- in fact all of Linux's ports (INPUT, OUTPUT, FORWARD) or open by default.  So I don't get how its any different?

---

### Post by LaRoza on 2008-07-03
> **kevdog said:**
> Windows has open ports, but by default so does Linux -- in fact all of Linux's ports (INPUT, OUTPUT, FORWARD) or open by default.  So I don't get how its any different?

Forget to mention, Windows has things listening by default.

---

### Post by the yawner on 2008-07-03
> **kevdog said:**
> Windows has open ports, but by default so does Linux -- in fact all of Linux's ports (INPUT, OUTPUT, FORWARD) or open by default.  So I don't get how its any different?

And Linux only listens if a corresponding application is running for the port.

---

### Post by original_jamingrit on 2008-07-03
> **macogw said:**
> Myth.  Jumping NAT isn't all that hard.
I just did some googling and found that you may have something there.  Apparently some NAT routers automagically replace commonly-used port numbers with a random port from a range elsewhere, so an attacker could brute-force guess an open port in that range directly.  This article went on to expound on some more failings, but I'm pretty sure if you are willing to spend the time to manually configure it and turn off that automagic crap, (and also the obvious stuff like change the passwords and don't DMZ something that's not a gaming server, and definitely kill UPnP), then a NAT should still be good enough.

> Yes, blocking outbound is good.  No phoning home.  No letting software you accidentally OK'd that you shouldn't have try to spread itself or send back spy info or anything like that.
I actually had a buddy who's a windows fan (not an MS fan but a windows fan) who was trying to get his pirated copy of visual studio to run, while connected to the Internet.  I just suggested he block it on the firewall, so it couldn't do its 'are you a pirate' call home.  It worked, go figure.

---

### Post by kenweill on 2008-07-03
i've never heared of such HIPS in linux firewalls.
is that windows specific feature?

and what about those stealth mode. is that possible in linux? coz i was planning to make Ubuntu as a gateway. Sharing internet connection to other PCs(windows PCs). And i wanted that stealth mode feature of commercial windows firewalls to implement in linux. 

What does that actually do? technically.
as what i've understand, it makes you invisible from the internet. you can surf the web to the internet but invisible from the internet. invisible from ping. invisible from port scan. i've read about those OPEN, CLOSED, and STEALTH ports. i wonder if it's possible to stealth all ports in linux while other PCs in the network can still browse the internet.

is that possible in linux?
i've tried some of those stealth mode in windows, but doint so, makes my workstations as well to not function. something like, can't communicate with the gateway.

how do i make stealth mode in linux while still, other PCs(in the network) can still browse the internet? is that possible?

---

### Post by macogw on 2008-07-04
> **kenweill said:**
> i've never heared of such HIPS in linux firewalls.
is that windows specific feature?

and what about those stealth mode. is that possible in linux? coz i was planning to make Ubuntu as a gateway. Sharing internet connection to other PCs(windows PCs). And i wanted that stealth mode feature of commercial windows firewalls to implement in linux. 

What does that actually do? technically.
as what i've understand, it makes you invisible from the internet. you can surf the web to the internet but invisible from the internet. invisible from ping. invisible from port scan. i've read about those OPEN, CLOSED, and STEALTH ports. i wonder if it's possible to stealth all ports in linux while other PCs in the network can still browse the internet.

is that possible in linux?
i've tried some of those stealth mode in windows, but doint so, makes my workstations as well to not function. something like, can't communicate with the gateway.

how do i make stealth mode in linux while still, other PCs(in the network) can still browse the internet? is that possible?

A port has 3 modes, yes, but they aren't "open" "close" "stealth." They are "accept" "reject" and "drop."  Drop is probably what they mean by stealth, because it doesn't send a reject packet.  It just doesn't respond, so if they know you're there, that might buy you time in the form of timeouts, and if they don't know you're there, it won't reveal that you are.

---

### Post by Koori23 on 2008-07-13
Just as Mac said.. "Accept, Request or Drop" are the only three options for a port to chose from. That in itself is the paradox of one specific port. Port 113. Any time you access your email or hit a webpage using another port.. That information get's sent to Port 113 for identification/authentication. It's sorta tricky to "stealth" a port when it has to be verified first. If you ever check your logs if you run a webserver or something you'll see 10 billion IDENT requests.

---

