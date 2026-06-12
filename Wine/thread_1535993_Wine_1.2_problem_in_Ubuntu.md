---
title: "Wine 1.2 problem in Ubuntu?"
date: 2010-07-21
forum: Wine
---

### Post by Ub28 on 2010-07-21
I'm getting a problem that nobody on the winehq website can reproduce.  Here's the problem: [http://bugs.winehq.org/show_bug.cgi?id=23670](http://bugs.winehq.org/show_bug.cgi?id=23670)

Nobody else there can reproduce it.  Do I have a bad install of Wine version 1.2 and can it be "fixed"?  Why does Ubuntu install things like "wisotool" and "winetricks" with Wine 1.2 - are these extras causing the problem?

---

### Post by cogadh on 2010-07-21
None of that "extra stuff" can cause a problem like this, they don't actually interact directly with Wine unless you specifically use them. For example, winetricks is a script you can run that will install certain Microsoft components in your .wine directory if you need them, but if you've never run winetricks, it doesn't do anything. All of the "extras" that are installed with the Wine 1.2 package are like that and are only there because nearly everyone will probably find a need for them at some point in their Wine adventure.

As for your specific problem, we need some more details, like Wine's terminal output and some hardware specs.

---

### Post by Ub28 on 2010-07-21
> **cogadh said:**
> As for your specific problem, we need some more details, like Wine's terminal output and some hardware specs.

Thanks for your reply.  Wine doesn't show a terminal.

Hardware specs, I can give you the following if it's helpful:
RAM 2GB 
CPU 2.80GHZ dual core Intel Pentium D
NVIDIA GeForce 7300 SE/7200 GS
Ubuntu 10.04 64-bit.

I could found all these hardware specs in the System > Administration in Ubuntu.

---

### Post by cogadh on 2010-07-21
Wine does show a terminal... if you use it from the terminal. Open up a terminal , change directories to the game's install directory, then "wine" the executable:
```

cd <path to game>
wine BALISTIC.EXE
```
Wine's error output will appear in the terminal; copy and paste it here, with any luck it will have a specific error that explains what is happening.

---

### Post by Ub28 on 2010-07-21
I've done what you said and opened the game in Wine using the terminal, but not got any errors.  I don't know why the colours in the game are wrong?  I've tried downloading the game again, I've tried re-installing Wine - I can't solve this problem!! :(

I appreciate your help - I really do. :)

---

### Post by cogadh on 2010-07-21
No errors is impossible, Wine always produces at least basic debug messages.

---

### Post by Ub28 on 2010-07-21
> **cogadh said:**
> No errors is impossible, Wine always produces at least basic debug messages.

Not getting anything.  No errors.

I've added an attachment to the Wine bug report showing what the game is supposed to look like when run in Windows XP (32-bit).

[http://bugs.winehq.org/show_bug.cgi?id=23670](http://bugs.winehq.org/show_bug.cgi?id=23670)

Unsolvable mystery??

---

### Post by cogadh on 2010-07-21
The fact that you are getting absolutely no output from Wine, which as I said is impossible, would seem to indicate that there is something wrong with your Wine installation. I'd suggest you do a complete uninstall and purge of Wine, including deleting the .wine directory from your home directory, then start over with a completely clean install.

---

### Post by Ub28 on 2010-07-21
I've tried running other programs in the terminal and I do sometimes get lines of text I don't understand.  It doesn't seem to do that for this game (Ballistic) and let's not forget that it's an ancient 16-bit game.

I've done a clean install, deleted the .wine folder from my Home folder, but the problem is still there after a completely clean install.

I don't know what to do now. :(

---

### Post by hikaricore on 2010-07-21
> **Ub28 said:**
> I've tried running other programs in the terminal and I do sometimes get lines of text I don't understand.  It doesn't seem to do that for this game (Ballistic) and let's not forget that it's an ancient 16-bit game.

1. Those are debug/error output and indicate wine is atleast trying to work.
2. This 16 bit game, are you sure it's for windows and not dos?  If it's for dos you will need to use dosbox or dosemu or something to run it, wine supports cli doslike programs that were ment to run from windows but not actual dos itself.

---

### Post by soldier1st on 2010-07-22
did you change any of the graphic settings in wine? also under wine/configure/application settings did you add the game and set it to XP?with wine if things don't work you need to fiddle with it to see if you can get the app to work.

---

### Post by asdfoo on 2010-07-22
> **hikaricore said:**
> 1. Those are debug/error output and indicate wine is atleast trying to work.
2. This 16 bit game, are you sure it's for windows and not dos?  If it's for dos you will need to use dosbox or dosemu or something to run it, wine supports cli doslike programs that were ment to run from windows but not actual dos itself.

It works for atleast one other person in the linked bug report, which I read and the answer is conclusive: the OP needs to run a regression test to pinpoint the cause of the bug.

All else is a waste of time since it will give a straight answer.

---

### Post by Ub28 on 2010-07-22
It is a Windows 3.1 game, NOT a DOS game.

I've tried your suggestions, but it's still displaying the colours wrongly in the game.  When I had Wine version 1.1.42 installed, the game worked fine.

I can't work this out.  Am I just unlucky??

---

### Post by cogadh on 2010-07-22
asdfoo is right. At this point, you need to run the regression test, since it appears that no one else can replicate your problem.

---

### Post by russcelt on 2010-10-28
Just installed Wine 1.2 update with Update Manager. Now Wine programs won't launch, Wine Config nothing, Wine Uninstall nothing happens.

Any ideas?

---

