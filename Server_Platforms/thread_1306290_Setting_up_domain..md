---
title: "Setting up domain."
date: 2009-10-30
forum: Server Platforms
---

### Post by H3l0 on 2009-10-30
Hey guys,

Ok here is my question.  I am wanting to setup a domain controller/DNS/DHCP/VPN box for my house.  I have the opportunity to get M$ server 2003 for free through my workplace.  Since this is the first time I am attempting this what would be easier for me to setup.  Ubuntu Server 8.04 or the M$ OS?   Note:  I am pretty new to Linux in general.  What would you guys recommend?

Thanks for the help!

---

### Post by elvinatom on 2009-10-30
MS - it goes like this: "Next, next, OK, Finish, Reboot".  And you don't even have to understand how it works :)

---

### Post by whoop on 2009-10-30
> **H3l0 said:**
> Hey guys,

Ok here is my question.  I am wanting to setup a domain controller/DNS/DHCP/VPN box for my house.  I have the opportunity to get M$ server 2003 for free through my workplace.  Since this is the first time I am attempting this what would be easier for me to setup.  Ubuntu Server 8.04 or the M$ OS?   Note:  I am pretty new to Linux in general.  What would you guys recommend?

Thanks for the help!

Well although I would prefer linux server myself, it's much more easy to get it up and running with Microsoft.
All the technology in linux exists but it has very very bad, incomplete out-of-date documentation. This really, really sucks!

You are about the tenth instance I've seen this year of people/organisations moving (or probably moving) to windows because of this. And I'm not even a people/organisation person:(

I would never go for the Microsoft solution but I have no trouble understanding why people would (taking the current state of documentation on open source alternatives).

The best documentation for open source tech I have found is:
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)
It's very complete but its for ubuntu **7.10**.

It's all just too bad...

---

### Post by H3l0 on 2009-10-30
LOL!  :p

Well I'm not the one to just set something up and not care to know how it works.  

Here is another question:  If I'm wanting to do VPN will I need to get a static IP from my ISP?

---

### Post by elvinatom on 2009-10-30
> **whoop said:**
> Well although I would prefer linux server myself, it's much more easy to get it up and running with Microsoft.
All the technology in linux exists but it has very very bad, incomplete out-of-date documentation. This really, really sucks!

You are about the tenth instance I've seen this year of people/organisations moving (or probably moving) to windows because of this. And I'm not even a people/organisation person:(

I would never go for the Microsoft solution but I have no trouble understanding why people would (taking the current state of documentation on open source alternatives).

The best documentation for open source tech I have found is:
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)
It's very complete but its for ubuntu **7.10**.

It's all just too bad...

That's exactly right.  I haven't even worked with Vista or Win7 and recommend to people to give ubuntu a try, but for people that don't like to, or don't have time to figure things out - MS is unfortunately the right choice (at least for now).

---

### Post by whoop on 2009-10-30
> **elvinatom said:**
> That's exactly right.  I haven't even worked with Vista or Win7 and recommend to people to give ubuntu a try, but for people that don't like to, or don't have time to figure things out - MS is unfortunately the right choice (at least for now).

I know it's a shame...

So please, everyone shout out. Let yourself be heard. Even if you go for the Microsoft solution or if you are a user that doesn't even need roaming profiles and the likes.
Everyone should understand, technology like this is a **must** for corporate environments to switch to linux.

Show support for blueprints like these:
[https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)
Let yourself be heard on threads like these (like I did):
[http://ubuntuforums.org/showthread.php?t=1304795](http://ubuntuforums.org/showthread.php?t=1304795)
There's probably other ways I didn't think of...

Personally, I'm not asking for point and click solutions, just complete up to date documentation for a technology that has priority number one.

---

### Post by elvinatom on 2009-10-30
> **H3l0 said:**
> LOL!  :p

Well I'm not the one to just set something up and not care to know how it works.  

Here is another question:  If I'm wanting to do VPN will I need to get a static IP from my ISP?

I don't know - i never used this, but if you like to learn the "good" stuff, DNS and DHCP is quite easy to set up under linux using the cli.

---

### Post by whoop on 2009-10-30
I've created an ubuntu idea on this topic: [http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)
Please Vote!

I don't expect this solved for Lucid, which is a shame as lucid is an LTS. But we can still hope somebody will get motivated to document it at least, even after the release.

I'll probably be trying to get it up and running when Lucid nears completion. So maybe I can even solve the problem. 
I'll see how far I can get, but there must be people that are experts on this.

---

