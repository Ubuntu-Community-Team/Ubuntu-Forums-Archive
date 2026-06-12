---
title: "Farewell Linux and Ubuntu"
date: 2009-01-09
forum: Testimonials &amp; Experiences
---

### Post by pengo_au on 2009-01-09
I'd like to thank the many paid and unpaid open source developers who made Linux possible (or in Stallmanese: thanks to the Free Software geeks who made GNU/Linux possible) and those who have worked tirelessly to create a free operating system and support it. However, I bid ye all a farewell, as I cannot stand to use it any more and am not planning to come back any time soon.

This is not a troll, this is a partial list of problems I've had with Ubuntu Linux over the past year of using it almost every day on my Lenovo X61, and why I have finally bit the bullet and reinstalled Windows. (I compiled this list after a friend asked why I'd stopped using Linux. I didn't think it would be quite as long as it turned out. But I thought it might be of interest to someone here.) My computer is in the ThinkPad family, which I believed to have a reputation for good Linux support. It also has fairly good support documentation on thinkwiki.org (an excellent site for ThinkPad owners), but this only helps so much.

Backlight brightness control stopped working (this was a last straw issue and I didn't bother to investigate why), thumbprint reader overheats (I fixed it once, but couldn't be bothered going through it again after upgrading Ubuntu), computer always overheating and fan never turns off (possibly fixable too with some work but no simple solution), dual screen support shitty (slowly improved over 2 major Ubuntu upgrades, but got worse at one point when fn-F7 no longer let me jump back to single screen mode. very annoying if you've just detached from an overhead projector and lost half your screen), colour management impossible to set up, poor support for my video card, I use adobe products which run slower in VirtualBox. GIMP (which I do use often enough) DOES NOT HAVE THE SAME FEATURES AS PHOTOSHOP NO MATTER HOW MANY TIMES YOU SAY IT DOES. Ubuntu makes you enter your admin password/fingerprint too often and sometimes for trivial things. Nothing on Ubuntu Brainstorm is ever implemented except by accident. Software updates come only once per 6 months, meaning you run old versions software much of the time unless you manually install software which defeats the whole purpose of a centralised software updater. Frequent crashes (Really? In Linux?! Yes.) I want to actually use my computer sometimes and not spend my life fixing known regressions. 

The only user-friendly partition manager (gparted) takes several minutes to refresh the list of drives (which you often do a number of times when repartitioning external drives), most tv tuner cards/dongle not supported, my webcam not supported, spyder not supported, bluetooth mouse worked once upon a time but can't be set up within the gui nor the command line tools any more, ntfs drives which weren't unmounted cleanly cannot be mounted at all, have to use terminal to type "sudo gedit /etc/..." instead of double clicking because Nautilus is too stupid to ask for a root password (and the root-mode plugin seems to not work or uninstall itself or be useless I'm not sure which), conflicting audio subsystems, audacity never plays audio, Flash runs slowly, increasing font size is a million times slower in Firefox on Linux than windows.

Virtual screen arbitrarily limited to 2048 x 2048 with Compiz Fusion. Compiz Fusion takes 2 hours to configure to be usefully usable and not all features work with the poor video driver for my card, and it conflicts with OpenGL applications and plays poorly with video (overlay) applications (maybe these issues were fixed 2 years ago too but not on a default Intreped install). Google Earth runs poorly. There should be separate login and password fields on the login screen (old usability bug). Can't send faxes. No user notification when an unknown device (USB) is connected. Camera remote control over MTP/PTP (eg for Nikon DSLR) is difficult and clunky to use (via gphoto2). Rotating the screen crashes the system. And most useful Linux applications are available for Windows anyway.

Audio dies after suspend or hibernate (although it once worked). Audio too quiet (need to manually load alsa-mixer to get volume high because default control doesnt go high enough. Windows is louder still for some reason). Doesn't always wake up from suspend. Incredibly slow to suspend/hibernate (XP is almost instant). Poor integration with GRUB (e.g. Shouldn't allow choosing a new option when waking from hibernate), difficult to configure display of system status on taskbar thing (CPU usage, CPU scaling, network, HDD) without it taking over half the bar and looking ugly as hell (I dont need this in windows as much because my CPU isn't always overheating and scaling down), gui preferences/system admin configuration is organised horribly, boot time is very long, as is shutdown time, mounting ISO images from Nautalis does something stupid (adding ;1 to the end of filenames), unmounting all partitions on a single device is difficult, too easy to screw up (e.g. with rm), forced Fsck at startup (supposedly a fixed issue, but kept happening to me still until I disabled it manually on my drive), hard drive fall/drop protection not supported or difficult to set up.

Basically a few minor hardware compatibility issues. Now, after a year of Linux, I'm running XP on the same machine, and for the first time in my life that windows startup sound doesn't sound so bad. By the way, if you think I'm a noob, I'm not. I'm just annoyed and cannot be bothered any more with trying to get Ubuntu to work when it doesn't (i.e. see above list). Some of the problems may be annoying or even fixable, but many are not.

I'm aware there are workarounds for many of these issues. Sometimes these workarounds have been around for years. Which is exactly what makes it so frustrating to use Linux -- having to go through a dozen steps in the terminal to fix an issue that you already fixed the last time you upgraded (e.g. scrolling with the nub has required had to be setup after installing and after each major upgrade, and even completely changed files that needed editing. Likewise, the thumbprint reader overheats whether or not you've used it or even installed drivers for it and this goes back after an upgrade. The well documented fix never seemed to have found its way to the distributions), or trying to find a image viewer that supports both pre-loading of the next image (and why on earth doesn't the default viewer?) and a raw camera format you need, only to discover your favourite viewer already supported it 2 years ago just no one ever bothered to update the repositories with the new version (GQview). 

The only thing I use Ubuntu or Linux for now is as a Live CD to give friends who need an OS until they get their broken Windows box running again.

Keep up the good work, and I might see you on the desktop in another decade.

P.S. ext2fsd works great for accessing ext2/3 partitions from within Windows, so I'll be still keeping a large EXT2 partition all the same.

---

### Post by SupaSonic on 2009-01-09
I think this should be in Testimonials.

---

### Post by glotz on 2009-01-09
Nice troll, now go back under the bridge!

Note the post count people and please do feed him.

---

### Post by yaztromo on 2009-01-09
> **glotz said:**
> Nice troll, now go back under the bridge!

Note the post count people and please do feed him.

Every testimonial which doesn't praise the God Ubuntu gets branded a troll on here.

---

### Post by Sealbhach on 2009-01-09
I'd be worried about stuff like this if he had bought a machine preloaded with Ubuntu.

Otherwise, it's the luck of the draw. Also, the Photoshop/GIMP thing... probably true but how many users would actually find this a deal-breaker?


.

---

### Post by handy on 2009-01-09
pengo_au may or may not have done better under Arch with its rolling release upgrade system & more up to date versions of software?

[quote=Sealbhach]
Otherwise, it's the luck of the draw. Also, the Photoshop/GIMP thing... probably true but how many users would actually find this a deal-breaker? [/quote]

I agree with your luck of the draw hardware statement, & personally I don't have a use for Photoshop/GIMP. ;-)

---

### Post by pengo_au on 2009-01-09
Why would someone use Linux for a year just to troll? I've been active on ubuntu brainstorm, and even helped people on some occasions in #ubuntu on freenode. This is my experience, I'm sharing it with you. If you're not interested, then ignore it.

---

### Post by Sealbhach on 2009-01-09
> **pengo_au said:**
> Why would someone use Linux for a year just to troll? I've been active on ubuntu brainstorm, and even helped people on some occasions in #ubuntu on freenode. This is my experience, I'm sharing it with you. If you're not interested, then ignore it.

Well, hope you have a more enjoyable time with Windows. Bye.


.

---

### Post by picturefreedom on 2009-01-09
oh don't be a sisy, comm'n reveal your old forum  handle. :)
have atleast the balls to say goodbye on your regular account.

---

### Post by jonfenton on 2009-01-09
I recently got frustrated with Ubuntu and reinstalled XP. It was a breath of fresh air at first but after a few months I realised why I got rid of it in the first place and now I am back on Ubuntu. That grass is not always greener and I think the perfect operating system has yet to be written.

---

### Post by Coffee3133 on 2009-01-09
To quote a friend:

> ELBSAK

Nuff said.

---

### Post by Nickedynick on 2009-01-09
I hope the devs take not of this post and others like it. It's one thing being a troll and telling everyone that Linux sucks, but this guy has obviously had a lot of problems - we should be working to counter things like these happening.

---

### Post by gn2 on 2009-01-09
Yawn.

---

### Post by tariquepark on 2009-01-09
to the OP, i understand your frustration but i think your being just a little picky. Most of the issues you listed are fairly common with laptops in general however i have installed Xubuntu on two X61's and faced a couple of the same problems. I must say though i found all fixes and workarounds on these forums withouteven needing to ask a question and have not had any problems since.
i think people in general get the wrong impression when changing OS's to ANY Linux distro.Its not that Linux is better but it gives you options and the power to make the system function as YOU want it to. Unfortunately it means you sometimes have to get your hands dirty to achieve the required results. 
Always remember INFORMATION IS POWER
:)

---

### Post by SteveHillier on 2009-01-09
Don't whinge about having to type in the admin password too many times.  Get yourself Vista and you will spend most of your time typing in the admin **username** and password.
Even with just the password Linux is more secure than Vista with all its so called security enhancements!

---

### Post by ratmandall on 2009-01-09
tl;dr

---

### Post by Coffee3133 on 2009-01-09
> **pengo_au said:**
> I'd like to thank the many paid and unpaid open source developers who made Linux possible (or in Stallmanese: thanks to the Free Software geeks who made GNU/Linux possible) and those who have worked tirelessly to create a free operating system and support it. However, I bid ye all a farewell, as I cannot stand to use it any more and am not planning to come back any time soon.

I am a little curious...  If I were invited over to a friend's house for dinner, and when I got there and ate.  I thanked him for inviting me over for dinner, but then on with a litany about how bad his cooking is... how do you think that friend would think of me?

> **pengo_au said:**
> I use adobe products which run slower in VirtualBox.

Had it ever occured that using virtual box uses a virtualized filesystem, which can cause massive CPU/Drive usage which has the possibility of being very evil in the ways of heat buildup. (especially in laptops.)

> **pengo_au said:**
> GIMP (which I do use often enough) DOES NOT HAVE THE SAME FEATURES AS PHOTOSHOP NO MATTER HOW MANY TIMES YOU SAY IT DOES.

GIMP in fact has MORE features than photoshop, but you have to take the time to learn them.  A help file is nice to read and worse comes to worse doing a bit of research can solve most problems.

Then again we live in a fast-food world where if we don't get the instant double-deluxe super belly buster burger in two seconds, we are normally complaining because the frys aren't lava hot.

> **pengo_au said:**
> Ubuntu makes you enter your admin password/fingerprint too often and sometimes for trivial things.

Oh so you want a system that has less security?  I guess you don't do much online shopping.

> **pengo_au said:**
> Software updates come only once per 6 months, meaning you run old versions software much of the time unless you manually install software which defeats the whole purpose of a centralised software updater.

That little red arrow pointing down is for updates, and you can cause it to manually come up anytime you wish by going to System > Administration > Update Manager.  I would be a little shocked if you never ran an update in 6 months time by doing this.

> **pengo_au said:**
> Frequent crashes (Really? In Linux?! Yes.) I want to actually use my computer sometimes and not spend my life fixing known regressions.

Linux is the most popular server software on the market because of 1. it's stability and 2. it's price.  I think you are having severe hardware issues or again, ELBSAK.

IN conclusion,  the transition to linux took me a while.  But once I made it, I understood how much more stable and better things were.  Truthfully you may be exepriencing that one in a million chance that your hardware configuration is not set up to run linux.  However, I feel it's just a question of impatience on wanting things to run exactly like windows only for free and the status value of saying "I run linux." without actually taking the time to learn it.

We will miss inexperienced users and are sad to see you go.

Now where's my belly-buster burger and I said I wanted a strawberry shake!

~Coffee

---

### Post by sn0m on 2009-01-09
Well, I feel sorry for you leaving linux. Maybe next time, if you ever decide to come back to linux, buy a linux certified hardware.
I have a dell inspiron that runs ubuntu and never had any of your problems.:(
Good luck.
Sokol

---

### Post by jeyaganesh on 2009-01-09
If Camera companies release their software for Linux, lot of people come to Linux.:D

---

### Post by Eisenwinter on 2009-01-09
Goodbye, Linux is not for everyone.

---

### Post by etnlIcarus on 2009-01-09
I'd say 33% of the op's complaints are perfectly valid, 33% aren't directly related to Ubuntu/linux itself or just seem like petty whinges and the other 33% of the time, he just has unrealistic expectations: it's linux - you're going to have to tinker sometimes.

---

### Post by pelle.k on 2009-01-09
> i'd say 33% of the op's complaints are perfectly valid, 33% aren't directly related to ubuntu/linux itself or just seem like petty whinges and the other 33% of the time, he just has unrealistic expectations: It's linux - you're going to have to tinker sometimes.
+1

---

### Post by SomeGuyDude on 2009-01-09
> **etnlIcarus said:**
> I'd say 33% of the op's complaints are perfectly valid, 33% aren't directly related to Ubuntu/linux itself or just seem like petty whinges and the other 33% of the time, he just has unrealistic expectations: it's linux - you're going to have to tinker sometimes.

Sounds about right.

Although, I wonder how many of these issues are just due to Ubuntu not particularly liking his hardware. Everyone seems to forget that when we talk about Linux v Windows, 99% of the time people are comparing a Windows system made specifically for a given machine against an installation of Linux that isn't. So when your display needs tweaking or this or that button on the keyboard doesn't work right, realize that the generic ISO is a lot different than preloaded.

Now, if you bought a Dell with Ubuntu on it and the audio didn't work right or it couldn't recognize your touchpad, THEN we'd have trouble, but otherwise you have to just acknowledge that there's no guarantee when dealing with an OS that isn't tailored to your computer.

---

### Post by BigSilly on 2009-01-09
> **jonfenton said:**
> I recently got frustrated with Ubuntu and reinstalled XP. It was a breath of fresh air at first but after a few months I realised why I got rid of it in the first place and now I am back on Ubuntu. That grass is not always greener and I think the perfect operating system has yet to be written.

This is an excellent point. I don't think anyone would deny the OP's right to move on if these problems are too much. I think I would feel the same if I'd had just half his issues. I don't think I would have lasted a year with those problems, so more power to the guy for fighting the tide.

*But* I remember all too well why I made the jump in the first place. It's easy to presume that Windows will save the day when you have gripes in Linux, but if you'd asked me to compile a list of all the things I had problems with in Windows before I switched, it would have been as long as the OP's without doubt. I'd had enough.

My best wishes to the OP however. Hope it all works out for you.

---

### Post by SomeGuyDude on 2009-01-09
> **BigSilly said:**
> This is an excellent point. I don't think anyone would deny the OP's right to move on if these problems are too much. I think I would feel the same if I'd had just half his issues. I don't think I would have lasted a year with those problems, so more power to the guy for fighting the tide.

*But* I remember all too well why I made the jump in the first place. It's easy to presume that Windows will save the day when you have gripes in Linux, but if you'd asked me to compile a list of all the things I had problems with in Windows before I switched, it would have been as long as the OP's without doubt. I'd had enough.

My best wishes to the OP however. Hope it all works out for you.

The best way to keep your memory fresh is to have people who use Windows that constantly need help with their computers.

The other day I had to clean something called "SpywareGuard 2008" off of my cousin's computer, and then do a generic "cleanup" of the system. The three hours I spent running four different scanners, registry cleaners, junk file tools, defragging, setting up anti-malware apps, plus the immense lag the system had even WHEN it was back in "top form" made me happy that I just have to deal with a broken system file once in a while.

---

### Post by Eisenwinter on 2009-01-09
> **picturefreedom said:**
> oh don't be a sisy, comm'n reveal your old forum  handle. :)
have atleast the balls to say goodbye on your regular account.
How dare you say that to anyone? "At least have the balls to use your real account"? What the hell?

What is this elitist crap?

The OP has a right to move back to Windows, or move to ANY operating system of his choice, and how do you know this isn't his "real" account anyway? Who made you the judge?

I moved to Arch about 2 months ago, does that make me the devil?

I suggest you start thinking of what you say, and take a good look at yourself - for example, I use Arch linux, I could go ahead and start calling you a "noob", just because you use Ubuntu.

But I don't, why? because anyone can use whatever OS they want to use.

It's people like you, the Linux preachers, that make Linux so unappealing to new people.

And I'm sorry if... wait, I'm not sorry, you're offended? I don't care :)

---

### Post by tjwoosta on 2009-01-09
why do people insist on making destructive threads like this?


do you really expect us to try and convince you to stay or something?

if you want to quit using linux, then quit!

if you really think you will have a better experience with windows, then go back to windows and leave us alone

but why make a thread about it on the ubuntu forums?

is it just to &!$$ people off?

is it to sway newcomers from trying?

is it so you can feel justification in your decision to leave? 


wait, whats that, your thinking that you made this post in an attempt to get poeple to recognize the issues so they can get fixed

well thats just plain stupid

thats what bug reports, and ubuntu brainstorm are for

also, if that were the case, why would you title it "farewell linux and ubuntu"!

so #$&% off and find somewhere else to whine

---

### Post by Eisenwinter on 2009-01-09
> **tjwoosta said:**
> why do people insist on making destructive threads like this?


do you really expect us to try and convince you to stay or something?

if you want to quit using linux, then quit!

if you really think you will have a better experience with windows, then go back to windows and leave us alone

but why make a thread about it on the ubuntu forums?

is it just to &!$$ people off?

is it to sway newcomers from trying?

is it so you can feel justification in your decision to leave? 


wait, whats that, your thinking that you made this post in an attempt to get poeple to recognize the issues so they can get fixed

well thats just plain stupid

thats what bug reports, and ubuntu brainstorm are for

also, if that were the case, why would you title it "farewell linux and ubuntu"!

so #$&% off and find somewhere else to whine
I completely agree with this.

There really isn't a need for all this dramatic "Awww... I'm leaving Linux, the god operating system, blah, blah, all cry and help me, convince me to stay, kiss my ***" crap.

---

### Post by magaio on 2009-01-09
If you have the urge to post a stupid one-liner, don't bother reading this.

> I am a little curious... If I were invited over to a friend's house for dinner, and when I got there and ate. I thanked him for inviting me over for dinner, but then on with a litany about how bad his cooking is... how do you think that friend would think of me?

If he were a real friend, he'd listen, no matter what it was. If it were true and he were humble, he'd listen and do something about it. If it were *untrue* he would know how to discuss the matter without being a pompous ***, if he were worth the oxygen he took in. To just say "LINUX ISN'T FOR YOU" is a stupid reply. He's obviously not stupid. Even if he were, should we still tell him to buzz off? No.

> Then again we live in a fast-food world where if we don't get the instant double-deluxe super belly buster burger in two seconds, we are normally complaining because the frys aren't lava hot.

Yes, that may be true. However, an OS isn't food. It's not entertainment, it's not just a hobby, it is a tool. A tool solves problems and makes life easier. And a tool should be easy to use. Otherwise, it's not a tool. It's a problem itself.

I love Linux and what I can do with it, but don't go saying that it's the perfect kernel and its software is too. To say that means we've stopped growing. If you don't want Linux to be used by more people -- "non-technical," "casual," "simple" people -- I say YOU should buzz off. You can't advocate one thing over the other if the criteria are different. Last I checked, Ubuntu was a general purpose OS, just like Windows. Either that means you one-liners are delusional (likely), or you truly believe that Windows and Ubuntu don't have the same criteria.


> Quote:
ELBSAK

Quote:

Coffee3133 said:
Nuff said.

You can see a pattern here. The usefulness of comments appears to be proportional to their length. Kind of like the richness of their intellect is multiplied by their ability to communicate. (Hint: zero) They'd rather use abbreviations and obscure their secret message than actually be open with someone.

> tjwoosta said:

so #$&% off and find somewhere else to whine

Again, who is being destructive here? At least the OP left some actual substance behind for us.

That casual users want Linux is largely a problem for userspace application developers, but also for system developers because of hardware compatibility. Yes, hardware designers can be utterly foolish when it comes to that. But by the time I type "vim text.txt" for the first time, the system should be configured, otherwise I've been lied to. The metaphor of the computer and the command line is now incorrect. 

If I want to customize the system, fine. Don't make something manual just because it "gives the user more control." Bull. Why don't we all just run an assembly debugger, then? "Need to print some text? Fire up a syscall!" Need to send a message to your friend? How about a post letter? It's easier in practically every way, even if it is slower. Yet here we are, banging away at keyboards, spending just as much time even CONFIGURING the client before actually using it!

Just because someone wants it easier doesn't necessarily mean they are ignorant. Always give someone the benefit of the doubt. Maybe this person just doesn't have the time to get a major in computer science from the local bookstore or library. Linux OS are not a mathematical truth nor physical truth. It's an OS, contrived and designed. It is a human artifact. Being thus, aesthetics matter. Yes, I said the "A" word and I'm not a Mac user.

Computers are more complex now and ever moreso. Remember when you could boot up DOS with a floppy (remember floppies?), and bam, you were ready? Maybe DOS looks ugly to you in retrospect, maybe it was crazy dangerous. But damn, it worked. It wasn't all GUI, wizardy, and "user friendly" but it still managed to be pretty simple, both under the hood and in the seat. I'm a man of principle and I strongly believe in free software but, in a lot of ways, I still miss DOS.

> 
From Nickedynick:

I hope the devs take not of this post and others like it. It's one thing being a troll and telling everyone that Linux sucks, but this guy has obviously had a lot of problems - we should be working to counter things like these happening.

Now there's a rational person. I'd rather have him on my team than most of you.

> Goodbye, Linux is not for everyone. 

Maybe you meant, "Linux ought not to be for everyone." If that is so, why does this forum exist? Why bother with wiki? Why bother with public docs? Why bother at all?

Maybe this isn't a problem *just for Ubuntu*. Maybe it is a hardware issue. I say this problem is for everyone: the developer, the doc writer (in which talent and numbers are lacking), the hardware designers, and more. We need to promote universality, openness, simplicity, and usability in computing -- not just scratch our own itch. If you want a secret club, go start your own password-protected, hacker-only, holier-than-thou forum, where you can use noodles for hammers and write with blood. I won't see you there.

---

### Post by Lisimelis on 2009-01-09
Sorry to hear that about living linux but maybe it was just plain bad luck on the hole. I think everybody runs into some os trouble from time to time but i personally prefer to have some trouble in  learning to do something new with linux than to have trouble with everyday issues like security and stability in windows. I also have a laptop and even though i cant have those cool compiz tricks it dont bother me cause at last i am able to keep a stable system for more than six months without the need to format c /s every now and then. Bye and take care.

---

### Post by chrisinspace on 2009-01-09
To the OP, I'd say you started with the wrong canvas.  In my experience ThinkPads are full of problems, no matter what OS they are running.

To everyone else, this isn't a holy war.  Let's try to learn from the problems others are having, help each other fix what we can, and work to make Ubuntu (and Linux in general) better.

---

### Post by Sealbhach on 2009-01-09
[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]

---

### Post by mdsmedia on 2009-01-09
I can't help thinking that, with a total of 3 posts, including those in this thread, the OP hasn't really spent 1 year USING Ubuntu. I didn't even read his entire first post.

Some thoughts come to mind, however. Firstly, these forums are starting to become the typically quoted "Linux elitist" stomping ground.

Some of the replies in this thread are horribly reactionary.

OK, this thread didn't start out in "Testimonials" but aren't FORUMS the place to discuss things? The guy has a gripe...a number of gripes...and he's expressed them....in discussion forums!!

He may have ill-founded gripes, but he still has the right to express them. I'd rather he did it here than on some other blog somewhere, where other ill-informed people would just take what he says and accept them.

Telling someone that here is not the place to express his gripes is utter BS!!

Secondly, telling someone that Linux isn't for everyone isn't a stab at the OP. It's true!! Just as Windows isn't for everyone, Mac isn't for everyone, Unix isn't for everyone. If you're happier with Windows, use Windows...you'll eventually see the light ;).

---

### Post by solwic on 2009-01-09
> **mdsmedia said:**
> I can't help thinking that, with a total of 3 posts, including those in this thread, the OP hasn't really spent 1 year USING Ubuntu. I didn't even read his entire first post.

Some thoughts come to mind, however. Firstly, these forums are starting to become the typically quoted "Linux elitist" stomping ground.

Some of the replies in this thread are horribly reactionary.

OK, this thread didn't start out in "Testimonials" but aren't FORUMS the place to discuss things? The guy has a gripe...a number of gripes...and he's expressed them....in discussion forums!!

He may have ill-founded gripes, but he still has the right to express them. I'd rather he did it here than on some other blog somewhere, where other ill-informed people would just take what he says and accept them.

Telling someone that here is not the place to express his gripes is utter BS!!

Secondly, telling someone that Linux isn't for everyone isn't a stab at the OP. It's true!! Just as Windows isn't for everyone, Mac isn't for everyone, Unix isn't for everyone. If you're happier with Windows, use Windows...you'll eventually see the light ;).

+1.  You just won my vote for Lord, Master, and Grand High Poobah of All of Creation.  That's the most intelligent comment I've ever read - ever - anywhere on this forum.  You are absolutely 1,000% correct.  

It's refreshing, posts like yours.  :)  

Cheers!

---

### Post by Moop on 2009-01-09
These goodbye threads always make for a good read. :popcorn:
I wonder if anyone ever says goodbye to Microsoft in the same way. :D

---

### Post by wolfen69 on 2009-01-09
the answer is simple really. buy a computer with linux preinstalled. :idea:   just like you did with windows. 

hell, i know of a couple people that could not use windows vista. even though it said on the computer: "vista capable".

mdsmedia: you really can switch gears in posting style, huh? your last post is not the mdsmedia i see over at ITwire. ;-)

---

### Post by solwic on 2009-01-09
> **Moop said:**
> These goodbye threads always make for a good read. :popcorn:
I wonder if anyone ever says goodbye to Microsoft in the same way. :D

Probably not.  I think most people say goodbye to Linux because they can, and because they are sick of Microsoft, can't afford OSX, and see Linux as a viable alternative that's *almost* ready for the big show.  

I think Ubuntu already is, to a point, but a lot of people don't, I guess.  I think the goodbye threads are really a way of saying, "I love this product and wish it worked on my system."

Maybe I'm reading too much into it, though.  After all, as Freud said, sometimes a cigar is just a cigar.  :)

---

### Post by estyles on 2009-01-09
I agree that flaming the OP is not constructive.  I think it's a good thing when people who have legitimately tried GNU/Linux post to say why it wasn't for them.  It wasn't a particularly whiny post, and it wasn't full of "IT SUCKS USE A REAL OS LIKE WINDOWS!!!" or anything like that.  If developers wish to gain users, they will take note of legitimate complaints like this.

On the other hand, while I agree with the OP's right to post his experience, I don't agree with all of the complaints.  (Though in the end, the fact that these things bother him and that he already apparently owns a copy of Windows are reason enough to switch if he wants to.)

First off, as someone else mentioned, if I listed all the frustrating problems I've had with Windows that caused me to switch, my list would be a lot longer than the original post.  Windows has problems, Linux has problems.  There are two main differences:

1) Most of the computers you buy come pre-loaded and tested with Windows.  If you bought a computer pre-loaded with Linux, you would expect everything to work flawlessly.  If you installed Windows on that machine, it might not be so useful (frex, I recently installed XP on a brand new machine that primarily runs Ubuntu - the XP partition had a 640x480 256-color resolution and couldn't use the onboard ethernet connection - had to go through like an hour of installing drivers for hardware that Linux supported natively).  However, it is true that driver software is generally much better for Windows.  We can hope that this is changing.

2) When you have a problem with Linux, there is almost always a solution, and you can almost always find out about it by asking in a public forum.  When you have a problem with Windows, the usual answer is to buy a program or a costly OS upgrade.  And that's if you can find an answer at all.  I can't tell you the number of times I've searched for an answer and just ended up giving up because I found tons of posts of other people who had the same problem and never got an answer.  Other times, I found buried in a 3-year-old MSDN posting, something about this being a bug in the OS that might be fixed at some point, but don't hold your breah.

So, that's *my* experience.  Of course, the OP bought a laptop that came with Windows pre-installed and was certified to work with Windows.  The fact that it didn't work with Linux is too bad, but that happens a lot with laptops that have all kinds of crazy features with driver interfaces that are proprietary and documented poorly if at all.  I mean, seriously, a thumb-print reader?  TV-tuner card on a laptop?  Who needs that stuff?  And I don't even know what a "Spyder" is.

As for gparted - maybe it's a little slow (it's not bad on my system, but I guess it is on some?), but it's awesome for what it does.  There's no free partitioning utility for Windows that allows you to resize partitions and create/format partitions in such a variety of filesystems.  (Maybe there's a resizer in Vista?  I doubt it, but maybe.  From all I've heard, the most popular way to do it is Partition Magic, which is supposedly way buggier than gparted.)

For me, I did want Vista when I bought a new computer.  Just to have it as a backup and to play games.  But in the end, it just wasn't worth ~$100 for an OS, when there are hundreds of Linux-based OS's that are FREE and that I prefer over Vista (which I do have on a laptop that I bought that came pre-installed - so I've tried it, but haven't completely explored everything it can do).

---

### Post by Mason Whitaker on 2009-01-09
> **Sealbhach said:**
> I'd be worried about stuff like this if he had bought a machine preloaded with Ubuntu.

Otherwise, it's the luck of the draw. Also, the Photoshop/GIMP thing... probably true but how many users would actually find this a deal-breaker?


.Yeah...most of us here are Geeks, not Graphic Designers XD;

---

### Post by estyles on 2009-01-09
> **Mason Whitaker said:**
> Yeah...most of us here are Geeks, not Graphic Designers XD;

While I'm not a graphic designer, I've been commissioned to do some graphic design because I know HTML and can format our advertising stuff.  I use GIMP whenever I can because I really prefer the way it does things.  I only use Adobe when I need to open indesign files or .eps files that our real graphic design guy creates.

---

### Post by wolfen69 on 2009-01-09
> **Mason Whitaker said:**
> Yeah...most of us here are Geeks, not Graphic Designers XD;

it's funny. i have heard so many things like, "gimp doesn't even come close to photoshop" complaints. (which i disagree with) you would be led to believe that most people in the world are professional graphics artists. give me a break.

---

### Post by stchman on 2009-01-09
Just another case of the whiners.  I have installed Ubuntu on many a laptop and all works well.  My Toshiba and Aspire One are happily running Hardy and Intrepid.  To this date I have installed Ubuntu on well over 10 machines including 5 laptops and they all work.  I guess I am just "lucky".

The OP has only 3 posts including his farewell.  I don't think he gave it time or asked for help.

---

### Post by 73ckn797 on 2009-01-09
> **jonfenton said:**
> I recently got frustrated with Ubuntu and reinstalled XP. It was a breath of fresh air at first but after a few months I realised why I got rid of it in the first place and now I am back on Ubuntu. That grass is not always greener and I think the perfect operating system has yet to be written.


The late Erma Bombeck stated "*the grass is always greener on the other side but usually it is over the neighbors septic tank*."

---

### Post by 73ckn797 on 2009-01-09
> **eisenwinter said:**
> how dare you say that to anyone? "at least have the balls to use your real account"? What the hell?

What is this elitist crap?

The op has a right to move back to windows, or move to any operating system of his choice, and how do you know this isn't his "real" account anyway? Who made you the judge?

I moved to arch about 2 months ago, does that make me the devil?

I suggest you start thinking of what you say, and take a good look at yourself - for example, i use arch linux, i could go ahead and start calling you a "noob", just because you use ubuntu.

But i don't, why? Because anyone can use whatever os they want to use.

It's people like you, the linux preachers, that make linux so unappealing to new people.

And i'm sorry if... Wait, i'm not sorry, you're offended? I don't care :)

[size=6]+1[/size]

---

### Post by Slug71 on 2009-01-09
Well for me its always sad to see people leave Linux and go back to MS but they have their reasons and Linux just isn't for everyone yet.

The 6 month updates the OP has spoken of is kinda annoying though but i can live with it and that is mostly the Apps devs fault and not really Ubuntu/Linux. I would like to see some Apps making its way to Ubuntu/Linux though that has the Update option like many for Windows does.
I'd even like to see them go one better where the version can be updated like from 1.5 to 2.0  without having to uninstall the older version first and then installing the newer like many Apps still do in Windows.

I think Jaunty is going to be good though and the following versions.

---

### Post by solwic on 2009-01-09
> **wolfen69 said:**
> it's funny. i have heard so many things like, "gimp doesn't even come close to photoshop" complaints. (which i disagree with) you would be led to believe that most people in the world are professional graphics artists. give me a break.

I agree with you.  Gimp is pretty good - maybe even better than photoshop - but nobody will ever know because (as I read once somewhere, though I can't remember where) the Gimp guys don't *want* to be like Photoshop.  

Which is admirable, I suppose, but in essence what they have done is taken a whole section of their consumer base (and a pretty large one at that, I would assume) and alienated them by refusing to give them a program that is inherently similar to the one they spent all that money in college learning.  True, it's not Gimp's fault that a lot of colleges only teach Photoshop, and it does suck that FOSS doesn't get much play in academia...but as the first quote in my sig says, "A man should look for what is, and not for what he thinks should be."  While it sucks the way things work, it *is* the way things work.  Denying it only insures that it'll never change.  

This reminds me of Microsoft and IE6/7, refusing to hold to the W3C guidelines for Web standards.  It's partly why Firefox is so popular, I think.  

Anyway...I don't use the Gimp because the classes I had in college were Fireworks/Photoshop based, and I don't do enough graphics design to justify spending hours (or days or weeks or months) relearning a program.  It's easier to stick with what I know (and granted, I do very little graphic editing/design), faster, too.  

I get why they did it, I think...but they're only shooting themselves in the foot.  

IMO, anyway.  :)

---

### Post by oldsoundguy on 2009-01-09
There are many ways around the issue(s) of various Linux builds on LAPTOPS .. the first being .. if your laptop does not work .. you will spend a lot of time doing research in HOPE that you can fix it .. and many times, because of the totally proprietary nature of the components within and the failure of the manufacturer to co-operate with the Linux community .. you will NEVER get that piece of junk to work!

I have yet to have a serious issue with setting up any Linux DESKTOP that swapping out a card or adding a card would not fix!  And that goes for the really old and slow .. just as long as there is enough ram available!

As to the need for Windows .. yep, for some programs there is no other choice at present.  Stuff written for Linux is close, but it is NOT close enough for some professional USERS of that software ..

So, solutions:
Virtual .. clumsy, but works
Separate partition .. also clumsy, but works 
Or the really EASY route .. a SECOND COMPUTER  ... (duhhhhh why didn't I think of that?)(since you only need the BOX and nothing else .. not too expensive a way to go!)
With a second computer and a KVM switch, you can have the best of both worlds, never take that Windows box ON LINE where it can get damaged by a sneeze of some script kiddie. And, therefore, not have to worry about the over 1 million baddies that can hurt the machine if you go on line! And NOT have to spend hours each week cleaning the crud off of it that Windows leaves behind every time you launch and then close a program. (yet alone stuff you inadvertently pick up .. even on the most protected machine .. by GOING ON LINE.)

Saying goodbye to a solid system such as Linux has become without investigating the alternatives is admitting that you really do not have a clue.  Nothing wrong with using BOTH as each has their merits.

---

### Post by solwic on 2009-01-09
> **tjwoosta said:**
> 
so #$&% off and find somewhere else to whine

Thank goodness you're not spokesperson for this community.  

Do you really think telling him off is going to make him or others stop posting goodbye threads?  

Do you really think the goodbye threads are meant to say goodbye, and that they're not really frustrated cries for help from people who want to be free of MS but can't get Linux to work on their systems, and who don't know enough to ask the right questions, or to even know which questions are right...all the while dodging people like yourselves who aren't interested in anything but stroking their own egos and tearing everyone else down to make themselves feel better?

Do you really think *you* are helping the situation any by adding to the "destructive thread"?

I know I shouldn't bother with these types of posts...but I can't help myself.  It upsets me to see people treated that way, even people who get branded with the name "troll" just because they're frustrated and post an angry post on the forums.  

So please, take your own advice and "#$&% off and find somewhere else to whine."  Please.  You're boring us.  And embarrassing yourself, too.  

:)

---

### Post by jrusso2 on 2009-01-09
> **jrock612 said:**
> I agree with you.  Gimp is pretty good - maybe even better than photoshop - but nobody will ever know because (as I read once somewhere, though I can't remember where) the Gimp guys don't *want* to be like Photoshop.  

Which is admirable, I suppose, but in essence what they have done is taken a whole section of their consumer base (and a pretty large one at that, I would assume) and alienated them by refusing to give them a program that is inherently similar to the one they spent all that money in college learning.  True, it's not Gimp's fault that a lot of colleges only teach Photoshop, and it does suck that FOSS doesn't get much play in academia...but as the first quote in my sig says, "A man should look for what is, and not for what he thinks should be."  While it sucks the way things work, it *is* the way things work.  Denying it only insures that it'll never change.  

This reminds me of Microsoft and IE6/7, refusing to hold to the W3C guidelines for Web standards.  It's partly why Firefox is so popular, I think.  

Anyway...I don't use the Gimp because the classes I had in college were Fireworks/Photoshop based, and I don't do enough graphics design to justify spending hours (or days or weeks or months) relearning a program.  It's easier to stick with what I know (and granted, I do very little graphic editing/design), faster, too.  

I get why they did it, I think...but they're only shooting themselves in the foot.  

IMO, anyway.  :)
There is a program
 thats easy to use and is better then gimp even is paint.net  Too bad
its only available for Windows it would be perfect for Linux.  I know they were working on a Linux port using Mono but like  alot of projects I have not heard anymore about it and it seems to still be in an early stage of development

---

### Post by shedt on 2009-01-09
I find it really hard as i feel stuck in the middle. I love Ubuntu, I love the idea, how things work. But sometimes that is it. Some many programs I use do not work, or there is no linux alternative. 

As well, if you buy a program and pay good money for it why should you use a alternative?

I'm really tired of dual-booting. Going back and forth. I prefer the gui, the way things are setup, but I need to use windows for many things.

The best thing though is knowing how Ubuntu and linux is getting better. It is so much better then when I first tried it out a few years ago. 

And the community is amazing. But if you run special hardware or programs sometimes you need windows. As well, the elitist attitude by many linux users is really saddening for me. It's not cool and really does more harm then good IMHO.

---

### Post by shedt on 2009-01-09
> **jrusso2 said:**
> There is a program
 thats easy to use and is better then gimp even is paint.net  Too bad
its only available for Windows it would be perfect for Linux.  I know they were working on a Linux port using Mono but like  alot of projects I have not heard anymore about it and it seems to still be in an early stage of development

Paint.net is really cool, and combined with gimp you really are rocking. But it is hard for many people that have learned on photoshop and make their living off it. I know some people that stills use only cs2 because they do not have time to re-learn cs3 or cs4.

---

### Post by pengo_au on 2009-01-09
FWIW, I listed the reasons I left Linux, not the good things about it. So here's some nice things for balance my "trolling", and then some more rambling, and I'm off:

Yes, I never had to worry much about security, much of my hardware "just worked" (with several notable exceptions), Nautilus does some very useful (and seemingly obvious) things like warning you there isn't enough space BEFORE it starts copying, the default PDF reader mostly works very well and is fast, Compiz Fusion work fairly well and usually looked great and was occasionally even functional (e.g. the magnifier), firefox is firefox, gparted (apart from very slow startups) is far more functional than the equivalent stupid Windows utilities, and yes, I'd be scared to use Partition Magic too (apparently older versions are more stable) so while I'll gripe about gparted doing weird slow analysis of my drives I'll probably continue to use it anyway (from a Live CD) whatever platform I'm using.

The GIMP is functional and useful (sorry, I didn't mean to start a flamewar) but it is lacking a 16 bit per channel mode, and doesn't handle camera raw files (except with a plugin which has to scale them down to 8-bit) which I don't particularly blame it for but these are features I could use. I welcome differences in the user interface of GIMP, as I don't particularly like Photoshop's user interface anyway.

> **estyles said:**
> I mean, seriously, a thumb-print reader?  TV-tuner card on a laptop?  Who needs that stuff?  And I don't even know what a "Spyder" is.

I have used the fingerprint scanner a few times simply because it's there and I can.. And it was surprisingly straightforward to make it usable in Linux. I installed the software from some sourceforge project and password prompts magically change to "Password or fingerprint" prompts. Neat.

The problem was with it overheating because it stays on instead of going into standby. This problem remained whether the software was installed or not. The work around existed, but was time consuming, stopped working after an upgrade, and seemed to be something that could be built-in easily enough (e.g. a default power setting for a USB ID).

Spyder is a device for colour-calibrating monitors. Someone seemed to have reverse engineered it for Linux once but I never got it working. Which didn't matter much because I couldn't set a colour profile for my monitor anyway (xcalib didn't even want to do it for some reason although it was happy to reverse my colour scheme if I asked it to). Fortunately GQview has some colour profile understanding, and that helped muchly. GQview is one of the best apps on the linux desktop, and I hope they get around to updating it in the repos someday, or making it the default image viewer.

> **estyles said:**
> ... XP partition had a 640x480 256-color resolution and couldn't use the onboard ethernet connection - had to go through like an hour of installing drivers for hardware that Linux supported natively.

And I needed to download literally 200 MB of drivers when I reinstalled Windows. 130 of that was a bluetooth driver (I'm not even going to ask why it's that size). Fortunately they were all downloadable from ibm/lenovo, and all my hardware worked perfectly once the drivers were installed. Of course, as has been pointed out plenty already, this machine, it seems, is made for Windows.

Anyway that's enough rambling from me. I'm out the door and gone anyway.

---

### Post by pengo_au on 2009-01-09
> **picturefreedom said:**
> oh don't be a sisy, comm'n reveal your old forum  handle. :)
have atleast the balls to say goodbye on your regular account.

I'll take this as a compliment :) Bye!

---

### Post by gn2 on 2009-01-10
> **shedt said:**
> ~ As well, if you buy a program and pay good money for it why should you use a alternative? ~

From a financial standpoint:

So you can break out of the expensive OS and hardware upgrade merry-go-round.

How long is your paid for app going to remain compatible with a Microsoft OS?

Will you want to pay again for a newer version that will work with the next OS?

Finding native Linux apps is all about future savings.

---

### Post by irpapabear on 2009-01-10
here and again like many of the posts read..if your gonna leave linux,,then just leave. <see ya in a few months> ya not need all this drama to leave. I have been totaly ms free for 6 months now and I have NO plans of ever going back. no even to look at win7. btw...the gimp rulez! nuff said.

---

### Post by albinootje on 2009-01-10
> **pengo_au said:**
> 
And I needed to download literally 200 MB of drivers when I reinstalled Windows. 130 of that was a bluetooth driver (I'm not even going to ask why it's that size). Fortunately they were all downloadable from ibm/lenovo, and all my hardware worked perfectly once the drivers were installed. Of course, as has been pointed out plenty already, this machine, it seems, is made for Windows.

Anyway that's enough rambling from me. I'm out the door and gone anyway.

You keep coming back here it seems ;-)

Of course, after this discovery, you did (persistantly) phone IBM/Lenovo right away, and asked them w h e n their website would also offer a 200 Mb of L I N U X drivers, didn't you ?

---

### Post by estyles on 2009-01-10
> **irpapabear said:**
> here and again like many of the posts read..if your gonna leave linux,,then just leave. <see ya in a few months> ya not need all this drama to leave. I have been totaly ms free for 6 months now and I have NO plans of ever going back. no even to look at win7. btw...the gimp rulez! nuff said.

It's not drama.  People post about why they are leaving linux for the same reason that you post that you are totally MS free for 6 months.  This is the testimonials area, and it's not just for "good" testimonials.  I agree that probably 90% of the "I'm leaving linux" posts are pointless, uninformed, whining for no reason.  This post is not that.  Don't flame *everyone* that has complaints.

Honestly, I think the main problem is that, while Ubuntu is certainly "ready for the desktop", it still has some time before it's ready for the *laptop*.  Laptops come with all sorts of weird proprietary hardware these days, and most of it is not properly supported by the manufacturer.  If the answer is that the kernel needs to support everything itself (and all the original drivers are closed source), then there will probably *always* be problems with laptops.  If manufacturers start to see some value in supporting Linux, or at least make their drivers Open Source, then the problem will gradually go away.  And manufacturers need to realize that open sourcing their drivers is rarely a bad thing for them.  It's not as detrimental to their competitive advantage as they think it is, and opens up a new market which, though small, is growing fast.

Really, I think the reason for closed source drivers more often than not is that they're full of stolen code.  Or at the very least non-GPL stuff that can't possibly be released under the GPL.  It's a mindset switch that needs to happen.  I'm actually okay with MS charging a couple hundred for Visual Studio, or Adobe charging a grand for CS4.  I don't feel that all software has to be FOSS.  But *drivers*?  Those are just there so that people will buy your hardware.  You don't sell the drivers!  So set them free!

Okay, yeah, that turned into an OT rant...  oh well.

---

### Post by aysiu on 2009-01-10
> **estyles said:**
> This is the testimonials area, and it's not just for "good" testimonials. Me nitpicking: testimonials are by definition positive. That is why I insisted we retitle this section *Ubuntu Testimonials **and Experiences***, because people are welcome to share bad experiences as well.

---

### Post by solwic on 2009-01-10
> **aysiu said:**
> me nitpicking: Testimonials are by definition positive. That is why i insisted we retitle this section *ubuntu testimonials **and experiences***, because people are welcome to share bad experiences as well.

+1

---

### Post by macintosh on 2009-01-10
> **yaztromo said:**
> Every testimonial which doesn't praise the God Ubuntu gets branded a troll on here.

Yes that is so true this is not a Ubuntu God Fountain this is a Community. Linux is a closed community if someone does not use Linux we don't want them there.

---

### Post by macintosh on 2009-01-10
> **wolfen69 said:**
> the answer is simple really. buy a computer with linux preinstalled. :idea:   just like you did with windows. 

hell, i know of a couple people that could not use windows vista. even though it said on the computer: "vista capable".

mdsmedia: you really can switch gears in posting style, huh? your last post is not the mdsmedia i see over at ITwire. ;-)

actually NO computers should just run linux.

---

### Post by solwic on 2009-01-10
> **macintosh said:**
> actually NO computers should just run linux.

I agree with that.  But I read your blog...and wow, dude.  You've got "misinformed" down to an art, brother.  :P

Cheers!

---

### Post by wolfen69 on 2009-01-10
> **jrock612 said:**
> But I read your blog...and wow, dude.  You've got "misinformed" down to an art, brother.  :P



yeah, it's too bad some people have to go through life with hate blood running through their veins. (no one in particular) it's a shame their energies could not go to a more positive use like earth conservation and such. this was just a general statement.

---

### Post by UriahHeap on 2009-01-10
I'm relatively new to Ubuntu & very new to these forums.  I found this thread because of the OP's (original poster???) title piqued my curiosity.  I'm looking for a Firefox fix & thought the thread might shed some light on my problem. Here's some newbie perspective.  Flame throwers get ready!

The Linux elitists who feed their egoes with posts villifying "noobs" chase more people away from Linux than any problem they may have with Linux.  Who wants to ask a question when a large per centage of responses are attacks & not of any help?  Just how many times will anyone ask for help if responses repeatedly point out how stoopid the question is?

I have searched these forums for help without posting.  I have been fortunate enough to find the answers to the numerous Ubuntu glitches I have run across.  Sometimes it has taken hours to find a solution because I wasn't using the correct search term or phrasing.  I have persisted because I want to learn & explore Ubuntu.  But, I can understand that some people don't have the time or inclination to be as persistent as I.

The old hands sometimes forget that a new (to the user) OS can be very frustrating.  It can be difficult to even phrase a question properly if the new user hasn't acquired the jargon of the new OS.  And, this acquisition doesn't happen via osmosis!  Like most learning, it happens by experience & asking questions.

I assume the original poster was honestly trying to give useful feedback to the community in the hopes of improving Ubuntu.  And, he didn't slam the door on ever using Ubuntu again.  In fact since his "farewell" post he has returned & offered positive feedback, too.  IMHO he dosen't deserve the "good-bye & good riddance" responses.

It won't take many flames for me to stop posting but it will not squelch my curiosity & desire to learn Ubuntu.

Excuse me while I don my flameproof threads!

Yesterday's a memory, tomorrow's a dream, LIVE today!
UriahHeap

---

### Post by mdsmedia on 2009-01-10
> **wolfen69 said:**
> the answer is simple really. buy a computer with linux preinstalled. :idea:   just like you did with windows. 

hell, i know of a couple people that could not use windows vista. even though it said on the computer: "vista capable".

mdsmedia: you really can switch gears in posting style, huh? your last post is not the mdsmedia i see over at ITwire. ;-)
Different audience on iTWire. There aren't too many Windows fanbois here.

---

### Post by sigurnjak on 2009-01-10
Paint.net is coming :
[http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

---

### Post by Aearenda on 2009-01-10
When Intrepid came out, it took me two months to get it working properly on my previously-happy laptop. Things that used to work, stopped working, or just changed, with no warning or documentation. I nearly threw in the towel too, after 5 years of Linux use (I started work in the computer industry in 1977, and commercial application and management of operating systems was my area of expertise). Replacing the laptop was not an option.

Fortunately, for my sins I get to fix a lot of Windows systems friends bring to me, and so I persevered. Intrepid now works *better* on my laptop than any previous Linux version. Not everyone could be expected to do this, and so I have posted my notes for others to follow.

I think people post leaving messages so that those of us who are responsible for improving Ubuntu's quality can pick up on their critical issues and hopefully work towards fixing them. Commercial software vendors pay people to do usability testing to find these issues; we get it for free, if only we will listen to it instead of shooting the defector.

We should be glad of messages like the OP's - there is gold buried in them.

---

### Post by directhex on 2009-01-10
> **sigurnjak said:**
> Paint.net is coming :
[http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

Won't be packaged until it properly terminates when you click "quit"

---

### Post by etnlIcarus on 2009-01-11
> **jrock612 said:**
> I agree with that.  But I read your blog...and wow, dude.  You've got "misinformed" down to an art, brother.  :P

Cheers!

I'm not sure it's his blog but it certainly is terrible. It does a great injustice to the original linux hater's blog.

---

### Post by albinootje on 2009-01-11
> **etnlIcarus said:**
> I'm not sure it's his blog but it certainly is terrible. It does a great injustice to the original linux hater's blog.

+1 Exactly.

---

### Post by VON_CAPO on 2009-01-11
> **uriahheap said:**
> 

the linux elitists who feed their egoes with posts villifying "noobs" chase more people away from linux than any problem they may have with linux.  Who wants to ask a question when a large per centage of responses are attacks & not of any help?  Just how many times will anyone ask for help if responses repeatedly point out how stoopid the question is?

I assume the original poster was honestly trying to give useful feedback to the community in the hopes of improving ubuntu.  And, he didn't slam the door on ever using ubuntu again.  In fact since his "farewell" post he has returned & offered positive feedback, too.  Imho he dosen't deserve the "good-bye & good riddance" responses.

+1000

---

### Post by albinootje on 2009-01-11
> 
the linux elitists who feed their egoes with posts villifying "noobs" chase more people away from linux than any problem they may have with linux. Who wants to ask a question when a large per centage of responses are attacks & not of any help? Just how many times will anyone ask for help if responses repeatedly point out how stoopid the question is?

Please come with some examples which show that the majority of people have said that the question of the OP was stupid.

You should have tried some UNIX IRC channels years ago (Linux is not UNIX, UNIX is an official trademark), that was all about RTFM. 

Have hardly seen that here, or on any Linux related mailinglists ever since I use Linux (1995).

---

### Post by solwic on 2009-01-11
> **albinootje said:**
> Please come with some examples which show that the majority of people have said that the question of the OP was stupid.

You should have tried some UNIX IRC channels years ago (Linux is not UNIX, UNIX is an official trademark), that was all about RTFM. 

Have hardly seen that here, or on any Linux related mailinglists ever since I use Linux (1995).

RTFM didn't get UNIX very far, at least in the consumer sect.  Of course, that may not have been their target or goal....

RTFM doesn't work, and I'm glad that you're right, and it doesn't flourish here very much.  If all the people who help here suddenly started up the RTFM nonsense, I would imagine Ubuntu would die off.  The community is what keeps this distro popular; compromise that, and I don't think the OS itself has enough pull to keep its users. 

JMO, though.  And again, glad we've evolved beyond RTFM.  :)

---

### Post by presence1960 on 2009-01-11
magaio I totally agree with you. We on here are sometimes intolerant of people with problems that are overwhelming them to the point of giving up on Linux. If we are really about helping others we will still try to be helpful or at the very least LISTEN! As a reformed drug addict clean 23 years this Feb 1 where would I be if after the numerous attempts I made at sobriety those who were trying to help me shunned me, ridiculed me or simply told me to leave and good riddance? That is exactly what we do on here to people with "problems". **This IS NOT HELPFUL to anyone!!**

---

### Post by presence1960 on 2009-01-11
> I think people post leaving messages so that those of us who are responsible for improving Ubuntu's quality can pick up on their critical issues and hopefully work towards fixing them. Commercial software vendors pay people to do usability testing to find these issues; we get it for free, if only we will listen to it instead of shooting the defector.

We should be glad of messages like the OP's - there is gold buried in them.

Aearenda, very wise words indeed!

---

### Post by solwic on 2009-01-11
> **presence1960 said:**
> magaio I totally agree with you. We on here are sometimes intolerant of people with problems that are overwhelming them to the point of giving up on Linux. If we are really about helping others we will still try to be helpful or at the very least LISTEN! As a reformed drug addict clean 23 years this Feb 1 where would I be if after the numerous attempts I made at sobriety those who were trying to help me shunned me, ridiculed me or simply told me to leave and good riddance? That is exactly what we do on here to people with "problems". **This IS NOT HELPFUL to anyone!!**

+1, although I'm afraid I must include myself on that "not helpful" list at times.  

I think it's a result of the exposure to this place.  That's not to say my words or actions are anybody's responsibility but my own, but I think when you spend a lot of time here on the forums, the whiny, b*tchy, attitude starts to rub off on you.  

I guess it'll take a concerted effort to put a stop to it, and even then I doubt it's possible to erase it entirely.  After all, there can be no helpful people without unhelpful people.  It's just physics.  Natural law.

Ah well.  I guess all I can do is resolve to not make myself as petty, childish, jealous, insecure, and obtuse as those who make this forum a bad place.  

:)

---

### Post by tjwoosta on 2009-01-11
i think alot of you are missing the obvious point of this thread

at Ubuntu forums we always help people when we can (those who need help and ask for help)

the OP is not asking for help, nor is he providing anything usefull

you honestly think that posting a goodbye rant on the ubuntu forums is going help improve ubuntu in any way?

like i said before this is exactly what bug reports and ubuntu brainstorm are for

its the people who post real bug reports, and give honest suggestions on ubuntu brainstorm, and even write some of their own code that make the real difference, not the people who rant and rave about how this doesn't work and that isn't compatible and say im leaving because it doesnt work like i want it to


PS  just so you know, this thread was not originally placed in the suggestions and feedback section

---

### Post by collinp on 2009-01-11
> **yaztromo said:**
> Every testimonial which doesn't praise the God Ubuntu gets branded a troll on here.

No, PEOPLE THAT TALK LIKE THIS and that only outline the bad parts of the OS they are using get branded a troll. Heh, I use Arch, but im not a troll :). If I made a post like this, there would probably be a mile long list of things that I want and that does not work etc., but I stick with things until I am done.

---

### Post by jordilin on 2009-01-11
Well, if you go back to windows good luck, you'll need it and you'll miss all this great and helpful community and the power of the "shell". ):P

---

### Post by solwic on 2009-01-11
> **Hellow said:**
> No, PEOPLE THAT TALK LIKE THIS and that only outline the bad parts of the OS they are using get branded a troll. Heh, I use Arch, but im not a troll :). If I made a post like this, there would probably be a mile long list of things that I want and that does not work etc., but I stick with things until I am done.

I don't know.  "Troll" is becoming as common as "It's not Ubuntu's fault" and "Ask for a refund."  

I don't agree that if you don't worship the "God Ubuntu" then you're branded a troll...but I do kind of wonder if you have a complaint/problem with Ubuntu, or you speak out against it...yeah, I think generally the "troll" label is applied.  

Ah well.  I doubt it's going away, so complaining about it is kind of pointless.  :P

---

### Post by presence1960 on 2009-01-11
> to everyone else, this isn't a holy war. Let's try to learn from the problems others are having, help each other fix what we can, and work to make ubuntu (and linux in general) better.

**+1**

---

### Post by jordilin on 2009-01-11
> **tjwoosta said:**
> i think alot of you are missing the obvious point of this thread

at Ubuntu forums we always help people when we can (those who need help and ask for help)

the OP is not asking for help, nor is he providing anything usefull

you honestly think that posting a goodbye rant on the ubuntu forums is going help improve ubuntu in any way?

like i said before this is exactly what bug reports and ubuntu brainstorm are for

its the people who post real bug reports, and give honest suggestions on ubuntu brainstorm, and even write some of their own code that make the real difference, not the people who rant and rave about how this doesn't work and that isn't compatible and say im leaving because it doesnt work like i want it to


PS  just so you know, this thread was not originally placed in the suggestions and feedback section

I agree. Sometimes, if you have a real problem with drivers or anything the best way is to notify the problem, so Ubuntu developers and the community can help to find a work around. Ubuntu is not the only Linux distro out there by the way, and sometimes another distro can run better for your specific hardware. I remember those years that I switched from distro to distro to find the best for my hardware, namely Fedora, SuSe, Debian, Mandrake. Now, there are thousands...Leaving for Windows because some things just don't work, well...

---

### Post by etnlIcarus on 2009-01-11
I'm honestly not sure what else people expected from this thread; the op didn't post this asking for help: he'd already given up.

This thread was a critique of ubuntu from one person's prespective. Disagreeing with that critique or aspects thereof =/= 'not being helpful', or 'being elitist'. *It's not that kind of thread*.

---

### Post by jerzydirtracer on 2009-01-11
So, Mr Pengo is going back to the dark side. I hope he feels better when XP is no longer supported, and the mistake called Vista is no longer, and he has to give in to corporate greed and "BUY" the next version of windows. Linux is not perfect. But windows is less perfect. I guess he cant see the freedom we have over windows. Also how much does one have to spend for anti-virus and all of the security programs for windows? pay $200 for full version, plus another $100 - $200 for anti-virus and firewall programs. Oh yea, besides there are programs that still run on the same basic kernel in linux since it started, no matter what distro. Say that about windows.

Oh he also mentioned friends with "BROKEN" windows boxes. Another thing we don't have here in Linux.

---

### Post by solwic on 2009-01-11
> **jerzydirtracer said:**
> Also how much does one have to spend for anti-virus and all of the security programs for windows? pay $200 for full version, plus another $100 - $200 for anti-virus and firewall programs. 

Not to be contrary, but you can get Spyware Doctor from PC Tools (through googlepack), ZoneAlarm basic, and AVG or Avast Antivirus all for free.  Norton and McAfee are junk; have been for a long time.  

IMO, anyway.  But you can protect Windows XP for nothing.  :)

---

### Post by spnkybnky on 2009-01-12
Sounds like your machine is the problem, not Ubuntu.  I first began on an old computer, then I decided to run dual boot Ubuntu / Vista on both my laptop and desktop mainly because of the business I do on the side is only Windows compatable. Running dual boot for the past year or so has let me gradually move my work from Wintows to Ubuntu and as every week has gone by, I do less on windows and more on Ubuntu to the point where I only boot into windows when necessary. I have had a few issues and that is to be expected when using an operating system that you are not familiar with. But I must conclude that you do not like learning anything new. You only like what is familiar and like to stay in your safety zone. And that's ok. Just don't trash an operating system just because you do not want to take the time to learn it. 

I have helped many senior citizens get on the internet using Linux. When someone starts from zero knowledge, it is eaiser for them to learn Ubuntu than Linux and I don't have to worry too much about teaching them spyware and virus protection at this time. I have them doing many things on their Ubuntu computers with none of the problems that you describe, So if the problems you describe are widespread, then I would have run into them after loading more than 100 other computers at senior citizen centers with it. So take a good look at yourself and your POC computer. 

So if you can't handle it, then get out. Personally comparing windows to Ubuntu is like comparing driving on crowded freeways in stopped traffic in LA to a nice country drive on a fast road breathing fresh air. ....

---

### Post by Rhyader on 2009-01-12
I've never seen so many problems as this guy reports. Then again my hardware is much less complex. But really, I would love to see Ubuntu become a popular replacement for Windows with smooth sailing. Frankly, though, that is not going to happen until the linux geeks can admit that Ubuntu just does not handle some things, like video, especially if multiple screen are involved, very well. The other major problem is GRUB. Grub is horrible! Hey don't jump on me - I LIKE Ubuntu. But I do think it would become more popular if some of the most often-complained-about issues were addressed.

---

### Post by stalkingwolf on 2009-01-12
> When its for real you never quit. You never give up.
Sailor. Uncommon Valor.

---

### Post by 37fleetwood on 2009-01-12
I am sort of new to linux and sort of new to Ubuntu. I have been trying Linux off and on for several years and just recently decided that I knew enough and Linux had progressed far enough and I made the switch from Windows.
I think for some they lose sight of why they tried Linux at all.
I'm a photographer and have used Photoshop since Photoshop 3. Photoshop works better for me and it may just be that I'm not familiar with the Gimp but there were several things I looked for and couldn't find. this said I don't think the Gimp is $1000.00 worse than Photoshop.
I got so tired of buying expensive software windows included or using pirated junk full of viruses and other nasty stuff, that Linux was a breath of fresh air.
in a fair comparison I would say Linux and windows are on par now. I know most here won't agree but it is true none the less. Windows works on all hardware, heck almost all pc hardware is designed with Windows in mind. software for Windows is great, while some of the Linux stuff is a bit behind but this is to be expected for now though great strides are being made in Linux.
the real issue though is with Windows, you get the OS and thats it. everything from there is a cost, and some, what a cost! with Ubuntu I just go to Synaptic and look around and find what I need and it gets installed for free. it's funny to me that one of the complaints was about updates considering in Windows, update means going to the computer store and getting the new version. sometimes they give you a break if you have the previous version but never free. with Ubuntu I have enough tools to get done most of what I need to get done. so I use wine for photoshop7, it works.
when I switched over I did a dual boot setup with xp just in case and you know how many times I've used xp? 2 or 3. I'm so happy with My Intrepid Ibex that even if they offered Windows free I don't think I would go back. the proof is that with so much pirated software available through various channels for free if you know where to look, I will stay right here. this works better at least for me.
finally I must say, I don't miss firing up the old xp and waiting 10 minutes for all the anti spyware and anti virus programs to get going and all the different stuff waiting in line to do their updates most of which are designed to safeguard their software rather than protect me and my data, or make my experience better.
I must say that I'm now proud to say I'm a PC...without Windows!
sorry if this isn't the place for this (I was actually looking for info in Vmware).
Scott8)

---

### Post by steveneddy on 2009-01-12
> **wolfen69 said:**
> the answer is simple really. buy a computer with linux preinstalled. 

I say this all the time.

Or make sure that your hardware is supported by the Linux Kernel.

My goodness, you wouldn't buy MAC hardware and expect Windows to run well on that hardware platform, would you?

I feel that the Thinkpad should have been able to run Ubuntu very well, but the learning skills were not there for this person.

To use Linux, you **must want to learn**, otherwise you will not have a good experience.

Once you start understanding it, it really is very easy.

---

### Post by etnlIcarus on 2009-01-12
> My goodness, you wouldn't buy MAC hardware and expect Windows to run well on that hardware platform, would you?I don't know, how many years have Intel Macs been the norm?

---

### Post by albinootje on 2009-01-12
> **etnlIcarus said:**
> I don't know, how many years have Intel Macs been the norm?

There's still loads of second hand non-intel macs for sale.
And does MS-windows work flawlessly on the intel macs ?

---

### Post by solwic on 2009-01-12
I'm going to paraphrase Tamlynmac here, and ask if I can see this dead horse we're all kicking.  

He's gotta be in bad shape....

---

### Post by cygnus-X1 on 2009-01-12
Opinions are like... Well, we all know what they're like. Frankly, I can understand this person's position. I also understand that you can't please all of the people, all of the time.

To start with, I'm not a Chevy v. Ford v. Dodge or OSU v. Michigan or Cowboys v. Steelers kind of guy. Nor am I Windows v. Mac v. Linux. The first system I worked on was called 'Pick' (ie - Pick Basic). Then there was Progress, Unix and Xenix. #-o 

That was 20 years ago. I wasn't a "programmer then, and I ain't one now. I hated the equivalent of CLI then as much as I do today. But I deal with it. I don't mind getting my hands dirty and thank god for copy/paste! =D>

I really don't care what the Linux Only or Windows Only 'preachers' have to say. You'll always make the choir happy. So what?! It doesn't solve anything! Besides, I hate *religion* of all kind. Not God, though.   *([Here's a good take on all computers in general]("http://www.youtube.com/watch?v=0-22EpQOm8c"))*(Mac vs. PC vs. Linux)

If Linux, specifically Ubuntu, wants to attract people away from Windows, (and Mac), instead of doing so through natural attrition, maybe they ought to actually listen to the people who use, modify and mostly have problems with it. ie - Find a need and *fill it.*

I've been "using" 8.04 for almost 9 months now, with boat-loads of problems. Hardware compatibilities, (memory that is listed as compatible that really wasn't, that was just found via process of elimination this past month). Software that alters itself at will, (ATI or screen resolution just yesterday). I wish I would have been as meticulous as the initial poster at keeping records of what all has been problematic. But that would give ma a page to myself...](*,)

People who voice their problems and that they decide to change their OS aren't trolls. Their frustrated. In most cases they came to Linux (Ubuntu) because of frustrations with whatever they were using. Maybe even like yourself. :-k 

In my case, Win2kPro. Which, by the way, I prefer to XP or especially Vista. (Too bad I can't get drivers for my main MoBo from ATI. Now I HAVE to consider XP. In my not-so-humble opinion, I'll put a bullet through my head before I would even consider Vista. "More crashes than a NASCAR event!" Sorry Vista users. :-({|=  
(see: [BLIMPTV: MICROSOFT VISTA SUCKS]("http://www.youtube.com/watch?v=jOh6Nh8w6f8"))

There are a lot of things I like about Ubuntu that Windows either doesn't do or do well. There are things that I like about 2K, (and even XP), that Linux just doesn't do at all. (Try C&C Red Alert series and Generals for starters). I see threads asking what it would take to go MS-Free? For me, solid A/V editing and games. (yes, I'm looking at Kino.)

Here's one suggestion I'ld make, especially since I'm not super-tech talented. I'ld love to see a 'HowTos' knowledge base to be made to address issues that HAVE been figured out, some sort of trouble-shooting forum that breaks things down by area/issue, AND for those problems to be fixed in the following releases. Maybe even some sort of step-by=step diagnostic tree.
[I]**Displays:**
HowTo:  Open:  16:9 Display acting like 4:3
HowTo:  Open:  Display changes settings at random
HowTo: Closed: Proper installation of ATI's latest driver[/I]

I plan on sticking with Ubuntu, even with the headaches. At least for now. Hopefully they will become fewer and farther between! The above is just my "opinion". Thanks for reading my take/rant. And sorry for the length...:oops:

---

### Post by albinootje on 2009-01-12
> **cygnus-X1 said:**
> For me, solid A/V editing and games. (yes, I'm looking at Kino.)

I keep on reading that Kino is good for getting the raw material from the DV tapes.
Many years ago a friend of mine told me :
I do the capturing with Kino in Linux, then the video editing in Adobe Premiere in MS-Windows, and then the rendering in Linux.

For running games in Linux, check Cedega and CrossOverGames.
And see : 
[http://www.linuxgames.com](http://www.linuxgames.com)
[http://www.happypenguin.org](http://www.happypenguin.org)
[http://www.playonlinux.com/en](http://www.playonlinux.com/en)
> 
I'ld love to see a 'HowTos' knowledge base to be made to address issues that HAVE been figured out, some sort of trouble-shooting forum that breaks things down by area/issue, AND for those problems to be fixed in the following releases.


Post that on [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) or better check whether someone else already did that.

---

### Post by 37fleetwood on 2009-01-12
You know, other than the time I deleted the dock, I havent had any problems.[IMG]http://i14.photobucket.com/albums/a315/hotshot66/gif/confused2.gif[/IMG]
there have been a few things I simply didn't know how to do and had to ask but everything else worked.
I have to admit that for quite some time I used Puppy Linux so I knew all my hardware was up for Linux. I did make the transition from an ATI video card to a Nvidia card but just figured it was cheaper than a copy of Vista.
Intrepid Ibex installed with no issues, compiz worked without any fuss, virtually everything. the only issue I have is that there seems to be no really good DVD authoring software. there are a few out there but they aren't as good and as easy as some of the Windows ones and the Windows ones don't work in wine, so I have to reboot into xp once in a while to make a DVD, no big deal.
I just got done downloading Windows 7 and installing it on a small hard drive and no matter what they do it's still Windows. it wouldn't find my sound card which is a fairly common one, it wouldn't accept the drivers that were fine in xp and couldn't find any on line. it came with no software to speak of and wouldn't do much more than let me play mahjong and surf the web as long as I didn't want to go anywhere that wanted to play a video.
my wish for linux is that more and more people would switch to it and more development would take place on a grand scale and guess what... my wish is coming true! every day Linux gets better while the general consensus is that Windows is getting worse.
I don't think it is as easy as saying Linux is going to grow and take over Windows' top spot, or Windows is going to squash Linux and it will never be great. I think it is going to be just where we are, some people will stay with Micro$oft and be very comfortable whether Linux would do a better job or not and others will use Linux. sadly Micro$oft doesn't see that there is room for more than one alternative to them. if they would embrace the competition everyone would benefit! I'm reminded of the railroads in the '20's, New York Central and Pensylvania both had trains that mede the same run and they both won playing on the competition. kinda like a football game. what fun would it be if you went to a game and the other team had been disqualified on a technicality before the game even started? sadly this is what Micro$oft is trying for. think about where Coke would be without Pepsi, people love going around and playing on a friendly rivalry. Windows is not horrible, some of the corporate philosophy is, but Windows serves a purpose and Linux gets a lot from Windows whether we like it or not. I'm curious to see where it goes, with Windows 7 looking like it coppied some stuff from KDE, this has to be a first. Linux has played catch up for long enough. now that Linux isn't behind it will be fun to see where it goes, it is easy to make cheap knockoffs but when everyones on the same page both sides will have to come up with new stuff on their own. I can't wait to see what the future of Linux holds for us. KDE4 and Compiz-Fuzion were a shot across the bow for Microsoft, and they know it. ask the people who tried "Mojave". they're not the only option anymore, people want more.
sorry I went on so long.
[CENTER][IMG]http://i14.photobucket.com/albums/a315/hotshot66/gif/createphp.gif[/IMG][/CENTER]
Scott8)

---

### Post by albinootje on 2009-01-12
> **37fleetwood said:**
> 
I did make the transition from an ATI video card to a Nvidia card but just figured it was cheaper than a copy of Vista.

Hmmm. Interesting observation! :)

---

### Post by Fenris_rising on 2009-01-12
I do think the OP gave a useful account of the problems he had. What ever the rights or wrongs of it it is a more useful goodbye because of his observations which may help you smart programming types 'tweak', if required, the areas mentioned. I have only been using Linux for 6 months on my main PC and am very pleased I made the change. My old laptop is still windows XP despite trying several Linux distro's mainly due to it's hardware make up being 'made for windows' Now It is in retirement as I have a 904 EEE PC which within 20 minutes of opening the box had it's XP os swept aside for Ubuntu 8.04.1 What an amazing combination! My PC has also gone down with a busted PSU so the 3e is working very hard. Now with my 3e I have been more daring in my use of terminal to install/remove software. Play around with this that and the other and much of what I needed to learn to apply to my use has been learned here either by searching the forum or if I really was lost or needed further clarification I could ask. I changed from Windows because it restricted my freedom to mess with my PC's hardware and the long term stability security issues. On the whole I liked win98 and XP but until I got Linux I was never able to really make my desktop 'mine' and the functionality therein. Also Linux seems more forgiving if you delve into it's guts. I have perhaps been lucky in the fact that but for a few minor issues at the beginning my change has been smooth and functional but others have not been so lucky and this will probably remain the norm for some time yet. So with that in mind it would be nice if all the members of this thriving, growing, community pulled together in a consistent positive manner to posts such as the OP's due to it's informative view point and content. More over the same attitude would be useful even to those who do 'troll?' Yes it's annoying at times if it seems ill informed and they haven't given it a fair go but the negative attitudes and posted replies do little to enhance this great community's image. I have tried Linux a few times on and off between 1995 and 2008 with only partial success. I asked questions, I tried fixes but ended up back on windows because at that time Linux was beyond me. But I also new my limitations so I stayed schtum! Now It's easier to a point and because it works I can learn at a comfortable rate. My new best friend is CLI even if I need to spend some time in here looking for the 'how to' for my latest install/tweak. My biggest fear is once I am happy everything is as I want it Linux will be stable for so long I will have forgotten how to do everything by the time it needs cleaning up/new hard drive/ a re install. 

Have I said enough? :D

regards

Fenris

---

### Post by rasmus91 on 2009-01-22
> Even with just the password Linux is more secure than Vista with all its so called security enhancements!

Security? Yeah totally, It is 99.99% sure of preventing the user of customizing anything, and also from enjoying sitting behind the screen...

---

### Post by Linuxforall on 2009-12-07
> **tjwoosta said:**
> why do people insist on making destructive threads like this?


do you really expect us to try and convince you to stay or something?

if you want to quit using linux, then quit!

if you really think you will have a better experience with windows, then go back to windows and leave us alone

but why make a thread about it on the ubuntu forums?

is it just to &!$$ people off?

is it to sway newcomers from trying?

is it so you can feel justification in your decision to leave? 


wait, whats that, your thinking that you made this post in an attempt to get poeple to recognize the issues so they can get fixed

well thats just plain stupid

thats what bug reports, and ubuntu brainstorm are for

also, if that were the case, why would you title it "farewell linux and ubuntu"!

so #$&% off and find somewhere else to whine

Good old attention seeking, if you make a similar one at MS forums, all they will tell you is don't let the door hit you hard on your way out.

---

### Post by Tamlynmac on 2009-12-07
> Linuxforall
Good old attention seeking, if you make a similar one at MS forums, all they will tell you is don't let the door hit you hard on your way out.

Seriously, You dredged up this almost one year old thread - just to make that statement? Especially, with  [Ms_Angel_D]("http://ubuntuforums.org/member.php?u=416115") and the T&E team trying to clean up the T&E.

Hopefully the mods will closed this thread or move it to recurring discussions.

---

