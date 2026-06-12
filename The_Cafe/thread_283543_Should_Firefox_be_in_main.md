---
title: "Should Firefox be in main?"
date: 2006-10-24
forum: The Cafe
---

### Post by bruce89 on 2006-10-24
I was looking at the [ubuntu components]("http://www.ubuntu.com/ubuntu/components") page, and I thought that the new package of Firefox might conflict with the definition of main.  For instance take this line:
> The main distribution component contains applications that are free software, can freely be redistributed and are fully supported
You could argue that Ubuntu's new "official" package of Firefox is not free software, as it doesn't allow modification under the same name.

I propose that Firefox should be moved to restricted.
Discuss.

---

### Post by mmcmonster on 2006-10-24
Eeekkksss!!!

[Oh no.  Not again!]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354622")

Technically, you are absolutely correct.  Ubuntu is apparently distributing a version of firefox that is not sanctioned by mozilla.com, and can therefore bite us in the future.  The only truley correct thing for Ubuntu (or mozilla.com, I suppose) to do is to repackage the firefox source with a "generic" name, such as "Internet browser" or some such, so that anyone can redistribute with that name.

---

### Post by dom02 on 2006-10-24
> **mmcmonster said:**
> Eeekkksss!!!

[Oh no.  Not again!]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354622")

Technically, you are absolutely correct.  Ubuntu is apparently distributing a version of firefox that is not sanctioned by mozilla.com, and can therefore bite us in the future.  The only truley correct thing for Ubuntu (or mozilla.com, I suppose) to do is to repackage the firefox source with a "generic" name, such as "Internet browser" or some such, so that anyone can redistribute with that name.

no I don't think that's a problem.  I think Ubuntu worked things out with mozilla, which is why we now have the official firefox icon.  The problem that he's talking about is that it makes it so that it can't be freely modified and distributed.  Ubuntu seems to have permission to use the firefox name and logo with their version but if I edited the Ubuntu version and posted it I couldn't call it firefox anymore.

---

### Post by bruce89 on 2006-10-24
> **dom02 said:**
> no I don't think that's a problem.  I think Ubuntu worked things out with mozilla, which is why we now have the official firefox icon.  The problem that he's talking about is that it makes it so that it can't be freely modified and distributed.  Ubuntu seems to have permission to use the firefox name and logo with their version but if I edited the Ubuntu version and posted it I couldn't call it firefox anymore.

That's exactly what I mean.

I am not the only one wary of Mozilla now - ["The Message: Practicality and Usability more important than Open Source"](http://blogs.gnome.org/view/bolsh/2006/10/24/0)

---

### Post by superm1 on 2006-10-24
> **dom02 said:**
> no I don't think that's a problem.  I think Ubuntu worked things out with mozilla, which is why we now have the official firefox icon.  The problem that he's talking about is that it makes it so that it can't be freely modified and distributed.  Ubuntu seems to have permission to use the firefox name and logo with their version but if I edited the Ubuntu version and posted it I couldn't call it firefox anymore.


It really isn't an issue that firefox can't be freely modified and distributed.  The whole issue at hand was that it could no longer be called firefox and be shippied with the official artwork if it was unless the changes were approved by mozilla.

---

### Post by bruce89 on 2006-10-24
I have filed a bug - [Firefox (for Edgy) should not be in main](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/68008)

---

### Post by givré on 2006-10-24
What's wrong with the icons ? (just a question, not a troll 8) )

---

### Post by bruce89 on 2006-10-24
> **givré said:**
> What's wrong with the icons ? (just a question, not a troll 8) )

The icons are not under a free licence, so they shouldn't be in main anyway.

My complaint is not about the icons (as such), it's just that things in main must be able to be modified, which Firefox (mostly) isn't, without Mozilla's permission.

I also don't like Mozilla's attitude of forgetting about its free software heritage.

---

### Post by shining on 2006-10-24
Indeed, firefox doesn't belong in main anymore.
And the dfsg in the name really should be removed.

> 
The restricted component is reserved for software that is very commonly used, and which is supported by the Ubuntu team even though it is not available under a completely free licence. Please note that it may not be possible to provide complete support for this software since we are unable to fix the software ourselves, but can only forward problem reports to the actual authors.


It seems to totally fit in the restricted section. It is very commonly used, but it isn't completely free. And it cannot be supported by ubuntu itself, but problems have to be forwarded to mozilla first.

> 
Some software from restricted will be installed on Ubuntu CDs but is clearly separated to ensure that it is easy to remove. We include this software because it is essential in order for Ubuntu to run on certain machines - typical examples are the binary drivers that some video card vendors publish, which are the only way for Ubuntu to run on those machines. By default, we will only use open source software unless there is simply no other way to install Ubuntu. The Ubuntu team works with such vendors to accelerate the open-sourcing of their software to ensure that as much software as possible is available under a Free licence.


Though, it doesn't fit with this second part of the description. It isn't essential for running ubuntu.

It seems like ubuntu has two conflicting goals. Being restrictive about free software and being user friendly IMHO don't go well together.
That's also why I think it's not bad to have both debian and ubuntu. Debian cares more about the first goal, and Ubuntu more about the second.
Though, I also believe it's important that both goals are kept in mind, but just that a preference is needed.
I think ubuntu did it quite well for wireless firmwares. I appreciate wireless working out of the box. But I also appreciate when it's made clear these are non free by putting them in restricted.
Same for firefox, I believe a distrib like ubuntu should keep providing it by default on the cd, but also make it clear what is special about it.

---

### Post by bruce89 on 2006-10-24
> **shining said:**
> > The restricted component is reserved for software that is very commonly used, and which is supported by the Ubuntu team even though it is not available under a completely free licence. Please note that it may not be possible to provide complete support for this software since we are unable to fix the software ourselves, but can only forward problem reports to the actual authors.

It seems to totally fit in the restricted section. It is very commonly used, but it isn't completely free. And it cannot be supported by ubuntu itself, but problems have to be forwarded to mozilla first.

I never considered that part, I might forward that arguement to the bug.

Sort of related, all discussion should be here, not on the bug.

In fact, this thread might be better in the cafe, as Edgy's forum will shut soon.

---

### Post by givré on 2006-10-24
> **bruce89 said:**
> The icons are not under a free licence, so they shouldn't be in main anyway.

My complaint is not about the icons (as such)
Ok, i thought it was that, the dfsg stuff is all about that.

---

### Post by neophyrigian on 2006-10-24
Hello Dear Friends,

Let's be serious and responsible: Are you trying to "punish" Firefox for it is not "free as desired to be" or am I getting it wrong? If this is the case, its childish. Firefox, with its whole body, is a free software. What's more, its one of the two battering rams of the Free Software front against the walls and gates of the proprietary dominance, opening the way for not only the GNU/Linux geeks but also for the masses -the other one being OpenOffice.org and the GIMP may be on the row. Up to my knowledge, Firefox -or Mozilla- is not waiting for medals for this tremendous effort and great victories they already had, but -if you ask for my feelings- they deserve a little bit more respect than trying to teach them such lessons.

Does the source codes of Firefox open? Yes, it is! Can anybody who likes to do so take those codes and change it, build something on it? Sure! Does the developer team of Firefox serve that software for the benefit of humankind without demanding any money? Absolutely, yes they do so!

So what is the problem?

Seems to be that: They want 3rd parties to use their original logo if its to be named Firefox! What a shame! What a big philosophical crime!

This is the point to be more serious, responsible and realistic: What Firefox demand is the most natural thing one can hear. Can you tell me why they shouldn't ask for it? Why are you insisting on to use Firefox without its original logo? Let's leave such hostile moves to the enemies of Free Software and let's all struggle against them, against such moves. Oh yes, its our right to use Firefox as a software but we shouldn't use Firefox's original logo because logo is not "bona fiscalia". Let me put it very openly: If they didn't protect their logo, I would blame them for not doing so. In the present conditions of the world and under the current system its much more better to protect the logo. Who knows and who guaranties us that no one will use that logo in clownish ways for the benefit of their wallets? Or who knows which clown will attempt to use Firefox with its original name and with any kind of humiliating logo?

The fact is: Firefox is here, not hidden from anybody. Source codes are there, open to anyone who like to do something with them and name it after whatever they like. That famous and lovely logo belongs to Firefox. If you want to distribute Firefox with that name, you should use that logo. If you don't want to use that logo, then don't use the software with Firefox name. What is the point ruining free software philosophy here, in concrete terms?

Also: Philosophical principles are not send from heavens. They are abstract but not "supernatural". They are closely linked with the material world, with the struggles going on that scene. If there exists a conflict with our Free Software principles and Firefox logo's legal protection -stressing that I don't think that there is such a conflict- then we should discuss about those principles not deal with excommunication of Firefox. Leaving assumptions aside, what we should do first is to understand the principles well.

Some days ago I've replied to the blog entry of a friend, stating that I would replace the blue world like sketch replaced with Firefox's original logo manually on my OS, namely Ubuntu. Thanks to the friends in charge of command, its as it should be at the moment. I want it to stay so.

In which repository Firefox should be? From what I wrote up to this point, you can guess my preference, but if one sentence has to be written: Childish "penalties" can not reverse the fact, but give harm to those who take such measures.

History will judge our position with respect to Firefox software of the beginning of 21st century, among other things, as well.

Regards,

K. Deniz Ogut

a.k.a.

neophyrigian

---

### Post by E-Jey on 2006-10-24
> **neophyrigian said:**
> Hello Dear Friends,

Let's be serious and responsible: Are you trying to "punish" Firefox for it is not "free as desired to be" or am I getting it wrong? If this is the case, its childish. Firefox, with its whole body, is a free software. What's more, its one of the two battering rams of the Free Software front against the walls and gates of the proprietary dominance, opening the way for not only the GNU/Linux geeks but also for the masses -the other one being OpenOffice.org and the GIMP may be on the row. Up to my knowledge, Firefox -or Mozilla- is not waiting for medals for this tremendous effort and great victories they already had, but -if you ask for my feelings- they deserve a little bit more respect than trying to teach them such lessons.

Does the source codes of Firefox open? Yes, it is! Can anybody who likes to do so take those codes and change it, build something on it? Sure! Does the developer team of Firefox serve that software for the benefit of humankind without demanding any money? Absolutely, yes they do so!

So what is the problem?

Seems to be that: They want 3rd parties to use their original logo if its to be named Firefox! What a shame! What a big philosophical crime!

This is the point to be more serious, responsible and realistic: What Firefox demand is the most natural thing one can hear. Can you tell me why they shouldn't ask for it? Why are you insisting on to use Firefox without its original logo? Let's leave such hostile moves to the enemies of Free Software and let's all struggle against them, against such moves. Oh yes, its our right to use Firefox as a software but we shouldn't use Firefox's original logo because logo is not "bona fiscalia". Let me put it very openly: If they didn't protect their logo, I would blame them for not doing so. In the present conditions of the world and under the current system its much more better to protect the logo. Who knows and who guaranties us that no one will use that logo in clownish ways for the benefit of their wallets? Or who knows which clown will attempt to use Firefox with its original name and with any kind of humiliating logo?

The fact is: Firefox is here, not hidden from anybody. Source codes are there, open to anyone who like to do something with them and name it after whatever they like. That famous and lovely logo belongs to Firefox. If you want to distribute Firefox with that name, you should use that logo. If you don't want to use that logo, then don't use the software with Firefox name. What is the point ruining free software philosophy here, in concrete terms?

Also: Philosophical principles are not send from heavens. They are abstract but not "supernatural". They are closely linked with the material world, with the struggles going on that scene. If there exists a conflict with our Free Software principles and Firefox logo's legal protection -stressing that I don't think that there is such a conflict- then we should discuss about those principles not deal with excommunication of Firefox. Leaving assumptions aside, what we should do first is to understand the principles well.

Some days ago I've replied to the blog entry of a friend, stating that I would replace the blue world like sketch replaced with Firefox's original logo manually on my OS, namely Ubuntu. Thanks to the friends in charge of command, its as it should be at the moment. I want it to stay so.

In which repository Firefox should be? From what I wrote up to this point, you can guess my preference, but if one sentence has to be written: Childish "penalties" can not reverse the fact, but give harm to those who take such measures.

History will judge our position with respect to Firefox software of the beginning of 21st century, among other things, as well.

Regards,

K. Deniz Ogut

a.k.a.

neophyrigian

I totally agree with you!! Mozilla has to protect the firefox logo and name. Otherwise people will make a version of firefox with spyware in it or something like that. 
I hope it's not possible to make a debian version with spyware in it and still can call it debian.

---

### Post by Colonel Kilkenny on 2006-10-24
Not again. If you really think that the logo was the biggest problem you should think again.

Maybe a clear message from Ubuntu devs would make the situation a bit clearer...

---

### Post by gunksta on 2006-10-24
At the risk of putting my nose where it doesn't belong, I don't think the OP ever said that Firefox shouldn't be distributed with Ubuntu. In fact, he points out how there are already things, like firmware drivers, that are in restricted AND distributed / used by Ubuntu by default. 

This is not an example of "childish penalties" this is a suggestion, that was brought up in an appropriate space and in a respectful manner. This is a suggestion to catalogue a piece of software in the repository where it may be more appropriate.

The OP never said FF shouldn't be the default browser. That is, after-all, a whole 'nother can of worms.

--andy

---

### Post by Wolki on 2006-10-24
> **E-Jey said:**
> I totally agree with you!! Mozilla has to protect the firefox logo and name. Otherwise people will make a version of firefox with spyware in it or something like that. 

'cause we all know criminals who force spyware on other people's computers respect trademarks.

Anyway, yes it's true that you have to defend your trademark to keep it. But it's not true that you have to
- force people who want to use your trademark to give control of their product over to you
- force people who want to use your trademark to distribute stuff under a copyright license that seems to be pretty draconian.

---

### Post by Toxicity999 on 2006-10-24
Also, take note of the 'About' Screen. No more Waterworld! =)

Personally... I love FF being branded correctly. I know it means nothing but I like showing people that many of the applications they use on Macs or Windows can be found carbon copied +50 on ubuntu. Of course... That's not really anything important. I love mozilla but that little mania fringe freaked me out a little. They have the project that got me into OSS I mean... thousands of people working on the code together for a common goal of omgwtfpwnage? That's pretty nice. I thought, looking back... it seems to be taking the same course as every other 'next big thing', slowly becoming what it is they fought, the big guy with a magnifying glass frying all the little ants (Microshizzle anyone?) Of course I by no means imply that is what they are now, just stating it could happen.

To the poster talking about their right to their intellectual property y'sure I totally agree. BUT, I rebut to you that what they were thinking is meerly standardization if one guy was pumping out Pr0nFox with an official logo, sure sue the Fox out of him. We're talking Ubuntu here, not some guy with a vendetta to be paid. There isn't enough room for love in these accusations they just blindly followed the law even though it's intent was to save users all they could of done is cause them grief, and save them from nothing... thanks Mozilla for causing alot of needless drama? We were just about to use that Waterworld logo to finish them off too... oh well.

Law is made to protect, when it's only used for the sake of being written, and not for it's actual intent it is futile to back it in the first place!

end rant

---

### Post by neophyrigian on 2006-10-24
Dear Friends,

Let's understand each other and then take any position we prefer. What I say is very obvious:

1- Firefox is totally a Free Software
2- If there's need to discuss about the logo protection, there's nothing which ruins the mentioned quality
3- If there is some other issue(s) let us know it; no need to refer to the discussions on some other bases, even some entries in this thread reminds us that the problem seems to be this
4- Firefox's demand for respect for their integrity is totally just
5- The original post of this thread quotes "The main distribution component contains applications that are free software, can freely be redistributed and are fully supported" and jumps to a conclusion that Firefox shouldn't be in the main repository because "Ubuntu's new 'official' package of Firefox is not free software, as it doesn't allow modification under the same name."
6- Referring to 1, 2 and 4; what claimed in 5 is not valid
7- Under these circumstances, placing Firefox to restricted repository (I don't know if there's such a plan, I didn't check the repositories, I'm discussing the principle at the moment based on the original proposal) will be a mistake, an unjust act. This is the objective description. Subjectively, I call it "a childish penalty".
8- If there's still need to write it: I want Firefox to appear in the most "main" and most "Libre" repository of Ubuntu because it doesn't fit well anywhere else.

Regards.

---

### Post by bruce89 on 2006-10-25
> **gunksta said:**
> The OP never said FF shouldn't be the default browser. That is, after-all, a whole 'nother can of worms.

Well I am an advocate of Epiphany as default actually, but that's unlikely to happen.

If Firefox is to remain as default (bad mistake)*, then it should be in restricted.

* I can give reasons on demand.

> **E-Jey said:**
> I totally agree with you!! Mozilla has to protect the firefox logo and name. Otherwise people will make a version of firefox with spyware in it or something like that. 
I hope it's not possible to make a debian version with spyware in it and still can call it debian.

So does GNOME, but have they told Ubuntu that they can't call their modified version of GNOME GNOME?  No they haven't.

> **neophyrigian said:**
> 1- Firefox is totally a Free Software

It depends on your definition of free.

> **neophyrigian said:**
> 4- Firefox's demand for respect for their integrity is totally just

The fact that nobody else has demanded this of distributors points to the fact that Mozilla are over-protective.  Consider a [google search for "firefox"]("http://www.google.co.uk/search?hl=en&q=firefox&btnG=Google+Search&meta=").  How many of these "sponsored links" adverts will be modified (possibly spyware) versions of Firefox?  Do they still call it Firefox?  Debian are a trusted distributor of software, why they should they be told they can't modify Firefox without changing the artwork/name, but these dodgy "sponsored links" get away with it.

> **neophyrigian said:**
> 5- The original post of this thread quotes "The main distribution component contains applications that are free software, can freely be redistributed and are fully supported" and jumps to a conclusion that Firefox shouldn't be in the main repository because "Ubuntu's new 'official' package of Firefox is not free software, as it doesn't allow modification under the same name."

That is essentially what I am saying.

> **neophyrigian said:**
> 7- Under these circumstances, placing Firefox to restricted repository (I don't know if there's such a plan, I didn't check the repositories, I'm discussing the principle at the moment based on the original proposal) will be a mistake, an unjust act. This is the objective description. Subjectively, I call it "a childish penalty".

I don't see why this would be the case.

---

### Post by chaosgeisterchen on 2006-10-25
I am of the opinion that we should rather use Ice Weasel than use Firefox just to save ourselves all those problems.

---

### Post by bruce89 on 2006-10-25
> **chaosgeisterchen said:**
> I am of the opinion that we should rather use Ice Weasel than use Firefox just to save ourselves all those problems.

Yes, I am all for that too.

---

### Post by givré on 2006-10-25
> **bruce89 said:**
> 
If Firefox is to remain as default (bad mistake)*, then it should be in restricted.

* I can give reasons on demand.

Please do.

Thanks

---

### Post by chaosgeisterchen on 2006-10-25
> **bruce89 said:**
> Yes, I am all for that too.

Is there already an Launchpad 'Bug' posted for suggesting IceWeasel to be used as primary browser? (Why on earth are they called bugs and not suggestions?)

Otherwise it would be a good idea to post one. We can talk long hours about this topic but we have to take action too.

---

### Post by givré on 2006-10-25
> **chaosgeisterchen said:**
>  (Why on earth are they called bugs and not suggestions?)

Because bugs could be wishes.

---

### Post by givré on 2006-10-25
> **chaosgeisterchen said:**
> 
Otherwise it would be a good idea to post one. We can talk long hours about this topic but we have to take action too.
"Actions" are already in the mailling list, but i don't see them moving yet.
Will see what's happens for edgy+1.

---

### Post by bruce89 on 2006-10-25
> **givré said:**
> Please do.

Thanks

[LIST]
[*]Firefox is not the GNOME default
[*]Mozilla don't release source tarballs of Firefox, distributors have to get it from CVS
[*]Firefox is slow GUI wise
[*]Mozilla are obsessed with brand, and not with making a better "product"
[*]Mozilla don't market Firefox as Open Source, even though it is
[*]Mozilla treat Linux as a second rate citizen, even though its origins are from it
[/LIST]


[LIST]
[*]Epiphany is the GNOME default
[*]Konqueror is the KDE default, and it is installed on Kubuntu as default
[*]Epiphany uses a native GTK+ interface
[*]Epiphany has no branding issues to worry about
[*]Epiphany is Free Software
[*]Epiphany has the best bookmarking abilites of any browser that I know of
[*]Epiphany is *nix only
[/LIST]

---

### Post by givré on 2006-10-25
Hum ok, don't really what i wanted to ask you.
My question was more, why firefox should be move in restricted.
With good arguments.

---

### Post by bruce89 on 2006-10-25
> **givré said:**
> Humm, nothing that should make it move to restricted, others ?

Well, the fact they don't allow modification under the same name, and the non-free artwork.

---

### Post by Wolki on 2006-10-25
> **bruce89 said:**
> Well, the fact they don't allow modification under the same name, and the non-free artwork.

At least under the DFSG, requiring a rename is perfectly acceptable; some other packages do that too (and are thus usually renamed in debian directly).
In this case, it's not even a copyright restriction that requires the rename.

The non-free icon is another matter though.

---

### Post by tubasoldier on 2006-10-25
> **bruce89 said:**
> [*]Mozilla don't release source tarballs of Firefox, distributors have to get it from CVS


CVS? Wow, Mozilla should be ashamed of themselves. CVS is in no way a more viable easier solution that a tarball. Actually, I have downloaded the source tarball from their website. It is freely available.

---

### Post by givré on 2006-10-25
The thing is that the copyright claim that firefox is GPL.
```
Overall, the firefox project is licensed under the terms of the Mozilla
Public License version 1.1 or, at your option, under the terms of the GNU
eneral Public License version 2 or subsequent, or the terms of the GNU
Lesser General Public License version 2.1 or subsequent.
```
If you don't think so, it's a problem between the FSF and mozilla.
And you should bring the case to the FSF.

---

### Post by chaosgeisterchen on 2006-10-25
In terms of following the 'free software'-way of Ubuntu strictly there is no logical option apart from including IceWeasel in Edgy+1.

I am not against Ephiphany but I wouldn't use it over IceWeasel.

---

### Post by Toxicity999 on 2006-10-25
> **chaosgeisterchen said:**
> In terms of following the 'free software'-way of Ubuntu strictly there is no logical option apart from including IceWeasel in Edgy+1.

I am not against Ephiphany but I wouldn't use it over IceWeasel.


Yea... Except one minor detail, IT'S THE SAME THING. I understand people wanting Epiphany in rebelion to Mozillas little action (now working well and understood mutually.) But when people say 'just rename it!' To rebel against them... that's just crazy. It's the same thing so why go through that when right now it works fine, and we have the nice 'lil orange fox keeping us company.

I understand your position, if only by following the ideals word for word. But Realistically.... why bother?

---

### Post by BWF89 on 2006-10-25
Firefox = some of the best the open source community has to offer

---

### Post by bruce89 on 2006-10-27
> **BWF89 said:**
> Firefox = some of the best the open source community has to offer

Unfortunately, it is made by a company who doesn't recognise that their programs are open source. - [http://blogs.gnome.org/view/bolsh/2006/10/24/0](http://blogs.gnome.org/view/bolsh/2006/10/24/0)

---

