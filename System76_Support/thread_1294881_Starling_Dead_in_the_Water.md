---
title: "Starling Dead in the Water"
date: 2009-10-18
forum: System76 Support
---

### Post by Eyore15 on 2009-10-18
HELP!

Last Friday I was using my Starling in classic mode when the battery died.  My fault; I wasn't watching the panel indicator.  The power cord was at work and I couldn't pick it up until today.

Once I had the power cord, I put the computer on house power and booted. It boots to classic view. All I get is the classic background WITHOUT the top panel.

It appears everything "under the hood" is working.  I created a blank directory so I could right click and get to the "open with" dialogue.  Once there I specified "Firefox", which attempted to open the directory.Once Firefox was open, I selected a site from the bookmarks panel.  It opened, so I know the wireless network is working.

What I need to do now is get the top panel back, so I can go back to UNR view. Once there, I can implement the command (gconftool-2 --recursive-unset /apps/panel) Mr. Aaron provided to solve a problem with the UNR not showing a top panel.  Since I have no top panel in classic view, I can't get a terminal -- at least I don't know how to get a terminal.

I tried booting with the (recovery mode) and "repair packages"; neither of them had any effect on the problem.

To summarize:

I need to get a top panel in classic view, or at a minimum get the left side of the panel (with preferences) back so I can switch to UNR.  Then I can open a terminal to run a command to fix a problem with the top panel in UNR

thanks for your help.  I'm really frustrated at the moment.  

If you have a starling and are considering changing to "classic" view --DON'T.

tia

MCM

---

### Post by macabrem on 2009-10-19
I had this problem a few times.  In two separate accounts I made, I lost all panels (I had 2 panels in each account).  I didn't know of a way to fix it, so I just deleted the account and recreated it.  (which wouldn't have been a good solution if I had anything important in the accounts). 

And my other accounts run fine with no panel problems, for some reason.  I always run in classic and not the Netbook Remix.  (My remix runs super slow and seems like it will lock up my Starling at anytime, but that is a subject I haven't tried to fix yet)

So, that above command that Mr. Aaron provided gets the panel back?

I believe you can launch a terminal by hitting ctrl+alt+f1 and/or ctrl+alt+f2

---

### Post by Eyore15 on 2009-10-19
> **macabrem said:**
> I had this problem a few times.  In two separate accounts I made, I lost all panels (I had 2 panels in each account).  I didn't know of a way to fix it, so I just deleted the account and recreated it.  (which wouldn't have been a good solution if I had anything important in the accounts). 

And my other accounts run fine with no panel problems, for some reason.  I always run in classic and not the Netbook Remix.  (My remix runs super slow and seems like it will lock up my Starling at anytime, but that is a subject I haven't tried to fix yet)

So, that above command that Mr. Aaron provided gets the panel back?

I believe you can launch a terminal by hitting ctrl+alt+f1 and/or ctrl+alt+f2

I used the options menu to get select a session and opened  a "failsafe" terminal and entered the command from Mr.  Aaron ((gconftool-2 --recursive-unset /apps/panel)) sent;  it had no effect.

I was able to use the hint on getting a standard terminal and hoped to enter the command from there to see if it made any difference, but that poses a new problem as well. Once in the standard terminal, my keyboard isn't functioning properly; for example o (oh) is rendered as "^[[C" (there are other examples as well if that would help diagnose the problem) and since my login is "eyore", I can't get logged in.    The standard Utuntu login works OK as did the failsafe terminal , but I get the weird characters once I get into the standard terminal using "cntrl+alt+f1"

So now I have two problems:

     the original problem of no panel and stuck in classic view (and apparently the gconf-2 command having no effect on that problem) 

     the added problem of the weird response from the keyboard in standard terminal mode

I stand by for any help that will dig me out of this hole I've dug myself.

Is there perhaps a way to allow a remote desktop that would allow someone to enter to resolve this?  I can put the starling on my wired network and get you an ip address.

Or

is there a way to simply reset to factory values?  I've got nothing on the computer that isn't backed up somewhere else.

mcm

---

### Post by macabrem on 2009-10-19
> **Eyore15 said:**
> Once in the terminal, my keyboard isn't functioning properly; for example o (oh) is rendered as "[C" and since my login is "eyore", I can't get logged in.  I did try and use the otions menu to get a "safe" terminal and enter the command from Mr.  Aaron; perhaps you have to enter it from within UNR because it had no effect on the classic view.

mcm


I'm trying to figure out why the O displays as [C...  

Have you played with the keyboard to see if the keyboard setting is just messed up - like it got switched to another layout?  Like maybe you can type other keys to come out with Eyore?  I know that may be a long shot...

---

### Post by thomasaaron on 2009-10-19
This may be related to this bug with the desktop switcher...
[https://bugs.edge.launchpad.net/desk...er/+bug/349519](https://bugs.edge.launchpad.net/desk...er/+bug/349519)

Please run this command...
gconftool-2 --recursive-unset /apps/panel
...and then reboot.

Did that fix it?

---

### Post by Eyore15 on 2009-10-19
> **thomasaaron said:**
> This may be related to this bug with the desktop switcher...
[https://bugs.edge.launchpad.net/desk...er/+bug/349519](https://bugs.edge.launchpad.net/desk...er/+bug/349519)

Please run this command...
gconftool-2 --recursive-unset /apps/panel
...and then reboot.

Did that fix it?

nope

still no panel.

---

### Post by Eyore15 on 2009-10-19
I gave up, downloaded UNR and am reformatting now with a new install.

I'll figure out the download of the system 76 driver, and that should be that.  Any more problems and I will open a new thread.

WARNING:  there appears to be a known bug in the desktop switcher that effects the Starling.  Switch desktops at your own risk.

mcm

---

### Post by HotShotDJ on 2009-10-19
> **Eyore15 said:**
> WARNING:  there appears to be a known bug in the desktop switcher that effects the Starling.  Switch desktops at your own risk.Just so you know, it effects other netbooks as well.  This bug bit me over the weekend with a friend's eeePC-900.  I didn't do a reinstall, I just deleted the ~/.gconf and then logged out and back in.  I probably didn't even need to delete the entire directory, but it restored the desktop to the default UNR.

---

