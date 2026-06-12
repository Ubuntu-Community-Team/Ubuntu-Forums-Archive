---
title: "Wine won't work anymore after Ubuntu Software Update"
date: 2010-07-05
forum: Wine
---

### Post by hoffmaster on 2010-07-05
Hi Everyone,

I am using Wine 1.1.42 and I have been playing WOW for days without a single issue.

Today two things occurred, I played with Compiz trying to see if I could get my firefox to open on the same workspace everytime so I enabled an option in Compliz.  The other thing that happened was Ubunut software updates installed.

Now when I try to start wow exactly the same way I did before I get an error and it wont work. 

Some information:
WOW folder is on an NTFS partition
I was using a shortcut, but I use wine (path)/Wow.exe -opengl

it tries to load, and then the wow error notifier gives an access violation.

I am totally lost and growing increasingly frustrated with the fact that I am spending most of my time trying to fix problems rather then actually using Ubuntu and Wine.  Am I the only one?  I already go my network shares screwed up to the point I just formatted and did a fresh install, now after less then a day I am at a standstill again.

Please help, I really want to switch to linux.

---

### Post by philinux on 2010-07-05
Moved to Wine forum.

---

### Post by hoffmaster on 2010-07-05
I have already done a fresh install and problem is fixed.  

In case someone out there is having the same issue my computer intuition tells me that somehow the opengl or nvidia drivers got disconnected from wine.  I had done a manual install of the Nvidia driver and for some reason I think that the Ubuntu update may have somehow made Wine think I was not using the correct

---

### Post by hikaricore on 2010-07-06
Actually it doesn't work that way.  
Your video drivers were just not functioning correctly thus WINE was unable to work properly.
If you manually install video drivers you have to completely remove the packaged ones first and vice versa.
Installing them from more than one source at a time just leads to mess.

---

