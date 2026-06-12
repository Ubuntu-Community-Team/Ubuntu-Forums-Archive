---
title: "I'm sorry, but I have to gripe!"
date: 2010-08-12
forum: The Cafe
---

### Post by wizarddrummer on 2010-08-12
All afternoon, I used my computer without any problems at my friends house. 

I shut it down at around 10pm. It seemed that it took longer to shut down than normal. I then transported the computer home and hooked it up and  ubuWindows had a problem ... it just sat there during the boot.

Here's my gripe. You people have put together one very stellar operating system that I am thoroughly impressed with. It is really a wonderful piece of work with the exception of one small thing.

I am old school, I started messing with computers in the 70's with the IBM360 (card reader) took a small break and came back when PDP11's were in style. Started my Unix at System III. All of these systems told you what was going on during startup.

Then got into the Microcheese world and hated XP when it came out because it had these stupid caterpillar progress bars that didn't tell you squat about what was going on when it was starting up.

Now, the most recent version of ubuntu (ubuXP) has 5 stupid dots that just blink in succession alternating from white to red or the other way around. 

C'mon guys, 5 stupid dots that blink? I waited for 15 minutes for the OS to start and still had the 5 blinking dots. Normally it comes up in 30 seconds.

I HATE USELESS CATERPILLAR PROGRESS BARS AND BLINKING DOTS THAT DON'T TELL ME WHAT THE F*&K IS GOING ON!

THERE I HAVE SAID MY GRIPE.

I wish there was a switch / preference that you could set so that when ubuntu starts i don't see some stupid splash screen with dots but what's happening under the hood.

If XP has a problem with the file system at least it's crappy chkdsk program starts and you know that's its trying to repair something.

This happened once before about two weeks ago and then all of a sudden, when I booted it i saw a brief message about fsck and then it started to work without my intervention.

Yeeeeeeeeeeesh.

Microsoft has influenced computer development in the worst way with glitzy stupid graphics that do nothing except try to look pretty.

Thanks for listening.

have a good day all.

---

### Post by mendhak on 2010-08-12
But you could disable it, surely?

Open up /boot/grub/menu.lst and change

# defoptions=quiet splash
to
# defoptions=

I think it's [different in 10.04](http://my.opera.com/linuxonlinehelp/blog/ubuntu-10-04-disable-purple-boot-splash-lucid-lynx-usplash-plymouth-tty0) though.

---

### Post by Admiral Yi on 2010-08-12
> I wish there was a switch / preference that you could set so that when ubuntu starts i don't see some stupid splash screen with dots but what's happening under the hood.

There is. Stop being so angry about it and search google. If you've used *nix before you really should know that it's fully customisable and almost anything can be changed. A quick search will show you many ways to disable the splash screen. 

On 10.04, install startup manager, then open it up. On the first page there is a checkbox that says 'display splash screen'. Click the box so the tick is gone. Done.

---

### Post by inameiname on 2010-08-12
I second the use of startup manager. It's a marvelous thing.

sudo apt-get install startupmanager

---

### Post by wizarddrummer on 2010-08-12
> **Admiral Yi said:**
> There is. Stop being so angry about it and search google. If you've used *nix before you really should know that it's fully customisable and almost anything can be changed. A quick search will show you many ways to disable the splash screen. 

On 10.04, install startup manager, then open it up. On the first page there is a checkbox that says 'display splash screen'. Click the box so the tick is gone. Done.

My friend, you missed my whole point.

What I am trying to illustrate is that the more we progress it seems the less the users are informed.

I used the system then I shut the system down and when I rebooted the system all I got was dots blinking and no OS booting up.

What's it doing? Is it hung? Did it encounter an error? Is it doing a file repair? How am I supposed to know if all I see is dots?

This is my point. Yes I know that it is customizable. Yes, I could Google and disable the splash screen, BUT, that is not what is important.

If the OS has encountered an error and something is NOT working correctly then the end user that's looking at a screen full of blinking dots should have some kind of alert or message or something that tell them that there's a problem.

Does linux automatically repair file systems?

In grub, i see a recover what's that used for? Do you get a terminal window?

I suppose I'll have to get the CD and then tell it to repair the file system.

My question is why is this not done automatically? And if it is, why isn't the user notified.

It's not just ubuntu. Virtually every software design out there now has some kind of useless progress bar that does not tell you very much.

I don't hate or am not angry with ubuntu. I HATE the trend that provides less information.

---

### Post by t0p on 2010-08-12
The OP makes a good point.  If a problem arises during boot-up, a message could be displayed telling the user to press some key or other if he wants to know what's going on.  If the OP feels strongly about this, he could bring this to the attention of the developers.

Problem is, this is a support forum.  The OP ought to  send this message to the dev's mailing list or wherever it is they hang out.

---

### Post by Grenage on 2010-08-12
You're not the first to mention this, and you won't be the last; I also do not like it.  The fact that one can press Esc and view the 'real' loading, is what stops me getting too bothered.

---

### Post by philinux on 2010-08-12
OP,
The problem is with the application plymouth. when it does the file system check, fsck, it does display info, but it sounds like something else was going on and not fsck being run.

Raise a bug at launchpad.

```
ubuntu-bug plymouth
```

---

### Post by kamaboko on 2010-08-12
Hmmm...and I was concerned about a friend of mine who was diagnosed with cancer yesterday.  Flashing dots on a screen is certainly more threatening and annoying.

---

### Post by TBABill on 2010-08-12
kamaboko, that's a bit unfair when the OP was stating something completely legitimate about his OS that certainly merits discussion and consideration. Comparing the problem to what you stated above is ridiculous because there will always be someone with worse problems in life than our own if we search hard enough. I realize it was sarcastic, and I sure appreciate sarcasm, but to put it into a reference comparing it to someone diagnosed with cancer is insulting to the OP. 
 
To the OP, you raise a perfectly valid point. If your system will NOT boot, how would you be expected to disable the splash screen? That puts the burden on the user, who would likely only really think about needing to see the boot sequence when encountering a problem. Who cares about a few flashing dots when the system boots in 20 seconds? It's when it does NOT boot that you care, and often when the OS is at a point you cannot take any action like suggested if the system is borked.
 
I hadn't thought of the "what if" with Plymouth if something won't work and I need info to explain how far throug the boot sequence the machine is getting. I will disable mine now for this very reason. Thanks for bringing it up....perhaps a more gentle way of stating it would have prevented some of the responses you got, but such is life :)

---

### Post by LowSky on 2010-08-12
> **wizarddrummer said:**
> My friend, you missed my whole point.

What I am trying to illustrate is that the more we progress it seems the less the users are informed.
Have you thought that most users don't want to be informed they just want it to work, and from the business side they just want us to buy a new one when a consumer assumes it is broken. I'm not saying its ideal but its how things are.

> I used the system then I shut the system down and when I rebooted the system all I got was dots blinking and no OS booting up.

What's it doing? Is it hung? Did it encounter an error? Is it doing a file repair? How am I supposed to know if all I see is dots? 
Ubuntu does tell you if it is checking the disk, its not just blinking dots

> This is my point. Yes I know that it is customizable. Yes, I could Google and disable the splash screen, BUT, that is not what is important.  It isn't? You have a choice to have things the way you want.

> If the OS has encountered an error and something is NOT working correctly then the end user that's looking at a screen full of blinking dots should have some kind of alert or message or something that tell them that there's a problem.

Does linux automatically repair file systems? Ubuntu tries to fix file systems as long as you use a journalling file system. but if the computer hangs the user isn't going to know what happened. Hangs means that there is no data.

> In grub, I see a recover what's that used for? Do you get a terminal window? There are Tutorials to help with this.

> I suppose I'll have to get the CD and then tell it to repair the file system.

My question is why is this not done automatically? And if it is, why isn't the user notified.

It's not just Ubuntu. Virtually every software design out there now has some kind of useless progress bar that does not tell you very much.
Ubuntu does do disk checking and repairs, and does notify it when it does one. from the dot blinking screen

> 
I don't hate or am not angry with Ubuntu. I HATE the trend that provides less information.

This "trend" is decades old. Nearly every OS on nearly every electronic device has gone to pretty load screens instead of lines of code.

---

### Post by wizarddrummer on 2010-08-12
> **kamaboko said:**
> Hmmm...and I was concerned about a friend of mine who was diagnosed with cancer yesterday.  Flashing dots on a screen is certainly more threatening and annoying.

Sorry to hear about your friend. I was diagnosed with Pulmonary Fibrosis a killer disease and congestive heart failure about 17 months ago.

Cancer is more painful than lungs slowly changing to scar tissue. I feel no pain, it just gets harder to breath each day.

---

### Post by Mr. Picklesworth on 2010-08-12
There's one thing I like less than no progress bars: progress bars that don't actually work for showing progress.

The old progress bar during boot was essentially meaningless. There is no reasonable way to determine how far along the system is in starting up (in terms of percentages), so it's pointless to present it as if that can be done.

Unusual things (like disk checking) show up in the boot splash, and you can press *Esc* to bring up the very detailed text output.

---

### Post by JustinR on 2010-08-12
> **wizarddrummer said:**
> My friend, you missed my whole point.

What I am trying to illustrate is that the more we progress it seems the less the users are informed.

I used the system then I shut the system down and when I rebooted the system all I got was dots blinking and no OS booting up.

What's it doing? Is it hung? Did it encounter an error? Is it doing a file repair? How am I supposed to know if all I see is dots?

This is my point. Yes I know that it is customizable. Yes, I could Google and disable the splash screen, BUT, that is not what is important.

If the OS has encountered an error and something is NOT working correctly then the end user that's looking at a screen full of blinking dots should have some kind of alert or message or something that tell them that there's a problem.

Does linux automatically repair file systems?

In grub, i see a recover what's that used for? Do you get a terminal window?

I suppose I'll have to get the CD and then tell it to repair the file system.

My question is why is this not done automatically? And if it is, why isn't the user notified.

It's not just ubuntu. Virtually every software design out there now has some kind of useless progress bar that does not tell you very much.

I don't hate or am not angry with ubuntu. I HATE the trend that provides less information.

Ubuntu isn't focused on being the 'geeky' linux OS anymore. Its appearance is appealing to new linux users. No body wants to see what the computer is doing at startup - most users don't care. They want it to look nice. If you want know what it's doing during startup, go to /etc/default/grub and delete 'quiet splash' under the kernel line.

---

### Post by sydbat on 2010-08-12
To the OP - How did you install Ubuntu? The answer to this can help us help you figure out what might be going on. If it was via wubi (as a 'program' running virtually inside Microsoft Windows), then any corruption of the Windows file system could completely bork your Ubuntu install.

---

### Post by wizarddrummer on 2010-08-12
> **TBABill said:**
> kamaboko, that's a bit unfair when the OP was stating something completely legitimate about his OS that certainly merits discussion and consideration. Comparing the problem to what you stated above is ridiculous because there will always be someone with worse problems in life than our own if we search hard enough. I realize it was sarcastic, and I sure appreciate sarcasm, but to put it into a reference comparing it to someone diagnosed with cancer is insulting to the OP. 
 
To the OP, you raise a perfectly valid point. If your system will NOT boot, how would you be expected to disable the splash screen? That puts the burden on the user, who would likely only really think about needing to see the boot sequence when encountering a problem. Who cares about a few flashing dots when the system boots in 20 seconds? It's when it does NOT boot that you care, and often when the OS is at a point you cannot take any action like suggested if the system is borked.
 
I hadn't thought of the "what if" with Plymouth if something won't work and I need info to explain how far throug the boot sequence the machine is getting. I will disable mine now for this very reason. Thanks for bringing it up....perhaps a more gentle way of stating it would have prevented some of the responses you got, but such is life :)

Well, gentle is not in my vocabulary sometimes. I get edgy. None of us have been promised that we will be here tomorrow. It's up to God, but when you get news that your life is potentially much shorter than what you anticipated then you tend to get a little aggravated at things that waste time. If I was healthy and working and making lots of money and had a reasonably long life expectancy I couldn't care less. I try to do something with each minute of my day.

The reason I switched to ubuntu from XP is that i was tired of spending so many heartbeats trying to fix that pile of crap. Google windows annoyances and look a the number of results and you get what i mean.

I don't see dead people ... I see useless progress bars everywhere :)

---

### Post by wizarddrummer on 2010-08-12
> **TBABill said:**
> kamaboko, that's a bit unfair when the OP was stating something completely legitimate about his OS that certainly merits discussion and consideration. Comparing the problem to what you stated above is ridiculous because there will always be someone with worse problems in life than our own if we search hard enough. I realize it was sarcastic, and I sure appreciate sarcasm, but to put it into a reference comparing it to someone diagnosed with cancer is insulting to the OP. 
 
To the OP, you raise a perfectly valid point. If your system will NOT boot, how would you be expected to disable the splash screen? That puts the burden on the user, who would likely only really think about needing to see the boot sequence when encountering a problem. Who cares about a few flashing dots when the system boots in 20 seconds? It's when it does NOT boot that you care, and often when the OS is at a point you cannot take any action like suggested if the system is borked.
 
I hadn't thought of the "what if" with Plymouth if something won't work and I need info to explain how far throug the boot sequence the machine is getting. I will disable mine now for this very reason. Thanks for bringing it up....perhaps a more gentle way of stating it would have prevented some of the responses you got, but such is life :)

How eloquent. "If your system will NOT boot, how would you be expected to disable the splash screen?"

I missed that on the first go around.

Thank you.

---

### Post by kamaboko on 2010-08-12
> **wizarddrummer said:**
> Sorry to hear about your friend. I was diagnosed with Pulmonary Fibrosis a killer disease and congestive heart failure about 17 months ago.

Cancer is more painful than lungs slowly changing to scar tissue. I feel no pain, it just gets harder to breath each day.

I'm familiar with pulmonary fibrosis, not that I have it.  Damn, that is tough.  I have to ask, how old are you?  To the OP and those that have taken my comment as insulting, in the grand scheme of things flashing dots is really a non-issue.  Reinstall the OS if ya have to and call it good. Windows, Linux, Mac OS...nothing is bullet proof and all of them come with issues.  If one believes otherwise, they're living in LaLa land.

---

### Post by wizarddrummer on 2010-08-12
> **kamaboko said:**
> I'm familiar with pulmonary fibrosis, not that I have it.  Damn, that is tough.  I have to ask, how old are you?  To the OP and those that have taken my comment as insulting, in the grand scheme of things flashing dots is really a non-issue.  Reinstall the OS if ya have to and call it good. Windows, Linux, Mac OS...nothing is bullet proof and all of them come with issues.  If one believes otherwise, they're living in LaLa land.

I'm 59.


I will never again use the ext4 file system that I can tell you for sure. I will address that issue in a new thread. I'm sure many people will disagree with what I have to say about it. I'll probably post it later tonight.

---

### Post by ceref on 2010-08-12
> **wizarddrummer said:**
> All afternoon, I used my computer without any problems at my friends house. 

I shut it down at around 10pm. It seemed that it took longer to shut down than normal. I then transported the computer home and hooked it up and  ubuWindows had a problem ... it just sat there during the boot.

Here's my gripe. You people have put together one very stellar operating system that I am thoroughly impressed with. It is really a wonderful piece of work with the exception of one small thing.

I am old school, I started messing with computers in the 70's with the IBM360 (card reader) took a small break and came back when PDP11's were in style. Started my Unix at System III. All of these systems told you what was going on during startup.

Then got into the Microcheese world and hated XP when it came out because it had these stupid caterpillar progress bars that didn't tell you squat about what was going on when it was starting up.

Now, the most recent version of ubuntu (ubuXP) has 5 stupid dots that just blink in succession alternating from white to red or the other way around. 

C'mon guys, 5 stupid dots that blink? I waited for 15 minutes for the OS to start and still had the 5 blinking dots. Normally it comes up in 30 seconds.

I HATE USELESS CATERPILLAR PROGRESS BARS AND BLINKING DOTS THAT DON'T TELL ME WHAT THE F*&K IS GOING ON!

THERE I HAVE SAID MY GRIPE.

I wish there was a switch / preference that you could set so that when ubuntu starts i don't see some stupid splash screen with dots but what's happening under the hood.

If XP has a problem with the file system at least it's crappy chkdsk program starts and you know that's its trying to repair something.

This happened once before about two weeks ago and then all of a sudden, when I booted it i saw a brief message about fsck and then it started to work without my intervention.

Yeeeeeeeeeeesh.

Microsoft has influenced computer development in the worst way with glitzy stupid graphics that do nothing except try to look pretty.

Thanks for listening.

have a good day all.
You have every right to gripe .. I started out on binary then later DOS then corporate use of compulsory Windows ..... I love them there dots because the rare occaison in the past few weeks of starting to use Linux and specificly Ubuntu 10.04 Lucid I get fast clean boot ups and close downs. 

You are very lucky not to have suffered long long long long boot ups and hanging around for waiting like all "coffee break" for Vista, XP and deadly 7 to get fired up .. these dots are just a divine sight that tells me I am in charge of my machine at long last. 

Only Windows people go "dotty" because they do not have hard consistant high performance as we have with Ubuntu 10.04.   

I would like to thank all you long term Linux and in particular Ubuntu users as you have all helped to make the promised golden future computers were going to give us we were told many decades ago a reality. 

Thanks

---

### Post by marshmallow1304 on 2010-08-12
So we either have a few experienced users (who should be able to customize this kind of thing) complaining about not enough data during boot, or hordes of new users complaining about the lack of a bootsplash (ZOMG! It looks like DOS! Linux is not ready for the desktop!).

---

### Post by rotwang888 on 2010-08-13
Why not use Slackware?  They have stated they will never use any pretty graphical boot thingies.

---

### Post by smellyman on 2010-08-13
> **marshmallow1304 said:**
> So we either have a few experienced users (who should be able to customize this kind of thing) complaining about not enough data during boot, or hordes of new users complaining about the lack of a bootsplash (ZOMG! It looks like DOS! Linux is not ready for the desktop!).
 
bingo

---

### Post by Grenage on 2010-08-13
Basic trouble shooting text would be enough for most users.

I added a new drive to my machine, but when booting Ubuntu the screen just hung there with its flashing dots.  I'm not a 'complete' newbie, so I was able to guess that I'd thrown disc order out (an archive drive was using /dev/sdaX rather than a UUID).

Rather than loading without mounting the archive (which I've seen happen), or even giving me a message that said "disc *xxx* not found, the lights continued on.  Not the end of the world, but a trivial thing that can cause some users headaches.

---

### Post by everytimeref on 2010-08-13
Anyone know why when I boot and it does a periodic disk check I get the Ubuntu Studio(!) disk check screen. ( I also see studio screens v briefly when I shut down ).

It's not really a problem, I'm just curious...

When 10.10 is launched I'm planning on doing a fresh install. It's just that it's pain to do that when you actually *use *your PC.

---

### Post by murderslastcrow on 2010-08-13
You hate the five dots, eh? Just look at a Mac- they only have one swirly thingy in the middle. Pain in the butt, I tells ya'.

---

### Post by Paqman on 2010-08-13
The information is still there, it's just obscured. For 99% of users that's the correct design choice, so should be the default. I think the OP should recognise that what he wants is a bit obscure, and that he shouldn't whinge about having to do a very minor piece of tweakage to get the system to show him what he wants. 

In fact, he should probably be glad he's using a system that makes that kind of change so easy to do...

---

