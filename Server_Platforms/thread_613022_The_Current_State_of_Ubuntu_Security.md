---
title: "The Current State of Ubuntu Security"
date: 2007-11-14
forum: Server Platforms
---

### Post by skm376 on 2007-11-14
I am interested in learning more about the various techniques Ubuntu uses (by default) to ensure security.  For instance, I know GCC 4.1 uses SSP, the stack is non-executable, ASLR, etc. but where is the complete list of all security measures enforced by Ubuntu...is there one?  Is there a list of what security measures the Linux kernel now supports by default?  

Thanks in advance.

---

### Post by The Tronyx on 2007-11-14
> **skm376 said:**
> I am interested in learning more about the various techniques Ubuntu uses (by default) to ensure security.  For instance, I know GCC 4.1 uses SSP, the stack is non-executable, ASLR, etc. but where is the complete list of all security measures enforced by Ubuntu...is there one?  Is there a list of what security measures the Linux kernel now supports by default?  

Thanks in advance.

I never like being the 'post-a-link for a reply' guy but I was looking over this site the other day and found it to be pretty informative.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

I hope that helps out with what you are looking for.

---

### Post by skm376 on 2007-11-14
That page is interesting, but not quite what I'm looking for.  If anyone knows where I can find out about specific security counter measures included in Ubuntu (or Linux in general) that is what I am looking for.  I am also interested in learning who and where discusses what new security measures will make it into future distro's/kernel's.

---

### Post by The Tronyx on 2007-11-14
Kind of a side note but have you checked out SELinux at all?

---

### Post by Mike'sHardLinux on 2007-11-14
In ubuntu, SELinux is disabled by default. I think this is even true in the server version. Coming from the Fedora/Redhat world, I found this a bit strange, but at least it's easier.

---

### Post by HermanAB on 2007-11-15
Here is a basic reading list:
Netfilter (iptables)
TCPwrappers
User privilege separation
Sudo
PAM
SELinux
OpenSSL
AES

Cheers,

Herman

---

