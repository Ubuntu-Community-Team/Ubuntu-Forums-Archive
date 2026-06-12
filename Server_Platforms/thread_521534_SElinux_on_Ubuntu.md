---
title: "SElinux on Ubuntu"
date: 2007-08-09
forum: Server Platforms
---

### Post by blue_mantra on 2007-08-09
huihu folks,
I'm a bit confused by the two wiki-articles about SELinux because they explain nearly nothing and seem outdated. I wanted to ask which packages I need to install from the repositories and what do I have to take care when installing it?

I'm using an Ubuntu Feisty Fawn desktop system.

bye

---

### Post by ruibernardo on 2007-08-09
> **blue_mantra said:**
> huihu folks,
I wanted to ask which packages I need to install from the repositories and what do I have to take care when installing it?


Hi blue_mantra,

I don't really use SElinux, but I was curious about it too and i've tried to install it. I got it to work (on Feisty). It only talks about installing it and make it active.

To see how I did it, check this:

[http://ubuntu.no.sapo.pt/selinux_ubuntu_feisty_eng.html](http://ubuntu.no.sapo.pt/selinux_ubuntu_feisty_eng.html)

If it woks for you too, maybe the wiki-articles could be updated (for Feisty).

---

### Post by dropwire on 2007-08-09
Does anyone know if Gusty will have an option during the install to enable SELinux by default?  I think that would a good call too allow the policy enforcement enabled straight out of the box.

---

### Post by HermanAB on 2007-08-09
You need RedHat, Fedora or CentOS if you want to play with SELinux.  If you install it yourself, then nothing will work - guaranteed.  It is very hard to configure properly and if you don't configure it properly, then there is no point in using it.  

More info on the NSA web site: [http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

Cheers,

Herman

---

### Post by dropwire on 2007-08-09
exactly why I hope the ubuntu devs will further implement it into the OS in further releases.

---

### Post by ruibernardo on 2007-08-09
Just for the record, SElinux is supported by Ubuntu kernel since Ubuntu 5.10 Breezy!

Only the packages aren't installed by default as in others distros.

---

### Post by HermanAB on 2007-08-10
Sure, SELinux is in kernel 2.6, but there is this little matter of configuration...

---

### Post by ruibernardo on 2007-08-10
> **HermanAB said:**
> Sure, SELinux is in kernel 2.6

Yes, but if you try to get a vanilla kernel, it wont work. Ubuntu kernel is compiled with the right options enabled (I think most distros as this by now).

> **HermanAB said:**
> but there is this little matter of configuration...

Yes, SElinux isn't easy to install and maintain. If you check SElinux site, you'll see that it isn't a light application.

Even in RH you can enable it if you want to, but most people don't because it cause problems to much problems with permissions. I say this just by seeing them talking about on Google.

It isn't really a "desktop" application ready to use.

SUSE has AppArmor, which is also available in Ubuntu, since Feisty.

---

### Post by HermanAB on 2007-08-10
Believe me, it is not simple at all.  There are two books that you can buy on it:
[http://www.amazon.com/SELinux-Example-Security-Enhanced-Development/dp/0131963694](http://www.amazon.com/SELinux-Example-Security-Enhanced-Development/dp/0131963694)
[http://www.amazon.com/SELinux-Source-Security-Enhanced-Linux/dp/0596007167/ref=pd_lpo_k2_dp_k2a_2_img/105-3301701-6568428](http://www.amazon.com/SELinux-Source-Security-Enhanced-Linux/dp/0596007167/ref=pd_lpo_k2_dp_k2a_2_img/105-3301701-6568428)

Unless you are doing military work, don't bother.  This is not for ordinary mortals.

Good luck - you'll need it...

Cheers,

Herman

---

### Post by kula on 2007-08-10
Hi guys,
I can't agree with that the SELinux is hard to implement and maintain. I'm using it on debian and fedora and it works properly. To be honest sometimes some applications doesn't work but after reediting polices its ok.
HermanAB "If you install it yourself, then nothing will work - guaranteed" that is totally an true.
I'm wonder for what reason you need it on desktop? Only explanation for me is you've got some servers on it, but in this case better choice is to bring up separate machine for it or if you want to experiment with it use a VM or Xen.
Really it isn't so hard, just need some work that's all. Try it.

---

