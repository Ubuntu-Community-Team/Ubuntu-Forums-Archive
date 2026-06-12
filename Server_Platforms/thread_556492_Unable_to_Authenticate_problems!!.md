---
title: "Unable to Authenticate problems!?!"
date: 2007-09-21
forum: Server Platforms
---

### Post by ZoSoSwiM on 2007-09-21
Hello everyone,

I'm fairly new to network administration and I've ran into a rather annoying problem which keeps popping up all over my network.

Running Windows Server 2003 

Users are able to log into our domain and use all the network features as they have always been able too. When some users try to access our email they use their username and password they've always used, but the website comes back saying that it was unable to Authenticate the user. If this person tries to check their email from another persons computer while they are logged in they can check their email no problem.

Also, if I or anyone else try to check our email we can't with the affected person logged in.

Our email is hosted by another company but we have administrative control over it. Other sites which need authentication or login are similarly affected too.

What could be causing a problems like this?

Things that I've tried..
-Resetting their passwords, it's worked a few times
-Disabling and re enabling their accounts
-removing and adding their commonly used computers


Thanks for any help!!

---

### Post by ZoSoSwiM on 2007-09-24
Sorry to bother everyone but I could really use some help..

---

### Post by HermanAB on 2007-09-24
You have my sincere condolences.

Here is something that may give you a few clues:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

BTW, I have found that Win2003 screws up from time to time, for no apaprent reason and there typically is no apparent fix either.  The best way to handle the situation is to install Win2003 on VMware and make regular snapshots so that you can go back to a previous snapshot when it inexplicable screws up.

Windows should not be lightly discarded.  It should be thrown, with great force.

Cheers,

H.

---

### Post by ZoSoSwiM on 2007-09-24
Thats just it.. out of the 1500 or so users it's only affecting a few people at a time. Some people haven't had a single problem while others continually have them.

The affected users can sign on to any workstation with no problem but when it comes to connection to outside websites is screws up. Why would the internal network login affect the outside internet?

---

### Post by HermanAB on 2007-09-24
You have to put a sniffer on the wire and look at the packets.

I have found cases where the system works with Windows clients, but fails with Linux, raising packet checksum errors.  I have also found the opposite, with Linux working and Windows failing.

Debugging this with a Windows client is basically impossible, since Windows has no debug capability.  You need a Linux client to be able to see what is going on, so you can use my guide to set one up.

The faults can be in the Windows clients or on the Server.  It can be a problem with time, routing, DNS, or the Windows server itself sending out bad packets.  Only with a Linux client will you ever be able to figure out what is wrong.  In the long run, you will be better served with a Linux based domain controller, since once you get that working, it will stay working and then all faults are guaranteed to be on the Windows clients only.

Cheers,

H.

---

### Post by ZoSoSwiM on 2007-09-25
Well I work for a school and right now the school year has started up and doing any full on system configurations would be pretty tough.. I guess I'll be waiting for a while..

Are there any great free server OS's out there ? 

I downloaded Ubuntu but haven't had a chance to play yet..

---

