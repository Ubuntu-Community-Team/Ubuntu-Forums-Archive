---
title: "Dist upgrade"
date: 2009-02-02
forum: Testimonials &amp; Experiences
---

### Post by wfp on 2009-02-02
So i thought i would try a dist upgrade from Hardy64 to inrepid64. Have to say it was a pleasant experience. It was nice and flawless the only thing i had to do was add medibuntu to intrepid after the install, and enable the Nvidia driver. Outstanding.

---

### Post by wolfen69 on 2009-02-03
glad it worked for you. but it's something i will never do. i hear too many horror stories of upgrading breaking things. fresh install is always the best way. plus there's nothing like that new os smell.

---

### Post by Crafty Kisses on 2009-02-03
That's good to hear my friend, glad it worked out for you.

---

### Post by wfp on 2009-02-03
Yes i was a little hesitate about doing a dist upgrade my self from reading some of the post on the forum. I tried to do a fresh install when intrepid first came out, but even with nvidia driver enabled it would not let me change screen resolution above 800*600. Also in intrepid you can no longer run sudo displayconfig-gtk they left that out. And since i am still noobish on a fresh install i would have had to gedit xorg.conf tried that but had no luck. Any way every thing worked out.

---

### Post by Crafty Kisses on 2009-02-03
Yeah that's good. I really don't like dist-upgrades but I've done them before, I prefer fresh installs, but hey, there's noting wrong with updating via Synaptic, I think it's a great way! Just backup any data. ;)

---

### Post by warjowuch on 2009-02-03
In the repos, you should find 2 packages, one called nvidia-settings and the other one about the same name.
At least one of these should make you able to adjust your resolution to the correct settings.

I had these problems with my sisters computer. After installing the advised nvidia-driver, and logging back in, she only got a stupid, very low resolution.
Installing and using this nvidia-settings tool, made it very easy to adjust the resolution to our likings.

Hope it helps!

---

### Post by wfp on 2009-02-03
Thanks i tried that with the fresh install of intrepid, even with nvidia driver enabled and nvidia-settings it would not let me past 800x600. Thats when i crossed my fingers and figured since i had nvida-settings set to 1024x768 in hardy64 a dist upgrade would be my best bet, hoping that my settings would still be there in nvidia-settings panel. Thanks for your suggestion thou.

---

### Post by warjowuch on 2009-02-03
What about nvidia-xconfig?

By the way, both Nvidia-settings and nvidia-xconfig are tools, that you have to open to use them.
They are NOT magic beings which make proper resolutions appear in the regular ubuntu resolution-program.

---

