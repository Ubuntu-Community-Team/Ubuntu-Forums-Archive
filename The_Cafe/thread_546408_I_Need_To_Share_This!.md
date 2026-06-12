---
title: "I Need To Share This!"
date: 2007-09-08
forum: The Cafe
---

### Post by DougieFresh4U on 2007-09-08
After having a power outage in my area yesterday, I was left with a broken system. Long story short: A black bar appeared in  the middle of my screen. After many attempts (and threads) at fixing it, I had to either reinstall or wait it out for some guru to come along. 
So, this afternoon I had an idea, I thought, let me reinstall but when partition part comes up I will resize and not overwrite all of my old system w/black bar across screen. So I resize partition in 1/2, new install on 2nd half, then it asked about import or some thing like that and I chose to import. After machine asking a few questions, it proceeded to install. After install and doing all updates and the tinkering every one does w/fresh installs, I some how got a screen up that asked for password and then my whole music collection appeared from borked  system.
What I am trying to say is, I am so glad that all was not lost and the good feeling I got knowing that most of every thing that was in the install that got borked yesterday I can still get access to and move to my new install. I am so impressed with what can be done with Linux
And to think how many other borked systems I have reinstalled and lost every thing when I didn't need to. Thanks to Linux and the devs for all the great work they are doing.  BTW, the borked system was Gutsy and the install today is Feisty
Just wanted to share this great experience that I encountered today:guitar:

---

### Post by n3tfury on 2007-09-08
well done!  it always feels good to do something like that without much fuss :)

---

### Post by loell on 2007-09-08
whew, that was close ;)

---

### Post by FuturePilot on 2007-09-08
It's a good thing you were able to save everything. I know it's too late now but maybe it just needed an fsck?:confused:

---

### Post by DougieFresh4U on 2007-09-08
> **FuturePilot said:**
> It's a good thing you were able to save everything. I know it's too late now but maybe it just needed an fsck?:confused:

Ok, you got my attention. i guess I didn't wait long enough, patients is not one of my strong points lately
I can still go into that system via grub. So please tell about this 'fsck' and maybe I will give it a shot.

---

### Post by Warren Watts on 2007-09-09
> **FuturePilot said:**
> It's a good thing you were able to save everything. I know it's too late now but maybe it just needed an fsck?:confused:

I have rescued borked installs on two different occasions with the use of fsck.  It's been a real lifesaver for me.

---

### Post by Palmyra on 2007-09-09
Why do you have your computer on at a time of bad weather?  As soon as I hear something in the sky, I turn my laptop off, and unplug everything.  

Make sure you don't take any chances.

---

### Post by FuturePilot on 2007-09-09
> **DougieFresh4U said:**
> Ok, you got my attention. i guess I didn't wait long enough, patients is not one of my strong points lately
I can still go into that system via grub. So please tell about this 'fsck' and maybe I will give it a shot.
You can boot the live CD and run this in a terminal
```
sudo fsck /dev/hda1
``` replace hda1 with whatever partition the damaged system is on. With Feisty it will probably be sdaX. And make sure it's **not** mounted or else it will be a real mess.

---

### Post by regomodo on 2007-09-09
thats unusual. Does Gutsy mot have the usual filecheck (dirty bit?) at every boot? I've accidentally switched my comp off at the wall and Feisty sorted itself out each time.

What FS are you using?

---

### Post by DougieFresh4U on 2007-09-09
> **Palmyra said:**
> Why do you have your computer on at a time of bad weather?  As soon as I hear something in the sky, I turn my laptop off, and unplug everything.  

Make sure you don't take any chances.

It was not bad weather.  A transformer in the area just blew up/caught  on fire

---

