---
title: "Best AV package to use with Dapper Mailserver"
date: 2007-01-25
forum: Server Platforms
---

### Post by jimwillsher on 2007-01-25
Hi all,

I'm currently using ClamAv on my Dapper installation, but as is widely discussed elsewhere ClamAv is outdated and (seemingly) no longer being maintained for Dapper.

99% of the related threads on this website state that you don't need an AV package for Linux unless you are running a mailserver. Well I AM running a mailserver - my Dapper box is a LAMP installation, and does nothing other that serve websites and filter emails to my Windows computers.

So, can anyone recommend a simple but reliable (and maintained!) AV solution which will integrate nicely into a Dapper installation - specifically Postfix and amavisd?

Many thanks,


Jim

---

### Post by renzokuken on 2007-01-25
didnt AVG release a linux AV port?

not sure how well it will integrate into a mailserver though

---

### Post by jimwillsher on 2007-01-25
Yes they did, but it seems to hinge around RPMs only, which leads me to suspect a RedHat background rather than Debian.


Jim

---

### Post by renzokuken on 2007-01-25
you could always use alien to install the rpm easily.

AVG have regular updates too.

---

### Post by jimwillsher on 2007-01-25
True, yes, that would be an option.

But am I doing ground-breaking stuff here? Surely I'm not the only one in this situation?

---

### Post by jtc on 2007-01-25
...or you could always install/compile ClamAV manually? True, it is not as automagically as getting it through apt-get/synaptic, but if you go for som external AV you might not find it in the repository either.

---

### Post by jimwillsher on 2007-01-25
I think I'll go for the compilation option. I prefer apt-get for everything, but it looks like ClamAv is NEVER going to be updated so I'm probably safe to compile.

Many thanks,



Jim

---

### Post by jimwillsher on 2007-01-25
Easy :-)

I've removed the old package via apt and then installed the new one via  ./configure, make, make install. I had to make a few tweaks to amavis, but everything is now working!

Many thanks for giving me the confidence to proceed.



Jim

---

### Post by live4fun on 2007-04-06
Have you tried checkinstall? Substitute make install with checkinstall. It tries to create an .deb packages. This is imho a much cleaner way to install selfcompiled software in debian/ubuntu.

---

### Post by eric_stewart on 2007-04-06
> **live4fun said:**
> Have you tried checkinstall? Substitute make install with checkinstall. It tries to create an .deb packages. This is imho a much cleaner way to install selfcompiled software in debian/ubuntu.

I got tired of waiting and I compiled ClamAV from source too.  It was fun but wouldn't you know that there's a new package for Feisty Fawn?  Oh well...all that work (geeky fun actually) for nothing  :-)

I'm now running Feisty Fawn beta and am happy with the new ClamAV package (version 0.90.1)   They must have been listening.

Eric

---

