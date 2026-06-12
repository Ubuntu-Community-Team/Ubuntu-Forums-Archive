---
title: "Still planning to use Ubuntu 12.04 LTS."
date: 2014-01-29
forum: The Cafe
---

### Post by rodel_catajay on 2014-01-29
This summer, after the school ends here in the Philippines, I will start venturing in Ubuntu. Hope you guys showers me with numerous encouragement and advises. At present I'm using Windows 7 Starter in my Samsung netbook.

---

### Post by Bucky Ball on 2014-01-29
[I]Thread moved to **The Cafe**.
[/I]
Welcome. Good luck with that and post a thread in the appropriate forum if you have any issues. ;)

I advise you start getting aquainted with Ubuntu or one of its flavours now (you can run it from a disk or USB dongle) and perhaps start using some of the open-source software available in Windows; Firefox, Thunderbird, Filezilla, Libreoffice or Openoffice and the many others.

Also, if you are talking about April, 14.04 LTS will be released by then so you might want to go for that. Five years support release.

---

### Post by rodel_catajay on 2014-01-30
sorry I'm just learning this out. actually this is my first time to joined in a forum. i joined because i want to study and use Linux.
Thanks.

---

### Post by Lars Noodén on 2014-01-30
If you're feeling adventurous you could try 14.04 as a preview.  The testing version is available already:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

A lot of things get fixed daily, usually small things, so be sure to update frequently if you try that.  Then as April 17th approaches, things should slow down and stablize.  But for most things, it is usable now and the advantage is that it is a Long Term Support (LTS) edition and will be good for the next 5 years.

---

### Post by Bucky Ball on 2014-01-30
> **Lars Noodén said:**
> If you're feeling adventurous you could try 14.04 as a preview.  The testing version is available already:



That would be a really bad place to start. It is stable most of the time, but expect unexpected breakages. It is not released until April, still testing  and not designed or intended for Linux newbie consumption. I wouldn't go there.

Wait til April. ;)

---

### Post by Lars Noodén on 2014-01-30
Ok.  Wait till April for 14.04. :)  However, I've been running Tahr for a long time now and probably used to the rough edges.

---

### Post by Frogs Hair on 2014-01-30
If this is a summer endeavor 14.04 might be out by than anyway .  I installed 12.04 on new netbook last week and will install 14.04 in April. I thought t was better to stick with LTS releases and use the desktop for testing of new non LTS releases. Since I built the desktop the hard-drive of course  had no factory / OEM partitions and this makes installations less complicated.

---

### Post by Pinoy Tux on 2014-01-31
Summer vacation in the Philippines starts April.  Just in time for 14.04 (and an LTS version to boot).  I recommend waiting for it to be released instead of installing 12.04.

Also, you might want to download the [Ubuntu manual]("http://ubuntu-manual.org/") to get you started. 14.04 isn't available yet, so get the 13.10 manual since information is more recent.  Older versions are also available.

Enjoy, best of luck and welcome to the [Ubuntu] Linux family!

---

### Post by RadicaX on 2014-01-31
That is perfectly fine Rodel, as some have said, you can for sure try and use linux on liveCDs and the such too. ^^ which might be a good idea to preview which ones you might like to use. Ubuntu is amazing, (I still have like an 8.04 cd somewhere.) my favorite so far is Xubuntu. Its end of life is soon now, but hey, the new version is out this april! (So try a live cd or usb if you want. Try any and all the *buntus.) Have fun with Linux.

```
sudo ufw enable
```

```
sudo ufw default deny
```

Two of my favorite commands after doing an install, and before going on the net.

---

### Post by 3rdalbum on 2014-01-31
> **RadicaX said:**
> That is perfectly fine Rodel, as some have said, you can for sure try and use linux on liveCDs and the such too. ^^ which might be a good idea to preview which ones you might like to use. Ubuntu is amazing, (I still have like an 8.04 cd somewhere.) my favorite so far is Xubuntu. Its end of life is soon now, but hey, the new version is out this april! (So try a live cd or usb if you want. Try any and all the *buntus.) Have fun with Linux.

```
sudo ufw enable
```

```
sudo ufw default deny
```

Two of my favorite commands after doing an install, and before going on the net.

1. The poor OP probably has no idea what those commands do... if they even realise that these are commands to be put into the terminal.

2. A default install of Ubuntu does not listen for incoming connections from the internet anyway. Ubuntu only starts listening if you install something that listens (such as a web server), or if you enable Desktop Sharing.

Running commands that do exactly nothing to improve your security over the default, is not a win in my book.

---

### Post by RadicaX on 2014-02-01
> **3rdalbum said:**
> 1. The poor OP probably has no idea what those commands do... if they even realise that these are commands to be put into the terminal.

2. A default install of Ubuntu does not listen for incoming connections from the internet anyway. Ubuntu only starts listening if you install something that listens (such as a web server), or if you enable Desktop Sharing.

Running commands that do exactly nothing to improve your security over the default, is not a win in my book.

Hardly a soul knows much of anything when they start something, but they can always come back and reference things (Or ask when the time comes). 

While yes, a default install does not listen for incoming connections, it just seems like good practice to go ahead and setup the firewall, now of course, if the OP was to set up a server, he would also want to do more rules. I think I seen on Bodhi Zazens site recommending those two commands if you were just doing typical desktop related things though (Which was linked in the security sub-forums). Maybe I misunderstood? But just in case the OP decides to turn the firewall off a simple command fixes that.

```
sudo ufw disable
```

---

