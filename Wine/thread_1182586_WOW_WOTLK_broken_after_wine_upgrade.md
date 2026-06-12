---
title: "WOW WOTLK broken after wine upgrade"
date: 2009-06-09
forum: Wine
---

### Post by dre_in_ham on 2009-06-09
hi,
i had a perfectly functioning wow install on 8.10 (fully updated) using fglrx on a radeon x1600 with wine 1.1.22.
As soon as i upgraded to wine 1.1.23 wow crashes when i try to start it. Could it have something to do with the new direct 3d features in this wine release? Are any other users having issues?
What technical details are needed to look into this?
As soon as i downgraded to to 1.1.22 wow worked again!

---

### Post by hikaricore on 2009-06-09
So 1.1.22 works?  Then just stay with it.
There is probably a regrssion in 1.1.23.

---

### Post by dre_in_ham on 2009-06-09
yea looks like it. not keen to turn the big regression testing wheel, was just wondering if its something wine or their users need to be aware of. Wine 1.1.22 brought me quite a big speed increase in 3d games so i def dont want to sit forever on one version in case future version offer even more. 

Although since there is wow realm maintenance on tuesdays i can pop in my 9.04 and do some testing there (which i sometimes do anyway to test the open source ati drivers) if anyone wants\needs me to....

---

### Post by NightMKoder on 2009-06-09
1.1.23 set the offscreenrenderingmode to fbo by default. It used to be backbuffer. Look up useful registry key entries and set it yourself. ATI is notorious for not working with fbo.

---

### Post by kattatilpresten on 2009-06-10
I am not able to install wotlk using wine on the download installer. Any one got any tips for settings or so I should change to make it work? Or provide me with info on how to get a hold of 1.1.22..

---

### Post by hikaricore on 2009-06-10
> **kattatilpresten said:**
> I am not able to install wotlk using wine on the download installer. Any one got any tips for settings or so I should change to make it work? Or provide me with info on how to get a hold of 1.1.22..

Read the stickies on where to download WINE and please refrain from thread-jacking.

---

### Post by dre_in_ham on 2009-06-11
great i will try that!
found the relevant keys here
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Will post back tomorrow

---

### Post by dre_in_ham on 2009-06-11
i added the following key

[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"OffscreenRenderingMode"="backbuffer"

and it now works with wine 1.1.23!
Looks like it was the default switch to fbo. What do we do shield me\others from future updates?

---

### Post by NightMKoder on 2009-06-11
> **dre_in_ham said:**
> i added the following key

[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"OffscreenRenderingMode"="backbuffer"

and it now works with wine 1.1.23!
Looks like it was the default switch to fbo. What do we do shield me\others from future updates?

Once you set the key once wine upgrades won't mess with it. It's just that you didn't have the key at all and it defaulted to the default - 1.1.22->backbuffer, 1.1.23->fbo.

Hopefully ati will get their drivers right eventually to allow fbo (fbo is the "actual" picture as opposed to only parts of it: the backbuffer)

---

### Post by dre_in_ham on 2009-06-12
Hi, thanks for the reply. I have a x1600, there will be no more drivers for this card from ati :( The current drivers i am using are the last i will ever get from ati (actually they are the only reason i am still using 8.10, they dont work on 9.04 and the open source drivers crash and are too slow, see [https://bugs.freedesktop.org/show_bug.cgi?id=22195](https://bugs.freedesktop.org/show_bug.cgi?id=22195)) so im pretty much between a rock and a hard place!
While i realise there cant be too many people with this combo of <=R500 ati cards running 3d apps in wine, what would be the chances of trying to get the wine guys to check what ati cards is present and then setting fbo or backbuffer?

---

