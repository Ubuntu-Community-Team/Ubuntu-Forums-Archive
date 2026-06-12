---
title: "Check Out RAM usage due to firefox!"
date: 2010-12-07
forum: The Cafe
---

### Post by akand074 on 2010-12-07
Take a look at the picture of my conky. Never have I had that much memory usage. It's been doing that ever since I installed Ubuntu 10.10 if I remember correctly (though it never got that high) I was actually at 92% memory usage a few seconds ago. I'm thinking this has something to do with the fact that I have a /home folder that hasn't been cleaned in forever, so perhaps a profile causing a memory leak? Either way I have no intention of fixing it now because I just finished building my new system (this one going to a friend) and when I have time (after exams likely) I'll be doing a clean install and transfer data to a brand new clean /home folder. Just thought some people might find this funny/interesting :P

---

### Post by juancarlospaco on 2010-12-07
one word:
Flash

---

### Post by akand074 on 2010-12-07
Oh yeah for sure. This starts as soon as I start streaming videos. Forgot about that.

---

### Post by juancarlospaco on 2010-12-07
one word:
HTML5

---

### Post by CharlesA on 2010-12-07
Might want to blank out yer public IP.

---

### Post by WinterMadness on 2010-12-07
> **CharlesA said:**
> Might want to blank out yer public IP.

I agree... and lets just say it should be blanked out, or the image removed from his post quick

---

### Post by lovinglinux on 2010-12-07
I don't think is flash fault. You have a serious memory leak there. 2.46 Gb for Firefox is simply too much. Not even Opera uses that amount of RAM, even when playing flash. Besides, Firefox uses plugin isolation. So, if it was flash, then the process using too much ram should be plugin-container, not firefox-bin.

Most likely is an extension leaking memory. I would start Firefox in safe mode and disable all extensions, then enable one-by-one until you find the culprit.

```
firefox -safe-mode
```

Also check the memory tweaks at [http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)

---

### Post by clonne4crw on 2010-12-07
What version of Firefox are you running? I'm using 3.6.12, and it usually uses 100-200 Mb, never a problem. Even when running flash stuff.

Nice Conky config, btw.

---

### Post by dexter777 on 2010-12-07
I had many problems with firefox and my computer ram. so i chose chrome.

---

### Post by matt_symes on 2010-12-07
> Take a look at the picture of my conky.

More tea vicar. Hurrumph ;)

---

### Post by akand074 on 2010-12-07
I'm using version 3.6.12 also. It's definitely some sort of memory leak somewhere.. maybe I'll find it sometime just for the fun of it. I don't think I've even had so much swap used before.

---

### Post by Helkaluin on 2010-12-08
Should be extentions. Do you have Firebug installed?

Take a look at: [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by akand074 on 2010-12-08
Well I only have adblock plus and extended status bar. I've had the same extensions in 10.04 and 9.10.. Maybe new update though?

---

### Post by lovinglinux on 2010-12-08
> **akand074 said:**
> Well I only have adblock plus and extended status bar. I've had the same extensions in 10.04 and 9.10.. Maybe new update though?

Start Firefox with a clean profile and check if the problem persists.

```
firefox -P
```

---

### Post by akand074 on 2010-12-08
> **lovinglinux said:**
> Start Firefox with a clean profile and check if the problem persists.

```
firefox -P
```

I just restarted my computer.. it started running so unbearably slow it was crazy! I'm going to see if the issue comes back again and pay attention to when. If it does then I might start a new profile or shut off extensions and start them one by one if I feel like taking the time. Otherwise I have to do a clean install soon any ways on a new hard drive so not a big deal.

---

### Post by hari.iiitb on 2011-03-16
Wow! how did you configure your conky like that? Mine just shows the default black one..

---

### Post by rg4w on 2011-03-16
I don't know if this is relevant, but I have a habit of opening and closing a lot of tabs (sometimes 20 or more during a good reading session), and after a few hours and I'm back to just a couple tabs I see FF is still using a surprising amount of RAM.

Whether this constitutes a true "leak" or not isn't a detail I've explored, but I do believe it seems reasonable to expect that once I've reduced my tab set down to a couple of tabs with lightweight pages in them that FF would have politely freed up the memory I'm no longer using.

I see this far more seriously with FF on my Mac than on my Ubuntu machine, FWIW.

Do you use a lot of tabs in your browsing?  Open and close many during a session?

---

### Post by Francewhoa on 2012-02-22
The following worked for us [http://ubuntuforums.org/showpost.php?p=11709281&postcount=16](http://ubuntuforums.org/showpost.php?p=11709281&postcount=16)

---

### Post by lovinglinux on 2012-02-22
Please leave the dead rest in peace. 

Closed because of necromancy.

---

