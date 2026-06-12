---
title: "Attempting to upgrade 8.04 server to supported release."
date: 2016-03-01
forum: Server Platforms
---

### Post by elfmtg on 2016-03-01
ok, so im trying to learn more about linux servers.   i currently am participating in an event where my team is supposed to update and secure a virtual network.  i currently have an ubuntu 8.04 dns server and we are trying to get upgraded to something that is not EOL.  our problem is that it is a virtual network and we are not allowed to just wipe and reinstall.  problem is that ive changed the update servers its pointing to since it wasnt pointing to the right ones, and now still when i try to upgrade (sudo apt-get update/upgrade and sudo do-release-update) it fails with a syntax error on the do release update.  in my searches i have found that it is mostly pointing to to 12.04 instead of 10.04.  however this  [http://ubuntuforums.org/showthread.php?t=2311898](http://ubuntuforums.org/showthread.php?t=2311898)  while it is a little more detailed than most i have found to this problem is the general, people leave it at wipe it and reinstall.  i know our team in last years event was able to basically step through upgrades all the way to 13.10 (now EOL) but those students have left and did not leave any documentation. so, any direction would be amazing

---

### Post by Bucky Ball on 2016-03-01
Welcome. That is akin to dreaming the impossible dream whilst awake. You understand how many EOL releases and changes you would need to get through to reach a supported release from 8.04 LTS? 8.04 LTS was the first LTS release I used ... and that was eight years ago! 

If you can't get in contact with these masters of the the black arts that made it from 8.04 to 13.10 (and that might be hard as they may have gone back to their magic place), I would go along with what you already have read: wipe and reinstall. But not an option for you. Can you start again, in that case, and simply make a new install quite apart from this one?

What team, what event? Two words of advice: we don't do homework (are you being set this ludicrous task as a school assignment?) and we don't officially support EOL releases. Besides those two points, you might get lucky.

Good luck.

(PS: I have changed your thread title for clarity and to avoid confusion as there is no confusion about what you're attempting to do.)

---

### Post by elfmtg on 2016-03-01
no, not homework lol.   its a cyber def competition.   we have 1 week with the environment to prepare and figure out all the problems.  i am by no means a linux master. i have just been working tutorials and forums to try to figure out what my problems are so i can fix them. otherwise  i am complete newb with it.  my first approach has just been to get updates and upgrades.  since we are given a broken virtual network to harden and get functional and cant wipe and restart what we are given, do you think that its going to cause a problem if we just leave it as is, do what updates are avail and leave it at that?  its just our 2ndary dns.

---

### Post by Bucky Ball on 2016-03-01
No idea. All I do know is that if a regular user were to post on here wanting to know how to upgrade from 8.04 we would advise them to forget it and reinstall. 8.04 is ancient and should only be used offline in settings such as yours. Are they expecting you to update and upgrade? Well, 8.04 is end of life and not updateable or upgradeable in any regular sense of those words, so that answers that question.

If your first approach is to get updates and upgrades, forget it. There hasn't been any available for 8.04 in years. Also answers the question of doing what updates are available. There are none. Easy fixed.

---

### Post by elfmtg on 2016-03-01
curses.  well, thank you a lot for the help.  guess my hours of digging bore no fruit.   thanks for saving me more time though.   also, would i be correct in assuming that debian and centos upgrades would be somewhat of a similar sittuation?

---

### Post by Bucky Ball on 2016-03-01
Ubuntu is based on Debian, but honestly wouldn't know. Know nothing about Centos. Sure some quick finger work will find you the answers you need.

---

### Post by mastablasta on 2016-03-02
centos has a lot longer support period.

---

### Post by darkod on 2016-03-02
That 8.04 is EOL is not such a big deal, as the fact that the next LTS, the 10.04, is also EOL now... There would be no issues to upgrade an EOL release, but I'm not sure if it can work when the next LTS is also EOL.

Maybe if you double check that you set the 8.04 archive repositories correctly and if you post the exact error message it gives you, someone can think of something. Could it be that you really have a syntax error in the sources?

PS. Of course, I would also recommend a new clean install but I'm going by what you said that a clean install is not an option... They could have at least given you 10.04 to try an upgrade, that is also EOL but it can be upgraded to 12.04. Maybe they didn't think that the difference from last year (or couple of years back) is that 10.04 is also EOL now and that shortens your options.

---

### Post by Bucky Ball on 2016-03-02
... or the fact that 8.04 is a world away as far as changes go to 12.04 in particular, and 10.04 too. There were plenty of breakages and mayhem at the time when everything was supported when the changeover to Unity happened. That caused a lot of people back then to require a clean install anyway because of breakages caused by the net upgrade.

---

### Post by coldraven on 2016-03-02
If they're using VirtualBox maybe you could grab one of these images and sneakily copy it onto the network :) 
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by Bucky Ball on 2016-03-02
Perhaps you could go on a technicality. An EOL release, particularly one that old, is not technically upgradeable or that easily upgraded to a supported one, but Ubuntu itself is upgradeable. If you are running an EOL release of Ubuntu you can upgrade it quite easily. By clean installing a supported one. :-k :)

---

### Post by darkod on 2016-03-02
..or at least ask them to give you 10.04 EOL to do the exercise/task. You can upgrade that easily and if the task is to see you know the process, that should count.

I mean, 8.04.... Why don't we start working with Windows 3.11 again... :)

---

