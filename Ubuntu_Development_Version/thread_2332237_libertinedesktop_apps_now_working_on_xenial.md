---
title: "libertine/desktop apps now working on xenial"
date: 2016-07-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-29
I was able to get libertine containers to work on xenial. I had a full message and was uploading attachments but apache popped up a forbidden error.

 Try again.

You have to allow container to build. When you open libertine and enter container name it will bounce back to install screen. Container is building in background. You have to close libertine and reopen and then try to install desktop apps , ie; firefox and nautilus. The close libetine and go to desktop apps in scopes and you will see apps and can test then.

---

### Post by ventrical on 2016-07-29
..and..

---

### Post by ventrical on 2016-07-30
pcmanfm working along side of nautilus.

---

### Post by ventrical on 2016-07-30
abiword on libertine/unity8

---

### Post by ventrical on 2016-07-30
Installing programs like Thunar and Abiword will bring in a few other things with  them :) but they still work.

---

### Post by ventrical on 2016-07-30
Stellarium does well with xmir. Much faster and clear graphics.

---

### Post by ventrical on 2016-07-30
Wow. chromium-bsu 3D game !! I have tested this game  a few times on regular unity7. it never had the 3D effects it has now on xmir. This is a surprise.!

---

### Post by ventrical on 2016-07-30
Also working on nVidia box.

Regards..

---

### Post by grahammechanical on 2016-07-30
Now, you are just showing off. :)

Wait until I buy some more RAM. Then I too can have fun. :)

Regards

---

### Post by ventrical on 2016-07-30
I am just about to remove my RAM from nVidia box to 1GB RAM.:) I hope it doesn't break completely, but , then again , that is part of why we are testers.

I don't forget where I came from ;)

Regards..

---

### Post by ventrical on 2016-07-30
Working on 1gb Ram.

---

### Post by ventrical on 2016-07-30
From what I have seen under the hood and by background behaviour I am assuming (without documentation) that this is a two pronged problem. 1. The network managing applications and, 2. The server used to create libertine containers. It is very pernickity atm. :)

There Are bugs and I don't mean the bunny rabbit :)

Also I can see in htop that it is finally starting to use swap mem.

regards..

---

### Post by ventrical on 2016-07-30
Actually .. now I am showing off :)

 I am running chromium-bsu, stellarium, firefox and terminal on 1gb of Ram and there is no interuption when working the two graphics programs. They are virtually working concurrently side by side. I haven't seen this done in unity7. So .. unique memory handling properties. :) bravo Canonical.

Regards..

---

### Post by ventrical on 2016-07-30
Watching hey jude on youtube and playing chromium-bsu. Ok.. :) I'll shut up now .

regards..

---

### Post by ventrical on 2016-07-30
Review of Unity8/libertine containers:

A working unity8 desktop with libertine seems to out-perform unity7 and other flavours in reference to memory management. I had developed a test case for a nVidia box that had 4GB of RAM and I simply removed 3 GBs of RAM.  I was able to run stellarium, chromium-bsu graphical game. terminal click and firefox with very good speed and excellent graphical performance. xmir seems to be doing the job it was designed to do and libertine containers with desktop-apps is allowing for mutiple animated games or tools to operate and xmir seems to be the bridge when you mouse over an animated session, that it sort of behaves like virtual box - so there is a smooth mouse transition from one app to the next. In my veiw it actually is faster and more economic using deb-apps in containers that on unity7. Unity8 seems to be running  very lightly and is not interferring with other apps and processes.

 This is very refreshing at this point. 

 Of course more testing is needed.

 oh .. yeah... and this certainly is fun testing ! :)

regards..

---

### Post by mc4man on 2016-07-30
Maybe I'll try on 16.04 (lenovo-Haswell-nv780m) as it still appears doa on 16.10
Do you need a ppa?

---

### Post by ventrical on 2016-07-30
> **mc4man said:**
> Maybe I'll try on 16.04 (lenovo-Haswell-nv780m) as it still appears doa on 16.10
Do you need a ppa?

```


sudo add-apt-repository ppa:ci-train-ppa-service/stable-phone-overlay

```

---

### Post by ventrical on 2016-07-30
I have it working here :

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes

```

and here:

```

Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 12.0.1 Direct Rendering: Yes

```

 ..just noticed that the above ^ is 16.10 with same ppa.

Also I was able to bring back a few older installs  that were broken.

If you have the old:

```

unity8-desktop-session-mir

```

you may have to remove it.

The trick with libertine is that you have to keep trying to create a container. Since the notification loop is busted at first run you have to judge by your modem and hdd lights that it installed. Then close libertine and open again. (a few times) until  you connect to the repo. there seems to be a bug with networking and server. It is very frustrating but if you keep trying to create a new and different container it will usually work.

Also maybe:

```

sudo apt-get remove libertine 
sudo apt-get install libertine 

```

and 
```

sudo apt-get remove unity8-desktop-session
Sudo apt-get install unity8-desktop-session

```

etc..

---

### Post by ventrical on 2016-07-30
On a broken  install I was able to restore and get libertine/containers to work.

@mac4man

It takes about 10-15 minutes to create a container (depending on bandwidth .. more like 10 mins).  The modem lights will take about a minute to start up after you have entered your container name and clicked OK. it will run for about a minute.. then go quiet .. then about 30 seconds later it will run again for about two minutes.. go quiet and then run again .. about 5 times in all. if you do not allow this process to complete it will not create the container.

 Ocne the container is created you can exit from <install> notification window and then restart libertine and you should be able to start adding apps. Note also that after each hard shutdown you have to open libertine icon to be able to see apps in Scopes Desktop -Apps.

regards..

---

### Post by mikodo on 2016-07-30
Thanks, for showing this. :)

Very nice to see this working.

> **ventrical said:**
> I have it working here :

Snippet

```

Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 12.0.1 Direct Rendering: Yes

```

---

