---
title: "I'm offered a partial upgrade, what should I do?"
date: 2011-10-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2011-10-13
**Precise offers a partial upgrade, what should I do?**

During the past few Ubuntu development cycles, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a **Partial Upgrade** is, and why, in most cases, you'll want to avoid it.

**Summary or "I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**

If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most "Partial Upgrade" situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, simply wait and hold off the updates until things settle down. 

**Short Version or "Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**

Due to the fact that uploads to the repositories of the active development branch are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a "Partial Upgrade" is a dist-upgrade.

When testing development releases, most of the time, a "Partial Upgrade" is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a "Partial Upgrade" is necessarily warranted.


**Long Version or "I want to be a better tester! I care! Tell me more!"**

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a "Partial Upgrade" can offer to remove important packages due to missing dependencies.

Now, the key question: 

"How do I know whether a package is actually meant to be replaced or removed?"

There's more than one way:

Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to packages.ubuntu.com and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/precise/+source/package_name/+changelog](https://launchpad.net/ubuntu/precise/+source/package_name/+changelog)

where package_name is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.

Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the Precise-changes mailing list.

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, refer to the next post.

Check the build status information page for Ubuntu on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.

Do a forum search, or join the #ubuntu+1 channel on irc.freenode.net and ask around to see whether other people are having problems with the same package(s).

If you're still confused, simply wait and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.

A typical interaction with a package manager involves the following three steps:
You select some packages to be installed / removed / upgraded

The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions

You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. Don't do that. Review that list of changes.

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning the basics of using development releases is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

With thanks to 23meg
__________________

---

### Post by ranch hand on 2011-10-14
Seeing how I disable all possibility of UM doing a thing it would be hard to get such an offer.

If one does come along I am going to take it.  I have noticed that things break more reliably if you do.

---

### Post by cariboo on 2011-10-14
The only time I see update-manager during a testing cycle, is if I haven't updated a system for a couple of days. I personally use aptitude or synaptic a couple of times a day.

---

### Post by ranch hand on 2011-10-14
Well, if you don't want things to break that is probably the way to go.

I usually use apt-get but aptitude is a fine tool too,  Some of aptitudes functions are just hard to beat.

If folks want to use UM they really ought to check out the fine job it is doing upgrading from 11.04 to 11.10 and think what it may do on a truly unstable system.

---

### Post by effenberg0x0 on 2011-10-14
I think that if somebody is being kind enough to offer you something, it's not very polite to refuse.

Regards,
Effenberg

---

### Post by cariboo on 2011-10-14
> Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state.

I really wish that people would pay more attention to the above statement, but then, we can't get them to read the stickies either, unless it is pointed out to them. :)

---

### Post by effenberg0x0 on 2011-10-14
Yes... stickies and the Ubuntu Online Documentation. Both are invisible to a large part of users. I wonder if Ubuntu uses Analytics or something to measure hits to those pages.

---

### Post by fabricator4 on 2011-12-09
> **cariboo907 said:**
> 

```
https://launchpad.net/ubuntu/+source/package_name/+changelog
```

where package_name is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


A small correction, the address should apparently be:
```

https://launchpad.net/ubuntu/precise/+source/package_name/+changelog

```

Chris

---

### Post by cariboo on 2011-12-09
> **fabricator4 said:**
> A small correction, the address should apparently be:
```

https://launchpad.net/ubuntu/precise/+source/package_name/+changelog

```

Chris

Fixed it, thanks for the heads up.

---

### Post by 57990166419925142424 on 2012-02-05
If I click "Close" instead of "Partial Upgrade", can I then safely click "Install updates", or will that do a partial upgrade nevertheless?

---

### Post by howefield on 2012-02-05
> **57990166419925142424 said:**
> If I click "Close" instead of "Partial Upgrade", can I then safely click "Install updates", or will that do a partial upgrade nevertheless?

It will carry out the partial upgrade if you go ahead.

---

### Post by fabricator4 on 2012-02-05
> **howefield said:**
> It will carry out the partial upgrade if you go ahead.


No, it will only do a partial upgrade if he clicks yes to a partial upgrade.  When you close the dialogue box it will go back to the update screen with the "partial" items unticked.  It is then safe proceed with the update as only the items with all dependancies of the correct versions will be updated.

Chris

---

### Post by cariboo on 2012-02-05
The best practice if update manager offers a partial update is to not do the update, and wait a couple of hours, then update the repositories again and see if you are still offered a partial update.

---

### Post by TerryNewton on 2012-02-05
> **cariboo907 said:**
> The best practice if update manager offers a partial update is to not do the update, and wait a couple of hours, then update the repositories again and see if you are still offered a partial update.

...and if it still offers partial after some time, then (for the GUI crowd) fire up synaptic mark all upgrades to see what it wants to remove. Sometimes it's just wanting to replace an older version of something with a newer version - this just happened with an iced tea update and happens every so often due to the nature of development, sometimes old stuff has to go. Of course if it wants to remove half the system don't do it, wait until the repos straighten out. What I've been doing is if any doubt I write down the packages it wants to remove so if really needed I can add them back later (perhaps in recovery mode...).

The main thing though is never blindly confirm a partial update. The wording (IMO) isn't accurate. Should say it's going to remove stuff (and say what it's going to remove), this was very confusing at first.

---

### Post by prusswan on 2012-02-06
Is there any way to rollback/revert a partial upgrade? I made the mistake thinking that it should be possible to reinstall any missing packages, but now with Unity broken (NO panels) and gnome-session-fallback in dubious state (alt-right click not working), and after reading this thread, I guess I could use a quick rollback option if any :(

---

### Post by zika on 2012-02-06
Look in log of that upgrade and (try to) repair manually...

---

### Post by Holdolin on 2012-02-14
Hehe, now I come along and read this helpful thread.  Whilst I don't consider myself a novice user, I was lacking the understanding of how this system works.  A day or so ago, i did do a "partial upgrade"  while it did a great job of removing a lot of "old" packages, it forgot to put anything in it's place, hence causing me to re-insert my iso and re-install my VM.  (It basically removed most of my system..hehe)  So yes boys and girls, heed the warning, and you're much less likely to end up learning as I did  :P

Oh,thanks for posting it too  :)

---

### Post by Musmanno on 2012-02-16
I also unwittingly hit the partial upgrade. Luckily, it didn't go through. It told me it could not calculate the upgrade because Unity was marked for removal and is on the removal blacklist.

So I just updated the selections that were chosen after rejecting the partial upgrade offer. Everything went fine. A lot of the files that were not updated are compiz related.

---

### Post by nrundy on 2012-02-18
> **cariboo907 said:**
> **Precise offers a partial upgrade, what should I do?**

During the past few Ubuntu development cycles, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a **Partial Upgrade** is, and why, in most cases, you'll want to avoid it.


Does this advice apply to 10.04 as well? I've been getting prompts from Update Manager to do a "partial upgrade" in 10.04. Or does your advice only apply to 12.04 pre-stable builds?

---

### Post by PaulW2U on 2012-02-18
> **nrundy said:**
> Does this advice apply to 10.04 as well? I've been getting prompts from Update Manager to do a "partial upgrade" in 10.04. Or does your advice only apply to 12.04 pre-stable builds?

Warnings about partial upgrades apply to all versions and flavours of the Ubuntu family.

---

### Post by nrundy on 2012-02-18
> **PaulW2U said:**
> Warnings about partial upgrades apply to all versions and flavours of the Ubuntu family.

so just to summarize: if I get a partial upgrade prompt from Update Manager, I should not update but instead wait a few hours or maybe a day or two to see if it goes away. If after a couple days, the partial upgrade prompt is still there, then I need to investigate examine the packages, etc. this a good approach to take involving the least hassle?

---

### Post by zika on 2012-02-18
> **nrundy said:**
> so just to summarize: if I get a partial upgrade prompt from Update Manager, I should not update but instead wait a few hours or maybe a day or two to see if it goes away. If after a couple days, the partial upgrade prompt is still there, then I need to investigate examine the packages, etc. this a good approach to take involving the least hassle?If You try ```
sudo apt-get dist-upgrade
``` You will get a list of packages that would be: installed, removed, upgraded and from that You could decide what to do...
Before You are sure You want to accept, do not accept it. You can (always) exit with "q" and ask for another solution with "n"... "Y" is only for the case where You are completely sure...

---

### Post by Stinger on 2012-02-18
> **nrundy said:**
> so just to summarize: if I get a partial upgrade prompt from Update Manager, I should not update but instead wait a few hours or maybe a day or two to see if it goes away. If after a couple days, the partial upgrade prompt is still there, then I need to investigate examine the packages, etc. this a good approach to take involving the least hassle?

I did a partial upgrade yesterday to get the new unity, kernel, etc.
Before the upgrade I checked with synaptic that no vital parts were removed :shock:, like the ubuntu-desktop and unity packages and that all packages were marked as upgradable or replaceable.

But as said before be careful, I have previously ruined my installation twice because I thought that it was possible to do a partial upgrade.
I now use a separate /home-partition to avoid to much data-loss.

---

### Post by prusswan on 2012-02-18
very rarely, partial upgrades are necessary(?). I had this change causing all other upgrades to be held in update manager for some unknown reason (they don't seem to be related dependencies), until I decided it was a case of package rename and upgraded it anyway via synaptic:

```

Removed the following packages:
libubuntuone-1.0-1

Upgraded the following packages:
libubuntuoneui-3.0-1 (2.99.3-0ubuntu1) to 2.99.4-0ubuntu1

```

---

### Post by zika on 2012-02-18
> **prusswan said:**
> very rarely, partial upgrades are necessary(?)In U+1 they are not rare, at least in several of +1 periods I've followed...

---

### Post by prusswan on 2012-02-18
> **zika said:**
> In U+1 they are not rare, at least in several of +1 periods I've followed...

I mean it was impossible to proceed without going through that partial upgrade, the package(s) simply had to be removed with no possibility of upgrade

---

### Post by Gregory Lee on 2012-02-18
> **nrundy said:**
> so just to summarize: if I get a partial upgrade prompt from Update Manager, I should not update but instead wait a few hours or maybe a day or two to see if it goes away.
In my beginner's opinion, yes.  I started from a blank disk (well, there was a MS Windows 7 system there -- same as blank) just a few days ago, and so far, the problems that prevented updating all packages have gone away within a day.

---

### Post by Miykel on 2012-03-14
G'Day;  I had that message earlier today, just closed the notice then went to details and was told to run command

[ sudo apt-get -f install ]

 Run that and then installed the upgrade ..perfect.

Regards Miykel

---

### Post by cariboo on 2012-03-14
> **Miykel said:**
> G'Day;  I had that message earlier today, just closed the notice then went to details and was told to run command

[ sudo apt-get -f install ]

 Run that and then installed the upgrade ..perfect.

Regards Miykel

At this point in time (beta 1) the changes do't come as fast as they do earlier in the cycle, so in most cases:

```
sudo apt-get -f install
```

will solve the problem, but there have been points where the above command won't work for several days.

---

### Post by jasonsmith01 on 2012-03-23
I guess I've been extremely lucky since I've done no less than 5 partial upgrades on 12.04. I think all is okay so far.

I must say though as a new to Ubuntu user I just made the assumption that the Upgrade status could be trusted beta or not. Who would think to go searching the forums to check if a specific OS feature could be trusted or not, especially a fairly serious one. It's too bad that partial upgrades can't just be disabled in a non final build.

---

### Post by cariboo on 2012-03-23
> **jasonsmith01 said:**
> I guess I've been extremely lucky since I've done no less than 5 partial upgrades on 12.04. I think all is okay so far.

I must say though as a new to Ubuntu user I just made the assumption that the Upgrade status could be trusted beta or not. Who would think to go searching the forums to check if a specific OS feature could be trusted or not, especially a fairly serious one. It's too bad that partial upgrades can't just be disabled in a non final build.

If you read the sticky, you know that stopping partial upgrades automagically is virtually impossible.  Ubuntu uses a build farm to automate building packages, and at times it's impossible to finish building packages all at the same time.

---

### Post by galaxy710 on 2012-04-11
Great article with excellent idea! I appreciate your post. Thanks so much and let keep on  sharing your stuffs.

---

