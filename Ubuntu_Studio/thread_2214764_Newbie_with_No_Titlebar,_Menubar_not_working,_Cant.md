---
title: "Newbie with No Titlebar, Menubar not working, Cant load Windows Manager"
date: 2014-04-03
forum: Ubuntu Studio
---

### Post by Pat C on 2014-04-03
Just as I was completing my migration from XP, Chaos invaded. Finally got all my files moved to ext4 format and then:

No Titlebar
Menubar not functioning
Pages load on left third of primary monitor showing partial pages and with "No TItlebar" no way of closing or moving anything
No Windows Manager  loading 
Terminal Emulator not functioning properly

Did not even give me a minute to enjoy the fruits of my labors ... NO MO xp ...  If I was paranoid. I would think that Windows is getting back at me ... Yet even with these problems I will never go back to xp ... just love studio to much ... but how do I fix this without loosing my data which is not on my system backup which I am currently using to post this ...

BTW is there a spell check here to help correct typos ...

---

### Post by jejeman on 2014-04-03
Which version of Ubuntu Studio?
Explain in detail what happend.

---

### Post by Pat C on 2014-04-03
Ubuntu Studio 12.04 Xfce

Was finishing up process of reformating data drives to have either one large ext4 partitions and/or large ext4 and smaller ntfs partitions. I used G-parted to create partitions. Using the terminal emulator, I change ownership to my user group so I could have r/w permissions. This process worked fine for the ext4 partitions but not for the ntfs partitions. I was trying to solve this but having trouble finding info on how to proceed. Hindsight is 20/20, I should have thought to use the forums before trying to go it alone. Not sure exactly what I did as I relied upon bookmarks as an audit trail but now have no access to them. I realize that this is not very detailed but its the best I can do at this point. I will try to retrace my steps best I can. In the mean time, do you have any suggestions?

*  Nautilus 3.4.2 seems to be working OK!

*  Window Manager (xfwm4) page loads as a blank page

*  Panel (xfce4-panel) seems to be functioning OK

---

### Post by su:bhatta on 2014-04-03
> **Pat C said:**
> Ubuntu Studio 12.04 Xfce
*  Window Manager (xfwm4) page loads as a blank page


Xfwm4 page, what is that?

Which page?

Please give details.

---

### Post by BrianSwatton on 2014-04-03
I had this a long time ago, I had to manually run one of the xfce programs from terminal that hadn't started again after a crash.  I thought it was xfwm4, but I guess not from your post.

Edit: I'm a bit of a noob myself too

---

### Post by Pat C on 2014-04-03
Its under Settings Manager in my Application Menu.


> **bhattabhishek said:**
> Xfwm4 page, what is that?

Which page?

Please give details.

---

### Post by Pat C on 2014-04-03
Problem has been solved on another forum. XFCE

Solution:

For Xfce 4.10+, you'll see a "Clear saved sessions" button in  Settings Manager->Session and Startup->Sessions. Click that then  log out and back in again.
For any version earlier, you'll need to log out, go to the first tty (Ctrl+Alt+F1), log in to the text session and execute:cd .cache
rm -rf sessions
...then head back to the gui (Ctrl+Alt+F7), log in and see if it helped.


I have Xfce 4.8 so I followed the instructions for earlier versions ... Didn't work at first .... But after entering my user name and password it workedGR*! Now I'm HAPPY! HAPPY! HAPPY!  Thank you for your responses!

---

