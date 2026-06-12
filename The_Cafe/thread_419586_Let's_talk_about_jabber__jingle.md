---
title: "Let's talk about jabber / jingle"
date: 2007-04-23
forum: The Cafe
---

### Post by Helmi on 2007-04-23
Hi,

i thought talking a bit about jabber and especially the jingle / jingle audio extension to the xmpp protocol would be a good idea.

Does anyone already have a stable jingle-setup running under ubuntu and doing regular calls to other jabber/jingle users (especiall gtalk).

I think jabber is one of the greatest stuff in open source world and definitely should get more attention. As for now attention is growing - thanks to google (gtalk), imified.com and other services utilizing jabber more an more and bringing it to a big community - but in my eyes it's still and underdog regarding software clients. Unfortunately i'm not a coder so my possibilities to actively support development are kinda limited.

What do you think is the reason projects like gaim, psi (with very limited jingle approaches yet) or jabbin are so stuck or slow in development? Is Jabber not widespreaded enough yet? Do we probably have to do some more community marketing for jabber to make it more popular and attract more developers this way? 

i think it's time to end the era of propietary messaging ;)

---

### Post by fsf@rula on 2007-04-24
I am definitely with you on this one! There is no jingle-enabled jabber program right now in Ubuntu Feisty, not sure about Kubuntu.
I am very sad about this too, as all of my family would joyfully move away from skype as soon as a non-proprietary software has voip capabilities. They already use jabber for text communication, voip through juingle would be a great addition!

---

### Post by Helmi on 2007-04-24
wow - one reply only. Probably this is the reason for the lag of jabbin capable clients: There's just no interest in it. :(

@fsf: thanks for your opinion.

---

### Post by Bloodfen Razormaw on 2007-04-24
I use Jabber almost exclusively.  Kopete supports jingle, but I never use it myself and I don't believe Debian compiles in support for it anyway.

---

### Post by Noah0504 on 2007-04-24
I decided to make the switch to Jabber a few weeks ago.  I knew it would be impossible to get any of my friends to make the switch also, but there aren't too many that I IM with anyway.

Now that I have made the switch, I have almost no one to talk to, haha.  But, I'm becoming stubborn in supporting proprietary software or services.  Open source for the win!  :)

---

### Post by Bloodfen Razormaw on 2007-04-24
Why impossible?  I got nearly everyone I talk to switch to Jabber.  I only have 1 holdout.

---

### Post by Noah0504 on 2007-04-24
> **Bloodfen Razormaw said:**
> Why impossible?  I got nearly everyone I talk to switch to Jabber.  I only have 1 holdout.
My friends see no point in it.  They don't understand the concept of open source, and if it's not "popular," it's pointless.

I'll keep working on them, but I don't think it will do much good.  I suppose I'll just try to make new contacts from around the forum and the IRC channels.

---

### Post by Helmi on 2007-04-24
I got a OpenFire setup running for a few days now with icq, msn, yahoo und aim transports. i'll give it some more testing and offer accounts to friends then. I think i'll get some of them with the transports, MUC (Multi User Chat) and hopefully good jingle-compatible clients soon.

---

### Post by rocknrolf77 on 2007-04-25
I use jabber but I only converted one person. Never heard about jingle, but it sounds like a good thing. People are to hooked om the msn protocol. Can't understand how they can trust sending all that information through the msn system. I sure as h*** don't

Edit : And I can't understand how they can use the msn live messenger, it's just full of commercials.

---

### Post by jfif on 2007-04-25
> **Helmi said:**
> wow - one reply only. Probably this is the reason for the lag of jabbin capable clients: There's just no interest in it. :(

@fsf: thanks for your opinion.

I'm definitely interested in it, especially for voice chat with GoogleTalk. I actually installed Jabbin on Edgy.  But it keeps silent.  How can I make the voice work?

---

### Post by Helmi on 2007-04-26
i also didn't have success with jabbin so far. It seems like it doesn't use ALSA for the sounds. Jabbin unfortunately is also kinda stuck in development.

---

### Post by fsf@rula on 2007-04-26
jabbin is just the psi client rebranded and compiled with voips (jingle) support, which psi has also. It's in beta version and the psi voip-enabled version isn't bugless either yet. I think currently the best-bet is the telepathy framework and tapiocaUI, which has support for jingle, but this is not compiled into the feisty version. We should make an ubuntu-voip repository or something, because jingle is really important! let's strike skype's rule, how can they make so much money with such crappy software and no linux support?!

---

### Post by Arkeos on 2007-04-27
There is a telepathy client with voip which looks pretty good, that's Colligo :

[http://codeposts.blogspot.com/2007/04/colligo.html](http://codeposts.blogspot.com/2007/04/colligo.html)
[http://codeposts.blogspot.com/2007/04/little-teaser.html](http://codeposts.blogspot.com/2007/04/little-teaser.html)
[http://codeposts.blogspot.com/2007/04/emoticons-are-coming.html](http://codeposts.blogspot.com/2007/04/emoticons-are-coming.html)
[http://codeposts.blogspot.com/2007/04/unfortunately-no-release-today.html](http://codeposts.blogspot.com/2007/04/unfortunately-no-release-today.html)

No release yet, but really soon it seems :)

**edit :** webcam support is planned :D

--
nb : non-native english speaker, please don't bit me ;)

---

### Post by fsf@rula on 2007-06-02
I managed to compile psi with jingle support.
I have made a .deb package, but I'm not really sure it works with gtalk yet, I need to test it.
I'm not sure about the dependencies. I'm pretty sure the deps are so:
* libqt4
* speex
* liblinphone1
* libortp0

, but if anyone could support this (or add to the deps), I can add the deps to the package.
The package can be found here: [ http://sjan.web.elte.hu/foss/psi_20070602-1_i386.deb ]( http://sjan.web.elte.hu/foss/psi_20070602-1_i386.deb ) , it was compiled on gutsy, but it's worth a try on feisty too.

Cheers!

ps. I hope it works, I have been trying to get a jingle client on ubuntu for a really long time.

---

### Post by fsf@rula on 2007-06-02
well, it seems I can't speak with gtalk users (client, not flash). pity, I'll check what could've gone wrong

---

### Post by aum11 on 2007-06-25
I am also really interested in this.  Any luck with the testing?

---

### Post by Saoshyant on 2007-07-10
This is actually a Ubuntu-marketing problem, since the developer team does not feel the need to promote the use of Jabber.

The first thing you get when you install Windows is a suggestion to register for MSN for e-mail and IM.  Then on Ubuntu you get nothing.

I think it's time to prove the developers that this is needed.  Our communications are if not more important than free software an equally important concern.  We should not be locked to proprietary IM schemes like AIM, Yahoo!, and MSN.  Or Skype, regarding VoIP.[/email]

---

### Post by Helmi on 2007-08-17
Thought i shouls step by again and watch the thread what's going on. Probably the lack in good jabber tools (with jingle audio/video) is just because nobody is interested in independent IM with VoIP Support?

Look at the problem skype has this day - it's a good example of what happens to propietary protocols and services and how dependent a lot of us already are.

Anyway, i still hope to see good telephony-support via jabber in ubuntu soon. though it's not primarly a problem of the ubuntu guys they surely would have the power to increase marketing relevance for jabber.

Come on guys ;)

---

### Post by ramkumail on 2007-11-05
Hi,
 I have tried psi-jingle from the above mentioned post, and as he says, it dint work with google talk. I have also tried jabbin. even that dint work for me.(even by starting 'aoss jabbin') though some have had success in making it work. i am really vexed and now it sees the only available options are tapioca and gizmo project. i cannot find a deb package for tapioca and the the  instructions from the site dint work for me. i will try gizmo project or else will think of switching to skype. can any one tell me when will jabbin be out of beta version?:(

---

### Post by Helmi on 2007-11-05
sound stupid but i don't gess jabbin will ever get out of beta - it doesn't even really move. I recently stepped through the devel-stuff in pidgin at it looks like jingle audio will get on the plan soon - in the meanwhile i already use skype even if i don't like it :(

---

### Post by der_vegi on 2008-01-07
Yeah, I am also desperately waiting for Gajim or Pidgin to implement jingle. Maybe then I can make some more friends switch to Jabber. *g

In the meanwhile, Wengophone seems to be a good alternative to crappy Skype, you can also call phones and it is even cheaper. I had problems to get the versions in Feisty and Gutsy working, but in Hardy alpha 2, it runs, even behind the proxy of my network. :)

---

