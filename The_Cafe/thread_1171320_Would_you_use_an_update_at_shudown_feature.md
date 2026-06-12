---
title: "Would you use an update at shudown feature?"
date: 2009-05-27
forum: The Cafe
---

### Post by davideotape on 2009-05-27
Regarding [this blueprint]("https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-karmic-update-on-shutdown"), I'm just wanting to get a feel of how many users would find the option to install updates at showdown useful. Leave your comments below!

---

### Post by konqueror7 on 2009-05-27
well, it would be a good addition to the current *software sources* tool, acting similar to windows' automatic update...but then again, wouldn't it be better that instead of putting it during shutdown, is to rather be able to put it in the background like most anti-virus programs do?

---

### Post by TheLions on 2009-05-27
what if update needs you input?
Then what? Postpone update or postpone shutdown?
Also what if there is a lot updates on your laptop and you forgot about them and put you laptop in the bag?

---

### Post by Skripka on 2009-05-27
There are also many folks who seldom turn their machines off.

Upsdate on shutdown is one of my big gripes about Windows XP.  Shutdown there already takes 2 minutes-why prolong the agony by having updates install then?

---

### Post by x33a on 2009-05-27
i always shutdown my machine in a hurry, and i wouldn't like to wait until the updates install.

---

### Post by Kareeser on 2009-05-27
The update tool isn't very obtrusive to me. It pops under, so I can get around to it on my own time.

If I'm distracted, then it will bother me again to update if it's important.

When I do get around to it, I click one button, type in my password, and go back to doing whatever I was doing. It's not very obtrusive... though I do prefer the old style notification.

---

### Post by aysiu on 2009-05-27
While I can see how this would be an interesting option to explore for some people in certain situations, I don't think it should be high on the developers' priority list.

One of the things I love about Linux is that I don't need to shut down or reboot to install updates (except kernel updates).

---

### Post by hatten on 2009-05-27
i would not use update during shutdown, and hate it being updated in the background. It is MY computer so I tell what should be updated and when.

---

### Post by jelle_ on 2009-05-27
that's not a feature, it's an useless annoyance.

---

### Post by davideotape on 2009-05-27
I'm getting the feeling that not many people like or would use this feature then.

---

### Post by init1 on 2009-05-27
No, when I click "shutdown", I want my computer to shutdown.

---

### Post by mamamia88 on 2009-05-27
it could be useful but you can accomplish the same thing by starting update manager before you want to shutdown and then set gsshutdown to a time that the updates will be done

---

### Post by Xbehave on 2009-05-27
You can update programs while running them, (used files stay on the disk until nothing is using them) so only certain types of update to certain packages mean you need to restart a program (it is very rare). The only reason windows updates on shutdown is because it cannot update a running program.

I think (shutdown only if update works)
```
sudo "apt-get update && apt-get dist-upgrade && shutdown -hP now "
```
shutdown anyway and hope that whatever failed doesn't prevent booting up
```
sudo "apt-get update ; apt-get dist-upgrade ; shutdown -hP now "
```

---

### Post by clonne4crw on 2009-05-27
I have 2 points of view to see this from:

1) The power user (most of us here): It is our computer, and as someone else said, when we click 'Shutdown', or type # shutdown now, we want it to end the session, send the KILL and TERM signals, and then power off the components using ACPI. We don't want it to do anything else. That's one of the ideals that UNIX was founded upon. Keep it simple, and let it do its task, and do it well.

2) The home user who simply wants it to work: A computer is a tool to browse the Web and check email. Things should happen automatically, and just work. Implmenting a feature like Automatic Updates would drastically improve security for a machine that might very well be vunerable without it, due to the lack of knowlege by the user.

Take what you want out of that. I guess I forgot the Coroprate/enterprise enviroment, but I think it falls under the first one.

---

### Post by Screwdriver0815 on 2009-05-27
the update mechanism like it was in Hardy and in Intrepid was perfect. The updater came up into the panel and remained there, showing that an update is ready to be installed and the user could decide, when he installs it.

The new update mechanism in Jaunty, where the update-window pops up automaticly and when you close it, you will not get the update, is just stupid and annoying.

Another new mechanism is just more annoying. When I want to have a shutdown, it should shutdown. Doing things which the user doesn't want and where he did not give the command for, is windows-style.

---

### Post by clonne4crw on 2009-05-27
> **Screwdriver0815 said:**
> the update mechanism like it was in Hardy and in Intrepid was perfect. The updater came up into the panel and remained there, showing that an update is ready to be installed and the user could decide, when he installs it.

The new update mechanism in Jaunty, where the update-window pops up automatically and when you close it, you will not get the update, is just stupid and annoying.


Agreed. There are several things about Jaunty that I don't care for, and that's one of them. 

The new behavior is very similar to the one in Fedora Linux, where a little notification window pops up and asks if you want to install updates. Of course, if you ignore it, it will disappear and leave you alone.

---

### Post by lisati on 2009-05-27
It's about freedom of choice - if such a feature was introduced, who is to say that using it is compulsory?

---

### Post by Screwdriver0815 on 2009-05-27
> **lisati said:**
> It's about freedom of choice - if such a feature was introduced, who is to say that using it is compulsory?
nobody. 

But if you introduce something which does nothing better than the thing before... just for the sake of doing something new... whats that? Compulsory? 

And switching back to the old behaviour is annoying too, because you have to search how to do it... and so on. 

IMO The most positive thing about the new updater in Jaunty is, that it is possible to switch back to the old one :D

---

### Post by Bungo Pony on 2009-05-27
I'd use a "check drives at shutdown" feature. It's irritating when you boot your PC and a drive check is forced during boot. When I boot, I want it to boot today unless a drive check is absolutely due to an improper shutdown.

---

### Post by lisati on 2009-05-28
I just noticed a thread where someone might find the "update and shutdown" idea useful: [http://ubuntuforums.org/showthread.php?t=1172717](http://ubuntuforums.org/showthread.php?t=1172717)

---

### Post by doas777 on 2009-05-28
I have no problem with the option per se, but windows gets a little pushy about it sometime. i feel like it wants to force me into an uninformed decision, prolly just to trick people into installing WGA by accident.

if nothing else, I like looking through the packages updated, as it gives me some clues to what my system is made of, in manageable bites. just seeing the names is helpful.

---

### Post by Mr. Picklesworth on 2009-05-28
I consider it a point of pride that Ubuntu actually shuts down when I tell it to while Windows these days has a way of deciding to hang for literally ten minutes, during which time I must watch it closely to be sure it doesn't melt my computer. (Somehow, it's worse than the "installing updates" at startup because it never tell me what the heck it's doing, either).

So no, I would make a strong point of not EVER using it but I would appreciate the option if it existed.

---

### Post by Script Warlock on 2009-05-28
now you know...hehehhe

---

### Post by Viranh on 2009-05-29
I'll add my voice to the countless others who have already said they wouldn't use this feature. I rarely shut down, and when I do I want the computer to do it NOW, not in ten minutes after updates install, etc.

---

### Post by oldsoundguy on 2009-05-29
Windows, as we know, does just that!  And it is a royal PITA when there is a lineup of updates that have not been installed.

I fixed a machine today and it updated auto.  I needed to shut it down and do some interior work and the damn thing took almost 1/2 hour to quit.

That is bogus CRAP!!

I hope that Linux NEVER resorts to that foolishness!

---

### Post by Bodsda on 2009-05-29
Personally, I dont care for the feature, but I have no problems with it as long as it is not enabled by default. 

If I want to do updates, I'l do them manually, one of the reasons I use fluxbox instead of gnome is because I dont get all the annoying panel applets screaming/prompting me all the time. So if I wanted to add updates before shutdown i'd just alias my shutdown command to include an update && upgrade

Regards,

Bodsda

---

### Post by schilcha on 2009-06-01
> **clonne4crw said:**
> I have 2 points of view to see this from:

1) The power user (most of us here): [...]

2) The home user who simply wants it to work: [...]


I think, pointing out these two extremes is very important to this discussion. Personally, I prefer to browse through the updates that are about to be installed. However, I've seen some ubuntu-installations with the update-notification icon being constantly ignored. Just because the users weren't aware of what updates are (and what they are good for). 

Implementing a reminder/request for authentication upon shutdown would be a good idea. Maybe similar to the authentication-request that pops up, when you try to shutdown the computer, while others are still logged in.

Of course, freedom of choice needs to be maintained --  as always.

Regarding the issue with updates that require user input, I doubt that the update script will receive well considered input from carefree home users.

BTW: I don't care about prolonged shutdown-times. I even check my disks on shutdown rather than on bootup.

---

### Post by spiceminesofkessel on 2009-06-01
I personally favor this sort of shut-down-and-install-updates feature. It's quite convenient to do my work/play and when I'm done, install updates while the computer shuts down. That's just more time I get to spend enjoying the use of my computer. It also helps me to remember to update my computer when I'm ready to shut down for the day.

---

### Post by lisati on 2009-06-01
I think I've already commented that I *might* use the feature, but wish to add that like several others who have contributed to this discussion, I usually use other means to download and update my machine. Like others, if I'm in a hurry to shut down my system I shouldn't be obliged to install updates. Isn't freedom to choose great?

---

### Post by Vadi on 2009-06-01
I like to read what am I getting updated. My mom wont though. But I voted for myself.

---

### Post by cmay on 2009-06-01
no. i do not want that. whem i shutoff my pc it is because i am so tired my eyes a falling out of my eyeballs and i would end up pulling the plug like i did on windows to stop those time consuming updates. when a man gotta sleep a man gotta sleep. :)

---

### Post by WinterMadness on 2009-06-01
I think the option should be there, I however probably wouldnt use it.

---

### Post by t0p on 2009-06-01
I also would not like updates at shutdown.  I like to see what ubuntu wants to install, so I can veto stuff I'm not keen on.  It's *my* computer and I never want to let the thing forget that.  Otherwise we're all in big trouble!

---

### Post by TheLions on 2009-06-01
i think this should be enabled by default on non-portable PC (home and office PCs) and disabled by default on portable PC(netbooks, notebooks, laptops etc)

The only problem could be detecting the right section

---

