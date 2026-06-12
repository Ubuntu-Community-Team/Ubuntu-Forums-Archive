---
title: "libgnome-desktop-3-5"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-24
We have now a new gnome-desktop3 (3.7.90).

However gnome-session-bin (3.7.4) depends on the old libgnome-desktop-3-5 (3.7.5).

---

### Post by Harry33 on 2013-02-24
Well now there is a new gnome-session 3.7.90 in the gnome3 Staging PPA.
However, GDM does not seem to work with it.
Had to downgrade it back to 3.7.4 version and retain the libgnome3-desktop-3-5.

---

### Post by zika on 2013-02-24
> **Harry33 said:**
> Well now there is a new gnome-session 3.7.90 in the gnome3 Staging PPA.
However, GDM does not seem to work with it.
Had to downgrade it back to 3.7.4 version and retain the libgnome3-desktop-3-5.
Not only that GDM doesn't work with it but now I had to revert to awesome since no gnome-session would work even in startX... ;)
Maybe it's time to turn ricotz on again... ;) Let me go and check what is there available...

---

### Post by Harry33 on 2013-02-24
> **zika said:**
> Not only that GDM doesn't work with it but now I had to revert to awesome since no gnome-session would work even in startX... ;)
Maybe it's time to turn ricotz on again... ;) Let me go and check what is there available...

Downgrading the four gnome-session packages (gnome-session, gnome-session-bin, gnome-session-common, gnome-session-fallback) and making sure that libgnome-desktop-3-5 is installed will help.

Again, with wget from here:
[http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-session/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-session/)

---

### Post by Harry33 on 2013-02-24
There is a new version already in the PPA:
gnome-session (3.7.90-0ubuntu1~raring2)

Will try that later today.

---

### Post by zika on 2013-02-24
> **Harry33 said:**
> There is a new version already in the PPA:
gnome-session (3.7.90-0ubuntu1~raring2)

Will try that later today.
It works again in startX, did not try it in GDM, had overtweaking episode with r8169 that deprived me of net access and sound... Regained both...

---

### Post by VinDSL on 2013-02-24
Thanks, for the heads-up!

I was doing to do an upgrade, before going to bed, last night, but...

Synaptic "Smart Upgrade" said it was going to remove "gnome", and a bunch of other related packages.

So, I tried a "Default Upgrade", and it said the same packages would be removed.  Hello!?!?!

At that point, I decided to wait until the morning.

Thought I should check the threads before moving forward...

Thanks, again!  ;)

---

### Post by VinDSL on 2013-02-24
> **zika said:**
> [...] had overtweaking episode [...]
LoL!  :D

Glad to hear, I'm not the only one that over-engineers everything.

It's a strength, and a weakness...

---

### Post by zika on 2013-02-24
> **VinDSL said:**
> LoL!  :D

Glad to hear, I'm not the only one that over-engineers everything.

It's a strength, and a weakness...It's a virus... ;)

---

### Post by Harry33 on 2013-02-25
The Gnome3 Staginf PPA works now well.
Old libgnome-desktop-3-5 is dropped.
So, the issue is solved.

---

