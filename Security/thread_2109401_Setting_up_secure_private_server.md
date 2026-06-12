---
title: "Setting up secure private server"
date: 2013-01-27
forum: Security
---

### Post by NilPointer on 2013-01-27
I want to run a private server on my desktop for myself and maybe a few friends. But thing is, I don't know for sure how to configure it. All machines, that would connect to it have dynamic IPs, so allowing only certain IPs won't work.

I want server to be invisible for most people to avoid hacking and unnecessary security risks (currently machine, which I want to use as server configured not to respond to pings from internet). Also, it would be good for connection to be secure.

From what I understand, setting up VPN may suit my needs, but is running VPN server safe?

---

### Post by Jonathan L on 2013-01-27
> **NilPointer said:**
> I want to run a private server on my desktop for myself and maybe a few friends. But thing is, I don't know for sure how to configure it. All machines, that would connect to it have dynamic IPs, so allowing only certain IPs won't work.

I want server to be invisible for most people to avoid hacking and unnecessary security risks (currently machine, which I want to use as server configured not to respond to pings from internet). Also, it would be good for connection to be secure.

From what I understand, setting up VPN may suit my needs, but is running VPN server safe?

Hi NilPointer

Running VPN server is a decent way to do this.

The main trick is if you want to only accept incoming packets from your known friends and completely reject everything else.   One way is with a service like dyndns.org, which you and your friends update.  Then you can check those DNS entries and only allow those in.  However, you might regard dyndns as something of an advertisement.

If you want to get clever, why not post images on Tumblr or wherever whose comments contain encrypted IP addresses?  You wget the latest page, wget the image, identify (from Image Magick suite) them to get the comment, decrypt with whatever you like, and then add to your firewalls.

Hope that's helpful.

Regards,
Jonathan.

---

