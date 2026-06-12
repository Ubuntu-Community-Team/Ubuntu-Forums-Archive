---
title: "nvidia current out of date"
date: 2012-06-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ELD on 2012-06-23
Is anyone planning on updating nvidia current? I need the latest to support my chip.

---

### Post by terry_gardener on 2012-06-23
you can get it from the xorg edgers ppa

---

### Post by ELD on 2012-06-23
I know that but I am wandering if someone is going to be updating the official repo?

---

### Post by Harry33 on 2012-06-24
That would be Alberto Milone I think.
The latest stable is 295.59 from June 2012.
There is 259.53 from May 2012 in official repos.
The 302.** versions are not stable yet.

---

### Post by ELD on 2012-06-24
Yeah i would need .59

---

### Post by firekage on 2012-06-24
Can somebody help me? I have problem with nvidia-current. New is 295.xx but my Ubuntu still installs 280.13 when using ```
apt-get install nvidia-current
```. I don't know why it doesen't want to install newer from repo.

---

### Post by cariboo on 2012-06-24
> **firekage said:**
> Can somebody help me? I have problem with nvidia-current. New is 295.xx but my Ubuntu still installs 280.13 when using ```
apt-get install nvidia-current
```. I don't know why it doesen't want to install newer from repo.

Try:

```
sudo apt-get install nvidia-current-updates
```

---

### Post by Guilden_NL on 2012-06-24
> **firekage said:**
> I don't know why it doesen't want to install newer from repo.

Maybe a little blow back from Linus flipping off nVidia last week? :lolflag:

---

### Post by jfernyhough on 2012-06-24
302.17 is in x-swat (though for precise, not quantal, it should still work fine).

---

### Post by vsespb on 2012-06-25
opposite problem.

I got 302.x version, and then found that my box cannot wakeup and that is know problem [http://www.nvnews.net/vbulletin/showthread.php?t=179956&page=5](http://www.nvnews.net/vbulletin/showthread.php?t=179956&page=5) also I found that 302.x is not considered stable.

How do I set my package manager to only receive stable version ?

Ubuntu 10.04.

---

### Post by vsespb on 2012-06-25
Oh, I get it

apt-cache policy nvidia-current
...
  Version table:                                                                                                                                                                                                                                                               
     302.17-0ubuntu1~lucid~xup1 0                                                                                                                                                                                                                                              
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Packages        

well, ubuntu-x-swat: "This PPA is for stable upstream releases of X.org components."

seems not so stable.

---

### Post by Harry33 on 2012-06-25
> **jfernyhough said:**
> 302.17 is in x-swat (though for precise, not quantal, it should still work fine).

Nope, it really does not.
X Swat (X Updates) version is for Precise and thus it depends on xserver_1.11 ABI.
In Quantal we have xserver_1.12 and thus a newer ABI.

Installing Precise version would remove the xserver_1.12.

---

