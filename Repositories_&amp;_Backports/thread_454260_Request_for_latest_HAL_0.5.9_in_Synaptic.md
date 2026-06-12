---
title: "Request for latest HAL 0.5.9 in Synaptic"
date: 2007-05-25
forum: Repositories &amp; Backports
---

### Post by joshtt on 2007-05-25
Hello,

my computer has a hick-up every two seconds, which is of course unbearable to work with (means a screen freeze every two seconds, either using nvidia or vesa driver and using either nvidia card or the onboard card).
Searching on some forums guided my to the fact that hald-addon-storage polls the cdrom drive every two seconds.

I found this issue on a web page, apparently written bu Ubuntu developers: [http://vizzzion.org/](http://vizzzion.org/)
Search for 'HAL'.

Pending on the hardware, this can cut in the power management. I have this thing.

In the newest HAL, there is a feature to make HAL stop polling any removable drive. So, if HAL is my problem, this would fix it.

Any chance on getting this update to HAL 0.5.9 into Synaptic?

Thank you,

Joshtt

ps: I wrongly posted this message in the Install/upgrade forum as well. Feel free to delete that one ... sorry.

---

### Post by tweedledee on 2007-05-26
> **joshtt said:**
> Hello,

my computer has a hick-up every two seconds, which is of course unbearable to work with (means a screen freeze every two seconds, either using nvidia or vesa driver and using either nvidia card or the onboard card).
Searching on some forums guided my to the fact that hald-addon-storage polls the cdrom drive every two seconds.

I found this issue on a web page, apparently written bu Ubuntu developers: [http://vizzzion.org/](http://vizzzion.org/)
Search for 'HAL'.

Pending on the hardware, this can cut in the power management. I have this thing.

In the newest HAL, there is a feature to make HAL stop polling any removable drive. So, if HAL is my problem, this would fix it.

Any chance on getting this update to HAL 0.5.9 into Synaptic?

Thank you,

Joshtt

ps: I wrongly posted this message in the Install/upgrade forum as well. Feel free to delete that one ... sorry.

Add backports to your sources list - the newest version is there.

---

