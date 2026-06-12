---
title: "Eclipse installation"
date: 2014-01-24
forum: Ubuntu Development Version
---

### Post by hoboy on 2014-01-24
Since I have upgrade to 
"Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty"
when I install eclipse I can launch when I try to create a for example new project File nothing happen
when I click on proejct fan to open nothing happen.

---

### Post by TheFu on 2014-01-24
14.04 is not a release ... until April. It is either alpha or beta software now.
Thanks for being a beta tester!

Hopefully this will be moved to the +1 forum.

---

### Post by mörgæs on 2014-01-24
I shall move it, but please remember that the development forum is meant for people who provide help by testing the new release and post their feedback (here or in Launchpad). It's not meant as a place for regular support.

---

### Post by hoboy on 2014-01-26
Tks for the info.
Where shall I go for help ?
Is there any patch for the eclipse issues ?

---

### Post by hoboy on 2014-01-26
Somebody please help I am desperated 
I don't want reinstall ubuntu, as it is difficult to go back to an early ubuntu version

---

### Post by xc3RnbFO8P on 2014-01-26
I'm installing  Eclipse now, not sure I can help you...

---

### Post by xc3RnbFO8P on 2014-01-26
Here is 2  screenshot of Eclipse in Synaptic Package Manager

[[img]http://farm4.staticflickr.com/3774/12151665426_96c5d1ca6c_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12151665426/)
[Screenshot from 2014-01-26 14:05:44](http://www.flickr.com/photos/96052779@N07/12151665426/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by xc3RnbFO8P on 2014-01-26
Ok, its up and running, what do you want me to do?

[[img]http://farm8.staticflickr.com/7314/12151762214_5f823c0542_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12151762214/)
[Screenshot from 2014-01-26 14:29:52](http://www.flickr.com/photos/96052779@N07/12151762214/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by hoboy on 2014-01-26
the situation is that if one install eclipse 3.8 from the ubuntu software center that works.
But if you downlaod eclipse and unzip it 
one has to do something like this:
#!/bin/bash
export UBUNTU_MENUPROXY=0
/home/luc/DEVS1/FuseIDE-6.0.0/FuseIDE
-----------
to make it work, that is extremly ennoying

---

### Post by hoboy on 2014-01-26
eclipse has a newer version now like 4.3.1. it is pitie that one can not use it

---

### Post by xc3RnbFO8P on 2014-01-26
Did you check if you have permission to run FuseIDE?
Just saying...

---

### Post by hoboy on 2014-01-26
the problem is all type of eclipse I install, that mean unzip and try to run it.
But when one does this export UBUNTU_MENUPROXY=0
then run eclipse it works

---

### Post by yCAxYRA on 2014-01-26
> **hoboy said:**
> eclipse has a newer version now like 4.3.1. it is pitie that one can not use it

If you download 4.3.1 from eclipse site and have java installed it works fine? For me unleast... Edit: 3.8 from repos seems to work at first glance too. Considering that this isnt even beta it works remarkably well for me :).

---

### Post by mc4man on 2014-01-27
If your only issue with your downloaded, not in Ubuntu repos, eclipse is that you need to start it under an env then find & edit it's launcher (.desktop) to do that
Add this to the front of the Exec= line
env UBUNTU_MENUPROXY=0
Ex.
```
Exec=env  UBUNTU_MENUPROXY=0 eclipse
```

---

