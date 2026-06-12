---
title: "is wine virus free?"
date: 2009-01-25
forum: Wine
---

### Post by arunkumar413 on 2009-01-25
recently i installed wine on my system and i wanted to know if wine is virus free.I got this doubt because wine runs windows programs on Linux and most of the windows programs are prone to viruses.does running a virus infected windows program under wine  pose any problem to the Linux

---

### Post by binbash on 2009-01-25
it wont be a problem

---

### Post by Mud.Knee.Havoc on 2009-01-25
> **arunkumar413 said:**
> recently i installed wine on my system and i wanted to know if wine is virus free.I got this doubt because wine runs windows programs on Linux and most of the windows programs are prone to viruses.does running a virus infected windows program under wine  pose any problem to the Linux

Check out [this thread]("http://ubuntuforums.org/showthread.php?t=72598").  It seems that it is possible to mess stuff up because a virus has access to all directories that are visible with wine (which includes /).  You can restrict this access to just ~/.wine by going into winecfg and clicking the harddrives tab.

They say that there's even a virus on wine's application DB that has a platinum rating. :)

EDIT: Oops, forgot to link to the thread I mentioned. Everything is fixed now.

---

### Post by Murrquan on 2009-01-25
I once saw an article that was talking about running tests with viruses on Wine, and saying that they all crashed or didn't do anything that he couldn't solve by force-quitting the window. He concluded by saying that viruses were an integral part of the Windows computing experience, and that the Wine developers needed to get their act together and improve Linux compatibility with Windows viruses. ^.^

That was a few years ago though, and Wine has been improving. It's probably best not to run any programs you know to be infected, just in case. Isn't there a virus scanner we can use, that scans for Windows viruses? *checks* Yes ... look for ClamAV in Add/Remove. You can use that if you're worried about a particular file's safety. I'm not sure if they keep up with the latest viruses all that well, or that anyone else does. But it's certainly better than nothing.

Hey, maybe you could run AV software in Wine! I wonder if that would work.

---

### Post by toopi on 2009-01-25
I'm sure Window viruses are capable of infecting the files within the bottle and cause chaos in those applications, but that should be the end of it.  They shouldn't cross the boundaries of the bottle, however, they may be able to do harm to other Window nodes on the network.

---

### Post by SunnyRabbiera on 2009-01-25
> **toopi said:**
> I'm sure Window viruses are capable of infecting the files within the bottle and cause chaos in those applications, but that should be the end of it.  They shouldn't cross the boundaries of the bottle, however, they may be able to do harm to other Window nodes on the network.

Yeh it seems to be very localized for the majority of them, all a windows virus can do without root access is close to nothing though and Ubuntu has disabled that in the first place.

---

### Post by gjoellee on 2009-01-25
You can easily get viruses with WINE, but because WINE is not fully Windows the viruses most likely wont have effect. The worst case scenario must be that you have to reinstall WINE. The Wiruses you get is most likely designed for Windows and will not have any effect on your Linux, BSD or Solaris system.

---

### Post by Meow27 on 2009-01-25
you can get viruses, and you can screw up ur linux system. just not ur main files


its safe to play it with no viruses :)

---

### Post by merlyn on 2009-01-26
> **Meow27 said:**
> you can get viruses, and you can screw up ur linux system. just not ur main files

It is possible to install some virii under wine. However you would have to do so manually.

Why? Well I'm glad you asked, and the short answer is that all the usual avenues of infection available on a Windows installation are not present in Wine.

Furthermore WINE is not an emulator, nor is it a virtual machine, the following quote is from the Wine Homepage.

> Wine is a translation layer (a program loader) capable of running Windows applications on Linux...Hence Wine does not provide the level of functionality that an emulator or Windows running in a virtual machine would, sufficient enough for virii to run effectively.

Further reading.

The Wine FAQ:                [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)     (in particular points 1.3 & 1.4)
Debunking Wine myths:   [http://wiki.winehq.org/Debunking_Wine_Myths](http://wiki.winehq.org/Debunking_Wine_Myths)

There is a really good article regarding attempts to install the most virulent virii in Wine which provides detailed results. Unfortunately I cannot remember where it is but this article is similar.

[http://jadmadi.net/blog/2005/01/27/linux-wine-how-to-running-windows-viruses-with-wine/](http://jadmadi.net/blog/2005/01/27/linux-wine-how-to-running-windows-viruses-with-wine/)

In a nutshell the article found that a number of virii would simply not install under Wine, and those that did had limited or no 'success' in functioning at all.

Perhaps there needs to be a sticky with relevant information about the Wine & Windows virii question as this crops up from time to time.

Cheers folks.

---

### Post by cogadh on 2009-01-26
Merlyn and Mud.Knee.Havoc are right on the money. You _can_ get a virus in Wine, but it will not screw up your entire system, just your .wine directory and possibly your user's home directory. If you make the mistake of running Wine with a root account or using sudo, that's a different story. When doing that, Wine and anything run with it has sufficient permissions to access the system files and potentially mess things up royally.

---

### Post by Nirro on 2009-01-26
For those of you who say: "at the most it will hurt your home directory but not the very important root directory or system files", remember that in a typical home desktop environment, most of the time, the files that exist in the home/user folder are *way* more important to the user than the system files...

This is not a multi-user server.

---

### Post by cogadh on 2009-01-26
Yeah, but the home directory files can all be easily fixed or replaced without having to re-install the whole system. If you screw up the system files, then you'll be lucky if the machine even boots, let alone runs normally.

---

### Post by Bios Element on 2009-01-26
> **cogadh said:**
> Yeah, but the home directory files can all be easily fixed or replaced without having to re-install the whole system. If you screw up the system files, then you'll be lucky if the machine even boots, let alone runs normally.

Your right. Here's a novel concept! Make Backups! I know it's annoying but if you care even a little about your files you should back them up anyway just incase your HD fails.

---

### Post by Nirro on 2009-01-26
You are both right and wrong IMO. 
You are right that for the personal files you always have to make backups, and backup again, and again. it's easy to say "make backups", but it's a murphy's law that if you happen to loose something, you would always loose the very same file that you haven't backup. Law.

On the other hand, the system files can always be restored by a (simple) reinstall (most of the time), and they are mostly more static and need less backups if you do decide to backup them.

---

### Post by cogadh on 2009-01-26
But unless you have taken the extra step of setting up your home directories on a separate partition from the system (which the average user does not do) that reinstall will make you lose your personal files anyway, when the new install overwrites them. To me, losing all of your personal data is far worse than possibly losing some of it that you neglected to backup.

---

### Post by Nirro on 2009-01-27
> **cogadh said:**
> But unless you have taken the extra step of setting up your home directories on a separate partition from the system (which the average user does not do) that reinstall will make you lose your personal files anyway, when the new install overwrites them. To me, losing all of your personal data is far worse than possibly losing some of it that you neglected to backup.

Not really. you can always save your private files (by using a liveCD for example) and then reinstall the OS.

But I agree that using seperate partition for your private documents and files (not home folder directly) is a good practice.

---

### Post by merlyn on 2009-01-27
Personally I go for the best of both worlds.

Whenever I install Linux, I always set up separate /boot, /, /swap and /home partitions.

That way should I ever choose to do a fresh install, all my personal data and settings will remain intact without the need to restore anything from backups.

Furthermore I also keep backups of all my personal data, and any config files that I've customised.

This is a little extra insurance just in case my hard drive snuffs it.

---

### Post by AndrewRiedi on 2009-01-27
Windows applications running in Wine are full-blown Linux (or whatever OS you use) applications.  If written cleverly, an application *could* detect Wine and use everything else any other application could (int 80h, etc.).  This is probably not what most people are talking about though, and provided the underlying system is secure enough, even this kind of virus shouldn't be able to hurt anything other than the files in ~/, unless there is some way to get priv. escalation, etc.

Presumably, most are talking about viruses aimed at true Windows run under Wine.  As a lot of these are just Win32 programs, Wine *can* and *will* run some of them, but again, these programs are limited to the ~/ directory.  (Unless they get around the underlying security mechanisms of the OS, in which case it isn't Wine's problem, but a problem with system libs., the kernel, overall design, etc.)  There is nothing stopping Wine from translating the calls into 'rm -rf /', but, of course, that will fail.

The solution, it seems, is just to create a second user account specifically for Wine if you want to run viruses, or just want to be safe.  This way Wine cannot hurt your regular user's data, but can only kill itself.  For gamers, this is probably the way to go.  For people who use Windows programs to create data, well, they can create a second acct. too, and then back their data up every now and then.  As a second precaution, it would be wise to run something like ClamAV on your Wine programs and files.

In the previous scenario, all that is needed to clean your infected install, provided the virus didn't create a copy of itself outside of ~/.wine (but inside ~/, in which case the following alternative is best), is just to rm -rvf ~/.wine (under the second Wine-only user.)  Alternatively, you could just remove that user and start all over.  The system and your normal user's files are all safe.  :)

Note:  I am not a security expert, but what I wrote is what I understand about Wine, and should be sufficient knowledge to keep people safe.  If someone who knows more wants to add to what I have said or wants to correct me, please feel free.

---

### Post by zeealpal on 2009-01-27
> **cogadh said:**
> Merlyn and Mud.Knee.Havoc are right on the money. You _can_ get a virus in Wine, but it will not screw up your entire system, just your .wine directory and possibly your user's home directory. If you make the mistake of running Wine with a root account or using sudo, that's a different story. When doing that, Wine and anything run with it has sufficient permissions to access the system files and potentially mess things up royally.

Even if you do get a virus in Wine, they are designed to infect windows programs and core files, which are not in Wine

---

### Post by cogadh on 2009-01-28
> **zeealpal said:**
> Even if you do get a virus in Wine, they are designed to infect windows programs and core files, which are not in Wine
They are if you have actually installed anything in Wine other than the virus. Besides, not all viruses are designed to do the same thing. A virus can infect or _affect_ any file type, depending on the payload the virus carries. There have been viruses in the past that were able to infect and spread through .doc files, so if you have any documents from a Windows machine in your home directory, they could easily be infected. Additionally, if the payload is something as malicious as a file deletion, it doesn't need to "infect" anything to do its damage once you run it. The point is, just because a virus is less likely to "infect" existing files on your Wine installation, doesn't mean it can't actually do any damage through Wine.

---

### Post by MasterNetra on 2009-01-28
Just a thought what about setting up your wine directories to be independent of your home stuff. ex. having all the directories (such as documents folder and etc) all within say the hidden wine folder and just keep the stuff seperate from each other? After all the virus only knows what wine shows it right?

---

### Post by cogadh on 2009-01-28
Yep, that would work in such a way that whatever the virus did would only harm the hidden directory and not anything else on your system. To fix it, you could simply delete and re-create the directory. It would require some significant custom configuration on your part, but once you have done it, it should be very easy to replicate. 

In fact, you could semi-automate the process by simply creating the directory and configuring it as you need, then make a backup copy of it before you actually install anything. That way if you happen to mess up the original with a virus, you can simply delete it, restore a copy from the backup and you are good to go.

---

### Post by toopi on 2009-01-29
> **toopi said:**
> I'm sure Window viruses are capable of infecting the files within the bottle and cause chaos in those applications, but that should be the end of it.  They shouldn't cross the boundaries of the bottle, however, they may be able to do harm to other Window nodes on the network.

Hold on guys... I just thought of something.  I may even have to retract what I said about Windows viruses are confined to the scope of the Wine bottle.

You guys remember how Wine maps ,for example, C:, D:, ... Y:,Z: drive letters to your /home/USERNAME directory right?  Then, viruses could indeed infect your other files in your home directory.  Well, it won't have the same effects, although, some viruses could render the files unreadable or corrupted.

Now, I'm really worried.  :confused: ...  ](*,)

---

