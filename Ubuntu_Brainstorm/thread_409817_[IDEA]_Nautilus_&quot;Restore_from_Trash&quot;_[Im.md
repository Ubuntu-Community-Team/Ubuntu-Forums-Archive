---
title: "[IDEA] Nautilus &quot;Restore from Trash&quot; [Implemented]"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
Currently, when a file is deleted in Gnome, it goes to the trash, but when it cannot be "restored" from the trash to its original location. It must be cut and pasted to a newly-specified location. "Restore from trash" would allow a user to easily restore her deleted files to their original locations.

**Rationale:**
It just adds functionality. Certainly if a user wants to cut and paste the files to a new location, she can do that. But if she deleted twenty music files from twenty different music folders, she shouldn't have to cut and paste twenty times and navigate to twenty separate folders in order to restore those accidentally-deleted files.

**Scope and Use Cases:**
Jenna highlights eighty songs in Rhythmbox (or whatever music player she's using) and intends to right-click to edit the tags. Instead, she ends up accidentally right-clicking and moving them to the files to the trash.

Those eighty songs were in individual folders by artist and album within her larger music folder. She goes into her trash and sees eighty songs. When she right-clicks, there's no option to restore those files to their original locations. So she manually digs two folders deep, moves the file, goes two folders up and two folders deep again, moves another file, and so on.

**Implementation Plan:**
Just do it? I don't know all the technical details involved, but I do know this feature has already been implemented in Thunar and KDE.

There's a thread about this, too:
[Feature: Wastebasket (trash can) restore in Nautilus](http://ubuntuforums.org/showthread.php?t=303238)

And a blueprint and bug report in Launchpad:
[https://blueprints.launchpad.net/ubuntu/+spec/gnome-trash-restore-files](https://blueprints.launchpad.net/ubuntu/+spec/gnome-trash-restore-files)
[https://launchpad.net/ubuntu/+source/nautilus/+bug/14412](https://launchpad.net/ubuntu/+source/nautilus/+bug/14412)

---

### Post by 23meg on 2007-04-15
Looks like it's non-trivial to implement, because it goes beyond the scope of Nautilus, and nobody has stepped up to do it so far.[These]("http://bugzilla.gnome.org/show_bug.cgi?id=41850#c18") [two posts]("http://bugzilla.gnome.org/show_bug.cgi?id=41850#c21") in the upstream Bugzilla cover the technical details.

---

### Post by .t. on 2007-04-15
Well, yes. But it should be trivial to have Nautilus create a gconf cache when a file is moved to .Trash which specifies where it came from. It could then use this to restore the file when necessary.

---

### Post by =0verlord= on 2007-04-15
Even if what the gnome devs want to do is nontrivial, there are dirty hack workarounds that could do the trick until it's done "for real," starting with a .history file in .Trash that simply kept track of what files were deleted from where and when.  I don't see that causing any problems or being very difficult.  Or maybe I don't know what I'm talking about: I blabber, you decide.

---

### Post by Rui Pais on 2007-04-15
thunar do 'Restore from trash', so nautilus should have this feature a long time now...

---

### Post by frup on 2007-04-15
One feature i have missed :(

---

### Post by finalbeta on 2007-04-15
These are the kind off things that shouldn't even be asked. Should have been implemented a long time ago. Even if it does require changes inside the core of GNOME.
This is one of the thinks people expect, like having air when you breathe. 2 thumbs up for me.

---

### Post by Erunno on 2007-04-15
But that would break the trash  can metaphor. How many people do you know that throw something into the trash and start rummaging in it a few seconds later just to retrieve it (apart from the people that make a living from it but they don't own computers anyway) ? This would just confuse less computer literate users.

---

### Post by aysiu on 2007-04-15
> **Erunno said:**
> But that would break the trash  can metaphor. How many people do you know that throw something into the trash and start rummaging in it a few seconds later just to retrieve it (apart from the people that make a living from it but they don't own computers anyway) ? This would just confuse less computer literate users.
Considering it's in Kubuntu, Xubuntu, Mac OS X, and Windows... I don't think it's going to confuse *anybody*. It's not as if you're forcing them to use "restore from trash," anyway.

And all metaphors break down at some point. If you really believe in the folder metaphor, then spatial mode is the way to go, but the developers were smart enough to realize that people don't operate based on the full implications of metaphors into the computer world--they operate based on what they're used to and/or what's easy. So they went with browser mode by default.

Your wallpaper isn't really your wallpaper. Your folder isn't really a folder. And your trash can isn't really a trash can. If the trash can metaphor were a fully functional metaphor, you wouldn't have a "move to trash" context menu item in Nautilus. After all, if I'm in my bedroom and want to throw an item away in the trash (which is in the kitchen), I can't just "move it to the trash" from the bedroom. I have to get up and move it to the kitchen. If we followed the trash can metaphor all the way through, people would always have to drag items directly to the trash icon to throw them away. There would be no delete command that bypassed the trash can. There would be items on top of other items (i.e., more recent items covering up stuff you threw away earlier), and the icon would start smelling badly after a few weeks.

Every metaphor breaks down at some point, especially when it comes to computer interfaces that pretend to be real-life objects. "Restore from trash" is an essential feature. And if you don't want to use it, you don't have to.

Can you link to any thread or blog post where a user states she's confused by the "restore" option in the trash?

---

### Post by picpak on 2007-04-15
This is just common sense. Practically any file manager that has trash support has this.

I'm not taking Nautilus seriously as a file manager until this is implemented.

---

### Post by aysiu on 2007-04-15
> **picpak said:**
> This is just common sense. Practically any file manager that has trash support has this.

I'm not taking Nautilus seriously as a file manager until this is implemented.
In the meantime, Thunar has really matured of late. You can use that in Gnome. I believe it's GTK-based as well.

---

### Post by tom56 on 2007-04-15
> **Erunno said:**
> But that would break the trash  can metaphor. How many people do you know that throw something into the trash and start rummaging in it a few seconds later just to retrieve it (apart from the people that make a living from it but they don't own computers anyway) ? This would just confuse less computer literate users.

But if you're not going to get stuff back from Trash what is the point in having it at all?

I think this is a great idea. Especially for people like me who have a pretty well-organised file system, but a less well-organised memory! I always delete things then can't remember where it came from when I want to put it back.

---

### Post by Erunno on 2007-04-15
> **aysiu said:**
> Considering it's in Kubuntu, Xubuntu, Mac OS X, and Windows... I don't think it's going to confuse *anybody*. It's not as if you're forcing them to use "restore from trash," anyway.

And all metaphors break down at some point. If you really believe in the folder metaphor, then spatial mode is the way to go, but the developers were smart enough to realize that people don't operate based on the full implications of metaphors into the computer world--they operate based on what they're used to and/or what's easy. So they went with browser mode by default.

Your wallpaper isn't really your wallpaper. Your folder isn't really a folder. And your trash can isn't really a trash can. If the trash can metaphor were a fully functional metaphor, you wouldn't have a "move to trash" context menu item in Nautilus. After all, if I'm in my bedroom and want to throw an item away in the trash (which is in the kitchen), I can't just "move it to the trash" from the bedroom. I have to get up and move it to the kitchen. If we followed the trash can metaphor all the way through, people would always have to drag items directly to the trash icon to throw them away. There would be no delete command that bypassed the trash can. There would be items on top of other items (i.e., more recent items covering up stuff you threw away earlier), and the icon would start smelling badly after a few weeks.

Every metaphor breaks down at some point, especially when it comes to computer interfaces that pretend to be real-life objects. "Restore from trash" is an essential feature. And if you don't want to use it, you don't have to.

Can you link to any thread or blog post where a user states she's confused by the "restore" option in the trash?

Seeing that you took your time to answer to my post in detail I almost feel bad to admit that it was just a (maybe poor) joke about the assumptions GNOME developers occasionaly make about their users to justify missing functionality. A quick look at the upper right corner of my post will tell you that I'm using a flavour of Ubuntu that implemented restore from trash since the stone age of free desktops ;-)

---

### Post by aysiu on 2007-04-15
> **Erunno said:**
> Seeing that you took your time to answer to my post in detail I almost feel bad to admit that it was just a (maybe poor) joke about the assumptions GNOME developers occasionaly make about their users to justify missing functionality. A quick look at the upper right corner of my post will tell you that I'm using a flavour of Ubuntu that implemented restore from trash since the stone age of free desktops ;-)
Ah, you were just taking the piss out of me!

I take things too seriously sometimes, I guess.

---

### Post by PartisanEntity on 2007-04-16
Great idea that is so common sense that many other OS's have implemented it.

---

### Post by mangar on 2007-04-16
what happens in the following cases:
1. the containing folder was removed.
2. the original location of the file was on a removeable media, now removed/ destroyed.
3. the user doesn't want the file in the previous location?

possible solution:
1. add "open original location" context-based operation to the item?

---

### Post by gnudoc on 2007-04-16
> what happens in the following cases:
1. the containing folder was removed.
2. the original location of the file was on a removeable media, now removed/ destroyed.
3. the user doesn't want the file in the previous location?

mangar, I've understood the OP's spec to be an added functionablity, not a replacement for the current behaviour of the trashcan. Assuming this to be correct, then:
1. a message pops up to say your original folder doesn't exist, do you want to put the file somewhere else.
2. shouldn't be a problem anyway, because files that are 'trashed' from removable drives (let's say it's mounted as /media/usbdisk) actually go to /media/usbdisk/.trash-username. when the removable drive is unmounted nautilus's trashcan forgets about them.
3. the user just doesn't use this option, she goes by the current behaviour.

however, bou makes a very good point - we should be pestering gnome on this one. :P

---

### Post by aysiu on 2007-04-16
> **mangar said:**
> what happens in the following cases:
1. the containing folder was removed. Well, it could be handled a few different ways (later on today, I'll actually test it to see how Konqueror and Thunar handle this case):
A) The context menu choice "restore to trash" disappears for that item if the location is no longer available
B) The location gets recreated by created new folders 
C) The file gets restored to the top level of whatever does still exist.

> 2. the original location of the file was on a removeable media, now removed/ destroyed. Well, in Gnome, Nautilus will actually move the item to the trash *on* the removable drive, not your hard drive. So it's a non-issue.

> 
3. the user doesn't want the file in the previous location? No one is forcing you to use "restore from trash." It would just be another option. Haven't you ever used Windows, Mac OS X, KDE, or Xfce? Every major graphical user interface *except* Gnome has a "restore from trash" feature. It wouldn't be an experimental new idea. It's just catching up to basic functionality offered by just about every other GUI.

By the way, I've moved discussion about the effectivenes of these [IDEA] threads to its own thread:
[ Are these [IDEA] threads going to actually do anything?](http://ubuntuforums.org/showthread.php?t=410941)

---

### Post by aysiu on 2007-04-16
FYI: This is how KDE handles "restore from trash" if the containing folder is gone.

---

### Post by aamukahvi on 2007-04-17
> **aysiu said:**
> FYI: This is how KDE handles "restore from trash" if the containing folder is gone.
That is mind-boggling; why not an option to recreate the containing folder?

---

### Post by aysiu on 2007-04-17
> **aamukahvi said:**
> That is mind-boggling; why not an option to recreate the containing folder?
Actually, at work, I found out this is how Windows does it--it just automatically recreates the containing folder (it's not an option... it just does it without asking you).

---

### Post by aysiu on 2007-04-17
In case anyone's curious, this is how Thunar handles the problem of restoring a file when the containing folder has already been deleted.

---

### Post by Lucifiel on 2007-04-17
Restore from Trash is certainly a great idea. It's always annoying when you need to cut and paste folders from Trash to another folder. Perhaps, there could be 2 options like:

"Restore to original directory" and "Restore to another directory". For the second option, the user simply selects where to move the directory to. 

Actually, the trash can behaviour needs to be modified as well.

I found out that it does not always show the trash deleted from various partitions, only the trash from your Ubuntu partition. This is really annoying and they should show the trash from all partitions that have been deleted within Ubuntu. Then again, it could be a bug, one which I've filed already.

---

### Post by aysiu on 2007-04-17
This is exactly how Thunar works. If you delete off a removable drive, it moves the file to your hard drive's trash, not the removable drive's trash. And you can always *move* a file from the trash to somewhere else. You're never forced to restore it to its original location. Restore is just another option.

---

### Post by Lucifiel on 2007-04-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/106455](https://bugs.launchpad.net/ubuntu/+bug/106455) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yeah!!!! They need to fix that!!!!! *shakes her fist* If Ubuntu wants to be easy to use, it ought to smooth out issues like these and not send the user into a totally confused mode. 

Newbie user: "Oh no, where did my files go?" *start panicking*

This is like emptying your trash from your waste basket into your trashcan, only for it to end up in your neighbour's trashcan. :p 

And not only do some of the files end up in the trash folder within each partition, sometimes, the trash files show up differently in the Trash folder for Nautilus and the Trash folder for Konqueror. (Edit: Perhaps Konqueror and Nautilus handle the Trash folder differently. Is it possible?)

Trash folder in Nautilus:

[http://img242.imageshack.us/my.php?image=trashfilemanagerkm2.png](http://img242.imageshack.us/my.php?image=trashfilemanagerkm2.png)

Trash folder in Konqueror:

[http://img242.imageshack.us/my.php?image=trashkonquerorpx0.png](http://img242.imageshack.us/my.php?image=trashkonquerorpx0.png)

Look at the attached link for the related bug report I filed, for further details.

---

### Post by aamukahvi on 2007-04-17
> **aysiu said:**
> In case anyone's curious, this is how Thunar handles the problem of restoring a file when the containing folder has already been deleted.
Much better!

---

### Post by simplyw00x on 2007-04-18
Upstream marked this as "really-want-to-fix-but-no-bleeding-idea-how-and-no-one-has-time-to-come-up-with-a-way", basically. It's a very complex problem and they want a solution that gets it right. Until then, everyone can work out their own temporary hack-ish solution (many call this 'using KDE').

---

### Post by 23meg on 2007-04-18
[QUOTE=simplyw00x](many call this 'using KDE').[/QUOTE]

Even more call it "using Thunar".

---

### Post by plb on 2007-04-18
I've seen this feature requested so many times. Maybe this time it will actually make it?

---

### Post by aysiu on 2007-04-18
I've moved the off-topic posts to their own thread:
[Can Thunar do thumbnails now?](http://ubuntuforums.org/showthread.php?t=412664)

---

### Post by aysiu on 2007-04-18
> **simplyw00x said:**
> Upstream marked this as "really-want-to-fix-but-no-bleeding-idea-how-and-no-one-has-time-to-come-up-with-a-way", basically. It's a very complex problem and they want a solution that gets it right. Until then, everyone can work out their own temporary hack-ish solution (many call this 'using KDE').
What exactly does that mean--"no idea how"?

It's implemented in Thunar, Konqueror, Windows, and Mac OS X. There are plenty of models for how to do this, and two of them are Linux ones.

---

### Post by 23meg on 2007-04-18
[QUOTE=aysiu]What exactly does that mean--"no idea how"?

It's implemented in Thunar, Konqueror, Windows, and Mac OS X. There are plenty of models for how to do this, and two of them are Linux ones.[/QUOTE]

Seemingly it's beyond the the scope of Nautilus; it's related to GnomeVFS. Someone has to come up with the required enhancements to GnomeVFS in order for Nautilus to implement it.

---

### Post by aysiu on 2007-04-18
> **23meg said:**
> Seemingly it's beyond the the scope of Nautilus; it's related to GnomeVFS. Someone has to come up with the required enhancements to GnomeVFS in order for Nautilus to implement it.
Ah. Thanks for the clarification.

---

### Post by simplyw00x on 2007-04-18
> Seemingly it's beyond the the scope of Nautilus; it's related to GnomeVFS. Someone has to come up with the required enhancements to GnomeVFS in order for Nautilus to implement it.
Sort of.

> It's implemented in Thunar, Konqueror, Windows, and Mac OS X. 
Yes, and it's implemented *badly*. What happens if you delete a file on a USB drive in any of those systems? The file dies. What about on an ftp server?  Same again. The point about GNOME is that users shouldn't have to worry about where the data is when leaning how to manage it. GNOME vfs is about transparency. The problem is, this in pretty hard, so whilst they figure it out (or at least pick some sensible defaults and provide configuration for the rest), you can do it yourself, by keeping track of where you delete files from, either manually or programmatically, or accepting the incompleteness that is KDE/Thunar/Windows/Apple's solution.

---

### Post by aysiu on 2007-04-18
> **simplyw00x said:**
> 
Yes, and it's implemented *badly*. What happens if you delete a file on a USB drive in any of those systems? The file dies. I think you don't know what you're talking about. In Thunar, the files gets moved to the trash on the user's hard drive. 

In any case, even if you think it's bad, you don't have to use it. Right now, in Nautilus you have one option--manually move it back to some folder. In Thunar and Konqueror, you have two options--manually move it back to some folder, or restore it to its original folder. > The point about GNOME is that users shouldn't have to worry about where the data is when leaning how to manage it. Right. That's why when you delete off a USB drive, Gnome moves the "deleted" files to the hidden trash folder on the USB drive. Then the new users get confused as to why no space was freed up by deleting the files, and they have no idea where the files went (unless they know to press Control-H and look in /media/usb/.Trash).

If the Gnome developers take your stance on this, then everything Linus says about them is true. I really hope they don't.

---

### Post by simplyw00x on 2007-04-18
> I think you don't know what you're talking about.
Ok, so I've never used Thunar. Sue me. That behaviour is still not optimal - what if HD space is low? Would a user expect deleting a remote file to take up local disk space? Wouldn't a user be surprised by long delete times?

> Right. That's why when you delete off a USB drive, Gnome moves the "deleted" files to the hidden trash folder on the USB drive.
Which is a more sensible default? Deleting things by default, keeping them on the drive, or moving them to the local drive? I don't know, and the GNOME devs happen to have made a different decision to the Thunar, Windows etc. ones.

> If the Gnome developers take your stance on this, 
My stance, however poorly-expressed, is that GNOME is trying to get things right. They like sensible defaults.If I had my 'druthers, users would have more scope to change these defaults, but that point is moot. The fact is, they're not going to be forced to accept a sub-optimal solution just because people think it's a good idea, having seen it in windows/Mac. 

The fact is, deleted-file-management is a tricky problem, and neither the GNOME devs nor I is claiming to have all the answers, and I would hope no-one else is, either.

---

### Post by aysiu on 2007-04-18
I'm just saying you're making it sound as if Gnome's approach is superior, when it is not.

Moving a "deleted" file to a hidden trash folder on external media is not what users expect. And not having the option to restore from trash is not better than having the option.

---

### Post by SonicSteve on 2007-04-18
I give both thumbs up, to this idea. I think it's needed also. I do hope that it can't be as hard as people are making out. I'm no programmer but, is it really that hard?

---

### Post by 23meg on 2007-04-18
[QUOTE=SonicSteve]I'm no programmer but, is it really that hard?[/QUOTE]

I'm puzzled; what answer are you expecting to this? "Actually it's not hard but we're lying because we don't want it implemented"?

Anyway, what it comes down to is that GNOME, like any other project of its size, credit and responsibility, rightly has certain fixed ways of dealing with things, and this works for the good of everyone most of the time. The only way to challange their views is to join them, prove your competence, and make a compelling case against the status quo with a good proof of concept followed by code that works. Does anyone feel up to the task, or know someone who would? If not, we either have to do with hackish workarounds (unlikely to end up in Ubuntu), or live without the feature until someone does.

---

### Post by SonicSteve on 2007-04-18
> **23meg said:**
> I'm puzzled; what answer are you expecting to this? "Actually it's not hard but we're lying because we don't want it implemented"?

Anyway, what it comes down to is that GNOME, like any other project of its size, credit and responsibility, rightly has certain fixed ways of dealing with things, and this works for the good of everyone most of the time. The only way to challange their views is to join them, prove your competence, and make a compelling case against the status quo with a good proof of concept followed by code that works. Does anyone feel up to the task, or know someone who would? If not, we either have to do with hackish workarounds (unlikely to end up in Ubuntu), or live without the feature until someone does.

I guess you like sarcasm?
Anyway, it sounds more political than difficult. They don't share our views but they could likely make the change   if they wanted to. Perhaps that's a bit simple but that sounds like what you said. So the answer to my question would be that it's not that hard but it's out of our hands.  Things aren't always difficult, but the road blocks make a solution hard to achieve. 

it's similar to this.
There is enough wealth in the world to keep everyone well fed and well housed. The trouble is the wealth in wrong hands. I hope you know what I getting at.

---

### Post by aysiu on 2007-04-18
Yeah, from 23meg's reply, it sounds as if it's a political issue more than a technological one. Red tape has put Thunar ahead of Nautilus within a year. I remember using Thunar last year (before Dapper showed up) and thinking it was okay but not really functional. Now it's my favorite file manager.

Well, the idea has been thrown out there. If the forum ambassadors and/or developers see fit to make it happen, that's great. Otherwise, we still have Thunar and Konqueror...

---

### Post by 23meg on 2007-04-19
It is very much a technical issue; it's just that most mature projects have their strict ways of dealing with things, and rightly so. There's invariably a lot of policy talk involved in proposing the slightest renovation or new feature in a project of this size and effect. 

A good way of going about this may be a putting a bounty on it. I'll check if there are any in Launchpad and elsewhere.

---

### Post by simplyw00x on 2007-04-19
> o the answer to my question would be that it's not that hard but it's out of our hands
No. It **is** that hard, **and** it's out of our hands to force an hackish solution.

---

### Post by bicchi on 2007-04-20
I vote Yes on this idea. We should make it easy for users to undo their mistakes even if it happens to be accidentally erasing a file.

---

### Post by 23meg on 2007-04-20
There are no bounties on this feature that I could find, and it seems there's not much we can do other than place one. The steps to take would be:

- Consult to upstream on what exactly needs to be done, in GnomeVFS, Nautilus and elsewhere
- Determine the value of the bounty
- Gather the amount, maybe with a [pledge]("http://www.pledgebank.com"), though I'd prefer otherwise
- Place the bounty, dividing the tasks into separate bounties if needed
- Notify any developers whom we know will be interested and possibly capable, as well as upstream

Based on the values of the current bounties on Launchpad, I reckon the value of this would be around $600, but nothing stops us from being more generous than that. I can easily toss $30 in the next month, more if absolutely needed.

Anyone?

---

### Post by Quikee on 2007-04-20
The [specification]("http://www.ramendik.ru/docs/trashspec.html") for a "common" trash (which alo includes this request) has been on freedesktop for quite some time. If any changes to Trash in upstream will be done, this "Trashs" specification should be followed.

---

### Post by 23meg on 2007-04-20
See [this]("http://bugzilla.gnome.org/show_bug.cgi?id=41850#c18"); upstream is aware of and would of course obey the freedesktop specification, but it seems GnomeVFS doesn't play well with it.

---

### Post by Lucifiel on 2007-04-20
Hmmm... I wonder, would it be possible to allow Gnome or Ubuntu, to detect the various .trash directories across the various partitions? And then, the Trash feature would show a listing of the various .trash directories like below. However, this would likely mean that the Trash directories would all have to be named differently instead of all Trash directories having a standard name like ".trash-PapaChicken". 

- .trash-PapaChicken <Partition hdc1>
- .trashMamaChicken <Partition hdc2>
- .trash-WeenieChicken <Partition hdc3>
- .trash-ChickenLittle <Partition sda1>
- .trash-ChickenTyrant <Partition sda2>

---

### Post by el_itur on 2007-04-20
I sugest to make a huge manifestation in cordination with all the loco teams we have here and ask them to make posters saying "hey GNOME devs we want restore from trash" and "hey GNOME devs we want XDS implemented" they will have to follow the masses

I'm not entirely joking.

---

### Post by 23meg on 2007-04-20
Where do we hang the posters? Do we march altogether to the non-existent GNOME headquarters afterwards?

Really, it seems enough people have said "we want this feature" up to now; GNOME is perfectly aware that lots of people want it. Instead of shouting around, let's try our best to get things done ourselves.

---

### Post by gnudoc on 2007-04-20
23meg, the number 30 sounds nice, but since i live on the british side of the pond, I'll make it £30.

so at current exchange rates, we're up to $90. why don't i add an extra £5 (cost of a large cup of coffee) and make it a round $100.

anyone else like to put their money where their mouth is? :)

---

### Post by 23meg on 2007-04-20
Hey, that's great! If we're going to make it $600 we already have ~17% of the sum. 

Anyone else with comments on my proposal, and contributions?

---

### Post by newen on 2007-04-20
I dont' believe this is so complicated to get to work, at least for someone who knows how gnome-vfs works.

The specification is there, and it says clearly that there should be an info file for each deleted file in trash $trash/info. We could add some new methods to the gnome-vfs API to handle retrieving of that information and copying back to the original location. Then, if nautilus is able to know that a specific folder is actually a trash folder, then it simply needs to call our new gnome-vfs methods to restore it.

---

### Post by 23meg on 2007-04-20
That's exactly what's said [in this post]("http://bugzilla.gnome.org/show_bug.cgi?id=41850#c21"). Someone has to do it and get it accepted.

---

### Post by Lucifiel on 2007-04-20
Oh and I was actually thinking about another enhancement for the Delete feature too.

I also feel that there should be some kinda warning or pop-up message. And if the developers can't program this into Ubuntu yet, then why not a simple message?

"Are you sure you want to delete these files? To find the files, either look in the trash folder in the partition from which they were deleted or in the trash folder for Ubuntu." 

"Yes or No."

Edit: Yeah it's a bandaid method but definitely better than not telling you where the files are.

---

### Post by newen on 2007-04-22
Ok, I'll take a look at gnome-vfs and how nautilus handles the trash. I can't promise anything, though.

---

### Post by 23meg on 2007-04-22
Keep us posted on your progress.

So, anyone else contributing cash for a bounty? We now have $100; not nearly enough to be attractive. 

Should we advertise this bounty effort elsewhere?

---

### Post by wormser on 2007-04-22
Restore from trash is a must have feature.  I cannot believe that it has not been done yet.

---

### Post by 23meg on 2007-04-23
> **wormser said:**
> Restore from trash is a must have feature.  I cannot believe that it has not been done yet.

Would you like to help us get it done?

---

### Post by wormser on 2007-04-23
> **23meg said:**
> Would you like to help us get it done?

I would like to help get it done.  The only way I think I can contribute is testing.  I do not have the skills needed to create it and financially I cannot afford to help because I need surgery and will not be able to work for the next 3 months.

---

### Post by botulismo on 2007-04-23
Just chiming in, this is a great idea. I was just finding myself extremely frustrated by this right before I saw this post. Why hasn't this been implemented before? Definitely needs to happen.

---

### Post by apoclypse on 2007-04-23
If they get something that actually works and I see progress then I'm good for a couple of bucks. I also believe that the issue isn't as hard as the gnome devs make it out. In fact saying so makes them seem incompetent and this isn't the first time either. There has been other instances where no-brainer features have been neglected and the response is always some obscure answer where you are not really sure if they don't know how to do it or just don't want to. I tend to go with the latter, but i'm starting to lean on the former as of late. Some of these things seem easy to implement you would think they would be done just to get them out of the way.

---

### Post by gemme on 2007-04-23
My 2 cents - once it's done, there should be an **undo** (**Ctrl-Z**) action in Nautilus :)

We've got undo in gEdit, GIMP, even Firefox can reopen closed tab. Why not Nautilus?

---

### Post by 23meg on 2007-04-23
> **wormser]I would like to help get it done. The only way I think I can contribute is testing. I do not have the skills needed to create it and financially I cannot afford to help because I need surgery and will not be able to work for the next 3 months.[/QUOTE]

I see said:**
> If they get something that actually works and I see progress then I'm good for a couple of bucks.

We can't start a bounty without some money in our hands. Right now we have two people guaranteeing a sum of $100, and it's just not enough.

> **apocalypse]I also believe that the issue isn't as hard as the gnome devs make it out. In fact saying so makes them seem incompetent and this isn't the first time either. There has been other instances where no-brainer features have been neglected and the response is always some obscure answer where you are not really sure if they don't know how to do it or just don't want to.[/QUOTE]

This isn't a no-brainer issue, due to the way that GNOME works. It's not particularly difficult either, and they're not saying so said:**
> Just chiming in, this is a great idea. I was just finding myself extremely frustrated by this right before I saw this post. Why hasn't this been implemented before? Definitely needs to happen.

Yes, definitely. Would you like to contribute towards it happening by putting money into a possible bounty?

[QUOTE=gemme]My 2 cents [/QUOTE]

Come on, that's not enough! Give us ten dollars and maybe we'll get somewhere.

---

### Post by gemme on 2007-04-23
> **23meg said:**
> Come on, that's not enough! Give us ten dollars and maybe we'll get somewhere.
I want to, but I've got hard ulimit on my $ :( And as a computer science student, I thought I might help with a problem like this and improve my desktop, but time doesn't permit this either :(

But another question came to my mind. If Ubuntu is used by so many people, and lots of these people didn't pay for their OS, why not allow them to fund some programming work? It can be done centrally - for example user wants to have a "Restore from trash" - he enters support-open-source.com or something like this, and declare $50 on this purpose (or anything else). Other users do the same. Next, programmers all over the world can implement those features, and - if code is accepted, they're paid their money.

Of course there are many bounties out there, but IMHO it would be a good idea to give users such an opportunity (bounties are generally paid by companies IIRC). I think that's the strength of Open Source. You can go to a university of technology and put an ad saying "I'll pay $200 for implementing my favourite feature". The problem is:
1) Users **don't know** they can do it.
2) Users may not have $200, but if 100 users wants their OS to be improved in a specific way and all of them is able to pay $2 for it (compare it to the price of Windows...), they can **together** fund the work. Like in the Nouveau driver story (and Wikipedia).

That's not as simple as said here and it would need some serious work to make such a system, but I think it would accelerate Open Source development (and maybe, finally outpace Microsoft?).
I'm sure there are developers eager to make some extra $ (even if they are not involved in FLOSS themselves). The question is: how many users would pay to make desktop of their dreams?

If it sounds stupid, forgive me. I'm tired at this hour 8)

---

### Post by apoclypse on 2007-04-23
> **23meg said:**
> I see; I'll keep you posted on testing if we get anywhere. Hope you get well soon.



We can't start a bounty without some money in our hands. Right now we have two people guaranteeing a sum of $100, and it's just not enough.



This isn't a no-brainer issue, due to the way that GNOME works. It's not particularly difficult either, and they're not saying so; it's just that nobody has implemented the prerequisite feature in GnomeVFS so far, and that's just what we're trying to amend. 



Yes, definitely. Would you like to contribute towards it happening by putting money into a possible bounty?



Come on, that's not enough! Give us ten dollars and maybe we'll get somewhere.

Notice how loud people scream when they want something but when it comes to clamming up the cash everybody is quiet. 

Saying it was a no-brainer was an exaggeration. What I meant to say that it is a no-brainer for a project as big and with as much resources as gnome has. Put a google SoC on this bitch. It would be done in one summer no problem. instead here we have the community trying to scrounge some cash to implement some rudimentary feature while the devs that are getting paid to work on gnome can't bother.

---

### Post by 23meg on 2007-04-23
gemme, anyone can place a bounty in Launchpad, and that's what we'll do. We may also place it elsewhere too, and post it to community sites (such as Digg?) to get more attention maybe. See: [https://launchpad.net/bounties/](https://launchpad.net/bounties/)

apoclypse, GNOME is huge, and maybe that's the problem; it's so big that some things inevitably stay unnoticed and not worked on for long periods. It's a matter of priorities, of someone just putting some time in it, and we can have some effect on that, with a bounty. I don't know how exactly SoC works, but I'll check if anyone is working on this, or can be persuaded to. Also, most GNOME developers aren't paid for their work.

---

### Post by apoclypse on 2007-04-23
> **23meg said:**
> gemme, anyone can place a bounty in Launchpad, and that's what we'll do. We may also place it elsewhere too, and post it to community sites (such as Digg?) to get more attention maybe. See: [https://launchpad.net/bounties/](https://launchpad.net/bounties/)

apocalypse, GNOME is huge, and maybe that's the problem; it's so big that some things inevitably stay unnoticed and not worked on for long periods. It's a matter of priorities, of someone just putting some time in it, and we can have some effect on that, with a bounty. I don't know how exactly SoC works, but I'll check if anyone is working on this, or can be persuaded to. Also, most GNOME developers aren't paid for their work.


I understand that, but how does KDE manage. I will hazard and say that KDE is much bigger and more complex than gnome. With two different version being worked on at the moment. by the kde camp,  I say its no excuse. Its free so I don't complain all that much, but to say that they have other priorities when they just announced a push for embedded devices. Listen bro work on the fundamentals first, then focus on the other stuff.

Not all the gnome devs gt payed true, but they devs do get resources from commercial companies such as, Redhatd, Novell, IBM , Sun, etc.

---

### Post by 23meg on 2007-04-23
[QUOTE=apoclypse]I understand that, but how does KDE manage. [/QUOTE]

Specifics, and different ways of working. The problem is with GnomeVFS, and KDE obviously doesn't have GnomeVFS, it perhaps has some other mechanism that I don't know about that does the equivalent job, and that mechanism handles the freedesktop.org trash specification in a way that satisfies KDE developers by now, whereas the same cannot be said of GnomeVFS.

---

### Post by justinjstark on 2007-04-23
While this feature might be useful to some, I don't find it that practical and cannot say that I would use it.

I like how .Trash is treated as a folder with no special properties.  It makes it very versatile: any program can move things to the trash without having to worry about gconf entries or a .history file.

Also, it is good practice to move files out of the trash manually so you know where they go.  Restore seems a bit funky in that if you don't know where the files came from, you won't know where they restore to.

---

### Post by gnudoc on 2007-04-24
> So, anyone else contributing cash for a bounty? We now have $100; not nearly enough to be attractive. 

Anyone? Anyone at all?

:(

---

### Post by oomingmak on 2007-04-24
> **justinjstark said:**
> Restore seems a bit funky in that if you don't know where the files came from, you won't know where they restore to.
You would know exactly where it was going if Gnome bothered to have a path / location column in folders.

---

### Post by justinjstark on 2007-04-24
> **gnudoc said:**
> Anyone? Anyone at all?

:(

Is it possible for me to put in a negative bounty?  Like, here's $50 if you don't implement this?  :)

---

### Post by 23meg on 2007-04-25
[QUOTE=justinjstark]
I like how .Trash is treated as a folder with no special properties. It makes it very versatile: any program can move things to the trash without having to worry about gconf entries or a .history file.[/QUOTE]

Once GnomeVFS can deal with it, I don't think gconf entries or other junk will be needed. 

[QUOTE=justinjstark]Is it possible for me to put in a negative bounty? Like, here's $50 if you don't implement this?[/QUOTE]

No, and you'd be wasting your money; just sit doing nothing. That will help it not get implemented.

---

### Post by UbuntuKhan on 2007-05-01
I second the aysiu idea. It's not futile.
Example:
I uninstalled Firefox and then reinstalled it, but before that I've send my profile to the trash to see if it was the one giving me troubles. Now I want to put it back. It would be so much easier if I could do it automatically restoring from trash.

---

### Post by 23meg on 2007-05-01
I've just checked, and we're past the deadline for new SoC 2007 projects. The list of accepted projects doesn't seem to be up yet, and web searches yield no result that indicates someone is working on this.

---

### Post by beefcurry on 2007-05-04
Shame, I do hope they implement this (and fix alot more nautilus bugs)

---

### Post by Laervian on 2007-05-04
I use Kubuntu and so have not any of the problems you talk about here, so I am not inclined to give some money on it...but what about moving this discussion in a more flashy place? I mean, in 2 weeks this thread has been seen by less than 2 thousand people, and it is no wonder so little people have answered. I do not know much about GNOME community forums or launchpad, but is there no way to make this thread more visible?

Examples: a post or two on digg, maybe a short video on YouTube (with a webcam should not be that hard) under false name so people get to see it ;) (happens all the time :D )...I have never found myself in the situation of advertising something like this, I am no expert in the field, but my guess is that if you want to collect the money for the bounty, you need to have more people aware of the initiative :D

---

### Post by ajmal_82 on 2007-07-16
WOw,what a great idea for bunch of crap apps,why didn't the developers thought of this silly piece of advice.by default we need
trash on desktop.& not Gconf-editor for making changes.how the hell N00bs understand what gconf editor for?
its like editing registry.how good is this?

---

### Post by aysiu on 2007-07-16
Why does the trash have to be on the desktop? It's already on the panel.

The Gnome philosophy is to have basic functionality and have the advanced options tucked away in *gconf-editor* or not available at all.

The KDE philosophy is to make a graphical configuration option for just about anything you can think of.

Trash on the desktop (which even KDE does not have a simple GUI config for... in fact, Windows and Mac do not have easy toggles for this either) is not essential. Restore from trash is, though.

---

### Post by Amaranth on 2007-07-16
> **ajmal_82 said:**
> WOw,what a great idea for bunch of crap apps,why didn't the developers thought of this silly piece of advice.by default we need
trash on desktop.& not Gconf-editor for making changes.how the hell N00bs understand what gconf editor for?
its like editing registry.how good is this?
If you have some reason to go into gconf-editor to change a setting you are by default not a regular user.

---

### Post by zero-9376 on 2007-08-19
The fact that this 'feature' is not implemented is quite ridiculous. I have just accidentally trashed ~200 songs from within rhythmbox (without a confirmation dialog?) and was VERY dissapointed to find that I could not restore them easily, this may not be trivial but neither is trying to work out where 200 songs came from. Granted I have never needed to use this 'feature' in 2 years, but now that I do and it isnt implemented I am honestly shocked. Considering that Gnome is the desktop environment of choice for Ubuntu I think that the Ubuntu devs should do something about this, other than passinng the responsibility to gnome devs. 

This should be fixed before Gutsy is released, before more people experience this HUGE problem. I would like to make this problem more public so that perhaps it would be fixed but this would of couse disuade people from using gnome/ubunutu/linux.

---

### Post by aysiu on 2007-08-19
> **zero-9376 said:**
> 
This should be fixed before Gutsy is released, before more people experience this HUGE problem. I would like to make this problem more public so that perhaps it would be fixed but this would of couse disuade people from using gnome/ubunutu/linux. This isn't a Linux problem. It is a Gnome problem. And, actually, as I found I recently when using my wife's Powerbook, it is a Mac OS X problem as well.

Both Xubuntu (Xfce) and Kubuntu (KDE) have a "restore from trash" feature.

---

### Post by zero-9376 on 2007-08-19
I realise other DE's dont have the issue I was saying that linux by association would be harmed by public exposure of the flaw. Lets get it fixed before too many people experience it and the good name of Ubuntu and linux by association is tarnished.

---

### Post by aysiu on 2007-08-19
> **zero-9376 said:**
> I realise other DE's dont have the issue I was saying that linux by association would be harmed by public exposure of the flaw. Lets get it fixed before too many people experience it and the good name of Ubuntu and linux by association is tarnished.
I think it's a major problem, but considering it hasn't harmed Mac OS X, it probably won't harm Linux.

Gnome devs are notoriously stubborn about these things. More details here:
[The Top 5 Gnome/Ubuntu Usability Bugs I&#8217;d Love to See Fixed](http://ubuntucat.wordpress.com/2007/07/12/the-top-5-gnomeubuntu-usability-bugs-id-love-to-see-fixed/)

---

### Post by Bailx on 2007-08-22
I just accidentally deleted around 45,000 files -> :guitar:


it somehow happened through samba, via win xp, even though there is no shortcut for "invert selection" it did, and deleted everything but what i had selected before i ever noticed....

anyhow... lucky for me i have my smb settings move everything to the trash....

i am using centos/gnome...

is there ANY FRIGGIN way to restore these to their original folders?

like... could i install KDE or thunar... and those programs be able to figure it out, having done what i've already done?

any help MUCH appreciated....

i know i'm not running ubuntu here, but i'm desperate...

---

### Post by aysiu on 2007-08-22
No, there's no way. The only way KDE or Thunar would help is if you'd used KDE or Thunar to delete those files in the first place.

---

### Post by Bailx on 2007-08-22
well guess i'll never be using GNOME again....

i've stood by gnome since around the time of redhat 8....

i always wondered when this feature (or lack thereof) would bite me in the ***....

now it has.... and i'll be using KDE the rest of my days...

---

### Post by aysiu on 2007-08-22
> **Bailx said:**
> well guess i'll never be using GNOME again....

i've stood by gnome since around the time of redhat 8....

i always wondered when this feature (or lack thereof) would bite me in the ***....

now it has.... and i'll be using KDE the rest of my days...
If you like Gnome otherwise, you can do what I do--use Thunar in Gnome instead of Nautilus in Gnome.

---

### Post by altonbr on 2007-10-28
I'm bringin back aysiu's thread of

[**Nautilus "Restore from Trash"**]("http://ubuntuforums.org/showthread.php?t=409817")

I just deleted some photos from what I thought was a duplicate folder. Turned out it wasn't and the duplicates were already in the trash.

So I had to go into the Trash and rename all of the files that had "$filename (copy).$extension" and "$filename (Another copy).$extension" to their original forms.

Talk about lack of user-friendliness.

Does anyone know where there are technical documents on how Windows uses some sort of abstraction to allow "infinite" files of the same name in it's trash can AND allows the user to restore to original location after deletion?

_Other useful links:_
[https://features.launchpad.net/distros/ubuntu/+spec/gnome-trash-restore-files](https://features.launchpad.net/distros/ubuntu/+spec/gnome-trash-restore-files)
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/14412](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/14412)
[http://bugzilla.gnome.org/show_bug.cgi?id=41850](http://bugzilla.gnome.org/show_bug.cgi?id=41850)

---

### Post by 23meg on 2007-10-28
[QUOTE=altonbr]Does anyone know where there are technical documents on how Windows uses some sort of abstraction to allow "infinite" files of the same name in it's trash can AND allows the user to restore to original location after deletion?[/QUOTE]

That kind of abstraction is done in GNOME via GnomeVFS, which is due to be replaced with GVFS, probably in GNOME 2.22. What you're looking to know is whether freedesktop.org compliant trash handling is already implemented in the GVFS API, and if it isn't, whether it's among the currently planned features.

---

### Post by 23meg on 2007-11-30
According to [this comment]("http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/#comment-315") by the GVFS developer, it's in progress.

---

### Post by altonbr on 2007-11-30
> **23meg said:**
> According to [this comment]("http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/#comment-315") by the GVFS developer, it's in progress.

Great, thank you for the information!

> Specifically about undo. There is someone working on that, and it seems to be progressing. Its a lot of work though to get a solid implementation of it though, so we’ll have to see when is finished.

---

### Post by jayde_drag0n on 2007-12-10
we SERIOUSLY need this functionality!!  obviously people have been asking for this sine at minimum feisty fawn and noone has done this... with every other major OS having this feature and the fact that you are trying to compete and tell users that they CAN switch.. it would be a good idea to cover this basic..

and if you think that noone accidentally deletes things and needs to restore anything.. let me give an example... 
AMAROK has no feature to just remove items from amarok.. instead if you want to remove it ... it DELETES the file.. now files that people have spent hours and years organizing.. have just unorganized themselves and placed themselves uncerimoniously into the trash bin where the now hapless user has to manually sort thru a few to mabye thousands of files and place them back where they were supposed to go... and what if they were audiobooks???


can we please stop placing this idea on the back burner??it is essential!!

---

### Post by ronacc on 2007-12-10
if they add this they also need to add the option to completely remove the trashcan , different people want different things I personaly do not want a trashcan, when I remove a file I want it gone ,not hidden and still eating up harddrive space . and yes I have enabled the delete option in nautilus , I dont want the trashcan to even exist.

---

### Post by jbtamug99 on 2007-12-10
Umm... just drag the file from the trash to where you want it??? 

I'm just thankful that it doesn't zap it into oblivion like SUSe used to.

---

### Post by 23meg on 2007-12-10
Merged into relevant Idea Pool thread.

---

### Post by gaspard.leon on 2007-12-11
It seems a trash can can have 2 forms:

"lucky"

"easy"

In the "lucky" model, the trash is simply a folder which can be cleared with a button "Empty trash"... file name collisions can occur, files have no memory of where they were, etc, e.g. like a "Real" trash can...

in the "easy" model, the trash can is "Smart" and remembers where files were, and uses some type of metadata wizardry to allow many files with the same name. This trash can also comes with a "restore" button/option for files so they can be put back where they were.

OS X and Windows 95 to Vista use the "Easy" model

I assume (have not tested) the Gnome/Ubuntu trash can, but from some of the posts in this thread, it appears to use the "lucky" model??

correct?

---

### Post by smartboyathome on 2007-12-12
> **gaspard.leon said:**
> It seems a trash can can have 2 forms:

"lucky"

"easy"

In the "lucky" model, the trash is simply a folder which can be cleared with a button "Empty trash"... file name collisions can occur, files have no memory of where they were, etc, e.g. like a "Real" trash can...

in the "easy" model, the trash can is "Smart" and remembers where files were, and uses some type of metadata wizardry to allow many files with the same name. This trash can also comes with a "restore" button/option for files so they can be put back where they were.

OS X and Windows 95 to Vista use the "Easy" model

I assume (have not tested) the Gnome/Ubuntu trash can, but from some of the posts in this thread, it appears to use the "lucky" model??

correct?

Correct. The gnome devs COULD just use the code from thunar to make it happen, but I don't see that happening.

---

### Post by aysiu on 2007-12-12
> **ronacc said:**
> if they add this they also need to add the option to completely remove the trashcan , different people want different things I personaly do not want a trashcan, when I remove a file I want it gone ,not hidden and still eating up harddrive space . and yes I have enabled the delete option in nautilus , I dont want the trashcan to even exist. Such an option *does* exist in Nautilus. I don't see how that's relevant to the discussion, but even if you imagine it is, then you should support the option to restore from trash, since you got your option as well.

There is a Delete option that can bypass the trash can.

---

### Post by Darkchef on 2008-03-20
This is mandatory stuff that needs to be implemented into the next version of Ubuntu. Can't believe no ones thought of adding it after how many versions ??

---

### Post by aysiu on 2008-03-20
According to people in [the Brainstorm proposal for this](http://brainstorm.ubuntu.com/item/60/), it has already been implemented in Ubuntu 8.04 (which may be coming out next month). I haven't confirmed it yet through testing.

---

### Post by smartboyathome on 2008-03-20
> **aysiu said:**
> According to people in [the Brainstorm proposal for this](http://brainstorm.ubuntu.com/item/60/), it has already been implemented in Ubuntu 8.04 (which may be coming out next month). I haven't confirmed it yet through testing.

Its not in there, the alpha 5 link says it has the POTENTIAL to be put in there now that GVFS is enabled. I haven't seen this function yet.

---

### Post by Amaranth on 2008-03-20
Right, this is not going to happen for GNOME 2.22. Hopefully it'll happen in GNOME 2.24 now that the infrastructure is in place. That means intrepid.

---

### Post by bikeboy on 2008-03-20
> **Darkchef said:**
> This is mandatory stuff that needs to be implemented into the next version of Ubuntu. Can't believe no ones thought of adding it after how many versions ??

What makes you think nobody has thought of it before and wanted to add it?

---

### Post by laptoplinux on 2008-03-21
From the looks of the Hardy beta, restore from trash still hasn't been implemented.  But the framework to do so is there now (GVFS), so I'm hoping that this feature will make it for Ibex.  Anyway, if the restore from trash feature becomes ready before Ibex, what are the chances that it could get put into Hardy through an update?  I just don't want to wait any longer than I have to for this, since a full implementation of the features promised by GVFS would solve many of the little nagging problems that keep parts of Gnome in the dark ages, well behind OSX, KDE, and, sad to say, even WIndows sometimes.

---

### Post by bruce89 on 2008-03-21
No chance for Hardy I'm afraid. Stable Release Updates (SRUs, not Scottish Rugby Union) are only security or bugfix updates.

---

### Post by smartboyathome on 2008-03-21
> **laptoplinux said:**
> From the looks of the Hardy beta, restore from trash still hasn't been implemented.  But the framework to do so is there now (GVFS), so I'm hoping that this feature will make it for Ibex.  Anyway, if the restore from trash feature becomes ready before Ibex, what are the chances that it could get put into Hardy through an update?  I just don't want to wait any longer than I have to for this, since a full implementation of the features promised by GVFS would solve many of the little nagging problems that keep parts of Gnome in the dark ages, well behind OSX, KDE, and, sad to say, even WIndows sometimes.

It should make it for Ibex. There just wasn't enough time with this release to implement it (which would you rather have, a stable Nautilus with tons of bug fixes or remove from trash?).

---

### Post by laptoplinux on 2008-03-21
Nice artsy ubuntu logo there.

Anyway, I'm not complaining, just asking.  I kinda figured this would happen anyway from watching GVFS's progress relative to Hardy's release date.  Restore from trash is a relatively minor thing, and I certainly prefer rock solid software.  I'm still running Beryl because at first Compiz-Fusion was too buggy for me.  I think Compiz-Fusion has come far and is fine now, and I'm just waiting for the Heron's release to make my switchover there.

But even so, restore from trash is still one thing Gnome lacks that every other desktop has, and since I tend to be the go-to guy for promoting Linux uptake at my workplace, every little patched chink in my arguments helps.

---

### Post by 23meg on 2008-03-21
Alex Larsson had mentioned on one of the comments in his blog that someone was working on it, at least a month and a half ago. This means it's very likely that it will make it to GNOME 2.24.

---

### Post by bruce89 on 2008-03-21
This will need new API in GIO, so I don't think this will happen until Hardy+2 (GLib 2.18). See [http://bugzilla.gnome.org/show_bug.cgi?id=518573](http://bugzilla.gnome.org/show_bug.cgi?id=518573).

This could be handled in nautilus directly, but it would be a bit of a hack.

---

### Post by aysiu on 2008-03-21
My preferred file browser is Thunar in the meantime.

---

### Post by 23meg on 2008-03-21
> **bruce89 said:**
> This will need new API in GIO, so I don't think this will happen until Hardy+2 (GLib 2.18). See [http://bugzilla.gnome.org/show_bug.cgi?id=518573](http://bugzilla.gnome.org/show_bug.cgi?id=518573).


There's a good chance that there will be new GTK and GLib releases for GNOME 2.24 (do a search and you'll find some related mailing list posts). I also recall Larsson talking about an interim solution to let apps utilize new GIO features in case of a delay caused by the GLib release cycle, but that may be pre-2.22 so don't hold me up to it.

---

### Post by bruce89 on 2008-03-21
> **23meg said:**
> There's a good chance that there will be new GTK and GLib releases for GNOME 2.24 (do a search and you'll find some related mailing list posts). I also recall Larsson talking about an interim solution to let apps utilize new GIO features in case of a delay caused by the GLib release cycle, but that may be pre-2.22 so don't hold me up to it.

Ah, I didn't think they were thinking of having another new GLib for 2.24. [http://www.mail-archive.com/gtk-devel-list@gnome.org/msg07639.html](http://www.mail-archive.com/gtk-devel-list@gnome.org/msg07639.html) confirms your interpretation.

---

### Post by Awalton on 2008-03-24
> **bruce89 said:**
> This will need new API in GIO, so I don't think this will happen until Hardy+2 (GLib 2.18). See [http://bugzilla.gnome.org/show_bug.cgi?id=518573](http://bugzilla.gnome.org/show_bug.cgi?id=518573).

This could be handled in nautilus directly, but it would be a bit of a hack.

Actually, it's a bit of a hack not to handle this in the application; the API requested there is a bad idea for a largish number of ideas (the biggest being there's no possible recovery path).

Here's the implementation I did of it already and the discussion of why it's a bad idea:

[quote=A.Walton]
The "g_file_restore_from_trash()" API seems like a bit odd to me; the
trash location is a real location now, we can move to and from it at
will, but it's certainly doable. The problem I see with this API is
that if you've got a GFile to the item in the trash, coding up the
restore operation isn't difficult at all, but probably should be
application-specific (as there are several different cases I can think
of in this situation).

The even bigger problem would be that this operation is very nasty in
the dozens of ways it can go wrong, of which we'd want much better
error handling and reporting than GLib could probably give us without
a dozen flags and/or operation versions. And it's is odd that it would
belong to the GFile namespace, but would only work for trash:/// URIs.
And if you already have one of them, why don't you implement it the
way you see fit anyways?

For the ridiculous email-ware implementation of this:
/**
 * g_file_restore_from_trash:
 * @file: a #GFile with a trash:/// URI pointing to a trashed file.
 * @flags: a set of #GFileCopyFlags to use during the move.
 * @cancellable: optional #GCancellable object, %NULL to ignore.
 * @progress_callback: #GFileProgressCallback function for updates.
 * @progress_callback_data: gpointer to user data for the callback function.
 * @error: #GError for returning error conditions, or %NULL
 *
 * Restores a file from the Trash bin to its original location. This method is
 * more than a little bit ridiculous IMO, as it gives no recovery
 * strategy; it just fails if there's any kind of error at all. It also lives
 * in the g_file_* namespace, even though it only works for
 * "trash:///" URIs. It also does sync I/O twice; once to get info on the
 * trashed file, and one very long I/O operation during the move. Did I
 * mention that I think this is a bit silly for GIO? ;)
 *
 * If you're writing an application that restores files from trash, you should
 * probably implement this yourself, and not use this method. It definitely
 * won't work for Nautilus ;).
 */
gboolean
g_file_restore_from_trash (GFile *file,
                          GFileCopyFlags flags,
                          GCancellable *cancellable,
                          GFileProgressCallback progress_callback,
                          gpointer progress_callback_data,
                          GError **error)
{
 GFileInfo *info;
 GError *my_error;
 g_return_val_if_fail (G_IS_FILE (file), FALSE);

 if (g_cancellable_set_error_if_cancelled (cancellable, error))
   return FALSE;

 if (!g_file_has_uri_scheme (file, "trash"))
   {
     g_set_error (error, G_IO_ERROR, G_IO_ERROR_INVALID_ARGUMENT,
        _("Restoring from non-trash URIs is not possible"));
     return FALSE;
   }

 info = g_file_query_info (source,
                           "trash::orig-path",
                           cancellable,
                           &my_error);
 if (info != NULL)
   {
     GFile *dest = NULL;
     gboolean success = FALSE;
     dest = g_file_new_for_path(g_file_info_get_attribute_byte_string
(info, "trash::orig-path"));
     success = g_file_move (file, dest, cancellable,
               progress_callback, progress_callback_data, &my_error);

     g_error_propagate (error, my_error);
     g_object_unref (info);
     g_object_unref (dest);
     return success;
   }
 else
   g_error_propagate (error, my_error);

 return FALSE;
}

Keep in mind I didn't test that, but it's more or less what would have
to happen.

If you only have the file name, enumerate the trash directory, sort
the results, and do a binary search for it. Not sure what would happen
if you trashed two files of the same name from the same directory
though, having to deal with the edge cases of the "_filename.2",
"_filename.3" with the same original path if you're thinking about
going that way though. Nautilus will have to do a lot more than the
above to keep track of these things, such as being able to recreate
directory structures if someone decided to delete them instead of just
trashing them, making sure that the item's original path is mounted
(which should probably always be the case, but who knows what
weirdness could happen), etc.
[/quote]

The code in Nautilus will need to be significantly more complex, but we do intend to work on it for 2.24.

---

### Post by subverted on 2008-06-17
Yes, this is retarded. I just install the trash project.

[http://www.linux.com/feature/138331](http://www.linux.com/feature/138331)

But after I installed it from source, I moved it to the trash can, now for some reason it doesnt work, and I can't empty my trash! The damn trash project folder is so special it can't be deleted and/or restored from trash! What a paradox.

---

### Post by smartboyathome on 2008-06-17
That isn't meant for Nautilus or any other file manager. It is meant for the command line, so it shouldn't affect Nautilus or any other file manager in any way.

---

### Post by amano on 2008-06-17
Is this still being worked on? From what I gather, nautilus will rather get tabs than a working trash can. :popcorn:

---

### Post by perroazul on 2009-02-18
another idea that I think would be very useful is adding a "date erased" column in the nautilus trash. very often I've found myself playing with the "date modified" and "date accessed" columns trying to find a particular file I know I erased. This could be difficult to do when you have thousands of files in your trash.

---

### Post by altonbr on 2009-02-18
> **perroazul said:**
> another idea that I think would be very useful is adding a "date erased" column in the nautilus trash. very often I've found myself playing with the "date modified" and "date accessed" columns trying to find a particular file I know I erased. This could be difficult to do when you have thousands of files in your trash.

I agree.

Does anyone know the status on restoring your trash? I heard it was in GNOME 2.24, but running Intrepid, I haven't seen this function yet.

---

### Post by CarpKing on 2009-02-20
> **altonbr said:**
> I agree.

Does anyone know the status on restoring your trash? I heard it was in GNOME 2.24, but running Intrepid, I haven't seen this function yet.

Open the "Trash" folder and right click on a file therein.  One of the options should be "Restore."

---

### Post by aysiu on 2009-02-20
> **CarpKing said:**
> Open the "Trash" folder and right click on a file therein.  One of the options should be "Restore."
What do you know? It made it in.

Apparently the Brainstorm idea is marked implemented, too:
[http://brainstorm.ubuntu.com/idea/60/](http://brainstorm.ubuntu.com/idea/60/)

---

