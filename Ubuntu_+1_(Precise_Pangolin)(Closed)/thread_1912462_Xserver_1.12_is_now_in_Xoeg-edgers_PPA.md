---
title: "Xserver 1.12 is now in Xoeg-edgers PPA"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-20
Xorg-edgers PPA has been updated to offer xserver 1.12 branch, now at rc1.
Also all input and video drivers have been updatet to meet the ABI:
- xorg-input-abi-16
- xorg-video-abi-12
You will find nvidia-current and fglrx there too.

I have tested nvidia-current (depending on video-abi-12) and it works fine.

One more thing, Precise will not have xserver 1.12.
Instead, it will have xserver 1.11 + some parts taken from 1.12, like multitouch system.

---

### Post by rojaasensei on 2012-01-20
By chance, would these packages help with the hybrid graphics issues with Radeon?  I cannot get graphic card switching to work no matter how I try. Switcheroo, Catalyst, nothing works on my Lenovo G770

---

### Post by paul_in_london on 2012-01-20
> **Harry33 said:**
> Xorg-edgers PPA has been updated to offer xserver 1.12 branch, now at rc1.
Also all input and video drivers have been updatet to meet the ABI:
- xorg-input-abi-16
- xorg-video-abi-12
You will find nvidia-current and fglrx there too.

I have tested nvidia-current (depending on video-abi-12) and it works fine.

One more thing, Precise will not have xserver 1.12.
Instead, it will have xserver 1.11 + some parts taken from 1.12, like multitouch system.

Hi Harry,

Are you also using the ricotz-unstable ppa at the moment? I recently started using that instead of xorg-edgers to get Xserver 1.12 and I'm wondering if I should now re-enable xorg-edgers.

Cheers,

Paul

---

### Post by Harry33 on 2012-01-21
> **paul_in_london said:**
> Hi Harry,

Are you also using the ricotz-unstable ppa at the moment? I recently started using that instead of xorg-edgers to get Xserver 1.12 and I'm wondering if I should now re-enable xorg-edgers.

Cheers,

Paul

Xorg-edgers PPA now has the same xserver 1.12 rc1 as Ricotz Unstable PPA has.
I switched to Xorg-edgers (disabling the Unstable), because it seems it is more frequently updated. For example it now contains a bit newer xorg build (git20120120).
Do not use both at the same time.

---

### Post by zika on 2012-01-21
> **Harry33 said:**
> Do not use both at the same time.Aren't they synchronized?

---

### Post by Harry33 on 2012-01-21
> **zika said:**
> Aren't they synchronized?

In fact they do have about the same content, edgers is a bit more recent just now, but that may change, who knows. Anyways, why use them both?

---

### Post by ricotz on 2012-01-21
My unstable ppa was just a place to prepare this transition for xorg-server 1.12 which now happened. So please use xorg-edgers ppa again. All packages should be properly overridden automatically. I already cleaned my ppa from the older packages.

---

### Post by zika on 2012-01-21
> **ricotz said:**
> My unstable ppa was just a place to prepare this transition for xorg-server 1.12 which now happened. So please use xorg-edgers ppa again. All packages should be properly overridden automatically. I already cleaned my ppa from the older packages.Done. Thank You for all that work...

---

### Post by paul_in_london on 2012-01-21
> **zika said:**
> Done. Thank You for all that work...

+1. Thanks for clarifying that.

---

### Post by bmbaker on 2012-01-26
i just re-enabled the x-org-edgers ppa and can't install the nvidia-current keeps giving me a dependency error needing  xorg-video-abi-11 !!

---

### Post by Harry33 on 2012-01-26
> **bmbaker said:**
> i just re-enabled the x-org-edgers ppa and can't install the nvidia-current keeps giving me a dependency error needing  xorg-video-abi-11 !!

You need to force install the xorg-edgers PPA version of nvidia-current, not the one in Precise repos.
Note, right now the precise repo version is higher and thus offered as a first choice to install.
Use Synaptic and choose force version option from the menu
or install it manually with dpkg.

---

### Post by bmbaker on 2012-01-26
Hi Harry, thanks for the heads up i will do that :-)

---

