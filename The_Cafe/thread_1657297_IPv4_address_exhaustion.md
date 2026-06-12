---
title: "IPv4 address exhaustion?"
date: 2011-01-01
forum: The Cafe
---

### Post by Austin25 on 2011-01-01
I know the game plan is to replace IPv4 with IPv6. Any tips for preparation?

---

### Post by ki4jgt on 2011-01-01
> **Austin25 said:**
> I know the game plan is to replace IPv4 with IPv6. Any tips for preparation?

Know I don't know much about the situation but how would the end user have to adapt to that? Isn't this more of an ISP thing? and isn't Ubuntu already compatible with it?

---

### Post by handy on 2011-01-01
You could talk to your ISP, or look on their site?

Mine has a page on it, as they are using IPv6 & IPv4, & customers are able to use IPv6 if they so choose, though the setup is the full responsibility of the customer at the client side.

I found the following interesting from their site:

[i]**Security**

While the IPv6 protocol is not new, its global deployment is still at a relatively early stage.

It is important to appreciate that the use of the Internode IPv6 Tunnel Broker effectively bypasses any firewall/security features in your existing IPv4 router/firewall, by connecting your end system directly to the IPv6 Internet. IPv6 client system firewall software and security features are in relatively early stages of development for some end systems.

If you are not comfortable using IPv6 at this time, on this basis, please do not proceed. [/i]

---

### Post by handy on 2011-01-01
You may find this page from the IPCop forum of some interest too:

[http://www.ipcops.com/phpbb3/viewtopic.php?f=4&t=13349&hilit=ipv6](http://www.ipcops.com/phpbb3/viewtopic.php?f=4&t=13349&hilit=ipv6)

---

### Post by jrusso2 on 2011-01-01
Its all a conspiracy for the government to hook up to everyone's pc so they can listen in.

---

### Post by ki4jgt on 2011-01-01
> **jrusso2 said:**
> Its all a conspiracy for the government to hook up to everyone's pc so they can listen in.

And how is the government supposed to achieve this?? I've actually heard that one before, but isn't it still just a bunch of random combos of numbers except with letters thrown in now.

---

### Post by heldal on 2011-01-01
> **Austin25 said:**
> I know the game plan is to replace IPv4 with IPv6. Any tips for preparation?

That depends on who/what you are, and keep in mind that the existing IPv4 network isn't falling apart anytime soon.

If you're an end-user: don't worry, your network provider will advise if/when there's a reason to change or implement dual-stack. At some point in the future you may find new services which only can be used over IPv6, but media will inform you in time. The transition to ipv6 is only getting easier the longer you wait as the tools used to assist in transition improves.

If you're running an enterprise network: you'll probably have some older equipment that doesn't implement IPv6 and problably won't. Implement dual stack within your own network as soon as possible. Few such networks can switch to v6-only in the short term.

Service-providers (hosting or network operators) should already be prepared to support any combination of single-stack v4/6 and dual-stack. As a customer, investor or supplier I'd question the ability to survive in the market for service providers which are not already prepared for v6.

---

### Post by CharlesA on 2011-01-01
> **ki4jgt said:**
> And how is the government supposed to achieve this?? I've actually heard that one before, but isn't it still just a bunch of random combos of numbers except with letters thrown in now.

IPv6 is a 128-bit address written in hexadecimal, it's not completely random, as there are standards, but it's not exactly the same as IPv4.

The reason not everyone is connected "directly" to the internet (with a public IP) is that IPv4 has a small amount of addresses compared to IPv6. That's one of the main reasons NAT was created - to deal with the limitations of IPv4.
I'll be interesting to see how the conversion goes

---

### Post by RandomJoe on 2011-01-01
For grins, I set up a dual-stack system at home.  I have a commercial account here, so have a fixed IPv4 address.  It took about three or four different howtos and blogs to put all the pieces together, but once I had done it I thought it was really fairly simple now.

It would be nifty to try for pure IPv6 here, but I have some older devices (IP cameras, print server) that won't do 6 at all.  Dual-stack works, but Firefox and anything on OS X default to v4 addresses if both are available so I wind up very rarely using v6 at all.  Perhaps I'll split the old stuff off to its own network and give it a try anyway.

My ISP is doing trials with v6, I keep thinking about calling them and asking to take part.  Just haven't had the time lately, so I'm still running through Hurricane Electric's 6to4 tunnel.

I remember tinkering with IPv6 a decade ago, and am amazed to find just how little progress in adoption had been made so far.  I've even started asking the IT people I run across at customer sites (relatively few - my work is HVAC control systems, but I do work with IT at some point) if they have done anything.  Almost all have said no!

---

### Post by MisterGaribaldi on 2011-01-01
I think a lot of us (myself included) are perhaps guilty of thinking IPv4 has always been around and just appeared, whole-cloth, one day. The truth of the matter is that it took a long while for it to come about and, frankly, for *any* standard to be adopted. It's just that we all came late to the party ourselves.

I don't know if "they've been dragging their heels" or not with IPv6. I do know it is mission-critical and it *must* "just work" when we all do switch to it. That isn't the kind of thing you crank out overnight, and it has to be extensively tested first.

Frankly, if this technology is what the planet is going to come to depend on for everything from surfing the web to operating spacecraft and running/monitoring life-saving equipment, then as far as I'm concerned, let them take the time they need.

---

### Post by LowSky on 2011-01-01
wasn't this posted about before?

IPv6 has been "in use" for over a decade and yet its still a problem.

---

### Post by Austin25 on 2011-01-01
What about those of us who use Ubuntu Server [router configuration]("https://help.ubuntu.com/community/Router")? I understand dual-stack can be done, but I'm not entirely sure how...

---

### Post by ki4jgt on 2011-01-01
> **CharlesA said:**
> IPv6 is a 128-bit address written in hexadecimal, it's not completely random, as there are standards, but it's not exactly the same as IPv4.

The reason not everyone is connected "directly" to the internet (with a public IP) is that IPv4 has a small amount of addresses compared to IPv6. That's one of the main reasons NAT was created - to deal with the limitations of IPv4.
I'll be interesting to see how the conversion goes

I know it's not completely random (IPv4 isn't completely random, but it's going to behave the same right? (Besides providing more connections and allowing direct access to more people) It's still going to be using headers and route the data the same way??? or no??

---

### Post by CharlesA on 2011-01-02
> **ki4jgt said:**
> I know it's not completely random (IPv4 isn't completely random, but it's going to behave the same right? (Besides providing more connections and allowing direct access to more people) It's still going to be using headers and route the data the same way??? or no??
Yeah, there really shouldn't be any real difference to the end users.

---

