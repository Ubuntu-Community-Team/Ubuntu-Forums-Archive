---
title: "Local Domain on Linux"
date: 2011-09-12
forum: Server Platforms
---

### Post by X-Legs on 2011-09-12
Hello,

I came across a really cool feature on Mac OS X where I can setup a local domain. For example, it is very easy to make it so that typing "mac.local" in a web browser on my LAN would take me to webpage I have hosted there. 

I know there is a way to do this in Linux, but I can't find instructions (or I'm to n00b for any instructions to be useful). Can someone help me do this in Linux? Thanks.

---

### Post by haqking on 2011-09-12
> **X-Legs said:**
> Hello,

I came across a really cool feature on Mac OS X where I can setup a local domain. For example, it is very easy to make it so that typing "mac.local" in a web browser on my LAN would take me to webpage I have hosted there. 

I know there is a way to do this in Linux, but I can't find instructions (or I'm to n00b for any instructions to be useful). Can someone help me do this in Linux? Thanks.

you mean running a webserver on your own machine and how to view it in browser ?

just type localhost in your browser

---

### Post by X-Legs on 2011-09-12
No, I mean that the Mac hosts the site and I can access it on any other device in my home network by typing "mac.local"

I know I can use an IP address, but this is easier to remember and kinda cool.

---

### Post by haqking on 2011-09-12
> **X-Legs said:**
> No, I mean that the Mac hosts the site and I can access it on any other device in my home network by typing "mac.local"

I know I can use an IP address, but this is easier to remember and kinda cool.

oh you mean the name that bonjour broadcasts in the lan.

you can edit your hosts file with ip to hostname mappings.

easier than using DNS for a small lan.

avahi is the zeroconfig equivalent of bonjour in linux

you could also look at [http://www.dns-sd.org/](http://www.dns-sd.org/) and [http://www.multicastdns.org/](http://www.multicastdns.org/) which are similar services to what bonjour does

---

### Post by volkswagner on 2011-09-13
> **X-Legs said:**
> No, I mean that the Mac hosts the site and I can access it on any other device in my home network by typing "mac.local"

I know I can use an IP address, but this is easier to remember and kinda cool.

If you have local dns working you can use hostnames.

For example, I set my router to act as the first or main dns.  Any machines that I want to have a static ip, I use the router to dish out the static ip based on mac address.  

If you setup static ip using /etc/network/interfaces file, then the hostname may not get passed to your router.

Once you have local DNS working you can access any machine using the hostname rather than using ip address (no need to add map to /etc/hosts on all machines).

For me, the major pitfall with this setup:  If I have to reset my router for any reason, I often have to reboot, or restart networking on all machines that are up and running for the DNS to work.

If all your machines are not set to the same workgroup, you may need to add that to the hostname as you describe, like:

mac.local, mac.mshome, mac.workgroup, otherwise you can just use the hostname "mac".

---

