---
title: "Ubuntu server with only Windows clients?"
date: 2009-06-03
forum: Server Platforms
---

### Post by Vunutus on 2009-06-03
I'm about to set up a network for a small office. Essentially, they need a server for database (MySQL), file, and print services. The clients must be running Windows, that is non-negotiable. I want the server to run Ubuntu for a multitude of reasons (most primarily the business has a small budget and doesn't need to be nickel and dimed to death by Microsoft). 

I'm wanting to know about any possible problems I might hit doing this. Obviously Samba is going to be a huge part of this network, but is it pretty seamless? What about active directory on a Linux server? I googled and found an article saying Samba had added active directory support in an alpha release. That article was from 2007. Is it fully released and stable by now?

---

### Post by LepeKaname on 2009-06-03
In my personal experience, you may run out with problems if your printer(s) is/are not supported in Linux. So first, check the model of the printer(s) and see if you can make them work through cups. If that works, then I thing the rest is piece of cake :popcorn:

---

### Post by Vunutus on 2009-06-03
> **LepeKaname said:**
> In my personal experience, you may run out with problems if your printer(s) is/are not supported in Linux. So first, check the model of the printer(s) and see if you can make them work through cups. If that works, then I thing the rest is piece of cake :popcorn:

I don't know the brand/model or anything, but I do know that the printer we will be using (at least for a while) is a VERY old printer (about 10 years old) with 3 million plus pages on it.

Without knowing the specific model, what are the odds that a printer that old will be supported?

---

### Post by LepeKaname on 2009-06-04
I suppose you use that printer from windows, right? What is the printer name? you can also check what drivers is using.
 
In general terms, it is very probable Ubuntu can auto-detect your printer in Linux, if not, you could use standard drivers. However, without the exact driver for that printer model (or at least the closest driver as possible) we can not be sure that will not produce unexpected behaviors (mainly when sending graphics for printing).

Once you can set it up with cups, it is very easy to setup your printer in Windows 2K, XP or greater (I'm not sure about Win98,ME).

---

