---
title: "Can't upgrade kernel after upgrade to raring"
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by vaskark on 2013-03-08
Hi. I recently completed an upgrade from 12.10 to 13.04 and everything went smoothly as far as i can tell. Except synaptic won't let me upgrade my kernel to 3.8 due to broken packages, so I'm still in kernel 3.5.0-26, I believe. What do you think is the safest way to resolve this?

Thanks.

---

### Post by ventrical on 2013-03-08
> **vaskark said:**
> Hi. I recently completed an upgrade from 12.10 to 13.04 and everything went smoothly as far as i can tell. Except synaptic won't let me upgrade my kernel to 3.8 due to broken packages, so I'm still in kernel 3.5.0-26, I believe. What do you think is the safest way to resolve this?

Thanks.


You can try going to terminal

CTRL + ALT + F1

then login


then...


sudo apt-get update
sudo apt-get upgrade

sudo reboot

then try synaptic

---

### Post by grahammechanical on 2013-03-08
How did you do the upgrade? The normal command for fixing broken packages is

```
sudo apt-get -f install
```

When upgrading from a stable release (12.10) to a development release (13.04) you might need to run 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

a few times. Have you run

```
sudo apt-get dist-upgrade
```

I converted 12.10 to Raring Ringtail back in November. This was before there was an ISO image available.  A few months later I wanted to put in another 13.04 install and the ISO images were broken. So, I installed 12.10 and converted to 13.04. This time there were a lot of issues. You see back in November 13.04 was still very much 12.10. Now it is almost completely different. At this point in the development cycle a fresh install is better, I think.

Regards.

---

### Post by mc4man on 2013-03-08
Do you have raring-proposed enabled?
(if so disable, refresh sources, ect.

---

### Post by vaskark on 2013-03-08
> **mc4man said:**
> Do you have raring-proposed enabled?
(if so disable, refresh sources, ect.
Awesome. That did it. Many thanks. One more thing: for how long should I leave raring-proposed disabled?

---

### Post by mc4man on 2013-03-08
> **vaskark said:**
> Awesome. That did it. Many thanks. One more thing: for how long should I leave raring-proposed disabled?
Generally speaking it's 'recommended' to not use -proposed during this dev 
You can get your install up to date without it & then if desired re-enable. If so then I'd use synaptic for updating & just pay attention to what any particular update will cause.
(I enable updates in synaptic either individually or in small blocks of similar packages, this also  gives an opportunity to check the change logs.

Otherwise you can just leave disabled or re-enable in mid april or so. (assuming a 13.04 release

---

