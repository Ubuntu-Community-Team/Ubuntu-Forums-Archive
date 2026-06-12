---
title: "Amazon mp3 downloader for 12.04"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cottfcfan on 2012-04-09
I have seen some discussion about Rhythmbox not having an Amazon plugin & Banshee not working with Amazon in 12.04.
So here is the solution:
```
sudo apt-get install clamz
```
Then go to the clamz download page here:
[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)
and choose your country's link at the bottom of the page.
Then to test go to Amazon and download a free mp3.
After you have checked out it will offer to save a file. (.amz file)
Save to your Desktop.
Right click the file and open with Clammp3 downloader.
A terminal opens and your music will be saved to your Home folder.
Handy little tool:p

---

### Post by keithpeter on 2012-04-09
> **cottfcfan said:**
> I have seen some discussion about Rhythmbox not having an Amazon plugin & Banshee not working with Amazon in 12.04.
So here is the solution:
```
sudo apt-get install clamz
```


Hello cottfcfan

Great, that works, just installed and tested it. I can continue to damage my credit card :twisted:

Tip of the hat due to the coders.

Everyone including developers

There has to be an idiot-proof GUI for Amazon does there not?

Is it not possible to have the Amazon store within Rhythmbox?

---

### Post by cromat on 2012-04-09
I haven't personally tried, but it looks like there is a new ppa available that can be added to get latest banshee which the amazon mp3 store should be still working for.

[https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)

---

### Post by oldos2er on 2012-04-09
> **keithpeter said:**
> There has to be an idiot-proof GUI for Amazon does there not?


[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)

---

