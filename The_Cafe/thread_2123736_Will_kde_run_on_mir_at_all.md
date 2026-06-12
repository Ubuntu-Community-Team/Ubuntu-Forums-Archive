---
title: "Will kde run on mir at all?"
date: 2013-03-08
forum: The Cafe
---

### Post by ELD on 2013-03-08
I hate to link phoronix but - [http://www.phoronix.com/scan.php?page=news_item&px=MTMyMjM](http://www.phoronix.com/scan.php?page=news_item&px=MTMyMjM)

So can we count kde out from when ubuntu uses Mir?

I don't really get much about what is going on. Seems canonical has just annoyed a lot of people over Mir, personally IDC what display server Ubuntu runs as long as it's open source and works well.

---

### Post by tartalo on 2013-03-09
One can only speculate because Mir is not much more than a list of wishes right now, but:

- KDE could be used with another Window Manager. This doesn't make much sense to me, but it is possible in theory.
- Kwin could run on top of XMir, the X compatibility layer Mir would provide (Essentially XWayland renamed).
- Kubuntu could use X or Wayland instead or Mir. For example Linux Mint devs have already announced that they don't plan to use Mir.

> Seems canonical has just annoyed a lot of people over Mir
Yes, not a good thing.

---

### Post by dino99 on 2013-03-09
its a bit too early to know if or if not something be supported/ported on, as meanly everybody right now have his nerves broken. Let see what will happen in the coming weeks.
[http://blog.martin-graesslin.com/blog/2013/03/reply-to-all-the-faces-of-ubuntu/](http://blog.martin-graesslin.com/blog/2013/03/reply-to-all-the-faces-of-ubuntu/)

---

### Post by Sef on 2013-03-09
Moved to the Cafe.

---

### Post by grahammechanical on 2013-03-09
It is this kind of thing that we are here to test. Each of us may have his own choice of user interface but as testers we test. All the devs have to do is ask. And we can give answers from real life installations and the perspective of real life users.

---

### Post by dino99 on 2013-03-09
dont hurry, there is nothing to test right now

---

### Post by MadmanRB on 2013-03-09
Well considering KDE does moist of its own thing anyway, I say this will not my decision to stick with KDE.

---

### Post by ELD on 2013-03-09
Well I use Cinnamon anyway and will probably switch to Linux Mint at some point in the future since i don't want or need Unity on my PC. Was just curious.

---

### Post by JDShu on 2013-03-09
The KDE maintainer[ has said that he will veto any patches relating to supporting Mir]("http://blog.martin-graesslin.com/blog/2013/03/war-is-peace/") for KDE. In order for KDE to run on Mir, Canonical and Ubuntu contributors will have to actively maintain a patch set for Ubuntu. However if another distribution besides Ubuntu decides to use Mir, then they will probably change their minds. Personally, I doubt that will happen.

---

### Post by ELD on 2013-03-09
> **JDShu said:**
> The KDE maintainer[ has said that he will veto any patches relating to supporting Mir]("http://blog.martin-graesslin.com/blog/2013/03/war-is-peace/") for KDE. In order for KDE to run on Mir, Canonical and Ubuntu contributors will have to actively maintain a patch set for Ubuntu. However if another distribution besides Ubuntu decides to use Mir, then they will probably change their minds. Personally, I doubt that will happen.

That's so pathetic and has just made my thoughts of KDE go down hill.

---

### Post by JDShu on 2013-03-09
> **ELD said:**
> That's so pathetic and has just made my thoughts of KDE go down hill.

Seems reasonable to me actually. Why should they spend time and effort maintaining support for one distribution? If two distributions decide to use Mir, then it makes sense to merge it upstream so that work isn't duplicated, but when only one distribution uses it, then they can do it themselves.

---

### Post by tartalo on 2013-03-09
> **ELD said:**
> That's so pathetic and has just made my thoughts of KDE go down hill.

Why? No project would go out of it's way because a single downstream has it's own plans. While the whole Linux ecosystem has been discussing Wayland, Canonical is going its own way without counting on anyone else, even some Ubuntu Community members are angry with the way Canonical is behaving lately, why should KDE developers patch their software to accommodate Mir?

---

### Post by llanitedave on 2013-03-09
The reason it's pathetic is because the wiser choice would simply be to withold judgement until it becomes clear whether Mir or Wayland is the superior system.  Why not let them pass and fail on relative merit?  If Mir turns out to be simpler and more flexible and usable on more platforms, why *wouldn't* it be supported?  If it crashes and burns, then it's ok to reject it.

This naysaying in advance just strikes me as childish.

---

### Post by ELD on 2013-03-09
It's a given fact that Ubuntu is the most popular Desktop distro, they (KDE) could potentially lose out on a lot of users couldn't they?

I am looking at this from a user perspective only it just seems pathetic. It just seems very unfriendly of KDE and quite childlike of that person to not accept patches.

I fail to see how accepting patches is going out of their way.

> **llanitedave said:**
> The reason it's pathetic is because the  wiser choice would simply be to withold judgement until it becomes clear  whether Mir or Wayland is the superior system.  Why not let them pass  and fail on relative merit?  If Mir turns out to be simpler and more  flexible and usable on more platforms, why *wouldn't* it be supported?  If it crashes and burns, then it's ok to reject it.

This naysaying in advance just strikes me as childish.

This +99999999.

It's very schoolyard stuf "oh no he's gone off without us, let's not let him back in!!".

---

### Post by JDShu on 2013-03-09
> **llanitedave said:**
> The reason it's pathetic is because the wiser choice would simply be to withold judgement until it becomes clear whether Mir or Wayland is the superior system.  Why not let them pass and fail on relative merit?  If Mir turns out to be simpler and more flexible and usable on more platforms, why *wouldn't* it be supported?  If it crashes and burns, then it's ok to reject it.

But he *is* withholding judgement. He says that if another distribution uses Mir then they will revisit the problem. If Mir turns out to be technically better than Wayland then I'm sure other distributions will adopt it. That all seems very reasonable to me.


> **ELD said:**
> It's a given fact that Ubuntu is the most popular  Desktop distro, they (KDE) could potentially lose out on a lot of users  couldn't they?

I am looking at this from a user perspective only it just seems  pathetic. It just seems very unfriendly of KDE and quite childlike of  that person to not accept patches.

I fail to see how accepting patches is going out of their way.


Accepting patches means accepting stewardship of the  code and maintaining it even as downstream changes, which requires time and effort, so yes it is  going out of their way.

---

### Post by Paqman on 2013-03-09
> **tartalo said:**
> While the whole Linux ecosystem has been discussing Wayland, Canonical is going its own way

Not really. Chrome OS doesn't use Wayland, Android doesn't use Wayland. Canonical talked about using Wayland, but have come to the same conclusion as Google that the best alternative to X is a new display server. If you take Google, Ubuntu and servers out of the "Linux ecosystem" you're not left with a great deal. So Wayland doesn't look like it'll ever be deployed very widely.

---

### Post by JDShu on 2013-03-09
> **Paqman said:**
> Not really. Chrome OS doesn't use Wayland, Android doesn't use Wayland. Canonical talked about using Wayland, but have come to the same conclusion as Google that the best alternative to X is a new display server. If you take Google, Ubuntu and servers out of the "Linux ecosystem" you're not left with a great deal. So Wayland doesn't look like it'll ever be deployed very widely.

Two things. Google is not part of the "Linux ecosystem".  They're well known for going their own way and causing problems for people in the community - see Chrome/Chromium which causes packaging problems. It works out fine for them because Google is a massive corporation with proven revenue stream and ridiculously smart engineers. That's why they can pull off things like Android and ChromeOS and reinvent the wheel a couple times.  This brings us to my second point: Canonical is not Google. Canonical is not provably profitable and their engineers are no better than the X devs (and from what we know, certainly worse when it comes to display servers). And display servers are a very hard problem, which is why we only have one that is currently in widespread use. Frankly, nobody with any technical knowledge thinks they can pull this off.

What has struck me about this debate is that there has been a  clear divide between people with some technical background and people  who don't (plus Canonical). Anybody who knows anything about software  development and the current state of FOSS can see why Mir is a bad idea  and have given reasons for why. Defenders of Mir simply fall  back on the idea that "Canonical can do whatever it wants" which nobody  disputes, "Everybody else is just bitter" which is not a technical  argument, and "Let's wait and see how Mir develops" while ignoring our  reasons for why we think Canonical has set itself up for failure.

---

### Post by Paqman on 2013-03-09
> **JDShu said:**
> Two things. Google is not part of the "Linux ecosystem".

Says who? They contribute a lot of code to Linux, sponsor lots of outside development, own the overwhelmingly dominant Linux distro in the mobile space, have released a desktop Linux distro, and use Linux very extensively. What more would they have to do for you to consider them part of the club? Change their logo to a penguin?

> Canonical is not Google.

Agreed. They may be smaller fry overall, but in the small pond of desktop Linux they're a pretty big fish.

> 
Anybody who knows anything about software  development and the current state of FOSS can see why Mir is a bad idea

Not "anybody". Are Canonical's leadership not included in those who "know anything about software development"? Is Mark Shuttleworth? How do you know they haven't researched and prototyped this to the point where they've decided it's feasible? I doubt the decision to abandon Wayland and start afresh was taken lightly, and I'm sure they're well aware that they've got a huge mountain to climb.

Maybe they're wrong to do so, maybe Mir will indeed fall on its face, but writing a project off before you've seen the output from it simply because the task is difficult is premature and defeatist.

Since you can't change what they're going to do, what's the point in complaining about it anyway?

---

### Post by JDShu on 2013-03-09
> **Paqman said:**
> Says who? They contribute a lot of code to Linux, sponsor lots of outside development, own the overwhelmingly dominant Linux distro in the mobile space, have released a desktop Linux distro, and use Linux very extensively. What more would they have to do for you to consider them part of the club? Change their logo to a penguin?


I think I'll just give you this  because arguing the semantics of the "Linux Ecosystem" is pointless. The fact that Canonical is not Google is more important.

> 
Agreed. They may be smaller fry overall, but in the small pond of desktop Linux they're a pretty big fish.


Their relative size doesn't matter, the point is that it's extremely unlikely they'll pull a big project like Mir off.

> 
Not "anybody". Are Canonical's leadership not included in those who "know anything about software development"? Is Mark Shuttleworth? How do you know they haven't researched and prototyped this to the point where they've decided it's feasible? I doubt the decision to abandon Wayland and start afresh was taken lightly, and I'm sure they're well aware that they've got a huge mountain to climb.

Maybe they're wrong to do so, maybe Mir will indeed fall on its face, but writing a project off before you've seen the output from it simply because the task is difficult is premature and defeatist.


HAHAHA this is an easy one. You haven't done a lot of research into this have you?

Ok, to be fair I should have said "Nobody with any technical knowledge who is not from Canonical". But I thought that went without saying.

On to the real substance. The reasons they gave on their wiki for not using Wayland were actually incorrect. The wayland devs called them out on it and they apologized and edited the wiki. Perhaps they put a lot of thought into abandoning wayland, but none of that was technical. The reason for Mir is certainly political. It's about Canonical's need to control everything on Ubuntu. That's valid and I don't personally blame them for it. However the fact that they couldn't even get a basic understanding of Wayland right makes it quite clear that they don't know what they're doing on the technical front.

Do you think a group of people who can't even properly evaluate existing solutions could actually implement their own? In one year?

> 
Since you can't change what they're going to do, what's the point in complaining about it anyway?

I'm not complaining, I'm saying they're going to fail. How badly they'll fail is an open question. That said, I can see why some people are angry, Canonical has acted very badly (well, worse than usual) this time around.

EDIT: Oh, and I'm explaining why the KDE devs are free to not include Mir patches upstream. The way I see it, it's Ubuntu fans who are complaining.

---

### Post by Paqman on 2013-03-09
> **JDShu said:**
> The reasons they gave on their wiki for not using Wayland were actually incorrect.

I was aware of that. However, I'm also wary of taking any he-said she-said back-and-forth in the FOSS blogosphere at face value when we're in the middle of another "drama". The real story tends to come out somewhat down the track once heads have cooled in my experience.

> 
Do you think a group of people who can't even properly evaluate existing solutions could actually implement their own. In one year?


Well if you think they made the decision for non-technical reasons then it shouldn't have any bearing on their ability to produce code.

> 
Canonical has acted very badly (well, worse than usual) this time around.


I'm really not seeing that. What exactly have they done wrong? They don't have to use or support Wayland. Nobody does.

---

### Post by JDShu on 2013-03-09
> **Paqman said:**
> I was aware of that. However, I'm also wary of taking any he-said she-said back-and-forth in the FOSS blogosphere at face value when we're in the middle of another "drama". The real story tends to come out somewhat down the track once heads have cooled in my experience.


What do you mean by real story? Either something is wrong, or something is right. There's no grey area when it comes to the functionality of Wayland. We're discussing computer programs, not philosophy. In this case Canonical wrote something on the wiki justifying Mir which was *wrong.* I'm not sure what kind of "real story" could come out to make that seem ok.

> 
Well if you think they made the decision for non-technical reasons then it should have any bearing on their ability to produce code.


Not sure what you're saying here. My point was that they clearly don't know what they're doing.

> 
I'm really not seeing that. What exactly have they done wrong? They don't have to use or support Wayland. Nobody does.

They said they would support Wayland a few years ago. Developed something else in-house for nine months without telling anybody. Made no effort to contact Wayland developers. Came out with Mir and worst of all spread FUD on their wiki. I'd say that is pretty bad.

---

### Post by Paqman on 2013-03-09
> **JDShu said:**
> Either something is wrong, or something is right.


Not when you're dealing with people. This is all about what people have said and done and why they've done it. There may also be factors behind Canonical's decision that we're not privy to, such as other projects that are still under wraps, or commercial negotiations/deals, etc. Who knows? Besides, these kind of FOSS spats tend to be characterised by a lot of high emotion, and people say things they might later regret.

> 
Not sure what you're saying here. My point was that they clearly don't know what they're doing.


They seem to have managed to bumble through most of the time. They run the most popular Linux distro, and get a release out the door twice a year. They can't be too useless.

> 
They said they would support Wayland a few years ago. 


Yep, then changed their mind. They're allowed.

> Developed something else in-house for nine months without telling anybody.

So? That's how they develop a lot of stuff.

> 
Made no effort to contact Wayland developers.


The Wayland devs knew Canonical were reviewing their support of Wayland, then they announced they'd decided to drop it. From the sound of it there wasn't really any close ongoing relationship between the two anyway.

> 
Came out with Mir


Yes, damn those people who develop new open source software!

> 
and worst of all spread FUD on their wiki.


FUD is a bit of an emotive term, it implies their intention was to somehow undermine Wayland. I don't think there's any suggestion of that.

I think this whole thing (yet another) massive storm in a teacup. People always wail an gnash their teeth about any change to Ubuntu, whether it's buttons on the left, dropping GIMP from the ISO or developing a new shell for Gnome, but none of it has actually led to the sky falling. I'm not saying Canonical are in any way infallible, but the regular doom-laden predictions of their detractors don't seem to be playing out either.

FWIW I do think trying to develop Mir is incredibly risky, but then so is the whole convergence project, of which a replacement for X is a key component. Canonical only have a limited amount of time to make Ubuntu profitable before they have to shut up shop, and it does feel like they're probably into borrowed time. This stage of the game was always going to be make or break. I think in five years time Ubuntu will have either made significant inroads into the home computing market or else Canonical will have gone bust and Ubuntu will be a fading star community project under the Ubuntu Foundation.

---

### Post by JDShu on 2013-03-09
> **Paqman said:**
> Not when you're dealing with people. This is all about what people have said and done and why they've done it. There may also be factors behind Canonical's decision that we're not privy to, such as other projects that are still under wraps, or commercial negotiations/deals, etc. Who knows? Besides, these kind of FOSS spats tend to be characterised by a lot of high emotion, and people say things they might later regret.


Canonical made a false claim. They made incorrect statements about the functionalitiy of Wayland. Are you denying this? Whatever "factors behind Canonical's decision that we're not privy to" there is, the fact is that they made incorrect statements and publicly posted them. I'm not talking about people here - come on are you just being purposely dense? The context is what Wayland can do. It can either do something, or it can't do something. I'll be even more specific: Canonical claimed that "Wayland input had all of X's security problems". Either Wayland has all of X's security problems, or it doesn't. 

> 
They seem to have managed to bumble through most of the time. They run the most popular Linux distro, and get a release out the door twice a year. They can't be too useless.


For how much longer I wonder.

> 
Yep, then changed their mind. They're allowed.


They're allowed, sure. But they gave no warning. Doing something you're allowed to do to the detriment of other people is called being a jerk. In this case the detriment is that everybody was expecting eventual Wayland adoption by all the distros, and then Canonical suddenly throws a wrench in the plans.

> 
So? That's how they develop a lot of stuff.


Yeah, and it sucks. In fact the stuff they develop tends to be pretty bad. That's another reason why many of us have no faith in them.

> 
The Wayland devs knew Canonical were reviewing their support of Wayland, then they announced they'd decided to drop it. From the sound of it there wasn't really any close ongoing relationship between the two anyway.


Canonical made incorrect claims about Wayland when they could have simply asked. It really doesn't sound like Canonical made an honest effort to review Wayland.

> 
Yes, damn those people who develop new open source software!


That is highly likely to cause fragmentation.

> 
FUD is a bit of an emotive term, it implies their intention was to somehow undermine Wayland. I don't think there's any suggestion of that.


It literally stands for fear, uncertainty, and doubt. When you say that Wayland has input security problems, you are spreading FUD, and whether intentional or not, it's bad behavior.

> 
I think this whole thing (yet another) massive storm in a teacup. People always wail an gnash their teeth about any change to Ubuntu, whether it's buttons on the left, dropping GIMP from the ISO or developing a new shell for Gnome, but none of it has actually led to the sky falling. I'm not saying Canonical are in any way infallible, but the regular doom-laden predictions of their detractors don't seem to be playing out either.


And I think Canonical has finally jumped the shark. Perhaps the sky hasn't fallen from any of the individual points stated above but the foundations appear to be crumbling.

> 
FWIW I do think trying to develop Mir is incredibly risky, but then so is the whole convergence project, of which a replacement for X is a key component. Canonical only have a limited amount of time to make Ubuntu profitable before they have to shut up shop, and it does feel like they're probably into borrowed time. This stage of the game was always going to be make or break. I think in five years time Ubuntu will have either made significant inroads into the home computing market or else Canonical will have gone bust and Ubuntu will be a fading star community project under the Ubuntu Foundation.

I agree, although I don't think replacing X is as important as Canonical claims. More importantly, I don't see why Canonical couldn't simply fork Wayland. That way they would both have control and avoid reinventing wheels. Still, as long as Mark Shuttleworth has money, I expect Canonical to keep hobbling along, making grand promise after grand promise.

---

### Post by fontis on 2013-03-10
I dont understand what the problem is.
I think it's a great idea that Canonical strives to get their hands dirty. If anything, it's about time. Too much of what they envision for Ubuntu is currently in conflict with what is readily available in terms of software. Putting out their own WM would serve their own needs far better than anything else out there at the moment. And it's fairly obvious to everyone apparently that X just isn't enough for the next step.

So why not? I'd rather have Canonical put in 100% effort into their vision and get it right (or fail trying to) rather than to just stick to whatever is out there and continue to fail getting anywhere.

---

### Post by tartalo on 2013-03-10
> **Paqman said:**
> What exactly have they [Canonical] done wrong? They don't have to use or support Wayland. Nobody does.

Well, this thread heated when someone said that KDE developers where doing something wrong about Mir, so I guess we have reached a point of agreement.

By the way Paqman, has Google said something about adopting Mir? That would be really interesting plot twist, but on the meantime Mir is what it is [https://launchpad.net/mir](https://launchpad.net/mir) No more, no less.

---

### Post by tartalo on 2013-03-10
> **fontis said:**
> And it's fairly obvious to everyone apparently that X just isn't enough for the next step.

Not to everyone, there are quite a few that don't think that replacing X is a good idea at all. And in my opinion they are gaining points lately.

---

### Post by Dry Lips on 2013-03-10
I think there's a good point made in this article:[B]


Wayland Still Working On Minimizing, Maximizing[/B]

*[COLOR=#000000][FONT=verdana]"Support for minimize and maximize requests is still being worked on the for the Wayland protocol. Yes, this is to allow windows to be minimized or maximized within the Wayland environment. [...] [/FONT][/COLOR]This work will likely be integrated in time for the next release of Wayland and the reference Weston compositor. This shows how long it takes to design and implement well a full-featured modern display server, with Wayland having been developed for about five years now while Canonical hopes Mir will be ready by later in the year and ready for all form-factors by next April."*

source:
[http://www.phoronix.com/scan.php?page=news_item&px=MTMyMjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTMyMjQ)

---

### Post by Roasted on 2013-03-10
While I don't fault Ubuntu for going with Mir, I do fault them for the false claims they made against Wayland. Very, very poor job fellas. I've been a life long Ubuntu fan and even I was the first to say that out loud. That said, it's given me some considerable thought to try out other desktop environments. Ironically, I ended up on Kubuntu with KDE. To say I'm happier here is an understatement. I don't care what KDE uses, but I do support KDE with whatever they use just as much as I support Ubuntu/Canonical with whatever they use. It's just the false claims that were made that really, really disappointed me. I don't blame KDE in the slightest for showing disinterest with Mir. Canonical has to understand that they cannot brew up a DS and assume the rest of the world will be anxious to follow and help out. They haven't exactly held the best reputation in the OSS community to attract such behavior from developers of other camps. I hope to see it land and succeed 100 times over again, but I also do believe they're a bit in over their heads, at least based on what I know with Wayland and what kind of development has gone into it already. It'll undoubtedly be interesting to see how it goes though, but part of me thinks the final revision that we see next year will just be a half baked spin off... sort of like Ubuntu Touch running on Cyanogenmod. But in the name of open source software, I'm anxious to see what happens, and I hope it flies.

---

### Post by ELD on 2013-03-10
Well as with everything I will wait patiently and see what happens since I don't understand a lot of it. I just hope it all works out for the better for the users and not for Canonicals personal business gains.

---

### Post by Paqman on 2013-03-10
> **JDShu said:**
> Canonical made a false claim. They made incorrect statements about the functionalitiy of Wayland. Are you denying this?

No, but frankly who cares? Unless you're involved with either Wayland or Ubuntu then it's someone else's argument. I don't really see why us bystanders need to get emotionally invested in it.

> They're allowed, sure. But they gave no warning.

Yes they did. Jono Bacon said in an interview to OMGubuntu that Wayland didn't suit their needs back in Jan.

> It really doesn't sound like Canonical made an honest effort to review Wayland.

You don't really know that.

> It literally stands for fear, uncertainty, and doubt. When you say that Wayland has input security problems, you are spreading FUD, and whether intentional or not, it's bad behavior.

FUD is a technique for smearing competing products in the media. Simply stating what you think something flaws are isn't FUD, even if you're wrong. It would be FUD if they were doing so with the intention to undermine support for Wayland, but that's not the case here.

---

### Post by Larkspur on 2013-03-10
> **JDShu said:**
> It literally stands for fear, uncertainty, and doubt. When you say that Wayland has input security problems, you are spreading FUD, and whether intentional or not, it's bad behavior

I guess that wiki is suggesting that Wayland hasn't resolved the issue X has concerning isolation of applications and inputs (e.g. if a hacker were able to run xinput on a target computer, they would effectively have a keylogger for all applications (and password prompts) running on that instance of X).

---

### Post by mips on 2013-03-10
> **ELD said:**
> It's a given fact that Ubuntu is the most popular Desktop distro, they (KDE) could potentially lose out on a lot of users couldn't they?

I am looking at this from a user perspective only it just seems pathetic. It just seems very unfriendly of KDE and quite childlike of that person to not accept patches.


Ubuntu is not Kubuntu. How many Kubuntu users are there compared to all the other KDE distros combined?

I don't think KDE is being childlike at all, just practical.

---

### Post by tartalo on 2013-03-10
> **mips said:**
> Ubuntu is not Kubuntu. How many Kubuntu users are there compared to all the other KDE distros combined?
And unless Mir becomes mandatory in _buntu for technical or political reasons, or Ubuntu becomes fully independent from Debian and the Universe repository disappears, Kubuntu will have the possibility to use X or Wayland or whatever Debian uses instead.

We could be discussing a non-issue.

---

### Post by JDShu on 2013-03-10
> **Paqman said:**
> No, but frankly who cares? Unless you're involved with either Wayland or Ubuntu then it's someone else's argument. I don't really see why us bystanders need to get emotionally invested in it.


I think if a company turns out to be either technically incompetent or malicious then it makes sense to care. Anyway, people can get emotionally invested in whatever they want. Acting like they have no reason to seems sanctimonious.

> 
Yes they did. Jono Bacon said in an interview to OMGubuntu that Wayland didn't suit their needs back in Jan.


And apparently they began six months prior to that. I personally thought they were joking when they said that they might roll their own.

> 
You don't really know that.


I know enough to know they didn't understand Wayland. Maybe they were just incompetent then.

> 
FUD is a technique for smearing competing products in the media. Simply stating what you think something flaws are isn't FUD, even if you're wrong. It would be FUD if they were doing so with the intention to undermine support for Wayland, but that's not the case here.

They clearly had the intention to undermine the legitimacy of Wayland however in order to justify starting Mir. The point is that if the Wayland devs hadn't made a big stink of it, users would have thought that Wayland was insecure and couldn't do many things which it could.

---

### Post by Paddy Landau on 2013-03-11
> **ELD said:**
> I just hope it all works out for the better for the users and not for Canonicals personal business gains.
I hope it works out for the better for the users **and** for Canonical's business gains. If Canonical goes bust, Ubuntu fails.

Whether or not you like Ubuntu, it is helping to bring a strong competitor to the Android-iOS-Windows environment. It is also the first OS to bring true unification between devices, which should spur competition further.

---

### Post by ZarathustraDK on 2013-03-11
> **tartalo said:**
> Why? No project would go out of it's way because a single downstream has it's own plans. While the whole Linux ecosystem has been discussing Wayland, Canonical is going its own way without counting on anyone else, even some Ubuntu Community members are angry with the way Canonical is behaving lately, why should KDE developers patch their software to accommodate Mir?

The crux of the argument is not about KDE going out of their way to patch their software to be compatible, it's about someone else coming up with a patch (doing the work for them) and then have them refuse to include it because of the Wayland/Mir-debacle.

I'd call that pathetic. Sure, if there's a technical reason why it shouldn't be included, fine; but hamstringing development because the contributor doesn't like your favorite band is childish IMO.

---

### Post by ELD on 2013-03-11
> **Paddy Landau said:**
> I hope it works out for the better for the users **and** for Canonical's business gains. If Canonical goes bust, Ubuntu fails.

Whether or not you like Ubuntu, it is helping to bring a strong competitor to the Android-iOS-Windows environment. It is also the first OS to bring true unification between devices, which should spur competition further.

Very true I wouldn't like to see Ubuntu fail since it's already given me so much.

Thinking on it, unless they remove X from the repo's it shouldn't be too much of an issue since you could install X and a different desktop, like me for example i use Ubuntu + Cinnamon and don't really plan on changing so for me I guess it would still all work out okay unless nvidia suddenly removed X support in favour of Mir (unlikely).

---

### Post by tartalo on 2013-03-11
> **ZarathustraDK said:**
> The crux of the argument is not about KDE going out of their way to patch their software to be compatible, it's about someone else coming up with a patch (doing the work for them) and then have them refuse to include it because of the Wayland/Mir-debacle.

I'd call that pathetic. Sure, if there's a technical reason why it shouldn't be included, fine; but hamstringing development because the contributor doesn't like your favorite band is childish IMO.

I fail to see the problem with "downstream specific patches should be applied downstream" policy.

---

### Post by ZarathustraDK on 2013-03-11
> **tartalo said:**
> I fail to see the problem with "downstream specific patches should be applied downstream" policy.

As long as upstream keeps its doors open if Mir goes mainstream, I don't have a problem either. Putting down a veto, though, communicates an unwarranted discriminatory stance on the project. As in "never gonna happen".

I guess it's a word-thing...

---

### Post by mr john on 2013-03-11
And here we have the biggest problem with Linux... Fragmentation,  clashing egos and a clear lack of leadership because everyone wants to be leader. It's pathetic. This is why Desktop Linux is such a mess. The product? A bunch of mediocre distros that are cobbled together in a disorganised manner. And everyone refusing to work together. This is why we're constantly playing catchup with organised companies.

---

### Post by ELD on 2013-03-11
> **mr john said:**
> And here we have the biggest problem with Linux... Fragmentation,  clashing egos and a clear lack of leadership because everyone wants to be leader. It's pathetic. This is why Desktop Linux is such a mess. The product? A bunch of mediocre distros that are cobbled together in a disorganised manner. And everyone refusing to work together. This is why we're constantly playing catchup with organised companies.

Indeed but then if we had clear leadership, clear this, clear this...there would only be one distro, that's the point of all the distro's everyone has slightly different views?

---

### Post by tartalo on 2013-03-11
> **ZarathustraDK said:**
> As long as upstream keeps its doors open if Mir goes mainstream, I don't have a problem either. Putting down a veto, though, communicates an unwarranted discriminatory stance on the project. As in "never gonna happen".

I guess it's a word-thing...

I guess, read the last two articles in Martin's blog and make your own conclusions:
[http://blog.martin-graesslin.com](http://blog.martin-graesslin.com)

The whole blog is very interesting for anyone curious about software development, for example this article from September about Wayland shows a way of doing things that, if I understand it correctly, would ease the inclusion of Mir when it gets adopted by more distributions:

[http://blog.martin-graesslin.com/blog/2012/09/a-real-update-on-the-progress-of-wayland-in-kwin-and-kde/](http://blog.martin-graesslin.com/blog/2012/09/a-real-update-on-the-progress-of-wayland-in-kwin-and-kde/)

Considering how versatile is KDE and how much is improving lately in performance and stability without sacrificing features makes me think that the project is in good hands.

---

### Post by mr john on 2013-03-11
> [COLOR=#000000]that's the point of all the distro's everyone has slightly different views?[/COLOR]

And that's why everything has been cobbled together in a disorganised an messy fashion. People go in a hissy fit if they don't get their way instead of learning to work together. Everyone wants to be leader, but no single entity has the resources to create a good product.

---

### Post by tartalo on 2013-03-11
Oh look! This is relevant to the thread:
[https://plus.google.com/113883146362955330174/posts/P4GFie3VoD8](https://plus.google.com/113883146362955330174/posts/P4GFie3VoD8)
EDIT: Interesting how KDE developer Aaron Seigo corrects yet another misunderstanding.

---

### Post by ZarathustraDK on 2013-03-11
> **tartalo said:**
> Oh look! This is relevant to the thread:
[https://plus.google.com/113883146362955330174/posts/P4GFie3VoD8](https://plus.google.com/113883146362955330174/posts/P4GFie3VoD8)
EDIT: Interesting how KDE developer Aaron Seigo corrects yet another misunderstanding.

10/10 for correcting, 4/10 for style :) I can understand the frustration and how it annoys him, but stoking the flames about some underlying anti-wayland conspiracy by the Mir-guys isn't really a constructive way to go about it. Do not attribute to malice that which can be explained by ignorance. :)

---

### Post by tartalo on 2013-03-11
> **ZarathustraDK said:**
> but stoking the flames about some underlying anti-wayland conspiracy by the Mir-guys isn't really a constructive way to go about it.

Where does he say anything like that? Did you read the same thread I read?

---

### Post by ZarathustraDK on 2013-03-11
> **tartalo said:**
> Where does he say anything like that? Did you read the same thread I read?

It's all cloak'n'daggers paranoia :) He isn't saying it per se, but we all know what people will take with them when they read:

> This is not the first time in all this that someone affiliated with Mir has publicly opined on the future of KDE's workspace efforts vis-v-vis Mir or Wayland, and I would like to ask you to stop doing that.

It's disrespectful on the one hand, and makes our job of communicating clearly with our users and partners more difficult as the conflicting information increases.

Again, I'm not saying it didn't happen, that he's wrong, or that he's consciously trying to incite anything; but let it boil for a couple of days and then the above will become something along the lines of "Canonical sabotaging Wayland" in the eyes of the community hivemind.

Sooo...I guess it's not really "stoking the flames" as much as it's "leaving that gasoline-can a bit close to the fire", hence the 4/10 for style :)

---

