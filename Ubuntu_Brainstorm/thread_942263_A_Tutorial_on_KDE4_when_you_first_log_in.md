---
title: "A Tutorial on KDE4 when you first log in"
date: 2008-10-09
forum: Ubuntu Brainstorm
---

### Post by skullmunky on 2008-10-09
Tell me if this sounds familiar - new user running KDE4 for the first time:

"What the - why can't I make icons on the desktop?!!??!!  "

*bam* out the window it goes.

That was me, too.  For about 6 months I figured that KDE4 was still early in its life cycle and was just buggy, and eventually that would get fixed.

Then one day I read about the folder view widget, which is brilliant, and I love it.  One of the best innovations with the desktop idea in ages.  But why should you have to get angry first before knowing about it?

Back in the day, computers used to come with a manual.  In the early days of GUI's, they'd come with a manual and tutorials on how to use this funny thing called a "mouse" so you could learn about what clicking and double-clicking were, how to drag things, etc.  After a while lots of people got familiar with the general idea, and now you don't get a manual of any kind anymore.  It's the age of the transparent, intuitive interface.

But we forget that it's only intuitive because we've learned it.  Change it around, sometimes even a little, and the whole rug gets pulled out.  Two more personal recent examples, so you don't think I'm just beating up on KDE:

- I just tried out Squeak today, which is of course amazing, weird, a window into the absolute origin of the GUI, and creates a sense of strangeness and unfamiliarity that's really a kick

- the iPhone.  New interface paradigm, no documentation, extremely baffling and frustrating device until you've jabbed at it for a long time.  

(it's nothing like the sexy zen trip you see in the commercials -it's more like having a good ol' 14.4 modem.  Except now you can experience that leisurely load time while trying frantically to get directions from it at 60mph on the BQE.)

Ok, back to Kubuntu - what about a little interactive tutorial explaining how KDE4 works that you can go through when you first log in?  

On a related note: 

If you have an account where you used Gnome or KDE3, and so you've got a Desktop folder with stuff in it, and then you go into KDE4:

It should perhaps have a folder view plasmoid by default for the Desktop folder.  But it should not create launcher icons for all the files and folders in your Desktop folder, because those launchers are NOT the same as files and folders so it gets really confusing; and because if you had a fair amount of stuff on your desktop, now, with the cool launcher-icon-toolbuttons surrounding everything, nearly every pixel becomes active and you get this crazy mess of fading in and fading out icons.

---

### Post by GeneralZod on 2008-10-09
To be honest, if a user is impatient enough to throw out a piece of software after a few minutes use, they're unlikely to sit through a tutorial :)

KDE trunk (which will be 4.2 soon) has a GUI option that offers a "traditional" desktop i.e. a file view onto ~/Desktop or some custom folder.  It will be interesting to see how many distros make this the default behaviour.

---

### Post by skullmunky on 2008-10-10
> **GeneralZod said:**
> To be honest, if a user is impatient enough to throw out a piece of software after a few minutes use, they're unlikely to sit through a tutorial :)

KDE trunk (which will be 4.2 soon) has a GUI option that offers a "traditional" desktop i.e. a file view onto ~/Desktop or some custom folder.  It will be interesting to see how many distros make this the default behaviour.

I don't know, I think some actually would make use of it.  I see this approach used all the time with other complex, unfamiliar software, like design and animation tools.  The other options for a new user are:

1. read the manual ( *snicker* )
2. click on things and try to figure out how it works by trial and error
3. ask someone else for help on the forums

Me, I've always been proudly in the #2 camp.  That's why it took me something like 3 months to find the folder view widget.  This works if the software has a high level of discoverability - but it also depends on initial assumptions.  If the new software has enough discontinuities with your previous knowledge, new learning is a lot harder.

I think this is about more than just the desktop and file view question.  Actually I really do think the folder view widget approach is brilliant and is a major step forward for Desktops, and it'd be a shame to disable it just because it's unfamiliar.  

Another anecdote of what I'm talking about, from the "Apple Thinks They're So Easy To Use" department.  These are some folks who have a new, shiny iMac, after decades with Windows. 

1. "we finally figured out where to put a CD into it.  But we can't figure out how to get it out, so there's a CD permanently stuck in there."
2. "yes, it's really fun, we never know what it's going to do.  we just click on these little pictures on the bottom of the screen but we have no idea what they're doing.  it's a real adventure."
3. "no, we still have the old compaq laptop, to do word processing.  whenever I save a file on the iMac I never can find it again."
4. " *** sent me all these pictures in an email, and I downloaded them, but I can't figure out where they went"
5. user's attempts to use the Spotlight search thingy produce a window with every single file on the hard drive, including everything in the secret hidden BSD directories.
6. "I thought I deleted all these - why did they come back?!  What are all these files?  Those aren't supposed to be here."
7.  "How do you delete files?"
8. User starts indiscriminately dragging clumps of files to the Trash in a desperate attempt to fight what looks like a massive infestation of downloaded crud (remember, former Windows user ;).  Oops, no, that's most of the operating system there in the Trash now.
9. User retreats for the time being to safety and comfort of Win98 laptop.
10. "Yes, we heard it had a camera on it.  We weren't sure if that meant people could watch us remotely so I was real clever and put a sticky note over the camera to block it, just to be on the safe side."

11. User is surprised and frightened to discover iChat video works and camera can magically see through sticky note, as if with X-ray vision.  Solution: sticky note was pasted over the Apple logo below the screen, not in fact over the camera.

Well, hopefully that was entertaining :)  I'll shut up and start making a tutorial for new KDE4 users.  Except I have to figure out how to use KDE4 first ... hmm, where did I put that manual ...

---

### Post by jacksaff on 2008-10-12
I'm sure this will get done eventually (and by the kde people, not  ubuntu).
At the moment kde4 is changing too fast to write a sensible tutorial, at least for the plasma desktop. Who knows what widgets will be the default in a few months time? They  probably haven't even been written yet! Even the apis got changed between 4.0 and 4.1 as it became clearer what the platform was capable of and how to make that easier for programmers to get at.

---

### Post by crisspybeers on 2008-10-16
> **GeneralZod said:**
> To be honest, if a user is impatient enough to throw out a piece of software after a few minutes use, they're unlikely to sit through a tutorial :)

KDE trunk (which will be 4.2 soon) has a GUI option that offers a "traditional" desktop i.e. a file view onto ~/Desktop or some custom folder.  It will be interesting to see how many distros make this the default behaviour.


There we go again throwing blanket statements around about new or even experienced Linux users.  Yeah, some people will not have the patience.  However, the forums are full of posts from people, both noobs and experienced users, asking about "missing functionality" or where things have moved to.  If you don't need it, just click the "Go Away" button, but if you do then you don't have to go searching for the answers.  Honestly, I feel most people just don't have the time to try to dig some of this stuff up.  You want people to use your cool desktop, how about helping them up front and not declaring them incompetent or lazy because they would like a little helping hand.  I thought the object was to bring in the masses, not be elitists.

---

### Post by rcdawson on 2008-10-25
KDE 4 has certainly frustrated me!  It may still be changing, but if it is defined enough to release...

We have several brand new concepts.  Plasmoids?  Activities?  Folder Views. 

And how do you remove links (or widgets or whatever they are) from the panel?  How do you install one for a particular program?

Is there somewhere to find some discussion of these things; what they are and how they are to be used?

---

### Post by LuisAugusto on 2008-10-26
> **rcdawson said:**
> KDE 4 has certainly frustrated me!  It may still be changing, but if it is defined enough to release...

We have several brand new concepts.  Plasmoids?  Activities?  Folder Views. 

Plasmoids= Are more or less Gadgets, widgets, etc.

> **rcdawson said:**
> And how do you remove links (or widgets or whatever they are) from the panel?  How do you install one for a particular program?

Ahem, you just right click on the panel, panel configuration, and you can add or remove as many plasmoids as you want. To install new plasmoids, you just select get more plasmoids, it isn't hard XD.

---

### Post by panda726 on 2008-10-26
One thing I noted in my brief time working with Kubuntu Intrepid (I still need to upgrade my grub partition grub in order to boot Intrepid, unless there is something strange going on), I found panels (is it still kicker, or do I need to install kicker, or should I just play with it when I can?) don't work neatly in the configuration I use.

What I like is one on the side of my screen for a taskbar, on which I have horizontal buttons for each window, and a panel on the top of my screen that is full width for all my notifications and other buttons, to keep them from turning into monstrous ugly things.

KDE 3.5 kicker recognizes two panels overlapping and runs on full width and ends the other where it meets the first.

When I create the two panels on the Live CD, I get one panel overlapping the other, with the last clicked on panel on top.  Very ugly and difficult to use.

A tutorial might help, but I am one who detested the XP start menu, and was just as happy with the classic look.  I also am more in the "#2" camp, ssooo... perhaps an easily browseable FAQ would be more to the point.

Tor

---

