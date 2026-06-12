---
title: "Comments from a Linux newbie"
date: 2007-05-20
forum: Testimonials &amp; Experiences
---

### Post by davlaw2000 on 2007-05-20
Hi yes another newbie with things to say. :o
Please forgive me if it's all been said before but I really believe in Linux  and the whole philosophy behind it. I have been a Windows user since Windows 3.11 and was a DOS user before that. I have used Commodore Amigas, Atari STs etc etc so feel I have seen enough OSes to know my way around. I installed Ubuntu on a home PC as an experiment and was blown away by  a) How quickly and easily it installed  b) how user-friendly it is and c) the other software that is 'bundled' with it. 
Now the criticisms....
I tried downloading and installing Xmame and GXmame (which went OK) and then tried copying over some ROMS from an old CD I had from years back. That's when I started hitting permission problems. For some reason I had virtually no permission to do anything and quickly found myself learning the joys of sudo and chmod. 
I got there in the end after hours of digging around in docs and forums. I do understand the whole 'you don't have permission' thing but is it unreasonable to ask for a method of sorting this out via the GUI, without resorting to typing commands in a terminal window?
You will probably disagree but I feel that whenever a 'dumb user' such as me has to resort to opening a terminal window and typing in commands then the GUI has failed. If it's like that for security reasons then how come you can get round it with a couple of simple commands in a terminal window? I can't remember the last time I had to open a 'command prompt' to do something in Windows. Why can't the GUI be extended to reduce to an absolute minimum the number of times you have to resort to typing in raw commands?
Ubuntu is labelled 'Linux for humans' and it really does go a long way to fulfilling that promise. I would say it is still for highly literate computer lovers as you have to know a significant amount about what goes on under the covers in order to achieve pathetically simple things like creating a new folder and copying files into it. 
Don't get me wrong I don't like Windows but you have to accept it is very user-friendly and generally intuitive. 
Is it worth me suggesting some specific GUI enhancements in this direction or is there a fundamental reason why such things will never ever become a part of Ubuntu? If there is then I have to say that most computer users I know will never put it on their computers as they have neither the time nor the inclination to get their hands so dirty. 
Like I say, sorry if you have heard it all before.....

---

### Post by bobplano on 2007-05-20
some distro's come with an option to open the file browser as root. Mepis i think, is an example if this. if you want to stay with ubuntu but don't want to type in commands for things like your cds you can use the command
```
gksudo nautilus
``` 
to open the file browser as root. there are plenty of other distro's if your not satisfied with ubuntu.

---

### Post by Zootropo on 2007-05-20
> **bobplano said:**
> some distro's come with an option to open the file browser as root. Mepis i think, is an example if this. if you want to stay with ubuntu but don't want to type in commands for things like your cds you can use the command
```
gksudo nautilus
``` 
to open the file browser as root. there are plenty of other distro's if your not satisfied with ubuntu.

Thunar has an option to open the current folder as root.
You may be more interested on that one.

---

### Post by ofb on 2007-05-20
I've been using 6.10 since Februrary and have a very similar background to you, starting with the PET. I'm still definitely an Ubuntu beginner, and only want to offer a minor observation here. 

I didn't have /any/ problem with permissions setting up and using kxmame, and didn't need to use CLI. What I have noticed elsewhere, and what you may be experiencing, is a lot of people online tend to give CLI advice, and they tend to give bad advice. On any given issue I've got stuck in, perhaps 4/5ths of what's suggested online isn't the best way to do things, and can really send you down a rabbit hole.

I'm wondering if perhaps you've just stubbed your toe on that situation. Keep an eye out for it anyway.

Strictly IMHO so far: Ubuntu isn't "ready for the desktop", but neither is Windows. Overall I definitely find Ubuntu is better, though still full of frustrations. My advice to anyone would be it's not easy. You'll have to become as savvy with it as you have to be with Windows to get Win running reliably and secure. It's a steep learning curve either way.

It's easy to think Win is intuitive after you've lived with it a long time. But I'm fortunate to remember deep frustration for several weeks converting from Amiga to Win. My experience converting to Ubuntu brought a lot of that back and reminds me that "intuitive" is pretty subjective.

---

### Post by userundefine on 2007-05-20
> **davlaw2000 said:**
> I do understand the whole 'you don't have permission' thing but is it unreasonable to ask for a method of sorting this out via the GUI, without resorting to typing commands in a terminal window?
You will probably disagree but I feel that whenever a 'dumb user' such as me has to resort to opening a terminal window and typing in commands then the GUI has failed. If it's like that for security reasons then how come you can get round it with a couple of simple commands in a terminal window? I can't remember the last time I had to open a 'command prompt' to do something in Windows. Why can't the GUI be extended to reduce to an absolute minimum the number of times you have to resort to typing in raw commands?
I don't think it's unreasonable to want to assume privileges from the GUI.  In fact, this is a limitation of nautilus (the default file manager in Gnome) than Linux itself.  As others have pointed out, different file managers give you the option to open a file/directory with root privs.  Konqueror also does this.  It's not about security of the CLI.  When you open synaptic, once you click the program the "command" is run that says "The user wants to open this program with root privileges" and then you get a GUI prompt for your password.  Nautilus just doesn't have that functionality built in, or at least that's how I remember it because it's been a while since I used it.

> Don't get me wrong I don't like Windows but you have to accept it is very user-friendly and generally intuitive. 
Is it worth me suggesting some specific GUI enhancements in this direction or is there a fundamental reason why such things will never ever become a part of Ubuntu?
Now here's where I think you're wrong.  A program just crashed in Windows while you're using it: any program.  Non-highly literate computer user does what?  Does the user go look at the Event log to see why it may have crashed?  No, average user doesn't know it exists.  This is common for the Windows environment: oh gosh, something crashed again, *proceed to double-click program to start once more*.  There is no questioning like "Windows isn't ready for the desktop" "Windows is buggy and unintuitive".  No one questions Windows like they do Linux because they probably grew up with Windows and try out Linux because they hear that it's "better".  When you hear something is "better", you inevitably have high expectations, and if something goes wrong, it's even MORE a disappointment because it was supposed to be better.  If something goes wrong in Windows, it's business-as-usual and you're used to having that happen.

So, I think you're wrong and simply proceed from an ignorance (meaning unaware, *not* meaning stupid) of being habituated to Windows' faults and expecting Linux to solve all of them.  And, when I say 'you' here, it's not a personal attack at all, and it generally more representative of the whole of new Linux users who have similar initial hurdles as you do.  I hope this has helped.

---

### Post by HereInOz on 2007-05-20
The reason that Windows is "easier" with the permissions thing is that Windows runs at administrator (root) level by default, whereas Ubuntu does not.  Not running as root is perhaps a very good thing, given the number of not particularly nice things out on the Internet.

It looks like all you needed to do is to learn one command, and that is:

gksudo nautilus

This will open a file browser with root priviledges, giving you all the functionality you desire.

Compare this to running Windows with restricted "user"  priviledges, and having to log out and log back in as administrator every time you run into the permissions thing.

I understand that the permissions thing is a nuisance some time, but the only other alternative is to run permanently as root, and that is a dangerous thing.  (see all the Windows users who have suffered drive-by downloads because of exactly this).

There is a way that "gksudo nautilus" can be put on the desktop, but do you really want it to be that easy?  Better to hide it a little, I feel.

---

### Post by aysiu on 2007-05-20
Windows isn't easier with permissions at all.

I run my Windows computer at work with limited permissions and also have an administrator account. It is not fun to try to do an administrative task like moving a system file--I essentially have to log out of the limited account, log into the administrative account, make the change, log out of the administrative account, and then log back into the limited account. That's because Windows has nothing like *gksudo nautilus*. *Run as...* does not work for Windows Explorer or (successfully) for Windows Updates. And since my work computer is on a domain, I can't use *Switch User* to do a quick switch to the administrative account. I actually have to log out and log back in and log out and log back in to make the change.

And Windows is not any more intuitive than Ubuntu. It has you use the Start menu to shut down. You have to use Control-Alt-Delete (a memorized key combination) to deal with many problems. I know a lot of even self-proclaimed non-tech-savvy users who have memorized Control-Alt-Delete. That's what it's all about--memorizing and getting used to doing things a certain way.

I will say that I have always wanted Ubuntu to include a Nautilus superuser mode by default (Mepis has a Konqueror superuser mode), but the devs don't dig that idea. Right now you have to find out through a web search how to use ```
gksudo nautilus
``` or a Nautilus script to get that kind of functionality.

---

### Post by grb1944 on 2007-05-20
Another newbie here. Have just spent 48 hours trying to get Ubuntu installed, running, and the programs I need installed. At end of first 24 hours I have little hair left, however things started to improve. I wiped the partition and installed a second time. Must have learnt something the first time because I now have most of the programs installed and running that I need. After thinking about the learning curve we experienced with Windows 95, 98, 
2000, xp and now vista I accept it takes time. It is a challenge now, not a frustration. Two questions. Is there a video editing program equivalent to Sony Vegas and another, Macromedia MX2004? When entering commands such as sudo etc are these entered in the terminal. Is this the location for entering all commands for program installation etc. Any help would be appreciated. Cheers.

---

### Post by linfidel on 2007-05-21
I'm an old Windows user, too.  I find linux easier in many ways as far as permissions go.  In Windows, if you don't run as administrator (and you really shouldn't), then you use "Runas", which doesn't work for everything from the GUI.  Vista is actually better in this regard, and prompts you for the password when needed.

By the way, you can't use runas in Explorer, because it's always running, and when you run it, it sees that it's running, and reverts to the running copy.  There is a trick, though.  You can run Internet Explorer using runas, then show folder view, and use it like Explorer, more or less.  But everything you run from it in that mode will be run as administrator.  PITA, but it works.

I've been using cygwin at work to do cross platform developement, using Xterm and Vim, so using linux at home wasn't too much of a stretch.  I like it a lot, and I may get VMware to run those Windows programs I need to use (right now I have 2 computers with a KVM switch).  I've recently installed every popular distro, some multiple times, and Ubuntu was by far the easiest and friendliest.  But they were all much, much better than a few years ago, and mostly they all worked well.

I loved being able to browse the internet while installing Ubuntu!

-- Marty Fried
public . forums @ gmail . com

---

### Post by aysiu on 2007-05-21
> **linfidel said:**
> 
By the way, you can't use runas in Explorer, because it's always running, and when you run it, it sees that it's running, and reverts to the running copy.  There is a trick, though.  You can run Internet Explorer using runas, then show folder view, and use it like Explorer, more or less.  But everything you run from it in that mode will be run as administrator.  PITA, but it works. Thanks for the tip. I don't even deal with system files, but if I do, that's a good trick to know.

---

### Post by Kobalt on 2007-05-21
> **aysiu said:**
> I will say that I have always wanted Ubuntu to include a Nautilus superuser mode by default
I'm with you on that aysiu. This could fit just fine in the System > Admin. menu, asking the password to launch. I know you can add it manually, but it would be neat to have it by default.

---

### Post by davlaw2000 on 2007-05-21
Thank you all for your responses. Confusingly they range from "you need to know more about the operating system to get the most from it" all the way to "it would be a good idea if Nautilus included such features". 
Just to clarify, all I wanted to do was create a new folder and copy some files over from a CD. 
I do understand the potential risks, so I was thinking of an extension to Nautilus that says "you are not currently authorised to do that but click here, enter the correct password and I will think about it". 
I suppose if I knew a bit more about the Linux filesystem I might find that I CAN create folders, but only in the right place (maybe as a User I have my own space somewhere, where I can create folders and store stuff - who knows?). My point is that the GUI stopped dead and just said "you can't do that". The favourite solution is 'gksudo nautilus' but even that has to be typed in a command window. 
I suppose the argument I am trying to put forward is this....
"If a user has to resort to typing commands in a terminal window then the GUI has failed them". 
I would expect that this will polarise opinion, but I would say the ultimate user-friendly GUI would allow the User to accomplish ANYTHING that can be done in a command window. 
I suppose this stems from laziness. I know so many different OSes at the command line level that I just don't have the willpower to get to grips with yet another one. It takes such a long time!
Thank you again for your input. :D

---

### Post by 3rdalbum on 2007-05-21
```
sudo apt-get install nautilus-gksu && killall nautilus
```

Whenever you want to open a folder or a file as root, right-click on it and select "Open as Administrator". I too think that the package should be included by default.

By the way, I had the opportunity to try and fix someone's Windows problems today. I didn't manage to fix many of them, but while using Google I found Microsoft's knowledgebase website. Microsoft's preferred solutions to some of these problems were to hack around with the registry and type in big long command strings into the MS-DOS prompt.

Heck, I had to resort to the MS-DOS prompt in order to batch encode some WMA files. Microsoft's oh-so-powerful GUI tried to make me encode them one at a time - not practical when you've got 5 albums on your hard disk to transcode.

---

### Post by aysiu on 2007-05-21
> **davlaw2000 said:**
> Thank you all for your responses. Confusingly they range from "you need to know more about the operating system to get the most from it" all the way to "it would be a good idea if Nautilus included such features". Well, I can explain what you consider confusing: what you're noting as being a deficiency is, in fact, a deficiency (one many of us have tried to propose to the developers to fix, and it's been rejected before with the false logic that users shouldn't be messing around with the system folders if they don't know what they're doing), **but** it's not a major deficiency and the workaround exists in a way that does not currently for Mac and Windows (no *gksudo Finder* or *gksudo explorer*).

> The favourite solution is 'gksudo nautilus' but even that has to be typed in a command window.  Well, it does in Ubuntu because the developers have chosen not to include it as a button or a keyboard shortcut. That's an implementation choice not a technological limitation.

You can very well create your own launcher or keyboard shortcut and thus not have to use the command window.

---

### Post by linfidel on 2007-05-21
> **davlaw2000 said:**
> Thank you all for your responses. Confusingly they range from "you need to know more about the operating system to get the most from it" all the way to "it would be a good idea if Nautilus included such features". 
Just to clarify, all I wanted to do was create a new folder and copy some files over from a CD. 
 The usual place to put stuff is in your home directory; you can create subdirectories here, too.  This is equivalent, in Windows, to C:\Documents and Settings\*UserName*  where *UserName* is your login name.

If you aren't familiar with the command line in linux, one big thing to know is that you can always access your home directory by using a tilde (~).  So, if you want to copy a file to "Documents" in your home directory, you would type "cp somefile ~/Documents".  Note that case always matters.

-- Marty Fried
public . forums @ gmail . com

---

### Post by davlaw2000 on 2007-05-23
Thanks again for the responses. The concensus seems to be that the GUI is a bit too restricted when it comes to file and folder management. 
Thank you also to Marty, for telling me that I should have created my new folder in the 'Home' directory. I just wish that somehow the GUI had made this more obvious to me. Perhaps an icon labelled 'My Files' or similar would have jumped out at me as being the obvious place to put new stuff.  I suppose I might have wanted to put it into a place where all users can access it, and that would not have sufficed. 
The other problems I encountered were quite similar.....
- the Partition Manager (can't remember the name - gparted?) would not run properly and suggested I might not have Root access. Fine but as a dumb user I neither understand this message nor know how to resolve it. I was therefore unable to prepare, partition and format the second hard drive in my PC.   I did find some instructions on how to do it via native commands in the terminal window(!) but again stumbled on the permissions side of things. 
- once I had partitioned and formatted the drive I had no permission to create a folder and copy files to it. 
- I ended up with an icon for the new hard drive on my desktop (not sure why) and could not find an easy way to get rid of it.

To be brutally honest I consider all of the above to be 'gui failures' as I was unable to see a way to resolve the problem via the gui and had to resort to the good old terminal window (after much rooting around on the Internet). When I was a software developer at IBM we put apps into a 'usability lab' and watched people use them with little/no training, so we could judge how user-friendly they were. A call to the 'help desk' (which these days is the equivalent of rooting around in Google/Forums) was considered a failure and we got a butt-kicking. 

My current conclusion is therefore that while Ubuntu goes a LONG way to being user-friendly, and the installation process is relatively pain-free, a real 'dumb user' will stumble and fall on all but the simplest tasks. 
Perhaps part of the solution is the equivalent of the 'Welcome to Windows' tutorial, which would cover the basics of the file system (including where to create personal files/folders) among other 'important things to know'. 

I suggest that the other part of the solution is to continue the effort to make the GUI (and the apps) even easier to use, particularly in the areas of file/folder permissions, and further prompting for passwords etc particularly when Root authority might be necessary to complete a task.   Most of the solutions/workarounds to the problems I experienced require a skill level higher than 'dumb user' - perhaps 'semi-geek' or 'apprentice nerd'? I realise that the apps are a separate issue but they were bundled into the distro and I considered them to be part of the OS. Others will do this too.

Thank you all for your responses. Now the hard questions....
[LIST=1]
[*]Are sufficient numbers of people saying the same things as me?
[*]Can so many people all be wrong?
[*]Will the 'user friendliness' thing ever really be grasped and addressed?
[/LIST];)

---

### Post by userundefine on 2007-05-23
[LIST=1]
[*]Are sufficient numbers of people saying the same things as me?
[*]Can so many people all be wrong?

Maybe, I really wouldn't know.  Different newbies have different complaints.  Most I'd say aren't as articulate about it as you seem to be, though.


[*]Will the 'user friendliness' thing ever really be grasped and addressed?

Probably, but you also have to understand that usability means different things to different people.  Because of that, there are MANY different GUis available for Linux.  If Gnome doesn't suit you, you can also try KDE, XFCE, or others, but those are probably the most user-friendly and feature-replete for new users.
[/LIST];)

---

### Post by Altarbo on 2007-05-24
> **davlaw2000 said:**
> [ . . . ]

Thank you all for your responses. Now the hard questions....
[LIST=1]
[*]Are sufficient numbers of people saying the same things as me?
[*]Can so many people all be wrong?
[*]Will the 'user friendliness' thing ever really be grasped and addressed?
[/LIST];)1. I started using Ubuntu a couple weeks ago and had the exact same problem.  I really feel like the root of the problem is the documentation though.  After I installed Ubuntu, I immediately started trying to move some files I had on a cd onto the harddrive, and found I couldn't do that.  I'm like, "OK, so how do I get permission?"  I get on ubuntu.com go to the docs pages and find this:[https://help.ubuntu.com/7.04/user-guide/C/nautilus.html](https://help.ubuntu.com/7.04/user-guide/C/nautilus.html) Do a quick ctrl+f and see if you find sudo mentioned at all there.  You won't.  

So I read that, get frustrated, and come to the forums.  I find many threads started by people that had the same problem and links to site like this:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
Do another ctrl+f and see if anything about sudo is there.  It's not.  It's because most of the docs are written for people that already know what they're doing.  The docs are not meant to educate and explain the *purpose and function *of commands, but to provide a cheat sheet for users that have forgotten the *names* of commands.  (there is some writing that is apparently geared toward people who have never used a computer before, but this isn't what I need either)

I found out about the sudo commands by accident.  I was reading instructions on how to do something and got an error message after entering a command line instruction, so I found a page with common Linux commands on it and read what the function of every piece of the command I had just typed was.  

I figured out that I could make launchers do command lines commands whenever I ran a program by typing its name into CLI.

3. I think so.  I honestly think that what I've seen of the UI isn't that bad.  As more people like us (people who haven't used a *nix system before.) begin using Linux, you'll see more literature geared toward that crowd.

---

### Post by aysiu on 2007-05-24
Well, it is a common issue, but there are several points of contention here:

1. **Is the issue Linux-specific or Ubuntu-specific?** It's Ubuntu-specific. I know at least Knoppix and Mepis has Superuser Mode as a menu item and Edit as Root as a context menu choice. So it's a matter of policy implementation, not technological implementation.

2. **Why is it a big issue?** Two reasons--A) Windows XP (which is currently in more common use than Vista) defaults to running as administrator, so people do not realize how difficult it is to manage and run XP with a separate limited and administrator account. It's actually more difficult than Ubuntu. B) Most Ubuntu users (99.999% or more probably) had to install and configure Ubuntu themselves. They couldn't just *use* Ubuntu. They had to perform a lot of administrative tasks to get things up and running. Buying the computer preinstalled with Ubuntu minimizes or nullifies the issue.

3. ***How* big an issue is it?** Honestly, it's big in terms of being widespread, but it is not big in terms of urgency. Set up a launcher or keyboard shortcut for *gksudo nautilus* and be done with it. Many of us (even those who are experienced with Ubuntu) have proposed to the developers to add in an authentication instead of just "you can't do that" when moving files to system folders or trying to edit system files. The developers, up until this point, have said no... maybe not an explicit "no," but waiting six years to... still not implement something... that's a kind of "no."

More details here:
[http://bugzilla.gnome.org/show_bug.cgi?id=65058](http://bugzilla.gnome.org/show_bug.cgi?id=65058)
[https://bugs.launchpad.net/nautilus/+bug/12154](https://bugs.launchpad.net/nautilus/+bug/12154)

---

### Post by davlaw2000 on 2007-05-25
Thanks again for the comments. Again I can see difference of opinion. I do understand the fundamental differences between (say) Windows XP and Ubuntu, and I do appreciate that different distros may go about things in a different manner - perhaps allowing a superusuer mode to get around permissions issues. 
My point though is that as a true dumb user you should neither know nor care HOW something is achieved - you just want to do something and you get frustrated when the OS appears to stand in your way. 

When you drive a car, you see a familiar set of controls no matter which type of car you drive. I accept that manual and automatic are quite different, but there are really not that many variations. A 'dumb user' can understand quite quickly how to start the engine and drive around. Do they have to know whether the engine has 16 valves or 8? How about whether it has a turbocharger or not? These things have no significant impact on the user interface. 

Switch over to computers. One OS lets me create folders and copy stuff into them. It even warns me against putting stuff into certain folders as they are a vital part of the OS itself. Cool. Another one seems to stop me, unless I open some wierd command window and type even wierder commands into it. Not cool. 

My point is that the 'engine' should be totally hidden from view and fundamental stuff like creating folders and copying files is such a basic task that the GUI should have it covered in such a way that HOW it is achieved is irrelevant to the User. You either CAN or CAN'T do something. If you CAN then it should just get on with it. If you CAN'T then the OS should tell you why not. If you CAN provided you ask nicely (ie provide more information) then the OS should prompt you for the information it requires to complete the task. 
Until this is addressed, the majority of the computer users I know will not convert to any flavour of Linux, as a lot of them are basic Users with no intention of becoming apprentice geeks.

---

### Post by aysiu on 2007-05-25
> **davlaw2000 said:**
> 
Switch over to computers. One OS lets me create folders and copy stuff into them. It even warns me against putting stuff into certain folders as they are a vital part of the OS itself. Cool. Another one seems to stop me, unless I open some wierd command window and type even wierder commands into it. Not cool. And one OS is extremely susceptible to viruses and malware, mainly because it defaults to letting you do pretty much anything you want. What you're basically saying is "Windows makes me the total administrator of the computer, and Ubuntu makes me administrator only with authentication," and I hate to be the one to tell you this, but the second scenario is more secure.

This has nothing to do with typing weird commands into a window. As I said before, Mepis and Knoppix already have a Superuser Mode, which is something you **click**. They also have a context menu (**right-click**) that allows you to Edit as Root (another thing you **click on**. Do you know **clicking** is not typing? Do you know it doesn't require the terminal?

If you run Windows in a secure fashion, as a limited user, you will find it far more difficult to administer and will long for the days when you could create a *gksudo nautilus* launcher. **Run as...** in Windows is extremely crippled.

But I've already said this two times before (this is the third time). I don't think you're getting it. You've somehow idealized Windows and don't really understand that Windows is worse when it comes to authentication and privilege escalation.

Your car analogy doesn't fly. I don't know anything about how the OS operates any more than I know how my car operates. I don't know what all those boot time services are that are running. I don't know what all those config files mean (there are three main config files I know... but I also know how to check the oil, coolant, and brake fluid in my car!). Here's a better analogy:

The mattress can store your money, and you don't have to remember a password or find an ATM machine. You can withdraw cash in the convenience of your own home. The bank forces you to find an ATM machine, carry around a card, and also remember a PIN code in order to withdraw cash. Those banks just make life too much trouble... geez!

In case you missed my earlier points, I'll repeat them again: [quote=me]Well, I can explain what you consider confusing: what you're noting as being a deficiency is, in fact, a deficiency (one many of us have tried to propose to the developers to fix, and it's been rejected before with the false logic that users shouldn't be messing around with the system folders if they don't know what they're doing), but it's not a major deficiency and the workaround exists in a way that does not currently for Mac and Windows (no gksudo Finder or gksudo explorer).[/quote] > Well, it does in Ubuntu because the developers have chosen not to include it as a button or a keyboard shortcut. That's an implementation choice not a technological limitation.

You can very well create your own launcher or keyboard shortcut and thus not have to use the command window. > Well, it is a common issue, but there are several points of contention here:

1. Is the issue Linux-specific or Ubuntu-specific? It's Ubuntu-specific. I know at least Knoppix and Mepis has Superuser Mode as a menu item and Edit as Root as a context menu choice. So it's a matter of policy implementation, not technological implementation.

2. Why is it a big issue? Two reasons--A) Windows XP (which is currently in more common use than Vista) defaults to running as administrator, so people do not realize how difficult it is to manage and run XP with a separate limited and administrator account. It's actually more difficult than Ubuntu. B) Most Ubuntu users (99.999% or more probably) had to install and configure Ubuntu themselves. They couldn't just use Ubuntu. They had to perform a lot of administrative tasks to get things up and running. Buying the computer preinstalled with Ubuntu minimizes or nullifies the issue.

3. How big an issue is it? Honestly, it's big in terms of being widespread, but it is not big in terms of urgency. Set up a launcher or keyboard shortcut for gksudo nautilus and be done with it. Many of us (even those who are experienced with Ubuntu) have proposed to the developers to add in an authentication instead of just "you can't do that" when moving files to system folders or trying to edit system files. The developers, up until this point, have said no... maybe not an explicit "no," but waiting six years to... still not implement something... that's a kind of "no."

More details here:
[http://bugzilla.gnome.org/show_bug.cgi?id=65058](http://bugzilla.gnome.org/show_bug.cgi?id=65058)
[https://bugs.launchpad.net/nautilus/+bug/12154](https://bugs.launchpad.net/nautilus/+bug/12154) Once you've set up a limited user account in Windows and administered Windows using *Run as...*, then come and talk to me about how much easier Windows is and how transparent it is. Try, for example, removing a program using *Run as...*.

---

### Post by linfidel on 2007-05-25
> **aysiu said:**
>  ...
In case you missed my earlier points, I'll repeat them again:    Once you've set up a limited user account in Windows and administered Windows using *Run as...*, then come and talk to me about how much easier Windows is and how transparent it is. Try, for example, removing a program using *Run as...*.
I agree with most of that.  Sometimes new things seem strange and inconvenient, but later become beloved features when you get used to them. I've long been aware of the problem with Windows, where you shouldn't run with administrator privileges, but it's so hard not to when it comes time to change something.  It's so much easier with Ubuntu.

I do understand though that it can be frustrating for new users.  Unfortunately, Linux doesn't have the millions of dollars to spend on usability studies, and thousands of programmers that get paid to do something about it.  Unfortunately, there are priorities, and the limited resources are allocated where they are needed the most.  As a GUI programmer, I know that simple changes aren't, and sometimes have far-reaching effects.

But the car comparison isn't really valid.  Someone already put the enging in the body, added all the wheels, etc, and tuned the thing to make it go.  Once you get Linux set up by someone with experience, it's the same way - you click on a program, it runs; you save a file, it goes into the right place.  etc, etc.  My wife could use it just as well as Windows, because she knows very litt
le about either.  She wouldn't know where a file goes, or even where it went.

PS  "aysiu":  The way I do something that doesn't have "runas" is to run IE using runas, switch to folder view, then navigate to control panel, and run the add, remove programs, or whatever.  It gets run as administrator that way.  Much harder than Ubuntu!

---

### Post by aysiu on 2007-05-25
The way I did it was Google for how to do it, found out there are these files buried in C:\WINDOWS\system32 with a .cpl extension. One is called *appwiz.cpl*--that's the Add/Remove (really just *remove* in Windows, for all practical purposes) file to *Run as...*

Good to know there are other methods, though.

By the way, I said it a couple of times before, but I do view *gksudo nautilus* as a workaround (albeit a better workaround than Windows offers... at least as of XP--never used Vista). It's been suggested to Gnome and Ubuntu developers (and I agree with the suggestion) that the authentication happen automatically. I don't know why they haven't implemented the feature yet.

If someone is in the *admin* group and tries to modify a system file or move a file to a system folder, instead of "you don't have permission to do that," an authentication dialogue should come up (just as it does for Synaptic and Users & Groups and GDM setup) saying that you're about to modify a system file, ask you for your password, allow you to cancel (should you wish to do so), but otherwise allow you to modify the file or folder.

Bottom line: Ubuntu's permissions implementation is better than Windows XP, but it is not perfect.

---

### Post by linfidel on 2007-05-26
> **aysiu said:**
> The way I did it was Google for how to do it, found out there are these files buried in C:\WINDOWS\system32 with a .cpl extension. One is called *appwiz.cpl*--that's the Add/Remove (really just *remove* in Windows, for all practical purposes) file to *Run as...*

Good to know there are other methods, though.
Yes, it is. I never think about using the control panel names very often, although I do use them sometimes for shortcuts.

> By the way, I said it a couple of times before, but I do view *gksudo nautilus* as a workaround (albeit a better workaround than Windows offers... at least as of XP--never used Vista). It's been suggested to Gnome and Ubuntu developers (and I agree with the suggestion) that the authentication happen automatically. I don't know why they haven't implemented the feature yet.
What is gksudo, compared to sudo?  I keep seeing that, but haven't had a chance to look it up.

Also, before I post a new question, maybe you know this one:  I keep seeing references to the menu "Applications" -> "System Tools" -> "Configuration editor", but I don't have a "System Tools" menu; is it supposed to be there, or has it changed and the documentation hasn't kept up.  I'd hate to think my menu has gone bad. :)  I was able to run the Configuration editor on a command line, but I'm wondering where it went.

>  Bottom line: Ubuntu's permissions implementation is better than Windows XP, but it is not perfect.
No, nothing is perfect.  It would probably be boring if it were.  :)

---

### Post by aysiu on 2007-05-26
> **linfidel said:**
> 
What is gksudo, compared to sudo?  I keep seeing that, but haven't had a chance to look it up. Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> Also, before I post a new question, maybe you know this one:  I keep seeing references to the menu "Applications" -> "System Tools" -> "Configuration editor", but I don't have a "System Tools" menu; is it supposed to be there, or has it changed and the documentation hasn't kept up.  I'd hate to think my menu has gone bad. :)  I was able to run the Configuration editor on a command line, but I'm wondering where it went. Ubuntu took it off the menu... in Breezy? Dapper? You can still access it using Alt-F2 ```
gconf-editor
```

---

### Post by dnzz on 2007-05-26
Think an OS as an House

Linux has a door at the entrance. If you buy something for your house first you must find your keys, then unlock your door then open it to put your new thing.

Windows has no doors. This means you can skip all the "key and door thing". its easier for use but if someone comes and takes everything in your house  it can be a real disaster.

---

### Post by jondecker76 on 2007-05-26
Also, keep in mind that you don't have to have root priveledges to install/move/copy files into your personal home folder - that is what it is there for.

It sounds to me like the files were trying to be copied into a directory they shouldn't have been put. It does take new linux users a while to get used to that

---

### Post by linfidel on 2007-05-26
> **davlaw2000 said:**
> When you drive a car, you see a familiar set of controls no matter which type of car you drive. I accept that manual and automatic are quite different, but there are really not that many variations. A 'dumb user' can understand quite quickly how to start the engine and drive around. Do they have to know whether the engine has 16 valves or 8? How about whether it has a turbocharger or not? These things have no significant impact on the user interface. 

In a way, Linux is like the manual transmission.  It's basically the same, but you have to know a little more than average.  The average person can't drive a manual transmission and doesn't want to.  Some can a little, but certain situations will bite them, like stopping on a hill.

> **davlaw2000 said:**
> 
Switch over to computers. One OS lets me create folders and copy stuff into them. It even warns me against putting stuff into certain folders as they are a vital part of the OS itself. Cool. Another one seems to stop me, unless I open some wierd command window and type even wierder commands into it. Not cool.   Actually, it's not that weird, and to tell you the truth, it's in the basic documentation for new users.  I know most people don't read documentation, like most people don't read a car owner's manual.  I'm the type that does look through the owner's manual, and likes manual transmissions, and understands how cars work, more or less.  Maybe that's why I don't have unsolvable problems (yes, I do have problems, or, as I like to call them, challenges).  :)

---

### Post by linfidel on 2007-05-26
> **dnzz said:**
> Think an OS as an House

Linux has a door at the entrance. If you buy something for your house first you must find your keys, then unlock your door then open it to put your new thing.

Windows has no doors. This means you can skip all the "key and door thing". its easier for use but if someone comes and takes everything in your house  it can be a real disaster. So, in Windows, you hire a bunch of people to watch your house to make sure nobody gets in, unless of course, they sneak in by pretending to be a friend, or know of a secret back door you forgot about, etc.  

Reminds me of paying protection money to the mob to leave you alone. :)

---

