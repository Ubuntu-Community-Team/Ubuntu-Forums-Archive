---
title: "Mono frustrations. I just want to run .Net apps in the latest version. (Keepass)"
date: 2009-05-14
forum: Virtualisation
---

### Post by BFG on 2009-05-14
Long story short - I used Keepass for ages on windows and I have about 100 man hours invested in the data held in this app.  I went to Keepass 2 to enable synchronisation with multiple machines, BUT too late I realised they had dropped their principles of portability and moved onto the .net platform.  Grr!

So.  They say that it can work with mono 2.2.  But, ubuntu ships with 2.0 only.

I'm not and never will ever be interested in developing mono apps. I only want to run apps that rely on the .net framework.  But, I can't find a way to have mono without the overhead of the development part.

And I think because it comes with development capability, the target audience is people who don't mind fiddling around to get the thing installed.

I have tried and failed a few times.  And all the documentation I can find is a few versions out and so doesn't help.  And even when I get mono working I'll still have to struggle to get Keepass to run on it, because they don't have docs on the process either.

All I want to do is get my passwords and this is so frustrating!  I have to boot w*****s in vmware just to open a web page :(


BTW - KeepassX does not support Keepass 2 files. At all.

---

### Post by directhex on 2009-05-14
Mono isn't a small app, it's a major framework. This means it's very hard to update it post-release as the risks of regressions are enormous.

As to KeePass, it seems to work just fine, other than some rendering glitches, on Jaunty (2.0.1). Just make sure you have the following packages installed, and run it with "mono KeePass.exe":

mono-runtime libmono-winforms2.0-cil

---

### Post by BFG on 2009-05-20
Thanks for that, it worked perfectly!!

---

