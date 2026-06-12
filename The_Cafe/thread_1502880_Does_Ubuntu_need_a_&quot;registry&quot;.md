---
title: "Does Ubuntu need a &quot;registry&quot;?"
date: 2010-06-06
forum: The Cafe
---

### Post by zaphod777 on 2010-06-06
Before everyone gets up in arms. 

I think the Windows registry really has a bad rap it is really a good and easy way to make changes to many system in a quick and efficient manner. I am not fully convinced the registry slows a machine down it is all of the crap software people install that gums up their machine.

With that said I am not suggesting we implement the same system but something similar to the log file viewer where you can view all of your configuration files and then edit them as needed.  

You can have sections configuring wireless, grub, x, and etc.

I know in a perfect world everything should just work or be changed in the normal GUI.

But when things don't work it would really be nice to have it all in a well organized location. 

What do you think?

---

### Post by vigstrom on 2010-06-06
That's a good question.

I think gconf is a start. But that's just for gnome-stuff.

As an admin I relied heavily on setting stuff on win clients through the registry. So I see the benefits. But there's also the problem with 3rd party apps leaving entries behind. I haven't checked, but doesn't apts purge option clean gconf when you uninstall?

Anyway, I see what you mean by a "registry" and I think gconf might be what you're seeking here. Or is it too limited in that it's only for gnome stuff?

---

### Post by realzippy on 2010-06-06
*....a well organized location*

Yes,the windows registry,a place to grow your children up.

---

### Post by zaphod777 on 2010-06-06
> **realzippy said:**
> *....a well organized location*

Yes,the windows registry,a place to grow your children up.

It can be a bit daunting at first but once you know what you are looking for it can be a life savor for deploying a fix or change to a large number of users. 

@vigstrom 

I never checked out gconf I will need to take a look at that one.

---

### Post by Paddy Landau on 2010-06-06
I disagree. Here's why.

The Windows registry was a fantastic idea -- in theory.

In practice, it became a monster. Programs had to rely on the registry for information about the system and even about themselves. The result was quite a bit of entanglement, which caused more than a few times of "sweat and tears" for me.

If you had a registry, even if optional, some programmers would start to rely on it. Those programs would become less and less portable, making it really hard for various distros.

One of the fantastic things about Linux is the way that configurations are held in folders in files. If I want to completely reset Firefox in Windows, I have to uninstall it, maybe reboot, then reinstall. That would affect every user on that computer. With Linux, all I need do is delete the .mozilla folder, and it affects only me, no one else on the system.

I can even back up the .mozilla folder first so that I can experiment and then restore (and I have done this on occasion). Try doing that with the Windows registry!

The current method in Linux seems to work excellently. If you need to get information about installed programs... Well, we already have a type of registry, namely Synaptic, don't we?

In the computer world, I've found through experience (and training) that the KISS philosophy ("keep it simple stupid") works best. Linux is simple. The registry is complex.

---

### Post by zaphod777 on 2010-06-06
> **Paddy Landau said:**
> I disagree. Here's why.

The Windows registry was a fantastic idea -- in theory.

In practice, it became a monster. Programs had to rely on the registry for information about the system and even about themselves. The result was quite a bit of entanglement, which caused more than a few times of "sweat and tears" for me.

If you had a registry, even if optional, some programmers would start to rely on it. Those programs would become less and less portable, making it really hard for various distros.

One of the fantastic things about Linux is the way that configurations are held in folders in files. If I want to completely reset Firefox in Windows, I have to uninstall it, maybe reboot, then reinstall. That would affect every user on that computer. With Linux, all I need do is delete the .mozilla folder, and it affects only me, no one else on the system.

I can even back up the .mozilla folder first so that I can experiment and then restore (and I have done this on occasion). Try doing that with the Windows registry!

The current method in Linux seems to work excellently. If you need to get information about installed programs... Well, we already have a type of registry, namely Synaptic, don't we?

In the computer world, I've found through experience (and training) that the KISS philosophy ("keep it simple stupid") works best. Linux is simple. The registry is complex.

Excellent point what I am suggesting is more of an app that views  and can edit the existing config files you would find for all the various config files.

Kind of a glorified text editor with a browser pane showing all of the various config .conf files and their respective locations. 

I would hate to take away the portability of linux programs.

---

### Post by Paddy Landau on 2010-06-06
> **zaphod777 said:**
> ... what I am suggesting is more of an app that views  and can edit the existing config files you would find for all the various config files.
Ah, an add-on package rather than a replacement?

That would work, if...

... If you created a standard way for an installation to tell the pack the configuration options and where to save them. I would suggest that such a package have an API. Then, any programmer who wanted to join would create an interface for the API to use.

Not a bad idea for the seriously technical behind-the-scenes stuff, though it would be too technical for me to use!

---

### Post by zaphod777 on 2010-06-06
> **Paddy Landau said:**
> Ah, an add-on package rather than a replacement?

That would work, if...

... If you created a standard way for an installation to tell the pack the configuration options and where to save them. I would suggest that such a package have an API. Then, any programmer who wanted to join would create an interface for the API to use.

Not a bad idea for the seriously technical behind-the-scenes stuff, though it would be too technical for me to use!

That is a good Idea I think the API would be pretty simple just a way of informing the package where your configuration files are located. 

It would sure beat looking up the location of the config file and then using gedit to edit the said file. 

In a perfect would it wouldn't be needed but I think it would help when things aren't working and you need to get under the hood and check things out.

---

### Post by BoneKracker on 2010-06-06
I think something entirely different is called for.  XML is an over-rated dot-com era legacy, and configuration a "database" is a trouble-prone single point of failure with a restrictive interface.

In the spirit of Plan 9 and the original UNIX concept that everything is a file, I think we should have a _configuration filesystem_.

Think /proc/sys.

The possibilities that would enable, (e.g., network transparency, universal compatibility with any interface you care to come up with, etc.) are endless.

Very much a *nix-ish approach.  Why copy something from Windows that sucks?

---

### Post by 23meg on 2010-06-06
Moved to CC.

---

### Post by koenn on 2010-06-06
> **zaphod777 said:**
> 
Kind of a glorified text editor with a browser pane showing all of the various config .conf files and their respective locations. 

I would hate to take away the portability of linux programs.

How is that different from opening a bunch of files in, say, gedit tabs ?
finding config files isn't really a problem either, if you use a distro that is reasonably organised. if you dont know where the conf for program xyz is, try /etc/xyz. Works 99% of the time (at least on Debian-based distros) - and the ones that don't, how are you going to make them comply to any other standard ? 

The real problem is that there is no real standard for the content of config files. Some use sections, some don't, some are lists of values, some have keyword/value pairs, some are meant to be sourced by a shell or executed by a php engine, etc. You don't solve that with a bit of superficial userfriendliness.

Lastly, configuring a program requires knowledge. You need to know what your doing in order to know what to put there in those files. That's the really hard part. Editing a file is peanuts compared to that. 
(think : writing modes/monitor sync values/... in an xorg.conf)

So maybe the right solution is to greatly reduce, possibly abolish entirely the need for configuration (by end-users).

---

### Post by BoneKracker on 2010-06-06
> **koenn said:**
> So maybe the right solution is to greatly reduce, possibly abolish entirely the need for configuration (by end-users).
I can't believe you said that.

I'm at a loss for words -- and that's rare.

---

### Post by handy on 2010-06-06
I fixed other people's windows problems for 10 years, it was my job. During that time I noticed that the registry was the prime site for system corruption, bloat & the home of all but a few of the security threats that windows suffered from.

It is my view that the registry was a part of the plan by MS, to fragment the windows system in an effort to make copy protection more effective. As opposed to the easy method of application duplication found in Apple's systems.

I consider the registry to be an horrid over complex monster, invented to remove reliability & user freedoms from the windows systems from win95 on.

Configuration files are a vastly superior method of working with a system. & as Arch has proven it can be made to happen very simply in only a few files that need to be touched from time to time. Most other more specialised config files never need to be touched by the average user.

---

### Post by ronnielsen1 on 2010-06-06
> Before everyone gets up in arms. 
Too late
> Re: Does Ubuntu need a "registry"?
No No No No
>  	Quote:
 	 	 		 			 				 					Originally Posted by **koenn** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9418849#post9418849") 				
 				*So maybe the right solution is to greatly reduce, possibly abolish entirely the need for configuration (by end-users).*
 			 		 	 	 
I can't believe you said that.

I'm at a loss for words -- and that's rare. 	

:confused::rolleyes:

---

### Post by zaphod777 on 2010-06-06
What my idea was is to take something like this

[http://picasaweb.google.com/lh/photo/HF8n-98EMbkt3OxBP2voPw?feat=directlinkng](http://picasaweb.google.com/lh/photo/HF8n-98EMbkt3OxBP2voPw?feat=directlinkng)

And have something that will show you all of the various config files on your system.

We "shouldn't" need to edit them but if we need to add a line to or remove a line from the xorg.conf or another config file it would be a quicker way to find the needed config file and make the change.

---

### Post by ranch hand on 2010-06-06
> **23meg said:**
> Moved to CC.
I have no way of expressing the full depth of my gratitude.  You are a wonderful mod.

---

### Post by Timmer1240 on 2010-06-06
When I was using windows I did a lot of registry edits most of my friends never touched the registry.I would be fixing their machine and open up the registry editor and they where like whats that how did you get there!I sure learned a lot about windows If you have problems you learn at least thats what I did!Had some friends that took their computer in it got a virus they were charged 300 bucks what a rip never knew about it until after I couldve helped for free.I always enjoyed the challenge of it I guess some people dont know where to begin!

---

### Post by spupy on 2010-06-06
The registry has no documentation. Sure, there may be something on the internet, but the registry editor offers none - only cryptic variable's names. The Search option sucks.

Config files have helpful comments and examples. Use grep to find what you're looking for.

---

### Post by phrostbyte on 2010-06-06
Yes I think it would be a good idea. Microsoft's implementation is garbage, unfortunately they gave the whole concept a bad name. But take a look at Gconf if you want to see a registry implementation done right. It would be awesome if more apps used it.

---

### Post by phrostbyte on 2010-06-06
> **spupy said:**
> The registry has no documentation. Sure, there may be something on the internet, but the registry editor offers none - only cryptic variable's names. The Search option sucks.

Config files have helpful comments and examples. Use grep to find what you're looking for.

Gconf supports *two* levels of comments. :)

---

### Post by spupy on 2010-06-06
> **phrostbyte said:**
> Gconf supports *two* levels of comments. :)

Yeah, I was talking about the Windows registry. Gconf is a newer and better thought-out implementation of the registry model.

---

### Post by Paddy Landau on 2010-06-06
> **handy said:**
> ... Most other more specialised config files never need to be touched by the average user.
I think that Handy has made a valuable point here.

For most users (like me), all we need are the options that the program gives. I wouldn't even consider going to an external "configuration" program to change the settings in, say, Firefox or Gimp; I'd go to those programs and click Edit > Preferences.

For example, I used gconf-editor only once, when someone on the forum  instructed me to for a specific purpose.

In the same vein, those people who want to get "behind the scenes" would probably find it simpler to just open a text editor and edit the configuration file (as I used to with xorg.conf before the drivers were fixed for my screen).

Given all that, I'd say that a registry would be superfluous, and a waste of manpower to develop and maintain.

That's just my opinion, of course, but then I'm an end-user.

---

### Post by Phrea on 2010-06-06
I'm a very new user, and not software technical at all, but it sounds like you guys are now leaning towards a **regedit**, rather than a registry itself?
One program that keeps track of all the config files and options, remembers where they are, and when you open that program, it loads them into one convenient regedit-like program?
gconf is mentioned before, and it's a good start, but as said, that's for Gnome only.

To me, that sounds like a wonderful idea, if that is what this discussion is beginning to lean towards tho [and if it doesn't already exist].

My apologies to you old die hard users if I have missed the point, then consider my post not posted.

---

### Post by Shining Arcanine on 2010-06-06
> **zaphod777 said:**
> Before everyone gets up in arms. 

I think the Windows registry really has a bad rap it is really a good and easy way to make changes to many system in a quick and efficient manner. I am not fully convinced the registry slows a machine down it is all of the crap software people install that gums up their machine.

With that said I am not suggesting we implement the same system but something similar to the log file viewer where you can view all of your configuration files and then edit them as needed.  

You can have sections configuring wireless, grub, x, and etc.

I know in a perfect world everything should just work or be changed in the normal GUI.

But when things don't work it would really be nice to have it all in a well organized location. 

What do you think?
This is a bad idea because it will complicate the task of package managers (it breaks encapsulation) and it will allow crude to remain on systems in places not obvious to the user that will only cause problems down the road.

---

### Post by cprofitt on 2010-06-06
A registry is a good concept for 'system-wide' settings. Applications settings should not be placed in a registry... as it would require users to have access to the registry. (Yes, I know with Windows you can grant permissions per-key. The sad fact is more Windows developers are still following a Windows 98 mode of programming and have not followed standards).

In short -- a registry would be good for system variable, but not for application variables. To be honest the Linux system seems to work fine as is.

---

### Post by koenn on 2010-06-06
> **Phrea said:**
> I'm a very new user, and not software technical at all, but it sounds like you guys are now leaning towards a **regedit**, rather than a registry itself?
One program that keeps track of all the config files and options, remembers where they are, and when you open that program, it loads them into one convenient regedit-like program?
gconf is mentioned before, and it's a good start, but as said, that's for Gnome only.

To me, that sounds like a wonderful idea, if that is what this discussion is beginning to lean towards tho [and if it doesn't already exist].

My apologies to you old die hard users if I have missed the point, then consider my post not posted.

OK, so
the regedit way : figure out what key to edit, start regedit, navigate to / try to find required key, figure out appropriate stuff to put there, type up appropriate stuff, close and exit.  

the linux way : figure out what file to edit (make educated guess: /etc/name_of_program) , start file browser of choice, navigate to required file, open with text editor of choice,  figure out appropriate stuff to insert, type up appropriate stuff, save and exit.


I honestly don't see how the first is easier than the second

---

### Post by screaminj3sus on 2010-06-06
> **Paddy Landau said:**
> I disagree. Here's why.

The Windows registry was a fantastic idea -- in theory.

In practice, it became a monster. Programs had to rely on the registry for information about the system and even about themselves. The result was quite a bit of entanglement, which caused more than a few times of "sweat and tears" for me.

If you had a registry, even if optional, some programmers would start to rely on it. Those programs would become less and less portable, making it really hard for various distros.

One of the fantastic things about Linux is the way that configurations are held in folders in files. If I want to completely reset Firefox in Windows, I have to uninstall it, maybe reboot, then reinstall. That would affect every user on that computer. With Linux, all I need do is delete the .mozilla folder, and it affects only me, no one else on the system.

I can even back up the .mozilla folder first so that I can experiment and then restore (and I have done this on occasion). Try doing that with the Windows registry!

The current method in Linux seems to work excellently. If you need to get information about installed programs... Well, we already have a type of registry, namely Synaptic, don't we?

In the computer world, I've found through experience (and training) that the KISS philosophy ("keep it simple stupid") works best. Linux is simple. The registry is complex.

Um I can backup my mozilla appdata folder in windows and copy it back on a fresh isntall after installing firefox and have ALL my settings back just as easily. So that point is completely inaccurate for firefox and a lot of other apps.

---

### Post by Paddy Landau on 2010-06-06
> **screaminj3sus said:**
> Um I can backup my mozilla appdata folder in windows and copy it back on a fresh isntall after installing firefox and have ALL my settings back just as easily. So that point is completely inaccurate for firefox and a lot of other apps.
Yes, OK. The point I had was that you have to reinstall. On Linux, it's not necessary.

Anyway, the point is probably moot. I rather think that Linux developers won't create this registry thing, as it involves another level of unnecessary complexity.

---

### Post by aysiu on 2010-06-06
> **Paddy Landau said:**
> Yes, OK. The point I had was that you have to reinstall. On Linux, it's not necessary.
You don't have to reinstall.

The Windows equivalent to /home/username/.mozilla is C:\Documents and Settings\username\Application Data\Firefox

Just delete that folder, and it's reset. No need to uninstall and reinstall.

More details here:
[http://support.mozilla.com/en-us/kb/profiles#Where_is_my_profile_stored_](http://support.mozilla.com/en-us/kb/profiles#Where_is_my_profile_stored_)

---

### Post by mgmiller on 2010-06-06
Wouldn't something like ubuntu tweak be what the OP was looking for?
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Dr. C on 2010-06-06
> **aysiu said:**
> You don't have to reinstall.

The Windows equivalent to /home/username/.mozilla is C:\Documents and Settings\username\Application Data\Firefox

Just delete that folder, and it's reset. No need to uninstall and reinstall.

More details here:
[http://support.mozilla.com/en-us/kb/profiles#Where_is_my_profile_stored_](http://support.mozilla.com/en-us/kb/profiles#Where_is_my_profile_stored_)

FLOSS applications such as Firefox are not the best example as to what is wrong with the Windows Registry since they 
1) Are not concerned with trying prevent copying of the installed application by hiding stuff in the registry, a form of DRM that is the most common abuse of the Windows Registry and 
2) Are typically designed to be cross platform so they will implement the GNU / Linux model of configuration files in Windows anyway.

One of the biggest problems with the Windows registry is that there no simple way to remove all traces of an application when things go wrong, migrate an application, etc. This is by design since the reasons for the design of the Windows registry are primarily for DRM purposes; namely to frustrate the copying of installed applications, and frustrate the complete removal of applications in order to enforce limit trails for example, and push the purchase of trail applications. 

Even wonder why trail version of an anti-virus that is installed with a new computer is so difficult to remove?

---

### Post by toupeiro on 2010-06-06
The windows registry was the worst thing that happened to windows.  It was the first step to many failures, and it actually started in windows 3.11, but that was its infancy stage, which it was still clean and the rules with which it was designed were still followed.  Windows 95 made short work of those rules, and within a year it was not even recognisable anymore.   Now, the registry resides in multiple segments, which in my opinion is even worse.

I never understand why people take a gander at linux and "wonder" if it needs to look like windows.  There is an OS out there fully dependant on a registry, its called Windows.  Have a ball.

---

### Post by sdowney717 on 2010-06-06
> A registry is a good concept for 'system-wide' settings. Applications settings should not be placed in a registry... as it would require users to have access to the registry. (Yes, I know with Windows you can grant permissions per-key. The sad fact is more Windows developers are still following a Windows 98 mode of programming and have not followed standards).


yes, I wrote an app and made extensive use of the registry for storing local user program variables outside of the sql database and some small amount of encryption. It worked fine very convenient, BUT, if someone did not want users to be able to access the registry, it would be a problem. mostly did it because it was  convenient and easy. I could have setup this user data in the sql DB, but did not want to bother. I figured those user settings were local to each machine so why not keep it local in the registry. And I though about putting the local data into files, but I did not want users deleting or modifying them.

---

### Post by PhilGil on 2010-06-06
The Windows registry is a godawful piece of crap that (as others have mentioned) is in place primarily to restrict users from configuring their system and customizing their software.  It is the most significant point of failure in Windows systems and the biggest contributor to the performance degradation that occurs over time on Windows.  Yes, I'm also in IT and maintain Windows systems.

With that out of the way, I have used gconf-editor on several occasions and find it convenient, easy to understand and well laid out.  The built-in key documentation is genius.  A tool that provided a common interface to configuration files, modeled on gconf-editor, would be a great idea.

The reality, however, is that there are so many different ways to implement configuration files that I doubt it would work; and I don't think the situation really warrants forcing all program developers to do configuration the same way.

---

