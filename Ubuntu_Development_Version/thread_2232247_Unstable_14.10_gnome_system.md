---
title: "Unstable 14.10 gnome system"
date: 2014-06-30
forum: Ubuntu Development Version
---

### Post by crcarson on 2014-06-30
Tried several daily builds (4 to be exact over the last week and a half) but unable to build a stable 14.10 gnome system.  May run for 10 minutes or 2 days but will crash and then I unable to boot.  Trying to boot I get a blank screen except for the Ubuntu banner (date, sound, and logoff).  Don't know how to document this failure, any advice?

---

### Post by zika on 2014-06-30
What do You see in logs for X and the rest?
Did You try renaming ~/..Xauthority?
Many possibilities, take one at a time...

---

### Post by crcarson on 2014-06-30
Thanks, should have looked at the logs before appending.  Found in the auth.log a failure of systemd failed to create a session.  Don't understand the difference between upstart and systemd but did add to the linux command in grub the init=/lib/systemd/systemd and was able to get the system to boot.  Looks like it went through a completely different boot process (at least it looked different).

---

### Post by sammiev on 2014-07-01
I'm seeing the same thing time to time. It seems ever 3 or 4 boot I have the same screen. I just use "Ctrl + Alt + F1" log in and enter "startx"
If I reboot I have no need for the above but just too lazy to wait for another reboot. 
I have no issues with locking up after I boot and yes I'm using gnome 14.10

---

### Post by Cavsfan on 2014-07-01
> **crcarson said:**
> Thanks, should have looked at the logs before appending.  Found in the auth.log a failure of systemd failed to create a session.  Don't understand the difference between upstart and systemd but did add to the linux command in grub the init=/lib/systemd/systemd and was able to get the system to boot.  Looks like it went through a completely different boot process (at least it looked different).

If you are interested in being able to boot with systemd or upstart where you can choose which one, the instructions for doing so are [_here_]("http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146").
Systemd seems more stable to most that have tried it.

---

### Post by zika on 2014-07-01
> **Cavsfan said:**
> If you are interested in being able to boot with systemd or upstart where you can choose which one, the instructions for doing so are [_here_]("http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146").
Systemd seems more stable to most that have tried it.Am I wrong when I conclude that the way of choosing You offer does not allow user to choose from different kernels that are installed...?
Or, on a second look, do user have to make additional entry for any additional kernel? It seems to me that You use symlinks that are not there by default...
I'll take another look...

---

### Post by Cavsfan on 2014-07-01
> **Cavsfan said:**
> If you are interested in being able to boot with systemd or upstart where you can choose which one, the instructions for doing so are [_here_]("http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146").
Systemd seems more stable to most that have tried it.

> **zika said:**
> Am I wrong when I conclude that the way of choosing You offer does not allow user to choose from different kernels that are installed...?
Or, on a second look, do user have to make additional entry for any additional kernel? It seems to me that You use symlinks that are not there by default...
I'll take another look...

You are right my option only allows to boot into the most recently installed kernel. But it just adds a single line at the top to do so.
It still leaves the normal grub entries below that one option. I have yet to see a need to boot into an older kernel but as I said all of the normal entries are below the first option.
So, you could select an older kernel at boot and edit that line to add **quiet splash init=/lib/systemd/systemd** if you wanted to.

This is what my grub screen looks like: 
[[img]http://www.zimagez.com/miniature/20140629115939.jpg[/img]](http://www.zimagez.com/zimage/20140629115939.php)

In order for me to boot into an older kernel I would have to make some other grub files executable.
But, I haven't had to do that so it hasn't been an issue.

---

### Post by Cavsfan on 2014-07-01
If you remember Ranch hand, he taught me all of this grub stuff and Drs305 helped a lot too.

It does use symlinks: 

[ATTACH=CONFIG]254382[/ATTACH]

---

### Post by zika on 2014-07-02
> **Cavsfan said:**
> You are right my option only allows to boot into the most recently installed kernel. But it just adds a single line at the top to do so.
It still leaves the normal grub entries below that one option. I have yet to see a need to boot into an older kernel but as I said all of the normal entries are below the first option.
So, you could select an older kernel at boot and edit that line to add **quiet splash init=/lib/systemd/systemd** if you wanted to.

This is what my grub screen looks like: 
[[IMG]http://www.zimagez.com/miniature/20140629115939.jpg[/IMG]]("http://www.zimagez.com/zimage/20140629115939.php")

In order for me to boot into an older kernel I would have to make some other grub files executable.
But, I haven't had to do that so it hasn't been an issue.

> **Cavsfan said:**
> If you remember Ranch hand, he taught me all of this grub stuff and Drs305 helped a lot too.

It does use symlinks: 

[ATTACH=CONFIG]254382[/ATTACH]My point(s) exactly.
Using Systemd from the very first moment.
There are very ellegant ways of achieving all that I've mentioned in Grub... It evolved a bit...

---

### Post by Cavsfan on 2014-07-02
> **zika said:**
> My point(s) exactly.
Using Systemd from the very first moment.
There are very elegant ways of achieving all that I've mentioned in Grub... It evolved a bit...

Yes grub is getting better all the time. Mint 17 uses another file that when setup properly allows custom colors in the fonts for the box and menu, while the regular one has colors for the top and bottom as in my picture.
I looked for systemd on Trusty but it was not there. Is there a ppa or something?

---

### Post by zika on 2014-07-03
> **Cavsfan said:**
> I looked for systemd on Trusty but it was not there. Is there a ppa or something?pitti/systemd

---

### Post by d-cosner on 2014-07-03
I did a dist upgrade from 14.04 to 14.10 a few days ago, so I have not tried a daily build. Currently Ubuntu Gnome is a mix of gnome 3.6, 3.8, 3.10 and 3.12, so to say the least the experience is lacking... It kind of has me worried because other than a couple of gnome 3.12 packages there has been very little activity with the Ubuntu Gnome Team.

---

### Post by Cavsfan on 2014-07-03
> **zika said:**
> pitti/systemd

I didn't know what you meant at first but figured it out. I tried it and failed miserably. I cannot tell you all I had to do to recover on this thread as that would be off topic.
But, I think I'll leave 14.04 alone and just run systemd on Utopic. :lol: LoL

---

### Post by zika on 2014-07-03
> **Cavsfan said:**
> I didn't know what you meant at first but figured it out. I tried it and failed miserably. I cannot tell you all I had to do to recover on this thread as that would be off topic.
But, I think I'll leave 14.04 alone and just run systemd on Utopic. :lol: LoLSorry to hear that... I have 2-3 minor complaints (not problems)and it is on 24/7 from the very day it was announced here... There must be some reason for that, maybe simple fact that this machine has much of other new stuff also installed... Sometimes that is a curse and sometimes that is a blessing... You never know...
At first I've put ppa: in front of pitty/systemd as it should be put but did not have time to fight with smileys that automagically replace some combination of characters... ;)
Update&#8321;: To dismiss possibility that You're using 3.13 and I'm on 3.1{5,6} I've just tried and I'm now writing from official 3.13-31... There are some glitches (text is not working in boot-line, .override is not workig in /etc/init, troubles with resolvconf,... etc.) but all in all it works nicely even in 3.13...

---

### Post by grahammechanical on 2014-07-03
> [COLOR=#000000]there has been very little activity with the Ubuntu Gnome Team.[/COLOR]

It is a very small team. They would want even the development version to be stable. Which is why newer stuff is put in to PPAs. It is way to test for bugs. They also have to maintain Ubuntu Gnome 14.04 and as Ubuntu is coming up for a point release with a newer hardware stack in July I would not be surprised that they are limited in what they can do in keeping up with the Gnome org developers. May be there is not so much coming from upstream Gnome any way.

Regards.

---

### Post by sammiev on 2014-07-03
> **grahammechanical said:**
> It is a very small team. They would want even the development version to be stable. Which is why newer stuff is put in to PPAs. It is way to test for bugs. They also have to maintain Ubuntu Gnome 14.04 and as Ubuntu is coming up for a point release with a newer hardware stack in July I would not be surprised that they are limited in what they can do in keeping up with the Gnome org developers. May be there is not so much coming from upstream Gnome any way.

Regards.

+1 one the above post. They also seem to do large updates shortly before the release of the main version.

---

### Post by crcarson on 2014-07-04
The startx does get the system up but not all functions are available.  In my case missing the audio device (no sound available).

---

### Post by zika on 2014-07-04
> **crcarson said:**
> The startx does get the system up but not all functions are available.  In my case missing the audio device (no sound available).```
sudo adduser &#8222;crcarson's_user_name_on_that_PC&#8220; audio
```should fix that...

---

### Post by Cavsfan on 2014-07-04
> **zika said:**
> Sorry to hear that... I have 2-3 minor complaints (not problems)and it is on 24/7 from the very day it was announced here... There must be some reason for that, maybe simple fact that this machine has much of other new stuff also installed... Sometimes that is a curse and sometimes that is a blessing... You never know...
At first I've put ppa: in front of pitty/systemd as it should be put but did not have time to fight with smileys that automagically replace some combination of characters... ;)
Update&#8321;: To dismiss possibility that You're using 3.13 and I'm on 3.1{5,6} I've just tried and I'm now writing from official 3.13-31... There are some glitches (text is not working in boot-line, .override is not workig in /etc/init, troubles with resolvconf,... etc.) but all in all it works nicely even in 3.13...

No problem! I don't blame you. It was my ambitious attempt that doomed me. 
It may have been that I had some updates to get before I tried adding the ppa but upon reboot I lost network manager, gnome-session-flashback and an unbelievable amount of other stuff. I did manage to get it all back by safemode, enabling network, dropping to a root shell, purging that ppa, reinstalling network manager and gnome-session-flashback. Then there were a few other things I had to re-install but it's back in good shape now. :)

> **grahammechanical said:**
> It is a very small team. They would want even the development version to be stable. Which is why newer stuff is put in to PPAs. It is way to test for bugs. They also have to maintain Ubuntu Gnome 14.04 and as Ubuntu is coming up for a point release with a newer hardware stack in July I would not be surprised that they are limited in what they can do in keeping up with the Gnome org developers. May be there is not so much coming from upstream Gnome any way.

Regards.

That does make sense. And that is fine with me that they only put out updates periodically. I'm looking forward to the 14.04.1 release. Thanks for the info. because I definitely am a gnome tester! :)

---

