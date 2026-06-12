---
title: "Ubuntu 13.04 unity does not works"
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-04-13
So couple of days ago i did an update and after the reboot unity stopped working and this is how it looks now

[IMG]http://i.imgur.com/GHlbDFZl.jpg[/IMG]

 I looked thru other threads but sadly I could not fix this problem.
Please note that I did an upgrade from ubuntu 12.10 that had header problems or something and I had to use this information to fix it 
[http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers](http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers)
 So can anyone tell me how to fix this issue 

 Thank you in advanced

---

### Post by Rukiri on 2013-04-13
Are you using closed drivers? I know when I check the closed nvidia 313.30 drivers in the software sources I would not see Unity, maybe this is the issue?
It's definitely a gfx driver issue not so much unity. 

What are you using?

IntelHD (what version)
Nvidia (What card do you have)
AMD Radeon HD (What card do you have)

Or do you have an old school 3dVoodoo card? ( Have one, unopened^^ )

---

### Post by Chelidze on 2013-04-13
Thank you for the reply :)
I am using nvidia proprietary 313 drivers but I tried to use open source drivers sadly same issue

---

### Post by grahammechanical on 2013-04-14
Changing to Nouveau is the first step. Run ```
dconf reset -f /org/compiz/
``` You may also need to reinstall compiz and reboot.

Regards.

---

### Post by Chelidze on 2013-04-14
> **grahammechanical said:**
> Changing to Nouveau is the first step. Run ```
dconf reset -f /org/compiz/
``` You may also need to reinstall compiz and reboot.

Regards.

 Thank you so much it worked like a charm :)

hope they will fix proprietary drivers issue soon

---

### Post by kc8hr on 2013-05-06
I have had a similar experience after upgrading from 12.10. . .

Logging in to the default Unity Desktop gives me a pretty desktop with wallpaper, but no toobars and no launchers. Nothing!

My system is a rather elderly Dell Optiplex with onboard Intel video, and lspci provides the following information:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Wazzup???
Thanks,
Tim

---

### Post by cariboo on 2013-05-06
> **kc8hr said:**
> I have had a similar experience after upgrading from 12.10. . .

Logging in to the default Unity Desktop gives me a pretty desktop with wallpaper, but no toobars and no launchers. Nothing!

My system is a rather elderly Dell Optiplex with onboard Intel video, and lspci provides the following information:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Wazzup???
Thanks,
Tim

Seeing as Raring has been released, It may be better to ask your question in General Help. In development time 3 weeks is a long time, and much changed in that time. Thread closed.

---

