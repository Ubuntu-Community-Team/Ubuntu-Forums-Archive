---
title: "Firefox and Jack"
date: 2013-08-16
forum: Ubuntu Studio
---

### Post by chkneater on 2013-08-16
I would sincerely like to know what is going on with Jack?  It works great for audio production, but God forbid I would like to browse firefox for some information while Jack is on.  If the page happens to have a Flashplayer on it or bsically anything you do, it runs slow and jams ALL the time, along with preventing pages from loading.  How is this going to get fixed or is there a fix out there??  Doubt, jack hasn't changed in five years.

---

### Post by gdesilva on 2013-08-16
Ditto. Started jackd while running Youtube and audio disappears.

---

### Post by jejeman on 2013-08-17
I gave already some solution if you are running firewire audo cards. Setting the asoundrc. Search the forum.
Flashplayer is not JACK compatible application, so we can not expect it to work with JACK. It is possible to use it with JACK, but without RT and little more latency.
Same goes for all non JACK aware applications.
As I said it before, JACK is not casual, consumer audio oriented.

---

### Post by chkneater on 2013-08-17
I get it, jack is complicated... I'm not the same person you replied to about this topic and my issue is not the same, and no firewire cards here...  from what I understand flash consumes OSS resources and there is a line that can be added to the ALSA config file to get jack to get along with flash.  And I understand adding latency and removing RT will give it time to load, but it still defeats the purpose of using applications that require JACK and also having to access any given web page which ALL have flash now.  It has been WAY to long to fix this well known issue.

IF someone knows the line to add to alsa config file please let me know, it is ridiculous that OpenSource programs can't be configured to get along with other popular and commonly used things like internets and flashes.

---

### Post by chkneater on 2013-08-18
Has anyone worked out a fix for this yet?

Haha, just kidding, in over 5 years they haven't figured out jack compatibility...  this is a call...

---

### Post by cub on 2013-08-19
You might get better reponse if addressing the issue on the JACK mailing list: [http://jackaudio.org/email](http://jackaudio.org/email)

;)

---

