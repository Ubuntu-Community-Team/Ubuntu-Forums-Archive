---
title: "Laptop logs itself out automatically"
date: 2013-01-22
forum: Ubuntu Development Version
---

### Post by Deuce1912 on 2013-01-22
Hello, 

The issue I'm having is on my laptop which was running 12.10, then upgraded to 13.04. If the laptop isn't running any processes it will stay logged in. As soon as I open an application and it sits for (I don't know specifically) 10-30 minutes the laptop logs itself out to the lightdm login screen.

I thought the issue was possibly with 12.10 so I ran the upgrade, which I rarely do as I normally do a fresh install but this wasn't a mission critical machine so I thought ah what the heck, why not?

I don't believe the problem is a 13.04 issue as it was initially on 12.10 and now persists into 13.04. Does anyone have any thoughts?

Thanks for any and all help,

- Deuce1912

---

### Post by cariboo on 2013-01-22
Have you created another user to see if the problem affects him/her too?

---

### Post by Deuce1912 on 2013-01-23
> **cariboo907 said:**
> Have you created another user to see if the problem affects him/her too?

I have not. I'm about to go to bed, so I'll try that when I get home from work tomorrow.

- Deuce1912

---

### Post by Deuce1912 on 2013-01-24
Okay, I've created a test account. When I returned several hours later I saw the computer had a blank screen. When I moved the mouse it would not bring back my Ubuntu desktop. I rebooted the machine and then logged back into the test account. I checked the system settings and turned off the lock feature under the brightness and lock.

I'm going to let it sit now (again going to bed) so I will check it tomorrow when I get home from work.

- Deuce1912

---

### Post by Deuce1912 on 2013-01-25
I checked the laptop when I got home and still logs out even on the new test account. I don't know where to go from here. It's not a huge deal, but if I am working on something and have to leave and forget to save something I will lose what I was working on. Any ideas would be greatly appreciated. 

- Deuce1912

---

### Post by Deuce1912 on 2013-02-07
Fresh install fixes all.  I still wish I knew what the issue was.

- Deuce1912

---

### Post by jpeddicord on 2013-02-07
> **Deuce1912 said:**
> Fresh install fixes all.  I still wish I knew what the issue was.

- Deuce1912

It was likely a graphics driver/configuration issue. The display was probably crashing, causing you to be kicked back to the login screen.

Did you get any crash popups after it happened? Sometimes weird things like these show up during development.

---

### Post by Deuce1912 on 2013-02-08
Now that you mention it, I was receiving crash reports every once and a while.  It didn't happen everytime it booted me to the login screen, but I was getting them.  Thanks for the info.

- Deuce1912

---

