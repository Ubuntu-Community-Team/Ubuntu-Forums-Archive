---
title: "Dual Display Misery - Not for Non-Geeks"
date: 2006-10-20
forum: The Cafe
---

### Post by justinchudgar on 2006-10-20
I just added a 2nd video card to my Ubuntu box so I could use a spare monitor as a 2nd display. Coming from the Windows world, I expected that this would be a matter of shutting down the PC, installing the new card, booting up and tweaking the resolution and placement.

Doh! ](*,) 

I spent the better part of an evening doing the **nano /etc/X11/xorg.conf**, **killall gdm**, **gdm** routine while running to my wife's PC to google man pages and how-to's.

I now have a poorly performing dual monitor setup, without the conveniences that Windows drivers provide. I know that Ubuntu cannot fix binary drivers; but, I really should not have to learn how to read the output of **lspci** to add a simple video card to my PC.

I believe that if ubuntu is to be truly non-geek user friendly, no user with reasonably standard hardware and configuration preferences should ever have to use a text editor to accomplish any system configuration tasks. That the .conf files are there for sysadmins and geeks to use is great; but, linux is not ready for primetime if knowing that your video card is at **PCI:2:2:0** or that save in nano is **<ctrl-o>** not **<ctrl-s>** is essential to get your display working.

Tools like [xorg-edit]("http://www.cyskat.de/dee/progxorg.htm") are a step in the right direction; but, as it exists now, it is just as non-intuitive as the xorg.conf file, but prettier. To be useful, the dialogs must be pre-populated with legal options; and, there must be tooltips or other immediate and detailed help text for each option. 

Google should be unnecessary for all but the most difficult situations. As it stands now, for anyone who has not been through the process several times before, googling for forum posts, man pages and the like is absolutely essential.

There are some really, really wonderful things about ubuntu; like being able to directly help the developers by providing debug information for crashes and being able to **apt-get install** just about anything. 

These things make me committed to continuing with ubuntu; but, the fact that someone (me) who started life in the IT field with NetWare 3.x and 4.x's command line interface has to spend hours accomplishing a task that a complete novice can manage in Windows in minutes shows a real need for focus. To a non-technical end user, development time on core system components like upstart vs sysvinit are meaningless. If they are unable to accomplish tasks with relatively similar effort that they could accomplish with Windows, they lose patience and interest.

I am a stubborn geek; so, being able to make my **xorg.conf** work or being able to get **flowscan, cuflow, and cacti** working is a challenge and a reward in itself. For most, it is hell.

Please focus on taking all the knowledge that is scattered around this and other forums and working it into *hand-holding* tools to make the life of the inexperienced much less difficult.

And, if any of you have any insight into how to learn GUI development so I can put my advice into practice, please let me know. I've got limited familiarity with half a dozen languages; but, I've never learned graphical interface programming. I've messed around with *GUI designer IDEs*, but, without a fundamental knowledge of GUI programming, they are little help.

Thanks,

Justin

---

### Post by maniacmusician on 2006-10-20
I don't know about programming QT (it seems hard), but for gnome apps you could probably use Glade GTK+ interface designer (or something like that. I'm sure it's in the repos). I've seen people produce pretty decent interfaces with it.

---

### Post by ~LoKe on 2006-10-20
I couldn't imagine anyone who's not a geek needing/wanting a second monitor. ;)

But regardless...my monitors just came in yesterday and I had them up and running pretty quickly.  All I needed to do was add a few TwinView lines and some resolution tweaks and it's good to go

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "TwinView"                 "true"
    Option         "RenderAccel"              "true"
    Option         "UseEdidFreqs"             "true"
    Option         "MetaModes" "1280x1024,1280x1024;1024x768,NULL;800x600,800x600;640x480,640x480"
EndSection
```
...
```
    SubSection     "Display"
	Viewport	0 0
        Depth       24
        Modes      "2560x1024" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
```

---

### Post by .t. on 2006-10-20
Well, the Xorg folks are in the middle of designing a new replacement to the twenty year old flat file. Hopefully, by using this, X config will be a google times easier.

---

### Post by zachtib on 2006-10-20
> **justinchudgar said:**
> And, if any of you have any insight into how to learn GUI development so I can put my advice into practice, please let me know. I've got limited familiarity with half a dozen languages; but, I've never learned graphical interface programming. I've messed around with *GUI designer IDEs*, but, without a fundamental knowledge of GUI programming, they are little help.

Look into using Glade, PyGTK and Python.  It's easy to pick up and you can make pretty good applications with it.

linky: [http://www.learningpython.com/](http://www.learningpython.com/) << some good examples

---

### Post by DC@DR on 2006-10-20
Yes, we all do know that Linux is not as well at hardware-support as Windoze, but what can we do, since Linux world is open-source/free world, it's different with billions-dollar-Windows-world, how could we ask for any hardware working _out_of_the_box, hot plug-and-play just by put in a driver installation CD, since the hardware vendors keep rejecting releasing documents/codes that FOSS/Linux developers can find useful things to develop the right drivers.... I really appreciate what FOSS/Linux developers have gone so far to support "closed-source" hardwares as good as it is now....Ofcourse there's still a long way to go for FOSS/Linux, but I think if any user who is not patient enough, not ready to play with command line, not willing to learn reading .conf files, can not find the fun how to get things done manually by configuring stuffs, I suggest that user should stick with Windows world, keep on paying license fees to M$....Just my 2 cents, no offense at any1 at all :)

---

### Post by justinchudgar on 2006-10-25
> **~LoKe said:**
> I couldn't imagine anyone who's not a geek needing/wanting a second monitor. ;)

I've got a graphic designer wife, several accountants, lawyers, etc. that I serve that use multiple monitors. None of them could tell you what kind of GPU they have, even those with ATI or nVidia stickers on the front of their PCs. Of course, they all use windows so this is not difficult.

Even my 74 year old neighbor got a 2nd monitor so that he could keep an eye on the poker tables while doing other stuff.

---

### Post by justinchudgar on 2006-10-25
> **zachtib said:**
> Look into using Glade, PyGTK and Python.  It's easy to pick up and you can make pretty good applications with it.

linky: [http://www.learningpython.com/](http://www.learningpython.com/) << some good examples

Thanks. I'm messing with a silly little prime generation app for practice.

---

### Post by jdehaan on 2006-11-23
I agree with Justin 100%.  I must have two monitors and if Linux wont do it in ten minutes, then I'll stick with XP.

---

### Post by mcduck on 2006-11-23
I have no problem with editing text files by hand. At least it's much better than editing binary registry files in windows...

But I only needed to run one command ('aticonfig --dtop=horizontal') to get dual screen working with my laptops Ati card..That was even easier than with the horrible GUI they have in Windows for the task.

---

