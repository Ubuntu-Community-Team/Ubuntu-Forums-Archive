---
title: "Lemur wireless and general instability"
date: 2013-02-05
forum: System76 Support
---

### Post by M4rotku on 2013-02-05
Hello all,

I have been experiencing a wireless problem with my Lemur (lemu2) for a while now.  This has happened before, but at the time the System76 person told me that it was a regular problem and that I should consider upgrading my wireless card.  While I did not like that idea, the problem soon went away and so I didn't worry about it.  The problem is now back with a vengeance.  

When I click on the nm-applet icon to see the various networks, several of the networks, instead of being listed as "Network", are listed as various options "Network, Network-1, Network-2..."  While this is not the core of the problem, I am describing it in hopes that it may be recognized.  The main problem is that when the networks are displayed in this manner, my wireless connection is unstable at best.  The average situation is that I am connected and it is working fine, and then I lose all connectivity, and have to restart my laptop in order to be able to connect to a network successfully.  Most recently, my laptop has also started freezing when this happens.  It is a full-system lockup, and I am not able to escape it via ctrl+alt+f1 or any other method.

In addition, several times a "Ubuntu has experienced an error" pop-up appears, but it is always related to the e-mail notification client (as far as I can tell) and not to the wireless.

If anyone has any ideas as to what is causing these problems or how to solve the problem, please let me know.  I have tried reinstalling NetworkManager, using wicd instead, and booting into different kernels and none of it has solved the problem.

Many thanks,
M4rotku

---

### Post by ccrs8 on 2013-02-06
I really do suggest following System76's suggestion and upgrading the wireless card.  I have a lemu3, but it sounds like you are having the exact problem many others are having:
[http://ubuntuforums.org/showthread.php?t=1916776](http://ubuntuforums.org/showthread.php?t=1916776)

I upgraded the wireless card from the default Realtec to a Intel advanced-n 6230 card, and it fixed all my problems.  The card was dirt cheap ($20-ish) and installing it took about 5 minutes with a screwdriver.

You may want to check with System76 to make sure the lemu2 can use this card (or get their suggestion for what card to upgrade to).

---

### Post by M4rotku on 2013-02-06
ccrs8,

Thank you for replying.  I remember hearing that other people have had this problem, but was not able to find that post to which you linked, so thank you especially for that.  It does seem (as far as I can tell) as though upgrading the wireless would be the best option.  Nevertheless, even though it is just $20, I am somewhat against it just on principle.  As much as I like System76, and want to support them, they shouldn't have sold these lemurs with default chips that don't function properly.  I know that the default hardware is not going to be as nice as the upgrade option, but it should at least work.

At this point, with all of the frustration that it has caused, I am willing to forego my principles and pay extra for a working chip.  However, I don't know if I can do so at the moment, since I need my laptop on a day to day basis to take notes in my classes.  I wonder if they have an option of shipping the chip to me, with some basic installation instructions, instead of me sending my laptop to them.  I don't trust myself to find the proper chip on amazon and ebay.  From my preliminary searching, I am not even sure if that chip is still available.  Maybe System76 can recommend a good one for upgrading.

Many thanks,
M4rotku

---

### Post by isantop on 2013-02-06
> **M4rotku said:**
> ccrs8,

Thank you for replying.  I remember hearing that other people have had this problem, but was not able to find that post to which you linked, so thank you especially for that.  It does seem (as far as I can tell) as though upgrading the wireless would be the best option.  Nevertheless, even though it is just $20, I am somewhat against it just on principle.  As much as I like System76, and want to support them, they shouldn't have sold these lemurs with default chips that don't function properly.  I know that the default hardware is not going to be as nice as the upgrade option, but it should at least work.

At this point, with all of the frustration that it has caused, I am willing to forego my principles and pay extra for a working chip.  However, I don't know if I can do so at the moment, since I need my laptop on a day to day basis to take notes in my classes.  I wonder if they have an option of shipping the chip to me, with some basic installation instructions, instead of me sending my laptop to them.  I don't trust myself to find the proper chip on amazon and ebay.  From my preliminary searching, I am not even sure if that chip is still available.  Maybe System76 can recommend a good one for upgrading.

Many thanks,
M4rotku

The problem with that default chip is that it only fails on some routers. On others (like the ones in our testing environments) it works excellently. It took us nearly a year to even track down the the wireless card was the solid culprit. 

We can definitely ship you a replacement card. It's very easy to replace, and you don't need to send your whole computer in.

---

### Post by M4rotku on 2013-02-06
hey isantop,

That makes a lot more sense.  I was wondering why it works when I am home, but not when I am at school.  And it does seem as though that would be a hard error to find.  I am glad to hear that the chip is easy to switch out.  How do I go about ordering one?  I guess I will go look around the main website for such an option.  Thanks for the help!

---

### Post by ccrs8 on 2013-02-07
> **M4rotku said:**
> That makes a lot more sense.  I was wondering why it works when I am home, but not when I am at school.  And it does seem as though that would be a hard error to find.  I am glad to hear that the chip is easy to switch out.  How do I go about ordering one?  I guess I will go look around the main website for such an option.  Thanks for the help!

Yeah, same here.  Worked fine at home on a normal Linksys router, but then when I traveled it would not work in airports or hotels.  Seems like the wireless networks that required extra authentication (sign in to a webpage, click on "agree", etc.) gave it problems.  No such problems with the new chip.

I don't work for System76, but I'd imagine if you opened a support ticket via the "My Account" section of their website, that will get things started.  I'd recommend providing a link to this thread in the ticket.

---

### Post by M4rotku on 2013-02-08
I filled out a ticket on the System76 website, so I'm marking this problem as solved.  Thanks guys!

---

### Post by cs35 on 2013-07-12
Did you hear back from System76? Did you change the network card from Realtec to Intel? If so, can you share details? I want to explore this option for same problems discussed above on my lemu2.

---

