---
title: "Downgrade Function"
date: 2007-10-26
forum: Ubuntu Brainstorm
---

### Post by flameproof on 2007-10-26
For the Developer: Design a DOWNGRADE function for new versions!

It's bad enough to get stuck with 7.10 with no easy roll back options.

---

### Post by elanthis on 2007-10-26
No.

---

### Post by hexion on 2007-10-26
> **elanthis said:**
> No.

I'm sure you can do better than that... any arguments you don't think it's a good idea?


[quote=flameproof] 		For the Developer: Design a DOWNGRADE function for new versions![/quote]

Do you reffer on a complete downgrade from a release to the previous? You can do that with apt-get. Just editing /etc/apt/preferences and giving 1001 to the repositories of the previous version.

About your request... I don't believe that's needed for the general user. Just counted situations.. And developing something for those counted cases is a waste of effort IMHO.

---

### Post by aidanr on 2007-10-26
The easy roll back option is to **_backup_** before you make any major changes to your system, backing up is something you should do anyway.

---

### Post by madmetal on 2007-10-26
> **aidanr said:**
> The easy roll back option is to **_backup_** before you make any major changes to your system, backing up is something you should do anyway.

i agree and that's all...
:KS

---

### Post by flameproof on 2007-10-26
> **hexion said:**
> 
Do you reffer on a complete downgrade from a release to the previous? You can do that with apt-get. Just editing /etc/apt/preferences and giving 1001 to the repositories of the previous version.


Can you explain that a bit more in detail? What I really don't want is to format my HDD for no reason.

> The easy roll back option is to backup before you make any major changes to your system, backing up is something you should do anyway.

Backup on the same HDD is no use if the HDD gets formated. And no, I don't bother about partitions. I just want to use the PC, that's it. XP can do that too.

---

### Post by Thunar on 2007-10-27
I have to agree... an easy way to get back would be nice. When you install Windows XP (yes I said it) it lets you uninstall it easily if it didn't work out for you, and after spending hours upon hours trying to get 7.10 to work (it's 3am and I am posting this on my windows machine) I wish I had never upgraded. Feisty worked perfectly, Gutsy Gibbon so far is a peice I wish I had never messed with. 

FYI, backing up files, which I did, wont give me those wasted hours of my life back :lolflag:

Now to spend days downgrading and getting all my settings in feisty back the way they were... I guess insted of being Gutsy I was just being foolhardy....

---

### Post by flameproof on 2007-10-27
I can not understand why anyone would be against a downgrade function. If you don't like it don't use it. That is how OPTIONS work, they are OPTIONS as the name implies.

---

### Post by hexion on 2007-10-27
> **flameproof said:**
> I can not understand why anyone would be against a downgrade function. If you don't like it don't use it. That is how OPTIONS work, they are OPTIONS as the name implies.

They are suggesting you what to do in order to avoid this situation in the future. I myself do a backup each 3 months, and of course I do one before each upgrade.

About the alternative I told you, you have to modify again your sources.lst changing "gutsy" for "feisty".
But the versions of your packages will be newer than the ones in the repos, so you have to create a /etc/apt/preferences file. In that file, you must asign a higher priority to feisty repositories.
To get more info on how to do it, type "man apt_preferences" in console.

After that, apt-get update && apt-get dist-upgrade should do the trick. Anyway, I', talking about theory here... I haven't tried that ever so do it at your own risk.

---

### Post by Hobbsee on 2007-10-27
Out of the billions of things that people want to implement, i'd say that the number of people who would benefit from this, vs the effort to do it (and the high potential of breakage), would put this fairly close to the bottom of the pile.

Just no.

Backups are good, people!

---

### Post by zeDuffMan on 2007-10-27
Or if you don't want to backup, get a working system set up and don't update it.

---

### Post by Auria on 2007-10-27
The devs spend enough time trying to get the updates to work correctly, if they have to spend time on making downgrade work, both updgrate and downgrade would end up broken.

---

### Post by scorpion-kde on 2007-10-27
It would be nice if there was a simple snapshotting system in place.  That way, you could take a snapshot, do an upgrade, then revert to the snapshot if it didn't work out.  If you have a separate partition for your / filesystem, it would probably be fairly easy to do with LVM.

---

### Post by Thunar on 2007-10-28
> **scorpion-kde said:**
> It would be nice if there was a simple snapshotting system in place.  That way, you could take a snapshot, do an upgrade, then revert to the snapshot if it didn't work out.  If you have a separate partition for your / filesystem, it would probably be fairly easy to do with LVM.

Exactly, every major operating system has some sort of option like that, except Linux. When it breaks, it's broken. If the upgrade doesn't work, as from what I've been reading on these very forums it often doesn't, it's 'too bad, you should've backed up'

btw, back up to disc? And back up what? I always back up important files, but this won't change the fact that every time you do a clean install, which seems to be the only way to go for each distro of Ubuntu, you have to spend several hours setting up your preferences, look, feel, Internet, Network, packages, background images, bookmarks, remembered passwords, parameters, updates and upgrades all over again. 

So I guess we'll have to do this every 6 months, eh? Or not get to play with the new toys! :lolflag:

As for the amount of people it can benefit, it may be far more than you think, and, unless I am mistaken, these forums are our chance to voice our opinions and to brainstorm ideas that we think may improve the overall experience of Ubuntu Linux. Developers spent their time making it, but we've spent our time using it and trying, sometimes very hard, to incorporate it into our everyday lives. But hey, if no one wants to do it, no one wants to do it. We are just the people who use it, not the people who make it, so what  do we know?

---

### Post by aidanr on 2007-10-28
> **Thunar said:**
> btw, back up to disc? And back up what? I always back up important files, but this won't change the fact that every time you do a clean install, which seems to be the only way to go for each distro of Ubuntu, you have to spend several hours setting up your preferences, look, feel, Internet, Network, packages, background images, bookmarks, remembered passwords, parameters, updates and upgrades all over again.
[Partimage]("http://www.partimage.org/Main_Page") to a external hd, dvd's or nas

---

### Post by 23meg on 2007-10-28
[QUOTE=Thunar]
btw, back up to disc? And back up what? I always back up important files, but this won't change the fact that every time you do a clean install, which seems to be the only way to go for each distro of Ubuntu, you have to spend several hours setting up your preferences, look, feel, Internet, Network, packages, background images, bookmarks, remembered passwords, parameters, updates and upgrades all over again.[/QUOTE]

Just back up your home partition or folder.

---

### Post by Thunar on 2007-10-28
> **aidanr said:**
> [Partimage]("http://www.partimage.org/Main_Page") to a external hd, dvd's or nas

Although that sound like a reasonable alternative it has two flaws in my case, and perhaps others as well: I have no external harddrive, and I have no DVD burner installed on my computer. And even if I did have a DVD burner, it would have to be a very small partition to fit on a 4.5 GB DVD, unless that program does volumes, but then you have a library of DVDs. Plus it seems to me that copying an entire partition back on to a harddrive can't be as easy as you are making it sound, but maybe it is... Still though, no DVD Burner and still no external HDD, therefor no way to back up an entire partition.

The bottom line is that I am just trying to make a point: I've seen lots of talk from the Linux camp about how it is easier to install and use than its mainstream competitors, and though it has made leaps and strides it's the little things that sometimes make a big difference, and Linux often falls short. 

Don't get me wrong: I appreciate all of the hard work the developers have put into Linux, specifically Ubuntu because that's what I use. I just started using it this year ( I went from Xubuntu 7.04, to Ubuntu 7.04 and now Ubuntu 7.10 in that time) and to be honest I am quite impressed. But going into your terminal and typing all kinds of crazy code to do things that come standard on other OS is not what I would call 'intuitive' or 'user friendly', and right now, with the release of Vista, is the perfect time for Linux to show it's stuff and win that jaded PC crowd over. 

I'll be the first to say that Linux rocks, but I'll also be the first to say that it has a long way to go, and the devs shouldn't write people off so quickly, because people are what this is all about. What's the point of developing such complex and functional software if no one will use it?

Anyways, end rant. 

I'm gonna go back my files up now, hahaha :lolflag:

---

### Post by rahulthewall3000 on 2007-10-28
I will give you an easy solution for this, just mount your home folder on a separate partition when you install Linux(any distro). That way, if the updates break your computer, you could happily and merrily do a fresh install retaining all your data, preferences, account settings, and everything because that would remain as it is on your home folder.

Cheers

---

### Post by chrismine on 2007-10-28
> **scorpion-kde said:**
> It would be nice if there was a simple snapshotting system in place.  That way, you could take a snapshot, do an upgrade, then revert to the snapshot if it didn't work out.  If you have a separate partition for your / filesystem, it would probably be fairly easy to do with LVM.

Don't know - but maybe TimeVault can do this?

---

### Post by ronacc on 2007-10-28
a lot depends on how complex your "move" is . Everything I need can be moved on a thumb drive , my persistant data I backup to dvd regularly. For me a rollback feature would be a waste of disk space. I always install new distros to their own drive having had a couple of bad experiences with rouge installers "eating" other partitions on the same drive and a fresh install automaticly cleans out all the crap you never got around to deleting ( in my case usualy more than what I want to keep).

---

### Post by DizzyTech on 2007-10-28
You guys are not understanding this.  You think its as simple as... "well, just do it!"  It's hardly that.  The fundamental design of APT is to install and update packages.  Downgrading a whole distribution would break hundreds of dependencies, not to mention accidentally uninstalling your core system.

---

### Post by flameproof on 2007-10-28
> **23meg said:**
> Just back up your home partition or folder.

Is everything in the HOME directory? How about the Thunderbird emails?

How about the SCIM settings and Turboprint?

If that's the only directory to update I would go with that.

---

### Post by ronacc on 2007-10-28
then backup your entire system . thats what a "downgrade (rollback)" function would have to do in essence . in order to ensure a smooth downgrade without breakage.

---

### Post by 23meg on 2007-10-28
> **flameproof said:**
> Is everything in the HOME directory? How about the Thunderbird emails?

How about the SCIM settings and Turboprint?

If that's the only directory to update I would go with that.

All per user data and settings should be in the home directory. Thunderbird emails certainly are; not sure about SCIM and Turboprint. And as has been said, if you just make a permanent home partition, you don't have to worry about moving things around.

---

### Post by Thunar on 2007-10-28
> **23meg said:**
> All per user data and settings should be in the home directory. Thunderbird emails certainly are; not sure about SCIM and Turboprint. And as has been said, if you just make a permanent home partition, you don't have to worry about moving things around.

Let's say you made a permanent home partition, when you upgrade, would it not also upgrade the settings, etc of the home partition as well? 

> **DizzyTech said:**
> You guys are not understanding this.  You think its as simple as... "well, just do it!"  It's hardly that.  The fundamental design of APT is to install and update packages.  Downgrading a whole distribution would break hundreds of dependencies, not to mention accidentally uninstalling your core system.

No one ever said it would be simple, at least I never did. All I was saying was that other OS have such features, and Linux doesn't. Besides, my upgrade from Feisty to Gutsy broke several dependencies to the point to where I had to do a fresh install anyway, losing all of my info, settings & programs. So it would seem the APT is not designed for updates or downgrades to or from different releases.

> **ronacc said:**
> then backup your entire system . thats what a "downgrade (rollback)" function would have to do in essence . in order to ensure a smooth downgrade without breakage.

The WIndows System Restore simply takes a snapshot of the system settings, not the entire contents, and it works smoothly enough to recover from all manner of breakage. Not to say that it would work that way for Linux, but maybe cloning the entire disk may not be necessary, even if it's the best way.

---

### Post by dead_end on 2007-10-28
Downgrading is not quite as simple as proponents of this would make it appear. Yes  Windows does allow you to *uninstall* but it does not allow you to downgrade. Downgrading an Operating system is more then just replacing one package with an earlier version. In Gutsy alone, during upgrade, the upgrader program told me that it was going to remove about 10 or 12 programs because they were no longer needed by the OS, and were no longer supported in main. It also needed to install about 300 programs and upgraded about 900.

The best way to downgrade and keep all files is to mirror your hard drives to removable drives before doing any thing that you just might regret, including upgrading critical parts of you box. And I'm not talking about just your home directory, but the whole drive or if you have split your OS onto multiple drives then  copy each drive individually onto a separate removable drives.  

Also I have also found that it is usually a very good idea to wait a month or so after release before you upgrade. That way many of the bugs that pop up will have a chance to be dealt with. Not all, but many.

Linux and Unix have both remained far superior to windows primarially because of Linux/unix's tradition of making one program do one thing, and one thing only, but be very good at it, and then stringing a bunch of those programs together.

---

### Post by ronacc on 2007-10-28
The WIndows System Restore simply takes a snapshot of the system settings, not the entire contents, and it works smoothly enough to recover from all manner of breakage. Not to say that it would work that way for Linux, but maybe cloning the entire disk may not be necessary, even if it's the best way.[/QUOTE]

windows restore and the rollback function from say xp to 98 are two entirely different things, I believe it does "clone" (hide) the original install. if it is even possible to do that I'm not sure I left long before xp.

---

### Post by Thunar on 2007-10-28
> **dead_end said:**
> Windows does allow you to *uninstall* but it does not allow you to downgrade. 

That's not entirely true... When you first install XP, it keeps your old install in your add/remove programs, where you can then go back and recover your 98, 2000, ME install should you need to. If you decide you no longer need it, you can uninstall the OS backup, therefor gaining your HD space back. 

And I will say it again: I don't pretend this would be easy or simple, I am just saying other OS have it, Linux doesn't.

> **ronacc said:**
> windows restore and the rollback function from say xp to 98 are two entirely different things, I believe it does "clone" (hide) the original install. if it is even possible to do that I'm not sure I left long before xp.

You are absolutely right, they are different. XP has both options, downgrade AND restore, while Linux has neither.

I have read lots of Linux articles where the Linux camp complains that the mainstream OS tend to ignore the great ideas and progress made by the very capable Linux developers. The odd thing is, I find that the Linux camp does the same thing. People who are fully in the Linux camp seem to assume that Linux is superior to every other OS in every way and therefore lend a deaf ear to the progress and ideas offered by the closed-source developers.

I use Ubuntu and Windows XP at home (and no, not dual boot, Ubuntu has it's own PC), and OS X at work, so I get to see every day what all three of these operating systems have to offer, and can tell you with all certainty that NONE of them have ANY of the others completely beat. They ALL have advantages and disadvantages. 

Maybe I'm wrong, but I though that at least part of the idea behind these forums was to allow people who use the software to voice their opinions about things they would like to see in Linux. It's not a demand, it's just an idea. 

Hi! I have an idea!

> **elanthis said:**
> No.

> **Hobbsee said:**
> Just no.

I am seeing some closed-minds in open-source. Isn't it ironic? Don't you think?

---

### Post by 23meg on 2007-10-28
[QUOTE=Thunar]Let's say you made a permanent home partition, when you upgrade, would it not also upgrade the settings, etc of the home partition as well?[/QUOTE]

I'm talking about fresh installs. If you **can't afford to** or **don't want to** or **don't have the skills to** have to deal with possible upgrade headaches, this can help.

[QUOTE=Thunar]Maybe I'm wrong, but I though that at least part of the idea behind these forums was to allow people who use the software to voice their opinions about things they would like to see in Linux. It's not a demand, it's just an idea.[/QUOTE]

Sure, and nobody is denying your right to voice your idea.

[QUOTE=Thunar]I am seeing some closed-minds in open-source. Isn't it ironic? Don't you think?[/QUOTE]

No, you're seeing people (who are well qualified to comment on the matter, by the way) state their position on a proposal. It happens very often.

---

### Post by Thunar on 2007-10-28
> **23meg said:**
> I'm talking about fresh installs. If you **can't afford to** or **don't want to** or **don't have the skills to** have to deal with possible upgrade headaches, this can help.

I see your point, but someone who doesn't have the "skills" to deal with upgrade headaches may also not have the "skills" to partition their drive on a fresh install much less an old one...

> **23meg said:**
> No, you're seeing people (who are well qualified to comment on the matter, by the way) state their position on a proposal. It happens very often.

Ok ok, granted, bad attempt at being funny, but when someone's only position on the matter is "NO" it just makes you feel like the discussion was closed before it was ever opened. (for the record: I have the highest respect for the developers who spend so much of their time making Ubuntu the best of the best Linux, in my opinion)

Linux's greatest strength is it's wealth of options and vibrant community, and I was just surprised to see so much vehement resistance to this proposal. It's not a bad idea, it's not even a new idea. It's tried and true, and could be a potential boon to Linux newcomers who often break their installations, as well as Linux old-timers who often break their installations on purpose. :)

remember, I didn't even start this thread, but I happened upon it accidentally (after being highly frustrated with my Gutsy upgrade and searching the forums for just such a possibility) and felt it needed a case to be made for it.

---

### Post by ronacc on 2007-10-28
certainly no one is saying not to post your ideas or not to voice your opinion . however when you do post in the forums expect to get both agreeing and dissenting opinions.

---

### Post by 23meg on 2007-10-28
[QUOTE=Thunar]I see your point, but someone who doesn't have the "skills" to deal with upgrade headaches may also not have the "skills" to partition their drive on a fresh install much less an old one...
[/QUOTE]

True, hence my saying "if". It's not an excuse for upgrades not working as supposed anyway. 


[QUOTE=Thunar]I was just surprised to see so much vehement resistance to this proposal. It's not a bad idea, it's not even a new idea. It's tried and true, and could be a potential boon to Linux newcomers who often break their installations, as well as Linux old-timers who often break their installations on purpose.[/QUOTE]

I don't think anyone is saying it would be bad to have a downgradable system; people are saying it's tough to implement and support, and that the potential gain may not justify the effort, at least now. You shouldn't be surprised to get this kind of feedback.

---

### Post by Thunar on 2007-10-28
> **23meg said:**
> I don't think anyone is saying it would be bad to have a downgradable system; people are saying it's tough to implement and support, and that the potential gain may not justify the effort, at least now. You shouldn't be surprised to get this kind of feedback.

Yeah, I guess it probably would cause more headaches than it's worth, unfortunately. Heck, for all I know, there could be some savvy programmer out there working on it right now! :)

if only I knew more about developing.... *sigh*

(I would probably be saying the same thing: NO, FORGETTABOUTIT!)

The bigger the community gets, the better the software gets.

---

### Post by crush304 on 2007-10-28
[http://https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

with tar or dd you should be able to backup your entire system and restore if the upgrade fails

---

### Post by ronacc on 2007-10-28
> **Thunar said:**
> I see your point, but someone who doesn't have the "skills" to deal with upgrade headaches may also not have the "skills" to partition their drive on a fresh install much less an old one...


anyone who dosen't have the "skills" to partition with gparted may be beyond help . I will admit that the installer could do a better job of preserving existing installs.

---

### Post by thtrgremlin on 2007-10-28
As if this flame needed any more stomping I'll just share from personal experience that jumping into alpha is a BAD IDEA. And the point everyone is trying to make is that the only people who would benefit from this feature is those that want to play sysadmin without knowing the kind of damage they can cause. Destroying your computer / install beyond repair is all part of the learning curve to becoming a linux guru, and likely a right of passage. 

It would be unfair to take that away from people.

---

### Post by hexion on 2007-10-28
I've got an idea around this issue...
Probably it will go nowhere (I suppose I think so because I didn't see any of the good ideas in this forum been developed) but there it goes anyway:

- The problem is relative to bad upgrades, or releases with some kind of lack that the previous release didn't have for a particular user.

- The solution is to go back to the system before upgrading.

- Modifying apt-get to be able to do that is insane. Dependency problems, downgrading config files, huge developing effort..... solution discarted.

- Manual backing up / restoring. Good solution but Joe users don't tend to do that kind of things usually. Also, we need an easy way for the user to restore a system that he might not be able to access to.



*** MY IDEA ***

To develop a pre-installing back-up system.
When a user inserts the LiveCD and double-click the install icon, a dialog would appear informing of the choice to do a backup to a file (or external device).
If the answer is affirmative, a simple GUI (to implement) will show with these options:
- Action (Backup / Restore)
- Type (Full / Only home)
- Exceptions (this would open a folder-tree view and allows to select folders to be ignored)
- Compression (High <slowest>, Normal, Low <largest>)
- Source/Destination (File / Burner)

I don't think I have to explain what would happen after that...
After the backup is done, the install asistant would start.


Now, in the case something goes wrong (imagine a disaster case, even the X doesn't load) and the user doesn't have the skills/time/whatever to try to solve himself:
- Inserts the LiveCD and reboots.
- When the system is started (the live session), starts the "backing up/restoring utility".
- Restores from the previously made backup.


*** PROBLEMS
I don't think a utility like this would be very difficult to be developed, but there are some issues:

- If the LiveCD is inserted, how could the application burn the back-up into a DVD? Could the LiveCD be extracted for a while?

- The user should be warned about where to save the backup file... of course not in the same partition where the system is going to be installed.



What do you think?

---

### Post by thtrgremlin on 2007-10-28
backup utilities do exist on the liveCD/DVD, not to mention your computer before you put in the install disk. While I can totally understand where you are coming from, backups should be second nature to people, and if there was a reminder every step of the way to backup every time it thinks you should, that would get annoying really quick. Additionally, I think the general direction with the installer is to have fewer menus / options / choices during the install process such that the choices are only those that will be necessary with every install.

---

### Post by Thunar on 2007-10-29
> **crush304 said:**
> [http://https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

with tar or dd you should be able to backup your entire system and restore if the upgrade fails

good to know :)

> **ronacc said:**
> anyone who dosen't have the "skills" to partition with gparted may be beyond help . I will admit that the installer could do a better job of preserving existing installs.

I'm just about the only one where I work that knows how to attach a file to an email, and everyone there uses computers. Let's face it, there are a lot of computer illiterate people out there who use computers everyday (mostly for games, Myspace or chat, but what the hey), and let's face it, this is part of the Linux target audience these days. I've seen more than a few articles where Linux is touted as a smart choice for schools, businesses and the like. And it's true, for many reasons. I don't think anyone would be worse off than they are with the Macs at my work (everyone just looks at them with the 'DUH' look on their faces)

Obviously, these won't be the people installing or upgrading Linux, and we hope the computer administrators know how to make a simple guided partition! :lolflag:

ok I'm straying off topic a little bit...

I guess when it comes down to it, someone who doesn't know how to attach a file to their email or partition a disk probably couldn't figure out how to use a restore or downgrade function either. And if something went wrong, heaven help them...

As for me, I did a clean install of Gutsy Gibbon after the upgrade failed me miserably, and my computer is once again happy and I almost have it back to the way it was. So I guess I didn't need it either. 

btw, once you get Gutsy happy, it's pretty darn cool!:guitar:

---

### Post by Frak on 2007-10-29
no, this would take much more effort than what would benefit from this. Just back up your data first.

---

### Post by Thunar on 2007-10-29
> **hexion said:**
> 
*** MY IDEA ***

To develop a pre-installing back-up system.
When a user inserts the LiveCD and double-click the install icon, a dialog would appear informing of the choice to do a backup to a file (or external device).
If the answer is affirmative, a simple GUI (to implement) will show with these options:
- Action (Backup / Restore)
- Type (Full / Only home)
- Exceptions (this would open a folder-tree view and allows to select folders to be ignored)
- Compression (High <slowest>, Normal, Low <largest>)
- Source/Destination (File / Burner)

I don't think I have to explain what would happen after that...
After the backup is done, the install asistant would start.


Now, in the case something goes wrong (imagine a disaster case, even the X doesn't load) and the user doesn't have the skills/time/whatever to try to solve himself:
- Inserts the LiveCD and reboots.
- When the system is started (the live session), starts the "backing up/restoring utility".
- Restores from the previously made backup.


*** PROBLEMS
I don't think a utility like this would be very difficult to be developed, but there are some issues:

- If the LiveCD is inserted, how could the application burn the back-up into a DVD? Could the LiveCD be extracted for a while?

- The user should be warned about where to save the backup file... of course not in the same partition where the system is going to be installed.



What do you think?

I actually kind of like this idea. I'm sure if there was such a comprehensive back-up utility that it would have some cd-swapping capability. Maybe there could be an option to back it up to a special folder or partition if there was no burner? The other thing I like about this idea is that it's a simple utility on the Live CD, would be available only on the Live CD, and would save the Devs the headaches of trying to implement a highly complex and unpredictable downgrade function in the newer distro.

> **thtrgremlin said:**
> backup utilities do exist on the liveCD/DVD, not to mention your computer before you put in the install disk. While I can totally understand where you are coming from, backups should be second nature to people, and if there was a reminder every step of the way to backup every time it thinks you should, that would get annoying really quick. Additionally, I think the general direction with the installer is to have fewer menus / options / choices during the install process such that the choices are only those that will be necessary with every install.

I've never seen a back-up utility on the Live CD, but I'll take your word for it... But I think we're talking about a comprehensive back up here... the "Make it like it never happened" kind of back-up. And instead of a reminder or an annoying pop-up maybe it could just be an option in the existing installer. Use it if you want, ignore it if you don't. And since it would only be available in the Live CD, you would only have to see it about once every six months.

I think this is a better idea than a downgrade function or restore utility...

---

### Post by flameproof on 2007-10-29
One question I would have:

Why does the LIVE cd formats the HDD anyway? When I upgraded to 7.04 from the previous Ubuntu I did that from Live CD, because the update function was broken. It forced me to format, even though the file system was the same.

Doing a "no format please" would be the first step to a better system.

---

### Post by evymetal on 2007-10-29
I would like to see a downgrade feature for one reason:

beta-testing.

Imagine the increased number of early bug-reports if more users felt comfortable using the betas...

Couldn't you do something like take a snapshot of the repos and then uninstall all packages installed since, re-install the previous versions, and re-install any packages which had them as depencencies? (kinda a noob to debian repositories)

---

### Post by ronacc on 2007-10-29
> **Thunar said:**
> good to know :)



I'm just about the only one where I work that knows how to attach a file to an email, and everyone there uses computers. Let's face it, there are a lot of computer illiterate people out there who use computers everyday (mostly for games, Myspace or chat, but what the hey), and let's face it, this is part of the Linux target audience these days. I've seen more than a few articles where Linux is touted as a smart choice for schools, businesses and the like. And it's true, for many reasons. I don't think anyone would be worse off than they are with the Macs at my work (everyone just looks at them with the 'DUH' look on their faces)

Obviously, these won't be the people installing or upgrading Linux, and we hope the computer administrators know how to make a simple guided partition! :lolflag:

ok I'm straying off topic a little bit...

I guess when it comes down to it, someone who doesn't know how to attach a file to their email or partition a disk probably couldn't figure out how to use a restore or downgrade function either. And if something went wrong, heaven help them...

As for me, I did a clean install of Gutsy Gibbon after the upgrade failed me miserably, and my computer is once again happy and I almost have it back to the way it was. So I guess I didn't need it either. 

btw, once you get Gutsy happy, it's pretty darn cool!:guitar:

Exactly my point ! thousands of computer shops make their living straightening out the way people screw up their windows systems even with the protections MS tries to build in.  I have friends like you describe , if you tell them, to fix that, do XYZ either look at you with a blank stare or abject terror.

---

### Post by misfitpierce on 2007-10-29
No. Downgrading is a bad idea.

---

### Post by jethro10 on 2007-10-29
I have 3 partitions on my Disk,

A /home and 2 for Ubuntu. I dont upgrade, I install on the second partiton. if it fails, I use the dual booting to stay on the current version.

Not quit downgrading but serves the same purpose.

If I choose the new version for my main use, in April next year I will install to the 'old' first partiton. 

Repeat. Repeat.....

J

---

### Post by hexion on 2007-10-29
> **jethro10 said:**
> I have 3 partitions on my Disk,

A /home and 2 for Ubuntu. I dont upgrade, I install on the second partiton. if it fails, I use the dual booting to stay on the current version.

Not quit downgrading but serves the same purpose.

If I choose the new version for my main use, in April next year I will install to the 'old' first partiton. 

Repeat. Repeat.....

J


That's what I do also :)
Now that Gutsy went final version, I have Gutsy in both of them.. but now my testing partition is testing the new (crappy) driver of ATI with AIGLX. When it's stable enough (if it's someday), I'll pull the "changes" to my stable partition.

And after that... the next will be Hardy alpha \\:D/

---

### Post by ronacc on 2007-10-29
thats what I do also, except that I go one step further and use a seperate drive .

---

### Post by Thunar on 2007-10-29
> **flameproof said:**
> One question I would have:

Why does the LIVE cd formats the HDD anyway? When I upgraded to 7.04 from the previous Ubuntu I did that from Live CD, because the update function was broken. It forced me to format, even though the file system was the same.

Doing a "no format please" would be the first step to a better system.

I'm just guessing here, but I think the reason there is no upgrade on the live is because it's much easier to package a clean install on a 650-750MB CD than to include all of the possible upgrades your particular set-up might need. Also, since the upgrade can be done from the Update Manager, it's probably considered unnecessary. Even though I must admit that my own experiences with the distro upgrade through the Update Manager were very poor.

---

### Post by Thunar on 2007-10-29
> **jethro10 said:**
> I have 3 partitions on my Disk,

A /home and 2 for Ubuntu. I dont upgrade, I install on the second partiton. if it fails, I use the dual booting to stay on the current version.

Not quit downgrading but serves the same purpose.

If I choose the new version for my main use, in April next year I will install to the 'old' first partiton. 

Repeat. Repeat.....

J

Not a bad idea, but since I'm rocking a 10GB HDD right now, don't laugh, that's not really an option for me at this point.

---

### Post by Frak on 2007-10-29
> **evymetal said:**
> I would like to see a downgrade feature for one reason:

beta-testing.

Imagine the increased number of early bug-reports if more users felt comfortable using the betas...

Couldn't you do something like take a snapshot of the repos and then uninstall all packages installed since, re-install the previous versions, and re-install any packages which had them as depencencies? (kinda a noob to debian repositories)
Debian/Ubuntu repos are somewhere around 15-20GB or above in size.

---

### Post by LaserJock on 2007-10-29
> **flameproof said:**
> One question I would have:

Why does the LIVE cd formats the HDD anyway? When I upgraded to 7.04 from the previous Ubuntu I did that from Live CD, because the update function was broken. It forced me to format, even though the file system was the same.

Doing a "no format please" would be the first step to a better system.

It has to format your HDD because it doesn't actually have many .debs to install/upgrade. The LiveCD works by actually copying over a real installed Ubuntu system over to the hard drive, not installing individual packages.

The way to upgrade via CD is to use the Alternate CD which does have the .debs .

-LaserJock

---

### Post by LaserJock on 2007-10-29
As a person who's dealt with Ubuntu/Debian packaging for over two years now my own experience tends to go with we should have a good backup system rather than a downgrading system. 

Downgrading via the package management system would be very very difficult and create a lot of headache for developers.  I suppose it  wouldn't be impossible, it's open source software after all :)

One thing I think might be useful to consider in this discussion is that there are some differences between Ubuntu and Windows in this area. One thing is that many computer manufacturers no longer ship Windows installation media let alone actual Windows discs. Therefore restoration is about all you've got if things go bad. With Linux and Ubuntu specifically the installation media is easy to get at so if say you don't like your current version you can easily get the installation media of a previous version. Therefore, having a good backup tool (there are several things going on in Ubuntu for this) that will allow you to easily have a fresh install while retaining personal files and settings should give you a much more stable system than trying to downgrade your system in place.

-LaserJock

---

### Post by kegie on 2007-10-29
The main problem with the downgrade feature is; why do you want it? You want it because of bugs in the upgrade/install process causing you problems, right? The thing is, a downgrade feature would technically be a whole lot more complicated than the upgrade/install, AND it would be a lot less tested since people tend to upgrade more than they downgrade.

So most likely, the downgrade feature would only ruin your system even more beyond repair.

The only way to be sure an install doesn't screw up and remove your data is to keep a backup somewhere else, as people say. And that goes for all operating systems!

Just today I was helping a friend recover her data from a vista upgrade, it turns out something called Norton Goback had made her drives unusable. Man was I glad to be running linux :]

---

### Post by Thunar on 2007-10-29
I'm going to go out on a limb and talk about things that I am not really that knowledgeable about here, so forgive my likely ignorance in these matters but:

My first taste of Linux was actually in Windows using a program called VMWare, which I am sure many here are familiar with. VMWare would use things called "Virtual Appliances", which, in the case of an operating system like Linux, would be a complete customized Linux distro with packages, settings, files, etc. that were put together by the maker of the appliance. Usually it would include a utility that allowed you to make a new appliance that included the customized settings, files, etc. that you added/removed after you installed it.

See where I'm going with this?

Maybe this isn't that much different than what crush304 suggested with tar or dd:

> **crush304 said:**
> [http://https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

with tar or dd you should be able to backup your entire system and restore if the upgrade fails

But I figured I'd just throw that into the mix.

---

### Post by Hobbsee on 2007-10-30
> **Thunar said:**
> I am seeing some closed-minds in open-source. Isn't it ironic? Don't you think?

Closed minds?  No.  Aware of the feasibility?  Absolutely.

---

### Post by evymetal on 2007-10-30
> **Frak said:**
> Debian/Ubuntu repos are somewhere around 15-20GB or above in size.

oh, I guess I thought there was some kind of versioning built into the syatem

---

### Post by Frak on 2007-10-30
> **evymetal said:**
> oh, I guess I thought there was some kind of versioning built into the syatem
If you mean backing up recently installed .deb's, yes that is possible, but it would likely double the size of your /usr directory.

---

### Post by Thunar on 2007-10-31
> **Hobbsee said:**
> Closed minds?  No.  Aware of the feasibility?  Absolutely.

OK OK! It was a joke! Nobody liked it! I get it!

Gosh! [-(

*stomps away in his best napoleon dynamite*

---

### Post by evymetal on 2007-10-31
> **Frak said:**
> If you mean backing up recently installed .deb's, yes that is possible, but it would likely double the size of your /usr directory.

No, I meant on the server - if you could do apt-get install [module] [version] then you could downgrade quite smoothly, but it souds like that's not supported  in Debian. In which case I would strongly suggest this feature for development for the Debian packaging system if possible.

---

### Post by mixmaster on 2007-10-31
Downgrading would be comparatively simple if the initial install did something more sensible than splatting everything into one partition.

I upgraded to gutsy and downgraded again when it caused me problems.  Downgrade was comparatively trivial because I had /opt, /usr/local/bin and /home in separate file systems.

I accept it is not trivial but it could be done without too much effort and it would be helpful under some circumstances.  Telling people to backup is fine but if you are trying to produce a mass-market product you have to accept that most people will not do this.

---

### Post by nocturn on 2007-10-31
> **aidanr said:**
> The easy roll back option is to **_backup_** before you make any major changes to your system, backing up is something you should do anyway.

Something like Apple's timemachine would be great.
Off course, the coolest way to get this would be with snapshots like ZFS (if Sun ever GPL's it).

---

### Post by elanthis on 2007-10-31
> I can not understand why anyone would be against a downgrade function. If you don't like it don't use it. That is how OPTIONS work, they are OPTIONS as the name implies.

And the thing that people like you fail to understand is that OPTIONS require development time, testing time, and then require unbounded maintenance time for the remainder of eternity.  Each and every single option has a very real and very distinct cost on developer time, and when that cost is not paid (as it usually isn't in the case of maintenance time, because maintenance is boring and there is never enough time) the option merely becomes a source of bugs.

When you're talking about a feature like dstiribution rollback, which is an insanely complex thing to do and which is only really useful to silly people who upgrade to testing on their non-test machine, that cost in time and the threat of additional bugs is simply not worth even considering.

If instead you are asking for rollback because Gutsy was too buggy, then ask yourself this: is adding yet more code, eating up more time that can't be spent fixing the actual bugs you're running into, anything other than a horrendously bad idea?

<developer rant>
This is why users really shouldn't ever ask for specific solutions to problems - they should only point out the existance of the problem, and let the developer find a solution.  Intead of saying, "I have this problem, I need a solution, please help me, thank you," users end up saying, "Add this feature to work around bug X that I am not even going to tell you about, and if you don't, I'm going to call you names."  Instead of identifying the problem and letting someone who understands the software figure out the solution, users instead come up with their own half-baked idiotic solution and then demand it be implemented (not ask, oh no, they never ask developers for anything - they demand it and then insult the developers when they refuse).  When the developers give in, the software simply ends up even more bloated and having new bugs and the original bug or problem the user had isn't even fixed in the process.

Even when users ask for new features they usually do it wrong.  Instead of saying, "I need be to do X, please help, thank you," they instead come up with some completely wacky and inefficient way the software could do X and then request that specific feature without ever identifying why they need it.  And if the developer gives in and implements the wacky feature, the software gets bloated, gets more bugs, and the user ends up with a poor solution to a problem that could probably have been solved in a much better way if the user had given the developer useful information.
</developer rant>

in other words, stop asking for rollback.  Go file bugs in Launchpad explaining what you find so onerous about Gutsy that you feel the need to rollback, and let the developers fix the actual problems with real solutions instead of implementing a completely incorrect and very complicated feature that doesn't actually solve anything.

---

### Post by Borzo on 2007-11-07
Hi,

In light of the issues I am having after upgrading to Gutsy, I would like to see a fallback mechanism incorporated into the upgrade process. Maybe before upgrading we could tick a box with "image current system before upgrade" where the current system is archived for possible restoration in case of trouble. I know you could image your system with partimage manually prior to upgrading and have the same thing, but having a similar mechanism available on hand when upgrading woud be, at least to me a positive thing.

thans for listening :)

---

### Post by yogo on 2007-11-07
That is a great idea.

I upgraded but after about two weeks of poor performance, I had to go thru reformatting and additional Feisty installs when Feisty was perfect.

I hope they do implement something like that, next time I am going to be gun shy if it is not implemented.

---

### Post by 23meg on 2007-11-07
I've merged your post into a thread where the same idea was discussed.

---

### Post by cainmark on 2007-11-21
> **Borzo said:**
> Hi,

In light of the issues I am having after upgrading to Gutsy, I would like to see a fallback mechanism incorporated into the upgrade process. Maybe before upgrading we could tick a box with "image current system before upgrade" where the current system is archived for possible restoration in case of trouble. I know you could image your system with partimage manually prior to upgrading and have the same thing, but having a similar mechanism available on hand when upgrading woud be, at least to me a positive thing.

thans for listening :)

I'm also in favor of this, and that's a good idea.
  I've backed up and have to reinstall fiesty now that Gutsy has played havoc with my wacom graphire4 and nvidia 5200fx video card, both of which worked in fiesty.
  Having a way to easily get back to when the hardware was working properly. without having to partion and format would be great for this end user who would prefer to stay an end user.

Thanks!

---

### Post by Frak on 2007-11-21
> **cainmark said:**
> I'm also in favor of this, and that's a good idea.
  I've backed up and have to reinstall fiesty now that Gutsy has played havoc with my wacom graphire4 and nvidia 5200fx video card, both of which worked in fiesty.
  Having a way to easily get back to when the hardware was working properly. without having to partion and format would be great for this end user who would prefer to stay an end user.

Thanks!
Back up your Hard Drive as an image and restore it when needed. Restoring old files is hazardous, time consuming, and tedious.

I doubt this would be implemented, just looking at the threads dead time.

---

### Post by Thunar on 2007-11-21
> **Frak said:**
> I doubt this would be implemented, just looking at the threads dead time.

Well we can only talk something to death for so long when everyone who can actually do anything about is wholeheartedly against the idea. Personally I think a "downgrade/backup/just get me back on the yellow brick road please" function is a great idea considering the very people that Linux Developers would likely wish to see in their camp: Defectors from the Windows and Apple camps, have enjoyed this functionality in their operating systems for years.

Bottom Line: 

The more user friendly Linux becomes, the more users it will have. 

period.

---

### Post by 23meg on 2007-11-21
> **Frak]I doubt this would be implemented, just looking at the threads dead time.[/QUOTE]

The thread's dead time has nothing to do with the chances of implementation. Some ideas discussed in threads in the Gutsy idea pool with some of the longest dead time got implemented, either because their participants actually did something other than discussion about them, or because they were products of zeitgeist said:**
> Bottom Line:

The more user friendly Linux becomes, the more users it will have.

period.

Here's some food for thought for you; you do seem to need it.

[Linux For Consumers (Havoc Pennington)]("http://log.ometer.com/2007-11.html#21")
[Popularity As Measure Of OSS Success (Bryce Harrington)]("http://www.advogato.org/person/bwh/diary.html?start=38")

---

### Post by cainmark on 2007-11-22
> **Frak said:**
> Back up your Hard Drive as an image and restore it when needed. Restoring old files is hazardous, time consuming, and tedious.

I doubt this would be implemented, just looking at the threads dead time.

That just proves my point.  How would an end user like me know to do that?  Or even know how to do it (I do, but most new end users won't)?

I get under the hood when I have to, not because I enjoy it (still much fewer times than I had to on WindowsXP, though :)  ).  

If there was something like the "oil change every whatever miles", that would have information on that shop and how to do it.

i.e. " Would you like to back up your hard drive as an image before you upgrade?" before the upgrade even started for end users like me would prevent a lot of frustration.  Followed by, "Where would you like to store this?"  and "Copy the following down:  This is is how you restore the image of your hard drive." 

And might stop developers from getting irritated at end users who'd like a function they know is possible and useful for other Oses.

Yes, it's handholding, but not everyone takes to the technical stuff, or has the time and/or persistence to search through all the community notes about it.

---

### Post by Frak on 2007-11-22
> **cainmark said:**
> That just proves my point.  How would an end user like me know to do that?  Or even know how to do it (I do, but most new end users won't)?

I get under the hood when I have to, not because I enjoy it (still much fewer times than I had to on WindowsXP, though :)  ).  

If there was something like the "oil change every whatever miles", that would have information on that shop and how to do it.

i.e. " Would you like to back up your hard drive as an image before you upgrade?" before the upgrade even started for end users like me would prevent a lot of frustration.  Followed by, "Where would you like to store this?"  and "Copy the following down:  This is is how you restore the image of your hard drive." 

And might stop developers from getting irritated at end users who'd like a function they know is possible and useful for other Oses.

Yes, it's handholding, but not everyone takes to the technical stuff, or has the time and/or persistence to search through all the community notes about it.
That's a good idea. Why don't you start an **[IDEA]** thread in the idea pool about it?

---

### Post by Thunar on 2007-11-22
> **23meg said:**
> Here's some food for thought for you; you do seem to need it.

I've actually read several similar articles, and it's always the same. It's no mystery that Linux developers (most of them) don't get paid, and it's also no mystery that Linux and Windows and OS X are different, always will be, and really should be. I've also read another similar article wherein it says that for something to be an improvement, it CAN NOT be the same. This is also very true. But where, pray tell, has Linux improved upon restoration technology? It seems practically absent to the average end user. Even an intuitive ghosting, imaging or system back-up technology would be nice.

It's not just about a "slug-out-the-feature-matrix strategy," it's about real world functionality for my mom, my grandma, my girlfriend, the kids, the schools, or anyone who isn't already some "guru" Linux user. And while popularity may not be the indicator for a successful operating system, it is definitely an indicator for an accepted one. And the more people accept Linux as their OS of choice, the bigger the community will become, and the more people there will be contributing to the Open Source community. Is this a bad thing?

Lucky for me, I'm no newbie when it comes to computers. Because every distro of Linux has had me in the terminal "fixing" things just like the DOS days, and spending hours in the support forums (thank goodness you guys are here). This is all fine and dandy, but it would be nice to see some sort of REAL system safeguard, because  Linux is not just for hackers any more.

---

### Post by Borzo on 2007-11-22
To those that oppose this idea: It all boils down to this - who is Ubuntu aimed for? I am sure nobody would suggest such a feature in a Gentoo or Slackware forum.

just my 2€ ;)

---

### Post by 23meg on 2007-11-22
[QUOTE=Borzo]To those that oppose this idea: It all boils down to this - who is Ubuntu aimed for?[/QUOTE]

It's definitely not aimed for people who wouldn't be able to repair a system broken further by a downgrade function. 

People have enough problems utilizing the supported *up*grade function due to bad unofficial packages and scripts, poor administrative practices and the like. Supporting *down*grading, especially without improving the overall situation regarding breakage in dist-upgrades (for whatever reason) wouldn't be a wise decision.

---

### Post by Borzo on 2007-11-22
ok, cant' we just launch partimage like memtest, from GRUB instead of downgrading with APT? then the system could be imaged to and recovered from  a dedicated backup partition first created when installing the system.

---

