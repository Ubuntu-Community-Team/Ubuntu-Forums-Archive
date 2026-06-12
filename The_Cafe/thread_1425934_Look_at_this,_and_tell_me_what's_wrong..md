---
title: "Look at this, and tell me what's wrong."
date: 2010-03-09
forum: The Cafe
---

### Post by swoll1980 on 2010-03-09
This is a screener I took of the Kubuntu 10.04 kickoff menu (leave tab) tab. Notice anything missing?

---

### Post by chris4585 on 2010-03-09
Where's shutdown?

---

### Post by Tibuda on 2010-03-09
shutdown and reboot?

---

### Post by swoll1980 on 2010-03-09
Ding ding ding! We have 2 winners.

---

### Post by swoll1980 on 2010-03-09
> **chris4585 said:**
> Where's shutdown?

I have no clue. 

```
sudo shutdown now
```

I guess.

---

### Post by The Toxic Mite on 2010-03-09
> **swoll1980 said:**
> ```
sudo shutdown now
```I guess.

That'll have to do, I guess... :?

---

### Post by fatality_uk on 2010-03-09
> **swoll1980 said:**
> Notice anything missing?

Waldo? :D

---

### Post by ibuclaw on 2010-03-09
Why not use the physical power button on your computing device?

---

### Post by The Toxic Mite on 2010-03-09
> **ibuclaw said:**
> Why not use the physical power button on your computing device?

That also, but don't hold it for too long since you'll lose all your work. Also, there's the added risk of a borked filesystem since it wouldn't be cleanly unmounted.

---

### Post by cascade9 on 2010-03-09
Can you logout and then shutdown from the login? 

I'd probably try using the traditional menu to see if that works (it probably wont, but its worth a try). Then again I dont like that menu system so I'm biased LOL

---

### Post by inobe on 2010-03-09
> **swoll1980 said:**
> This is a screener I took of the Kubuntu 10.04 kickoff menu (leave tab) tab. Notice anything missing?

that's a kubuntu problem, in suse with kde 4.4 shutdown is there.

---

### Post by swoll1980 on 2010-03-09
I appreciate the advise. This thread is merely for the comedic value of a shutdown menu without a shutdown option. I realize there's a hundred ways around this, and that it's still in development. I would file a bug report, but I know there's no way this isn't on there already.

---

### Post by doorknob60 on 2010-03-09
Question: Are you using KDM? If not, that's probably why.

---

### Post by Regenweald on 2010-03-09
I'm impressed with the look of your desktop though. You just scored one for KDE on my machine.

---

### Post by swoll1980 on 2010-03-09
> **doorknob60 said:**
> Question: Are you using KDM? If not, that's probably why.

No I'm not using kdm. Guess that explains that.

---

### Post by swoll1980 on 2010-03-09
> **Regenweald said:**
> I'm impressed with the look of your desktop though. You just scored one for KDE on my machine.

This is default kde 4.4 It does look pretty cool.

---

### Post by chessnerd on 2010-03-09
This happened when I installed KDE on my laptop alongside Gnome in Karmic. Also, Log Out and Switch User didn't work. I ended up shutting down via command line and then uninstalled KDE as quickly as I could.

KDE has always been buggier for me than Gnome. However, I have a new computer that I got from my aunt this week and I've vowed to put Kubuntu Lucid Lynx on it when it comes out. Hopefully a clean KDE install will work for me. 

Also, KDE 4.4 is looking awesome. You can set up tabs on windows for applications! That's a feature I've wanted in an OS for a long time. Forget using the task bar to switch between browser and word processor, just have two tabs on one window instead of two windows. It's so simple and intuitive!

---

### Post by jrusso2 on 2010-03-09
For some reason in Kubuntu if you don't use KDM but use GDM this is what happens.

---

### Post by RiceMonster on 2010-03-09
> **jrusso2 said:**
> For some reason in Kubuntu if you don't use KDM but use GDM this is what happens.

It's not Kubuntu specific. KDE always relies on KDM for shutdown/restart and suspend/hibernate.

I think GNOME relies on GDM for that as well, not sure if you can use KDM instead, though.

---

### Post by dragos240 on 2010-03-09
> **RiceMonster said:**
> It's not Kubuntu specific. KDE always relies on KDM for shutdown/restart and suspend/hibernate.

I think GNOME relies on GDM for that as well, not sure if you can use KDM instead, though.

Also, if you don't use GDM for GNOME you cannot mount anything, so, big problem.

---

### Post by swoll1980 on 2010-03-09
> **dragos240 said:**
> Also, if you don't use GDM for GNOME you cannot mount anything, so, big problem.

yeah, and I just found out that if you use GDM KDE can't mount anything.

---

### Post by squilookle on 2010-03-09
> **RiceMonster said:**
> It's not Kubuntu specific. KDE always relies on KDM for shutdown/restart and suspend/hibernate.

I think GNOME relies on GDM for that as well, not sure if you can use KDM instead, though.

I'm running gnome on arch without gdm, and I can shutdown from the system menu and mount things. When I ran kde without kdm on the same arch install, however, I also did not have shutdown in the leave menu, and had to do it from the command line...

---

### Post by Post Monkeh on 2010-03-10
> **chessnerd said:**
> This happened when I installed KDE on my laptop alongside Gnome in Karmic. Also, Log Out and Switch User didn't work. I ended up shutting down via command line and then uninstalled KDE as quickly as I could.

KDE has always been buggier for me than Gnome. However, I have a new computer that I got from my aunt this week and I've vowed to put Kubuntu Lucid Lynx on it when it comes out. Hopefully a clean KDE install will work for me. 

Also, KDE 4.4 is looking awesome. You can set up tabs on windows for applications! That's a feature I've wanted in an OS for a long time. Forget using the task bar to switch between browser and word processor, just have two tabs on one window instead of two windows. It's so simple and intuitive!

i've always found it buggy to install one ubuntu variant  on top of another fully set up ubuntu. it just takes a bit of tweaking to get things working as they should as the different de's want to use all their own services to do things

---

