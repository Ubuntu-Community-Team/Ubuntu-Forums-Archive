---
title: "Seriously, what's the point of PulseAudio?"
date: 2009-07-07
forum: The Cafe
---

### Post by AmyRose on 2009-07-07
I have heard of so many users on the forums having problems with it, and it just doesn't make any sense to me because ALSA has dmix, which mixes the audio streams. And almost any OSS program can be dmixed too with aoss from the alsa-oss package.

So seriously, what's the point of having PulseAudio on a typical desktop system? I don't need network transparency, and I doubt that many of the users Ubuntu is targeting need it too.

I apologize if this has been asked before, but I spent a couple hours poking around the forums and searching for an answer on this, and came up with nothing useful. And I'm sorry if this is in the wrong section.

---

### Post by ssam on 2009-07-07
it brings new features and works well for most people.

it also exposes some bugs in alsa, but those will get fixed. networkmanager exposed bugs in the wireless drivers, now these are fixed wireless on linux is much improved.

---

### Post by lovinglinux on 2009-07-07
Pulseaudio is only causing problems for me. I tried to fix it, but ended removing it completely on my desktop running Jaunty. A notebook, running Intrepid, also started to display performance issues since a couple of weeks ago, with Firefox going grey very often and slowing down the machine to a point of no return. So I also removed pulseaudio from it two days ago and Firefox isn't freezing anymore. It just goes grey eventually, but comes back.

---

### Post by wbee on 2009-07-07
To your question:

I don't know.

That said,I appreciate that Ubuntu is a labor of love among many volunteers. I have not taken a sample and counted it;but it seems,at least anecdotally,that sound issues are among the most frequently posted problems on these fora.

(If you have not found it already,) A Google search will take you to the Pulse Audio site. A page there is labeled,"the perfect set up". Sadly,this distribution is imperfect. Markbuntu has a post that recurs often,explaining how to get PA working properly.

Since I don't need a recording studio,don't need something to connect with "Jack",I use PA for one purpose only,to combine outputs from two sound cards.

The aforementioned site has a FAQ page that FINALLY explained to me how to get sound from my TV tuner card,that samples at 35.0 instead of at 44.1. There is a Pulse Audio command that will combine the output of cards 0 and 1,automatically resampling the 35.0 to 44.1.

Speaking for myself,that is the only reason I do not simply use AlSA.

It's been asked before and will be,no doubt,asked again.

---

### Post by AmyRose on 2009-07-10
> **ssam said:**
> it brings new features and works well for most people.What new features does it bring that most people need? And looking at these forums, and my friends' experiences, I doubt it works well for most people.
> **ssam said:**
> it also exposes some bugs in alsa, but those will get fixed. networkmanager exposed bugs in the wireless drivers, now these are fixed wireless on linux is much improved.Network manager filled a gap that was much needed: an easy GUI-based way to configure the network. Again, what new features does PulseAudio bring to the table that most people need? Key word here is need.

> **lovinglinux said:**
> Pulseaudio is only causing problems for me. I tried to fix it, but ended removing it completely on my desktop running Jaunty. A notebook, running Intrepid, also started to display performance issues since a couple of weeks ago, with Firefox going grey very often and slowing down the machine to a point of no return. So I also removed pulseaudio from it two days ago and Firefox isn't freezing anymore. It just goes grey eventually, but comes back.This sounds like the type of trouble I, and most other people with sound issues, seem to have with it.

> **wbee said:**
> To your question:

I don't know.Then why did they force it on everybody in the first place?

> **wbee said:**
> That said,I appreciate that Ubuntu is a labor of love among many volunteers.Oh, I appreciate that too.

> **wbee said:**
> I have not taken a sample and counted it;but it seems,at least anecdotally,that sound issues are among the most frequently posted problems on these fora.And most of them seem to be PulseAudio-related. Gee, I wonder why!

> **wbee said:**
> (If you have not found it already,) A Google search will take you to the Pulse Audio site. A page there is labeled,"the perfect set up". Sadly,this distribution is imperfect. Markbuntu has a post that recurs often,explaining how to get PA working properly.

Since I don't need a recording studio,don't need something to connect with "Jack",I use PA for one purpose only,to combine outputs from two sound cards.

The aforementioned site has a FAQ page that FINALLY explained to me how to get sound from my TV tuner card,that samples at 35.0 instead of at 44.1. There is a Pulse Audio command that will combine the output of cards 0 and 1,automatically resampling the 35.0 to 44.1.

Speaking for myself,that is the only reason I do not simply use AlSA.

It's been asked before and will be,no doubt,asked again.Well, I can understand that some people will need it, but I don't understand why it's installed by default when it causes problems for so many users on the forum.

---

### Post by malrost on 2009-07-10
No offense to the pulseaudio team intended. Despite the following criticism, I'm still trying to learn and incorporate pulseaudio. It works well enough for media sound --flash, video, amarok, games.

From what I understand, pulseaudio's design incorporated a method that avoided a security flaw that arose after a larger-level kernel modification a while back that pushed the ALSA drivers into the kernel. In went pulseaudio, because warts and all it eliminated a basic security vulnerability that would arise from letting user applications have direct access to a kernel driver.

Despite the security flaw that arose w/ ALSA, the interface was fairly refined, and the move to pulseaudio meant the control interface had not (and still has yet to) gone through enough revisions yet.

Additionally, the ubuntustudio packages have addressed probably the biggest previous obstacle to low latency recording w/ jack & ALSA apps: you had to compile your own a kernel w/ Ingo Molnar's real time kernel patch. It's not particularly difficult to do, but certainly not for the feint of heart. Selecting a package is easier than compiling a kernel. 

ALSA's maturity meant its control interface had a level of sophistication and revision, whereas going from alsamixer and qjackctl to PulseAudio Manager still seems a step backwards, conceptually. 

The pulse approach to ins and outs --of separating devices from clients, for example, seems an arbitrary distinction. When you're trying to conceptualize sound as paths from noise to ear, who cares if you call something a sink or a source? The distinction seems so unnecessary.

IMO, qjackctl in particular in an example of great interface design. The simplicity of the layout is logical, consistent, and scales well. Advanced hardware configuration is easily accessible.

---

### Post by FuturePilot on 2009-07-10
> **AmyRose said:**
> 
Network manager filled a gap that was much needed: an easy GUI-based way to configure the network. Again, what new features does PulseAudio bring to the table that most people need? Key word here is need.
It brings a GUI to sound configuration among other things. For example, right now with PulseAudio, if you have 2 sound cards, you can with a point and click of the mouse change the default sound card. Prior to PulseAudio, if you wanted to do this, you needed to edit an extremely obscure and mind bogglingly confusing configuration file. People always say we need a GUI for this type of thing, now we have one.



> And most of them seem to be PulseAudio-related. Gee, I wonder why!
But most of the time, the root of the issue is not in PulseAudio, it's usually a driver bug. This has happened at least in two other instances. As someone already mentioned, Network Manager exposed numerous driver bugs that otherwise were hard to find and difficult to reproduce and would have taken much much longer to fix. Instead of hacking around misbehaving drivers, the real way to fix these issues is to fix the root of the problem, the drivers. Another example of this is Compiz. When Compiz first came out, it exposed all sorts of driver problems and Xorg problems. People always blamed it on Compiz itself when it was actually a driver problem.

---

### Post by CharmyBee on 2009-07-11
Is unusually high latency a driver bug?

---

### Post by 23meg on 2009-07-11
[http://0pointer.de/blog/projects/jeffrey-stedfast.html](http://0pointer.de/blog/projects/jeffrey-stedfast.html)

---

### Post by frup on 2009-07-11
Correct me if I'm wrong, but before Pulse Audio I could only get one application playing sounds at once. This meant that if I had rhythmbox open and something in my browser such as flash made a sound, one of the two wouldn't work. I have had no problems with sound since PA was introduced.

If people are having problems now, if the case is the same as NM, then in a short time things will be better than they ever were before.

---

### Post by PurposeOfReason on 2009-07-11
> **frup said:**
> Correct me if I'm wrong, but before Pulse Audio I could only get one application playing sounds at once. This meant that if I had rhythmbox open and something in my browser such as flash made a sound, one of the two wouldn't work. I have had no problems with sound since PA was introduced.

If people are having problems now, if the case is the same as NM, then in a short time things will be better than they ever were before.
You could always have more than one output.

IMO, linux really needs to just settle down with audio. Do the whole take a step back and think type thing. We have alsa, oss, gstreamer, xine, jack, pulse, the list goes one. For media players, choice is good. For getting audio to be configured right and to play it should be basic. If that requires a major project, which it would, get started sooner rather than later because all we seem to be doing is adding layers upon layers to fix problems. Sounds good when it all works, but if the bottom layer breaks, everything does.

---

### Post by michaelzap on 2009-07-11
> **frup said:**
> Correct me if I'm wrong, but before Pulse Audio I could only get one application playing sounds at once.

I'm pretty sure that you're wrong on that. I use Alsa now (in order to get 5.1 sound on my Lenovo laptop), and I can play sound in multiple programs at once. I think maybe you're describing a bug related to Flash audio in particular playing well with other software.

---

### Post by pt123 on 2009-07-11
to have an all round "buginess" feel to Ubuntu/Gnome

---

### Post by dragos240 on 2009-07-11
> **ssam said:**
> it brings new features and works well for **very few** people.

it also exposes some bugs in alsa, but those will get fixed. networkmanager exposed bugs in the wireless drivers, now these are fixed wireless on linux is much improved.

Fixed.

---

### Post by stimpack on 2009-07-11
Found this rather interesting on the state of the various Linux sound systems. [http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

As it is a blog I'd rather have some more sources, but ignoring OSSv4 for an ever expanding collection of systems that break at least one audio application on my computer since day 1 of using linux, is not a good thing.

---

### Post by SunnyRabbiera on 2009-07-11
Well pulse currently brings little to the table, but soon it will be a major audio sound system.
Pulse promises to bring multiple sound playback, incredible sound card compatibility and extra sound effects.

---

### Post by 3rdalbum on 2009-07-11
Well, let's put on our memory caps.

Years ago, some programs supported only OSS, and some supported only ALSA. If you were using an OSS program you could not hear any other programs, and if you were using only ALSA programs and you tried to start an OSS program it would not be able to give you any sound.

Pulseaudio wraps around your other sound systems, so you don't need to worry about what sound system is in use. And it works very well; I haven't had any problems with Pulseaudio for ages.

There are also individual volume controls for each application. If you say "Who cares, I already have a volume control in Rhythmbox" then you're missing the point, which is that a lot of programs that generate sound aren't the kinds of programs that have volume controls. Ever watched a quiet scene in a movie on Blu-ray and had your instant messenger open at the same time?

The network transparency in Pulseaudio is actually quite useful, if you're creative :-)  I'm sure in the 1990s people were saying "Why is X11 network-transparent", and now it's acknowledged as a useful feature.

And finally, all this stuff is trivial to set up in Pulseaudio, whereas ALSA is still a nightmare to configure.

---

### Post by SunnyRabbiera on 2009-07-11
Hahah the phail ad bot :D

---

### Post by ddrichardson on 2009-07-11
Its all well and good to blame pulse audio but there's a very good argument to blame ourselves, Ubuntu. Jeffrey Stedfast (already linked to [above]("http://is.gd/1uCaQ")) has said it himself very succinctly:> I work for Red Hat and PulseAudio is not part of RHEL at this time.I think there are a couple of decisions made recently about default installs and distribution software that are not necessarily in the best interests of the distribution - Empathy being a point in case - yes the Telepathy framework is better and there are issues with Pidgin point blank refusing to do video support but really, is Empathy ready?  As sabdfl said "[Pretty is a feature too]("http://www.markshuttleworth.com/archives/63")".

---

### Post by 23meg on 2009-07-11
> **ddrichardson said:**
> Jeffrey Stedfast (already linked to [above]("http://is.gd/1uCaQ")) has said it himself very succinctly:

It's Lennart Poettering saying that; Stedfast is the "topic" of the post.

---

### Post by ddrichardson on 2009-07-11
> **23meg said:**
> It's Lennart Poettering saying that; Stedfast is the "topic" of the post.
My bad but the point still stands.

---

### Post by Icehuck on 2009-07-11
> **AmyRose said:**
> I have heard of so many users on the forums having problems with it, and it just doesn't make any sense to me because ALSA has dmix, which mixes the audio streams. And almost any OSS program can be dmixed too with aoss from the alsa-oss package.

So seriously, what's the point of having PulseAudio on a typical desktop system? I don't need network transparency, and I doubt that many of the users Ubuntu is targeting need it too.

I apologize if this has been asked before, but I spent a couple hours poking around the forums and searching for an answer on this, and came up with nothing useful. And I'm sorry if this is in the wrong section.


It's a bandaid fix that does absolutely nothing for linux. Sound has always been an issue on linux and that trend will most likely continue. This is where there needs to be a standard way of doing things. Pick OSS or ALSA and make one of those work. Those programs that only depend on one or the other will get ported over. So what's the problem? Everyone has to do 20 different things...

---

### Post by tjwoosta on 2009-07-11
I have had many problems with pulse audio, especially with games. Eventually I just gave up on it and set up alsa, now everything works perfect.

I agree that pulse audio could be great, once all of the bugs are worked out, but the fact that it is still so buggy is a damn good reason to not include it in an official release. Is there any reason that everyone who uses ubuntu is forced into testing buggy software? I can see how having every single ubuntu user as a guinea pig could really speed up development, but come on now. Keep buggy software in testing releases!

Weather the bugs are rooted in the pulse audio software itself, or in the drivers should not make a difference. If it's only when using pulse audio that all the bugs are exposed, how about just not use pulse audio until the bugs are fixed regardless of where the bugs are coming from? They can figure that stuff out in testing. Instead ubuntu says well ok were just going to use it anyway, despite the hundreds of people who have issues with it.

---

### Post by swoll1980 on 2009-07-11
Nobody is being forced into anything. If you don't like PA uninstall it. If **hundreds** of people have problems with it, that wouldn't be so bad considering their are **millions** of people using Ubuntu. That's way less than 1%.

---

### Post by tjwoosta on 2009-07-11
Obviously hundreds of people was just an estimate off the top of my head, I dont actually know how many people have problems with pulse audio, but Im sure its greater then 1%.

---

### Post by michaelzap on 2009-07-11
> **swoll1980 said:**
> If **hundreds** of people have problems with it, that wouldn't be so bad considering their are **millions** of people using Ubuntu. That's way less than 1%.

Strictly speaking, that's not a logical conclusion. He didn't say how many hundreds, so there's no way of knowing what percentage this rough estimate implies. It could be thousands of hundreds...

And in any case, no word game can cover up that a significant percentage of Ubuntu users have experienced very frustrating issues with PA, which to me makes me wonder whether it should have been rushed into the main distro.

I for one had absolutely no audio issues before PA was introduced...

---

### Post by swoll1980 on 2009-07-11
> **michaelzap said:**
> Strictly speaking, that's not a logical conclusion. He didn't say how many hundreds, so there's no way of knowing what percentage this rough estimate implies. It could be thousands of hundreds...


I'm pretty sure he would have said hundreds of thousands, if that's what he meant. He seems like a pretty smart guy. I don't think he would ever use a term as stupid as thousands of hundreds. I can't really think of anyone older than 6, or 7, years old that would say thousands of hundreds, unless maybe they were mentally handicapped.

---

### Post by michaelzap on 2009-07-11
> **swoll1980 said:**
> I'm pretty sure he would have said hundreds of thousands, if that's what he meant. He seems like a pretty smart guy. I don't think he would ever use a term as stupid as thousands of hundreds. I can't really think of anyone older than 6, or 7, years old that would say thousands of hundreds, unless maybe they were mentally handicapped.

What happens when you make assumptions:
[http://www.soakingwetchild.net/thebadnewsbears/manningdontassume.aif](http://www.soakingwetchild.net/thebadnewsbears/manningdontassume.aif)

Obviously whatever he said or meant to say has zero bearing on how many Ubuntu users actually have had issues with PA, so I don't see much point in a word game based on an offhand comment.

---

### Post by AllenGG on 2009-07-11
[SIZE=4]**First: it is a reasonable question. **[/SIZE]
but looking at [http://www.pulseaudio.org/](http://www.pulseaudio.org/) is a good start.
Quite a few Ubuntu users have stated flatly that "PulseAudio" is a mistake.*** It is not,***
here's why.
Most of the basic problems come from the sound cards, is yours set up correctly ?
.........._.no surprise that's about half the complaint_s.
Did you set up PulsaAudio correctly ? I didn't at first, trying to rush, on a previous setup.
Did your soundcard have issues with PA ? mine did (SB Live! EMU10K10) easily fixable.

Since PA is cross platform a lot of previous problems were eliminated. Many "players" now work  that seemed out of it before. Like a typical Ubuntoad I've got about 6 or 7 players. "Listen" being my fav of the day. Movies now play with great sound !!!
Oops more like 20 players.
[SIZE=4]**Anyway, it's about "choice".**[/SIZE]  [B]
And that's what PulseAudio gives us.         :cool:
[/B]

---

### Post by Swarms on 2009-07-11
> **michaelzap said:**
> And in any case, no word game can cover up that a significant percentage of Ubuntu users have experienced very frustrating issues with PA, which to me makes me wonder whether it should have been rushed into the main distro.

I for one had absolutely no audio issues before PA was introduced...

Are you delivering facts here or are you just pulling numbers out from your behind?

One fact remains though, the unhappy minority voices often drowns the majority.

---

### Post by michaelzap on 2009-07-11
> **Swarms said:**
> Are you delivering facts here or are you just pulling numbers out from your behind?
Do you see any numbers in my post?

---

### Post by oldsoundguy on 2009-07-11
my personal experience with Pulse .. it sux!!  Just because I got it to work fine in digital output for about 3 months, then an update killed my Creative card and NO sound works now, not even analog.  

On three other Ubuntu based machines, I did NOT install  Pulse and the ANALOG works fine on them.

IMO, it is an experiment that has gone WAY BAD and needs to be totally re-evaluated .. and FIXED in all forms of Ubuntu .. not just the next release.

---

### Post by Swarms on 2009-07-11
> **michaelzap said:**
> Do you see any numbers in my post?

No but amounts, you were sure that it was a significant percentage who have had trouble with PA, and it then was a too bold move to include it with Ubuntu. With no numbers to back that claim up.

So I am just making a just as stupid counterargument by saying for each angry PA hater, there is atleast 1000 who have no troubles with it.*

[SIZE="1"]*I too, have nothing to back this claim with.[/SIZE]

---

### Post by tjwoosta on 2009-07-11
How about we start a new thread with a poll?  That would at least be more accurate then pure speculation.

---

### Post by aysiu on 2009-07-11
> **tjwoosta said:**
> How about we start a new thread with a poll?  That would at least be more accurate then pure speculation.
Here's one, but it's closed:
[Pulse Audio: Is it really successful or a disaster?](http://ubuntuforums.org/showthread.php?t=1058606)

---

### Post by ddrichardson on 2009-07-11
> **tjwoosta said:**
> How about we start a new thread with a poll?  That would at least be more accurate then pure speculation.
Not too sure about that, having spent some time on statistics and variation recently I'm inclined to think a poll is more likely to draw those with strong feelings.  In this case, those who have had problems are more likely to be aware of pulse audio than those that haven't.

Besides, what's the question - is Pulse Audio a good thing or did Ubuntu adopt too early?

---

### Post by michaelzap on 2009-07-11
> **Swarms said:**
> No but amounts, you were sure that it was a significant percentage who have had trouble with PA, and it then was a too bold move to include it with Ubuntu. With no numbers to back that claim up.

So I am just making a just as stupid counterargument by saying for each angry PA hater, there is at least 1000 who have no troubles with it.*

[SIZE="1"]*I too, have nothing to back this claim with.[/SIZE]

"A significant percentage" is not really an amount; it's an opinion. Specifically, mine. Mr. "Less than 1% of Ubuntu users have had problems with PA" is suddenly giving lectures about backing up every opinion with cold hard statistics (even if such stats do not exist either way)?

Please. I've no idea what your point even is. Unless it's "Shut up, you whiners".

I personally don't think a poll would be a very accurate representation of how many users have had problems with PA, and it's very unlikely to affect the developers anyway. They likely already know that there have been problems with PA and are working on resolving them. Personally I wish that PA had been more thoroughly vetted before becoming part of the distro, but I'm sure that over time the kinks will be ironed out.

I hope the same thing doesn't happen with Empathy...

---

### Post by Swarms on 2009-07-11
> **michaelzap said:**
> "A significant percentage" is not really an amount; it's an opinion. Specifically, mine. Mr. "Less than 1% of Ubuntu users have had problems with PA" is suddenly giving lectures about backing up every opinion with cold hard statistics (even if such stats do not exist either way)?

Please. I've no idea what your point even is. Unless it's "Shut up, you whiners".

I personally don't think a poll would be a very accurate representation of how many users have had problems with PA, and it's very unlikely to affect the developers anyway. They likely already know that there have been problems with PA and are working on resolving them. Personally I wish that PA had been more thoroughly vetted before becoming part of the distro, but I'm sure that over time the kinks will be ironed out.

I hope the same thing doesn't happen with Empathy...

I fail to see how that sentence boasts of personal opinion, and it is still an amount...
If you had said, "I believe that many people", or "in my personal experience" etc, then your intentional argument would have been less subtle.

My point is bipartite. Firstly, that I dislike people (on either sides) who are very quick to believe they know what every person believes without having anything valid material to back up their argument.
Secondly, I was pointing out that the vocal minorities often gives a wrong idea of their size and makes people forget they are still a minority. Therefore leading people to using the argument in my first point.

---

### Post by michaelzap on 2009-07-11
> **Swarms said:**
> I fail to see how that sentence boasts of personal opinion, and it is still an amount...
If you had said, "I believe that many people", or "in my personal experience" etc, then your intentional argument would have been less subtle.

My point is bipartite. Firstly, that I dislike people (on either sides) who are very quick to believe they know what every person believes without having anything valid material to back up their argument.
Secondly, I was pointing out that the vocal minorities often gives a wrong idea of their size and makes people forget they are still a minority. Therefore leading people to using the argument in my first point.

:rolleyes: Nah. You just like to argue.

---

### Post by Swarms on 2009-07-11
> **michaelzap said:**
> :rolleyes: Nah. You just like to argue.

That is why we all are here right? :)

---

### Post by racerraul on 2009-07-11
> **frup said:**
> Correct me if I'm wrong, but before Pulse Audio I could only **get one application playing sounds at once**. This meant that if I had rhythmbox open and something in my browser **such as flash** made a sound, one of the two wouldn't work. I have had no problems with sound since PA was introduced.


I have that exact problem with PulseAUdio installed.  Granted it a default install and I didn't go into it to see what needed to be "configured" if it was improperly setup with the Ubuntu install.

Nevertheless... I removed it and all is still the same.  So far I can't tell that there were any gains by running PulseAudio.

---

### Post by tjwoosta on 2009-07-11
> Correct me if I'm wrong, but before Pulse Audio I could only get one application playing sounds at once. This meant that if I had rhythmbox open and something in my browser such as flash made a sound, one of the two wouldn't work. I have had no problems with sound since PA was introduced.

You used to have to enable dmix to play sounds from two apps at once with alsa, but thats no longer the case. With alsa 1.0.9rc2 and up dmix is enabled by default for cards that dont support hardware mixing.

---

### Post by buzzmandt on 2009-07-11
for me testing karmic and very recent pulseaudio, it's the first time i've ever actually been able to use teamspeak linux client and any other sound using application at the same time, even with alsa-oss attempts it wouldn't work.  I LOVE pulseaudio and the direction it's taking us.  Sometimes the more difficult path is the better one to take.

---

### Post by sdowney717 on 2009-07-11
pulse with intrepid gave me silent movies.
pulse with jaunty gives me good sound. It never goes out, not even once. With Intrepid it was always going silent.
I was going to ignore jaunty release but I had to get the the sound fixed.

---

### Post by izizzle on 2009-07-11
I completely removed Pulse from my KDE system. Not only was it useless, but it was causing ALSA to only give sound from 2 of my 5 speakers.

---

### Post by init1 on 2009-07-11
> **frup said:**
> Correct me if I'm wrong, but before Pulse Audio I could only get one application playing sounds at once. This meant that if I had rhythmbox open and something in my browser such as flash made a sound, one of the two wouldn't work. I have had no problems with sound since PA was introduced.

If people are having problems now, if the case is the same as NM, then in a short time things will be better than they ever were before.
Still happens with me when I'm using audacity. If any application that makes a sound is running, audacity won't work.

---

### Post by picpak on 2009-07-11
> **init1 said:**
> Still happens with me when I'm using audacity. If any application that makes a sound is running, audacity won't work.

Go to Edit > Preferences, and under "Playback" and "Recording", change the Devices to "ALSA: pulse". Now Audacity should work. :)

---

### Post by racerraul on 2009-07-11
> **tjwoosta said:**
> You used to have to enable dmix to play sounds from two apps at once with alsa, but thats no longer the case. With alsa 1.0.9rc2 and up dmix is enabled by default for cards that dont support hardware mixing.

I am running 1.0.17... can only have one audio source at a time... if I have anything running and start a flash movie without closing the other app using sound... alsa gets hosed I have to force a restart of alsa...

how do I enable dmix?

---

### Post by PurposeOfReason on 2009-07-12
> **racerraul said:**
> I am running 1.0.17... can only have one audio source at a time... if I have anything running and start a flash movie without closing the other app using sound... alsa gets hosed I have to force a restart of alsa...

how do I enable dmix?
Google.
[http://alsa.opensrc.org/index.php/Dmix](http://alsa.opensrc.org/index.php/Dmix)
They say this will hurt sound quality, but not all that much. I never really notice it at least unless I sit and try.

---

### Post by ddrichardson on 2009-07-12
> **buzzmandt said:**
> Sometimes the more difficult path is the better one to take.
In the long term but the difficult path also needs more preperation, it mightn't be wise to just head off down their and run into problems that could've been avoided.

---

### Post by Icehuck on 2009-07-12
> **ddrichardson said:**
> In the long term but the difficult path also needs more preperation, it mightn't be wise to just head off down their and run into problems that could've been avoided.


What was the point of the difficult path again? Why couldn't you just add the missing "features" to OSS or ALSA?  Why do you need to have three different ways to handle sound?

---

### Post by MasterNetra on 2009-07-12
I've had no Issue with Pulse Audio. Its simply another alternative, just like Ubuntu is simply another alternative to Windows. (A better one of course, but one none the less.) If it indeed does expose bugs in wireless and other things then even better.

---

### Post by ddrichardson on 2009-07-12
> **Icehuck said:**
> What was the point of the difficult path again? Why couldn't you just add the missing "features" to OSS or ALSA?  Why do you need to have three different ways to handle sound?
[http://is.gd/1uCaQ](http://is.gd/1uCaQ)

---

