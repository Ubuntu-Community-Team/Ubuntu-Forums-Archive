---
title: "Re: My Opinion of Ubuntu"
date: 2010-04-05
forum: The Cafe
---

### Post by oldefoxx on 2010-04-05
There is really, really a lot to appreciate and admire about Ubuntu.  People have liked and enjoyed some of the earlier releases so much that they are hard to convence to move to a later version.  But finally they do, and unlike Windows, the switchover can be almost seamless, which is what you want.  You don't usually have that as an option with Windows.

Of course you have to know pretty much what you are doing under Ubuntu, because to do this, you have to use the manual partition mode when installing it, and you do not want to reformat the partition that has your /home folder and everything under it, because that has your user accounts and all your data (pretty much) there together.  You could copy all that off to a backup somewhere and go from that point, so you do have a bit of an option here.

It also means you can pretty much go right for the latest and greatest version of Ubuntu, but I don't necessarily mean go right to the bleading edge.  Like I still prefer version 9.04 over 9.10, and I have played with them both.  I am likely months away from giving version 10.04 and higher a chance, since I want as much stability and finished code as possible.

Yes, Ubuntu is great, but I can't call it perfect.  There are a few odditites in the way it behaves, most particularly a tendency for the screen to stop updating until you took some action with the keyboard or mouse.  Then it would jump ahead to where it should be by the time lapsed, go for awhile, then the screen might freeze again.  Only an irritant under Ubuntu direct, but apparently proving to be much more of a problem when you add VirtualBox and a client like Windows to the equatioons.  This one aspect of all three together is driving my wife crazy, because it is both a distraction and nuisance.  She wants me to get rid of Ubuntu and VirtualBox and leave her just Windows.

For me, that is not a real solution.  Windows 2K and XP are rather old and unattended, except for occasional security patches.  Almost no new features or capabilities, and OEMs eventually quit providing drivers to work with either, so you get a new PC, getting old software to run on it can be a real challenge.  Much more of a challenge than starting first with Ubuntu and VirtualBox. All the new chipsets and other aspects that have been added since their time is the problem. Ubuntu really handles the hardware integration quite well, and VirtualBox provides the fit between the other two.  And that is what I think is absolutely the best.

Without something like Ubuntu and VirtualBox, and when dealing with new PCs, I would have to acknowledge that the problems with trying to get either Win2K of WinXP on that box are nearly insurrmountable, and the problems encountered just could not be resolved in their entirety.  So rather than try, it might make more sence to go with Vista or Windows7 as alternatives.  If you have read my posts elsewhere, you know how much I hate to admit that apparent fact.

I've tried bug reporting, but that is a no-win game in and of itself.  They might try to blame VirtualBox instead of Ubuntu, they might merely indicate that it is the uncertain area between the two, they might tell you to try the very latest version of Ubuntu (like that would automatically include a fix, when the problem has still not been acknowledged yet, and the latest version always involves experimental code that has yet to be fully tested and accepted).  I know there are good developers working to make Ubuntu ever better, but the bugger-clowns that they have screening through bug reports keep the matter out of their hands.

Concerning the last, Windows has always faired worse, but that is the nature of a profit-minded corporation taking over the whole process.  Anyone want to prove that Ubuntu is better, you best start getting it on with the bug reporting.  Don't leave matters stuck out there.  If I can keep getting the hesitant screen problem, even when just running with the LiveCD, then that should be enough to start with.

So here is what bothers me most at present.  I am not opening bug reports, because to me that is a failed process.  I put it here, if you can confirm then that can help, or not confirm and that can mean something too.

Screen stops updating under Ubuntu.  Irritant under Ubuntu itself, more severe in its impact under VirtualBox and guest OS.

Partitioning choices could be broader.  Preserve existing /home accounts could be one option.  overwrite existing installs of Linux or what have you could be another. Preserve Boot.ini boot method instead of a /boot/grub replacement might be worth considering.  Want people comfortable with process to follow, rather than to hope for the best.  Follow with an offer to uninstall and revert if desired if you are not satisfied with the results.

Some choices and details about bringing some versions of Windows under Ubuntu, and easement of the process, could be very influential to anyone that isn't even aware that this might be possible.  Some discussion of efforts to just bring certain applications over instead can also be bought to light.

Keep in mind that in general, Windows owners and users have come to accept that an OS and given applications are just natural elements of a PC, and the whole process of getting them together and putting them on there is therefore unknown to them.  Leaving it for them to go from scratch will mean most of them won't bother, and matters will just stay as they are, with Windows firmly in control and in the lead.

Those that have come to really respect and appreciate Linux, particularly Ubuntu, and have seen the real benefit involved with employing it, would then remain in the small minority.  Maybe that is not so bad someways, but now I have to deal with my wife's anger and frustration with her PC because Ubuntu has this wee little bug that hasn't been identified and resolved

Oh, I didn't mention that when I had to switch from Win2K as the client to XP, I found that XP could not see the shared folders.  But that would be a VirtualBox issue I suppose.  It is so much fun going though, finding some problems, then trying to determine which package or whatever is at the heart of the problem.  I'm just a user of sorts.  How can I know all that stuff?  But they want you to tell them that when you open a bug report.

---

### Post by Sef on 2010-04-06
Moved to its own post.

---

### Post by oldefoxx on 2010-04-06
Sorry for my obviously sour outlook at present. I went at setting up some family PCs with the mix of Ubuntu + VirtualBox + Wib2k + Applications + User Data because it was really teriffic on the first PCs I set up this way, but after a two months struggle trying to do it from backups, I am faced with rejection of the results by my wife and no good recourse as an alternative.  And right now I can name exactly three reasons for her reaction:

Slight lockup involving the screen and maybe other things, which the keyboard and mouse can influence.

Slight lockup by Win2K during boot sometimes, that moving the mouse seems to fix.  Possibly related to the one involving Ubuntu,

Keyboard lockup with the client that has to be cleared by some activity of the mouse, the only one found is to toggle into or out of Full Screen mode,

Inability of Acronis True Image to restore into client virtual drive and have it bootable.  Might be related to personal effort to create partitons on the local C Drive.  Will have to retest this aspect later when more time available.  Win2K cannot be reinstalled in this state.  Can install WinXP in place of 2K, but neither 2K nor XP adequately links to existing Registry or User Accounts.  Lots of left behind unresolved issues as result.

Extremely long backup and restore intervals required for client, like only about 1/10th normal rate.  Nultitasking at a high rate with two OSes and busy application could be reason.

WinXP failed to do anything to access shared folders provided through VirtualBox.  Win2K was good at this.  No idea why the difference.  WinXP also recognized smart card devices, which should not have happened until VirtualBox is instructed to pass them to client.  Did not see this with Win2K. Effects Windows perception of drive designations.

Why talk about VirtualBox here?  Because in my many efforts, it is tied to Ubuntu, and their bonding is so close that I am encouraged to think that this is what the future might be.  I mean you can hardly believe how well that they pull together and how well Windows can function as a client in in such an environment.  So if they just get down on the few drawbacks that still remain, and it could really be just about everything you could want or expect.

And while I have several quibbles with VirtualBox, I am really down to just that one with Ubuntu:  Why it ceases to update the screen and why it seems to lock out the mouse and keyboard when leaving these idle for a time under VirtualBox and the client.

Oh, another glitch at times under FireFox, mostly when running it under Windows and maybe on forums like this one.  A sudden tendancy for the screen to suddenly leap up or down in the display area, possibly as a result of an automatic save action.  To get back to the right place, you press a key on the keyboard, and where you were entering text jumps or falls back into view, but it might suddenly jerk out of view again.  Only happens every once in awhile, but it is not funny and somewhat unsettling.   

That is pretty much a summary of what seems wrong, and the best I can guess or tell about where the problem might lie.  What else can I say?

---

### Post by oldefoxx on 2010-04-13
Let's say you wnat to put a second, or possibly a third install of Linux on your PC.  Maybe several versions of Ubuntu.  Nor what appears to happen is that some overlap in partition designation may occur, though you do not specify or want this.  So one install nay intrude on another in some way, such as maybe a sharing of /home or whatever.  I mean I can't prove that it happens, but it could explain some odd things that happened several times when I did multiple installs.

The trick might be to mask off a prior install so that the next one does not see it.  But you can't do this when running the privious install, because renaming or moving a critical folder or file could be bad news right then and here.  But there is that in-between phase, the use of the LiveCD mode in preperation of another install.  Interesting idea, right?

Well, there is no harm with a quick look-see.  I'm going to grab a Ubuntu 9.04 disk (it doesn't have to br 9.04) and use it as a LiveCD.  Then I will come back here and see what I can find out from the LiveCD that might have a bearing on this matter.  So 'bye for a few minutes, and I should be back.  Then we will see where we can go once there.

Aw, forget it.  I'm back on the LiveCD, I went through the whole process of dealing with the matter, had it written up with suitable Terminal commands in place, had really explained what it entailed and why, then when I tried to file my modified post, this stinky forum threw it out because I had been logged in too long or something.  Everything I had added to this post was just blown, with no chance of recovery.  I now know something that most of you don't know, but this crappy setup took it away before I could file it, and so I am fed up.  Time for a shower anyway.

If this were the first time, or even the first incident today, it would not rank so bad.  But I did well on a couple of other threads, only to have someone decide to either move it or close it.  One was closed today, and obviously it was being put to some decider-uppers as to whether to leave in on the forums at all.  You aren't my bosses, and you don't tell me what to write, or when to stop.

---

