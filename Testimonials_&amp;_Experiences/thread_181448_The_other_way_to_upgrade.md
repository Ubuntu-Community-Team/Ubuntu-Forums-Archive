---
title: "The other way to upgrade"
date: 2006-05-24
forum: Testimonials &amp; Experiences
---

### Post by matthew on 2006-05-24
I have a tendancy to push my systems to the point of breakage...and I did it again. Just like the guys from ["Break My Gentoo"]("http://breakmygentoo.net/index.html") or the wiki page ["Break My Ubuntu"]("https://wiki.ubuntu.com/BreakMyUbuntu") I have a tendancy to play, tweak and add until things quit working and then figure out how to fix it.

A while back I acquired an older system just to test things on, experiment and play with so I would quit doing that on my main work system. Well, with my recent move my testbox is still being shipped from the USA to Morocco so I only have my main laptop available at the moment. So what did I do? I got bored and started to play.

I have been saying I wasn't going to upgrade my laptop from Breezy to Dapper until after the final release, and I really didn't plan to do that. However, last night I was playing around mixing repositories from Debian and Ubuntu (both Breezy and Dapper) upgrading little bits of software here and there. I have often done this with no trouble, but only for the occasional thing, never more than one or two programs/libraries. Everything was going great for the first 30 or 40 packages, then I did it. I broke my Breezy install. Oops! It wouldn't even get to a grub menu on reboot but instead began seg faulting all over the place. :) A reinstall was in order.

Since Dapper is so close to release I thought I might as well go with that, but I don't have a Dapper cd available. I found my Breezy install cd and did a fresh installation (my /home is on a separate partition so nothing valuable was lost and my configuration remained). 

Then I thought, why not do a dist-upgrade right now before I reinstall the ATI fglrx drivers and the ipw2200 wireless stuff?? So I did. It worked beautifully. Not only that, but installing the 3D ATI drivers in Dapper was simple and the ipw2200 drivers are current in Dapper. Furthermore, setting up WPA was a cinch with gnome-netapplet. 

I'm now a happy man sitting at my Dapper laptop with a working ATI fglrx driver, working ipw2200b/g internet with WPA and a this thing is significantly faster in every way!! Boot times were cut by at least a third and shut down takes less than half the time.

Super-huge kudos to the dev team. This is the best edition of Ubuntu yet!!!

---

### Post by Rxke on 2006-05-24
Yes Dapper has been going quite smooth since like what seems ages, now. 
I'm pretty amazed about it too, only once or twice I had to tweak and reinstall some stuff on my laptop to get things going again, these people are amazing!

---

### Post by matthew on 2006-05-24
I should add, after about 12 hours of uptime I have noticed my computer is running significantly cooler as well...the old average was right around 60C and now the processor is at about 52-54C on average. 

The fan is running less, the memory usage is decreased, and the swap file hasn't been used at all (which was rare before, what with 1024M of RAM).

---

