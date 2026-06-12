---
title: "Ubuntu 10.04 Server Security?"
date: 2011-06-24
forum: Server Platforms
---

### Post by vpswing on 2011-06-24
Hi,

I just got a VPS a few weeks ago, and I've been playing with the various Linux distros made available to the VPS. 

So far, I'm quite impressed with ubuntu 10.04 LTS but I do have a question which I hope is not too silly to ask.

I noticed that many of the software packages are not the latest - for example,

Apache2 - 2.2.14-5ubuntu8.4

But on apache's changelog:
[http://www.apache.org/dist/httpd/CHANGES_2.2](http://www.apache.org/dist/httpd/CHANGES_2.2)

Latest version is 2.2.19 which has several security fixes/patches.

So, my question is - are the software packages that comes with Ubuntu 10.04 LTS secure enough for a production server? 

I've done:
apt-get update && apt-get upgrade

to ensure all the installed packages are up to date.

Many thanks for your insights and advice!

Adrian

---

### Post by falko on 2011-06-24
If there was an important security fix, Ubuntu would make it available through its security repository.

Don't let the version number fool you - often package maintainers backport security fixes to older versions, so your Apache 2.2.14 could well be up to date security-wise.

---

### Post by Dangertux on 2011-06-24
My suggestion is that you should make yourself aware of all the possible threats, and determine if the risk level is something you are willing to accept. 

Also find out if in fact the patch was back-ported, as the above poster mentioned.

You can find a list of known vulnerabilities here.

[http://httpd.apache.org/security/vulnerabilities_22.html](http://httpd.apache.org/security/vulnerabilities_22.html)

These itemize exactly what is at stake with each of the known/patched vulnerabilities. This is not inclusive and there may be exploit code that has not been seen in the wild. Also it is important to note that even with the most updated patches a 0 day exploit is still going to own you. 

So what it really comes down to, is you have to use composite risk management and decide if it is a risk your application can handle. Or if it needs to be further mitigated. However from the quick glance I gave it, it would appear your system is not directly effected by any of the more critical methods. While the possibility for Denial of Service appears, I wouldn't be overly concerned with data compromise.

Hope this helps.

---

### Post by vpswing on 2011-06-24
Hi Falko & DangerTux,

Many thanks for the replies and assurance. This gives me the confidence to proceed :-)

Cheers!

---

### Post by Dangertux on 2011-06-24
Just remember, stay vigilant and constantly educate yourself on security. Just because something is what it is now, doesn't mean it will be that way tomorrow.

Good luck.

---

### Post by vpswing on 2011-06-25
Thanks DangerTux, will keep that in mind!

---

