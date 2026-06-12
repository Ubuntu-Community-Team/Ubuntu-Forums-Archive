---
title: "Now, let's all fight about dconf."
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 3vi1 on 2011-11-16
Long rant mode engaged...  (Feel free to back me up or post anti-rants to educate me)

On one of my systems (a CR-48 ), I've had to rename/delete ~/.config/dconf/user more than a half dozen times (and lose *all* related settings) during the Oneiric and now Pangolin cycles in order to get Unity to login.

I'm pretty tolerant of the breakage, because I know what to expect when running alpha software.  It's not the breakage that aggrevates me - it's the design, and my impression that we're headed in an inferior direction.

Anyone who's read The Art of Unix Programming, or simply needed to make a simple change across a lot of systems, knows that there are inherent benefits to text files.  That is, you can update them from a ton of simple utilities that work with text streams, and they never all corrupt at once.  XML files, while harder to manipulate than flat formats, still share in most of this benefit.

Now, binary formats have a counterposing strong point too: You can serialize a lot of settings into a file that can be read quickly.  But, that's about it.

Solution?:
---------
I don't like to whine without offering solutions, so I'm throwing this design option there:  Why not store all of the settings in XML files, but cache a compressed binary version on write?  Allow apps to update the text files, then call a dcconfig or something to rebuild the binary.  That way, if the binary becomes corrupt you can delete the xml file for the last app you touched and re-run dcconf.  The design of dconf seems predicated on their being few writes vs. reads, so this does not sound like it would cause any real loss of performance.

I know performance is somewhere we need to improve, but let's not throw out the baby with the bath water.

As a disclaimer:  I only know what I know about dconf from observation and decapitation.  Maybe the designers have a better plan in place for the future.

---

### Post by seeker5528 on 2011-11-16
I assume '~/.dconf/user' should have been '~/.config/dconf/user' since '~/.donf/' doesn't exist on my system but '~/.config/dconf/' does. 

I'm not a big fan of binary configuration files, but I have not had any issue the would give me a reason to delete the dconf configuration file.

If you are deleting it because of corruptions, then you have to question 'Why is this file getting corrupted?'.

Seems more like a symptom of some other issue than a problem with dconf.

That's not to say dconf couldn't to things in a way to reduce the possibility of corruption and increase the likely hood of automated recovery if corruptions do occur, but in the face of instability due to less stable drivers, software, packaging issues leading to bad combinations of stuff or problems comleting an install/uninstall, etc... there is always potential that something will become corrupt. 

Later, Seeker

---

### Post by 3vi1 on 2011-11-16
> **seeker5528 said:**
> I assume '~/.dconf/user' should have been '~/.config/dconf/user' 

Correct, and fixed!

---

### Post by 3vi1 on 2011-11-16
> **seeker5528 said:**
> If you are deleting it because of corruptions, then you have to question 'Why is this file getting corrupted?'.


That's the wonderful thing about binary formats:  Who the hell knows if it's corrupt, or if it's just that one of my dozens of custom settings doesn't work with a new version of one of the packages I just updated.  :)

You make a good point though:  It may have been corrupt, I did use to have drive problems on that machine before I replaced it (I think I've had to delete dconf only once or twice since then).  But that brings forward another inherent design flaw:  If you have an app that writes it's settings a lot, your chance of corrupting your *entire* desktop settings are multiplied by the activity of that app.  It's a wonderful multiplier for potential problems.

I can't recreate the problem at will, or I'd have troubleshot it and filed a bug.  I'll back up my dconf dir now though, and try to resist the urge for daily tweeks to my settings.  Maybe if I submit the two versions of the binary file to someone with the right binary tools they can tell me why one works and the other doesn't.  After all, I, and I'm sure everyone else here, doesn't mind publicly uploading a file that contains the settings for every one of their apps - and we all know for sure that no programmer will be stupid enough to stick sensitive info in that file in the future.  ;)

---

### Post by effenberg0x0 on 2011-11-16
> **3vi1 said:**
> Anyone who's read The Art of Unix Programming"

... would be smart enough to:

- diff the binary "user" file when in the desired system state versus when in other states and create a patching solution with the patch command or even sed, to be auto executed when the user logs in.
- Simply keep a backup of the file when in the desired system state, and have a script autocopy it over the system one at every login.
- Use apt (or for God's sake even Google) to easily find out there a program called dconf editor, find out what the problem is (key/setting) using the GUI or command-line tool, use the program dconf to enforce the desired key/setting at every boot via script.

I can continue. I won't.

**EDIT:** I recommend this book: [http://goo.gl/3Vfhg](http://goo.gl/3Vfhg)

---

### Post by seeker5528 on 2011-11-16
> **3vi1 said:**
> That's the wonderful thing about binary formats:  Who the hell knows if it's corrupt, or if it's just that one of my dozens of custom settings doesn't work with a new version of one of the packages I just updated.  :)

If you make that many changes, you do increase the 'human error' factor. If some software doesn't handle the migration of it's own settings as it relates to dconf, that would be (to me) a bug in the software that failed to migrate/delete the old setting. 

An incompatible-with-some-software setting, shouldn't prevent you from using dconf-editor to find the incompatible setting. Less convenient that scrolling through a text file, but more convenient (for me at least) than having to attempt to decypher some may-be-considered-text-but-certainly-isn't-plain XML stuff.

> But that brings forward another inherent design flaw:  If you have an app that writes it's settings a lot, your chance of corrupting your *entire* desktop settings are multiplied by the activity of that app.  It's a wonderful multiplier for potential problems.

How do you define a lot?

If an application wants to update it's settings *that* much, that is it's own design flaw.

If dconf doesn't handle corrupted data coming from these applications or has it's own problem that result in the database being corrupted, than that is a problem with dconf. It's still pretty young yet, hopefully more robustness (assuming that's found to be an issue) and more tools for backup/repair/cleaning of the database, etc... will come along as it develops.

At least you *can* delete the database file and get back to some semblance of a workaing state.

If you dual boot with Win7/Vista, then while in Linux try renaming your user hive file (the user specific registry hive) '/media/your-windows-parition/users/your-user-profile-directory/ntuser.dat', then boot your windows installation and try logging in and see how far that gets you.

And if ntuser.dat gets corrupted.... [shudder](http://windows.microsoft.com/en-US/windows-vista/fix-a-corrupted-user-profile)....

Later, Seeker

---

### Post by 3vi1 on 2011-11-17
> **effenberg0x0 said:**
> ... would be smart enough to:

- diff the binary "user" file when in the desired system state versus when in other states and create a patching solution with the patch command or even sed, to be auto executed when the user logs in.
- Simply keep a backup of the file when in the desired system state, and have a script autocopy it over the system one at every login.
- Use apt (or for God's sake even Google) to easily find out there a program called dconf editor, find out what the problem is (key/setting) using the GUI or command-line tool, use the program dconf to enforce the desired key/setting at every boot via script.

I can continue. I won't.

**EDIT:** I recommend this book: [http://goo.gl/3Vfhg](http://goo.gl/3Vfhg)

I actually had been using option #2 (but only manually copying it on corruption).  So your soulution is to make everyone suffer until they reach our level?  "Goodbye new users".

---

### Post by 3vi1 on 2011-11-17
> **seeker5528 said:**
> 
If an application wants to update it's settings *that* much, that is it's own design flaw.


Normally, I would agree.  But to play devil's advocate, let's not assume that every program would never have a use for keeping an up-to the minute state.

How about the contrived example of distributed computing apps and such that might want to write their state every few minutes?  Yes... yes... they should do it to another file, since dconf is now a horrible solution for this kind of app... but did any of the previous solutions suffer from this drawback or give them the ability to corrupt all of your system settings?

If we tell programmers "here's a call that can easily save app settings", they'll use it without any further thought.  So, at the very least we should build systems resilient to bad practices.  Make the dconf write commands start logging "Program ____ taints system integrity." or something to the log if it writes too often... but let's not leave ourselves open for it to ruin the system and give the user the impression that "Ubuntu is a buggy POS" instead of "Program _____ is a poorly performing POS".

---

### Post by effenberg0x0 on 2011-11-17
1) [http://live.gnome.org/dconf/SystemAdministrators#Key_File_Directories](http://live.gnome.org/dconf/SystemAdministrators#Key_File_Directories)
2) sudo apt-get install dconf-tools
3) 

It can't be any simpler to read / write to dconf via bash, C, any api, etc. There are three basic things you can do. Read, Write and List. That's it. I won't do the entire thing because it has no use to me. But check the GetRootKeys function and do something like what I commented below to navigate throw the paths of each root using arrays, like KEY[${#KEY[@]}] == `dconf list $KEY[${#KEY[@]}-1]/ 
 
```
#!/usr/bin/env bash
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
#set -x
#set -v
###############################################################################
# Lines kept under 80 characters max for easier console editing! 
# Use hashes as guides on console / non-gui IDEs and editors. 
# Indentation = 4 spaces (no tabs).
###############################################################################
#
# dconf-explorer.sh
#
# A very lame draft on how to dump data from dconf
# which is actually a stupid thing to do.
# 
# Effenberg0x0 <launchpad.net/~effenberg0x0>, 2011

PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin

ROOTKEY=""
KEY=""
KEY_VALUE=""

function GetRootKeys {
    for ((i=1; i<=`dconf list / | wc -l`; i++)) {
        ROOTKEY[$i]=$(dconf list / | awk NR==$i)
    }
}         

#function ExploreKeys {
#    for ((i=1; i<${#ROOTKEY[@]}; i++)) {
#        Echo "Exploring rootkey ${ROOTKEY[$i]}"
#        KEY[0]=${ROOTKEY[$i]}
#        TREE_ENDED="false"
#        while [[ $TREE_ENDED != "true" ]]; do
#            if [[ `dconf list /${KEY[${#KEY[@]}-1]}` != "" ]]; then
#                KEY[${#KEY[@]}]=`dconf list /${KEY[${#KEY[@]}-1]}`
#                #pipe the key to another function that use sed on it to convert to xml, json, whatever you feel like,
#            if [[ `dconf list /${KEY[${#KEY[@]}-1]}` > 1 ]]; then
#                #Theres a bisection here. Mark this position, take one path and then another.
#            fi                
#            if [[ `dconf list /${KEY[${#KEY[@]}-1]}` == "" ]]; then
#                #end of the path. use dconf read to get the key values.
#                TREE_ENDED="true"
#                unset KEY
#            fi
#        done
#    }        
#}

#function DoSomethingWiTextUsingSedAndWriteItToAFile {
#Get freaking $1 | sed something >> somefile.
#}

function main {
GetRootKeys
ExploreKeys
SayGoodByeWaveAndExit
}

case $1 in
    export)
    main export
    ;;
    import)
    main import
    ;;
    *)
    echo -e "\yada yada yada yada yada yada yada yada yada yada yada yada yada yada yada yada "
    echo "USAGE: Turn on PC, sit in front of it, look at the magic screen, yada yada yada"
    exit 1
    ;;
esac

```

---

### Post by effenberg0x0 on 2011-11-17
4) dconf 0.9.0 (dont think it's in Ubuntu yet, not sure) supports dump and reload commands:

```
dconf dump / >> dconf_dump.txt

[org/gnome/desktop/sound]
event-sounds=true
theme-name='__custom'

[org/gnome/evince/default]
window-ratio=(1.7126050420168066, 1.1199524940617578)

[org/gnome/file-roller/dialogs/batch-add]
default-extension='.zip'

[org/gnome/file-roller/dialogs/extract]
overwrite=true
recreate-folders=true
skip-newer=false

[org/gnome/file-roller/general]
encrypt-header=false

[org/gnome/file-roller/listing]
list-mode='as-folder'
name-column-width=250
show-path=false
sort-method='name'
sort-type='ascending'

```

---

### Post by Paddy Landau on 2011-11-17
I must agree with the OP. I find it disturbing that dconf reminds me of the Windows registry...

In today's computing world, I hardly think that reading a text file is a great drain on a computer's resources. If it was made binary for speed or to reduce the file size, I think that is the wrong decision. But maybe there is another reason for the decision.

Having said that, you may want to [read another opinion]("http://askubuntu.com/questions/34490/why-the-controversy-about-switching-from-gconf-to-dconf").

---

### Post by effenberg0x0 on 2011-11-17
SAP is marketing "In Memory Computing", that is, loading very critical DBs to RAM to gain some speed, avoid the HDD bottlenecks, etc. The truth is that no single HDD, RAID, Fibre Channel Storage is fast enough for todays needs, OSs and applications. Just install 16GB of 1.666MHz RAM on a PC, create a 12MB RamDisk, change some env vars to be able to install and run apps, libs, includes from it and test - it's clearly ridiculously faster than any high-performance SATA3 HDD RAID, Sata 3 SSD RAID, SAS, SCSI, anything you can possibly buy. 

It's not so critic when you have just a standard user, using a desktop to let the world know he is having coffee and cookies on Facebook. But considering large clusters, in which density vs capacity is the game, datacenters, etc it makes sense. 

Storage technologies manufacturers failed to evolve their products and follow the rhythm in which other components evolved. And now they're working with a very low margin, small investment in R&D, etc. Things won't change so soon. At most, SSDs are getting a little cheaper. That's it.

Any software-based technology to speed up read access, cache parts of config to ram, etc is very welcome. Dconf was well thought in this sense, also allowing configs to be written in text files and immediately absorbed by the system (a typical user will write much less than he reads from HDD). Dumping it's contents for daily, hourly, etc backup demands no knowledge using the provided tools and API.

---

### Post by seeker5528 on 2011-11-17
> **3vi1 said:**
> Normally, I would agree.  But to play devil's advocate, let's not assume that every program would never have a use for keeping an up-to the minute state.

How about the contrived example of distributed computing apps and such that might want to write their state every few minutes?  Yes... yes... they should do it to another file, since dconf is now a horrible solution for this kind of app... but did any of the previous solutions suffer from this drawback or give them the ability to corrupt all of your system settings?

I guess I would need an actual example to wrap my head around what you are trying to get at.

I don't know the details of dconf and how it manages things, but... As far as the command line tools are concered they treat the data as a '/directory/directory/data' kind of thing, the documentation indicates data is stored in a database, so it doesn't seem likely to me that dconf writes the whole file every time a program requests a change, but you never know.  

Browsing with dconf-editor I'm not seeing any preferences that seem like they would need more than an occasional update, even if they did changes are small bits of information.

Information about state is a whole other thing, that's the realm of dbus, lock files, '/tmp/whatever/whatever', or whatever other mechanisms programs might use to track dynamic/transitory information.

That's not to say a program couldn't use dconf to keep information about it's state, but I can't think of a reason why a program would be designed that way.

If something is relatively new and you experience problems with it it's natural to question how good it is, but my attempts to google for dconf corruption issues doesn't give me any obvious indication that corruption has been a significant problem. 

Later, Seeker

---

### Post by Mr. Picklesworth on 2011-11-18
> **3vi1 said:**
> You make a good point though:  It may have been corrupt, I did use to have drive problems on that machine before I replaced it (I think I've had to delete dconf only once or twice since then).  But that brings forward another inherent design flaw:  If you have an app that writes it's settings a lot, your chance of corrupting your *entire* desktop settings are multiplied by the activity of that app.  It's a wonderful multiplier for potential problems.

That's why dconf works over dbus. It provides a single, reliable and trustworthy program on the session bus whose job is storing and retrieving settings. Therefore, if your settings *are* being corrupted, the problem is in that one place.
This is *also* something we can categorize under the Unix philosophy: one tool that does one thing well ;)
There's lots about dconf's design over on [its wiki page](http://live.gnome.org/dconf).
I agree with 3vi1 that exposing settings *directly* as text files would be cool, and it's probably quite doable with fuse or gvfs.

---

### Post by MacUntu on 2011-11-19
Accessing hundreds of text files does not only have advantages. ;)

Haven't had any issues with the dconf DB file so far.

---

### Post by seeker5528 on 2011-11-21
> **MacUntu said:**
> Accessing hundreds of text files does not only have advantages. ;)

Is there a translation for this, for those of us who natively speak American English? ;)

Or was 'only' mistakenly included.

No judgements from me, I've had plenty of 'That made perfect sense in my head.' moments, often due to thinking in shorthand and forgetting to expand on things for the benefit of those people who do not live inside my head. :oops: :p

Later, Seeker

---

### Post by MacUntu on 2011-11-21
"Does not only have X (but also Y)", where "(but also Y)" has been ommitted because I thought it should be derivable from the context. Sorry for the Yoda-speak. My not too shabby English went down the toilet when I started using the internet. :-P

---

### Post by seeker5528 on 2011-11-21
So in other words....

'Accessing hundreds of text files does not only have advantages but...'

Which is one of the possiblities I thought of, just wasn't sure.

Later, Seeker

---

### Post by effenberg0x0 on 2011-11-21
The characteristic of having a thousand text files in a Linux system is a legacy from when a Unix server had 4 servers running. No one can possibly think that is a good thing today. Ok, it's easier to edit and set up these files, great. Question is: How many times have you edited all your text config files today? 1.000, 10.000, 100.000?

It's insane. Even windows is smarter using the registry. 

Given that dconf CAN BE EDITED USING TEXT, they managed to not kill the "Linux way" through which any Linux user is used to fixing, tweaking and learning a system, while still providing an obvious architectural improvement. Any statistics one can make, using known tools, about how many times your HDD is accessed to Read and Write config files during a standard session, makes it clear they had to focus on enhancing the reading capabilities of this software, while it's writing-routines didn't need much tweaking. It's absolutely rational.

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> It's insane. Even windows is smarter using the registry.
Uh, well, not the way the Windows registry was implemented. As one example: the problem that Windows programs stored their  settings in the registry, which is why in Windows you need to deinstall  and reinstall a program to reset its settings, whereas of course up to now that  has been nonsensical in a Linux environment.

If dconf retains the standard Linux way that a user cannot make a change that affects anyone else (unless that user is root), then, yes, OK, that's perfectly acceptable. Otherwise, I am concerned indeed that it will become the spaghetti mess that the Windows registry became. 

The rest of your explanation clarifies nicely why the change was made; thank you.

---

### Post by effenberg0x0 on 2011-11-22
> **Paddy Landau said:**
> Uh, well, not the way the Windows registry was implemented. As one example: the problem that Windows programs stored their  settings in the registry, which is why in Windows you need to deinstall  and reinstall a program to reset its settings, whereas of course up to now that  has been nonsensical in a Linux environment.

**If dconf retains the standard Linux way that a user cannot make a change that affects anyone else (unless that user is root), then, yes,** OK, that's perfectly acceptable. Otherwise, I am concerned indeed that it will become the spaghetti mess that the Windows registry became. 

The rest of your explanation clarifies nicely why the change was made; thank you.

I believe it will retain that, for sure, as each user has it's own $HOME/.config/dconf/user accessible by it's PIDs. Changing the per-user settings/permissions would go way beyond the chosen method for settings storage, as it would simply break a lot of Linux existing code that counts on it. I have noticed that I generally have two dconf-service PIDs running here. One owned by root and one owned by me.

---

### Post by MacUntu on 2011-11-22
> **Paddy Landau said:**
> Uh, well, not the way the Windows registry was implemented. As one example: the problem that Windows programs stored their  settings in the registry, which is why in Windows you need to deinstall  and reinstall a program to reset its settings, whereas of course up to now that  has been nonsensical in a Linux environment.

If dconf retains the standard Linux way that a user cannot make a change that affects anyone else (unless that user is root), then, yes, OK, that's perfectly acceptable. Otherwise, I am concerned indeed that it will become the spaghetti mess that the Windows registry became. 

If I look at my current dconf DB it already looks like mess. If you uninstall a program, all the settings you made (which aren't default) are kept in the DB. No surprise, but unlike the ~/.gconf based way there seems to be no easy way to remove them in case you want to.

---

### Post by effenberg0x0 on 2011-11-22
> **MacUntu said:**
> If I look at my current dconf DB it already looks like mess. If you uninstall a program, all the settings you made (which aren't default) are kept in the DB. No surprise, but unlike the ~/.gconf based way there seems to be no easy way to remove them in case you want to.

I disagree:
```
[09:48 AM][ahsl:AL-DESK:/]
$ dconf help reset
Usage:
  dconf reset [-f] PATH

Reset a key or dir.  -f is required for dirs.

Arguments:
  PATH      Either a KEY or DIR
  KEY       A key path (starting, but not ending with '/')
  DIR       A directory path (starting and ending with '/')


```

A simple example:
```
[09:50 AM][ahsl:AL-DESK:/]
$ dconf read /apps/indicators/sound/interested-media-players 
['banshee', 'rhythmbox']

[09:51 AM][ahsl:AL-DESK:/]
$ dconf reset /apps/indicators/sound/interested-media-players 

[09:51 AM][ahsl:AL-DESK:/]
$ dconf read /apps/indicators/sound/interested-media-players 
```

It's pretty obvious isn't it?

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> I believe it will retain that, for sure, as each user has it's own $HOME/.config/dconf/user accessible by it's PIDs.
Good, I'm glad to read that.

> **effenberg0x0 said:**
> I disagree: ... It's pretty obvious isn't it?
That is sarcastic, isn't it? To remove the settings for a specific program the old way, you found the folder and deleted it. Now you need to find the various keys and reset all of them.

---

### Post by effenberg0x0 on 2011-11-22
> **Paddy Landau said:**
> Good, I'm glad to read that.


That is sarcastic, isn't it? To remove the settings for a specific program the old way, you found the folder and deleted it. Now you need to find the various keys and reset all of them.

Not really! type dconf read and press tab twice to see the tree, like you could do on a file system. You can also visually see all of them using dconf-editor gui tool. You can also search specific keys using gsettings, grep, etc. example: gsettings list-schemas | grep -i sound

Do not forget that the only reason you think editing files is easier is because you know where the files are. For example, I don't think twice when I want to edit xorg.conf, resolv.conf, interfaces, smb.conf, grub.conf, etc. None of these files could ever be deleted, but had to be edited. Mostly everything in /etc can't be deleted, never could. An ordinary non-technical user will never know the location to all of the txt config files. It's much easier to click on find in a gui tool, change the needed values using such tool. Cli commands like the one I just used as an example will probably only be used by technical users/scripting.


**EDIT:** Also, it is very common for programs to need to change one or two values inside a config file, not delete it entirely. When it's a text file, we need to rely on complicated coding to find the proper key and edit it. Or use json, xml, etc, which can be externally edited easily. gtk programs generally have to call glib to read the files, locate the key, etc. Most bash scripts need to rely on a composition of sed/awk that is greek to newbies. Why not make it easier?

---

### Post by MacUntu on 2011-11-22
> **effenberg0x0 said:**
> ...
Thanks! Though the -f parameter doesn't work for paths, and given that it says 'reset' and not 'remove' (plus the fact that this didn't work in earlier versions) make me believe that this is a bug rather than expected behavior. 

Gotta talk to the GNOME devs about it. :-)

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> Not really! ...
All right, that makes sense. But it would be good to have a standard where a program stores everything under a single main key so that it is easy to delete the entire tree without affecting everything else.

---

### Post by effenberg0x0 on 2011-11-22
> **MacUntu said:**
> Thanks! Though the -f parameter doesn't work for paths, and given that it says 'reset' and not 'remove' (plus the fact that this didn't work in earlier versions) make me believe that this is a bug rather than expected behavior. 

Gotta talk to the GNOME devs about it. :-)

> **Paddy Landau said:**
> All right, that makes sense. But it would be good to have a standard where a program stores everything under a single main key so that it is easy to delete the entire tree without affecting everything else.

I agree with both: It's far from organized right now. The GUI tool lacks essential features and the command-line tools have missing options and bugs. It's too alpha still. An example: dconf --help doesn't show you that you can use dconf dump. Other options are undocumented or not entirely implemented. There's much room for improvement in the ways of managing it. It seems to me that, so far, their main focus was on hacking the thing to write/read as fast and reliably as possible. That you can test and see (or just read the code) and conclude it's very well thought. But other functionalities certainly were postponed.

**EDIT: **Another important thing: Using dconf to store settings and removing settings when some application is removed, will certainly depend on other tools, such as the APT suite being upgraded to do so. It's not implemented now, which causes old keys/value pairs to remain there when you remove an application. This has to be worked a lot.

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> Another important thing: Using dconf to store settings and removing settings when some application is removed, will certainly depend on other tools, such as the APT suite being upgraded to do so. It's not implemented now, which causes old keys/value pairs to remain there when you remove an application. This has to be worked a lot.
It doesn't happen now with the old method, and it won't happen with the new method. It would require the package manager to check and, if necessary, modify data within every user's account without permission to do so. In other words, it would break the security model.

---

### Post by effenberg0x0 on 2011-11-22
> **Paddy Landau said:**
> It doesn't happen now with the old method, and it won't happen with the new method. It would require the package manager to check and, if necessary, modify data within every user's account without permission to do so. In other words, it would break the security model.

Not sure Paddy. The way I *think* it will eventually work is:

sudo apt-get install some_program (will write to the $USER dconf)
sudo apt-get remove --purge some_program (will delete from the $USER dconf)

Other users dconf are within their $HOME/.config/dconf/user, protected by the chown/chmod of their $HOME, like user:user chmod 775, for example.

In the case of global apps, say something like dhcpd, dnsmasq, settings (/etc, etc) will probably be on /root dconf I believe, protected by the same traditional perms.

Of course this is all speculation from my part. In the end many of those choices will be done by the distro I think.

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> Not sure Paddy. The way I *think* it will eventually work is:

sudo apt-get install some_program (will write to the $USER dconf)
sudo apt-get remove --purge some_program (will delete from the $USER dconf)
Uh, *which* $USER? Remember that sudo means apt-get is running as root! Either it needs to access every user's home, or none of them.

And what about when a user is added after a program has been installed? Must apt-get then go and retrospectively change the dconf settings -- before the user has even signed on?

No. Linux's present model is tried, tested and proven. apt-get must not fiddle with user's home folders. When the program runs for the first time *for a specific user*, with the old model it created the relevant folder (within ~/.config or gconf for the newer ones); with the new model it will create the relevant keys in dconf -- *for that user only*.

---

### Post by effenberg0x0 on 2011-11-22
> **Paddy Landau said:**
> Uh, *which* $USER? Remember that sudo means apt-get is running as root! Either it needs to access every user's home, or none of them.


I disagree, because /proc FS exists. Try this example on your machine, so you can see your environment:

```
$ sudo update-manager &
[1] 17830

$ sudo cat /proc/17830/environ 

```> **Paddy Landau said:**
> 
And what about when a user is added after a program has been installed? Must apt-get then go and retrospectively change the dconf settings -- before the user has even signed on?

No. Linux's present model is tried, tested and proven. apt-get must not fiddle with user's home folders. When the program runs for the first time *for a specific user*, with the old model it created the relevant folder (within ~/.config or gconf for the newer ones); with the new model it will create the relevant keys in dconf -- *for that user only*.
[quote]
Yes, I agree that that is the standard, tested, reliable procedure. As a user runs the program for the first time, he will get settings written to his dconf, no prob with that. What I mean is that, since apt works restricted to each user environment, as you seen above, it is safe to let it clean old configs from dconf, the same way it already does when you use apt-remove with the --purge modifier.  Otherwise, I can't think of a way to keep dconf keys tidy.

---

### Post by Mr. Picklesworth on 2011-11-22
> **effenberg0x0 said:**
> Yes, I agree that that is the standard, tested, reliable procedure. As a user runs the program for the first time, he will get settings written to his dconf, no prob with that. What I mean is that, since apt works restricted to each user environment, as you seen above, it is safe to let it clean old configs from dconf, the same way it already does when you use apt-remove with the --purge modifier.  Otherwise, I can't think of a way to keep dconf keys tidy.

Package installation is not a per-user problem at the moment, and I expect it would be nothing short of disastrous to attempt to make it one without a thorough rethinking of what software packages are. In your example, each user would need to uninstall the same package, or an administrator would need to run apt-get remove on each user's behalf.

Another thing to know is applications don't tell dpkg anything about files they have added. The way --purge works is some packages have an extra bit of metadata in their packaging directory: [conffiles]("http://www.debian.org/doc/manuals/maint-guide/dother.en.html#conffiles"). The package needs to know about all its (potential) configuration files in advance and they need to be listed there. (Or, naturally, something like */etc/conffiles-for-my-package*). If something is added at run time and it isn't a part of the package, dpkg will never know.

With that said, I for one would be pretty thrilled if application packages and system packages were considered different things, where the former *could* be a per-user problem.

I suspect you could solve this problem with some changes in dconf itself. GSettings makes it really clear that it wants a schema for every key that is set in the settings database. So, settings without schemas can be considered junk and removed accordingly. This way you won't need to touch anything that runs with escalated privileges, and you won't need to poke users's files with those privileges.

---

### Post by effenberg0x0 on 2011-11-22
> **Mr. Picklesworth said:**
> Package installation is not a per-user problem at the moment, and I expect it would be nothing short of disastrous to attempt to make it one without a thorough rethinking of what software packages are. In your example, each user would need to uninstall the same package, or an administrator would need to run apt-get remove on each user's behalf.

Another thing to know is applications don't tell dpkg anything about files they have added. The way --purge works is some packages have an extra bit of metadata in their packaging directory: [conffiles]("http://www.debian.org/doc/manuals/maint-guide/dother.en.html#conffiles"). The package needs to know about all its (potential) configuration files in advance and they need to be listed there. (Or, naturally, something like */etc/conffiles-for-my-package*). If something is added at run time and it isn't a part of the package, dpkg will never know.

With that said, I for one would be pretty thrilled if application packages and system packages were considered different things, where the former *could* be a per-user problem.

I suspect you could solve this problem with some changes in dconf itself. GSettings makes it really clear that it wants a schema for every key that is set in the settings database. So, settings without schemas can be considered junk and removed accordingly. This way you won't need to touch anything that runs with escalated privileges, and you won't need to poke users's files with those privileges.

The division between System Packages and Application Packages is *indeed* interesting. I have never thought of it on that perspective. Actually it's such a good idea, I'm sure someone probably already brought it up. I'll search and study if this possibility is / has ever been considered / suggested by anyone. It really makes a lot of sense in various ways. Per-user applications are, in my point of view, something in Linux nature, considering per-user apps and settings have always been a reality as the permissions / modes structure has always been in its core. Root always could add/remove apps from the system and grant/deny access, in a way that they are effectively controlled in user or group level at least. System (global/daemons) are generally protected by root, not to be accessed by the ordinary user anyway.

The problem in my mind was managing removal the user-level app settings. Your suggestion on schemas is very good. Of course, a key *can* be identified as junk. 

Thanks for the enlightenment.

---

### Post by Paddy Landau on 2011-11-22
> **effenberg0x0 said:**
> ... the same way it already does when you use apt-remove with the --purge modifier.
AFAIK, purge does not touch individual user's homes. It never has done so when I've tested it.

---

### Post by effenberg0x0 on 2011-11-22
> **Paddy Landau said:**
> AFAIK, purge does not touch individual user's homes. It never has done so when I've tested it.

I was under the impression that it did. I'm looking for something to test it.
[B]
EDIT: [/B]Ah, found it. You are absolutely right. I was wrong, because my machine is setup different... The behavior here is setup accordingly to IT management rules... It's a customization using dpkg and apt configuration tag "post-invoke". It finds /home/*/.<config_file>, when the package is removed and moves it out of the machine to the storage. It's a long script they did, lots of checking and rechecking, but basically:

find /home/*/ -name "$*(dpkg --list | grep '^rc\b' | awk '{print $2}'*)"
Then it uses sed to remove version numbers, architecture, etc.
Then it checks:
If a regexp of the file can be found for the user that ran apt.
If the same file_name exists for all users
If sizes differ 
Last modified
It grep the file to find a mention to the package name
Then it does some math to validate the process
After that, tar.gz them to /var/transmit/<file_name>.store.$USER.$DATE
And /var/transmit is rsyncd to company storage "trash" (which is not emptied immediately, I think files are kept for IT for 6 months, not sure).

It clearly is not that they are interested in keeping home directories clean. They wanna know who installed/removed what and keep proof of it, of course...nice...

---

### Post by Paddy Landau on 2011-11-23
> **effenberg0x0 said:**
> It clearly is not that they are interested in keeping home directories clean. They wanna know who installed/removed what and keep proof of it, of course...nice...
Ooh, sneaky! But that explains the earlier confusion we had while discussing it.

---

### Post by effenberg0x0 on 2011-11-23
> **Paddy Landau said:**
> Ooh, sneaky! But that explains the earlier confusion we had while discussing it.

Sneaky, ok, and kindda frustrating too. I've been using this thing for a couple years, entirely unaware of it. I found the source of it: There's a "mandatory" deb that installs some of the company stuff in your PC, like: ssh keys (ssh, rsync, etc), vpn client (when you're from home-office or in business travel), it maps your network folders/shares to fstab so you can read/write from it, send files to others, etc, create backup routines on cron to rsync to their storage, adds the company documents templates to your home, sets i&#7765;tables so everything works the way they want to, etc. But I would never imagine they messed with apt, not in a million years... I really did not enjoy this part of the thing... Not happy at all.

---

### Post by Paddy Landau on 2011-11-23
> **effenberg0x0 said:**
> ... I really did not enjoy this part of the thing... Not happy at all.
LOL. That's what you get when using your own hardware with a company's.

I saw an article just yesterday worrying about this type of problem in a very general way.
[App Freedom vs. Corporate Security]("http://www.informationweek.com/news/security/antivirus/231903385")

---

### Post by effenberg0x0 on 2011-11-23
> **Paddy Landau said:**
> LOL. That's what you get when using your own hardware with a company's.

I saw an article just yesterday worrying about this type of problem in a very general way.
[App Freedom vs. Corporate Security]("http://www.informationweek.com/news/security/antivirus/231903385")

As most companies are doing here, they stimulate employees to work from home (pay your broadband, anything you need to put together a home-office, from furniture to IP phone and video-conference gear), provide you with a killer PC, laptop, etc. It has been proven it improves productivity, reduces employees wasted time and stress due to traffic, employees get happier to be closer to their home and families, eventually work more hours, cut offices and infrastructure costs, etc. Great.

In this scenario, I don't have anything against some rules being applied to the PCs they provide or other of employees devices when it comes to accessing their network. Of course, some security measure is needed when you take your typical lan devices to the wlan scope. But changing the way my hardware deals with APT was a little too much IMO.

---

### Post by 3vi1 on 2011-11-23
> **effenberg0x0 said:**
> I disagree:
... It's pretty obvious isn't it?

Great.  You've found a way to "easily" delete unused program settings (whereas before I could grep everything by date and have the old/unused stuff brought to my attention without looking through every key).

Now, let's see a "dconf restore" command that makes it as easy to put back all of my old settings for one or two programs as it was to restore only those directories from a backup.

---

### Post by effenberg0x0 on 2011-11-23
> **3vi1 said:**
> Great.  You've found a way to "easily" delete unused program settings (whereas before I could grep everything by date and have the old/unused stuff brought to my attention without looking through every key).

Now, let's see a "dconf restore" command that makes it as easy to put back all of my old settings for one or two programs as it was to restore only those directories from a backup.

Are you under the impression that I have to prove anything to you? 
Newsflash: I don't. I strongly advise you to think, hax0r.

---

