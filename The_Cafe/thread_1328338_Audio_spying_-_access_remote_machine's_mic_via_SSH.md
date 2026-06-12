---
title: "Audio spying - access remote machine's mic via SSH"
date: 2009-11-16
forum: The Cafe
---

### Post by youbuntu on 2009-11-16
Hi guys. I just learnt a clever little trick [SIZE=6][COLOR=Red]*use with caution and respect the privacy of others - using this technique for the wrong reasons, <<could>> see you in legal troubles!*[/COLOR][/SIZE]:

Basically, you are able to open the microphone of a remote GNU/Linux machine, [COLOR=Red]**so long as you have the SSH password for that machine**[/COLOR], and so long as the remote machine has SSH server installed & running.

Here is how I got it to work:

Assume the following; 192.168.1.1 is LOCAL, 192.168.1.2 is REMOTE.

1/ I installed openssh-server & openssh-client on BOTH test machines:

```
sudo aptitude install openssh-server openssh-client
```2/ On the LOCAL (my) machine, I opened terminal and entered:

```
ssh <username>@192.168.1.2 'dd bs=1k if=/dev/audio' > /dev/audio
```Basically, you are concatenating the audio input device (REMOTE) to the audio output device (LOCAL) with a stream block size of 1Kb.

Your sound card may be /dev/audio1 as mine is (it is a USB sound card) so I shall assume you know it is /dev/<yourSoundCardNode>


3/ You *should* now hear every single sound from the microphone on the REMOTE machine!


:p [COLOR=Red]**use responsibly**[/COLOR], and have a lot of fun.

---

### Post by The Funkbomb on 2009-11-16
Is this only if there's no password auth or passkey auth enabled or does it work regardless of these security measures?

---

### Post by youbuntu on 2009-11-16
> **The Funkbomb said:**
> Is this only if there's no password auth or passkey auth enabled or does it work regardless of these security measures?

I can only assume one would need FULL root permissions for the remote machine - I am not enough of a guru to say for sure, though. I used two default Karmic installs, of which I am admin to both.

---

### Post by The Funkbomb on 2009-11-16
So, you picked the lock of an open door?

---

### Post by youbuntu on 2009-11-16
> **The Funkbomb said:**
> So, you picked the lock of an open door?

It's just for *fun* dude, it is not supposed to be breaking into someone's machine LOL.

PS: Picking the lock on an open door would be no less hard; I simply PUSHED the open door! :D

---

### Post by coldReactive on 2009-11-16
> **glossywhite said:**
> it's just for *fun* dude, it is not supposed to be breaking into someone's machine lol.

Ps: Picking the lock on an open door would be no less hard; i simply pushed the open door! :d

del taco!

---

### Post by youbuntu on 2009-11-16
> **coldReactive said:**
> del taco!

???...

---

### Post by kyuubi777 on 2009-11-16
dont be pickin on op... it is always a good thing when people try new things w/ technology... thanks for posting
just make sure there aren't FBI agents behind the doors you open :D

---

### Post by coldReactive on 2009-11-16
> **glossywhite said:**
> ???...

[http://www.homestarrunner.com/sbemail50.html](http://www.homestarrunner.com/sbemail50.html)

---

### Post by youbuntu on 2009-11-16
> **kyuubi777 said:**
> dont be pickin on op... it is always a good thing when people try new things w/ technology... thanks for posting
just make sure there aren't FBI agents behind the doors you open :D

ROFL nooo, just for fun - I really have better things to do :p

---

### Post by earthpigg on 2009-11-16
this could potentially be useful if one had an extra computer laying around, and wanted to use it as a free baby crying monitor.

or perhaps wanted to check up on a babysitter or house sitter one wasnt sure about.

---

### Post by Dragonbite on 2009-11-16
> **earthpigg said:**
> this could potentially be useful if one had an extra computer laying around, and wanted to use it as a free baby crying monitor.

or perhaps wanted to check up on a babysitter or house sitter one wasnt sure about.

Oooohhh!

First, I just thought it was cool.  Now with that babysitter monitor idea this sounds even BETTER!

@glossywhite : thanks for this information! they may close it for security purposes sometime in the future but it's great that somebody is poking around and finding new ways to do things!  Keep up the good (exploratory) work!

---

### Post by youbuntu on 2009-11-16
> **Dragonbite said:**
> Oooohhh!

First, I just thought it was cool.  Now with that babysitter monitor idea this sounds even BETTER!

@glossywhite : thanks for this information! they may close it for security purposes sometime in the future but it's great that somebody is poking around and finding new ways to do things!  Keep up the good (exploratory) work!

"Security reasons"?... I think they'd realise that ANYONE can buy a baby monitor - it is basically the same thing, only better :p.

Knowledge is about freedom and learning - it would kinda be going against that, to close the thread. A knife is only dangerous in a murderer's hands, if he intends to kill - it doesn't stop bread knives being sold :)

Google "audio surveillance equipment" and you'll find a plethora of sources from which to buy bugs, spy cameras etc. I would like to say that ethically, I think it is completely wrong to do ANY sort of spying on ANYONE - the only reason I posted this was because I was so pleased with my experiment, and it was a simple demonstration of routing one node to another, for fun!.  I don't like spying and I certainly don't like the lack of morality which usually determines it's usage - BAD, BAD people have to resort to such things.

---

### Post by Dragonbite on 2009-11-16
I was meaning closing the ability to SSH into audio, not the thread.  If it requires root (sudo) access then chances of this going away is even less I suspect.

---

### Post by Exodist on 2009-11-16
***O dear.. I can picture this happening now while Glossy is at work....***

**Glossy**: Hmm, wonder what the wife and kids are doing at home? Lets ssh and listen.. hehe

**Home**: /strage porno sounds noises in background.. "O Milk Man!!"

**Glossy**:  :confused:

---

### Post by sudoer541 on 2009-11-16
This is ILLEGAL and it compromises user privacy.

---

### Post by schauerlich on 2009-11-16
> **sudoer541 said:**
> This is ILLEGAL and it compromises user privacy.

You have to be given shell access and (probably) root access to do it. root = no expectation of privacy.

---

### Post by FuturePilot on 2009-11-16
> **Dragonbite said:**
> I was meaning closing the ability to SSH into audio, not the thread.  If it requires root (sudo) access then chances of this going away is even less I suspect.

Why would they remove the ability to do something like this? That's kind of the whole point of SSH; to be able to tunnel stuff.

> **sudoer541 said:**
> This is ILLEGAL and it compromises user privacy.

By that definition, so is the root account.

---

### Post by youbuntu on 2009-11-16
> **sudoer541 said:**
> This is ILLEGAL and it compromises user privacy.
Alarmist, much?. Illegal Schmegal... so SSH is illegal, microphones are illegal,  GNU/Linux is illegal, network interfaces are illegal?...

What tripe.

---

### Post by RiceMonster on 2009-11-16
> **glossywhite said:**
> Alarmist, much?. Illegal Schmegal... so SSH is illegal, microphones are illegal,  GNU/Linux is illegal, network interfaces are illegal?...

What tripe.

Legal or not, you're still spying on the person at hand. Whatever though, I guess it depends on how you're doing it. I'll give you the benefit of the doubt in that you did post that warning in the OP.

---

### Post by youbuntu on 2009-11-16
> **RiceMonster said:**
> Legal or not, you're still spying on the person at hand. Whatever though, I guess it depends on how you're doing it.

Noone is spying on ANYONE. It has to be proved that one is using this technique in the context of spying upon someone, to be illegal. Opening the mic via SSH is not illegal, and has other uses apart from the bad ones - if I hand you a box of matches, does that mean you *MUST* commit arson?.

This is a TECHNICAL example - if I want to control my other laptop mic with my computer, I'd like to see you OR ANYONE stop me. LOL. :D

Don't be so ridiculous.

---

### Post by earthpigg on 2009-11-16
how is it illegal or immoral to survey ***ones own residence*** to verify that the babysitter doesn't have his/her girlfriend/boyfriend over, or to verify that the house sitter doesn't have a wild party going on?

---

### Post by wilee-nilee on 2009-11-16
> **sudoer541 said:**
> This is ILLEGAL and it compromises user privacy.

Exactly it is illegal and posting this on a gigantic world wide forum is not good. The OP doesn't know how this will be used by others, now where is that report button.

---

### Post by Exodist on 2009-11-16
> **sudoer541 said:**
> This is ILLEGAL and it compromises user privacy.
LOL what country you in.. 

1) There is NOTHING illegal about monitoring YOUR OWN RESIDENCE.. LMAO!!
People these days have web cams with security codes mounted in their homes and residences so they can watch their children while at work. To listen in on your own residence is your own right.

2) Your not breaking into anything, its your own computer your _LOGING_ into becuase you put your own password in that system. And if you did wish to break into your own system per se. ITS YOUR SYSTEM thus it is not illegal.

---

### Post by earthpigg on 2009-11-16
> **wilee-nilee said:**
> Exactly it is illegal and posting this on a gigantic world wide forum is not good. The OP doesn't know how this will be used by others, now where is that report button.

security by arbitrary forced ignorance?

wow. what a joke this thread is rapidly becoming.

unfortunate, too, as i personally appreciate the OP's post and this thread.

[ SARCASM ]
hey! shhh, i have a secret to tell... ***hammers can bash things!*** dont tell anyone, though, as we have no idea how bad guys will use that knowledge. in fact, please delete this post immediately or we risk bad people bashing things owned by others using a hammer.
[ /SARCASM ]

---

### Post by Giant Speck on 2009-11-16
Show me anywhere in the OP's post where he included code that steals the user's root password in order to obtain access to their computer and then maybe I'll consider it to be *possibly* a violation of the user's privacy.

---

### Post by Exodist on 2009-11-16
> **wilee-nilee said:**
> Exactly it is illegal and posting this on a gigantic world wide forum is not good. The OP doesn't know how this will be used by others, now where is that report button.


The OP didnt post anything Illegal. 

1) He / She OWNs both computers.
2) He / She has admin rights to both computers.
3) He / She posted this about monitors the users Home.

So the OP didnt post anything. He/She just happend to notice that with a GNU/Linux OS you can have more control over the system you are actually logging into. Even the ability to access the multimedia abilities of the machine like the microphone if its plugged in. Which is NORMAL and NOT ILLEGAL..

OMG Wheres the face palm pic for this thread!!!!

[IMG]http://www.heathenz.com/wp-content/uploads/2008/10/picard-no-facepalm.jpg[/IMG]

---

### Post by RiceMonster on 2009-11-16
> **glossywhite said:**
> Noone is spying on ANYONE. It has to be proved that one is using this technique in the context of spying upon someone, to be illegal. Opening the mic via SSH is not illegal, and has other uses apart from the bad ones - if I hand you a box of matches, does that mean you *MUST* commit arson?.

This is a TECHINCAL example - if I want to control my other laptop mic with my computer, I'd like to see you OR ANYONE stop me. LOL. :D

Don't be so ridiculous.

Yes sorry, I didn't really read the OP the first time around, so my apologies.

---

### Post by FuturePilot on 2009-11-16
> **earthpigg said:**
> 

wow. what a joke this thread is rapidly becoming.

unfortunate, too, as i personally appreciate the OP's post and this thread.



this

---

### Post by youbuntu on 2009-11-16
"Illegal"...?

[IMG]http://www.lafferty.ca/wp-content/uploads/2007/05/fail-24.jpg[/IMG]

---

### Post by Dragonbite on 2009-11-16
I guess I better print out the instructions on the first post before this thread gets deleted.

Oh, wait. There's nothing illegal on this and certainly nothing illegal in all of the countries of the world.  Heck, governments would use this if they could (like, if they knew all of our passwords, IP addresses and our firewalls were open to SSH).

How is this any worse than a nanny-cam?  It's actually even less "invasive" because it is audio-only and with no video.

---

### Post by wilee-nilee on 2009-11-16
It is the possibility of miss use that a rational person realizes why this should not be on a forum. Yes all of you who question this probably would not break the law, probably, but what is basically wiretapping needs a court order. This is a contextual use consideration, Yes you can monitor your own home or business, but observing others without a court order is illegal in America. I am not sure the nanny cam is legal without telling the nanny you have the ability to monitor, please read I am not sure twice.

---

### Post by earthpigg on 2009-11-16
wilee-nilee:

see my above comments about the hammer. you could make your exact same case using a hammer instead of SSH.

> observing others without a court order is illegal in America.

I suppose everyone that has security video cameras set up around their home needs to be immediately arrested, then. I suggest you alert the media to your profound legal discovery.

All of your statements in this thread are complete and utter rubbish, friend.

The only question I have is this: are you a troll, or do you honestly believe what you are saying?

I see no reason to hold anything against you if the latter is the case, but I am beginning to suspect that the former is the case.

---

### Post by Icehuck on 2009-11-16
> **wilee-nilee said:**
>  observing others without a court order is illegal in America. 

No one here is advocating creating wire taps, breaking into someones home, or cracking someones root account password. These are all felonies of various degrees. Simply monitoring your own home is not illegal and well within your rights.

---

### Post by wilee-nilee on 2009-11-16
> **earthpigg said:**
> wilee-nilee:

see my above comments about the hammer. you could make your exact same case using a hammer instead of SSH.



I suppose everyone that has security video cameras set up around their home needs to be immediately arrested, then. I suggest you alert the media to your profound legal discovery.

All of your statements in this thread are complete and utter rubbish, friend.

The only question I have is this: are you a troll, or do you honestly believe what you are saying?

I see no reason to hold anything against you if the latter is the case, but I am beginning to suspect that the former is the case.

Your reading into my posts, and insinuating I am a troll is  a hierarchal methodology for a I am better then you Look at my post count look at the help I have given others. Labeling does not help it separates. Socially accepted norms are not always found to be accurate or a positive way to communicate, for example when America was fonded the native population was considered as savages, when in actuality they had a fully formed culture that has been dated back at least 10,000 years, it just wasn't the European model. Thinking in a more abstract way will set you free.;) 

If you are in a public place and there is a way of recording activities there has to be a sign stating you may be being observed, also read the use context. 

It is the possibilities of misuse that makes this problematic. Even if you own the computers, this doesn't give you the right to spy yes it is in the thread title.

Before you just respond with a rubbish statement you may want to look at the laws on this sort of thing.

In the end the OP is just so proud of his little script that the ego needs fulfillment by bragging about it, without considering the ramifications of the possibilities.

This will be my last post and I will turn off the auto notification to this thread I don't want to get any further argumentative interactions, I love you all in a humanistic broad sense. ;)

---

### Post by Luke has no name on 2009-11-16
I find it funny so many people are attacking the OP for posting this, as it could possibly be used for spying purposes. It's a tech demo, people.

**I take college courses that teach us things like this, how to perform passive man-in-middle attacks, intrusion detection, network scanning, keylogging, password cracking, and on and on...**

People who want to know how to do this stuff can already do it. It's up to good people to use the knowledge so they can protect against it.

---

### Post by coldReactive on 2009-11-16
> **Luke has no name said:**
> People who want to know how to do this stuff can already do it. It's up to good people to use the knowledge so they can protect against it.

I've been taught the knowledge about how they do it, but I don't know how to prtect myself from it.

---

### Post by Exodist on 2009-11-16
> **coldReactive said:**
> I've been taught the knowledge about how they do it, but I don't know how to prtect myself from it.
Dont hand out your Root password.. thats it..

---

### Post by coldReactive on 2009-11-16
> **Exodist said:**
> Dont hand out your Root password.. thats it..

If that's the only thing we linux people have to do, I'm glad I use linux. My grandma will probably be using linux in a while, once I move out. I explained to her why I use linux, and needless to say, she was intregued.

---

### Post by Dragonbite on 2009-11-16
It is just another means similar to a webcam (if the monitor is turned off, how do you know your webcam is not running?) and is limited to the same laws and limitations.

Different tool, existing purpose, same legal protection.

For example, a home is not a public place, and you are allowed certain privileges as the "resident". That doesn't mean the landlord can use this on tenants any more than he (she) can sneak video cameras.

I do not recall every building with cameras that I've gone into having signs that say "you are under surveillance". Some of the more public ones, yes.

Again, different tool, same purpose, same legal protection.

---

### Post by coldReactive on 2009-11-16
Nope, my grandma won't go to linux, for fear of her computer breaking.

I fail at converting people, :( I wish they would convert, I'm sad whenever I see windows.

---

### Post by Giant Speck on 2009-11-16
> **coldReactive said:**
> Nope, my grandma won't go to linux, for fear of her computer breaking.

Why would your grandmother want to go to a kernel?  ;)

---

### Post by t0p on 2009-11-16
> **wilee-nilee said:**
> If you are in a public place and there is a way of recording activities there has to be a sign stating you may be being observed, also read the use context. 

But this isn't about public places.  It's about a computer you own (or at least own root on) so presumably in your own home.  Anyway, I doubt this law you mention actually exists.  And I *know* it doesn't exist in the UK.  

> **wilee-nilee said:**
> 
It is the possibilities of misuse that makes this problematic. Even if you own the computers, this doesn't give you the right to spy yes it is in the thread title.

What "misuse"?  Someone mentioned using this as a "nannycam"; so such use is *not* misuse, it's being used the way it was intended to be used.

> **wilee-nilee said:**
> 
Before you just respond with a rubbish statement you may want to look at the laws on this sort of thing.

No, I think it's *you* who ought to quote the laws you are referring to.  Though of course you won't.  Because you *can't*.


> **wilee-nilee said:**
> In the end the OP is just so proud of his little script that the ego needs fulfillment by bragging about it, without considering the ramifications of the possibilities.

Ooh, is that jealousy I can smell?

> **wilee-nilee said:**
> 
This will be my last post and I will turn off the auto notification to this thread I don't want to get any further argumentative interactions, I love you all in a humanistic broad sense. ;)

If you stop replying in this post, it's because you know that your claims are false and you don't want to have to try to justify your nonsense.  If you had anything about you, you'd respond to this with evidence of your imagined "laws".  But you won't.

But even if US law were as you describe: so what?  There's nothing illegal in the UK about what's been described.  So it's okay for Brits to read about it, but not for US citizens?  Ridiculous.

> **Dragonbite said:**
> How is this any worse than a nanny-cam? It's actually even less "invasive" because it is audio-only and with no video.

I'm sure this trick would work with a webcam too.  But that's not "invasive" either, because you have the *right* to look at your own property. (I know you're not claiming that it's somehow "wrong".  I'm just making the point.)

Lots of people have cameras that can be accessed through the world wide web, precisely so they can monitor their property remotely.  And there are lots of publicly-accessible webcams that are set up just for amusement.

Anyway, this is interesting because it means *any* device can be accessed remotely.

---

### Post by earthpigg on 2009-11-16
> **coldReactive said:**
> Nope, my grandma won't go to linux, for fear of her computer breaking.

I fail at converting people, :( I wish they would convert, I'm sad whenever I see windows.

this thread is about SSH... learn to use SSH and the command line, and you can remotely administer your grandmothers computer and fix anything that breaks, thus potentially alleviating her concern. :D

with her permission, of course. with my own mother and this setup, the first thing i taught her was how to manage users and groups (system -> admin -> users and groups) and thus remove my ability to remotely access her computer if she ever decides to.

```
[chris: ~]$ uname -a
Linux ***_chris-desktop_*** 2.6.31-ARCH #1 SMP PREEMPT Tue Nov 10 19:01:40 CET 2009 x86_64 Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz GenuineIntel GNU/Linux
[chris: ~]$ callmom
Connecting...
earthpigg@-removed-.-removed-.net's password: 
[earthpigg@mom-desktop ~]$ uname -a
Linux ***_mom-desktop_*** 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
[earthpigg@mom-desktop ~]$ 
```

i also taught her how to check if anyone besides her was logged into her computer:

```
[earthpigg@mom-desktop ~]$ users
earthpigg mom
[earthpigg@mom-desktop ~]$ 
```


in ***that*** particular case, it would indeed be illegal and immoral to listen in on the mic (or do anything else involving her computer) without her permission. on the other hand: if she where away from home, got a phone call from the neighbor that there may be something funny going on at her home, and then called me and ***asked me*** to listen in using methods the OP described.... that would be perfectly legal and moral.

she chose to trust me, and i taught her how to remove my ability to remotely log into her computer if she ever changes her mind.

---

### Post by wilee-nilee on 2009-11-16
> **t0p said:**
> But this isn't about public places.  It's about a computer you own (or at least own root on) so presumably in your own home.  Anyway, I doubt this law you mention actually exists.  And I *know* it doesn't exist in the UK.  



What "misuse"?  Someone mentioned using this as a "nannycam"; so such use is *not* misuse, it's being used the way it was intended to be used.



No, I think it's *you* who ought to quote the laws you are referring to.  Though of course you won't.  Because you *can't*.




Ooh, is that jealousy I can smell?



If you stop replying in this post, it's because you know that your claims are false and you don't want to have to try to justify your nonsense.  If you had anything about you, you'd respond to this with evidence of your imagined "laws".  But you won't.

But even if US law were as you describe: so what?  There's nothing illegal in the UK about what's been described.  So it's okay for Brits to read about it, but not for US citizens?  Ridiculous.



I'm sure this trick would work with a webcam too.  But that's not "invasive" either, because you have the *right* to look at your own property. (I know you're not claiming that it's somehow "wrong".  I'm just making the point.)

Lots of people have cameras that can be accessed through the world wide web, precisely so they can monitor their property remotely.  And there are lots of publicly-accessible webcams that are set up just for amusement.

Anyway, this is interesting because it means *any* device can be accessed remotely.

Nice display of thinking with dichotomies, oops now I have posted again; your bait worked you can be proud of yourself. ;) It is not a binomial world. Coming to conclusions as to why I do or what I don't do is a projection.

I have full access to world wide data bases via my college enrollment If I even cared about this other then a cursory set of comments I would be glad to find the laws and post them, can you prove I am wrong? or is it just a natural response to argue. Your information is no more valid in it's presentation then mine. we all know the laws in whatever country we live in, at least in a broader sense.

I think we need to look at the larger picture, If you take a course in computer sciences or whatever there called you will practice hacking and cracking..etc. This is in a completely different setting. So lets say a jealous partner wants to spy on their partner and something negative happens because of this ability to remote spy. There are numerous reasons why this is not a good idea being posted on a forum.

Jealous; I have never wanted to write a script it is psychological observation and the OP himself says he was so proud of it, This is some basic stuff, what is the motivation for posting this, especially when as another poster says you would learn this in a computer science course.

I would be glad to give a more analytical observation of your motivations but I think I have said enough and I suspect you don't understand anyway, or are stuck in your black and white thinking process. Just a observation man. ;)

---

### Post by earthpigg on 2009-11-16
> So lets say a jealous partner wants to spy on their partner and something negative happens because of this ability to remote spy.

well, if you are aware of this happening then please go ahead and call the police.

> There are numerous reasons why this is not a good idea being posted on a forum.

and you haven't posted any, except that you think it's better for only computer science majors to be able to do clever things with their computers.

---

### Post by t0p on 2009-11-16
> **wilee-nilee said:**
> Nice display of thinking with dichotomies, oops now I have posted again; your bait worked you can be proud of yourself. ;) It is not a binomial world. Coming to conclusions as to why I do or what I don't do is a projection.

It was an assumption.  And a pretty good one, judging from your reply.  And yes, I was goading you to reply.  Because I want you to back up your assertions with evidence.  Not your opinions: your *assertions*.  And I still want you to do so.  Please.

> **wilee-nilee said:**
> 
I have full access to world wide data bases via my college enrollment If I even cared about this other then a cursory set of comments I would be glad to find the laws and post them, can you prove I am wrong? or is it just a natural response to argue. Your information is no more valid in it's presentation then mine. we all know the laws in whatever country we live in, at least in a broader sense.

Regardless of whether you're right about US law prohibiting unannounced surveillance in public places, you haven't addressed the fact that one's own home is not a public place.  You also haven't addressed my point about the internet being an international medium.  Then there is your implication that information is somehow "wrong".  That it's bad to know how to do things.  

> **wilee-nilee said:**
> 
I think we need to look at the larger picture, If you take a course in computer sciences or whatever there called you will practice hacking and cracking..etc. This is in a completely different setting. So lets say a jealous partner wants to spy on their partner and something negative happens because of this ability to remote spy. There are numerous reasons why this is not a good idea being posted on a forum.

So now you change focus from legalities to moralities.  Okay, I'll bite.  Let's say you don't trust your partner, so you follow her in your car.  You catch her cheating on you, and shoot her with a gun.  So it is wrong for someone to teach you how to drive or to shoot.

No doubt you'll accuse me of reductio ad absurdum.  That would be inaccurate.  Driving, shooting, and remotely accessing your own computer's microphone are all legal activities with perfectly innocent applications.  If someone chooses to use such a skill for evil ends, that is completely up to them.  It does not make it wrong to teach those skills.

> **wilee-nilee said:**
> 
Jealous; I have never wanted to write a script it is psychological observation and the OP himself says he was so proud of it, This is some basic stuff, what is the motivation for posting this, especially when as another poster says you would learn this in a computer science course.

You implied that the OP recklessly ignored the obvious dangers of sharing his discovery in his conceited desire to boast.  A less inflammatory, more realistic interpretation would be that he wanted to tell us about what he'd found because of a genuine desire to share information. Pride in his discovery does not necessarily mean he shared it to feed his ego; your interpretation could only be meant to derogate. 

> **wilee-nilee said:**
> 
I would be glad to give a more analytical observation of your motivations but I think I have said enough and I suspect you don't understand anyway, or are stuck in your black and white thinking process. Just a observation man. ;)

You wrote all that, but still avoided answering any of my points.  How about you actually address them in your next reply?  Or am I right in thinking that you now realize how utterly mistaken you were in your original comments and regret having ever posted them?  You can just write "I was wrong.  I am sorry."  Or you can continue to try and divert attention onto me.  But your evasive tactics look pretty pathetic.  Just an observation man.

---

### Post by starcannon on 2009-11-16
If you have ssh access to a machine, there is very little you couldn't access, given an account with enough permissions. Mic, Camera, email, browser history, one could even undelete files. I would assume any machine I had ssh access to would be part of a trusted relationship, whether with my wife, or a boss, or employee, or child, and that eves-dropping would not be needed anyway.

---

### Post by earthpigg on 2009-11-16
here is why I personally am slightly put off by your posts, wilee-nilee:

I have never taken ***any*** college courses relating to computers. not a single one.

I am a student of the ***University of ubuntuforums.org***.

I regard discussions here as classes I am taking.

Look back through my post history if you disbelieve me. Look at a few random posts by me in the last month, then go back to my first 100 posts or so. I am certainly no guru, but I've learned a heck of a lot since coming here as a complete Linux novice.

I absolutely rely on open forum discourse for my continued learning.

The general tone and rationale of your posts are a direct attack on my continued education, and I will very rapidly depart ubuntuforums.org permanently if the mods ever adopt what you propose (disallowing discussions of anything that could potentially be used for immoral/illegal purposes would destroy UF for me).

I suspect that I am not the only one.


Mods: I understand you will want to clean this thread up. If you do so, may I request that you delete/jail/move/do-whatever-you-like to the posts debating whether or not this should be posted, but please leave the thread open and the original post and on-topic discussion intact?

---

### Post by Tibuda on 2009-11-16
> **earthpigg said:**
> I am a student of the University of ubuntuforums.org.

That's a nice university... :)

---

### Post by youbuntu on 2009-11-16
> **wilee-nilee said:**
> Nice display of thinking with dichotomies, oops now I have posted again; your bait worked you can be proud of yourself. ;) It is not a binomial world. Coming to conclusions as to why I do or what I don't do is a projection.

I have full access to world wide data bases via my college enrollment If I even cared about this other then a cursory set of comments I would be glad to find the laws and post them, can you prove I am wrong? or is it just a natural response to argue. Your information is no more valid in it's presentation then mine. we all know the laws in whatever country we live in, at least in a broader sense.

I think we need to look at the larger picture, If you take a course in computer sciences or whatever there called you will practice hacking and cracking..etc. This is in a completely different setting. So lets say a jealous partner wants to spy on their partner and something negative happens because of this ability to remote spy. There are numerous reasons why this is not a good idea being posted on a forum.

Jealous; I have never wanted to write a script it is psychological observation and the OP himself says he was so proud of it, This is some basic stuff, what is the motivation for posting this, especially when as another poster says you would learn this in a computer science course.

I would be glad to give a more analytical observation of your motivations but I think I have said enough and I suspect you don't understand anyway, or are stuck in your black and white thinking process. Just a observation man. ;)

You're making a mountain from a grain of sand, and it is laughable.

---

### Post by squilookle on 2009-11-16
Even so, there may be situations where this is useful... of the top of my head, maybe you are not spying on someone, but want to hear what you voice sounds like and the speakers on REMOTE and the microphone on LOCAL are broken... it could happen...

---

### Post by starcannon on 2009-11-16
> **squilookle said:**
> Even so, there may be situations where this is useful... of the top of my head, maybe you are not spying on someone, but want to hear what you voice sounds like and the speakers on REMOTE and the microphone on LOCAL are broken... it could happen...
Also useful for home security device.

---

### Post by Dragonbite on 2009-11-16
> **wilee-nilee said:**
> I think we need to look at the larger picture, If you take a course in computer sciences or whatever there called you will practice hacking and cracking..etc. This is in a completely different setting. So lets say a jealous partner wants to spy on their partner and something negative happens because of this ability to remote spy. There are numerous reasons why this is not a good idea being posted on a forum.

Any jealous partner can still spy on their partner through whatever means they would have beforehand, really.  Like just looking through the window. 

The tool isn't an issue and how many people are serviced now by knowing this is possible? Would this be an issue if it were instructions on how to use a legitimately bought webcam?  What about when webcams first came out?

I don't have to worry about this because I'm having enough trouble getting the mic of my webcam working in the first place!

---

### Post by wilee-nilee on 2009-11-17
<snip>

---

### Post by phrostbyte on 2009-11-17
/dev is just a enumeration of various devices on your PC

Linux is based on POSIX model of "everything is a file", where most devices are virtualized as files. So your speaker and mic are just files. Even processes are just files, check /proc, where there is metadata and access to the address space of every process running (it's a cute way to do IPC, I guess)

You don't need root to do this btw. Just like you don't need root to use your mic. Many programs will read from /dev/audio or /dev/dsp to get mic input. IT used to be that the ONLY way to play audio or get mic was to read or write to these files (ALSA changed that), but I think in BSD this is still true today.

A cool consequence of this that you can do some pretty powerful things with just the shell, because all a language needs in Linux is File I/O and it can do some powerful things. It doesn't need to know how to play music or write sockets or a number of things. Just how to write to and read from files :)

---

### Post by wilee-nilee on 2009-11-17
So it turns out that in the United States if you listen remotely to somebody else it is covered under Tort laws, but it is very complex, and different states have different laws. I suspect that these sort of laws are mirrored in other countries as well.

So some of the reasons why it is okay in general, expressed in this thread without cherry picking are generally correct, although check your local laws if you intend to use this in any manner that is called Intrusion upon Seclusion in the Tort rulings. 

I think some of you are argumentative in nature and will follow this model just to prove your point while trying to demean others by labeling. When you at the same time cherry pick and have no real proof of your own argument. You have to be careful not to project this ego based argumentative model, you may have others agree with you but does this serve any sort of functional way of discussion? Does this model actually limit you from a more deeper cognitive realization and expression?

I recognize the OP's argument that they have no ill intent, personally I believe very little of what I see people say as far as personal responsibility on the net or hear in real life. The known human reactions to getting ahead at the expense of others is a easy model to recognize. In all of my responses was the idea of the possibilities of miss use of this sort of tool set.

[http://itlaw.wikia.com/wiki/Intrusion_into_seclusion](http://itlaw.wikia.com/wiki/Intrusion_into_seclusion)

This thread was so similar to the I am leaving Linux to go back to Windows posting and the all to familiar side stepped backlash from the Linux bound community. It was actually quite funny as it always is to observe the whole thing. ;)

---

### Post by youbuntu on 2009-11-17
> **wilee-nilee said:**
> So it turns out that in the United States if you listen remotely to somebody else it is covered under Tort laws, but it is very complex, and different states have different laws. I suspect that these sort of laws are mirrored in other countries as well.

So some of the reasons why it is okay in general, expressed in this thread without cherry picking are generally correct, although check your local laws if you intend to use this in any manner that is called Intrusion upon Seclusion in the Tort rulings. 

I think some of you are argumentative in nature and will follow this model just to prove your point while trying to demean others by labeling. When you at the same time cherry pick and have no real proof of your own argument. You have to be careful not to project this ego based argumentative model, you may have others agree with you but does this serve any sort of functional way of discussion? Does this model actually limit you from a more deeper cognitive realization and expression?

I recognize the OP's argument that they have no ill intent, personally I believe very little of what I see people say as far as personal responsibility on the net or hear in real life. The known human reactions to getting ahead at the expense of others is a easy model to recognize. In all of my responses was the idea of the possibilities of miss use of this sort of tool set.

[http://itlaw.wikia.com/wiki/Intrusion_into_seclusion](http://itlaw.wikia.com/wiki/Intrusion_into_seclusion)

This thread was so similar to the I am leaving Linux to go back to Windows posting and the all to familiar side stepped backlash from the Linux bound community. It was actually quite funny as it always is to observe the whole thing. ;)

Well it would appear that you being a natural cynic, is your issue to deal with, not ours. Oh, and I thought you weren't going to participate in this thread any longer?... interesting...

---

### Post by HermanAB on 2009-11-17
Playing with audio can be hours of fun.  these tricks can also be useful as a burglar alarm, door intercom, baby monitor, music server and the like.

You could pipe the audio through sox, to compress it before sending it over SSH, then pipe it through sox again on the receiving side to expand it.  See 'man sox' for details.

A more efficient use of bandwidth on a LAN is to use netcat instead of SSH.  See 'man nc' for details.

These tricks can of course also be used to pipe a webcam/scanner/printer/whatever over the net.

---

### Post by wilee-nilee on 2009-11-17
> **glossywhite said:**
> Well it would appear that you being a natural cynic, is your issue to deal with, not ours. Oh, and I thought you weren't going to participate in this thread any longer?... interesting...

I was asked to show proof of my contention, so I did. A interesting without at the least a hypothesis is nonsensical, come on man spit it out. ;)

---

### Post by youbuntu on 2009-11-17
> **wilee-nilee said:**
> I was asked to show proof of my contention, so I did. A interesting with at the least a hypothesis is nonsensical, come on man spit it out. ;)
If really have no intention of talking to one so difficult to understand, and as provocative as you, thankyou. If you wish to convince people of your theories, it is not for me to stop you, but rest assured, this is the last communication you will receive from me.

Thanks.

---

### Post by wilee-nilee on 2009-11-17
> **glossywhite said:**
> If really have no intention of talking to one so difficult to understand, and as provocative as you, thankyou. If you wish to convince people of your theories, it is not for me to stop you, but rest assured, this is the last communication you will receive from me.

Thanks.

Sorry you feel that way. ;)

I think if your not understanding me it is that I am challenging norms of thought and communication. This comes from many years of study in this area I am not an expert but there is plenty of peer reviewed empirical research to support this analysis.

---

### Post by earthpigg on 2009-11-18
@ wilee-nilee -

in regards to your advocating that this does not belong on a public forum, and only belongs in private paid college courses... i touched on this earlier, but allow me to be more blunt with my question because you chose not to address my point:

so, in a nut shell, someone to poor to go to college is not worthy of information that will convert his old computer into a free baby monitor, because someone else could theoretically hypothetically maybe kinda sorta perhaps use it to spy on his wife?

that is what your proposal amounts to.

correct me if i am wrong. please.

alternatively, what is your proposal to allow the low-income family to learn how to convert their old (perhaps, donated) computer into a baby monitor if this information must be censored?

---

### Post by toupeiro on 2009-11-18
Personally, I thought it was clever as heck.  Luckily this prank would be wasted on me.  All my mic's have off switches, and are generally off. :P

---

### Post by wilee-nilee on 2009-11-18
> **earthpigg said:**
> @ wilee-nilee -

in regards to your advocating that this does not belong on a public forum, and only belongs in private paid college courses... i touched on this earlier, but allow me to be more blunt with my question because you chose not to address my point:

so, in a nut shell, someone to poor to go to college is not worthy of information that will convert his old computer into a free baby monitor, because someone else could theoretically hypothetically maybe kinda sorta perhaps use it to spy on his wife?

that is what your proposal amounts to.

correct me if i am wrong. please.

alternatively, what is your proposal to allow the low-income family to learn how to convert their old (perhaps, donated) computer into a baby monitor if this information must be censored?

(Sarcasm)
Yeah that's exactly what I said.

Show me where I said that, your converting what you think I said into your own interpretation, it is called a, projection. What rational person would say that, oh wait a minute you did. :)

What rational person would say that as a baby monitor it is not useful, kind of a expensive baby monitor. 

The whole problem with all of you who try to make this into a argument with me is your not reading what I wrote. Yes my statement that it was illegal was a broad statement but I clarified the possibilities of miss use, and posted the link to the tort rulings. :)

I also in the tort ruling post said that it is a very complex issue and that every state is a little different. The difference is basically whether you have to let a person know if your recording or listening.

Why are we even having this conversation I was asked for proof I have shown it, I will spin on my head while juggling three apples to if you want. ;)

Edit; @wilee-nilee Quote "So some of the reasons why it is okay in general, expressed in this thread without cherry picking are generally correct, although check your local laws if you intend to use this in any manner that is called Intrusion upon Seclusion in the Tort rulings".

---

### Post by kauboy on 2009-11-18
I don't think this is as much a security issue as other things you could do with SSH (with an admin account). If someone has access to another computer on a network via SSH, its clear that this person has the necessary permission to access that system. Mic is a part of that system. Whether it can be accessed via a non-admin account or not is something I'm not sure of.

As someone pointed out, the remote system has to have a mic, it has to be turned on, and the system has to be turned on, for all this to work as an effective spying mechanism. Unless the person using this setup has direct physical control over the remote system (LAN in one's home) or is well acquainted with the admin of that system to socially-engineer him/her into this setup, this kinda arrangement is, to a great extent, not feasible 24x7. While allowing someone to access your system remotely via SSH, one has to be aware of these security issues.

I would like to commend the OP for making this public; what if he/she had chosen to keep it to himself/herself and used it for all those wrong reasons for personal gain? (I'm sure he/she didn't!) In that case, many of us may well have been in the dark, not being aware that such a possibility even exists! It is only because this was posted publicly that we are able to have a discussion on this and guard ourselves against it. Of course, this info may be available elsewhere on the Internet, but I got to know this only here.

This could be used for so many constructive purposes, say a network voice chat! Just because the knife could be used for all the very wrong reasons doesn't mean that kids shouldn't be taught how to cut an apple with it. Same applies to using mic-to-speaker tunneling via SSH. :D

Besides, I suppose all this discussion popped up only because of the title 'Audio spying'. Can we change that please?? :D

---

### Post by Exodist on 2009-11-18
> **earthpigg said:**
> @ wilee-nilee -

in regards to your advocating that this does not belong on a public forum, and only belongs in private paid college courses... i touched on this earlier, but allow me to be more blunt with my question because you chose not to address my point:

so, in a nut shell, someone to poor to go to college is not worthy of information that will convert his old computer into a free baby monitor, because someone else could theoretically hypothetically maybe kinda sorta perhaps use it to spy on his wife?

that is what your proposal amounts to.

correct me if i am wrong. please.

alternatively, what is your proposal to allow the low-income family to learn how to convert their old (perhaps, donated) computer into a baby monitor if this information must be censored?
+infinity


> I don't think this is as much a security issue as other things you could do with SSH (with an admin account). If someone has access to another computer on a network via SSH, its clear that this person has the necessary permission to access that system.True that..

> Sarcasm)
Yeah that's exactly what I said.

Show me where I said that, your converting what you think I said into your own interpretation, it is called a, projection. What rational person would say that, oh wait a minute you did. :smile:

What rational person would say that as a baby monitor it is not useful, kind of a expensive baby monitor. 

The whole problem with all of you who try to make this into a argument with me is your not reading what I wrote. Yes my statement that it was illegal was a broad statement but I clarified the possibilities of miss use, and posted the link to the tort rulings. :smile:

I also in the tort ruling post said that it is a very complex issue and that every state is a little different. The difference is basically whether you have to let a person know if your recording or listening.

Why are we even having this conversation I was asked for proof I have shown it, I will spin on my head while juggling three apples to if you want. :wink:

Edit; @wilee-nilee Quote "So some of the reasons why it is okay in general, expressed in this thread without cherry picking are generally correct, although check your local laws if you intend to use this in any manner that is called Intrusion upon Seclusion in the Tort rulings".Wilee, you ever heard of a net camera? Same thing..  100% legal in all states to put in your own house. Also 100% legal to post on your property viewing the public streets and neighborhood. Why you ask, ITS PUBLIC.   

Big question is, what are you really afraid of? /makes Willie a tin-foil hat.....

[Link to network cameras on newegg ]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=521&Tpk=network%20camera")

---

### Post by wilee-nilee on 2009-11-18
> **Exodist said:**
> +infinity


True that..

Wilee, you ever heard of a net camera? Same thing..  100% legal in all states to put in your own house. Also 100% legal to post on your property viewing the public streets and neighborhood. Why you ask, ITS PUBLIC.   

Big question is, what are you really afraid of? /makes Willie a tin-foil hat.....

[Link to network cameras on newegg ]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=521&Tpk=network%20camera")

I prefer the tinfoil coveralls you know gotta keep in touch with the mother ship. ;)

---

### Post by bluenova on 2009-11-18
Great thread :popcorn:

It's amazing how many people in this thread think the content should be restricted for the good of society. You would do well working for the Chinese government :D.

---

### Post by Grenage on 2009-11-18
ssh <username>@192.168.1.2 'dd bs=1k if=/dev/audio' > /dev/audio

I didn't know you could reference dd without an ouput destination; nice.

---

### Post by t0p on 2009-11-18
> **wilee-nilee said:**
> (Sarcasm)
Yeah that's exactly what I said.

Show me where I said that, your converting what you think I said into your own interpretation, it is called a, projection. What rational person would say that, oh wait a minute you did. :)

What rational person would say that as a baby monitor it is not useful, kind of a expensive baby monitor. 

The whole problem with all of you who try to make this into a argument with me is your not reading what I wrote. Yes my statement that it was illegal was a broad statement but I clarified the possibilities of miss use, and posted the link to the tort rulings. :)

I also in the tort ruling post said that it is a very complex issue and that every state is a little different. The difference is basically whether you have to let a person know if your recording or listening.

Why are we even having this conversation I was asked for proof I have shown it, I will spin on my head while juggling three apples to if you want. ;)

Edit; @wilee-nilee Quote "So some of the reasons why it is okay in general, expressed in this thread without cherry picking are generally correct, although check your local laws if you intend to use this in any manner that is called Intrusion upon Seclusion in the Tort rulings".

Actually no, you didn't post a link to anything that "proves" your assertion.

The linked article refers to "intrusion into seclusion" and invasion of privacy.  Since the person behind the remote "bugging" has admin privileges on the computer in question, it is reasonable to assume that the computer is in his home or place of business, in a room to which he has access.  Therefore it is reasonable to assume that no-one in that room can have legitimate expectation of privacy from him.  Therefore he cannot be intruding into someone else's seclusion.

In an earlier post, you wrote that under US law, it is illegal to spy on people in a public place unless you display a sign warning about the surveillance.  "Intrustion into seclusion" has no relevance in that situation.

And you still have not addressed a very important point I raised earlier.  You say that if the surveillance is illegal under US law, the OP shouldn't have posted about it in this forum.  What makes US law the deciding factor?  This forum is hosted by Canonical, whose offices are in London and on the Isle of Man.  Shouldn't UK or European law govern this?  If US law, why not Phillipines law?  Or People's Republic of China's law?

(That'd be pretty crazy: if Chinese law governed what could and couldn't appear on the internet.)

But all the talk of laws is irrelevant.  We are talking about discussion of a technical subject in a tech-related forum.  Your original assertion that the OP had done something "wrong" was ridiculous; you must have realized that by now, but some kind of foolish pride is stopping you from admitting you were wrong or from even just shutting up.  It's just as well that other forum members are as pig-headed and argumentative as you.

---

### Post by t0p on 2009-11-18
> **kauboy said:**
> 
I would like to commend the OP for making this public; what if he/she had chosen to keep it to himself/herself and used it for all those wrong reasons for personal gain? (I'm sure he/she didn't!) In that case, many of us may well have been in the dark, not being aware that such a possibility even exists! It is only because this was posted publicly that we are able to have a discussion on this and guard ourselves against it. Of course, this info may be available elsewhere on the Internet, but I got to know this only here.


I don't think the value of the original post is that it warns us about the possibility of spying.  It is the fact that it's an example of how devices can be controlled remotely.  A technical matter, nothing more.

And yes, the info is available in many other places.  But when one "discovers" something, one often feels compelled to share one's "discovery".  This should be encouraged, otherwise we'll never get to hear about real new discoveries.

---

### Post by renkinjutsu on 2009-11-18
now, someone figure out how to SEND audio through a remote mic.. This can be used for simple calls!

---

### Post by Grenage on 2009-11-18
> **renkinjutsu said:**
> now, someone figure out how to SEND audio through a remote mic.. This can be used for simple calls!

That's also possible, along similar lines.

---

### Post by Dragonbite on 2009-11-18
I've fallen, and I can't get up!

---

### Post by earthpigg on 2009-11-18
ugh. still dodging.

@ wilee-nilee, who said...
> Exactly it is illegal and posting this on a gigantic world wide forum is not good. The OP doesn't know how this will be used by others, now where is that report button.


what is your proposal to allow the low-income family to learn how to convert their old (perhaps, donated) computer into a baby monitor if this information must be censored?

---

### Post by kauboy on 2009-11-19
> **t0p said:**
> I don't think the value of the original post is that it warns us about the possibility of spying.  It is the fact that it's an example of how devices can be controlled remotely.  A technical matter, nothing more.

And yes, the info is available in many other places.  But when one "discovers" something, one often feels compelled to share one's "discovery".  This should be encouraged, otherwise we'll never get to hear about real new discoveries.

Yes, I agree. It's simply something technical you could do with SSH. That "spying" line was directed at skeptics! As I said, this whole discussion might not have turned in the (wrong) direction of "spying" (instead of the actual technical aspect) if the title weren't so. (I changed my Re: title) :D

---

### Post by renkinjutsu on 2009-11-19
> **renkinjutsu said:**
> now, someone figure out how to SEND audio through a remote mic.. This can be used for simple calls!

I cannot, for the life of me, figure this out! D;

---

### Post by earthpigg on 2009-11-19
> **renkinjutsu said:**
> > now, someone figure out how to SEND audio through a remote mic.. This can be used for simple calls!

I cannot, for the life of me, figure this out! D;

ssh from computer 1 to computer 2, and from there ssh ***back*** to computer 1 and pull the audio accordingly using the command in the OP.

on computer 2, add a line to the end of the .bashrc of an otherwise unused username, so whenever anyone ever logs into that username, the first thing it does is execute the command in the OP to pull audio from computer one.

essentially, a super complex set of two tin cans with a string.

---

### Post by renkinjutsu on 2009-11-19
> **earthpigg said:**
> ssh from computer 1 to computer 2, and from there ssh ***back*** to computer 1 and pull the audio accordingly using the command in the OP.

on computer 2, add a line to the end of the .bashrc of an otherwise unused username, so whenever anyone ever logs into that username, the first thing it does is execute the command in the OP to pull audio from computer one.

essentially, a super complex set of two tin cans with a string.

=\ can't do that if the client i'm connecting from is behind a firewall or doesn't have an ssh server, but that'll do for now

---

### Post by wilee-nilee on 2009-11-19
> **kauboy said:**
> Yes, I agree. It's simply something technical you could do with SSH. That "spying" line was directed at skeptics! As I said, this whole discussion might not have turned in the (wrong) direction of "spying" (instead of the actual technical aspect) if the title weren't so. (I changed my Re: title) :D

I think your correct in the use of the word spy in the thread title.

@earthpig I did answer your question, presenting a hypothetical is okay I made some myself but I didn't harp on others to exactly agree with my contentions. Your motivation of I am right and you are wrong are flawed; when all of us in this thread have made statements and opinions without a full understanding of the laws and contextual situations in which they could be inforced.

I could cherry pick these out with my own interpretation and be a aggressive poster but it just doesn't seem functional, whatever that actually is.

Also as far as college enrollment I see a Semper FI in your signature if you were or are in the military you have free college enrollment or at least partially payed. The argument of poor people not being able to attend is problematic anybody can get financial aid from the US government, if you qualify to attend college and you don't have a former financial unpaid debt or bad credit, even bad credit though wont necessarily keep a person from getting financial aid. There are also many grants available, and scholarships.

To the rest of you the link to the Tort laws is the frame work you would need to investigate more. The link is a short comment. The Tort rulings or laws are very complex and are state bound in there enforcement in the United States. Although there are probably federal laws and rulings involved in several scenarios.

If you look further into the Torts you may notice that even in your own house with your own computers you could break the law using this method, so there lie a set of problems interpretation of the laws and personal needs.

If we go through life using confirmation bias and rudimentary uses of dichotomies to come to opinions it is a lack of cognitive development.

---

### Post by youbuntu on 2009-11-20
> **wilee-nilee said:**
> I think your correct in the use of the word spy in the thread title.

@earthpig I did answer your question, presenting a hypothetical is okay I made some myself but I didn't harp on others to exactly agree with my contentions. Your motivation of I am right and you are wrong are flawed; when all of us in this thread have made statements and opinions without a full understanding of the laws and contextual situations in which they could be inforced.

I could cherry pick these out with my own interpretation and be a aggressive poster but it just doesn't seem functional, whatever that actually is.

Also as far as college enrollment I see a Semper FI in your signature if you were or are in the military you have free college enrollment or at least partially payed. The argument of poor people not being able to attend is problematic anybody can get financial aid from the US government, if you qualify to attend college and you don't have a former financial unpaid debt or bad credit, even bad credit though wont necessarily keep a person from getting financial aid. There are also many grants available, and scholarships.

To the rest of you the link to the Tort laws is the frame work you would need to investigate more. The link is a short comment. The Tort rulings or laws are very complex and are state bound in there enforcement in the United States. Although there are probably federal laws and rulings involved in several scenarios.

If you look further into the Torts you may notice that even in your own house with your own computers you could break the law using this method, so there lie a set of problems interpretation of the laws and personal needs.

If we go through life using confirmation bias and rudimentary uses of dichotomies to come to opinions it is a lack of cognitive development.


You should pursue a career as a politician - you'd be fantastic at it, baffling people with hair-splitting analysis which leads nowhere and wastes time. You are wasted here, you can do better than speak to us mere mortals ;).

---

### Post by earthpigg on 2009-11-20
well, this was odd.

```
ssh <username>@192.168.1.2 'dd bs=1k if=/dev/audio' > /dev/audio
```

i got permission denied when using that command, so i used

```
ssh <username>@192.168.1.2 '***sudo*** dd bs=1k if=/dev/audio' > /dev/audio
```

and got:

```
[username: ~]$ ssh <username>@192.168.1.2 'sudo dd bs=1k if=/dev/audio' > /dev/audio
<username>@192.168.1.2's password: 
[sudo] password for <username>: ***sudoer-password-displayed-in-plain-visible-text-here-as-i-typed!***
```

the part in bold-italics is the relevant part. i've never seen this behavior before.

---

### Post by NCLI on 2009-11-20
Does anyone know whether it's possible to SSH into a machine connected to my home network from, for example, an airport? The problem is that it's behind a router, so if I SSH into the IP-address displayed at whatismyip.com, I just connect to my router.

---

### Post by earthpigg on 2009-11-20
> 
Does anyone know whether it's possible to SSH into a machine connected to my home network from, for example, an airport? The problem is that it's behind a router, so if I SSH into the IP-address displayed at whatismyip.com, I just connect to my router.

need to enable port forwarding on the router. on my AT&T one, its called "DMZ plus" mode.

if you do that, i also suggest you use a port other than the default 22.

```
[username: ~]$ cat /etc/ssh/sshd_config | grep Port
Port 44444
```

so, in that example, i would connect to my computer from another...

```
ssh -X -p 44444 username@123.123.123.123
```

the -X is for x forwarding, so i could run graphical apps stored on the host computer.

but you may be like me and have a dynamic IP address. meaning that when you leave home on friday your IP was 123.123.123.123, but it changed on Saturday morning it changed for some number you don't know. and IP addresses are hard to remember anyways.

we need a 3rd party that we can set up the host computer to notify of it's current IP address.

[http://en.wikipedia.org/wiki/Dyndns](http://en.wikipedia.org/wiki/Dyndns)

one of the cost-free services they provide is allowing you to register a DNS address. you then install a daemon they provide (i think its also in the ubuntu repos) that notifies dyndns of the host's current IP address every n minutes.

so, after you have all that set up the command becomes:

```
ssh -X -p 44444 username@ncli.homelinux.net
```

all you need to remember is the random port you picked (44444), ncli.homelinux.net, and your normal login username/pass.

for a bit of extra security, define the AllowUsers in sshd_config to be just the people you want to have access...

```
[username: ~]$ cat /etc/ssh/sshd_config | grep Allow
AllowUsers nvli
```

and verify that Protocol 2 is being used. the old protocol 1 apparently has all sorts of known security vulnerabilities.

```
[username: ~]$ cat /etc/ssh/sshd_config | grep Protoc
Protocol 2
```

so, you can now access that computer from any other computer with ssh.

bad guys would need to know (in order of easy v hard to figure out) and you need to remember:

-either your IP address, or your registered DNS address.
-the random port you picked.
-your username.
-your password.

iirc, OS X has ssh installed by default.

you will also want to monitor /var/log/auth.log periodically.

```
tail /var/log/auth.log
```

---

### Post by FuturePilot on 2009-11-20
> **NCLI said:**
> Does anyone know whether it's possible to SSH into a machine connected to my home network from, for example, an airport? The problem is that it's behind a router, so if I SSH into the IP-address displayed at whatismyip.com, I just connect to my router.

You have to forward the port to the computer with the SSH server on it. Also, if you're able to connect to your router remotely, I suggest disabling remote access to your router. It's a huge security issue and rarely would you need access to that remotely.

> **earthpigg said:**
>  on my AT&T one, its called "DMZ plus" mode.



Be careful with DMZ as it usually forwards **all** ports.

---

### Post by renkinjutsu on 2009-11-20
> **earthpigg said:**
> well, this was odd.

```
ssh <username>@192.168.1.2 'dd bs=1k if=/dev/audio' > /dev/audio
```

i got permission denied when using that command, so i used

```
ssh <username>@192.168.1.2 '***sudo*** dd bs=1k if=/dev/audio' > /dev/audio
```

and got:

```
[username: ~]$ ssh <username>@192.168.1.2 'sudo dd bs=1k if=/dev/audio' > /dev/audio
<username>@192.168.1.2's password: 
[sudo] password for <username>: ***sudoer-password-displayed-in-plain-visible-text-here-as-i-typed!***
```

the part in bold-italics is the relevant part. i've never seen this behavior before.

You shouldn't need root privelages to access the audio device.. are both your users in the audio group?

---

### Post by earthpigg on 2009-11-20
> **renkinjutsu said:**
> You shouldn't need root privelages to access the audio device.. are both your users in the audio group?

that was it, i should have thought of that :D

---

### Post by NCLI on 2009-11-20
> **FuturePilot said:**
> You have to forward the port to the computer with the SSH server on it. Also, if you're able to connect to your router remotely, I suggest disabling remote access to your router. It's a huge security issue and rarely would you need access to that remotely.
It was just to illustrate my point, remote access is not enabled ;)

> **FuturePilot said:**
> Be careful with DMZ as it usually forwards **all** ports.

Exactly what I thought when reading that post. I use use DMZ for my PS3, since it's currently impossible to hack, even if you have local access...

Anyway, other than the DMZ-thing, thanks a lot for the guide earthpigg! I'll try it out next time I'm forced to leave my house(AKA Monday).:D

---

### Post by xpod on 2009-11-20
Has anyone else tried while using some kind of encryption rather than normal passwords as it just hangs after i enter my passphrase(rsa).I can log in just fine normally of course.
```
 ssh -p **** me@192.168.1.2 'dd bs=1k if=/dev/audio' > /dev/audio
Enter passphrase for key '/home/me/.ssh/id_rsa': >**then nothing**<

```

---

### Post by wilee-nilee on 2009-11-20
> **glossywhite said:**
> You should pursue a career as a politician - you'd be fantastic at it, baffling people with hair-splitting analysis which leads nowhere and wastes time. You are wasted here, you can do better than speak to us mere mortals ;).

That is very funny, :) in actuality I don't consider myself as smarter or better then anybody. 

It would lead to somewhere if a person steps back from pre-formed thought and thinks abstractly. If you closely look at some of my responses I say we all have walked on our own edge of truth that has no concrete base. As far as splitting hairs the cherry picked out of context questioning on what I posted is hair splitting, but I did the same to the responses.

There is nothing like placating personal responsibility by placing the blame on another, it feels so good to be the higher power doesn't it. ;)

---

### Post by youbuntu on 2009-11-20
> **wilee-nilee said:**
> That is very funny, :) in actuality I don't consider myself as smarter or better then anybody. 

It would lead to somewhere if a person steps back from pre-formed thought and thinks abstractly. If you closely look at some of my responses I say we all have walked on our own edge of truth that has no concrete base. As far as splitting hairs the cherry picked out of context questioning on what I posted is hair splitting, but I did the same to the responses.

Really? that's amazing :rolleyes: *yawn*

---

### Post by Z3ro3X on 2010-11-25
This command no longer works in 10.10.  There's no /dev/audio anymore.  Perhaps someone with more skill then I can provide the command that would work.

---

### Post by earthpigg on 2010-11-25
does /dev/snd exist and work for you?

---

### Post by Z3ro3X on 2010-11-25
> **earthpigg said:**
> does /dev/snd exist and work for you?

Yes but it's a folder with files.

$ ls -l /dev/snd
total 0
drwxr-xr-x  2 root root      60 2010-11-24 18:02 by-id
drwxr-xr-x  2 root root      80 2010-11-24 18:02 by-path
crw-rw----+ 1 root audio 116, 9 2010-11-24 18:02 controlC0
crw-rw----+ 1 root audio 116, 5 2010-11-24 18:02 controlC1
crw-rw----+ 1 root audio 116, 8 2010-11-25 00:18 pcmC0D0c
crw-rw----+ 1 root audio 116, 7 2010-11-25 13:30 pcmC0D0p
crw-rw----+ 1 root audio 116, 6 2010-11-24 18:02 pcmC0D1c
crw-rw----+ 1 root audio 116, 4 2010-11-25 00:34 pcmC1D0c
crw-rw----+ 1 root audio 116, 3 2010-11-24 18:02 seq
crw-rw----+ 1 root audio 116, 2 2010-11-24 18:02 timer

---

### Post by nikonian on 2012-08-08
Update:

Here is how to do this using default pulseaudio mic and speakers, over ssh:


ssh user@ip-of-monitored-ubuntu-pc 'pacat -r' | pacat -p

;)

---

### Post by cariboo on 2012-08-08
This is a two year old thread. Closed.

---

