---
title: "Synaptic refuses to install too many updates"
date: 2005-07-19
forum: Repositories &amp; Backports
---

### Post by dude2425 on 2005-07-19
I've been away from my computer for 3 months, and now I have a huge list of Breezy updates to go through. I've selected them all like I usually do and find it want's to download 1144 packages, and it does. It then attempt's to install them, but instead it just sits there with a blank terminal screen and try's to tell me it's done. I highly doubt apt-get has been so improved that it takes less than a second to finish installing everything. I also set it up so it'd remove some things conflicting with other packages, and it doesn't even do that. I'm redownloading the 1144 packages right now to try again. Any help on this matter will be appreciated.

---

### Post by Lord Illidan on 2005-07-19
Select them 1 by 1..

---

### Post by dude2425 on 2005-07-19
do you mean download and install each one individually, or actually selecting each individual package individually? When I select them, I select each package individually so that if a package wants me to remove 50 of my most needed packages, then I don't have to download it like I would with a dist-upgrade. I have thought about the other one, but it'd take forever, and I'm using my neighbors connection ATM untill I get my own next wednesday (just moved)

EDIT: Well I got most of the updates installed, although xbase-clients refuses to upgrade to the newer version because xcursorgen refuses to install, and xcursorgen refuses to install because I don't have a new enough version of xbase-clients installed. The only way I can get xcursorgen to install is if I get rid of xbase-clients, which is going to also get rid of all of the stuff that depends on it. I am so damn confused.

---

