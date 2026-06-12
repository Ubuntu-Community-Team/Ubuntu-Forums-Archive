---
title: "Why do kernel upgrades invariably bork my machine?!"
date: 2009-08-04
forum: The Cafe
---

### Post by dpatel on 2009-08-04
It seems (almost) every time I do a kernel upgrade something falls over. When I went from 2.6.28-11 to -13 I found I had no sound at all (and still don’t so use -11 which still works OK). No doubt I have to upgrade ALSA or something…but I shouldn’t have to. And, also, when it went from -13 to -14 recently I found that it broke X completely – couldn’t get to login screen. So I just uninstalled it. But somehow it had effected my suspend which worked fine under -11 kernel. Not sure how -14 affected suspend under -11!

Don’t get me wrong, I love Linux and open source. And I think the people who work on it do a great job but I’m not clear why this occurs so often?

And, following on, why is it necessary for the frequent kernel upgrades? Security? And the question I’d really like to understand is how this differs from Microsoft’s updates – I don’t see updates to their kernel as such. And the updates they make don’t seem to have the same level of issues as do kernel upgrades in Linux. Is this due to more resource to test?

---

### Post by moster on 2009-08-04
Windows has hybrid kernel and linux monolithic. Linux is designed  like unix and unix is old like pharaonic tomb. Old design is one of downsides of linux.

I once had problem just like you, but I alter my system much before upgrade mess all up. Never find out why exactly.

---

### Post by Giant Speck on 2009-08-04
I don't think Microsoft updates the NT kernel except for with new releases of Windows, which is sad if you think about it (and if I'm even correct about it).

---

### Post by blueturtl on 2009-08-04
Are you using Ubuntu?

If you are, you should note that Ubuntu is very bleeding edge. A side effect to being bleeding edge is buggyness.

I've been around since 5.04 and I found that each update while improving on some things would break others previously working.

If you want a more stable experience you may want to try a more conservative distro like Debian. Debian is essentially Ubuntu, but less up-to-date and less hand-holding.

---

### Post by dpatel on 2009-08-04
> **blueturtl said:**
> 
you should note that Ubuntu is very bleeding edge.

I've been around since the time of Dapper and could understand things falling over then since it was still fairly new.

I didn't realise Ubuntu was bleeding edge though. Surely to encourage more adopters, Ubuntu should be less bleeding edge - certainly now after years of development??

---

### Post by moster on 2009-08-04
> **dpatel said:**
> I've been around since the time of Dapper and could understand things falling over then since it was still fairly new.

I didn't realise Ubuntu was bleeding edge though. Surely to encourage more adopters, Ubuntu should be less bleeding edge - certainly now after years of development??

That is why you have Ubuntu 8.4 LTS. 8.10, 9.4... are all "test" till next LTS  :)

edit:
If I want latest one ubuntu, but to be safest possible, I would update it only with critical updates.

---

### Post by dpatel on 2009-08-04
> **moster said:**
> 
edit:
If I want latest one ubuntu, but to be safest possible, I would update it only with critical updates.

Well, I tried that (tried to lock version on kernel) but the update-manager kept complaining that it couldn't do full update and I should do a 'partial upgrade' - got fed up so unlocked everything again.

I've learnt - the hard way - to do a backup before any significant update (kernel, hardware drivers, etc)

---

### Post by kpkeerthi on 2009-08-04
I've never had breakages with Jaunty upgrades. It looks to me that you have **version specific dependent module packages **installed. You should install version independent module packages so any updates to the kernel packages will bring in the corresponding updated module packages.

For instance, if you have **linux-restricted-modules** installed, updates to **linux-image-generic** (kernel) will automatically bring in the corresponding restricted modules updates. On the other hand, if you have **linux-restricted-modules-2.6.28-14-generic** then updates to next **linux-image** will not bring in the required updated version of **linux-restricted-module** package.

Note: I used linux-restricted-modules just as an example. Depending on your hardware the you might be using one or more **modules** packages.

Oh btw.. Ubuntu is not Bleeding Edge.

---

### Post by moster on 2009-08-04
I think solaris has that option to "undo" patches. Maybe this is not so relevant to you but... :)

---

### Post by RiceMonster on 2009-08-04
> **blueturtl said:**
> Ubuntu is very bleeding edge.

Not really. Even Fedora is much more bleeding edge, and that's not rolling release.

---

### Post by moster on 2009-08-04
> **kpkeerthi said:**
> 
Oh btw.. Ubuntu is not Bleeding Edge.

Why you think Ubuntu 9.4 is not bleeding edge? Kernel 2.6.31 rc4 is OVER edge.

---

### Post by kpkeerthi on 2009-08-04
> **moster said:**
> Why you think Ubuntu 9.4 is not bleeding edge? Kernel 2.6.31 rc4 is OVER edge.
9.4? Haven't heard of such Ubuntu release. If you mean 9.04 (Jaunty), then its definitely not bleeding edge. The kernel version in Jaunty's repository is [2.6.28.14.19]("http://packages.ubuntu.com/jaunty/linux-image-generic")

---

### Post by Skripka on 2009-08-04
> **RiceMonster said:**
> Not really. Even Fedora is much more bleeding edge, and that's not rolling release.

Yep running 2.6.30-ARCH, which we call "stable".

---

### Post by dpatel on 2009-08-04
> **kpkeerthi said:**
> I've never had breakages with Jaunty upgrades. It looks to me that you have **version specific dependent module packages **installed. You should install version independent module packages so any updates to the kernel packages will bring in the corresponding updated module packages.

For instance, if you have **linux-restricted-modules** installed, updates to **linux-image-generic** (kernel) will automatically bring in the corresponding restricted modules updates. On the other hand, if you have **linux-restricted-modules-2.6.28-14-generic** then updates to next **linux-image** will not bring in the required updated version of **linux-restricted-module** package.

Note: I used linux-restricted-modules just as an example. Depending on your hardware the you might be using one or more **modules** packages.

Oh btw.. Ubuntu is not Bleeding Edge.

Interesting - yes I use restricted drivers (due to Nvidia graphics card) but I've not consciously picked dependent modules (in fact, I wasn't aware there were dependent or independent modules). I'll check when I get to my Linux machine.

How could I have started using dependent modules? Is is because I installed NVidia binaries directly or using Envy?

---

### Post by Viva on 2009-08-04
I've had some problems with kernel upgrades with Hardy, but every upgrade has smooth in Jaunty. As for the microsoft updates, isn't one of criticisms of microsoft that they don't patch bugs regularly?

---

### Post by RiceMonster on 2009-08-04
> **Viva said:**
> As for the microsoft updates, isn't one of criticisms of microsoft that they don't patch bugs regularly?

Yes, but the OP's problem is the patches are causing problems for them.

---

### Post by kpkeerthi on 2009-08-04
> **dpatel said:**
> 
How could I have started using dependent modules? Is is because I installed NVidia binaries directly or using Envy?
See? No wonder why your X broke after a kernel update. Install [nvidia with dkms]("http://ubuntuforums.org/showthread.php?t=1036788") and you should be fine.

---

### Post by Viva on 2009-08-04
> **dpatel said:**
> And the question I’d really like to understand is how this differs from Microsoft’s updates – I don’t see updates to their kernel as such.

> **RiceMonster said:**
> Yes, but the OP's problem is the patches are causing problems for them.

Yes, but I was answering this question.

---

### Post by Viva on 2009-08-04
I have had problems with kernel upgrades when I used envy too, but that was in Hardy.

---

### Post by blueturtl on 2009-08-04
Let's not start a feud over this guys. :)

A six month release cycle is what makes Ubuntu so 'shiny'.
I noticed that Dapper (which was delayed two months) was considerably less buggy than other Ubuntu releases. The Ubuntu team doesn't have very much time to test after the so called feature freeze.

I think Ubuntu is actually reconstructed from Debian Unstable every 6 months (as opposed to being built on top of the old Ubuntu). Can someone say if this is correct?

Anyway, I've also noticed that some types of system configurations are a lot more likely to have trouble with Ubuntu than others. Some systems are rock solid throughout their lives, with some every batch of updates seems to break something.

---

### Post by Viva on 2009-08-04
> **blueturtl said:**
> Let's not start a feud over this guys. :)

A six month release cycle is what makes Ubuntu so 'shiny'.
I noticed that Dapper (which was delayed two months) was considerably less buggy than other Ubuntu releases. The Ubuntu team doesn't have very much time to test after the so called feature freeze.

I think Ubuntu is actually reconstructed from Debian Unstable every 6 months (as opposed to being built on top of the old Ubuntu). Can someone say if this is correct?

Anyway, I've also noticed that some types of system configurations are a lot more likely to have trouble with Ubuntu than others. Some systems are rock solid throughout their lives, with some every batch of updates seems to break something.

Really? Dapper was awful on my computer. I almost left ubuntu after Dapper. Thank **** I didn't:twisted:

---

### Post by moster on 2009-08-04
> **kpkeerthi said:**
> 9.4? Haven't heard of such Ubuntu release. If you mean 9.04 (Jaunty), then its definitely not bleeding edge. The kernel version in Jaunty's repository is [2.6.28.14.19]("http://packages.ubuntu.com/jaunty/linux-image-generic")

> **Skripka said:**
> Yep running 2.6.30-ARCH, which we call "stable".

What are you saying? that Ubuntu has "old fart" kernel? Of course it is older NOW. But when Jaunty came out it was newest as possible. At least in time of freezing. This is not rolling release as your Arch.

It is bleeding edge as possible but not rolling release.

---

### Post by RiceMonster on 2009-08-04
> **moster said:**
> What are you saying? that Ubuntu has "old fart" kernel? Of course it is older NOW. But when Jaunty came out it was newest as possible. At least in time of freezing. This is not rolling release as your Arch.

It is bleeding edge as possible but not rolling release.

Try Fedora; not rolling release, 6 month release cycle, more bleeding edge than Ubuntu.

Ubuntu may be a more up to date distro, but I wouldn't call it bleeding edge. Especially considering the fact that they do version freezing.

---

### Post by Skripka on 2009-08-04
> **moster said:**
> What are you saying? that Ubuntu has "old fart" kernel? Of course it is older NOW. But when Jaunty came out it was newest as possible. At least in time of freezing. This is not rolling release as your Arch.

It is bleeding edge as possible but not rolling release.

No it is NOT "bleeding edge".  

It just isn't-I don't know what I can say that has not already been said to convey this lesson to you.  At time of package freeze there was already the 2.26.29 kernel out--Jaunty is STILL only on 2.26.28 IIRC.  Ubuntu is NOT bleeding edge.

---

### Post by kpkeerthi on 2009-08-04
Ubuntu is not bleeding edge. Its package versions are frozen once a release is officially made. Only security updates make into the repository. It doesn't keep up with the current upstream release.

Arch is a rolling distro and is bleeding edge.

Fedora does not roll but bleeding edge. Unlike Ubuntu, a Fedora release will receive package updates through its lifetime.

---

### Post by moster on 2009-08-04
> **Skripka said:**
> No it is NOT "bleeding edge".  

It just isn't-I don't know what I can say that has not already been said to convey this lesson to you.  At time of package freeze there was already the 2.26.29 kernel out--Jaunty is STILL only on 2.26.28 IIRC.  Ubuntu is NOT bleeding edge.

Ubuntu being bleeding edge is not something I made up. Shuttleworth said so in his interview. Maybe you should sent him email and inform him :D

get outta here :D

---

### Post by kpkeerthi on 2009-08-04
> **moster said:**
> Ubuntu being bleeding edge is not something I made up. Shuttleworth said so in his interview. Maybe you should sent him email and inform him :D

get outta here :D
Where? link please.

---

### Post by RiceMonster on 2009-08-04
> **moster said:**
> Ubuntu being bleeding edge is not something I made up. Shuttleworth said so in his interview. Maybe you should sent him email and inform him :D

get outta here :D

Oh, well that changes EVERYTHING!

---

### Post by ukripper on 2009-08-04
> **moster said:**
> Ubuntu being bleeding edge is not something I made up. Shuttleworth said so in his interview. Maybe you should sent him email and inform him :D

get outta here :D

Where is the link to support your claim?

---

### Post by Barrucadu on 2009-08-04
Ubuntu is not bleeding edge because the packages are old. Nothing anybody says can change that.

---

### Post by moster on 2009-08-04
> **ukripper said:**
> Where is the link to support your claim?

[https://wiki.ubuntu.com/MarkShuttleworth](https://wiki.ubuntu.com/MarkShuttleworth)

---

### Post by Skripka on 2009-08-04
> **moster said:**
> [https://wiki.ubuntu.com/MarkShuttleworth](https://wiki.ubuntu.com/MarkShuttleworth)

It is extra funny when someone in the computer world puts a shoe store in their mouth with a comment that they really ought to know better than to say or type.

---

### Post by Keyper7 on 2009-08-04
> **moster said:**
> Ubuntu being bleeding edge is not something I made up. Shuttleworth said so in his interview. Maybe you should sent him email and inform him :D

I agree, why let something irrelevant as **facts** get in the way of what an important person said?

---

### Post by nothingspecial on 2009-08-04
> **kpkeerthi said:**
> 
Oh btw.. Ubuntu is not Bleeding Edge.

It can be, if you want - although I wouldn`t recommend it.

```
## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.30-02063003-generic
uuid            0f69107c-3df5-4078-9338-f57e571689b6
kernel          /boot/vmlinuz-2.6.30-02063003-generic root=UUID=0f69107c-3df5-4078-9338-f57e571689b6 ro quiet splash 
initrd          /boot/initrd.img-2.6.30-02063003-generic
quiet

```

---

### Post by moster on 2009-08-04
> **Skripka said:**
> It is extra funny when someone in the computer world puts a shoe store in their mouth with a comment that they really ought to know better than to say or type.

It is extra funny when somebody install arch and conclude that world knowledge melt into his brain :D

---

### Post by RiceMonster on 2009-08-04
> **moster said:**
> It is extra funny when somebody install arch and conclude that world knowledge melt into his brain :D

What a relevant counter argument.

---

### Post by FuturePilot on 2009-08-04
> **dpatel said:**
> 
Is is because I installed NVidia binaries directly or using Envy?

There's your problem. Don't install the Nvidia driver manually. Use the package in the repositories that is specifically designed for Ubuntu and you won't have breakage.

---

### Post by moster on 2009-08-05
> **RiceMonster said:**
> What a relevant counter argument.

What is your argument on thinking that you are one of smartest people in whole world and nobody can change your opinion?

You are in stage that you do not know, that you do not know.

---

### Post by Skripka on 2009-08-05
> **moster said:**
> What is your argument on thinking that you are one of smartest people in whole world and nobody can change your opinion?

You are in stage that you do not know, that you do not know.

Just because Mark Shuttleworth has a _weird and completely absurd_ definition of "bleeding edge" that _NO ONE else in the linux community shares_ does not mean that he is right and everyone else is wrong.

---

### Post by &#32 Greg on 2009-08-05
> **moster said:**
> What is your argument on thinking that you are one of smartest people in whole world and nobody can change your opinion?

**You are in stage that you do not know, that you do not know.**

Wait- what?

---

### Post by SunnyRabbiera on 2009-08-05
well rather  if ubuntu is bleeding edge or not I use what works :D

---

### Post by moster on 2009-08-05
> **Skripka said:**
> Just because Mark Shuttleworth has a _weird and completely absurd_ definition of "bleeding edge" that _NO ONE else in the linux community shares_ does not mean that he is right and everyone else is wrong.
If "everybody" means you and 15 year old RiceMonster, then you are right :D
> **  Greg said:**
> Wait- what?
Young people tend to think they know everything. But, how much they can really know in so little years of life.

---

### Post by Skripka on 2009-08-05
> **moster said:**
> If "everybody" means you and 15 year old RiceMonster, then you are right :D

Young people tend to think they know everything. But, how much they can really know in so little years of life.

I take it you have not noticed then how now one else on this forum of Ubuntu users has jumped to your defense, and agrees with you on this?  Yea--you're hopeless.

---

### Post by RiceMonster on 2009-08-05
> **moster said:**
> If "everybody" means you and 15 year old RiceMonster, then you are right :D

Young people tend to think they know everything. But, how much they can really know in so little years of life.

Actually, I'm 20 years old. Why you need to resort to personal attacks because multiple people disagreed with you is beyond me.

---

### Post by Chame_Wizard on 2009-08-05
At least the kernel works fine for me.

---

### Post by moster on 2009-08-05
> **Skripka said:**
> I take it you have not noticed then how now one else on this forum of Ubuntu users has jumped to your defense, and agrees with you on this?  Yea--you're hopeless.

Ok. It is 2:1 for you. You win =D>

> **RiceMonster said:**
> Actually, I'm 20 years old. Why you need to resort to personal attacks because multiple people disagreed with you is beyond me.

My intention is not to offend you.

What do you exactly expect from me? I see your nick, your cartoon avatar and you think you know better then creator of Ubuntu. If that is not childish, then childish do not exist.

---

### Post by Barrucadu on 2009-08-05
> **moster said:**
> What do you exactly expect from me? I see your nick, your cartoon avatar and you think you know better then creator of Ubuntu. If that is not childish, then childish do not exist.

It is possible for people to, you know, make mistakes. Which is what Shuttleworth did when he called Ubuntu bleeding edge. Simply being the main guy behind Ubuntu doesn't make him right.

---

### Post by moster on 2009-08-05
> **Barrucadu said:**
> It is possible for people to, you know, make mistakes. Which is what Shuttleworth did when he called Ubuntu bleeding edge. Simply being the main guy behind Ubuntu doesn't make him right.

Well, I tend to believe more to former debian developer and mastermind of ubuntu then a guy who is not yet allowed to drink :D

(and his arch buddy)

edit: This is last of me in this thread... we can go like this forever.

What I suppose to tell the OP, what is difference between LTS and later versions?! I should made something up? Or quoting somebody who made the damn thing.

---

### Post by &#32 Greg on 2009-08-05
> **moster said:**
> Well, I tend to believe more to former debian developer and mastermind of ubuntu then a guy who is not yet allowed to drink :D

(and his arch buddy)

Except that he's wrong. Arch Testing is bleeding edge. Debian Sid is bleeding edge. Ubuntu is not. It's more or less up to date, yes. But bleeding edge is the newest stuff now, and Ubuntu lacks that- as evidenced by a 2.6.28 kernel.

---

### Post by RiceMonster on 2009-08-05
> **moster said:**
> Well, I tend to believe more to former debian developer and mastermind of ubuntu then a guy who is not yet allowed to drink :D

Shockingly enough, I am old enough to drink. Amazing how laws differ around the world.

---

### Post by tjwoosta on 2009-08-05
> **dpatel said:**
> It seems (almost) every time I do a kernel upgrade something falls over. When I went from 2.6.28-11 to -13 I found I had no sound at all (and still don&#8217;t so use -11 which still works OK). No doubt I have to upgrade ALSA or something&#8230;but I shouldn&#8217;t have to. And, also, when it went from -13 to -14 recently I found that it broke X completely &#8211; couldn&#8217;t get to login screen. So I just uninstalled it. But somehow it had effected my suspend which worked fine under -11 kernel. Not sure how -14 affected suspend under -11!

Don&#8217;t get me wrong, I love Linux and open source. And I think the people who work on it do a great job but I&#8217;m not clear why this occurs so often?

And, following on, why is it necessary for the frequent kernel upgrades? Security? And the question I&#8217;d really like to understand is how this differs from Microsoft&#8217;s updates &#8211; I don&#8217;t see updates to their kernel as such. And the updates they make don&#8217;t seem to have the same level of issues as do kernel upgrades in Linux. Is this due to more resource to test?

I have always had the same problems with kernel upgrades in ubuntu, but with arch (which actually is bleeding edge) I have never had any issues at all in the year and a half that Ive been using it. So I dont think its an issue with linux itself, but more of a debian/ubuntu thing.

---

### Post by nothingspecial on 2009-08-05
> **  Greg said:**
> Except that he's wrong. Arch Testing is bleeding edge. Debian Sid is bleeding edge. Ubuntu is not. It's more or less up to date, yes. But bleeding edge is the newest stuff now, and Ubuntu lacks that- as evidenced by a 2.6.28 kernel.

All true and correct except that it is perfectly possible to use a later kernel if you wish, as I pointed out before.

---

### Post by &#32 Greg on 2009-08-05
> **nothingspecial said:**
> All true and correct except that it is perfectly possible to use a later kernel if you wish, as I pointed out before.

Of course you can configure any distro to be the absolute bleeding edge by downloading the necessary packages and compiling it. We're talking about the distro itself though, and Ubuntu just plain isn't bleeding edge.

---

### Post by nothingspecial on 2009-08-05
> **  Greg said:**
> Of course you can configure any distro to be the absolute bleeding edge by downloading the necessary packages and compiling it. We're talking about the distro itself though, and Ubuntu just plain isn't bleeding edge.

I`m not saying it is.

What I`m trying to point out is that Ubuntu can be bleeding edge if you want it to be, there`s nothing stopping you.

Yes some distros are "bleeding edge" by default, but that doesn`t mean ubuntu can`t be.

---

### Post by dmizer on 2009-08-05
This thread has gone way too far off on a tangent, and I'm seeing too many potentially flammable remarks.

Thread closed. Thank you for participating.

---

