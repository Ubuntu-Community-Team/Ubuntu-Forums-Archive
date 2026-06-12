---
title: "Lockups with some gtk applications"
date: 2012-12-15
forum: Ubuntu Development Version
---

### Post by rolandixor on 2012-12-15
I'm experiencing random lockups with some GTK applications, and apparently with only those that use GTK+ 3.x, in 13.04.

I upgraded to it yesterday, so I don't know if it is a result of the upgrade not transferring some setting or something. The lockups seem to be related (partly) to opening menu items, such as indicators, as the menus then turn white and the system becomes unresponsive to clicks. I also get a problem with Firefox Nightly, Plank (the dock), Gedit, Dconf Editor, etc - where they just freeze after running for a few minutes.

---

### Post by dino99 on 2012-12-15
does not get all that stuff here on i386  ):P

maybe clean the system: remove these folders (they are cleanly rebuilt on next reboot)
.local
.gnome2
.gconf
.config

---

### Post by zika on 2012-12-15
> **dino99 said:**
> does not get all that stuff here on i386  ):P

maybe clean the system: remove these folders (they are cleanly rebuilt on next reboot)
.local
.gnome2
.gconf
.configI have valuable info in these folders... Settings for various apps that I do backup on a schedule... I would not be happy if someone would erase these folders on my machine, without backup...
They are rebuilt but settings are gone...

---

### Post by dino99 on 2012-12-15
> **zika said:**
> I have valuable info in these folders... Settings for various apps that I do backup on a schedule... I would not be happy if someone would erase these folders on my machine, without backup...
They are rebuilt but settings are gone...

thats true, but its not a big deal, and remove the oldish crap :p

---

### Post by zika on 2012-12-15
> **dino99 said:**
> thats true, but its not a big deal, and remove the oldish crap :pIt depends what is a computer used for...
Never mind...

---

### Post by rrnbtter on 2012-12-15
Greetings,
It probably depends on whether you are testing or just using the release but I have always favored a clean install for myself. I copy over Home and just the hidden software settings that I need for my email ,browser, backup program, financial etc. Leave the rest behind. That way I'm not blaming today on yesterday.  
rrnbtter
PS. I'm not a tester but I do send in the reports few as they are.

---

### Post by cariboo on 2012-12-15
Using a testing version as your main system exclusively, isn't recommended. There have been several times over the last few cycles, where the system has become totally unusable for days at a time. I always recommend that you have a previous version as a backup, just in case. You may never need it, but at least you do have a safety net.

---

### Post by rolandixor on 2012-12-15
I'm still experiencing the problem after clearing almost everything, so I'm going to start with a pretty much clean account (except for my important files).

Also, I'm on a new account with no problems, so it's clearly related to the old account.

---

### Post by rrnbtter on 2012-12-15
Original by cariboo907
> Using a testing version as your main system exclusively, isn't  recommended. There have been several times over the last few cycles,  where the system has become totally unusable for days at a time. I  always recommend that you have a previous version as a backup, just in  case. You may never need it, but at least you do have a safety net.

Thanks, you are right no question about it. Thing is I don't care one hoot if it crashes or not. Just look at the price of a movie, popcorn, and drink and I will take a reinstall anytime. But thanks for the thought.
rrnbtter
PS: I don't run an update on my wife's computer until I know mine will work:) .

---

### Post by rrnbtter on 2012-12-15
Greetings,
Oh, yes, I forgot. I also have a copy of Carolina Puppy Linux installed on my hard drive that I can boot into. It has all of the software that I use in Ubuntu installed and even uses the same Claws-Email folder as my Ubuntu System since its on the same partition in a directory. Only thing I don't have in the Puppy installation is GphpEdit. 
Life is good! Live it to the Ubuntu-ist!
rrnbtter

---

### Post by VinDSL on 2012-12-16
> **rrnbtter said:**
> PS: I don't run an update on my wife's computer until I know mine will work:) .
Bwahahahaha!

Happy wife -- Happy life!  :D

---

### Post by rrnbtter on 2012-12-16
Greetings,
Original by VinDSL
> Bwahahahaha!

Happy wife -- Happy life!  :grin:+1:razz:

rrnbtter

---

### Post by zika on 2012-12-16
> **cariboo907 said:**
> Using a testing version as your main system exclusively, isn't recommended. There have been several times over the last few cycles, where the system has become totally unusable for days at a time. I always recommend that you have a previous version as a backup, just in case. You may never need it, but at least you do have a safety net.Right. But (it might be just me, I admit) using testing version to do all the work as if it is only machine You've got is the only way to really test that version... Anything else (again, in my book) is missing a target...
I know this is off-topic and I stop here.
The only reason I've wrote my message above is because after months people do search and come across this kind of message, erase their folders and do complain... Over&out... ;)

---

### Post by cariboo on 2012-12-16
> **zika said:**
> Right. But (it might be just me, I admit) using testing version to do all the work as if it is only machine You've got is the only way to really test that version... Anything else (again, in my book) is missing a target...
I know this is off-topic and I stop here.
The only reason I've wrote my message above is because after months people do search and come across this kind of message, erase their folders and do complain... Over&out... ;)

I totally agree that we should be using Raring as much as possible for day-to-day usage, but having an install to fall back on can be a great help in chasing a problem on an unresponsive/broken system. I'm currently chasing a problem with network-manger and the broadcom wl drivers. Any network related functions and sudo don't work on the system at the present time, so being able to access it from a working install is a great help.

The one thing we don't suggest often enough, is to create a second user, on a system where the hidden configuration files may be a problem.

---

### Post by zika on 2012-12-16
> **cariboo907 said:**
> I totally agree that we should be using Raring as much as possible for day-to-day usage, **but having an install to fall back on can be a great help in chasing a problem on an unresponsive/broken system**. I'm currently chasing a problem with network-manger and the broadcom wl drivers. Any network related functions and sudo don't work on the system at the present time, so being able to access it from a working install is a great help.

The one thing we don't suggest often enough, is to create a second user, on a system where the hidden configuration files may be a problem.I've never disputed that...

---

### Post by rrnbtter on 2012-12-16
Greetings,
I'm going to throw in one more bit of opinion on this line of discussion and then I'm giving it up because it is way off topic. Plus this hasn't been mentioned and should for the new user. 
If you do decide to run a development (testing) version as your primary system, leave "proposed updates" turned OFF in your update settings and absolutely avoid "partial updates". This should get you by most of the "bad ones". Plus all of the suggestions in this thread are valid. I'm just an old hack that doesn't care.  And I'm moving on to something else.
It's been a fun thread.
rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by rolandixor on 2012-12-17
Well I managed to migrate to a new user profile, which works fine for me because a new profile just feels better anyway :)

BTW, since running Ubuntu from 7.10 till now, I've only once had a system get so bad that I had to reinstall, and that was because I didn't know how to fix a "broken" kernel :)

---

