---
title: "AMD unsupported hardware, Radeon HD 6450"
date: 2013-03-31
forum: Ubuntu Development Version
---

### Post by nefarinus on 2013-03-31
Hello everybody

I have just installed ubuntu 13.04 and everything was fine until I installed graph drivers, because after reboot I got such a watermark in right-bottom corner: AMD unsupported hardware, just like this:

[http://i.img.itunix.eu/2131353-1313775254.jpg](http://i.img.itunix.eu/2131353-1313775254.jpg)  (it's not my photo)

So I have searched for problem solution, but most tutorials I found in google were made for old ubuntu versions and didn't work for me (or I couldn't make them work :D)

Can anyone help me with this problem?

P.S. I'm using AMD radeon hd 6450

---

### Post by Hreinsi on 2013-03-31
Have you try this
[http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html](http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html)

---

### Post by nefarinus on 2013-03-31
I have tried but unfortunately... I got an error like this: sed -e sign 45: [ or [^ dont match

---

### Post by deadflowr on 2013-03-31
Pretty much spitballing here, but read through this thread to see if it gives any help for you

[http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)

---

### Post by nefarinus on 2013-03-31
I've done everything as it says in tutorial (with the latest 13.3 drivers), but I don't have  /ect/ati/signature folder nor even /ect/ati/ folder, so I can't save  this signature code. What to do?


*Sorry, I have found it :) but still I don't know how to open signature.save file to check if it is unsigned

---

### Post by Xgen on 2013-03-31
gksu gedit /etc/ati/signature

copy signature code to that file, save and restart session.

---

### Post by nefarinus on 2013-03-31
One more question. This signature is in the 12.11 drivers installation tutorial. Will it also work for  drivers 13.3?

And what finally should be in the signature file? Only signarure code, or signature code and "UNSIGNED"? (It may be a silly question, but I just want to be perfectly sure)

---

### Post by jfernyhough on 2013-03-31
There are two possible watermarks:
1) Not supported
2) Testing use only

To fix the "testing" watermark you can replace the signature file (/etc/ati/signature) with one from a full driver release, for example that from 13.1 attached in post 79 of the "fglrx in raring" thread: [http://ubuntuforums.org/attachment.php?attachmentid=230872&d=1359650532](http://ubuntuforums.org/attachment.php?attachmentid=230872&d=1359650532)

Essentially, each full driver release is given a release signature. Unreleased drivers, betas, etc. are "UNSIGNED", which triggers the "testing" watermark.

To fix the "unsupported" watermark you need to replace the /etc/ati/control file with one from a previous release that officially supports your hardware. You can download the previous fglrx package from Launchpad, for example, and extract just that control file using file-roller (Archives?). Otherwise you can try the Xorg Edgers version ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ; I wouldn't add that repository if you're not confident with ppa-purge, but I've found it to be fairly robust up until now).

---

### Post by nefarinus on 2013-03-31
OK so I have to replace original signature file in /etc/ati/ with this u have attached?

---

### Post by nefarinus on 2013-03-31
Jfernyhough  You are my master! Great thanks to you :D I dont have watermark any more after replacing signature file XD

One more time great thanks - problem solved.

---

### Post by jeSah8ci on 2013-04-08
> **jfernyhough said:**
> There are two possible watermarks:
1) Not supported
2) Testing use only

To fix the "testing" watermark you can replace the signature file (/etc/ati/signature) with one from a full driver release, for example that from 13.1 attached in post 79 of the "fglrx in raring" thread: [http://ubuntuforums.org/attachment.php?attachmentid=230872&d=1359650532](http://ubuntuforums.org/attachment.php?attachmentid=230872&d=1359650532)

Essentially, each full driver release is given a release signature. Unreleased drivers, betas, etc. are "UNSIGNED", which triggers the "testing" watermark.

To fix the "unsupported" watermark you need to replace the /etc/ati/control file with one from a previous release that officially supports your hardware. You can download the previous fglrx package from Launchpad, for example, and extract just that control file using file-roller (Archives?). Otherwise you can try the Xorg Edgers version ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ; I wouldn't add that repository if you're not confident with ppa-purge, but I've found it to be fairly robust up until now).

Worked like a charm; thank you! I no longer have the 'Unsupported Hardware' watermark in Raring. Here's a link to the [Xorg Edgers pool]("http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/f/fglrx-installer/?C=M;O=D") where all the tar files are, if anyone else needs them. The correct 'control' file is located in the **[FONT=Courier New]/usr/lib/fglrx/etc/ati/[/FONT]** folder in the archive, (just in case anyone else is a newbie like me and mistakenly copies the 'control' file inside the **[FONT=Courier New]/DEBIAN/[/FONT]** folder).

---

