---
title: "Mark Shuttleworth responds to the recent X debacle"
date: 2006-08-27
forum: The Cafe
---

### Post by matthew on 2006-08-27
From the article:> Luis Villa is [absolutely right in his castigation]("http://tieguy.org/blog/2006/08/24/more-on-qa-ubuntu-trust-etc/") of our X update on Wednesday this week. As a team we made a series of errors, and the result was a desktop that was broken for thousands of users, for several hours. It has been a severe lesson in QA, something Luis knows plenty about.
 An incident report is being compiled by the team and we will publish that for our broader community and users as soon as it is complete. My apologies to those who have been affected, I know that a blue screen of death is the very last thing anybody ever wants to see on Linux desktops and that any downtime caused by mistakes on our part, even measured in minutes, is unacceptable.
Here's a link: [http://www.markshuttleworth.com/archives/54](http://www.markshuttleworth.com/archives/54)

---

### Post by Klaidas on 2006-08-27
I'm very glad that this is working out and Ubuntu isn't trying to hide the details.
Keep up the good work, I'll be waiting for the complete report :)

---

### Post by zenwhen on 2006-08-27
I am glad he personally addressed this.

---

### Post by sanderella on 2006-08-27
Openness and accountablility are great qualities in a leader and a team!

---

### Post by gnomeuser on 2006-08-27
I don't see much addressing really just an apology for pisspoor quality assurance for what is supposed to be an enterprise ready deployment. I'd like to know what they plan to do to avoid something like this in the future.

---

### Post by matthew on 2006-08-27
> **gnomeuser said:**
> I don't see much addressing really just an apology for pisspoor quality assurance for what is supposed to be an enterprise ready deployment. I'd like to know what they plan to do to avoid something like this in the future.I haven't heard any final announcements, but here is a dev's blog discussing some of what they are talking about. [http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html](http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html)

---

### Post by mdsmedia on 2006-08-27
> **gnomeuser said:**
> I don't see much addressing really just an apology for pisspoor quality assurance for what is supposed to be an enterprise ready deployment. I'd like to know what they plan to do to avoid something like this in the future.And the kind of response you'd get without a properly constructed incident report would be more of the same.

Sorry, but people sometimes want QUALITY but then they want it YESTERDAY.

Mark (and the team) is obviously making inroads into looking at what happened, why it happened, how not to let it happen again. Wanting responses to those questions YESTERDAY isn't going to get you quality responses. It'll just get you the same fixes to fixes to fixes that comes out of places like Redmond.

They're looking at it with the same dedication which has created the best Linux distro around. Wanting perfection for nothing will get you anything but perfection.

---

### Post by TravisNewman on 2006-08-27
well spoken mdsmedia. This is hard on them and its going to take time to see what went wrong, and how to prevent it in the future.

---

### Post by KiwiNZ on 2006-08-27
> **panickedthumb said:**
> well spoken mdsmedia. This is hard on them and its going to take time to see what went wrong, and how to prevent it in the future.

Exactly , knee jerk reactions cause only pain.

---

### Post by DoctorMO on 2006-08-27
I forgive them, I'm sure they didn't mean to do it.

I'd be a little anoyed if it effected me and I was a paying customer, but I havn't heard very many paying customers complain so I don't know if it effected them.

---

### Post by The Noble on 2006-08-27
I am very glad that Mark is addressing this himself. Canonical has had a hard week, and I am glad he came out to lend strength to the situation.

---

### Post by The Pinny Parlour on 2006-08-27
I accept your apology Mark.  ;)   Now, let it never happen again please.

---

### Post by gnomeuser on 2006-08-27
> **mdsmedia said:**
> And the kind of response you'd get without a properly constructed incident report would be more of the same.

Sorry, but people sometimes want QUALITY but then they want it YESTERDAY.

Mark (and the team) is obviously making inroads into looking at what happened, why it happened, how not to let it happen again. Wanting responses to those questions YESTERDAY isn't going to get you quality responses. It'll just get you the same fixes to fixes to fixes that comes out of places like Redmond.

They're looking at it with the same dedication which has created the best Linux distro around. Wanting perfection for nothing will get you anything but perfection.

Well **** me for not doing instant worshipping and questioning the lack of proposed solutions and action plans.

Dapper is advertised as enterprise ready, that includes proper QA, this incident is clear evidence that they can handle that currently. I would have settled for "we are sorry and here's the current plan for how to avoid this happening again - please help us improve upon it". 

I'm frankly worried that Ubuntu will slip into the same rhythm as every other distribution, ship a fairly stable release and then when issuing updates they are lax with testing. This is the same thing that caused Fedora Core 4 to break for users with Intel videocards during a upgrade about a year ago. Fedora Core 5 updated the kernel and broke dmraid. Mandriva has issued several bad updates. Gentoo has a history of doing the same (but it's likely that they have better testing than most distros but also more added complexity to complicate matters).

We should be serious about QA if we want to hit the lofty goal of being stable not only at release time.

This means setting up a proper QA team and encouraging widespread testing of updates before deployment to catch such mistakes.

I'd propose something like a proposed-updates repo and having every single update issued blocked by default. We can't let anything slip into the stable distribution that has been tested only in house by the developers (aside security updates which must for obvious reasons go out ASAP).

The tricky part is getting qualified people to test the updates and getting them tested on enough setups to get good coverage. I think we might be able to do this easily by appealing to the correct user group, there are people who want to do QA. Currently after each release most of these people are likely to switch to the next unstable platform to get the newest stuff and help hunt bugs. If we could get maybe 2-5% of the users who'd automatically switch to unstable to run the proposed-updates repo we'd have pretty good coverage.

I believe we can utilize Launchpad to great advantage here, build up a team for these people to give them a way to cordinate testing. Another thing that would be cool would be to use the hardware reporting tools to get some indication of what hardware setups a given update has been tested on and to which effect. That would narrow down problems quickly. We could also need to have an indication as to the urgency of a given update, are there classes of hardware out there that are horribly broken and which of our testers can handle them. If we don't have any on the team we can use the forums to recruit some that have this hardware with all the users we have here the likelihood of someone having access to the affected hardware is high and if it's broken they'd be sure to want it fixed even given the risk of a broken update like the X one.

Another thing we absolutely need is to work with other distributions especially Fedora in this area seems like a good candidate. Their soon to be deployed Beaker automated testing service would be a wonderful addition to any QA team and I'm sure we can get them to work with us to expand on the automated testing of FLOSS applications.

I believe we have most of the infrastructure to do this, we just need to motivate people to help out and highlight the problem as much as we can. Remembering that most people blindly update we need daredevils to protect them for inflicting massive harm upon their setups.

So who is willing to help keep Ubuntu solid instead of pointing fingers and issuing apologies?

Are you a daredevil, do you wear superhero underwear then the testing team needs you!

Uncle Mark wants you!

</start energy>

- Grand testing poobah GNOMEuser

---

### Post by Wight_Rhino on 2006-08-27
A couple of thoughts; 

In this day and age to see ***any*** "CEO" (SABDFL!) to admit to mistakes, apologize and promise results is nothing short of astounding! Well Done Mark.

I agree with Luis that much of the drama is because we have come to hold Ubuntu to extremely high standards. That's a good thing, it's good that this was greeted with surprise and anger, it means that Ubuntu is well on it's way to solving bug #1. Folk already expect it not to break!!

---

### Post by gnomeuser on 2006-08-27
> **Wight_Rhino said:**
> Folk already expect it not to break!!

You mean you expect your system to break at random.. I've always expected my system to work and done a great deal of bugreporting when it didn't.

I fully believe most people expect their computers to work, but in the same breath most people are disappointed by their computers 99% of the time because of it.

---

### Post by professor_chaos on 2006-08-27
I like that mark appologized, but if he didn't, I wouldn't care.
Why, because I didn't pay anything for the OS and he owes me nothing. In fact I owe him and all the devs more than they can even owe me. 

Don't get me wrong, I don't like it when my system breaks, but if I'm not paying for support my complaint is unworthy. I feel ok with making a critical opinionated suggestion, but if I can't help the situation, it's best I stay out of the disscussion. 

Cheers

---

### Post by Wight_Rhino on 2006-08-27
> **gnomeuser said:**
> You mean you expect your system to break at random.. I've always expected my system to work and done a great deal of bugreporting when it didn't.

I fully believe most people expect their computers to work, but in the same breath most people are disappointed by their computers 99% of the time because of it.

Sarcasm/Irony is pretty difficult to convey in a text form. However this one's entirely my fault, I should have used a 'smiley' character. (Wink, probably).

Oh well.

---

### Post by chaosgeisterchen on 2006-08-28
Hey, I really like Mark Shuttleworth :) 

In fact he's not one of those leaders which are not supposed to be down-to-earth-people anymore. Great to read through this.

mHmh.. could be the spirit of ubuntu :)

---

### Post by 3rdalbum on 2006-08-28
I'm looking forward to the investigation results, though I wasn't affected (I only apply updates to packages when they fix bugs that annoy me, or when they add new features that I want).

I can forgive them just this once, because many of the people who would've tested it were away from home, furiously coding, and therefore not applying updates.

---

### Post by awakatanka on 2006-08-28
> **professor_chaos said:**
> I like that mark appologized, but if he didn't, I wouldn't care.
Why, because I didn't pay anything for the OS and he owes me nothing. In fact I owe him and all the devs more than they can even owe me. 

Don't get me wrong, I don't like it when my system breaks, but if I'm not paying for support my complaint is unworthy. I feel ok with making a critical opinionated suggestion, but if I can't help the situation, it's best I stay out of the disscussion. 

CheersThe OS may be free but lots pay for the LTS. The still earn money on the OS this way. 

Looks like they rushed the LTS, Dapper was released with to many problems for user an now they put a update out to fast.

Before giving this kind of support they have to  be ready on every part in there company, and this kind of things shows they rushed there LTS. It will effect the LTS costumers more then the forum people here.

---

### Post by nocturn on 2006-08-28
It's nice of him to apologize, as is the statement on Ubuntu.com.

But they are underestimating the seriousness of this issue.
1# The patch was not recalled as fast as they claim since it still appeared in my update-list about 10 hours after the bugreport was filed.

2# This is not a minor inconvience.  For those non-technical users out there, their desktop is so broken that only reinstalling would fix it (neither of both they can do themselves).  Since X no longer starts, they cannot get online to see the fix (nor would they be able to fix it themselves), nor can they install the fixed package.

The result would be that their computers have to be repaired by someone with technical skills or they are still dead in the water.

I was lucky, I could reach my non-technical friend for who I installed Ubuntu only minutes before she clicked update!

EDIT: with this message, I'm not trying to flame anyone since I really think this incident will make things better in the future.
I do however think we should realise the full effects of this breakage to effectively implement safeguards against it in the future, including a fast-track for redrawing patches.

---

### Post by The Pinny Parlour on 2006-08-28
<quote>
The statement added: “When we learned of the problem, the patch was immediately withdrawn. Mirrors have also been disabled to ensure that the faulty patch isn’t available from them. We have launched an investigation and formal quality process review to understand exactly how this happened and what corrective actions to take.”
</quote>
immediately withdrawn..*bullchit*  17 hours wasn't it?

[http://stuff.techwhack.com/archives/2006/08/26/incorrect-patch-ubuntu/](http://stuff.techwhack.com/archives/2006/08/26/incorrect-patch-ubuntu/)
[http://www.theinquirer.net/default.aspx?article=33991](http://www.theinquirer.net/default.aspx?article=33991)

---

### Post by insane_alien on 2006-08-28
i forgive them. its the first mistake i've seen them make. and they done something about it. if it was MS it would have been weeks and then they would define it as a new standard.

---

### Post by G Morgan on 2006-08-28
> **insane_alien said:**
> i forgive them. its the first mistake i've seen them make. and they done something about it. if it was MS it would have been weeks and then they would define it as a new standard.

They've broken other things, software shutdown comes to mind, but this was more critical because unless you're a programmer or admin this breakage basically made the entire OS unusable.

Prehaps Canonical should define a series of crucial packages that are pre-requistite to just about the entire system and test these more vigourously.

These things will happen and its nice to see an acknowlegement from Canonical but really its a case of changing practices so that crucial things are less likely to fail. It's not as if MS have anything like a perfect record for releasing good updates its just they haven't brought down the entire GUI in an update since the heady days of DX1/2.

Overall this isn't a panic situation, this sort of thing happens to companies with far greater financial resources and in the end the process gets fixed so it doesn't happen again.

//The idea of a pre-release repository that can be locked down via apt-pinning might not be a bad idea actually. Make it so new releases have to spend at least a week in the pre-release repos and the community can take a lot of the testing work off your hands if they so choose.//

---

### Post by Turgon on 2006-08-28
This mistake was a really bad one and can not happen again! I managed to fix my desktop almost right away with some help from the forum, but not everyone have a second computer to read the commands from. 

I really like that Mark comments personaly on this. Hope they can work out some way to avoid souch updates in the future.

---

### Post by The Pinny Parlour on 2006-08-28
> **insane_alien said:**
> i forgive them. its the first mistake i've seen them make. and they done something about it. if it was MS it would have been weeks and then they would define it as a new standard.

LMAO  that is funny. =D>

---

### Post by nocturn on 2006-08-29
We are taking the heat for what happened.

Here's an article in The Inquirer about the incident:
[http://www.theinquirer.net/default.aspx?article=33991](http://www.theinquirer.net/default.aspx?article=33991)

[quote=TheInquirer]
The update was sent out last week and it immediately tiggered the Ubuntu graphics interface.

Since Ubuntu is seen as one of the less technical Linux distribs, Linux boards were full of people wondering what to do. In the true spirit of Linux boards everywhere they were immediately told that if they couldn’t run their entire operations from a command line, they shouldn't be allowed to touch Linux. [/quote]

This will be coming back to haunt us for a time to come...

---

### Post by G Morgan on 2006-08-29
Did anyone actually say that you had to be able to run from the command line to use Ubuntu.

---

### Post by aysiu on 2006-08-29
We may be taking the heat, but I don't think that's fair. Anyone can sign up for the forums, and I think most people agreed it was a mistake. Only a small handful of people took the elitist attitude on this one.

[quote=G Morgan]Did anyone actually say that you had to be able to run from the command line to use Ubuntu.[/quote] I believe one person might have actually said it, but the article deliberately exaggerates for sensationalist purposes. The general feeling I got was not that many veteran users were telling novices they shouldn't be using Ubuntu. I'll try to find a relevant link.

**Edit**: No such remark in [Ubuntu devs discuss how to avoid update problems like last recent X update](http://ubuntuforums.org/showthread.php?t=243511)

Such a remark appears in post #16 of [How could an update break X?](http://ubuntuforums.org/showthread.php?t=241334): [quote=bonzodog]I think it would be hoped that most users can use the system entirely from the command line, including web browsing with something like links2. It would also help if people made themselves familiar with aptitude and apt-get, and dpkg.[/quote] Then there's post #71: [quote=kellogs]If it is that grave to you, now that it's fixed you've got the freedom to leave to another OS.[/quote] That's two out of 79 posts in that thread. Seriously. And both of those post-ers had under 500 posts--hardly forum veterans trying to intimidate new users.

In [do you think that the xserver crush was a good thing ?](http://ubuntuforums.org/showthread.php?t=242252), 121 one people voted, and 84% said the X breakage was not a good thing. In the 67 posts in that thread, I saw none of the tone that article indicated.

The big debate really seemed to be about "This is a terrible thing!" and "It was a bad thing, but don't make such a big deal about it. It got fixed."

---

### Post by nocturn on 2006-08-29
> **aysiu said:**
> We may be taking the heat, but I don't think that's fair. Anyone can sign up for the forums, and I think most people agreed it was a mistake. Only a small handful of people took the elitist attitude on this one.

I meant the community as a whole, not just the forums.
The breakage and the response to it where the worst kind of press for Ubuntu and it will take some time before it passes.

I checked the forums rather quickly after the incident and most responses where pretty decent.  As we are a large community, there will always be those that cannot respond in a respectful or kind manner, but their number is extremely small compared to the number of people that genuinely want to help.

---

### Post by aysiu on 2006-08-29
Oh, I know what *you* meant. I was referring to *the article*, which talked about the "Linux boards." I took that to mean the Ubuntu Forums and not IRC.

In any case, it might have made sense--if this were real reporting--to say that the wonderful support was to be found on the Ubuntu Forums, though other outlets greeted new users with a more elitist attitude of "love it or leave it."

---

### Post by frup on 2006-08-29
I've noticed that alot of the reporters covering these stories appeared to have no idea what they were talking about... Which is bad because these stories got quite high on google news too.

I think a good installation guide linked on the download section wouldnt be a bad idea... and making sure that all users understand what a live CD can do. A good encouragement within the community to use these live CD's to ask for help if mistakes happen...

Do the CD's have the option to restore an existing version of ubuntu? (i.e keep all installed files but make system files default again or what ever works)

From the month or so i tried linspire a longtime ago one cool thing to make the process easier in situations like this would be for synaptic/repos to remember what programs you have installed... i was lucky that i fixed my break with in 5 minutes of it happening... but if i hadnt been able to i would probably have just reinstalled... the hard part is trying to remember all the packages i had downloaded.

---

