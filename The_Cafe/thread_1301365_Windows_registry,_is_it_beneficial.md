---
title: "Windows registry, is it beneficial?"
date: 2009-10-26
forum: The Cafe
---

### Post by dodle on 2009-10-26
I don't know a whole lot about the Windows registry, but I do know that the OS and many applications are dependent upon it.  Is this a benefit of the Windows OS?  I know that I can get quite annoyed with registry errors.  And, does Linux use a similar type of tool.  I haven't noticed anything like the Windows registry in Ubuntu.

Right now I am dealing with file association issues in Windows XP.

**Edit:** Sorry if I posted this in the wrong category [general help].

---

### Post by fancypiper on 2009-10-26
The Windows registry is the most horrible kludge I have ever seen.

Linux doesn't have anything as horrible.  Different distros have different package managers so the installed program info is kept in a database, AFAIK.

---

### Post by QIII on 2009-10-26
The registry may be the single worst feature of Windows.  It's not bad.  As fancypiper said, it's horrible.

*nix systems operate completely differently.  The entire distasteful concept can be removed from your vocabulary.

---

### Post by Exodist on 2009-10-26
There is no registry on Linux. Instead of keeping settings for programs in a file from hell. Your settings for programs are stored mostly in your home folder and are hidden with a ".". For example GIMPs settings are stored in a directory called ".gimp", which is hidden.

---

### Post by sea_monkey987 on 2009-10-26
without making assertions about the quality of the registry (i personally haven't had problems with it), the concept is whole-heartedly part of gnome.  run the command gconf-editor to see it.  in the back, these settings are stored as .xml files.  due to the nature of open-source, the way it works is transparent (it isn't in windows) but like i said, the concept is there in ubuntu.

---

### Post by CJ Master on 2009-10-26
> **sea_monkey987 said:**
> without making assertions about the quality of the registry (i personally haven't had problems with it), the concept is whole-heartedly part of gnome.  run the command gconf-editor to see it.  in the back, these settings are stored as .xml files.  due to the nature of open-source, the way it works is transparent (it isn't in windows) but like i said, the concept is there in ubuntu.

How gnome does it is completely different from the way Windows does it.

---

### Post by dodle on 2009-10-26
> **sea_monkey987 said:**
> without making assertions about the quality of the registry (i personally haven't had problems with it), the concept is whole-heartedly part of gnome.  run the command gconf-editor to see it.  in the back, these settings are stored as .xml files.  due to the nature of open-source, the way it works is transparent (it isn't in windows) but like i said, the concept is there in ubuntu.

Yeah, I have seen that and messed with its configurations.  But that is specifically for the gnome desktop right?  Most applications installed on your system won't have anything to do with it am I correct?

> **Exodist said:**
> There is no registry on Linux. Instead of keeping settings for programs in a file from hell. Your settings for programs are stored mostly in your home folder and are hidden with a ".". For example GIMPs settings are stored in a directory called ".gimp", which is hidden.

I have noticed that many open source/multi-platform applications do this on my Windows PC.  I have folders in my home directory like ".gimp-2.6" and ".VirtualBox", unfortunately in Windows the "." does not hide a folder.  But that is okay as I do not use the home folder in Windows for anything.

Another question:  Does anyone know if Windows 7 follows its predecessors by make use of a registry, or has Microsoft decided to do without it?  I have tested the beta on VirtualBox, but never thought to look and see if there was a registry.

---

### Post by sea_monkey987 on 2009-10-26
> **CJ Master said:**
> How gnome does it is completely different from the way Windows does it.

*sighs*

---

### Post by sea_monkey987 on 2009-10-26
> **dodle said:**
> Yeah, I have seen that and messed with its configurations.  But that is specifically for the gnome desktop right?  Most applications installed on your system won't have anything to do with it am I correct?



I have noticed that many open source/multi-platform applications do this on my Windows PC.  I have folders in my home directory like ".gimp-2.6" and ".VirtualBox", unfortunately in Windows the "." does not hide a folder.  But that is okay as I do not use the home folder in Windows for anything.

Another question:  Does anyone know if Windows 7 follows its predecessors by make use of a registry, or has Microsoft decided to do without it?  I have tested the beta on VirtualBox, but never thought to look and see if there was a registry.

if you don't mind the abrasive language, [http://linuxhaters.blogspot.com/2008/06/registry-is-dead-long-live-registry.html](http://linuxhaters.blogspot.com/2008/06/registry-is-dead-long-live-registry.html) describes the registry situation in ubuntu.  He briefly lists the differences between the registry based concept and the .folders and configuration files.  You be the judge of the merits between the two.  Of course, as you have probably guessed, I like the registry concept better, since it is standardized.

and yes, win 7 still has the registry.  even if MS was moving away from it (which they are not), they couldn't simply drop the registry due to legacy application support.

---

### Post by Xbehave on 2009-10-26
> **CJ Master said:**
> How gnome does it is completely different from the way Windows does it.
Yup it's in XML instead of binary making it slower.

Note: Also it's in XML instead of binary making it more readable and harder to corrupt.

---

### Post by 23meg on 2009-10-26
> **sea_monkey987 said:**
> without making assertions about the quality of the registry (i personally haven't had problems with it), the concept is whole-heartedly part of gnome.  run the command gconf-editor to see it.  in the back, these settings are stored as .xml files.  due to the nature of open-source, the way it works is transparent (it isn't in windows) but like i said, the concept is there in ubuntu.

The only real similarity is the hierarchical organization of items, visualized in a "Registry-like" fashion by gconf-editor (which is a graphical interface for manipulating GConf). The assertion that "the concept is the same" can only be valid if what you call "the concept" is limited to storing things in a hierarchical manner.

---

### Post by 23meg on 2009-10-26
> **Xbehave said:**
> Yup it's in XML instead of binary making it slower.

Note: Also it's in XML instead of binary making it more readable and harder to corrupt.

The data is not necessarily stored as XML. GConf backends are pluggable, the XML backend being only one (albeit most widely used and stable) of them.

---

### Post by Xbehave on 2009-10-26
> **23meg said:**
> The only real similarity is the hierarchical organization of items, visualized in a "Registry-like" fashion by gconf-editor (which is a graphical interface for manipulating GConf). The assertion that "the concept is the same" can only be valid if what you call "the concept" is limited to storing things in a hierarchical manner.
or the concept of having a single file containing keys which programs can read though an API.

---

### Post by Rinzwind on 2009-10-26
> **CJ Master said:**
> How gnome does it is completely different from the way Windows does it.

alt-f2
gconf-editor

How's that different?

---

### Post by mivo on 2009-10-26
> **fancypiper said:**
> Linux doesn't have anything as horrible.  Different distros have different package managers so the installed program info is kept in a database, AFAIK.

Config data is all over the place in Linux, and different distros and programs use different structures and systems. Arch is the most advanced and consistent here. Registry is certainly not great, but you overestimate the consistency and straight-forwardness of most Linux distros. That is one of the reasons why it is so unappealing to commercial game makers to release Linux versions.

---

### Post by dodle on 2009-10-26
What about Macs?  I understand they are based on Unix, does that mean their system is more Linux-like or do they a registry like Windows?

---

### Post by misfitpierce on 2009-10-26
Indeed. It is needed for windows to store all the backbones to all app's but it gets sloppy and does not maintain itself very well and when it gets really cluttered it slows down windows... One of the many reasons windows slows down over time really bad. There are registry cleaners but sometimes and only sometimes it deletes stuff you need and can actually be bad. Its all a risk you must take :P

---

### Post by dodle on 2009-10-26
> **misfitpierce said:**
> .... There are registry cleaners but sometimes and only sometimes it deletes stuff you need and can actually be bad. Its all a risk you must take :P

I've had to reinstall an OS two or three times because of something that was deleted from the registry.  The first time was my fault, I was dinking around with things I should have.  Another time, it was screwed up by a registry cleaner.

---

### Post by Xbehave on 2009-10-26
> **mivo said:**
> Arch is the most advanced and consistent here
How so? I thought arch did the least in messing with each apps personal style (or maybe that's slackware), but I'd never heard that it did anything fancy with configs (even its init system is nice old BSD style).
> That is one of the reasons why it is so unappealing to commercial game makers to release Linux versions.
Again how so? 
It is not hard to get API versions and games don't really care what other apps settings are. Additionally the dependencies games have tend to have system wide configs which are in /etc/ and so unaffected by individual distros and so their easy to read. Also if game developers develop a game against [LSB]("http://en.wikipedia.org/wiki/Linux_Standard_Base"), they can get compatibility against redhat,debian,fedora,ubuntu and just about all distros.

---

### Post by maflynn on 2009-10-26
The registry (along with dll hell) is the worst aspects to windows.  It's a single point of failure that malware writers found many ways to hide their malicous code and its so easy to mess up.

As a server admin, I'm in there quite a lot cleaning up crap left over by applications or correcting because applications working.

---

### Post by Xbehave on 2009-10-26
> **maflynn said:**
> The registry (along with dll hell) is the worst aspects to windows.  It's a single point of failure that malware writers found many ways to hide their malicous code and its so easy to mess up.

As a server admin, I'm in there quite a lot cleaning up crap left over by applications or correcting because applications working.
In principle it's no different to gconf (which to be fair is only for user settings so doesn't matter that much), it's only the implementation that sucks not the idea (which is in principle faster than gconf when using xml, ted tso (the ext4 guy) even suggested moving kde & gnome to compressed registry style configs to speed up boot and improve filesystem access.)

---

### Post by handy on 2009-10-26
I've always thought that the reason that the MS architects designed the registry, in combination with  /system was to protect commercial software from just being copied from one computer to another; as can usually be done on most other systems I've ever looked at.

For example I had to back up some software onto a CD from a person's Mac once, then replace the drive & rebuild the system.  I found it quite amusing that the backed up directory containing Photoshop, would run directly off of the CD when I attempted to run it just to see if it would. :)

With the AmigaOS you could just copy the directory or file from one machine to another; in *nix provided you meet the dependencies one way or another it's the same.

This situation doesn't suit people that want to sell you a license to use their software.  

In the case of MS, they created the monster called the registry to guard their own & other vendors software.  

Due to the registry's inherent complexity, poor design & the lack of any effective inbuilt maintenance - it is unfortunately also the prime cause of instability & insecurity for the MS systems that use it.

---

### Post by CJ Master on 2009-10-26
> **sea_monkey987 said:**
> *sighs*

Right, well, thank you for that gem of a comment.

> **Rinzwind said:**
> alt-f2
gconf-editor

How's that different?

Now I didn't say anything about the similarities of the interface, now did I?

---

### Post by drawkcab on 2009-10-26
> **handy said:**
> I've always thought that the reason that the MS architects designed the registry, in combination with  /system was to protect commercial software from just being copied from one computer to another; as can usually be done on most other systems I've ever looked at.

For example I had to back up some software onto a CD from a person's Mac once, then replace the drive & rebuild the system.  I found it quite amusing that the backed up directory containing Photoshop, would run off the CD when I attempted to run it just to see if it would. :)

With the AmigaOS you could just copy the directory or file from one machine to another; in *nix provided you meet the dependencies one way or another it's the same.

This situation doesn't suit people that want to sell you a license to use their software.  

In the case of MS, they created the monster called the registry to guard their own & other vendors software.  

Due to the registry's inherent complexity, poor design & the lack of any effective inbuilt maintenance - it is unfortunately also the prime cause of instability & insecurity for the MS systems that use it.

I always thought the same thing.  I don't really understand its purpose otherwise.  It is a horrible thing.  Every time I run the registry cleaner in windows, it has to fix like 9000 errors.

---

### Post by misfitpierce on 2009-10-26
> **dodle said:**
> I've had to reinstall an OS two or three times because of something that was deleted from the registry.  The first time was my fault, I was dinking around with things I should have.  Another time, it was screwed up by a registry cleaner.

If you still use windows and must run a registry cleaner, I would recommend just using CCleaner for registry cleaning and junk cleaning and keep it up to date. Friend uses on his and I used years ago and it never did me wrong. It seems to be safe enough on the registry and allows you to backup your registry before deleting... Sometimes it takes a few runs through registry to get clean but I wouldn't run it except maybe once every 1-2 months atleast. Don't go crazy and do it every week or so.

---

### Post by Mr. Picklesworth on 2009-10-27
> **23meg said:**
> The data is not necessarily stored as XML. GConf backends are pluggable, the XML backend being only one (albeit most widely used and stable) of them.

There is even a Windows Registry backend now ;)

Put me down as one who prefers centralized configuration, although there has to be a good split between what goes in the XML files (strings, check box type settings) and what belongs elsewhere (images...). The great thing with gconf is that it is REALLY easy to mark a key as mandatory or default across the system. Thus, really good, fine-grained control for administrators.

---

### Post by phrostbyte on 2009-10-27
Gconf supports comments for the entries, one of the huge weaknesses IMO of the Windows approach is the mess of key-value pairs and no clue what any of it does. Gconf also supports so called "instant" configuration, where changing a configuration key (from any app) is immediately reflected in the apps that consume it. It's storage is also separate from it's interface, so it can do XML backend, SQLlite backend, etc.

The concept of a central configuration store with type-checking/contracts is a good one, please don't let crappy implementations fool you. GConf is an actual good implementation, and I would love to see it become a Freedesktop.org standard, at least.

---

### Post by sea_monkey987 on 2009-10-27
i was thinking, isn't it dangerous that all the registry (gconf) settings are held in the home directory?  any program could make unauthorized changes to other programs' settings or even nuke the whole thing.

also phrostbyte, i did notice the instant changes while messing around with it.  that's very impressive indeed.  do you know how it's accomplished?  what i mean is that is it an event that is "pushed" to the program when the entry changes or does the program have to continuously check for an updated setting change?  i've done some amateur programming in c# on windows.  some registry keys were simply loaded into memory at the start of the program.  other keys, i made the program access them "on demand" when the user clicked something so the instant change phenomenon was there also.  continously checking the registry for the keys that were loaded on startup would have been just too wasteful.

---

### Post by JoshuaRL on 2009-10-27
> **sea_monkey987 said:**
> i was thinking, isn't it dangerous that all the registry (gconf) settings are held in the home directory?  any program could make unauthorized changes to other programs' settings or even nuke the whole thing.

Not really.  Have you ever deleted your .gconf folder?  Log out, log in, and you have a default Gnome install.  Sure, all of your customizations are gone, but everything works just fine.  Keeping proper user configs in userspace is what makes Linux as secure as it is.  Things that can harm the system proper are under root access.

---

### Post by Xbehave on 2009-10-27
> **sea_monkey987 said:**
> i was thinking, isn't it dangerous that all the registry (gconf) settings are held in the home directory?  any program could make unauthorized changes to other programs' settings or even nuke the whole thing.
This isn't so much a gconf problem as a desktop problem as far as i know no OS sandboxes desktop apps so any program you run can ruin all settings held in your home, (windows might actually get around this by only allowing A.exe to edit As registry settings but given that registry cleaners work I'm not sure it does)

> **JoshuaRL said:**
> Keeping proper user configs in userspace is what makes Linux as secure as it is.  
Being picky here, but this has nothing to do with userspace, just privilege separation (might be the wrong term, maybe file permissions is more accurate). userspace is to do with program execution, everything the kernel doesn't do is userspace, and everything it does is kernelspace, so if you run "sudo ps" your still in userspace. The rest of your post was perfectly correct I'm just nitpicking.

---

### Post by JoshuaRL on 2009-10-27
> **Xbehave said:**
> Being picky here, but this has nothing to do with userspace, just privilege separation (might be the wrong term, maybe file permissions is more accurate). userspace is to do with program execution, everything the kernel doesn't do is userspace, and everything it does is kernelspace, so if you run "sudo ps" your still in userspace. The rest of your post was perfectly correct I'm just nitpicking.

You are technically correct, the best KIND of correct.

Please excuse my improper usage of phraseology in reaching for a soundbite.  What I meant was that system-level changes need system-level permissions.  Even wiping .gconf out completely doesn't really harm the system, so it doesn't need to be permissions-protected.

---

### Post by chriswyatt on 2010-06-08
The registry is such a pain to fix if it gets corrupted, as opposed to some config file lying around in your hard drive.  E.g. if the part of you hard drive corrupted where the GIMP configuration was stored, in Ubuntu you probably wouldn't be able to run GIMP, in Windows the computer might not even boot.

There are tools to fix corrupted registries etc., these should really come with Windows.

---

### Post by whiskeylover on 2010-06-08
Centralized configuration has its pros and cons. Pro: easier to manage everything in one place, instead of having a bazillion .hidden files all over the home directory. Con: One part of the configuration can corrupt the entire tree, if not implemented properly.

---

### Post by Elfy on 2010-06-08
Thread closed - necromanced by spammers - who've long since departed.

---

### Post by whiskeylover on 2010-06-08
> **forestpiskie said:**
> Thread closed - necromanced by spammers - who've long since departed.

If they've departed, why not just delete their posts and let the discussion continue?

---

### Post by koenn on 2010-06-08
there's a similar, more recent thread nearby

[http://ubuntuforums.org/showthread.php?p=9418945](http://ubuntuforums.org/showthread.php?p=9418945)

---

