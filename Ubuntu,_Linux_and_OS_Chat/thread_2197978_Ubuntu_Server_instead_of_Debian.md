---
title: "Ubuntu Server instead of Debian?"
date: 2014-01-06
forum: Ubuntu, Linux and OS Chat
---

### Post by treb0r on 2014-01-06
Hi All,

I'm a born again Ubuntu user, on the desktop at least.

I really love the OS, and as far as I'm concerend it's the best out there for desktops (and no doubt, phones tvs and tablets soon).

I have a small web business and I've been using Debian for client hosting for nearly 15 years now and it has never let me down.

I must confess to loving Debian too - the whole community ethos is attractive to me.

Having said all that, I find myself reading more and more about Ubuntu server, and innovative new features like Juju, etc.

I'm now looking at the trusty release as a possible time for change.

Anybody else out there moved from Debian to Ubuntu for client hosting?

I'm looking for rock solid stability first and foremost, although sexy new features are welcome too, as long as the stability is still there.

I'd value any insights that you might have.

Rob

---

### Post by tgalati4 on 2014-01-06
Set up a development machine and load the latest Ubuntu server and try out some of the new features.  Stability and new features are mutally exclusive, so you have to do a lot of testing to determine if the new features/services are stable enough for your purposes.  Juju is aimed at service orchestration, so unless you are managing a lot of remote/virtual machines and have hosting clients that require spinning up additional, on-demand services, then Juju may not help your existing client base.

List out the use cases in your current business (you don't need to share them) and see what new features would help support those use cases.  Having at least one Ubuntu server will allow you to migrate clients that want to try the new services. 

Share your experiences of what works and what doesn't.

---

### Post by treb0r on 2014-01-06
Yes, I know what you are saying about new features versus stability.

I'm just hearing a lot about stability, and with new Ubuntu QA testing discussed here by the SABDFL:

[http://www.markshuttleworth.com/archives/1306](http://www.markshuttleworth.com/archives/1306)

I'm thinking the unthinkable, that it is in fact possible to have both.

Now, I don't know for sure, but I don't think the Debian project has the resources to carry out this kind of testing.

Also, I didn't mention that I do in fact have a need to offer my clients the ability to scale up and down. Think Christmas ecommerce, etc. I can handle this now by using adaptable VMs with certain hosting providers, but I'm fascinated by the possibilites, particlaurly as I'm 100% Wordpress.

The last factor is around using Vagrant for local development - in the Wordpress community, Ubuntu seems to be emerging as the standard server OS.

You are corrrect though, I should give it a test first and try it out. Thanks.

---

### Post by tgalati4 on 2014-01-06
I have not played with vagrant (love that name!) but Linux Outlaws ([http://sixgun.org/episodes/lo330](http://sixgun.org/episodes/lo330)) gave it a thumbs up.  For Ubuntu server news, this article provides a nice summary:  [http://www.networkworld.com/reviews/2014/010614-ubuntu-test-277284.html?page=1](http://www.networkworld.com/reviews/2014/010614-ubuntu-test-277284.html?page=1)

As far as stability vs popularity, I use [http://bitnami.org/stacks](http://bitnami.org/stacks) as a gauge for what services are being supported on Ubuntu LTS server.  Because of the immense amount of work it is to support these packages/services, most are targeted to the current LTS.  You can run them on 13.10, but if something breaks, you are on your own.

---

### Post by rg4w on 2014-01-06
> **treb0r said:**
> Anybody else out there moved from Debian to Ubuntu for client hosting?
A little company called Dreamhost switched over the summer - with some 20,000 servers:

[http://www.linuxandlife.com/2013/06/dreamhost-now-uses-ubuntu-instead-of.html](http://www.linuxandlife.com/2013/06/dreamhost-now-uses-ubuntu-instead-of.html)

And I switched the development server in my office, so there's 20,001. :)

---

### Post by tgalati4 on 2014-01-07
That is an interesting development.  We'll see where Dreamhost is in a couple of years.   This may be a trend of more companies moving to Ubuntu for server support.

---

### Post by grahammechanical on 2014-01-07
First, I must say, that I have no experience with the server environment but I cannot imagine "sexy new features" being applicable to a server OS. But from the little I have seen I would say that the combination of Ubuntu and OpenStack would fit the description of "sexy." And Ubuntu is leading the field with being the basis for OpenStack deployment.

[http://www.ubuntu.com/cloud/tools/openstack](http://www.ubuntu.com/cloud/tools/openstack)

Regards.

---

### Post by treb0r on 2014-01-07
> **tgalati4 said:**
> That is an interesting development.  We'll see where Dreamhost is in a couple of years.   This may be a trend of more companies moving to Ubuntu for server support.

Yes, this is another thing.

It does seem to me that the sweet spot for business users is GPL licensed code with a solid business behind it offering support, much like Ubuntu (Canonical) and Wordpress (Automattic). 

I can't deny that the idea of using landscape for managing all of my servers in one place is very attractive, particularly when i can alos pick up the phone if I hit a problem.

---

### Post by treb0r on 2014-01-07
> **grahammechanical said:**
> First, I must say, that I have no experience with the server environment but I cannot imagine "sexy new features" being applicable to a server OS. But from the little I have seen I would say that the combination of Ubuntu and OpenStack would fit the description of "sexy." And Ubuntu is leading the field with being the basis for OpenStack deployment.

[http://www.ubuntu.com/cloud/tools/openstack](http://www.ubuntu.com/cloud/tools/openstack)

Regards.

Yeah, I hear what you are saying, maybe sexy was the wrong word. Innovative?

I think if you compare Debian stable with Ubuntu Server LTS you do get more in the way of features. Even small stuff like NTP pre-configured, etc is a boon for me.

---

### Post by lykwydchykyn on 2014-01-07
It's hard to generalize, but I stick with Debian for the meat-n-potatoes stuff.  I've setup Ubuntu server for some situations where I needed specific stuff like LTSP that was significantly newer in Ubuntu.  Ubuntu definitely has more momentum in cloud type services, so if that's your area of interest, it's probably worth it.

---

### Post by stuckeyneila1982 on 2014-01-10
I was using 10.04 LTS with a home file server for a long time no issues, I have since updated it to 12.04 after support for 10.04 ended.   I  know its not the same application your going to use but you cant go wrong with Ubuntu LTS for any server use.  I have not had a question or issue that was not resolved on this forum. Debian is good but Ubuntu is the best for support and features.  Ubuntu LTS with CLI interface with Webmin is rock solid Period.  Only thing i would suggest is only install what you need and use LTS version.  Using full Desktop distro with non LTS may introduce bugs and issues that you dont need on the server.  Also i use Clonezilla to take a complete system image before installing any regular updates just to make sure i have something to revert to.  I wont update the Ubuntu release until the LTS is not supported anymore and again i make a complete image backup of the system with Clonezilla. Even though i recommend using CLI and webmin only, using LTS with desktop for server use is fine i set one up for my employer just because its faster to use the GUI.  But again i cannot express how important it is to use full system backups before doing any altering of the server. Not doing backups and altering system settings has bitten me before and it wont happen again.

---

