---
title: "What is Canonical thinking!?!"
date: 2008-04-28
forum: The Cafe
---

### Post by TBOL3 on 2008-04-28
All right, everyone is complaining about that bug that hardy has, or that feature that was removed.

Well, my complaint is completely different.  I like ubuntu very much, and hardy is the best release to date.  Until the 29th time I boot up my computer.

If Canonical prides themselves in making a good user friendly system (which they do), then why, why, WHY! do they do the disk scan automaticly every 29th boot.  I've needed to start my laptop, and have it working in 5 minutes.  But no, it had to search.  Thus, almost tripling the time it takes to boot.

Why can't it do this search as it shuts down.  When I turn off my laptop, I don't care if it takes 2 minutes, or 20 minutes to shutdown.  And if it's worried about the laptop battery running out, it could do a simple scan and if, say, there's 50% juice or more, then it will scan, if not, it will wait until the next shutdown.

And why does it go directly to text only.  If I didn't know anything about computers, and my computer came up with all of this texty stuff, I would be worried my computer was broken, and the first time that it did the scan, I was worried that I broke something.  So, why can't it put a big graphic on say, the upper half of the screen saying, "don't worry, your computer is preforming a simple scan, it should end soon, and your computer will shutdown,"  or something to that effect.

(sighs, takes a breath, calms down, and begins to type again)

Or is there something that prevents this from being possible?

Once again, ubuntu is an awesome product, and I really like the new version, as it fixes graphics card driver problems.

And I also know that this is a community form, and is not related to canonical in any way.

Thank you

---

### Post by Lostincyberspace on 2008-04-28
that is a good Idea you should go put it in the brainstrom.

---

### Post by picpak on 2008-04-28
Isn't there a shortcut (Ctrl+C, I believe) that cancels the scan process?

---

### Post by TeraDyne on 2008-04-28
> **PetePete said:**
> i compleatly agree with you, but no doubt someone will point out the various patches/apps to change the behaviour of this. ... and i'd like to be the first to point out that the ability to patch something is irrelivent, it shouldn't happen in the first place. aunty Betty isn't going to know how to download and run the script to modify the system

maybe someone should file a bug to launchpad. i would. but . well . i cant be f*cked

Nah, this is more of a brainstorm thing. I agree with your thoughts, though.

> **picpak said:**
> Isn't there a shortcut (Ctrl+C, I believe) that cancels the scan process?

Last time I did that... Well, I try not to think about it. Basically, I had to restart, as it refused to mount the partition it was checking (my home partition). I was going nuts, hoping it hadn't seriously messed with anything.

---

### Post by TBOL3 on 2008-04-28
> **Lostincyberspace said:**
> that is a good Idea you should go put it in the brainstrom.

Yes, I was going to give it to them, but I wanted to make sure that
there was no problems with it before I bothered them with it.

Thank you.

---

### Post by qamelian on 2008-04-28
Strange. My Hardy install prompts me to press a key to skip the check if I want.

---

### Post by smoker on 2008-04-28
found this: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460)

---

### Post by LaRoza on 2008-04-28
Why not? It can be changed if you don't want it to do that.

---

### Post by SuperSon!c on 2008-04-28
> **TBOL3 said:**
> Yes, I was going to give it to them, but I wanted to make sure that
there was no problems with it before I bothered them with it.

Thank you.

nah, suggest it!  good idea.

---

### Post by Barrucadu on 2008-04-28
As far as I recall this is an ext2/3 thing. A value is set in the superblock determining how many boots until it is checked. You could switch to another filesystem if you really wanted? (Go on, be adventerous ;))

---

### Post by bilal.17 on 2008-04-28
Imagine if a newbie had encountered this.. they would probably think that they broke their computer somehow. They should make it like in Windows where it provides a much better looking check that wont scare anyone and the option to skip it.

  An even better solution would be to create a GUI for this to be as simple as possible and not scare away any of the newbies. I would not want my mom to suddenly be freaked out that her Ubuntu laptop is suddenly not working when she turns it on and all this text comes out and has some weird number thing. If Ubuntu is ever to reach the mainstream casual user they need to fix this minor problem or anyone  who is not computer literate will run away screaming from Ubuntu and Linux in general.

---

### Post by ghindo on 2008-04-28
I'm able to skip through fsck in Hardy.  I just press Escape and I'm out of it.

---

### Post by Ptero-4 on 2008-04-28
What the OP wants to get implemented IIRC would require ubuntu to use bootsplash instead of usplash since usplash doesn't support (and can't support without kernel hooks) using graphics for this type of process (it also cannot use graphics for the hibernate sequence).

---

### Post by LaRoza on 2008-04-28
> **bilal.17 said:**
> imagine if a newbie had encountered this.. they would probably think that they broke their computer somehow... they should make it like in windows where it provides a much better looking check that wont scare anyone ... and the option to skip it... an even better solution would be to create a gui for this to be as simple as possible and not scare away any of the newbies... i would not want my mom to suddenly be freaked out that her ubuntu laptop is suddenly not working when she turns it on and all this text comes out and has some weird number thing... if ubuntu is ever to reach the mainstream casual user they need to fix this minor deficiency or anyone with who is not computer literate will run away screaming from linux

That is far fetched. It says what it is doing, and it does it and continues to boot as normal.

I doubt that the look of the file system check is a big factor in usability.

---

### Post by dasunst3r on 2008-04-28
Even though I am lucky enough to only have this happen once every two months (standby works on my computer), it is definitely bothersome if you are on battery power.  You should suggest that the test is deferred to the next boot whenever the computer is on battery.  I wouldn't advocate skipping it outright because those tests are good for the computer's stability.

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> That is far fetched. It says what it is doing, and it does it and continues to boot as normal.

I doubt that the look of the file system check is a big factor in usability.
So what your saying LaRoza is that a text only interface is normal for a casual user who just browses the internet and has some photos. To a user like this  it might scare them into thinking that something might have happened to their system because they are not used to the non-GUI interface. 

I am in no way saying that a file system check is not necessary. But just merely pointing out that the way it is displayed is not the most user friendly way there is.

---

### Post by LaRoza on 2008-04-28
> **bilal.17 said:**
> But to a newbie it might scare them thinking that something might have happened to their system because they are not used to the non-GUI interface. 

I am in no way saying that a file system check is not necessary. But just merely pointing out that the way it is displayed is not the most user friendly way there is.

I have seen posts on this forum showing concern about it, but I never saw a new user suddenly get that and decide it was a problem.

It isn't like it happens the first time one boots.

Yeah, it may surprise them, but it is obvious what it is doing as it is stated on the screen. Having a pretty GUI is just a waste especially for that.

---

### Post by stmiller on 2008-04-28
There are many ways to change the settings. Here is one:

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

File system checks are actually a good thing...

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> I have seen posts on this forum showing concern about it, but I never saw a new user suddenly get that and decide it was a problem.

It isn't like it happens the first time one boots.

Yeah, it may surprise them, but it is obvious what it is doing as it is stated on the screen. Having a pretty GUI is just a waste especially for that.

To you it may seem like a waste, but to someone who has never seen this before they will probably think that there is something wrong. To someone who never sees the text based part of linux, it would probably worry them.
 I think that it would really help, these type of users if a better way of displaying this is provided. If we are going to try and take away market share from Windows then  we must be able to support all users whether it is a basic user or a computer programmer and this is one of those things in Linux that i think can be improved on.

---

### Post by LaRoza on 2008-04-28
> **bilal.17 said:**
> So what your saying LaRoza is that a text only interface is normal for a casual user who just browses the internet and has some photos. To a user like this  it might scare them into thinking that something might have happened to their system because they are not used to the non-GUI interface. 

I am in no way saying that a file system check is not necessary. But just merely pointing out that the way it is displayed is not the most user friendly way there is.

No it isn't pretty. But then again, it doesn't do anything and the user doesn't have to interact with it, just wait. Yes, they will likely think something went wrong, but it states what it is doing and why when it does it.

Saying it is "CLI" is somewhat misleading, as it doesn't require any interaction.

---

### Post by Atomic Dog on 2008-04-28
Install Bonager.  It will tell you a forced scan is coming up and will let you delat it till you have time to do it.  It will still scan on startup, but at least it won't be a surprise.

---

### Post by LaRoza on 2008-04-28
The new users will get over and go on with their life in time and possibly with counseling.

---

### Post by LaRoza on 2008-04-28
The new users will get over it and go on with their life in time and possibly with counseling.

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> No it isn't pretty. But then again, it doesn't do anything and the user doesn't have to interact with it, just wait. Yes, they will likely think something went wrong, but it states what it is doing and why when it does it.

Saying it is "CLI" is somewhat misleading, as it doesn't require any interaction.
Unless it finds an error, then the user does have to interact with it. Anyways I'm just trying to say that it would be more helpful if it was displayed in a more user friendly way.

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> The new users will get over it and go on with their life in time and possibly with counseling.

Not if they are the type of user who wants things to just work. They usually dont want to search google or the ubuntuforums for things like this.

---

### Post by smoker on 2008-04-28
> **LaRoza said:**
> The new users will get over it and go on with their life in time and possibly with counseling.

three years later, and my psyche is still mortally wounded and i have difficulty facing society, can you recommend a good shrink?:lolflag:

---

### Post by LaRoza on 2008-04-28
> **bilal.17 said:**
> Not if they are the type of user who wants things to just work. They usually dont want to search google or the ubuntuforums for things like this.

I like helping people, but I have a limit. If a screen that states exactly what it is doing and why isn't clear enough, I really don't want to be on the other end of the ethernet.

> **smoker said:**
> three years later, and my psyche is still mortally wounded and i have difficulty facing society, can you recommend a good shrink?

Yes, cold water.

---

### Post by smoker on 2008-04-28
> **LaRoza said:**
> Yes, cold water.

:lolflag:

---

### Post by TBOL3 on 2008-04-28
I must agree, at least a nice splash screen would be 100x better.  And for those of you who think it is a waist.  Unless there is some incompatibility issue, then I think that the 1 mb max needed to put an image there is WELL worth it.

---

### Post by p_quarles on 2008-04-28
> **bilal.17 said:**
> Unless it finds an error, then the user does have to interact with it. Anyways I'm just trying to say that it would be more helpful if it was displayed in a more user friendly way.
Errors (of the type that can't be fixed automatically) are extremely rare, and would be difficult enough that even a "sleek" GUI for fixing it would confuse a non-technical user. 

As for the ASCII progress bar "scaring" away new users, do you have *any* evidence for this claim? Are there droves of newbies running back to Windows because their hard drive was scanned by an unfriendly-looking program for a couple minutes?

---

### Post by LaRoza on 2008-04-28
> **TBOL3 said:**
> I must agree, at least a nice splash screen would be 100x better.  And for those of you who think it is a waist.  Unless there is some incompatibility issue, then I think that the 1 mb max needed to put an image there is WELL worth it.

No, it wouldn't be any better. It is a rare event. It is a non interactive event. And it can be controlled.

Do you know what it would entail putting a GUI for that? More than 1 MB...

---

### Post by TBOL3 on 2008-04-28
> **p_quarles said:**
> Errors (of the type that can't be fixed automatically) are extremely rare, and would be difficult enough that even a "sleek" GUI for fixing it would confuse a non-technical user. 

As for the ASCII progress bar "scaring" away new users, do you have *any* evidence for this claim? Are there droves of newbies running back to Windows because their hard drive was scanned by an unfriendly-looking program for a couple minutes?

Well, if I didn't hate windows as much as I do, then I would be one.

A few of the people I know would love ubuntu, but they would hate the ascii.

One person I know left ubuntu because of some ugly ascii (it was for ubuntu's default grub settings).  But then, that same person thought ubuntu looked like poo.

I've seen several reviews of linux computers, praising OSs for having a graphical user interface.

And the majority of the market that are very computer illiterate don't know much about linux at the moment, but it's things like this that makes them say.  Linux, what a joke.

---

### Post by LaRoza on 2008-04-28
> **TBOL3 said:**
> Well, if I didn't hate windows as much as I do, then I would be one.

A few of the people I know would love ubuntu, but they would hate the ascii.

One person I know left ubuntu because of some ugly ascii (it was for ubuntu's default grub settings).  But then, that same person thought ubuntu looked like poo.

I've seen several reviews of linux computers, praising OSs for having a graphical user interface.

And the majority of the market that are very computer illiterate don't know much about linux at the moment, but it's things like this that makes them say.  Linux, what a joke.

I am not concerned with new users. I like having a usable system. There are other distros that hide the fact that the OS is not a GUI. Some of them don't even have an easy way to get a terminal.

---

### Post by TBOL3 on 2008-04-28
> **LaRoza said:**
> No, it wouldn't be any better. It is a rare event. It is a non interactive event. And it can be controlled.

Do you know what it would entail putting a GUI for that? More than 1 MB...

I wouldn't really know, that's why I said if there isn't any compatibility issues.  But it still is much calmer if a screan came up and said, "DON"T PANIC"

---

### Post by LaRoza on 2008-04-28
> **TBOL3 said:**
> I wouldn't really know, that's why I said if there isn't any compatibility issues.  But it still is much calmer if a screan came up and said, "DON"T PANIC"

I would hate that also. This isn't OS X..."Pay no attention to the details, you are too stupid to be trusted with knowing what is going on". Nor is it Windows..."Hey! File systems get corrupted. Big deal. It will be easily fixed with a reinstall"

---

### Post by Darkhack on 2008-04-28
I have to agree with LaRoza on this one.  You are assuming that the user is going to freak out **only** on the basis that the computer is displaying information via a command line instead of a GUI.

The reason average users don't like the CLI is because they hate memorizing commands and they like to see what options are available.  Graphical menus give them choices and they know what is available.  It is also faster for some tasks, more intuitive, and required for tasks like image editing or WYSIWYG document processing.

The user is not going to freak out if the CLI is being used just to display a message as long as it says what it is doing.  Windows has the same thing if I remember correctly.  If you shut down Windows 98 suddenly instead of via the shutdown menu, then on the next boot it displays a CLI and does a disk check.

The average user isn't your senile grandmother; she is a below average user.

I can't find the discussion off hand but, there was a discussion on the Epiphany mailing list a while back about a dialog being displayed with buttons "Allow" or "Deny".  I can't remember what the dialog was for but probably something about cookies or allowing unencrypted elements on an https page.  Anyways, it turned into a massive flame war over the UI design of this dialog.  There was a checkbox for "Remember this setting" or "Don't ask me again" kind of thing.  I swear to god that someone called checkboxes "confusing" and that four buttons with "Always Allow", "Allow", "Deny", or "Always Deny" was better.  I do prefer the checkbox method since I typically associate more permanent settings with a checkbox more so than a button, but that's not the point.  The point is that this whole war erupted because someone thought the checkbox was too confusing to the average user.

The average user does need some hand holding, yes, but don't assume they need a straitjacket and a bottle of Prozac to use the computer.

---

### Post by TBOL3 on 2008-04-28
No, that's not what I'm saying.

In ubuntu 6.06, there was the load bar in a gui, under that was the commands that were going on.

If you include a simple picture in the top half of the screan, containing the don't panic, and a loading bar, and then the ascii below, that would be 100x better.

Also, even if the entire screen said DON"T PANIC, that still wouldn't be as bad as OS X, because in OS X, you can't change the default DON'T PANIC, but in linux, if you even know enough about the ascii to do anything about it, then you should know enough to say type in a simple command to turn that 'feature' on.  Rather then the other way around.  Because you need to know what you are doing before you can even think of turning that 'feature' off.

And I don't buy the whole, "Well, they should learn it" philosophy.  People don't want to know the interworking of a computer.  They just want it to work.  An analogy would be a car, I don't want to know how it works, so long as it works.

---

### Post by LaRoza on 2008-04-28
> **TBOL3 said:**
> And I don't buy the whole, "Well, they should learn it" philosophy.  People don't want to know the interworking of a computer.  They just want it to work.  An analogy would be a car, I don't want to know how it works, so long as it works.

They don't have to. It is performing a disk check, it takes a little bit of time, then it is done. 

I don't care if people don't want to learn the terminal, but this is a trivial issue. 

It is like the bios screens. Instead of being useful, like on older computers, you get the computer's manufacturer's logo and you have to try to press the keys to get any useful information.

---

### Post by martyssweb07 on 2008-04-28
Actually I don't mind it, it would be a nice tweak if it would popup a gui box telling you the time before when shutting down. and let you choose to say ok or schedule it for a different time

---

### Post by TBOL3 on 2008-04-28
Exactly, showing the logo, or some other image is better.  Once again, if you know enough to play with the bios, then you should know enough to turn on the settings.  Besides, it takes less the 1 sec. to press the keys.  And I'd much rather see a logo, then stupid text.

Also, here a video showing the people like a nice gui.
[http://video.google.com/videosearch?q=linux%20sucks&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wv](http://video.google.com/videosearch?q=linux%20sucks&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wv)
And also, more proof, the existence of compiz-fusion.

---

### Post by LaRoza on 2008-04-28
> **TBOL3 said:**
> Exactly, showing the logo, or some other image is better.  Once again, if you know enough to play with the bios, then you should know enough to turn on the settings.  Besides, it takes less the 1 sec. to press the keys.  And I'd much rather see a logo, then stupid text.


The ultimate proof that this is not a turn off for ex-Windows users:

[img]http://www.freesmileys.org/smileys/violent002.gif[/img]

---

### Post by Nessa on 2008-04-28
If I had a laptop and was worried about battery life, I'd prefer it the way it is rather than something flashy and graphic.

---

### Post by SunnyRabbiera on 2008-04-28
well the system check does help though, if you have bad files it will tell you...
besides its not as bad as defragging all the time in windows

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> I am not concerned with new users. I like having a usable system. There are other distros that hide the fact that the OS is not a GUI. Some of them don't even have an easy way to get a terminal.

Maybe you arent concerned with new users, but others want to encourage new users to try out ubuntu. It would help if it had a nice GUI for them to use.

---

### Post by bilal.17 on 2008-04-28
> **SunnyRabbiera said:**
> well the system check does help though, if you have bad files it will tell you...
besides its not as bad as defragging all the time in windows

Also I am not saying that a system check is not helpful, just saying it can be presented differently.

---

### Post by LaRoza on 2008-04-28
> **bilal.17 said:**
> Maybe you arent concerned with new users, but others wont to encourage new users to try out ubuntu. It would help if it had a nice GUI for them to use.

It does have a nice GUI to use. It has Compiz-fusion.

> 
This is a free operating system, with an advanced GUI application called Compiz. It has a helpful and free support forum. It has thousands of apps easily installed with a couple clicks. It is light on resources compared to Windows, and it isn't vulnerable to virus and spyware.

Oh, by the way, every 23 reboots it will do a boring file system check before you can log on. It is plain text.


If someone goes screaming into the night because of this, well, the night deserves them.

---

### Post by smoker on 2008-04-28
> **bilal.17 said:**
> Maybe you arent concerned with new users, but others want to encourage new users to try out ubuntu. It would help if it had a nice GUI for them to use.

are you serious, you're referring to a guy with over 9000 posts, been thanked nearly 600 times, and has a list of helpful links in his sig!

as for a nice gui, the first time i saw the disk check didn't have me scurrying back to windows. maybe windows users have dumbed down a lot since then (no offence intended!)
:)

---

### Post by kavon89 on 2008-04-28
> **TBOL3 said:**
> And why does it go directly to text only.  If I didn't know anything about computers, and my computer came up with all of this texty stuff, I would be worried my computer was broken, and the first time that it did the scan, I was worried that I broke something.  So, why can't it put a big graphic on say, the upper half of the screen saying, "don't worry, your computer is preforming a simple scan, it should end soon, and your computer will shutdown,"  or something to that effect.

I agree with you and [made a suggestion]("http://ubuntuforums.org/showthread.php?t=515875") a while ago about it.

It's been implemented in 8.04, so it's a non-issue now.

[http://brainstorm.ubuntu.com/idea/11/](http://brainstorm.ubuntu.com/idea/11/)

> This is implemented in Hardy Heron. You can press the escape key to cancel the disk check.

---

### Post by mustang on 2008-04-28
> **TBOL3 said:**
> All right, everyone is complaining about that bug that hardy has, or that feature that was removed.

Well, my complaint is completely different.  I like ubuntu very much, and hardy is the best release to date.  Until the 29th time I boot up my computer.

If Canonical prides themselves in making a good user friendly system (which they do), then why, why, WHY! do they do the disk scan automaticly every 29th boot.  I've needed to start my laptop, and have it working in 5 minutes.  But no, it had to search.  Thus, almost tripling the time it takes to boot.

Why can't it do this search as it shuts down.  When I turn off my laptop, I don't care if it takes 2 minutes, or 20 minutes to shutdown.  And if it's worried about the laptop battery running out, it could do a simple scan and if, say, there's 50% juice or more, then it will scan, if not, it will wait until the next shutdown.

And why does it go directly to text only.  If I didn't know anything about computers, and my computer came up with all of this texty stuff, I would be worried my computer was broken, and the first time that it did the scan, I was worried that I broke something.  So, why can't it put a big graphic on say, the upper half of the screen saying, "don't worry, your computer is preforming a simple scan, it should end soon, and your computer will shutdown,"  or something to that effect.

(sighs, takes a breath, calms down, and begins to type again)

Or is there something that prevents this from being possible?

Once again, ubuntu is an awesome product, and I really like the new version, as it fixes graphics card driver problems.

And I also know that this is a community form, and is not related to canonical in any way.

Thank you

I agree with your point and sentiment. You even offer a good solution. See if you can push this idea upstream.

edit: way to read the entire thread. /me slaps myself. Good on you amar for suggesting this first!

---

### Post by LaRoza on 2008-04-28
> **smoker said:**
> are you serious, you're referring to a guy with over 9000 posts, been thanked nearly 600 times, and has a list of helpful links in his sig!

as for a nice gui, the first time i saw the disk check didn't have me scurrying back to windows. maybe windows users have dumbed down a lot since then (no offence intended!)
:)

Or girl, or her sig. ;)

---

### Post by Polygon on 2008-04-28
The hard drive check is essential and shouldent be changed

and also you cant do the hard drive check while the disks are mounted, so i dont think it is possible, or it would be harder to do the check when its shutting down.

I have the text enabled for the ubuntu loading screen and when it does a drive check it says "checking disk" and then gives a percentage, so i dunno what it does for a normal installation, but something like this would be nice

---

### Post by smoker on 2008-04-28
> **LaRoza said:**
> Or girl, or her sig. ;)

yes! i apologise, guilty of careless presumptions:)

---

### Post by LaRoza on 2008-04-28
> **smoker said:**
> yes! i apologise, guilty of careless presumptions:)

Think of me as the Borg.

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]

---

### Post by TBOL3 on 2008-04-28
"Prepare to be assimilated.

Would you like a coke?"

Wow, I just realized, I started the second flame war in my life.

I'm sorry.

---

### Post by p_quarles on 2008-04-28
> **LaRoza said:**
> Think of me as the Borg.

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]
Shouldn't that be: "Think of *us* as the borg"? :)

---

### Post by LaRoza on 2008-04-28
> **p_quarles said:**
> Shouldn't that be: "Think of *us* as the borg"? :)

I am the collective. We are the Borg.

Resistance is futile. You will be assimilated into me.

(Data asked the same question, and got the same answer basically.)

---

### Post by smoker on 2008-04-28
> **LaRoza said:**
> Think of me as the Borg.

[IMG]http://www.freesmileys.org/smileys/alien003.gif[/IMG]

ah ha! so that's where you get the power from:
[http://ubuntuforums.org/showthread.php?t=773298](http://ubuntuforums.org/showthread.php?t=773298)
:)

---

### Post by schauerlich on 2008-04-28
A nice compromise might be a pseudo-GUI in the command line, similar to the alternate install disk or dpkg-reconfigure xserver-xorg interface.

---

### Post by bilal.17 on 2008-04-28
> **EDavidBurg said:**
> A nice compromise might be a pseudo-GUI in the command line, similar to the alternate install disk or dpkg-reconfigure xserver-xorg interface.
yeah that sounds like a good idea

---

### Post by LaRoza on 2008-04-28
> **EDavidBurg said:**
> A nice compromise might be a pseudo-GUI in the command line, similar to the alternate install disk or dpkg-reconfigure xserver-xorg interface.

That is called ncurses.

What would it look like?

I think it does use ncurses actually.

The last thing we want is a blue background (BSOD anyone?)

---

### Post by bilal.17 on 2008-04-28
> **LaRoza said:**
> That is called ncurses.

What would it look like?

I think it does use ncurses actually.

The last thing we want is a blue background (BSOD anyone?)

:lolflag: that brings back terrible memories

---

### Post by schauerlich on 2008-04-28
> **LaRoza said:**
> That is called ncurses.

What would it look like?

I think it does use ncurses actually.

The last thing we want is a blue background (BSOD anyone?)

Couldn't the background be pretty easily made a different color? Black, perhaps? And, a mockup:

> 
Occasionally, the file system needs to be scanned for errors. This process may take a couple minutes to complete if you have a large hard drive.

Would you like to proceed with this scan? If you choose to skip the scan, this screen will come up again the next time you start your computer.

[Proceed with scan]   [Skip scan for now]

Scanning the file system for errors...
[                        Progress Bar                                ] n%



The wording can be modified as needed, but something like that would be nice.

---

### Post by LaRoza on 2008-04-28
> **EDavidBurg said:**
> Couldn't the background be pretty easily made a different color? Black, perhaps? And, a mockup:

The wording can be modified as needed, but something like that would be nice.

It is black now. This is very trivial what you are suggesting. It is kind of silly.

---

### Post by schauerlich on 2008-04-28
> **LaRoza said:**
> It is black now. This is very trivial what you are suggesting. It is kind of silly.

It may not even need to have ncurses implemented. I think what's most concerning is that 10 or so lines fly by, and then this process starts halfway down the screen. A novice would be overwhelmed by this, think something is wrong, and not read it, just like a BSoD. Maybe having the only think show up be the fsck explanation/process with a Continue? [Y/n] option would suffice.

---

### Post by LaRoza on 2008-04-28
> **EDavidBurg said:**
> It may not even need to have ncurses implemented. I think what's most concerning is that 10 or so lines fly by, and then this process starts halfway down the screen. A novice would be overwhelmed by this, think something is wrong, and not read it, just like a BSoD. Maybe having the only think show up be the fsck explanation/process with a Continue? [Y/n] option would suffice.
Perhaps that is true. If it only said what was needed instead of the boot sequence that preceeds it.

(That is actually very easy to do, just call clrtobot() before doing the sequence)

---

### Post by init1 on 2008-04-28
> **LaRoza said:**
> Why not? It can be changed if you don't want it to do that.
But a beginner wouldn't know how.

---

### Post by LaRoza on 2008-04-28
> **init1 said:**
> But a beginner wouldn't know how.

A beginner should be doing that without understanding exactly what they are doing.

---

