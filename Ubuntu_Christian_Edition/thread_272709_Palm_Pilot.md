---
title: "Palm Pilot"
date: 2006-10-06
forum: Ubuntu Christian Edition
---

### Post by rcdeacon on 2006-10-06
I cannot get my Palm Tungsten E to sync. Anyone have any ideas? It does not even connect. I got it to connect one time. It is hooked to the usb port but it will not pick it up.

---

### Post by mhancoc7 on 2006-10-07
> **rcdeacon said:**
> I cannot get my Palm Tungsten E to sync. Anyone have any ideas? It does not even connect. I got it to connect one time. It is hooked to the usb port but it will not pick it up.

I used to use my Palm with Ubuntu, and it was bit tricky. I tried Jpilot, and Gnome Pilot. I think I remember having to press Hotsync a couple of times or something. If I get a chance I will try to dust off my Palm and see if I can remember what I did.

Jereme

---

### Post by rcdeacon on 2006-10-07
Thanks for the reply. In earlier distros it would work but it doesn't work well in Mepis either. Any help is appreciated. I use my palm constantly for work and if I could get it to sync with evolution or jpilot it would be great. It is connected on /dev/ttyUSB1.

---

### Post by Shay Stephens on 2006-10-09
I am just now trying to get a pilot to work too.  I have it working in edgy, but not dapper.

(edit)I just got it working in dapper.  Instead of using the gnome pilot app, I installed jpilot from the repositories.  In the setup, I made the port /dev/ttyUSB1 and it now syncs.  I tried ttyUSB0 but it wouldn't connect.

I have to hit the sync button in the app and then hit the sync button on the docking thingy for it to connect.

I got the info for this here:
[http://ubuntuforums.org/showpost.php?p=1162628&postcount=5](http://ubuntuforums.org/showpost.php?p=1162628&postcount=5)

---

### Post by rcdeacon on 2006-10-09
I didn't have any luck with jpilot before but I will try it again. Thanks for the info.

---

### Post by funkenstein on 2006-11-10
I've just resurrected my old palm pilot m500...
I actually went all-out and used the following line to install the software:
```

sudo apt-get install '^jpilot*' '^pilot*'

```

I then started jpilot, pressed its sync button and then the one on the cradle. it worked with no tinkering on Edgy :) I don't even know what port it's using, and I couldn't find the gnome-pilot app (not even in the command line... :confused: )

---

### Post by megamania on 2006-11-10
> **rcdeacon said:**
> I cannot get my Palm Tungsten E to sync. Anyone have any ideas? It does not even connect. I got it to connect one time. It is hooked to the usb port but it will not pick it up.
First thing I suggest to do is to upgrade to Edgy (your profile says you're using dapper), because there's a specific problem with the kernel used by dapper.

There are many threads on this subject which could be of help. In my case, jpilot and pilot-link under Edgy work ok with a Palm TX.

---

