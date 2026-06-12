---
title: "My List of What Linux Still Needs"
date: 2009-01-18
forum: Ubuntu Brainstorm
---

### Post by Yfrwlf on 2009-01-18
My new list of needed Linux features for anyone interested. :)


1 ) Feedback in the GUI when programs fail to be launched, and more user feedback in general.  To accomplish this, error output should be redirected to the GUI unless it is being run from the console.  There has to be a fundamental change that could accomplish this instead of just "tacking on" a fix, perhaps the entire program output and error reporting system needs redoing.

2 ) Use a cross-distro standard packaging API system.  Allow developers, regardless of whether they are creating closed or open source software, to be able to release a single package for Linux and have it install and work with a few clicks.  This will eliminate the need for the crappy installers and "work arounds" that have been developed to try to cope with this problem.

3 ) Along with the above which is sometimes the cause for the need to do so, put an end to the user ever needing to learn the command line.  That's not something that is expected of users on other platforms, and it shouldn't be on Linux either.  Specifically, find a more graceful method to deal with administrative privileges.  If this involves taking PackageKit further for instance, cool.  But pulling up a command line in order to get admin rights to something is a no-no.  Perhaps a more helpful permission denied error box, like one that includes a way to give admin credentials like what PackageKit does.

4 ) Make a user's drives be permanently mounted or give the ability to do so.  I don't know how many times I've seen a Windows user who's new to Linux change their desktop wallpaper to a file on their Windows drive/partition, only to find a black background for their desktop the next time they log in.  Something to deal with a new hard drive and perhaps an option to make it always mounted would be nice as well.  "Ubuntu has detected a new media: Seagate 500 GB hard disk.  Would you like to format and mount it now?"

5 ) One slider to adjust the "size" of one's desktop.  There are size adjustments for panels, fonts, etc etc, but if there was one thing to scale the entire desktop up or down, I think that may be useful to some users.  The way it is right now, Gnome by default has a "smaller" desktop in comparison to Windows at the same screen resolution, because the icons and windows are quite a lot bigger.  Where as some users may very much want exactly that, to others it makes Linux look more like a "toy".  If GTK had a way to scale everything up or down easily, that could potentially be a really awesome feature of Linux, to instantly have a much bigger desktop as in more desktop real estate.  More Firefox windows, more Nautilus windows, etc.  I'm not sure if this is a feature GTK currently has or can do, nor am I sure if QT might have it.

6 ) Always have to say it, but more drivers. ^^

7 ) Merge StartUp Manager and Login Window somehow, at the very least include a GUI option for changing the default OS, helpful for those who dual boot.

8 ) Bring back accessibility to virtual terminals and create a bailout hotkey for closing/minimizing full screen programs without having to ctrl-alt-backspace the entire desktop.  Not sure what happened or if it's a driver thing but X will hog access to terminals so that ctrl-alt-f# won't work if the main program running on F7 gets hosed.  A more stable graphics situation is needed and bailout keys for newbies who only know ctrl-alt-del.  Something like ctrl-alt-del is needed so users can escape back to the desktop or some kind of bailout system other than force-closing all their currently opened programs (without saving!) by forcing an X restart.  Program crashes happen, Linux needs to be able to gracefully deal.

9 ) Easier way of adding menu entries to Gnome without having to open the menu editor.  Dragging and dropping shortcut icons to the panel is great, now if only the menu could do things like that!

**Edit:** 10 ) Make desktop GUI responsiveness have higher priority so that the Linux desktop is capable of multitasking more gracefully.

**Edit:** 11 ) Make Linux, or give the option to make Linux use more RAM when available to speed things up and make the desktop snappier.  Make a Performance GUI section for general system performance settings like this.  This is a sorely missed area of the Linux desktop IMO.

Of course there are many more ideas, but these are some of the areas I can think of that are needed to make the Linux desktop better, and some sticking points for new potential Linux users that I witness as I show the masses what it's like living without Microsoft and Apple.  Feel free to contribute/comment. ^^

---

### Post by ushimitsudoki on 2009-01-18
These are mostly good ideas.

8 - Is AllowClosedownGrabs what you want here? I use this to kill fullscreen OpenGL games that have locked up.

---

### Post by barbedsaber on 2009-01-18
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)
have fun.

---

### Post by Yfrwlf on 2009-01-18
> **ushimitsudoki said:**
> These are mostly good ideas.

8 - Is AllowClosedownGrabs what you want here? I use this to kill fullscreen OpenGL games that have locked up.

That's part of the OGL API or is that a GTK API thing or what?  Well I have no idea how to do that, and if I don't, normal users, especially those coming from Windows, sure won't.  They need an **easy** solution, like ctrl-alt-del or the special/super/Windows key in Windows.

No offense, thanks tho. ^^

---

### Post by ushimitsudoki on 2009-01-18
This is a X server option.

--Rant ahead that has been building up for a while, please do not take personally--

Not to be rude, but frankly I couldn't give a tinker's damn about what "normal users" or those coming from Windows need. That's a sure-fire way to destroy Ubuntu - you'll run off the people that actually contribute and you won't ever make Windows-demanding people happy with Ubuntu **anyway**, because Linux **ain't** Windows and that's what they want. They **have** to come around to the Linux way of doing things - and we can improve the Linux way as that happens.

If that option does what you want, it takes exactly one line in xorg.conf to enable it, and then CTRL-ALT-KP* will kill fullscreen apps. How much easier exactly should that be? Should the xorg server magically read the user's mind and know if that option should be enabled, and what keystrokes the user expects?

Consider: the devs already think CTRL-ALT-BACKSPACE is too difficult for users - it's going to be disabled in Jaunty. How can one then argue that CtlAltBkSp is too difficult, but CtlAltKp* is desired? In both cases the justification is pretty much "Windows users are stupid." Now, **I** don't think that, but that's the basic justification put plain.

It also shows that you can pretty much pick anything and say it's "too hard". You know why? Because **anything** is "too hard", if you assume the user is a dribbling idiot. But, most users **aren't** dribbling idiots - not even the ones coming from Windows. They may need education, sure, but that does **not** make them stupid. People can get smarter, but design mistakes stay mistakes. And a system designed for idiots, stays designed for idiots.

Furthermore, Windows is **not** the gold standard to aspire to; Windows users are **not** the ideal user to cater to. I don't mean we look down on them or run them off, but we don't bend over backwards to accommodate them and try to turn Ubuntu into "no-cost Windows Extreme" either.

I don't mean to rant, but I'm sick to death of hearing about "normal users" or "Windows" every time someone mentions Linux usability. Fixing Bug #1 doesn't mean becoming Bug #1. We need to **improve** Linux, not **clone** Windows.

---

### Post by HungryMan on 2009-01-18
> **ushimitsudoki said:**
> This is a X server option.

Consider: the devs already think CTRL-ALT-BACKSPACE is too difficult for users - it's going to be disabled in Jaunty. 

WHAT!? But I use that when Compiz locks-up when I tinker with it.

Also, difficulty is subjective. The only thing objective that's remotely similar to difficulty is complexity. It involves many steps, it's complicated, but NOT difficult.

---

### Post by bruce89 on 2009-01-18
> **Yfrwlf said:**
> 1 ) Feedback in the GUI when programs fail to be launched, and more user feedback in general.  To accomplish this, error output should be redirected to the GUI unless it is being run from the console.  There has to be a fundamental change that could accomplish this instead of just "tacking on" a fix, perhaps the entire program output and error reporting system needs redoing.

A sort of GUI stderr. Interesting, but probably would be better to not have programs fail in the first place.

> **Yfrwlf said:**
> 2 ) Use a cross-distro standard packaging API system.  Allow developers, regardless of whether they are creating closed or open source software, to be able to release a single package for Linux and have it install and work with a few clicks.  This will eliminate the need for the crappy installers and "work arounds" that have been developed to try to cope with this problem.

This is impossible as all distros have different directories for the same things and some have different tools to do the same things.

> **Yfrwlf said:**
> 3 ) Along with the above which is sometimes the cause for the need to do so, put an end to the user ever needing to learn the command line.  That's not something that is expected of users on other platforms, and it shouldn't be on Linux either.  Specifically, find a more graceful method to deal with administrative privileges.  If this involves taking PackageKit further for instance, cool.  But pulling up a command line in order to get admin rights to something is a no-no.  Perhaps a more helpful permission denied error box, like one that includes a way to give admin credentials like what PackageKit does.

People don't have to learn the command line, and doing so is a good thing (depending on what you need to do). Getting rid of it would be crazy.

Also, you're thinking of PolicyKit.

> **Yfrwlf said:**
> 5 ) One slider to adjust the "size" of one's desktop.  There are size adjustments for panels, fonts, etc etc, but if there was one thing to scale the entire desktop up or down, I think that may be useful to some users.  The way it is right now, Gnome by default has a "smaller" desktop in comparison to Windows at the same screen resolution, because the icons and windows are quite a lot bigger.  Where as some users may very much want exactly that, to others it makes Linux look more like a "toy".  If GTK had a way to scale everything up or down easily, that could potentially be a really awesome feature of Linux, to instantly have a much bigger desktop as in more desktop real estate.  More Firefox windows, more Nautilus windows, etc.  I'm not sure if this is a feature GTK currently has or can do, nor am I sure if QT might have it.

There was a blog post about the possiblity of a scalable GTK+, as someone was annoyed how small everything was on their high-resolution screen.

> **Yfrwlf said:**
> 8 ) Bring back accessibility to virtual terminals and create a bailout hotkey for closing/minimizing full screen programs without having to ctrl-alt-backspace the entire desktop.  Not sure what happened or if it's a driver thing but X will hog access to terminals so that ctrl-alt-f# won't work if the main program running on F7 gets hosed.  A more stable graphics situation is needed and bailout keys for newbies who only know ctrl-alt-del.  Something like ctrl-alt-del is needed so users can escape back to the desktop or some kind of bailout system other than force-closing all their currently opened programs (without saving!) by forcing an X restart.  Program crashes happen, Linux needs to be able to gracefully deal.

It's called xkill.

> **Yfrwlf said:**
> 9 ) Easier way of adding menu entries to Gnome without having to open the menu editor.  Dragging and dropping shortcut icons to the panel is great, now if only the menu could do things like that!

The snag with this is I can imagine a lot of people making mistakes (trying to click, but they actually drag).

> **Yfrwlf said:**
> **Edit:** 11 ) Make Linux, or give the option to make Linux use more RAM when available to speed things up and make the desktop snappier.  Make a Performance GUI section for general system performance settings like this.  This is a sorely missed area of the Linux desktop IMO.

Linux, like all UNIX-type things cache everything they load into memory:

```

bruce@Scooby-Dum:~$ free
             total       used       free     shared    buffers     cached
Mem:       1024260     935692      88568          0      53112     376632
-/+ buffers/cache:     505948     518312
Swap:      1301224       4744    1296480

```

As you can see, only about 86.5 MiB of my memory isn't being used, of which about half is cached stuff.

---

### Post by ushimitsudoki on 2009-01-18
> **bruce89 said:**
> xkill comes to mind.

In my limited experience, when an OpenGL fullscreen game locks up, you can't get out of it, so xkill isn't an option.

Perhaps there is some way I don't know of - that's certainly possible. However, before I found AllowClosedownGrabs, the only other thing I found that worked was Ctrl-Alt-Backspace.

---

### Post by mamamia88 on 2009-01-18
heres my list

1. not having to reinstall flash at least once a month
2. finding easier ways to install stuff that is not in add/remove or synaptic.
3. why can't every developer that develops for ubuntu just make a deb already?

---

### Post by bruce89 on 2009-01-18
> **mamamia88 said:**
> 1. not having to reinstall flash at least once a month

Nothing can be done about non-free stuff.

> **mamamia88 said:**
> 3. why can't every developer that develops for ubuntu just make a deb already?

Because there is no such thing as "develop[ing] for ubuntu", you write the code and hope it runs on as many distros as possible.

---

### Post by mamamia88 on 2009-01-18
dang man i just had to rant after flash broke for the millionth time on me

---

### Post by Shippou on 2009-01-18
> **ushimitsudoki said:**
> This is a X server option.

--Rant ahead that has been building up for a while, please do not take personally--

Not to be rude, but frankly I couldn't give a tinker's damn about what "normal users" or those coming from Windows need. That's a sure-fire way to destroy Ubuntu - you'll run off the people that actually contribute and you won't ever make Windows-demanding people happy with Ubuntu **anyway**, because Linux **ain't** Windows and that's what they want. They **have** to come around to the Linux way of doing things - and we can improve the Linux way as that happens.

If that option does what you want, it takes exactly one line in xorg.conf to enable it, and then CTRL-ALT-KP* will kill fullscreen apps. How much easier exactly should that be? Should the xorg server magically read the user's mind and know if that option should be enabled, and what keystrokes the user expects?

Consider: the devs already think CTRL-ALT-BACKSPACE is too difficult for users - it's going to be disabled in Jaunty. How can one then argue that CtlAltBkSp is too difficult, but CtlAltKp* is desired? In both cases the justification is pretty much "Windows users are stupid." Now, **I** don't think that, but that's the basic justification put plain.

It also shows that you can pretty much pick anything and say it's "too hard". You know why? Because **anything** is "too hard", if you assume the user is a dribbling idiot. But, most users **aren't** dribbling idiots - not even the ones coming from Windows. They may need education, sure, but that does **not** make them stupid. People can get smarter, but design mistakes stay mistakes. And a system designed for idiots, stays designed for idiots.

Furthermore, Windows is **not** the gold standard to aspire to; Windows users are **not** the ideal user to cater to. I don't mean we look down on them or run them off, but we don't bend over backwards to accommodate them and try to turn Ubuntu into "no-cost Windows Extreme" either.

I don't mean to rant, but I'm sick to death of hearing about "normal users" or "Windows" every time someone mentions Linux usability. Fixing Bug #1 doesn't mean becoming Bug #1. We need to **improve** Linux, not **clone** Windows.


What an enlightening post! :)

This sure stays in the mind: 
Fixing Bug #1 doesn't mean becoming Bug #1. We need to **improve** Linux, not **clone** Windows.

Gonna make this my sig, together with this:

"What Intel giveth, Microsoft taketh away."

Cheers,
Shippou

---

### Post by perce on 2009-01-18
> **Yfrwlf said:**
> My new list of needed Linux features for anyone interested. :)


1 ) Feedback in the GUI when programs fail to be launched, and more user feedback in general.  To accomplish this, error output should be redirected to the GUI unless it is being run from the console.  There has to be a fundamental change that could accomplish this instead of just "tacking on" a fix, perhaps the entire program output and error reporting system needs redoing.


I agree completely with this point it would be useful, but my biggest wish is monitors hotplug: being able to add an external monitor to my laptop without having to restart X.

---

### Post by kk0sse54 on 2009-01-18
> 2 ) Use a cross-distro standard packaging API system.  Allow developers, regardless of whether they are creating closed or open source software, to be able to release a single package for Linux and have it install and work with a few clicks.  This will eliminate the need for the crappy installers and "work arounds" that have been developed to try to cope with this problem.
They do you just need to compile and install it yourself :P. Otherwise I really don't think we need to have a standardized package management system since linux is all about choice and my preference might sound absolteuly ghastly to you :)

> 3 ) Along with the above which is sometimes the cause for the need to do so, put an end to the user ever needing to learn the command line.  That's not something that is expected of users on other platforms, and it shouldn't be on Linux either.  Specifically, find a more graceful method to deal with administrative privileges.  If this involves taking PackageKit further for instance, cool.  But pulling up a command line in order to get admin rights to something is a no-no.  Perhaps a more helpful permission denied error box, like one that includes a way to give admin credentials like what PackageKit does.
while I agree we can still ease the transition to using the command line I don't think it should just totally thrown away. Every linux user should at least have some sort of a basic understandong of the terminal as it's an incredibly powerful tool and isn't going to be going anywhere any time soon.

>  4) Make a user's drives be permanently mounted or give the ability to do so.  I don't know how many times I've seen a Windows user who's new to Linux change their desktop wallpaper to a file on their Windows drive/partition, only to find a black background for their desktop the next time they log in.  Something to deal with a new hard drive and perhaps an option to make it always mounted would be nice as well.  "Ubuntu has detected a new media: Seagate 500 GB hard disk.  Would you like to format and mount it now?"
Just edit your fstab


> 7 ) Merge StartUp Manager and Login Window somehow, at the very least include a GUI option for changing the default OS, helpful for those who dual boot.

grub?


> **Edit:** 11 ) Make Linux, or give the option to make Linux use more RAM when available to speed things up and make the desktop snappier.  Make a Performance GUI section for general system performance settings like this.  This is a sorely missed area of the Linux desktop IMO.
Just decrease your swapiness

---

### Post by steveneddy on 2009-01-18
I agree with more drivers.

---

### Post by smartboyathome on 2009-01-18
> **Yfrwlf said:**
> 1 ) Feedback in the GUI when programs fail to be launched, and more user feedback in general.  To accomplish this, error output should be redirected to the GUI unless it is being run from the console.  There has to be a fundamental change that could accomplish this instead of just "tacking on" a fix, perhaps the entire program output and error reporting system needs redoing.

They've been doing something similar during the testing phase which is more useful, having it submit bugs. For some reason, though, it is disabled upon release. A shame, really, because it is really helpful when submitting bugs.

> **Yfrwlf said:**
> 2 ) Use a cross-distro standard packaging API system.  Allow developers, regardless of whether they are creating closed or open source software, to be able to release a single package for Linux and have it install and work with a few clicks.  This will eliminate the need for the crappy installers and "work arounds" that have been developed to try to cope with this problem.

That won't happen, because when they try to, distros fight. I like the pacman package manager, but you might like the debian package manager (included in Ubuntu). There is also RPM, portage (in Gentoo), as well as many others. Many distros would not think about changing their own package manager because it would be too much work for too little gain (imagine Ubuntu having to port all of its 25,000 different packages to RPM :o).

> **Yfrwlf said:**
> 3 ) Along with the above which is sometimes the cause for the need to do so, put an end to the user ever needing to learn the command line.  That's not something that is expected of users on other platforms, and it shouldn't be on Linux either.  Specifically, find a more graceful method to deal with administrative privileges.  If this involves taking PackageKit further for instance, cool.  But pulling up a command line in order to get admin rights to something is a no-no.  Perhaps a more helpful permission denied error box, like one that includes a way to give admin credentials like what PackageKit does.

Even in Windows, I have had tech support have me use the command line. It won't ever go away, but certain tasks which need it can have GUIs added to make things easier.

I do agree that it would be helpful to have a "Run as Administrator" checkbox in the alt+f2 run dialog to make things easier for users. :)

> **Yfrwlf said:**
> 4 ) Make a user's drives be permanently mounted or give the ability to do so.  I don't know how many times I've seen a Windows user who's new to Linux change their desktop wallpaper to a file on their Windows drive/partition, only to find a black background for their desktop the next time they log in.  Something to deal with a new hard drive and perhaps an option to make it always mounted would be nice as well.  "Ubuntu has detected a new media: Seagate 500 GB hard disk.  Would you like to format and mount it now?"

I think that PySDM might be good for you. It is too technically made for the average user, though, since fstab is too technical for the average user. If the drives were represented with their label (like in nautilus), then it might be a little easier for them.

> **Yfrwlf said:**
> 5 ) One slider to adjust the "size" of one's desktop.  There are size adjustments for panels, fonts, etc etc, but if there was one thing to scale the entire desktop up or down, I think that may be useful to some users.  The way it is right now, Gnome by default has a "smaller" desktop in comparison to Windows at the same screen resolution, because the icons and windows are quite a lot bigger.  Where as some users may very much want exactly that, to others it makes Linux look more like a "toy".  If GTK had a way to scale everything up or down easily, that could potentially be a really awesome feature of Linux, to instantly have a much bigger desktop as in more desktop real estate.  More Firefox windows, more Nautilus windows, etc.  I'm not sure if this is a feature GTK currently has or can do, nor am I sure if QT might have it.

I think neither XFCE, GNOME, nor KDE have this. There are gconf settings for this in GNOME (I think) so making a GUI for it wouldn't be trivial.

> **Yfrwlf said:**
> 6 ) Always have to say it, but more drivers. ^^

Yep, if only manufacturers recognized Linux more as a viable platform to release drivers for. :(

> **Yfrwlf said:**
> 7 ) Merge StartUp Manager and Login Window somehow, at the very least include a GUI option for changing the default OS, helpful for those who dual boot.

How about a graphical GRUB. It shouldn't be too trivial on newer hardware (might be on older hardware).

> **Yfrwlf said:**
> 8 ) Bring back accessibility to virtual terminals and create a bailout hotkey for closing/minimizing full screen programs without having to ctrl-alt-backspace the entire desktop.  Not sure what happened or if it's a driver thing but X will hog access to terminals so that ctrl-alt-f# won't work if the main program running on F7 gets hosed.  A more stable graphics situation is needed and bailout keys for newbies who only know ctrl-alt-del.  Something like ctrl-alt-del is needed so users can escape back to the desktop or some kind of bailout system other than force-closing all their currently opened programs (without saving!) by forcing an X restart.  Program crashes happen, Linux needs to be able to gracefully deal.

I wish that X had a universal binding for the xkill command. Unfortunately, though, it doesn't (which is why it doesn't work in 3D games).

> **Yfrwlf said:**
> 9 ) Easier way of adding menu entries to Gnome without having to open the menu editor.  Dragging and dropping shortcut icons to the panel is great, now if only the menu could do things like that!

I see this backfiring, as I sometimes accidentally drag menu items. If this were enabled, the menu items would get deleted off the menu. :(

> **Yfrwlf said:**
> **Edit:** 10 ) Make desktop GUI responsiveness have higher priority so that the Linux desktop is capable of multitasking more gracefully.

Isn't this something GNOME, KDE, etc or even Xorg is responsible for? Remember, Ubuntu packages stuff together, and doesn't do as much developing of stuff. That is what Red Hat is for. :P

> **Yfrwlf said:**
> **Edit:** 11 ) Make Linux, or give the option to make Linux use more RAM when available to speed things up and make the desktop snappier.  Make a Performance GUI section for general system performance settings like this.  This is a sorely missed area of the Linux desktop IMO.

How about an option to adjust swapiness in the power preferences? I doubt GNOME would allow it, though.

> **mamamia88 said:**
> 2. finding easier ways to install stuff that is not in add/remove or synaptic.

This isn't possible, as compiling from source is very trivial. Only way to do this is really with a universal package manager (and as said above, this won't happen because distros will fall into fighting).

---

### Post by kk0sse54 on 2009-01-18
> **smartboyathome said:**
> 
I do agree that it would be helpful to have a "Run as Administrator" checkbox in the alt+f2 run dialog to make things easier for users. :)
Good suggestion but I don't think gksudo is too hard to type either.


> 
How about an option to adjust swapiness in the power preferences? I doubt GNOME would allow it, though.
Great idea :)

---

### Post by cardinals_fan on 2009-01-18
1. A huge +1.  Feedback is ***essential***

2. I'm not saying that it is a bad idea, but I have yet to see any reasonable standard that can actually be implemented and implemented well.  I don't see why a package should be anything more than a gzip'd file.

3. What exactly is wrong with gksu, kdesu, subox, and everything else out there?

4. This is definitely possible, since it only requires a minor modification to fstab.

5. I don't see the point, but it could be useful for some.

6. Yeah, I'd like for Santa to be real too.

7. Fedora has a bootloader configuration tool.

8. Xkill could easily be bound to a shortcut key.

9. It would strike me as fairly logical to edit a menu with the menu editor, but maybe I'm crazy.

10. What is "desktop GUI responsiveness"?  Does it have to do with resource usage?

11. Preload?

---

### Post by smartboyathome on 2009-01-18
> **C!oud said:**
> Good suggestion but I don't think gksudo is too hard to type either.

> **cardinals_fan said:**
> 3. What exactly is wrong with gksu, kdesu, subox, and everything else out there?

The problem is how discoverable it is. "Run as administrator" in the Run box is far easier than having to search the web for gksu/kdesu.

---

### Post by cardinals_fan on 2009-01-18
> **smartboyathome said:**
> The problem is how discoverable it is. "Run as administrator" in the Run box is far easier than having to search the web for gksu/kdesu.
Yes, but the whole point is that these tools already exist.  I'll be the first to agree that distros targeting new users could make them more accessible with menu shortcuts, but there's no need to do anything major.  I'm also entirely unsure of what the OP meant by "taking PackageKit further".

---

### Post by smartboyathome on 2009-01-18
> **cardinals_fan said:**
> Yes, but the whole point is that these tools already exist.  I'll be the first to agree that distros targeting new users could make them more accessible with menu shortcuts, but there's no need to do anything major.  I'm also entirely unsure of what the OP meant by "taking PackageKit further".

I didn't ask for anything major. Just a checkbox which says "Run as administrator". ;)

Also, I think the OP means that it might involve using packagekit to grant permissions instead of something like (gk)sudo.

---

### Post by cardinals_fan on 2009-01-19
> **smartboyathome said:**
> 
Also, I think the OP means that it might involve using packagekit to grant permissions instead of something like (gk)sudo.
Perhaps they meant **PolicyKit**? ;)

---

### Post by MockY on 2009-01-23
> **C!oud said:**
> 
Just edit your fstab


You shouldn't have to even open fstab. fstab is way beyond what an average  computer user should have to deal with. I mean, for the user who just wants to use a computer and does not give a crap about the inner workings, the following line means absolutely nothing:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
nor will they know how to add or change things in it. This is obviously fine for the stereotypical Linux user who enjoys tinkering with these things. Canonical is not pushing Ubuntu on the Uber-Geek, but to regular people such as my mother, neighbor, or grandpa...in other words "Human Beings". Simply telling the user that a new hard drive has been detected and asking what the user would like to do with it does not seem like something that would be to hard to implement.

Furthermore, this should be the case for most hardware. If I plug in, lets say, a USB network card. Ubuntu does not notify you what so ever about it, nor asks you what you want to do. In order for restricted drivers (if required) for this device to even show up in the restricted driver manager, you have to reboot your system. Seems odd.

Again, I'm fine with the way it is since I actually enjoy poking with things and figure out how things work, but for a lot of people...not so much.

---

### Post by galileon on 2009-01-26
> **ushimitsudoki said:**
> Fixing Bug #1 doesn't mean becoming Bug #1. We need to **improve** Linux, not **clone** Windows.

QFT. I wish the devs wouldn't turn into Redmond zombies and force stuff like pulseaudio(read stuttering audio) or Xorg 1.7(no more Nvidia GL acceleration) on the rest of us...

---

### Post by bruce89 on 2009-01-26
> **galileon said:**
> QFT. I wish the devs wouldn't turn into Redmond zombies and force stuff like pulseaudio(read stuttering audio) or Xorg 1.7(no more Nvidia GL acceleration) on the rest of us...

Why is PulseAudio MS-related? Also, nothing stops you using an old distribution if you really want to.

---

### Post by galileon on 2009-01-27
> **bruce89 said:**
> Why is PulseAudio MS-related? 
It's not. But it feels awfully like it. (think UAC, SP2, etc)

> **bruce89 said:**
> 
Also, nothing stops you using an old distribution if you really want to.

I still use Gutsy Gibbon, but it's showing signs of old age (new programs ask for new libraries, which need new xxx-lib which needs new yyy-lib, etc. (Nothing specific in mind atm), but I'll need a new desktop install soon. In fact, I'm probably gonna try intrepid. I'll just pray my skype and nvidia drivers will work :D (*bows head in shame*).

---

### Post by bruce89 on 2009-01-27
> **galileon said:**
> It's not. But it feels awfully like it. (think UAC, SP2, etc)

PulseAudio is a necessary thing, alsa just didn't work. All new technology has teething problems (D-Bus, HAL etc.), so it's not fair to the developers of PulseAudio to keep complaining about it.

---

### Post by cardinals_fan on 2009-01-27
> **bruce89 said:**
> PulseAudio is a necessary thing, alsa just didn't work. All new technology has teething problems (D-Bus, HAL etc.), so it's not fair to the developers of PulseAudio to keep complaining about it.
ALSA worked just fine for me.  I don't need PulseAudio...

---

### Post by Twitch6000 on 2009-01-27
> **Yfrwlf said:**
> My new list of needed Linux features for anyone interested. :)


1 ) Feedback in the GUI when programs fail to be launched, and more user feedback in general.  To accomplish this, error output should be redirected to the GUI unless it is being run from the console.  There has to be a fundamental change that could accomplish this instead of just "tacking on" a fix, perhaps the entire program output and error reporting system needs redoing.

2 ) Use a cross-distro standard packaging API system.  Allow developers, regardless of whether they are creating closed or open source software, to be able to release a single package for Linux and have it install and work with a few clicks.  This will eliminate the need for the crappy installers and "work arounds" that have been developed to try to cope with this problem.

3 ) Along with the above which is sometimes the cause for the need to do so, put an end to the user ever needing to learn the command line.  That's not something that is expected of users on other platforms, and it shouldn't be on Linux either.  Specifically, find a more graceful method to deal with administrative privileges.  If this involves taking PackageKit further for instance, cool.  But pulling up a command line in order to get admin rights to something is a no-no.  Perhaps a more helpful permission denied error box, like one that includes a way to give admin credentials like what PackageKit does.

4 ) Make a user's drives be permanently mounted or give the ability to do so.  I don't know how many times I've seen a Windows user who's new to Linux change their desktop wallpaper to a file on their Windows drive/partition, only to find a black background for their desktop the next time they log in.  Something to deal with a new hard drive and perhaps an option to make it always mounted would be nice as well.  "Ubuntu has detected a new media: Seagate 500 GB hard disk.  Would you like to format and mount it now?"

5 ) One slider to adjust the "size" of one's desktop.  There are size adjustments for panels, fonts, etc etc, but if there was one thing to scale the entire desktop up or down, I think that may be useful to some users.  The way it is right now, Gnome by default has a "smaller" desktop in comparison to Windows at the same screen resolution, because the icons and windows are quite a lot bigger.  Where as some users may very much want exactly that, to others it makes Linux look more like a "toy".  If GTK had a way to scale everything up or down easily, that could potentially be a really awesome feature of Linux, to instantly have a much bigger desktop as in more desktop real estate.  More Firefox windows, more Nautilus windows, etc.  I'm not sure if this is a feature GTK currently has or can do, nor am I sure if QT might have it.

6 ) Always have to say it, but more drivers. ^^

7 ) Merge StartUp Manager and Login Window somehow, at the very least include a GUI option for changing the default OS, helpful for those who dual boot.

8 ) Bring back accessibility to virtual terminals and create a bailout hotkey for closing/minimizing full screen programs without having to ctrl-alt-backspace the entire desktop.  Not sure what happened or if it's a driver thing but X will hog access to terminals so that ctrl-alt-f# won't work if the main program running on F7 gets hosed.  A more stable graphics situation is needed and bailout keys for newbies who only know ctrl-alt-del.  Something like ctrl-alt-del is needed so users can escape back to the desktop or some kind of bailout system other than force-closing all their currently opened programs (without saving!) by forcing an X restart.  Program crashes happen, Linux needs to be able to gracefully deal.

9 ) Easier way of adding menu entries to Gnome without having to open the menu editor.  Dragging and dropping shortcut icons to the panel is great, now if only the menu could do things like that!

**Edit:** 10 ) Make desktop GUI responsiveness have higher priority so that the Linux desktop is capable of multitasking more gracefully.

**Edit:** 11 ) Make Linux, or give the option to make Linux use more RAM when available to speed things up and make the desktop snappier.  Make a Performance GUI section for general system performance settings like this.  This is a sorely missed area of the Linux desktop IMO.

Of course there are many more ideas, but these are some of the areas I can think of that are needed to make the Linux desktop better, and some sticking points for new potential Linux users that I witness as I show the masses what it's like living without Microsoft and Apple.  Feel free to contribute/comment. ^^

Interesting list... I must reply to this list :D.

1. I agree here... this needs to be fixed =[...

2. I have been thinking about this recently and I have to agree... it would make things so much easier...

3. Agreed

4. I think this is possible not sure though. However if it is not possible,yes this needs to be made possible.

5. Well I know on some DE's and Distros this is made possible.(to some extint) However I do not think this is to big of a deal.

6. Who can't agree :P.

7. I think there is a program that does just this... I think Ubuntu Tweak Or some other program like Ubuntu Tweak does this.(I know I used it... lol)

8. no comment

9. I am not sure if I am getting this, because I can simply add items with a few clicks >.>.

10. Agreed

11. I think this has been a question before, and I think this should be made. Only as a choice though ;).

---

### Post by maspin on 2009-01-27
> **ushimitsudoki said:**
> This is a X server option.

--Rant ahead that has been building up for a while, please do not take personally--

Not to be rude, but frankly I couldn't give a tinker's damn about what "normal users" or those coming from Windows need. That's a sure-fire way to destroy Ubuntu - you'll run off the people that actually contribute and you won't ever make Windows-demanding people happy with Ubuntu **anyway**, because Linux **ain't** Windows and that's what they want. They **have** to come around to the Linux way of doing things - and we can improve the Linux way as that happens.

If that option does what you want, it takes exactly one line in xorg.conf to enable it, and then CTRL-ALT-KP* will kill fullscreen apps. How much easier exactly should that be? Should the xorg server magically read the user's mind and know if that option should be enabled, and what keystrokes the user expects?

Consider: the devs already think CTRL-ALT-BACKSPACE is too difficult for users - it's going to be disabled in Jaunty. How can one then argue that CtlAltBkSp is too difficult, but CtlAltKp* is desired? In both cases the justification is pretty much "Windows users are stupid." Now, **I** don't think that, but that's the basic justification put plain.

It also shows that you can pretty much pick anything and say it's "too hard". You know why? Because **anything** is "too hard", if you assume the user is a dribbling idiot. But, most users **aren't** dribbling idiots - not even the ones coming from Windows. They may need education, sure, but that does **not** make them stupid. People can get smarter, but design mistakes stay mistakes. And a system designed for idiots, stays designed for idiots.

Furthermore, Windows is **not** the gold standard to aspire to; Windows users are **not** the ideal user to cater to. I don't mean we look down on them or run them off, but we don't bend over backwards to accommodate them and try to turn Ubuntu into "no-cost Windows Extreme" either.

I don't mean to rant, but I'm sick to death of hearing about "normal users" or "Windows" every time someone mentions Linux usability. Fixing Bug #1 doesn't mean becoming Bug #1. We need to **improve** Linux, not **clone** Windows.

My idea for what Linux still needs, is a less elitist attitude!

The only way your OS will improve is if a wider audience uses it. Otherwise any improvement will be a slow and painful process, as there is less demand, and less reason to better the OS. The easier the OS is to use, the more people will use it. Which means the better it will get.

I agree that Ubuntu should not be a clone of Windows (And I don't think it ever will be), but this just sounds elitist.. I am a "Normal" user. I moved over from Windows recently and I am happy I did. But attitudes like this will never help. You should welcome the new, because that is where the majority of the future of your OS is.. 

Otherwise, stick to your current distribution, and never upgrade.. If it works well for you now, keep it that way.. But don't expect everything to stay complicated because you like it that way.. You may understand how your OS works better than alot of other people do, but it doesn't mean they don't deserve something they can understand..

Don't think I'm trying to start a conflict here. But as a new user (one who is actually ABLE to understand Ubuntu well enough to solve my own problems) I only see this mindset as slowing Linux down in the long run

---

### Post by cardinals_fan on 2009-01-27
> **maspin said:**
> My idea for what Linux still needs, is a less elitist attitude!
Would you show me some examples of an elitist attitude?
> **maspin said:**
> 
The only way your OS will improve is if a wider audience uses it. Otherwise any improvement will be a slow and painful process, as there is less demand, and less reason to better the OS. The easier the OS is to use, the more people will use it. Which means the better it will get.
"Improvement" is entirely subjective.
> **maspin said:**
> 
Otherwise, stick to your current distribution, and never upgrade.. If it works well for you now, keep it that way.. But don't expect everything to stay complicated because you like it that way.. You may understand how your OS works better than alot of other people do, but it doesn't mean they don't deserve something they can understand..

They deserve something they can use and I deserve something I can use.  This is the great thing about Linux: we have multiple distributions that offer different things to different audiences.  I can have a clean, simple base system and those who want them can have total automation and complex GUIs.  I believe that everyone deserves something they want to use, including myself.

---

### Post by maspin on 2009-01-27
> Would you show me some examples of an elitist attitude?
Some stuff here about what I see as an elitist attitude.
[http://entertainment.slashdot.org/article.pl?sid=09/01/15/158216](http://entertainment.slashdot.org/article.pl?sid=09/01/15/158216)

That whole story is ridiculous. This lady was being threatened and treated teribally because she wasn't all that technologically inclined.. Sure, it isn't THAT hard to figure Ubuntu out. There are other factors into the reasons she dropped out. But this (from my eyes) gives a bad view of Linux.

> "Improvement" is entirely subjective.

Yeah. Improvement is based on personal perceptions.. But even so, I am sure you find your OS has some major improvements from a few years back?

> They deserve something they can use and I deserve something I can use. This is the great thing about Linux: we have multiple distributions that offer different things to different audiences. I can have a clean, simple base system and those who want them can have total automation and complex GUIs. I believe that everyone deserves something they want to use, including myself.

Yep, multiple distrobutions to suit the needs of the people using them.. I really love that concept.
Ubuntu is one of the easiest ones to make that first step over from another OS. So on an Ubuntu forum, I thought the attitude in the comment 

> I'm sick to death of hearing about "normal users" or "Windows" every time someone mentions Linux usability

was a bit odd for an OS known for being more suitable for a "normal user" or someone in the transition from Windows.

I am not saying everyone who uses Linux is an elitist.. In fact, most of the people I know that use it are pretty helpful.

---

### Post by cardinals_fan on 2009-01-27
> **maspin said:**
> Some stuff here about what I see as an elitist attitude.
[http://entertainment.slashdot.org/article.pl?sid=09/01/15/158216](http://entertainment.slashdot.org/article.pl?sid=09/01/15/158216)

That whole story is ridiculous. This lady was being threatened and treated teribally because she wasn't all that technologically inclined.. Sure, it isn't THAT hard to figure Ubuntu out. There are other factors into the reasons she dropped out. But this (from my eyes) gives a bad view of Linux.
1. "That whole story" is absurd.  Uninformed/lazy consumer buys a product she doesn't want.  *yawns*

2. There's a reason I avoid Slashdot and Digg.  They attract the lowest forms of life lurking around the internet outside of Youtube comments.
> **maspin said:**
> 
Yeah. Improvement is based on personal perceptions.. But even so, I am sure you find your OS has some major improvements from a few years back?
Yes, but only a small fraction of the publicity about operating systems over the past few years has benefited me.  I really have no interest in Compiz, Pulseaudio, Plasma, and many other so-called "revolutionary" components.  I have noticed tremendous growth in hardware support in the Linux kernel and I love SliTaz's Tazwok system.
> **maspin said:**
> 
Yep, multiple distrobutions to suit the needs of the people using them.. I really love that concept.
Ubuntu is one of the easiest ones to make that first step over from another OS. 
This is why I'm not completely trolling here in the Ideas section.  I am willing to respect that Ubuntu aims at someone other than myself, and am content to use NetBSD and SliTaz while trying to give some sane input here.
> **maspin said:**
> 
So on an Ubuntu forum, I thought the attitude in the comment 

was a bit odd for an OS known for being more suitable for a "normal user" or someone in the transition from Windows.

I am not saying everyone who uses Linux is an elitist.. In fact, most of the people I know that use it are pretty helpful.
I do understand what the poster in question is thinking.  If you reread that post, it was actually quite well-reasoned and, in my opinion, the *opposite* of elitist.  (S)he says: > But, most users aren't dribbling idiots - not even the ones coming from Windows. They may need education, sure, but that does not make them stupid. People can get smarter, but design mistakes stay mistakes.
I see that as a pretty sensible attitude.

---

### Post by maspin on 2009-01-28
Yeah, slashdot is a bit odd that way..

I wasn't saying she didnt make a huge mistake, she did. She also blamed all her problems on the fact that she has an OS she wasn't used to. But the responses that created were in some cases, rather harsh.

I can understand his frustration, but as a "normal user" and someone who recently migrated to Ubuntu, I find the resentment towards what *I* use it for a bit frustrating.. I don't want to fork over massive amounts of money for an OS and software that I don't even like.. Probably just as much as him.. So I think my opinions and needs for Ubuntu should be just as valid! :)

---

