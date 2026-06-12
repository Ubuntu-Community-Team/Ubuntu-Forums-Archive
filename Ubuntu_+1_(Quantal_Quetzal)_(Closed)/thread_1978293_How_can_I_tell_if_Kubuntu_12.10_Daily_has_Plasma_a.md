---
title: "How can I tell if Kubuntu 12.10 Daily has Plasma and KDE Applications 4.8.3"
date: 2012-05-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mparillo on 2012-05-11
See: [http://www.kubuntu.org/news/kde-sc-4.8.3](http://www.kubuntu.org/news/kde-sc-4.8.3)

---

### Post by JMB74 on 2012-05-11
Package list is here

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/quantal-desktop-i386.manifest](http://cdimage.ubuntu.com/kubuntu/daily-live/current/quantal-desktop-i386.manifest)

As far as I have seen no 4.8.3 packages have yet been pushed to the Quantal repos. Presumably once they are they will start being included in the daily build manifest.

Keeping an eye on the quantal upload mailing list may also give you a heads up on when they are likely to arrive.

[http://lists.ubuntu.com/mailman/listinfo/Quantal-changes](http://lists.ubuntu.com/mailman/listinfo/Quantal-changes)

---

### Post by mparillo on 2012-05-11
> **JMB74 said:**
> Package list is here

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/quantal-desktop-i386.manifest](http://cdimage.ubuntu.com/kubuntu/daily-live/current/quantal-desktop-i386.manifest)

As far as I have seen no 4.8.3 packages have yet been pushed to the Quantal repos. Presumably once they are they will start being included in the daily build manifest.

Keeping an eye on the quantal upload mailing list may also give you a heads up on when they are likely to arrive.

[http://lists.ubuntu.com/mailman/listinfo/Quantal-changes](http://lists.ubuntu.com/mailman/listinfo/Quantal-changes)

Thank you very much, and I believe you are correct.
I successfully installed today's daily build to VMware Player (and the VMware tools auto-installed successfully), and the About KDE in Dolphin and rekonq showed: 
Platform Version 4.8.2 (4.8.2).

---

### Post by JMB74 on 2012-05-11
Maybe 4.8.3 will be pushed once UDS is wrapped up.

Saying that, I don't think it's that long until the first KDE 4.9 beta tagging and release, so maybe that will be uploaded to Quantal instead?

---

### Post by mparillo on 2012-05-14
Today's updates to Friday's daily build appear to have pushed 4.8.3:
Platform Version 4.8.3 (4.8.3)

---

### Post by mparillo on 2012-05-31
KDE 4.8.3 has been pushed to Kubuntu 12.04 also.
No intervention was necessary:
[http://www.kubuntu.org/news/kde-sc-4.8.3](http://www.kubuntu.org/news/kde-sc-4.8.3)

---

### Post by xebian on 2012-06-01
I believe 4.9 beta 1 should be out (not publicly yet), and will be in quantal shortly?

---

### Post by JMB74 on 2012-06-01
Seems to have been a few bumps getting the 4.9 beta together, if mailings lists are correct. But seems to be going ahead.

Says kubuntu devs have been to some effort to start packaging it, so presumably will arrive at some not too distant point.

---

### Post by mparillo on 2012-06-15
> **xebian said:**
> I believe 4.9 beta 1 should be out (not publicly yet), and will be in quantal shortly?

I think we must be getting close.  I just loaded the 2012-06-09 Daily Build, and after:
sudo apt-get update
sudo apt-get dist-upgrade
I now have:
Platform Version 4.8.90 (4.8.90)

---

### Post by JMB74 on 2012-06-15
4.8.90 = KDE 4.9 Beta 2

Seems to work nicely.

---

