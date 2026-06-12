---
title: "Why is 10.04 UNR not LTS?"
date: 2010-05-02
forum: The Cafe
---

### Post by Paddy Landau on 2010-05-02
10.04 is a long term support (LTS) release.

Except for the Ubuntu netbook remix (UNR).

Any idea why the UNR is excluded from LTS?

I will be upgrading all our computers to Ubuntu 10.04 or Xubuntu 10.04.

But what about the netbook? Should I...

[LIST]
[*]Upgrade the netbook to 10.04 UNR, and again when we get the next UNR LTS?
[*]Or should I change it to 10.04 Ubuntu? (But that won't take advantage of the chipset, will it?)
[*]Or wait until the next UNR LTS? (Which version would it be? How do I find out?)
[/LIST]
It's a pain that the LTS applies to only selected remixes of the release.

---

### Post by P4man on 2010-05-02
Is there really a difference between the NBR and a regular ubuntu with the nbr interface installed?  Since that is in the repo's of ubuntu, I dont see how the NBR would effectively at least, not be a LTS.

---

### Post by m4tic on 2010-05-02
It's still usable

---

### Post by Paddy Landau on 2010-05-02
> **P4man said:**
> Is there really a difference between the NBR and a regular ubuntu with the nbr interface installed?
Yes, according to the [Canonical UNR page]("http://www.canonical.com/projects/ubuntu/unr"):
> All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom™ processors and it is specially designed for netbooks.
...
**Optimised for netbook components** - built from the ground up to take advantage of speed and power capabilities of the chip set

---

### Post by P4man on 2010-05-02
> **Paddy Landau said:**
> Yes, according to the [Canonical UNR page]("http://www.canonical.com/projects/ubuntu/unr"):

Its outdated. The intel low power architecture (LPIA) has been abandoned. Netbooks run the standard i386 or AMD64 builds now. There is no LPIA buld anymore.

its in the release notes somehere, but here as well:
[http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml](http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml)

edit: from the [release notes:]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs")

LPIA architecture discontinued

The lpia architecture present in previous releases has been discontinued as of Ubuntu 10.04 LTS. The hardware is still supported, but systems that were installed as lpia will need to be backed up and reinstalled from scratch using either the i386 or amd64 architectures. See bug 523295, which includes an unsupported method for migration from lpia to i386.

---

### Post by snowpine on 2010-05-02
> **Paddy Landau said:**
> 10.04 is a long term support (LTS) release.

Except for the Ubuntu netbook remix (UNR).

What is your source for this information?

Ubuntu and Ubuntu Netbook are the same except for the "launcher" interface. I do not see how one could be LTS and not the other. They share the same kernel, libraries, applications, etc.

---

### Post by Paddy Landau on 2010-05-02
> **P4man said:**
> Its outdated...
Oh, interesting! Thanks for the links.

Does that mean it would it make sense to install Ubuntu 10.04 and then add the UNR interface? Hmm, perhaps not, as the UNR for 10.04 would be supported for only 18 months.

Hmm. I still don't know which way to go!

---

### Post by Paddy Landau on 2010-05-02
> **snowpine said:**
> What is your source for this information?
I first read it in the newsletter dated 29 April. See it in [the Fridge]("http://fridge.ubuntu.com/node/2030"):
> Ubuntu 10.04 LTS will be supported for three years on desktops and five years on servers. Ubuntu 10.04 Netbook Edition will be supported for 18 months.

---

### Post by snowpine on 2010-05-02
> **Paddy Landau said:**
> I first read it in the newsletter dated 29 April. See it in [the Fridge]("http://fridge.ubuntu.com/node/2030"):

Thanks for the link. This thread is the first I'd heard of it. Strange decision by Canonical.

I am guessing it is only the netbook-specific components (the launcher etc.) that are not LTS. (And it won't suddenly stop working after 18 months, it just means no new updates.) The kernel, applications, etc. must be supported 3 years since they are the same as the desktop edition.

What do I know though, I try new distros like crazy--I've never stuck with anything for longer than 6 months, let alone 3 years. ;)

---

### Post by P4man on 2010-05-02
> **snowpine said:**
> Thanks for the link. This thread is the first I'd heard of it. Strange decision by Canonical.

I am guessing it is only the netbook-specific components (the launcher etc.) that are not LTS. (And it won't suddenly stop working after 18 months, it just means no new updates.) The kernel, applications, etc. must be supported 3 years since they are the same as the desktop edition.


Im not LTS specialist, but arent they supporting everything in the repo's for 3 years? the NBR interface is in the default repo's, so how could they stop supporting it?

---

### Post by snowpine on 2010-05-02
> **P4man said:**
> Im not LTS specialist, but arent they supporting everything in the repo's for 3 years? the NBR interface is in the default repo's, so how could they stop supporting it?

By not providing any more updates/bug fixes/security patches. You are correct that you're not going to log in one day and your launcher has disappeared; it will just get stale (if this information is indeed accurate, I have my doubts). ;)

---

### Post by Paddy Landau on 2010-05-02
> **snowpine said:**
> ... I try new distros like crazy--I've never stuck with anything for longer than 6 months
As fun as that may be, I don't have time to fiddle like that. I prefer to stay with an LTS and upgrade only occasionally.

---

### Post by NCLI on 2010-05-02
I think it simply means that, if you buy support, they will not be able to help you with the 10.04 UNE interface after 18 months. The netbook-launcher is the only thing that wouldn't receive updates, and it's hardly a critical application in terms of how dangerous a bug in it would be.

---

### Post by snowpine on 2010-05-02
Also I've read the upcoming 10.10 will be very netbook-centric, so maybe they are encouraging netbook users to upgrade in October instead of sticking with 10.04.

---

### Post by P4man on 2010-05-02
> **snowpine said:**
> By not providing any more updates/bug fixes/security patches. 

Providing security updates and bug fixes (and allowing bug reports) is the only thing that makes a  release or package supported . I dont see how they can refuse to patch/accept bug reports etc for the nbr launcher if its in the default repo's.

---

### Post by lykwydchykyn on 2010-05-02
The same thing happened with Kubuntu for 8.04.  It's typically because the technology is in such a state of transition that it cannot be realistically supported for 3 years.  

If it's like the Kubuntu situation, what it means is that the packages specific to that release will not be officially supported past 18 months. Obviously the core of the OS, and applications used in other Ubuntu flavors will still be supported.

---

### Post by cariboo on 2010-05-02
From what I understand the the indicator applets are going to be reworked in MM, starting with the netbook interface, as they are now, they are quite a mess, needing both a right click and a left click to accomplish some things, moving the mouse over some of the indicators shows you the status, while others you have to right click to see it.

---

### Post by Paddy Landau on 2010-05-03
Thank you all for the recent messages. It's given me a better overview and allowed me to come to a decision.
 
 I'll upgrade to 10.04, and see what happens in the future.

> **lykwydchykyn said:**
> It's typically because the technology is in such a state of transition that it cannot be realistically supported for 3 years.
Well, that makes sense. I'll mark the thread Solved.

---

### Post by NMFTM on 2010-05-03
Much more broadly speaking, why would the netbook remix need to be LTS? LTS is primarily for servers and is designed to be the Ubuntu equivilent of Debian Stable. I don't think anyone's hosting a server on their netbook.

---

### Post by snowpine on 2010-05-03
> **NMFTM said:**
> Much more broadly speaking, why would the netbook remix need to be LTS? LTS is primarily for servers and is designed to be the Ubuntu equivilent of Debian Stable. I don't think anyone's hosting a server on their netbook.

I would have to disagree with that. Many non-server users stick with the LTS releases. Some people just don't like upgrading their OS every 6 months and prefer stability to bleeding-edge. This is especially true for netbooks; a lot of people just use them for web browsing, email, chat, etc. so why do they need the latest and greatest?

---

### Post by BigSilly on 2010-05-03
I agree. I was hoping to stick Lucid UNR on our EeePC and leave it there for the full three year term. Still, we'll go the 18 months with it at least. :)

---

### Post by Paddy Landau on 2010-05-03
> **NMFTM said:**
> Much more broadly speaking, why would the netbook remix need to be LTS? LTS is primarily for servers and is designed to be the Ubuntu equivilent of Debian Stable. I don't think anyone's hosting a server on their netbook.
As an 'average' user, I want reliability rather than bleeding-edge (fun as that may be). I don't want to have to upgrade frequently; I want a system that "just works" with the minimum of fuss.

I suppose it's the same as the difference between a car enthusiast who is also a technician, who is happy to tinker and frequently get new cars, and a basic driver (like me) who wants a car that "just works" and replaces the car only when he has to.

---

### Post by mikewhatever on 2010-05-03
> **snowpine said:**
> I would have to disagree with that. Many non-server users stick with the LTS releases. Some people just don't like upgrading their OS every 6 months and prefer stability to bleeding-edge. This is especially true for netbooks; a lot of people just use them for web browsing, email, chat, etc. so why do they need the latest and greatest?

Why would Hardy Heron users want to move to Lucid Lynx?
firefox 3.6
Facebook/Twitter integration.
faster boot times.
more abundant community support
In short, there is a certain piece of mind in sticking to LTSs, but a year or two after the release, the consideration may become stable vs outdated.

---

### Post by jheaton5 on 2010-05-03
I tried to install the standard 10.04 on my Dell mini 9.  I could not do so, kept getting errors that I needed a different kernel.  I installed UNR with no problems.

---

### Post by snowpine on 2010-05-03
> **mikewhatever said:**
> Why would Hardy Heron users want to move to Lucid Lynx?
firefox 3.6
Facebook/Twitter integration.
faster boot times.
more abundant community support
In short, there is a certain piece of mind in sticking to LTSs, but a year or two after the release, the consideration may become stable vs outdated.

I agree. Lucid (the new LTS, no matter what they say) came along just in time, as Hardy (the outgoing LTS) was getting a bit stale. (although, FYI, you can use Firefox 3.6 and Facebook in Hardy, too! ;))

Personally I am still stuck on 9.04 and probably won't be moving to 10.04 any time soon... but that's just me. ;)

---

### Post by snowpine on 2010-05-03
> **jheaton5 said:**
> I tried to install the standard 10.04 on my Dell mini 9.  I could not do so, kept getting errors that I needed a different kernel.  I installed UNR with no problems.

Sounds like your issue is "solved" :) but next time make sure you use the i386 release rather than the amd64... that is the most likely cause I can think of for that error message (a bad burn is another possibility).

---

### Post by Paddy Landau on 2010-05-03
> **mikewhatever said:**
> Why would Hardy Heron users want to move to Lucid Lynx?
firefox 3.6
Facebook/Twitter integration.
faster boot times.
more abundant community support
For the 'average' user (the typical business person, perhaps, or low-key computer user with emails, documents and a bit of browsing), those are meaningless terms.

The really good thing about upgrading Ubuntu, though, is the high probability that the upgrade (or at least a new installation) will work, and you won't have to purchase new programs and hardware just because you upgraded.

---

### Post by NMFTM on 2010-05-03
> **Paddy Landau said:**
> As an 'average' user, I want reliability  rather than bleeding-edge (fun as that may be). I don't want to have to  upgrade frequently; I want a system that "just works" with the minimum  of fuss.
I've found that upgrading to a new version every 6 months provides for a  more stable system. Your only looking at it from the perspective that  your using the same software and not upgrading. But you also have to  look at it from the perspective that in 3 years when the current LTS  release is no longer supported, your outdated software is going to be  plagued by all of the bugs that the people who've updated their packages  got rid of years ago.

I'll use Thunderbird as an example. The old version of Thunderbird as included in the repos for 9.10 requires the user to go to their email providers website and RTFM how to setup their account. The version of Thunderbird included in the repos for 10.04 just asks the user to put in their email address, password, and it'll autoconfigure all of the options that really inexperienced users might have trouble with. Like what ports or incoming/outgoing servers to use. I might not have a problem setting those things up manually, but the stereotypical "grandma" computer user probably would. And they'd find the version of Thunderbird that comes with 10.04 much easier to use.
> **Paddy Landau said:**
> For the 'average' user (the typical business person, perhaps, or low-key computer user with emails, documents and a bit of browsing), those are meaningless terms.
I guess if by "average computer user" you mean the stereotypical grandma who doesn't know anything about computers than yes. But unlike Windows and OSX where (in my opinion) there is very little noticeable improvements between releases, in the world of Linux (at least for desktop users) things are improving by leaps and bounds every year. I first tried Linux out (Fedora Core 2) in late 2004 and from what I remember it was horrible. My flash drive wouldn't even automount and from what I remember, things were always crashing and freezing up. Of course, it's also true that I was much less technically inclined back then.

---

### Post by Paddy Landau on 2010-05-03
> **NMFTM said:**
> I've found that upgrading to a new version every 6 months provides for a  more stable system.
Except when the upgrades don't work! For example, 9.10 didn't work on my machine; I've stuck with 8.04 because it has suited my needs almost perfectly.

> **NMFTM said:**
> But you also have to  look at it from the perspective that in 3 years when the current LTS  release is no longer supported, your outdated software is going to be  plagued by all of the bugs that the people who've updated their packages  got rid of years ago.
Well, again, non-power users won't worry about that. Their system works fine. Your image of a stereotypical grandma is not, in my experience, appropriate. I often help friends (and my wife) who just want to do emails, write letters, and browse the Internet, and wouldn't even be able to install Ubuntu. 8.04 still satisfies those needs perfectly well.

I think that computer users fall into three camps (very generally speaking):

[LIST=1]
[*]Power technical guru type users, who may be programmers or support personnel. (Like a car technician who knows just about everything about cars.)
[*]Power users, but not guru types, who know their way around machines well. (Like a car lover who's not a mechanic but knows quite a bit about cars.)
[*]Normal users (business people, secretaries, clerks, accountants, etc.) who need the computer to "just work" and really aren't fussed about fancy new features. (Like the person who enjoys a nice car, but doesn't understand much more about the machine than how to pump up the tyres and fill the petrol tank.)
[/LIST]
To me, the LTS releases are highly suitable for the third type of person. They're even suitable for people like me, who fit into #2 but prefer to avoid any power work.

---

### Post by cariboo on 2010-05-03
> **NMFTM said:**
> I've found that upgrading to a new version every 6 months provides for a  more stable system. Your only looking at it from the perspective that  your using the same software and not upgrading. But you also have to  look at it from the perspective that in 3 years when the current LTS  release is no longer supported, your outdated software is going to be  plagued by all of the bugs that the people who've updated their packages  got rid of years ago.

I'll use Thunderbird as an example. The old version of Thunderbird as included in the repos for 9.10 requires the user to go to their email providers website and RTFM how to setup their account. The version of Thunderbird included in the repos for 10.04 just asks the user to put in their email address, password, and it'll autoconfigure all of the options that really inexperienced users might have trouble with. Like what ports or incoming/outgoing servers to use. I might not have a problem setting those things up manually, but the stereotypical "grandma" computer user probably would. And they'd find the version of Thunderbird that comes with 10.04 much easier to use.

I guess if by "average computer user" you mean the stereotypical grandma who doesn't know anything about computers than yes. But unlike Windows and OSX where (in my opinion) there is very little noticeable improvements between releases, in the world of Linux (at least for desktop users) things are improving by leaps and bounds every year. I first tried Linux out (Fedora Core 2) in late 2004 and from what I remember it was horrible. My flash drive wouldn't even automount and from what I remember, things were always crashing and freezing up. Of course, it's also true that I was much less technically inclined back then.

There are point releases and security updates throughout the life of an LTS version, so your install will be more bug free and secure. Even if the original producer stops supporting a version, Ubuntu still provides security updates, check out the [Ubuntu Security Notices]("http://www.ubuntu.com/usn/")

---

