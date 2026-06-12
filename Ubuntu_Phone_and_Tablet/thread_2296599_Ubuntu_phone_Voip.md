---
title: "Ubuntu phone Voip"
date: 2015-09-27
forum: Ubuntu Phone and Tablet
---

### Post by timo-tervahauta on 2015-09-27
Hello there. As many of you know there is not a way to make voip calls with the phones. 
Hangout beta does make the call but dosent identify your mic and cam. 
Please someone tell me if there is a ongoing work on this?

---

### Post by dumazdamaz on 2015-10-02
skype?

---

### Post by timo-tervahauta on 2015-10-05
Calls not working

---

### Post by Lars Noodén on 2015-10-05
Which VoIP?  Jitsi and Ekiga work fine and, I have heard that Linphone works too.  Dialout to regular phones should work but that is dependent on your SIP provider.

---

### Post by timo-tervahauta on 2015-10-05
Cant find those three in ubuntu store on my meizu... (skype, hangouts not working)

---

### Post by dumazdamaz on 2015-10-05
Then there is nothing.

for now...

But see:
 [http://news.softpedia.com/news/Canonical-Working-to-Add-Whatsapp-and-Dropbox-as-Services-and-Not-Apps-483172.shtml](http://news.softpedia.com/news/Canonical-Working-to-Add-Whatsapp-and-Dropbox-as-Services-and-Not-Apps-483172.shtml)
 [http://news.softpedia.com/news/ubuntu-developers-say-whatsapp-for-ubuntu-is-a-chicken-and-egg-problem-493057.shtml](http://news.softpedia.com/news/ubuntu-developers-say-whatsapp-for-ubuntu-is-a-chicken-and-egg-problem-493057.shtml)

---

### Post by qduaty on 2015-10-11
Linphone works from terminal. Of course, install it before use: ```
sudo apt-get install linphone
```

---

### Post by handaxe on 2015-10-11
Indeed, but first read about setting the phone as read/write and the implications of this for receiving the OTA updates...:-)

---

### Post by timo-tervahauta on 2015-10-14
Ohh... I don't want too mess up the phone. I use it daily.
Do u have a link on that? (handaxe)
Thanks

Qduaty.
Does it not have an interface?
Im terrible in terminal

---

### Post by handaxe on 2015-10-14
> **timo-tervahauta said:**
> Ohh... I don't want too mess up the phone. I use it daily.
Do u have a link on that? (handaxe)


[Here]("https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/") is one such link. Note that someone on Google+ offered that it does not disable the upgrades, it simply removes the safety of the normal read-only system. Is that true - who knows, because if it is, then the cited page is written very poorly.

---

### Post by qduaty on 2015-10-14
> **handaxe said:**
> Indeed, but first read about setting the phone as read/write and the implications of this for receiving the OTA updates...:-)

In fact I installed programs like this without even knowing that the phone can be set read/write. Remounting the root filesystem temporarily rw is enough to use apt-get and does not disable OTA.

> **timo-tervahauta said:**
> Does it not have an interface?
Im terrible in terminal

Text Linphone in this case works poorly anyway and is only suitable for console geeks as a toy, but I found that GTK linphone (X-based) can connect flawlessly to another Linphone on Windows. Unfortunately, you need to connect Xmir to mir (in order to have X11), which is rather tricky. I have another thread on that matter.

---

### Post by timo-tervahauta on 2015-10-15
It sounds like i have to wait on a app. I don't do stuff i can't handle and i don't have the time/potential too start learning. 
But thanks anyway.

I really hope someone with the potential and will make a great voip app. The one who do will get all my credit.

---

### Post by krusty8 on 2015-11-24
> **qduaty said:**
> connect Xmir to mir (in order to have X11), which is rather tricky. I have another thread on that matter.

Care to offer a link to that thread?

---

### Post by handaxe on 2015-11-24
> **krusty8 said:**
> Care to offer a link to that thread?

This may help:

[https://plus.google.com/app/basic/stream/z123jpiw4xzwyvsct221zrmbbqe4grkdd](https://plus.google.com/app/basic/stream/z123jpiw4xzwyvsct221zrmbbqe4grkdd)

---

