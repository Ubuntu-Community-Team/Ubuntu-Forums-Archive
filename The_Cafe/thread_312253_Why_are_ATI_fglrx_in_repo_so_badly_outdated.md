---
title: "Why are ATI fglrx in repo so badly outdated?"
date: 2006-12-04
forum: The Cafe
---

### Post by mahy on 2006-12-04
Is there any profound reason for restricting Edgy users (and below) to fglrx version 8.28.somethin, while Feisty users can enjoy 8.31.something? If somebody already downloads the driver package from ATI's page, makes a .deb package out of it and places it into Feisty's repository, why not place it into Edgy's repo AS WELL? It has nothing to do with backporting, coz the darn drivers are closed-source. Besides, with each new release the drivers get more and more stable and performance increases.

With the move to include binary drivers in Feisty release cd, i'd say users' satisfaction is quite high on Ubuntu developers' priority list. So WTH do i have to install fglrx drivers manually to keep up with the current version?

Mahy

---

### Post by kvonb on 2006-12-04
Yes because support for the 9200 and below cards is dropped in drivers higher than 8.28.8 (courtesy of ATI) and people like me would have no driver support :)

---

### Post by siimo on 2006-12-04
> **kvonb said:**
> Yes because support for the 9200 and below cards is dropped in drivers higher than 8.28.8 (courtesy of ATI) and people like me would have no driver support :)

ever heard of the OSS driver?  it gives me better performance and FPS in games than ati binary driver on my 9250 Radeon if i turn Hyper-Z and Page flipping on.

---

### Post by kvonb on 2006-12-04
> ever heard of the OSS driver? it gives me better performance and FPS in games than ati binary driver on my 9250 Radeon if i turn Hyper-Z and Page flipping on.

It looks like I worded that badly, I didn't mean that I use it, just that people with 92xx series cards could be left out.  I've read that Feisty will include the binary drivers, which means that they logically will provide the 8.28.8 version so as to provide support for the 92xx series, I do not know if they are planning to make the binary driver the default (I really hope not), but there is a lot of flaming going on over the issue

I use the OSS driver exclusively on my system, it is absolutely fabulous and I do NOT plan on using the ATI binary.  The devs did a great job on it, I run Cedega/QuakeII/Wolfenstein/ET/Glest and all with Beryl as well :).

siimo: can you give me the xorg.conf lines for enabling Hyper-Z and Page flipping please?  Or point me to a how-to?

Regards, Kev :)

---

### Post by mahy on 2006-12-04
> **kvonb said:**
> Yes because support for the 9200 and below cards is dropped in drivers higher than 8.28.8 (courtesy of ATI) and people like me would have no driver support :)

Well, you say you're using OSS drivers, and what if you upgrade to Feisty?

---

### Post by kvonb on 2006-12-04
I assume (and hope) that they will be including the OSS driver as default, but give the user the choice to install the binary driver.  Like I said there are a lot of arguments happening over this but there is plenty of time for them to sort it out, I have confidence that they will do the right thing in the end :mrgreen:.

If not then I will have to start saving up for a new video card and stick with Edgy till I can afford to upgrade.

Maybe nvidia this time for maximum compatibility.

---

### Post by mahy on 2006-12-04
unfortunately, i have the radeon X300 card and the OSS driver is no option for me. That's why i'd welcome easy installation of up-to-date drivers.

---

