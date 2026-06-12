---
title: "Ubuntu 11.10 Upgrade to 12.04 Beta 2"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by aoniumo on 2012-04-08
Is it possible to upgrade without internet connection?

I have a mobile internet connection that can only do from 25-50 kb/s dl speed.   It will take 12 hours to download all packages when I do the following after downloading the alternate beta 2 iso:

sudo mkdir -p /media/cdrom sudo mount -o loop ~/Desktop/ubuntu-12.04-beta2-alternate-i386.iso /media/cdromgksu "sh /media/cdrom/cdromupgrade"

After running these commands, installation still wants me to download update packages even though I selected "no." It will take 12 hours and my connection disconnects so if it disconnects, downloads of packages and upgrade installation cancels and I have to start over again.

Is it possible to upgrade without downloading these packages and just what is available from the alternate beta cd?

Thank you,

aoniumo

---

### Post by aoniumo on 2012-04-09
OK.  Since there are no replies, I just went ahead and downloaded the  packages.  Apparently, packages that have already been downloaded are  retained so even if I got disconnected I can continue where the package  download left off.  It still took hours on slow connection.

Now, it's upgraded successfully with only one problem.  What's wrong with the text?  They're all white.

---

### Post by 2F4U on 2012-04-09
Just for reference, here are the possible ways to upgrade Ubuntu from one version to the next:
[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

With respect to the colors they look a bit like monochrome? Does the rest of the desktop look the same? Did you get errors during the upgrade?

---

### Post by leecheroflife on 2012-04-09
Can you see the text when you highlight it? If so try changing your theme, it might just be a clash with the font colour.

---

### Post by aoniumo on 2012-04-09
It seems a lot of white text on grey background - Transmission, file  labels are white on grey folder background, update manager.  Libreoffice  is ok.  The text box for this post is ok.  Terminal is ok.  These are  the only few I've observed so far.

---

### Post by aoniumo on 2012-04-09
I can see the text when highlighted.  Changed the theme from zukitwo and that fixed it.  Changed back to zukitwo, and white text on grey background came back.

---

### Post by ryanwolf74 on 2012-04-09
Zukwito isn't updated for GTK 3.4 yet, which is what Ubuntu 12.04 uses. That explains the white text.

---

### Post by aoniumo on 2012-04-11
Yes, it looks like only radiance and ambiance won't result in white text on white background.  All other of my themes do.

---

