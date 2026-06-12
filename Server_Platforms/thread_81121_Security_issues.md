---
title: "Security issues"
date: 2005-10-23
forum: Server Platforms
---

### Post by ScatterBrain on 2005-10-23
I have a couple of Hoary based servers floating around and am contemplating putting Breezy out on all new servers that I tend to.

Early last week, one of them got hacked due to a PHP injection weakness in the Cacti package.  This weakness allowed the attacker to install a rootkit and basically have root access to the box - they added a user account to the machine among other things.

This weakness in Cacti (as far as I can tell) should have been taken care of with v0.8.6f, but Hoary is supplying v0.8.5-8.

This fact has made wonder whether or not I should be using "packaged" applications (re apt-get install....).  I know that no matter what, there will be bugs in software and I can't be 100% safe no matter what.  But I'm wondering if I had been running the latest version of Cacti (and compiled from source where applicable) if I would have been hacked.

Since I'm sure that more expeienced people than I are browsing this forum, I put the question to you:  How do you install packages on production servers?  Do you install the base system and then add everything with apt/synaptic or compile from source?  I'd like to hear why no matter which direction you choose.

I'm not wanting to start a flame war, I'm trying to learn and I hope that everyone responding to this post will keep that in mind.

---

### Post by LordHunter317 on 2005-10-23
[QUOTE=ScatterBrain]Since I'm sure that more expeienced people than I are browsing this forum, I put the question to you:  How do you install packages on production servers?[/quote]Packages from the distributor, including security updates.

I'd only ever consider source built code in two situations:[list][*]When I need compiled-in features upstream doesn't provide (rare in Debian and Ubuntu)[*]When they aren't releasing security updates in a timely fashion[/list]

---

### Post by dbee on 2005-10-23
I like to put in everything myself ... I mean if you just 

apt-get install 

then you only have yourself to blame when you get hit by some script-kiddie. 
Not to talk about the fact that you'll be vulernable to the exact same type of attacks that the other x amount of people who use

apt-get install  

are vulnerable to.

But then I'm a fairly paranoid type of guy (with time on my hands :)  )

---

### Post by LordHunter317 on 2005-10-24
[QUOTE=dbee]I like to put in everything myself ... I mean if you just 

apt-get install 

then you only have yourself to blame when you get hit by some script-kiddie.[/quote]And you still have yourself to blame when your custom-compiled version gets hacked.  This maeks no sense. 

> Not to talk about the fact that you'll be vulernable to the exact same type of attacks that the other x amount of people who use

apt-get install  

are vulnerable to.Unless the exploit came from an Ubuntu patch, you're still vulnerable.

---

### Post by cactus on 2005-10-24
For php based apps, I generally just download them from the developer site.

---

### Post by ScatterBrain on 2005-10-25
Well, it appears as though Cacti is located in "Universe" and as such does not warrant security updates.  It is a PHP application and I could simply replace the code with the newer version.

What it basically boils down to is:

[LIST=1]
[*]I should have paid more attention to the box in the first place
[*]I should look for the developer for this particualr application - and use their updated version when needed
[/LIST]

I appreciate the views from all that responded.

---

