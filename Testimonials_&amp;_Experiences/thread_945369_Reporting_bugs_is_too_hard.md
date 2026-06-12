---
title: "Reporting bugs is too hard"
date: 2008-10-12
forum: Testimonials &amp; Experiences
---

### Post by php_penguin on 2008-10-12
Hi,

I've been using Ubuntu since around v6.10, and I can remember the following situation as having happened at least 10 times:

 - I find a small (non-fatal) annoying bug in a program
 - I think "lets report that bug!"
 - I get to the relevant page (bugzilla or w/e)
 **- It asks me to register + login before I can report that bug**
 - I give up because its only a small bug

REPORTING BUGS IS TOO COMPLICATED (I know, shouting)

Seriously, if we want Ubuntu (and gnome/linux in general) to really progress and not annoy the users, we really need to make it easier to report bugs.

The developers won't have thought of this for the following reasons:
 - they already have bugzilla accounts, because they are more commited than the average user
 - they only use "power-users" programs, meaning the programs the standard user uses regularly are overlooked

Anyway, what I envisage is simple:
 - a "Report a bug" link in _every_ program's Help menu
 - This link goes to the same program (gnome-bug-report or w/e it might be called)
 - This program is also accessible from the System menu (same link name, but with a program chooser)
 - When a user submits a bug report, it also adds system info etc to the bug report and checks for duplicate bugs.
 - Bugs submitted this way go into a seperate bug space, to stop the main bugzilla threads getting spammed.

I think this would really help getting the majority of small annoying bugs out of the way.

---

### Post by sokopok on 2008-10-12
It takes about 1 minute to setup an account at launchpad. If you're using KDE another minute for an account at bugs.kde.org. That's a one time only thing. Is that too much to ask? Of course maybe you'd rather be annoyed everytime you use your computer by some silly bug you were too lazy to report?

btw: havent use gnome for a while, so not sure there, but every kde app has the "report bug" thingie in the help menu... (which also fills out half the bug report, and attaches traces etc. for you)

---

### Post by the8thstar on 2008-10-12
We shouldn't have to register to anything to report a bug. PERIOD. I don't find this to be acceptable in any way.

---

### Post by PmDematagoda on 2008-10-12
> **the8thstar said:**
> We shouldn't have to register to anything to report a bug. PERIOD. I don't find this to be acceptable in any way.

Perhaps it is unacceptable for you, but if you were a developer and if you had to sift through all the spam that could accumulate by your leniency in not requiring people to register, then you may think quite the opposite.

Edit:- By the way, this thread is more a testimonial than anything else, therefore it has been moved to the Ubuntu Testimonials and Experiences section.

---

### Post by sokopok on 2008-10-12
You registered here, didn't you? Was that too much?
Without bugreports, there will be no bugfixes. Without bugfixes there will be no Linux.

---

### Post by the8thstar on 2008-10-12
I understand the need and service that bug reporting represents and I'm happy with that. Now, I still maintain that registering on launchpad shouldn't be necessary. 

When you send a crash report in Windows, you're not asked to register to anything to be able to send your info. Learn from that.

---

### Post by sokopok on 2008-10-12
I understand your annoyance. I hate having to register myself. But it provides a very effective coutermeasure to spamming and bugus reports.
Tell me: if you want to download something from a website that requires you te register, you will, won't you? Cause there's something in it for you. Why can't you see this is exactly the same. You doné file bug reports for the benefit of others, you file them for yourself. In the next version of app-XXX there's a very good chance your problem is fixed, or your feature-request has been implemented.
When you send a bug report to m$, do the fix it? maybe, maybe not. Bugfixes is are not very high n their priority list (that's a literal statement from Bill). Of course, you might feel a little better after this kind of noop bugreport, but that's just placebo. It wears off very soon (actually the next time you use the same app.)

---

### Post by PmDematagoda on 2008-10-12
> **the8thstar said:**
> I understand the need and service that bug reporting represents and I'm happy with that. Now, I still maintain that registering on launchpad shouldn't be necessary. 

When you send a crash report in Windows, you're not asked to register to anything to be able to send your info. Learn from that.

When Windows crash reports are sent, they are sent automatically and in such a way that the user has little or no control over what it contains, therefore you would be hard set to send spam in it, and since Microsoft does not make the bug reports public it would render any spam useless.

In Launchpad, not only are the bug reports public(except perhaps with CVS bug reports) but the user can add any information or data which he/she may consider useful, now if no registering was necessary, can you estimate the amount of spam you may see on Launchpad?

---

### Post by lisati on 2008-10-12
Part of the time I suspect it's the kind of mental juggling act where **Sombody Else** will do it, **Nobody** wnats to do it and **Anybody** can do it.

---

### Post by Greyed on 2008-10-12
> **PmDematagoda said:**
> Perhaps it is unacceptable for you, but if you were a developer and if you had to sift through all the spam that could accumulate by your leniency in not requiring people to register, then you may think quite the opposite.

I certainly wouldn't.  Neither does Debian whence Ubuntu spawned...

[http://wiki.debian.org/reportbug](http://wiki.debian.org/reportbug)

Imagine that, a command in the OS itself to report a bug which doesn't require registration.  Good enough for Debian, good enough for Ubuntu.

---

### Post by sokopok on 2008-10-12
Bug reports sent this way are often not very useful. How can the developers know what you were doing at the time, what you expected to happen, etc...
The kind of automatic reports you mention ar usefull for program crashes, not for any other kind of bugs. The way opensource software is developped is very different. The enduser kan directly influence the development process.
The last bug I filed was related to a Copy/Paste operation not working properly. How can this be done automatically? The computer has no way of knowing this. Most bug reports aren't related to crashes.
And what I mean with spam is not spam for you, but spam for the developers.

I noticed your slogan: "I am an experimenter, give me the most stable OS and I can make it unstable in a few hours." If that is true, you'd be a great bughunter ;)

EDIT:
** Apologies: I thought I was responding to  php_penguin (I'm a bit distracted, still trying to get X running in the mean time)**

---

### Post by forger on 2008-10-12
> **the8thstar said:**
> I understand the need and service that bug reporting represents and I'm happy with that. Now, I still maintain that registering on launchpad shouldn't be necessary. 

When you send a crash report in Windows, you're not asked to register to anything to be able to send your info. Learn from that.

On the one hand, I've sent a lot of those windows so-called crash reports, and after 1 year of daily reporting of that crash, my explorer.exe still crashes every 5-8 minutes.
On the other hand, I've sent a lot of bug reports to launchpad, where I can see and track whether they have been fixed, or if a developer has some interest in fixing it.

Now you tell me - which one works better and who should learn from whom :)

---

### Post by PmDematagoda on 2008-10-12
> **Greyed said:**
> I certainly wouldn't.  Neither does Debian whence Ubuntu spawned...

[http://wiki.debian.org/reportbug](http://wiki.debian.org/reportbug)

Imagine that, a command in the OS itself to report a bug which doesn't require registration.  Good enough for Debian, good enough for Ubuntu.

This seems to be similar to what Windows does. In this case, the tool doesn't seem to be one that a Debian newbie would know and in any case can only be used to(Probably, but it could be used on Ubuntu as well) report bugs through Debian itself, so it would be more difficult to distribute spam through it since:-
1) It may not be that well known.

2) It may be difficult for a newbie to use when compared to a report bugs publicly on the web.

3) It may have certain limitations on what could be sent. E.g no links could be sent through it.

And the tool, while being useful, doesn't address the point this thread talks about(and which my post talked about) since it concerns the reporting of bugs publicly through such systems like Launchpad.

---

### Post by Greyed on 2008-10-12
> **PmDematagoda said:**
> This seems to be similar to what Windows does.

Uh, no, it isn't.  This is user initiated, they see exactly what is send and is able to comment on the bug.  It is 100% transparent.

> In this case, the tool doesn't seem to be one that a Debian newbie would know and in any case can only be used to

The point isn't that a newbie would know about it.  The point is that the concept is sound.

> And the tool, while being useful, doesn't address the point this thread talks about(and which my post talked about) since it concerns the reporting of bugs publicly through such systems like Launchpad.

This is public reporting, where do you think a good portion of the bugs on bugs.debian.org come from?  That tool.  Spam?  It uses email for delivery.  So it goes through standard email spam fighting tools which are literally years ahead of any tool protecting web based solutions.

---

### Post by the8thstar on 2008-10-12
Well, I won't report anything then. I simply can't abide a system I don't agree with. Here is to Freedom. As always, do whatever you wish.

---

### Post by Keyper7 on 2008-10-12
*Useful* bug reports are not supposed to be easy. They involve describing *precisely* the software version, the distro version and the specific circustances on which the bug happened. And that's just the minimum necessary.

System customizations you previously did, other programs you were running in the moment of the bug, what exactly did you type, system logs... everything can be relevant and the bug reporter must be ready not only to report a bug but to give all relevant info that a developer might request afterwards. He must also be willing to test proposed packages because sometimes he might be the only one able to reproduce the bug at the moment.

Reporting bugs is not a magical button that sends an alarm to a developer who then goes "Oh, someone reported this bug. I'll fix it. There, done.". Reporting bugs is a *commitment from the user* and the initial report is *just the beggining*. If you want to make an *useful* contribution, the registering step is the *easiest* one, specially because you only need to do it *once* for *all* bugs.

In all honesty, if you are too lazy to register on Launchpad, then I think it's *better* if you do not report any bugs. Because you'd obviously be also too lazy to subscribe to the bug and reply to what the developer requests (this usually takes more time and effort than registering). You'd just leave the bug report there, with no deep details, and expect your slaves to fix it while you drink a beer.

Launchpad already has enough noise without users who think FOSS means "everyone works for me for free" instead of "I'm part of the community and should contribute as well". If you want your problems solved, show that you give a damn.

---

### Post by Kevbert on 2008-10-12
Reporting a bug may take a while but don't forget that the people trying to solve the bug are working in isolation - they don't know what your PC is, the setup and what software you are using.  Somehow they need to simulate the problem with the information that is provided.  To make it easier when the fault occurs a snapshot of what was happening and your hardware/software configuration could be taken along with some logfiles.  Sometimes the bug may be a runtime error which only occurs in certain situations and no logs are generated. Personally I wouldn't like to do the bug hunters job (having done this with mobile phones in the past).  I think they do a good job given the lack of information and varying skill levels of the end user.
Taking a screenshot of the fault where possible can help.

---

### Post by php_penguin on 2008-10-12
Just as a clarification of what brought this about:

I was playing the gnome-sudoku game in the Ubuntu 8.10b distrobution and whenever I completed a game the time always came in at around 55 seconds... I was playing a hard-level game that took me about 8 minutes (roughly) to complete.

This is a tiny little bug that has no real relevance or effect, and so is barely worth reporting. Asking me to register/login to report this makes the commitment seem pointless...

I am not talking about huge system-killing bugs here, I am talking about small annoyances, quirks, and other such things.

With regards to a built-in graphical bug reporting tool, the only automated bits would be:
 - program selection (carries through from the program that initiated the auto-bug tool)
 - installed program list + versions
 - distrobution information

The actual describing of the bug would still be left for the user.

---

### Post by Kevbert on 2008-10-12
> **php_penguin said:**
> Just as a clarification of what brought this about:

I was playing the gnome-sudoku game in the Ubuntu 8.10b distrobution and whenever I completed a game the time always came in at around 55 seconds... I was playing a hard-level game that took me about 8 minutes (roughly) to complete.

This is a tiny little bug that has no real relevance or effect, and so is barely worth reporting. Asking me to register/login to report this makes the commitment seem pointless...

I am not talking about huge system-killing bugs here, I am talking about small annoyances, quirks, and other such things.

With regards to a built-in graphical bug reporting tool, the only automated bits would be:
 - program selection (carries through from the program that initiated the auto-bug tool)
 - installed program list + versions
 - distrobution information

The actual describing of the bug would still be left for the user.

Bug has just been reported on Launchpad by me - [[COLOR="Red"]Gnome-sudoku timings all wrong[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-sudoku/+bug/282315") I've cross-referenced it with your post.  The timings should be from when the game starts until it ends - it isn't.

---

### Post by Ms_Angel_D on 2008-10-12
Why not integrate the launchpad registration process with installation, then the account gets setup during install, if the user is connected to the internet?? If the they are not connected during install, you can store the registration information on their computer until they do get connected at which time if they clicked a bug report link which **_could be_** available in every app the registration and/or login information could then be submitted.

---

### Post by Keyper7 on 2008-10-12
> **php_penguin said:**
> This is a tiny little bug that has no real relevance or effect, and so is barely worth reporting. Asking me to register/login to report this makes the commitment seem pointless...

Just because a bug is simple, doesn't mean its cause is. The developers might still need you to describe the problem in more details, to specify steps for reproduction and to test proposed fixes. Any of those three things require more effort than registering. If you're too lazy to do those simple procedures, then regardless of registering or not, your help would probably be worthless anyway.

---

### Post by Greyed on 2008-10-13
> **Keyper7 said:**
> *Useful* bug reports are not supposed to be easy. They involve describing *precisely* the software version, the distro version and the specific circustances on which the bug happened. And that's just the minimum necessary.

What a load of crap that is.  Seriously.  Have you even tried reportbug?  I'm betting not.  Here's a fine example.  

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462266](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462266)

Note that everything past the description of the bug is automatically generated.  So it describes exactly all of the relevant versions of packages satisfying the dependencies of that package.

Now, a report in Launchpad...

[https://bugs.launchpad.net/mutt/+bug/16750](https://bugs.launchpad.net/mutt/+bug/16750)

Notice what is missing?  A whole hell of a lot which is **easy** to obtain.  As evidenced in this launchpad report which does use reportbug.

[https://bugs.launchpad.net/mutt/+bug/155999](https://bugs.launchpad.net/mutt/+bug/155999)

So please, take your "reporting a bug should be hard" FUD elsewhere.  It is utterly false and completely counterproductive!

> In all honesty, if you are too lazy to register on Launchpad, then I think it's *better* if you do not report any bugs. Because you'd obviously be also too lazy to subscribe to the bug and reply to what the developer requests (this usually takes more time and effort than registering).

Or, since reportbug is sent via *e-mail* if the developer has more questions he could, I dunno, e-mail the person!  Imagine that!  Having a conversation through email.

> You'd just leave the bug report there, with no deep details, and expect your slaves to fix it while you drink a beer.

You got all that from a legitimate complaint?  Hell, I dislike having to register to report bugs as well.  I certainly don't have the above attitude.  I just know, for a fact, there is a better way to do it.

> Launchpad already has enough noise without users who think FOSS means "everyone works for me for free" instead of "I'm part of the community and should contribute as well". If you want your problems solved, show that you give a damn.

Take your own advice.  The last thing you want to do is have people not report bugs.  Show **you** give a damn by growing up and shutting up until you get a clue!  You probably have done more damage to the entire process with this crappy attitude of yours than a years worth of people who earnestly want to help but not be troubled to register for yet another **useless web site** for pointless communication when the whole communication thing was solved almost 30 years ago in email!  That is not something to brow-beat them over.  That's something over which to empathized with them!

---

### Post by Keyper7 on 2008-10-13
Ok, Greyed, that was a little bit rude but I guess you're just reflecting my own rudeness from previous posts. Since a flamewar will get us nothing but the locking of this thread, I apologize to you and php_penguin for the harsh words and will try to move on with the discussion in a more civilized manner. Sorry.

My point is: I'm not questioning that the initial process in Launchpad could be improved, but I've followed a lot of bug reports and in my opinion in most of the cases this initial process is the easiest step, regardless of registering or not.

One of the things I dislike the most, be it on Launchpad, bugzilla or mailing lists, is lack of commitment from the reporter. A developer replies with "ok, could you tell me if the bug also happens when you blah blah blah..." and receives no response. This not only generates noise in the site/list, but also kinda shows a little bit of disrespect for the developers ("Here. Fix it. I'll just leave."). It irritates me a little bit. I was a little but FUD-ish on purpose because I think that reporting bugs and not commiting to them is worse than not reporting. I see a lot of "I DEMAND YOU TO FIX MY PROBLEMS NOW!!!" posts around here, tend to be a little more irritated by it than I probably should and sometimes lash out at the wrong people.

So I ended up replying to php_penguin thinking of him as an uncommited user and someone who is doomed to be unhelpful regardless of how easy the reporting process is. This is not necessarily true and I do apologize. Anyway, I hope we can move on from my useless rudeness and keep discussing productively. Specially because, as far as Launchpad goes, I do agree it could use some improvement.

---

### Post by sokopok on 2008-10-13
Have you tried reporting a bug for KDE4?
Should look very familiar to you. Maybe the Gnome developers should go take a quick peek there ;)

---

### Post by Greyed on 2008-10-13
Yeah.  Sorry about that.  You're right.

---

### Post by 3rdalbum on 2008-10-13
Why not use capchas? I realise that they are not the be all and end all of securing your website against spam, but they do quite well.

I do agree; I once wanted to report a bug and I couldn't be bothered trying to find where I put my login details for that particular bug tracker, so I don't think I ever did report it. If the barriers could be broken down some more, that would be excellent.

---

### Post by hyper_ch on 2008-10-13
yesterday on IRC was also a bit talk on bug reporting. Someone mentioned that quite a few people join the irc channel then say something like:

"[user x joins channel]Hi, application X crashes on me. Pls fix that![user x leaves chanenl]".

That gives no indication at all and does not help. In that case ignoring the "bug report" is just simpler. The registration of yourself also helps the devs to get back to you if they need to know more. I mostly don't provide all the info they want either because I'm just lacking the experience of knowing what else is all connected together so IMHO it's a good thing I need to be registered.

---

