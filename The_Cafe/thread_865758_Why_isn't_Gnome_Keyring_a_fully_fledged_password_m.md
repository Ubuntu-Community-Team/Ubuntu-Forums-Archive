---
title: "Why isn't Gnome Keyring a fully fledged password manager?"
date: 2008-07-21
forum: The Cafe
---

### Post by sicofante on 2008-07-21
Many times Gnome developers don't really grasp the potential of some of their own apps. The Keyring is, IMO, a perfect example.

No one should need to use any other password manager while having a desktop-wide one like this, but still Keyring only holds one or two passwords in most systems (most notably, Network Manager's).

Why don't Keyring developers take a look at Roboform (for instance) and make Keyring actually useful?

---

### Post by Polygon on 2008-07-21
because not many apps in gnome NEED  a passowrd (except for like you said network manager), its up to other apps to take advantage of the keyring thats included in most gnome installations

stuff like instant messaging clients, email checkers, anything that requires a password could do well by having it save the password in gnome keyring. Hell, pidgin saves its passwords as plain text, it would help a lot.

---

### Post by Bachstelze on 2008-07-21
I'm certain the Gnome developers will kindly accept your patches.

---

### Post by sicofante on 2008-07-21
> **Polygon said:**
> because not many apps in gnome NEED a passowrd (except for like you said network manager), its up to other apps to take advantage of the keyring thats included in most gnome installations
I wonder if it's easy to do so or not. I'm not a programmer, but it seems to me that only if it's easy for programmers to use Keyring, they would.

> stuff like instant messaging clients, email checkers, anything that requires a password could do well by having it save the password in gnome keyring. Hell, pidgin saves its passwords as plain text, it would help a lot.You see? There are quite a number of places where the Keyring could do something. In Roboform you can also save credit card information, web-site login forms (with more than the usual username-password pair), and more. It is the app that talks to Firefox and not the other way round, by the way.

> **HymnToLife said:**
> I'm certain the Gnome developers will kindly accept your patches.
What's that supposed to mean?

---

### Post by -grubby on 2008-07-21
> **sicofante said:**
> You see? There are quite a number of places where the Keyring could do something. In Roboform you can also save credit card information, web-site login forms (with more than the usual username-password pair), and more. 


What's that supposed to mean?

Writing code for gnome-keyring-manager

---

### Post by sicofante on 2008-07-21
> **nathangrubb said:**
> Writing code for gnome-keyring-manager
As if everyone on Earth writes code? What an absurd assumption.

---

### Post by Bachstelze on 2008-07-21
> **sicofante said:**
> As if everyone on Earth writes code? What an absurd assumption.

Sorry, I forgot the [sarcasm] tags ;)

Has the idea never occured to you that the reason gnome-keyring doesn't have the features *you* think it should have might just be because the Gnome team doesn't have a developer available and/or interested for coding it?

---

### Post by Dr Small on 2008-07-21
> **sicofante said:**
> As if everyone on Earth writes code? What an absurd assumption.
Oh... You must be one of the rare ones that don't ;)

---

### Post by quinnten83 on 2008-07-21
<preachy rant>
You know, 
just because somebody can't code, does not mean that they can't have an idea that is brilliant. i find the negative feedback that people get just for suggesting something that has to do with an existing program very exhausting.

There might very well be a reason why gnome keyring is not a full fledged password manager, but a simple explanation of why you think that is, would be better than all out sarcasm.

Answers like, maybe you should code it yourself are especially annoying as contrary to popular belief, most people on this forum can not code.
Perhaps this was not the best forum to suggest what he did, but a simple: "hey, why don't  you post on the gnome forums" would do, wouldn't you think?

Now, if I am reading this out of context, then please forgive me, but if I'm not, then we need to change our attitude.
</preachy rant>

---

### Post by Bachstelze on 2008-07-21
> **quinnten83 said:**
> 
You know, 
just because somebody can't code, does not mean that they can't have an idea that is brilliant.

Yes, I know. Are you, by any chance, trying to tell me that no one ever got the idea of having gnome-keyring manage all passwords in Gnome applications? I'm pretty sure someone did already. So I repeat, the reason this is not implemented is most likely one of the following:

1) The Gnome devs decided that it was irrelevant, too complicated, or otherwise unsuitable.
2) The Gnome devs liked the idea, but at the moment, no one is available and/or interested for coding it.

So if someone really wants this feature implemented into gnome-keyring right now, they must go talk to the Gnome devs and either try and convince then of the greatness of such a feature, or tell them they're interested in implementing it.

That's how it works, no offense meant to anyone.

---

### Post by Mr. Picklesworth on 2008-07-21
If I recall correctly, the GNOME Keyring folks are indeed aware that its interfaces are imperfect, and there was some talk of making it easier and more satisfying to work with. (I think some of that work may have hit 2.22, in fact).
It is definitely a good idea to use the keyring manager since it automatically deals with encryption, makes it easy to run backups (as with gconf), and can work between different applications.

The trouble now is we have to wait for other projects to support the thing. Your best bet is filing bugs in the respective projects' bug trackers, or maybe even look at pushing patches their way. Pidgin, for example, is currently storing passwords in plain text. Using the keyring for each platform would really be a good thing.


On another topic, the only idea I see here so far is to "make it better". What's with all the babbling?!

---

### Post by sicofante on 2008-07-22
> **HymnToLife said:**
> Sorry, I forgot the [sarcasm] tags ;)

Has the idea never occured to you that the reason gnome-keyring doesn't have the features *you* think it should have might just be because the Gnome team doesn't have a developer available and/or interested for coding it?
Dear HymnToLife: I'm well aware of your sarcasm, your mentality and your lack of manners. My replies were only meant to highlight all of this and you have done as expected. There's little to no interest in take any conversation further on this "code it yourself" aggressive attitude held by still too many Linux developers. Thankfully, this is not these forums' style, and that's the reason why "the rest of us" feel comfortable here. I've seen this tone of yours in many other threads and I beg you please try and stop it. It doesn't make any good to you or to these forums and of course never helps the ones asking questions.

> **Mr. Picklesworth said:**
> If I recall correctly, the GNOME Keyring folks are indeed aware that its interfaces are imperfect, and there was some talk of making it easier and more satisfying to work with. (I think some of that work may have hit 2.22, in fact).
That's great news. 

> The trouble now is we have to wait for other projects to support the thing.
Which is in direct relation to how easy and obvious it is, how much Gnome enforces that policy, etc. Think of OSX's Keychain.

> On another topic, the only idea I see here so far is to "make it better". What's with all the babbling?!Actually, it has been suggested that the Keyring is promoted to a higher status inside the Gnome desktop by making it easy to use with applications running inside that Desktop. It needs to be flexible enough to store different kinds of sensitive information, not just "username-password" pairs. Also it should have a well exposed interface so developing plugins for those apps not yet supporting it was very easy (thus relieving the developers of those apps of making that decision themselves). Of course that means "make it better" but my main point is "make it more present in the Gnome desktop" or only Gnome itself will be using it, which is exactly what happens right now.

---

### Post by Polygon on 2008-07-22
your blowing that comment way out of porportion dude, his comment wasn't bad at all and he is right, you are free to submit patches to gnome keyring if you want to see improvements 'now'

and  you cant compare this to osx, since apple created all the programs like mail, ichat and all that, so they all use the apple keyring cause they were DEVELOPED by apple, the only gnome projects that use passwords are like evolution and nm, and i think they both already use it....

---

### Post by Mr. Picklesworth on 2008-07-22
Does anyone know if FreeDesktop has a keyring specification? The keyring system being desktop-specific doesn't make much sense anyway, and that could be why it's so blatantly ignored. A proper standard across the ecosystem would definitely help things :)

---

### Post by iceback on 2008-07-22
'Cause it just took out 1.4GB of memory.

---

### Post by sicofante on 2008-07-22
> **Polygon said:**
> and  you cant compare this to osx, since apple created all the programs like mail, ichat and all that, so they all use the apple keyring cause they were DEVELOPED by apple, the only gnome projects that use passwords are like evolution and nm, and i think they both already use it....
Errr, wrong and wrong. Many third party apps use OSX's keychain because it's easy to use and has been properly promoted by Apple. Evolution does not use the Keyring. That alone is probably an indication that Keyring is the poor child in Gnome, and I'm suggesting it shouldn't be.

---

### Post by Polygon on 2008-07-22
going off what someone above ^ just said, the keyring in mac os x is standarized, there is only one for the entire os...with linux there is a bunch of combinations of software that a program can run on, kde, xfce, gnome, any of the lightweight *boxes, icewm, etc etc...if there is no standard then it becomes troublesome to support one keyring manager and not the other.

---

### Post by bruce89 on 2008-07-22
I heard there were plans to have WebKit use gnome-keyring. Shame Ephy 2.24 will still be Gecko.

---

### Post by sicofante on 2008-07-22
> **Polygon said:**
> going off what someone above ^ just said, the keyring in mac os x is standarized, there is only one for the entire os...with linux there is a bunch of combinations of software that a program can run on, kde, xfce, gnome, any of the lightweight *boxes, icewm, etc etc...if there is no standard then it becomes troublesome to support one keyring manager and not the other.
That's why this thread is about the **Gnome** keyring. It happens to be the desktop of choice for Ubuntu. That makes it no different from OSX in this regard.

---

### Post by frup on 2008-07-22
sicofante, if you desire this feature so much could I suggest that maybe you draft out your idea very very carefully and think of all the possibilities, use case scenarios and possible problems in very good detail and submit a bug report somewhere.

Along with your bug report you should probably post a bounty, you could pledge a certain amount for every other person who also pledges and that might spark a programmers interest.

Instead of being aggressive and hostile to other people pointing out mere facts, why not be proactive and takes steps to making your idea happen.

---

### Post by sicofante on 2008-07-22
> **frup said:**
> Instead of being aggressive and hostile to other people pointing out mere facts, why not be proactive and takes steps to making your idea happen.
I'm not being aggressive and hostile to other people (at least not to those that haven't been agressive or hostile to me before...), but you are making a point and you're partially right.

I *could *become a designer for Gnome (that's exactly what you're asking for, believe it or not), but I am just a *user *who believes this is one big design flaw in Gnome. I don't expect Gnome designers to just follow every suggestion or request, but I do believe users must expose their complaints so developers get to know what users are demanding and why.

I certainly do expect Mark Shuttleworth reads these forums looking for users' demands. 

(I'm assuming Gnome and Ubuntu are being done for others and they're not following a "scratch your own itch" model, but I might be wrong.)

---

### Post by hanzomon4 on 2008-07-22
They don't care, unless you praise them... it's not like they're trying to get your cash.

---

### Post by sicofante on 2008-07-22
> **hanzomon4 said:**
> They don't care, unless you praise them... it's not like they're trying to get your cash.
They do care I hope, and they certainly should. Mark Shuttleworth is indeed trying to get my cash.

---

### Post by Wolki on 2008-07-22
> **sicofante said:**
> Evolution does not use the Keyring. That alone is probably an indication that Keyring is the poor child in Gnome, and I'm suggesting it shouldn't be.

Are you sure it doesn't? My keyring contains my email account information and claims it was put there by evolution.

---

