---
title: "apt-get Vs aptitude"
date: 2010-11-17
forum: Server Platforms
---

### Post by VipX1 on 2010-11-17
I tried Ubuntu 10.10 on my laptop at the weekend. I noticed Aptitude is no longer installed with this release. Only apt-get was available for command line installation etc. Why is this the case. Ubuntu maintain apt-get and so this application is there priority I am guessing and of course they prefer apt-get. Then if so, is apt-get better than aptitude.
I was always under the impression that aptitude was better than apt-get just from reading articles and other bits. Some quick test show they do the very same job of finding dependencies. 
When I am installing applications or updating my Ubuntu servers which application should I use?? Which application is keeping up with the times?

---

### Post by sikander3786 on 2010-11-17
Both of them are good. My personal opinion, aptitude is better at handling dependencies.

You can install aptitude on Maverick by

```
sudo apt-get install multiget
```

Google apt-get vs aptitude and you'll see many opinions there.

---

### Post by arrrghhh on 2010-11-17
+1 to sikander's comments about googling and looking at all the opinions ;)

With that said, back in the day aptitude used to be MUCH better at removing old stuff when you removed a package.  I believe apt-get has been 'fixed' in a sense for a long time tho, so there's not a huge difference between the two anymore.  I just use aptitude out of habit now :p

---

### Post by endotherm on 2010-11-17
> **VipX1 said:**
> I tried Ubuntu 10.10 on my laptop at the weekend. I noticed Aptitude is no longer installed with this release. Only apt-get was available for command line installation etc. Why is this the case. Ubuntu maintain apt-get and so this application is there priority I am guessing and of course they prefer apt-get. Then if so, is apt-get better than aptitude.
I was always under the impression that aptitude was better than apt-get just from reading articles and other bits. Some quick test show they do the very same job of finding dependencies. 
When I am installing applications or updating my Ubuntu servers which application should I use?? Which application is keeping up with the times?
I'd just use apt-get. since Feisty, the functional difference has mainly been the number of keystrokes to type the command.

---

### Post by sikander3786 on 2010-11-17
> **endotherm said:**
> I'd just use apt-get. since Feisty, the functional difference has mainly been the number of keystrokes to type the command.
If you mean the difference between apt-get and aptitude, it is only 1 character :-)

---

