---
title: "office 2007"
date: 2009-10-05
forum: Wine
---

### Post by rygar on 2009-10-05
I just installed Office 2007 using one of the guides available on this forum, and things seem to be working great (so far) except for one thing...

It won't let me enter a product key!  When I open Word or Excel, the box pops up and tells me I need to enter a product key, but it won't let me put my cursor in the box where I enter the key.

How can I fix this??

Thanks!
Jeff

---

### Post by hikaricore on 2009-10-06
I'm not sure about fixing it but have you tried alternate methods such as the tab key to move to the entry box?

---

### Post by wilee-nilee on 2009-10-06
Did you install in windows or linux.

---

### Post by hikaricore on 2009-10-06
> **wilee-nilee said:**
> Did you install in windows or linux.

......

---

### Post by rygar on 2009-10-06
yup, i've tried using tab and such, but it still doesn't work :(

and i'm installing it in linux, under wine...

---

### Post by wilee-nilee on 2009-10-07
You can activate the key loader by clicking on the icon in the top right corner then word options then resources you will see a list click on activate Microsoft word. Hopefully this will will work.

---

### Post by rygar on 2009-10-07
what icon in the top right corner?

---

### Post by NightMKoder on 2009-10-07
I think he meants top left corner. The office logo.

---

### Post by rygar on 2009-10-07
> **NightMKoder said:**
> I think he meants top left corner. The office logo.

Thanks, that is indeed what he meant, but unfortunately this just brings up the same screen that asks me to enter my product key--and I still can't enter anything in the text box.

---

### Post by wilee-nilee on 2009-10-08
> **rygar said:**
> Thanks, that is indeed what he meant, but unfortunately this just brings up the same screen that asks me to enter my product key--and I still can't enter anything in the text box.

 Sorry about the wrong corner, I am sure MS wants you to use word so might try calling them for help, even if your running it in Linux.

---

### Post by hikaricore on 2009-10-08
> **wilee-nilee said:**
> Sorry about the wrong corner, I am sure MS wants you to use word so might try calling them for help, even if **you're** running it in Linux.

Microsoft isn't going to help anyone run Office on Linux... that is retarded.

~

What version of wine are you using?  This does sometimes matter.
Have you read the appdb page for office to see if anyone's listed any workarounds?

---

### Post by wilee-nilee on 2009-10-08
> **hikaricore said:**
> Microsoft isn't going to help anyone run Office on Linux... that is retarded.

~

What version of wine are you using?  This does sometimes matter.
Have you read the appdb page for office to see if anyone's listed any workarounds?

 Having you call me retarded is a COC violation I will not report as I am not offended, but you might change it to a more PC response to protect yourself.

---

### Post by hikaricore on 2009-10-08
nevermind I'm pming you about this wilee, i'm tired of thread drama

---

### Post by rygar on 2009-10-16
managed to fix it, for anyone else having this problem here's what to do:

i had listed a few overrides in winecfg libraries, such as

riched20 - native
riched32 - native
usp10 - native,builtin

i did this because several tutorials told me to do so.  however, after removing all of these, i was able to enter a serial number.

however, after installation is complete (after you have entered the serial), you need to re-enable them in order to activate the software!  all fixed!

by the way, i'm using jaunty and wine 1.1.31

---

### Post by benhur99ph on 2009-10-18
I just installed MS Office 2007 on my Ubuntu 9.04 machine yesterday. I've tested Word, Excel, and Powerpoint and they all work fine. The one glitch that I experienced was when I was trying to insert a clipart. There's a weird error... but I don't really use cliparts anyways so it doesn't really matter.

I installed it on Wine 1.1.31 ... :D

---

### Post by cabrey on 2009-10-18
When you originally installed it in Wine, didn't it ask you for the product key? Why is it asking for it after the fact?

---

