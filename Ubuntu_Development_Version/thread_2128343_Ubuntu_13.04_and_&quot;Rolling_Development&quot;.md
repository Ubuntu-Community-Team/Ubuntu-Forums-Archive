---
title: "Ubuntu 13.04 and &quot;Rolling Development&quot;"
date: 2013-03-22
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-03-22
"Rolling Development" (supposed to begin with 13.04) but not actually called "Rolling" even though it essentially will be... is apparently what they voted to do...they will make it so that it will point to each next development release without needing to actually upgrade to it...From what i read, it sounds like it would be accomplished using a "symlink" though the details on the best way to do it, they still have to work out...don't know if we will have to set it up manually in the terminal, an option to select in the software updater or automatically (though i'd imagine it wouldn't be by default....since some may want to just have their install continue as a normal release when it goes final...

If anyone hears any updates on how and when they think they will be doing that, please post in this thread if they see or find out something...does anyone have any ubuntu developer "contacts" they might get any advanced information from? :D  comments also welcome as well ;)

---

### Post by mr john on 2013-03-22
Well, this is a good start. I've been using Ubuntu since Breezy and it's been a royal pain in the butt sitting through massive updates every 6 months on multiple machine. It used to be nice, but the novelty has worn off.

---

### Post by craig10x on 2013-03-22
> **mr john said:**
> Well, this is a good start. I've been using Ubuntu since Breezy and it's been a royal pain in the butt sitting through massive updates every 6 months on multiple machine. It used to be nice, but the novelty has worn off.

I hear you and could not agree more ;)
I am getting so tired of re-installing every 6 months to get the latest ubuntu...

This is the first time i ever installed the development version and have been very surprised by the excellent reliability of the updates (aside from a small breakage in the VLC media player sound which they got fixed in about 2 days or so)...In fact, for a while, i use to run Linux Mint's LMDE which is pointed to debian testing and had FAR more problems with that...in fact, had to re-install it twice and then finally gave it up...Ubuntu development for me has been FAR more reliable...

Of course, keep in mind this change only affects development (not the normal 6 month releases)...so you would have to run development to get that "rolling like" feature...
It should be far more reliable then trying to "upgrade" each development version, and overall should work out better then running the 6 month standard version and attempting those 6 month upgrades which can, as you know, be very "hit and miss" in nature...

The way it would work is that when the development starts on the next ubuntu version, your updates in development would simply switch over ("point to"... as it were) to that (providing the "symlink" or whatever they decide to use for this is activated of course)...

---

### Post by Elfy on 2013-03-23
> **craig10x said:**
> ...does anyone have any ubuntu developer "contacts" they might get any advanced information from? ...

I'd subscribe to the mailing lists

[https://lists.ubuntu.com/#Development+Lists](https://lists.ubuntu.com/#Development+Lists)

---

### Post by entangled on 2013-03-23
All distributions are potentially 'rolling' to some extent because updates (mostly security related) are frequently offered (but you don't have to accept them). Even Windows is rolling in this sense.
Many distributions have an aiming point for a multi-package bundle of development, the 'next release', and this serves as a start point for new users. It is also a major update for existing users, which can be done either by re-installing or by using the usual update mechanism on a large scale.
Some, like ArchLinux, have more package-focused, smaller, development bundles, and also release 'snapshots', to allow for efficient start points.

Having used both, on and off, for quite a while, on both VM and real hardware, I think I prefer the smaller-scale Arch approach; in practice it has been very stable for me, even through the systemd shake-up.

---

### Post by craig10x on 2013-03-23
I think it could work out real well with the new system for the development...i just hope they get it worked out and implemented before April 25th when 13.04 will be going final...they did mention it is suppose to start with 13.04 (both the new 9 months of updates for the incremental versions and the new "always pointing to the latest development" for development version) and i wonder how it will be done and how we will be notified about it...

---

### Post by EgoGratis on 2013-03-23
> **mr john said:**
> Well, this is a good start. I've been using Ubuntu since Breezy and it's been a royal pain in the butt sitting through massive updates every 6 months on multiple machine. It used to be nice, but the novelty has worn off.

To be honest for users thinking like that "rolling model" does not bring much benefits. There will still be massive updates but not as "one time upgrade model" every 6 months but represented in more constant but we could say still massive  flow of updates on multiple machines... compared to something like LTS release model with 5 years support. I doubt "rolling model" will improve your situation on how to stay "current" or better "up-to-date" on multiple machines.

---

### Post by craig10x on 2013-03-23
Of course, he won't have "massive updates" if he lets it update every day...now if he waits a few weeks between updating, well that would be a different story :D
With 13.04 development, i do my updates every morning when i boot up the computer..just takes a few minutes...

---

### Post by EgoGratis on 2013-03-23
I think i am skilful enough to "survive" rolling release model or at least try to but i doubt this is something average user/OEM wants. And to be honest i don't see what is the point of rolling if we have interim releases. Interim release will still be the product/key and this new rolling release will benefit exactly who?

Probably i don't have all the information right now and i will wait and see but until there are interim releases what is the point in having developers and testers on rolling release? It doesn't make any sense to me to be honest and i don't believe rolling model is something that needs to happen today knowing all the facts. It might make sense when some things change but currently i don't see the point and benefit in doing it! I might be wrong but as i said i will wait and see!

---

### Post by craig10x on 2013-03-23
I think interim releases would be fine if the upgrades were "bullet proof"...If you could be assured that it would all go perfectly, then i think it would be fine...but unfortunately that is not the case right now...
With the development release, always pointed to each new version, you would not need to upgrade to continue as you do now...so aside from the testers, i think there will probably be quite a few that will want to use it...

As i previously mentioned, i had far more problems running mint's LMDE pointed to debian testing, then i have on this 13.04 development release...my "impression" is that quality control is way better here then it is in debian testing...

I also recall getting FAR MORE updates each day on debian testing, then i generally get here...with far greater chance of breakages on there...and LMDE is not a testers distro...

---

### Post by EgoGratis on 2013-03-24
> I think interim releases would be fine if the upgrades were "bullet  proof"...If you could be assured that it would all go perfectly, then i  think it would be fine...but unfortunately that is not the case right  now...

BUT nobody is ditching interim releases? They are here to stay and the exact same thing will still be true. 

And i don't believe rolling will improve this because a lot of upgrades to new release problems are related to binary drivers and this won't change and probably it will make things worse. How would you deal with upgrades you are 100% sure will brake binary drivers in rolling? You would brake them and there is no way around it ATM. Maybe in the future if display server used would change this drastically then this would not be the problem anymore but ATM it is.

And software does brake in rolling too. I don't believe everybody will/would follow rolling tempo and when some updates that brake software will occur how will you deal with that? You couldn't you will/would brake it and until it's fixed it would not work properly and this could easily lead to frustration.

> With the development release, always pointed to each new version, you  would not need to upgrade to continue as you do now...so aside from the  testers, i think there will probably be quite a few that will want to  use it...

Yes tester will use the release that is different form interim release and it doesn't make sense to me. Why exactly would you do that? The whole point of development release/cycle is to develop/test it not to use it daily for surfing the internet for example.

> As i previously mentioned, i had far more problems running mint's LMDE  pointed to debian testing, then i have on this 13.04 development  release...my "impression" is that quality control is way better here  then it is in debian testing...

How would putting more effort on rolling improve interim situation? It doesn't make sense to me but i could be wrong but somebody should explain this to me first to see if it's valid.

> I also recall getting FAR MORE updates each day on debian testing, then i  generally get here...with far greater chance of breakages on  there...and LMDE is not a testers distro...

BUT "rolling" is something small margin of users will/should use or do you think the plan is to test it and if it works to ditch interim releases? I expressed my opinion in previous thread:

[http://ubuntuforums.org/showthread.php?t=2121105](http://ubuntuforums.org/showthread.php?t=2121105)

P.S. And in this thread and i will just wait and see what happens and i just hope something impulsive and foolish doesn't happen too soon (before some things change in a way to enable Ubuntu and all built on top of it to go faster and not making a mess while doing it)! And i am not quite sure if it's the best strategy i still think LTS releases with long support cycles are the key/value and to enable new ways for all that is built on top of LTS releases to go faster if they choose to go faster.

---

### Post by EgoGratis on 2013-03-24
Ditch everything non LTS and do LTS every 18 month. Enable ways to get new software, kernels, drivers in USC. Testing for stuff like UnityNext/Mir use developer PPAs for it for interested parties and don't care if it brakes sometimes this is not the stuff for regular users anyway.

Don't do development release. 18 months is fair cycle to push developers to introduce new polished great stuff like UnityNext, maintenance burden would be only for LTS release and i would not call it a burden because everything fixed would benefit end users of Ubuntu. Fix more stuff in LTS releases after the release!

---

### Post by cariboo on 2013-03-24
I don't know if any one followed the discussion on the mailing list, but quite a few developers are looking forward to whatever we call the release type, as it will give them a chance to fix bugs without any time limit. Currently, they are in a rush to repair as many current bugs as possible before the release date, and then they move on to repairing bugs for the next release, this type of schedule doesn't give them the chance to go back and fix any of the older bugs. The new release style should give them a chance to fix some long standing bugs that have been ignored up until now.

---

### Post by EgoGratis on 2013-03-24
If u are referring to cutting down the time interim releases are officially supported and rather working more on fixing bugs instead of "wasting time" supporting interim releases 18 months then it does make sense but i don't exactly understand what is the connection with new "rolling release" model and why it is needed if interim releases will not be ditched. 

About time limit i don't know if i agree it will make much difference. I think it will take the same amount of time to produce polished UnityNext and it doesn't make much difference if you do it in 3 Ubuntu interim releases bit by bit and it's ready for LTS or do it between two LTS releases or to built it on top of rolling release in 2 year times. It takes let's say roughly 2 years time but i doubt time limit will be this long or extended beyond let's say 2 years for this goal. It will still be tight schedule and it doesn't make much difference if it will be built for interim/LTS/rolling Ubuntu.

---

### Post by EgoGratis on 2013-03-24
Go faster by reducing the time LTS releases are made to 18 months and by ditching everything in between. Do development on latest LTS release and testers should use developers PPAs. This way latest LTS would get latest UnityNext + future option for running UnityNextNext and that would add additional value to it. Developers could work on latest LTS to produce UnityNextNext and to fix UnityNext bugs for solid 18 months after that additional support (few years) would be security updates and backporting few but very important bug fixes if it would make sense to do it.

12 month after LTS would be released LTS NextNext would be made in 6 month cycle from upstream components and bug fixing would start + UnityNextNext porting to UnityNext and starting of developement of UnityNextNextNext...

This way a lot of maintenance burden would go away developers and users would use the same release for at least 12 months (yes the whole year) and both would focus on that same release for 12 months (yes the whole year). Users using it and developers fixing it after they thought it was ready (and boy/girl, where they wrong) and probably this way bugs would become the thing of the past (not really) and making UnityNextNext could get more attention.

OEMs would get 18 month window to properly support their hardware and 3rd party developers would have more time to think about their app and not to think about (daily) if it runs on latest LTS or rolling Ubuntu or that other versions between them a lot of Ubuntu users use too.

---

### Post by craig10x on 2013-03-24
The new method of being able to have it just "point" to the next development version instead of having to upgrade (or re-install) to get it, is a major improvement for development...
I would think it will be highly appreciated by both the "testers" who will continue to aid in discovering and reporting bugs which help the developers...

In addition, i think it will also attract a certain percentage of regular ubuntu users (not all who currently use the interim and LTS releases) who will look at this as essentially a chance to have
a rolling style ubuntu that hopefully, they would not have to re-install or "upgrade" every 6 months...and would give them all the latest ubuntu "stuff and software" (lol) as it comes in...

And thanks to the high reliability that the development branch has reached in regard to the updates you receive each day, an apparently FAR MORE RELIABLE rolling release then you'd get using
most of the others that "roll" (including LMDE which runs on debian testing)...

That is what is attracting me to it, i've been running 13.04 about 2 months now and have been amazed how stable and reliable it's been with very few real problems...
I just hope they get the new system set up in time for me to be able to start "rolling" with my currently installed 13.04  :)

---

### Post by EgoGratis on 2013-03-24
> The new method of being able to have it just "point" to the next  development version instead of having to upgrade (or re-install) to get  it, is a major improvement for development...
I would think it will be highly appreciated by both the "testers" who  will continue to aid in discovering and reporting bugs which help the  developers...

This would make sense if interim releases would be ditched. Because AFAIK interim releases are here to stay i don't see how it would help interim releases to have developers and testers on "rolling Ubuntu"?

> In addition, i think it will also attract a certain percentage of  regular ubuntu users (not all who currently use the interim and LTS  releases) who will look at this as essentially a chance to have
a rolling style ubuntu that hopefully, they would not have to re-install  or "upgrade" every 6 months...and would give them all the latest ubuntu  "stuff and software" (lol) as it comes in...

I see it more like experiment what might happen yes and the whole reason it exists is to test just that BUT for foreseeable future if interim releases will stay it will be a mess. USC should solve this problem (latest software on LTS) not making the earth move faster and braking the moon by doing it.

> And thanks to the high reliability that the development branch has  reached in regard to the updates you receive each day, an apparently FAR  MORE RELIABLE rolling release then you'd get using
most of the others that "roll" (including LMDE which runs on debian testing)...

I wonder how much effort is spent on this yes. Having development release that should not brake and how much bugs more woudl be fixed if it would brake occasionally.

> That is what is attracting me to it, i've been running 13.04 about 2  months now and have been amazed how stable and reliable it's been with  very few real problems...
I just hope they get the new system set up in time for me to be able to start "rolling" with my currently installed 13.04  :smile:

I bet you would not have problems turning on PPA for UnityNextNext and reporting bugs you find on stable LTS release at the same time. For LTS and UnityNextNext.

---

### Post by sgage on 2013-03-25
It's funny to think that Quantal is going to be supported for 3 months past Raring's support period. Strange days indeed...

---

### Post by pfeiffep on 2013-03-26
So how exactly does one utilize rolling releases. Does software updater download, or should I use apt-get dist-upgrade? I'm using 12.10 and have a second partition for 13.04.

---

### Post by craig10x on 2013-03-26
> **pfeiffep said:**
> So how exactly does one utilize rolling releases. Does software updater download, or should I use apt-get dist-upgrade? I'm using 12.10 and have a second partition for 13.04.

In the developer's comments on the decision, it wasn't mentioned exactly how they are planning on implementing it...they said they had to work out the "details"....
One mentioned something about a "symlink"...if they used that, you would probably have to enter 2 commands (i think) in the terminal to add it...or perhaps they would add it as an optional
"software updater" sources option to check (i don't think it would be activated by default as some might just want to ride 13.04 into a final release and not continue to the next version)....

I hope we will see information in this section about how it will be done before 13.04 goes "final"...

Basically, the plan is to make it so that you would not need to do an "upgrade" in development to move to each new development version....you would simply get "pointed" to the updates for the next version when they starting sending them...essentially, making development "roll" though they are not going to call it that ;)

As time goes on and we get closer to 13.04 release, it would be appreciated if anyone who sees any articles, or gets any information on it, will hopefully post here to my thread about it (with links to any information)...

---

### Post by zika on 2013-03-26
> **craig10x said:**
> In the developer's comments on the decision, it wasn't mentioned exactly how they are planning on implementing it...they said they had to work out the "details"....
One mentioned something about a "symlink"...if they used that, you would probably have to enter 2 commands (i think) in the terminal to add it...or perhaps they would add it as an optional
"software updater" sources option to check (i don't think it would be activated by default as some might just want to ride 13.04 into a final release and continue to the next version)....

I hope we will see information in this section about how it will be done before 13.04 goes "final"...

Basically, the plan is to make it so that you would not need to do an "upgrade" in development to move to each new development version....you would simply get "pointed" to the updates for the next version when they starting sending them...essentially, making development "roll" though they are not going to call it that ;)

As time goes on and we get closer to 13.04 release, it would be appreciated if anyone who sees any articles, or gets any information on it, will hopefully post here to my thread about it (**with links to any information**)...
Or symlinks... :)

---

### Post by craig10x on 2013-03-30
Forgot to give you an LOL for that one, zika :)

by the way, this is the way they put it when they voted on the changes and made the final decision about the new 9 month support for 6 month releases and making it so that development could go right into each next version without the need for upgrading...i am kind of a layman with the technical stuff...what is a "meta" series and "archive mirrors" they are referring to and any guesses on how they might implement it the way they are explaining it?
does anyone want to take a "stab" at this?  I am curious ;)

[B]Enable users to continuously track the development focus of Ubuntu
without having to explicitly upgrade[/B]

[COLOR=#333333][FONT=Lucida Grande]This discussion was about making it easier for some of our users to keep their machine always on the current development release.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]This has nothing to do with Rolling Releases and is purely about setting up some kind of meta-series on the archive mirrors that people can use instead of having to manually upgrade from one development release to the next.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]There again, all 3 present members agreed with this proposal.[/FONT][/COLOR]

---

### Post by craig10x on 2013-04-03
I guess no one had any thoughts about how they might do this...i was curious though, in case they don't have the new way of "pointing to the next version without upgrading", ready in time for the 13.04 final release, in case i would want to move from my 13.04 development to 13.10 development, i was wondering how that is done?  

Anyone who had done it in the past, perhaps you can post here the simplest way to do it...and does it work smoothly?  How do you know when to do the upgrade and does it work well?

---

### Post by EgoGratis on 2013-04-03
> Anyone who had done it in the past, perhaps you can post here the  simplest way to do it...and does it work smoothly?  How do you know when  to do the upgrade and does it work well?

[https://help.ubuntu.com/community/Upgrades#Upgrading_to_development_releases](https://help.ubuntu.com/community/Upgrades#Upgrading_to_development_releases)

It's fairly easy to do this ("one command") and to be honest i personally don't see the point if interim releases are not ditched why additional efforts would be put in the development release to make them work reliable for regular users through the whole development cycle. It should brake regularly for at least 2 to 3 months because it's weird in a way to maintain development release in a way it would be appropriate for regular users and in the same time shift focus from fixing bugs from LTS and interim releases users actually do use.

I still feel Ubuntu is doing it wrong it tries to focus too much on the stuff regular users don't use. Just after the LTS release is available focus ships to interim release and just after interim release is out everything is focused on development release and this new proposals actually tries to make this more obvious.

Why? I feel this is very inefficient behaviour.

As i [suggested]("http://ubuntuforums.org/showthread.php?t=2128343&page=2&p=12572332#post12572332") the process should go in the other direction and to put the all available focus on "solid core" and stay there for a while for something to be built upon it and then go further.

There realy isn't any reason why Unity(Next) + Mir + you name it yourself... could not be developed ON Ubuntu 12.04 and to use development PPAs for testing and at the same time to improve this "solid core" Ubuntu 12.04 represents!

---

### Post by craig10x on 2013-04-03
Good to know that it is easy to upgrade...well, i think what it is... the reason why development updates have mostly become pretty reliable is for improvements in automated checking before the updates are sent, i don't think that it is so much to do with manual intervention on the developer's part (at least that is what i got from some Mark Shuttleworth blog i read about it)...so, it's not like their concentrating on making development reliable as opposed to the LTS and interim releases...

What i can't figure is why don't they simply have LTS and have it update software to keep it current and new kernels and other system improvements, so that you would only really need to install every 2 years at the most (or less if you wanted to continue running with the same version)....

Even in windows, software gets updated all the time without problems...so i can't see why they (ubuntu) couldn't do the same..

The main reason i was considering continuing with development is because of the "rolling style" aspect of it...and with the hope i wouldn't need to re-install as often...
with 6 month releases, there is too much temptation to re-install every 6 months to get the newest improvements...

---

### Post by EgoGratis on 2013-04-03
I spent way too much time thinking about this. :) I will probably manage o use whatever Ubuntu will do.

I would ditch everything but LTS releases and focus on them, slightly reduced time between them and focus on them for at least additional 6 to 12 month after the release but who knows maybe in a year's time i will be on "Ubuntu Rolling" and it will work OK.

---

### Post by craig10x on 2013-04-03
LOL...me too (spending too much time thinking about this) :)

Well, i think i figured...why not go ubuntu development "rolling" and maybe it will go along fine and i won't need to re-install for a long, long time...
and if things get a bit "buggy" or problematic... well, when 14.04 arrives, maybe i'd consider just going LTS to LTS from that point on....

I don't want to roll back to 12.04 because certain large bugs i had on 12.04 and 12.10 on my system were gone as of 13.04 and i like the various improvements in 13.04 that i have noticed...
I'm too spoiled now ;)

---

### Post by EgoGratis on 2013-04-03
> good to know that it is easy to upgrade...well, i think what it is...  the reason why development updates have mostly become pretty reliable is  for improvements in automated checking before the updates are sent, i  don't think that it is so much to do with manual intervention on the  developer's part (at least that is what i got from some Mark  Shuttleworth blog i read about it)...so, it's not like their  concentrating on making development reliable as opposed to the LTS and  interim releases...

AFAIK when something breaks somebody has to fix it (immediately) but i don't see the point in wasting too much resources on this task for first couple of months in dev cycle. For sure it's nice to have dev release working reliable through all of the dev cycle but it's not essential in my opinion.

> what i can't figure is why don't they simply have LTS and have it update  software to keep it current and new kernels and other system  improvements, so that you would only really need to install every 2  years at the most (or less if you wanted to continue running with the  same version)....

even in windows, software gets updated all the time...so i can't see why they couldn't do the same..

Windows OS (the core) needs upgrading every few years. About latest software yes that is something USC needs to solve in my opinion adding concepts like PPAs to it and gradually allow upstream developers to maintain their app in USC. This is not straightforward task or a task to be done over night and probably not a task for 100% of available software but small step in the right direction. It might make sense "Ubuntu Staff" does this for some of the most popular software in the beginning...

> the main reason i was considering continuing with development is because  of the "rolling style" aspect of it...and with the hope i wouldn't need  to re-install as often...
with 6 month releases, there is too much temptation to re-install every 6 months to get the newest improvements...                 

This is one way of looking at it but for majority of users i think latest LTS with 5 years support time is more desirable (if only USC would offer latest app they like to use). It's solved with PPAs usually BUT there are too many Ubuntu releases and because focus shifts after some months PPAs start to loose support for latest LTS release and focus on latest one or two interim releases...

---

### Post by EgoGratis on 2013-04-03
But OK i will be open minded about this and who knows maybe Ubuntu could become rolling release or to have rolling flavour and to work out great!

---

### Post by craig10x on 2013-04-03
I hope so too...now where's that "symlink" ;)

---

### Post by jerrylamos on 2013-04-04
I'm using "unstable" development ubuntu mostly, with fallback to "stable LTS" partition for when I'm doing something important or "unstable" is really "unstable".

On a "rolling release" how do you tell what is "stable LTS" install and what is "shaky unstable" development?

---

### Post by zika on 2013-04-04
> **jerrylamos said:**
> I'm using "unstable" development ubuntu mostly, with fallback to "stable LTS" partition for when I'm doing something important or "unstable" is really "unstable".

On a "rolling release" how do you tell what is "stable LTS" install and what is "shaky unstable" development?
Shake it? ;)

---

### Post by EgoGratis on 2013-04-04
> On a "rolling release" how do you tell what is "stable LTS" install and what is "shaky unstable" development? 				

It's pretty easy to tell... When it doesn't work as you would expect it to work then you are on "development release" and when it works as expected then it's "stable LTS". You can't go wrong. :)

---

### Post by zika on 2013-04-04
> **EgoGratis said:**
> It's pretty easy to tell... When it doesn't work as you would expect it to work then you are on "development release" and when it works as expected then it's "stable LTS". You can't go wrong. :)But lately we have more stable development releases than previous stable releases... ;)

---

### Post by EgoGratis on 2013-04-04
I will wait to see what approach will Mir take on GPU drivers (blobs) on desktop and after that it will be easier to agree/disagree with that statement. For now i would not be comfortable to put Ubuntu Rolling (current RR development release) on PC from regular PC users i know. If only FOSS drivers coudl be used (Intel and some AMD) then maybe it could work but until then (Mir) i think latest Ubuntu LTS release or interim releases are better suited for regular users and probably are more stable too.

---

### Post by craig10x on 2013-04-04
zika has a good point there...:)
except for a few "glitches" along the way, 13.04 development has been more stable and bug free then my previously installed "stable" 12.10...

while i think i'd want to give a newbie to linux a regular release (like 12.04 or 12.10 or 13.04 when it final releases) for someone who has been using linux and/or ubuntu for a while, i am getting the impression that ubuntu RR development would be ok to use for a main system for us more "seasoned" users...when an occasional glitch comes along, with a bit of feedback from other users we seem to usually figure out how to solve it...and the occasional minor breakage (like when i lost my vlc sound) seems to get fixed pretty quickly on the ubuntu end...

---

### Post by EgoGratis on 2013-04-04
> zika has a good point there...:smile:
except for a few "glitches" along the way, 13.04 development has been  more stable and bug free then my previously installed "stable" 12.10...

I don't share that enthusiasm i think RR is OK for "development release" expectations but then the reality kicks in.

Bugs:
[http://ubuntuforums.org/showthread.php?t=2121960](http://ubuntuforums.org/showthread.php?t=2121960)

GPU (blobs) driver issues support on "moving target" and lack of support for software that doesn't  comes directly from UCS... It's not production ready and Ubuntu 12.04 for example kicks RR (dev) a...

> while i think i'd want to give a newbie to linux a regular release (like  12.04 or 12.10 or 13.04 when it final releases) for someone who has  been using linux and/or ubuntu for a while, i am getting the impression  that ubuntu RR development would be ok to use for a main system for us  more "seasoned" users...when an occasional glitch comes along, with a  bit of feedback from other users we seem to usually figure out how to  solve it...and the occasional minor breakage (like when i lost my vlc  sound) seems to get fixed pretty quickly on the ubuntu end...                 

Yes 1% of "us geeks" would probably manage to pull this off and that is about it and other 99% need more "long-term" relationship. ;)

P.S. Love and caring and commitment and stability and Mir and Unity... ;)

---

### Post by EgoGratis on 2013-04-04
I will say it again Ubuntu needs to focus JUST on LTS for at least 18 months and do there what is possible then move further to next LTS. Ubuntu is operating system and not web browser.

P.S. Everything else is just for "us geeks" (interim included)!

---

### Post by Gyokuro on 2013-04-04
Maybe it is good to mimic the development of Debian - LTS is stable and testing for a rolling development with weekly snapshots to minimize the download amount for updated applications. I think with this approach you do not need the interim releases between LTS releases anymore.

---

### Post by craig10x on 2013-04-04
> **Gyokuro said:**
> Maybe it is good to mimic the development of Debian - LTS is stable and testing for a rolling development with weekly snapshots to minimize the download amount for updated applications. I think with this approach you do not need the interim releases between LTS releases anymore.

Yes, and actually ubuntu development has daily iso images that are up to date...so when initially installing with it, you don't get hit with tons of updates...

I use to run LMDE (linux mint's debian version pointed to "testing") and actually had more problems over in that...ubuntu has managed to get the automated "quality control" process working to the point that updates in development have become pretty reliable...with only a "glitches" popping up occasionally...which are generally pretty easily straightened out...

---

### Post by Gyokuro on 2013-04-04
> **craig10x said:**
> Yes, and actually ubuntu development has daily iso images that are up to date...so when initially installing with it, you don't get hit with tons of updates...
I use to run LMDE (linux mint's debian version pointed to "testing") and actually had more problems over in that...ubuntu has managed to get the automated process working to the point that updates ain development have become pretty reliable...with only a "glitches" popping up occasionally...which are generally pretty easily straightened out...

I'm aware of the daily images which I used in my idea as snaphots - LMDE is using a semi-rolling approach as they have to make from time to time cuts to release their update packs and this approach is nice as you can take care that the binary gpu blobs work with the rolled out service pack.

---

### Post by jerrylamos on 2013-04-04
> **EgoGratis said:**
> ......Ubuntu is operating system and not (just a) web browser.
So I got a $199 Acer Chromebook which is really "just a web browser".  Rather pretty good and fast and convenient.  I got it because some people are running (chr)ubuntu on it, maybe I'll just use as is until I'm convinced some variant of ubuntu will support the nice graphics accelerator.

I'm not a "cloud" fan so it'll be interesting if the chromebook will be able to do offline office write & spread (& slides).  Google is resisant but there is a demand.  Personal opinion clouds are a great gift for hackers and identity theft and targeted marketing.....

So mostly running some sort of unstable ubuntu.  Amazing how quick my 10.10 Maverick (no longer supported) is on the same hardware as unity ubuntu.

---

### Post by Linux-one on 2013-04-05
Hi,
Why not follow this example:

**12-04 LTS** Released
12-12 Released (as 12-10)
13-08 (13-04 should be delayed)

**14-04 LTS** 
14-12
15-08
**16-04 LTS**
16-12
17-08
**18-04 LTS**
18-12
19-08
**20-04 LTS**
......

and so on.

---

### Post by jerrylamos on 2013-04-06
Since Beta 2 is out I'm usually looking for the next development, P, Q, R, (S?) to put into apt sources.list.  Is there going to be an S or not?  How does "rolling release" U+1 get started?

---

### Post by EgoGratis on 2013-04-06
Yes interim releases where not ditched and there will probably be "S". This is the reason i personally don't see the point in adding another "rolling flavour". 

In the end it might turn out you will not have to put anything in "sources.list" it will just "be rolling" to "S" but i could be wrong and that is about it!

---

### Post by craig10x on 2013-04-06
Yeah i would love to know how they are going to do the "rolling" (though not officially called that...lol again) U+1 release...when they voted at the conference to implement it, they mentioned that they had to figure out how exactly how they would do that...one developer did mention about a possible "symlink" but other then that we haven't heard anything since...

Not sure if the "symlink" or whatever method they use would be automatic or optional on development...and if optional, then whether you would do it by terminal command or it would be an add on to "software sources" that you would have to say, "check" to activate...i would think it would likely have to work one of those two ways...

Also, i wonder if they will have it implemented in by the time 13.04 is released...

---

### Post by EgoGratis on 2013-04-06
Probably it's so awesome they want to keep it for them self for a while. ;)

Next dev cycle is closing in and probably we will see soon what it's planed for it.

---

### Post by ronacc on 2013-04-06
somnolent sloth .

---

### Post by zika on 2013-04-06
[IMG]http://www.smartnetzone.com/wp-content/uploads/2012/07/sloth.jpg[/IMG]
or
[IMG]http://www.retireyoung.com.au/wp-content/uploads/2012/07/three-toed-sloth.jpg[/IMG]
or
[img]http://www.desibucket.com/db2/01/25702/25702.jpg[/img]
...?

---

### Post by craig10x on 2013-04-06
> **EgoGratis said:**
> Probably it's so awesome they want to keep it for them self for a while. ;)

LOL :D

Next dev cycle is closing in and probably we will see soon what it's planed for it.

Quite so...can't wait to see what it will be...

@zika:  sloth?  i like Raring Ringtail better....has a nice "ring to it"  he he

---

### Post by zika on 2013-04-06
> **craig10x said:**
> Quite so...can't wait to see what it will be...

@zika:  sloth?  i like Raring Ringtail better....has a nice "ring to it"  he he
Nothing could compare with the depth of this blye eyes daydreaming on the last picture... ;)

---

### Post by ventrical on 2013-04-09
> **jerrylamos said:**
> Since Beta 2 is out I'm usually looking for the next development, P, Q, R, (S?) to put into apt sources.list.  Is there going to be an S or not?  How does "rolling release" U+1 get started?

Let me know too.

---

### Post by philinux on 2013-04-09
Maybe we'll find out after May's UDS

[http://www.iloveubuntu.net/second-online-uds-officially-announced-between-may-14-16-2013](http://www.iloveubuntu.net/second-online-uds-officially-announced-between-may-14-16-2013)

---

### Post by craig10x on 2013-04-09
> **philinux said:**
> Maybe we'll find out after May's UDS

[http://www.iloveubuntu.net/second-online-uds-officially-announced-between-may-14-16-2013](http://www.iloveubuntu.net/second-online-uds-officially-announced-between-may-14-16-2013)

But wouldn't that conference be after they have already started development on 13.10?  I would think if they were going to add that new way to smoothly transition into the next development version, it would have to be announced before 13.10 development begins...how long after the final release date do they usually start the new version?

---

### Post by cpatrick08 on 2013-04-09
> **craig10x said:**
> But wouldn't that conference be after they have already started development on 13.10?  I would think if they were going to add that new way to smoothly transition into the next development version, it would have to be announced before 13.10 development begins...how long after the final release date do they usually start the new version?

I've upgraded to the dev release before on release day of the previous version

---

### Post by craig10x on 2013-04-09
In case that newer "path" isn't ready by release date, i was curious as to how you do it using the "upgrade" method, to continue on to the next development version (in this case, 13.10)?
and does it go smoothly?

---

### Post by ventrical on 2013-04-09
> **craig10x said:**
> In case that newer "path" isn't ready by release date, i was curious as to how you do it using the "upgrade" method, to continue on to the next development version (in this case, 13.10)?
and does it go smoothly?

Usually Cariboo will put up that information when it is available.

---

### Post by craig10x on 2013-04-09
Thanks ventrical :)
Though i am still hoping they'll have that "new way" available by then...

---

### Post by craig10x on 2013-04-10
I was just wondering, in case they don't have that "new way" of moving from ubuntu 13.04 development to 13.10 development by the final release time, as far as doing it by upgrading, someone mentioned it is just one terminal command...i was searching around a bit online and it was mentioned that it would be done with this command and i was wondering if that is how it is done, and what you do after that: 
 [B]do-release-upgrade -d



[/B]

---

### Post by EgoGratis on 2013-04-10
On desktop preferred/recommended way is this command:

update-manager -d

It's all done in GUI and the command you posted is preferred/recommended way on server/command line:

sudo apt-get install update-manager-core
sudo do-release-upgrade -d

Basically both way can be used on Ubuntu desktop. Some users manually change sources.list file for example... 

P.S: It depends in the end how much of an geek is in you but in no way is this process/procedure hard to do in my opinion in a way rolling would be needed to simplify the procedure.

---

### Post by craig10x on 2013-04-10
Oh..very cool...so you could actually do it with just the one command?:
update-manager-d     nothing else to do?  

The way they are supposed to do it is probably with a "symlink" or something similar...but i imagine you would still have to enter some command in the terminal or perhaps check an extra box in software sources...i don't think they will have it turned on by default, as some may just want to let it finalize and not move on to the next version...but instead of an upgrade, it would simply point to the new updates for the next version (with no upgrading needed)....

---

### Post by EgoGratis on 2013-04-10
> Oh..very cool...so you could actually do it with just the one command?:
update-manager-d     nothing else to do?

Yes it opens up GUI interface and you click on button and upgrade. Using the same procedure you would upgrade Ubuntu 12.10 to Ubuntu 13.04 (final release).

When upgrading to development relese GUI sometimes fails and probably because of that it's quite common to upgrade to development release with command line option. 

> The way they are supposed to do it is probably with a "symlink" or  something similar...but i imagine you would still have to enter some  command in the terminal or perhaps check an extra box in software  sources...i don't think they will have it turned on by default, as some  may just want to let it finalize and not move on to the next  version...but instead of an upgrade, it would simply point to the new  updates for the next version (with no upgrading needed).... 				

Probably once you will upgrade to development release this will be it (always on development release from that point on). This is how i understand the proposal. 

Original proposal was to drop interim releases and have only this + LTS and because interim releases are here to stay for now i see the whole thing as an experiment and if it goes OK then interim releases might be ditched. Well see how it goes and this could change in the future and something completly different could be introduced.

---

### Post by craig10x on 2013-04-10
Yes, probably that will be the way they will do it...

Ok, and just to clarify then, while you could do the development upgrade with that one command and using the update manager's gui, it is recommended to use the alternate method (two terminal commands you gave) because it is usually the more reliable... instead?

also, how do these upgrades in development usually go?  are they smooth?
[COLOR=#000000]
sudo apt-get install update-manager-core[/COLOR]
[COLOR=#000000]sudo do-release-upgrade -d

This is my first time using development, so i am trying to learn [/COLOR];)

---

### Post by EgoGratis on 2013-04-10
It depends. I do imagine users of development release do want some excitement and to see things brake occasionally and the obvious choice is first to try the GUI. If it breaks then it's much more fun to open the terminal and clean the mess. ;)

Jokes aside in the past GUI failed quite often for me not only upgrading but doing regular daily updates on development release especially at the beginning of the development cycle but it might work more reliable these days. That said you really can try both procedures on Ubuntu desktop or to manually change things in sources.list file with sed command but this procedure might be different this time because we don't quite know how will next development release look like and i don't find Ubuntu development releases production ready i use LTS or interim releases for my daily work and development release only for some fun!

---

### Post by EgoGratis on 2013-04-10
Everything i said but in pictures:

[http://www.ubuntubuzz.com/2013/03/how-to-upgrade-ubuntu-1210-quantal.html](http://www.ubuntubuzz.com/2013/03/how-to-upgrade-ubuntu-1210-quantal.html)
[http://www.ubuntubuzz.com/2013/04/upgrade-via-terminal-yet-another-way-to.html](http://www.ubuntubuzz.com/2013/04/upgrade-via-terminal-yet-another-way-to.html)

P.S. But we don't know if any changes will be made in future development release and things could change!

---

### Post by craig10x on 2013-04-10
That is excellent...though i like the gui method better then the terminal...i find that first part about finding that file in text editor a bit confusing...the rest would be easy...

I'm actually this as my sole system...up to now (except for a few glitches that weren't too difficult to deal with)...it has been great...i might eventually go LTS to LTS instead (starting with 14.04) but until the, i'd love to be able to roll until we reach it...

---

### Post by ventrical on 2013-04-11
> **EgoGratis said:**
> On desktop preferred/recommended way is this command:

update-manager -d

It's all done in GUI and the command you posted is preferred/recommended way on server/command line:

sudo apt-get install update-manager-core
sudo do-release-upgrade -d

Basically both way can be used on Ubuntu desktop. Some users manually change sources.list file for example... 

P.S: It depends in the end how much of an geek is in you but in no way is this process/procedure hard to do in my opinion in a way rolling would be needed to simplify the procedure.


 But we still may have to wait for the toolchain to be uploaded and/or the code name of the next cycle for anything to work. We have to change /raring/ to /new_name_here/ in the sources.list.  What is it? I don't know. There may even be a new convention involved if they go rolling.

---

### Post by ronacc on 2013-04-11
hopefully when the time comes someone will convey the necessary information down to we poor and huddled masses .

---

### Post by grahammechanical on 2013-04-12
> [COLOR=#000000]also, how do these upgrades in development usually go? are they smooth?[/COLOR]

At the start of the development cycle there is not much of a code difference between the newly completed release and an installation of the new release that has had its repositories renamed to the development release code name. The switch is usually without problems for that reason. Once ISO images become available I would recommend using one of those images to put in a development branch installation. The code difference may be too great not to cause problems.

It is wise to have a stable release that could be used as a standby OS in case things break. Which has happened during both the Quantal and the Raring cycles. In fact during this cycle I have had to use 12.04 to burn ISO images because for most of the time my Raring install would not detect a disk in the DVD drive, not even an audio disk.

From here on in anyone who installs an interim release will need to upgrade every six months. It is no longer possible to by-pass a release or two. Otherwise they will be using an End of Life operating system for 3 months while waiting for the next release. That or take the backward step of installing an older LTS release.

On this I agree with Mark. If you want stability - install the LTS. If you want bleeding edge - install the development branch. 

Regards.

---

### Post by craig10x on 2013-04-12
Thank you grahammechanical...that was quite informative...if i follow you correctly, are you saying that you should use a daily build iso of the new version (in this case, 13.10) to have it upgrade the current 13.04 development we are running, rather then doing the upgrade directly from our 13.04 installation? That it would be safer that way?  And if you do that, does it transfer over all the stuff you have installed already?

Regarding the rest...yeah, i agree, now that the support time for interim releases has been cut to 9 months, it does kind of make it necessary to re-install every 6 months (not that i wasn't doing that already...lol)..
So choice is really re-install every 6 month...or go LTS to LTS and re-install just once every 2 years...or run Development (and keep your fingers crossed along the way...double LOL)... ;)

By the way, there is a slight possibility they may have that new method of moving into the next development ready when 13.04 goes final, but of course we haven't heard anything yet...though maybe something will be announced close to release date (April 25th)...

I've been a bit daring i guess..i am have been running 13.04 development exclusively with no dual boot back up...was 13.04 rougher in it's early stages?  Since i installed 2 months ago, nothing has come along that i couldn't handle and for the most part, the updates have been very reliable for me...

---

### Post by cariboo on 2013-04-12
I honestly don't think we'll see the change to a rolling type release until 14.04, there have to be many things put into place before that can happen, and I can see Canonical wanting to push Mir and Unity Next out the door before making the needed changes.

That being said, grahammechanical's method to start with is the only way to upgrade to the next version, when the toolchain is first uploaded. I haven't paid any attention to when an upgrade via upgrade-manager becomes available, but to me it normally doesn't happen for the first couple of months of the development cycle

---

### Post by serdotlinecho on 2013-04-12
[TL;DR]Yawn...just give me SS archives and I will edit sources.list(business as usual...). I'm bored now. :-({|=[/TL;DR]

---

### Post by grahammechanical on 2013-04-12
I have just brought another hard disk and I have been pondering how to use it in testing. I have decided to follow the practice of one forum user of having  not only a separate / and /home partitions (as now) but also a separate data partition. I know I will need to edit the fstab file to do this. So, this is the partitioning scheme of my new 500GB hard disk.

sdb1 = 20GB primary mount point / 13.04 installed
sdb2 = Extended partition of the rest of the disk
sdb5 = 20GB logical mount point /home for the 13.04
sdb9 = 361GB logical to be Data partition

This 13.04 will be my standby OS and upgrade every six months until 14.04.

sdb 7 & 8 = 20GB each to be / & /home respectively of a new 13.04 install that I will put in after release day and convert to 13.10 (or whatever) when the tool chain is loaded by using the sed command. That will be my development branch and I will edit the fstab file so that it can access the data partition of sdb9

sdb6 = 2GB = swap

What I need to do now is transfer over to the new drive my data files and stuff and work out how I am going to use the old drive for testing.

I have never been able to safely test the Install alongside option. Now, I might be able to. I have a download of Windows 8 preview that I have never tried. I might install that and then test the Install Alongside option using the old drive for this.

Regards.

---

### Post by craig10x on 2013-04-12
I was just curious....is it safer to say, go from 13.04 final to 13.10 final (in October when it is available) instead of going 13.04 development to 13.10 development?

I am trying to figure out a way i can run 13.04 through 13.10 without having to re-install...my goal is to make it to 14.04, when i probably will go to a LTS to LTS cycle instead...
I don't want to go back to 12.04 at this point, because i love 13.04 and also some major bugs i experienced in both 12.04 and 12.10 are no longer present in 13.04...

Which way is likely to go smoother?

---

### Post by grahammechanical on 2013-04-12
On condition that you have a stand by Ubuntu and your data is safe from a re-install, then the answer is Yes. Just keep changing the repository names. First at the start of May (13.10 dev), then at the start of November (14.04 dev). That should get you to 14.04. I am going to do the same with this 13.04 that I just installed in my new hard drive.

There will no doubt be a post in this section announcing when the tool chain has been put in the repositories. Keep watching.

---

### Post by ventrical on 2013-04-12
> **cariboo907 said:**
> I honestly don't think we'll see the change to a rolling type release until 14.04, there have to be many things put into place before that can happen, and I can see Canonical wanting to push Mir and Unity Next out the door before making the needed changes.

That being said, grahammechanical's method to start with is the only way to upgrade to the next version, when the toolchain is first uploaded. I haven't paid any attention to when an upgrade via upgrade-manager becomes available, but to me it normally doesn't happen for the first couple of months of the development cycle

 Is there any definitive word on this, in regards to rolling release or no rolling release during the 13.10 cycle?

*edit*

Looks like 13.10 is already set up .

[https://launchpad.net/ubuntu/+milestone/ubuntu-13.10](https://launchpad.net/ubuntu/+milestone/ubuntu-13.10)

So just keep an eye there.

---

### Post by craig10x on 2013-04-12
Very good...i am not dual booting...however, i will burn an iso of 13.04 final before i upgrade to 13.10 on development (as a back up install disc)...i keep my data (photos, videos, music, documents, etc) on a flash drive and use that when i do a fresh install, so that preserves my "stuff" (and also saves a lot of work too)...

And from ventrical's link since they are getting 13.10 up, we probably will see something soon...

Oh, i had asked earlier: is it best to use a live session iso of 13.10 do upgrade of my installed 13.04?  (or just do it either by gui or terminal commands on the installed one)...if you do it with iso, does it preserve what you have on your current system?  (this is assuming they don't have the new easy way to roll into the next version by 13.04's release)...

---

### Post by ronacc on 2013-04-12
after a couple of disasters with the partitioner " going rouge "  I built a completely separate test box . I no longer allow a developement install ( any distro ) anywhere near my "work" system , not even to the extent of d/ling the iso to burn to a cd/dvd to run on the test box .

---

### Post by ventrical on 2013-04-12
> **craig10x said:**
> Very good...i am not dual booting...however, i will burn an iso of 13.04 final before i upgrade to 13.10 on development (as a back up install disc)...i keep my data (photos, videos, music, documents, etc) on a flash drive and use that when i do a fresh install, so that preserves my "stuff" (and also saves a lot of work too)...

And from ventrical's link since they are getting 13.10 up, we probably will see something soon...

Oh, i had asked earlier: is it best to use a live session iso of 13.10 do upgrade of my installed 13.04?  (or just do it either by gui or terminal commands on the installed one)...if you do it with iso, does it preserve what you have on your current system?  (this is assuming they don't have the new easy way to roll into the next version by 13.04's release)...

There will not be an .iso for several weeks. Wait for the 'toolchain' or watch the forums for messages from Cariboo907 and check here ;
[http://ubuntuforums.org/showthread.php?t=2073477](http://ubuntuforums.org/showthread.php?t=2073477)

for the latest.

Also..you can study this:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by craig10x on 2013-04-12
I will watch out for any developments...Also, i am sure Cairiboo907 and Phillinux will post anything new also...

Oh, yeah, i was wondering....do you have to temporarily uncheck your ppas when you do an upgrade?
I don't have a lot...only 2 actually...Google Chrome and also webupd8.org's ppa for updating Oracle Java (that one does say "Raring Ringtail" in the ppa...Chrome's does not of course)...

Also, you know the simplest way they could have development transition, is to just continue calling it (in development) the same name...true?  (in the case of what we are running, that would be Ringing Ringtail...so...just in development...Raring Ringtail would be 13.04, 13.10, 14.04, etc...)....point releases would continue the new names of course...In fact, i think Mark Shuttleworth has suggested that...

---

### Post by cariboo on 2013-04-12
> **craig10x said:**
> I will watch out for any developments...Also, i am sure Cairiboo907 and Phillinux will post anything new also...

Oh, yeah, i was wondering....do you have to temporarily uncheck your ppas when you do an upgrade?
I don't have a lot...only 2 actually...Google Chrome and also webupd8.org's ppa for updating Oracle Java (that one does say "Raring Ringtail" in the ppa...Chrome's does not of course)...

Also, you know the simplest way they could have development transition, is to just continue calling it (in development) the same name...true?  (in the case of what we are running, that would be Ringing Ringtail...so...just in development...Raring Ringtail would be 13.04, 13.10, 14.04, etc...)....point releases would continue the new names of course...In fact, i think Mark Shuttleworth has suggested that...

The update-manager should disable the ppas, but just in case it may be an idea to disable them before starting update-manager.

---

### Post by serdotlinecho on 2013-04-13
> **ventrical said:**
> There will not be an .iso for several weeks. Wait for the 'toolchain' or watch the forums for messages from Cariboo907 and check here ;
[http://ubuntuforums.org/showthread.php?t=2073477](http://ubuntuforums.org/showthread.php?t=2073477)

for the latest.

Also..you can study this:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)


Also learn how to chroot ;)

---

### Post by craig10x on 2013-04-16
I was just curious... two questions:

1) I was looking at the release schedule for 13.04 and it shows a RC (release candidate) scheduled for this thursday (April 18th)...does that mean the regular ubuntu 13.04 w/unity will have an actual RC on thursday? 

2) Also, if someone has an install for 13.04 final (after next thursday) if he should decide that he would like to have it follow "development" and upgrade it to 13.10 development, would he use the same method that you use to upgrade 13.04 development to 13.10 development?....

Thanks ;)

---

### Post by serdotlinecho on 2013-04-16
I'm waiting for SS [archive]("http://archive.ubuntu.com/ubuntu/dists/") ;)

---

### Post by sgage on 2013-04-17
Is it known, definitively, just what the release scenario is going to be as we go forward? IMO, this whole issue has been clouded with contradictory statements from various parties for weeks now. 

How long is Raring going to be supported?

Is there going to be an "SS"?

What does "rolling release" even mean in the context of what various parties have been saying recently? I've heard a few different scenarios...

Somebody needs to lay down the smack, and describe in clear and detailed language just what the plan is, because this much uncertainty is not good for a project that wants to be taken seriously. I am not in the loop, and maybe things are being decided, buttons being pressed and knobs twiddled, but right now there just seems to be a lot of ???

---

### Post by ventrical on 2013-04-17
> **grahammechanical said:**
> I have just brought another hard disk and I have been pondering how to use it in testing. I have decided to follow the practice of one forum user of having  not only a separate / and /home partitions (as now) but also a separate data partition. I know I will need to edit the fstab file to do this. So, this is the partitioning scheme of my new 500GB hard disk.

sdb1 = 20GB primary mount point / 13.04 installed
sdb2 = Extended partition of the rest of the disk
sdb5 = 20GB logical mount point /home for the 13.04
sdb9 = 361GB logical to be Data partition

This 13.04 will be my standby OS and upgrade every six months until 14.04.

sdb 7 & 8 = 20GB each to be / & /home respectively of a new 13.04 install that I will put in after release day and convert to 13.10 (or whatever) when the tool chain is loaded by using the sed command. That will be my development branch and I will edit the fstab file so that it can access the data partition of sdb9

sdb6 = 2GB = swap

What I need to do now is transfer over to the new drive my data files and stuff and work out how I am going to use the old drive for testing.

I have never been able to safely test the Install alongside option. Now, I might be able to. I have a download of Windows 8 preview that I have never tried. I might install that and then test the Install Alongside option using the old drive for this.

Regards.

  I installed Windows 8 Executive Toy Plaything-64bit and it worked real fast on my Acer Extensa Dual Core. I then proceeded to install Ubuntu alongside it and now  the 10 second start-up/shut down of Win 8  has been corrupted. Why . I have no idea. Also , raring will still not detect Radeon ATi cards properly, giving relics, distortions and phatoms in the Unity Dash.

---

### Post by ventrical on 2013-04-17
> **sgage said:**
> Is it known, definitively, just what the release scenario is going to be as we go forward? IMO, this whole issue has been clouded with contradictory statements from various parties for weeks now. 

How long is Raring going to be supported?

Is there going to be an "SS"?

What does "rolling release" even mean in the context of what various parties have been saying recently? I've heard a few different scenarios...

Somebody needs to lay down the smack, and describe in clear and detailed language just what the plan is, because this much uncertainty is not good for a project that wants to be taken seriously. I am not in the loop, and maybe things are being decided, buttons being pressed and knobs twiddled, but right now there just seems to be a lot of ???

bifurcation?

:)

---

### Post by sgage on 2013-04-17
> **ventrical said:**
> bifurcation?

:)

Who knows! But I would like to...

---

### Post by craig10x on 2013-04-17
I know what you mean, sgage...you would think they would make some announcements...this kind of information should actually be available at the ubuntu website...they should keep us up to date on what is going on...first there's the new 9 months support business...(at least that they said definitely starts with 13.04) but then the other things are kind of fuzzy...i still hear things about it going rolling by 14.04...then i read rolling is definitely out...and when is the "smooth transistion" from development to development supposed to go into effect?  On 13.04?  13.10? when?  how will it be done?  will it be done?
???????

---

### Post by sgage on 2013-04-17
> **craig10x said:**
> I know what you mean, sgage...you would think they would make some announcements...this kind of information should actually be available at the ubuntu website...they should keep us up to date on what is going on...first there's the new 9 months support business...(at least that they said definitely starts with 13.04) but then the other things are kind of fuzzy...i still hear things about it going rolling by 14.04...then i read rolling is definitely out...and when is the "smooth transistion" from development to development supposed to go into effect?  On 13.04?  13.10? when?  how will it be done?  will it be done?
???????

Exactly, craig10x. The Canonical powers that be need to clarify the plan, ASAP. People need to make decisions, and they need to know what to expect...

---

### Post by ventrical on 2013-04-17
I do know that Ubuntus want to distrubute across various form-factors with tablets and phones as priorities. Windows 8 is  , well, "years ahead " as far as working on both tablets, phones AND desktops. Actually the Win 8 almost functions just like gnome-shell. So with new Mir server comming I am thinking that there is a lot of scrambling in the back-rooms of Canonical to come up to par competetion with MS. We are feeling the brunt of it now.  I guess we have to go one day at a time and see how it all pans out.

---

### Post by jerrylamos on 2013-04-17
> **ventrical said:**
> ... I am thinking that there is a lot of scrambling in the back-rooms of Canonical to come up to par competetion with MS. We are feeling the brunt of it now.  I guess we have to go one day at a time and see how it all pans out.
There'd better be a lot of scrambling.  I've got 10" tablet, 7" tablet, Chromebook each about 1 gHz processors.  They boot up in seconds, including connecting to my hidden wireless network, zoom I"m onto internet and into email, news, you name it.

Raring, with hardware that's much faster, seconds tick by.  Finally desktop up.  Ooops, disconnects from hidden wireless network (12.04.2 doesn't).  Manually select systems settings network.  Couple seconds later, get a drop down, select the only network showing.  oh, my, network out of range.  It's not.  Select it again, and after some seconds puts up the required encryption key etc. and asks If I want to connect.  I do.  Some seconds later connects.  Then I go back to desktop, unity launcher, and select firefox.  Which comes up after more seconds.

The Chromebook is long since up, I'm into composing email or viewing a video.....very nicely, on slower hardware than ubuntu has....

So I have choices.  My opinion, set ubuntu raring beside the tablets and chromebook, hit power on, and ubuntu better figure out how to match the competition.  

At my level of expertise, office write and spreadsheets I don't know how to do on the tablets and chromebook.

---

### Post by cariboo on 2013-04-17
You're forgetting one think jerrylamos , you aren't starting your tablet or chromebook from power-off, I know my Android tablet takes just as long as my computer to boot, when the power is completely turned off, when both devices are in sleep mode the difference is only a couple of seconds.

---

### Post by daKoolaid on 2013-04-17
> **jerrylamos said:**
> There'd better be a lot of scrambling. I've got 10" tablet, 7" tablet, Chromebook each about 1 gHz processors. They boot up in seconds, including connecting to my hidden wireless network, zoom I"m onto internet and into email, news, you name it.

Raring, with hardware that's much faster, seconds tick by. Finally desktop up. Ooops, disconnects from hidden wireless network (12.04.2 doesn't). Manually select systems settings network. Couple seconds later, get a drop down, select the only network showing. oh, my, network out of range. It's not. Select it again, and after some seconds puts up the required encryption key etc. and asks If I want to connect. I do. Some seconds later connects. Then I go back to desktop, unity launcher, and select firefox. Which comes up after more seconds.

The Chromebook is long since up, I'm into composing email or viewing a video.....very nicely, on slower hardware than ubuntu has....

So I have choices. My opinion, set ubuntu raring beside the tablets and chromebook, hit power on, and ubuntu better figure out how to match the competition. 

At my level of expertise, office write and spreadsheets I don't know how to do on the tablets and chromebook.


Tablets and Chromebooks run from internal SSDs, are you running Raring off of one too?

---

### Post by ventrical on 2013-04-18
> **jerrylamos said:**
> There'd better be a lot of scrambling.  I've got 10" tablet, 7" tablet, Chromebook each about 1 gHz processors.  They boot up in seconds, including connecting to my hidden wireless network, zoom I"m onto internet and into email, news, you name it.

Raring, with hardware that's much faster, seconds tick by.  Finally desktop up.  Ooops, disconnects from hidden wireless network (12.04.2 doesn't).  Manually select systems settings network.  Couple seconds later, get a drop down, select the only network showing.  oh, my, network out of range.  It's not.  Select it again, and after some seconds puts up the required encryption key etc. and asks If I want to connect.  I do.  Some seconds later connects.  Then I go back to desktop, unity launcher, and select firefox.  Which comes up after more seconds.

The Chromebook is long since up, I'm into composing email or viewing a video.....very nicely, on slower hardware than ubuntu has....

So I have choices.  My opinion, set ubuntu raring beside the tablets and chromebook, hit power on, and ubuntu better figure out how to match the competition.  

At my level of expertise, office write and spreadsheets I don't know how to do on the tablets and chromebook.


On my Acer Extensa 4420 laptop (non-touch), AMD AthlonX2, 120GB SATA, 3GB/DDR2 Win 8-64bit is COLD started, running and network up in 9 seconds. (That does not include the time it takes me to type in my password). 6 Seconds to shut down. I removed all power and battery first and replaced before COLD start. Win 8 has a sort of gnome-shell/compiz/ring-shifter type desktop and works great on older desktops and laptops as well.  All that raring  is currently aspiring to morph into is accomplished with Win 8.  I did do a sideXside install. I thought there was a boot corruption error but that was a wrong assumption on my part. Ubuntu is still my core OS on all of my machines as I know win 8 will eventually regress with updates, malware etc...but at current  the  ball is now in Ubuntu's court as far as start-up and shut down times are concerned, especially with older machines.  A wise move by MicroSoft to include all those older laptops to work with Win 8.  They did not forget where they came from.

---

### Post by craig10x on 2013-04-18
When the first daily build isos come out for 13.10, couldn't you use that to upgrade from 13.04 development to 13.10 development as well?  
I noticed when installing from a daily build a few days ago (on a friend's computer) that one of the options is to "upgrade"....

When you use that, does it carry over all your files (like videos, music, photos, documents) as well as all the programs you have installed?
And does it retain their settings?  (or do they return to their defaults)...
Is that a good way to upgrade?

Thanks :)

---

### Post by ventrical on 2013-04-18
> **craig10x said:**
> When the first daily build isos come out for 13.10, couldn't you use that to upgrade from 13.04 development to 13.10 development as well?  
I noticed when installing from a daily build a few days ago (on a friend's computer) that one of the options is to "upgrade"....

When you use that, does it carry over all your files (like videos, music, photos, documents) as well as all the programs you have installed?
And does it retain their settings?  (or do they return to their defaults)...
Is that a good way to upgrade?

Thanks :)


[B]aptitude update && aptitude  safe-upgrade

But you would have to download and install aptitude first.[/B]

---

### Post by arpanaut on 2013-04-18
Personally, my feeling is that all this "rolling release" business will be sorted during the Developer's Summit and we will all know after that.
I'm sure everyone's attention is focused on getting this release out and then decisions will be made.
Not much happens with the "Next Release" as far as packages go until after the Summit anyway.
To me it is not a big deal, we will know soon enough.

---

### Post by jerrylamos on 2013-04-19
> **daKoolaid said:**
> Tablets and Chromebooks run from internal SSDs, are you running Raring off of one too?

Yes.  SSD's help linux. SSD's really helps my wife's XP which she uses to support a couple websites with Dreamweaver, not available on linux.

Acer C710 acts like it is running from SSD.  It does have a 320 gb hard drive.  I don't know what goes on which.

---

### Post by kansasnoob on 2013-04-20
> **arpanaut said:**
> Personally, my feeling is that all this "rolling release" business will be sorted during the Developer's Summit and we will all know after that.
I'm sure everyone's attention is focused on getting this release out and then decisions will be made.
Not much happens with the "Next Release" as far as packages go until after the Summit anyway.
To me it is not a big deal, we will know soon enough.

+1!

I'm busy right now with the final round of QA testing ......... no time to worry about what's up next :)

---

