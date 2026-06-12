---
title: "Is Beta 2 being delayed?"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-25
I saw some chatter on a couple of mailing lists but I'm not really "with the program" ATM ;)

But even at the QA tracker I see little to no activity:

[http://iso.qa.ubuntu.com/qatracker/milestones/238/builds](http://iso.qa.ubuntu.com/qatracker/milestones/238/builds)

Sorry to just ask stupid questions :redface:

---

### Post by mc4man on 2012-09-25
Don't know - looks like testing is going on - just gave the live session a fail here
(& could also fail all three install tests - if one can't complete step one then the rest is moot.

---

### Post by wojox on 2012-09-25
I've been running the amd64 build for a few hours now. Have I always been able to move the Workspace Switcher anywhere in the Launcher?

---

### Post by mc4man on 2012-09-25
> **wojox said:**
>  Have I always been able to move the Workspace Switcher anywhere in the Launcher?
No, new to unity 6.6, now  all launcher icons except the Dash & trash can be moved

---

### Post by kansasnoob on 2012-09-26
Just checked again and most images are rebuilding :)

---

### Post by kansasnoob on 2012-09-26
BTW this is the message I received on Monday:

> Hi testers,

just for a change, the QA releases for a milestone release are delayed. There is very good reason for this. The -release team have stamped their feet and said that we, as QA, will get a release candidates for Beta 2 that will not need a respin even before they arrive. Yes, they would have preferred to have our QA candidate out on time; but I am 100% behind them on this decision. I ask that you keep an eye on the Beta 2 [1] area for when the little critters arrive. The last update I had was that we were awaiting a new kernel build (along with several 'opportunity' fix bugs). I ask that you be patient and keep an eye on the iso tracker page[1]. Obviously, once they arrive please jump all over them and get them tested!

Thank you for your patience and continued testing,

Phill. 

I know I've received no testing notifications, but on the up-side the subscriptions page at the QA tracker is working:

[ATTACH]224659[/ATTACH]

So I know I'm subscribed, and I'm tempted to at least test the Lubuntu alternate image, and both Lubuntu and Ubuntu upgrades ............ but I hate to waste my time :)

---

### Post by balloons on 2012-09-26
> **kansasnoob said:**
> BTW this is the message I received on Monday:

 

I know I've received no testing notifications, but on the up-side the subscriptions page at the QA tracker is working:

[ATTACH]224659[/ATTACH]

So I know I'm subscribed, and I'm tempted to at least test the Lubuntu alternate image, and both Lubuntu and Ubuntu upgrades ............ but I hate to waste my time :)

We also just noticed that although subscriptions now work, since we replaced all the testcases, your not getting the notice :-) (since you have notices against the old testcases). Work is going to be done to migrate you so you get notices again, and also to allow you to signup by product instead of testcase (which could change). In the interim, if you wish to get a notice, unsubscribe from everything and re-subscribe. I believe that should give you the notices again.

---

### Post by jerrylamos on 2012-09-26
Daily build still getting updates daily. Usually the changes settle down before a Alpha/Beta.  Haven't settled down yet.  When I get tired waiting I'll try an install.

---

### Post by kansasnoob on 2012-09-26
> **guitara said:**
> We also just noticed that although subscriptions now work, since we replaced all the testcases, your not getting the notice :-) (since you have notices against the old testcases). Work is going to be done to migrate you so you get notices again, and also to allow you to signup by product instead of testcase (which could change). In the interim, if you wish to get a notice, unsubscribe from everything and re-subscribe. I believe that should give you the notices again.

It's all good, but after reading Phill's message I just decided to keep waiting ............. but then I saw no message about Beta 2 itself being delayed.

And I noticed that a lot of test-cases were being neglected so I wondered what was up ;)

---

### Post by kansasnoob on 2012-09-26
> **jerrylamos said:**
> Daily build still getting updates daily. Usually the changes settle down before a Alpha/Beta.  Haven't settled down yet.  When I get tired waiting I'll try an install.

This is not about what images are available. It's a matter of iso/upgrade testers NOT receiving notifications of new changes that need to be tested.

---

### Post by jerrylamos on 2012-09-27
Things that need to be tested?   Will the live image boot?  Will the display be readable?  Will it install to the selected partition?  When I boot, can I read the screen?  Can I set 1366x768 on this TV monitor using mysterious (to me) xrandr parameters?  Will the hidden wireless WPA actually connect?  Will the amd64 external monitor & laptop monitor work right?

Basic stuff we have trouble with during the development cycle.  There are still some posts about difficulties with all the different hardware out there.  Hopefully most of this will work on Beta 2.  I do expect trouble with the "hidden" wireless WPA.  Of late, logging into different desktops has been problematical hopefully that's fixed.

Now some of the experts can test the nuances of Unity/compiz/lenses/shopping way beyond my level.  I just try to be "ordinary user" and see if Office will work, or is it busted, do the internet browsers work or crash, etc.  

(Just got some wierd behavior a previous message on a different tab got pasted into this note and had to be deleted.  No I can't reproduce it for a launchpad bug but it's been happening at odd times the last couple days.)

Some others are looking at increases in internet traffic and battery drain.  I haven't figured out how to test those yet.  I sometimes look at gtkperf slowing down but that has not been of interest to the developers.

I use a netbook with TV monitor, a widescreen amd64 notebook to external 1280x1024 monitor, and a 3.3 gHz tower 1440x900 monitor.  Bugs that show on one might not on another. Oh, yes, a Thinkpad with Maverick & Precise I use portably.  QQ doesn't support it.

---

### Post by jerrylamos on 2012-09-27
zsync the same today as yesterday so installed amd64 and updated.  Its got launchers for Ubuntu One Music and Amazon.  I check hidden and top left corner on Appearance Behavior also set icon size to 32 so no big deal out of sight most of the time.

Got a crash then apport crashed reporting the crash. #1057676

Got another crash. #945124 been around a while. 
 
update-apt-xapian-index crashed with IOError in __init__(): [Errno 2] No such file or directory: '/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'

Maybe that makes sense to someone other than me.

Anyway up and running Firefox & Opera.  Opera in case mail.AOL.com Reply bug returns.

---

### Post by ventrical on 2012-09-27
Installing ... so far so good.. no problems yet.

Anybody else get the big red "slursh' for a background?

---

### Post by bird1500 on 2012-09-27
> **ventrical said:**
> Installing ... so far so good.. no problems yet.

Anybody else get the big red "slursh' for a background?

The background bike-shedding is always interesting. Apple (finally) learned that it's not worth putting a background related to the release or theme color - people just don't use that, instead just put something clear and beautiful. Canonical didn't learn that yet, they're still trying to put blurry images of pink/brow/red slush to match the theme color . Not a big deal tho.

---

### Post by mcellius on 2012-09-27
The background I get during install is the new Quantal smear that someone - I really wish I could remember who - said looked like a nostril.  (I thought he was just making up something, but now I see it: it DOES look like a nostril!)  Orangeish/purplish blobby/swirly thing.

---

### Post by ventrical on 2012-09-27
> **mcellius said:**
> The background I get during install is the new Quantal smear that someone - I really wish I could remember who - said looked like a nostril.  (I thought he was just making up something, but now I see it: it DOES look like a nostril!)  Orangeish/purplish blobby/swirly thing.


Yeah .. it does. I thought it was a blood smear on a slide.

---

### Post by funicorn on 2012-09-27
No. I think it's a strategy by Canonical, and a psychological one. One feels good when it's beautiful, and feels better when it's more beautiful because of him. So changing a different wallpaper replacing the ugly default makes people love Ubuntu more.

> **bird1500 said:**
> The background bike-shedding is always interesting. Apple (finally) learned that it's not worth putting a background related to the release or theme color - people just don't use that, instead just put something clear and beautiful. Canonical didn't learn that yet, they're still trying to put blurry images of pink/brow/red slush to match the theme color . Not a big deal tho.

---

