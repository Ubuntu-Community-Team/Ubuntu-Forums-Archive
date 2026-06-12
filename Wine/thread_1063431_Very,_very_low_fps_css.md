---
title: "Very, very low fps css"
date: 2009-02-07
forum: Wine
---

### Post by adoyle626 on 2009-02-07
Hello,
I currently am using a Radeon Xpress 200G Series video card and whenever I play CSS it says I need to update my drivers. When I go to it, it is not supported by Ubuntu!!! 
According to CSS my FPS is roughly 7 FPS!!
I used to run windows XP and I could run WoW and other high graphic games VERY smoothly!

Someone PLEASE help me out here.
Thank you!!!!

---

### Post by Vince4Amy on 2009-02-08
Which version of Ubuntu are you using? I'm not sure that your GPU is compatible with the latest ATI Drivers (9.1) which may mean you will not be able to play WINE Games to their full potential.

Edit: It seems that you can get the latest ATI Driver for your chipset install from below:

```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-1-x86.x86_64.run
```

```
sudo sh ati-driver-installer-9-1-x86.x86_64.run
```

Run through all the steps in Automatic.

```
sudo aticonfig --initial -f
```

Reboot.

I can't gaurantee that this will work for you so try this at your own risk, you should however be okay to do this but I won't take resposibility if it doesn't work. More infomation can be found here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by adoyle626 on 2009-02-09
I'm trying this out.
If something goes wrong and I can't figure it out, I'll post on a different computer for help.

I hope this works =)

Thank you

---

### Post by 0bso on 2009-02-10
Just so you know, Steam will always tell you that you need to update your video drivers if you are running it on wine.

---

### Post by Vince4Amy on 2009-02-11
> **0bso said:**
> Just so you know, Steam will always tell you that you need to update your video drivers if you are running it on wine.

Didn't last time I used it. However I haven't checked it recently. Did the ATI Drivers work for you?

---

### Post by adoyle626 on 2009-03-03
They worked, it didn't ask me for drivers, but I messed with steam and it didn't work for a while.

It is working great now. Thanks! :D

---

