---
title: "Secure Remote Desktop"
date: 2011-02-19
forum: Server Platforms
---

### Post by Monotoko on 2011-02-19
Hi Guys,

I was wondering if it would be secure to add xubuntu-desktop to my server and then open RDP so my colleuges can jump in and out as they need to. Would it bring any major security risks to my server to do this?

I have heard there are ways to put a chroot around an RDP session, so it is like logging into a virtual machine, how would I go about that?

Daniel

---

### Post by Vegan on 2011-02-19
I use OpenSSL and have a secure remote connection to my server.

I firewall it from outside though as the management console is local.

---

### Post by Monotoko on 2011-02-19
OpenSSL, can I use Windows RDP to access it from elsewhere? 

Thanks,
Daniel

---

### Post by HermanAB on 2011-02-20
Windows RDP is totally different from SSH and uses RC4 cypher.  OpenSSL uses a variety, but AES is the usual default.  These things are not compatible at all.

---

