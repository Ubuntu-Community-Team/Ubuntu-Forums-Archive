---
title: "cleaner for linux?"
date: 2007-06-28
forum: The Cafe
---

### Post by weverjames on 2007-06-28
does anyone know any good software similar to pccleaner but for ubuntu?

---

### Post by malspa on 2007-06-28
I use CCleaner in Windows XP but I don't know what the comparable application would be for Ubuntu.  However, in Mepis I have KleanSweep installed, maybe you could use that.  I haven't tried it but I believe it's in the Ubuntu repositories.

I think CCleaner is a tool that will clean up the Windows registry.  Linux doesn't have a registry, so I'm not sure if a tool like CCleaner is necessary.

---

### Post by rejser on 2007-06-28
There is a apt addon that looks for unused packages and so on. Don't remember the name at the moment..
Install and remove everything with aptitude and there will be nothing to clean on your ubuntu-install.

---

### Post by starcraft.man on 2007-06-28
Firstly, from everything I've seen and read there isn't any need for a registry/computer cleaner product, Linux doesn't have the bloated useless blob Windows calls a registry. You won't see a slow down as you install more and more programs and remove them (at least I haven't). That said, you shouldn't be running more than your CPU can handle at once thats the only reason I think Linux would slow down.

Secondly, I (after having read up on those registry cleaners for Windows and used/tested a few, also having read articles by respected tech people) am of the opinion that all those registry cleaner products are "voodoo magic". At best, they make a horizontal move in performance and do little to nothing in terms of speed improvements, at worst they delete registry entries that are still in use by Windows. I would never use one to "clean" the registry. I have heard many stories of times when an entry was deleted from the registry by such products and then promptly some services in Windows became unstable/degraded in performance.

My advice to those who pay or use a registry cleaner, get a refund for the product, and go invest in a drive imaging software. Install a clean copy of Windows with all your applications, then when Windows slows down image your drive back (restore the "image") to the clean state and restore your data. That is a safe way of making your computer faster, it restores a clean bit for bit copy of the registry as it was in your clean state. Oh and things like XP system restore are not substitutes for a drive imaging suite. For those who want a free image suite, have a look at partimage and ghost4linux. 

Thats my two cents, take it as you will.

---

### Post by LookTJ on 2007-06-28
sudo apt-get autoclean?

---

### Post by malspa on 2007-06-28
> My advice to those who pay or use a registry cleaner, get a refund for the product, and go invest in a drive imaging software. Install a clean copy of Windows with all your applications, then when Windows slows down image your drive back to the clean state and restore your data. That is a safe way of making your computer faster.

Might be good advice, however CCleaner is free software, so forget the refund part.  I and my good friend (she uses ONLY XP) have used it for some years now with no problems at all, seems to be a good tool.  But I'll take your words to heart, never too old to learn something new, even at my age!

---

### Post by stmiller on 2007-06-28
[IMG]http://gallery.stacken.kth.se/albums/2006-clean/linux_color.sized.jpg[/IMG]

---

### Post by starcraft.man on 2007-06-28
> **malspa said:**
> Might be good advice, however CCleaner is free software, so forget the refund part.  I and my good friend (she uses ONLY XP) have used it for some years now with no problems at all, seems to be a good tool.  But I'll take your words to heart, never too old to learn something new, even at my age!

Just a note to that, I've never used CCleaner (didn't know it was free, most are trial based software in my experience) myself so can't vouch for it personally being good or bad. I simply know that as a whole, the entire class of registry cleaners has more or less been entirely rebuffed by those in the tech community that I trust. 

I might add that just because no problem presents, does not mean one is not present. I can point to numerous people who swear by Norton Products even though they are incredibly bloated security suites that do hog serious system resources (I've seen numbers from 10-30% of even modern CPUs) in order to provide near bullet proof security (supposedly). My opinion of course to these people would still be that Norton is bordering on a viral infection the way it hogs resources and degrades performance, if those people find that acceptable thats up to them.

Thats it for me on the subject.

Edit: Oh and lol at stmiller, that should be a trademark violation or something maybe Linux should threaten to sue to get license fees? :p

---

### Post by FuturePilot on 2007-06-28
> **starcraft.man said:**
> Firstly, from everything I've seen and read there isn't any need for a registry/computer cleaner product, Linux doesn't have the bloated useless blob Windows calls a registry. You won't see a slow down as you install more and more programs and remove them (at least I haven't). That said, you shouldn't be running more than your CPU can handle at once thats the only reason I think Linux would slow down.

Secondly, I (after having read up on those registry cleaners for Windows and used/tested a few, also having read articles by respected tech people) am of the opinion that all those registry cleaner products are "voodoo magic". At best, they make a horizontal move in performance and do little to nothing in terms of speed improvements, at worst they delete registry entries that are still in use by Windows. I would never use one to "clean" the registry. I have heard many stories of times when an entry was deleted from the registry by such products and then promptly some services in Windows became unstable/degraded in performance.

My advice to those who pay or use a registry cleaner, get a refund for the product, and go invest in a drive imaging software. Install a clean copy of Windows with all your applications, then when Windows slows down image your drive back (restore the "image") to the clean state and restore your data. That is a safe way of making your computer faster, it restores a clean bit for bit copy of the registry as it was in your clean state. Oh and things like XP system restore are not substitutes for a drive imaging suite. For those who want a free image suite, have a look at partimage and ghost4linux. 

Thats my two cents, take it as you will.
All that is very true. I've had an experience with those Registry cleaners where it did remove some important keys which messed a whole bunch of stuff up. I don't trust those things. They think certain keys are unimportant but when in fact they are. 

And yes Linux does not slow down at all, no matter how much stuff you have installed. Ubuntu is still running as fast as when I first installed it.


> **stmiller said:**
> [IMG]http://gallery.stacken.kth.se/albums/2006-clean/linux_color.sized.jpg[/IMG]
ROFL!!:lolflag:

---

### Post by DC@DR on 2007-06-28
Have you guys heard about this: Gconf-cleaner: [http://code.google.com/p/gconf-cleaner/](http://code.google.com/p/gconf-cleaner/)
Review for it: [http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html](http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html)

---

### Post by Rui Pais on 2007-06-28
and there are deborphan and gtkorphan, to remove unneed libs and stuff from old pckages installs and trials...
but i'm not sure if they are safe to use with ubuntu...

---

### Post by Jouke74 on 2007-06-28
Well there are a few options already with apt:

** Sudo apt-get clean** 
Will wipe out the downloaded files for packages you installed or updated (somewhere from the harddisk, don't know where exactly).

** Sudo apt-get autoclean** 
Will do the same, however this includes the dependencies that were also downloaded.

** Sudo apt-get remove** 
Will remove all files that are not needed for your system according to apt. It asks for conformation so you can check what it wants to remove. As with the registry cleaners, do check this carefully.

** Sudo apt-get autoremove** 
Will do the same as previous, including all underlying dependencies which are not necessary anymore.

---

### Post by Tundro Walker on 2007-06-28
I noticed that after un-installing some apps, they'd leave behind .conf files and such.  I apt'ed KleanSweep, and ran it.  It found all kinds of empty files and such.  I deleted things that didn't look important, and it worked pretty good.  But, there were some things that looked "dangerous", so I skipped them (IE: programs that it found that I had no clue if it was actually broken or orphaned or not.)  I'd exercise caution when using it, because even as cautious as I was, I must have deleted some .conf file for my panels or something, because they've been kinda finiky ever since (like I'll get an error saying an applet can't run or be found...then it'll strip a lot of my applets off my panel, and I have to go add them again...annoying.)

In the "Tutorials" section, WackToMack came up with one talking about [how to clean your system]("http://ubuntuforums.org/showthread.php?t=140920&highlight=clean").  Talked about the apt-get autoclean and such, but also talks about using deborphan to use CLI to remove orphans, or how to setup a filter in Synaptic to search for Orphaned packages and remove them that way.  Works pretty good.

---

### Post by airtonix on 2007-06-28
to totally remove a program (including its conf files etc etc) use synaptic to remove it...

to do this you ave to right click on the software package you want to "completey remove". and select that option..

it will then tell you what other packages it might need to remove.

there is also a prog called fslint....think it does what kleansweep does

---

### Post by Andrew.Z on 2008-12-30
> **weverjames said:**
> does anyone know any good software similar to pccleaner but for ubuntu?

[BleachBit is a registry cleaner for Linux](http://bleachbit.sourceforge.net/)

> **malspa said:**
> I think CCleaner is a tool that will clean up the Windows registry.  Linux doesn't have a registry, so I'm not sure if a tool like CCleaner is necessary.

[Myth: Linux Doesn't Need a Registry Cleaner ](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html)

> **starcraft.man said:**
> I simply know that as a whole, the entire class of registry cleaners has more or less been entirely rebuffed by those in the tech community that I trust. 

On what grounds?  I agree the claim of improving performance is overrated, but cleaning dangling references can be useful.  See the article above.

---

### Post by jrusso2 on 2008-12-30
> **Andrew.Z said:**
> [BleachBit is a registry cleaner for Linux](http://bleachbit.sourceforge.net/)



[Myth: Linux Doesn't Need a Registry Cleaner ](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html)



On what grounds?  I agree the claim of improving performance is overrated, but cleaning dangling references can be useful.  See the article above.

There is not such thing as a " smart cleaner" for Windows or Linux and I have had extensive experience with the Windows ones and I have been more damage caused then help.

See Tundra Williams post above this is typical of damage these cleaners can do.

Also Linux does not have a registry so not sure what those Linux registry cleaners do.

---

### Post by oldos2er on 2008-12-30
How is BleachBit different from fslint?

---

### Post by ubuntu-freak on 2008-12-30
> **Jouke74 said:**
> Well there are a few options already with apt:

** Sudo apt-get clean** 
Will wipe out the downloaded files for packages you installed or updated (somewhere from the harddisk, don't know where exactly).

** Sudo apt-get autoclean** 
Will do the same, however this includes the dependencies that were also downloaded.

** Sudo apt-get remove** 
Will remove all files that are not needed for your system according to apt. It asks for conformation so you can check what it wants to remove. As with the registry cleaners, do check this carefully.

** Sudo apt-get autoremove** 
Will do the same as previous, including all underlying dependencies which are not necessary anymore.

 
+1
 
The above is all you need. You can use the following combo too:
 
**sudo apt-get clean && sudo apt-get autoremove**
 
On a sidenote, you can cause problems with symlinks if you go around deleting apparently unused folders and files, so don't be too obsessive when cleaning up your system.

P.S. The command "apt-get autoclean" only removes old package files that can no longer be downloaded, so "apt-get clean" is actually more thorough.

---

### Post by Andrew.Z on 2008-12-31
> Also Linux does not have a registry so not sure what those Linux registry cleaners do.

Yes, Linux has many registries.   For example, menu entries are registered in about 6 different places, file associations are registered in several others, auto-start applications in a few more, etc.

> **oldos2er said:**
> How is BleachBit different from fslint?

fslint is application agnostic, so it looks for things like duplicate files and broken symlinks.  BleachBit (currently) is application-oriented, so it deletes things like Firefox cache, broken menu entries (by parsing the .desktop file), VIM history, and Flash cookies.

BleachBit is faster than fslint because fslint often scans large directories.

---

### Post by koenn on 2008-12-31
> **Andrew.Z said:**
> Yes, Linux has many registries.   For example, menu entries are registered in about 6 different places, file associations are registered in several others, auto-start applications in a few more, etc.

Linux configuration is stored in text files. They only get read when an application needs them. If the app in question has been removed but the config file hasn't been removed,  all you are suffering from is a few KB of text  on your hard disk.

Now with the Windiows registry :
a/ it grows every time an application adds a key, and it doesn't schrink again, even if a key is deleted
b/ It's loaded to memory (some say entirely, but it may also be just large chuncks of it) when the system boots (hardware conf) and when a user logs on (user conf)
So you have an ever expanding blob taking up memory every time the system boots.
That's why Windows systems over time boot more slowly (the registry grows so it takes longer to load it) and might become sluggish (less available memory). Registry cleaners claim to remedy this.

Some orphaned text files taking up a few KB of disk space don't have that effect. The only gain in removing them is to recover tose few bytes of disk space.
Also, calling a bunch of text files "a registry" in the sense of the Windows registry, just because they happen to be used for the same purpose of holding configuration data,  is misleading, and utter nonsense. Are you a salesman ?

---

### Post by geoken on 2008-12-31
Thanks for the link Andrew. I think most people are completely missing the point that CCleaner is a privacy sweeping app first, and a registry cleaner second.

---

### Post by Dharmachakra on 2008-12-31
> **Andrew.Z said:**
> 
On what grounds?  I agree the claim of improving performance is overrated, but cleaning dangling references can be useful.  See the article above.

Especially for switching between different versions of the same software. Ever tried a few different video drivers on Windows without manually removing their registry entries? You'll surely get a headache within a few days.

---

### Post by benny bronx on 2008-12-31
Just tried out bleachbit.  Not bad, although it did wipe out my ff bookmarks (I always have a back-up).  Also, if you set your flash preferences through the adobe settings manager, cleaning flash with the program will delete those settings.  I'd say it is a fairly useful, though somewhat unnecessary, program for me and should be used with some caution.  It is, however, less dangerous than kleansweep, in my opinion of course.

Edit: My restored bookmarks disappeared when I closed and re-opened firefox.

---

### Post by oldos2er on 2008-12-31
> **benny bronx said:**
> Just tried out bleachbit.  Not bad, although it did wipe out my ff bookmarks (I always have a back-up). 

 After hearing the differences between bleachbit and fslint, I see no reason to favor the former over the latter--especially since I seldom run fslint anyway.

---

### Post by spupy on 2009-01-01
> **DC@DR said:**
> Have you guys heard about this: Gconf-cleaner: [http://code.google.com/p/gconf-cleaner/](http://code.google.com/p/gconf-cleaner/)
Review for it: [http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html](http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html)

Oh my god, a registry cleaner for Linux... The end is near!

By the way, anyone know how to clean /tmp. It is not big but infested with some files I can't read.

---

### Post by oldos2er on 2009-01-01
"anyone know how to clean /tmp"

 Reboot.

---

### Post by Andrew.Z on 2009-01-06
> **benny bronx said:**
> Not bad, although it did wipe out my ff bookmarks (I always have a back-up).  

Good for you to have a backup!

Please note BleachBit warns, "The *places* database contains URLs including bookmarks and visited URLs."   The reason this is one option is Firefox v3 stores URL history and bookmarks in one file called Places.  In the future, BleachBit will probably allow each part of this Places file to be deleted separately.

> anyone know how to clean /tmp. 

BleachBit includes /tmp/ as an option, and it also cleans /var/tmp/ (which is less obvious and on my system contained huge files).

> It is, however, less dangerous than kleansweep

BleachBit was designed to be less dangerous and more useful than Kleansweep and FSLint, but the old saying is, "One man's junk is another man's treasure."

---

### Post by -jay- on 2009-01-22
thanks for the link andrew

---

