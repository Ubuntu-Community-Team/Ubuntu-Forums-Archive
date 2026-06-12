---
title: "Best practises for operating and maintaining Linux systems"
date: 2007-07-08
forum: The Cafe
---

### Post by David Ostrom on 2007-07-08
Hello All,
I would like to get your ideas for a list of best practises for operating and maintaining Linux systems. Specifically Ubuntu.

---

### Post by bread eyes on 2007-07-08
1. Plug it in
2. Pay the power bill
3. Don't pee in it

---

### Post by init1 on 2007-07-08
> **bread eyes said:**
> 1. Plug it in
2. Pay the power bill
3. Don't pee in it
lols

---

### Post by David Ostrom on 2007-07-08
1. Plug it in
2. Pay the power bill
3. Don't pee in it
Not exactly what I was looking for but its a start. Thanks!:lolflag:

---

### Post by starcraft.man on 2007-07-08
Nothing. You don't need a spyware cleaner, an antivirus or a registry/other cleaners (I don't even recommend automated registry cleaners for windows, thats another matter). Have fun, there isn't anything you need to do to maintain Ubuntu, just don't do anything (like editing files your not sure about) to damage it.

---

### Post by notwen on 2007-07-08
Not so much maintenance, but if you should get in the habit of making a copy of files you edit, especially if they're somewhat new to you.  Maybe even check your sources.list every so often to make sure that certain repos are up-to-date.  Other than that I'm stumped.  =]

---

### Post by jrusso2 on 2007-07-08
boot it up, back up your data, and don't toast your pop tarts on the cpu.

---

### Post by ice60 on 2007-07-08
> **notwen said:**
> Not so much maintenance, but if you should get in the habit of making a copy of files you edit, especially if they're somewhat new to you.  Maybe even check your sources.list every so often to make sure that certain repos are up-to-date.  Other than that I'm stumped.  =]
when i last used ubuntu (i mainly use other distros) the beryl repo was down, does anyone know if it's down for good, or if it was just a server problem?

---

### Post by insane_alien on 2007-07-08
> **jrusso2 said:**
> boot it up, back up your data, and don't toast your pop tarts on the cpu.

my cpu never gets hot enough, they're always lukewarm.

---

### Post by girard on 2007-07-09
I was wondering about the same thing, hence my coming across this thread. 

In almost all cases, users have been claiming that there isn't a need to maintain a linux system. I wonder how accurate this might be? This is coming from the universal perspective that everything you use frequently has to be maintained well in order for it to function properly and stay in good working condition(shoes, cars, equipment, appliances, windows). But in all my searches, linux users always claim that there isn't a need to maintain the system. I'm trying to break a possible self-perpetuating belief which could be wrong all together, and worse, which we feed unto new naive users (i'm new to this myself).

The claim that linux does not need an anti-virus is I think only real to the extent that most computer viruses are aimed at infecting a windows system. This should not be thought of as tantamount to saying that linux cannot get infected. It just so happened that there aren't so much threat to worry about - but the system can indeed get infected. I would think that the same goes for spyware and adware - that most are targetting IE and not Firefox - but that does not also mean that FF is not vulnerable altogether. 

As regards the registry (not even sure if that exists in one form or another for linux), file fragmentation, etc... well, I guess we'd have to wait some computer expert to read this thread... but again, if you use it, they will get fragmented... actually, i remember reading somewhere that it's not that an EXT (linux?) file system **does not **fragment at all, it's just that NTFS and FAT (both windows?) systems fragment more easily than EXT's (I hope I'm using my terms correctly).

I'm not an expert, nor do I have any real technical knowledge about this matter, so I'm hoping that someone with a real technical know-how on why there isn't a need to maintain a linux system, could help clear out this issue. But in essence, yeah we still do need to maintain our system the same way windows does need to be maintained (as well as everything else)... it's just that we don't need to worry about it too much and we don't need to do them as often.

---

### Post by maniacmusician on 2007-07-09
> **ice60 said:**
> when i last used ubuntu (i mainly use other distros) the beryl repo was down, does anyone know if it's down for good, or if it was just a server problem?
Beryl is being phased out anyways...they still support it, but they won't for long. And it's not getting any updates or bugfixes. You can install Fusion (merge of beryl and compiz), and yes, it does have working repos.

---

### Post by sloggerkhan on 2007-07-09
I recomend keeping your /home on its own partition and backing it up every week if you use your comp a lot and can back it up.
Otherwise, always make backups of config files when you edit them. If a config file is heavily customized, keep a backup in you /home so you don't have to redo edits if the rest of the system dies.

I suppose you could also backup the rest of the system, too. A few people make a partition of a fresh install (or fresh + a few additions)  that they revert over the main install if things go bad. But they are the sort who like to tinker and use lots of beta and alpha. Still, it's a convenient way to go. Quicker than using a LiveCD and re-downloading extra packages if you do have to reinstall the main system.

---

### Post by girard on 2007-07-09
this might add to the info:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Altarbo on 2007-07-09
> **girard said:**
> [ . . . ]

The claim that linux does not need an anti-virus is I think only real to the extent that most computer viruses are aimed at infecting a windows system. This should not be thought of as tantamount to saying that linux cannot get infected. It just so happened that there aren't so much threat to worry about - but the system can indeed get infected. I would think that the same goes for spyware and adware - that most are targetting IE and not Firefox - but that does not also mean that FF is not vulnerable altogether.  [ . . . ]Hello,

I couldn't give an answer to your filesystem question that would help at all, but I think I can explain the internet related one.  There are two main reasons that Windows is so prone to malware.  One is related to the OS itself and the other to the browser/email/rss client.

Microsoft has tried to maintain backwards compatibility with MS-DOS.  DOS was designed with the philosophy that it should be so basic, any machine could run it.  That meant that many things that have become important today (such as networking and multiple users) were ignored in DOS.

Linux is a rewrite of Unix which was designed with multiple users and networking in mind.  The principle behind Unix is that you have a user name and password that you can use to give any single process a certain level of permission.  Microsoft waited until Vista to implement this, because they were concerned that it would make older applications (written for DOS or win16 API's) incompatible.

This causes the first problem with Windows.  Say hypothetical man John Doe downloads Crazy Funtime Partycursor from shadywarez.russia on his two computers one running Ubuntu and one running Windows XP.  Whenever  Partycursor  attempts to format his entire hard disk on Ubuntu, Mr. Doe will be presented with a message explaining that Crazy Funtime Partycursor needs administrative privileges to do some task and explains that he should enter his user name and password to give those privileges to the process.  On the XP machine Partycursor will be give every privilege that the user running it has, so John's information will all be erased without any objection from Windows.

There are few things you should note about this problem.  Microsoft has tried to implement a privilege system more like Linux, BSD, Solaris, etc. in Vista.  Also, this security requires that end users be able to understand what processes are going to need these priveleges.

The second problem is related to internet browsing.  Explorer and Outlook (I haven't used Outlook for a while though, so it may have changed) default to Javascript, VBscript, and I think DirectX being embedded in webpages.  It is also (the last time I used either) a tremendous pain to turn these things off.  They allow webpages to run pretty close to complete applications in a browser, but the problem is that you might not want to run a thousand different applications, many written by people you do not know or trust, every year.

This is probably longer than it needed to be, but to close I want to emphasize that Ubuntu makes it easier to be secure, but ignorant users will still be able to ruin their system.  And Windows makes it harder to be secure, but informed users can still protect their systems pretty well.  If you're going to use Windows (especially 9x, Me, 2000, or XP), get a firewall, get an adware program, get an antivirus program, and get firefox.  Go to Edit>Preferences>Content in Firefox and disable Javascript (VBscript is native to Explorer).  View your email in text only mode, or get an email client that supports it.  Set your computer to start the firewall and the antivirus program when you boot for all users.    Scan your computer every couple weeks (for adware and virus) and don't install software from vendors you don't trust.  You won't be as secure as you could be with Linux or especially OpenBSD, but if you're using the computer for desktop usage, I doubt you'll have any problems.

- Altarbo

Also:
You didn't ask about this, but one thing I've like about Ubuntu is the way dependency libraries are handled.  In Windows, over time you build up many libraries that you don't need and that slow your computer down.  APT (used by Debian and Ubuntu) will remove these unused dependencies whenever you uninstall the last piece of software to rely on them.  This isn't so much a linux thing though.  Slackware and RedHat are just as bad as Windows when it comes to this.

---

### Post by jrusso2 on 2007-07-09
> **girard said:**
> I was wondering about the same thing, hence my coming across this thread. 

In almost all cases, users have been claiming that there isn't a need to maintain a linux system. I wonder how accurate this might be? This is coming from the universal perspective that everything you use frequently has to be maintained well in order for it to function properly and stay in good working condition(shoes, cars, equipment, appliances, windows). But in all my searches, linux users always claim that there isn't a need to maintain the system. I'm trying to break a possible self-perpetuating belief which could be wrong all together, and worse, which we feed unto new naive users (i'm new to this myself).

The claim that linux does not need an anti-virus is I think only real to the extent that most computer viruses are aimed at infecting a windows system. This should not be thought of as tantamount to saying that linux cannot get infected. It just so happened that there aren't so much threat to worry about - but the system can indeed get infected. I would think that the same goes for spyware and adware - that most are targetting IE and not Firefox - but that does not also mean that FF is not vulnerable altogether. 

As regards the registry (not even sure if that exists in one form or another for linux), file fragmentation, etc... well, I guess we'd have to wait some computer expert to read this thread... but again, if you use it, they will get fragmented... actually, i remember reading somewhere that it's not that an EXT (linux?) file system **does not **fragment at all, it's just that NTFS and FAT (both windows?) systems fragment more easily than EXT's (I hope I'm using my terms correctly).

I'm not an expert, nor do I have any real technical knowledge about this matter, so I'm hoping that someone with a real technical know-how on why there isn't a need to maintain a linux system, could help clear out this issue. But in essence, yeah we still do need to maintain our system the same way windows does need to be maintained (as well as everything else)... it's just that we don't need to worry about it too much and we don't need to do them as often.

All these questions have been answered in this forum so many times people get tired of having to explain it over and over.  But if you do a search of this forum all the answers are in there.

---

### Post by smoker on 2007-07-09
it is always wise to maintain up to date backups of all your crucial data, mainly in case of hardware failure rather than os failure.

and occasionally take the cover off the case and give the inside a good clean, remove dust and grime from fans, heatsinks, etc, again, not os related, but good practice.

---

### Post by somafm on 2007-07-09
Just make sure it's running how you need it to, and keep up on the software updates and you should be fine! But the most important thing I think is to backup! And don't just have a backup file and think you're good. You should always test your backups and make sure they work! Have a plan of how you will restore your system in the event of a crash, how long it will take (if needing the data is critical), what you will do step by step, etc.

I think that's a mistake many people are probably making right now:  having an automated backup of some kind and feeling like they are set, but they never really test their backups or simulate a crash (like by using another machine).

---

### Post by saulgoode on 2007-07-09
> **Altarbo said:**
> Also:
You didn't ask about this, but one thing I've like about Ubuntu is the way dependency libraries are handled.  In Windows, over time you build up many libraries that you don't need and that slow your computer down.  APT (used by Debian and Ubuntu) will remove these unused dependencies whenever you uninstall the last piece of software to rely on them.

I do not believe this is an accurate description. APT will remove packages which depend upon the package you are removing. It does not remove packages (e.g., libraries) upon which the package you are removing depends.

For example, if you install the GIMP, APT would realize that the GIMP requires the PANGO library and automatically install it at the same time. If you then uninstall the GIMP, PANGO will **not** be removed. (If, however, you remove PANGO then the GIMP would be uninstalled.)

---

### Post by Alterax on 2007-07-10
My best practices:

Harden your system.  If you don't use a particular network daemon, remove it from your system.

Use strong passwords:  8-12 characters, including a mix of capitals, lowercase letters, numbers, and characters.

Regular backup routine.  It's not terribly expensive to get a USB external drive for this.  And periodically check to make sure your backups are good--installing them on a virtual machine is a GREAT, non-invasive way to check them.

Work with POLA:  The Principle of Least Authority--users only should work with the amount of privilege they need to do their jobs with their computers.  Running as root is like driving with your feet--you can do it, but that doesn't mean it's to be done.

When changing configuration files, always make a backup first, and always document your changes so you'll know what you did.

If you have to do some lengthy processes more than three times in the terminal, write a shell script.

Learn what the main directory structure of Linux is for, and use it by putting things where they logically belong.  This makes it MUCH easier to track things down later.

That's about it, I think.


--Alterax

---

### Post by Robynsveil on 2007-08-06
> **Alterax said:**
> My best practices:

Harden your system.  If you don't use a particular network daemon, remove it from your system.

--Alterax

I just read an [article]("http://www.newsforge.com/article.pl?sid=04/12/01/2329229") about 'hardening' your system, and I think the term could do with a bit of explanation, with prejudice towards Ubuntu users, particularly neophytes like us. Removing an unused network daemon (which leaves open a port?) is one point - I'm sure there are others. Someone mentioned earlier that there are heaps of threads on the subject - perhaps it might be a good idea to make protecting your Linux box from vulnerabilities a sticky item.

Cheers,
Robyn

---

### Post by insane_alien on 2007-08-06
> As regards the registry (not even sure if that exists in one form or another for linux), file fragmentation, etc... well, I guess we'd have to wait some computer expert to read this thread... but again, if you use it, they will get fragmented... actually, i remember reading somewhere that it's not that an EXT (linux?) file system does not fragment at all, it's just that NTFS and FAT (both windows?) systems fragment more easily than EXT's (I hope I'm using my terms correctly).

1/ there is no registry or any equivalent in ubuntu

2/ ext can and does fragment but the principles it works on means the more you add and remove and move about the harddrive the more ordered it will get with the way files get placed on the HDD. with windows they just get shoved in the first available space whether it fits or not.

ext will not see appreciable fragmentation even under heavy use till it is around 85-90% full.

---

### Post by Depressed Man on 2007-08-06
I thought there was something like a registry in Linux? I remember reading a post saying one of the differences between KDE and Gnome was that KDE doesn't attempt to hide the registry.

Though then again it just may be something that's spewed up from a KDE vs Gnome war.

---

