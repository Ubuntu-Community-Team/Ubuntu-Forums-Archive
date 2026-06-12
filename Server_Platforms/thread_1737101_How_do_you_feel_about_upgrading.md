---
title: "How do you feel about upgrading?"
date: 2011-04-23
forum: Server Platforms
---

### Post by HighCommander540 on 2011-04-23
Hello, other awesome Ubuntu users. I run my own Ubuntu home server for my own purposes (version 8.04).

I would like to hear from the other users that do similar things about their upgrading experiences? I am a big fan of 8.04, but I can't always install the things I want (without a big hassle).

Is it worth upgrading? Are there any regressions that cause major instability or just a lot of re-learning involved? Or is it just the same experience but better?

I would really just like to hear from people. Because I want to upgrade but I have my doubts about getting more programs and different features. (I know lots of companies that stick with the same version forever)

---

### Post by nickleboyblue on 2011-04-23
Some of the latest and greatest features are only available (or at least, a lot more easily available) in newer releases.  I have never had any issues with upgrading on my own machines.  The biggest issue is how you decide to upgrade.  Personally, on a desktop simple upgrading is fine, but on a server, I prefer to do the upgrade as a fresh install.  If that's the road you take, make sure you know what applications you need, backup any configuration files you have custom-edited, etc.  Once you've done this, an upgrade should make up for any hassle with how easy it is to use.

As for changes, well, I wouldn't know about server changes since your version, but I don't believe they will be particularly difficult to get used to.

---

### Post by H4rm0ny on 2011-04-23
> **HighCommander540 said:**
> Hello, other awesome Ubuntu users. I run my own Ubuntu home server for my own purposes (version 8.04).

I would like to hear from the other users that do similar things about their upgrading experiences? I am a big fan of 8.04, but I can't always install the things I want (without a big hassle).

Is it worth upgrading? Are there any regressions that cause major instability or just a lot of re-learning involved? Or is it just the same experience but better?

Well there certainly isn't a lot of re-learning. Maybe the odd very tightly focused area such as OpenLDAP configuration gets changed enough to make you need to go back to the docs, but basically you'll be doing everything the same way you always did. I mean if you're talking about Server, then things don't change that radically that often at the level of how you use it.

It depends what you use your installation for. I have a Samba file server on mine, a music streaming server for my radio plays and one of my email accounts is served from it via IMAP. Those aren't things that get changed around a lot or need the latest and greatest update (other than security fixes, of course!). So it's fine for the server to just sit there doing its thing year on year.

That said, I'm upgrading it to Narwhal this morning because I need to reinstall anyway due to complete hardware overhaul. Well, I don't need to reinstall, but I might as well. You should set your server up so that it's very easy to reinstall / upgrade, e.g. /srv on its own partition, back up all your configuration files. And then at that point I don't carry out an dist-upgrade, I actually re-install the whole thing from scratch whilst preserving my data partitions.

For desktop, I always grab the latest and greatest: there's a steady turn over of cool features and I never know when I might want to stick in some new thing that isn't available (easily) for a previous version. For servers, I'm happy just ticking along with whatever the current LTS is.

That said, if you're still on 8.04, I'd probably grab the new 11.04 beta and whack that on (after backing everything up!) just for the Hell of it.

Hope this helps. Could answer more if we knew what you used your server for.

H

I would really just like to hear from people. Because I want to upgrade but I have my doubts about getting more programs and different features. (I know lots of companies that stick with the same version forever)[/QUOTE]

---

### Post by HermanAB on 2011-04-23
Hmm, an old curmudgeon here...

I learned years ago, never to upgrade a Linux system.  I rather install from scratch every two or three years, do all the updates, make sure it works properly, then I turn auto-updates off and leave the thing alone for the next few years.

---

### Post by HighCommander540 on 2011-05-02
> **HermanAB said:**
> Hmm, an old curmudgeon here...

I learned years ago, never to upgrade a Linux system.  I rather install from scratch every two or three years, do all the updates, make sure it works properly, then I turn auto-updates off and leave the thing alone for the next few years.

That's what I meant. I was just referring more of doing the switch itself. I have had your same experience upgrading almost never works how you want it to.

Thanks everyone! I will be upgrading really soon, so I can use the programs I am trying to.

---

