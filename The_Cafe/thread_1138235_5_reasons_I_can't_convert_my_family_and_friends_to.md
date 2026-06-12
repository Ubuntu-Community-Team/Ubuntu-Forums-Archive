---
title: "5 reasons I can't convert my family and friends to Linux/Ubuntu"
date: 2009-04-26
forum: The Cafe
---

### Post by hobo14 on 2009-04-26
----I originally put his post in the beginrer's forum, but I think it might be more appropriate here...

I recently made the permanent change on my main machine to Ubuntu only (have dabbled with dual boots a few times before, and still have an XP gaming box), and am so glad I did.  
Next I started trying to convert heathen non-believers from Windows, starting with my friends and family.

Unfortunately I failed because of the following 5 "characteristics" of Ubuntu that I(newb) can't change for them:

1.)  Automount is crap - external disks have to be manually mounted in terminal to be able to see files with Chinese characters in their names, and if a disk is first pulled out of a Windows box without being "safely removed" (which is what usually happens) Ubuntu automount won't mount it, it has to be manually mounted with the force option.

2.)  External disks have to be unmounted before data is written to them, and so they will automount next time. (I know, I know, don't tell me "Windows does too". In Windows you should, but it's rarely necessary, and most people don't.)

3.)  Installing new programs you find online can be hard - most Linux stuff seems to be source downloads that have to be compiled, and even deb packages don't install nicely enough for people who only know how to use windows: they need to be able to doubleclick the install package, then click next, ok, and see the new program magically appear in their menu and on their desktop. Always, no exceptions ever.

4.)  Eventually they are going to find themselves in a situation where they need to open a terminal window.  This is unacceptable to them; Ubuntu needs to be able to do at least as much through the GUI as Windows can. 

5.)  Other partitions on the internal hard drive mounted at boot belong to root and don't have friendly enough permissions to avoid using "sudo", so I like to change /etc/fstab to make the owner of the partition the main user of the machine, and to give him full control of that partition including execute permission.  Unfortunately text files on these partitions are marked executable, so doubleclicking them means they are run as scripts instead of being opened for editing.  I can change Nautilus to always view text files instead of running them (being asked  each time is not acceptable to the reluctant converts), but then they can't run script files....


I can work around these things, but my friends and family can't or won't. :(
Hopefully some of these can be corrected now by people who know more than I do, and the rest will be corrected in future versions of Ubuntu, so Linux can be brought to the clueless majority.

---

### Post by meeples on 2009-04-26
i just managed to convert my friend to ubuntu yesterday and he loves it, but i suppose it depends on the person and how computer capable they are..

---

### Post by SunnyRabbiera on 2009-04-26
> 
1.)  Automount is crap - external disks have to be manually mounted in terminal to be able to see files with Chinese characters in their names, and if a disk is first pulled out of a Windows box without being "safely removed" (which is what usually happens) Ubuntu automount won't mount it, it has to be manually mounted with the force option.

Nonsense, also "safe removal" is a good idea no matter what

> 
2.)  External disks have to be unmounted before data is written to them, and so they will automount next time. (I know, I know, don't tell me "Windows does too". In Windows you should, but it's rarely necessary, and most people don't.)
Actually you do need to teach the practice of safe removal, especially if the drives are NTFS based.
NTFS can seriously get crapped out if not mounterd properly, I have seen it happen.
Fat drives have this issue too...
The safe removal feature IS needed, I have seen external hard drive deaths happen because of stupid behavior.

> 3.)  Installing new programs you find online can be hard - most Linux stuff seems to be source downloads that have to be compiled, and even deb packages don't install nicely enough for people who only know how to use windows: they need to be able to doubleclick the install package, then click next, ok, and see the new program magically appear in their menu and on their desktop. Always, no exceptions ever.
We hear this all the time, for me installing software in linux is the better.
The only real advantage Windows has is that many make CD's with .exe's on them as its the dominant desktop OS.
If it was Ubuntu you would see more .deb installers out there.
Most of the time you dont have to compile software these days, if you know where to look you can find many places with .deb installers like getdeb.
For me installing software in linux is more simple, using trusted repositories and sources keeps linux safe...

> 4.)  Eventually they are going to find themselves in a situation where they need to open a terminal window.  This is unacceptable to them; Ubuntu needs to be able to do at least as much through the GUI as Windows can.
Actually Ubuntu much less other linux disros are less CLI based then they used to be, linux has come a long way in the 4 years I have used it...
Heck its made more progress in 4 years then Windows has done in 10

> 5.)  Other partitions on the internal hard drive mounted at boot belong to root and don't have friendly enough permissions to avoid using "sudo", so I like to change /etc/fstab to make the owner of the partition the main user of the machine, and to give him full control of that partition including execute permission.  Unfortunately text files on these partitions are marked executable, so doubleclicking them means they are run as scripts instead of being opened for editing.  I can change Nautilus to always view text files instead of running them (being asked  each time is not acceptable to the reluctant converts), but then they can't run script files....
This is more of a Gnome issue then a Ubuntu one in general, if you use KDE its a little better in this area

---

### Post by SpriteSODA on 2009-04-26
install gmount-iso, will make your life easier.

---

### Post by Bölvaður on 2009-04-26
Yes, I would not advice you to try to get your family or friends to use linux for now. If something comes up they would need a support guy with great experience and understanding if gnu/linux. This is something you will learn by reading support questions and answers on these forums and by using and fittling with ubuntu. Should take you about 4-5 months to be able to fix most problems.
So therefore I encurrage you to try to get them to switch if they want 1 month after ubuntu 9.10 comes out. (this one month gives them time to avoid most bugs that wasn't discovered until after release.)

When installing software on ubuntu:


[LIST=1]
[*]Look for what the software is called. (do not install anything from their webpage!!!)
[*]Open Synaptic package manager and install it from there.
[*]If that doesnt work, see if there is a .deb package or an executable binary file for linux on their website.
[*]If there is none then look on getdeb.net
[*]If there is none on getdeb then use what ever you find.
[/LIST]

But why did I suggest waiting for more experience before you install linux on your family's computer?
Well... #1 there is nothing you'd have to do with the terminal in reality... #2 scripts can be launched without being asked, if you really must use them in the first place (no idea why you would) #3 using partitions that you made with root will not give your users access to it -.- change the user and/or permissions.


Back to your post... this looks more like 5 rants than support questions.
If these are bugs which you seem to think, then please report them to launchpad.net
But if you want answers to questions please make threads asking 1 question each, with title that describes the content of the thread.

---

### Post by kenweill on 2009-04-26
> **hobo14 said:**
> 

2.)  External disks have to be unmounted before data is written to them, and so they will automount next time. (I know, I know, don't tell me "Windows does too". In Windows you should, but it's rarely necessary, and most people don't.)



I have observed this in windows as well. After saving something in the flash drive, as long as its done copying, whether you remove it safely or not, all the files are already there.

In linux, if you unplug your flash drive without unmounting manually, you lost some of the files, even if its done copying.

---

### Post by Bölvaður on 2009-04-26
> **kenweill said:**
> In linux, if you unplug your flash drive without unmounting manually, you lost some of the files, even if its done copying.

reason &#8594; ntfs

---

### Post by kwacka on 2009-04-26
Don't convert them, let them convert themselves - they'll be resistant otherwise and (as you've found) they'll find something to complain about.

If they want to carry on using Windows, no problem. BUT if you're supporting them using Windows withdraw that support - "I'll try and do it on Thursday" instead of "I'll come round later".

I've deliberately ignored anything I see about Visa, so I can just say "I know nothing about Visa" and will be doing the same when Windows 7 comes around.

More difficult if you're a professional of course.  ;)

---

### Post by mr.propre on 2009-04-26
If people find windows fitting there need more then Linux, than that's fine. I use them both to be most productive and really happy with it.

Complaining about Linux that it's not windows is like complaining that apples aren't pears. That people don't want to see that is not the problem of the Linux community, but the problem of the people who chose to be ignorant.

---

### Post by Eisenwinter on 2009-04-26
Trying to convert people is the stupidest thing you can do to attract attention to Linux.

Linux is used for other things than Windows, mostly, and it has a different way of doing things, and requires a different way of thinking.

Oh wait, you said you just started using Ubuntu only...

---

### Post by swoll1980 on 2009-04-26
Take a look at [this. ]("http://ubuntuforums.org/showthread.php?t=58017&highlight=anatomy+linux+troll")  If you set it up properly, and they unmounted their drives properly you wouldn't have these issues.

---

### Post by kevdog on 2009-04-26
linux isnt windows.  If they find it inconvenient to manually umount/mount a drive (which is actually very easy), then they must be very proficient at ridding themselves of viruses, registry errors, worms, trojans and such on their windows machines.

---

### Post by mr.propre on 2009-04-26
> **kevdog said:**
> linux isnt windows.  If they find it inconvenient to manually umount/mount a drive (which is actually very easy)...

Manual mounting under windows inspired by... *nix
[http://www.mkssoftware.com/docs/man1/mount.1.asp](http://www.mkssoftware.com/docs/man1/mount.1.asp)

---

### Post by Polygon on 2009-04-26
#1 seems like a bug, but the not mounting it if ntfs was not properly unmounted is for your protection, it gives windows a chance to run chkdisk on it to repair the drive....

---

### Post by howefield on 2009-04-26
> **Eisenwinter said:**
> Oh wait, you said you just started using Ubuntu only...

No he didn't.

---

### Post by RiceMonster on 2009-04-26
I don't understand why they should be converted in the first place.

---

### Post by Wiebelhaus on 2009-04-26
I had hopes for this thread before I opened it , then I had to ingest terminology such as "stupid , sucks" and other negative terminology.

---

### Post by sloggerkhan on 2009-04-26
> **hobo14 said:**
> ----I originally put his post in the beginrer's forum, but I think it might be more appropriate here...

I recently made the permanent change on my main machine to Ubuntu only (have dabbled with dual boots a few times before, and still have an XP gaming box), and am so glad I did.  
Next I started trying to convert heathen non-believers from Windows, starting with my friends and family.

Unfortunately I failed because of the following 5 "characteristics" of Ubuntu that I(newb) can't change for them:

1.)  Automount is crap - external disks have to be manually mounted in terminal to be able to see files with Chinese characters in their names, and if a disk is first pulled out of a Windows box without being "safely removed" (which is what usually happens) Ubuntu automount won't mount it, it has to be manually mounted with the force option.

2.)  External disks have to be unmounted before data is written to them, and so they will automount next time. (I know, I know, don't tell me "Windows does too". In Windows you should, but it's rarely necessary, and most people don't.)

3.)  Installing new programs you find online can be hard - most Linux stuff seems to be source downloads that have to be compiled, and even deb packages don't install nicely enough for people who only know how to use windows: they need to be able to doubleclick the install package, then click next, ok, and see the new program magically appear in their menu and on their desktop. Always, no exceptions ever.

4.)  Eventually they are going to find themselves in a situation where they need to open a terminal window.  This is unacceptable to them; Ubuntu needs to be able to do at least as much through the GUI as Windows can. 

5.)  Other partitions on the internal hard drive mounted at boot belong to root and don't have friendly enough permissions to avoid using "sudo", so I like to change /etc/fstab to make the owner of the partition the main user of the machine, and to give him full control of that partition including execute permission.  Unfortunately text files on these partitions are marked executable, so doubleclicking them means they are run as scripts instead of being opened for editing.  I can change Nautilus to always view text files instead of running them (being asked  each time is not acceptable to the reluctant converts), but then they can't run script files....


I can work around these things, but my friends and family can't or won't. :(
Hopefully some of these can be corrected now by people who know more than I do, and the rest will be corrected in future versions of Ubuntu, so Linux can be brought to the clueless majority.


I a lot of your downsides lead to really weird and suspect practice IMO. Having a home folder is pretty much exactly like Mac or user folder on windows (parent of my documents, whatever it's called). If you have users who save stuff to random locations throughout the PC, that's pretty problematic on any OS. There is NO reason normal users need access outside of their home folder and any extra hard disks or network shares that may be mounted. 

Likewise, standard users should not be installing software, they should be asking you, the admin, to install it. (Though like Mac, they could download a binary and install it locally to their home folder). Really, if users need to install software routinely, I think something's wrong. Not to mention package manager is REALLY friggin easy to use.

So far as automount, I can't speak to the chinese character issue, I've never had an issue with seeing any non-standard chars excluding occasions when I didn't have the correct character set installed. Automount itself work great, just make sure the disk automounts with the proper permissions. There seems to be a tendency for some disks to mount with privileges for root or a particularly user. This is an easy to fix permission issue.

Likewise each user can have their own prefs for what opens things by default with nautilus. It's exactly like on windows, you can set 'opens with' to be a default or choose something different for one time. And you shouldn't be giving users read/write access to folders of system scripts.

So far as terminal window situation... Not any different from a Mac. My Dad has had to use it a couple of times to do some system stuff and harden the thing, but my Mom has never touched it. If someone else where to get a logon for my PC, they wouldn't need to touch command line, either. Everything works.

Overall your list of complaints is semi-ambiguous and to me seems to reflect poor decisions in set up and admin rather than any issues with linux. Most of the things you list seem the same on Mac, and sometimes even on Windows.

---

### Post by hobo14 on 2009-04-26
Good grief.  I was only pointing out what stopped my family of inexperienced computer users from using Ubuntu, and they aren't the ones writing here.  I am, and I am very happy with Ubuntu.

I thought perhaps I would get some replies with other reasons why other posters couldn't get their friends and families to use a Linux distro (and possibly some constructive suggestions on how to work around some things I mentioned, but that was very much a secondary goal).

Lighten up people, I'm not attacking Ubuntu, I love it.


> **SunnyRabbiera]Nonsense, also "safe removal" is a good idea no matter what[/QUOTE]
Nonsense? Which part, the Chinese characters or the force option?  Both are correct.


> Actually you do need to teach the practice of safe removal, especially if the drives are NTFS based.
Totally agree. The point is that people who don't do this at the moment don't want to have to start doing it.


> We hear this all the time, for me installing software in linux is the better.
The only real advantage Windows has is that many make CD's with .exe's on them as its the dominant desktop OS.
If it was Ubuntu you would see more .deb installers out there.
Most of the time you dont have to compile software these days, if you know where to look you can find many places with .deb installers like getdeb.
For me installing software in linux is more simple, using trusted repositories and sources keeps linux safe...
What is best for you is irrelevant in my post.  It's what is best for inexperienced, windows only users, who know nothing else.


> This is more of a Gnome issue then a Ubuntu one in general, if you use KDE its a little better in this area
Good point, thanks.  I haven't really tried KDE.


[QUOTE=Bölvaður]Back to your post... this looks more like 5 rants than support questions.
If these are bugs which you seem to think, then please report them to launchpad.net
But if you want answers to questions please make threads asking 1 question each, with title that describes the content of the thread.[/QUOTE]
Not rants, not bugs, not support questions.  I don't want answers to these "questions".  I'd really like to hear what else stops Windows users using Ubuntu.


[QUOTE=mr.propre]Complaining about Linux that it's not windows is like complaining that apples aren't pears. That people don't want to see that is not the problem of the Linux community, but the problem of the people who chose to be ignorant.[/QUOTE]
Yes, but I'd really enjoy seeing less people using windows, and more people using Ubuntu or some other distro, and those ignorant people are the vast majority.  
You can't just ignore what they want/like/need, _if_ you want increase your "market" share.


[QUOTE=Eisenwinter]Trying to convert people is the stupidest thing you can do to attract attention to Linux.

Linux is used for other things than Windows, mostly, and it has a different way of doing things, and requires a different way of thinking.

Oh wait, you said you just started using Ubuntu only...[/QUOTE]
???? Most of this is beyond my comprehension, but I use Linux for exactly what I used to use Windows for (except gaming).


[QUOTE=swoll1980]Take a look at this.  If you set it up properly, and they unmounted their drives properly you wouldn't have these issues.[/QUOTE]
Perhaps you should take a look at it yourself to refresh your memory on exactly what it says before you refer other people to it.
Either that or point out the "If I can't use it, nobody can" part of my original post for me, because I can't see it...


[QUOTE=kevdog]If they find it inconvenient to manually umount/mount a drive (which is actually very easy)[/QUOTE]
You and I find it easy kevdog, but they don't.


[QUOTE=RiceMonster]I don't understand why they should be converted in the first place.[/QUOTE]
Then perhaps this thread was not the right one for you to click on.  There is no good reason, other than I like Ubuntu so much better than Windows that I'd like to see more people using it.


[QUOTE=sx66gns]I had hopes for this thread before I opened it , then I had to ingest terminology such as "stupid , sucks" and other negative terminology.[/QUOTE]
I assume you don't mean my post? said:**
> ...
There is NO reason normal users need access outside of their home folder and any extra hard disks or network shares that may be mounted.
...
Likewise, standard users should not be installing software, they should be asking you, the admin, to install it. 
...
So far as automount, I can't speak to the chinese character issue, I've never had an issue with seeing any non-standard chars excluding occasions when I didn't have the correct character set installed. 
...
It's exactly like on windows, you can set 'opens with' to be a default or choose something different for one time. And you shouldn't be giving users read/write access to folders of system scripts.
...
So far as terminal window situation... Not any different from a Mac. My Dad has had to use it a couple of times to do some system stuff and harden the thing, but my Mom has never touched it. 
...
Overall your list of complaints is semi-ambiguous and to me seems to reflect poor decisions in set up and admin rather than any issues with linux.
Whoa there sloggerkhan...
I am not a sys admin running a network for "normal users", and I don't want to be, I certainly don't want to be installing every piece of software they find online.

There IS reason for these users to want to access other partitions: they contain large numbers of files they have accumulated over years of Windows use.

Guess you'll just have to trust me on the Chinese characters then won't you: the character set is installed, characters show perfectly everywhere except that Chinese named files on external devices are invisible unless manually mounted.

Nautilus is not "exactly like windows", and not every file has an extension, and I said nothing about access to system scripts.

Good for your Dad.  Unfortunately my Dad wouldn't be willing to do that.

Feel free to point out the "semi"-ambiguity, I'll clear it up.  I would also be very happy to receive constructive advice on how to rectify any poor decisions.

---

### Post by pbpersson on 2009-04-26
> **kwacka said:**
> 

I've deliberately ignored anything I see about Visa, so I can just say "I know nothing about Visa" and will be doing the same when Windows 7 comes around.


"I'm sorry, I don't use Windows any more - I switched to Ubuntu Linux years ago because it doesn't have those weird problems.....it just works."  :)

:lolflag:

---

### Post by gymophett on 2009-04-26
> **mr.propre said:**
> 

Complaining about Linux that it's not windows is like complaining that apples aren't pears. That people don't want to see that is not the problem of the Linux community, but the problem of the people who chose to be ignorant.

I love that!

---

### Post by swoll1980 on 2009-04-26
> **hobo14 said:**
> 
 The point is that people who don't do this at the moment don't want to have to start doing it.




The fact that you believe Ubuntu should compensate for people who "don't want to have to start" unmounting their drives properly, is just ridiculous to me.

---

### Post by hobo14 on 2009-04-26
> **swoll1980 said:**
> The fact that you believe Ubuntu should compensate for people who "don't want to have to start" unmounting their drives properly, is just ridiculous to me.
It may be ridiculous to you, but it isn't ridiculous to them - and they number in the hundreds of millions.
If Canonical Ltd. want larger numbers of Ubuntu users (and I'm happy to admit I have no idea whether they do or not.  It may be just me...) then they'll have to take it into consideration.

---

### Post by MikeTheC on 2009-04-26
I'm sorry, but if people can't deal with something as nice and centralized as Synaptic for searching through available software titles by name, category or description, them I'm not convinced they should be running Linux in the first place. I don't mean to be cruel, but how is *not having* to scour the web for software to download a bad thing? I mean, it's not like it's "easy" to use the web to find software, especially if you really don't know what you're looking for.

I've discovered software I would *never* have thought to download simply from looking through Apt's list.

---

### Post by MikeTheC on 2009-04-26
> **mr.propre said:**
> Complaining about Linux that it's not windows is like complaining that apples aren't pears. That people don't want to see that is not the problem of the Linux community, but the problem of the people who chose to be ignorant.
+1 here. Awesome observation!

> **Eisenwinter said:**
> Trying to convert people is the stupidest thing you can do to attract attention to Linux.
You can only lead a horse to water. You cannot make them drink. Putting a gun to their head would be, I agree, counter-productive.

---

### Post by Eisenwinter on 2009-04-26
> **swoll1980 said:**
> The fact that you believe Ubuntu should compensate for people who "don't want to have to start" unmounting their drives properly, is just ridiculous to me.
+1 here.

---

### Post by ndefontenay on 2009-04-26
Keep working at converting your whole family! When all the PCs will be running linux, you won't have the incompatibility problems related to fat or ntfs anymore! 

For the Chinese issues on the external HD, I have no idea. I think you should open a bug request for that. It looks like a genuine bug to me, not misbehavior.

For the installation of applications, stick to add/remove from the repository and use sources as a last resource.

I've posted a thread a while ago about what arguments to use if you are converting people. And something that have to make really sure your family and friend understand is that Linux is not Windows. They won't use the exactly same application as there is on windows. They can't request it. (at the exception of a few like google earth and skype). No more photoshop but The Gimp. no more microsoft office but open office.

Finally, the best way to convert people is really to manage to get them sit next to you when you sit at your computer working on ubuntu. Prepare a really awesome compiz demo, blow them away with lots of desktop 3D feature. Show them the magic they will get interest. Only then tell them what will change.

Just found my thread. Hope it helps:

[http://ubuntuforums.org/showthread.php?t=991764](http://ubuntuforums.org/showthread.php?t=991764)

Nico

---

### Post by swoll1980 on 2009-04-26
> **hobo14 said:**
> It may be ridiculous to you, but it isn't ridiculous to them - and they number in the hundreds of millions.
If Canonical Ltd. want larger numbers of Ubuntu users (and I'm happy to admit I have no idea whether they do or not.  It may be just me...) then they'll have to take it into consideration.

Linux isn't for a lot of people. Those who don't/won't unmount their drives properly, probably fall into this category. The funny part about this is, that I never knew about the problem, because I always unmounted my drives.

---

### Post by sloggerkhan on 2009-04-26
> 


Whoa there sloggerkhan...
I am not a sys admin running a network for "normal users", and I don't want to be, I certainly don't want to be installing every piece of software they find online.
First of all, it still hasn't been explained why these 'users' need software outside of the repositories. On Ubuntu, the only instance of routine use of *.tar.gz binary releases I know of is for games that release frequently such as nexuiz. These kinds of games can just have download stuck in the home folder and run from there exactly like a Mac. Very simple and self explanatory. Likewise, your users don't seem likely to be installing svn releases of stuff from source, and I assume you would add any non-standard repos such as medibuntu yourself. If your users aren't capable of installing stuff from synaptic or add/remove, it's your job to either teach them and grant them the privilege by giving them partial admin privileges or to be willing to type sudo aptitude install <program> for them every so often. This whole 'users need to be able to download and install stuff systemwide' makes no sense from a Linux perspective. Sure, users can DL and run stuff from their /home (allowable out of the box on Ubuntu, BTW), or they can get repo access through being given the proper privileges by admin. Neither is crazy, illogical, or problematic. I'm more worried about what these bizarre pieces of software you think your family will be downloading and installing all over the place are.

> 
There IS reason for these users to want to access other partitions: they contain large numbers of files they have accumulated over years of Windows use.
I never said users don't need access to storage partitions. And it's something you only need to set up once. For the drive you shared, add it to /etc/fstab properly and make its mount folder read/writable by the users group. Likewise, if it automounts, you can still make its group the users group with proper permission and the change should persist across mounts. It should automatically show up on everyone's desktop, no issues. However there is not reason users need complete access or even awareness of the filesystem outside of /media and /home/<username>. Access to files elsewhere should be transparent to the user if needed, and giving them write access to places like /usr/bin or /etc is asking for trouble.

> 
Guess you'll just have to trust me on the Chinese characters then won't you: the character set is installed, characters show perfectly everywhere except that Chinese named files on external devices are invisible unless manually mounted.
Can't speak to this, never had issues like that.


> 
Nautilus is not "exactly like windows", and not every file has an extension, and I said nothing about access to system scripts.
ummm... don't understand what you are getting at... Of course not every file has an 'extension,' on linux filetypes are determined by mime-type also. But the faculty for determining what opens a file by default is pretty much like windows... Double click means open with default app. Right-click open-with will open with an app of your choice once, and right-click, properties:open with will let you choose default app. Pretty simple thing to teach someone if they want a photo to open with gimp instead of f-spot, say. Based on this I am also failing to understand the situation where users click on files that want to run as scripts instead of opening in text editors. That's not a normal situation.



> 
Good for your Dad.  Unfortunately my Dad wouldn't be willing to do that.
I'm not suggesting your Dad do that. I am only pointing out that even in home environments you have one root authority, or maybe a few, who take care of the computer and makes things easier for everyone else. Sometimes you have a couple of people share the responsibility if they're both knowledgeable. But you don't leave your Mom who's computer illiterate to try and figure out how to install and manage everything herself. And if you leave with permissions to do things she doesn't really understand, bad stuff will happen as a result. Instead you set stuff up and show her how to log in, what applications to use for what, tell her if she needs help, ask. Not leave her to go download random .exe or something.

> 
Feel free to point out the "semi"-ambiguity, I'll clear it up.  I would also be very happy to receive constructive advice on how to rectify any poor decisions.Overall, your statements are really ambiguous to me because none of them make sense from the perspective of a properly set up linux box. The only clear problem you listed was the one about gnome not displaying chinese characters under certain circumstances. The rest are really weird generalizations that do not make sense to me and seem to imply a lot of improper system management.

---

### Post by MaxIBoy on 2009-04-26
> **hobo14 said:**
> It may be ridiculous to you, but it isn't ridiculous to them - and they number in the hundreds of millions.
If Canonical Ltd. want larger numbers of Ubuntu users (and I'm happy to admit I have no idea whether they do or not. It may be just me...) then they'll have to take it into consideration.

Canonical probably does want more users. But what about us?

Think about it. 

These are people with such a dread of the command line (despite the fact that it's actually a lot easier than a graphical interface for a lot of tasks) that even the mere thought of possibly maybe copying and pasting some something into it is repulsive to them. 

These are people who, when you expect at least a basic understanding of what they're talking about, will indignantly tell you, "*I don't know how to use a computer*, and *I don't want to*! I just want to do [task]!" Well, gee, you just spent $500 on a piece of equipment, and you don't even want to know how to use it? Pretty dumb idea, if you ask me. Now run home and play with your VCR. 

Microsoft and Apple advertise to these people, and they can keep them for all I care.

---

### Post by sailthesea on 2009-04-26
I don't try and convert my Windows worshipping friends and family to Linux/Ubuntu for very simple reasons.
 They don't get it
 I'd have to fix things when they break them
 They PAY for Windows and are happy to have the PC in the shop when theres no need!
 I can't change anyones mind for them:P

---

### Post by bxcrx on 2009-04-26
My friend plays games, watches videos, and surfs the net.  His main point to me is maybe Ubuntu can mimic his Windows setup, but that doesn't give him a good enough reason to switch.  Ubuntu would have to excel in a certain area to draw him in.

1.  Linux doesn't play WoW well in comparison to Windows
2.  Browsing with Firefox isn't as perfect as it is in windows
    *see high cpu usage -- flash ads*
3.  Linux doesn't do anything better for my friend who is a smart 
    Windows user
4.  You can pretty much guarantee that anything can be thrown at Windows and it will be supported by third party (cameras, mp3 players, printers, scanners, cell phones etc...)

5.  Can't think of another

Linux is great, but we need more companies to start coming over so that when we throw anything at it it eats it up and spits out gold.

---

### Post by hobo14 on 2009-04-26
> 
Linux isn't for a lot of people.
_______

Microsoft and Apple advertise to these people, and they can keep them for all I care.

These are perfectly valid opinions, but I don't agree, and I doubt Canonical does either.


> **sloggerkhan said:**
> First of all, it still hasn't been explained why these 'users' need software outside of the repositories.
//snip
I'm more worried about what these bizarre pieces of software you think your family will be downloading and installing all over the place are.
Not quite sure what you're on about, was just replying to your suggestion that I should be installing all their software instead of them doing it themselves.


[QUOTE=sloggerkhan]I never said users don't need access to storage partitions. 
//snip
 Access to files elsewhere should be transparent to the user if needed, and giving them write access to places like /usr/bin or /etc is asking for trouble.[/QUOTE]
Again, doesn't seem to be related to the original post.  I have given users access to storage partitions, and they don't have access to /usr/bin or /etc.


[QUOTE=sloggerkhan]ummm... don't understand what you are getting at... Of course not every file has an 'extension,' 
//snip
Based on this I am also failing to understand the situation where users click on files that want to run as scripts instead of opening in text editors. That's not a normal situation.[/QUOTE]
Some software is set up to be run from a script (eg. Sopcast + GUI front end, off the top of my head), ie. users need to be able to run scripts as well as edit text files - to understand the situation reread the original post.



[QUOTE=sloggerkhan]I'm not suggesting your Dad do that. 
//snip
 Not leave her to go download random .exe or something.[/QUOTE]
Perhaps you live with your parents.  I don't.
The point is I can't (and don't want to) be hanging around holding their hands when they use their computers.


[QUOTE=sloggerkhan]Overall, your statements are really ambiguous to me because none of them make sense from the perspective of a properly set up linux box. The only clear problem you listed was the one about gnome not displaying chinese characters under certain circumstances. The rest are really weird generalizations that do not make sense to me and seem to imply a lot of improper system management.[/QUOTE]
Well, I guess ambiguous is better than "semi-ambiguous".
I assume by "only clear problem" you mean "the only problem that I don't not consider a problem"?
Like I said before, very happy to take suggestions on improving system management.

---

### Post by Saint Angeles on 2009-04-26
#3 and #4 don't exist...

i mean, i've installed Ubuntu onto my sister's desktop and my mom's work computer as well as several friends. my mom and my sister know almost nothing about electronics or computers. they've never once used a command line or needed it or even knew it existed.

my mom could never even understand how XP worked. i would have to explain several times how to do something but she would never understand. with xubuntu, I made simple (and huge) icons on her desktop that would lead to all the apps she would need (for work). she liked gnumeric much more than excel and abiword was easier for her than word. my sister enjoyed using rhythmbox much more than itunes. it actually worked with her ipod much better than itunes ever did. she enjoyed the simplicity of gnome and pidgin and using brasero was easy for her...

they have no need to install any software because when i set up the computer, i installed all the software they needed. anything they might need would be in the repositories. I'm sure they could easily figure out the "add/remove" button on the bottom of their "Applications" menu. its a lot easier than windows' version of searching the internet for exe files and then installing them.

plus, deb files are practically the same as exe files except better. they automatically search for, download, and install all needed dependencies.

oh, and about that partition thing... have you ever tried to open up an ubuntu partition from windows? you can't... so just because you are having some strange problem when opening windows partitions from ubuntu, just remember that at least you have the ability to open up windows or mac partitions.

i however have a windows partition that mounts perfectly and easily. i really dont understand the problem you are having.

---

### Post by swoll1980 on 2009-04-26
> **hobo14 said:**
> These are perfectly valid opinions, but I don't agree, and I doubt Canonical does either.



Not opinion, fact. Linux is not for everyone. Linux is not for my brother. Linux is not for a my friend John. Linux is not for your family, obviously. Look in the testimonials, you will see all kinds off people for whom Linux is not for. Linux is surely not for people who want another free version of Windows, or for those that can't unmount a drive before they unplug it.

---

### Post by hobo14 on 2009-04-27
> **swoll1980]Not opinion fact. Linux is not for everyone. Linux is not for my brother. Linux is not for a my friend John. Linux is not for this guy's family, obviously. Look in the testimonials, you will see all kinds off people for whom Linux is not for.[/QUOTE]
That's a very interesting interpretation of "fact".  I agree Linux is not for everyone, but that's not what you said, is it?
Anyway, your opinion, and my opinion on this aren't important, Canonical's is.


[QUOTE=Saint Angeles said:**
> #3 and #4 don't exist...
...
they've never once used a command line or needed it or even knew it existed.
...
they have no need to install any software because when i set up the computer, i installed all the software they needed. anything they might need would be in the repositories. 
...
plus, deb files are practically the same as exe files except better. they automatically search for, download, and install all needed dependencies.
...
oh, and about that partition thing... at least you have the ability to open up windows or mac partitions.
...
i however have a windows partition that mounts perfectly and easily. i really dont understand the problem you are having.
I beg your pardon? Don't exist? One man's problems are not every other man's problems, and they most certainly do exist.

Great, but have _you_ ever had to use it on their computers? They are lucky you are that available.  I'm not that available.

That's rather narrow-minded.  You installed everything they could ever conceivably need in one shot?  I don't think so.  If I'm wrong then I'd say they are the exception rather than the rule.
The repositories are great, but they certainly don't contain everything.

I love the automatic installation of dependencies too, but that's not the issue I was talking about.

Yes, and I'm glad, but it doesn't change the problem I described.

Check the ownership and permissions of every file on that partition.  Try to change them without editing /etc/fstab.  That is the root of that problem.




In case anyone missed it before, I love Ubuntu. I'm extremely happy with it, I think it's miles above Windows, ok?

---

### Post by MaxIBoy on 2009-04-27
> **hobo14 said:**
> Yes, and I'm glad, but it doesn't change the problem I described.

Check the ownership and permissions of every file on that partition.  Try to change them without editing /etc/fstab.  That is the root of that problem. This is for security reasons. The NTFS filesystem doesn't support UNIX permissions. For all Ubuntu knows, there's some really sensitive, damaging stuff on there, and NTFS is unable to say, "hey, this stuff is really sensitive and damaging! Don't let anyone touch it!" I could see some scenario where Ubuntu errs on the side of caution and marks everything as "root only," but I've never actually had anything like this happen with NTFS-format disks. Perfectly willing to concede that it's happening for you, though. Just tweak your FS table or something, it can't be a difficult fix.

---

