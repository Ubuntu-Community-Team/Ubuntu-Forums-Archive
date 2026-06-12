---
title: "Suggestions for GMail notifier?"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fluteflute on 2012-09-29
I've been previously using gm-notify, but that hasn't been updated to work with the new messaging menu API. (see [https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259))

Just wondering if anyone had any suggestions for something that integrates with the messaging menu?

---

### Post by x-shaney-x on 2012-09-29
I haven't tried it in 12.10 but I used an app called unity-mail not long ago (in the default repos).
Has notifications in the messaging menu AND a launcher icon with mail count badge.

---

### Post by jbicha on 2012-09-29
I've not tried it yet, but supposedly unity-webapps-gmail can do what you need. If it works right, Firefox or Chromium might actually suggest you install it instead of you having to figure it out manually.

If you have a Google Apps for Your Domain account, you'll need to wait a bit longer until that [works]("http://pad.lv/1028381") too.

---

### Post by x-shaney-x on 2012-09-29
I was hoping to use the gmail webapp but here it prompts for integration but doesn't work.

---

### Post by jbicha on 2012-09-29
Two other things to try: Add your Google credentials to Online Accounts and log out and log back in to Unity.

Or just wait until nice people fix the bugs...

---

### Post by kostkon on 2012-09-29
> **fluteflute said:**
> I've been previously using gm-notify, but that hasn't been updated to work with the new messaging menu API. (see [https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259))

Just wondering if anyone had any suggestions for something that integrates with the messaging menu?
gm-notify needs an all around update (gconf &#8594; dconf, gtk2 &#8594; gtk3, indicate &#8594; messagingmenu). EDIT: Oh right, it's being tracked already in the bug report you've given so someone will take care of it eventually, I hope.

---

### Post by emdeem on 2012-10-12
Now that we're at RC status, are there any Unity Gmail notifiers that work?

---

### Post by pqwoerituytrueiwoq on 2012-10-12
does mail-notification work in unity?
i have used mail-notification for few years in 10.04

---

### Post by craig10x on 2012-10-12
Google Mail Checker Plus Classic is great if you use Chrome or Chromium...it's available from the extensions section...one of the BEST i have ever used...

---

### Post by baizon on 2012-10-13
I'm using and recommend popper: [https://launchpad.net/popper]("https://launchpad.net/popper")

---

### Post by GreatDanton on 2012-10-13
Instead of Gmail notifier I am using Thunderbird.

---

### Post by ELD on 2012-10-14
> **jbicha said:**
> I've not tried it yet, but supposedly unity-webapps-gmail can do what you need. If it works right, Firefox or Chromium might actually suggest you install it instead of you having to figure it out manually.

If you have a Google Apps for Your Domain account, you'll need to wait a bit longer until that [works]("http://pad.lv/1028381") too.

The problem is gmail has to be open in your browser for the web app to do anything. It needs to work all the time.

---

