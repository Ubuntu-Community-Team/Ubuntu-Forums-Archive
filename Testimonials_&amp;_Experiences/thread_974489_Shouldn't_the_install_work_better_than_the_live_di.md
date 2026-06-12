---
title: "Shouldn't the install work better than the live disc?!?"
date: 2008-11-07
forum: Testimonials &amp; Experiences
---

### Post by brodiesel on 2008-11-07
I will be the first to admit that I am not a gifted computer user, and that my problem is much more aptly described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288148") than i could ever do (since that page doesn't make any sense to me), but i also think i have what is a fair complaint. 

I "upgraded" from a fairly healthy Hardy to Intrepid, and after days of trying to figure out how to solve my wireless problem relating to the ATH5K bug, and having that compounded by the fact that wireless is basically MY ONLY AVAILABLE CONNECTION, i dowloaded the live disc, and to my relief/all-consuming anger, found that the wireless in the live disc version worked perfectly. In fact, everything does. 

What am I missing? I have posted this to other boards, but I am now looking at a completely fresh install, which I don't really know how to do, and is going to take a long time, and all because I foolishly hit the "upgrade" button. As a linguist, I can safely say that there are profound problems with Ubuntu's semantic understanding of the term "upgrade"...

---

### Post by cariboo on 2008-11-07
The bug you linked to pretty well tells you what to do. Remove the ath5k that is installed by default, then enable the backport repositories in System-->Administration-->Software Sources, then install the ath5k module from the backports repositories. To remove the module in a terminal type:

```
sudo rmmod ath5k
```

Then use Synaptic Package Manager to install the newer version.

Jim

---

### Post by brodiesel on 2008-11-11
Thanks for the tips, sorry it took me so long to get back to you. 

I did try these, but unfortunately, ran into a few problems. the first is that when i tried to remove the ath5k, there wasnt one to remove. the second is that when i tried to go to the software sources, i was unable to find anything that said "backports repositories."

and, finally, there is the issue of the "software drivers" (i have written about all of this elsewhere if you feel inclined to search) which, as it tells me when i open Hardware Drivers, is a bundle of drivers that is needed in order to have the modem work. the one time i had access to an ethernet cable i tried twice to install that package, and both times it crashed my computer. 

and fixing doesnt address the reason i posted this here: i am befuddled by the fact that the live disc works when the install doesn't.

---

