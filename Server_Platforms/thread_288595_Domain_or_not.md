---
title: "Domain or not?"
date: 2006-10-30
forum: Server Platforms
---

### Post by mozetti on 2006-10-30
Well, I've dabbled in Linux off and on for the past 2 years and I've been using Ubuntu as my sole OS for the past 4-5 months. I've got a good base and I'm ready to bring it all together. 

I've got Samba set up on my main rig (desktop, P4, 500Gigs) sharing out my files. My 2 laptops (Xubuntu & XPSP2-Home) are able to access it. I've also got a couple spare boxes - P3-667/120Gigs and an old (OLD) laptop, Win98 era.

I've been thinking about how to use the old P3-667 box. It would be a waste to run it soley as a router/dhcp server/intrusion-detection system, so I thought about setting it up as a Samba PDC. But, I don't have extensive knowledge of networking/network architecture. So, I've come to you to for advice.

What benefits will a domain bring to me?

_Additional Info:_
-Mixed WiFi and hardwired network
-This network will continually expand over the next few years to a total of about 10 machines.
-One goal (after I buy a house in a couple years) is to have centralized, network-accessible storage for media. Music, Movies, Photos all accessible from each computer in the house.
-One computer will be a home-entertainment PC (probably running MythTv)
-I *may* set up a webserver/mailserver at some point, but I don't think it's going to happen anytime soon.

---

### Post by unless on 2006-10-30
I guess this is a matter of personal perspective, but as I see it, the fundamental advantage of having a domain is centralized administration of users. If you already had a network of ~10+ users, or were dealing with multiple sites, I'd say that a domain would be the way to go. But if it's just for home use, plain old Samba shares will make for far fewer headaches than managing a domain. It'd make some things easier, but will render other things far more complicated than they need to be.

Web servers and mail servers wouldn't benefit by having a domain structure (at least not at home).

The only solid argument that I can see for setting up a domain would be for the experience. If you're interested in learning, then why not. 

Just one word of advice: If you choose to set up a PDC, make sure you've got a BDC running somewhere as well (like on the 500GB machine), in case the old battle-axe P3 decides to go belly up.

---

### Post by mozetti on 2006-10-30
> **unless said:**
> But if it's just for home use, plain old Samba shares will make for far fewer headaches than managing a domain. It'd make some things easier, but will render other things far more complicated than they need to be.

That's kinda what I thought, but I wasn't sure if I was missing something.

> **unless said:**
> The only solid argument that I can see for setting up a domain would be for the experience. If you're interested in learning, then why not.

Again, same thing I was thinking. I may still do it, but maybe using a seperate subnet so I don't mess up anything that works. :D

> **unless said:**
> Just one word of advice: If you choose to set up a PDC, make sure you've got a BDC running somewhere as well (like on the 500GB machine), in case the old battle-axe P3 decides to go belly up.

Good point. And from my reading I know that SAMBA can **only** be a PDC. What program could I use to run as a BDC?

---

### Post by mozetti on 2006-10-31
**BUMP**

I wouldn't mind getting a little more feedback on this, if you don't mind and have the knowledge.

Thanks!

---

### Post by jimm on 2006-10-31
Hi,

I agree with the other poster about the domain thing. Do it because you want to learn. I went through the same thought process as you and decided that although I didn't really need it, it was a good learning experience.  

The other 2 reasons (and also apart from the learning bit is why I still run and host my own domain) are: 

1.) So you can have and manage your own email server. i.e. as many mailboxes as you want, control over spam filtering, your own domain and you get to learn how to setup sendmail or exim or whatever :-) 

2.) So you can have and manage your own website with as many php, cgi, doo-hicky apps as you want! Again mostly it gives you experience setting up apache and stuff like that.

Of course you can still have your own domain and _not_ host your own stuff, so if at a later date you get sick of it you can farm it off to a hosting company or something! :-)

If you are going to do it, I recommend DynDNS.org as the place to register and have manage your domain records. The admin pages they provide are excellent and registry service is very easy to use. Also they do a neat dynamic DNS thing (amongst other services) that allows you to not have to worry about fixed IP addresses or changes when you change ISP or whatever. I have been using them for ages and they are brilliant. 

On the BDC thing... I have never done PDC \ BDC's with SAMBA (never had the need), but if you want a BDC, you need to build yourself a good old NT4 server and make it a BDC. I'd make a VM BDC (Vmware server) so you can make an easy backup... But then I'd probably make my SAMBA server a VM as well... but thats just me :-)

Thanks,
James

---

### Post by mozetti on 2006-11-01
> **jimm said:**
> On the BDC thing... I have never done PDC \ BDC's with SAMBA (never had the need), but if you want a BDC, you need to build yourself a good old NT4 server and make it a BDC. I'd make a VM BDC (Vmware server) so you can make an easy backup... But then I'd probably make my SAMBA server a VM as well... but thats just me :-)

Thanks,
James

Thanks for stopping in, Jim. I hadn't really considered running the SAMBA and & BDC as VMs. I'll have to look into that (got XP running as a VM right now). And I've got a free account with DynDNS, so I'll look into using them for my registration, too.

---

