---
title: "Artful Insecure Connection problem"
date: 2017-05-26
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2017-05-26
On Xenial I have no problem using Firefox to log in to my doctor's office over their portal.

On Artful same exact same attempt to log in there's a message about "Insecure Connection" and refuses to access the site.

Any ideas, or how do I generate an Ubuntu Bug for this?

Thanks.

---

### Post by dino99 on 2017-05-26
If the doctor's portal is still using 'http' instead of 'https', then you get the explanation; but the exposed message also propose to bypass that warning if you want to take the risk.

---

### Post by jerrylamos on 2017-05-26
> **dino99 said:**
> If the doctor's portal is still using 'http' instead of 'https', then you get the explanation; but the exposed message also propose to bypass that warning if you want to take the risk.
The medical groups site is:
[https://www.mydh.org/portal/](https://www.mydh.org/portal/)
There is a https.  This is from xenial wonder what artful sees, let me reboot.
Thanks.

---

### Post by CharlesA on 2017-05-26
> **jerrylamos said:**
> The medical groups site is:
[https://www.mydh.org/portal/](https://www.mydh.org/portal/)
There is a https.  This is from xenial wonder what artful sees, let me reboot.
Thanks.

Seems like the certificate chain is incomplete on that site (per ssllabs). That's probably why you are getting the warning - the browser doesn't know to trust it.

What is the exact error you are getting?

---

### Post by jerrylamos on 2017-05-26
Artful screen says:

[https://www.mydh.org/portal/](https://www.mydh.org/portal/)
Your connection is not secure
The owner of [www.mydh.org](www.mydh.org) has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website.
Learn more…
Go Back                        Advanced
Report errors like this to help Mozilla identify and block malicious sites

that's all.

Help says" l Firefox  50.1.0

Let me go check Xenial's level of Firefox

BTW, Google Chrome on Artful has no such problem.

---

### Post by jerrylamos on 2017-05-26
Oh, Firefox on Xenial is 53.0.2
which is a different level than on Artful's 50.0.1

Let me see if I can up level the Firefox I got with Artful, 
BTW my Artful is from .iso from 
[http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso.zsync)
and have done several 
sudo apt-get update 
sudo apt-get dist-upgrade

---

### Post by cariboo on 2017-05-26
I just checked Firefox on Xubuntu 17.10, it's version 52.0.1 here. I don't get any messages about an insecure site when clicking your link.

---

### Post by CharlesA on 2017-05-26
Firefox 53 here and I don't have any errors either. o.O

---

### Post by jerrylamos on 2017-05-26
Tried to upgrade Artful level of Firefox.
No luck.  Whatever I tried didn't work....Try again.

---

### Post by jerrylamos on 2017-05-26
No luck.  Artful says:

jerry@Lenovo2:~$ sudo apt-get upgrade firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version (50.1.0+build2-0ubuntu1).
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Somehow my Artful list of "newest version" is way out of date.  How do I get Artful updated?  sudo apt-get update isn't doing it...

---

### Post by howefield on 2017-05-26
> **jerrylamos said:**
> Somehow my Artful list of "newest version" is way out of date.  How do I get Artful updated?  sudo apt-get update isn't doing it...

You don't, at least not through the Ubuntu repositories yet anyway, Artful is still on the version that you already have. : [https://packages.ubuntu.com/search?keywords=firefox](https://packages.ubuntu.com/search?keywords=firefox)

---

### Post by cariboo on 2017-05-26
I've got proposed enabled, so I installed the newer version.

---

### Post by wildmanne39 on 2017-05-27
I have seen that message before and I received that message when I clicked on the link you provided, but I have also received that message with 16.04 and 17.04.

It has nothing to do with 17.10 it is firefox detecting that the site is not secure.

Firefox is supposed to let you add it as an exception so you can access it but that does not work for me, so it may be a bug in firefox.

---

### Post by Smask on 2017-05-27
The latest releases of Firefox dropped support for SHA-1 certificates. Might this affect the browsing in some way?

---

### Post by jerrylamos on 2017-05-27
Tried this to update Firefox:from [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa)

Adding this PPA to your system
You can update your system with unsupported packages from this untrusted PPA by adding ppa:ubuntu-mozilla-daily/ppa to your system's Software Sources. (Read about installing)

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update

Didn't work.  Artful is stuck on old firefox 50.1.0

Anybody any hints?

Thanks

---

### Post by mc4man on 2017-05-27
> **jerrylamos said:**
> 

Didn't work.  Artful is stuck on old firefox 50.1.0

Anybody any hints?

Thanks
enabled proposed repo, update sources, upgrade firefox to 53.xx, disable proposed, update sources

---

### Post by CharlesA on 2017-05-27
> **wildmanne39 said:**
> I have seen that message before and I received that message when I clicked on the link you provided, but I have also received that message with 16.04 and 17.04.

It has nothing to do with 17.10 it is firefox detecting that the site is not secure.

Firefox is supposed to let you add it as an exception so you can access it but that does not work for me, so it may be a bug in firefox.

If you click on the Advanced button it'll tell you the exact reason why it thinks it is insecure. :)

> **Smask said:**
> The latest releases of Firefox dropped support for SHA-1 certificates. Might this affect the browsing in some way?

The site in the OP is using a SHA256 cert that was renewed about two weeks ago.

---

### Post by jerrylamos on 2017-05-27
> **mc4man said:**
> enabled proposed repo, update sources, upgrade firefox to 53.xx, disable proposed, update sources

How do I enable proposed repro?

Thanks

---

### Post by howefield on 2017-05-27
Develepers options tab in Software & Updates.

---

### Post by jerrylamos on 2017-05-27
> **howefield said:**
> Develepers options tab in Software & Updates.

That worked for update, Firefox updated to 53.0, Artful Firefox still gets "Your connection is not secure" while Zesty does not.

Updated Artful with proposed on.  Got a bunch of updates and went from Artful 21 to Artful 22.

Bug still exists.

Oh well I've still got Zesty which works for this case.

I don't know how to submit an ubuntu-bug for this so maybe someone else will experience the problem.

---

### Post by mc4man on 2017-05-27
Maybe setup a new Firefox profile & see if site works then..
in terminal without FF running, self explanatory (give the new one any name you want other than current of 'default'
```
 firefox -profilemanager
```

---

### Post by jerrylamos on 2017-05-31
mc4man,

firefox -profilemanager

worked.  I just called it test.  Thanks.

I assume Artful got its profilemanager from Xenial since Artful Firefox picked up bookmarks etc. from Xenial Firefox since I do a Sync.  
Google-chrome I also import settings etc. etc. from Xenial no such problem, just Firefox

Perhaps no one else will get this situation....

Thanks for your solution.

---

