---
title: "Ubuntu and systemd"
date: 2014-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by rayalexie on 2014-11-22
I don't know where this would be classified, so forgive me if it's in the wrong place.

Since Debian has recently announced that systemd will be the default init system in its next major release, I wanted to ask how Ubuntu will respond to this.  Some articles have suggested that Ubuntu will abandon upstart in favor of this, but only in the farther future.  Is the community more-or-less in favor of it, or against it?  I've been horribly out-of-touch with Ubuntu in the last year-ish.

---

### Post by sandyd on 2014-11-22
I have moved your thread to *Ubuntu Linux and OS Chat*

---

### Post by QIII on 2014-11-22
Hello!

I can give you only my personal opinion.

As a regular user of Fedora with systemd, I think the partisan hysteria and rampant paranoia is blown way out of proportion.

As a pragmatist listening to those repeating the meme "Do one thing and do it well!", I say "Do things efficiently when possible."

---

### Post by rrnbtter on 2014-11-22
Greeting,
Ubuntu will likely default to systemd with 16.04 or sooner. It debuted as optional in Utopic and is also optional in Vivid. I have been using it myself since the appearence of the first systemd thread in the Development section when Utopic went to dev. I suggest that you get you information from that thread since is a serious thread followed by members that are actually using systemd. The ultimate switch to systemd by Canonical follows Redhat, Suse, Debian and others to support their server market needs.  Since Ubuntu plays in that market it makes sense to me that they follow suit in order to compete.  I am personally pleased with the results and agree with post #3 that "the partisan hysteria and rampant paranoia is blown way out of proportion".

---

### Post by rayalexie on 2014-11-22
Yeah, the flame threads have been getting out of hand -- for both sides.  But it seems like the sysd developers have no interest in transparency, so I sympathize with many users who stand against it for those reasons.  Someone in the Debian forums posted a good read regarding the thoughtless animosities on each side:

[http://uselessd.darknedgy.net/ProSystemdAntiSystemd/](http://uselessd.darknedgy.net/ProSystemdAntiSystemd/)

---

### Post by grahammechanical on 2014-11-22
Debian developers decided to switch from Upstart to systemD and Ubuntu is built on Debian. So, Mark Shuttleworth decided that Ubuntu would switch to SystemD. 

[http://www.markshuttleworth.com/archives/1316](http://www.markshuttleworth.com/archives/1316)

First, Debian has to use SystemD, then when Ubuntu syncs with Debian Ubuntu will also get SystemD. That being said, there is already a lot of SystemD code in Ubuntu Vivid Vervet. Follow the discussion by those who have switched to SystemD.

[http://ubuntuforums.org/showthread.php?t=2249915](http://ubuntuforums.org/showthread.php?t=2249915)

One of the issues that Ubuntu developers have is the need to convert Upstart scripts to SystemD scripts without breaking Ubuntu. This is especially true for Ubuntu server.

[https://launchpad.net/systemd](https://launchpad.net/systemd)

See, the SystemD Transition session in the recent Ubuntu Online Summit.

[http://summit.ubuntu.com/uos-1411/meeting/22401/systemd-transition/](http://summit.ubuntu.com/uos-1411/meeting/22401/systemd-transition/)

Regards.

---

### Post by sffvba[e0rt on 2014-11-22
[http://boycottsystemd.org/](http://boycottsystemd.org/)

As you can see from this site there are many reasons to be wary of systemd.  For me the greatest worry is how many dependencies systemd is going to start demanding that comes directly from the people at Gnome.  And the list and scope seems to be ever expanding.  From the little I understand it really looks like enforcing things on the whole ecosystem in a way that later makes it very difficult to revert.

edit: also worth mentioning - [http://uselessd.darknedgy.net/](http://uselessd.darknedgy.net/) basically systemd doing only what a good init system is supposed to do...

---

### Post by vellon on 2014-11-23
Firstly, as balance, let me point you to a spoof of that paranoid site   [http://boycottlinux.org/](http://boycottlinux.org/)

Secondly, think of systemd as a process manager, not just an init system.

Thirdly, opposition to systemd is largely based on "but what happens if this paranoid scenario occurs?" rather than any direct experience or past performance of systemd. Like other posters above, I use systemd elsewhere and it works. RHEL 7 with systemd is out in the wild too, and the internet hasn't fallen over yet.

---

### Post by kevdog on 2014-11-23
I must be a very dumb and uninformed user.  I'm obviously no developer, just an end user.  I use Ubuntu -- with their Upstart system -- and Arch -- with the systemd - process.  It's a little bit of difference, but after reading about using systemd for awhile when starting arch and how to start processes, it wasn't that hard of transition.  I'll admit I'm not that big of fan of the journaling system, but it doesn't seem to be any deal breaker.

---

### Post by buzzingrobot on 2014-11-23
My opinion is the same as QIII's for the same reason.

I'll add that an init system should never makes its presence known to an ordinary user.   If I --as a user --have a reason to enable or disable a system service, then a simple, safe, GUI ought to be available.  If it is not, I'd call that a weakness of that particular system.

Also note that Unity hides services and default startup apps from users by default.  No outcry has surfaced about this.

Professional developers and admins are not typical mainstream users and have different interests and requirements. If the transition to systemd provides better products for users at the expense of some transient unhappiness among those people who are paid to cope with Linux, I'm OK with that.

The 'one tool for one task' notion is an appealing concept, one that seduces many CS students when they first delve in to Unix. It's constraining, though, if it takes precedence over innovation and capability.

---

### Post by SagaciousKJB on 2014-11-24
I read most of the links pointed to in this thread.  I still do not know entirely what SystemD is or what it will entail.

As an end user my primary concern is this: How much crap am I going to need to relearn to manage my system?  I'm still use to running scripts out of /etc/init.d to start or stop services.  The only thing that will annoy me is booting into a newer version of Ubuntu or Debian and having to relearn how to do this.  What about all the mounting talk?  Will I no longer define my mount-points in /etc/fstab It wasn't broken, so why did you "fix" it?  These issues present annoyances.

But progress is always needed, even if it's painful.  I'm sure I'll learn the new way to do things.  If we all disqualified new things simply because we had to learn them, I doubt anyone would have ever switched from a Windows to Linux or a *nix like OS.  Or for that mater, learned how to drive a car instead of walking or riding a bike.  While I wouldn't compare the functionality between this system and the one in current use in the same regard as a car versus a bike, it does kind of point out that often times refusing to let go of antiquated methods only leaves us clutching to obsolete methods.

My take is this: Everyone complains about something new at first, but only a few will refuse to adapt.  Those people are the minority and usually aren't happy with any change, so we kind of have to just take it as expected that they will complain while others just accept new things.  Haters gonna hate I guess.

Seems like this discussion could be more broadly applied to technological advancement in general, and I think most people are kind of in the middle.  They would like things to remain predictable and and not have to re-learn everything, but on the other hand they appreciate improvements so are able to see the trade-off.

If you ask me, I would just tell you I hate high definition television.  My eyesight isn't that good anyway, standard definition was fine!  Now I have to buy unnecessarily expensive cables and small ass TVs that don't look any better to me.  Trust me I understand the frustration when forced to adopt new technology that you don't care for, but I'm pretty sure that the rest of the world is happy to have HD.

---

### Post by vellon on 2014-11-24
As an end user, on mainstream distros, you are unlikely to need to relearn anything. If you use a more technical hands-on distro like Arch, Slackware or Gentoo (and, of those, only Arch currently uses systemd) you would need to know how to stop and start daemons (eg. systemctl start sshd.service instead of /etc/rc.d/sshd start), and check logs (eg. journalctl instead of tail /var/log/syslog). Regardless of any other concerns about systemd, the commands themselves should not be much of a challenge to learn and are standard across distros (unlike the daemon stop/start commands of old, which may have different paths).

---

### Post by Lars Noodén on 2014-11-24
> **vellon said:**
> As an end user, on mainstream distros...

The ones that are going to notice getting hurt directly are the sysadmins, power users, tinkerers, devops and certain kinds of developers.  

Then there is the unlikelihood that something so big, bloated and complex will function safely and without continual major security concerns.  Two top developers have already called it a hairball and at the outer limits of complexity.  Complexity unavoidably breeds maintenance and security nightmares.  

It has been allowed to get as far as it has because it has largely flown under the radar having been misrepresented as an init system for years.  If the question came down to simple choice of init systems, systemd would be out of contention because it is not an init system.  In that regard, and for several other reasons, Upstart is far superior and less dangerous both to security and to user freedom/flexibility.  Even SysVinit beats it in those areas.  

I guess the last straw is that it is still in the early phases of planning.  Functionality is still being decided and major structural changes are being made regularly.  As such it has not even hit pre-alpha stage and should certainly not be allowed near production machines until long after change has levelled off and it has passed through proper alpha and beta testing.

One way out for Ubuntu would be to move to using Debian/kFreeBSD as a base.  That would be easy for the server version, I think, but for the desktops, more kernel development would be needed to catch up on hardware support.

---

### Post by Lars Noodén on 2014-11-24
> **vellon said:**
> As an end user, on mainstream distros...

For novice home users, the systemd problem comes down to one of two positions, either 'meh' or a chain of expletives, mostly the former.

The ones that are going to notice getting hurt directly are the sysadmins, power users, tinkerers, devops and certain kinds of developers.  However, everyone loses with the loss of flexibility (freedom) it imposes.  

Then there is the unlikelihood that something so big, bloated and complex will function safely and without continual major security concerns.  Two top developers have already called it a hairball and at the outer limits of complexity.  Complexity unavoidably breeds maintenance and security nightmares.  

It has been allowed to get as far as it has because it has largely flown under the radar having been misrepresented as an init system for years.  If the question came down to simple choice of init systems, systemd would be out of contention because it is not an init system.  In that regard, and for several other reasons, Upstart is far superior and less dangerous both to security and to user freedom/flexibility.  Even SysVinit beats it in those areas.  

I guess the last straw is that it is still in the early phases of planning.  Functionality is still being decided and major structural changes are being made regularly.  As such it has not even hit pre-alpha stage and should certainly not be allowed near production machines until long after change has levelled off and it has passed through proper alpha and beta testing.

One way out for Ubuntu would be to move to using Debian/kFreeBSD as a base.  That would be easy for the server version, I think, but for the desktops, more kernel development would be needed to catch up on hardware support.  Also, it might be controversial for some to hear, but it may be time to drop GNOME because of the systemd dependencies.

---

### Post by mastablasta on 2014-11-24
> **Lars Noodén said:**
> 
Then there is the unlikelihood that something so big, bloated and complex will function safely and without continual major security concerns.  Two top developers have already called it a hairball and at the outer limits of complexity.  Complexity unavoidably breeds maintenance and security nightmares.  

It has been allowed to get as far as it has because it has largely flown under the radar having been misrepresented as an init system for years.  If the question came down to simple choice of init systems, systemd would be out of contention because it is not an init system.  In that regard, and for several other reasons, Upstart is far superior and less dangerous both to security and to user freedom/flexibility.  Even SysVinit beats it in those areas.  

I guess the last straw is that it is still in the early phases of planning.  Functionality is still being decided and major structural changes are being made regularly.  As such it has not even hit pre-alpha stage and should certainly not be allowed near production machines until long after change has levelled off and it has passed through proper alpha and beta testing.

One way out for Ubuntu would be to move to using Debian/kFreeBSD as a base.  That would be easy for the server version, I think, but for the desktops, more kernel development would be needed to catch up on hardware support.  Also, it might be controversial for some to hear, but it may be time to drop GNOME because of the systemd dependencies.

ouch. some say it's good and simplifies things, but others it is way more complex. for me as a novice user it is hard to tell. but I am worried what will happen to server. 

things should be made easier not more complex. and not just for end users but for programmers as well.

in Debian there is a big split now as previous claim that users will be able to use both systems turned out to be invalid. how could a vote be made to include an alpha or beta project to enter business grade OS like debian stable or Ubuntu  is beyond my understanding.

I am not saying systemd is a bad choice, but it should be at least well tested and very stable as it integrates with the system on many levels. but then again Red hat has it and they are the biggest in commercial world. but even there it is quite new, so I guess no one found a seucrity flaw yet that would cause them to lose customers.

---

### Post by /ADM on 2014-11-24
I think many admins will probably switch to using FreeBSD for their server platforms.  It pretty much keeps the web online and the 'jails' are sweet.

For me this is a good thing, less server Linux and more Linux for 'normal people'.  Leave BSD to be the server OS, it is great for that.

---

### Post by buzzingrobot on 2014-11-24
> **/ADM said:**
> I think many admins will probably switch to using FreeBSD for their server platforms.

Amateurs, maybe. Assuming they're that obsessive about this. 

Professionals, though, can't just change their employer's OS platform in a fit of pique.  They're hired to administer whatever that employer wants to use.

All the chatter and ranting about the "Debian Way" or the "Unix Way" or "One Tool for One Job" has zero resonance with businesses and organizations. They don't care and don't have a reason to care. From their perspective, if they want to move their 500-seat RHEL6-without-SystemD 6 institution to a 500-seat RHEL7-with SystemD shop, they will and any grouchy admins can find solace in their paychecks.

---

### Post by /ADM on 2014-11-24
> **buzzingrobot said:**
> Amateurs, maybe. Assuming they're that obsessive about this. 

Professionals, though, can't just change their employer's OS platform in a fit of pique.  They're hired to administer whatever that employer wants to use.

All the chatter and ranting about the "Debian Way" or the "Unix Way" or "One Tool for One Job" has zero resonance with businesses and organizations. They don't care and don't have a reason to care. From their perspective, if they want to move their 500-seat RHEL6-without-SystemD 6 institution to a 500-seat RHEL7-with SystemD shop, they will and any grouchy admins can find solace in their paychecks.

After using CentOS7 with SystemD I can say it is actually a pleasure to use and administer.  You just have to relearn things, which is something that *NIX greybeards don't like doing.  Probably because it diminishes their 'I have known this since 1970' to 'now I do not know this'.

---

### Post by vellon on 2014-11-24
The hysteria was mentioned on the first page, and here it is.

> **Lars Noodén said:**
> For novice home users, the systemd problem comes down to one of two positions, either 'meh' or a chain of expletives, mostly the former.

The ones that are going to notice getting hurt directly are the sysadmins, power users, tinkerers, devops and certain kinds of developers.  However, everyone loses with the loss of flexibility (freedom) it imposes.  

How are the novice home users going to know or care about systemd on a mainstream distro like Ubuntu that uses a GUI to set startup services?

Sysadmins and power users are intelligent adults who need to keep their skills and knowledge updated throughout their careers. The internet barely existed 20 years ago, a period  well within the working life of many admins, so think how much that development alone has changed sysadmin tasks.

You must stop assuming your own opinions are shared by everyone, no matter how much you want them to be. They are not, and that's just a fact of life in all walks of life.

> **Lars Noodén said:**
> Then there is the unlikelihood that something so big, bloated and complex will function safely and without continual major security concerns.  Two top developers have already called it a hairball and at the outer limits of complexity.  Complexity unavoidably breeds maintenance and security nightmares.  

As I have pointed out before, the kernel is massive too, but I see no campaign to change to a microkernel model.

> **Lars Noodén said:**
> I guess the last straw is that it is still in the early phases of planning.  Functionality is still being decided and major structural changes are being made regularly.  As such it has not even hit pre-alpha stage and should certainly not be allowed near production machines until long after change has levelled off and it has passed through proper alpha and beta testing.

RHEL 7.0 uses systemd, so Red Hat seems to disagree with you, and it's their money at risk.

---

### Post by /ADM on 2014-11-24
> **vellon said:**
> As I have pointed out before, the kernel is massive too, but I see no campaign to change to a microkernel model.

GNU Hurd tried that and 15 years later it still isn't finished ;)

---

### Post by Lars Noodén on 2014-11-24
> **vellon said:**
> 
As I have pointed out before, the kernel is massive too, but I see no campaign to change to a microkernel model.


Well, shoot, let's all just run busybox then while we're at it.  

If systemd were any good it could be defended without name calling.  But alas it cannot.  

Since you bring up Red Hat again but this time in this thread, what is Red Hat's official, written position statement on systemd?  Some one or committee there has given Poettering a budget and a long leash, who and why?

---

### Post by vellon on 2014-11-24
You would think systemd could be argued against without the death threats and insults to the developers too, but apparently not.

You'd have to ask Red Hat. I have no connection with them except in the past as a user at work.

---

### Post by /ADM on 2014-11-24
> **Lars Noodén said:**
> Well, shoot, let's all just run busybox then while we're at it.  

That's a bit extreme.  It's great for embedded/small devices but no use in running it on a desktop/server unless you want to be able to drop the 'GNU/' without RMS correcting you ;)
> **Lars Noodén said:**
> 
If systemd were any good it could be defended without name calling.  But alas it cannot. 

Running CentOS 7, I think it's pretty good.  Sure I liked the text files in the old init system, it's a change and some people cannot handle change after several decades of the same init system.
> **Lars Noodén said:**
> 
Since you bring up Red Hat again but this time in this thread, what is Red Hat's official, written position statement on systemd?  Some one or committee there has given Poettering a budget and a long leash, who and why?

Because Red Hat is his employer and his budget is his salary.  Do people who are hired by MS have a budget for '.net'?

Conspiracy theorists make me laugh.

---

### Post by Elfy on 2014-11-24
Keep the discussion respectful.

Thanks.

---

### Post by SagaciousKJB on 2014-11-24
Honestly it kind of seems like it's being developed just for the sake of being developed.  I don't hear much about its advantages or benefits of upgrading to it.  It's like the best thing anyone seems to be able to say for it is that it's not bad.

But yeah, I'm use to just stepping out of the way for progress.  So I'll have to relearn a few things.  Oh well, as it stands so many things are different from distro to distro that was probably inevitable anyway.

---

### Post by mastablasta on 2014-11-24
> **/ADM said:**
> 
Running CentOS 7, I think it's pretty good.  Sure I liked the text files in the old init system, it's a change and some people cannot handle change after several decades of the same init system.


right. I installed it in vbox. it runs ok.

but I never did any security review on it. or any serious work like running single or multiple servers or some farms etc etc. but I guess it runs ok there as well. 

however the issue is only as more people/distros move to it bugs and incompatibilities will start to float. if they fix them on time and do security patches it is ok. if they can't then it becomes an issue.

I just hope the decision to move to it has really solid ground. But from what i can't read on various blogs, the ground is becoming bit shaky.

in any case for me personally and as a user it's like the OS. the less I see it, the better.

---

### Post by christopher9 on 2014-11-24
With each new announcement of a Debian developer resigning from the team ostensibly due to the init system controversy, one does begin to wonder if there is indeed something more to the issue than "If you don't play the game my way, I'm taking my football and going home!"...

I do have a simple-minded end-user type question, though...will systemd be 'retrofitted' to 14.04 LTS (not sure that's the correct terminology - perhaps the reverse is true) or just applied to 15.04 and beyond ?

---

### Post by Elfy on 2014-11-24
> **christopher9 said:**
> ...

I do have a simple-minded end-user type question, though...will systemd be 'retrofitted' to 14.04 LTS (not sure that's the correct terminology - perhaps the reverse is true) or just applied to 15.04 and beyond ?

I've seen no discussion. no hints of any sort that they'd even contemplate that.

I'd very much doubt that they'd do anything as large as that for an already released LTS.

---

### Post by buzzingrobot on 2014-11-24
> **mastablasta said:**
> 

but I never did any security review on it. or any serious work like running single or multiple servers or some farms etc etc. but I guess it runs ok there as well. 




CentOS is a verbatim rebuild of RHEL.  That includes patches/fixes/updates released by RH.

---

### Post by mastablasta on 2014-11-25
> **buzzingrobot said:**
> CentOS is a verbatim rebuild of RHEL.  That includes patches/fixes/updates released by RH.

I know, but I doubt many businesses moved their servers to 7 already. or have they? also I see many projects based on 7 just started with their roadmaps. which is kind of interesting since 7 is out for a while now I believe.

also make sit a bit strange why they included something considered in development stage in their business distribution?

---

### Post by buzzingrobot on 2014-11-25
RHEL7 or CentOS7 aren't in a "development" stage.  I don't know what RHEL7's adoption rate is, but I doubt RH expects to see businesses rush to replace RHEL5/6 if they don't want the new features in 7. Every 5/6 customer is still paying subscription fees.

---

### Post by mastablasta on 2014-11-25
not RHEL or CentOS 7 - but systemd (according to some) is still in alpha or beta stage so how come it go it's way into stable RHEL 7 ? it must give them some added value that such a risk (if it even is a large risk) is worthwhile.

edit: all was good with OpenSSH until critical mass was reached. then we go heartbleed and such. according to latest reports many system are still left unpatched.

---

### Post by Lars Noodén on 2014-11-25
(You perhaps mean OpenSSL.  That was the one with the trademarked bugs and the dedicated website.)

By the definitions I've read of alpha stage, a package that is still adding features is not yet even in alpha.

[http://www.phoronix.com/scan.php?page=news_item&px=MTc2Nzk](http://www.phoronix.com/scan.php?page=news_item&px=MTc2Nzk)
[http://www.phoronix.com/scan.php?page=news_item&px=MTgyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTgyNDY)
[http://www.phoronix.com/scan.php?page=news_item&px=MTgyODQ](http://www.phoronix.com/scan.php?page=news_item&px=MTgyODQ)

But  I share your curiosity and want to know what's in it for Red Hat.  I don't see the value added, even for them.

---

### Post by buzzingrobot on 2014-11-25
RH more or less pioneered systemd, via Fedora, so I imagine they don't agree with its opponents. 

They'd also have quantative data acquired during 7's lengthy development process and in the Fedora iterations.

---

### Post by Lars Noodén on 2014-11-25
> **buzzingrobot said:**
> RH more or less pioneered systemd, via Fedora, so I imagine they don't agree with its opponents. 

They'd also have quantative data acquired during 7's lengthy development process and in the Fedora iterations.

Yes, we can all speculate, but I have not seen any actual position aside from letting Poettering be the defacto face of the shambles.  Since we are speculating, that lack of a public policy or position implies they are reserving the option to be able to drop it quickly at some future date and blame him.

---

### Post by buzzingrobot on 2014-11-25
> **Lars Noodén said:**
> Yes, we can all speculate, but I have not seen any actual position aside from letting Poettering be the defacto face of the shambles.  Since we are speculating, that lack of a public policy or position implies they are reserving the option to be able to drop it quickly at some future date and blame him.

I don't agree that it's a 'shambles' and I doubt RH makes business decisions based on who they might scapegoat in the future.  Aversion to change among admins is a poor basis for business decisions. In any case, admins generally aren't the folks spending money to buy RH. 

The anti-systemd hysteria seems, to me, largely rooted in emotion driven by an ideological conceit that Linux must always conform with Unix customs created 40 years ago. RH or any other vendor would be foolish to be influenced by that.

If systemd is fundamentally incapable of supporting users, then users will migrate to distributions that offer something better.

---

### Post by vellon on 2014-11-25
systemd is not in alpha. Where did that FUD start?

There is no shambles. systemd is in use by various stable distributions, and has been for a while now (since 2011 in some cases), which may be an uncomfortable fact for some people, but it is nevertheless a fact. No distributions have backed it out.

The anti-systemd hysteria is mainly from those with no experience or knowledge of systemd - having read some anti articles on the internet, these people are armed wth all the knowledge they need to feel outraged.

---

### Post by cariboo on 2014-11-25
I've been using systemd since the middle of the Utopic development cycle, and aside from a problem loading Nvidia drivers, that was fixed fairly quickly, I can't even tell the difference between upstart and it, except that my system does boot a little faster:

```
systemd-analyze
Startup finished in 2.426s (kernel) + 5.060s (userspace) = 7.487s
```

This is on an AMD 8 core system with 16GiB of ram and a 252GiB SSD.

---

### Post by mastablasta on 2014-11-26
> **cariboo907 said:**
> I've been using systemd since the middle of the Utopic development cycle, and aside from a problem loading Nvidia drivers, that was fixed fairly quickly, I can't even tell the difference between upstart and it, except that my system does boot a little faster:


fingers crosses it will be like that on next LTS. and no more loading drivers problems. :)

what about other devices? same smooth ride? Phone, tablets, TV sets... any of them using it already?

BTW isn't upstart just the init system while system is a lot more than that? and the other part is not developed yet well. eh I could be wrong. like I wrote above - not noticing much of the difference (ok I know there are different commands) is how I want it as a user.

---

### Post by vellon on 2014-11-26
Drivers are the kernel's responsibility, nothing to do with systemd or any init system.

systemd definitely covers more ground than upstart, which is the main complaint by opponents. As well as process management, it includes logging (journald) and session management (which I believe is the part required by Gnome).

---

