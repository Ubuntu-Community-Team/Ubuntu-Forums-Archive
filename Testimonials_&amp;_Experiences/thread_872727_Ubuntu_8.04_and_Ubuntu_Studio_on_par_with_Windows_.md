---
title: "Ubuntu 8.04 and Ubuntu Studio on par with Windows 95 when talking about audio..."
date: 2008-07-28
forum: Testimonials &amp; Experiences
---

### Post by pikseli@work on 2008-07-28
Sad but true. I have given up trying to get this working.

In my experience, long ago Windows 98 had better audio drivers, mixers etc. than Ubuntu 7.10-8.04. 

I am still trying to get MULTI*CHANNEL SOUND! Wow, novelty, huh? Yeah, currently only single app gets to use the sound. 

And Ubuntu Studio - lots of hot air, that one. Its great for 3D/2D graphics. All the sound apps, realtime-kernel -stuff and video editing stuff are absolutely useless. Either do not work at all, or when you get them working they are so 1996 I would rather use Win98 stuff.

The ONLY multichannel audio program for linux I know of, Energy XT, does not work AT ALL on my intel 945 series Asus Pundit.

As far as I am concerned, according to my experience Ubuntu and Ubuntu Studio are as useful for audio editing as Windows 95.

---

### Post by sydbat on 2008-07-28
Sorry to hear that. I have no problem with my sound, but that may just be my hardware. Maybe it has to do with the Intel 945 series Asus Pundit being a barebones system? You may have to upgrade the audio card? Not helpful, as per drivers, but that may be the problem.

---

### Post by Methuselah on 2008-07-29
Some peopel have experienced some initial config issues but the sound is actually pretty advanced when set up right.
Search the forums for 'pulseaudio' in 'hardy' and I'm certain you'll come upon helpful topics.
Hopefully some of the glitches are ironed out in intrepid.

EDIT: Seems I kind of misunderstood your issue.
Nonetheless, you might be able to find help on the forums.

---

### Post by zero244 on 2008-07-29
Sounds like your using a laptop. I agree doing multi-channel audio editing with a onboard sound card may not be the best.
Keep in mind your audio chip was created and optimized with Windows in mind.
If that is your only complaint just dual boot with Windows and do your editing in XP.
Just a thought.

---

### Post by pikseli@work on 2008-07-29
Well, actually Intel was the first manufacturer that officially started to support driver dev, afaik. Methuselah, yes, I have tweaked so many nights its not funny anymore. And zero244 no, its not a laptop, its a top of the line Asus barebone.

Looking at the amount of problems people are experiencing its easy to see its not a driver problem, or a hardware problem - but its a Pulseaudio problem (jmo). 

Look around at Multimedia & Video -forum! The sound problem thread is higher than jacks beanstalk. Every 2 hours someone asks about the very same single-app-sound-thanks-to-pulseaudio problems.

**The sooner Ubuntu community realizes that Pulseaudio is still in its Alpha, the better.**

This is not what Open Source is about. Its not about wasting THOUSANDS of hours on testing unfinished pieces of software out there on users desktops. Most people cannot really report, troubleshoot or debug problems in a way that is in any way useful to the developers.

This has been, in my experience, worst case of releasing untested software layer as finished, in 'final' OS, ever. Your mileage may vary.

All this has resulted is loss of thousands and thousands of hours of time, of all the people who wanted to listen to music, work on sound, compose or mix music.

---

### Post by beniwtv on 2008-07-29
Yes, this is a problem with some sound cards and PulseAudio (and even ALSA)

What happens is the following:

One application is using PulseAudio to playback music, let's say Rhythmbox. Now, PulseAudio is not an audio driver, but a sound server. This means that is has to use ALSA (which is not a sound server, but an audio driver subsystem) to play it back.

Now, if you start another application which uses PulseAudio it will work fine, as PulseAudio mixes the streams before sending them to ALSA (make sure you have activated sound mixing in the management GUI of PulseAudio).

The problem appears when the other application does not use PulseAudio, but ALSA directly. This is still the case with many audio production programs, as they have been not ported to PulseAudio yet (or won't).

In that case, ALSA would have to do the mixing between PulseAudio and the app. Unfortunately, ALSA by default does not mix streams, so you're sound card needs to have a hardware mixer, which many don't have.

However, there's still hope: ALSA in recent version includes a software mixer, which you can enable. It's called 'dmix'. If you search the forums you might find a tutorial on how to set that up with PulseAudio (so it uses dmix), and all other applications use PulseAudio (including the ALSA ones).

Please note also that we're still in the process of 'migrating' to PulseAudio, and not all applications are using PulseAudio yet. Just give it some time, and it will iron out itself. Linux currently is changing very much in all aspects, to expect it to be a little be rough sometimes. :)

Cheers,

---

### Post by pikseli@work on 2008-07-29
Yes, I tried those scenarios, too. Dmix, confing confing confing. No luck.

Yes, I can tell we're still in the process. But it is WRONG to release OS with semi-alpha-nonsupported-inbetween-something. Whoever made this choice, just isn't a developer. Bad. Not like this. Fail fail fail.

I will use this Pulseaudio mess as an example of how not to do versioning, transitions or migrations if I ever have to make speeches or lectures on software developing...

---

### Post by saratchandra on 2008-07-29
> **pikseli@work said:**
> Well, actually Intel was the first manufacturer that officially started to support driver dev, afaik. Methuselah, yes, I have tweaked so many nights its not funny anymore. And zero244 no, its not a laptop, its a top of the line Asus barebone.

Looking at the amount of problems people are experiencing its easy to see its not a driver problem, or a hardware problem - but its a Pulseaudio problem (jmo). 

Look around at Multimedia & Video -forum! The sound problem thread is higher than jacks beanstalk. Every 2 hours someone asks about the very same single-app-sound-thanks-to-pulseaudio problems.

**The sooner Ubuntu community realizes that Pulseaudio is still in its Alpha, the better.**

**This is not what Open Source is about. Its not about wasting THOUSANDS of hours on testing unfinished pieces of software out there on users desktops. Most people cannot really report, troubleshoot or debug problems in a way that is in any way useful to the developers.**

This has been, in my experience, worst case of releasing untested software layer as finished, in 'final' OS, ever. Your mileage may vary.

All this has resulted is loss of thousands and thousands of hours of time, of all the people who wanted to listen to music, work on sound, compose or mix music.

That is exactly what opensource is about. Everybody should contribute some way, whether its developing or bug reporting.

> **pikseli@work said:**
> Yes, I tried those scenarios, too. Dmix, confing confing confing. No luck.

Yes, I can tell we're still in the process. But it is WRONG to release OS with semi-alpha-nonsupported-inbetween-something. Whoever made this choice, just isn't a developer. Bad. Not like this. Fail fail fail.

I will use this Pulseaudio mess as an example of how not to do versioning, transitions or migrations if I ever have to make speeches or lectures on software developing...

Then use windows. Nobody forced to use a linux distro

---

### Post by pikseli@work on 2008-07-30
No, I do not agree with you that wasting time, electricity and resources on testing software on end users computers is what Open Source is about. Just a silly concept all together. And I would like to also think that Open Source is NOT about giving false impressions.

If a solution or application doesn't work yet, it should be in the bleeding edge. As far as I know, I downloaded and installed final releases. Am I confused by the Ubuntu release system? Perhaps.

With debian I never had this problem - I always knew if it was stable or unstable repos I was using.

Basically you could think of it this way, imho: Ubuntu needs level of standards similar to debian. If you have final releases then only stable stuff goes into those releases. JMO.

---

### Post by sink on 2008-07-30
I don't have this problem.

I can play sounds in several programs with no problem.

I am using a lenovo laptop

---

### Post by hyper_ch on 2008-07-30
How can Open Source give a wrong impression? You can check line for line what a program does ;) you might get wrong impressions yourself but not that OSS is giving you those ;)

---

### Post by pikseli@work on 2008-08-09
How?

Well if I download a final release of some Operating System version, and it has packages that are nowhere near beta - that is giving the wrong impression, imho. 

Go read the Pulseaudio marketing buff on KDE or Gnome sites. Do they make it sound like it works BETTER than just ALSA/whatever? In my opinion yes. 

However, after consulting with developers and mavens, I find that REALITY is that ALSA and Pulseaudio and applications have conflicts that will take years to be resolved. Look into it. 

I am not just making this up or the only one or using some esoteric hardware. This is imho real issue, case of releasing stuff that developers KNOW (or knew) simply isnt going to work. Thanks for your questions though.

Thats what I mean with wrong impressions.

I guess with Debian I got used to always being able to count on the fact that stable/final release and repository only has stuff that will work with minimal trouble and conflicts.

I think these lines drawn in water, if thats what you were thinking.

---

### Post by hyper_ch on 2008-08-09
> **pikseli@work said:**
> Well if I download a final release of some Operating System version, and it has packages that are nowhere near beta - that is giving the wrong impression, imho.
Well, it works stable for me and thousands of others... so it's definitively not nowehere near beta ;9

> **pikseli@work said:**
> Go read the Pulseaudio marketing buff on KDE or Gnome sites. Do they make it sound like it works BETTER than just ALSA/whatever? In my opinion yes.
Go and read the M$ marketing buff... do they make it sound like it works BETTER than just about anything else? In my opinion yes.

> **pikseli@work said:**
> However, after consulting with developers and mavens, I find that REALITY is that ALSA and Pulseaudio and applications have conflicts that will take years to be resolved. Look into it.
After consulting ............. I find that REALITY is that VISTA ..... have conflicts that will take years to be resolved. Look into it.

> **pikseli@work said:**
> I am not just making this up or the only one or using some esoteric hardware. This is imho real issue, case of releasing stuff that developers KNOW (or knew) simply isnt going to work.
Well, it works for many, many, many people just great... so it can't be your hardware, right? Well, it so working so releasing stuff did not release anything that doesn't work.

> **pikseli@work said:**
> Thats what I mean with wrong impressions.
It might just be you and a few others who have really problems with it so it is still not giving wrong impressions.

> **pikseli@work said:**
> I guess with Debian I got used to always being able to count on the fact that stable/final release and repository only has stuff that will work with minimal trouble and conflicts.
Not everything works on debian either ;)

---

### Post by beniwtv on 2008-08-09
pikseli,

Do you realize not everyone has this problem?

It's not that PulseAudio does not work. It just does not work for _you_. And yes, that's bad. But it works for me, and many others. And I can do cool stuff which I can't with ALSA only.

But did you ever fill a bug report for your hardware and configuration? No?

_That's_ what open source is about. Collaboration. Creating technology which can be used be everyone. But that means we need to help each other making the software better. Agreed, it may not always be _stable_ when a product is new, but it will get there with the help of the community.

Also, I think accusing the Ubuntu dev's being no real developers is just plain rude, IMHO.

Thank you,

---

### Post by CameO73 on 2008-08-09
I have to agree with pikseli@work. Some choices that were made for Hardy (LTS!) have lead to some serious problems. I know of at least two major problems that will discourage users starting with Ubuntu: the Flash + Firefox crashes and this Pulseaudio problem.

Don't get me wrong: I know there are solutions, I know these forums provide excellent feedback and support ... but still, these problems are a real turn-off for anyone coming from Windows. A lot of those users probably won't even come here; they just go back to Windows and discourage others.

I'm not one of those "we must do everything to cater Windows users", but I do believe in providing a stable desktop environment. I know some risky choices had to be made to go forward (that's why I understand Firefox 3 beta was added to the Hardy release). And I really see a bright future for Pulseaudio ... but perhaps 8.04 was too soon.

Let's at least stop the "if you don't like it, don't use it" answers. Those don't help anyone. Yes, Ubuntu has some problems. No, they don't disappear overnight. Stop killing the messenger and listen to the message.

---

### Post by zipperback on 2008-08-09
> **pikseli@work said:**
> How?Well if I download a final release of some Operating System version, and it has packages that are nowhere near beta - that is giving the wrong impression, imho. 

Simply because something is marked as beta doesn't denote that it isn't an application that is stable enough for distribution. I can think of numerous &#8220;commerical&#8221; applications which are sold by big software companies that are &#8220;final&#8221; and yet those applications are problematic and have numerous bugs.


> **pikseli@work said:**
> 
Go read the Pulseaudio marketing buff on KDE or Gnome sites. Do they make it sound like it works BETTER than just ALSA/whatever? In my opinion yes

I have Ubuntu Hardy installed on my laptop and I am not having any problems with my audio. I personally know of around 50 others who I've help install Ubuntu Hardy on their computers, and they too are generally happy. The problems that I encountered on their systems were generally easily resolved by updating the preferences of the problematic applications to use the correct sound systems settings in most instances.

. 
> **pikseli@work said:**
> 
However, after consulting with developers and mavens, I find that REALITY is that ALSA and Pulseaudio and applications have conflicts that will take years to be resolved. Look into it

YEARS? I doubt the developers said it was seriously going to take years to work it out. ALSA is well documented and highly implemented.

Please provide factual evidence supporting this claim of &#8220;it will take years to resolve&#8221;. That sounds like &#8220;FUD&#8221; to me. 




.> **pikseli@work said:**
> 
I am not just making this up or the only one or using some esoteric hardware. This is imho real issue, case of releasing stuff that developers KNOW (or knew) simply isnt going to work. Thanks for your questions though.

You aren't really saying much about any actual problems. 

You're just stating that there are problems and that it shouldn't be released because the developers &#8220;KNOW&#8221; it isn't going to work.

A major reason that software is released before the final stage of the product, is so the software can be tried out on the largest selection of hardware available.

When a bug is found, it should then be reported to the appropriate bug tracker for the project in question. 

By doing that, the developers are able to work through the priority problems which can impact the largest number of people. Once the highest priority problems are fixed, they can move on to lesser priority problems and continue working on making advances to the code base in general.

This is not specific to the Pulseaudio project, but rather it applies to all software development projects. 

Developers fix the critical problems as soon as possible and then fix the minor problems as time allows.
 

> **pikseli@work said:**
> 
Thats what I mean with wrong impressions.

In order to lessen the possibility of creating the wrong impressions, it is good to always provide factual supporting evidence to support your claims when you believe there is a problem.


> **pikseli@work said:**
> 
I guess with Debian I got used to always being able to count on the fact that stable/final release and repository only has stuff that will work with minimal trouble and conflicts.I think these lines drawn in water, if thats what you were thinking.


Not sure where you are going with that, but perhaps you could clarify what you mean by it.

zipperback
:popcorn:

---

### Post by pikseli@work on 2008-08-09
Why is it a bad thing to accept realities?!? 

**Pulseaudio is not ready. Ubuntu is still in its audio-infancy!**

This "Windows User" argument keeps popping up, I dont know why, but I know what it means. I dont see it as relevant. 

I think Ubuntu is meant for End Users. HUMANS. Ubuntu doesn't make claims to be a geek OS, or ex-windowser OS, and so on.

Personally I am something of a "Debian User" at heart.

**hyper_ch **- It seems you do not have the whole picture about this Pulseaudio -issue. I may be mistaken.

We can argue and nitpick this small stuff for weeks, even months, it may be fun for you, in trollish or intellectual way...

But that wont help people 1) make better Ubuntu, 2) get the audio working, 3) learn*from mistakes and choose better developement strategies in the future.

**beniwtv** - Like hyper, your point is evidently that I shouldn't criticise Ubuntu and create more discussion on the Pulseaudio -issue, "Because it works for some people"? Sorry, but thats a really weak argument. And since you do not know how many bug reports I have filed.. Sigh.

This very thread is an attempt to contribute, and yet you seem to want me to shut up, instead of actually talking about Pulseaudio/Ubuntu -issues.

Hey, by writing this thread - **if I can help just one one musician to save their time and for now go with something else than Ubuntu, that makes me happy.**

Because instead of hours of making music, I have spent hours configuring my Ubuntu, and that is bad and has made me angry and frustrated and I dont think thats the original intention behind "Ubuntu for Human Beings." 

Whether **you** think that Pulseaudio has problems or not doesn't make the problems go away - so in that sense you are victim of the very egocentrism you think I am victim of.

Not even Pulseaudio developers think that it would work great for everybody or every app. There are many known conflicts. Look into it, google, go to Pulseaudio site.

CameO73 - Yes, I guess the bottom line is: too much, too soon. I keep wondering is Ubuntu really in such a hurry? To do what, win Windows? Since the release cycle is only 6 months, why did there have to be this kind of Beta in the final release. 

OTOH, with browsers I can sort of understand that, and FF3 Beta wasn't a complete disaster at all.

I am really starting to understand the logic and experience behind Debian's release cycles, and the result of rushing... or should I say *feel*, in my musical nerve, still yearning...

---

### Post by zipperback on 2008-08-09
> **CameO73 said:**
> Let's at least stop the "if you don't like it, don't use it" answers. Those don't help anyone. Yes, Ubuntu has some problems. No, they don't disappear overnight. Stop killing the messenger and listen to the message.


If someone doesn't like the Ubuntu distribution they decided to use, and it isn't going to meet their needs, then they shouldn't be using it.

That's plain, simple, and straight to the point.

If there is a problem and something isn't working, then the choice is simple. Move on to something which will work and meet their needs.

Ubuntu isn't the right choice for everyone, Just like Windows isn't the right choice for everyone.

Just about everyone will have a different idea in what they want to accomplish and what will work best to meet their goals.

If someone doesn't feel that Linux will meet their needs, then perhaps they should try some other operating system. 

There are hundreds of different distributions of open source operating systems available.

There's Ubuntu, Kubuntu, Edubuntu, Xubuntu, Debian, Fedora, FreeBSD, OpenBSD, NetBSD, the list goes on and on. Just look at [http://www.distrowatch.com]("http://www.distrowatch.com") and you can see what I mean. 

If a person decides that an open source operating system isn't going to do what they want, and they honestly feel they can meet their needs in the best possible manner using Windows, OS X, or some other closed source operating system, then my opinion is “Go head! Use what works best for YOU!” 

Whatever a person decides to use is up to them, my advice is simply to do as much research as possible and make the most informed decision as to what will work best for their needs, and what will provide the greatest compatibility with the hardware they have available. It's pointless to select an operating system to use if the hardware you have available isn't able to be used by the operating system in question.

For my business and personal needs, I use an open source operating system, which happens to be Ubuntu Hardy.

- zipperback
:popcorn:

---

### Post by pikseli@work on 2008-08-09
> **zipperback said:**
> I have Ubuntu Hardy installed on my laptop and I am not having any problems with my audio. I personally know of around 50 others who I've help install Ubuntu Hardy on their computers, and they too are generally happy. 
Oh ok, so we have at least 56 people that it works for, for some use. Oh, I guess we can all go home now, quit developing Pulseaudio and Ubuntu, and screw all the people it doesnt work for, huh? Screw all these bug reports etc? Lets tell everyone no problems exist and Ubuntu is 100% ready? [http://www.pulseaudio.org/report/1?sort=type&asc=1](http://www.pulseaudio.org/report/1?sort=type&asc=1)
:-P

Again, thats simply not an argument with software dev & Ubuntu.

> YEARS? I doubt the developers said it was seriously going to take years to work it out. ALSA is well documented and highly implemented.

Please provide factual evidence supporting this claim of “it will take years to resolve”. That sounds like “FUD” to me. 


But you haven't looked into it, huh? And now you demand *I* should do your homework for you here, even if all *I wanted was to make some beautiful music*.

"Sounds like FUD" is not good enough. Your thinks are just conjecture. 

The fact that transition to (hope-fully) working Pulseaudio will take at least a year or two is reality.

Look into whats ALSA, whats Pulseaudio and how applications work with them now, and how they are supposed to work in the future. Simply put, aside from ALSA-Pulseaudio-conflicts, if you look into it, you will realize that current apps are not built for Pulseaudio, and will have to be changed to support it.

A year is a short time in software developement.

> You aren't really saying much about any actual problems. 

You're just stating that there are problems and that it shouldn't be released because the developers “KNOW” it isn't going to work.


In order to lessen the possibility of creating the wrong impressions, it is good to always provide factual supporting evidence to support your claims when you believe there is a problem.


This is not a support forum. But yes, if you just keep your eyes really really closed maybe the problems will disappear and all will suddenly be good and fine?

Funny, your ideation reminds me of an ostrich. I wonder why? 

I feel here with this it is now you who will have to look for your own 'evidence', as I *really* want to make some music now, whether I can record and edit on my computer or not. 

Thanks for comments.

---

### Post by hyper_ch on 2008-08-09
> **pikseli@work said:**
> Why is it a bad thing to accept realities?!?
I do but you seem not to... as said, for a great many people it works just fine - but for you it doesn't. Because it doesn't for you, you are of the opinion that it must be really bad quality software.

> **pikseli@work said:**
> Pulseaudio is not ready. Ubuntu is still in its audio-infancy!
See above.

> **pikseli@work said:**
> This "Windows User" argument keeps popping up, I dont know why, but I know what it means. I dont see it as relevant.
You forgot the thread title you chose? ;)
 
> **pikseli@work said:**
> Personally I am something of a "Debian User" at heart.
And this has a relevance to this thread in ..... ?

> **pikseli@work said:**
> It seems you do not have the whole picture about this Pulseaudio -issue. I may be mistaken.
You might very well be...

> **pikseli@work said:**
> We can argue and nitpick this small stuff for weeks, even months, it may be fun for you, in trollish or intellectual way...
Ah, getting onto a personal level here by calling the other one a troll... this normally happens if you run out of arguments or if you have no arguments first-place.

> **pikseli@work said:**
> But that wont help people 1) make better Ubuntu, 2) get the audio working, 3) learn*from mistakes and choose better developement strategies in the future.
That's good... but (1) audio is working just fine and (2) did you submit bugs?

> **pikseli@work said:**
> Like hyper, your point is evidently that I shouldn't criticise Ubuntu and create more discussion on the Pulseaudio -issue, "Because it works for some people"? Sorry, but thats a really weak argument. And since you do not know how many bug reports I have filed.. Sigh.
It works for most people because otherwise there would be an aweful lot more threads all over UF on that issue. Since there are hardly any I think it's safe to assume that it works for most just fine.
Besides criticising is a good thing... as long as it's positive critics. I refer to thread title again and any fool should see that it's not criticising but bashing. I still fail to see any mentioning of you to have submitted any bug-report.

> **pikseli@work said:**
> This very thread is an attempt to contribute, and yet you seem to want me to shut up, instead of actually talking about Pulseaudio/Ubuntu -issues.
If you are so much debian-experienced as you say then you should now all too well that you should submit bugs. So I don't really see this as an attempt to contribute.

> **pikseli@work said:**
> Because instead of hours of making music, I have spent hours configuring my Ubuntu, and that is bad and has made me angry and frustrated and I dont think thats the original intention behind "Ubuntu for Human Beings."
There we go. Thx for admitting this thread started out of anger and frustration. Yet you still claim to want to be helpful.

> **pikseli@work said:**
> Not even Pulseaudio developers think that it would work great for everybody or every app. There are many known conflicts. Look into it, google, go to Pulseaudio site.
Well, any sane developper would not admit that his software works on every possible configuration perfectly without any bugs... not even M$ manages this on a single plattform with their resources.

> **pikseli@work said:**
> Yes, I guess the bottom line is: too much, too soon. I keep wondering is Ubuntu really in such a hurry? To do what, win Windows? Since the release cycle is only 6 months, why did there have to be this kind of Beta in the final release.
As said before: Pulseaudio works for most people just fine. So it's nowhere in such a state as you claim it to be.

---

### Post by pikseli@work on 2008-08-09
Trolling, huh? Arguing with you whether my experience of not getting sound recording workstation running properly is reality or not is like participating in the special olympics. 

I want to give you props for your faith in the superbness of Pulseaudio - your Zeal is similar to the chinese communists in the 50's who yelled a lot and thumped Mao's little red book and lynched and mobbed people for just arguing with them.

---

### Post by hyper_ch on 2008-08-09
> **pikseli@work said:**
> Trolling, huh? Arguing with you about my experience that I cannot get sound working is like participating in the special olympics.

q.e.d.

---

### Post by hyper_ch on 2008-08-09
Just arrived by PM:
> **pikseli@work said:**
> 
 Hey friend
Dude, do you have problems.

I suggest you try to deal with them. And maybe a little holiday.

And if you want to contribute positively, why not try actually UNDERSTANDING PEOPLE, instead of trying to FORCE THEM INTO CONFORMING TO YOUR IDEOLOGY.

That just does not work. People want to be free.

Your zeal just makes you ignore stuff you dont want to see, like the fact that the frustration is a very good source of positive contributions, and thats how dozens of OS projects started.

Sound any good? Trolling on here wont make you feel any better about yourself, you know?

Well, all the best! I hope you get over it soon.

As said, if one runs out of arguments or finally notices his arguments have no point at all they slip to a personal level (sort of the same goes for shouting... shouting does not add any credibility to the arguments - au contraire it weakens them)
Thx for that pm ;)

Besides, as said above: q.e.d.

---

### Post by pikseli@work on 2008-08-09
hyper_ch - Ok, I admit it, if thats what will make you happy. 

All my experiences of audio failing, all the time I put into trying to get it working, and all the hours wasted hacking incomplete solution instead of making beautiful music was MY PERSONAL FAILURE. Yes, the audio didnt work because I was mistaken, wrong and generally a bad person.

Now are you happy? Now did things suddenly get all better? Funny, I still dont have these compositions on CD, still cant mix mp3s, or record multitracl. Hmm, I still dont get proper audio.

Funny, despite admitting to my incapability of reporting every bug so that hyper_ch is happy, none of the audio problems went away. Still many users in the multimedia & drivers forum that have no sound or only 'monophonic' sound and problems exist.

Funny, despite my personal shortcomings that I admitted to, as per hyper_ch attacks subdued me - end users STILL have to configure audio drivers and layers and whatnot, instead of making music!!

Gosh, I am so confused now. Which reality is true, hyper_ch's or this other?

---

### Post by hyper_ch on 2008-08-09
> **pikseli@work said:**
> hyper_ch - Ok, I admit it, if thats what will make you happy.
What makes me happy is of no relevance ;)
 
> **pikseli@work said:**
> All my experiences of audio failing, all the time I put into trying to get it working, and all the hours wasted hacking incomplete solution instead of making beautiful music was MY PERSONAL FAILURE. Yes, the audio didnt work because I was mistaken, wrong and generally a bad person.

Now are you happy? Now did things suddenly get all better? Funny, I still dont have these compositions on CD, still cant mix mp3s, or record multitracl. Hmm, I still dont get proper audio.
As said, my personal happiness is of no relevance ;)

> **pikseli@work said:**
> Funny, despite admitting to my incapability of reporting every bug so that hyper_ch is happy, none of the audio problems went away.
well, not reporting any bugs leads to that devs don't know there is something to fix and that leads to that the bugs don't get fixed. And you are surprised it got not fixed?

> **pikseli@work said:**
> Still many users in the multimedia & drivers forum that have no sound or only 'monophonic' sound and problems exist.
Still very little complains compared to the gravity as you make the problem sound like. There should be a lot more complaints. Hence I still assume it's not as bad as you make it sound.

> **pikseli@work said:**
> Funny, despite my personal shortcomings that I admitted to, as per hyper_ch attacks subdued me
What attacks? I only stated that you like to slide to a personal level and drew my conclusions from it.

[/QUOTE]Gosh, I am so confused now. Which reality is true, hyper_ch's or this other?[/QUOTE]
Maybe you should follow your own advice in the pm sent to me.

---

### Post by zipperback on 2008-08-09
> **pikseli@work said:**
> Why is it a bad thing to accept realities?!? 

The acceptance of reality of not a bad thing, it is a good thing in my opinion.

The acceptance of a falsehood as a fact is unacceptable.


> **pikseli@work said:**
> Pulseaudio is not ready.

I've not been experiencing any problems which I could not resolve on my system.
I am running Ubuntu Hardy with the currently available updates applied.


> **pikseli@work said:**
>  Ubuntu is still in its audio-infancy!

I disagree. You're statement is a generalization, as not everyone has the same needs in regard to audio.

For example, I have Ubuntu Hardy 8.04.1 installed on my laptop, and I watch movies, listen to streaming audio, create mp3's, backup my mp3 player, and perform numerous other tasks which are related to the management of my needs in regard to audio.

I'm quite happy with Ubuntu, and have not experienced any problems which I could not resolve at this point in time.


> **pikseli@work said:**
> 
This "Windows User" argument keeps popping up, I dont know why, but I know what it means. I dont see it as relevant. 

Linux is not Windows. This is a fact. Things don't work the same as Windows, nor should they be expected to do so.


> **pikseli@work said:**
> I think Ubuntu is meant for End Users. HUMANS. Ubuntu doesn't make claims to be a geek OS, or ex-windowser OS, and so on.

Ok. So I guess this is going to show my age a little here but I thnk it's a valid point I have about this.

I started using “personal computers” back in 1979 when I began learning how to use them. I started out with an Apple ][+. Since that time, I've went from being a causal computer user, to being a person who has worked professionally in the industry for numerous years.

As far as Linux in general goes, it is a very powerful operating system which has an overall excellent community of developers, and has come a very long way in recent years.

As far as the Ubuntu distribution is concerned in my opinion, I really think it's an excellent distribution and the ideology behind his is a really solid one. It does a really good job of allowing people to get Linux installed on their computers with very minimal problems, and makes it very easy to manage the system using Synaptic Package Manager. And yes, I am fully aware that all “modern” Linux distributions have some sort of package management system. I've just using this as an example of ease in which people can manage their system.

And for those people who want to get into their system and make changes to it at a more technical level, there is nothing to prevent you from doing so. All you need to do is “Applications &#8594; Accessories &#8594; Terminal” and you can do whatever it is that you want to do at the CLI.

When it really comes down to it, once any Linux distribution is installed and fully configured, if a person knows what they are doing, then it's really all the same, it's all “Linux” and you can do pretty much the same thing on any Linux distribution.

I like the fact that Ubuntu is a quick and easy installation and most things just work right out of the box for me. This isn't to say that I wouldn't have a similar experience using some other distribution, but it is saying that the things that Ubuntu does, it does really well.


> **pikseli@work said:**
> 
Personally I am something of a "Debian User" at heart.

As are all Ubuntu users. Debian is what Ubuntu is based upon. 



> **pikseli@work said:**
> 
**hyper_ch **- It seems you do not have the whole picture about this Pulseaudio -issue. I may be mistaken.We can argue and nitpick this small stuff for weeks, even months, it may be fun for you, in trollish or intellectual way... But that wont help people 1) make better Ubuntu, 2) get the audio working, 3) learn*from mistakes and choose better developement strategies in the future.

**beniwtv** - Like hyper, your point is evidently that I shouldn't criticise Ubuntu and create more discussion on the Pulseaudio -issue, "Because it works for some people"? Sorry, but thats a really weak argument. And since you do not know how many bug reports I have filed.. Sigh.


You are correct. We don't know how many bug reports you've filed. However, it's always a good idea to follow up on your bug reports and to take an active participation in the resolution of those bugs whenever possible.


> **pikseli@work said:**
> 
This very thread is an attempt to contribute, and yet you seem to want me to shut up, instead of actually talking about Pulseaudio/Ubuntu -issues.

The problem as I see it with  threads like this one, is that some people provide very little if any factual evidence as to what they perceive the problem to be. 

I've personally seen thread after thread where someone will come across a problem and then say things like “XXXXXX distribution sucks. It doesn't work. This is crap.”, But yet they fail to provide any supporting evidence. And quite often the “bug” they have found isn't a bug at all, but the simple matter that someone has forgotten to do something as simple as change the preferences in their audio application. 
I've personally encountered numerous threads where people post the thread to just vent out their anger about some problem they are having, but then they do nothing to help themselves resolve the problem.

> **pikseli@work said:**
> 
Hey, by writing this thread - if I can help just one one musician to save their time and for now go with something else than Ubuntu, that makes me happy.

Rather than stopping someone from using Ubuntu, why not help resolve the problems and make the distribution all that much better. No operating system is perfect. If you want it to get better, then try to help fix it. 

> **pikseli@work said:**
> 
Because instead of hours of making music, I have spent hours configuring my Ubuntu, and that is bad and has made me angry and frustrated and I dont think thats the original intention behind "Ubuntu for Human Beings." 

And having worked through all the many problems you encountered, did you create any howto documents which can help others resolve those problems? Did you create any scripts which can help others to automatically configure their systems to avoid those problems?


> **pikseli@work said:**
> 
Whether **you** think that Pulseaudio has problems or not doesn't make the problems go away - so in that sense you are victim of the very egocentrism you think I am victim of.

Clearly I've not experienced the level of frustration with my computer that you are experiencing with your audio. However, simply because you've had a bad experience, it doesn't mean that everyone is having the same level of frustration as you are.

I find it somewhat interesting that you've made this statement however:


> **pikseli@work said:**
>  ** so in that sense you are victim of the very egocentrism you think I am victim of.**

The word “egocentrism” is defined as: * limited in outlook or concern to one's own activities or needs*.

I find it interesting because you're making the assumption that others shouldn't use Ubuntu because YOU had a bad experience with it.

Linux us about FREEDOM. And others should have the freedom to make their own decisions about what works best for them, yet you want to persuade others to not use Ubuntu because you don't think they should.


> **pikseli@work said:**
> 
Not even Pulseaudio developers think that it would work great for everybody or every app. There are many known conflicts. Look into it, google, go to Pulseaudio site.
No application will work for everyones needs. To assume that it would, is an unreasonable assumption.


> **pikseli@work said:**
> 
CameO73 - Yes, I guess the bottom line is: too much, too soon. I keep wondering is Ubuntu really in such a hurry? To do what, win Windows? Since the release cycle is only 6 months, why did there have to be this kind of Beta in the final release.

It isn't about “win Windows”. It's about making advances for the distribution in general. You're experience isn't the typical experience of most users. And you're level of frustration is focused primarily it seems on only one areas which appears to be problematic.


 
> **pikseli@work said:**
> 
OTOH, with browsers I can sort of understand that, and FF3 Beta wasn't a complete disaster at all.

It's great browser in my opinion, but not everyone feels that same way. It's all about choice. Use whatever works best for you. And allow others the freedom to make their own choices about what works best for them.

> **pikseli@work said:**
> 
I am really starting to understand the logic and experience behind Debian's release cycles, and the result of rushing... or should I say *feel*, in my musical nerve, still yearning...

Ubuntu Hardy is an LTS release. As stated on the Ubuntu website “With the Long Term Support (LTS) version you get three years support on the desktop, and five years on the server.”

It's a long time before the next LTS release. It isn't a rushed release.

Each time there is a new release of just about any distribution, there are always people who come forward and claim “This is the worst release” or “Why'd they do this?” and things like that.

The distribution is exactly what it is. It's the next release of Ubuntu. Yes there are some problems, but those problems really aren't that big of a deal if you consider everything that goes into creating a new release version.

If the current version of Ubuntu isn't working for you, but the previous version worked great, then just go back to using the previous version. It's still a very viable option and no one is telling you that you can't do it. 

zipperback

:popcorn:

---

### Post by pikseli@work on 2008-08-09
Ok, suppose that your disbelief is solid and honest, and not just argumentative, provocative or lazyness. 

I *still* think you did not understand what this thread is about. 

To clarify what I feel the problem is: its not if *some sound* for *some apps* work, but if *making music with ubuntu or ubuntu studio actually works or not*.

As you can see, I have related my experience in simple terms. Arguing that wont help.

Then, if you really are willing to see "how deep the rabbit hole goes" (or is this how high is the mole hill?) ...

I would like to ask you to trial these minimal sound recording tasks on your Ubuntu:

* Can you get multitrack recording working on your computer so that the very very basic task of recording audio from audio input while previously recorded audio is playing? 

Using any of the audio suites included in Ubuntu repos, or for example Energy XT?

* Can you get Jack audio server working, chain few effects and some audio generator and get audio output? Or even stereo audio output WITHOUT choppyness?

See what I mean? Well, maybe it works for you. To me it seems to be as far as Fiji.

---

### Post by PmDematagoda on 2008-08-09
With the last comments in this thread, I think it has gone far enough.

This thread is closed.

---

