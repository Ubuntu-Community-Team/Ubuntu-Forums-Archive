---
title: "How to force Ubuntu to upgrade Apache to 2.2.17"
date: 2011-01-11
forum: Server Platforms
---

### Post by mrhuhk on 2011-01-11
I have a PCI compliance notice sitting here telling me to upgrade to Apache 2.2.17.  Thing is, Ubuntu is quite happy sitting on 2.2.16 (Ubuntu).

I understand that the Ubuntu folks' reasoning in rolling security updates back to 2.2.16, but I need to get an automated scan to shut up.

How do I do this?

---

### Post by sj1410 on 2011-01-11
what ubuntu version you are using

---

### Post by Thirtysixway on 2011-01-11
> **mrhuhk said:**
> I have a PCI compliance notice sitting here telling me to upgrade to Apache 2.2.17.  Thing is, Ubuntu is quite happy sitting on 2.2.16 (Ubuntu).

I understand that the Ubuntu folks' reasoning in rolling security updates back to 2.2.16, but I need to get an automated scan to shut up.

How do I do this?

How is the scan obtaining the version number? If it's just scanning your website, you could change apache settings so instead of sending out the version number it just says apache.

[http://httpd.apache.org/docs/2.0/mod/core.html#servertokens](http://httpd.apache.org/docs/2.0/mod/core.html#servertokens)

---

### Post by mrhuhk on 2011-01-14
> **sj1410 said:**
> what ubuntu version you are using

10.10 server

---

### Post by mrhuhk on 2011-01-14
> **Thirtysixway said:**
> How is the scan obtaining the version number? If it's just scanning your website, you could change apache settings so instead of sending out the version number it just says apache.

[http://httpd.apache.org/docs/2.0/mod/core.html#servertokens](http://httpd.apache.org/docs/2.0/mod/core.html#servertokens)

I don't know how kosher that is.  But, I may have to look into it.

---

### Post by Waappu on 2011-01-15
Hi,

It might you check serverTokens directive
[http://httpd.apache.org/docs/current/mod/core.html#servertokens](http://httpd.apache.org/docs/current/mod/core.html#servertokens)

---

### Post by Thirtysixway on 2011-01-15
> **mrhuhk said:**
> I don't know how kosher that is.  But, I may have to look into it.

It's a perfectly normal apache setting to change.  A lot of major websites will switch it to only say Apache as keep people from knowning their exact versions etc.

---

### Post by ravingmad on 2011-08-29
So is there actually a way to force Ubuntu to upgrade Apache to 2.2.19 ??

Is there a repository to add because "apt-get install apache" says I am up to date but I have v 2.2.14 and I would like to move to 2.2.19 for various reasons.

---

### Post by DanielDan on 2011-10-02
Anyone?  I mean, this is really an important issue.  With the DDoS vulnerability in apache, how is this not a priority??  Security updates should be released quickly.

---

### Post by Dangertux on 2011-10-02
There are multiple workarounds with out updating. I know I have posted several on this forum. There are also numerous solutions on the web available. Try googling it I can't post links ATM as I am on my phone. 

Also it's not a DDoS just a DoS and security vulnerabilities are important however due to the fact it is a DoS and does not allow arbitrary code execution it is not going to be a top priority particularly considering it is very easy to control range header requests.

Edit : wow this is an old thread and not even related to CVE-2011-3192. Ugh to the OP the correct answer is don't hire compliance auditors that only use automated scanning tools.

---

### Post by DanielDan on 2011-10-03
Thanks Dangertux.  I've been googling and that's what led me here.  I'll search around for your previous posts.  Cool blog btw.  Interesting stuff.

---

### Post by Dangertux on 2011-10-03
> **DanielDan said:**
> Thanks Dangertux.  I've been googling and that's what led me here.  I'll search around for your previous posts.  Cool blog btw.  Interesting stuff.


Thanks -- I'm glad you like it, I should really reblog the 3 majorly accepted workarounds since I always go looking for them but here is one that works as well.

[https://bechtsoudis.com/hacking/use-mod_rewrite-to-protect-from-apache-killer/](https://bechtsoudis.com/hacking/use-mod_rewrite-to-protect-from-apache-killer/)

---

### Post by SeijiSensei on 2011-10-03
[2.2.14-5ubuntu8.6]("https://launchpad.net/ubuntu/+source/apache2/2.2.14-5ubuntu8.6") for Lucid contains the patch for the range exploit.  If you've updated recently and have that version, you should be protected.

I'm still using the "SetEnvIf Range" method that the Apache Foundation [described]("http://httpd.apache.org/security/CVE-2011-3192.txt") while they were developing the patch.  I don't stream video or other large files where byte ranges matter.

See also [http://www.ubuntu.com/usn/USN-1199-1/](http://www.ubuntu.com/usn/USN-1199-1/).

---

### Post by mmazing on 2013-04-23
I love how nobody here has given anything resembling an answer to the original question as it was asked.

If someone wants to upgrade Apache to 2.2.17, they probably have a specific reason for doing so. Saying "well just trick the scan site" into thinking it's a proper version isn't an answer. Saying that you shouldn't bother to upgrade Apache isn't an answer.

This thread is a waste of time for anyone trying to upgrade Apache for whatever reason they want to.

---

### Post by CharlesA on 2013-04-24
> **mmazing said:**
> I love how nobody here has given anything resembling an answer to the original question as it was asked.

If someone wants to upgrade Apache to 2.2.17, they probably have a specific reason for doing so. Saying "well just trick the scan site" into thinking it's a proper version isn't an answer. Saying that you shouldn't bother to upgrade Apache isn't an answer.

This thread is a waste of time for anyone trying to upgrade Apache for whatever reason they want to.

No suggestions on how to upgrade Apache then?

The answer to the OP's question is here:

> **Dangertux said:**
> 
Edit : wow this is an old thread and not even related to CVE-2011-3192. Ugh to the OP the correct answer is don't hire compliance auditors that only use automated scanning tools.

That being said, the thread is from 2011 and was regarding Ubuntu 10.10, which is End of Life.

---

