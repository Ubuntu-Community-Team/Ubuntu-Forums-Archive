---
title: "Chromium browser started behaving weirdly !"
date: 2011-04-08
forum: Security
---

### Post by alienxx on 2011-04-08
Today while I was checking my mail,I got fooled by an e-mail , I clicked some link and it took me to some ugly looking website and then suddenly my browser started behaving weirdly , my cursor was running here and there , all the files on desktop opened automatically, then chromium got closed,I was unable to click at all...then comp got shutdown automatically.

Now I am afraid that some malware or someting like that **** got into my computer,I am also afraid it might have stolen my password(using gmail)....
I heard ubuntu(using 10.10)  doesn't get affected by viruses etc., but it did.
Please help me,currently it's working fine , I am able to write this post , but how to make sure nothing got into my computer, are there any antivirus programs for linux?

---

### Post by alienxx on 2011-04-09
please help me.... I am a small child in this ubuntu world.

---

### Post by Enigmapond on 2011-04-09
My only suggestion is to clear the cache/cookies/browsing history and see if that helps. If not open terminal and try:

```
sudo apt-get purge chromium-browser && sudo apt-get install chromium-browser
```

---

### Post by wacky_sung on 2011-04-09
First of all, did you install Wine or running virtual box running with any of the Window OS?If not, then installed [Bleachbit]("http://bleachbit.sourceforge.net/") to clear all your browser cache , java cache, flash cache, etc. I am very sure it can easy resolved all your issue. Likewise i am very much look forward if you can forward or paste that ugly looking website link here and i will verify it for you.

---

