---
title: "Spyware and Adware?"
date: 2006-02-27
forum: Server Platforms
---

### Post by jason.b.c on 2006-02-27
:confused: I've been reading through the ( security ) section in this forum and was wondering:confused: , is there any kind of spyware/adware programs out there for ubuntu?.  because if you were duel booting or something like that, that stuff could get in your windows system.:(    I mean there's ( clam av ) for viruses and ( firestarter ) for a firewall, so why not spy/adware???;) ...

---

### Post by Zeroangel on 2006-02-27
Because there is none! 

Oh yea, the virus scanner is meant mostly to detect Windows viruses, since there really isnt any Linux viruses in the wild.

Isn't Linux great?

---

### Post by habrys on 2006-02-27
[QUOTE=Zeroangel]
Because there is none!
[/QUOTE]
Yet.
Probably.

---

### Post by xhie on 2006-02-27
Someday soon I'm sure there will be. Like you used to never have any sort of security issues with firefox, then you did, because out there somewhere is some nerd using firefox that decided that it needs to be included in the adware installing popup thingie he was making. 

I'm sure soon enough enough there will be enough people running linux so that whoever writes adware is gonna start paying attention.

But then again, I guess the average skill level or whatever amoung linux users is higher then windows people.

---

### Post by Jason_25 on 2006-02-27
[QUOTE=jason.b.c]  because if you were duel booting or something like that, that stuff could get in your windows system.:( [/QUOTE]
So are you stating this as fact?  On one hand you seem to be asking for advice on the subject, and on the other, giving it.

---

### Post by jason.b.c on 2006-02-27
> So are you stating this as fact? On one hand you seem to be asking for advice on the subject, and on the other, giving it.


> So are you stating this as fact?

yes, has it not already been proven that although windows based viruses/spyware/adware do not affect linux they can still be transmitted into windows via burned cd, swap partition, usb pen drive, CF card reader,etc etc ???;) 


> and on the other, giving it.
 
yes, giving it to anyone who didn't think thats stuff could still happen!;)

---

### Post by woedend on 2006-02-28
2 points here.  1 - virii/spyware are generally not crossplatform(would take one helluva job to get that done, and well, not gonna happen).  That said, if by some miracle something f'd your windows up, linux would still work fine.  And vise versa...unless i supposed you mounted your ntfs partition, set it writeable to all, and found a virus which would infect it.  Slim to no chance I would think.  Most importantly is 2.
2 - This is why we have ubuntu repositories...I LOVE THEM!  Why?  Because each package is tested a billion times(generally mind you) before being available to us.  This means that if gaim decided to include popups and spyware/adware, im sure it would be dropped quickly.  And this my friend is the beauty of open source.  One could then pick out offensive parts...improve on the code...etc etc depending on licensing I suppose. In windows, you must download each package at your own risk.  Here, you install through synaptic(most things!).  And its real easy to fine tune your system not to allow this behavior anyways(selinux comes to mind but not necessary).  But lets enjoy this time we have - spyware free/virus free.

---

### Post by az on 2006-02-28
[QUOTE=jason.b.c]:confused: [/QUOTE]

It's easy to get confused by the different opinions out there.

[QUOTE=jason.b.c]
I've been reading through the ( security ) section in this forum and was wondering:confused: , is there any kind of spyware/adware programs out there for ubuntu?.  [/QUOTE]

Not in the repositories.  Everything in main and universe is open source, right?  Spyware is by definition, closed-source!

[QUOTE=jason.b.c]
because if you were duel booting or something like that, that stuff could get in your windows system.:(  [/QUOTE]
No.  The only reason you would need to run virus software is if you are running a mail server and you are required to do so by law.

[QUOTE=jason.b.c]
  I mean there's ( clam av ) for viruses and ( firestarter ) for a firewall, so why not spy/adware???;) ...[/QUOTE]

Clamav for the desktop is bullcrap.  Useless on linux.  A firewall is also useless for a desktop - just don't run services that listen to the outside.  If you do, know what they are doing.  Otherwise, you are just going to run those services, run a firewall, but poke a hole through it to let your service talk to the outside.  Like an umbrella with a hole.

---

### Post by jason.b.c on 2006-02-28
> It's easy to get confused by the different opinions out there.


Yes, I would have to tend to agree with you there!;) 

The only reason why i asked my question is that i knew that there was but only the handfull of viruses and stuff out there ( at least thats what i've read here in _this_ forum ) that could actually affect linux even only at a minimum, i just thought that if you had a duel boot setup that there was still the chance ( depending on your setup ) they could still get into windows!!

I guess i've just been using windows for way too long!:rolleyes:

---

### Post by Rizado on 2006-02-28
Now, linux and windows doesn't work the same way, while it's perfectly possible to create adware and viruses for linux, is it worth it? In linux you're running as a user with almost no access to the important files so it's quite hard for it to do any harm, and the security holes would probably be closed in no time.

Windows on the other hand is usually absolutely open, with hundreds of ways of hiding stuff from the user. (How often do you check all files in your windows directory, and all other ones?)

---

### Post by aysiu on 2006-02-28
[QUOTE=Rizado]Now, linux and windows doesn't work the same way, while it's perfectly possible to create adware and viruses for linux, is it worth it?[/quote] Probably not, because malware writers can do more damage to a larger userbase if they write adware and viruses for Windows. 

> In linux you're running as a user with almost no access to the important files so it's quite hard for it to do any harm, and the security holes would probably be closed in no time. I've heard this argument a lot, and I have to say the *important files* to me are my *personal files*, not my system files. I can always reinstall Ubuntu and get my system files back. If my personal files get erased, corrupted, compromised, then I'm in deep s**t. The best thing to do is encrypt your personal files and/or bar them from internet access and back them up frequently.

> 
Windows on the other hand is usually absolutely open, with hundreds of ways of hiding stuff from the user. Supposedly that default setup is going to change with Vista. 

> (How often do you check all files in your windows directory, and all other ones?) How often do I check all the files in my /etc, /var, /usr, /lib, and /boot directories? Almost never. *All* the files?

---

### Post by woedend on 2006-02-28
put your personal files in a separate partition and make it unwriteable to all.  When you get more that you want to add,, make it writeable and write to it.  And...in linux you can delete files while they are running, something i've not been able to do in windows since windows 95 using a special program.

---

### Post by Perfect Storm on 2006-03-01
Just make sure to backup the things you have, no matter which OS you're running. It's good policy.

I've never heard of anyone in reallife or on this board(or other linux board I'm visiting) who got infected by a virus. There's been some threads about their anti-virus program picked up some win-viruses on their fat32 and/or emulated win programs. Other threads that said "OMG I got viruses on my linux system!!!11" had been false alarm so far.

But I do not deny that linux can get virus, but it's not so easely done.

---

### Post by LordHunter317 on 2006-03-01
> **jason.b.c]yes, has it not already been proven that although windows based viruses/spyware/adware do not affect linux they can still be transmitted into windows via burned cd, swap partition, usb pen drive, CF card reader,etc etc ??? said:**
> Which in this case, isn't a Linux software distributors concern.

It might be if we were talking about a file server.  But the fact the user has to explcitly take action makes it not the distribution's problem.

[quote=woedend]2 - This is why we have ubuntu repositories...I LOVE THEM! Why? Because each package is tested a billion times(generally mind you) before being available to us.No, they're not, and I don't know what would give you that idea.  Are they tested?  Yes.  But that odesn't mean what you think it means.

>  put your personal files in a separate partition and make it unwriteable to all. When you get more that you want to add,, make it writeable and write to it. That would be, all the time.  You have to have write access to modify the files too, you know.

> And...in linux you can delete files while they are running, something i've not been able to do in windows since windows 95 using a special program.And that gives what sort of security?  It doesn't, actually.

[quote=azz]Spyware is by definition, closed-source![/quote]No, I don't what gives you this idea, but it couldn't be more wrong.  The two things are completly orthogonal.

> No. The only reason you would need to run virus software is if you are running a mail server and you are required to do so by law.Umm, I know of no laws anywhere that mandate that.  I have no clue what you're talking about, but I'm pretty certain you don't, either.

[quote=Rizado]In linux you're running as a user with almost no access to the important files[/quote]Depends on how you define important.   Can I further compromise applications?  No.  Can I mess with the users data or steal it?  Yes.  Can I still steal their Internet or run a botnet or other such activity?  Yes.

>  so it's quite hard for it to do any harm,You can do plenty.

>  and the security holes would probably be closed in no time.Several of them are fundamental to the model all operating systems use.

> Windows on the other hand is usually absolutely open, with hundreds of ways of hiding stuff from the user. No, it isn't.  Admin isn't even root, and you'd be suprised at the number of limited Windows accounts anyway.

[quote=aysiu]The best thing to do is encrypt your personal files and/or bar them from internet access[/quote]The latter can only be done by only using a computer detached from the Internet, which is useless for a lot of things, if not most things.

---

### Post by ice60 on 2006-03-01
it's always good practise to scan downloads from the internet so you don't end up deleting your home directory when you run your new program. even official releases of programs can end up being infected, like the imfamous [Korean Mozilla Foundation infection](http://security-protocols.com/modules.php?name=News&file=article&sid=2944).

it's important to keep your programs updated, there's exploit code for old Linux programs and "hackers" know exactly where to find it. i can also think of the Sun Java "updating problem" whereby when you update to a newer version, which will normally include security patches, the old version is left on the system and can still be exploited. 

so the important thing is to be security aware, keep your programs up-to-date, and don't listen to anyone who says you don't need an AV or you can't get viruses/malware.

---

### Post by az on 2006-03-01
[QUOTE=LordHunter317]Which in this case, isn't a Linux software distributors concern.

It might be if we were talking about a file server.  But the fact the user has to explcitly take action makes it not the distribution's problem..[/QUOTE]

Right.


[QUOTE=LordHunter317]

No, they're not, and I don't know what would give you that idea.  Are they tested?  Yes.  But that odesn't mean what you think it means..[/QUOTE]

Do you really think a keystroke logger would last a long time in the repositories?


[QUOTE=LordHunter317]No, I don't what gives you this idea, but it couldn't be more wrong.  The two things are completly orthogonal..[/QUOTE]

What I mean is that spyware is typically installed by the user without consent or the knowledge that they are getting this "value-added" software.  Open-source software does not have these kinds of installers.

"click-this-file-to-install" software is not the norm in Ubuntu.  

As for what is in the repositories, I have never heard of someone ever installing spyware from a Debian or Ubuntu repository.  Have you?  (serious question, not being sarcastic - you probably would know more than myself)

[QUOTE=LordHunter317]Umm, I know of no laws anywhere that mandate that.  I have no clue what you're talking about, but I'm pretty certain you don't, either.
[/QUOTE]

Here in Canada, an ISP who provides email service is liable for dammages that are incurred if they pass on a virus and did not take appropriate precautions to avoid that.  I thought it was the same for the US, too.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=azz]Do you really think a keystroke logger would last a long time in the repositories?[/quote]Possibly, yes.  The source code isn't heavily audited.

For example, if Linus gated a patch in that had a keystroke logger in it, then yes, I suspect that would last in the repositories until it was discovered.  

The odds of that are low, but they're not non-zero.  And Ubuntu doesn't have a group that actively searches for such things.  Most distributions don't, in fact.

You have to rely on upstream.

Also, if the ftpmaster was compromised, you could be sending out bad packages in the meanwhile.  This happened to Debian, though it was discovered reasonably quickly and the impact was low.

But it's still existent, albeit small.

This is why repositories are signed and the binary package are signed when built, and why one should be careful before installing unsigned packages.  They provide mitigation against a compromise of the distribution server.

> What I mean is that spyware is typically installed by the user without consent or the knowledge that they are getting this "value-added" software.Fine, then say that.  What you said doesn't mean that, and could confuse people.  It's a false assurance.

> Open-source software does not have these kinds of installers.VMWare is partially open-source, and it has an installer.  So does NVidia, etc.  

**Open-source** has no bearing on this.  Period.  Spyware in an open-source application would be rather silly, unless it was embedded deep in the application's core, but there's nothing about being open-source that prevents you from including spyware.

As I said, they're orthogonal concepts.  They have no bearing on each other.

"click-this-file-to-install" software is not the norm in Ubuntu.  

> As for what is in the repositories, I have never heard of someone ever installing spyware from a Debian or Ubuntu repository.  Have you?  (serious question, not being sarcastic - you probably would know more than myself)No, but the point is it's more than possible to install trojan software as a result of a security breach.

> Here in Canada, an ISP who provides email service is liable for dammages that are incurred if they pass on a virus and did not take appropriate precautions to avoid that.  I thought it was the same for the US, too.No, in fact, the US has laws that mandate the exact opposite behavior for certain professionals, like stock traders.  *All* communications with traders must be recorded.

That law is absolutely silly, I might add.

---

### Post by az on 2006-03-01
[QUOTE=LordHunter317]
VMWare is partially open-source, and it has an installer.  So does NVidia, etc.  
[/QUOTE]

They are not in the repos.  If they were dfsg-compliant, they would be.  As such the nvidia binary is packaged in linux-restricted-modules, with no installer needed.  And Vmware is not redistributeable.

So what's the straight dope?  What's your view of viruses, spyware and other malware in ubuntu.


Do you think you need clamav, firestarter or an antispyware application running on an Ubuntu desktop?

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=azz]They are not in the repos.[/quote]And that's relevant how?  You weren't talking about them in what I replied to.


> So what's the straight dope?  What's your view of viruses, spyware and other malware in ubuntu.The risk is low, except in the events of a distribution server compromise, local system compromise, or upstream source compromise.

But there's little you can do about any of those.

Nor are they relevant to what you said.  **You weren't talking about Ubuntu, *you made bad generalizations.***

That aren't true.  One could put spyware in open-source software, though one would have to wonder why.  Will Ubuntu ship such things?  Doubtful.  Does that mean we may not see such a beast one day?  No, not at all.  It's more than possible, and there's a lot of sleezy people out there who would (and could) repackage existance OSS software with crap in it.

> Do you think you need clamav, firestarter or an antispyware application running on an Ubuntu desktop?No, but again, this isn't relevant to what you said.

---

### Post by Ptero-4 on 2006-03-01
> 
Quote:
(How often do you check all files in your windows directory, and all other ones?) 	
How often do I check all the files in my /etc, /var, /usr, /lib, and /boot directories? Almost never. All the files?

Well I do check the /System, /Library, and /Private directories monthly.

---

### Post by az on 2006-03-01
[QUOTE=LordHunter317]And that's relevant how?  You weren't talking about them in what I replied to.[/QUOTE]

The original question was "is there spyware out there for Ubuntu" to which my answer was "not in the repos".

[QUOTE=LordHunter317]
The risk is low, except in the events of a distribution server compromise, local system compromise, or upstream source compromise.

But there's little you can do about any of those.

Nor are they relevant to what you said.  **You weren't talking about Ubuntu, *you made bad generalizations.***

That aren't true.  One could put spyware in open-source software, though one would have to wonder why.  Will Ubuntu ship such things?  Doubtful. [/QUOTE]

That was my point.   We are not disputing this.

[QUOTE=LordHunter317]
 Does that mean we may not see such a beast one day?  No, not at all.  It's more than possible, and there's a lot of sleezy people out there who would (and could) repackage existance OSS software with crap in it.

No, but again, this isn't relevant to what you said.[/QUOTE]

Sure it is.  We are not talking about open souce in general, but Ubuntu.  You just went over how an open source spyware app is not likely to be in the Ubuntu repositories.

I can understand that you have a problem with the uninformed open source rhetoric.  I think this sort of unfounded gossip about free-libre open source software superiority is harmful, too.   My phrase was a generalisation, but I think there was a context to it.  But technically,  you are right.

I think FLOSS has a lot to offer.  For my needs, I think it is way superior to proprietary software.  I think it's important to relay accurate facts that can survive the bullshit test, otherwise, people tent to not take it seriously.  

Actually, it would have been better if you had just come out and said that to begin with, instead of picking nits with one phrase.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=azz]Actually, it would have been better if you had just come out and said that to begin with, instead of picking nits with one phrase.[/QUOTE]I, umm, did.  Your statment was a **logical impossibility,** and I said that much.  I'm not sure how much more concrete of a bullshit test you can make, frankly.

Sorry for dragging this out, however.

---

### Post by woedend on 2006-03-02
deleting executables while running would make eliminating a lot of windows spyware/adware extremely easy.  hence why i would like to do it on linux should the day ever come.  i dont understand what sorts of modifications you must make to your files, as my personal files are all songs, pictures, videos, and final documents i have written.  I do not need to modify them often if at all, this system works for me?  I do not see spyware making it into ubuntu repo's, and I find your suggesting this slightly harsh.

---

### Post by LordHunter317 on 2006-03-02
[QUOTE=woedend]deleting executables while running would make eliminating a lot of windows spyware/adware extremely easy.[/quote]No, it wouldn't.  The application could just write itself back out to disk at shutdown.

> i dont understand what sorts of modifications you must make to your files, as my personal files are all songs, pictures, videos, and final documents i have written.If you're a developer like me, you may overwite a file anywhere from 100-1000 times a day, easy.  I probably save any school work I'm doing every 5 minutes.  Certain documents, like lab reports, I save more often.  Any time I make a formatting change in Word or embed another object, I save out of reflexive habit.  That could easily lead to 50 saves in a few hour period, for a complicated report or document.

It's simply impractical. 

> I do not need to modify them often if at all, this system works for me? But it's not a general case solution in the least.

>  I do not see spyware making it into ubuntu repo's, and I find your suggesting this slightly harsh.Well, find it harsh.  Only ignorance or simple lack of understanding could lead to the belief that such a thing is out-and-out impossible, albiet unlikely.

Will it happen?  Probably not, ever.  Can it happen?  Yes.  There's a big difference there.

---

### Post by jason.b.c on 2006-03-02
> I, umm, did. Your statment was a logical impossibility, and I said that much. I'm not sure how much more concrete of a bullshit test you can make, frankly.

Sorry for dragging this out, however.

( *laughing histaricaly* :eek: oh boy , wow just look at the crap i've started, i've got a guy in canada bickering with people in the US, and the people in the US bickering with each other, isn't life great???:p

---

### Post by woedend on 2006-03-02
no no, not bickering.  I don't hold any ill feelings toward lordhunter, obviously an intelligent person.  simple  disagreements in standards i suppose.  think of it as a discussion :).

---

### Post by jason.b.c on 2006-03-02
> no no, not bickering. I don't hold any ill feelings toward lordhunter, obviously an intelligent person. simple disagreements in standards i suppose. think of it as a discussion .

Ya I know, I just couldn't believe my simple little question would go _this_ far..:)

---

### Post by az on 2006-03-02
[QUOTE=jason.b.c]Ya I know, I just couldn't believe my simple little question would go _this_ far..:)[/QUOTE]
It is a good question.

---

### Post by jason.b.c on 2006-03-02
> It is a good question.

Thank you, I just figured someone had to ask, and then others out would learn more as well, including myself.:)

---

### Post by Rizado on 2006-03-03
Wow, I thought no one had replyed :oops:
[QUOTE=aysiu]How often do I check all the files in my /etc, /var, /usr, /lib, and /boot directories? Almost never. *All* the files?[/QUOTE]What I meant is that in windows thoose files (or their equivalents) are accessible by everyone. In linux their not, so it's hard to make malware that's hidden in the same way.

---

### Post by simon_is_learning on 2006-03-03
But I must belive that someone out there is working or thinking on a linux virus. 
becouse still it is big buisness taking peoples credit cards number..

Don't think it will happen in a while, but someday maybe.

---

### Post by LordHunter317 on 2006-03-03
[QUOTE=Rizado]What I meant is that in windows thoose files (or their equivalents) are accessible by everyone.[/quote]No, they're not.

---

### Post by az on 2006-03-03
[QUOTE=simon_is_learning]But I must belive that someone out there is working or thinking on a linux virus. 
becouse still it is big buisness taking peoples credit cards number..

Don't think it will happen in a while, but someday maybe.[/QUOTE]

Not a virus, but any other kind of security exploit.  Keep up-to-date with your security updates.

---

### Post by Ptero-4 on 2006-03-03
Hi. How hard (or easy for the paranoids) would it be to hide a troyan/worm/virus/exploit/misc malware. in the /System or /Library dirs.

---

