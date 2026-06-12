---
title: "Skype... Now with tabs"
date: 2010-12-12
forum: The Cafe
---

### Post by keksn on 2010-12-12
I think a lot of people want to have tabs in Skype. Tired of waiting till the moment when they find time for them I've read libX11 manuals and using some kind of black magic reached some success with it.

[[IMG]http://imm.io/media/2t/2tyJ.png[/IMG]]("http://lh6.ggpht.com/_1_TkZrguBPE/TQKskzX4QBI/AAAAAAAAAjU/o9T5UWGcOGE/file4ha4aP.png")

[Short demonstration]("http://www.youtube.com/watch?v=mZ_NvXhGEu0")

[PPA]("http://launchpad.net/~keks9n/+archive/skypetab")

[Source code]("http://github.com/kekekeks/skypetab-ng)

Note: If you are building from source you need also have wmctrl utility installed to have it working.

P. S. Sorry for my ugly English, I'm not a native speaker.

---

### Post by Spice Weasel on 2010-12-12
RPM please? :) My friend has been bugging me about this for ages.

---

### Post by Tibuda on 2010-12-12
> **keksn said:**
> Unfortunately cann't release the source now because of some code, that cann't be released under GPL...

GPL is not the only license out there.

---

### Post by fatality_uk on 2010-12-12
No offence, but until I can see/compile the source or can install from a trusted source, my online conversations will have to remain untabbed.

---

### Post by keksn on 2010-12-12
OK, I'll try to remove "proprietary" code faster. It's 20:35 here, so, I have time till the midnight.

---

### Post by keksn on 2010-12-12
[http://sourceforge.net/projects/skypetab/files/skypetab.tar.gz/download](http://sourceforge.net/projects/skypetab/files/skypetab.tar.gz/download) - you can get it here.

---

### Post by nilarimogard on 2010-12-12
The Skype conversation windows lag a lot behind the tabs wrapper when moving the window... can this be fixed?

---

### Post by keksn on 2010-12-12
Not at this time, because I cann't embed them in the wrapper :-? (actually I can, but it breaks keyboard input and makes the program useless). But I'm thinking, how to do it.

---

### Post by keksn on 2010-12-13
Package updated: new method of notification about unread messages added.

---

### Post by treesurf on 2010-12-21
Thanks. Although it's a bit rough, this really helps to unclutter things when I've got more than one chat going.

---

### Post by olof_ on 2010-12-26
I agree with treesurf, but I have a little issue which makes using your program a bit nervous in the long run. The tabs and the settings opens up fine and such. But when I have one (or several) chat tabs open, the window list which belongs to the Skype chat window starts to flash constantly. It flashes with an interval of maybe 0.1 seconds and this flashing continues on every program in the whole window list. It flashes in a white colour, which covers the whole "indicator" for the previous mentioned short interval. edit: forgot to mention that the flashing only occurs when opening the new chat window.
Specs:
Ubuntu 10.10, skype 2.1.0.81.
Maybe matters, I am using xinerama with a quad-monitor setup. fglrx 10.12.

edit: I tried to reproduce the issue, and now it's only the skype chat window list which is affected...

---

### Post by maddbaron on 2010-12-26
i have a question, once u open skype and start chatting with someone how do u show your camera or see theirs? there is no view/show button or anything...

---

### Post by gaz514 on 2011-05-18
I just tried this out. Great idea and well needed, although it's still a bit buggy so I'm not keen to start using it full-time yet:
- Issue olof_ mentioned with flashing in the window list
- If you close a tab, it's impossible to open another conversation with that person.
- A tab closed itself randomly at the same time as I closed a completely unrelated window (a Thunar window). Not sure if this was coincidence.

Edit: another solution is using Pidgin's Skype plugin, which also provides other nice features like logging conversations and group chats in plain text in a sensible hierarchy, although it has its limitations: doesn't support file transfer so you need to go back to Skype to do that, and Pidgin's always been buggy as hell so the comfort factor isn't any higher.

---

### Post by beew on 2011-05-18
> **gaz514 said:**
> I just tried this out. Great idea and well needed, although it's still a bit buggy so I'm not keen to start using it full-time yet:
- Issue olof_ mentioned with flashing in the window list
- If you close a tab, it's impossible to open another conversation with that person.
- A tab closed itself randomly at the same time as I closed a completely unrelated window (a Thunar window). Not sure if this was coincidence.

Edit: another solution is using Pidgin's Skype plugin, which also provides other nice features like logging conversations and group chats in plain text in a sensible hierarchy, although it has its limitations: doesn't support file transfer so you need to go back to Skype to do that, and Pidgin's always been buggy as hell so the comfort factor isn't any higher.

Why waste your time? Skype will probably be dead for Linux in a year or so.

---

### Post by BrokenKingpin on 2011-05-18
> **beew said:**
> Why waste your time? Skype will probably be dead for Linux in a year or so.
Just because MS owns it now does not mean they are just going to drop Linux support. The work has already been done to make it cross platform, so it is in their best interest to have it available on as many platforms as possible.

---

### Post by beew on 2011-05-18
> **BrokenKingpin said:**
> Just because MS owns it now does not mean they are just going to drop Linux support. The work has already been done to make it cross platform, so it is in their best interest to have it available on as many platforms as possible.

I hope you are right, but what does "cross platform" mean for MS? I am not sure if it would be in their best interest to support Linux and of course "best interest" is not based on your or my judgment.

In any case, it is better to have alternatives just in case (and it is not a remote scenario). Why put all your eggs in someone else's basket?

---

### Post by Dustin2128 on 2011-05-18
> **BrokenKingpin said:**
> Just because MS owns it now does not mean they are just going to drop Linux support. The work has already been done to make it cross platform, so it is in their best interest to have it available on as many platforms as possible.
Since when has MS been good at figuring out what was in their best interest?

---

### Post by Quadunit404 on 2011-05-18
Ya know, I find the whole "Micro$oft hates Linux and would never support it!" funny because a few years back they contributed 20000 lines of code to the kernel, they support Linux guests in their virtualization products and more recently, they [started supporting CentOS.]("http://www.theregister.co.uk/2011/05/17/microsoft_and_centos/")

So... what were you guys saying about Microsoft not supporting Linux? :wink:

PS: By MS, do you mean Mark Shuttleworth, Mississippi or Microsoft? Because all three of those can be abbreviated as MS :wink: :lol:

---

### Post by olof_ on 2011-06-26
Tried it now, and I must say that the project really have matured!
None of the above mentioned bugs persist and it just works. great job!

(see [http://code.google.com/p/skypetab/issues/detail?id=5]("http://code.google.com/p/skypetab/issues/detail?id=5") for a slight design suggestion of mine.)

---

### Post by Gaygerbil on 2011-09-16
This doesn't work for me, I open it and it flashes some windows and does nothing.

I tried opening it with the terminal and this is my output:


```
bewbman@bewbman-desktop:~$ skypetab

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for X11.X ---> System.DllNotFoundException: libX11.so
  at (wrapper managed-to-native) X11.X:XOpenDisplay (intptr)
  at X11.X..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at SkypeTab.Globals.Main (System.String[] args) [0x00000] in <filename unknown>:0 
bewbman@bewbman-desktop:~$ X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x2e00003
  Serial number of failed request:  90
  Current serial number in output stream:  90

```

---

### Post by ki4jgt on 2011-11-28
Is there an update for this?

---

### Post by keksn on 2011-12-17
Yes, there is. It's just moved to  [PPA]("http://launchpad.net/~keks9n/+archive/skypetab") and the package is now called "skypetab-ng".

---

