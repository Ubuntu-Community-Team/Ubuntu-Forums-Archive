---
title: "Utopic Flashback (with Compiz) boots to the default wallpaper unable to change it"
date: 2014-09-25
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-09-25
I booted into Utopic after a couple of days being away. I noticed some previous Ubuntu versions wallpapers were installed recently.
Normally I am greeted with my background but today it was the default wallpaper. Then after logging in I had the same thing. I tried to change it back to what it was to no avail.

Then I tried changing the wallpaper to anything and no bueno.

Here is what I am stuck with (even though in Appearance it shows the wallpaper I had been using):

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-09-25113958.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-09-25113958.php")

The time is also 4 hours behind the actual time and that has been happening off and on for a while.

---

### Post by Cavsfan on 2014-09-26
Same thing in Unity.

---

### Post by cariboo on 2014-09-26
I've run into the same thing on Unity here. On first startup this morning, the system came up with just the background and nothing else. After creating a new folder on the desktop, I was able to navigate to /usr/bin/xterm using nautilus, and opened a terminal. I was then able to reset compiz:

```
dconf reset -f /org/compiz/
```

and reset unity:

```
setsid unity
```

I was able to use unity. I had to reset the icon size and auto-hide, but right-click doesn't work on the desktop,  so going to System Settings->Appearance is the only way to make any changes, but changing the desktop doesn't work. I can select a new one, but nothing else happens.

---

### Post by Cavsfan on 2014-09-26
> **cariboo907 said:**
> I've run into the same thing on Unity here. On first startup this morning, the system came up with just the background and nothing else. After creating a new folder on the desktop, I was able to navigate to /usr/bin/xterm using nautilus, and opened a terminal. I was then able to reset compiz:

```
dconf reset -f /org/compiz/
```

and reset unity:

```
setsid unity
```

I was able to use unity. I had to reset the icon size and auto-hide, but right-click doesn't work on the desktop,  so going to System Settings->Appearance is the only way to make any changes, but changing the desktop doesn't work. I can select a new one, but nothing else happens.

Thanks I'll give that a try. I've been in 14.04 LTS for some time. Guess I'll go give it another look.

---

### Post by Cavsfan on 2014-09-26
I should mention that I didn't really lose anything except the wallpaper. I still had everything else; just the inability to have any wallpaper.

So I booted into Unity and I had the Unity bar on the side but nothing else and so I reset it with the commands you mentioned.
Then I couldn't change sessions. No matter what I chose I got Unity, Then I remembered that you pretty much have to redo CCSM to get flashback back, I did that and got flashback back as it was.

There were also some updates but they didn't fix this problem.

I was able to login as guest and change the wallpaper to whatever I wanted.

Then when I logged in as me no wallpaper again. I guess I shouldn't complain too much as I have everything except the ability to change the background.
What is this the beta from hell? :p

---

### Post by mc4man on 2014-09-26
I have a fairly recent install that I haven't used much so updated & installed flashback.
See no issues changing wallpapers at all.
Overall flashback w/compiz works OK though the default window deco is awful, (orange here
Have you tried a guest or new user account?

---

### Post by cariboo on 2014-09-26
I was away from the computer most of the day, when I went to unlock the screen, I saw that the wallpaper of the lock screen changed, but the desktop itself was still using the same wallpaper I set earlier this week.

**Edit:** I just tried to change the wallpaper again, and found the lockscreen/lightdm wallpaper does change immediately, just not the desktop wallpaper.

---

### Post by Cavsfan on 2014-09-27
> **mc4man said:**
> I have a fairly recent install that I haven't used much so updated & installed flashback.
See no issues changing wallpapers at all.
Overall flashback w/compiz works OK though the default window deco is awful, (orange here
Have you tried a guest or new user account?

Yes I did login as guest and could change the wallpaper to whatever I want. But when I login all I have is the orange default wallpaper and it won't change.
All is good on Utopic Mate Remix although I did lose emerald window decorator, which I had working prior to a couple of days ago.
I installed them both (on Utopic and Utopic Mate) from this ppa - [http://www.noobslab.com/2014/02/emerald-decorator-and-themes-available.html](http://www.noobslab.com/2014/02/emerald-decorator-and-themes-available.html)

> **cariboo907 said:**
> I was away from the computer most of the day, when I went to unlock the screen, I saw that the wallpaper of the lock screen changed, but the desktop itself was still using the same wallpaper I set earlier this week.

**Edit:** I just tried to change the wallpaper again, and found the lockscreen/lightdm wallpaper does change immediately, just not the desktop wallpaper.

I couldn't change either one nothing but orange here. But I got some updates on Utopic Mate - more compiz updates and the 3.16.0-18-generic. I need to go back to Utopic and see if anything has changed.
I get confused with so many Utopics all up in here. :lol:

---

### Post by Cavsfan on 2014-09-27
Same orange background on Utopic even though in Appearance it looks like it's set to a wallpaper. 
I did get Emerald back though. /usr/bin/emerald exists so it works. Just had to set compiz up as I had reset it by logging into Unity.

On Mate /usr/bin/emerald doesn't exist any more and I tried to reinstall it but it could not find the package.

Oh well guess it's time for a clean install.... NOT! :p

Still using this install since Trusty.
```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 10 2014
```

(I borrowed that from VinDSL one time.)

---

### Post by mc4man on 2014-09-27
> **Cavsfan said:**
> Yes I did login as guest and could change the wallpaper to whatever I want. But when I login all I have is the orange default wallpaper and it won't change.

Possibly one of your settings is stuffing it up. It may be discoverable or maybe resetting dconf back to defaults would free up. (sledgehammer approach

---

### Post by Cavsfan on 2014-09-28
> **mc4man said:**
> Possibly one of your settings is stuffing it up. It may be discoverable or maybe resetting dconf back to defaults would free up. (sledgehammer approach)

If you mean **dconf reset -f /org/compiz/** I did that and rebooted into a Unity session. Setup CCSM and logged out and back in to Flashback with Compiz.

It fixed my time; it was set to manually update and was regularly 4 hours off with the automatic option greyed out. Now it's set to Auto and the time is right.

But still no bueno on the wallpaper. 

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-09-28095441.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-09-28095441.php)

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-09-28094437.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-09-28094437.php)

---

### Post by mc4man on 2014-09-28
> **Cavsfan said:**
> If you mean **dconf reset -f /org/compiz/** I did that and rebooted into a Unity session.
No, more  like reset all your gsettings back to defaults.
Not sure if there is a magic command, haven't run across one.

It used to be easy to see if it was helpful - just go into ~/.config/dconf, rename the user file to user.bak & log out/in. Now that will no longer work as that file is re-written from mem on log out/session end so you'll end up with same file.
What you need to do now is rename the file from another session (another  user account or install)  or rename it in your user session & immediately kill X

If all is well when re logging in the just set up your preferences as before or restore the old one & search thru dconf for the offending setting (though it's always possible it's nothing you'll find

To restore the old user file do basically the same deal ( remove the new user file, rename user.bak to user, if in your session immediately kill X ...

(here I keep a backup of my user file made after basic user & app  setup in a separate location as a couple of times it seems the user file has gotten corrupted or something that leads to weird behavior.

---

### Post by Cavsfan on 2014-09-28
> **mc4man said:**
> No, more  like reset all your gsettings back to defaults.
Not sure if there is a magic command, haven't run across one.

It used to be easy to see if it was helpful - just go into ~/.config/dconf, rename the user file to user.bak & log out/in. Now that will no longer work as that file is re-written from mem on log out/session end so you'll end up with same file.
What you need to do now is rename the file from another session (another  user account or install)  or rename it in your user session & immediately kill X

If all is well when re logging in the just set up your preferences as before or restore the old one & search thru dconf for the offending setting (though it's always possible it's nothing you'll find

To restore the old user file do basically the same deal ( remove the new user file, rename user.bak to user, if in your session immediately kill X ...

(here I keep a backup of my user file made after basic user & app  setup in a separate location as a couple of times it seems the user file has gotten corrupted or something that leads to weird behavior.

Thanks! That worked. I renamed the user file while booted into Utopic Mate (which I'm pretty fond of I might add). It's odd how you have to sort of create the flashback session from a Unity session.
If you just login to Unity and then go back to flashback, you have to literally change Unity into flashback via CCSM.
But after changing some things in CCSM, several logouts and a reboot while doing so and also a couple of things in dconf I got it back to where it was.

I believe you helped me recover something similar in the past that dealt with sessions and this time it's ~/.config/dconf/user. I'm glad you're paying attention because compared to you I feel as if I'm asleep at the wheel!

I don't think I'm even going to bother restoring the bak file; it'll probably mess it up again. It doesn't seem that difficult to just make the same adjustments made previously.

I think I'll backup the user file while it's good just in case.
Thanks again. :guitar:

        Cariboo907, are you good with this too?

---

### Post by mc4man on 2014-09-28
If you're good that certainly dump that .bak, it's worthless & possibly corrupted somewhere.
Once you're set up a backup of user is a good idea, remember that some apps also write pref's to it, I back it up after after everything I always have is in place & set up
(though resetting personal pref's isn't that big a deal.

---

### Post by Cavsfan on 2014-09-28
> **mc4man said:**
> If you're good that certainly dump that .bak, it's worthless & possibly corrupted somewhere.
Once you're set up a backup of user is a good idea, remember that some apps also write pref's to it, I back it up after after everything I always have is in place & set up
(though resetting personal pref's isn't that big a deal.

Yes, I already deleted the .bak file as you say it's probably got more harm in it than it does good lol.

And I made a copy named user.good.bak just in case but I agree resetting the dconf settings and setting them back up isn't that big of a deal.
It's what we all do on an initial install and how many times have we done that? I've done my share and I know you've done more than I have. :lol:

I'm going to mark this thread solved as I'm pretty sure it will solve Cariboo907's woes as well as any one else's that experienced this problem.

Thanks again!

---

