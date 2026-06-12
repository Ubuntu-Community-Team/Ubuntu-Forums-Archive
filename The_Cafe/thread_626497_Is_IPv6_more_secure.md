---
title: "Is IPv6 more secure?"
date: 2007-11-29
forum: The Cafe
---

### Post by RAV TUX on 2007-11-29
Is IPv6 more secure?

I just found this interesting article:

> **IPv6 more secure? Forget it...**

                                                            *Submitted by [michael]("http://www.networkworld.com/community/user/3999") on Mon, 11/26/2007 - 4:03pm.*     So you heard as well that IPv6 is going to make the Internet more secure? Well, think again... In my opinion IPv6 is going to add a lot of complexity to our networks, and generally security goes DOWN when complexity increases. 
 Let me expand on this a bit. First of all, IPv6 doesn't change anything fundamental for security. IPv6 follows exactly the same paradigms as IPv4; you won't be able to trust the source address for example either. IPsec was meant to be a differentiator, but by now IPsec is equally deployed for IPv4. Equally? Actually, much more than for IPv6. 
 This means, that whatever you did for IPv4 security so far, you will have to replicate for IPv6. Note: Replicate - Not replace! Or do you think you can get rid of IPv4? Dream on - At best (although you may argue whether this is really "best") you can run "dual stack", ie both protocols in parallel. 
 Then you will need:
- Packetfilters for IPv4 *and* IPv6
- Firewalling for IPv4 *and* IPv6
- IDS for IPv4 *and* IPv6
- Host security for IPv4 *and* IPv6
- ... (you get the idea). 
 Ever complained about the length of a firewall config? Well, you'll have to practically double that with IPv6. Or the performance of your IDS system? Well, with IPv6 it'll have to do twice the analysis - it's going to be slower, of course!
 On top of that, you'll have to take care of various "transition mechanisms". I put this term in quotes, because in my opinion I won't live to see the "end" of the IPv4 Internet. So what is commonly called "transition" will be more like a permanent fixture in the Internet. There are lots of different ways to go from v4 to v6 and vice versa. Including all sorts of fun tunneling mechanisms. Tunneling is a great way to bypass security, as we all know. And, you'll have to controll *all* of the potential transition mechanisms, to be secure. Forget one and you have a hole. 
 So in summary: You'll have to completely duplicate all security mechanisms you have in place for IPv4 also for IPv6. Completely. Are you ever sure you haven't forgotten something for IPv4? Well, your chances of making a mistake have now at least doubled. I would argue it's actually worse, given the transition mechanisms. 
 Looks like IPv6 may come at some point. Probably we'll have no choice. And we'll manage, of course we'll manage. But easy it's not going to be. And more secure? No way, quite the opposite if we're not VERY VERY careful...

[http://www.networkworld.com/community/node/22271](http://www.networkworld.com/community/node/22271)

---

