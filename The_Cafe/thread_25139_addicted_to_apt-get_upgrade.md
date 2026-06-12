---
title: "addicted to apt-get upgrade ?"
date: 2005-04-09
forum: The Cafe
---

### Post by dusu on 2005-04-09
Hi !

I upgraded from Warty to Hoary a bit less than 2 months ago (03-16-2005). During that time, I got used to the daily apt-get update/upgrade.
These upgrades were bringing some surprise to the every day life. For example :
[list]
[*] X died during my first upgrade (03-17-2005)  :-? 
[*] I could not listen to radios any more (03-18-2005)  ](*,) 
[*] I lost my French keyboard in gdm (03-30-2005) :( 
[*] 04-01-2005 was a shock for me, as for any one :shock:
[/list]
All this is over, since Hoary has now been released !
Of course, I share the enthusiasm of every one for this major event :-D 

But somehow, I miss my daily upgrade so much. Does any one have a cure to my disease ?  #-o

---

### Post by jdong on 2005-04-09
Try this: **sudo rm -rf /**

;) (Seriously, don't. I'm not responsible for any damage you incur....)

---

### Post by joshmachine on 2005-04-09
You only run it once a day?

I admire your restraint.

I'd say the cure for your woes is more unoffical apt-sources.

Try backports:
[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

for some really sweet a/v stuff check out
rarewares.org
deb [http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable) ./

---

### Post by im_ka on 2005-04-09
[QUOTE=dusu]Hi !

I upgraded from Warty to Hoary a bit less than 2 months ago (03-16-2005). During that time, I got used to the daily apt-get update/upgrade.
These upgrades were bringing some surprise to the every day life. For example :
[list]
[*] X died during my first upgrade (03-17-2005)  :-? 
[*] I could not listen to radios any more (03-18-2005)  ](*,) 
[*] I lost my French keyboard in gdm (03-30-2005) :( 
[*] 04-01-2005 was a shock for me, as for any one :shock:
[/list]
All this is over, since Hoary has now been released !
Of course, I share the enthusiasm of every one for this major event :-D 

But somehow, I miss my daily upgrade so much. Does any one have a cure to my disease ?  #-o[/QUOTE]

upgrade to breezy as soon as it hits the servers. that's what i'll do on my test box.

---

### Post by dusu on 2005-04-09
> **jdong]Try this: **sudo rm -rf /**[/QUOTE]

Thanks jdong for this helpful advice ! It installed lots of stuff  said:**
> You only run it once a day?

I admire your restraint.

I'd say the cure for your woes is more unoffical apt-sources.

Try backports:
[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

for some really sweet a/v stuff check out
rarewares.org
deb [http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable) ./


Thanks a lot for the advices, I've tried backports, and I'll give a try to rarewares.org (I did not know it so thanks a lot !).
P.S. I used to upgrade more than once a day :)

[QUOTE=im_ka]
upgrade to breezy as soon as it hits the servers. that's what i'll do on my test box.
[/QUOTE]

Well, I'm not sure I'm experimented enough to upgrade to Breezy so soon. I guess it will be pretty unstable in the beginning ?
I only upgraded to Hoary 2 months before its release, so it was quite stable, which is maybe not so bad for someone like me...

---

