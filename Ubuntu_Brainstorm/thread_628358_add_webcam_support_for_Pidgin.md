---
title: "add webcam support for Pidgin"
date: 2007-12-01
forum: Ubuntu Brainstorm
---

### Post by Mr.mouse on 2007-12-01
Pidgin developers don't want to develop a Voice/video support, 
this is starting to be Ubuntu users problem so perhaps ubuntu develop this feature (anyway this needed for 8.04) 

more on this
[http://developer.pidgin.im/ticket/34](http://developer.pidgin.im/ticket/34)

---

### Post by smartboyathome on 2007-12-01
It isn't Ubuntu's problem, it is Pidgin's. If Pidgin doesn't want to develop it even though several users have asked for it, it shouldn't be put on Ubuntu's shoulders (after all, the Ubuntu devs develop a lot of stuff for Ubuntu and may not have time).

---

### Post by kelbizzle on 2007-12-01
It would be nice. Although there's far more common hardware that ubuntu should be looking to get working. It's not really ubuntu's problem But it'll all happen in due time. Ubuntu has come a super long way since the beginning. We should be grateful for that :-D. With the [Hardware partrner track]("http://www.ubuntu.com/partners/IHV") and ISV we will see more hardware and software come into to play. Skype does have some sort of webcam support maybe that could work for now.

---

### Post by foerdi on 2007-12-01
Ubuntueros doesn't develop much stuff...

The most stuff is done in KDE and GNOME

And I think, somewhere in the GNOME Site there was mentioned something about future A/V support (one library for all apps)

---

### Post by RAOF on 2007-12-02
> **foerdi said:**
> ...
And I think, somewhere in the GNOME Site there was mentioned something about future A/V support (one library for all apps)

You'd be thinking of Telepathy, the freedesktop.org instant-messaging/irc/presence/VoIP framework, and Empathy, the Gnome Telepathy client.

Currently the voice & video code for Empathy isn't enabled in Ubuntu because it doesn't work properly yet.  There's a proposal for Empathy to become an official part of the Gnome desktop, but I haven't really been following the progress of that.

---

### Post by Auria on 2007-12-02
There is work in progress:

(this is Adium, wich is approximately pidgin for mac. but anyway changes they do will also end up in pidgin)
[http://www.adiumx.com/blog/2007/10/happy-leopard-day.php](http://www.adiumx.com/blog/2007/10/happy-leopard-day.php)

> 
Sean Egan and the rest of the Pidgin team are working closely with us on integrating AV capabilities into Libpurple itself. These new functionalities are being developed in a new branch of Pidgin, and development will continue as we improve our support for AV-capable protocols. So far, GTalk receiving audio has been implemented into the Pidgin voice and video branch


> 
These changes will anchor a large amount of new technology being implemented. The entire team is looking forward to this monumental push forward for Adium, Pidgin, and all projects that use Libpurple.


---

### Post by puccaso on 2007-12-02
a few users?

how about every single pidgin/msn user?
thats about what, a few million?

---

### Post by moe_syzlak on 2007-12-09
i have visited the pidgin developers chat about video and voice chat in pidgin

all the devs over there are basically moaning, groaning, and whining: they don't want to do it. because it is too much work.

the libpurple devs are lazy. some are willing but dont know where to start

other libpurple developers are just being pessimistic and b!tching. how long do they think that Linux, *BSDs, and people who use pidgin are going to do without video/voice chat?

SUMMARY: they won't do it because they are not getting paid to do all that work and are being pussyfoot

---

### Post by qamelian on 2007-12-09
> **puccaso said:**
> a few users?

how about every single pidgin/msn user?
thats about what, a few million?
You're over-estimating. Out of 41 people on my MSN buddy list, only one uses a webcam and none use voise chat. Out of over 100 people on all my buddy lists combined from 4 different IM protocols, a total of 4 use webcams and only 2 use voice chat.

---

### Post by foerdi on 2007-12-10
Empathy (/Telepathy) looks nice

---

### Post by RAOF on 2007-12-11
> **moe_syzlak said:**
> i have visited the pidgin developers chat about video and voice chat in pidgin

all the devs over there are basically moaning, groaning, and whining: they don't want to do it. because it is too much work.

the libpurple devs are lazy. some are willing but dont know where to start
...

It's worth noting that posts like this, if read by a pidgin dev, are likely to slightly **reduce** the chances that voice/video get implemented.  Like most of the Ubuntu devs, most of the Pidgin devs are volunteers, and will hence work on what they want or believe to be important and achievable.  Calling a volunteer 'lazy' and 'whining' is likely to demotivate them, either consciously or otherwise.

This isn't really a problem of expectations.  You're welcome to expect Pidgin to do voice/video, and from the meta-bug on the Pidgin bug tracker it's obvious that the pidgin devs expect pidgin to do vv.  Someday.  Which is the problem - you'd like it done soon.  So, if you don't want to implement this yourself (and obviously no one does, currently), you need to motivate someone else to do this.  In the absence of monetary incentive, you need to make people feel good about working on it.  Your post (and the many posts like it - see the bug itself) are actually *hindering* your goal by associating this feature with a bunch of negative feeling and frustration.

With software you pay for (either directly or otherwise) this isn't as much of an issue, and making this sort of noise can sometimes help.  Things work differently with volunteers, and you have to adjust your approach accordingly.

> **moe_syzlak said:**
> 
...
other libpurple developers are just being pessimistic and b!tching. how long do they think that Linux, *BSDs, and people who use pidgin are going to do without video/voice chat?

SUMMARY: they won't do it because they are not getting paid to do all that work and are being pussyfoot

They probably think that people who use pidgin are going to be without video/voice until someone wants it enough to implement it.  You *can* be that person, if you want to be, but you probably don't want to invest the time and effort required.  This doesn't make you lazy, or pussyfoot, but neither does it make the pidgin devs lazy or pussyfoot.

---

### Post by tact on 2007-12-11
> **moe_syzlak said:**
> i have visited the pidgin developers chat about video and voice chat in pidgin

all the devs over there are basically moaning, groaning, and whining: they don't want to do it. because it is too much work.

...and the problem with that is?
(I personally do not see any problem if someone does not have the same enthusiasm for something I am enthusiastic about.  Nor do I have a problem when people do a lot that benefits me (pidgin) out of enthusiasm and the goodness of their hearts, for free  - then stop when they feel like it)
> **moe_syzlak said:**
> 
the libpurple devs are lazy. some are willing but dont know where to start

... Lazy?  I thought lazy was a term reserved for people who know they SHOULD be doing something and fail to do it. (eg work, exercise).

Last I checked there was no-one on the whyteboard with a mandatory task or obligation to mankind, to you, or to me, to add some feature to some free software.
> **moe_syzlak said:**
> 
other libpurple developers are just being pessimistic and b!tching. how long do they think that Linux, *BSDs, and people who use pidgin are going to do without video/voice chat?

Yes!  We will not endure this foul treatment much longer..  if "they" don't do something soon we will all go and....   (ummm... what?  what will we all go and do?)...  I know...  we will all go out and...  err..  no.  That won't work.

Lets stamp our feet!!!  Yes - with viciously pouty lips thrown in for good measure!  So watch out you dirty lazy devs....  

*chuckle*  Joker.

---

### Post by Mr.mouse on 2007-12-11
RAOF,

is that possible to use (as plug)  the amsn webcam library to Pidgin ?

so Ubuntu will have some solution for that problem (Better then nothing)

---

### Post by chips24 on 2007-12-11
use ekiga

---

### Post by foerdi on 2007-12-11
> **Mr.mouse said:**
> RAOF,

is that possible to use (as plug)  the amsn webcam library to Pidgin ?

so Ubuntu will have some solution for that problem (Better then nothing)

i asked the aMSN guys for uniting with pidgin :)
first, they laughed a lot ;)

second, aMSN and pidgin are programmed different
third, aMSN guys say that everything (Webcam-Support) is there pidgin guys should just come and take it

look in the aMSN forums

---

### Post by qamelian on 2007-12-11
> **foerdi said:**
> i asked the aMSN guys for uniting with pidgin :)
first, they laughed a lot ;)

second, aMSN and pidgin are programmed different
third, aMSN guys say that everything (Webcam-Support) is there pidgin guys should just come and take it

look in the aMSN forums

Unless aMSN has suddenly developed the ability to use protocols other than MSN, it is useless to me. Although about 40% of the folks on my buddy list use MSN, the other 60% are split up amongst Yahoo, Jabber, AIM and ICQ. Pidgin is really one of only a very few options if I want to stick to one client app instead of several simultaneously. It doesn't matter to me though that it doesn't do voice and video chat because I have no interest or desire to use either and neither do most of the more than 100 people on my combined buddy lists. It's just not a compelling feature to me or most of the people I chat with.

---

### Post by Auria on 2007-12-11
Didn't anyone read my post? :confused:

Video is currently being added to libpurple by the Adium team... So why complain so much? it's coming :) just let them enough time

---

### Post by yelo3 on 2007-12-13
Pidgin is not only missing video and audio... But also the ability to support (send and receive) offline messages, so that you can communicate even with apparetly offline users (invisible users)!
These are the most important things that an IM client must have.

---

### Post by Mr.mouse on 2007-12-13
it's look like there is a solution, not perfect but good enough for the time being 
[http://adiumxtras.com/index.php?a=xtras&xtra_id=4959](http://adiumxtras.com/index.php?a=xtras&xtra_id=4959)

the question is, will the ubuntu developers add this plug to Pidgin ui ?

---

### Post by Auria on 2007-12-13
> **Mr.mouse said:**
> it's look like there is a solution, not perfect but good enough for the time being 
[http://adiumxtras.com/index.php?a=xtras&xtra_id=4959](http://adiumxtras.com/index.php?a=xtras&xtra_id=4959)

the question is, will the ubuntu developers add this plug to Pidgin ui ?

This "plug-in" just opens the website [http://www.mebeam.com/](http://www.mebeam.com/)... just bookmark the website it will do the same ;) an real implementation of a/v is still to come

---

### Post by qamelian on 2007-12-14
> **yelo3 said:**
> Pidgin is not only missing video and audio... But also the ability to support (send and receive) offline messages, so that you can communicate even with apparetly offline users (invisible users)!
These are the most important things that an IM client must have.
Not by a long shot. There is already a way to reach off-line contacts. It's called email. I just don't understand why people insist in bloating IM apps with functionality that has nothing to do with what IMs were originally intended for: convenient, real-time text messaging from your PC. Frankly, If pidgin ever get vioce and video chat, I'll be dropping it in favour  of a more lightweight client at that point.

---

### Post by Gourgi on 2007-12-14
if it's too hard too implement cam support , no problem to me 
i like the pidgin just the way it is , simple - multiple protocol support - lightweighted 
 and i think i'm gonna use it for a looooong looong time :D
pidgin  rocks !!!!!!! 
the best im client around ;)

---

### Post by lunarcloud on 2008-01-02
> **chips24 said:**
> use ekiga


Yea, the problem with that is ekiga scares me trying to set it up. Then you have to type in an url or something to connect to someone else? I just rather use skype for voice/video.

---

### Post by puccaso on 2008-01-02
mmmmmmmmmmm

DIFFICULT HEY?

i bet someone, a while back was saying "ahh, this is too difficul - how can we create a USER INTERFACE THAT IS CONTROLED BY A SERIAL DEVICE.. A RAT? WHAT IS IT A RAT? ITS CALLED A RODENT? OHH A MOUSE"

then im sure somebody also said "WHY DOES ANYONE NEED A GUI ANYWAY, PEOPLE SHOULD JUST LEARN CLI AND USE EMACS AND IRC FOR EVERYTHING"

now, those people were told to shuttup by intelegent people who had forsight and now, the current computer *nix world uses some sort of UI. it might have been difficult, it might have been tedious - but it happened, and we are here not because of it.

so right now - is somebody going to really start to complain about webcam support isnt that important? or that its tooo difficult? 


well?

---

### Post by [h2o] on 2008-01-05
> **puccaso said:**
> so right now - is somebody going to really start to complain about webcam support isnt that important? or that its tooo difficult?
If it was an easy trivial task it would have been done already. Supporting A/V-conversations for multiple protocols is probably not something you do quickly. But please, be my guest and prove me wrong. I would love having the possibility to do video chat in Pidgin.

I agree with the "stop bitching"-statements that others have already stated.
If you are a programmer with some spare time, then fix what you are bitching about. If you are not, then please voice what you think should be done with a program but don't expect people to work for free while you are bossing htem around calling them lazy.

---

### Post by mangar on 2008-01-05
there are three ways to get voice/ video support:

1. use skype
2. hire a developer (~20k$/year at least, almost anywhere in the world)
3. start programming yourself, and see the patches rotting..  the source is open, after all.

here's start:

/***************
* Super ultra cool patch for audio/video support
*
*author: <insert name here>
* license: LGPL
***************/
#include <stdio> 

int main()
{
   printf("this is my awesome void/video plugin!\n");
   return 0;
}

---

### Post by 23meg on 2008-01-05
Did anyone read post #6?  

> **puccaso said:**
> mmmmmmmmmmm

DIFFICULT HEY?

i bet someone, a while back was saying "ahh, this is too difficul - how can we create a USER INTERFACE THAT IS CONTROLED BY A SERIAL DEVICE.. A RAT? WHAT IS IT A RAT? ITS CALLED A RODENT? OHH A MOUSE"

then im sure somebody also said "WHY DOES ANYONE NEED A GUI ANYWAY, PEOPLE SHOULD JUST LEARN CLI AND USE EMACS AND IRC FOR EVERYTHING"

now, those people were told to shuttup by intelegent people who had forsight and now, the current computer *nix world uses some sort of UI. it might have been difficult, it might have been tedious - but it happened, and we are here not because of it.

so right now - is somebody going to really start to complain about webcam support isnt that important? or that its tooo difficult? 


well?

Not a good comparison (read post #6), because you're (read post #17) comparing an unforeseen, completely new paradigm (read post #6) with support for a well known feature (read post #17) in specific apps (read post #6) on a specific platform. 

Everyone knows about audio and video chat (read post #6) , and that some people need those features (read post #6) .

Did you read post #17? 

> **mangar said:**
> there are three ways to get voice/ video support:

1. use skype
2. hire a developer (~20k$/year at least, almost anywhere in the world)
3. start programming yourself, and see the patches rotting..  the source is open, after all.

4. Learn to read, and read post #6, and stop complaining about patches rotting without having done anything to help with the issue. 

From [http://developer.pidgin.im/ticket/34](http://developer.pidgin.im/ticket/34):

> Add voice and video support for all protocols that support it. This WILL happen eventually, but it is a rather large undertaking and very few core developers are interested in working on it.

DO NOT leave a comment here asking us when it will be finished, or asking us to hurry, or telling us why we should spend all our free time working on it.

If you really want to help, have 15 hours a week of free time, have at least five years experienced programming in C and have experience with undocumented network protocols then please email our devel mailing list and ask where you can get started. 

Does this look like a "patches rotting" situation (read post #6)? And how about the quotes in post #6?

---

### Post by avdzm on 2008-03-03
Hey all,

I love pidgin, the fact that i can chat multiple protocols simultaneously.

I don't mind the not having wink support, i've always found them a lil annoying.
The smilies are perfect for me.

It is one of the reason why i use Google Talk more and try convince my friends to use it.(so far only 1 has moved, its a step)

There are 2 things i want to see from pidgin in the near future,
faster transferring of files and
asap the webcam support or at least audio as a beginning.

anyway thank you pidgin developers...

tc all

---

### Post by Triggerhapp on 2008-03-19
Why not try aMsn? that has some very good webcam support, and alot of features that Pidgin doesnt have, I started on pidgin but I found it was "too generic", in my view, Thats not good. I know that alot of people love it for bieng equally good at everything, but I believe pidgin goes against the Linux principle "A program should do one thing, and do it well" It feels to me that Pidgin limits itself in every format, trying to make them equal and leaving the more intimate parts of each format out.
I would advise people who want webcam to just take a quick peek at aMsn, if not, just remove it again after, no damage done/

---

### Post by bruce89 on 2008-03-19
> **Triggerhapp said:**
> Why not try aMsn? that has some very good webcam support, and alot of features that Pidgin doesnt have, I started on pidgin but I found it was "too generic", in my view, Thats not good. I know that alot of people love it for bieng equally good at everything, but I believe pidgin goes against the Linux principle "A program should do one thing, and do it well" It feels to me that Pidgin limits itself in every format, trying to make them equal and leaving the more intimate parts of each format out.
I would advise people who want webcam to just take a quick peek at aMsn, if not, just remove it again after, no damage done/

Its webcam code could be nicked, but AFAIK it's written in tcl.

---

### Post by willskills on 2008-03-19
I use pidgin as an IM client. I use Skype beta 2.0 for voice and video/webcam support, and it works really well.

---

### Post by Triggerhapp on 2008-03-19
> **bruce89 said:**
> Its webcam code could be nicked, but AFAIK it's written in tcl.

It is in tcl, this'll make it difficult to move the webcam code, because im sure pidgin isnt tcl/tk...

Feel free to make your own fork of pidgin, but last I checked, they werent sure HOW they could add webcam support to libpurple, which is format based, and they said it wouldnt be correct to add it outside of the library context (straight into the gui that is)

---

### Post by bruce89 on 2008-03-19
> **Triggerhapp said:**
> It is in tcl, this'll make it difficult to move the webcam code, because im sure pidgin isnt tcl/tk...

Indeed, it's C.

---

### Post by Triggerhapp on 2008-03-19
makes sense, I remember it running quicker on my ancient laptop ;)

---

### Post by hvac3901 on 2008-06-21
> **yelo3 said:**
> Pidgin is not only missing video and audio... But also the ability to support (send and receive) offline messages, so that you can communicate even with apparetly offline users (invisible users)!
These are the most important things that an IM client must have.

Not true, you should enable the Pounce Plug-in.


Your invisible users, are likely displaying themselves as offline, even though they are online, to see them, select "display offline users" or contacts however the word usage goes.

buddies > Show > offline buddies.

---

### Post by yelo3 on 2008-06-21
What's this plugin for? I don't have it installed...

---

### Post by hvac3901 on 2008-06-27
> **yelo3 said:**
> What's this plugin for? I don't have it installed...


offline messages.

---

### Post by yochaigal on 2008-07-10
How come nobody like kopete?  It has full webcam support, plus XMPP, MSN, AIM, etc...

I myself prefer pidgin (stability, GNOME, etc) but if we could port kopete to windows/mac then people would abandon skype (which sucks in linux).

---

### Post by smartboyathome on 2008-07-11
> **yochaigal said:**
> How come nobody like kopete?  It has full webcam support, plus XMPP, MSN, AIM, etc...

I myself prefer pidgin (stability, GNOME, etc) but if we could port kopete to windows/mac then people would abandon skype (which sucks in linux).

Good luck getting Kopete in Ubuntu (being Qt, it doesn't have a very high chance of getting in). If you could get it ported to Windows (a couple years down the road, when KDE is mostly ported to Windows), AND can port it to GTK, then Ubuntu might consider it, but as it stands, it won't.

---

### Post by yochaigal on 2008-07-11
what do you mean? it's in the repositories, and many people use kde libraries in gnome (amarok anyone?) so I don't think that'll be the problem. I also am not saying it should be the default; personally I started using funpidgin ever since they disabled the window resize function.

---

### Post by smartboyathome on 2008-07-11
> **yochaigal said:**
> what do you mean? it's in the repositories, and many people use kde libraries in gnome (amarok anyone?) so I don't think that'll be the problem. I also am not saying it should be the default; personally I started using funpidgin ever since they disabled the window resize function.

I mean that Ubuntu doesn't include anything by default that isn't GTK because, even though a lot of people DO use Amarok on GNOME, the KDE libs take up a lot of space, and they want to keep the cd's size as minimal as possible. I was just thinking if you want to make it popular, then you should make a GTK port so that it can be used with, and enhance the power of, Ubuntu.

---

### Post by jdorenbush on 2008-09-12
I just bought a webcam to use with a couple friends.

I hate that I have to login to my Windows machine and use AIM just to chat with them with video/audio.

I tried...
Ekiga = complicated - This looks the most promising though. As I confirmed my webcam IS working with it. Does anyone know how to setup an AIM account in Ekiga?
Empathy = Even more complicated
Kopete = Bloated and ugly

---

### Post by smartboyathome on 2008-09-12
Have you tried Skype? It is available for Linux and allows video and audio chat over several different networks.

---

### Post by jdorenbush on 2008-09-13
> **smartboyathome said:**
> Have you tried Skype? It is available for Linux and allows video and audio chat over several different networks.

Can you video chat with someone on AIM?

---

### Post by smartboyathome on 2008-09-13
> **jdorenbush said:**
> Can you video chat with someone on AIM?

I don't know, I don't use Skype. :(

---

### Post by Neon Lights on 2008-09-13
> **jdorenbush said:**
> Can you video chat with someone on AIM?
Not with Skype, nope.

Pidgin IS working on implementing Voice/Video now [finally], but it's still got a while to go. Empathy looks like it'll bear fruit sooner than Pidgin at this rate, but who knows?

---

### Post by gnomeuser on 2008-09-13
> **Neon Lights said:**
> Not with Skype, nope.

Pidgin IS working on implementing Voice/Video now [finally], but it's still got a while to go. Empathy looks like it'll bear fruit sooner than Pidgin at this rate, but who knows?

Actually Pidgin are implementing voice/video via telepathy. The same underlying framework as empathy uses. They will gain the underlying technology at the same time, hooking up the gui is pretty quick afterwards.

This was all done as part of GoC2008 so it should hopefully land soon.

---

### Post by jdorenbush on 2008-09-13
> **gnomeuser said:**
> Actually Pidgin are implementing voice/video via telepathy. The same underlying framework as empathy uses. They will gain the underlying technology at the same time, hooking up the gui is pretty quick afterwards.

This was all done as part of GoC2008 so it should hopefully land soon.

Soon as in I should stop screwing around with a bunch of other software? Are we talking the next couple of months?

---

### Post by bruce89 on 2008-09-13
> **jdorenbush said:**
> Soon as in I should stop screwing around with a bunch of other software? Are we talking the next couple of months?

Probably a bit beyond that.

Empathy supports webcams on some protocols (Jabber perhaps), but I've not tried it.

---

