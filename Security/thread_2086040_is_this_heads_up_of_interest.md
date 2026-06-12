---
title: "is this heads up of interest?"
date: 2012-11-19
forum: Security
---

### Post by candtalan on 2012-11-19
Just seen this on twitter from 

===============================
Mikko Hypponen @mikko 
 Remarkable new Linux rootkit: [http://blog.crowdstrike.com/2012/11/http-iframe-injecting-linux-rootkit.html](http://blog.crowdstrike.com/2012/11/http-iframe-injecting-linux-rootkit.html) … Capable of injecting malicious iframes into web traffic. Analysis by @ochsff
===============================

I am no expert and I would appreciate any informed comments

---

### Post by jerome1232 on 2012-11-19
I see it works on a specific kernel, 2.6.32-5, that's a *very* old kernel. I didn't see anything about whether it works on other kernels or not.

---

### Post by OpSecShellshock on 2012-11-19
Even I'm a bit confused here. The analysis in the Crowdstrike post seems to me to be implying this is client-side malware, but the Full Disclosure post looks like they're talking about a server being compromised in such a way that it injected code in http responses which were then directing other clients to malware. To me a server compromise seems more likely, but it's already been cleaned up and identifying information on the attackers has not been made available.

Edit: I checked out the Kaspersky link as well. It's on a server, and it is kind of a novel approach. Rather than using a shotgun approach of remote file inclusion exploits with PHP, they are instead (somehow, not specified in the posts) installing the rootkit, which is more persistent and more versatile. The end game still appears to be directing people who browse the sites to other places for malware though, which is nothing new at all. This leaves the malware risk to desktop Linux users in the same place it was before.

---

