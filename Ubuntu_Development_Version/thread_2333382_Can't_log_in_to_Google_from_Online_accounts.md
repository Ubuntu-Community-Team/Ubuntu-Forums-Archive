---
title: "Can't log in to Google from Online accounts"
date: 2016-08-09
forum: Ubuntu Development Version
---

### Post by Yahoé on 2016-08-09
I can't log in to Google from Online accounts.

The window displays the Google log in page, but as soon as I interact with the window, click inside, or even use the side slider, the windows goes blank.

I've tried uninstalling and reinstalling the Google account plugin to no avail. This used to work on this 16.10 machine.

Help would be appreciated.

---

### Post by jbicha on 2016-08-11
I believe this is because WebKit and WebKit 2 need to be rebuilt against GTK 3.20. This was actually done but it got entangled in a few other transitions (qt, webp, packagekit) so the updated packages aren't quite in Ubuntu Yakkety yet.

This will cause some bad theming issues with things that use WebKit like Evolution, Epiphany (the GNOME Web browser) or the Help app.

---

### Post by mc4man on 2016-08-11
Works ok in an ubuntu session. (at least with fresh install, 1st. attempt.

---

### Post by tremblay-bernard on 2016-10-17
Same issue here, cannot connect online account to google and outlook.com.
Is there a solution other than wait for an update to correct the problem ?

---

### Post by ventrical on 2016-10-17
> **mc4man said:**
> Works ok in an ubuntu session. (at least with fresh install, 1st. attempt.

Same here .. and I  have already changed sources.list to zesty, not that it matters.
unity-desktop
Regards..

---

### Post by ventrical on 2016-10-17
Got this. Obviously there are issues or I signed on incorrectly.

Cant send screenshot but here is link:

struck out link

edit:

The caveat is that you have to secondarily log on  to give ubuntu authorization to use online-accounts. You have to use the username and password of the install you created on your hdd, not your SSO or email or email password .

regards..

---

### Post by ventrical on 2016-10-17
Going a bit further -- installing evolution.

```

sudo apt-get install evolution

```

Works like a charm. I ran evolution and it auto logged on to my gmail account seamlessly. No log-out , no restart.. classic ubuntu excellence.

Regards..

---

### Post by mc4man on 2016-10-17
Edit: likely just needed for 16.04...
I use it for google-drive in nautilus, in that case I have to use the online accounts in gnome-control-center to add google, not the one in ubuntu-control-center.

---

