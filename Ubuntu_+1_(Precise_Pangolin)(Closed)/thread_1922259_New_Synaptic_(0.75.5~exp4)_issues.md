---
title: "New Synaptic (0.75.5~exp4) issues"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-02-08
Todays update of Synaptic, version 0.75.5~exp4, brought some problems.

1. Now we have twice as many scroll bars as we used to. And they do not disappear.
2. Quick search (apt-xapian-index) is not working anymore.

Has anyone else found something else too?

Oh yes, and I have experienced one crash too.
Similar to Dino's bug report (928975):
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928975](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928975)

---

### Post by bmbaker on 2012-02-08
yes i get a crash when after en/disabling repositories and then refreshing I filed a bug on the link you provided harry33

---

### Post by mc4man on 2012-02-08
Been working ok, (no crashes yet
Don't know the purpose of the horizontal scrollbar in description box, text always resizes to box size

The quick search works, just can't type in (can be pasted into, then highlighted & deleted after use

---

### Post by dino99 on 2012-02-08
Quick Filter : focus lost

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955)

to me its a regression since ~exp3

---

### Post by ventrical on 2012-02-08
no crash here .. works great ..

---

### Post by dino99 on 2012-02-08
> **ventrical said:**
> no crash here .. works great ..

I got these issues while logged as gnome-classic on i386. Purging then reinstalling does not help.

---

### Post by ventrical on 2012-02-08
> **dino99 said:**
> Quick Filter : focus lost

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955)

to me its a regression since ~exp3


yep .. no field input activity

---

### Post by ventrical on 2012-02-08
right click over feild while hovering and select <insert unicode control character> <left ot right> and the colours and brands will come up at least.


edit .. but those settings are not saved ...

---

### Post by ventrical on 2012-02-08
> **dino99 said:**
> I got these issues while logged as gnome-classic on i386. Purging then reinstalling does not help.

 I'm using Unity 3D. It's not working .. your description is correct.!
If you hover your mouse over ,Quick Filter Field, and then right click, choose insert unicode .. etc.. and click left to right and the colous feilds and Ubuntu logos will brand up... but those settings are not saved.

---

### Post by dino99 on 2012-02-08
> **ventrical said:**
> right click over feild while hovering and select <insert unicode control character> <left ot right> and the colours and brands will come up at least.


edit .. but those settings are not saved ...

i've not tweaked the "right click" before, and i've made your proposing: now the "auto removable" list has been emptied :( and dont know exactly about the default settings used.
Tried a few settings but still cant get the field focus, so cant insert a package name :(

Well, switched back/forward menus, and get back the previous list of "removable". :)

---

### Post by bmbaker on 2012-02-08
even copy/paste into search field make synaptic stall

---

### Post by ventrical on 2012-02-08
> **dino99 said:**
> i've not tweaked the "right click" before, and i've made your proposing: now the "auto removable" list has been emptied :( and dont know exactly about the default settings used.
Tried a few settings but still cant get the field focus, so cant insert a package name :(


  Thats what I meant to say .. The 'field focus' is not working as you reported. So I right clicked on that field and there is a menu that gives the option to insert unicode and I chose the first Left to Right and the colours and logos patched over to the list but still no field focus..

---

### Post by ventrical on 2012-02-08
Just noticed this !!

edit ... ok .. means nothign .. ignore..

---

### Post by ventrical on 2012-02-08
And on my system with the previous version of synaptic :

---

### Post by dino99 on 2012-02-08
> **ventrical said:**
> And on my system with the previous version of synaptic :

Mine is set to the most higher choice, but should not break anything as its the dev version.

---

### Post by ventrical on 2012-02-08
> **dino99 said:**
> Mine is set to the most higher choice, but should not break anything as its the dev version.


yes .. correct .. thank you ..

---

### Post by Bobhuber on 2012-02-08
I'm unable to enter anything in the quick filter box in the Synaptic Packager Manager.
Anyone else having this problem ??

OOPS - See the other posts now. Disregard.

---

### Post by Harry33 on 2012-02-08
> **Bobhuber said:**
> I'm unable to enter anything in the quick filter box in the Synaptic Packager Manager.
Anyone else having this problem ??

OOPS - See the other posts now. Disregard.

We already have this thread here:

[http://ubuntuforums.org/showthread.php?t=1922259](http://ubuntuforums.org/showthread.php?t=1922259)

---

### Post by cariboo on 2012-02-08
Merged two threads on the same subject.

---

### Post by dino99 on 2012-02-08
> **Bobhuber said:**
> I'm unable to enter anything in the quick filter box in the Synaptic Packager Manager.
Anyone else having this problem ??

OOPS - See the other posts now. Disregard.

go to bug report and add "affect me too" on top page.

---

### Post by kyleabaker on 2012-02-08
> **mc4man said:**
> Don't know the purpose of the horizontal scrollbar in description box, text always resizes to box size

Yes, this is odd.


> **dino99 said:**
> Quick Filter : focus lost

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955)

to me its a regression since ~exp3

Thanks for the link, added my +1. I just noticed this earlier today.

---

### Post by dino99 on 2012-02-09
Have updating my system this morning, got several installed packages ready to upgrade, but some were also silently added into the archives , i mean usually synaptic list these new packages into "new in archives" in the left side pane when using "status", but today i've not seen this menu opened.

---

### Post by ventrical on 2012-02-09
Yup ... new kernel update and running on another system, Unity 2D.. nothing .. no can type in field.

---

### Post by dino99 on 2012-02-09
> **ventrical said:**
> Yup ... new kernel update and running on another system, Unity 2D.. nothing .. no can type in field.

Thanks for confirmation. Report made, set your "affect me too" please.
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/929597](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/929597)

---

### Post by ventrical on 2012-02-09
> **dino99 said:**
> Thanks for confirmation. Report made, set your "affect me too" please.
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/929597](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/929597)

Done.

---

### Post by dino99 on 2012-02-09
> **ventrical said:**
> Done.

Thanks, but i'm confused, i made an other update checking a few minutes back, and get that "new in repositories" back; so it seems a transitional issue, wait & see.

---

### Post by ventrical on 2012-02-09
> **dino99 said:**
> Thanks, but i'm confused, i made an other update checking a few minutes back, and get that "new in repositories" back; so it seems a transitional issue, wait & see.


Just got that now . baffling. I think your right. But I also think it may have to do with a depends  .. err.. <menu> I think , which reported a conflict.

---

### Post by ventrical on 2012-02-09
OK.. synaptic crashed and destroyed itself after last update.. can't send bug report.

will try reboot.

---

### Post by dino99 on 2012-02-09
> **ventrical said:**
> OK.. synaptic crashed and destroyed itself after last update.. can't send bug report.

will try reboot.

dont worry, crash is a new feature :)

---

### Post by ventrical on 2012-02-09
> **dino99 said:**
> dont worry, crash is a new feature :)

 yeah .. that s right .. just remembered...

ok .. synaptic is back after reboot and the <new in repositories> comes and goes. I think it is a feature perhaps .. that after there new files are upgraded, being that there is nothing left inrepositories.. it may be a bug..??

---

### Post by dino99 on 2012-02-09
> **ventrical said:**
> yeah .. that s right .. just remembered...

ok .. synaptic is back after reboot and the <new in repositories> comes and goes. I think it is a feature perhaps .. that after there new files are upgraded, being that there is nothing left inrepositories.. it may be a bug..??

synaptic also use libc6 , as this one seems to have some trouble, i'm waiting a new libc6 package before reporting against other packages using it. Should get a new one very soon as its a critical issue for the whole system.

---

### Post by ventrical on 2012-02-09
> **dino99 said:**
> synaptic also use libc6 , as this one seems to have some trouble, i'm waiting a new libc6 package before reporting against other packages using it. Should get a new one very soon as its a critical issue for the whole system.


Thanks for heads up .. I'll wait for the pkg also..

---

### Post by ventrical on 2012-02-09
Ok.. new possibly realated bug.



[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/929689](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/929689)

please see description

---

### Post by dino99 on 2012-02-09
> **ventrical said:**
> Ok.. new possibly realated bug.



[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/929689](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/929689)

please see description

Most of the reports about libc6 or synaptics have the quite same symptom: "read an unknown vma" meaning troubles dealing with memory (data buffer lost, confusion then crash). All of this related to gui only :)

---

### Post by Harry33 on 2012-02-09
There is a new update to Synaptic in repos soon.

Here:
[https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp5]("https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5%7Eexp5")

> **Changelog**

          synaptic (0.75.5~exp5) experimental; urgency=low
*common/rpackage.cc:
- use SetCandidateRelease() when forcing a version to ensure
that experimental/backports work better
* common/rpackageview.cc:
- add subview for not-automatic package in the origins filter,
this is useful for e.g. debian/experimental or ubuntu-backports
Note that you need to force the version using the menu:
"Package/Force Version"'
-- Michael Vogt <email address hidden>  Wed, 08 Feb 2012 21:21:43 +0100      




Anyways, seems it does not fix anything.

---

### Post by dino99 on 2012-02-09
> **Harry33 said:**
> There is a new update to Synaptic in repos soon.

Here:
[https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp5]("https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5%7Eexp5")




Anyways, seems it does not fix anything.

Will know better after getting the new libc6 packages

---

### Post by ventrical on 2012-02-09
I downloaded the new synaptic updates, rebooted, clicked synaptic from the Unity panel, entered my password and  it killed my Dell.

 :)
 blackspace....

 ok.. will re-boot again...

  oh joy .. the breakage ! :)

---

### Post by ventrical on 2012-02-09
yep... no difference.. got my screen back..

---

### Post by ventrical on 2012-02-09
> **dino99 said:**
> Will know better after getting the new libc6 packages

libc6 update fixed nothing !

---

### Post by Harry33 on 2012-02-10
> **ventrical said:**
> libc6 update fixed nothing !

Seems to be so.
At least the quick search function is off.

However, my Synaptic has not crasher any more, perhaps this is a little improvement here.

---

### Post by dino99 on 2012-02-10
> **Harry33 said:**
> Seems to be so.
At least the quick search function is off.

However, my Synaptic has not crasher any more, perhaps this is a little improvement here.

Got new crash today, but even if we got  new libc* packages, none of the numerous dependants have been rebuild with the new libc6, so still waiting for them.

---

