---
title: "Ubuntu repos greatly out of date?"
date: 2009-04-19
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-04-19
I have Transmission installed on both OSX and Ubuntu when I noticed that the OSX version has more features than the Ubuntu version. Such as the ability to restrict the use of bandwidth to certain times of the day.

So I compared the version numbers and it turns out the Ubuntu repos only have version 1.34 while the latest version is 1.52. So I went to Transmission's website and 1.34 came out in September 2008. Since then there have been five new releases. It's not like Transmission is an obscure piece of software that doesn't get used by very many people. It's the default BitTorrent client for the distro. If a widely used piece of software like Transmission is five versions out of date how out of date are some of the more obscure packages?

I'm sure they're doing the best the can with what they have but the people who run Ubuntu's software repos should get more people to maintain the packages and make sure things are kept more up to date.

---

### Post by yabbadabbadont on 2009-04-19
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

By default, they won't update the version of a package until the next Ubuntu release.  Only for security issues and possibly major bugfixes.  You can get some newer versions of some software by enabling the backports repository as explained in the link above.

---

### Post by blueshiftoverwatch on 2009-04-19
> **yabbadabbadont said:**
> [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

By default, they won't update the version of a package until the next Ubuntu release.  Only for security issues and possibly major bugfixes.  You can get some newer versions of some software by enabling the backports repository as explained in the link above.
Thanks, although I feel very stupid now.

Even the backports people don't have a newer version of Transmission. If a new release wasn't coming out on Thursday I'd install it manually. But I can wait.

---

### Post by Vostrocity on 2009-04-20
Same thing with FF add-ons. :(

---

### Post by cariboo on 2009-04-20
Jaunty has version 1.51, which was the version available at feature freeze.

Jim

---

### Post by jmszr on 2009-04-20
blueshiftoverwatch,

You can get Transmission 1.52 here: [http://www.getdeb.net/](http://www.getdeb.net/) .

---

### Post by =^,^= on 2009-04-20
Why dont you just add the transmission repo from:

[http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

Then everytime a new version of transmission is released its delivered straight to you!

---

### Post by Kareeser on 2009-04-20
+1 on adding Transmission's beta builds repo to your list of software sources :)

I do the same with WINE as well.

---

### Post by namegame on 2009-04-20
I'd imagine that you could also compile it from source if you're into that kind of thing.

---

### Post by billgoldberg on 2009-04-20
> **blueshiftoverwatch said:**
> I have Transmission installed on both OSX and Ubuntu when I noticed that the OSX version has more features than the Ubuntu version. Such as the ability to restrict the use of bandwidth to certain times of the day.

So I compared the version numbers and it turns out the Ubuntu repos only have version 1.34 while the latest version is 1.52. So I went to Transmission's website and 1.34 came out in September 2008. Since then there have been five new releases. It's not like Transmission is an obscure piece of software that doesn't get used by very many people. It's the default BitTorrent client for the distro. If a widely used piece of software like Transmission is five versions out of date how out of date are some of the more obscure packages?

I'm sure they're doing the best the can with what they have but the people who run Ubuntu's software repos should get more people to maintain the packages and make sure things are kept more up to date.

Wow, before going on a rant you should do your research.

Ubuntu isn't a rolling release distro. 

All the packages (normally) only get securitry updates.

This is for stability purposes.

It you want to be up to date all the time, use another distro.

---

### Post by Vostrocity on 2009-04-20
Actually, yabbadabbadont already said that. And OP replied. So no need to bash him.

---

### Post by billgoldberg on 2009-04-20
> **Vostrocity said:**
> Actually, yabbadabbadont already said that. And OP replied. So no need to bash him.

And yet I did.

He'll think twice before making an uninformed rant again after his thread failed.

---

### Post by megamania on 2009-04-20
> **billgoldberg said:**
> And yet I did.

He'll think twice before making an uninformed rant again after his thread failed.
Unfortunately, the OP wasn't making a rant. Looks like you need to make a rant, though.

After 5 years with Ubuntu (and only Ubuntu), I agree somehow with the OP. There are some packages which is safer not to update for stability reasons (Gnome, for example).
On the other hand, updating Jpilot, xChat, Transmission or Tomboy is very *unlikely* to bring stability issues.

So, as you can see there can be informed disagreement. :)

---

### Post by SunnyRabbiera on 2009-04-20
This is sort of why we have ppa's, not every release is a major security patch or critical update.

---

### Post by billgoldberg on 2009-04-20
> **megamania said:**
> Unfortunately, the OP wasn't making a rant. Looks like you need to make a rant, though.

After 5 years with Ubuntu (and only Ubuntu), I agree somehow with the OP. There are some packages which is safer not to update for stability reasons (Gnome, for example).
On the other hand, updating Jpilot, xChat, Transmission or Tomboy is very *unlikely* to bring stability issues.

So, as you can see there can be informed disagreement. :)

Sure, I feel the same way.

But everyone knows that this isn't the case.

Yet the OP makes it sound like the Ubuntu folk and Canonical aren't able to keep their repos up to date, while it's just for stability's sake they aren't doing it.

---

