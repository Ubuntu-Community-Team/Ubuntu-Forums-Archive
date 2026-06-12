---
title: "Ubuntu review - beyond the hype"
date: 2008-01-03
forum: Testimonials &amp; Experiences
---

### Post by mdklnxtps on 2008-01-03
I have just uploaded my Ubuntu review, you can find it here:
[Ubuntu - beyond the Hype]("http://www.mandrake.tips.4.free.fr/ubuntubeyondthehype.html")

Any comments, corrections, flames or praise, please leave them in this topic. Note that I will ignore all comments with flames...

If you find any factual error I'll be happy to stand corrected and update my review.

I hope you'll enjoy the read,
aRTee

---

### Post by snakeeyes on 2008-01-03
I have to say one thing, even I don't realise how Ubuntu is easier than other distros. No flames please I use Kubuntu. I have tried many distros and they r all as easy, infact openSUSE is way easier than Ubuntu. Also I agree that Ubuntu doesn't always work, some hardware works better on other distros like Mandriva, Fedora, or openSUSE. All Linux distributions r very good, all that matters is ur tastes and preferences and the hardware u use.

I think the reason Ubuntu has so much popularity is because Ubuntu advertises itself whereas other distros don't.

---

### Post by gleam on 2008-01-03
Nice review. IMHO, ubuntu belongs to the group of easier linux distros along with mandriva, pclos, suse, fedora, sabayon, debian, mint, mepis... Some people may find ubuntu the easiest, while others may find some other distro the easiest. As they say, YMMV. 

I just wanted to comment on this passage near the end of the review:
***I think perhaps many Debian users have found a new home over the past few years in Ubuntu - based on Debian but with lots more convenience built in and more up to date; some of these users may have been genuinely surprised at the ease with which most things work, and from there to all the hype it only takes a very tiny but vocal minority. From the joke: Ubuntu is an ancient word that means: "I can't configure Debian", perhaps this is closer to what's going on: "I'm in the mood for Debian but with more convenience and more up to date and I don't have as much time".***

What I, as a long-time debian user, find dubious in this passage is the suggestion that ubuntu would be more convenient and more up to date than debian. The reviewer is so convinced of the truth of this statement that he tells it twice. Obviously the reviewer is thinking of debian "stable". But only few home users actually use debian "stable" on their desktops -- it's more suitable for servers. Most people who use debian as a desktop, use debian "testing" (or even debian "unstable" if they like to live dangerously). And I'd say that ubuntu isn't really much more convenient or any more up to date than debian "testing". In fact, some pieces of software are more up to date in debian "testing" than in ubuntu, because debian "testing" is a "rolling release" that receives updates every day.

But you don't just have to take my word for it. You can install the latest weekly snapshot of debian "testing" and see for yourself if debian really is less convenient and less up-to-date than ubuntu. You might be surprised. ;)
[http://www.debian.org/devel/debian-installer/index.html](http://www.debian.org/devel/debian-installer/index.html)

I'll also let you in on a secret: you can grab some more up to date packages from debian "unstable" while most of your system stays safely in debian "testing". It's easier than you'd think. Here's how to do it:
[http://forums.debian.net/viewtopic.php?t=15612](http://forums.debian.net/viewtopic.php?t=15612)

Perhaps it's true that a lot of former debian users have found a new home in ubuntu, but I think it's equally true that a lot of new users have first tried ubuntu and then moved on to debian proper. I also think that debian's reputation as a difficult to use distro is nowadays undeserved. Many ease of use features that the new users admire in ubuntu come directly from debian. I'd like to urge people to try debian, so they could tell what is really original and worth praising in ubuntu -- in other words, what is really beyond the hype. :)

---

### Post by Nano Geek on 2008-01-03
> **snakeeyes said:**
> I have to say one thing, even I don't realise how Ubuntu is easier than other distros. No flames please I use Kubuntu. I have tried many distros and they r all as easy, infact openSUSE is way easier than Ubuntu. Also I agree that Ubuntu doesn't always work, some hardware works better on other distros like Mandriva, Fedora, or openSUSE. All Linux distributions r very good, all that matters is ur tastes and preferences and the hardware u use.

I think the reason Ubuntu has so much popularity is because Ubuntu advertises itself whereas other distros don't.I haven't seen any official Ubuntu advertising.
Could you show me a specific example?

---

### Post by Nequeo on 2008-01-03
Couple very minor points.

The reason why 'vim' seemed odd was because by default the recent Ubuntu's install the package 'vim-tiny'. I think this was done to save space on the install CD. "apt-get install vim" will give you the regular version. 

Also, for a root terminal, I think it is better to use 'sudo -i' rather than 'sudo bash'. I think. I believe that 'sudo -i' will initialize root's environment, while 'sudo bash' will give you a terminal with root privileges, but your current user's environment. Please correct me if I am wrong.

---

### Post by mdklnxtps on 2008-01-03
Thanks to all of you for the comments and feedback.

Snakeeyes, yeah, I agree, most Linux distributions are quite close in terms of how easy they are to use. It's just that I have seen told time and time again how people's problems with Linux wouldn't have been if only they had used Ubuntu...

About OpenSUSE, on my hardware it was almost DOA. Read my review about it, it was really tough to get to a usable state - and that on Novell Certified hardware...
No beginner would have managed some of the problems. (For starters: not seeing all of the screen, just the left top, and not being able to get to the panel - no scrolling either...)

> I think the reason Ubuntu has so much popularity is because Ubuntu advertises itself whereas other distros don't.

Well, lots of distributions advertise themselves as best they can. The one big thing Ubuntu has is ShipIt. 
And naturally, lots of people making big claims, all over the web.


Gleam, you wrote:
> What I, as a long-time debian user, find dubious in this passage is the suggestion that ubuntu would be more convenient and more up to date than debian. The reviewer is so convinced of the truth of this statement that he tells it twice.
Nah, don't sweat it. It's just that I still don't see a good reason for all the hype of Ubuntu, and so I was trying to make some lighthearted comment about it - I didn't mean to imply any recent firsthand experience wtih Debian, nor that this is solid fact. If anything, take it tongue in cheek, it's just a reference to the Debian joke I started the review out with...

Anyway, thanks for the info on Debian, I'm sure someone will put it to good use.


Nequeo, you wrote:
> The reason why 'vim' seemed odd was because by default the recent Ubuntu's install the package 'vim-tiny'. I think this was done to save space on the install CD. "apt-get install vim" will give you the regular version. 
Thanks for the info.
But, why was there both vi _and_ vim then? And would that mean that vim-tiny has the executable vim, and the package vim also has the executable vim?
If so, that's interesting, I'd never have found that out by myself, so it's good to know. I'm actually not close friends with vi (in any flavour), I just wanted to note the few things I noticed...

> for a root terminal, I think it is better to use 'sudo -i' rather than 'sudo bash'. I think. I believe that 'sudo -i' will initialize root's environment, while 'sudo bash' will give you a terminal with root privileges, but your current user's environment.
Well, I guess that depends on what you want to do. If you want to use the root privileges, 'sudo bash' should be fine, as should 'sudo su', alongside 'sudo -i'. If you want to figure out if there's a problem with root rights in your settings (supposing something is giving you problems, and you want to rule out access rights), you will want to use sudo bash or sudo su.
I'm not familiar with sudo -i, but from your description I think it is equivalent to 'sudo su -'...

---

### Post by Nequeo on 2008-01-03
> 
Thanks for the info.
But, why was there both vi _and_ vim then? And would that mean that vim-tiny has the executable vim, and the package vim also has the executable vim?
If so, that's interesting, I'd never have found that out by myself, so it's good to know. I'm actually not close friends with vi (in any flavour), I just wanted to note the few things I noticed...


There is only vim, but it is either aliased or symlinked (I never bothered to check, and don't have an Ubuntu handy right now to confirm) as 'vi' as well. 

I think that most distributions do this, so I have the habit of just typing 'vi'. But I have been caught out by this before, as my University has some old SunOS machines that do have both vim and the original vi installed. 

If you check out the files installed by 'vim-tiny' and 'vim', you'll see that one adds /usr/bin/vim.tiny and the other adds /usr/bin/vim.basic, so there's no conflict there. Pretty sure the Debian 'alternatives' system is used to pick between them.

I could talk about vim all day, really... But I'd better not. 

Cheers,

---

### Post by Nunu on 2008-01-04
> **asjdfwejqrfjcvm msz34rq33 said:**
> I haven't seen any official Ubuntu advertising.
Could you show me a specific example?

conical had a billboard up next to a busy high way for one :)

---

### Post by mdklnxtps on 2008-01-04
Hmm, more of a mystery coming up....

> **Nequeo said:**
> There is only vim, but it is either aliased or symlinked (I never bothered to check, and don't have an Ubuntu handy right now to confirm) as 'vi' as well. 

Interesting, so I just did a chroot to my Ubuntu root partition, and lo and behold, I got the following:
```

root@madeira:/# ls -l /usr/bin/vi
lrwxrwxrwx 1 root root 20 2007-12-07 22:59 /usr/bin/vi -> /etc/alternatives/vi
root@madeira:/# ls -l /usr/bin/vim
lrwxrwxrwx 1 root root 21 2007-12-07 22:59 /usr/bin/vim -> /etc/alternatives/vim
root@madeira:/# ls -l /etc/alternatives/vi
lrwxrwxrwx 1 root root 17 2007-12-07 22:58 /etc/alternatives/vi -> /usr/bin/vim.tiny
root@madeira:/# ls -l /etc/alternatives/vim
lrwxrwxrwx 1 root root 17 2007-12-07 22:58 /etc/alternatives/vim -> /usr/bin/vim.tiny
```

BUT...!!
If I edit some file, /etc/X11/xorg.conf or so, by doing:
```
vi /etc/X11/xorg.conf
```
and I type 'i' to go into edit mode, then use the arrow keys, each key will insert a character (A, B, C or D, depending on which arrow key I use) instead of moving around in the file.
If however I start by doing:
```
vim /etc/X11/xorg.conf
```
I can go into edit mode by hitting 'i' and still navigate with the arrow keys.

But Wait! If I started with 'vi' instead of 'vim', go into insert mode, use the page up or down key, then use the arrow keys, they will work. I can then type directly where the cursor is. After typing I first have to use pgup/pgdown to have properly working arrow keys. Don't even get me started on the behaviour of the end and home keys...

Very weird, but in any case, I was wrong that Ubuntu comes with the old 'vi'. I was right that it's better to use 'vim'... No clue why, or how exactly...

---

### Post by Nunu on 2008-01-04
Never even noticed that... Interesting :)

---

### Post by nosrednaekim on 2008-01-04
the problem with the adept taskbar icon floating, as well as the goofy pager in kubuntu are actually a problems with compiz-kde interaction (compiz is rather GNOME oriented). check out the compiz-kicker package (not sure if its in the repositories for Gutsy, but it is for hardy) and is available on kde-look as well.

---

### Post by welkiner on 2008-01-06
aRTee, thank you so much for this great review.
Not that I agree with all of your conclusions, but I appreciate so much the hard work and due diligence that went into this review.  It's the best review that I have seen in a long time. 
 
I (and I would think many others) am so tired of reviewers loading a livecd and writing a review, or at most, installing to hard drive and now they're an expert.

As a Linux user since 93, I found Ubuntu to be all hype and not much more until Dapper, at which point I bit the bullet and got onboard.  Less than a year later I discovered an Ubuntu derivative called Linux Mint.  According to most reviews Mint is simply Ubuntu with codecs and plugins.  Obviously they have not used it, or they would be talking about it's stability and speed which go much much deeper than a remaster.

After my initial negative opinion of Ubuntu, I have to admit that Ubuntu is an amazing distribution, which has had a great and positive impact on Linux.  And like you, (after a great deal of reluctance) I agree that for a desktop computer "sudo" is much better than an active root account.  Like you, (and Linus) I feel Gnome does limit my options, but I do like the Gnome look and I don't like the cluttered look of most KDE desktops...But I do like that KDE functionality!  (Mint KDE is the cleanest I've found)

aRTee, once again, thank you for the great review.

-welkiner

---

### Post by yman on 2008-01-07
part of a comment I made [Here:]("http://www.bitburners.com/articles/the-best-desktop-linux-distribution-of-2007/3894/")
> easy installation: 1 live CD, rather than 5 installation CDs. this is what made me choose it over Fedora Core, openSUSE, freeBSD, and Solaris. during installation I only had to deal with stuff that I felt I should deal with.

good enough choices of default packages, at least for someone unaccustomed to the alternatives. there may have been better choices, but these feel good enough to me.

easy to get: ShipIt, as well as the downloads everyone offers. the ability to get official copies is a major plus to someone used to relying on official releases from big-money corporations. getting official copies for free is a big plus for a cheapskate like me.

when it comes to free VS proprietary, it chooses the option that gives the best user experience, while trying not to force users to use proprietary software. they also try to limit it to show-stopper issues like drivers.

software management is pure bliss.

it is easy and convenient for me for just about every use I have.

for some odd reason I just plain love it. same thing happened with GMail making email a great experience, or Firefox making me a web addict. some things just feal right and using them is pure pleasure. I can't always tell people why, and it is possible, perhaps even likely, that something better would come along (Konqueror on KDE 4.0 looks like it has the potential).

I've been using Ubuntu since 6.06, and to me it did live up to the hype (except for a problem with my Ethernet card). maybe it's just because it's the first I tried, but my main discomfort came from it being too familiar. I was hoping for a totally different interface than Windows, and a different concept for file-systems.

for a while I was considering both KDE and GNOME, but I felt more comfortable in GNOME, mainly because FF looked better in it and I didn't like Konqueror. also, I was having problems with the KDE System Settings, or maybe it was KControl. I did like that in KDE I could at least have the application menu on the panel similar to Mac OSX. KDE in general felt a bit less good-looking and more cluttered. I did like KDE on Sabayon Linux 3.1 (I think it was that release. 3.x anyway).

as people often say, it's a matter of personal preference, and it seems that the largest chunk of people find that Ubuntu suits them best. the rest (the majority of ~70%), find that other distributions are better suited for their needs. Ubuntu suits my needs almost perfectly. also, I don't see why use of the CLI is relevant, since Ubuntu seems to have made the exclusive use of the GUI a goal. it seems to me that if a user ever needs to access the CLI, that is a shortcoming of Ubuntu. if Ubuntu isn't so good with the CLI, that shouldn't be held against it either. obviously I mean that one shouldn't say Ubuntu is a bad OS because it has a bad CLI, but could say that it is not best suited for those who wish to use the CLI. this last comment is really for reviewers in general, who seem to many times declare something as a bad product based on usages it was not designed or meant for.

And we all know what they really mean when they say "Linux for human beings", so why not just give that a rest? it's a marketing slogan and that's all. it's not meant to be derogatory towards users of other distributions, but to appeal to users of proprietary, closed-source operating systems. it is also not saying anything about anyone other than itself. it's not saying "unlike other distributions, we are Linux for human beings (ie, casual home users)"

---

### Post by mdklnxtps on 2008-01-08
welkiner, thanks for your compliments.
It's nice to see my work is appreciated, and more so that it's actually noticed that such a review is really a _lot_ of work.
> Not that I agree with all of your conclusions
that's fine, as long as you don't go in the direction that Linux is not ready for your desktop. Remember: Linux is ready for all desktops, but some desktops are just more ready for Linux than others.


yman, thanks for your feedback.

> easy installation: 1 live CD, rather than 5 installation CDs. this is what made me choose it over Fedora Core, openSUSE, freeBSD, and Solaris. during installation I only had to deal with stuff that I felt I should deal with.
 
 good enough choices of default packages, at least for someone unaccustomed to the alternatives. there may have been better choices, but these feel good enough to me.
 
 easy to get: ShipIt, as well as the downloads everyone offers. the ability to get official copies is a major plus to someone used to relying on official releases from big-money corporations. getting official copies for free is a big plus for a cheapskate like me.
 
 when it comes to free VS proprietary, it chooses the option that gives the best user experience, while trying not to force users to use proprietary software. they also try to limit it to show-stopper issues like drivers.
 
 software management is pure bliss.
 
 it is easy and convenient for me for just about every use I have.

Well, apart from the ShipIt part, which in cases (mine for instance) takes 6 weeks or more, the exact same can be and is said about: Mandriva, PCLinuxOS, Knoppix, etc.

> I've been using Ubuntu since 6.06, and to me it did live up to the hype (except for a problem with my Ethernet card).
So, it didn't live up to the hype, you had a problem. It only needs a single issue, and not on your hardware, but on anyone's hardware, to not live up to the hype.
Many big/popular Linux distributions have been hyped to be the one that will take over (or at least break into) the average desktop (which is today running MSWin as it was way back when as well) (this is the wishful thinking part), because (here comes the claim) it 'Just Works'.

Well, some Mandriva versions have done that for me when it was still Mandrake. Not without fiddling at all - but with less fiddling than MSWin for instance. That on other hardware and for other users, this was not quite the case is exactly the point - it invalidates the claim that it just works. You yourself had issues with the nic, so it didn't just work...

This is not a bad thing per se, but my point is that the claims out there are often very exaggerated, the one about how Ubuntu (or any other Linux) just works is the most common one.

On a side note, hardware functionality is largely dependent on the kernel, and though some patches may be different at some point in time for the various distributions, it's all GPL2 code and all gets merged, so nominally, most distributions can perform more or less the same on the same hardware...
(yeah I know, auto configuration differences and such...)

> my main discomfort came from it being too familiar. I was hoping for a totally different interface than Windows, and a different concept for file-systems.
Try ratpoison for something different in interface matters. Or E17. Or metisse - sure it's kde with a different window manager, but it is very different. Or try some of the other ones. 
A different concept for file-systems? You mean: for file management...?

>  for a while I was considering both KDE and GNOME, but I felt more comfortable in GNOME, mainly because FF looked better in it and I didn't like Konqueror. also, I was having problems with the KDE System Settings, or maybe it was KControl. I did like that in KDE I could at least have the application menu on the panel similar to Mac OSX. KDE in general felt a bit less good-looking and more cluttered. I did like KDE on Sabayon Linux 3.1 (I think it was that release. 3.x anyway).
? Are you saying that on the exact same system, FF looked different on KDE than on GNOME?
If so, that is new to me, I didn't know that was possible...
Otherwise, I find the application menu on the panel braindead, but I don't like the whole desktop metaphor so much anyway...
If you have a large screen, the panel is too far away from your app, so too far to move the mouse. If you have a smaller screen, your app should be maximised and the panel is taking away expensive real estate from your application(s). Yeah, my panels are hidden, actually they are on the compiz-fusion widget layer, not even on auto-hide but only there when called by keystroke...

> as people often say, it's a matter of personal preference, and it seems that the largest chunk of people find that Ubuntu suits them best.
I beg to differ. I think there is no preference for most people, since most people don't try out one distribution after another, most people don't have time for that.
So they wouldn't know if Ubuntu suits them best; it might suit them better than some other distribution they have seen/tried, but yet another distribution they didn't try might suit them even better.
But none of that really matters.
What I want to ask you: why do you think the 'largest' chunk of people are on Ubuntu? I'm not sure of that... How would you know?
I have yet to see any useful poll or other way to measure that. There are no real numbers of total amount of Linux users as a whole either, for similar reasons.

> also, I don't see why use of the CLI is relevant, since Ubuntu seems to have made the exclusive use of the GUI a goal. it seems to me that if a user ever needs to access the CLI, that is a shortcoming of Ubuntu. if Ubuntu isn't so good with the CLI, that shouldn't be held against it either. obviously I mean that one shouldn't say Ubuntu is a bad OS because it has a bad CLI, but could say that it is not best suited for those who wish to use the CLI. this last comment is really for reviewers in general, who seem to many times declare something as a bad product based on usages it was not designed or meant for.
If this is really your position, then Ubuntu except on a recent Dell machine fails miserably by your own standards, due to the way to get dvd playback working...
BTW I've never seen it claimed that Ubuntu is not for those who want to use the CLI. I guess I missed that memo. (I think you may want to inform Mark Shuttleworth about it too, I doubt he knows... :) )
And yes, if the CLI is bad, the OS is bad. Sorry - I couldn't resist... BTW I don't think the CLI on Ubuntu is bad, it just has some unexpected crappy settings. It's still bash, and you'd still have to pry it from my cold, dead hands...

Besides, it's Linux, so to use the CLI is definitely something it should be designed for.

> And we all know what they really mean when they say "Linux for human beings", so why not just give that a rest? it's a marketing slogan and that's all. it's not meant to be derogatory towards users of other distributions, but to appeal to users of proprietary, closed-source operating systems. it is also not saying anything about anyone other than itself. it's not saying "unlike other distributions, we are Linux for human beings (ie, casual home users)"

Well, to me, interpreting English (I'm not a native speaker, as you might have guessed) as best I can, the slogan "Linux for human beings" infers, by the use of 'for', that there may be other targets than the use by human beings, but _this_ particular Linux distribution is not targeted at that other audience...
If they'd want to appeal to users of proprietary, closed systems, shouldn't it be: "The system for human beings", or "The open system for human beings" if you want to push the concept of openness..?
Or at least it could be "Linux, for human beings" or so?
Maybe an English major could weigh in here. To me, even after your explanation, it still comes across as implying that other Linux systems are not for human beings... 
As you said, it's a slogan, no biggie...

---

### Post by jrusso2 on 2008-01-08
> **Nunu said:**
> conical had a billboard up next to a busy high way for one :)

Wow that's really cool.  Where was that bill board at I would have loved to have seen that it would have made my day.

---

### Post by Eddie Wilson on 2008-01-09
Nice review. I usually don't read reviews for the reason there are so many different elements that can be at work when one installs a distro. You can have hardware issues which is going to always happen, and then you have personal preference issues which are going to always happen and these are highly subjective. I've installed Ubuntu on several machines without a problem at all, and also I've installed other distros on machines that did not work well with what was in Ubuntu. It was always hardware related. There are about a billion different machine setups nowadays.  Sometimes the personal preference of the user would play in. Anyway there are a lot of good linux distros out there and there is no harm in using one that is not your main distro. I don't like to talk down any distro so I wouldn't be a good reviewer. Besides, I may have the only computer like mine in the world.:) So how could I be fair?
Thanks,
Eddie

PS: Ubuntu is my main distro, I also boot Mepis for my Kde fix.

---

### Post by SeanHodges on 2008-01-09
Good review, well done.

To shed some light on the problem with Majesty: The binary you were trying to run was compiled for a 32bit system, whilst you had installed 64bit Ubuntu. The joys of closed-source I'm afraid :(

---

### Post by mdklnxtps on 2008-01-09
Eddie Wilson, thanks for the heads up and no, if you don't like to talk down a distro that doesn't mean you're not fit to be a reviewer... My most negative review was openSUSE 10.3, but that's only because I didn't actually write a review about Ubuntu when I first tried it...

I quite liked it now though. And I believe it's a good choice for for instance Dell to offer preinstalled.

Sean, thanks.
Yeah, I figured out that that was the reason - my problem was just that I didn't realise 32 bit compatibility is so 'hard' on Ubuntu - it was much easier (i.e.: absolutely nothing to do) on openSUSE and Mandriva... which was why I was puzzled and didn't realise that that was the issue, I thought 32 bit code should just run, based on my past experiences...
You have to admit though, the file command showing that the program is executable and the response on trying to execute it being: no executable - that's really far out...

Completely forgot...
nosrednaekim, thanks for the comment, have to try that. Strange that those packages don't get installed by default as dependencies of kde-desktop or so...

welkiner, thanks for actually joining this forum to give me some feedback. It's much appreciated.

---

### Post by mikewhatever on 2008-01-16
Very nice and comprehensive. I wonder how much time did it take to complete. In the beginning, I was a bit worried you'd start bashing, but read on and found nothing of the sort. Personally, I absolutely detest the hype around Ubuntu. Why the hell do people need to worship one thing and hate the other? Yet, since so it is, the hype is good, be it Ubuntu, Mandriva any other distro. It draws attention to Linux as an alternative, introduces people to the world full of good OSs, most of them free, and make them wonder. To be fare, I really think the hype is based less on the quality of Ubuntu, but more on things like [bug number 1]("https://launchpad.net/ubuntu/+bug/1").

Thanks for the review.

---

### Post by yman on 2008-01-17
> **mdklnxtps said:**
> 
yman, thanks for your feedback.

you're welcome

> 
Well, apart from the ShipIt part, which in cases (mine for instance) takes 6 weeks or more, the exact same can be and is said about: Mandriva, PCLinuxOS, Knoppix, etc.


the ShipIt part was important to me. for other users, like experienced Linux users, I think it wouldn't be. for a cheapskate novice like me, it is.

> 
So, it didn't live up to the hype, you had a problem. It only needs a single issue, and not on your hardware, but on anyone's hardware, to not live up to the hype.
Many big/popular Linux distributions have been hyped to be the one that will take over (or at least break into) the average desktop (which is today running MSWin as it was way back when as well) (this is the wishful thinking part), because (here comes the claim) it 'Just Works'.

Well, some Mandriva versions have done that for me when it was still Mandrake. Not without fiddling at all - but with less fiddling than MSWin for instance. That on other hardware and for other users, this was not quite the case is exactly the point - it invalidates the claim that it just works. You yourself had issues with the nic, so it didn't just work...

This is not a bad thing per se, but my point is that the claims out there are often very exaggerated, the one about how Ubuntu (or any other Linux) just works is the most common one.

On a side note, hardware functionality is largely dependent on the kernel, and though some patches may be different at some point in time for the various distributions, it's all GPL2 code and all gets merged, so nominally, most distributions can perform more or less the same on the same hardware...
(yeah I know, auto configuration differences and such...)


then I guess we didn't listen to the same hype (I actually don't know what the word "hype" means, so I may be misusing it). I decided to try Ubuntu after reading a review in a general-audience windows-oriented computer section of a popular web portal that ended with the conclusion that it's not perfect, but good enough for him to keep using alongside XP and OSX. I never heard of it before.

> 
Try ratpoison for something different in interface matters. Or E17. Or metisse - sure it's kde with a different window manager, but it is very different. Or try some of the other ones. 


might be too late for that. at the beginning I tried everything I heard of, but trashed my system a few times in the process. since then I've learned caution.

> 
A different concept for file-systems? You mean: for file management...?


a flat filesystem. everything is under the root directory, so to speak. special self containing, cross-linked package files for application software. exclusive use of labels for organization purposes. heavy reliance on search.(I'm not sure that's exactly what I had in mind. this was over 1.5 years ago, and I haven't thought about it since) I thought something like that would solve all my organizational problems.

needless to say, I was disappointed in Linux for not using such a scheme.

> 
? Are you saying that on the exact same system, FF looked different on KDE than on GNOME?
If so, that is new to me, I didn't know that was possible...


it did. looked butt ugly, too. maybe it's because I turned on some sort of GNOME compatibility thing I can hardly remember anymore.

> 
Otherwise, I find the application menu on the panel braindead, but I don't like the whole desktop metaphor so much anyway...
If you have a large screen, the panel is too far away from your app, so too far to move the mouse. If you have a smaller screen, your app should be maximised and the panel is taking away expensive real estate from your application(s). Yeah, my panels are hidden, actually they are on the compiz-fusion widget layer, not even on auto-hide but only there when called by keystroke...


I like it. it works for me. and I don't have a huge screen.

> 
I beg to differ. I think there is no preference for most people, since most people don't try out one distribution after another, most people don't have time for that.
So they wouldn't know if Ubuntu suits them best; it might suit them better than some other distribution they have seen/tried, but yet another distribution they didn't try might suit them even better.
But none of that really matters.
What I want to ask you: why do you think the 'largest' chunk of people are on Ubuntu? I'm not sure of that... How would you know?
I have yet to see any useful poll or other way to measure that. There are no real numbers of total amount of Linux users as a whole either, for similar reasons.


that figure was based on a survey of 15,000 attendees at a Linux conference some time ago. I guess it's irrelevant. actual figures, or boasting numbers wasn't my point. I'm just trying to say that as popular as Ubuntu may be, even more people prefer a different distro. you seem to disagree on the question of whether it is choice, or something else, which determines who uses what.

I think that is characteristic of underdogs who try to make excuses for their failings rather than fix what they are doing wrong.

> 
If this is really your position, then Ubuntu except on a recent Dell machine fails miserably by your own standards, due to the way to get dvd playback working...


I guess so, but I wouldn't know.

EDIT: I misunderstood you. I thought you were talking about problems with Dell pre-installed machines.
there is no need for a command line. just add the medibuntu repository (with GUI tools) and install libdvdcss from Synaptic. no biggie.
it's still a failure because it's not as easy and obvious as it should be. just be accurate about what the failure is.

> 
BTW I've never seen it claimed that Ubuntu is not for those who want to use the CLI. I guess I missed that memo. (I think you may want to inform Mark Shuttleworth about it too, I doubt he knows... :) )


I guess I'm wrong on that one.


> 
And yes, if the CLI is bad, the OS is bad. Sorry - I couldn't resist...


Are you serious? a screw driver is bad cause you cant drive it to work?

> 
BTW I don't think the CLI on Ubuntu is bad, it just has some unexpected crappy settings. It's still bash, and you'd still have to pry it from my cold, dead hands...


I've seen many people say this, but I still don't get it - why should I take your bash away from you, when I can get my own free copy?

> 
Besides, it's Linux, so to use the CLI is definitely something it should be designed for.


Linux is a kernel. I don't think it should have any preferences about which UI is used.

as to distros, if using the CLI is part of what they are designed for, then yes. but if they are intended to be self sufficient on GUI alone, then no. you seem to expect that your basic needs are universal, when they are definitely not. I'm living proof. if I could perform file operations (edit, copy and paste, etc) with root access from the GUI alone, from my normal account, I wouldn't need the CLI. I would also find it more convenient. same goes for trasnferring user and group ownership over files. it can be implemented. this isn't a limitation of GUI interfaces, and I would find it more convenient.

> 
Well, to me, interpreting English (I'm not a native speaker, as you might have guessed) as best I can, the slogan "Linux for human beings" infers, by the use of 'for', that there may be other targets than the use by human beings, but _this_ particular Linux distribution is not targeted at that other audience...
If they'd want to appeal to users of proprietary, closed systems, shouldn't it be: "The system for human beings", or "The open system for human beings" if you want to push the concept of openness..?
Or at least it could be "Linux, for human beings" or so?
Maybe an English major could weigh in here. To me, even after your explanation, it still comes across as implying that other Linux systems are not for human beings... 
As you said, it's a slogan, no biggie...

"human beings" implies normal users, as opposed to geeks and power users. in other words, Ubuntu is supposed to be easy and straightforward for normal usage (which I find it is). this is opposed to the image in the general public of "Linux" being difficult and for geeks and hackers only.

it's not addressing reality, which is that "Linux" is easy, but the wrong perception of it, and trying to gain more users for itself at the same time. if it would just say "Linux is ready for everyone", then users won't come flocking to it, it won't be visible to corporations, and Canonical won't get support contracts.

---

### Post by mdklnxtps on 2008-02-04
Sorry I took so long to reply here - I actually had other (non-computer related) things that were more important... Yeah, I'm ashamed to have to admit that I have a life... Takes lots of important time away from promoting Linux and Free Software... ;)
Thanks for your feedback, here are some points from my side....

> **mikewhatever said:**
> Very nice and comprehensive. I wonder how much time did it take to complete. 
Since you ask... about all the computer time I could make available during about 3 weeks. That includes all from installing, configuring, web searching to fix things and find out how to, to writing, polishing, screen shot preparation and sorting etcetc.

> In the beginning, I was a bit worried you'd start bashing, but read on and found nothing of the sort. Personally, I absolutely detest the hype around Ubuntu. Why the hell do people need to worship one thing and hate the other? 
Exactly, and why are they so religious about it?
From a logical point of view, Free Software just makes sense. From the same logical point of view, it's not even possible that Ubuntu (and siblings) would be so much better than other Linux distributions, since the code is all available...

> Yet, since so it is, the hype is good, be it Ubuntu, Mandriva any other distro. It draws attention to Linux as an alternative, introduces people to the world full of good OSs, most of them free, and make them wonder. To be fare, I really think the hype is based less on the quality of Ubuntu, but more on things like [bug number 1]("https://launchpad.net/ubuntu/+bug/1").

Thanks for the review.

I disagree on the hype being good - there are too many claims that Ubuntu (and Linux in general) just can't live up to. Just check this subforum, and see how many people give up Ubuntu to go back to Win XP or even Vista.
Which brings me to bug nr 1, which I hadn't seen, and which is absolutely correct - I've been addressing this bug since I started out on my Linux journey...


> **yman said:**
> 
the ShipIt part was important to me. for other users, like experienced Linux users, I think it wouldn't be. for a cheapskate novice like me, it is.

I guess it makes a difference if you have no stable connection and no burner. Else the cost is just some time (online and to burn) - for the disc you can use an RW one...
The big difference of ShipIt is that it allows the people who don't know about Linux/Ubuntu to get it from their friends who do and who can hand out discs.

> 
then I guess we didn't listen to the same hype (I actually don't know what the word "hype" means, so I may be misusing it). I decided to try Ubuntu after reading a review in a general-audience windows-oriented computer section of a popular web portal that ended with the conclusion that it's not perfect, but good enough for him to keep using alongside XP and OSX. I never heard of it before.


That's not what I call hype. That's just one guys experience. And there's nothing wrong with that.

> 
might be too late for that. at the beginning I tried everything I heard of, but trashed my system a few times in the process. since then I've learned caution.

I don't understand how you can trash a system by installing another wm/de on it - as long as you install from the repositories for your system (version and build), this cannot trash the system. You could mess up your home dir, but then a separate user account is easy to set up, so no worries there....


> 
a flat filesystem. everything is under the root directory, so to speak. special self containing, cross-linked package files for application software. exclusive use of labels for organization purposes. heavy reliance on search.(I'm not sure that's exactly what I had in mind. this was over 1.5 years ago, and I haven't thought about it since) I thought something like that would solve all my organizational problems.

needless to say, I was disappointed in Linux for not using such a scheme.

You mean a database file system. I have no idea why that would be better than what we have now, because your database file system couldn't just show you the files flat, it would have to order them... and it would make most sense to do that by various things that you can today also have your files show up as - most simply as per the directory structure, as the files are on your system, but also as per the date, type, etc, which you can do now with the various desktop search engines.

> 
it did. looked butt ugly, too. maybe it's because I turned on some sort of GNOME compatibility thing I can hardly remember anymore.
...
I like it. it works for me. and I don't have a huge screen.

So you don't mind to sacrifice some screen real-estate, whereas I do. 2 different users, 2 different ways to use. All normal I think. (Which is why I don't like GNOME - too much "that's not how you should use this system" going on; btw that's why I feel locked up whenever I have to use Windows, and I doubt I would feel much better on Mac OS X, which I have limited experience with, afaics both are worse than GNOME in the prescribing how to use _your own_ computer.)

> 
that figure was based on a survey of 15,000 attendees at a Linux conference some time ago. I guess it's irrelevant. actual figures, or boasting numbers wasn't my point. I'm just trying to say that as popular as Ubuntu may be, even more people prefer a different distro. you seem to disagree on the question of whether it is choice, or something else, which determines who uses what.

IMHO It's mainstream press (paper and online) that determines mostly what newbies go for. I just know that many longtime users are not on Ubuntu, because most can fix their problems (they are longtime users, so that figures) on whatever distribution they have, and they just stay with what they know (don't we all) unless forced otherwise. (Oh those poor SCO Caldera Linux users...)
But the point I was making is that for many if not most people it is not personal preference to use Ubuntu, because they never tried anything else. Look at this subforum, if Ubuntu doesn't work, people go back to WinXP/Vista.
They rarely say, hey, I'm outta here to check out Fedora/Mandriva/openSUSE because Ubuntu doesn't do it for me.

That's part of the whole overhyped thing, btw...

> 
I think that is characteristic of underdogs who try to make excuses for their failings rather than fix what they are doing wrong.


The point I tried to make is that what you refer to as the failings of other distro's at this point seems to be at least in part that there's less wildly exaggerated claims/hype going on...


> 
I guess so, but I wouldn't know.

EDIT: I misunderstood you. I thought you were talking about problems with Dell pre-installed machines.
there is no need for a command line. just add the medibuntu repository (with GUI tools) and install libdvdcss from Synaptic. no biggie.
it's still a failure because it's not as easy and obvious as it should be. just be accurate about what the failure is.

Ok thanks, didn't know about medibuntu repo.. Where could I have found that, and why is that info not on the standard wiki where the dvd playback info is?


I said earlier: 
And yes, if the CLI is bad, the OS is bad. Sorry - I couldn't resist...
to which you reply:
> 
Are you serious? a screw driver is bad cause you cant drive it to work?

Ehm, well, this was a bad jab at MSWin...
All other OSes that I've worked with have a decent command line.
And I have yet to find the screw driver that I can't drive to work. So far, they all let me, just quietly sat there, whereever in the car I put them, whilst I drove to work. But the one screw driver that refuses to come along on my drive to work, yes, that's a very bad one. Naughty, even.

As for bad CLI, bad OS, all I can say is: yes, a decent CLI is a requirement for _me_ to consider the OS decent, because without a decent CLI you can't do CL scripting, which is like the shopping list you give your assistant - much better in some situations than, say, the tourist in a different language region who's ordering an ice cream by pointing (GUI).

I wrote:
It's still bash, and you'd still have to pry it from my cold, dead hands...
> 
I've seen many people say this, but I still don't get it - why should I take your bash away from you, when I can get my own free copy?

Ehm, no, that's not the joke - the point was that I wouldn't want a system without bash... which some people seem to advocate, wanting all to be possible from the gui and such....

> 
Linux is a kernel. I don't think it should have any preferences about which UI is used.

Ok, I should have written GNU/Linux this once. Which is what I meant. Which is still the basis of Ubuntu. So without CLI it would be quite the abberration...

> 
as to distros, if using the CLI is part of what they are designed for, then yes. but if they are intended to be self sufficient on GUI alone, then no. you seem to expect that your basic needs are universal, when they are definitely not.
No, I don't expect or think that. I just think that like the windows registry, there's a point with deskop linux that one gets/has to use the cli.

> 
I'm living proof. if I could perform file operations (edit, copy and paste, etc) with root access from the GUI alone, from my normal account, I wouldn't need the CLI. I would also find it more convenient. same goes for trasnferring user and group ownership over files. it can be implemented. this isn't a limitation of GUI interfaces, and I would find it more convenient.

That's fine, and I have nothing against that.
But there's a reason why many advanced users like and prefer the cli in many cases. For those users, on a (relatively) general purpose machine, taking away the cli is practically equal to invoking the death penalty for that system... because practically all Linux systems need advanced users to improve the system, and many of those need/want the cli.
There's a reason Mac OS X actually has a good cli (bash) as well.
That most users don't need it (on many Linux systems as on Mac OS X) doesn't mean it has no important use.

> 
"human beings" implies normal users, as opposed to geeks and power users.
"Because there are already other Linux distributions for those.."
Which was my point.

> 
in other words, Ubuntu is supposed to be easy and straightforward for normal usage (which I find it is). this is opposed to the image in the general public of "Linux" being difficult and for geeks and hackers only.

"Yeah, you, the general user, can use Ubuntu, it's the Linux for you. It's not the difficult Linux that those hackers and geeks are talking about, they're talking about some other Linux..."

> 
it's not addressing reality, which is that "Linux" is easy, but the wrong perception of it, and trying to gain more users for itself at the same time. if it would just say "Linux is ready for everyone", then users won't come flocking to it, it won't be visible to corporations, and Canonical won't get support contracts.

I beg to differ, Linux is not easy. At all. It's quite hard. The common perception unfortunately is that Windows and Mac _are_ easy, which they also aren't... For Windows I have yet to see a mildly skilled or novice user who did not need (extensive) assistance from power users to get the computer to do its job, without becoming part of a spam zombie network.
For Mac I have yet to see a mildly skilled or novice user who could actually use his machine efficiently - if they are professional users, they can use those few programs they use professionally well, but that's usually it...

Anyway, thanks for an interesting discussion!

---

### Post by yman on 2008-02-07
> **mdklnxtps said:**
> 
I guess it makes a difference if you have no stable connection and no burner. Else the cost is just some time (online and to burn) - for the disc you can use an RW one...
The big difference of ShipIt is that it allows the people who don't know about Linux/Ubuntu to get it from their friends who do and who can hand out discs.

No, that is not at all why it was good for me. You missed the point entirely. It was good for me because I had a need to have an official copy. I don't expect you to understand, but when I first looked for Linux I searched for it on Google, and reached either Linux.com or Linux.org (don't remember which) and searched it for the official Linux OS. Needless to say, I couldn't find it. I saw some customized versions of "Linux", but I was afraid to try them because they weren't "official", so who knows how good they were, or if they stole personal information from the users or something? Getting an official CD from a real commercial entity was a big comfort for me, because it reassured me that I'm getting something that was backed by commercial interests to make money, and that I'd have who to sue if something goes wrong. They also wouldn't want to do anything malicious, for fear of being sued.

> 
That's not what I call hype. That's just one guys experience. And there's nothing wrong with that.

Then I guess I was never exposed to any hype around Ubuntu in the first place.

> 
I don't understand how you can trash a system by installing another wm/de on it - as long as you install from the repositories for your system (version and build), this cannot trash the system. You could mess up your home dir, but then a separate user account is easy to set up, so no worries there....

There were system-wide settings that were changed (like the boot-splash) that I had no idea how to change back. Also, I have no idea how to get rid of all orphaned dependencies of a specific package, so my menus were all cluttered with applications I had no use for. My HD space was very limited (6GB), so every MB counted, and I had to be very conservative about space. I figured doing a fresh install was faster than cleaning up the system.

I'm sorry for creating confusion by using too harsh a term ("trashed").

> 
You mean a database file system. I have no idea why that would be better than what we have now, because your database file system couldn't just show you the files flat, it would have to order them... and it would make most sense to do that by various things that you can today also have your files show up as - most simply as per the directory structure, as the files are on your system, but also as per the date, type, etc, which you can do now with the various desktop search engines.

I guess so, but now I'm getting along OK with fat3. If you ever hear of such a FS for Linux(or any other free or open source kernel), please tell me. I might be interested in trying it out on a VM.

> 
So you don't mind to sacrifice some screen real-estate, whereas I do. 2 different users, 2 different ways to use. All normal I think. (Which is why I don't like GNOME - too much "that's not how you should use this system" going on; btw that's why I feel locked up whenever I have to use Windows, and I doubt I would feel much better on Mac OS X, which I have limited experience with, afaics both are worse than GNOME in the prescribing how to use _your own_ computer.)

agreed. I'm glad you can see my POV here.

> 
IMHO It's mainstream press (paper and online) that determines mostly what newbies go for. I just know that many longtime users are not on Ubuntu, because most can fix their problems (they are longtime users, so that figures) on whatever distribution they have, and they just stay with what they know (don't we all) unless forced otherwise. (Oh those poor SCO Caldera Linux users...)
But the point I was making is that for many if not most people it is not personal preference to use Ubuntu, because they never tried anything else. Look at this subforum, if Ubuntu doesn't work, people go back to WinXP/Vista.
They rarely say, hey, I'm outta here to check out Fedora/Mandriva/openSUSE because Ubuntu doesn't do it for me.

Interesting. Incidentally, a poll taken on the Ubuntu forums some time ago showed that the previous OS of ~80% of Ubuntu users was Windows. I might agree with you on this one after all. I need to try to think of this more from a newbie's perspective.

> 
Ok thanks, didn't know about medibuntu repo.. Where could I have found that, and why is that info not on the standard wiki where the dvd playback info is?

I'm not trying to make excuses for Ubuntu's failings here, so I'm not the address you're looking for.  However, it might have to do with the repository containing stuff that may be illegal to redistribute in certain countries, or maybe it isn't an official repository, so as a matter of policy they can't include it in official documentation.

EDIT: to literally (I don't know if this is what you intended) answer your question, check out these links:
[About enabling encrypted DVD playback.]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29")
[The Wiki page on Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Before you criticize, I'll let you know that these instructions are for the command line. I'm sure you understand why, seeing as you are a CLI fan, but I don't think this will be all that appealing to users who want to just get their DVDs to play. As far as I know, it is possible to achieve the same result from GUI alone. And I should know, seeing as I have enabled the reading of encrypted DVDs using only the GUI.

> 
As for bad CLI, bad OS, all I can say is: yes, a decent CLI is a requirement for _me_ to consider the OS decent, because without a decent CLI you can't do CL scripting, which is like the shopping list you give your assistant - much better in some situations than, say, the tourist in a different language region who's ordering an ice cream by pointing (GUI).

so you have one goal, and I have another goal. therefor you choose one OS that caters to your needs, and I choose another OS that caters to my needs. Just because you need a CLI, doesn't mean I need it, or should be required to use it or even have it at all.

> 
Ehm, no, that's not the joke - the point was that I wouldn't want a system without bash... which some people seem to advocate, wanting all to be possible from the gui and such....

That was a little joke of my own. I like making fun of how the literal meaning of an expression conflicts with what it is meant to express.

> 
Ok, I should have written GNU/Linux this once. Which is what I meant. Which is still the basis of Ubuntu. So without CLI it would be quite the abberration...

So is the purpose GNU that users communicate with their system specifically with the CLI? I don't think so, although I don't know.

> 
No, I don't expect or think that. I just think that like the windows registry, there's a point with deskop linux that one gets/has to use the cli.

Only certain types of users, for certain types of tasks. Others don't even want to know it exists, and would just give up on a task if they can't easily perform it from a GUI. Systems designed for the latter don't need a CLI, because it wouldn't be used anyway.

> 
That's fine, and I have nothing against that.
But there's a reason why many advanced users like and prefer the cli in many cases. For those users, on a (relatively) general purpose machine, taking away the cli is practically equal to invoking the death penalty for that system... because practically all Linux systems need advanced users to improve the system, and many of those need/want the cli.
There's a reason Mac OS X actually has a good cli (bash) as well.
That most users don't need it (on many Linux systems as on Mac OS X) doesn't mean it has no important use.

But if the machine was designed for a target audience that wants nothing to do with the CLI, then there is no reason to include it by default. They may not be advanced users, but if they don't like the system, they won't use it, and then what is all the development effort worth? it might even be possible to have developers without having a CLI, although the level of developer satisfaction may vary.

> 
"Yeah, you, the general user, can use Ubuntu, it's the Linux for you. It's not the difficult Linux that those hackers and geeks are talking about, they're talking about some other Linux..."

What exactly is wrong with that? They aren't saying that all other Linux-based OSs are targeted at a geek audience.

> 
I beg to differ, Linux is not easy. At all. It's quite hard. The common perception unfortunately is that Windows and Mac _are_ easy, which they also aren't... For Windows I have yet to see a mildly skilled or novice user who did not need (extensive) assistance from power users to get the computer to do its job, without becoming part of a spam zombie network.
For Mac I have yet to see a mildly skilled or novice user who could actually use his machine efficiently - if they are professional users, they can use those few programs they use professionally well, but that's usually it...

Maybe. The problem is I'm used to computers, and used them almost throughout my entire life, so I can't see them from the previous generation's perspective. I expect that in a few decades I'll understand the difficulties better, although by then the use of technology might be simplified to a level that requires no learning curve at all. Who knows?

> 
Anyway, thanks for an interesting discussion!

Is this goodbye?

---

### Post by Nirevus on 2008-02-07
Just a quick point, when talking about boot you said:

"There's a progress bar, but apparently no way to get to see more details about what the system is doing."

While not accessible directly from that area, if while still on the GRUB screen you remove "quiet splash" from the end of Ubuntu's boot options, you'll receive the verbose output for that boot. If you wanted it on every boot you could change it in the GRUB config.

Also:

> **yman said:**
> if I could perform file operations (edit, copy and paste, etc) with root access from the GUI alone, from my normal account, I wouldn't need the CLI. I would also find it more convenient.

This is already possible. You can either write the scripts yourself, or use Automatix to isntall them, it allows you to either edit scripts in gedit with root, or open nautilus at that location with root access. Of coures it requires you to input your password, but any other way also should.

---

### Post by Nirevus on 2008-02-08
Double post, please delete.

---

### Post by mdklnxtps on 2008-02-14
> **yman said:**
> No, that is not at all why it was good for me. You missed the point entirely. It was good for me because I had a need to have an official copy.

Well, the point was easy to miss since you didn't actually make it until now...

> I don't expect you to understand, but when I first looked for Linux I searched for it on Google, and reached either Linux.com or Linux.org (don't remember which) and searched it for the official Linux OS. Needless to say, I couldn't find it. I saw some customized versions of "Linux", but I was afraid to try them because they weren't "official", so who knows how good they were, or if they stole personal information from the users or something? 
That paranoid huh? Yep, you sound like a well informed Win user alright... ;)

> Getting an official CD from a real commercial entity was a big comfort for me, because it reassured me that I'm getting something that was backed by commercial interests to make money, and that I'd have who to sue if something goes wrong. They also wouldn't want to do anything malicious, for fear of being sued.
Well, MS is a commercial entity that does lots of malicious stuff, and very few customers have sued them successfully, so I'm not sure I agree entirely with your reasoning, but yeah, I get it.

> 
Then I guess I was never exposed to any hype around Ubuntu in the first place.

Nope, I don't think you were.

> 
There were system-wide settings that were changed (like the boot-splash) that I had no idea how to change back. Also, I have no idea how to get rid of all orphaned dependencies of a specific package, so my menus were all cluttered with applications I had no use for. My HD space was very limited (6GB), so every MB counted, and I had to be very conservative about space. I figured doing a fresh install was faster than cleaning up the system.

I'm sorry for creating confusion by using too harsh a term ("trashed").

Ok, that makes sense. At all experience levels, there's a different answer for the question: "What's the best thing to do now."

> 
I'm not trying to make excuses for Ubuntu's failings here, so I'm not the address you're looking for.  However, it might have to do with the repository containing stuff that may be illegal to redistribute in certain countries, or maybe it isn't an official repository, so as a matter of policy they can't include it in official documentation.

EDIT: to literally (I don't know if this is what you intended) answer your question, check out these links:
[About enabling encrypted DVD playback.]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29")
[The Wiki page on Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Before you criticize, I'll let you know that these instructions are for the command line. I'm sure you understand why, seeing as you are a CLI fan, but I don't think this will be all that appealing to users who want to just get their DVDs to play. As far as I know, it is possible to achieve the same result from GUI alone. And I should know, seeing as I have enabled the reading of encrypted DVDs using only the GUI.

What's strange is that the built-in system will take care of media codecs, but the built-in fix for libdvdcss is to compile from source...
BTW the official docs that I got my info from are on a user maintained wiki, it wouldn't have hurt to include a comment that a more convenient method does exist but it's illegal in some parts of the world, so one has to get it from elsewhere....

> 
so you have one goal, and I have another goal. therefor you choose one OS that caters to your needs, and I choose another OS that caters to my needs. Just because you need a CLI, doesn't mean I need it, or should be required to use it or even have it at all.

...

So is the purpose GNU that users communicate with their system specifically with the CLI? I don't think so, although I don't know.


Only certain types of users, for certain types of tasks. Others don't even want to know it exists, and would just give up on a task if they can't easily perform it from a GUI. Systems designed for the latter don't need a CLI, because it wouldn't be used anyway.


But if the machine was designed for a target audience that wants nothing to do with the CLI, then there is no reason to include it by default. They may not be advanced users, but if they don't like the system, they won't use it, and then what is all the development effort worth? it might even be possible to have developers without having a CLI, although the level of developer satisfaction may vary.

GNU tools comprise many many things, most of which are command line tools.

The point I was making is that any GNU/Linux system without CLI will not be able to attract many experienced users and developers, and will therefore cost more effort of whatever organisation stands behind such a system.
The fact that you'll happily use a (Linux or even other) system without CLI is just as much a moot point as that I wouldn't happily use such a system, GNU/Linux/Free Software systems thrive on (aptly shouted by Ballmer, CEO of MS) Developers Developers Developers...


> 
What exactly is wrong with that? They aren't saying that all other Linux-based OSs are targeted at a geek audience.

I'm still reading this in another way, sorry...

> 
Maybe. The problem is I'm used to computers, and used them almost throughout my entire life, so I can't see them from the previous generation's perspective. I expect that in a few decades I'll understand the difficulties better, although by then the use of technology might be simplified to a level that requires no learning curve at all. Who knows?

Take any device or tool with mild versatility and you'll find that the average inexperienced person will not be able to use it efficiently/properly without being instructed or reading (comprehending) the manual.
The no-learning curve is only possible for things that have only one use or that are based on something existing (perhaps various devices combined into one) that the user has experience with.
Example: digital photo cameras.

No, too easy.

Better example: a screwdriver. How many people in your direct environment will not use a straight small screwdriver which sort-of will fit a phillips (cross) screw, but go find the proper fitting screwdriver instead?
And how many will force the straight screwdriver to the point that either the screw and/or the screwdriver will be (ever so slightly) damaged?

I'm sure you can come up with lots more of examples, proper use of a hammer is one of them.

Devices that are versatile and based on regular tools..?
Phone plus photocam? Can people handle that without instructions? I doubt it.

In fact, even a cup/glass needs lots of practice, as I see now with my 18 m.o. daughter.

> 
Is this goodbye?
What, just because I put in an intermediate thank you for an interesting discussion? Nope.
;)

---

### Post by mdklnxtps on 2008-02-14
> **Nirevus said:**
> Just a quick point, when talking about boot you said:

"There's a progress bar, but apparently no way to get to see more details about what the system is doing."

While not accessible directly from that area, if while still on the GRUB screen you remove "quiet splash" from the end of Ubuntu's boot options, you'll receive the verbose output for that boot. If you wanted it on every boot you could change it in the GRUB config.

Yeah, I know that, but why make it necessary to modify the boot loader line, instead of offering the option to hit 'esc' for more information, just as many other distributions do?

> 
This is already possible. You can either write the scripts yourself, or use Automatix to isntall them, it allows you to either edit scripts in gedit with root, or open nautilus at that location with root access. Of coures it requires you to input your password, but any other way also should.

:confused:
Now I'm confused, not by the above information, but because of the mention of Automatix, because I read everywhere that it should be avoided if one doesn't feel like messing up the system...

Thanks for the feedback.
:)

---

### Post by armandh on 2008-02-14
since the 90s, about every year and a half I would try a linux distros 
none of those I could get to load remained on a computer.
knoppix live sparked my interest but would not load to HDD for me.
Ubuntu is the first linux distros that worked sufficiently well right out of the box to actually keep on the computer. 
or worth reloading when I phucked it up. 
more compatible than vista. less virus prone than xp with a good AV and faster on old equipment [P-IIIs] 
It is now on 3 machines including my un safe surfing brother in law's loaner. 
way better than the genuine disadvantage. the $39 replacement XPSP2 disk remains unopened.

---

### Post by Nirevus on 2008-02-16
> **mdklnxtps said:**
> Yeah, I know that, but why make it necessary to modify the boot loader line, instead of offering the option to hit 'esc' for more information, just as many other distributions do?)

True, this would be a great option to have, and I hope it's considered for Hardy.



> **mdklnxtps said:**
> :confused:
Now I'm confused, not by the above information, but because of the mention of Automatix, because I read everywhere that it should be avoided if one doesn't feel like messing up the system...

I'm not sure what the reasoning here is, however I've used Automatix on probably over 40 installs now (on many different computers) and have never had a problem; if somebody can find some good information about why it's suggested against, I'll be interested in reading it.

---

### Post by yman on 2008-02-16
> **Nirevus said:**
> True, this would be a great option to have, and I hope it's considered for Hardy.

I think they did it so for a reason, and that it won't change. I don't really mind either way, though.

> 
I'm not sure what the reasoning here is, however I've used Automatix on probably over 40 installs now (on many different computers) and have never had a problem; if somebody can find some good information about why it's suggested against, I'll be interested in reading it.

I've read some detailed stuff about why Automatix can seriously mess up an Ubuntu system, written by one of the developers of Ubuntu, but I lost the link.

BTW, mdklnxtps: check your [post.]("http://ubuntuforums.org/showpost.php?p=4331589&postcount=25") you kind of messed up, and wrote it all twice.

and about the CLI thing: my point has nothing to do with whether a platform thrives, but with whether or not it is good. a good platform achieves it's goals. this does not necessarily have anything to do with attracting developers, or rapid development.

and I stand corrected about GNU, but I'll remind you that GNU is a separate project from Linux, and may not share the same goals. nor do the goals of GNU have any bearing on any project that uses it.

> What's strange is that the built-in system will take care of media codecs, but the built-in fix for libdvdcss is to compile from source...
I have no idea what you are talking about.

---

### Post by ashmew2 on 2008-02-18
You have done a lot of work on the Article (it shows...) and it is quite remarkable. Although at times you seem to be sarcastic (remember the "Linux for Human Beings" thingy ?)..But well written and Good Job.
The Bottom Line is...Everyone has different needs and wants , there is no PERFECT operating system..(Not yet anyways.)
Ubuntu has it's pros and cons , so does MS Windows , or Mandrake or SUSE or REDHAT (or any other OS for that matter).

---

### Post by ibuclaw on 2008-03-16
Hi, not sure if someone has said this yet, but after reading your (fair) review.

I thought I might point out that ubuntu does have commands such as "ll" and "la".
Though before I dub them, they aren't infact commands. They are **alias'**.
But anywho, its all in your ".bashrc" text file. Just hashed out.

```
 # some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF' 
```
Just unhash them and it will work.
Hope this helps you with most of your frustration in the CLI  of Ubuntu.

Iain

---

### Post by ibuclaw on 2008-03-16
And you can easily add these to your .bashrc file too.

```
 # interactive removal
alias rm='rm -iv'
alias rmdir='rmdir -iv'

```

But, I suppose the point that you were making is true that if you want a system to be as user friendly as humanly possible down to the absolute detail,  safety nets are required.

But lets be honest, for new, inexperienced users. They are hardly going to jump to the command line (given that all hardware detection and usage goes well) when the current version of ubuntu has the very (very bare) minimum for them to experience good quality usage for the 6 month release period without it!

Iain

---

### Post by mdklnxtps on 2008-03-20
Hmm, almost forgot about this thread (and linux in general, have not been on my laptop for ages)....

> **yman said:**
> 
and about the CLI thing: my point has nothing to do with whether a platform thrives, but with whether or not it is good. a good platform achieves it's goals. this does not necessarily have anything to do with attracting developers, or rapid development.

My point is that a good open platform (what gnu/linux is by definition) is nothing without developers, and developers won't warm up to a system which they can't really use. And imnsho developers can't use a system without a decent cli...

> 
... but I'll remind you that GNU is a separate project from Linux, and may not share the same goals. nor do the goals of GNU have any bearing on any project that uses it.

Perhaps, but I venture to say that GNU is as important as the kernel. GCC to name a component...

I wrote:
 What's strange is that the built-in system will take care of media codecs, but the built-in fix for libdvdcss is to compile from source...
> 
I have no idea what you are talking about.

Well, I wrote this in my review [>here<]("http://www.mandrake.tips.4.free.fr/ubuntubeyondthehype.html#conf"), and I think I added the link as well - essentially, the wiki has information on how to install libdvdcss and it includes getting all compilation requirements, downloading the source and compiling it.
See here:
[https://help.ubuntu.com/7.10/musicvideophotos/C/video.html]("https://help.ubuntu.com/7.10/musicvideophotos/C/video.html")
which tells you to run this command:
sudo /usr/share/doc/libdvdread3/install-css.sh
and the following page:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
has the info on which things to install so that the install-css.sh script will work.

Since that information is the information that a google search comes up with, and it's from the official Ubuntu site, I assumed that that would be the proper way to get decss installed - Ubuntu being tuned for beginners (as well as advanced users) and low barrier to enter and such.



> **ashmew2 said:**
> You have done a lot of work on the Article (it shows...) and it is quite remarkable. Although at times you seem to be sarcastic (remember the "Linux for Human Beings" thingy ?)..But well written and Good Job.
Thanks, and I agree, I was a bit sarcastic, but I found that tone to contrast nicely with the rest.


> **tinivole said:**
> Hi, not sure if someone has said this yet, but after reading your (fair) review.

Thanks..
> 
I thought I might point out that ubuntu does have commands such as "ll" and "la".
Though before I dub them, they aren't infact commands. They are **alias'**.
But anywho, its all in your ".bashrc" text file. Just hashed out.

```
 # some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF' 
```
Just unhash them and it will work.
Hope this helps you with most of your frustration in the CLI  of Ubuntu.

Iain

From my mandriva system:
```
$ alias
alias cd..='cd ..'
alias cp='cp -i'
alias d='ls'
alias df='df -h -x supermount'
alias du='du -h'
alias egrep='egrep --color'
alias fgrep='fgrep --color'
alias grep='grep --color'
alias kde='xinit /usr/bin/startkde'
alias l='ls'
alias la='ls -a'
alias ll='ls -l'
alias ls='ls -F --show-control-chars --color=auto'
alias lsd='ls -d */'
alias mc='. /usr/share/mc/bin/mc-wrapper.sh'
alias md='mkdir'
alias mv='mv -i'
alias p='cd -'
alias rd='rmdir'
alias rm='rm -i'
alias s='cd ..'

```

Hmm, I just found some nice extra things I didn't realise...
But anyway, yes, I know that you can add things to your .bashrc but that's beside the point, which was that systems with common aliases in place offer more convenience than those that don't have that. Of course you can configure things yourself, roll your own, etc. But that's not exactly userfriendly, I chose not to use LFS for a reason...
It's not a big point though.
Thanks for your feedback Iain.

---

### Post by slam on 2008-06-22
Finally, after so much crap - a real review!

Thanks for taking your time to really not just install, but use an operating system before writing about it. What you did was a really full blown review from a user's point of view for users. Very well done!

However, usability and "how it fit's into my needs and daily workflow" is just one important point on making a good operating system.

All other important points are not so easy to review, I understand. But that does not make them less important: Security, stability, speed, extendability, flexibility, manageability, cross-compatibility and support quality.

I am looking forward to more serious reviews following your example, targeting the above.

Greetings,
Chris

---

