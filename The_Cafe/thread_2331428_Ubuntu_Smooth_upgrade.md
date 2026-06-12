---
title: "Ubuntu Smooth upgrade"
date: 2016-07-22
forum: The Cafe
---

### Post by shantiq on 2016-07-22
When i first used U back in 2009 with Karmic upgrade always went disastrously 
and things were not where they should be or simply not working.
But I always tried them mostly ending in having to do a clean install losing all settings
and sometimes all files...

This was then ...

After 13.10 i decided enough of the short term 6-months affairs; LTS is my bag from now on

So when 14.04 came along I ran software-properties-gtk unclicked all my other software (no need for that on 16.04 as it knows to disable other software
and even tells you to click them back on other side of install)
and ran ```
do-release-upgrade -d
``` expecting to have to go to clean soon after; but no it all went ace; 
maybe a couple of things had to be redressed but i cannot recall which...
So on 14.04 until april but then said wisely wait till 21-07 to upgrade
So on 21-07 i ran ```
do-release-upgrade -d
``` again and it gave me warnings about it can take hours etc
but took One and a half in total if that ...one needs to pay attention to terminal 
tho as there are a few options presented
which will need at least enter to be pressed; maybe 3 times in total

Then I reloaded still a tad apprehensive; and all was there in 16.04
Guake had disappeared [Python upgrade issue?]and had to be re-installed
and Audacious was acting up so deleted and re-installed

Skype fine !!! and Rosegarden ditto


So all this here to say congrats to the team ... this beast this Ubuntu is a slick animal
due to all the hard work and dedication ...   and i am VERY appreciative and grateful



shan

---

### Post by shantiq on 2016-07-27
------------

---

### Post by shantiq on 2016-08-08
Then I did the exact same upgrade on my 2005 Macbook dual-boot and no sound  !!!!!!
Read a few threads and found it was something simple but tricky if you do not know so here goes for anyone in same bateau

====================================
Sometimes the default setting on a new install or upgrade do not go to where you need

so install pavucontrol```
 sudo apt install pavucontrol

```
and to click on configuration

The default here was Analog Stereo Duplex 

For me it meant zero sound

Changed it to surround further down the list and voila
So to try that
Or whoever reads this thread with same very annoying drawback


see pics for help


[ATTACH=CONFIG]270650[/ATTACH][ATTACH=CONFIG]270651[/ATTACH]

---

### Post by WinEunuchs2Unix on 2016-08-10
I agree with the spirit of your message(s). Ubuntu 16.04 upgrade from 14.04 went smoothly for me. Started the upgrade and went shopping. When I came back it was on the last step of cleaning up. It said it may take several hours but only took 5 minutes.

A minor issue with PulseAudio version 8 switching sound from TV to laptop during suspend but a little bash script fixed that up. Some on going issues with faulty USB stuff strangely affecting fonts but hopefully a bug fix will come soon. In the mean time I just need to unplug powered USB hub before booting and plug it in after booting.

I like 16.04 but unlike you I'll upgrade to short term release 16.10 when it comes out in October in order to get PulseAudio version 9.

---

### Post by shantiq on 2016-08-11
thanx younux2younix :)    the sound issue is still over the forums a lot  ...   bit is a HUGE issue when it is your first time with U   ...    a bit like moving into a new home and found they forgot the doors or windows   ....    does not do good public relations for this ACE OS

if only it could be simplified    he sez     but i suppose the whole LINUX ethos is let us have ALL the sound options ;    and therein lies the chance of zero sound ...   which has had to be a deal-breaker for many new converts surely


anyway ....    failing that    smooooooooth

PS. 5mn! You must have serious hardware and internet connection
I was asked 3 times to pick an option on the terminal and if not answered it stays there
so no way could i have gone shopping unless it was a figure of speech &#55357;&#56871;

---

### Post by coldraven on 2016-09-05
I've hung back from upgrading, I usually do a fresh install. But this time I might go for it! Note to self: do backup first!!

---

