---
title: "module key 'Magrathea"
date: 2014-07-22
forum: Security
---

### Post by cogset on 2014-07-22
I'm seeing these lines in the logs of a new Lubuntu Trusty installation:

```
Request for unknown module key 'Magrathea: Glacier signing key: 5682f337b8a0a17eef58c6ac5e9a85712c9208df' err -11

Loaded X.509 cert 'Magrathea: Glacier signing key: 77d70e1df42996dc92b01d759d3e8562ea32a1c7'
```

Now what does that mean? I take it may have something to do with WIFI,but what is it actually?

---

### Post by bashiergui on 2014-07-23
Looks like a bug to me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1253155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1253155)
that link says it's been fixed so update and it should resolve.

---

### Post by cogset on 2014-07-24
I've been applying all the available updates,I'll have to keep an eye on it and see if the message disappears from the logs.
BTW,I take this is a serious security flaw-or am I wrong?

---

### Post by bashiergui on 2014-07-25
If you scroll down in the launchpad link to where it says "CVE References" you can read the specifics of the vulnerabilities that the bug introduces. 

TL;DR - If exploited the attacker could get some leaked info from the kernel or cause a denial of service. Looks like maybe a bad guy could do "unspecified stuff" if he's local sitting in front of your machine. (What are the odds you know someone capable of exploiting this and that also has the desire to do so on your machine) Doesn't look like anyone publicly released a remote code execution exploit using this bug so I would not call this "serious." I'd give it a low or medium ranking depending on how critical the box is for me. 

You could use free versions of vulnerability scanners like Nessus or Nexpose to see how they rate the CVEs you find.

---

### Post by cogset on 2014-07-30
Thanks for your explanation (and for pointing out the bug in the first place),however I may have a doubt:looking at the CVE references in the bug,isn't this [https://bugs.launchpad.net/bugs/cve/2014-1690](https://bugs.launchpad.net/bugs/cve/2014-1690) the actual vulnerability issue for Trusty (which is indeed rated as High)  > The help function in net/netfilter/nf_nat_irc.c in the Linux kernel before 3.12.8 allows remote attackers to obtain sensitive information from kernel memory by establishing an IRC DCC session in which incorrect packet data is transmitted during use of the NAT mangle feature.
and isn't it way more serious than the local attacker issue?

---

### Post by bashiergui on 2014-07-31
Yah vulnerability management sucks. It's hard to know what resources to use if you don't do it a lot.

Here's an explanation from launchpad what low medium high critical mean for 'importance'. Note that the ranking has little to do with security and much more to do with functionality. Example: a bug that prevented everyone from connecting to a box would actually be a low security risk but it would be classified by the vendor as *critical* functionality ranking. 
[http://blog.launchpad.net/bug-tracking/triage-in-launchpad-suite](http://blog.launchpad.net/bug-tracking/triage-in-launchpad-suite)

Take a look at this link:
[http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-1690](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-1690)

IMO the NIST database it the simplest to understand **security** vulnerabilities. In that link they rated the severity low and they ranked the difficulty to exploit high. A successful exploit results in the attacker getting info about your system. He won't get root. This is why I and nist rated it low/medium.

---

