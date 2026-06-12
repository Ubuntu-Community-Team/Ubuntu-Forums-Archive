---
title: "Do  online Sever Upgrades work?"
date: 2012-12-13
forum: Server Platforms
---

### Post by itpro007ca on 2012-12-13
I'm new to this(not to Linux),so bare with me.

In view of the fact that last year I tried an online upgrade for Ubuntu Desktop 11.04-11.10,which broke the system and I had to do an autmoatic repair,which was never perfect,because sometimes on login,it would go to the command line,comaplin of 'low graphics',and sometimes,on reset,log into Unity perfeectly,I'm a bit cautious.

That also goes because in reading some of the online upgrade threads,I see people's system's become almost and sometimes completely unusable.

I'm just wondering  if anybody has successfully upgraqded the Desktop version and Server versions online?

Currently,I'm running Server 12.04 + Unity,Webmin,LAMP and a few other things.

---

### Post by haqking on 2012-12-13
> **itpro007ca said:**
> I'm new to this(not to Linux),so bare with me.

In view of the fact that last year I tried an online upgrade for Ubuntu Desktop 11.04-11.10,which broke the system and I had to do an autmoatic repair,which was never perfect,because sometimes on login,it would go to the command line,comaplin of 'low graphics',and sometimes,on reset,log into Unity perfeectly,I'm a bit cautious.

That also goes because in reading some of the online upgrade threads,I see people's system's become almost and sometimes completely unusable.

I'm just wondering  if anybody has successfully upgraqded the Desktop version and Server versions online?

Currently,I'm running Server 12.04 + Unity,Webmin,LAMP and a few other things.

it is common sense regardless of the OS or version.

Do backups, upgrade. And if commerical then hopefully you have tested and have a good reason to upgrade.

Online upgrades are always susceptible to failure as are offline, if it is a corporate server do it at a time when the systems are under utilsied etc.

But more than anything have BACKUPS then it doesnt matter if it fails

---

### Post by Cheesehead on 2012-12-13
> **itpro007ca said:**
> I'm just wondering  if anybody has successfully upgraqded the Desktop version and Server versions online?

Yes, many times on many machines, both desktop and server since 2007.

Last full reinstall was in 2009. And that was my own fault, not the upgrade.

Sure, I have been bitten by a few hardware regression bugs on a few upgrades. WiFi in 2010, suspend in 2012, and a few others. But if you file good bug reports, stay involved with the bug, offer to help test solutions, and make a real effort to actually help the triagers and developers identify the problem...they get fixed.

On the upside, the nearly-useless VGA port became very useful, printing went from voodoo-art to easy, Xorg bugs nearly vanished off the map, audio went from scratchy and troublesome to clear and convenient, and Unity went from dead-slow to almost-fast-enough. Those were the unheralded results of hard work by developers, and I'm excited every time I revisit an old issue and discover it fixed.

If you're not new to Linux, the Ubuntu Testing Team is always looking for more volunteers to help create test cases, the Ubuntu Friendly Team is looking for more in-the-wild hardware to test Checkbox upon, the Bug Squad needs help Triaging those bugs and prioritizing the critical showstoppers for the Release Team to work. And the Release Team is always looking for more alpha-testers to identify and confirm new bugs weeks/months before release...so they can be fixed. And *everybody* likes patches that fix those bugs!

---

### Post by CharlesA on 2012-12-13
> **haqking said:**
> it is common sense regardless of the OS or version.

Do backups, upgrade. And if commerical then hopefully you have tested and have a good reason to upgrade.

Online upgrades are always susceptible to failure as are offline, if it is a corporate server do it at a time when the systems are under utilsied etc.

But more than anything have BACKUPS then it doesnt matter if it fails

This x 9000.

I have only done clean installs, but if it is a corp box, an upgrade after backing everything up is a good idea.

---

