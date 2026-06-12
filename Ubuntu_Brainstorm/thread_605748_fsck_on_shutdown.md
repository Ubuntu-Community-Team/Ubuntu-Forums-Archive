---
title: "fsck on shutdown"
date: 2007-11-07
forum: Ubuntu Brainstorm
---

### Post by AusIV4 on 2007-11-07
This was discussed in the Gutsy Gibbon Idea Pool, and I thought I'd bring it up again. As a laptop user, I find it very irritating that ubuntu periodically and without warning checks my disks when I boot up.

Now, I know how to check and see how many more mounts I have until a forced check, and I generally try to force an fsck at a time that won't be an inconvenience. But occasionally I forget, then I get to class and have to wait 5 minutes before I can start taking notes.

I don't know how plausible this is, but it would be much more convenient for fsck to occur on a shutdown rather than startup. It's very rare that I have to have my computer off quickly, but quite common that I need it to boot up quickly.

This may not be the best option for everyone, so it would be nice if it were configurable, but I think it would be a great feature for those of us running laptops.

---

### Post by soccerboy on 2007-11-07
I haven't run into this problem but I don't use my laptop for notes yet (still looking for a good notetaking software).  But, I know as soon as I do start using it much more, since hibernate doesn't work on my laptop, I am sure to run into the same problem as you.  I would love for this to be a configurable option also.

---

### Post by teasum on 2007-11-08
I agree with this as strongly as I possibly can.  I encounter this as a problem almost weekly, as I also use a laptop that has hibernation issues.  Already this semester, as a TA, I've had to keep colleagues and/or students waiting while my laptop ran a disk check 4 times.  Bonager is a good start, but I think the best option by far is to somehow get fsck to run at shutdown.

---

### Post by AusIV4 on 2007-11-08
I seem to remember a utility a while back with similar intent. Someone had found a way to force the computer to reboot rather than shutdown when an fsck was imminent, run fsck on that boot, then shutdown. 

I would hope that the ubuntu developers should be able to come up with a more elegant solution, but if not it would even be nice to have a script like that in the repositories.

---

### Post by CrazyGuy123 on 2007-11-09
Anyone want to have a go at coding this?

I don't think it should take more than a few lines of bash.

I propose the following behaviour:

On startup, the current procedure stays unchanged.  This is because if the disk is transfered between PC's or if it's shutdown uncleanly, the disk needs to be checked before it's used.

On shutdown, a new section added to one of the shutdown scripts so the number of mounts left is checked, and if there's less than say 2 mounts left it'll run fsck.

A patch could then be submitted to the scripts maintainer for inclusion in hardy.

I know the startup "boot screen" has interactivity support, however the shutdown boot screen I'm not so sure about - that may cause the system to appear to freeze when in fact it's running fsck.   If interactivity is available, it would be nice to have a press any key to skip fsck, for those times you do need the system off in a hurry - eg. a hardware change.

---

### Post by AusIV4 on 2007-11-09
Here's what I remembered, and it looks like they've cleaned it up quite a bit. Now I just hope they'll include it with Ubuntu or put it in the repositories for Hardy.

[url]
https://wiki.ubuntu.com/AutoFsck
[/url]

---

### Post by atlfalcons866 on 2007-11-13
You change the amount of boots for fsck to run if your using ext2/3 by doing

sudo tune2fs -c x /dev/sdax

Where x is the the number of boots to for fsck to run.

---

### Post by mkro on 2007-11-14
Fsck being forced on every n boots should be classified as a bug. It felt like a d*mn DoS attack: I needed to check my online bank before leaving for work today, but when I tried to boot my PC it said it had been 22 times since my last check, and ran fsck for me. There is NO option for skipping, ctrl-c did not work, there was nothing I could do.

I had to wait 15 minutes for it to finish (500 gig disk), and I missed my bus. :mad:

Even Windows 98 let me skip disk checks. This is beyond retarded.

---

### Post by jharbert on 2007-11-14
I second this idea.  There have been many times where I have wanted to boot quickly to check something and have been delayed by the fsck.  Being forced to wait for it to finish and having no means of killing it other than a cold shutdown (and it will still come back the next time you boot) is unacceptable.  Moving it to shutdown (or at least having a way to stop it) would be a great improvement.

---

### Post by ssam on 2007-11-15
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck) is working well for me. with a simpler GUI i'd like to see it included by default

---

### Post by slavik on 2007-11-15
When I am going to sleep at 2am and have to wake up in 5 hours for work, I'd like my machine off ... NOW! :)

Autofsck seems very nice :)

---

### Post by CrazyGuy123 on 2007-11-16
Autofsck needs a nicer question box by default.

My proposal would be:

-----------------------------------------------------------
                          Disk Check
-----------------------------------------------------------
A disk check will take about 20 minutes and is
recomended to keep your system running reliably.

Would you like to run disk check before shutdown?
                  --------                    -------- 
                 |  Yes  |                   |   No  |
                  --------                    -------- 
------------------------------------------------------------


The dialog box should default to "Yes" after 20 secs of inactivity, as it is presumed the computer has been left unattended.

---

### Post by smartboyathome on 2007-11-16
I remember reading another thread about this and someone said that it was not possible to run it on shutdown (though I don't remember why). Anyway, I would say just make it integrate better into Usplash so that it doesn't get rid of Usplash and ask if you want to run FSCK on this bootup. It should state that if you choose not to do it, it will be run on your next bootup.

---

### Post by AusIV4 on 2007-11-19
> **atlfalcons866 said:**
> You change the amount of boots for fsck to run if your using ext2/3 by doing

sudo tune2fs -c x /dev/sdax

Where x is the the number of boots to for fsck to run.

Having fsck run at every 50 or 100 boots makes it inconvenient less often, but it still happens and it's generally still a surprise. I'm looking for (and found, with AutoFsck) something that lets the user choose when to fsck on a case by case basis.

---

### Post by wieman01 on 2007-11-19
No idea if that's been mentioned but 'fsck' at shutdown can be an issue if you happen to own a laptop computer. If the PC runs out of juice, shuts down and is forced to run 'fsck', you might end up having serious troubles. No good idea.

---

### Post by Choad on 2007-11-20
this is a very good thread!

really need an option to skip it. it is so annoying when you just want to boot the damn thing

in my opinion, it should behave as follows: scheduled checks should be skippable with no warning, and just try again at the next boot. if skipped again, try again next time etc. etc. checks due to bad unmount (and therefor far more likely to inlude errors) should warn the user that it is a bad idea to skip this check, but still allow the user to skip it.

the whole thing should be nice and graphical too. dropping to a cli every 20 mounts or whatever it is is ugly and unprofessional looking

---

### Post by Choad on 2007-11-20
> **CrazyGuy123 said:**
> Autofsck needs a nicer question box by default.

My proposal would be:

-----------------------------------------------------------
                          Disk Check
-----------------------------------------------------------
A disk check will take about 20 minutes and is
recomended to keep your system running reliably.

Would you like to run disk check before shutdown?
                  --------                    -------- 
                 |  Yes  |                   |   No  |
                  --------                    -------- 
------------------------------------------------------------


The dialog box should default to "Yes" after 20 secs of inactivity, as it is presumed the computer has been left unattended.
you can't just say "20 minutes"

firstly, i expect that is way higher than the average. plus, the average means nothing. it's all to do with how big the partition is and how full it is and how fast the disk is.

---

### Post by mrbungle on 2007-11-22
i have also needed to use my computer in a hurry and then guess what pops up!!! at the worse possible times.  they need a option to skip.

---

### Post by CrazyGuy123 on 2007-11-23
My decision to give an estimate time was because it gives the user a rough idea. ie. is it going to take 1 sec, 1 min, 1 hour, 1 day or 1 week - that will impact their decision as to if it's a good idea to let it run.  Prehaps wording it as "a few minutes" would be better, given the large number of combinations of disk size etc. which will impact time.  Also I figured overestimating time is always better than underestimating - for example there's the case of "oh - I need to use my PC in half an hour for that video conference - oh, just enough time to run this check thinggy".

Either way, the message box on autofsck needs simplifying down to no more than ~40 words to keep is simple.

---

### Post by drumour on 2007-11-24
i still have to dual boot with Windows XP.  When  Windows inevitably crashes and I return to ubuntu I am forced to wait 20+ minutes while it checks a 300GB linux partition that was not in play when the windows system crashed.  It wont find any errors, I have tried pressing ctrl-c, ctrl-d, Break and Del keys, but nothing can stop fsck from trundling away. It is the most frustrating problem remaining with linux for me

---

### Post by wieman01 on 2007-11-24
> **drumour said:**
> i still have to dual boot with Windows XP.  When  Windows inevitably crashes and I return to ubuntu I am forced to wait 20+ minutes while it checks a 300GB linux partition that was not in play when the windows system crashed.  It wont find any errors, I have tried pressing ctrl-c, ctrl-d, Break and Del keys, but nothing can stop fsck from trundling away. It is the most frustrating problem remaining with linux for me
Don't press ctrl+c or something like that. It might break your Linux installation. I did that once and have learned the lesson the hard way.

---

### Post by drf_av on 2007-11-24
I remember that you can prevent fsck from running from fstab... even if it's not a great idea.

---

### Post by smartboyathome on 2007-11-24
Yes, it is VERY frustrating, especially when you have more than one ext filesystem (it wants to check all the ones that are due :mad:).

---

### Post by CrazyGuy123 on 2007-11-25
how about attacking the problem from a different angle.

Update fsck to make any keypress cancel the check - it could be as simple as a wrapper script that uses stdin from the keyboard and then kills the fsck process when it gets any keystrokes.

that IMO would be better than a sutdown dialog box.

---

### Post by tjagoda on 2007-11-25
I agree with fsck on shutdown instead of boot.  

I disagree with the pressing any key to skip comment - I think it would be a better idea to specify a key.  Or, alternatively, if the dialog was chosen, as long as a "fsck will start in x seconds if no key is pressed" and a yes/no option were there,  would be happy.

---

### Post by smartboyathome on 2007-11-26
tjagoda, if FSCK was on shutdown, and you had to turn off your computer (say it is a laptop with a very low power capacity) don't you think the laptop shutting down on it could harm your drive (which is probably the same reason why you can't kill it)? Say there WAS a corrupt portion, now you might not be able to boot.

Anyway, startup sounds better to me technically (you most likely won't have anything that will kill the process then), though I get where people are coming from, so I would agree that a way to skip it before it happens would be good.

---

### Post by CrazyGuy123 on 2007-11-26
I've just gone back to basics and done a bit of research, and I'm struggling to find the reason you need to fsck ext3 file systems at all.  Ext3 is journalled, journalled means all writes can be reverted or completed, with no full disk scan required.  Therefore, any hardware faliure or kernel panic won't cause inconsistant disk structures.

I've started a new thread over here ([http://ubuntuforums.org/showthread.php?p=3843018](http://ubuntuforums.org/showthread.php?p=3843018)) to ask file system experts direct.

---

### Post by teasum on 2007-11-26
> **smartboyathome said:**
> tjagoda, if FSCK was on shutdown, and you had to turn off your computer (say it is a laptop with a very low power capacity) don't you think the laptop shutting down on it could harm your drive (which is probably the same reason why you can't kill it)? Say there WAS a corrupt portion, now you might not be able to boot.

Couldn't the eventual solution, whether a script or whatever, simply detect if the laptop was running on AC, and only run fsck if and when plugged in?  That would seem logical and simple enough to implement.  Someone please correct me if I'm wrong, however.

---

### Post by tjagoda on 2007-11-26
> **teasum said:**
> Couldn't the eventual solution, whether a script or whatever, simply detect if the laptop was running on AC, and only run fsck if and when plugged in?  That would seem logical and simple enough to implement.  Someone please correct me if I'm wrong, however.

That actually sounds like a sort of power save in the long run, really.  That is something that's really annoying to me, sitting there watching my fsck chug away at the expense of my limited battery power.  Especially when I'm in a car or something and I dont have any sort of car adapter.

---

### Post by musther on 2007-12-20
Hi, I'm the author of AutoFsck.

I've been trying and trying to get developers to take notice of this issue, it's **a major usability issue** but doesn't seem to be taken seriously.

AutoFsck isn't perfect, but I think it's pretty good.  There's a petition collecting names at the bottom of:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

As far as I can tell, there is overwhelming user support, and thank you for it. :-)

---

### Post by 23meg on 2007-12-20
musther, what's up with [the blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/prompt-for-fsck-on-shutdown")? Did you talk to Scott and/or the rest of the TB people for approval? What's their take?

I don't think it's not being taken seriously, since it's mentioned among "future work" in an approved blueprint, [exit-strategy]("https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy").

---

### Post by musther on 2007-12-20
I've made requests to the ubuntu-desktop team, and others, for guidance (you can see at least one request on the blueprint page) - no replies.

The blueprint page looks fine, but it's all just content I've put there, I've not been able to get any feedback from the teams.

---

### Post by 23meg on 2007-12-20
You should talk to them on IRC (#ubuntu-devel) and/or post to ubuntu-devel-discuss about the spec then.

---

### Post by Vadi on 2007-12-20
The program fills an extremely useful need, and I find is completely stupid of whoever decided to force it at bootup. Like, not everybody here has a desktop, and never turns their computer off.

I already had to find another laptop for a presentation because fsck kicked in (-great- promotion of Ubuntu. Like, really.), and missed other things on countless occasions because of fsck.

While the dialog interface of autofsck isn't all that shiny, the program fills a *very* important, one might call it a need or a flaw, and seeing the blueprint get completely ignored for 7.10 and onto 8.04 is just frustrating.

---

### Post by musther on 2007-12-20
Vadi - that's exactly how I feel.

I've (re)started the discussion on the ubuntu-devel-discuss list, but that list can discuss, but not really make decisions.  I wish I knew more about the decision making process.  

I've not had a two way conversation with any developers about this issue, I feel very frustrated.  It seems completely stagnant.

---

### Post by 23meg on 2007-12-20
[QUOTE=musther]I've (re)started the discussion on the ubuntu-devel-discuss list, but that list can discuss, but not really make decisions. [/QUOTE]

It can. Developers (including TB members) do frequent that list, though more sparsely than ubuntu-devel, to which you may want to post later if the discussion doesn't yield results. But instead of that I'd recommend just going to #ubuntu-devel on IRC since you want to have a direct conversation.

[QUOTE=musther]I wish I knew more about the decision making process. [/QUOTE]

These should help:

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)
[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)
[https://wiki.ubuntu.com/SpecLifeCycle](https://wiki.ubuntu.com/SpecLifeCycle)

---

### Post by musther on 2007-12-20
Thanks for the info 23meg.  :-)

---

### Post by vnkatesh on 2007-12-24
Totally support the AutoFsck.

Good thing the developer himself is here.

---

### Post by smartboyathome on 2007-12-24
By the way, I don't know if this is included with Ubuntu, but while using Arch I found out the command reboot has an option to do a reboot without doing a check. Maybe this could be used for the shutdown?

---

### Post by Vadi on 2007-12-24
We already have the solution,,, the problem is actually getting it in.

---

### Post by Rufe0 on 2007-12-29
To get round the whole time issue some people seem to be stuck on why doesn't it A) make an educated guess considering total size and amount of data on the disc or B) just remember how long the previous scan(s) took?

---

### Post by musther on 2007-12-29
People don't like the fact that it takes a long time, how does knowing exactly (or approximately) how long that will be help?

---

### Post by Vadi on 2007-12-30
Is there any progress on the blueprint?

---

### Post by musther on 2007-12-30
No, sorry.  What can I say.

---

### Post by 23meg on 2007-12-31
> **Vadi]We already have the solution,,, the problem is actually getting it in.[/QUOTE]

We have here a *possible* solution, not necessarily the panacea said:**
> Is there any progress on the blueprint?

Depends on what you'd call "progress". In response to mushter's post to the list, Matthew Garrett proposed removing the boot fsck entirely. Others presented different views. The discussion seems to be continuing.

---

### Post by musther on 2007-12-31
> **23meg said:**
> We have here a *possible* solution, not necessarily the panacea; there can be more feasible solutions. The problem is actually deciding on the most feasible one and going ahead with it.

I agree entirely, we have a possible solution, but we certainly have the desire for one.  AutoFsck is certainly not the best solution, well, not in its current form - having said that, what it achieves could definitely be the way to go.  

> Depends on what you'd call "progress". In response to mushter's post to the list, Matthew Garrett proposed removing the boot fsck entirely. Others presented different views. The discussion seems to be continuing.

Well maybe, of course it is the holiday season :-).

I contacted some of the team who worked on ext3 (and ext4), and (as I posted to the list) they said that checks are definitely necessary.  

From Mingming Cao:
> Periodically fsck ext3 is still needed, even if ext3 is a journalled fs.
kernel code vm/fs could be buggy, or disks IO errors, which cause
filesystem metadata corrupted silently, this can't be detected by simply
replaying the journal log.

From Andrew Morton (do you need to run fsck?):
> Theoretically: no.

Practically: yes.  There are software bugs and hardware bugs and
things can go wrong on-disk.  You want to catch them early.

Personally I disable the auto-fsck thing and I'll run fsck manually
once or twice a year, when the time suits me.

---

### Post by Vadi on 2007-12-31
I just really hope we get *something* in.

---

### Post by chrisccoulson on 2007-12-31
> **musther said:**
> Hi, I'm the author of AutoFsck.

I've been trying and trying to get developers to take notice of this issue, it's **a major usability issue** but doesn't seem to be taken seriously.

AutoFsck isn't perfect, but I think it's pretty good.  There's a petition collecting names at the bottom of:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

As far as I can tell, there is overwhelming user support, and thank you for it. :-)

I've just tried using AutoFsck on my Gutsy machine. I don't believe it currently supports /dev/mapper devices though, so it doesn't work for people using DMRAID or Linux software RAID. I think it would be a simple fix to get it working though. When you do a grep on lines 312 and 326, I've simply added an extra pattern '--regexp="/dev/mapper/nv"', and this matches RAID devices on my NVIDIA chipset. Theoretically, you could add extra patterns for different chipsets and for Linux software RAID too.

I don't know if it works completely yet, as none of my volumes are close to needing a check yet, but I'll let you know what happens.

---

### Post by musther on 2007-12-31
Thanks for the insight, please contact me directly when you find out if it works (musther@gmail.com) as this will be helpful.  

Do we need to try to find all the patters and use 

--regexp="/dev/mapper/nv"

Could we not use the following?

--regexp="/dev/mapper/"

My problem is testing, I don't use RAID, so does using the above expression catch your devices (without picking up things we don't want it to)?

---

### Post by henriquemaia on 2008-01-06
This thread is really interesting. Any updates on this?

---

### Post by musther on 2008-01-06
Well, the discussion on ubuntu-dev-discuss seemed to show that everyone thinks something needs to be done.  There were other suggestions about what form it should take, when the user should be prompted etc, but basically most people would approve of AutoFsck functionality (although not provided by AutoFsck*).
The conversation on that mailing list seems to be over now.

*This is as much my opinion as anybody else's.  AutoFsck is not reliable enough in itself, something else which provided its functionality would be a must for inclusion.  For example, I get some people emailing me because after installing AutoFsck, they're prompted every shutdown, investigation shows that the mount count of one of their partitions is 'stuck' above the max mount count.  Of course the mount count should be reset when fsck is run, but for some reason on these 'stuck' ones it's not.  The solution generally comes in two forms:  Changing the frequency of the checks through the AutoFsck GUI sometimes fixes it (this changes the max mount count) - if not, you have to use tune2fs to reset the mount count of the offending partition manually, afterwards it seems to behave normally.

---

### Post by articpenguin on 2008-01-06
JFS is a filesystem i know that dosent force fsck periodically like ext3 does. But JFS does have its drawbacks though.

---

### Post by musther on 2008-01-06
You're right, JFS doesn't force fsck, but that's not a good thing.  As the devs said, the periodic fsck is to catch errors which cannot be caught by the journal, therefore JFS is at risk from those errors too.

---

### Post by jharbert on 2008-01-07
I'm glad to see something done with this problem (it can be quite a headache to have to do a scan when running on battery).  How about just providing an option simply to cancel the check or put a prompt giving the option to put it off.  The prompt could look something like this:

A check needs to be performed on filesystem [insert filesystem name] in order to ensure there are no critical errors which may cause corruption and/or loss of data.  This may take a while depending on the size of your drive [maybe give an estimate time - I'm not sure if that is possible or not].  Would you like to run this check now or wait till next time?

Provide a timeout of say 10 seconds and then select yes for those people who leave the computer alone while their computer boots.  If the user says no, they will be prompted again on the next boot to run the check.  If they say yes fsck will be run.  That way the disk is still checked occasionally, and people who don't have time for the check can skip it until later.

---

### Post by Vadi on 2008-01-07
I would still like to see a way of stopping the check though. I can see myself looking away for a bit while in a hurry and missing the option.

---

### Post by barbedsaber on 2008-01-09
what about if it was still at startup but you could cancell it and, you could click an icon to do it manually once you had logged in, or use the terminal to do it at shutdown when you have the time eg finished work, will leave computer to fshk or whatever and shutdown when it finishes.

---

### Post by smartboyathome on 2008-01-09
You cant do it while you are logged in since the filesystem has to be unmounted.

---

### Post by Lster on 2008-01-10
Nice reading guys and, like others, I think something must be done! Personally I think just allowing it to be skipped is good enough - if thats possible?

---

### Post by qix on 2008-01-10
I just want to express my support for this project. The forced check on boot is the MOST annoying (and unprofessional) thing I've found in ANY OS, not only Ubuntu/Linux.

This is _annoying_. When I use my computer, I want to be in control. I want the OS to be made for me, and to support me. I don't want an OS that hinders my work and interaction with the computer. Afterall the goal of a PC and an OS is to help the user, not to support itself.

---

### Post by musther on 2008-01-25
I'm looking for a developer to help get AutoFsck into a state which is appropriate for inclusion in Ubuntu, see this thread for details:
[http://ubuntuforums.org/showthread.php?t=675639](http://ubuntuforums.org/showthread.php?t=675639)

---

### Post by 23meg on 2008-01-25
Is "a state which is appropriate for inclusion in Ubuntu" defined? I suggest you sort that out (or whether this or another app is really needed at all) with the Ubuntu people before going ahead.

---

### Post by musther on 2008-01-26
No, it's not defined, and that's why I'm hoping to find somebody with some experience in the area.  For example, I know it has to translatable for languages other than English, but I have no idea how this is accomplished.

As for whether it is needed, there's been overwhelming support, I really don't think holding the users computer hostage for 10, 20, 30 minutes during boot is acceptable...  ever  -  and I haven't seen any compelling reason why it is.

---

### Post by 23meg on 2008-01-26
I'm not talking about whether something needs to be done about the fsck problem. What I meant by "whether this or another app is really needed at all" was: is *an application* really needed to solve the problem? If the real solution is to permanently put the fsck into the shutdown sequence, or have it in the startup but make it skippable, or simply get rid of it altogether, then an added application will be a stopgap solution. 

If a policy problem can be solved properly, in the right place, once and for all, there's no use in nagging users about it. It's better to just solve it and make things just work the way they have to work.

---

### Post by musther on 2008-01-26
Ah yes, I agree with that.  A forum user (cesium62) suggested this:

> How about a read-only mode of fsck that can be run in the background to check for problems on the disk? If no problems are found, update the counter. If problems are found, crash the system and run the 20 minute fsck on a writeable disk.

Are you worried that writes to the disk will interfere with the read-only fsck? Build a data logging area where writes can be posted for later flushing to the correct location. If the area fills up, stop the fsck, flush the logging area, and restart the fsck later when the system looks idle.

Seems like a pretty much ideal solution to me, of course it would be quite a job.

You're right though, that wrapping fsck in another layer isn't as good as solving the problem at the root.

---

### Post by 23meg on 2008-01-27
> If problems are found, crash the system

?

[QUOTE=mushter]You're right though, that wrapping fsck in another layer isn't as good as solving the problem at the root.[/QUOTE]

Good to know that we agree. This is why, instead of working to improve AutoFsck to reach a yet undefined state, you should prod people to reach a consensus on what exactly should be done on the fsck problem and when, as soon as possible.

---

### Post by articpenguin on 2008-01-28
ext3 has the longest fsck out of all the filesystems. ext4 is faster because unallocated block groups and sections of the inode table are marked as such.

---

### Post by hellion0 on 2008-02-05
> **wieman01 said:**
> No idea if that's been mentioned but 'fsck' at shutdown can be an issue if you happen to own a laptop computer. If the PC runs out of juice, shuts down and is forced to run 'fsck', you might end up having serious troubles. No good idea.Well, isn't there a way, perhaps writing a  script that can run to determine if the laptop's on battery power, and postpone the check until the next shutdown if that's the case?

If there is, it'd solve that problem, and regardless, I'm for this idea.

---

### Post by Trail on 2008-02-05
Nice idea. I agree.

---

### Post by musther on 2008-02-05
> **hellion0 said:**
> Well, isn't there a way, perhaps writing a  script that can run to determine if the laptop's on battery power, and postpone the check until the next shutdown if that's the case?

Yes, I'm sure it is possible to do that, I haven't done it with AutoFsck, but then again the user has the choice to say no, and if they don't say anything it'll timeout and shut down.  This seems like the simple way to solve the battery issue.

In fact the reason I wrote in the timeout was some guy contacted me and said he had closed his laptop lid and not noticed the AutoFsck dialogue, it had then spent over an hour running in the bag with him on his journey home, and was almost out of power, all not good.

---

### Post by musther on 2008-02-08
I was interested in knowing how many people were downloading AutoFsck, and also wanted to expand on the wiki page, so I moved the file hosting to sourceforge.net, and put a wiki on wikispot.

If anybody is interested you can see the AutoFsck dowload stats at:
[http://sourceforge.net/project/stats/detail.php?group_id=216366&ugn=autofsck&mode=week&type=prdownload](http://sourceforge.net/project/stats/detail.php?group_id=216366&ugn=autofsck&mode=week&type=prdownload)

and the AutoFsck wiki is at:
[www.autofsck.wikispot.org](www.autofsck.wikispot.org)

---

### Post by Vadi on 2008-02-08
Yeah, the timer is very good since for a long while I had my laptop do a -really- annoying beep for a long while.

... turns out it was AutoFsck wanting me to look at it. I usually shut the laptop down, & close the lid right away. Now I know!

---

### Post by plun on 2008-02-08
> **musther said:**
> 

and the AutoFsck wiki is at:
[www.autofsck.wikispot.org](www.autofsck.wikispot.org)

Thanks,  testing  :)

Running Hardy and debconf halts on beep install and root permission.
I don't know if its the same with Gutsy ? Nevertheless confusing for a lot of users and also to find the terminal window.

fsck halts during startups are really annoying....

---

### Post by musther on 2008-02-08
I haven't done any testing of AutoFsck on Hardy, but I will nearer the time - rest assured it will be ready before the 8.04 release.

---

### Post by MadEgg on 2009-02-22
I'm bumping an apparently quite old thread, but this issue still bugs me on 8.10. 

While it is nice that the fsck on boot can be skipped, the only thing this results in is that the next time it is asked again. I see the need for the check happening and therefore this is simply not a solution because this leads to cancelling the check each time. I would need to reboot it after I am done with the computer but of course I forget.

AutoFSCK's behaviour of asking at shutdown is way better, because this also allows to reboot te computer to check the disk and then shutdown without any further interference.

The thing is, AutoFSCK does not seem to work on Intrepid anymore. I can install it, but I never get any check warnings during shutdown while the normal ones do appear during boot boot. So, unlike in Hardy, in Intrepid this solution actually seems unsolvable...

---

### Post by cariboo on 2009-03-07
This is really a none issue with ext4. Fsck is so fast now that it only adds a couple of seconds for a 5Gb root partition to be checked. I myself prefer fsck to run every 26 boots. My data is important to me, on top of having at least 2 backups I want my partitions checked at regular intervals. 

Jim

---

### Post by gnomeuser on 2009-03-07
Isn't this the wrong way to attack the problem. Instead of moving the delay from boot to shutdown we should eliminate it. There is a a solution that will let us do that, online fsck.

We need the filesystem to be capable for running a filesystem check while it is up. This isn't science fiction, FreeBSD has been doing this since FreeBSD 5. It's not easy and it is not without downsides but it can be done. The biggest downside is probably that till such a time as the inline fsck is activated, any unclaimed space is considered lost, also it would mean incuring a performance hit while the check is running.

However this would also allow us to schedule regular fsck runs for machines that are constantly up which might be useful, along with DeviceKit-disks it could report problems to the user and early warning signs of hardware decay.

---

