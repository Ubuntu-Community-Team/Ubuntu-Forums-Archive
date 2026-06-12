---
title: "Configure Dansguardian"
date: 2015-12-07
forum: Ubuntu Christian Edition
---

### Post by al.coda on 2015-12-07
Hello, I am returning to ubuntu after a 3 year hiatus. I always liked ubuntu ce, but gave it up because of the frustration of dansguardian.
There are no children in my home , no unauthorized users. A quick look shows me that there is a new frontend for dansguardian making it seem more user friendly. I understand the reason for a web filter like DG but for me and probably many other users it can be a frustration. As an example, DG won't even allow a download of Ubuntu 15.04 from the Ubuntu site. Any advice on how to configure the restrictions of Dansguadian would be greatly appreciated.

---

### Post by david_kt on 2015-12-07
Try below in terminal:

sudo perl -pi -e 's/^\./#\./g' /etc/dansguardian/lists/bannedextensionlist 
sudo sed -i 's/\(^[a-z]\)\(.*\)/#\1\2/' /etc/dansguardian/lists/bannedmimetypelist
sudo perl -pi -e "s/$DATA/naughtynesslimit = 100/g;" /etc/dansguardian/dansguardianf1.conf

DK

---

### Post by QIII on 2015-12-07
A bit of explanation of what that is intended to do would be appropriate.

---

### Post by david_kt on 2015-12-07
1. Remove the usual extension from banned list ( solve this problem: DG won't even allow a download of Ubuntu 15.04 from the Ubuntu site)
2. Remove the usual mimetype from banned list
3. set naughtyness limit to 100 to avoid many false positive. You can change to 5000 if you still face too many false positive.

DK

---

### Post by al.coda on 2015-12-08
> **david_kt said:**
> 1. Remove the usual extension from banned list ( solve this problem: DG won't even allow a download of Ubuntu 15.04 from the Ubuntu site)
2. Remove the usual mimetype from banned list
3. set naughtyness limit to 100 to avoid many false positive. You can change to 5000 if you still face too many false positive.

DK
I truly appreciate the effort you have gone to in attempting to help me, Thank you very much. Unfortunately I could not get these commands to work for me. The second command, brought up a lengthy reply that directed me to a general help site for Gnu software. Rather than frustrate myself unduly, I will uninstall Ubuntu CE before it sours me on Ubuntu in general. As it stands now it is only another email checker, which I don't need. The verbage contained in the software centre, describes Dansguardian as being adjustable by the user. Quote "as draconian or unobtrusive as you like", the developers of this site offer no help or support for the configuration of this web filter, in fact seem to make it as difficult as possible, judging by the amount of code provided in the commands. I am not a geek but I am not a novice either, is it to much to ask, to make an OS that can be configured by the average computer user? As a bible teacher and former pastor, I am disappointed that an OS which could have so much potential for Christians, is only a source of frustration. Time commitments and a very limited, metered internet connection prevent me from spending any more time on this. I came, I saw, I left (again).

---

### Post by brian-mccumber on 2015-12-08
Here is a link to uninstall commands for Dansguardian. 

[http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html](http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html)

---

### Post by Edison_James on 2015-12-08
> **al.coda said:**
> I truly appreciate the effort you have gone to in attempting to help me, Thank you very much. Unfortunately I could not get these commands to work for me. The second command, brought up a lengthy reply that directed me to a general help site for Gnu software. Rather than frustrate myself unduly, I will uninstall Ubuntu CE before it sours me on Ubuntu in general. As it stands now it is only another email checker, which I don't need. The verbage contained in the software centre, describes Dansguardian as being adjustable by the user. Quote "as draconian or unobtrusive as you like", the developers of this site offer no help or support for the configuration of this web filter, in fact seem to make it as difficult as possible, judging by the amount of code provided in the commands. I am not a geek but I am not a novice either, is it to much to ask, to make an OS that can be configured by the average computer user? As a bible teacher and former pastor, I am disappointed that an OS which could have so much potential for Christians, is only a source of frustration. Time commitments and a very limited, metered internet connection prevent me from spending any more time on this. I came, I saw, I left (again).

I sympathize with your plight. You are not the first, I am sure you will not be the last.

> **brian-mccumber said:**
> Here is a link to uninstall commands for Dansguardian. 

[http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html](http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html)

It's been quite a while but I am pretty sure when I uninstalled  Dansguardian, my browser quite working entirely. I could be wrong though, anyway for the OP, it is certainly worth a try.

---

### Post by al.coda on 2015-12-08
> **brian-mccumber said:**
> Here is a link to uninstall commands for Dansguardian. 

[http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html](http://installion.co.uk/ubuntu/vivid/universe/d/dansguardian/uninstall/index.html)

Thank you I will try this. Actually I would be happy to simply configure Dansguardian, not actually remove it, but if this is the only option, then I will take it.

> **Edison_James said:**
> It's been quite a while but I am pretty sure when I uninstalled  Dansguardian, my browser quite working entirely. I could be wrong though, anyway for the OP, it is certainly worth a try.

You are right, dansguardian is removed, I am now unable to access the internet with any browser. Very disappointing. Thank you for the heads up. I am going back to Slackware (it works). I won't be back here.

---

### Post by Edison_James on 2015-12-08
> **al.coda said:**
> You are right, dansguardian is removed, I am now unable to access the internet with any browser. Very disappointing. Thank you for the heads up. I am going back to Slackware (it works). I won't be back here.

I thought that would happen. I agree with your assessment of Ubuntu CE. Every OS is a product of it's designer's and developers, CE is no different, it is what it is by design. In a world of OS, CE is unique, with it's Christian theme. As much as I would love to use it, I feel it has missed the mark, mainly by not being user friendly. It is probably safe to say that most new linux user's don't even know what a command line is. They are used to doing everything from the GUI, as such the learning curve is steep, not worth the effort for many. There are over 3 billion people in the world who profess to be Christian, the potential for a Christian themed OS is simply phenomenal.
Unless Ubuntu CE does some major changes it will never capitalize on that enormous market. Will that happen? I doubt it, again it is what it is by design, if you don't like it you only have one option______________. You finish the sentence.

---

### Post by david_kt on 2015-12-08
Those script I used to preconfigure dansguardian in previous ubuntu ce. If return any error, you should post the error and I will adjust the script as I don't have ubuntu ce. Otherwise, edit those three files by hand.

---

### Post by brian-mccumber on 2015-12-09
It looks like you were dead set against Ubuntu CE from the start.

I am not sure how the software center works in Ubuntu CE but if it is like Ubuntu 14.04 you could reinstall Firefox or Chromium with Dansguardian uninstalled and that would possibly fix the problems you're having but then again installing another OS would fix it too.

---

### Post by incognito4 on 2015-12-09
This topic intrigues me. Is Ubuntu CE really that hard to use for average computer users? I intend to see for myself. One thing I notice right away is when I went to distrowatch looking for a download, the most recent version is 12.04, which is surprising since I have been using 15.04 which is a big improvement over 12.04. I will post my results here, or in a separate thread in this forum. If I can do it, I'm sure anyone can. It seems like the biggest obstacle for many people is the web filter, dansguardian. I will focus my attention there. More to come.

---

### Post by Bucky Ball on 2015-12-09
The original poster writes:

> **al.coda said:**
> I won't be back here.

al.coda has just left the building. Happy trails. 

*Thread closed.*

---

