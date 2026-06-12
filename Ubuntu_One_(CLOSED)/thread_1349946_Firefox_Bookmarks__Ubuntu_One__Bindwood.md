---
title: "Firefox Bookmarks / Ubuntu One / Bindwood"
date: 2009-12-08
forum: Ubuntu One (CLOSED)
---

### Post by paradigm2 on 2009-12-08
I am playing around with Ubuntu One now and trying to get the shared firefox bookmarks feature working.  One machine is running Ubuntu 9.10 the other is running Ubuntu Netbook Remix 9.10.  Both have Ubuntu One installed and configured.  Both PCs are authorized under the same Ubuntu One account.  Both have the stock Firefox with Bindwood installed.

But nothing is happening.  The bookmarks aren't syncing.  I noticed the desktop did ask me to "allways allow" bindwood access as per the wiki instructed however on the netbook running UNR 9.10, it never did pop up and ask this.  I've tried reinstalling Bindwood on the netbook but it still does nto work or ask for access as it should.  Bindwood is clearly installed as an extension in firefox on the netbook.

Any suggestions on how to resolve this?

---

### Post by paradigm2 on 2009-12-09
A simple reboot solved it.  However I am experiencing the same constant freeze others are on my netbook,  I will try it again later when the bugs are fixed.

---

### Post by joshuahoover on 2009-12-15
> **paradigm2 said:**
> A simple reboot solved it.  However I am experiencing the same constant freeze others are on my netbook,  I will try it again later when the bugs are fixed.

Please see this new FAQ I just created: [https://answers.edge.launchpad.net/bindwood/+faq/859](https://answers.edge.launchpad.net/bindwood/+faq/859)  This points you to a Bindwood specific PPA you can use to get the latest version that performs much better. :)

Thank you,

Joshua

---

### Post by paradigm2 on 2009-12-18
> **joshuahoover said:**
> Please see this new FAQ I just created: [https://answers.edge.launchpad.net/bindwood/+faq/859](https://answers.edge.launchpad.net/bindwood/+faq/859)  This points you to a Bindwood specific PPA you can use to get the latest version that performs much better. :)

Thank you,

Joshua

Thanks.  I will install it and give it another go and report back. :)

edit: I found this which I think incorporates the fix?
[https://launchpad.net/~urbanape/+archive/bindwood-exp](https://launchpad.net/~urbanape/+archive/bindwood-exp)

---

### Post by paradigm2 on 2009-12-18
Yes it's definitely working a lot better now (I also am using the ubuntuone beta ppa with the bindwood beta ppa).  It seems to be functional after that initial delay and is not causing any problems so far.  Thanks again!

---

### Post by gibbylinks on 2009-12-19
> **paradigm2 said:**
> I am playing around with Ubuntu One now and trying to get the shared firefox bookmarks feature working.

Personally I find the "xmarks" add in for Firefox is brilliant for sharing bookmarks. I can sync all my bookmarks whether I'm using my Linux laptop, Win XP desktop or my Vista using IE at work.

I also like the profiles feature so I can use a different set for work and home.

:guitar:

---

### Post by manoriax on 2009-12-21
Is there a way to sync the CouchDB with Google Chrome?

---

### Post by stuartlangridge on 2009-12-21
> **manoriax said:**
> Is there a way to sync the CouchDB with Google Chrome?
There isn't right now, but we're working on it. The problem is that there isn't an easy way to have Chrome find out where your desktopcouch is without writing a compiled "NPAPI" plugin, which will take some time. If someone wanted to chip in and help with that we'd be more than happy to give some pointers as to what needs doing; talk to me (aquarius) or urbanape on #ubuntuone on IRC!

---

