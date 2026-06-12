---
title: "Shopping for a VPS provider"
date: 2010-07-11
forum: Server Platforms
---

### Post by mdlueck on 2010-07-11
Greetings-

We are shopping for VPS vendors to run Ubuntu at.

We were quite impressed with [http://www.linode.com/](http://www.linode.com/) however they do NOT have a total ban on adult content as our current provider, 1&1, has. So we will not be considering them further.

I was impressed with a couple of things that Linode offered:
1) Their Lish remote server console access --> [Link to page with Lish demo video]("http://www.linode.com/features.cfm")
2) Documented support for doing Ubuntu version upgrades. --> [How to Upgrade to Ubuntu 10.04 LTS (Lucid)]("http://library.linode.com/troubleshooting/upgrade-ubuntu-10.04")

I noticed Linode uses Xen.

So does any other provider using Xen also offer the above two items AND ban adult content?

We will be looking to run 10.04 since it is an LTS version.

Also one sharp spot just came up at 1&1. With Virtuozzo which 1&1 uses, the filesystem is not defined in /etc/fstab. We need to add acl support to the ReiserFS, thus have an open ticket for days now to get 1&1 admins to check the box that our filesystem is to be mounted with acl support. Not sure how Xen works, but however it does work we would need acl support on our filesystem. We would prefer xfs which natively supports acl's, but xfs is not a showstopper for us.

Sincerely,

---

### Post by doogy2004 on 2010-07-11
Lish is specific to Linode.

I'm kind of curious why you want a VPS provider to ban adult content?

---

### Post by mdlueck on 2010-07-11
Just do not want to do business with anything near adult content. Do not want hosting provider admins tempted to be snacking on adult content of one customer's sites and then try to be helping us with our systems. etc... No, no, NO!! Period.

About Lish... do you think it is a proprietary fork / extension to Xen, or did Xen leave Lish type capabilities that Linode just put to use? Thinking since it has been done once, could be done again.

---

### Post by doogy2004 on 2010-07-11
> **mdlueck said:**
> Just do not want to do business with anything near adult content. Do not want hosting provider admins tempted to be snacking on adult content of one customer's sites and then try to be helping us with our systems. etc... No, no, NO!! Period.

Thanks for the answer, I was just curious.

> **mdlueck said:**
> About Lish... do you think it is a proprietary fork / extension to Xen, or did Xen leave Lish type capabilities that Linode just put to use? Thinking since it has been done once, could be done again.

I'm preaty sure that "Lish" is something that was written in house at Linode.  Lish is basically a way of seeing what is going on in the virtual machine console, like looking at the monitor of a physical server.  You will be looking for a VPS that gives you access to the Xen console.

List of Xen VPS Providers - [http://wiki.xensource.com/xenwiki/VirtualPrivateServerProviders](http://wiki.xensource.com/xenwiki/VirtualPrivateServerProviders)

---

### Post by ryry46d9 on 2010-07-11
> **mdlueck said:**
> Do not want hosting provider admins tempted to be snacking on adult content of one customer's sites and then try to be helping us with our systems.

I don't want to rain on your idea here, but lets say you find a host that does block said content coming in to / out of the building. The Tec could be watching it on a portable DVD player or a laptop/netbook. No one but him would know.  

I used to work for a call center and our tec would bring in his laptop to watch movies in the background as he was waiting for a install of a workstation to be completed / waiting for a computer to crash.

To not pick a company over a silly thing like this, may make it hard for you to find the best service at the right price. 

Either way good luck in your hunt

---

### Post by mdlueck on 2010-07-22
> **doogy2004 said:**
> List of Xen VPS Providers - [http://wiki.xensource.com/xenwiki/VirtualPrivateServerProviders](http://wiki.xensource.com/xenwiki/VirtualPrivateServerProviders)

Thanks for sharing that list. I contacted several that say they offer Ubuntu. All said they support Ubuntu version upgrades. All said that they support connecting to the remote server console screen. Must be that such is standard fare with Xen visualization.

Much relieved, I will conduct a more in-depth evaluation. Thanks again!

---

### Post by Frak on 2010-07-22
Sorry to rain on your parade, but you'll never find a VPS where this never happens. And even then, it is a tad silly to exclude a company just because someone that works there likes 'adult content'.

---

### Post by clanky on 2010-07-22
Welcome to the internet.

Fundamentalism FTW.

---

### Post by mdlueck on 2010-07-22
> **Frak said:**
> it is a tad silly to exclude a company just because someone that works there likes 'adult content'.

???? I said I was not going that detailed.

Just that I would _prefer_ to find one with a similar ban that 1&1, our current provider, has. That is, no hosting that type of content.

It would be very silly for someone to think that they could control what employees of said provider do "on their *'own'* machines".

---

### Post by Frak on 2010-07-23
> **mdlueck said:**
> ???? I said I was not going that detailed.

Just that I would _prefer_ to find one with a similar ban that 1&1, our current provider, has. That is, no hosting that type of content.

It would be very silly for someone to think that they could control what employees of said provider do "on their *'own'* machines".
I tend to stand by "Hate, vulgar, or offensive speech is still free speech." I would be proud to use the same host as the Westboro Baptist Church, not because I support them, oh no. I would be proud because I would be using a host that respected free speech, no matter how ignorant or wrong it is, because in the end, who really has the ability to say what is right and what is wrong?

---

### Post by B_Davis on 2011-03-29
I dont want to spoil anything, but 1 and 1 DO allow adult content. OTCAMS is an adult hardcore webcam show and live sex service, I dont think you could get any more adult than that. 1 & 1 seem perfectly fine hosting that for the last few years. In fact most hosting companies run adult servers in the same racks, but just advertise it under different company names.:(

---

### Post by SeijiSensei on 2011-03-29
As a very satisfied Linode user, I could care less whether they "ban" adult content or not.  First off, they're renting virtual servers. How the hell would they know what I'm hosting? Nor it is any of their business.  Their business is to provide me with a working virtual machine and good support, which they do quite well.  How I use that machine is up to me, and I'm liable for any consequences what I do may entail.  I certainly don't want a busybody provider that scans my virtual hard drives looking for porn or whatever else might be there they don't like.

Just in case you're wondering, no, they wouldn't find any porn there anyway, but that's not the point.

---

