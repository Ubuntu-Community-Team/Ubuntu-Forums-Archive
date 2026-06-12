---
title: "Better Mobile Phone Sync"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by brickbat on 2007-10-18
For the next release can we please have some effort on phone syncing.  for example, opensync in the repos is still 0.19.  Thats over a year old.  The current version is 0.33.  Also, the whole procedure needs a gui.  The best in class program  for this is apples isync.

---

### Post by b20963a2 on 2007-10-19
I think [Conduit]("http://www.conduit-project.org/") is meant to improve the situation. It's already in the Gutsy repos but needs to be extended some more...

---

### Post by Zdravko on 2007-10-19
Yeah, this is already done for Gutsy.

---

### Post by brickbat on 2007-10-19
If you think its already done then please tell me how to sync my N73 Nokia phone with Thunderbird Contacts. Conduit is a good start but its not there yet.  It needs to be better integrated with Bluetooth and Opensync so you just select your phone, pair it and tell it what you want to sync it with.

---

### Post by Zdravko on 2007-10-19
I don't know. [b20963a2]("http://ubuntuforums.org/member.php?u=191242") said it is already in Gutsy's repos.

---

### Post by brickbat on 2007-10-19
Just because a single part of the puzzle is in the repo that doesnt mean its all done.  Do you even know what I'm talking about?

---

### Post by Zdravko on 2007-10-19
Not really. Sorry. Trying to be of some help :(

---

### Post by yelo3 on 2007-10-20
This is really usefull!

---

### Post by Zdravko on 2007-10-20
[yelo3]("http://ubuntuforums.org/member.php?u=166038"), yepp - it is.

---

### Post by Turgon on 2007-10-21
You will sadly not be able to sync you mobile phone with thunderbird or evolution with conduit at the moment, but as far as I know, its about to get implemented. 

I hope they will get this done for hardy, and I think thins is one of the things the devs should focus on. Edgy, feisty and gutsy really wasn't that much about adding new features that is useful after you have fully installed the system, and I hope they could focus more on that now.

---

### Post by brickbat on 2007-10-21
[http://www.conduit-project.org/ticket/172](http://www.conduit-project.org/ticket/172)

it is not even assigned to anyone and it is in the wishlist 3 year milestones - a bad sign.

Like i said, this whole area needs lots more work.

---

### Post by sneax on 2007-10-23
I agree, It's really annoying I can not sync my cell phone with ubuntu. Well I can actually after a lot of trying out (which a newbie never can, because there's not even a tutorial about it) and it works only half, totally useless (contacts gettings lost, calendar not syncing both ways ...).

---

### Post by DoctorMO on 2007-11-01
Good job I'm at the Ubuntu Developers Summit pushing this problem forward then isn't it:

[https://blueprints.edge.launchpad.net/ubuntu/+spec/syncintegration](https://blueprints.edge.launchpad.net/ubuntu/+spec/syncintegration)

We'll be talking about all the issues, solutions and problems with politics between OpenSync and Conduit.

---

### Post by Turgon on 2007-11-01
> **DoctorMO said:**
> Good job I'm at the Ubuntu Developers Summit pushing this problem forward then isn't it:

[https://blueprints.edge.launchpad.net/ubuntu/+spec/syncintegration](https://blueprints.edge.launchpad.net/ubuntu/+spec/syncintegration)

We'll be talking about all the issues, solutions and problems with politics between OpenSync and Conduit.

NIce job! Im reading on the conduit mailing list, and it seem like some good efforts to get this done.

---

### Post by seventynine on 2007-11-02
This would be great. Btw, I have my Nokia sync with Ubuntu already. Try this great step by step guide: [http://www.linuxscrew.com/2007/09/12/nokia-e-series-sync-with-evolution-via-bluetooth-in-ubuntu/](http://www.linuxscrew.com/2007/09/12/nokia-e-series-sync-with-evolution-via-bluetooth-in-ubuntu/)

Took me about 10 hours (over a few days), because I'm new to linux, but got it to work. It'd be really useful for Ubuntu to have this feature built-in. :wink:

---

### Post by jmesquita on 2007-11-04
Every time I try to talk anyone into exchanging Windows for Ubuntu I get 2 basic questions on the following order:

1. Will I be able to do everything I do nowadays?
2. What about all my Windows programs and files I am used to?

I see many posts on this forum that might start to answer the second question and that, I have to agree, is the hard one to solve. It is hard to get ppl to change from whatever they are used to something challenging and new like GimpShop instead of Photoshop or Totem instead of WMP, etc ...

But, what happened to the 1st question? Are we loosing focus somewhere down the road? The answer to most of the people who have asked me that question is still NO, or sometimes, with luck, MAYBE.

Guys, what do most ppl do with their computers? Check emails (fine with evolution or thunderbird), surf (firefox), print (I can see we are on the way with that) and, finally, use the computer as its personal organization tool making all the above glue together!! We are on the mobile phone era for christ sake! Everyone that uses a computer, wants to listen to MP3 or sync contacts with its "outlook"! This should be high priority IMHO.

Opensync works fine with evolution and with Nokia phones, but Ubuntu is running a damn old version of the libs on the repo (.19 where it should be .34).

The blueprint is really cool and will be eventually implemented, but what do Gusty users do? Can we at least upgrade the repo so it runs with basic phones for more advanced users? I don't want to recompile evolution-data-server just because my phone needs to be synced. I might as well keep my nokia PCSuite on a Windows second boot just for backing up and still have separate devices that are unable to talk to each other.

Anyway, I thought that after looking and searching for a week on how to get my damn phone to sync, I would start with the word out. I am sorry if I was a bit cranky about this, but I am a little disappointed with Gutsy on some points and thats the way I can contribute on it getting better.

Regards to all and thanks to every single one of you that made this possible,

João Mesquita

---

### Post by otto67 on 2007-11-06
Opensync 0.19 is well working with my Nokia E70 and I cannot see what is the crucial downside compared to 0.22 I used in Feisty.
Multisync-qad (now in apt-get  called multisync0.90) is nice graphical UI to do the thing. 
Dont blame linux developers. If phone manufacturers like Nokia are constantly refusing to work out their solutions for linux platform, then linux developers alone cannot go faster. 
I really wonder how crappy is Nokias attitude to this problem. PC-Suite for win is a bad software, refusing to do lot of things and when doing then with lot of unstability (f.ex. please Backup your Messages). Their PC-Suite application GUI is written in Java and should work in multitude of platforms but surprise - we support only MS Windows. 
Id like to put a stick in a certain hole on of these developers. Nokias attitude is very exemplary in this world. Simply because in every detail they chase only money. Doing crappy PC-Suite in the hope that poor mobile phone consumer will spend more and more to buy "quality extensions" to this software etc. etc.
But i sincerly hope that one day a big phone manufacturer will not neglect linux community and start to develop quality linux software for its phones (like NVIDIA is doing for videochips). And if then this community will use this manufacturer phones then probably other manufacturers start to change their attitude (like ATI is now doing for videochips).

---

### Post by jmesquita on 2007-11-06
> Opensync 0.19 is well working with my Nokia E70 and I cannot see what is the crucial downside compared to 0.22 I used in Feisty.
Multisync-qad (now in apt-get called multisync0.90) is nice graphical UI to do the thing. 

Nokia E61, E61i or the older 6xxx just gets "System Error" messages on the phone and its a reported bug on version 0.22 and now fixed on the newer versions (don't exactly recall what version).

> Dont blame linux developers. If phone manufacturers like Nokia are constantly refusing to work out their solutions for linux platform, then linux developers alone cannot go faster.

Let me emphasize one part of my post that was not very clear. I am NOT blaming the developers for anything, that was my idea of making suggestions on harsh way. We are both on the same side me being a developer and all and I know how hard it is to go "faster".

But, your critique is not entirely true if you look back at the Linux early ages. Linux started off by creating and developing fast support to proprietary hardware. NICs as a startup and then, lately, video cards. That was the way we got Nvidia and now ATI as well as most NIC developers to develop GPL drivers for their cards, wasn't it? The manufacturer not giving proper support or developing open source software was not a problem to us back then, why should it be now? We are freaking good and we can reverse engineer and make it work even better then their own softwares and IMO that's what makes Linux and open source in general worth it.

Anyway, I digress. My post was intended to get Ubuntu developers to draw some attention to the poor folks on the opensync project that has no user base to compare to and lack of hands to develop their promising piece of software. Ubuntu has that kinda of firepower and then again, IMHO that's where all the cannons were supposed to point at at the moment.

> But i sincerly hope that one day a big phone manufacturer will not neglect linux community and start to develop quality linux software for its phones (like NVIDIA is doing for videochips). And if then this community will use this manufacturer phones then probably other manufacturers start to change their attitude (like ATI is now doing for videochips).

Could not agree more over there. Till then, let's hack them up. :)

Sorry if I was a bit too agressive, that's my way of being ...

Mesquita

---

### Post by DoctorMO on 2007-11-14
> Anyway, I digress. My post was intended to get Ubuntu developers to draw some attention to the poor folks on the opensync project that has no user base to compare to and lack of hands to develop their promising piece of software. Ubuntu has that kinda of firepower and then again, IMHO that's where all the cannons were supposed to point at at the moment.

This is a constant misunderstanding about Canonical and Ubuntu; Ubuntu has no developers to work on these things; I'm going to work on this problem of integrating existing tools in my spare time since I have a job and a family that require attention too.

If people would pay for development to happen it wouldn't be so bad, but just because they get software for free they think it's free to create too.

---

### Post by scorp888 on 2008-11-09
> **Turgon said:**
> You will sadly not be able to sync you mobile phone with thunderbird or evolution with conduit at the moment, but as far as I know, its about to get implemented. 

I hope they will get this done for hardy, and I think thins is one of the things the devs should focus on. Edgy, feisty and gutsy really wasn't that much about adding new features that is useful after you have fully installed the system, and I hope they could focus more on that now.


13 months later, I wonder if Ubuntu has moved on any when it comes to phone sync, there doesn't seem to be a list of "good phones" that I can go get that work out the box, and there doesn't seem to be any moves towards supporting the basic syncml supporting phones either.

Ian

---

### Post by scorp888 on 2008-11-09
> **DoctorMO said:**
> This is a constant misunderstanding about Canonical and Ubuntu; Ubuntu has no developers to work on these things; I'm going to work on this problem of integrating existing tools in my spare time since I have a job and a family that require attention too.

If people would pay for development to happen it wouldn't be so bad, but just because they get software for free they think it's free to create too.

So easy answer, how much does it cost to get XXX model phone supported.

I'm pretty sure if Canonical can get the framework in place, supporting plugins, ala Isync, then if each model cost say £200, then you'd quickly find 200 users prepared to pay £1 towards it.

Ian

---

