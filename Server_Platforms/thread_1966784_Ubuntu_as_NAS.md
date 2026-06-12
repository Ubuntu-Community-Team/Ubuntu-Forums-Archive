---
title: "Ubuntu as NAS"
date: 2012-04-27
forum: Server Platforms
---

### Post by alka5eltzer on 2012-04-27
Hi there all,

I've recently joined a new company.

Currency all users (12) on the network just use their local HD's for storage.
I've asked them why don't they have a central forma of storage that everyone can share... e.g. a NAS Box and he's asked me to look in to it.

I've found an old XP desktop PC with OK spec with 2 drive bays. I was thinking of installing ubuntu or ubuntu server on this and  2 new SATA I drives (1Tb each) and setting up a mirror, RAID1?

I've set up Samba before... but is it easy to set up this kind of raid configuration?
How will I know if one of the drives fail?

Also... in the future... will it be hard to set up Home dirs and permissions to certain folders?
And VPN in to this or certain folders from outside?... is this easy to set up?

A friend of mine told me about a front end that does all of this for you... like a management console... adding users and permissions etc but he cant remember the name?

Thanks loads

---

### Post by arrrghhh on 2012-04-27
Hrm, there's many front-ends... not sure which one in particular he was talking about.

Webmin is good.  [Zentyal](http://www.zentyal.com/en) sounds like it would fit your needs nicely, although I've never used it.

As for setting up RAID and Samba those are really two completely separate things.  If you've setup RAID and are familiar with it, and you've setup Samba and are at least somewhat familiar with it... you should be fine.

Per-user permissions start to get tricky, I haven't done much with it - but I know you can go all out and even authenticate users via LDAP.  Never done this myself tho ;).

VPN is another thing I am not too familiar with, but I know there's a couple of solutions here based on your needs.

---

### Post by alka5eltzer on 2012-04-27
I've set up Raid but on a Windows machine... so I'm maybe in unknown territory here lol

---

### Post by Jonathan L on 2012-04-27
Hi alka5eltzer

Go one step at a time and you'll do fine.  I recommend Ubuntu server 10.04.4 Server, which is a very stable Long Term Support version (12.04 LTS is just released: I'd go with the older one).

I've no experience of the web control panels, but if you invest a little time learning the command line "proper server way" you'll find you reap the benefit again and again.

For a dozen users what you're suggesting is perfectly sensible.

RAID1 is easy enough to set up in software.  Here's a perfectly good tutorial [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

You can monitor the behaviour with mdadm, which will tell you what's happening.

Samba will do all you need and more.

VPN can be done over openSSH.

An alternative which you might find appealling is FreeNAS, which is based on FreeBSD, not Ubuntu, and is pretty much designed for what you describe.  Control panel is on a web interface.  [http://www.freenas.org/features/feature-overview](http://www.freenas.org/features/feature-overview)

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by arrrghhh on 2012-04-27
> **alka5eltzer said:**
> I've set up Raid but on a Windows machine... so I'm maybe in unknown territory here lol

Ah, well perhaps you have to consider what type of RAID is appropriate.  mdadm is quite robust, and for most needs this is more than adequate.  This is software RAID, and dependent on the OS.

There is also hardware RAID - where there's a hardware RAID controller that actually does the heavy lifting.  There's additional cost with this setup, and if the controller dies you have to basically make sure you replace it with an identical controller...  The advantages are usually speed and reliability - but this is more of a large enterprise thing, I would think software RAID is more than enough for your needs.

---

