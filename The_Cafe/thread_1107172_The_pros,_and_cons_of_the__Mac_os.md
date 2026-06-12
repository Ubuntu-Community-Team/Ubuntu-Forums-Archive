---
title: "The pros, and cons of the  Mac os"
date: 2009-03-26
forum: The Cafe
---

### Post by swoll1980 on 2009-03-26
I have to do an outline of the pros, and cons of the 3 major operating systems Windows XP, OSX, and Linux. Windows, and Linux are easy, because I use them everyday, on the other hand I have never used a Mac OS, so what do you think are the good things, and bad things about the Mac OS? Please keep it objective, no Mac sucks, or anything that isn't helpful thanks.

---

### Post by mamamia88 on 2009-03-26
id say a pro was that it's like linux but without as much effort and i'd say a con was that it costs alot and you can't customize the gui as much

---

### Post by JohnFH on 2009-03-26
You mean this?:

[http://en.allexperts.com/q/Macs-Apples-1506/Pros-Cons-Mac-OS.htm]("http://en.allexperts.com/q/Macs-Apples-1506/Pros-Cons-Mac-OS.htm")

---

### Post by damis648 on 2009-03-26
**_Pros:_**
User friendly for computer novices
Secure
Has software from major software developers (Microsoft, Adobe, etc.)
Hardware and software are sold together, so as to avoid hardware incompatibilities and issues.

**_Cons:_**
Very, Very restrictive (very closed source, can only be installed on Apple computers, EFI, etc.)
Hardware (only hardware that can legally use the OS) is very expensive.


I bet I know more but cannot think of them now.

---

### Post by swoll1980 on 2009-03-26
> **JohnFH said:**
> You mean this?:

[http://en.allexperts.com/q/Macs-Apples-1506/Pros-Cons-Mac-OS.htm]("http://en.allexperts.com/q/Macs-Apples-1506/Pros-Cons-Mac-OS.htm")

Well I could have used a different source, but doing it here gives you guys something to talk about, so I figured I'd come here.

---

### Post by hewbert on 2009-03-26
I second what damis648 says.

I use OSX everyday.  I won't go into details on that though.

At first, I was not impressed with it, I eventually grew more impressed, and now, I'm back to not being impressed at all, really.  I'd advocate it to some Windows friends that are tired of Windows but don't want something like Linux.

It's easy to use and a lot of things "just work", but that's about it.  If you're into hacking away and customizing things, it's considerably restrictive in that regard.  I often wonder why the developers didn't add more options for certain things (i.e. the dock - not much to configure there).  A lot of tasks that are trivial to us users of x.org based desktops require some third party utility on the Mac, which often costs money.


Jordan Hubbard (One of the FreeBSD founders and now "Director of Engineering of Unix Technologies" at Apple said in an interview:

> 
JA: What is it about your new job that's fun?

Jordan Hubbard: The work environment and the people I get to work with are certainly a real high point, but I think the coolest thing is being able to work on a really NICE desktop OS which doesn't make a bunch of horrible compromises to achieve user friendliness, like welding the hood shut as programmers like to describe working with Windows. There's a real Unix under there and on the desktop, I can blast Wintel PC users over the net in Return to Castle Wolfenstein! How much better than that does it get? :)


:: [Full Interview Here]("http://kerneltrap.org/node/278")

Of course, this is all my perspective.  YMMV, etc.

---

### Post by mrsteveman1 on 2009-03-26
I've used all of the major OS for a long time, Windows since 3.1 all the way through 7, OS X, probably 6 different desktop distros of Linux. I manage linux servers daily, and i've used freebsd and solaris quite a bit as well. There simply isn't another operating system for desktop use that is put together better.

From a users perspective:

Application installation and removal is very well thought out, but can easily be made difficult if developers choose to alter system files or install things where they shouldn't otherwise be. Applications on OS X are distributed most of the time as a .App bundle, which is really just a folder but the operating system treats it as a single file. To install most applications, you download them and drag them into the Applications folder, and run them. All the needed files, libraries, pictures, graphics, sounds and music that application needs to run are usually inside that .App bundle or provided by the operating system, so it can be moved around and thrown in the trash easily. This is in contrast to some platforms that require sophisticated tools to install and uninstall applications or make changes all over the place, for instance Windows applications commonly alter the Windows registry, something that is hard to track and detect, and difficult to undo. There are package installers for OS X and a few applications do use them, for instance if an application needs to install a driver, usually a .pkg installer will be used, such as with VMwares Fusion software.

On an interface level, i very much like the desktop design Apple has chosen, like the dock. You can put applications you commonly use down there, and they stay there whether they are running or not. Conceptually there is a separation of the running application, from the windows it provides for you to work in, they reside in different parts of the dock and are functionally separate, in contrast to Windows where a running application tends to be represented by its open application windows. Some people don't like that because it is difficult to go from the Windows metaphor of clicking items on the taskbar to activate them, however if you use Expose it is even faster to multi-task and switch between open application windows, assuming you like using Expose, if you don't you would hate it, because without Expose it is difficult to switch between application windows :)


The default appearance of OS X, at least in 10.5, is quite attractive, and all applications benefit from it, things for the most part have a consistent look and feel which makes it easier to work once you get used to it, and makes it easier for users to pick up new applications.

A lot of things that users would otherwise require help with, are already done by Apple, for instance configuring file sharing for a local network is very easy, opening the preferences panel, clicking sharing, and checking the box next to file sharing. Control over what gets shared and who can access it is in the same window with a simple easy to understand layout. The same thing is true of almost everything, from setting up a printer to connecting a new hard drive and formatting it, or burning a CD, all of them require little effort.

From a security point of view:

OS X makes it very easy to protect your personal information, a single check box will enable you to encrypt your home folder and all of your personal data, so that if the laptop is stolen your data can't be read or used to steal your identity. This comes with the system and has for a few years now, i believe since around 2003. To do this on other platforms requires planning before installation (ubuntu alternate install cd encryption), working in the terminal (encrypting home folder manually in linux or windows), or installing separate 3rd party applications after the OS is installed (truecrypt). Vista now makes it easy to encrypt the entire operating system, but only if you buy the business or ultimate editions, which most people do not have.

There is also a simple checkbox to enable encryption for the swap file the system uses for virtual memory (When ram is in short supply). This makes it much harder for someone to steal your laptop and recover passwords you used on your bank website, or recover personal data you wrote in a text editor or on a web page. Similar things can be done on Linux, but again not without a special installation CD in most cases, or working in the terminal.

The operating system itself is more secure by default compared to windows, there are no highly vulnerable services open and listening on the network by default without your knowledge, Windows for a long time has shipped with the SMB over TCP port 445 open along with 137,138 and 139, which have in the past been used to spread malware around the internet. OS X also does not suffer from the flawed services model of Windows, where background services can interact in any way they wish with the user or with user processes, things are segmented and protected from each other by default because the core of the system is Unix based.


From a developer/administrators perspective:

The operating system itself is very well designed, for a while it seemed like i would find something in my use of OS X daily that made me think, wow, that was really a good design decision. And by that i mean from the lowest levels, all the way down to the firmware that starts the system, to the interior kernel design, to the graphic display system, to the individual components of the OS that keep it running, all of them reflect attention to detail and careful planning which pays off big in some situations.

At a low level, the firmware is quite intelligent, it knows what hardware is in the system at boot time, and it passes that information to the kernel during the boot process so that the kernel does not have to probe for hardware itself like another kernel would, say for instance Linux. At the same time, OS X does driver "caching", if nothing has changed in the hardware it can load a cached copy of all needed drivers into memory at once instead of loading each one from the filesystem. This speeds boot time significantly.

The firmware also can be extended and used for much more complex operations than simply booting the operating system, it can be extended with a full unix-like shell, it can be given arbitrary new drivers to read new filesystems or operate on the network (it has a full TCP/IP stack).

The OS also keeps a list of "hot files" on the hard drive, and moves them to areas of the disk that can be accessed quickly and sequentially. It can also do on the fly defragmentation, if a file meets a few criteria like being smaller than 20mb and not currently in use (among other things) it will automatically be defragmented the next time it is opened.

The init system on OS X as of 10.4 is called Launchd, it can launch daemons and run services on demand or respond to events on the system, and it can monitor services and keep them running if they fail for some reason. Ubuntu now has a similar system called Upstart, though they are not using it to its full potential right now, it is simply acting as a wrapper for the old init system.

The programming frameworks are very high quality and in most cases allow developers to easily and quickly produce easy to use beautiful applications. 

Thats all i can think of off the top of my head, that was a bit more pro than con (if at all), but i find very few cons, most of them have to do with personal preference or getting used to the way the OS works. I'm sure someone will call me out on at least SOMETHING i said, or correct me, but yea. there you go. :)

---

### Post by JackieChan on 2009-03-26
It's pretty secure, it's user friendly, has a lot of software developers like Adobe backing it up, and it's the next best operating system for PC gaming besides Windows.

---

### Post by swoll1980 on 2009-03-26
Here's What it looks like if anyone cares. I'm still learning word, so might not be to pretty. Format is not important for this class. Thanks for the input.

---

### Post by dragos240 on 2009-03-26
My only reference is my friend tom.

My experience is:

PROS:
Nice bash-like terminal,
Unix-like style
Very pretty gui!

CONS:
As said before, closed source.
Bad with hardware that doesn't come with it.
One button mouse (yuck)

And i really can't say much more about it.

---

### Post by damis648 on 2009-03-26
> **dragos240 said:**
> One button mouse (yuck)

Ugh, here we go again. THE MOUSE HAS FOUR BUTTONS. They just aren't visible. You can left, right, and middle click, and you can pinch the sides. Four buttons.

---

### Post by dragos240 on 2009-03-26
guess my friend tom didn't know that either, he always told me it was one, also i could find any other, also when i clicked left, nothing different, right no different, middle, see where i'm going?

---

### Post by damis648 on 2009-03-26
> **dragos240 said:**
> guess my friend tom didn't know that either, he always told me it was one, also i could find any other, also when i clicked left, nothing different, right no different, middle, see where i'm going?

You have to enable them. :popcorn: Just go into System Preferences and choose Mouse, adjust what each button does. By default, they all work the same. You can set the right to option click for right click, and middle to dashboard and pinch to expose, that's what most do.

---

### Post by conundrumx on 2009-03-26
> **dragos240 said:**
> My only reference is my friend tom.

My experience is:

PROS:
Nice bash-like terminal,
Unix-like style
Very pretty gui!

CONS:
As said before, closed source.
Bad with hardware that doesn't come with it.
One button mouse (yuck)

And i really can't say much more about it.

That's not a "bash-like" terminal, it's good old fashioned bash.
```
$ bash --version
GNU bash, version 3.2.17(1)-release (i386-apple-darwin9.0)
```

I was poisoned by another Mac user, and for me the pros are simple.  It's a POSIX OS (I can compile plenty of tarballs with little to no extra switches/modifications, on top of running plenty of my standard tools), and "it just works."™  I reached a point where running Linux on my Thinkpad was sometimes more frustrating than my servers and users combined.  In list form:

Pros:
- Tightly integrated experience (since the same company controls HW and SW boot time is fantastic, and driver concerns outside the odd peripheral are non existent)
- POSIX compiant, Unix like OS.  Bash, nmap, nc, X11, ssh.  It's all available.
- Amazing community of independent developers.  Yes, some of the apps cost money, but pretty much all of them are on par with some of the best F/OSS has to offer.  (GNOME Do, Firefox, etc)
- Lower TCO than Windows, if you include time and anguish in your calculations!
- Small market share = small malware market share

Cons:
-Expensive entry price.  The associated Hardware doesn't really have a low end model the way a lot of PC manufacturers do.
- Less mainstream applications are developed for OSX, though with time this is changing.
- Much less customization options.
- Less protection from actual exploits.  (See: Charlie Miller's comments)

I tried to stay away from the hardware, since that's a whole 'nother holy war.

---

### Post by mrsteveman1 on 2009-03-26
OS X is not really closed source, in comparison to windows it is WAY more open. You can get the source for SOME of Windows too depending on who you work for and what you want to do with it, you can get the source for a LOT of OS X regardless of the reason.

They don't provide source to their windowing system, or their core libraries, those are some of the most valuable parts of the OS. The kernel is open source, you can grab the source, build it and replace the one that came with the system. Much of the userland is open source, launchd the system controller for lack of a better word (init, cron, inetd etc) is open source, some of the implementations of protocols like bonjour are open source.

---

