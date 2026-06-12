---
title: "Upgrade process not so keen?"
date: 2006-12-07
forum: The Cafe
---

### Post by wylfing on 2006-12-07
Hi, I have been a Debian (or Debian-derivative) user for about 7 years. I am very accustomed to server-side Debian (of which I run three), and by that I mean stability is king and only trumped by security updates. You would have to stick me with a cattle prod to make me do a dist-upgrade on any of my servers. On my desktop, I tend to be much more liberal.

I started using Ubuntu at Breezy. It was so good that I finally dumped Windows on my desktop* (i.e., I do NOT dual boot). From there I followed the upgrade chain to Dapper and ultimately (although belatedly) to Edgy. My perception of things, though, is that stability goes down with each release.

Now, nothing has happened that I can't handle. I am not looking for support here. In relative terms, I am a Debian Linux expert. I don't panic when the kernel does, I fix it. But I still see an increase in crashes with each new release.

My question is whether I should be blaming Ubuntu, the fact that I have upgraded so often, or the fact that I am too experimental? I am not a nice user -- I break things, I try new things out, especially on the desktop that is not work-critical.

What is the overall perception of stability for Edgy? Has it degraded since the Breezy days?

* This was a long-time ambition. I had tried Fedora, Mandrake, and straight Debian as a desktop solution but always found something lacking. Ubuntu was the first time I found a distro that could replace Windows on my desktop.

---

### Post by Brunellus on 2006-12-07
I found Dapper at least as stable as Breezy on my hardware--indeed, it fixed lots of things.  

Edgy has been considerably less stable than dapper for me.

As I put in a sticky on the Absolute Beginners section:  Edgy is...edgy (sometimes at least).  If you want stability, stay with Dapper for a while.

---

### Post by mips on 2006-12-07
> **wylfing said:**
> Hi, I have been a Debian (or Debian-derivative) user for about 7 years. I am very accustomed to server-side Debian (of which I run three), and by that I mean stability is king and only trumped by security updates. You would have to stick me with a cattle prod to make me do a dist-upgrade on any of my servers. On my desktop, I tend to be much more liberal.

I started using Ubuntu at Breezy. It was so good that I finally dumped Windows on my desktop* (i.e., I do NOT dual boot). From there I followed the upgrade chain to Dapper and ultimately (although belatedly) to Edgy. My perception of things, though, is that stability goes down with each release.

Now, nothing has happened that I can't handle. I am not looking for support here. In relative terms, I am a Debian Linux expert. I don't panic when the kernel does, I fix it. But I still see an increase in crashes with each new release.

My question is whether I should be blaming Ubuntu, the fact that I have upgraded so often, or the fact that I am too experimental? I am not a nice user -- I break things, I try new things out, especially on the desktop that is not work-critical.

What is the overall perception of stability for Edgy? Has it degraded since the Breezy days?

* This was a long-time ambition. I had tried Fedora, Mandrake, and straight Debian as a desktop solution but always found something lacking. Ubuntu was the first time I found a distro that could replace Windows on my desktop.

There are warnings out there that Edgy is well "edgy". Stick to Dapper.

---

### Post by wylfing on 2006-12-07
Yeah, I knew about those "warnings." I always thought they were directed toward (sorry!) the inexperienced crowd. I apologize if that sounds arrogant, I really don't mean it to. It's just that I am quite accustomed to fixing issues on my own, and I have a long experience with Linux, so I don't heed such warnings very seriously.

Anyway, it's nice to have a few opinions mirror what I have experienced. Would a clean install help anything? How about a clean install of Dapper?

---

### Post by mips on 2006-12-07
> **wylfing said:**
> 
Anyway, it's nice to have a few opinions mirror what I have experienced. Would a clean install help anything? How about a clean install of Dapper?

I always do a clean install, edgy did not work out for me. A clean install of Dapper might be a good idea.

Please note that other have had positive experiences with edgy. Me, I'm sticking to dapper for now.

---

### Post by wylfing on 2006-12-07
Thanks for the input. It matches what I have been thinking of doing. I'll just plan on doing a clean install of Dapper sometime soon, since I have good backups.

---

### Post by FyreBrand on 2006-12-07
I upgraded from Dapper to Edgy and found that the upgrade didn't go smooth at all.  I'm not an expert by any means so I probably made some mistakes along the way that broke things.  Also I had customized some things and that didn't go over well with the upgrade.  However, I did do a fresh clean Edgy (Kubuntu) install and I find it to be remarkably stable.  I did do a clean Ubuntu/gnome install of Edgy just to test it and found it equally as stable which makes sense since they are so similar.

If you don't mind a recommendation from a newbie, I would say at this point clean installs are better than upgrades if you do a lot of customization of settings or the environment of your desktop.  We'll see how Feisty goes.  I'm pretty excited for some of the things of the development plate for that.  Hopefully upgrading will go smoother.

---

### Post by Brunellus on 2006-12-07
> **FyreBrand said:**
> I upgraded from Dapper to Edgy and found that the upgrade didn't go smooth at all.  I'm not an expert by any means so I probably made some mistakes along the way that broke things.  Also I had customized some things and that didn't go over well with the upgrade.  However, I did do a fresh clean Edgy (Kubuntu) install and I find it to be remarkably stable.  I did do a clean Ubuntu/gnome install of Edgy just to test it and found it equally as stable which makes sense since they are so similar.

If you don't mind a recommendation from a newbie, I would say at this point clean installs are better than upgrades if you do a lot of customization of settings or the environment of your desktop.  We'll see how Feisty goes.  I'm pretty excited for some of the things of the development plate for that.  Hopefully upgrading will go smoother.
There is at least one #ubuntuforums regular who constantly advocates clean installs as a panacea for all ills.  I clash with him constantly.

The whole reason I went with a Debian Daughter Distro was that apt allowed graceful dist-upgrades.  This is still largely true.  My box has dist-upgraded from Hoary to Breezy to Dapper to Edgy.

---

### Post by wylfing on 2006-12-07
Hm, good input, thanks. Now I have to consider whether to do a clean install of Dapper or Feisty :)

Edit: @Brunellus: On the main I agree with you. I have upgraded Debian-type boxes for years and years.

---

### Post by midwinter on 2006-12-07
Played with Debian Etch? :)

---

### Post by Henry Rayker on 2006-12-07
I always do a clean installation, but for a couple reasons...sure the upgrade process is easy, but I've heard nightmares as far as a downgrade goes...I'm always worried I'll want to go back D:

---

### Post by Brunellus on 2006-12-07
> **Henry Rayker said:**
> I always do a clean installation, but for a couple reasons...sure the upgrade process is easy, but I've heard nightmares as far as a downgrade goes...I'm always worried I'll want to go back D:
Let me speak up for the non-upgrading people.  

Generally, dist-upgrading "just because" is a bad idea. Unless there's a compelling reason to dist-upgrade, then you're actually probably just as well off with ubuntu -1 or even ubuntu -2.  The release cycles will still cover you. 

Those of you who are extremely cautious would do well to remember this.

---

### Post by wylfing on 2006-12-07
That is sage advice, and that is what I do for my servers, because breakage == badness in server-world. In addition, if you have a work-sensitive machine, you should always keep at least current-1 so that you know your work is going to get done.

These are always my strategies. I'm just inquiring about Edgy's perceived stability among the technoliterati :)

---

### Post by FyreBrand on 2006-12-07
> **Brunellus said:**
> There is at least one #ubuntuforums regular who constantly advocates clean installs as a panacea for all ills.  I clash with him constantly.

The whole reason I went with a Debian Daughter Distro was that apt allowed graceful dist-upgrades.  This is still largely true.  My box has dist-upgraded from Hoary to Breezy to Dapper to Edgy.I will still try to upgrade when Feisty is stable or nearly so.  I'm not against it, and with what I've learned this last time I'm sure it will go smoother.  I'm pretty much still a newbie so some things that an experienced user might know how to deal with I sometimes do the wrong thing first before I find the right answer.  That was true with this last upgrade.  Most of my problems hinged around broken packages and dependencies.  I also don't mind experimenting, breaking things, and then learning how to fix them.

My upgrade goal is not to do a clean install, but sometimes if things go wrong then that seems like a good choice.  Also I've noticed people attribute poor stability on upgrade to the next version, ie: Dapper -> Egdy.  I don't think this is always the fault of the version but something that hitched in the upgrade process.  So if there is poor stability on upgrade, then testing that with a clean install and comparing them (possibly in two separate partitions) seems logical.

---

