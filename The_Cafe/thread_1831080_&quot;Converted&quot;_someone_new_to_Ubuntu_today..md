---
title: "&quot;Converted&quot; someone new to Ubuntu today..."
date: 2011-08-22
forum: The Cafe
---

### Post by ninjaaron on 2011-08-22
.. and it wasn't even my mom. :P

Course, this girl happened to be running a machine with Vista on it, so it was like offering a glass of water to someone in hell.  It was taking her computer like three or four minutes to boot, and it was booting to like 1.3GB of RAM from a cold start.

Hardware was all compatible with Ubuntu right away, so that was good.  We didn't actually test the mic, webcam, or headphone jack, so there may be surprises in the future.  She's not a gamer and she doesn't do heavy graphic or video editing.  The only bumpy spot may be that she's an MS Word power-user.  LibreOffice can pretty much do all the same stuff (and more), but it's a new system to learn.  We'll see how it goes.

She's already sold on the system because it's so much faster, but I don't think she'll be wiping windows any time soon.  I put Ubuntu on a rather small partition (12 GB), but  I modified /etc/fstab so it would load her windows partition automatically to a folder inside her home folder, and she's making shortcuts to all the folders with her personal files so she can use the same folders for data on both sides.

I set her up with flash aid in firefox immediately so she wouldn't have to see how crippled the default flash is on linux.  Also put in flashgot, and she was excited about that, since flash is still a piece of crap and it's much nicer to watch the videos offline with no buffering and VLC, which is much more efficient than a flash container.

What else... installed Faenza and Ubuntu Tweak immediately (the latter mostly for the good, GUI based system cleanup tools, since she is working with a small partition)...  Edited the Grub config file to force active power regulation, which improves power usage by 30%, since it's a laptop, and it already gets hot [edit: this generated some interest in the comments.  It's actually called, "Active-State Power Managemnet." more [here]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")].

Told her how to get support from #ubuntu IRC channel on freenode...  told her about the Bible tools for linux (we're graduate students in Biblical studies).  She was excited about this, since she doesn't have any on Windows.

Installed Skype... didn't set up any other chat, broadcast or email accounts.  She said she prefers to do that stuff through her browser.  It's her party, I guess.

Did I miss anything?

---

### Post by dniMretsaM on 2011-08-22
Sounds like you set her up pretty good!  You might show her the LibreOffice guides on [this](http://www.libreoffice.org/get-help/documentation/) page to help her get started.

---

### Post by 1roxtar on 2011-08-22
I love stories like this.  I am in the process of doing pretty much the same thing for a friend of mine.  She has a decently spec'd Dell desktop that is about 4 years old.  She is a single Mom with a minimal budget.  She wants a new computer because her kids complain that their machine is too slow.  I checked out her computer and told her that a simple gig upgrade to her Ram would help her a lot.  

I have been telling her about Ubuntu for a while now and had her check out the Ubuntu website.  She is intrigued and I told her I'd add the extra memory as a gift.  While I "work" on her computer, I'm giving her a loaner desktop with Ubuntu 11.04 installed and told her I'd give her a few days for her and her kids to play with.  I told her I'd then see if they wanted to give Ubuntu a chance on their own computer.  I'll let you know what happens in a couple of days.  ;)

---

### Post by ninjaaron on 2011-08-23
> **dniMretsaM said:**
> Sounds like you set her up pretty good!  You might show her the LibreOffice guides on [this](http://www.libreoffice.org/get-help/documentation/) page to help her get started.

I might just do that.  I can probably help her with most stuff.  I've been using OpenOffice since I started college six years ago (in grad school now... not one of 'those' people), and I already sent her a template I created a while back that with all of the special formatting that is typical in our discipline (basically Chicago style with some tweaks designed to make people go crazy).

But it still looks like there might be some good stuff over there, so I'll pass it along (might even give it a shot myself).

---

### Post by Megaptera on 2011-08-23
Hi and thanks for sharing! I use a laptop so will look into active power regulation.

---

### Post by Oxwivi on 2011-08-23
> **ninjaaron said:**
> Edited the Grub config file to force active power regulation,

What exactly is that? Link to info about it, and how to apply, please?

> **ninjaaron said:**
> Installed Skype... didn't set up any other chat, broadcast or email accounts.  She said she prefers to do that stuff through her browser.  It's her party, I guess.

You can sign into Skype online using [imo.im]("http://imo.im/").

---

### Post by anaconda on 2011-08-23
office 2007 works well in wine

so if she doesnt like libreoffice there is a choice

---

### Post by ninjaaron on 2011-08-23
> **Megaptera said:**
> Hi and thanks for sharing! I use a laptop so will look into active power regulation.

> **Oxwivi said:**
> What exactly is that? Link to info about it, and how to apply, please?

I guess it's actually called "active-state power management."  Sorry for misslabeling!

[Fix from Webupd8]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

> You can sign into Skype online using [imo.im]("http://imo.im/").She used Skype locally on Windows.  I dunno.  She's the boss, I guess.

> **anaconda said:**
> office 2007 works well in wine

so if she doesnt like libreoffice there is a choiceDoes it?  I've always had trouble doing anything with Wine, but I did tell her it was possible, and that if it didn't work, there was always crossover, which would definitely work.

---

### Post by ninjaaron on 2011-08-23
> **1roxtar said:**
> She is intrigued and I told her I'd add the extra memory as a gift.  While I "work" on her computer, I'm giving her a loaner desktop with Ubuntu 11.04 installed and told her I'd give her a few days for her and her kids to play with.  I told her I'd then see if they wanted to give Ubuntu a chance on their own computer.  I'll let you know what happens in a couple of days.  ;)

He...  I got some people using Ubuntu like this once.  I had an old laptop that had stopped working, and then it magically started again one day but I had already replaced it, and had no use for it at all, so I did a fresh install of Ubuntu on it and gave it to someone with an even more messed up laptop than that.

It's easy to get people using Linux when you start giving away hardware.:P

They were total hippies also, so I was able to sell them on some softer Stallman rhetoric as well (which is funny, since I think he's kinda a nutter).

---

### Post by don_quixote on 2011-08-23
> **ninjaaron said:**
> Does it?  I've always had trouble doing anything with Wine, but I did tell her it was possible, and that if it didn't work, there was always crossover, which would definitely work.

As I have to use Word 2007 for work (document compatibility in LO or OO just isn't there yet), I can confirm that most Office applications install without a problem and even allow for some, but not all, VB capability.

---

### Post by Oxwivi on 2011-08-23
> **ninjaaron said:**
> [Fix from Webupd8]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

Ah, the ASPM workaround. Hope they fix kernel bug soon...

---

### Post by XubuRoxMySox on 2011-08-23
> **ninjaaron said:**
> .. 
Hardware was all compatible with Ubuntu right away, so that was good.  **We didn't actually test the mic, webcam, or headphone jack**...

Oops. 

Kinda contradictory to say "all compatible" if you didn't actually *test* "all" the hardware. 

That is where Linux falls short most often, in hardware compatibility! So it's always better to test *everything* using the LiveCD before installing any Linux distro. 

Ubuntu really shines among distros for it's compatibility with a wide range of hardware, but installing it for a new user without testing all the hardware is a high-risk move, especially if you're hoping to "convert" them to Linux.

-Robin

---

### Post by ninjaaron on 2011-08-23
You've got a point there.  She said she doesn't use the webcam anyway, and I've installed Ubuntu on a fair number of machines and the only one where the webcam didn't work was a Mac, for obvious reasons.  I have had sound issues on a couple of machines, but those had newish hardware.  This computer is a few years old, and it's mostly low-end hardware (decent video card though), so I don't anticipate a problem.

But you're right, I should have checked it.  I'll tell her to test it today so we can get any issues out of the way before she tries to use it to talk to her grandma or something.

---

### Post by Megaptera on 2011-08-23
Thanks for the link to Webupd8, appreciated!

---

### Post by dniMretsaM on 2011-08-23
> **ninjaaron said:**
> I might just do that.  I can probably help her with most stuff.  I've been using OpenOffice since I started college six years ago (in grad school now... not one of 'those' people), and I already sent her a template I created a while back that with all of the special formatting that is typical in our discipline (basically Chicago style with some tweaks designed to make people go crazy).

But it still looks like there might be some good stuff over there, so I'll pass it along (might even give it a shot myself).

Yeah they're pretty nice. I've recommended them to a few people.

---

### Post by forrestcupp on 2011-08-23
> **don_quixote said:**
> As I have to use Word 2007 for work (document compatibility in LO or OO just isn't there yet), I can confirm that most Office applications install without a problem and even allow for some, but not all, VB capability.
I haven't looked into it for a very long time, but you used to have to jump through a lot of hoops to get Office 2007 to install properly in Wine. Does it now install normally without workarounds in the latest version of Wine?

One thing to keep in mind is that while most parts of MS Office can work with Wine, Access will not work with Wine or Crossover or anything in Linux other than a VM running Windows.

---

### Post by anaconda on 2011-08-25
office 2007 installs in wine without problems.

Doesnt even have to be the newest wine. the wine in ubuntus repositories work well.

and yeah. Both Word and Exel work very well. Havn't tested the other programs much.

The most recent office pack may be harder to get working, but with office 2007 you wont have problems

---

### Post by DangerOnTheRanger on 2011-08-25
I love it when people are converted to Ubuntu! It means more people for me to talk to on UF! :)

I'll chip in with my own little success story: Guess what my mother (who converted to Ubuntu) said when she had to use a Windows XP computer?

> 
*sigh* I hate Windows. Can you install Ubuntu on this computer?
Mission accomplished. :) And don't worry, I own said PC, I just hadn't installed Ubuntu on it yet.

---

### Post by ninjaaron on 2011-08-25
Update:

Checked all of her hardware, and it works.  Her computer actually has some massive hardware problems which Ubuntu does not fix (the screen does really strange thing, the volume knob is nuts, and sometimes it freezes when the system is going down).

So far, she hasn't booted windows since the install.  I was playing around, and I changed something in the BIOS that made Ubuntu boot much faster for some reason, so I went to check and see if Windows was any faster.

And I got the blue screen of death.  I was super scared that Ubuntu had killed Vista (not that Vista didn't have it coming).  While she wasn't thrilled at this prospect, she said it really wouldn't be such a horrible thing if Vista never came back, since all of her files were available through Ubuntu, and Vista had actually done this before with no help from Ubuntu.

I ran the startup recovery tool in Windows, and it worked (at least something works well!).  Vista is back, and Ubuntu is faster than ever with the BIOS tweak.

All is well, except for the fact that the hardware is teetering on the edge of usability.  She's extremely impressed with Ubuntu so far, and keeps on mentioning how it doesn't make sense that a free operating system can be so much smarter and better than Windows (which is still something I think about all the time).  The real question is if she is impressed enough with it to install it herself when she gets a new system with Windows 7 that actually works.  She is very smart and is fully capable of installing Ubuntu (which isn't really a strong measure of intelligence), but she is extremely lazy when it comes to maintaining her computer, and not like me, who has a seperate partition set aside just to try other distros for my idea of "fun."

Now that she's sufficiently impressed with the way it operates, I should probably start piping her a little FOSS ideology to seal the deal.  Works for me.  While usability is by far the most important thing, a little FOSS love goes a long way to get me through some of the *rough** patches***. (WORST JOKE EVER):lolflag:

---

### Post by dniMretsaM on 2011-08-25
> **ninjaaron said:**
> Now that she's sufficiently impressed with the way it operates, I should probably start piping her a little FOSS ideology to seal the deal.  Works for me.  While usability is by far the most important thing, a little FOSS love goes a long way to get me through some of the *rough** patches***. (WORST JOKE EVER):lolflag:

:lolflag::lolflag::lolflag:

Ok, anyway, sounds like you've done pretty good on this conversion! It's great that all the hardware is compatible, and it's great that she's willing to install it herself over Win7 when she gets a new computer. My mom has this idea in her head that everything I do with my computer is hard. From installing Ubuntu in the first place to running my web browser. Granted I have made some major tweaks to the interface (like removing the forward/back buttons, that really confused her), but it's still not that hard. Anyway, in her mind Ubuntu is only for people who are really technologically literate. I don't really know where she got this idea since she's never used it for more than two minutes, but it's still there. My dad thinks the same thing and he's good with computers. It's just annoying to me that people get this idea in there head and refuse to give it a chance.
/rant

Again, congratz on the conversion!

---

### Post by Famicube64 on 2011-08-25
I would be so angry if someone did this to my computer.

---

### Post by sanderd17 on 2011-08-25
> **Famicube64 said:**
> I would be so angry if someone did this to my computer.

I suppose it was done in agreement with each other. 

I also switched our family computer to Linux (Mint to be precise). Install progams you think they need, mount the Windows drive somewhere and use symlinks to point their images, documents etc to the right windows folders.

And they are quite happy with it. I put it as the default GRUB option, it's about 10 months ago and they didn't even once boot up Windows again. But I think I should do some maintenance, it's a long time ago since I upgraded packages.

---

### Post by ninjaaron on 2011-08-25
> **dniMretsaM said:**
> :lolflag::lolflag::lolflag:

Ok, anyway, sounds like you've done pretty good on this conversion! It's great that all the hardware is compatible, and it's great that she's willing to install it herself over Win7 when she gets a new computer.

Thanks!

But she didn't actually say that.  I was questioning whether that would be the case, since Windows 7 is actually a reasonably good OS for the average user, and she is very, very lazy.

---

### Post by sanderd17 on 2011-08-25
> **ninjaaron said:**
> Thanks!

But she didn't actually say that.  I was questioning whether that would be the case, since Windows 7 is actually a reasonably good OS for the average user, and she is very, very lazy.

Once you are used to Linux, it's hard to return to a world without choice.

---

### Post by ninjaaron on 2011-08-25
> **Famicube64 said:**
> I would be so angry if someone did this to my computer.
I would be too, but I'm a nerd, and I take charge of my own system.  She's some girl from school who doesn't tinker and doesn't want to fix stuff herself.

She asked me to work on her computer, which was total wreck.  I told her that it would be much faster with Ubuntu, and she said anything would be an improvement on the current setup.  The hardware is still a wreck, but the software is no longer compounding the problem.  There was a brief windows startup scare, but it wasn't the first time, and may have had nothing to do with me or Ubuntu, and I fixed it (or rather, it basically fixed itself with a few well-placed clicks).  The only foreseeable problem is, since the computer is running so much faster, now the machine is a high-speed wreck, where it was previously so slow that there was little possibility of injury :D  (on a bad-joke roll tonight!)

tl;dr:
She asked me to work on her **** computer.  I suggested that Ubuntu would fix some of the problems.  She agreed to try it.  It fixed some of the problems.  She is happier (it's still a pile of ****).

---

### Post by kaldor on 2011-08-25
> **ninjaaron said:**
> tl;dr:
She asked me to work on her **** computer.  I suggested that Ubuntu would fix some of the problems.  She agreed to try it.  It fixed some of the problems.  She is happier (it's still a pile of ****).

To a certain other forum, installing Linux on someone else's computer means you're a zealot. 

/me ducks

Edit:

> **Famicube64 said:**
> I would be so angry if someone did this to my computer.

The guy already said the person agreed. No need to try to show off for upcakes.

I'll just shut up about this now.

---

### Post by ninjaaron on 2011-08-25
> **kaldor said:**
> To a certain other forum, installing Linux on someone else's computer means you're a zealot. 

While I'm not against closed-source, proprietary software, and it definitely has some benefits, I definitely think FOSS as a movement is something that is worth a little active support.  This may seem kinda weird, since I am a die-hard supporter of the free-market, but it sort of comes down to the fact that I don't want the state regulating intellectual property (or a great many other things).  The success of FOSS would subvert the idea that intellectual property laws are necessary to promote progress.  It also subverts the idea that community values and ecosystems need to be organised by the government.  Enlighten people are perfectly capable of function as a community without government intervention, and tend to do so with much greater efficiency.  It's not that I don't want to share, It's just that I want to do so by choice, like free as in freedom.

On the other hand, I'm enough of a pragmatist to recognise the shortcomings of FOSS at the present, and do not feel that it is contradictory to use the best tools for the job while generally supporting the FOSS movement.

And finally, I'm an observant Christian, so being labelled as a zealot by internet dorks is nothing new.

ps- now wondering if this post is"religious/political" enough to get the thread locked down.  Everything here is FOSS related, so I guess it complies with the CoC, but that will be up to the staff, I suppose.

---

### Post by sanderd17 on 2011-08-25
> **ninjaaron said:**
> 

ps- now wondering if this post is"religious/political" enough to get the thread locked down.  Everything here is FOSS related, so I guess it complies with the CoC, but that will be up to the staff, I suppose.

I was tempted to talk about politics, but just able to resist :P

---

### Post by ninjaaron on 2011-08-25
> **sanderd17 said:**
> I was tempted to talk about politics, but just able to resist :P

Well, the thread sort of had it's 'productive discussion phase' and was starting to drift into ideological rants anyway, so if it gets locked, it's no skin off my back (and I support this action, as ubuntuforums are private property, and the proprietors have every right to control the content thereon :D).

---

### Post by keithpeter on 2011-08-25
> **ninjaaron said:**
> I might just do that.  I can probably help her with most stuff.  I've been using OpenOffice since I started college six years ago (in grad school now... not one of 'those' people), and I already sent her a template I created a while back that with all of the special formatting that is typical in our discipline (basically Chicago style with some tweaks designed to make people go crazy).

Zotero? Firefox add-in for academic referencing? Synchronised notes on references, export/copy to clipboard in a variety of formats including Chicago (and my pet hate, Harvard).

Apologies if I am stating the obvious. You seem to have most bases covered.

---

### Post by ninjaaron on 2011-08-25
> **ninjaaron said:**
> Well, the thread sort of had it's 'productive discussion phase' and was starting to drift into ideological rants anyway.
> **keithpeter said:**
> Zotero? Firefox add-in for academic referencing? Synchronised notes on references, export/copy to clipboard in a variety of formats including Chicago (and my pet hate, Harvard).

Apologies if I am stating the obvious. You seem to have most bases covered.

I stand corrected sir!  I have used Zotero in the past, but support for it in the newer versions of firefox seemed to have dropped off for a while, so I had stopped using it. Just checked in FF6, and it appears they are back in business.  I get the feeling she might be too tech-lazy to use this kind of thing, but I will pass it on, and I will certainly use it myself!

Thanks again!

---

### Post by XubuRoxMySox on 2011-08-25
[My favorite "conversion" story]("http://www.linuxforums.org/articles/non-geeky-girls-love-linux-too-_368.html")!

---

### Post by Megaptera on 2011-08-25
> **dixiedancer said:**
> [My favorite "conversion" story]("http://www.linuxforums.org/articles/non-geeky-girls-love-linux-too-_368.html")!

Amy (in that link) has your writing and grammar style too - are you connected to that story other than (I think) being "Robin"? :confused:

---

### Post by ninjaaron on 2011-08-25
I puked in my mouth a little, but good for her.

---

### Post by KiwiNZ on 2011-08-25
> **ninjaaron said:**
> I puked in my mouth a little, but good for her.
 
 this thread has reached an end
 
Closed

---

