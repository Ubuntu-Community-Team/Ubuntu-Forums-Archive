---
title: "how do i stealth my ports?"
date: 2008-05-04
forum: Security
---

### Post by waggingwabbit on 2008-05-04
how do i stealth my ports? the only port thats stealthed when i run [http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) is my netbios port. how do i get all the other ports to be stealthed?

---

### Post by Blakefreak on 2008-05-04
Dunno, mine are all stealthed.

---

### Post by The Cog on 2008-05-05
I'm not too impressed with that hackertwatch web site. It just failed to notice my open SSH port.

---

### Post by stmurray on 2008-05-05
Install a firewall (I recommend firestarter).  By default it will "drop silently" all packets that it doesn't allow, thus making the service "stealth".  Just make sure you allow any services you do need in the "Inbound traffic policy" of the rules, otherwise they will not work.

---

### Post by rmtatum on 2008-05-06
I prefer using Steve Gibson's ShieldsUP!

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by lespaul_rentals on 2008-05-06
> **waggingwabbit said:**
> how do i stealth my ports? the only port thats stealthed when i run [http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) is my netbios port. how do i get all the other ports to be stealthed?

Are you behind a router/NAT?

---

### Post by Oldsoldier2003 on 2008-05-06
> **rmtatum said:**
> I prefer using Steve Gibson's ShieldsUP!

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

pfft. another semi useless marketing scare tactic. All that does is check your router/gateway for open ports it doesn't mean that you are at risk at all. in fact it means nothing about your machine if you have a nat router/gateway unless you forward the ports to your box.

the only time either of these sites can even come close to being useful is if you have a direct connection to the internet with no intervening NAT devices or router.

---

### Post by The Tronyx on 2008-05-06
> **Oldsoldier2003 said:**
> pfft. another semi useless marketing scare tactic. All that does is check your router/gateway for open ports it doesn't mean that you are at risk at all. in fact it means nothing about your machine if you have a nat router/gateway unless you forward the ports to your box.

the only time either of these sites can even come close to being useful is if you have a direct connection to the internet with no intervening NAT devices or router.

Amen.  I wish I had a response with more content but unfortunately Oldsoldier2003 hit the nail on the head.:guitar:

---

### Post by lespaul_rentals on 2008-05-07
> **Oldsoldier2003 said:**
> pfft. another semi useless marketing scare tactic. All that does is check your router/gateway for open ports it doesn't mean that you are at risk at all. in fact it means nothing about your machine if you have a nat router/gateway unless you forward the ports to your box.

the only time either of these sites can even come close to being useful is if you have a direct connection to the internet with no intervening NAT devices or router.

Rubbish.  While part of what you say is true, Shields Up! is a great tool for a novice user to check his/her port security.  If one of the ports is open, it must lead somewhere because a service is listening.  Maybe someone's son set his computer as the DMZ host to do some gaming, and due to DHCP IP address assignments the family computer with NetBIOS and Remote Desktop running became exposed to the network.  I myself have used it as a quick port scan to test if my router is forwarding FTP and SSH ports correctly.

---

### Post by The Tronyx on 2008-05-07
> **lespaul_rentals said:**
> Rubbish.  While part of what you say is true, Shields Up! is a great tool for a novice user to check his/her port security.  If one of the ports is open, it must lead somewhere because a service is listening.  Maybe someone's son set his computer as the DMZ host to do some gaming, and due to DHCP IP address assignments the family computer with NetBIOS and Remote Desktop running became exposed to the network.  I myself have used it as a quick port scan to test if my router is forwarding FTP and SSH ports correctly.

Does it need to lead somewhere?  My router uses NAT, if I open port 22 on my router, but there is no active SSH service on port 22 (or any other service using port 22 for that matter) it will say port 22 is open/closed but not stealthed.

---

### Post by lespaul_rentals on 2008-05-08
> **2point0 said:**
> Does it need to lead somewhere?  My router uses NAT, if I open port 22 on my router, but there is no active SSH service on port 22 (or any other service using port 22 for that matter) it will say port 22 is open/closed but not stealthed.

It really does no good to "open" a port on your router.  By "open" I assume you mean "forward."  If you have forwarded port 22 to your Linux server running an SSH daemon, Shields Up! will pick it up.  However, if you have forwarded the port to a non-existent IP address, it will show up as closed.  I have never had Shields Up! tell me that a port with no service was open.

I really don't understand what everyone's problem with Shields Up! is.  It's nothing more than a basic port scan for novices to test their router security.  They even give you tips on how to protect your network.  Someone earlier in the thread accused GRC of using Shields Up! as a sales gimmick or something; however, they offer much support for free and even have other great tools such as SpinRite.

---

