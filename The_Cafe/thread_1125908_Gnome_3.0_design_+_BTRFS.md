---
title: "Gnome 3.0 design + BTRFS"
date: 2009-04-14
forum: The Cafe
---

### Post by BGFG on 2009-04-14
With the 'data loss' fiasco behind us and a freshly patched kernel, to those who have been keeping up with the 3.0 development (I'll create a new user and try it myself soon) What is going on with 3.0 being ready to fully maximize the features of btrfs ?

Clearly the structure of SOMETHING has to change and that was brought to the fore in very recent memory. It would be downright remedial for us to experience a same such situation with the advent of a stable btrfs and a same such problem being an 'unforseen' eventuality.

This post was inspired be Gnomeuser's sig, and is a sincere attempt at some 'old style' forum chatting :)

So hit up wiki and launchpad and google then come out blazing! 

Another note: The shell seems to be pushing 'type to launch' into the main menu, with that and more functionality(i assume) built in, where will that leave our beloved docky ?

---

### Post by BGFG on 2009-04-15
Ha! like i'd let this one die without a fight... bump!

---

### Post by gnomeuser on 2009-04-15
Someone loves me.. yay.. :KS:KS:KS

Now back to business, does GNOME take advantage of btrfs functionality such as snapshot. The answer is no, not yet and then again it does a little. You see there is apparently work going on to port Sun' timeslider in Nautilus from ZFS to btrfs (or a generic abstraction layer I hope to avoid hardcoding for this, which we could do with lvm as well). 

Aside that there aren't many things to really take advantage of from a GNOME perspective. As a distribution and with the PackageKit glasses on one could do rollbacks of package upgrades using btrfs snapshots, this is very likely an area that are filled with corner cases and I suspect the putting on of thinking caps will be required. I haven't given much thought to this specific area. 

We might also be able to have a little thing in DeviceKit-disks to enable compression (and when support arrives partition encryption) on volumes that support it such as btrfs.

The problem right now I suspect is that btrfs isn't really in peoples hands yet. The only distro to ship preview support to developers can easily play with it and be sure that their distro will accept bugs and pipe them to developers actually working in that code is Fedora 11. I am hoping that Ubuntu and openSUSE will join the wagon for their next releases, with some kind of magical argument at install time to activate to keep it clear that this is expected to be bumpy (Fedora uses the humorous icantbelieveitsnotbtr).

Now you mention data safety, the very same issue that affects ext4 (or affected, behaviour is now the same as with ext3) affected btrfs but it has also been patched while applications and libraries are being fixed.

---

### Post by Methuselah on 2009-04-15
> 
Now you mention data safety, the very same issue that affects ext4 (or affected, behaviour is now the same as with ext3) affected btrfs but it has also been patched while applications and libraries are being fixed.


This was my understanding, that applications have been making some assumptions that no longer hold true for the newer file systems.

So I guess these patches to the filesystems are just temporary and will be unneccessary once the appropriate pattterns are adopted again.

I'm looking forward to giving ext4 a test drive myself.
My current Jaunty installation is an upgrade which still uses the Intrepid partition.

---

### Post by gjoellee on 2009-04-15
I am using Arch and have been using Ext4 in a few months, and it works great! Everything goes a little faster and it really makes me even happier!

---

### Post by gnomeuser on 2009-04-15
> **Methuselah said:**
> This was my understanding, that applications have been making some assumptions that no longer hold true for the newer file systems.

So I guess these patches to the filesystems are just temporary and will be unneccessary once the appropriate pattterns are adopted again.

I'm looking forward to giving ext4 a test drive myself.
My current Jaunty installation is an upgrade which still uses the Intrepid partition.

It's a disagreement between what application developers expect and what filesystem developers expect. Filesystem developers lean on the POSIX standard which explictly states that the behaviour they implemented is allowed. Application developer on the other hand are happy with the way ext3 works, especially since kernel developers first yelled at them for using fsync and now they are required to do it. 

There is the concern that performance will be adversely affected by adding fsync calls, this is likely to cause the same issue which made Firefox 3.0 lockup for seconds or minutes (this was due to excess fsyncing). Requiring everything that cares about data security to do this or think of some clever way to do things is seen as dangerous and a lot of work when retaining the ext3 behaviour does the same and performance is not seemingly affected much.

I can see both sides of the story here, we have no data to show the real impact of requiring everything to call fsync but there is the fear that will we create huge pauses for the user where the system is non-responsive. This would be fatal. It is perfectly understandable that application developers are unwilling to just do this, they risk a significantly lower throughput and a positively horrible desktop experience. 

I personally think that the POSIX standard was written many years ago, when we did not have the computing environment we do today. It might be time to rethink some of the assumptions that lead to this decision and see if it jives with what we generally need and if we can do better. That is not to say that POSIX should be ignored but I think in the places were we can do better (like we do with relatime) we should consider it. We make changes in a documented fashion and sometimes, it is the spec that requires fixing not the code.

Another concern is that changing things now when not all major distros have picked up ext4 as their default filesystem will cause performance to suck really badly on ext3 which is what most distros will be shipping. There is an uneven ground on which to build right now, once ext3 has been phased out of say the major 3 distros it is a better climate to experiment with this kind of major changes in behaviour since that will ensure uniform experiences for users on the default settings.

All in all this should have been communicated better but I doubt another really knew the impact. I am happy that the filesystem developers have merged patches to restore ext3 type behaviour till such a time as we can assess the true impact of this change. It will take years to shake out all the little bugs and come up with designs that suit everyones needs.

In case anyone wonders, I have been using Ext4 as my sole filesystem since F9 made me able to install on it. I have continued this usage now on Ubuntu (which I am happy to say works nicely including the grub patch, excellent work people).

---

### Post by BGFG on 2009-04-15
After what happened, i sincerely believe tht there will be more communication between FS and APP devs, or at the very least, app developers will keep track of FS behavior and hopefully test the further versions on the beta filesystems. As i say this i am suprised that the existing desktop environment devs did not catch this at an earlier stage.

but to be fair, stable or not, jaunty is still in beta and this is the stage when such things are meant to be caught anyway....

I hope that BTR gains even more development momentum and we are able to see a 'everyday' usable version come 1st qtr '11 ? :) I can't wait for an online defrag tool in ext4 or BTR. In any case, when i converted my partitions from 3 to 4, fsck gave me a report of 6.something % fragmentation, which i think is ridiculously low after over a year of use.

---

### Post by gnomeuser on 2009-04-16
> **BGFG said:**
> After what happened, i sincerely believe tht there will be more communication between FS and APP devs, or at the very least, app developers will keep track of FS behavior and hopefully test the further versions on the beta filesystems. As i say this i am suprised that the existing desktop environment devs did not catch this at an earlier stage.


Actually we already have some interesting approaches ready now, Chris Mason (of btrfs fame) wrote a new handling mechanicsm called data=guarded which should combine the best of both worlds we are able to right now on ext3. 

The latency issues with ext3 which is causing some nasty multi second pauses is also being worked on actively and we are now down from a highly reproducable +5 pause on fsync to some occasional ~2sec ones on Linus' reference machine. There is still work to be done. 

If anyone wants to read up on this, [Linux Weekly News](http://www.lwn.net) has an excellent article this week on this subject. I cannot recommend getting a subscription enough. 2.50$ buys you some of the best techical reporting on Linux around every week. 

If you are an Ubuntu member I believe you can get a subscription for free from Canonical, the same goes for Fedora developers (I believe there's 50 subscriptions up for grabs every year - I never took one as I don't mind paying myself). 

> 
but to be fair, stable or not, jaunty is still in beta and this is the stage when such things are meant to be caught anyway....


Sad fact is that even the best possible code has one bug per 1000 lines of code. Stable depends on how you define it. Sometimes data corruption bugs require those odd corner cases that just aren't triggered in stress testing. I remember once there was a bug in a popular feed reader that only manifested itself on Feb 29th. And just looking at the situation with ext3 currently years after it got deployed and marked stable we are finding all manners of nasty latency and potential data corruption bugs. Stability is a never ending process of constant testing.

> 
I hope that BTR gains even more development momentum and we are able to see a 'everyday' usable version come 1st qtr '11 ? :) I can't wait for an online defrag tool in ext4 or BTR. In any case, when i converted my partitions from 3 to 4, fsck gave me a report of 6.something % fragmentation, which i think is ridiculously low after over a year of use.

btrfs is the future, but I doubt for the reasons you think. There are features in there we really want but it's not as you seem to believe a big stability be all, end all nor in fact a substantial performance enhancement over current filesystems. But that is a whole different debate. When will it be ready, I think in a years time we can see mainstream distributions such as Ubuntu and Fedora offering it as a choice without to many warnings. 

The aim is realisitically to have it be ready for production rollouts in time for deployments like RHEL7 (which is probably 3-4 years out). There are though different demands for stability and enterptises like their filsystem to have been hammered on for a good while before they trust millions of dollars worth of data to it.

---

### Post by BGFG on 2009-04-16
Nah, i know those are'nt the only reasons to be looking forward to BTRFS but it's one of the many.
A year you think ? from what I have seen looking at the ext4 cycle, a year would mean blazing fast development, but then, FED11 IS offering it so it must be well along.(icantbelieveitsnotbtr is just corny!:P) The comparison against ZFS inevitably comes up often, is BTR really a leapfrog past ZFS ?

BTR, Tux3, Gnome 3.0, palimpset, time slider port, Next two years are shaping up to be very exciting!

---

### Post by gnomeuser on 2009-04-16
> **BGFG said:**
> Nah, i know those are'nt the only reasons to be looking forward to BTRFS but it's one of the many.
A year you think ? from what I have seen looking at the ext4 cycle, a year would mean blazing fast development, but then, FED11 IS offering it so it must be well along.(icantbelieveitsnotbtr is just corny!:P) The comparison against ZFS inevitably comes up often, is BTR really a leapfrog past ZFS ?

BTR, Tux3, Gnome 3.0, palimpset, time slider port, Next two years are shaping up to be very exciting!

btrfs is not guaranteed to even have a stable dataformat, it's not something you should install your main system on. It will eat babies occasionally or at least fail to boot. 

It is however as I understand not expected, unless nasty surprises are uncovered, that the dataformat will change again. This is an important step for testing since it means you will be able to keep your partition instead of having to reformat your btrfs partition to follow development updates.

I know that Chris Mason has used btrfs as his laptop filesystem for a while without hitting problems. According to smolt we have 106 active btrfs users currently and following the mailing lists I haven't seen anyone report that everything went up in flames. 

I still think that to get to a point where distributions might be comfortable supporting it as a choice it will take a year. Fedora 11 has it as a technology preview, from ext4 being in that state to becoming the default was 2 cycles (F9 and F10 then default in F11). If we look at btrfs the same way that would be F11 + F12 as preview then F13 for default. I doubt this will hold but Red Hat are very invested in btrfs development now and it seems clear to me that they want it in RHEL7. So I expect for the rest of us this will mean an increased effort to get btrfs ready as soon as poosible - which we might all agree is good.

RHEL6 development is expected to be based on F11. This puts RHEL7 out as being based on F15-F17, extrapolating from the previous development schedules it takes about 2-3 years in between RHEL releases so that seems reasonable. There would thus be a push on their part to get it ready for wide testing before that branching point.  

My guess would be that for F13 (a year from now), you will see it at a stage where Fedora will feel confident enough to offer it as a supported choice (without the preview enabling butter disbelief magic) but the default will remain ext4. This is quick, but I see an awful lot of work going into it and it is getting stable encouragingly quick. I was able to install on btrfs and use it when I tried the other day just for fun. It's not a terribly smooth ride but it is there today.

There is still a long way to go, the userspace tools needs work, a grub patch needs to be cooked up. The ecosystem around Linux needs to be able to take advantage of btrfs features. It's not just about where we are in terms of the kernelspace part. If e.g. we want the package management systems to take advantage of this for rollback, we really need to get testable btrfs systems out in the hands of these developer as soon as possible. I think it's dangerous to set dates, my deep hope is for F14-F15 for it to be really good and solid for every day use on my machine.

(For people not fond of the Fedora based timeline, I use it because it is focused on technology delivery dates and Fedora is early adopters land which drives a lot of this technology. Thus this is a good gauge for giving dates on this specific target. You can replace the term with 6 month intervals F11 being the baseline release set May 26th 2009).

---

### Post by BGFG on 2009-04-16
> **gnomeuser said:**
> 

There is still a long way to go, the userspace tools needs work, a grub patch needs to be cooked up. The ecosystem around Linux needs to be able to take advantage of btrfs features. It's not just about where we are in terms of the kernelspace part. If e.g. we want the package management systems to take advantage of this for rollback, we really need to get testable btrfs systems out in the hands of these developer as soon as possible. I think it's dangerous to set dates, my deep hope is for F14-F15 for it to be really good and solid for every day use on my machine.


Full agreement here, no point to cutting edge tech if the user tools can't take advantage of it or are simply lagging behind. With jaunty final I'll begin using the shell and prob next year i'll try a test on btrfs and see how i can contribute. By that time hopefully I'll have a better (and i mean phenom/ddr3 when i say better) machine that can give me a proper VM or just set up a discrete partition for a legit test boot.
i really need to check out fedora.

---

### Post by wildman4god on 2009-04-17
Speaking of gnome 3.0, two of its most talked about and controversial technologies is the gnome shell, and zeitgeist.

Personally I like both idea's and I have talked to others who also liked them, most in particularly like zeitgeist, I have heard a lot of people slam these ideas saying they limit "freedom" in the ability to customize your desktop, and while I even hate to see that go, it seems that most computer users (those who actually need to get work done) aren't as concerned about how customizable their desktop is, they just wanna get work done, and I believe that this is part of gnome's philosophy, to get out of the user's way and let them get work done. Plus these two technologies are really innovative, something that no other OS has done before. any thoughts?

---

### Post by days_of_ruin on 2009-04-17
I am really interested in the gnome shell. But lets hope them menus don't update change like on windows. Also they need to add the applications categories, no way searching for apps by name and description could be as usable. At least if you don't already know exactly what you are looking for.

---

### Post by Skripka on 2009-04-17
> **days_of_ruin said:**
> At least if you don't already know exactly what you are looking for.

To play Devil's Advocate: Don't most people know, or have a general idea what apps they have on their system?

i.e. Gimp, Firefox, etc

---

### Post by wildman4god on 2009-04-17
I saw some where once before that when you click the more button under your favorite apps, it slides out to an application browser, with categories and you can select how they are listed (list, details, icons, etc) It looks similar to the app browser on Ubuntu netbook remix, however I can't seem to find the screenshot again to show you.

---

### Post by days_of_ruin on 2009-04-17
> **Skripka said:**
> To play Devil's Advocate: Don't most people know, or have a general idea what apps they have on their system?

i.e. Gimp, Firefox, etc

Not if they are new to ubuntu. And some programs you would never use
except that you saw them while looking for something else, ie disk usage analyzer.

---

### Post by Skripka on 2009-04-17
> **days_of_ruin said:**
> Not if they are new to ubuntu. And some programs you would never use
except that you saw them while looking for something else, ie disk usage analyzer.

Finding a disk usage analyzer (FileLight comes to mind) can be just as time consuming to find in a hierarchical menu as it is in an indexed search, as if you don't know where it got dropped you have to go by process of elimination.  Odds are if you are new enough to Ubuntu to not know what got installed and where it is-you probably aren't fluent enough with the multiple menu pull downs to save any kind of meaningful time and effort.

It is best not to just go one or the other-but to have the option of both until one has familiarity with what they have.


Everyone thinks differently though. I prefer an indexed menu-as it wastes much less screen space and stays out of the way.  Which on smaller monitors can be a big issue.  Of course, I also know what apps I have on my system.

---

### Post by BGFG on 2009-04-17
Zeitgeist looks like it will take some getting used to. Does the currently offer any aesthetic settings ? Change look to something more like docky or AWN for example ? I read that the AWN lead dev is involved in the 3.0 development.

---

### Post by days_of_ruin on 2009-04-17
> **Skripka said:**
> Finding a disk usage analyzer (FileLight comes to mind) can be just as time consuming to find in a hierarchical menu as it is in an indexed search, as if you don't know where it got dropped you have to go by process of elimination.  Odds are if you are new enough to Ubuntu to not know what got installed and where it is-you probably aren't fluent enough with the multiple menu pull downs to save any kind of meaningful time and effort.

It is best not to just go one or the other-but to have the option of both until one has familiarity with what they have.


Everyone thinks differently though. I prefer an indexed menu-as it wastes much less screen space and stays out of the way.  Which on smaller monitors can be a big issue.  Of course, I also know what apps I have on my system.

My point was browsing is easier in a menu system. You can see all the apps
that are available.

---

### Post by wildman4god on 2009-04-17
> **BGFG said:**
> Zeitgeist looks like it will take some getting used to. Does the currently offer any aesthetic settings ? Change look to something more like docky or AWN for example ? I read that the AWN lead dev is involved in the 3.0 development.

every thing you are seeing now about gnome3.0 is all proto-types, remember they still have a year to go to develop and making it look pretty is a big part of gnome 3.0 but first they need a stable functional foundation. They also say that if 3.0 isn't ready by march next year they will delay it another release to avoid the kde 4 feasco.

---

### Post by oomingmak on 2009-04-17
> **days_of_ruin said:**
> My point was browsing is easier in a menu system. You can see all the apps that are available.
Exactly!

If you browse a menu, then you can see the options available to you, and the selection process becomes "guided" as you make choices and navigate your way down the menu tree. You'll also often jog your memory in the process, because you can see the various options appearing right in front of you. Of course, once you are very familiar with something, then this can be seen as a cumbersome way to launch, but for such tasks users will often place launchers in convenient places or use hotkeys to launch directly, but that does not mean that such an approach should be used for all tasks.

If, however, you are just confronted with a text entry box (plus a couple of icons for 'recently run' actions), then you have to *know *(and remember) exactly what it is you want to access, because until you start typing into the text box, the list won't start being filtered and offering suggestions. Type the wrong starting letter(s) (because you've remembered it incorrectly or you've made a typo) and the program / task that you are looking for won't come up at all. This will only serve to frustrate the user.

I also don't understand how they propose to move away from application-centricity to task based actions, because the underlying programs that will be called into action in response to the user requested tasks are still going to be using the application paradigm. 

Task to application mapping will certainly not be one-to-one due to the legacy of multi-purpose software and the invariably resulting functional overlap.

---

### Post by gnomeuser on 2009-04-18
Just showing off, nothing of real importance. This by the way is my one and only system, and yes that is btrfs as the / filesystem. 

This is how much I trust it currently. I will report further as experience gets more detailed.

---

### Post by BGFG on 2009-04-18
> **gnomeuser said:**
> Just showing off, nothing of real importance. This by the way is my one and only system, and yes that is btrfs as the / filesystem. 

This is how much I trust it currently. I will report further as experience gets more detailed.

I am NOT that brave. What is the system response like as opposed to ext4 ? or is it too early to tell as some features may be yet unimplemented ?

---

### Post by gnomeuser on 2009-04-18
> **BGFG said:**
> I am NOT that brave. What is the system response like as opposed to ext4 ? or is it too early to tell as some features may be yet unimplemented ?

To early to tell, I have also only had the system configured like this for a day. So far no baby eating behaviour but I am not by any standard recommending it. I, partly, have this setup like this in the hope that I can participate in the "break a filesystem" test day that's coming up for Fedora.

---

### Post by gnomeuser on 2009-04-18
The land of excitement. At first the system ran beautifully, everything was very nice. Then there started to be constant disk access and kacpid took up an awful lot of CPU time. This turned my desktop into a horrible molasses which was completely unusable. Followed after two hours by a refusal to turn off and then voila a nice kernel panic with data loss as garnish.

I am not sure btrfs caused all of that, I have had a problem with the nouveau driver which should have been fixed. 

See, breaking my machine so you don't have to, that's the kind of guy I am.

---

### Post by BGFG on 2009-04-18
Btrfs just became an 11.04 enterprise for me :) Meet you guys in the shell in a few weeks though. How's the machine ? might I suggest Advil....
I've been using the binary blob so smooth sailing here....

---

### Post by dreaminhere on 2009-04-22
just found this article [http://www.linux-mag.com/cache/7308/1.html](http://www.linux-mag.com/cache/7308/1.html)  It has the ext3, ext4, and btrfs comparisons as well as info on btrfs.  Thought it might be interesting

---

### Post by BGFG on 2009-04-24
I just posted the exact same article an another thread :) I get happy everytime i read 'heavy development'

---

