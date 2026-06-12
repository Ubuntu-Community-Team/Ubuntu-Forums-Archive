---
title: "About the &quot;Partial Upgrade&quot; option"
date: 2011-10-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-20
Should it even exist in Update-Manager? As far as I can tell, it almost never really helps. Maybe it should be hidden inside some advanced settings?

Example: I tried to update today, but had lots of held packages. Installed the ones I could. Almost immediately after finishing the update on terminal, I got a pop-up telling me to do a Partial Upgrade. But I did a second standard upgrade (sudo apt-get dist && update && sudo apt-get upgrade). That's it, no packages hold, everything installed, all normal. There clearly was no need to go for the partial BEFORE trying a normal update one (or more) times. 


**EDIT: **After investigating a little: Because of an out of sync libjpeg-dev, the thing would remove more than 100 packages if I had accepted.

---

### Post by jerrylamos on 2011-10-20
I never use "Update" for anything.  I don't need more keystrokes and slower action.  I go into software sources and set it to never.  I update when I want to and don't need "Update" blasting in to what I'm doing.

When I'm ready, usually daily during development, I run an exec that does:

sudo apt-get update && sudo apt-get upgrade

Now if apt-get crashes an installation (incompatible packages?) usually more than once during a development cycle, I shift back to sudo aptitude update, sudo aptitude safe-upgrade.  "Update" has crashed an installation several times for me so I don't use it.  Ever.

Jerry

---

### Post by effenberg0x0 on 2011-10-20
> **jerrylamos said:**
> I never use "Update" for anything.  I don't need more keystrokes and slower action.  I go into software sources and set it to never.  I update when I want to and don't need "Update" blasting in to what I'm doing.

When I'm ready, usually daily during development, I run an exec that does:

sudo apt-get update && sudo apt-get upgrade

Now if apt-get crashes an installation (incompatible packages?) usually more than once during a development cycle, I shift back to sudo aptitude update, sudo aptitude safe-upgrade.  "Update" has crashed an installation several times for me so I don't use it.  Ever.

Jerry

Hey Jerry, yes a lot of people mention aptitude as a more reliable tool to handle broken deps, etc. But these are the "advanced" users, that comprehend the update process, packages, depends, rdepends, etc. We don't have to worry about them. But thinking about the "standard" users, which will only update when the update-manager dialog pops (update-notifier). I think they shouldn't ever be offered a partial upgrade.

**EDIT: **In other words: If we do have stickies in thread sections advising against it, why does the system continues to promptly offer it? :)

---

### Post by arpanaut on 2011-10-20
. > I think they shouldn't ever be offered a partial upgrade.The partial upgrade is a phenomenon that rears its head mostly in testing where there is less oversight of the syncing of the many rapidly uploaded packages.
And after a final-release greater care is taken that all packages are in place before the updates are released.
99% of the time an average user will not see this.

During testing I never let Update Manager handle things. I use the terminal or synaptic.
Yes, everyone should be aware of this pitfall, but after a proper-release it is not much of an issue.

---

### Post by ronacc on 2011-10-20
the warning about "partial upgrades "  is always one of the stickies in this forum .

---

### Post by jbicha on 2011-10-20
Why don't you propose (with a LP bug) that the "partial upgrade" button go away? Or at least be discouraged a bit more, either with a warning or by hiding the button by default.

---

### Post by ronacc on 2011-10-20
> **jbicha said:**
> Why don't you propose (with a LP bug) that the "partial upgrade" button go away? Or at least be discouraged a bit more, either with a warning or by hiding the button by default.

I agree it is too tempting for the average user and available via other means for more advanced users .

---

### Post by cariboo on 2011-10-20
I think this discussion is slightly ridiculous, we discourage new users from installing a testing release, as they usually don't have the experience/skill to fix things when they break.

The sticky explicitly says that update-manager should not be used during a testing session because of the rate of change in the repositories. I'd suggest turning off notifications until after the final release.

Running a testing release is a special circumstance, where we shouldn't even think about new users, until the final beta, the object here is to run a testing release on as many different platforms as possible so that whatever bugs may turn up are reported and dealt with.

---

### Post by PaulInBHC on 2011-10-20
Strangely enough I installed beta 1, then after that, I only used the update manager. I would wait a day or two after you guys said that the updates worked and then update. I didn't have a single problem. Crash popups occasionally but nothing that made it unusable.

---

### Post by cariboo on 2011-10-20
> **PaulInBHC said:**
> Strangely enough I installed beta 1, then after that, I only used the update manager. I would wait a day or two after you guys said that the updates worked and then update. I didn't have a single problem. Crash popups occasionally but nothing that made it unusable.

You did it the right way, but many users see that there are updates available and run them, without really paying attention to what update-manager tells them, they assume that a partial upgrade only means that some packages won't be installed, not that there could be broken dependencies, even though it is right there on the screen in front of them.

We all use and setup our systems differently, and have our favorite applications, but in the case of running a testing release, if you use update-manager, you should read and pay attention to what it is telling you about the upgrade you want to do. That is the problem, many less experienced users don't understand what they are seeing, that is why I recommend synaptic and aptitude, they won't continue unless you specfically tell it to, and you are given sufficient warnings.

---

### Post by ronacc on 2011-10-20
we shouldn't have to think of new users in the testing phase and yet they do show up pleading for help .

---

### Post by effenberg0x0 on 2011-10-20
I agree with Cariboo907 that helping new users is not the focus of a testing release, but Ronacc is right. If we compare this one to last cycle, this forum section will be filled with requests for help, broken systems and "how do I revert" questions by Alpha 1. Should they be testing? No. But if we can avoid the stress by omitting the update-manager at all, or removing the partial-update option, that would be a good thing. We should not forget that there are many more users out there besides the ones we see in this forum. Some will never get to read this forum stickies.

But I was thinking more on the final release than the development ones.  If you look at forums (not only this one), we do see people that somehow managed to get offered a partial upgrade and clicked it, many times ending up with an unusable system. Of course it's more rare for packages to be out of sync later, but it can and does happen. 

In my opinion, these small changes we have the opportunity to see, discuss and suggest to developers are the ones that eventually help make a more reliable, less likely to be broken by users, system, that may provide them with a better experience. 

I'll suggest for the partial-upgrade to not be offered. If there are help packages and broken depends, the behavior should be to not perform the upgrade and exit (try later, something like that). I think it's the safest behavior, considering this one is LTS, etc.

Regards,
Effenberg

---

### Post by cariboo on 2011-10-20
We can't stop people from doing stupid things to their systems, if there is way to screw it up even with all the precautions in place, someone will still find a way to do it, and then come to the forums, wanting help to fix it.

For example, a couple of years back we had a whole raft of people running:

```
chmod -R 777 /
```

The simplest fix for that problem is a reinstall, but there were several users that insisted on trying to fix it by manually changing the permissions of each and every directory, needless to say doing it that way takes a long time, and in most cases they didn't get it right. They then of course blamed Ubuntu for allowing them to do it.

We can't hold each and every users hand, and stop them from hosing their system, they have to take some responsibility themselves, which many users refuse to do.

---

### Post by ronacc on 2011-10-20
true , there is a fine line between reasonable protections ( and I think not offering partial upgrades would be one ) and excessive restrictions on user actions .

---

### Post by effenberg0x0 on 2011-10-20
I screw up sometimes LOL... I can only imagine what people that are not used at all with console can do. You know, typing too fast without looking to screen, thinking on other stuff, etc. I have made stuff like sudo rm -rf *some_extension like this:
sudo rm -rf * some_extension ... Notice the space between * and <some_extension>... I've done that a couple times actually.

---

### Post by ranch hand on 2011-10-20
I have no objection to the removal of UM but I never use it anyway.

The problem with removing it from the dev release is that, in that case, it will not be tested.  This was pointed out to me a couple cycles ago in a similar discussion.

Unfortunately this is true and if UM is to be included in the final release it needs tested.   It could be disabled early on maybe or left out for part of the time but that sounds like a lot of needless work for the devs.  It may also cause trouble for them to keep it up with upgrades going on for the entire package management suite.

I think improved warnings are about the best you can do.

---

### Post by gsmanners on 2011-10-21
Actually, the *best* that you could do is make Update Manager discern the difference between a good partial upgrade and a bad one. That would resolve the issue completely.

---

### Post by effenberg0x0 on 2011-10-21
> **gsmanners said:**
> Actually, the *best* that you could do is make Update Manager discern the difference between a good partial upgrade and a bad one. That would resolve the issue completely.


I agree... But while there are some bugs or annoyances, some specific features missing, etc in Ubuntu that we can link to programmers lack of time, focus, small mistakes, etc, I consider the apt apps and deb system one of the most complicated to play with. If a feature is not there, it probably is very hard to implement...

I know a guy who's working on something very similar for an ERP system: He's created a very basic framework for testing. There are only 10 packages (A, B, C, etc). Each package can have any number of versions. (A1, B1, C2, D1.0.1, etc). Then you start to input rules in a xml file saying stuff like: A depends on B. B depends on D. E conflicts with A, but E1 can be used with A as long as D version is > 2.0, D2.0 is not compatible with A<1.6, etc. Now, the remote server get their xml rules from a central server and must execute them in order. XML rule1, xml rule 2, etc. Now, suppose the central system is dispatching xml rules for 3 years and, it's on xml rule 1.000 and you install a new zeroed server that will receive these rules. Should the new server download, erase, redownload, apply, unapply, etc packages from xml rules 1,2,3,4,5...1000? No, of course not. It should calculate the best, fastest, using less bandwidth way to get to rule 1000.

It's not that one can't develop C code to solve the puzzle. The question is how to solve the puzzle efficiently: Fast, make use of packages that are already downloaded when possible, make sure local packages are OK (md5, etc) or re-download them, reinstall them, without breaking deps, etc. And then when you get to a unknown status (failed download, broken package, down server offline, wrong xml rule - all of these will eventually happen), know  how to get back to the last possible status using resources efficiently, in a way that the system will never get broke.

From the standpoint of programming logic it might sound easy... pure mathematics - compare packages versions to rules. But just about any code you make would be criticized by a program manager, code optimization specialists, etc. It won't be truly efficient until a late and mature version.

So, in the case of update-manager, considering that developers should choose between something similar to that and commenting out a button... I'd comment out the button :)

---

### Post by gsmanners on 2011-10-21
> **effenberg0x0 said:**
> From the standpoint of programming logic it might sound easy... pure mathematics - compare packages versions to rules. But just about any code you make would be criticized by a program manager, code optimization specialists, etc. It won't be truly efficient until a late and mature version.

Conveniently, this is what testing is for. And we do have a forum full of testers here, right? :D

I'm not saying this should be implemented today or tomorrow or even within a year. I'm just saying this seems to me like the right direction: just fix the thing.

Now, in that anecdote you mention something important: breakage. It seems to me that we can expedite a fix by properly defining exactly what breakage means. Once we can distill that down into numbers and logical rules, it seems to me that it would be trivial for a developer to put that into a test package for us to try out.

---

### Post by effenberg0x0 on 2011-10-21
> **gsmanners said:**
> I'm just saying this seems to me like the right direction: just fix the thing.

I agree, of course. Just thinking about the complexity of such an improvement.

> **gsmanners said:**
> 
Now, in that anecdote you mention something important: breakage. It seems to me that we can expedite a fix by properly defining exactly what breakage means. Once we can distill that down into numbers and logical rules, it seems to me that it would be trivial for a developer to put that into a test package for us to try out.

In that story I told, they're now coding with the idea of "Working Sets". You have xml rules being posted: Download X, update Y,  downgrade Z, remove W, etc. But the server that dispatches XML rules also publishes a file that contains all the packages and versions expected to be together in the each version. If one remote system gets confused, it downloads the latest "Working Set" file, compares to it's internal list of packages, and then will only work on the differences between this system and the latest working set. If the latest set is proven to be broken, it is excluded from the list of working sets. All systems will now consider the previous working set as what they should adapt to.

**EDIT**
But that would never work for us here: While some packages are mandatory and some "Working sets " are known (in the default install), users may install lots of alternative programs, which may or may not respect and use the shared files (libs, etc) from the latest "Working set". The LTS release ISO and subsequent updates are the only "Working Sets" we could work with. And applying them would eliminate users additional programs. To that effect, dist-upgrade is supposed to be the "Apply Working Set" feature. Partial-upgrade is hmm, lets see how many packages we can get, but there's no guarantee we are creating a working set.

---

### Post by gsmanners on 2011-10-21
Or it could be something as simple as if you have to remove 3 packages for every 1 you install, then that should require manual intervention or something like that.

---

### Post by effenberg0x0 on 2011-10-21
In my language there's an expression that can't be properly translated to English or other language I think LOL. It  says "and that's when the snake is gonna smoke", meaning (who knows why, since snakes don't typically are addicted to cigarettes) that that's when things get real ugly :) So, when I hear the words "manual intervention", that's when the snake is gonna smoke. We see at forums users that happily removed grub, compiz, unity, their video-driver, etc to solve dep breakages. It's like me if I was left alone in front of a surgeon table with an open body in front of me and 10 minutes to do something. "-Well, maybe if I remove this... push that a little... or that.. What's that for? Maybe I can connect it elsewhere or I pinch this vein..." lol

---

### Post by ronacc on 2011-10-21
since it wouldn't seem to be too hard to add a line of code to not offer the upgrade if it would result in broken packages , it might be interesting to bring this up at UDS and see what the rationale is for not having done so .

---

### Post by cariboo on 2011-10-21
I personally think it would be much better to set the default notification of updates to once a month, except for security updates, instead of the way it is now, where you basically get notification whenever there are updates available, this would in most cases make sure that all the dependencies are also available.

---

### Post by gsmanners on 2011-10-21
Maybe they could make a special meta package called "testing-update-trigger" which only gets updated when the developers want you to run an update in Update Manager during testing.

---

### Post by seeker5528 on 2011-10-21
> **cariboo907 said:**
> I think this discussion is slightly ridiculous, we discourage new users from installing a testing release, as they usually don't have the experience/skill to fix things when they break.

Some people are too quick to discourage. Willingness to learn should be a bigger factor than being new.

As for the 'partial upgrade' thing, it comes up a lot, so it gets discussed a lot.

Later, Seeker

---

### Post by sisco311 on 2011-10-21
> **effenberg0x0 said:**
> In my language there's an expression that can't be properly translated to English or other language I think LOL. It  says "and that's when the snake is gonna smoke", meaning (who knows why, since snakes don't typically are addicted to cigarettes) that that's when things get real ugly :) So, when I hear the words "manual intervention", that's when the snake is gonna smoke. We see at forums users that happily removed grub, compiz, unity, their video-driver, etc to solve dep breakages. It's like me if I was left alone in front of a surgeon table with an open body in front of me and 10 minutes to do something. "-Well, maybe if I remove this... push that a little... or that.. What's that for? Maybe I can connect it elsewhere or I pinch this vein..." lol

The etymology of the expression is quite interesting. It was first used as an adynaton ("when will pigs fly", "when it's snowing red" or "(it will happen) on February 31st")...

/offtopic

---

### Post by ranch hand on 2011-10-21
> **seeker5528 said:**
> Some people are too quick to discourage. Willingness to learn should be a bigger factor than being new.

Later, Seeker
Yes.  Restricting who can install a dev release is just not in the Linux way of doing things at all.

Information on what is likely to happen, breakage, is a good thing and can't be over done.  If folks want to do it they should be encouraged to do so while expecting a good bit of learning to be necessary to continue do it.

It is their choice.

Can't be that hard to do.  We do it.

---

### Post by cariboo on 2011-10-21
> **ranch hand said:**
> Yes.  Restricting who can install a dev release is just not in the Linux way of doing things at all.

Information on what is likely to happen, breakage, is a good thing and can't be over done.  If folks want to do it they should be encouraged to do so while expecting a good bit of learning to be necessary to continue do it.

It is their choice.

Can't be that hard to do.  We do it.

I never said restricting anyone from using a testing version was a good idea, and I agree with seeker5528, that if someone is willing they will receive all the help they need. It's the people coming here for help then two hours later they post that they solved the problem by installing a different version or if they have difficultly following instructions that have already been posted in a thread.

I did say that if people are unwilling, or unable to solve simple problems on their own, they should be discouraged from using a testing version.

---

### Post by gsmanners on 2011-10-21
There's also the fact that breakage contaminates the results of otherwise good testing, good testers break their systems every now and then, and all the discussion of partial upgrades is definitely a big distraction (which slows testing). Is that enough motivation to fix this bug? :D

---

### Post by ranch hand on 2011-10-21
> **cariboo907 said:**
> I never said restricting anyone from using a testing version was a good idea, and I agree with seeker5528, that if someone is willing they will receive all the help they need. It's the people coming here for help then two hours later they post that they solved the problem by installing a different version or if they have difficultly following instructions that have already been posted in a thread.

I did say that if people are unwilling, or unable to solve simple problems on their own, they should be discouraged from using a testing version.
I was agreeing with that one statement of  his.  Restriction of access comes up nearly every cycle.   I object to in on principle.  It will not work anyway.

I have been around here long enough to know that you are not of the restriction advocates.

---

### Post by effenberg0x0 on 2011-10-21
> **cariboo907 said:**
> 
I did say that if people are unwilling, or unable to solve simple problems on their own, they should be discouraged from using a testing version.

Agreed. I think there's just a small misunderstanding on the term "discourage". Not properly discouraged I think but very emphatically warned that things can go pretty bad. I think sometimes users with a Windows background don't realize that they can actually make a Linux OS unbootable (in terms - "black screen") by simply performing an upgrade.

Ideally, and I know you hate me for saying that again, I really think users should have an option in Grub to reset their install preserving non-config files at /home/*/*. It is easy to do, would allow more people to play and learn, take chances, knowing they can revert to default.

---

### Post by ronacc on 2011-10-21
heck they don't even have to upgrade windows to get a BSOD .

---

### Post by seeker5528 on 2011-10-21
> **ronacc said:**
> heck they don't even have to upgrade windows to get a BSOD .

I had a system the other day where people were complaining about a blue screen so I was all prepared to go into troubleshooting mode. Turns out the background was set to a solid color.... blue. :-s

Wish they were all that easy. :P

Later, Seeker

---

### Post by jbicha on 2011-10-22
> **cariboo907 said:**
> I personally think it would be much better to set the default notification of updates to once a month, except for security updates, instead of the way it is now, where you basically get notification whenever there are updates available, this would in most cases make sure that all the dependencies are also available.

I thought the default update check was once a week these days.

---

### Post by gsmanners on 2011-10-22
The more I think about this problem, the more I'm convinced that this is really a server-side logistical problem. Maybe there's some ideal time of day to do an update. Is there any way to confirm this? Or do groups of packages just enter the repositories whenever?

---

### Post by masgeeks on 2011-10-22
Anyone who does an upgrade is someone who likes headaches.  Canoncial should change the update manager default for checking for new distro upgrades to NEVER.  Really.  Honest.  Truly.

It is so sad to listen to users freakout because they upgraded and things fell apart.

Clean installs are not hard!  Reinstalling apps is not hard and neither is copying back your config files!  Backing up data is not hard...!!!  It takes far less time then upgrading... and hurts your head less, lol...  :D

---

### Post by ranch hand on 2011-10-22
> **gsmanners said:**
> The more I think about this problem, the more I'm convinced that this is really a server-side logistical problem. Maybe there's some ideal time of day to do an update. Is there any way to confirm this? Or do groups of packages just enter the repositories whenever?
The reason you rarely, if ever, see a partial upgrade in Update Mangler in released OS' is that the repo entries are put in as a group (package and dependencies).  This is the stable repo policy.

In development the entire process is different.  This is a fast moving target and packages go into the repo when they are ready to be there.  The depends may get there first.  They may get there next week.  They are usually pretty well coordinated.

A lot of developers are working at vastly different places around the world.  Racing to get this thing built.  They may be having trouble getting a package to build or been to a funeral.

This is what makes testing FUN.

Using UM is generally not a real good idea.  Use apt-get or aptitude.  READ what they tell you is going in and being removed.  If something is removed see what is being installed.  It may replace the removed package.

I have found that, for me, installing upgrades is fairly safe if nothing is being removed.  That is me, you have to decide for yourself.

If you are not familiar with apt-get and aptitude read up on them and make a file of commands for your self.  They both are good tools with some interesting differences.  They are the safe way to do all your update/upgrades no matter what the version.

---

### Post by gsmanners on 2011-10-22
> **ranch hand said:**
> ...

In development the entire process is different.  This is a fast moving target and packages go into the repo when they are ready to be there.  The depends may get there first.  They may get there next week.  They are usually pretty well coordinated.

A lot of developers are working at vastly different places around the world.  Racing to get this thing built.  They may be having trouble getting a package to build or been to a funeral.

This is what makes testing FUN.

It also makes testing Update Manager (which still has many many bugs in it to judge from its launchpad page) a risky venture on the client side, which is bad for testing. And, yeah, this is what I've been assuming about packages, but I'm wondering if it *really* does work like that.

You may get updates from say the US, Australia, Europe and maybe sometimes other parts of the world, but I'm thinking most of the updates are from Europe or the US. And the build server is what is building these packages, right?

The build servers don't have to build the packages right away. They can start building at 4am or whenever is most convenient for a server to do something that uses a lot of CPU. I assume they're already configured this way, anyway.

And the reason that a release doesn't break is that packages always go into the proposed repo, where they are tested first. Then, if they work, they get moved into the proper repo. At least, that's my understanding of the matter.

---

### Post by ranch hand on 2011-10-25
It may be that most updates to the repo come from Europe and North America but I am not sure of that at all. I know that some of the devs are in Asia.  I would be surprised if Australia and Africa do not have devs there too.

The simple time differences will cause some disruption.

Just use care.  If something breaks running your update/upgrade cycles through recovery or chroot for a couple of days will usually clear it up.

---

### Post by cariboo on 2011-10-25
> **ranch hand said:**
> It may be that most updates to the repo come from Europe and North America but I am not sure of that at all. I know that some of the devs are in Asia.  I would be surprised if Australia and Africa do not have devs there too.

The simple time differences will cause some disruption.

Just use care.  If something breaks running your update/upgrade cycles through recovery or chroot for a couple of days will usually clear it up.

All packages are submitted to the Main repositories first, before they are propagated to the rest of the mirrors, so it's more a matter of the mirrors not being updated fast enough. There is also an autobuild system. where in some cases a package has been built, but some of the dependencies may take a little longer before they are done.

Once a package has been submitted and accepted, there isn't any human intervention before it shows up in the repositories

---

