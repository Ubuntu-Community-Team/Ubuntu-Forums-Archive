---
title: "Software Updater wants to do partial upgrade (14.04)"
date: 2014-02-17
forum: Ubuntu Development Version
---

### Post by craig10x on 2014-02-17
Here we go again...just got this when i ran software updater this morning...i know it's a bad idea to do the partial upgrades...and i did not proceed...
Question: It best to just wait until tomorrow morning when it automatically checks again and perhaps at that point it would have whatever needs to continue normally?
Or do something else?  What is the best way to proceed and avoid potentially borking my system?

Thanks :D[ATTACH=CONFIG]250425[/ATTACH]

---

### Post by sammiev on 2014-02-17
I would wait and check back later on the update.

---

### Post by QDR06VV9 on 2014-02-17
> **craig10x said:**
> Here we go again...just got this when i ran software updater this morning...i know it's a bad idea to do the partial upgrades...and i did not proceed...
Question: It best to just wait until tomorrow morning when it automatically checks again and perhaps at that point it would have whatever needs to continue normally?
Or do something else?  What is the best way to proceed and avoid potentially borking my system?

Thanks :D[ATTACH=CONFIG]250425[/ATTACH]
Are you just testing the update-mangler?
CLI just works.;)

---

### Post by zika on 2014-02-17
> **craig10x said:**
> Here we go again...just got this when i ran software updater this morning...i know it's a bad idea to do the partial upgrades...and i did not proceed...
Question: It best to just wait until tomorrow morning when it automatically checks again and perhaps at that point it would have whatever needs to continue normally?
Or do something else?  What is the best way to proceed and avoid potentially borking my system?

Thanks :D[ATTACH=CONFIG]250425[/ATTACH]As far as I do remeber If You choose Partial_Upgrade You will be asked one additional time for Yes/No... I just guess that this time there is unity-settings-daemon package that needs to be installed (for the first time) and that is the reason for &#8222;partial upgrade&#8220;... I might (and probably am) wrong... ;)

---

### Post by craig10x on 2014-02-17
@runrickus: nah...i use it all the time :D usually, it's very reliable i have been finding....but when this comes up (which isn't very often) i always start pondering what to do 8-[
in case it doesn't straighten out on it's own (i will wait patiently until it checks automatically when i boot up tomorrow morning) what were the terminal commands to run to do the updates and avoid this?

@zika: you know you may be right about that (i read about it)...question is: what is best to do....wait to see if the updater gets it straightened out or try an alternate method to update...
and if an alternate....what to do...

---

### Post by QDR06VV9 on 2014-02-17
> **craig10x said:**
> nah...i use it all the time...usually, it's very reliable i have been finding....but when this comes up (which isn't very often) i always start pondering what to do 8-[
in case it doesn't straighten out on it's own (i will wait patiently until it checks automatically when i boot up tomorrow morning) what were the terminal commands to run to do the updates and avoid this?
For Me it is 
"sudo apt-get update" 
"sudo apt-get upgrade"
For held packages "sudo apt-get dist-upgrade"

---

### Post by zika on 2014-02-17
> **craig10x said:**
> @zika: you know you may be right about that (i read about it)...question is: what is best to do....wait to see if the updater gets it straightened out or try an alternate method to update...
and if an alternate....what to do...There is no &#8222;best way&#8220;... I do use CLI-only... But, I just gave You answer on Your chosen way to do it... As I said, there is no thing such as best cake or best color... ;)
If there is a new package to be installed SU will not settle. He is just cautious enough to delegate decision in such cases to You... Not more and not less than that. As dist-upgrade also do... Not to mention that they are just front-ends to the same main engine...

---

### Post by craig10x on 2014-02-17
Got you...so it sounds like i'd probably need to use the terminal to get it straightened out....thanks for the commands, runrickus....i understand the first two commands...but what does the 3rd one do?  And do you run all three of them?  (I don't use the terminal much so i am kind of newbish with that stuff)...

[COLOR=#000000]"sudo apt-get update" [/COLOR]
[COLOR=#000000]"sudo apt-get upgrade"[/COLOR]
[COLOR=#000000]For held packages "sudo apt-get dist-upgrade"[/COLOR]

---

### Post by zika on 2014-02-17
> **craig10x said:**
> Got you...so it sounds like i'd probably need to use the terminal to get it straightened out....thanks for the commands, runrickus....i understand the first two commands...but what does the 3rd one do?  And do you run all three of them?  (I don't use the terminal much so i am kind of newbish with that stuff)...

[COLOR=#000000]"sudo apt-get update" [/COLOR]
[COLOR=#000000]"sudo apt-get upgrade"[/COLOR]
[COLOR=#000000]For held packages "sudo apt-get dist-upgrade"[/COLOR]Third one is a nickname for something SU calls &#8222;partial upgrade&#8220; ... ;)
```
dist-upgrade           
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```
Be always careful with partial/dist upgrade and read questions You're asked... Never answer &#8222;Y&#8220; if You're not sure what is going to happen... ;)
For example, there is a package (new one) that is needed to be installed in order so that some old package could be upgraded or there is a need to remove some old package so that newer version of it (with possibly different name) could be installed in order to get some package that is dependent on that package could be upgraded... I hope You get the picture... Follow packages and their change-logs and You'll see what I'm writing almost instantly...

---

### Post by sammiev on 2014-02-17
I updated 2 flavours of 14.04 since the OP 1st post and was never was asked to do a partial update. All is good here.

---

### Post by QDR06VV9 on 2014-02-17
> **zika said:**
> Third one is a nickname for something SU calls „partial upgrade“ ... ;)
```
dist-upgrade           
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```
Be always careful with partial/dist upgrade and read questions You're asked... Never answer „Y“ if You're not sure what is going to happen... ;)
For example, there is a package (new one) that is needed to be installed in order so that some old package could be upgraded or there is a need to remove some old package so that newer version of it (with possibly different name) could be installed in order to get some package that is dependent on that package could be upgraded... I hope You get the picture... Follow packages and their change-logs and You'll see what I'm writing almost instantly...
Thanks zika I could not have put it any better.;)

---

### Post by zika on 2014-02-17
> **runrickus said:**
> Thanks zika I could not have put it any better.;)I'm not sure if I could also... Lazy enough not to try... ;)

---

### Post by craig10x on 2014-02-17
I just ran the first two commands in the terminal and all updates were smoothly installed and no questions asked...however, after re-booting and running the software updster again, i still get the message about partial upgrade....so i was wondering if:
1) I should use the terminal and just run the third command and if it asks any questions about removing anything i should say no?
or  2) run software updater and hit proceed button or hit the partial upgrade button?

---

### Post by craig10x on 2014-02-17
Update:  I took a chance and did the partial upgrade on the software updater and it went smoothly...it did not ask any questions until the very end...it mentioned it was going to remove 10 obsolete packages and i let it do it...hope that was not a mistake?...i watched the packages being installed and indeed it did relate to the big changes in unity that came down today...

Then i ran software updater again and it's back to normal (shows i am up to date)...

---

### Post by jerrylamos on 2014-02-17
I didn't get a partial update today on apt-get update, apt-get dist-upgrade but the screen display resolution is all screwed up and the settings display fails.  
Bug #1281274 has screen capture.
GDBus.Error: org.gnome.SettingsDaemon was not provided by any .service files.
?

---

### Post by Mateusz Stachowski on 2014-02-17
> **jerrylamos said:**
> I didn't get a partial update today on apt-get update, apt-get dist-upgrade but the screen display resolution is all screwed up and the settings display fails.  
Bug #1281274 has screen capture.
GDBus.Error: org.gnome.SettingsDaemon was not provided by any .service files.
?

There should be another update to Unity which will most likely resolve your problem. Alternatively you can install unity-settings-daemon.

[https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140217-0ubuntu1](https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140217-0ubuntu1)

---

### Post by craig10x on 2014-02-18
Everything working great since i did the partial upgrade...no problems and software updater running as smooth as ever :D
One thing i was curious about...i ran the updater a little while ago and a whole slew of Unity 8 stuff was installed...is Unity 8 actually running by default now?

---

### Post by grahammechanical on 2014-02-18
> [COLOR=#000000].is Unity 8 actually running by default now?[/COLOR]

No. And it will not be running by default in 14.04 but we will get an option to login to a Unity 8 preview session. I created a post earlier with links to a video about what is going to come in 14.04, including a Unity 8 preview option. I am guessing that is what those Unity 8 packages are doing there.

Regards.

---

### Post by deadflowr on 2014-02-18
> **craig10x said:**
> Everything working great since i did the partial upgrade...no problems and software updater running as smooth as ever :D
One thing i was curious about...i ran the updater a little while ago and a whole slew of Unity 8 stuff was installed...is Unity 8 actually running by default now?

Here's a couple of videos for you on that
(well one video on that:P)

[http://discourse.ubuntu.com/t/unity-updates-for-14-04/1494](http://discourse.ubuntu.com/t/unity-updates-for-14-04/1494)

---

### Post by Redalien0304 on 2014-02-18
I had the same Problem with Partial Upgrades but **OrangeCrate** came up withe this in another post. Has worked for me so Far 2 times if i Remember right.

Do this, in this exact order:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

sudo apt-get update

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

That should do it.

(And yes, you can combine some of those command together with &&, but, let's keep it simple.)

[http://ubuntuforums.org/showthread.php?t=2202148&p=12912262#post12912262](http://ubuntuforums.org/showthread.php?t=2202148&p=12912262#post12912262)

---

### Post by mc4man on 2014-02-18
> **craig10x said:**
> Everything working great since i did the partial upgrade...no problems and software updater running as smooth as ever :D
One thing i was curious about...i ran the updater a little while ago and a whole slew of Unity 8 stuff was installed...is Unity 8 actually running by default now?

I believe all those packages were pulled in by a possibly poorly crafted control file or just a point in time. 
[http://ubuntuforums.org/showthread.php?t=2206158](http://ubuntuforums.org/showthread.php?t=2206158)
In any event unity8 is not on the current iso

---

### Post by craig10x on 2014-02-18
Thanks guys...i thought that might be the case ;)

---

