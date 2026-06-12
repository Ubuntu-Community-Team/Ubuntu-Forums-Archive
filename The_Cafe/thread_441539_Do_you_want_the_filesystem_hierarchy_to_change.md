---
title: "Do you want the filesystem hierarchy to change?"
date: 2007-05-12
forum: The Cafe
---

### Post by Rhox on 2007-05-12
This is the less messed up version.

edit1: read this before you say something about compatibility: [http://en.wikipedia.org/wiki/Gobolinux#Symlinks](http://en.wikipedia.org/wiki/Gobolinux#Symlinks)
edit2:before you start reading this please keep these in mind:
- This would not brake anything.
- If this was implemented it would be totally optional.

---

### Post by Tundro Walker on 2007-05-12
Not sure what you mean by this.  Please clarify.

Like, do we want the file system to change from Ext3 format to something else?  Or do we want the folder names to change?

---

### Post by Rhox on 2007-05-12
> **Tundro Walker said:**
> Not sure what you mean by this.  Please clarify.

Like, do we want the file system to change from Ext3 format to something else?  Or do we want the folder names to change?

Another name for filesystem hierarchy is directory hierarchy.

---

### Post by mech7 on 2007-05-12
I would like to see something like

/applications
/users/%username%/
/users/%username%/desktop
/users/%username%/applications_settings
/temporary_files
/operating_system

Something like that would be great i think :)

---

### Post by juxtaposed on 2007-05-12
You mean just change how it is organized? Like instead of '/home/patrick/Desktop', my desktop would be '/desktops/Patrick's Desktop' or something?

I think it would create alot of problems, and the hard core linuxers would hate any change, but it might be something to consider.

This looks interesting:

> GoboLinux is an alternative Linux distribution. Its most salient feature is its reorganization of the filesystem hierarchy. Under GoboLinux, each program has its own subdirectory tree, where all of its files can be found.[1]

It might be a more logical way to do things.

---

### Post by Rhox on 2007-05-12
> **juxtaposed said:**
> You mean just change how it is organized?

yep, that's what I mean.

---

### Post by mech7 on 2007-05-12
> **juxtaposed said:**
> You mean just change how it is organized? Like instead of '/home/patrick/Desktop', my desktop would be '/desktops/Patrick's Desktop' or something?

I think it would create alot of problems, and the hard core linuxers would hate any change, but it might be something to consider.

This looks interesting:



It might be a more logical way to do things.

That sounds pretty interesting..

> GoboLinux is an alternative Linux distribution which redefines the entire filesystem hierarchy.
In GoboLinux you don't need a package manager because the filesystem is the package manager:

Isn't this a bit like how mac handles things? I thought they also have like one file which you can just drag n drop to install.

---

### Post by tehkain on 2007-05-12
> **mech7 said:**
> That sounds pretty interesting..



Isn't this a bit like how mac handles things? I thought they also have like one file which you can just drag n drop to install.

Well the Mac has a typical unix structure. They use some clever linking and a modified file browser to allow two views, the standard clean view and the actual structure. Yea gobo does the drag and install thing. The only Issue I have with that is the apps don't update them self. The OS should handle the updating not each app.

Also isnt this the 3rd thread about this in two days. Can't we keep it in one place if you would like to discuss it. Making new threads isnt going to change peoples mind.

---

### Post by Rhox on 2007-05-12
> **tehkain said:**
> Well the Mac has a typical unix structure. They use some clever linking and a modified file browser to allow two views, the standard clean view and the actual structure. Yea gobo does the drag and install thing. The only Issue I have with that is the apps don't update them self. The OS should handle the updating not each app.

Also isnt this the 3rd thread about this in two days. Can't we keep it in one place if you would like to discuss it. Making new threads isnt going to change peoples mind.

I messed up the first poll so it's really 2. Also, gobo does update the apps.

---

### Post by Adamant1988 on 2007-05-12
I think the idea is essentially good, however, both views of the file system need to be allowed.  This means I either want the OPTION of which I see, or I want both immediately available.

---

### Post by Drooling Iguana on 2007-05-12
Some minor tweaking would be nice (I've always thought that there should be a separate directory for user-specific config files so that they don't clutter up ~,) and a bit more standardization on what goes where would be appreciated, but I don't see any need to throw the whole thing out wholesale, especially when the alternative seems to be with Windows-style "all files for a given program thrown into the same directory" technique.

It's not like end users have to venture outside their home directories much these days anyway.

---

### Post by deanjm1963 on 2007-05-12
I think the file hierarchy is fine as it is. I can't see the Debian devs changing from the standard, remember Ubuntu is based off Debian. It would take a lot of work on the Ubuntu side of things to have a file hierarchy like Gobo, why fix it when it isn't broken?

---

### Post by Rhox on 2007-05-12
> **deanjm1963 said:**
> I think the file hierarchy is fine as it is. I can't see the Debian devs changing from the standard, remember Ubuntu is based off Debian. It would take a lot of work on the Ubuntu side of things to have a file hierarchy like Gobo, why fix it when it isn't broken?

It is broken, it isn't perfect.

---

### Post by Polygon on 2007-05-13
how is it broken? 

and it all makes sense when you think about it. No normal user is going to want to really access anything other then their home directory anyway... i mean even for compiling you dont need to go deep into the file system to install the files,whenever i compile i save everything to the desktop and work from there, and most programs you just do "sudo make install" or use checkinstall to make a deb package, you dont manually put the files in their respective directories

read this, it provides some good insights on why things are the way they are

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by Rhox on 2007-05-13
> **Polygon said:**
> how is it broken? 

and it all makes sense when you think about it. No normal user is going to want to really access anything other then their home directory anyway... i mean even for compiling you dont need to go deep into the file system to install the files,whenever i compile i save everything to the desktop and work from there, and most programs you just do "sudo make install" or use checkinstall to make a deb package, you dont manually put the files in their respective directories

read this, it provides some good insights on why things are the way they are

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Sure, you don't need to but it would be a hell of a lot more organized. It's broken because its harder for powerusers or admins then it needs to be. I'd imagine the only reason you put them in your home is because it's too hard for you.

---

### Post by Adamant1988 on 2007-05-13
I think what we have here is a subtle attempt (read: not really subtle) to argue the point that the directory hierarchy isn't the most user-friendly thing on the planet, but we really need to look at demographics here.

For system admins and professionals, the current structure works like a dream.  They understand it, they like it, and it's good.  For the home user, it's irrelevant, really. 

Why?  Beagle, Tracker, [GLSCube](http://www.glscube.org/) .  These technologies make things easier to find for the home user, more organized, etc. without changing the base system or hierarchy.  These technologies will not change the structure, they'll change the way that people need to interact with it.  In the future, even going into your home folder to find a file may be unnecessary.  So really, the hierarchy doesn't need to change for home users, but it wouldn't hurt them either. 

So, as you've said, the power users of the world are the ones who would benefit from this most readily, but you know, most of them aren't even screaming for this kind of change either.  Many of these supposed power users aspire to develop code for Linux, or maybe be an IT pro or system administrator.  They benefit more readily from learning the structure as is.   So really I think Gobo's file system changes are for a minority of users who want/need them, but for the majority it's a wasted effort. 

[/opinion]

---

### Post by Rhox on 2007-05-13
> **Adamant1988 said:**
> 
For system admins and professionals, the current structure works like a dream.


You base this on what?

---

### Post by Adamant1988 on 2007-05-13
> **Rhox said:**
> You base this on what?

Their own accounts.  I know sysadmins and several people who work in the IT industry, there's also a wealth of people working in those fields in this forum.  Those people have been against this kind of a change almost as a collective in this forum, with the occasional defector.

---

### Post by Rhox on 2007-05-13
> **Adamant1988 said:**
> Their own accounts.  I know sysadmins and several people who work in the IT industry, there's also a wealth of people working in those fields in this forum.  Those people have been against this kind of a change almost as a collective in this forum, with the occasional defector.

Could you point them out. I think you are exaderating.

---

### Post by Adamant1988 on 2007-05-13
> **Rhox said:**
> Could you point them out. I think you are exaderating.

Let me go through the multitude of threads on this forum and find a few examples.  I'm only going to supply as much as I feel necessary simply because you aren't supplying any evidence to the contrary other than your own opinion and Gobo Linux FAQ info.  

[quote=igknighted]Ewww, its a return to the wretched windows file hierarchy!! Keep it away!

Only partially in gest... I think the separation the *nix based systems have, while tricky for new users to grasp, is more logical in a computing sense. So sure, it could be changed around like gobo does, but I am not in favor, I prefer the current method.[/quote]
[http://ubuntuforums.org/member.php?u=125907](http://ubuntuforums.org/member.php?u=125907)

(I also think you should look at the stats from your current poll, the consensus is obviously against this change) 

There are more, lots more, but I'm trying to keep this brief, because you can learn to google search the site.  As I've dug through the threads the only real benefit I see to this is 'Click n' drag' installs of applications.  If this kind of a change makes application installation easier, and allows for a new kind of package manger that could make it easier to install the latest greatest app ("Oh man, Pidgin 3.0 just released!) then I can be behind that much.

I still believe though, this needs to be highly targeted to a demographic that actually would benefit from it, and it should not be the standard.  'Opt in' is better than 'Opt out'.

---

### Post by mech7 on 2007-05-13
> **Drooling Iguana said:**
> It's not like end users have to venture outside their home directories much these days anyway.

I disagree many apps don't make proper menu items so you have to find out where the file is which needs to be executed.

---

### Post by Henry Rayker on 2007-05-13
use gobolinux if you love it so much. Jesus Christ....I'm sick and tired of these goddamn posts.

---

### Post by Kulgan on 2007-05-13
The current hierarchy is great, I think. But then anything better than the Windows one is good. Linux's is perfectly organised, I can find what I want, etc. I'm happy so long as those two things are true, and so long as there are no messed up chars (see: windows) in the directory names. 

Why would someone want to change it?

---

### Post by NESFreak on 2007-05-13
A temp dir in your home would be cool.

Have tried to symlink /temp to $HOME/.temp But it somehow didn't work out really well. This way i could mount my system partition read-only. Guess it wouldn't work out while using a homedir with a very limited disk-quotum.

but it would be nice to allow it someway.

---

### Post by Adamant1988 on 2007-05-13
> **Kulgan said:**
> The current hierarchy is great, I think. But then anything better than the Windows one is good. Linux's is perfectly organised, I can find what I want, etc. I'm happy so long as those two things are true, and so long as there are no messed up chars (see: windows) in the directory names. 

Why would someone want to change it?

Linux is a big playground and people do have different needs.  I think there is a select niche that would like to see these file system changes (apparently they're modeled after Mac OS X's own, or done in the same manner) .  Although I think the future is going to change the way we interact with our filesystems to such a degree that the hierarchy won't matter anyway...

---

### Post by Kulgan on 2007-05-13
> I think the future is going to change the way we interact with our filesystems to such a degree that the hierarchy won't matter anyway...
Then you agree that it might as well stay the same? :D

---

### Post by Adamant1988 on 2007-05-13
> **Kulgan said:**
> Then you agree that it might as well stay the same? :D

Yup, I just don't think it's going to matter.  I'm waiting for the IndexFS ti arise.  When editting your sources.list is about as complex as opening up a window and typing in sources.list.

---

### Post by BoyOfDestiny on 2007-05-13
> **mech7 said:**
> I disagree many apps don't make proper menu items so you have to find out where the file is which needs to be executed.

I disagree with this assertion. The location of the file doesn't matter. I installed uae, to make a shortcut, it would be uae (explicit path is not needed.)

To be honest I compiled it from source, and I don't know where it installed it to.

**If you must know where it is located for whatever reason**
Open a terminal:

whereis uae
uae: /usr/local/bin/uae

GUI way:
Or you can go to synaptic, right click on the package, choose Properties, then the installed files tab.

Worst case use the Search For Files (under the Places menu.)

Admins and power users would use the tools given (and should learn about them.) In the use case given (app doesn't have a menu entry) time would be better spent on making sure all apps have that (and a nice icon)

P.S. Wasn't there another poll on changing fhs too?

---

### Post by mech7 on 2007-05-13
> **Henry Rayker said:**
> use gobolinux if you love it so much. Jesus Christ....I'm sick and tired of these goddamn posts.

Yes because let's face it this is the perfect os let's face it.. no need to do any work on it no need for upgrades it is allready is the perfect os and there is no room for change or improvement :)

---

### Post by Adamant1988 on 2007-05-13
> **mech7 said:**
> Yes because let's face it this is the perfect os let's face it.. no need to do any work on it no need for upgrades it is allready is the perfect os and there is no room for change or improvement :)

Someone coming here and hinting or suggesting that XYZdistribution should act and behave exactly like ZYXdistribution is not far from someone coming in here and demanding a Windows theme for Ubuntu as default.  
The same argument applies, if that's what you want, go use it.

---

### Post by mech7 on 2007-05-13
> **Adamant1988 said:**
> Someone coming here and hinting or suggesting that XYZdistribution should act and behave exactly like ZYXdistribution is not far from someone coming in here and demanding a Windows theme for Ubuntu as default.  
The same argument applies, if that's what you want, go use it.

Nobody is demanding anything but let's face it every OS has it's strong points and what is wrong with borrowing those ? Everybody does that :) for example look at browsers first Opera had them then Firefox and years later IE comes with some tabs :lolflag:

---

### Post by PartisanEntity on 2007-05-13
Sorry not quite on the topic, but I really like GLScube which **Adamant1988** posted, very nice features, as you mentioned it really makes the location of the files quite unimportant.

Does installing it change anything as far as system stability or updates are concerned? (or other software and applications?)

---

### Post by Henry Rayker on 2007-05-13
> **mech7 said:**
> Yes because let's face it this is the perfect os let's face it.. no need to do any work on it no need for upgrades it is allready is the perfect os and there is no room for change or improvement :)

My argument is more along the lines of, "This suggestion is stupid." I know GoboLinux does it this way, and, honestly, if it were so amazing, more distros would follow suit. The only reason anyone has ever suggested is so that Joe-schmo who shouldn't be mucking around in his system files wants to...the same guy who will complain that he can't get rid of the / directory and wants to know what these permissions mean. I don't like that guy; not only does he want to break all of his stuff, but he wants to complain when we make it a little difficult for him.

You refer to this feature as a strong point, I (and all of the other people who seem to be strongly opposed to it) find it a foolish waste of time and effort.

Why don't we just include little comments on the folders so, when a user hovers over the folder, a tool-tip will pop up telling him/her what is inside. No need for symlinks or pissing anyone off.

---

### Post by Rhox on 2007-05-13
I don't get you people, why does this piss you off. It gives people options. Nothing would change if you didn't want it to. It wouldn't take that long. All you are doing is trying to look good.

---

### Post by Rhox on 2007-05-13
> **Henry Rayker said:**
> My argument is more along the lines of, "This suggestion is stupid." I know GoboLinux does it this way, and, honestly, if it were so amazing, more distros would follow suit. The only reason anyone has ever suggested is so that Joe-schmo who shouldn't be mucking around in his system files wants to...the same guy who will complain that he can't get rid of the / directory and wants to know what these permissions mean. I don't like that guy; not only does he want to break all of his stuff, but he wants to complain when we make it a little difficult for him.

You are making a lot of assumptions. Disliking the hierarchy doesn't make someone dumb.

---

### Post by Kulgan on 2007-05-13
> You are making a lot of assumptions. Disliking the hierarchy doesn't make someone dumb.
If they disagree with my opinion, it does XD

jk

---

### Post by BoyOfDestiny on 2007-05-13
I'd suggest that people take a look at this.

Filesystem Hierarchy Standard

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

There is a rhyme and reason to the existing filesystem. 

Note: I'm not aversed to it being modified (as it has been already, there is room for improvement), or symlinks, or tool tips as someone mentioned (I actually think tool tips with the data this article has would be neat)

---

### Post by Adamant1988 on 2007-05-13
> **PartisanEntity said:**
> Sorry not quite on the topic, but I really like GLScube which **Adamant1988** posted, very nice features, as you mentioned it really makes the location of the files quite unimportant.

Does installing it change anything as far as system stability or updates are concerned? (or other software and applications?)

GLScube is just an example of the kind of things that a semantic system can do.  Unfortunately, there haven't been any great new developments on it and I'm fairly sure the project is all but dead.  I only posted it as an example of what kinds of things we might be able to expect in the future.

---

### Post by Adamant1988 on 2007-05-13
> **mech7 said:**
> Nobody is demanding anything but let's face it every OS has it's strong points and what is wrong with borrowing those ? Everybody does that :) for example look at browsers first Opera had them then Firefox and years later IE comes with some tabs :lolflag:

I'm pointing out a trend in behavior.  This thread is a subtle attempt to convince Ubuntu users that a filesystem hierarchy change is necessary (which is why the OP has been defending his point so rabidly).  It is not far removed from another recent thread where a  troll demanded that a Windows theme be added to the Ubuntu default themes.

---

### Post by Rhox on 2007-05-13
> **Adamant1988 said:**
> I'm pointing out a trend in behavior.  This thread is a subtle attempt to convince Ubuntu users that a filesystem hierarchy change is necessary (which is why the OP has been defending his point so rabidly).  It is not far removed from another recent thread where a  troll demanded that a Windows theme be added to the Ubuntu default themes.

No,no,no you have it all wrong. A change isn't truly necessary but it would be beneficial. I'm defending my point rabidly because you don't seem to see the benefit and how easy it would be to implement. Also, if this was a troll it would be an incredibly stupid one considering that FHS would still be there intact.

---

### Post by happy-and-lost on 2007-05-13
No. It's taken me 6 months to figure out what everything in /usr/share/applications does as it is.

I quite enjoy the challenge :D

---

### Post by Rhox on 2007-05-13
> **happy-and-lost said:**
> No. It's taken me 6 months to figure out what everything in /usr/share/applications does as it is.

I quite enjoy the challenge :D

:-s

---

### Post by Polygon on 2007-05-13
> **Rhox said:**
> Sure, you don't need to but it would be a hell of a lot more organized. It's broken because its harder for powerusers or admins then it needs to be. I'd imagine the only reason you put them in your home is because it's too hard for you.

no... because its easier to just save it to the desktop rather then in some random place in the filesystem, when i dont even decide where all the files go anyway. Its easier to type ~/ rather then /usr/share/random folder/ random folder/

and the filesystem is really the one thing that users shouldent have a choice about (unless its a new one with symlinks).... because the FHS exists so that programs, operating systems, users, developers are all using the same thing, so when a programmer creates a program, he will be assured that the program will install correctly on every single OS that is FHS compliant. 

and i think the people who created the FHS have some sort of reasoning on why it exists the way it does... maybe its because they actually created the whole unix/linux operating system and they may just have a good idea on why the certain directories are there and what purpose they serve

and again, there is almost no reason for a normal user or even a power user to go searching for files that belong to a certain program anyway.  all config files that a power user would want to edit are located in the home directory. Almost all programs that you need to compile are installed either by a premade script (make install) or even a checkinstall to provide a deb

so if you still dont like it, either go support gobo linux or  go present your case to the FHS mailing list. Im sure they will be happy to provide you with whatever answers you need. [http://sourceforge.net/projects/freestandards/](http://sourceforge.net/projects/freestandards/).

---

### Post by mvaniersel on 2007-05-13
No, because it's going to mess up all the scripts I wrote over time. And not just for me.

And the advantages of such a far-reaching change seem pretty minimal to me.

---

### Post by Rhox on 2007-05-13
All scripts and programs that work now would still work. The only difference would be that you could see it differently.

---

### Post by Polygon on 2007-05-13
that means it be like mac OS X and it uses symlinks or some other clever scheme to have different folders that just act as placeholders as they just point to the same folders that are in every unix-like operating system..... with /usr /root / home / tmp and all that sorta stuff

so its not really changing it, its just making it look prettier. I have no objection to this as long its as easy to turn off as pressing like ctrl + whatever (kinda like with hidden files/folders and ctrl+h)

---

### Post by jpkotta on 2007-05-14
Don't know what the directories are for? [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Don't know were something is?  Use: locate, dpkg -S, dpkg -L, find, ...

The reason there the directories are the way they are is because over the decades, Unix developers saw a need for the arrangement, and it *evolved* to be that way.  The names are little cryptic because everything in Unix is a little cryptic.  That is not a good thing, but those who actually deal with the system have no trouble.  I sure wouldn't want /bin to become /essential_executables.  And this is the point - that only those who deal with the system should ever need to know this stuff.  If a user does need to know a detail about the naming conventions, then it should be in the documentation of whatever application requires it, and the application should probably be improved so such details are not needed.  You know how in Windows, when you first install it, it hides the root (C:) and things like Program Files and Windows?  Same idea.  Because normal users shouldn't (and shouldn't have to) poke around in there.

---

### Post by Rhox on 2007-05-14
> **Polygon said:**
> that means it be like mac OS X and it uses symlinks or some other clever scheme to have different folders that just act as placeholders as they just point to the same folders that are in every unix-like operating system..... with /usr /root / home / tmp and all that sorta stuff

so its not really changing it, its just making it look prettier. I have no objection to this as long its as easy to turn off as pressing like ctrl + whatever (kinda like with hidden files/folders and ctrl+h)

Yes, the current hierarchy would still exist untouched. It would just _look_ different if you wanted it to. I should have explained it better.

---

