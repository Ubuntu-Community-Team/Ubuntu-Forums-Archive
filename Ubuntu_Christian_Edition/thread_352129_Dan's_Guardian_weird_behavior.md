---
title: "Dan's Guardian weird behavior"
date: 2007-02-02
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-02-02
Ok, here is something I have finally nailed down with Dan's guardian.  I notice whenever I use my wireless I get a lot of tiny proxy errors.  I have no idea why, I click a link and it takes forever to load, and then it gives me a white page with a tiny proxy error at the top of the page something about a cache error or something like that.  I have had this problem before, but that was when I was using the DHCP IP address with wireless.  Now I have a static IP address with wireless and still have the same problem.  However I have noticed that if I plug into my ethernet cable, 1.  It works faster (not really noticeable when I didn't have dan's guaradian before)  2.  I never get the tiny proxy errors.  Oh, another funny thing about the wireless connection.  If I disable Dan's Guardian, I occasionally still get the tiny proxy errors when running the wireless.  I don't notice any problem with the wireless when not running Dan's guardian (when it wasn't installed.)   

1.  Does anyone else have this problem?  Or is this an isolate incidence? 

2.  Does anyone have any idea why this could be a problem? (If this is an isolated incidence, I guess there would not be much reason to troubleshoot it.)

I'm using a DWL-g630 D-Link airplus wireless card. (works out of the box with Ubuntu - always has - that is a big factor that drew me to Ubuntu!)

Shane

---

### Post by mhancoc7 on 2007-02-03
I have had this same issue. I have not been able to figure out why this happens.

The reason that you still get the error is that the Disable feature in the updated GUI does not completely disable it. I mean your connection still runs through tinyproxy it just does not get filtered. The next release of Ubuntu CE will address this.

In fact, I have attached what will probably be the GUI in the next release. It has not been fully tested, but it should work just fine. This way you can completely disable dansguardian.

Let me know what you think about it.

God Bless, Jereme

---

### Post by danoyoto on 2007-02-03
It sounds like tiny proxy has a timeout limit.  If the page doesn't load within a certain time frame, then you get that 'cannot load page' page.  When you're on a wired link speed is always good (DSL?)  So I think the issue is your wireless speed.  I have no idea how to address that (I don't use wireless) but if you post a thread with your card and setup in the wireless forum I'm sure someone will help!

---

### Post by shane2peru on 2007-02-03
> **mhancoc7 said:**
> I have had this same issue. I have not been able to figure out why this happens.

The reason that you still get the error is that the Disable feature in the updated GUI does not completely disable it. I mean your connection still runs through tinyproxy it just does not get filtered. The next release of Ubuntu CE will address this.

In fact, I have attached what will probably be the GUI in the next release. It has not been fully tested, but it should work just fine. This way you can completely disable dansguardian.

Let me know what you think about it.

God Bless, Jereme

Ok, thanks Jereme.  Hey the deb worked great!  No problems to install it.

> **danoyoto said:**
> It sounds like tiny proxy has a timeout limit.  If the page doesn't load within a certain time frame, then you get that 'cannot load page' page.  When you're on a wired link speed is always good (DSL?)  So I think the issue is your wireless speed.  I have no idea how to address that (I don't use wireless) but if you post a thread with your card and setup in the wireless forum I'm sure someone will help!

I recently switched back to using UCE.  Before I had been using wireless flawlessly for months.  I really didn't notice much speed difference.  I'm on DSL, and my wireless card is a G and my wireless hub too.  I have used a B (or whatever the older letter was) before and certainly can tell a difference between wireless and the wired.  This may be a hair slower, but not much at all.  I don't know all the specs.  I'm thinking you are on the right track though.  It must be something to do with the tiny proxy settings not getting all the info it needs or something fast enough.  I will do some searching around.  I'm still curious if this is just a problem with my wireless setup, or if it can be confirmed to be a problem with others.  If it is not an isolated incidence there should be something on google.  Thanks for the replies.

Shane

---

### Post by mhancoc7 on 2007-02-03
@shane2peru
Great! Just let me know if you have any trouble with it since it will be in the next release.

God Bless, Jereme

---

### Post by gladman on 2008-02-28
i downloaded the DEB file and installed it, but do i run it? and whats GUI mean

---

### Post by TravMan63 on 2008-03-03
GUI is an acronymn for 'Graphical User Interface' - it gives you the things to click on and lets you use the mouse with it (as opposed to a text interface - where you have to type it all in)

---

