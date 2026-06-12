---
title: "Did a little fine tuning on 14.04."
date: 2014-10-05
forum: Ubuntu, Linux and OS Chat
---

### Post by d-cosner on 2014-10-05
I stopped distro hopping a while back but started wondering if I could get more performance out of Ubuntu? I found a lot of guides and I used to do some of these things in the past but things have changed. I tried some of the things I thought might really help. 

Changing swappiness from 60 to 10 really helped a lot when running Virtualbox! My desktop has 4 GB of RAM and the laptop has 8 GB but with the default settings my systems would slow to a crawl. Now Virtualbox no longer slows anything down.

It used to take both systems several seconds for the desktop to load after typing my password. By default startup services are hidden, I made them visible and turned off the ones I do not need. Now the desktop loads in a couple of seconds and it looks smoother.

I installed Preload because some applications took several seconds to load, now they only take a couple of seconds.

I also found a tweak for shrinking the inode cache. I had never tried this one but it seems to help and it did not cause any problems.

When I was all finished both machines ran noticeably faster! Memory and processor use looked great on both systems! I never expected this much improvement when I started. I wanted to keep Unity rather than switch to a lighter DE because I like it. Both my machines are middle of the road hardware wise, not bad but nothing great either. They both do have a decent amount of RAM though and I was prepared in case something went wrong.

Does anyone else use these tweaks? If so, did you end up with similar results? I know not everyone is inclined to try these kinds of things but I though it was worth the time to give it a shot to try and increase performance and it worked out well for me!

Edit: I can provide links and information on what I used if anyone needs them. They are "use at your own risk" though but the tweaks I used are pretty much proven safe so long as you have enough memory. I do recommend backing up any important data before you begin, just in case.

Edit 2: Got rid of indexing! I hated indexing in Windows and the same with Linux, nice to be rid of it!

---

### Post by Tar_Ni on 2014-10-05
Well to be honest if I want to get more performance out of my hardware I don't go into that kind of trouble, I just use Xubuntu (Xfce) or Lubuntu (LXDE)

---

### Post by d-cosner on 2014-10-05
All of the things I did can be found on these sites.

[http://ubuntuhandbook.org/index.php/2013/11/show-all-hidden-startup-applications-ubuntu1310/](http://ubuntuhandbook.org/index.php/2013/11/show-all-hidden-startup-applications-ubuntu1310/)

[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

I am running Xubuntu on an older computer I salvaged, it runs very well! I thought maybe some, like me would like to get more speed out of Ubuntu and have the Unity interface. My computers are not the latest greatest, Core 2 Duo 7500 and AMD E-Series E1-120. The laptop has the AMD E-Series E1-120 and was considered slow by Windows users. The laptop runs amazingly well on Ubuntu 14.04 with the tweaks I mentioned and the battery life is good using TLP.

I found out that the laptop, an HP 655 is certified by Ubuntu, I did not know that when I bought it though. At any rate I thought some might benefit from these things like I did.

---

