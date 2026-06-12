---
title: "How did you installed Nvidia and ATI on newly installed Gusty Gibbon?"
date: 2007-10-19
forum: The Cafe
---

### Post by maduranga on 2007-10-19
How did you installed Nvidia and ATI cards on your newly installed Gusty Gibbon? It seems like envy is also available to gusty, Is there any advantage (specially in quality of graphics) you have found on selecting one method over the other?

---

### Post by FuturePilot on 2007-10-19
I used the Nvidia driver in the repos. 1 because it's the latest driver, and 2 so I don't have to worry about X breaking after kernel updates. That's not that big of a deal for me, I know how to fix it, just more convenient.
On my old laptop I also stuck with the nvidia-glx in the repos even though it's not the latest. I haven't seen any advantage of the 9643 over the 9639.

---

### Post by Ultra Magnus on 2007-10-19
Gutsy recognised my ati x1400 card using the open source driver but the resolution was slightly wrong so I enabled the propriatory driver by doing: system -> administration -> restricted drivers 

or you could just do "sudo apt-get install xorg-driver-fglrx

Then to get compiz working install xgl with "sudo apt-get install xserver-xgl"

---

