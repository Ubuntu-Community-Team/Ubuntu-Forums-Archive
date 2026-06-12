---
title: "upstart, systemd, Canonical and Debian"
date: 2014-01-17
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-01-17
I came across 
[Debian May Be Leaning Towards Systemd Over Upstart]("http://www.phoronix.com/scan.php?page=news_item&px=MTU3NDc") and 
[Debate initsystem upstart]("https://wiki.debian.org/Debate/initsystem/upstart") and 
[Debate initsystem systemd]("https://wiki.debian.org/Debate/initsystem/systemd")

There's reference to Canonical's "contributor license agreement" as one obstacle, if that is an appropriate word, to upstart's acceptance. Why is that?

---

### Post by ian-weisser on 2014-01-17
Phoronix is fun, but that doesn't mean their analysis is reliable. They amp up trivial disagreements in earthshaking click-magnets. 
Don't fall for their hyperbole.

I expect the Debian debate over systemd vs Upstart to go on much longer. It requires a consensus, and I predict no consensus in the next couple years. In the absence of consensus, Debian will either make no change at all, or do a change that tries to please everybody (including Ubuntu). Debian's governance is specifically set up to encourage inaction when there is a lack of consensus.

And, honestly, it's not a big deal for Ubuntu. The conversion from sysvinit to Upstart is already part of the Debian to Ubuntu sync each release cycle. The ecosystem of Upstart patches are already written and in place. Consequently, the Ubuntu Technical Board has said that they won't turn away from Upstart without a compelling reason. Both Upstart and all those Ubuntu Upstart job patches are fully open source and GPL and available in Launchpad.

The claim that the CLI is the big showstopper to universal Upstart acceptance has a bit of merit, but is mostly hyperbole. Sure, some contributors have heartburn about the CLI, and that's totally understandable. However, if the CLI vanished tomorrow, many of the same opponents have other reasons to dislike Upstart - it changes their favorite syntax, they don't like the name, they don't like the Upstream project, it abuses their favorite kernel module, it reminds them of a bad breakup, whatever. It's opinion. Opinions in this community are sometimes based on reason, but often based on emotion and politics. And that's okay.

The real news is that Debian has two great open-source sysv init replacements available. And no real compelling need to choose between them soon. This is certainly **not** the precursor to an implied (and purely imaginary) Debian-Ubuntu divorce.

---

### Post by su:bhatta on 2014-01-20
I have no clue about what the nittigritties of this means to me, or if & how it will affect me, But

> **ian-weisser said:**
> 
I expect the Debian debate over systemd vs Upstart to go on much longer. It requires a consensus, and I predict no consensus in the next couple years. In the absence of consensus, Debian will either make no change at all, or do a change that tries to please everybody (including Ubuntu). Debian's governance is specifically set up to encourage inaction when there is a lack of consensus.

The real news is that Debian has two great open-source sysv init replacements available. And no real compelling need to choose between them soon. This is certainly **not** the precursor to an implied (and purely imaginary) Debian-Ubuntu divorce.

one of the many reasons I just like Debian. Specially  "Debian's governance is specifically set up to encourage inaction when there is a lack of consensus."

---

### Post by ssam on 2014-01-20
CLA would mean that Canonical would not accept any patches from Debian (assuming debian devs did not want to sign it). Debian could still make changes and maintain a branch that used those changes. That means its a little bit more maintenance work for Debian (not much in the age of distributed version control). Its much more of a loss for Canonical/Ubuntu because they can't use the nice fixes and changes that Debian make.

The overall structure of events versus dependencies and support for none linux kernels is more likely to decide the issue.

---

### Post by vasa1 on 2014-01-21
> **vasa1 said:**
> ...
There's reference to Canonical's "contributor license agreement" as one obstacle, if that is an appropriate word, to upstart's acceptance. Why is that?
It seems that CLAs are being discussed elsewhere with very interesting comments here: [https://plus.google.com/111049168280159033135/posts/NstZfwXbAti](https://plus.google.com/111049168280159033135/posts/NstZfwXbAti) and some of the names seem to be respectable.

---

### Post by ian-weisser on 2014-01-21
> **vasa1 said:**
> It seems that CLAs are being discussed elsewhere with very interesting comments here: [https://plus.google.com/111049168280159033135/posts/NstZfwXbAti](https://plus.google.com/111049168280159033135/posts/NstZfwXbAti) and some of the names seem to be respectable.

And lots of the same-old-flamebait retreads, too. By respectable names.

---

### Post by vasa1 on 2014-02-10
[http://www.itwire.com/opinion-and-analysis/open-sauce/63079-debian-init-system-vote-has-become-a-farce](http://www.itwire.com/opinion-and-analysis/open-sauce/63079-debian-init-system-vote-has-become-a-farce)

---

### Post by kostkon on 2014-02-10
Actually, Canonical vs Red Hat, again..

---

### Post by buzzingrobot on 2014-02-11
This is a discussion about something that ought to be invisible to users in normal day-to-day use. Regardless of the init system used, developers could expose it to users via a GUI. Whether they should do that is very debatable because relatively few users know enough to reliably identfy services they do not need,  much less recognize them by name. Distribution pacakgers should just avoid starting services that aren't approriate to the installed envirionment.

Meanwhile, anyone holding out hopes for One Universal Approach to rule all of Linux is, as usual, engaging in wishful thinking. It won't happen.  It shouldn't happen. Slavish adherence to standards blocks innovation.

---

### Post by 1clue on 2014-02-11
It's definitely Redhat vs the rational Linux world.

There has been a very hot set of threads on this on Gentoo forums.  Systemd is a travesty.  A service, especially an init service, should do exactly one thing and do it really well.  Systemd is trying to be lots of things.

The biggest problem in my opinion is the way it's being promoted.  Throughout the history of Open Source, some group writes a component, people start using it and it slowly gains traction based on how good it is in relation to everything else that performs the same service.  Projects/apps are born, mature, age and die based on their usefulness, and they're pretty much interchangeable because they all do one thing, no problem.

This time, Redhat made systemd and it does lots of things, people are starting to make their apps depend on it specifically and they're basically trying to force it down everyone's throats.

I haven't looked much at Canonical's offering, but it can't be much worse than systemd.  The whole point of Open Source is that we should be able to use what we want.  It doesn't matter much with a binary distro as far as the end user is concerned but it DOES matter when it comes to new distros or any source-based distro.

---

### Post by buzzingrobot on 2014-02-12
> **1clue said:**
> 

This time, Redhat made systemd and it does lots of things, people are starting to make their apps depend on it specifically and they're basically trying to force it down everyone's throats.



Hard for me to see how RH is forcing anything on anyone.  If developers of X want to make Y a dependency, that's their call.  It's the way Linux is designed and built.  If a developer wants to use X but avoid Y, let him code his way out of it.  After all, the source is there. 

The contradiction between asserting that FOSS is about choice (it isn't; it's about access to source) and the insistence that all of FOSS standardize as much as possible is obvious, but widespread.

---

### Post by vasa1 on 2014-02-12
> **1clue said:**
> It's definitely Redhat vs the rational Linux world.
...
But what about Arch and OpenSUSE? Don't they also use systemd?

---

### Post by mips on 2014-02-12
> **vasa1 said:**
> But what about Arch and OpenSUSE? Don't they also use systemd?

Yes.

Aptosid
Arch Linux
Chakra Linux
CoreOS
**Debian GNU/Linux**
Fedora
Frugalware Linux
Gentoo Linux
Mageia
Manjaro
openSUSE
Red Hat Enterprise Linux
Sabayon Linux
siduction

---

### Post by mips on 2014-02-12
[https://lists.debian.org/debian-ctte/2014/02/msg00405.html](https://lists.debian.org/debian-ctte/2014/02/msg00405.html)

**Bug#727708: call for votes on default Linux init system for jessie**

[HR][/HR]
[LIST]
[*]*To*: Anthony Towns <aj@erisian.com.au>
[*]*Cc*: [email]727708@bugs.debian.org[/email], [email]secretary@debian.org[/email]
[*]*Subject*: Bug#727708: call for votes on default Linux init system for jessie
[*]*From*: Bdale Garbee <bdale@gag.com>
[*]*Date*: Tue, 11 Feb 2014 07:35:13 -0700
[*]*Message-id*: <[87vbwlvhsu.fsf@rover.gag.com]("https://lists.debian.org/debian-ctte/2014/02/msg00405.html")>
[*]*Reply-to*: Bdale Garbee <bdale@gag.com>, [email]727708@bugs.debian.org[/email]
[*]*In-reply-to*: [<]("https://lists.debian.org/msgid-search/20140211084517.GA21823%40master.debian.org")[20140211084517.GA21823@master.debian.org]("https://lists.debian.org/debian-ctte/2014/02/msg00402.html")>
[*]*References*: [<]("https://lists.debian.org/msgid-search/20140211084517.GA21823%40master.debian.org")[20140211084517.GA21823@master.debian.org]("https://lists.debian.org/debian-ctte/2014/02/msg00402.html")>
[/LIST]
[HR][/HR]Anthony Towns <aj@erisian.com.au> writes:

> A.6.6: Schwartz set is {D,U}
> A.6.8: There are no defeats in the Schwartz set, so the elector with
>        the casting vote chooses which of these options wins.
>
> Per 6.3.2, the casting vote is held by the Chairman, who is currently
> Bdale.

Thank you, Anthony, for your analysis of the votes.

Per 6.3.2, I use my casting vote to choose D as the winner.

Therefore, the resolution reads:

  We exercise our power to decide in cases of overlapping jurisdiction
  (6.1.2) by asserting that the default init system for Linux
  architectures in jessie should be systemd.

  Should the project pass a General Resolution before the release of
  "jessie" asserting a "position statement about issues of the day" on
  init systems, that position replaces the outcome of this vote and is
  adopted by the Technical Committee as its own decision.

Bdale

---

### Post by mips on 2014-02-12
So it looks like it's gonna be systemd for Debian Jessie.

[http://www.reddit.com/r/linux/comments/1xm7c6/bdale_officially_uses_his_casting_vote_to_choose/](http://www.reddit.com/r/linux/comments/1xm7c6/bdale_officially_uses_his_casting_vote_to_choose/)
[http://www.phoronix.com/scan.php?page=news_item&px=MTYwMDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTYwMDQ)
[http://www.vitavonni.de/blog/201402/2014021101-debian-chooses-systemd-as-default-init.html](http://www.vitavonni.de/blog/201402/2014021101-debian-chooses-systemd-as-default-init.html)
[http://www.muktware.com/2014/02/finally-debian-chose-systemd-default-init-systemd-bye-bye-upstart/20887](http://www.muktware.com/2014/02/finally-debian-chose-systemd-default-init-systemd-bye-bye-upstart/20887)

---

### Post by 1clue on 2014-02-12
Redhat and Gnome have been politicking hard for systemd.  Post #13 on this thread shows a list of distros, but some of that I know to be false.

For example, Gentoo only requires systemd if you use gnome, which is the way it should be because gnome has hardcoded a dependency for systemd on it.  Otherwise there is no dependency on a particular init system.

Also based on discussions in Gentoo and the associated links in those discussions, it's obvious that there's a bunch of bad information out there, mostly exaggerating who has adopted it and to what degree they have adopted it.

I don't deny that projects can choose their dependencies, but an init system?  Really?  And on top of that there are people joining forums solely to push systemd.

FOSS IS about choice.  You should be able to choose which software you run.  There are several init systems out there, and a lot of politicking about how many projects require systemd, in an attempt to convince distros that they should make it the default.  I don't know why, but it seems many of these choices are not made by merit of the package.

By adding a bunch of extra junk onto systemd, it's no longer just an init system.  If too many projects drink the bad kool-aid and start believing it's actually better for every use case, then they start coding it into their projects the way Gnome has.  I have yet to be convinced that it's better for ANY use case, but if anything it would be the full-blown desktop.  Most of my Linux installations are not full-blown desktops, and the minimal server use case is definitely NOT helped by systemd.

I'm all about allowing choice, but IMO it should be an informed choice.  People who care about their boot process and init system should see what the fuss is about and make their own call.

---

### Post by mips on 2014-02-12
> **1clue said:**
> Redhat and Gnome have been politicking hard for systemd.  Post #13 on this thread shows a list of distros, but some of that I know to be false.

For example, Gentoo only requires systemd if you use gnome, which is the way it should be because gnome has hardcoded a dependency for systemd on it.  Otherwise there is no dependency on a particular init system.


Well point out all the false info, it's a list I got from wikipedia which we all know is not the be all and end all of information sources.

Gentoo supports both OpenRC & systemd, they are not enforcing systemd as a defacto standard.
[http://wiki.gentoo.org/wiki/Project:Systemd/Ebuild_policy](http://wiki.gentoo.org/wiki/Project:Systemd/Ebuild_policy)

---

### Post by 1clue on 2014-02-12
One of the Gnome guys (Olav Vitters) joined up on Gentoo forums just for that discussion.  I mentioned his blog and somebody else started pointing out errors.  I haven't heard from him since, and the errors are still there.  I thought you got the list from his blog, but evidently either he wrote the wikipedia page or somebody quoted him from it.  Or maybe the other way around?  His blog is unashamedly biased toward systemd (he mentions that at the top) so I don't know who wrote what first.

---

### Post by mips on 2014-02-12
> **1clue said:**
> One of the Gnome guys (Olav Vitters) joined up on Gentoo forums just for that discussion.  I mentioned his blog and somebody else started pointing out errors.  I haven't heard from him since, and the errors are still there.  I thought you got the list from his blog, but evidently either he wrote the wikipedia page or somebody quoted him from it.  Or maybe the other way around?  His blog is unashamedly biased toward systemd (he mentions that at the top) so I don't know who wrote what first.

Was not aware of that, I got the list from [http://en.wikipedia.org/wiki/Systemd#Adoption](http://en.wikipedia.org/wiki/Systemd#Adoption) ;)

Edit: All this talk of Gentoo has now given me an itch to install it again. Sigh and I swore my Gentoo days were over, must resist :biggrin:

---

### Post by vasa1 on 2014-02-12
> **1clue said:**
> Redhat and Gnome have been politicking hard for systemd.  Post #13 on this thread shows a list of distros, but **some of that** I know to be false.
...
Quite possibly. But what about Arch? Anyway, even assuming that Redhat owns/controls GNOME, the point is that individual distros have made choices.

---

### Post by mips on 2014-02-12
> **vasa1 said:**
> Quite possibly. But what about Arch? Anyway, even assuming that Redhat owns/controls GNOME, the point is that individual distros have made choices.

Well most of the bigger base distros have moved over, I suspect their derivatives will follow.

---

### Post by 1clue on 2014-02-12
> **mips said:**
> Was not aware of that, I got the list from [http://en.wikipedia.org/wiki/Systemd#Adoption](http://en.wikipedia.org/wiki/Systemd#Adoption) ;)

Edit: All this talk of Gentoo has now given me an itch to install it again. Sigh and I swore my Gentoo days were over, must resist :biggrin:

Install it if you have a reason.  It's a lot of work just to say you did it, but if nothing else fits your purpose then you can't beat a source-based distro.


> **vasa1 said:**
> Quite possibly. But what about Arch? Anyway, even assuming that Redhat owns/controls GNOME, the point is that individual distros have made choices.

Some distros have made choices, but the point I'm trying to make is that the list everyone seems to be using is incorrectly claiming adoption in at least one case.  If some distro looks at that list without checking its validity, and if users do the same, then that's not really a good thing.

A binary distro making a choice is OK.  Some of the binary distros I've used let you choose a different init system, but historically speaking a distro generally has a focus (desktops, servers, appliances, whatever) and they choose their packages based on what works best for their application.  That's perfectly fine.  But if they make their decision based on false input, surely you can see how that would be bad?

A source-based distro, I can't see any good reason to specify any single init system.  Or anything else for that matter.

---

### Post by lykwydchykyn on 2014-02-14
Well... I guess we can add Ubuntu to the list:

[http://www.markshuttleworth.com/archives/1316](http://www.markshuttleworth.com/archives/1316)

---

### Post by buzzingrobot on 2014-02-14
> **lykwydchykyn said:**
> Well... I guess we can add Ubuntu to the list:

[http://www.markshuttleworth.com/archives/1316](http://www.markshuttleworth.com/archives/1316)

Rather inevitable.  

These kind of decisions are big dreals for developers and distro packagers.  But, for users, the gains and losses, if any, only show up as new capabilities that might be exposed as a result.  Otherwise, it's plumbing buried in the walls.

(Caveat:  If you know enough about you init system to leverage or otherwise mess around with it, I'd say you've left the ranks of mainstream userdom and become a tinkerer.  That distinction is relevant because folks like Canonical, et al, are making software for users, not tinkerers.)

---

### Post by ikt on 2014-02-14
If anyone is interested in learning a little bit about systemd have a watch of this:

[http://mirror.internode.on.net/pub/linux.conf.au/2014/Monday/175-The_Six_Stages_of_systemd_-_Rodger_Donaldson.mp4](http://mirror.internode.on.net/pub/linux.conf.au/2014/Monday/175-The_Six_Stages_of_systemd_-_Rodger_Donaldson.mp4)

It's called 'The Six Stages of SystemD'!

---

### Post by mips on 2014-02-14
Would love to hear what [ian-weiser]("http://ubuntuforums.org/showthread.php?t=2200186&p=12903350&viewfull=1#post12903350") has to say now :biggrin:

---

### Post by mips on 2014-02-14
Just to throw another spanner into the works I somehow suspect a similar outcome wrt to MIR vs Wayland. they will punt it but at the end of the day when everyone but Ubuntu (excluding kubuntu, xubuntu, lubuntu) uses wayland it becomes pretty lonely out there and the logistics of swimming against the stream becomes to much they will switch.

---

### Post by entw on 2014-02-14
I hate the fact that it happened, but we should only blame Debian.

---

### Post by mips on 2014-02-14
> **entw said:**
> I hate the fact that it happened, but we should only blame Debian.

Then you should probably also admonish debian for ubuntus existance, or not?

---

### Post by entw on 2014-02-14
> **mips said:**
> Then you should probably also admonish debian for ubuntus existance, or not?

Why? I can't see the logic here.

---

### Post by ian-weisser on 2014-02-14
> **mips said:**
> Would love to hear what [ian-weiser]("http://ubuntuforums.org/showthread.php?t=2200186&p=12903350&viewfull=1#post12903350") has to say now :biggrin:

-Snort-...huh?
(Blinks blearily)
Why, what happened?
Did the flamethrowers run out of fuel?
EDIT: Oh, I see. Debian chose systemd for init, and SABDFL announced  that Ubuntu will match debian by changing to systemd for init.

My position hasn't changed: Debian is blessed with two good, new init alternatives. I wish *my* problems were deciding among good choices.

I was, of course, wrong when I predicted a slow decision.

I stand by my opinion that Phoronix is a lousy source for good, dispassionate analysis.

---

### Post by vasa1 on 2014-09-03
[s]Now[/s] there's a website for those not in favor of systemd: [http://boycottsystemd.org/](http://boycottsystemd.org/)

While that link is quite technical, "binary blob" and "SPOF" (single point of failure) aren't comforting.

---

### Post by rrnbtter on 2014-09-03
Greetings,
That site has been up for a while, it is not new. I take it to be just more of the same old high chair banging over the demise of the older Linux OS/Desktop/Tools that fit the low powered systems of yesteryear. I am not personally interested in flag waving only the enjoyment of a forward moving experience. Ubuntu and Unity so far has fit the need. I am updating my Ubunut-next on a daily basis and so far am please with the clumsy results. :)  P.S. SystemD seems to fit the new paradigm just fine!

---

### Post by vasa1 on 2014-09-03
> **rrnbtter said:**
> Greetings,
That site has been up for a while, it is not new. ....
Okay, I'll remove "Now" :)

---

### Post by 1clue on 2014-09-03
I think there's a lot to the argument.  Systemd might become good enough in the future but I don't think it is now.  The single point of failure argument is huge IMO, and the complexity of systemd and all its so-called optional components that somehow always need to be loaded anyway.

Linux is built on the premise that an app does exactly one thing, and does it really well.  Systemd is slowly taking over the entire system.  This is not good, it's not faster and it's not better.

---

### Post by buzzingrobot on 2014-09-03
> **1clue said:**
> I think there's a lot to the argument.  Systemd might become good enough in the future but I don't think it is now.  The single point of failure argument is huge IMO, and the complexity of systemd and all its so-called optional components that somehow always need to be loaded anyway.


An identical argument could be made about the kernel and X.

> Linux is built on the premise that an app does exactly one thing, and does it really well.  Systemd is slowly taking over the entire system.  This is not good, it's not faster and it's not better.

Well, systemd is not an application.  It's a replacement for, and an enhancement of, an init system organized rather haphazardly over the years as a long chain of interconnected shell scripts. Neither solution is simple, and can't be.

Linux was created by Torvalds because he was a college kid who wanted, but could not afford, a real Unix, source and all. By that time, Unix was well beyond it's very early one-tool-for-one-task aproach (even then mostly a virture made from necessity: slow, weak hardware.)  That approach has merit when users are sophistcated  and skilled enough to create scripts to leverage those simple tools, piping output from one into input of another, etc., *and* when graphic displays and mice weren't available.  Making GUI tools that "do one thing and one thing well" doesn't really make sense.

As a user who spent a good amount of time in the past dealing with the innards of Linux when that was mandatory if you wanted a usable and functioning desktop, I think the workings of the init system counts as something I  -- as a user -- shouldn't -- and don't -- worry about.  Systemd has a job to do. If it does it well, I won't know it's there. If it does it poorly and draws attention to itself, I'll go find another distribution.

---

### Post by cariboo on 2014-09-03
I'm currently running Utopic with systemd enabled, and aside from a slight problem with cups, that has been fixed upstream, it works seamlessly. The only difference between upstart and systemd that I can see, is that the system starts a bit faster.

---

### Post by rrnbtter on 2014-09-03
Greetings,
@vasa1, Sorry for my comment regarding your post. I actually wasn't trying to correct your post. I neglected to follow with what was my intention to say, the boycott site was started prior to Ubuntu going to Systemd. Systemd got traction by being picked up by Redhat, Suse and the like that are heavy in the server market. Since it has the big guys behind it, it is strongly maintained. When it started to migrate into Fedora, Debian and the desktops is when the creator of the boycott got a fire burning. I kind of get his point. There has been a consistant segment of the user base that want to keep it simple and they seem to be pretty vocal about their concerns. What I think is that Puppy Linux and quite a few others do a really good job in the "small" segment of Linux. Its obvious to me the Canonical has other asperations. I personally like the way that Systemd works and the general direction of Ubuntu/Unity.

---

### Post by 1clue on 2014-09-03
> **buzzingrobot said:**
> An identical argument could be made about the kernel and X.


Really, about neither.  The kernel is an interface between the hardware and a standard API.  It really does nothing much else.

X is a windowing interface:  An APi for an app to specify drawing things in a rectangle.  The specification is handled by the app.  On top of X you specify a window manager:  A basic API for drawing window frames and controls for them, and handling basic events based on that.  And so on.

> 
Well, systemd is not an application.  It's a replacement for, and an enhancement of, an init system organized rather haphazardly over the years as a long chain of interconnected shell scripts. Neither solution is simple, and can't be.


I certainly would classify it as an app.  Some might call it a daemon, but it's an app which handles startup of system resources.  It's what runs the stuff that runs your system.  To date it has had a very simple purpose and has performed it well.  OpenRC is orders of magnitude simpler than systemd, and systemd offers nothing of interest to me in the first place.

Why should I multiply my system's attack surface by a hundred for no benefit?  Why should the boot code insist on changing our filesystem layout?  Why should the boot system insist on javascript in the boot process?  Javascript is the least secure language ever written for computers, and has no business where they put it.

> 
Linux was created by Torvalds because he was a college kid who wanted, but could not afford, a real Unix, source and all. By that time, Unix was well beyond it's very early one-tool-for-one-task aproach (even then mostly a virture made from necessity: slow, weak hardware.)  That approach has merit when users are sophistcated  and skilled enough to create scripts to leverage those simple tools, piping output from one into input of another, etc., *and* when graphic displays and mice weren't available.  Making GUI tools that "do one thing and one thing well" doesn't really make sense.


When I got into this, X (Xfree86) was a novelty that took days to download over a 1200 baud modem, compile and set up.  It was unstable and completely unnecessary.  Today, almost all my Linux installations are headless without any sort of GUI.  Frankly, I'd say that most current Linux installations in the world are headless without a desktop.  Why should these systems use systemd?

The init system has changed dramatically since I started, even if you ignore systemd.  But it's always had an elegant, single-purpose structure.  Different distros didn't always have the same one, and sometimes offered alternatives.

That's the key here:  To date every init system has been an interchangeable part, up until recently.  Lennart is trying to insist that all of Linux do things his way:  The Microsoft way.

> 
As a user who spent a good amount of time in the past dealing with the innards of Linux when that was mandatory if you wanted a usable and functioning desktop, I think the workings of the init system counts as something I  -- as a user -- shouldn't -- and don't -- worry about.  Systemd has a job to do. If it does it well, I won't know it's there. If it does it poorly and draws attention to itself, I'll go find another distribution.

Average people should not have to worry about the init system.  For years, most Linux users have cared less about it.  For those users who DO care, it's important.

Systemd has a lot of flaws.  For one thing, they insist on the presence of /usr during boot.  That's a terrible idea.  Traditional init systems like openrc have /bin and /sbin specifically so the / partition can be small.  Only core files needed at boot need to be on /.  These core files are rarely updated and as such if you handle your partitions correctly your / partition has very few writes and has much smaller chance of errors.  /usr is supposed to get files which are "regular" applications not necessary during boot.  These are updated much more frequently, and they take a lot more space, many times more than those in /bin and /sbin.  Statistically speaking, the partition with the files normally found in /usr is much more likely to have an error.  If you MUST load /usr during boot, and it has an error, then you just don't get to boot.

The list goes on and on and on.

---

### Post by 1clue on 2014-09-03
> **su:bhatta said:**
> one of the many reasons I just like Debian. Specially  "Debian's governance is specifically set up to encourage inaction when there is a lack of consensus."


Actually it's one of the reasons I **don't** like Debian.  I'd rather they be more up-to-date and decisive, and intelligent while they're at it.

---

### Post by vasa1 on 2014-10-17
[http://lwn.net/Articles/616571/](http://lwn.net/Articles/616571/)
> This GR seeks to preserve the freedom of our users now to select an
  init system of their choice, and the project's freedom to select a
  different init system in the future.

---

### Post by buzzingrobot on 2014-10-17
Well... users are always free to grab the source of whatever init system they like and build and go from there. (I'm not sure why users might care about the inner workings of their init system, though, other than the fact that it works.)

When we use software built and packaged by other people, we are always constrained by the choices they make.

---

### Post by Lars Noodén on 2014-10-17
> **buzzingrobot said:**
> Well... users are always free to grab the source of whatever init system they like and build and go from there. (I'm not sure why users might care about the inner workings of their init system, though, other than the fact that it works.

There is a misunderstanding.  Systemd is not an init system, though I don't know what to call it yet.  

If systemd were just an init system then that approach would work and few would have issue with systemd.  However, it passed that phase a long time ago and now feature creep has expanded it to also include half-baked versions of udev, logging, dhcp, ntpd, cron, automount, inetd, and network configuration just to name a few.   And, code quality issues aside, it is as modular as a good stew.  It is impossible to replace or change one without replacing all of systemd.  Further, the logging is in a complicated binary format.  In short, the more it becomes ingrained in a distro, the less freedom users have to grab the source of whatever init system they like and build and go from there.  The technical and organizational problems can be listed for pages.

There is a (real or perceived) need for a new init system, but systemd is not it.

---

### Post by buzzingrobot on 2014-10-17
All those things should be invisible to a user. Userland capabilities should be exposed via individual GUI-fied tools that hide the underlying plumbing.

I was attempting to be facetious with that remark about users grabbing source and building their own init system. To me, that's the dividing line between "user" and "developer".  Distributions choose which demographic they target, and will make choices that are constrained by that fundamental decision. Anyone adopting a distribution is also constrained by that decision.

---

### Post by RichardET on 2014-10-17
So currently Ubuntu is still not using systemd?

---

### Post by 1clue on 2014-10-17
Systemd is an init system that was built by a team who either does not comprehend the value of a simple, separate init system or does not want there to be any init system except theirs.  Yes I know who wrote it and have been following this topic for much more than a year on several forums.

I strongly disagree that we should depend on gui-fied anything.  I have more than a dozen Linux boxes, some of which are VM hosts, and only a small handful even have a gui.  There's no reason to do so.

Systemd is clearly broken from the concept up.  Redhat likes the idea of what it does, and they have many more dollars to throw at it than everyone else combined, so all their projects are starting to require systemd.  Doing that is insane, there is no reason why any post-init system should require a specific init system.

---

### Post by buzzingrobot on 2014-10-17
> **1clue said:**
> Systemd is an init system that was built by a team who either does not comprehend the value of a simple, separate init system or does not want there to be any init system except theirs.  Yes I know who wrote it and have been following this topic for much more than a year on several forums.

I strongly disagree that we should depend on gui-fied anything.  I have more than a dozen Linux boxes, some of which are VM hosts, and only a small handful even have a gui.  There's no reason to do so.

Systemd is clearly broken from the concept up.  Redhat likes the idea of what it does, and they have many more dollars to throw at it than everyone else combined, so all their projects are starting to require systemd.  Doing that is insane, there is no reason why any post-init system should require a specific init system.

If you run a dozen Linux boxes, most without a GUI, you are far from being a typical user. You're an admin.

If you know enough to cope with those dozen boxes, then you should be able to learn enough to cope with systemd, or switch to an OS that doesn't use it.

*Users* are not admins.  *Users* are not developers. Users are people who buy devices to run applications.  *Anything* they need to do should be made as easy, as simple, and as foolproof as possible.

The notion that only admins and developers should determine what should and should not be in Linux is a notion that will doom Linux to remain as marginalized as it has been for the last two decades.

---

### Post by sffvba[e0rt on 2014-10-18
> **RichardET said:**
> So currently Ubuntu is still not using systemd?

Not yet, it will change once it is in use by the version of Debian that is used for that release.

---

### Post by mips on 2014-10-18
> **not found said:**
> Not yet, it will change once it is in use by the version of Debian that is used for that release.

I did a Debian Sid install the other day and that uses systemd.

---

### Post by RichardET on 2014-10-18
> **not found said:**
> Not yet, it will change once it is in use by the version of Debian that is used for that release.

Thus if one remains with 14.04, one should remain systemd free?

---

### Post by ian-weisser on 2014-10-18
> **RichardET said:**
> Thus if one remains with 14.04, one should remain systemd free?

Yes, 14.04 will use Upstart until support ends in 2019.
Such a major change mid-release would quite undermine the entire concept of calling the release "LTS."

---

### Post by 1clue on 2014-10-19
> **buzzingrobot said:**
> If you run a dozen Linux boxes, most without a GUI, you are far from being a typical user. You're an admin.


Correct.

> 
If you know enough to cope with those dozen boxes, then you should be able to learn enough to cope with systemd, or switch to an OS that doesn't use it.


Correct.

> 
*Users* are not admins.  *Users* are not developers. Users are people who buy devices to run applications. 


Not necessarily correct, especially when they install a non-stock operating system on a computing device.

> 
*Anything* they need to do should be made as easy, as simple, and as foolproof as possible.


Incorrect.  If you installed any form of Linux -- even Ubuntu -- on a computer, you're an admin.  You may not know enough to be an effective admin, but you're an admin nonetheless.

However, there is something to agree with:  Any software system critical to the operation of the machine needs to be as simple and foolproof as possible, while fulfilling the task.  Systemd is the most complex piece of software ever positioned as an init system on any free UN*X, and probably significantly more complicated than any of the commercial options.  It is so complicated that it is overrunning many other systems which should remain separate.

The thing that should worry everyone is that its complexity dictates factors which should not matter to an init system, and which cause the system to be less reliable and less secure.  The thing that should worry every Ubuntu user is that Gnome Desktop, which is being driven by the same company as Systemd, has declared a hard dependency on Systemd.

From a political and monetary standpoint, the motive for doing this is extremely clear, there can be no question.  From a security and reliability standpoint systemd is potentially catastrophic.  The attack surface is massive compared to any other init system on Linux.

> 
The notion that only admins and developers should determine what should and should not be in Linux is a notion that will doom Linux to remain as marginalized as it has been for the last two decades.

Oddly enough, we agree on this one.  Let me phrase a scenario which exactly represents this situation in aeronautical terms:

Let's say you're going to fly on an airplane on a long trip.  You have a choice between 2 different jets.  The first has an engine with 1000 moving parts and has a mean time between failures of 100 thousand hours.  The second has an engine with 100 moving parts and has a mean time between failures of a million hours.  The first, by its nature is susceptible to misconfiguration and tampering by a hostile entity.  The second is much less susceptible.  Which jet do you choose?  The first jet is systemd and the second is pretty much every init system before it.

There is no significant benefit to systemd, and many many faults.

---

### Post by 1clue on 2014-10-19
All that said, it's possible that systemd could at some point become beneficial.  There are shortcomings in so-called legacy init systems that could benefit from an overhaul or rewrite.

If the systemd team can pull their heads out and get rid of the bloat, and address other real issues surrounding their product, then in some time I could be singing their praises.  It has happened lots of times since I started using Linux in the 90s where somebody has an idea, gets cranking and messes it up with bloat, and then gets it back into goodness after its rocky start.

---

### Post by buzzingrobot on 2014-10-20
> **1clue said:**
> 

Incorrect.  If you installed any form of Linux -- even Ubuntu -- on a computer, you're an admin.  You may not know enough to be an effective admin, but you're an admin nonetheless.


Of unfortunate necessity. It's not something users willingly take on, on Linux or elsewhere.  Arguing that Linux gives users the freedom and flexibility to do that, as with access to the shell, is making a silk purse out of a pig's ear. The overwhelming majority of users would be quite happy to avoid all that altogether if they could get their Linux systems to work satisfactorily without getting their hands dirty.

Whatever processes, etc., that are controlled by any init system, as well as anything systemd may or may not encompass, should be exposed to users at a very high level of abstraction, if they are exposed at all. That does not mean legitimate admins should be deprived of the finer grained access they need, but neither approach precludes the other. If systemd is removing some of that kind of access, then *that* criticism has merit.

> Any software system critical to the operation of the machine needs to be as simple and foolproof as possible, while fulfilling the task.  Systemd is the most complex piece of software ever positioned as an init system on any free UN*X, and probably significantly more complicated than any of the commercial options.  It is so complicated that it is overrunning many other systems which should remain separate.

I have no evidence, one way or the other, to substantiate that. I certainly don't think the mantra of "one tool for one task" has been applicable for years and years, certainly not since the first GUI's rolled out. (How, for example, do X or emacs fit that paradigm?)

I had a lengthy professional association with a good number of sys admins and, frankly, found many of them to be some of the most obstinate and change-averse professionals I've worked with. Sometimes that aversion was with good reason, and sometimes they just didn't want to be compelled to learn and do something different.  I'm not asserting all hostility to systemd is driven by simple aversion to change and the workload it brings, but I certainly believe some of it is.

My bottom line, though, is that the entire discussion is about something that should never be visible to users.

---

### Post by 1clue on 2014-10-20
> **buzzingrobot said:**
> Of unfortunate necessity. It's not something users willingly take on, on Linux or elsewhere.  Arguing that Linux gives users the freedom and flexibility to do that, as with access to the shell, is making a silk purse out of a pig's ear. The overwhelming majority of users would be quite happy to avoid all that altogether if they could get their Linux systems to work satisfactorily without getting their hands dirty.


I'm not sure exactly what you're talking about, but when I consider my friends and family who are Mac/Windows users I can see that they often don't know about system administration and therefore ignore it, but I'm pretty sure that given the choice of them administering the computer and having someone else do it they would probably tell me to get lost.  So no, I can't agree with you.

When I got into Linux, XFree86 was a novelty and pretty unstable, and there were no other real alternatives at the time.  It was years after it became stable that I started using a windowing system on Linux, and years after I had started using Linux as my workstation.

The issue I think is that most computer owners would rather that system administration not be necessary at all, and since they don't understand it they ignore it.

> 
Whatever processes, etc., that are controlled by any init system, as well as anything systemd may or may not encompass, should be exposed to users at a very high level of abstraction, if they are exposed at all. That does not mean legitimate admins should be deprived of the finer grained access they need, but neither approach precludes the other. If systemd is removing some of that kind of access, then *that* criticism has merit.


I don't know what you're talking about, but I don't like the sound of it.  It implies that there should be layer upon layer between the init system and a system administrator.  That's false.  Every layer of "abstraction" is a layer of obfuscation and yet another place a problem can exist.

There are already GUI tools to configure and control pretty much everything you want to control, if you install the gui.  That exists without systemd, so tell me again what systemd gives you?

> 
I have no evidence, one way or the other, to substantiate that. I certainly don't think the mantra of "one tool for one task" has been applicable for years and years, certainly not since the first GUI's rolled out. (How, for example, do X or emacs fit that paradigm?)


You have to be kidding.  X is a bunch of simple tools combined.  At its heart the server is a utility to draw a rectangle on a screen, and move it around.  It doesn't even handle window frames or content.  The window manager does that.  The window manager can be as complex or as simple as you want, but again this is plug and play, you can use any or none at all.  The client handles mouse/keyboard/whatever events and sends the requests to the server.  Browse the Ubuntu repository for X and Gnome, look how many components there are for each.

Editors:  Again, this is a need for the basic idea of editing text.  The system admin chooses editors based on that need, and that's that.  Emacs is a really good example of a sophisticated, modular programming editor with lots of plugins.  You get the basic editor and add to it what you want.  Likewise Vim (I'm a Vim guy) is a sophisticated modular editor with lots of available plugins.

The critical concept here is that neither X nor Emacs are critical to the boot process or to the operation of the system.  As such they're apples as compared to the oranges which are init systems.  Init systems are what ensure that the system works.  If there's a bug in one then nobody who uses that init system (likely that distribution) can have a stable system.

> 
I had a lengthy professional association with a good number of sys admins and, frankly, found many of them to be some of the most obstinate and change-averse professionals I've worked with. Sometimes that aversion was with good reason, and sometimes they just didn't want to be compelled to learn and do something different.  I'm not asserting all hostility to systemd is driven by simple aversion to change and the workload it brings, but I certainly believe some of it is.

My bottom line, though, is that the entire discussion is about something that should never be visible to users.

And some of them are averse to change simply because they like the good old days.  I'm not that way.  I'll set up a new box just to play with the new idea for awhile, and then if I don't like it I'll scrape it off and put something else on.  Moreover, I'm  not averse to mixing commercial software in with an Open Source environment.  I've bought several commercial tools because I thought they were worth it.  Since you mentioned editors above, Sublime Text 2 works equally well on Windows, Mac and Linux.  As a GUI editor goes it's tiny, less than 7M download, and it's one of the most flexible and easy editors I've ever used.  It has lots of plugins from lots of different groups.  I still use vim about half the time, but I have no problems with paying for this one.

If the discussion were truly about "users" then you're right.  The init system shouldn't matter.  On the systems where I am root, almost nobody even heard of an init system, let alone knowing or caring what it's for.  For many years after I started using Linux, I didn't know.  Even after I learned about the boot process, I didn't know an init system was a distinct part of that.

What I care about, and what you and everyone else using Ubuntu should care about, is whether the core functionality of Linux is bloated and/or crippled due to some small team's desire to have it their way, and to insist that everyone else have it their way too.  Meaning, the systemd way, not the way you might choose if you knew about and cared about the options.

I'm not telling you or anyone else which init system to use.  I'm telling you that stepping into it blind might be an unfortunate decision if your use case and opinion does not match the Redhat Way.

---

### Post by buzzingrobot on 2014-10-20
> **1clue said:**
> ... when I consider my friends and family who are Mac/Windows users I can see that they often don't know about system administration and therefore ignore it, but I'm pretty sure that given the choice of them administering the computer and having someone else do it they would probably tell me to get lost.  So no, I can't agree with you.

They should not need to administer their computing devices. If, for example, they want to make sure something runs when they log in or boot up, then they ought to be able to do that simply and easily with no knowledge of the system's interior plumbing, or even that it exists.  I.e., fill in a blank or click on a filename.

Expectations about using computing devices are being set by phones and tablets, not by Linux admins. The idea that all users want to ,or will, get smart and demand free access to everything on their systems is as much a nonstarter as it has always been. Some people want that, fewer need it, but they will always remain marginalized.

> I don't know what you're talking about, but I don't like the sound of it.  It implies that there should be layer upon layer between the init system and a system administrator.  That's false.  Every layer of "abstraction" is a layer of obfuscation and yet another place a problem can exist.

It requires that users be allowed to do the things users needs to do as easily and as simply as possible. That's not obsfucation. 

Life for users should not be made more difficult simply to make life for admins easier. There  is no truth to the notion that simplicity and ease of use are necessarily antithetical to capability.  That they often are contrived that way in much of today's software is a sad result of uncreative/bad/derivative/lazy software developers.

I'm a user, a user with close to 20 years experience in Unix and Linux.  I have done, and can still do, a great deal that I don't think users should need to do.  Since I also have a life, though, I'm happy that Linux on the desktop has progressed to the point that I can use it without getting my hands dirty in its plumbing. I have no idea what systemd will mean to me. Nor do I care much.  I'll judge distributions that use it on their merits.  Hopefully, I won't need to know what's going on behind the scenes.

---

### Post by ZoiaGuyver on 2014-10-20
Well this I guess is probably the "discussion" that will, if anything destroy the Linux "community". 

Let me explain that comment a little more, the community for all the years I have been part of it has had a choice on what we wanted to use on "our" own systems. Whether it was trivial or not each person still had the choice. systemd is not about having a "choice" its a "You will do it my way or no way" Redhat solution. Why does an "init" system that controls boot processes have to also control hardware management (udev), networking (the latest DHCP stuff they are including), desktop enviroment (login) and god knows what else (whatever Redhat decides is the next thing they want to control I guess)... Upstart was imo a far better solution with most of the advantages of systemd but not even a fraction of the intrusiveness. The latest on it is even Debian are still up in the air on the choice as there has been a backlash from users, devs, admins about exactly how all encompassing systemd is.

I'm a long term linux/unix user (over 15 years on my own machines (for linux) and 20+ for Unix in general) systemd is probably the worst thing I have seen happen to the linux community in that time, it even makes the ruckass with Pulseaudio (Redhat again) pale in comparison. I've actually been reading a lot on this, when you read about kernel leaders/devs not accepting patches from people writing systemd due to it "breakage" of userspace and the systemd devs saying that obvious bugs (the whole syslog argument) is to be "ignored" as they can't fix the problem worries me even more.

People will choose what they want to use but systemd has about asmuch "Unix" philosophy as MS do, actually MS probably has more of it. 

If you look around you will see a lot of devs asking questions about systemd that they can't answer or are ignored. has GNU/Linux really came to the point where its a "do as we say" dictatorship.

People spout off about Ubuntu all the time badmouthing them for "forking" projects or "taking" different routes, yet those same people that badmouth are fine to take everything Redhat says as gospel.. Redhat is probably the biggest contributor to Linux in general, because they have people in every section of the community. 

Most of the reasons people spout about when it comes to "linux" in general is "freedom" but where is the "freedom" with systemd? when it's being crammed down your throat by almost every distro because they have no choice.. it has became a dependency for so much of the system that is actually confuses some of the smartest people in our community (go read up on Linus Torvalds and Theodore Ts'o remarks on it). 

systemd does not have a "unix" like direction, hell i'd go as far as to say it doesn't have an open-source direction as it just wants to be linked to everything while playing nicely with only the parts that Redhat has a part in.

Now I know the user outlook on things, they don't care aslong as it works and that by me is fine, but how the hell is giving them something that's basically "Windows open-source ala Redhat" going to "just work". Redhat just want to brute force everything into what suits them, they already have control over a lot of projects, have shown in the past the unwillingness to be "open".

One thing with Microsoft I always respected was atleast you knew you were being screwed over from the EULA. Redhat imo is screwing over most of the community by forcing us to use certain things that we don't want to. I don't want a "system deamon" that basically rules everything I do on my system, including the other daemons. 

I'm saddened and infuriated at the same time that the so called "linux advocates" are all for bashing Canonical for things like Mir and Upstart, yet they are all fine for things like this and spout about "this is unifying" You can't unify anything that is controlled by a small section of elitists with their heads so far up each others backsides they rarely see daylight..

I'm sorry for the rant, but all this coming out at the moment and Redhat being the centre of 99% of it has really got me frustrated. Linux isn't meant to be "locked down" yet that is exactly what Redhat and systemd are looking to do, the vocal majority who take offence to Canonical giving a "choice" to users are also the same ones allowing Linux to become no more than another "Walled garden" except Linux has a bit more Trellis.

---

### Post by buzzingrobot on 2014-10-20
> **ZoiaGuyver said:**
> 

Let me explain that comment a little more, the community for all the years I have been part of it has had a choice on what we wanted to use on "our" own systems. Whether it was trivial or not each person still had the choice.

It's always been developers and software vendors who have determined the course of Linux, not users.  It can't be any other way because Linux is software, nothing more and nothing less.  Users do not create software.  Users have considerably fewer ways to influence developer choices within FOSS than they do in the commercial sector.  For example, Windows 10 will differ from Windows 8 because Win8 isn't generating enough revenue.  Meanwhile, people can go on ranting about Gnome 3 for years and it want have any influence at all on Gnome developers, because they don't need anything from users. Any influence FOSS users have on FOSS developers is at the consent of the developers.

The choices users have in Linux are constrained by the choices made by developers, not the other way around.  FOSS exists to provide freedom to software developers, first and foremost.

The debate about systemd is a debate about something that is no more relevant to users than what is going on inside their TV's.  People want TV's to do what they buy TV's to do, period. Ditto computing devices.

> ..."Unix" philosophy...

It's a lovely thing.  I've read the books.  Worked my way through "Software Tools" on a green screen and 286 umpteen years ago. No one else really cares.   And shouldn't.  Anyway, it all vanished when hardware got capable enough that people could avoid living inside shell scripts and pipes leveraging one tool for one job. If it was all that appealing, you know, we'd all still be using ed and awk and our green phosporous displays..

---

### Post by mikodo on 2014-10-20
> **buzzingrobot said:**
> 

My bottom line, though, is that the entire discussion is about something that should never be visible to users.

I have no technical knowledge, to base an opinion on. I do enjoy seeing dialogue by knowledgeable people with linux (adms.), bringing issues to the table for needed discussion. If I, a casual user, can see the issues being discussed, it may help me make decisions for the future with my OS's choices. To me, there is merit in open discussion. I think it has more merit for our younger upstart professionals, (who may not have reached development channels yet) to witness how linux has come to where it is, and to see how open dialogue is important for decision making for all of linux and is needed to provide them with history to give them a knowledgeable foundation for taking their turns at growing linux openly, through informed discussion. These kind of open discussions, probably will do more to grow linux in the future, than closed discussions. I don't see any downside, to open discussions with everyone who has an interest, being able to read.

---

### Post by buzzingrobot on 2014-10-20
> **mikodo said:**
> I have no technical knowledge, to base an opinion on. I do enjoy seeing dialogue by knowledgeable people with linux (adms.), bringing issues to the table for needed discussion. If I, a casual user, can see the issues being discussed, it may help me make decisions for the future with my OS's choices. To me, it has merit to be openly discussed. I think it has more merit for our younger upstart professionals, (who may not have yet reached development channels yet) that need to witness how linux has come to where it is, and to see how open dialogue is important for decision making for all of linux and is needed to provide them with history to give them a knowledgeable foundation for taking their turns at growing linux openly, through informed discussion. These kind of open discussions, probably will do more to grow linux in the future, than closed discussions. I don't see any downside, to open discussions with everyone who has an interest, being able to read.

Open debate is fine.  But this debate is about something -- systemd -- that ought not to be visible to users. Users should be able to use their software, day in and day out, without knowing it, or its alternatives, exist.

For years, Linux has followed a developer-centric and admin-centric path. This has led to Linux use by developers and admins and comparatively few marginalized users.  If we want Linux to succeed as a consumer desktop platform, it needs to follow a consumer-centric path. The admins will be paid, regardless.

---

### Post by mikodo on 2014-10-20
Well, if things haven't improved, (I hope they do) and I haven't lost too many marbles upon retirement, I may try Gentoo and Slackware. They could be a fun and viable alternatives to systemd. 

Too bad, I started with all this when I was old already.

Again, I appreciate open discussion in userland.

---

### Post by mips on 2014-10-21
> **ZoiaGuyver said:**
> 
Most of the reasons people spout about when it comes to "linux" in general is "freedom" but where is the "freedom" with systemd? when it's being crammed down your throat by almost every distro because they have no choice.. it has became a dependency for so much of the system that is actually confuses some of the smartest people in our community (go read up on Linus Torvalds and Theodore Ts'o remarks on it). 

You have freedom of choice, nobody is forcing you to use anything. You can install a different init system, choose a different distro, move to one of the BSDs or something like [COLOR=#333333][FONT=Arial]illumos etc.[/FONT][/COLOR]


> **mikodo said:**
> Well, if things haven't improved, (I hope they do) and I haven't lost too many marbles upon retirement, I may try Gentoo and Slackware. They could be a fun and viable alternatives to systemd. 


Have you used systemd before?  What improvements do you desire? You could always install a different init system or someone can make a respin based on openrc for example. I used a arch derived distro which has had systemd for yonks now and it does not bother me, someone else however created an openrc spin, choices.

---

### Post by vellon on 2014-10-21
Some random thoughts:

Too many opponents of systemd start with their conclusion (without using  it, obviously, although that is balanced by extensive internet  knowledge...), then search for evidence against it. Any scientist would examine the  evidence (objectively) and draw conclusions from that.

Idealism - one of the big issues with Linux. There is no shortage of those willing to pontificate about things that have no bearing on their, or others', usage patterns, but which the poster thinks of as fundamental to everyone.
Choice, for example. OK, so users want to pick their DE, applications, theme, etc, but normal users do not want to pick an init system. Anyone who thinks otherwise is not a normal user (and thinking of themselves as normal users is a common misconception on Linux forums).
The Unix way, small tools to do each job separately. If you use a graphical file manager, you are not using the Unix way. Someone comedically tried to defend emacs as a modular system. On my distro of choice, emacs is a monolithic 34MB, before dependencies. Non-lightweight Gedit is 2MB, and, for comparison, Firefox 35MB)

[complexities] "which cause the system to be less reliable and less secure" - I hear this often from the anti-systemd crowd. Systemd is undoubtably complex, but seems to have created remarkably few major issues. Why not outline some of these reliability and security problems you have personally had with systemd?

---

### Post by mikodo on 2014-10-21
> **mikodo said:**
> Well,** if things haven't improved**,  <snip>  

> **mips said:**
> Have you used systemd before?  What improvements do you desire? You could always install a different init system or someone can make a respin based on openrc for example. I used a arch derived distro which has had systemd for yonks now and it does not bother me, someone else however created an openrc spin, choices.

I have not tried systemd, but I am going to keep reading about it, due to the concerns others' have voiced. 

I shouldn't have said, "if things haven't improved", but rather, **if some of the concerns I have read become problematic, (for me)**, then .. the rest of what I have said. 

That more accurately portrays, what I was thinking.

---

### Post by mips on 2014-10-21
> **mikodo said:**
> I have not tried systemd, but I am going to keep reading about it, due to the concerns others' have voiced. 

I shouldn't have said, "if things haven't improved", but rather, **if some of the concerns I have read become problematic, (for me)**, then .. the rest of what I have said. 

That more accurately portrays, what I was thinking.


Could I suggest that you actually try it for yourself before forming an opinion based on what others are saying. Initially it's a bit of a learning curve and you might get frustrated.
One thing I'm not fond of is the binary logs but then again I don't spend much time digging around in log files.

---

### Post by mikodo on 2014-10-21
> **mips said:**
> Could I suggest that you actually try it for yourself before forming an opinion based on what others are saying. Initially it's a bit of a learning curve and you might get frustrated.
One thing I'm not fond of is the binary logs but then again I don't spend much time digging around in log files.

I just wanted you to know, I appreciate your suggestion.

---

### Post by 1clue on 2014-10-21
> **buzzingrobot said:**
> They should not need to administer their computing devices.


That's like having a car and never having to put in gas or change the oil, or check the tires.  Technically you don't have to do any of that, but the usefulness of the device suffers.  This isn't about what users WANT.  It's about what a computer owner must do.

> 

If, for example, they want to make sure something runs when they log in or boot up, then they ought to be able to do that simply and easily with no knowledge of the system's interior plumbing, or even that it exists.  I.e., fill in a blank or click on a filename.


They can already.  And systemd makes zero changes in that respect.  Generally speaking, you want to install something on your Ubuntu box, either server or desktop, so you figure out the name of it and install it.  Done.  How is systemd better again?

As far as an app starting when they log in, they're probably going to have to ask a question no matter what.  Even so, installing a service or automatically starting an app already exists, without systemd.  It's already pretty easy, without systemd.

> 
Expectations about using computing devices are being set by phones and tablets, not by Linux admins. The idea that all users want to ,or will, get smart and demand free access to everything on their systems is as much a nonstarter as it has always been. Some people want that, fewer need it, but they will always remain marginalized.


I make no claims on user expectations.  There are some things you must do as a computer owner.  There are some things you must do as a human.  Technically you don't have to eat or breathe, or brush your teeth.  I can see where humans would want to eat and breathe as something that brings happiness into their life, but brushing teeth must by any account be considered to be a maintenance task which as an 'administrative' thing you say regular users should not be bothered with.  Again, they don't have to.  But there are consequences.

> 
It requires that users be allowed to do the things users needs to do as easily and as simply as possible. That's not obsfucation. 

Life for users should not be made more difficult simply to make life for admins easier. There  is no truth to the notion that simplicity and ease of use are necessarily antithetical to capability.  That they often are contrived that way in much of today's software is a sad result of uncreative/bad/derivative/lazy software developers.


Systems should not layer complexity on complexity in order to coddle users.  Systems which are too helpful lose their flexibility and can only be used in a few ways.

I'm in no way claiming that things should be difficult for users.  I'm claiming that the 'never perform administrative tasks' requirement is false and does not happen in real life.  You ever look for new apps on your phone?  That's an administrative task.  You ever delete an app on a phone?  That's an administrative task.  You ever look at security settings on your phone?  Backups?  Security/lost phone service?  Change your data plan?

Simple devices have simple maintenance but they have it nonetheless.  A toaster requires maintenance, either that or you throw it out when it gets an inch of bread crumbs in the bottom.

We're talking about desktops and laptops and servers and mobile devices here.  Generally speaking, things bigger than a tablet or phone.  There will be administrative tasks, and neither systemd nor you will ever make that go away.

> 
I'm a user, a user with close to 20 years experience in Unix and Linux.  I have done, and can still do, a great deal that I don't think users should need to do.  Since I also have a life, though, I'm happy that Linux on the desktop has progressed to the point that I can use it without getting my hands dirty in its plumbing. I have no idea what systemd will mean to me. Nor do I care much.  I'll judge distributions that use it on their merits.  Hopefully, I won't need to know what's going on behind the scenes.

If you don't know what systemd will mean to you, then why are you arguing so strongly for it?  You should actually know something about it before you argue for or against.

---

### Post by buzzingrobot on 2014-10-21
> **1clue said:**
> If you don't know what systemd will mean to you, then why are you arguing so strongly for it?  You should actually know something about it before you argue for or against.

Because I haven't been arguing for it, or against it.  

What I've said is that the entire debate is about something -- plumbing -- that should be invisible to users.  Systemd and all of its predecssors and alternatives are just means to an end:  Better applications for users. 

Admins and greybeards are seizing on this because they see themselves losing control of Linux.  As a user, I tend to think that it would be a good thing if they lost control of Linux.  If admins and greybeards determine the course of Linux, only admins and greybeards will use Linux.

As I've said, I'll judge the results by the products that are delivered to me.  Whether systemd is inside or not won't matter.

---

### Post by 1clue on 2014-10-21
> **buzzingrobot said:**
> It's always been developers and software vendors who have determined the course of Linux, not users.  It can't be any other way because Linux is software, nothing more and nothing less.  Users do not create software.  Users have considerably fewer ways to influence developer choices within FOSS than they do in the commercial sector.  For example, Windows 10 will differ from Windows 8 because Win8 isn't generating enough revenue.  Meanwhile, people can go on ranting about Gnome 3 for years and it want have any influence at all on Gnome developers, because they don't need anything from users. Any influence FOSS users have on FOSS developers is at the consent of the developers.

The choices users have in Linux are constrained by the choices made by developers, not the other way around.  FOSS exists to provide freedom to software developers, first and foremost.

The debate about systemd is a debate about something that is no more relevant to users than what is going on inside their TV's.  People want TV's to do what they buy TV's to do, period. Ditto computing devices.


And the developers are users who decided they wanted something, learned to code and designed it to be the way they wanted it.  Or, they were hired by somebody who wanted a solution to work a certain way enough to have somebody else do it.

There ARE options for users, but you seem to think the Open Source community is something other than what it is.  The first bit of my code that wound up in the Open Source community got there when my boss put it there.  Much of Open Source comes from commercial entities and was built by paid developers.  Do you think those commercial entities don't have a profit motive?  Have you heard of Wine?  Have you heard of Crossover Office?

The entire point of Open Source was and still is to let people who want the product define the product.  Apache Web Server came into existence because a bunch of people really needed a web server with certain characteristics.  None existed, so they wrote one.  It looks the way they want it to, and generally speaking the way it looks is really good to other people who need web servers.  So it goes for pretty much every Open Source project.

> 
It's a lovely thing.  I've read the books.  Worked my way through "Software Tools" on a green screen and 286 umpteen years ago. No one else really cares.   And shouldn't.  Anyway, it all vanished when hardware got capable enough that people could avoid living inside shell scripts and pipes leveraging one tool for one job. If it was all that appealing, you know, we'd all still be using ed and awk and our green phosporous displays..

The really big questions for you:
[LIST=1]
[*]Does the visibility of a thing define its existence?
[*]If an init system is invisible, does it mean it is no longer there, or never was?
[*]If an init system is invisible does it mean its details are not important?
[*]Just because you think it should be invisible, does that outlaw any discussion of it on a forum?
[*]If people don't discuss it how do you expect anything to change?
[/LIST]

Here are some things I think you need to hear:
[LIST=1]
[*]As far as I've read on this thread so far, none of the things you seem to want are brought about by systemd.  Zero.
[*]Aside from the kernel, the init system is probably the most important piece of software on the computer.
[*]To date, Linux has supported several init systems which have been interchangeable.
[*]Interchangeable parts are as important for Linux as they are for your car.
[*]Systemd is not interchangeable with anything.  It does the things needed for an init system, but in taking it you take the entire trainload of garbage that comes with it, like it or not
[*]Nobody is forcing you to take part in this discussion.
[*]Nobody will make you leave either, but you should think about the true implications of what you're saying.
[/LIST]

---

### Post by buzzingrobot on 2014-10-21
> **1clue said:**
> 
... you seem to think the Open Source community is something other than what it is.

I think the open source community is a community of developers. FOSS was created by developers to benefit developers.

The list of arguments you offer re: systemd don't really address what I've said.

To repeat, the debate about systemd is about something that should be invisible to users. It's the job of developers to make good software for users.  How they do that -- what's in the plumbing, or whether it's coded in C++ or Algol or tied together with bits of string  -- doesn't matter to users so long as they like the product.

---

### Post by QIII on 2014-10-21
Take care to keep this discussion from devolving into a contest to see who can most thoroughly wet the other's shoes, please.

---

### Post by vasa1 on 2014-10-21
> **buzzingrobot said:**
> ...
To repeat, the debate about systemd is about something that should be invisible to users. ... -- what's in the plumbing, or whether it's coded in C++ or Algol or tied together with bits of string  -- doesn't matter to users so long as they like the product.
Not at all. Whether people understand the intricacies of what goes on behind the scenes or not isn't relevant to deciding whether what is going on is "good" or "bad". A trivial example is the Chrome versus Chromium issue. Some people's beliefs keep them from using Chrome.

---

### Post by 1clue on 2014-10-21
> **buzzingrobot said:**
> Open debate is fine.  But this debate is about something -- systemd -- that ought not to be visible to users. Users should be able to use their software, day in and day out, without knowing it, or its alternatives, exist.


This has absolutely nothing to do with the choice of an init system.  You're yelling about a non-issue.  Most Linux people don't have any idea what an init system is, and that's OK.

> 
For years, Linux has followed a developer-centric and admin-centric path. This has led to Linux use by developers and admins and comparatively few marginalized users.  If we want Linux to succeed as a consumer desktop platform, it needs to follow a consumer-centric path. The admins will be paid, regardless.

I'm not sure you understand the reality.  Back when I started this, the only people who used Linux were developers, because nobody else could even get it installed.

Linux is used on far many more desktops and far more in Enterprise than it ever has been, and it's used in these places as desktop environments even more than its server-side use has grown.

Redhat and Canonical and Oracle are all for-profit organizations.  Canonical is in control of Ubuntu.  Everything Canonical does is for profit in some way.  These organizations are market-driven because if the product doesn't earn them money in some way, they will drop the product.

That said, Redhat/Canonical/Oracle do not define Open Source.  Open Source is defined as a group of like-minded individuals collaborating on a product they all want to see.  You, as a user, can collaborate in some fashion even though you might not be a developer.  You are not powerless unless you choose to be.

---

### Post by 1clue on 2014-10-21
> **mikodo said:**
> Well, if things haven't improved, (I hope they do) and I haven't lost too many marbles upon retirement, I may try Gentoo and Slackware. They could be a fun and viable alternatives to systemd. 

Too bad, I started with all this when I was old already.

Again, I appreciate open discussion in userland.

Gentoo is awesome, it's my favorite distro if I have time to mess with it.  You'll learn more about Linux and how it works than you ever thought possible.

I haven't used slack since before Redhat went public.

---

### Post by 1clue on 2014-10-22
> **vellon said:**
> Some random thoughts:

Too many opponents of systemd start with their conclusion (without using  it, obviously, although that is balanced by extensive internet  knowledge...), then search for evidence against it. Any scientist would examine the  evidence (objectively) and draw conclusions from that.


And too many proponents hear that it's the latest thing and assume it is automatically better.

> 
Idealism - one of the big issues with Linux. There is no shortage of those willing to pontificate about things that have no bearing on their, or others', usage patterns, but which the poster thinks of as fundamental to everyone.
Choice, for example. OK, so users want to pick their DE, applications, theme, etc, but normal users do not want to pick an init system. Anyone who thinks otherwise is not a normal user (and thinking of themselves as normal users is a common misconception on Linux forums).


We actually agree on this one.  Almost nobody chooses an init system.  I've done it both ways using Gentoo.  You're correct in that I'm not a normal user.  You assume just because I'm not a normal user that what I'm saying has no bearing on your life, which is where you lose track of the truth.  The people who build an average distro choose an init system, and they extremely frequently do so for political or profit motive rather than for the benefit of the users.  Keep in mind that many distros now have a commercial interest.

The fundamental benefit of Open Source is peer review.  The same fundamental benefit of our current scientific methodology is also peer review.  A researcher/programmer can release anything they want, and they can say anything they want about it.  It's understandable that the people who wrote a piece of software are enthusiastic about it and can see many benefits over the other packages of the similar type.

Other researchers/programmers will inevitably look at what these guys did, and review it.  They'll either speak well of it or they'll speak ill of it.  Or both.  Still others who care but are either not technical enough to understand the principles involved or who don't have time to look directly will read the reviews, or the reviews of the reviews as it were (For example, published in Scientific American and then talked about in more mainstream magazines or even on TV news) and make their decisions based on those reviews.  That's how it works.

Some of you may not care about an init system, but when those who neither know nor care about the issues being discussed rant about things which are not really relevant to the topic it just dilutes the real issues and makes it harder for anyone else to follow.

> 
The Unix way, small tools to do each job separately. If you use a graphical file manager, you are not using the Unix way. 


I disagree here.  The Unix way is to have a tool do one thing really well, by some standard.  You can choose any tool you want.  You can use a graphical file manager, and I can just use the command line.  The fact that each tool only really does one thing makes it possible for the parts to be interchangeable.  If however you try to adopt something that is a file manager, but which requires that you use a specific window manager and a specific network setup then you lose flexibility because somebody is dictating your architecture in a way you may not like, and which prevents easy adoption of a new tool that might be a better choice later.

> 
Someone comedically tried to defend emacs as a modular system. On my distro of choice, emacs is a monolithic 34MB, before dependencies. Non-lightweight Gedit is 2MB, and, for comparison, Firefox 35MB)


That was me.  On Ubuntu Server 12.04, the command **apt-cache search emacs** yields 318 packages that have some reference to emacs.  If you want to trim it down a bit, you can **grep -i emacs** to weed out the packages which do not mention emacs in the name or description, and you get 185 packages.  Emacs is modular.  I'm not forcing you to install that or any other editor.  If Gedit is good enough for your needs then you can choose your own text editor as you see fit.  People who need a programming editor usually want more than Gedit.  Emacs and Vim are popular with developers because they're programming editors.  Programming editors have much more functionality than simple editors, therefore there are more lines of code.

To get this back on track a little bit, the very fact that text editors do essentially one thing makes it so your choice of editor impacts almost nothing else on your system.  If you chose something like Microsoft Word you'd have to install certain dependencies which you might not like, because of all its extras.

> 
[complexities] "which cause the system to be less reliable and less secure" - I hear this often from the anti-systemd crowd. Systemd is undoubtably complex, but seems to have created remarkably few major issues. Why not outline some of these reliability and security problems you have personally had with systemd?

Bug prediction algorithms, based on statistics of mature products and their bug history, indicate that there are usually something between 15 to 50 bugs per 1000 lines of code written.  By the time the product gets to production it's generally under 1 bug per 1000 lines, but it will never get to zero.  The more code you have, the more chances of bugs, and a really good argument can be made that even though you don't know of a bug you can count on its existence when your code base is large enough.  It's large enough even with a simple init system, and systemd is much larger than a typical init system.

Continuing along this thing, systemd dictates the tools you use for many things which are not related to an init system. If you want examples, go to the systemd documentation.  Once you start gluing unrelated packages onto the init system because not using that package causes the init process to be more difficult, you lose flexibility.

One well accepted measure of code quality is that you can take any single component of the code and write a test which exercises that code, and it will work correctly without a bunch of other bits glued in.  Likewise you can remove that bit of code and put it into its own app and it will work, although that's rarely done.  Systemd can't work without its own suite of tools which really have nothing to do with what an init system is supposed to do.

---

### Post by 1clue on 2014-10-22
> **buzzingrobot said:**
> Because I haven't been arguing for it, or against it.  

What I've said is that the entire debate is about something -- plumbing -- that should be invisible to users.  Systemd and all of its predecssors and alternatives are just means to an end:  Better applications for users. 

Admins and greybeards are seizing on this because they see themselves losing control of Linux.  As a user, I tend to think that it would be a good thing if they lost control of Linux.  If admins and greybeards determine the course of Linux, only admins and greybeards will use Linux.

As I've said, I'll judge the results by the products that are delivered to me.  Whether systemd is inside or not won't matter.

What I've said is that the visibility of the init system has absolutely nothing to do with the importance of the init system, or the choice of which one to use.  The topic of this discussion is the relative merits of systemd and other init systems, focusing on systemd.  You say init systems shouldn't be visible, so how does the visibility of any init system relate to whether systemd is better or worse than other init systems, and why does that make it better or worse?

I'm an admin, and pretty close to a greybeard.  I've never been in control of Linux and don't want to be.  The grab for power is being made by the Microsoft of Linux.  The largest commercial entity whose entire focus is Linux is doing things in a way that will cause a monolithic, kludgy hunk of software to be in control of any distro which adopts it.  You see me as being opposed to change just because I don't like a new init system, when its newness has nothing to do with it.  It's monolithic nature and hard dependencies on things which should not matter to an init system are what defines my dislike.

---

### Post by 1clue on 2014-10-22
> **buzzingrobot said:**
> I think the open source community is a community of developers. FOSS was created by developers to benefit developers.


Originally, yes that's exactly what it was.  As far as I'm concerned I care not even a little bit if it ever gets beyond that, since I'm a developer.  The world being what it is though, other entities choose to introduce it to the rest of the world.  More power to them.

> 
The list of arguments you offer re: systemd don't really address what I've said.


The list of arguments I offered re: systemd address the topic of the discussion, which is the relative merits of systemd vs upstart, which is another init system.  And the implications for Canonical and Debian.  I'm talking about other init systems but in a general way, which includes upstart.

The desired visibility of an init system has no bearing whatsoever on which init system is better, or on any implications for Canonical or Debian.  In any case, ANY init system can have a control panel like Windows has, and can have service setup happen when you install the service.  So the visibility is the same no matter whether you use systemd or upstart or openrc or whatever else you might want.

> 
To repeat, the debate about systemd is about something that should be invisible to users.


No, by your account the **init system** should be invisible to users.  This is an open forum, and systemd vs upstart is extremely important and pertinent with respect to the future of Ubuntu.  You can and do rail against the very concept of peer review of an 'invisible' piece of software, but the discussion of merit by people who understand it and care cannot be a bad thing.  If you want the discussion to be invisible, then ignore this thread and others like it, and your wish will be granted.

That's not an attempt to get you off the discussion, it's a statement of the only reasonable way to hide the discussion.

> 
 It's the job of developers to make good software for users. How they do that -- what's in the plumbing, or whether it's coded in C++ or Algol or tied together with bits of string -- doesn't matter to users so long as they like the product.


To a point.  If the developers give you a feature rich app full of bugs, it can cause your system to be unstable.  If they put out code with a security hole in it, it can cause all your credit card data to wind up in some third world country, or turn your box into a spam-bot.  If the software has these holes and is also big, kludgy and as fragile as such software often is, then the fix comes later rather than sooner.  All this DOES matter to the users, at least when it's their credit card that was stolen.

---

### Post by 1clue on 2014-10-22
Oh yeah.  And if the feature rich app with bugs and security holes is the thing which runs your system, then you're in some serious trouble.

And when the feature rich app with the bugs and holes has no compatible replacement, then you're pretty much SOL.

I don't argue against systemd because it does more things than other init systems, I argue because it is incompatible with many things that should not even be understood by an init system, and by adopting it you adopt something which has no replacement.  If it's broken, your whole computer is broken.

Code which is 'modular' but needs all its modules to run on a real system is not modular.  Systemd is like that.  Technically could run, but by the time you have a typical working system, you have almost all the modules.  This, to a developer, is a perfect description of unmaintainable code.  Which means it's broken code.

---

### Post by vellon on 2014-10-22
1clue, you write some real essays which obscure the real points. From what I can gather is that you are opposed to systemd in terms of politics and theory. What I want to hear about are your personal experiences of systemd problems. You are basing your comments on extensive experience of systemd, right?

---

### Post by mips on 2014-10-22
The horse has bolted...

I suspect there will be similar wailing and gnashing of teeth the day xorg is depreciated & wayland takes the reigns. This seems to happen with most major changes but eventually things carry on as normal and the old is forgotten.

---

### Post by bapoumba on 2014-10-22
*Welcome to the **Recurring Discussions**.*

---

### Post by vasa1 on 2014-10-23
I can't tell if the irony is intended or not: [Avoiding systemd isn't hard]("http://www.vitavonni.de/blog/201410/2014102101-avoiding-systemd.html") but as long as the trains run on time all is well.

---

### Post by /ADM on 2014-10-25
It is just an init system, whenever anything become un *nix all the usual paranoid people spring into action.  Systemd is great, advancing Linux is what is needed.  That includes getting rid of antique cruft.

---

### Post by buzzingrobot on 2014-10-25
> **/ADM said:**
> It is just an init system, whenever anything become un *nix all the usual paranoid people spring into action.  Systemd is great, advancing Linux is what is needed.  That includes getting rid of antique cruft.

The plan/goal/vision of SystemD encompasses a great deal more than the functionality of a traditional init.  One of the arguments its supporters make is that SystemD can help position Linux as a modern desktop platform, removing much of the iterative clutter that has accumulated in Unix/Linux over the decades that they feel restricts Linux.  Others disagree.

This debate really highlights two different concepts of what Linux should be:  Is it primarily a traditional Unix-like platform targeting server rooms, with desktop usage bolted on top?  Or, is it a mainstream application-running platform?  I don't see those two visions as mutually exclusive.  But, a tension has always existed within the Linux community pushing the platform to uniformity and consensus.

Mixed into this is what has become something of a theological mantra in some circles:  One tool for one job. (I'd argue that this notion was fostered by the weak hardware that existed when Unix was created,  which couldn't handle complex demanding applications. Hence, the concepts of piping, etc., came into use. If Unix/Linux actually adhered to that, it would be rather unusable:  NO GUI's, just thousands of single purpose command line tools.)

As a user, naturally I side with those whose goal is to make my life easier by creating better platforms and better software catering to my needs. If I earned my living as an admin, I would side with those who support my perceived interests as an admin. 

So, I'll judge systemd by the new capabilities distributions using it can bring to me.  Beyond that, I expect it, or any of its current or proposed alternatives, to work reliably, day in and day out, without drawing attention to themselves. Like a car's transmission: When it needs your attention, something's almost certainly gone wrong.

---

### Post by MartyBuntu on 2014-10-25
> **buzzingrobot said:**
> But, a tension has always existed within the Linux community...


The legitimate tension was/is in the **developer** community.

Most workstation users complaining about *"Get this EVIL systemd monstrosity off my computer!"* are simply arguing for the sake of blowing hot air out of their pie-holes.

---

### Post by buzzingrobot on 2014-10-25
> **MartyBuntu said:**
> The legitimate tension was/is in the **developer** community.

Most workstation users complaining about *"Get this EVIL systemd monstrosity off my computer!"* are simply arguing for the sake of blowing hot air out of their pie-holes.

Well, yes, because the developer community is, for all practical purposes, *the* community. At least, in the sense that it is developers (and designers) who decide what software gets built.  Whether or not FOSS developers have reasons to care that anyone ever uses their software is a much more hazy question than it is in the commercial sector, where the goal is to make money and the software is a means to that end.

Many developers have used specific, highly modified, interfaces for years. They have an established workflow that relies on things like specific windows being in specific places, and specific keystrokes moving to specific places, etc.  It's normal, and justifiable, to be disgruntled when your platform of choice moves to a different set of tools that cannot accommodate your very specific, very finely tuned, muscle-memory dependent way of working.

On the other hand, projecting your discontent upon all of Linux, decrying that the "new thing" will ruin Linux for all time, is not justified. Developers, admins, and other who have created their own reliance on very specific configurations represent a very small subset of the Linux user community.  As such, it isn't reasonable to expect interfaces, distributions, and other tools that are deliberately targeting the broad base of mainstream consumers to alter course to cater to their specific needs.

---

### Post by 1clue on 2014-10-26
@vellon,

The reason for the politics and theory is because I was addressing politics and theory.  I'm not so good at that.

I have decades of experience with other init systems, and a small amount of experience with systemd.  I've read the documentation and the pro-systemd arguments, tried it on an i7 and on a raspberry pi, and oddly enough the only one that sort-of benefitted was the raspberry pi.  It actually has a faster boot time on Arch than on Raspbian.  I don't get that.  The i7 booted significantly slower using CentOS than Gentoo or Ubuntu, both loaded to a best guess at equivalent software to CentOS, using the native init system in each OS.

@mips,

I was compiling and trying to use xorg when it was still alpha code.  I don't gnash my teeth at anything new, I try the new thing to see what merit it has, and acknowledge the good and point out the bad.  For that matter my home equipment mostly uses Gentoo, and one of the reasons is access to much more recent software than Ubuntu uses.  Another is that I get to configure things pretty much exactly the way I want.

@vasa1,

Avoiding systemd at the moment is easier than using it.  As yet Ubuntu doesn't use it, and neither does Gentoo in the default mode.  Those are the two main distros I use, although there are others.  Including CentOS which is systemd.

@/ADM,

If systemd were just an init system, then there would be so little discussion most of the people who now know about init systems would not know yet, because nobody mentions an init system.  Certainly I would not care one way or the other if it were just an init system.  The problem is it's much more than an init system, and it tries to dictate much that it has no valid reason to dictate.  From the sounds of the documentation on CentOS it seems that whatever part of the boot process and core function of Linux is left, is only left because they haven't gotten around to replacing it yet with their own system.

For example, it wants /usr to be on the / partition, which is completely nuts.  There are extremely good reasons to keep them separate, and one of them is ensuring a stable, safe boot in the event of a bad partition.

By tradition (which became tradition because it has good solid science behind it) the / partition contains just enough to boot the system into a usable state.  This partition contains information which rarely changes, meaning very few writes to this partition.  That translates to much longer statistical use before a data failure.

The /usr partition contains the lion's share of the software. It gets most of the software updates, you're continually adding or removing software, and it's much bigger than /.  All that means that statistically it's more likely to have a failure, even on the same device.  Keeping /usr on a separate partition has saved my systems dozens of times, because I can boot and perform maintenance.

Systemd has its parallel system initialization which is supposed to make things faster but in my experience doesn't on a processor I actually use in business.  This parallelism sounds great but in reality they can't figure out how to do the core things first (what is typically on / and not /usr) and wait for /usr to mount for the rest, so they merged the /usr partition into the / partition.  Their arguments for doing so don't hold water.

I have many other reasons to dislike systemd, based on real facts of how things work.  I'd rather not enumerate them all on this thread.

@buzzingrobot,
[quote="buzzingrobot"]
The plan/goal/vision of SystemD encompasses a great deal more than the functionality of a traditional init. One of the arguments its supporters make is that SystemD can help position Linux as a modern desktop platform, removing much of the iterative clutter that has accumulated in Unix/Linux over the decades that they feel restricts Linux. Others disagree.

This debate really highlights two different concepts of what Linux should be: Is it primarily a traditional Unix-like platform targeting server rooms, with desktop usage bolted on top? Or, is it a mainstream application-running platform? I don't see those two visions as mutually exclusive. But, a tension has always existed within the Linux community pushing the platform to uniformity and consensus.

Mixed into this is what has become something of a theological mantra in some circles: One tool for one job. (I'd argue that this notion was fostered by the weak hardware that existed when Unix was created, which couldn't handle complex demanding applications. Hence, the concepts of piping, etc., came into use. If Unix/Linux actually adhered to that, it would be rather unusable: NO GUI's, just thousands of single purpose command line tools.)

As a user, naturally I side with those whose goal is to make my life easier by creating better platforms and better software catering to my needs. If I earned my living as an admin, I would side with those who support my perceived interests as an admin.

So, I'll judge systemd by the new capabilities distributions using it can bring to me. Beyond that, I expect it, or any of its current or proposed alternatives, to work reliably, day in and day out, without drawing attention to themselves. Like a car's transmission: When it needs your attention, something's almost certainly gone wrong.
[/quote]

One tool for one job is my mantra.  That doesn't mean more than one tool for the same job can't exist on the system, but each use case can dictate which tool is most appropriate.  Linux to date still largely follows that mantra.  Components can be big or small as you want, the choice is yours.

Your assessment of weak hardware being the cause for this approach is false, as is your assumption that it can't support complex demanding applications.  The tool can be command line or gui.  Your web browser can be wget or it can be firefox, your text editor can be ed or it can be Libre Office, or anywhere in the middle.  The thing that makes this approach strong is that you can interconnect tools in ways not imagined by the architects of the tool.

Go look at top500.org.  There are 15 systems on the top 500 which are not Linux. Some of them have millions of cores.  Extremely few of those systems use systemd.  Who would pay that much money for a system that doesn't make a profit?  Who would pay that much money and put a free operating system on it when a paid operating system would be more effective and productive?  The 'do one thing well' approach is used throughout the UN*X-oriented computing industry, and it is used because it works extremely well.

If systemd actually has a benefit it would be for a desktop system.  In my opinion it has shown no actual benefits in real practice, and because of its focus on desktop benefit when I evaluated it it was on a fully loaded desktop install, compared to another fully loaded desktop install.  It's not the only multithreaded init system, and none of the other init systems is nearly as intrusive on the makeup and layout of the operating system.

@MartyBuntu,

Yes, the **legitimate** tension was/is in the developer community, and in professional system administrators of many systems.  Nobody else would have much of an idea what was going on, or why systemd's approach would be a problem.

@buzzingrobot (again),
> 
Well, yes, because the developer community is, for all practical purposes, *the* community. At least, in the sense that it is developers (and designers) who decide what software gets built. Whether or not FOSS developers have reasons to care that anyone ever uses their software is a much more hazy question than it is in the commercial sector, where the goal is to make money and the software is a means to that end.


You are extremely wrong here.  The reason the FOSS developers even wrote the free software is because they personally have a financial stake in that sort of application for their income, and the commercial options suck.  Apache web server didn't come out of thin air for no reason.  **The reason they made it is because the developers ARE the users.**

There's a huge difference between software which is designed by marketing people who think the feature will make them more money *because people will use that feature as a purchasing point*, and software which is designed by people who want to use the product for their own ends.

There's a huge reason why apache web server is the most used web server on the planet and has more than half of all web server installations.  Those installations are there to make money, and if a commercially produced web server had any advantage those sites would be using that commercially produced server without a second thought.

Good Open Source software rocks.  It is built by professionals who actually want to use the product, who know about the end application in a detail that a non-user can't possibly imagine.  Apache is one of countless examples.

> 
Many developers have used specific, highly modified, interfaces for years. They have an established workflow that relies on things like specific windows being in specific places, and specific keystrokes moving to specific places, etc. It's normal, and justifiable, to be disgruntled when your platform of choice moves to a different set of tools that cannot accommodate your very specific, very finely tuned, muscle-memory dependent way of working.


True to a point, but after you've been in it for awhile you realize software is constantly changing, especially software used for development.  Change is the only constant.  It's our job as developers to alert people who don't know to bad code.

> 
On the other hand, projecting your discontent upon all of Linux, decrying that the "new thing" will ruin Linux for all time, is not justified. Developers, admins, and other who have created their own reliance on very specific configurations represent a very small subset of the Linux user community. As such, it isn't reasonable to expect interfaces, distributions, and other tools that are deliberately targeting the broad base of mainstream consumers to alter course to cater to their specific needs.


I've said this before on this thread:  Linux is in constant change.  Tools/services/apps come and go, and while some of us (me included) have complained loudly about tools that suck when they come out, I've often been using that very tool two years later.  I don't discount the possibility in the case of systemd, but the caveat is that the developers of those other tools listened and caused their tool to not suck.  There are options out there which don't suck.  Any tool which has good features and very bad features will have those good features adopted into some other tool which does not have the bad features.

Finally:

My main interest in Linux is servers, and almost none of my servers have a gui.  There is no reason for them to, all it does is waste resources.  Some of them use a web front-end like webmin, but most don't even bother with that.  In my world, a disk failure is not a possible future calamity, it's a certainty with predictable regularity, even if I can't say which drive on which system will fail next.  I keep my own statistics on drive failure by brand and type.

I suspect that most of the posters on this thread do not live in my world.  That's OK.  I don't tell anyone to not use systemd or any other piece of software.  I use lots of software either for personal use or for my work, from pretty much any platform you want to name including multiple commercial UNIXes and Mac OS and Windows, Android, whatever.  Come to think of it I don't use any iOS devices.

I'll say it again:  If systemd were JUST an init system I would have no objections to it.  The fact that it's not just an init system and that the differences cause it to put your system into a less reliable state cause me to post to threads like this one.

---

### Post by buzzingrobot on 2014-10-26
> **1clue said:**
> 
> One tool for one job is my mantra.

Unix was my first OS, and I've used Linux since 1995.  I just don't think that has much relevance today.  Users -- who I explicitly define as people who buy computing devices to run applications -- do not conceive of computing in that fashion. They do not think in terms of linking the output of one application with the input of another program. They are not concerned with the perceived beauty or simplicity of symmetry of the underlying OS. In other words, no one wants to do vi | roff | lpr when they need to write a memo for work.
 
[quote]Your assessment of weak hardware being the cause for this approach is false

The hardware on which Unix was developed was very weak by today's standards, and in addition could not support GUI interfaces. That's why it was character-based, and memory and storage limitations were determining factors in the design of many of the small applications developed then, which are now traditional parts of the Unix/Linux toolset.

> f systemd actually has a benefit it would be for a desktop system.  

That's the only environment that interests me.  I'm a user. I use a desktop, a laptop, a  tablet, and a phone. I do not develop, administer servers, etc. (I did some of that once upon a time, then came up with a better way to live.)  My interest in developers is exclusively limited to the software they create for me to use.

I don't know and I don't care if systemd is good, bad, or indifferent.  That's not an issue that interests me.  As I have said here repeatedly, whatever systemd, or any other piece of plumbing does, should be hidden from me, a user.  If sysytemd delivers new capabilities that can be exposed to me via new applications, though, and if I find those applications attractive, then I will have reasons to migrate to distributions that allow me to run those applications. If systemd doesn't do that, I won't.

>  **The reason they made it is because the developers ARE the users.**

I'm a user and I don't run Apache. If someone runs Apache, they are, in that capacity. admins, not users.

Of course, developers use software.  But, their needs, their expertise, and their outlooks are different from the typical mainstream consumer. In this regard, developers represent an edge case. It's inappropriate to project developer conceptions of useful software onto the broad real-world base of mainstream consumers.  Better to consult the developers' moms.

Focusing on what developers and admins do, and what developers and admins want,  as well as the needs of the organizations that employ them, has given us things like Debian and RHEL:  Solid, reliable, invisible in the mainstream consumer marketplace.  

If someone's vision of Linux is that it needs to remain faithful to its Unix heritage above all, and that it is primarily a platform for developers and admins and their employers, then it's only logical that they will be concerned about changes to its internal core.

If someone's vision of Linux is that it can, and should, be a platform whose Unix heritage provides an excellent base on which to build systems and applications for the computing devices that are used, and will be used, today and tomorrow, by billions of mainstream consumers, then it is logical that they will be most interested in the applications and capabilities created for users.

I'm in the latter camp.

---

### Post by 1clue on 2014-10-26
> **buzzingrobot said:**
> 
Unix was my first OS, and I've used Linux since 1995.  I just don't think that has much relevance today.  Users -- who I explicitly define as people who buy computing devices to run applications -- do not conceive of computing in that fashion. They do not think in terms of linking the output of one application with the input of another program. They are not concerned with the perceived beauty or simplicity of symmetry of the underlying OS. In other words, no one wants to do vi | roff | lpr when they need to write a memo for work.
 

The end user doesn't have to know that many tools were chained together to get their gui.  You think each control panel widget is a single thing written from scratch?  X is a bunch of little tools, each thing doing its own job.  This includes xorg and pretty much everything currently planned to replace it.  There are toolkits for gui apps, just as there are for command-line apps, so that a developer (or even a curious beginner) can focus on the task at hand rather than reinventing the wheel.

You're thinking of command line pipes, which is an example of one tool for the job but certainly not the only example.  Most of those commands has an API which can be called from C or from any other language, without shelling out to the command line and without other command-line awkwardness.  Linux and UNIX are *modern* operating systems in every sense of the word, with or without systemd.  The API someone uses may be a shared library, a static library or a service, but really it doesn't matter on the outside.

> 
The hardware on which Unix was developed was very weak by today's standards, and in addition could not support GUI interfaces. That's why it was character-based, and memory and storage limitations were determining factors in the design of many of the small applications developed then, which are now traditional parts of the Unix/Linux toolset.


So?  The hardware on which UNIX was developed was very powerful by the day's standards.  You think it's stayed the same as it was all this time?  The tools developed then which are still there are there because they're still useful.  They have been updated again and again in order to handle larger amounts of data and interface with other modern apps.  You don't have to use those tools if you don't want to, but many of your GUI tools that you think of as the new way of doing this use those tools under the covers.  The introduction of systemd will in no way affect their existence.

> 
That's the only environment that interests me.  I'm a user. I use a desktop, a laptop, a  tablet, and a phone. I do not develop, administer servers, etc. (I did some of that once upon a time, then came up with a better way to live.)  My interest in developers is exclusively limited to the software they create for me to use.


Do you care that the web site you visit works correctly?  Do you care that the web site you just gave your credit card to is secure?

> 
I don't know and I don't care if systemd is good, bad, or indifferent.  That's not an issue that interests me.  As I have said here repeatedly, whatever systemd, or any other piece of plumbing does, should be hidden from me, a user.  If sysytemd delivers new capabilities that can be exposed to me via new applications, though, and if I find those applications attractive, then I will have reasons to migrate to distributions that allow me to run those applications. If systemd doesn't do that, I won't.


I have never once implied that the init system should be visible to users.  I'm saying that announcing bad design on a public forum is important, in the same way that while you probably don't care about the inner workings of your car, you probably would want to know if your car has brakes that are inclined to fail due to bad design.  Or an air bag that goes off for no reason, with too much force and is likely to kill women or children when it does so.

I've also said that simply owning a device means you either must perform some administrative tasks or you must accept that your device will be substandard for you sooner than it would if you didn't perform those tasks.

> 
I'm a user and I don't run Apache. If someone runs Apache, they are, in that capacity. admins, not users.


Do you use Firefox, or any other web browser on any platform?  If so, then you also use apache unless you use your web browser in a closed corporate environment with no access to the outside, and can guarantee that Apache does not exist on that network.  Nonetheless, Firefox is a single tool for a single purpose and applies as much as apache to this discussion.

> 
Of course, developers use software.  But, their needs, their expertise, and their outlooks are different from the typical mainstream consumer. In this regard, developers represent an edge case. It's inappropriate to project developer conceptions of useful software onto the broad real-world base of mainstream consumers.  Better to consult the developers' moms.


Who is projecting anything on users?  Why do you care if a bunch of developers talk about init systems on an open forum which is for anyone who uses an Ubuntu-based Linux (including admins and developers)?  Most users will either read the posts and maybe ask a few questions, or find out it's about 'boring invisible stuff' and stop reading.

> 
Focusing on what developers and admins do, and what developers and admins want,  as well as the needs of the organizations that employ them, has given us things like Debian and RHEL:  Solid, reliable, invisible in the mainstream consumer marketplace.  

If someone's vision of Linux is that it needs to remain faithful to its Unix heritage above all, and that it is primarily a platform for developers and admins and their employers, then it's only logical that they will be concerned about changes to its internal core.

If someone's vision of Linux is that it can, and should, be a platform whose Unix heritage provides an excellent base on which to build systems and applications for the computing devices that are used, and will be used, today and tomorrow, by billions of mainstream consumers, then it is logical that they will be most interested in the applications and capabilities created for users.

I'm in the latter camp.

If you're in the latter camp, why are you so verbosely talking on a thread which is clearly aimed at something you want to be invisible to you?  This thread is for people who care about init systems.  This forum is for not only users but also for developers and system admins, and this topic is pretty much only interesting to what you would refer to as an admin.  Nobody is forcing you to take part, and your continually pointing out the same unrelated things over and over causes the discussion to stray.

The things you keep saying you hate about UN*X will not change because of the presence or absence of systemd.  As far as I can tell, systemd will not significantly make improvements even to desktop users.  All it is is bloatware in a place where bloatware can be especially harmful.

The only reason Ubuntu came into existence is because of a bunch of programmers who decided the mainstream commercial operating systems left something to be desired, and they made something else.  That something was built by developers, for developers. Later the folks who built the commercial operating systems decided that their market-driven design had caused them to be too rich on visible features and their internal workings sucked.  Apple switched to UNIX on the underside, using both a commercial license and adopting much from Open Source.  Microsoft pretty much copied their networking stack from BSD, and revamped just about everything else.  RedHat and Suse started making Linux work for Enterprise, and Canonical started developing a distribution aimed more at home users.

If you don't want developers and admins to talk about things that matter to developers and admins, then how do you expect us to produce software for you, or build cool web sites or do any of the thousands of other things that enable you to be a happy user who can remain ignorant of everything he can't see?

---

### Post by JKyleOKC on 2014-10-26
> **1clue said:**
> The hardware on which UNIX was developed was very powerful by the day's standards.Perhaps it's time to inject a bit of history into the discussion. I don't know exactly which hardware you meant by the quoted statement, but the original development was a skunk-works project done on an unused mini. However, the people doing the work **had** just come from what was at the time the world's most powerful system -- Project MAC at MIT, the ancestor of just about everything we do in the computing industry today. And the hardware involved at that time was far less capable than today's smart phones and tablets.

While I wasn't part of Project MAC, I was a most interested spectator, as a tech writer at General Electric generating the service manuals for the world's very first video terminal. I became interested in teaching the computers to do my job for me, and consequently tried to keep up with all developments in the industry. I was totally flabbergasted at just how primitive things still were in 1967! Punched cards were still the primary i/o method. Remote access was still in its infancy. And it had just become obvious that Project MAC (variously translated as Man And Computer or as Machine Aided Cognition) was a huge money pit and getting nowhere fast, because it was more ambitious than the hardware of the day could support.

That was reported to be the reason why Bell Telephone Labs pulled out, and recalled Dennis Ritchie and Ken Thompson back to Cherry Hill. There, they initiated their project to create a single-user version of Project MAC -- and came up with Unix. By dealing with just one user at a time, it bypassed many of its ancestor's problems, and the "do one thing and do it well" philosophy evolved because it vastly multiplied the power of the tiny machine on which it initially ran.

I have no dog in this fight; so long as the init process does its job properly and reliably, it's no problem for me as a user no longer concerned with operating system internals. However any engineer worthy of the name should be fully aware that the more complicated a structure becomes, the more points of possible failure it must contain -- and Murphy's Demon will guarantee that each such point of **possible** failure will eventually exert its possibility. And that reduces its reliability.

That, in itself, seems adequate justification for the "do one thing well" approach. Even with such a mantra, the complexity of our current structure seems to be well past the optimum level!

---

### Post by buzzingrobot on 2014-10-26
> **1clue said:**
>   You think each control panel widget is a single thing written from scratch?

No, I don't.  I've written software and managed developers.

  
> You're thinking of command line pipes...

...where the notion of "one tool, one job" orginated and where it has traditionally been applied. 



> The hardware on which UNIX was developed was very powerful by the day's standards.  

You don't substantiate that claim.  

In any case, the assertion isn't germaine to my position on SystemD, which I've expressed over and over. Please take the time to note that I am not at all concerned about the technical merits or perceived simplicity or lack thereof, of SystemD. Or whether developers and admins like it, hate it, are indifferent to it, or have to learn something new to cope with it. 

 My only interest in it is whether or not it delivers new capabilities that application writers can expose in new applications for users like me to use. (Something I haven't seen discussed in this thread or any where else where this sad argument flares. It all seems to be about devs and admins not wanting to complicate their lives. The entire debate seems focused on the interests and prejudices of devs and admins, not what is good for users.) Otherwise, I can't foresee any circumstances in which an ordinary user like myself would choose a Linux distribution based solely on the presence, or non-presence, of SystemD in that distribution.

The near-hysterical hissy fit raging in the developer and admin community about SystemD is, among other unfortunate things, about developer and admin interests and biases that users do not share. Users, frankly, simply do not care how hard devs and admins have to work, or how happy they are about the software they have to use, to do their job, which is to make software and keep systems running for users.  

The SystemD advocates, at least, say they want to make Linux a better platform for ordinary users.  Maybe it will, maybe it won't.  But, I don't hear the opposition saying the same thing. 


> I've also said that simply owning a device means you either must perform some administrative tasks or you must accept that your device will be substandard for you sooner than it would if you didn't perform those tasks.


The only admin'ing I do on my phone and tablet is to install and remove apps. *That's* what users expect from any computing device.  The need to fuss with settings, etc., is seen as a sign of poor design and inadequate software. Contrary to what a lot of Linux people seem to think, mainstream users do not want to face a system with near-infinite configuration options.  They want it to work like they expect it to work as soon as they turn it on for the first time. If it doesn't, they'll go find something else.


> Do you use Firefox, or any other web browser on any platform?  If so, then you also use apache...

So long as the server manages to serve files to me, I don't care, and do not need to know, and, in fact, do not know, what software is running on that server.  Could be apacahe, could be nginx, could be IIS. That's parallel to my position on SystemD.  It's the job of the people paid to run the site to make sure it works so I don't have to be bothered with thinking about it.  Ditto the people who write system-level Linux code: It's their job to make sure it works so people like me can avoid knowing it's there.

---

### Post by 1clue on 2014-10-26
@JKyleOKC,

My comments about the systems that UNIX was developed on was not referring to the very first UNIX box.  It was referring to the size of the boxes UNIX lived on for the first few decades of its life.  It's only relatively recently that a regular person could afford hardware that would run UNIX or anything UNIX-like.

> **buzzingrobot said:**
> 
...where the notion of "one tool, one job" orginated and where it has traditionally been applied. 


But not the only place it applies.  Have you ever tried to use a spork?  Is it better than a spoon, a fork and a knife?  Have you used a swiss army knife?  Is it better than a knife, a screwdriver, another screwdriver, a toothpick and a pair of tweezers, and one of whatever else is included?

One tool one job applies to far more than just computers.  It's considered best practices in virtually every endeavor humans undertake.  Multiple tools combined force the user to accept everything in the entire package, rather than just choosing a screwdriver and a wrench, if they only need the screwdriver and the wrench.  One tool one job enables the designer to build the best tool for the job, rather than obsessing about all the other tools that might be interesting for that same user.  Notice that I say "user" and not "developer" or "admin".  A spork was designed for a user, not for a developer or admin.  And they suck.

In computing, this concept need not be visible to users, but it's nice when it is visible.

> 
In any case, the assertion isn't germaine to my position on SystemD, which I've expressed over and over. Please take the time to note that I am not at all concerned about the technical merits or perceived simplicity or lack thereof, of SystemD. Or whether developers and admins like it, hate it, are indifferent to it, or have to learn something new to cope with it. 


And as I've pointed out over and over, this discussion is *about* the technical merits of systemd vs upstart.  You may feel free to start your own thread, which I may take part in and contribute to, rather than just redirecting you to the actual topic.  You are off topic and have been for almost every post you've made in this thread.

Surely as a developer and as a manager of developers, you've been frustrated when you go into a meeting (particularly, paying everyone in the meeting) about technical aspects of a project and somebody keeps inserting dialogue which is out of scope?

---

### Post by vasa1 on 2014-10-26
> **1clue said:**
> ...
Who is projecting anything on users?  Why do you care if a bunch of developers talk about init systems on an open forum which is for anyone who uses an Ubuntu-based Linux (including admins and developers)?  Most users will either read the posts and maybe ask a few questions, or find out it's about 'boring invisible stuff' and stop reading.
...
This. If someone doesn't want to know about something that's fine. I don't see what is wrong in posting about perceived pros and cons of something. I don't see intemperate language being used.

For those who ask "have you actually used it?", I don't really see experience in something being a prerequisite to learning about that something. I can decide not to eat veal or pâté de foie gras just by reading about it.

---

### Post by 1clue on 2014-10-27
> **vasa1 said:**
> This. If someone doesn't want to know about something that's fine. I don't see what is wrong in posting about perceived pros and cons of something. I don't see intemperate language being used.

For those who ask "have you actually used it?", I don't really see experience in something being a prerequisite to learning about that something. I can decide not to eat veal or pâté de foie gras just by reading about it.

+1 for all that.

Regarding experience with systemd, one can form an opinion without even using it if one knows about init systems and their purpose.  Just as an architect can probably tell if a building is sound by looking at it or its design, without even crunching the numbers, or a mechanical engineer can look at bad design and know something is wrong without crunching numbers or testing it to failure.  I'm sure each of you in your field of professional expertise can glance at something and say it's not good, and be generally right.  You'll want to back that up with some sort of closer examination and proof, but you can be right in your initial assessment.

Real knowledge only comes from experience, and while I've used systemd I can't say I have exhaustive first-hand experience.  What I have is decades of programming experience, and college education in doing so, and many refresher courses to keep current.  I have dived into the Linux boot process using several other init systems, including sysvinit, openrc and upstart.  I also did this a long time back, not sure if it was a different implementation of sysvinit or if it was something brewed by the distro, and since it was one of the first times I tried it I didn't really understand what an init system was.

Here's what I know, and it's abstract truths about programming rather than aimed at init systems:
[LIST=1]
[*]If code can't be broken down into simple parts, it is almost always:
[LIST=1]
[*]Fragile (changing one little thing can break the whole component)
[*]Unmaintainable (In order to change one thing, you need to have some familiarity with the whole part, which can be big and overwhelming)
[*]Costly to maintain.
[*]Prone to inexplicable bugs that, when fixed, cause other bugs.
[*]Bad overall design.
[/LIST]

[*]If code can't be tested outside of the production environment then it's almost always bad code.
[LIST=1]
[*]This applies to automated unit testing and automated integration testing.  Human testing requires a complete component wrapped in an app, so it doesn't really apply.
[*]Unit testing is taking a component or method or function and feeding values to it on its own, and getting a result back just for that method or function.  The method can be a 'leaf' in the sense that it does not call anything else, or it can call many other functions, as long as it is not hooked into the rest of the application in order to work.
[*]Integration testing is testing a function or component while it is integrated into the end product.  An example of this is to run the entire app, programmatically hit a button and check for the results for validity.  This test method can also take shortcuts to test only a single part, as long as the part is wired into the entire running product.
[/LIST]

[*]If code is modularized but can't work without a large number of other specific but supposedly independent modules in real practice, then it's the same as monolithic.
[*]If code adds a lot of complexity but gains little benefit, it's bad code.
[*]You should be able to scrap a whole module and rewrite it in a different way -- or plug in some third-party module with the same purpose -- and make your other code still work with minimal changes.
[/LIST]

Speaking from personal experience I've built some of those monolithic apps, and then been at the same company long enough to replace some of them with more modular, testable, easily maintainable versions in a fraction of the time it took to build the monolithic ones.  One tool, one job, reusable code, easy maintainability, a little bit of glue to make it into a nice app.

The easy to maintain, lightweight components have a shorter development cycle.  That means when the customer asks for a feature, we can give it to them in a fraction of the time it took for a similar feature on the old monolithic app.  That translates directly into lower cost and happier customers.  Meaning, in my case, the people who sit on the computer and USE my apps are happier and more productive, for less money and time spent.  The requested feature arrives before their work flow changes and makes the feature irrelevant.

Here's how all that pertains to this discussion:
[LIST=1]
[*]Systemd is alone in the group of init systems in that:
[LIST=1]
[*]It requires a lot of specific components that control things which do not matter to any other init system.
[LIST=1]
[*]You (or the distro maintainers) lose the flexibility of choice in those components, which means the distro may be required to deviate from their charter.
[*]You (the user) are required to use some of those components, which may be inferior to other components for your purposes.
[*]The requirement of specific components indicates bad code, see my list above.
[*]The requirement is simply there because the developers wanted a one-size-fits-all elegant-on-paper solution with parallel startup.  Which requires that all or at least most software started at boot time is on the root partition.
[/LIST]

[*]It requires you to place exponentially more code on the root partition than any other init system.
[LIST=1]
[*]This dramatically increases the chance that the root partition has an error on it, which means the system becomes unbootable.
[*]EVERY other init system I've heard of allows the system to come to a somewhat usable state similar to safe mode in Windows, where the system can be repaired or data extracted from a failing partition.
[*]This disk failure I'm talking about isn't abstract.  I ran into it a lot before I started using Linux professionally, and when you manage a lot of boxes you get this error in the /usr partition or massively written data partitions with a certain degree of regularity.
[/LIST]

[*]The 'exponentially more code' in item 2 causes the root partition to be written much more often because the code is frequently updated.  The root partition in any other init system generally only requires code needed for boot and repair, and settings for booting.  Which means it's very seldom written, and which in turn means the chance of surface failure is much smaller.  This is pure statistics on mechanical objects.
[/LIST]
[/LIST]

---

### Post by vellon on 2014-10-27
The art of precis is long-dead, clearly...

The systemd argument seems to wind a lot of people up. The trouble is, it is like 'discussing' politics and religion. Any participants already have their conclusion and no evidence is going to change that (despite all the participants' claims to the contrary).

I'm with buzzingrobot. I don't care. I use a distro with systemd. It works well.

As far as the Debian greybeards are concerned, let's wait and see. I would prefer it if they just got on with it, though, rather than just talking about it.

Edit: to clarify, I am not particularly pro-systemd, just not rabidly anti-systemd.

---

### Post by Lars Noodén on 2014-10-27
@vellon:  yet you joined this discussion.  The problems with systemd have been a long time coming and tinkers, powerusers, sysadmins, devops and developers have had a long time to look at the data and make a decision.  It happened neither quickly nor in a vacuum.  If you would contribute something, perhaps you can contribute Red Hat's official reasoning for systemd.  They are letting Poettering be the face for it and take all the flak.  We know his position, what is Red Hat's?  Why does Red Hat push systemd?

---

### Post by vellon on 2014-10-27
> **Lars Noodén said:**
> @vellon:  yet you joined this discussion.

I did and now I've left it.

---

### Post by buzzingrobot on 2014-10-27
> **1clue said:**
> @JKyleOKC,

  > It's only relatively recently that a regular person could afford hardware that would run UNIX or anything UNIX-like.

True when Unix ran on minicomputers, like Dec's. Later, the barrier to entry was less the hardware cost than the license fees. I ran 386BSD on a 386 box in the early nineties.  At some point back then, AT&T marketed their own brand of PC's that ran Unix.  The effort failed because, among other reasones, Unix, in and of itself, isn't very marketable to mainstream users.

[quote]this discussion is *about* the technical merits of systemd vs upstart.


Says who?

Here's why my comments are relevant: 

The opponents of SystemD seem to think that their assessment of technical merit should drive the acceptance or rejection of SystemD, and, by extension, any system-level component in Linux. That's in keeping with a specific vision of Linux as a true-blue traditional Unix-like platform that should be kept that way.

I think that's the view that has dominated much of Linux for two decades. It's also kept Linux locked into its position as a niche desktop product. Advocates of tradition Unix/Linux have essentially been arguing that Linux should remain the same and that increased acceptance should come from evangelizing the virtues of traditional Linux (and FOSS) among mainstream desktop users.  I think the evidence clearly shows that has failed.

So, I'm quite willing to sacrifice some traditional, or Unix-y, features in Linux if that effort delivers more capabilities exposed to users via new kinds of applications. For users, it's only those capabilities, those new tools, that matter. What's two or three layers deep that makes that possible doesn't interest them, nor should we expect it to.

That's why the argument about SystemD is an argument about something that should be invisible to users.

SystemD, then, could turn out be a brilliant piece of technical work, or a sorry kludge.  But, if the former didn't deliver new userland capabilities and the latter did, I'd go with the latter.

Linux has always been developer-led. Now, the SystemD debate is developer-led.  I want Linux to be customer-led.

---

### Post by 1clue on 2014-10-27
> **buzzingrobot said:**
> 
True when Unix ran on minicomputers, like Dec's. Later, the barrier to entry was less the hardware cost than the license fees. I ran 386BSD on a 386 box in the early nineties.  At some point back then, AT&T marketed their own brand of PC's that ran Unix.  The effort failed because, among other reasones, Unix, in and of itself, isn't very marketable to mainstream users.


That's a valid point as well.  But nonetheless UNIX gained acceptance as it did using hardware that was beyond the reach of a consumer and beyond most small businesses too.

Which extends back to my point that today UN*X is extremely more user-friendly, and widely accepted by people who don't even know it's UN*X.  Mac OS X, iOS and Android being primary examples.  40 years ago UNIX wasn't common knowledge among consumers.

> 
Says who?


The original poster, vasa1, from the tone of the first post.  Maybe I'm wrong?

> 
Here's why my comments are relevant: 

The opponents of SystemD seem to think that their assessment of technical merit should drive the acceptance or rejection of SystemD, and, by extension, any system-level component in Linux. That's in keeping with a specific vision of Linux as a true-blue traditional Unix-like platform that should be kept that way.


I do feel that way, and the reason is that if the mechanics of the system is crap then it's not worth putting any more effort into it until such time as they fix the problems inherent in the design.  This is common sense.

Would you get into an airplane if it looked shiny and comfortable, but knowing it was 10 times more likely to crash than an uglier plane?  The developers and admins who oppose systemd are doing so on a technical level because if there are technical problems that cause it to be bad in some way, it's just not worth using.  The end.

Apple and Microsoft went for years with crap back-ends and flashy user interfaces, because it sold more computers.  Finally Apple gave up and put UNIX underneath because their actual operating system sucked and everyone knew it.  Mainstream TV was making jokes about how slow and unstable System 7 was, and it was funny because people knew what they were talking about.

Microsoft underwent vast changes too out of necessity, but they didn't completely cut the cord with their older stuff, which is IMO why they still have so many problems with viruses.

> 
I think that's the view that has dominated much of Linux for two decades. It's also kept Linux locked into its position as a niche desktop product. Advocates of tradition Unix/Linux have essentially been arguing that Linux should remain the same and that increased acceptance should come from evangelizing the virtues of traditional Linux (and FOSS) among mainstream desktop users.  I think the evidence clearly shows that has failed.


There's plenty of talk about user interface, and I'm involved in some of it.  If the foundation of the operating system is stable and reliable, you can do pretty much anything you want on top.  Repeat:  A nice easily usable interface can be done just fine with a more typical init system just as it can with systemd.  The reason for systemd's unwieldiness is Lennart [COLOR=#000000]Poettering wanted a nice conceptually neat approach toward an init system, and in doing so broke a lot of other things that were there for very good reasons.
[/COLOR]
For the record, Lennart Poettering is also responsible for pulseaudio, which has been confusing new users for years.  When all anyone wanted was a volume control and sound card selector, maybe a mixer and balance control -- and have it work out of the box -- he gave us countless panels and widgets that we (users) need to tinker with just to make sound come out of your computer.  Thankfully you don't need pulseaudio in most cases, and your audio is much easier to manage without it.

> 
So, I'm quite willing to sacrifice some traditional, or Unix-y, features in Linux if that effort delivers more capabilities exposed to users via new kinds of applications. For users, it's only those capabilities, those new tools, that matter. What's two or three layers deep that makes that possible doesn't interest them, nor should we expect it to.


The reason Linux looks the way it does is because the people focusing on the GUI are Linux nerds.  It has absolutely nothing to do with what's underneath.  I don't use Linux because it's free to use.  I use it because I don't have to install anything on it that I don't want to be there.  That includes a GUI.

Generally speaking more layers is not a good thing, unless they either simplify operation or compartmentalize something conceptually in a way that makes sense.  The layering systemd does, in my opinion, does nothing beneficial.

> 
That's why the argument about SystemD is an argument about something that should be invisible to users.


Nobody has disagreed with your opinion that init systems should be invisible to users.  Why do you keep bringing it up?

> 
SystemD, then, could turn out be a brilliant piece of technical work, or a sorry kludge.  But, if the former didn't deliver new userland capabilities and the latter did, I'd go with the latter.

Linux has always been developer-led. Now, the SystemD debate is developer-led.  I want Linux to be customer-led.

Go buy a Mac.  It's much the same, different kernel but it's Open Source and you can install Darwin on your PC.  Same Open Source software on top, kernel made mostly by Apple.  You don't get Apple's gui though if you don't have the mac.  But it's market-driven the way you want it.

There are lots of consumer-driven operating systems out there.  You can scream about it all you want, but Linux is Open Source, and Open Source is led by developers.  Given the nature of the way Open Source licensing works, it's not even theoretically possible for it to become consumer-led.

---

### Post by Dog's_Breakfast on 2014-10-28
Hi, I'm new here on this forum, but I've been following the systemd debate for quite a while.

I'll state upfront - I'm opposed to systemd. However, I didn't come to that conclusion overnight. Indeed, it's take me quite a while to reach that conclusion, and it's only in the past two months that I finally decided. So here's why...

One reason, really: security. Yeah, I know the systemd developers will all insist that it's rock-solid secure. They write bug-free code. After all, they say so, thus it must be true.

Not. Nobody can claim to write bug-free code. The recent unpleasantness with the Heartbleed and Shellshock bugs should make it clear that even software that has been around for quite a while and thoroughly audited still occasionally harbors undiscovered bugs. And this is especially true for software written in C, which is the language that most init systems are written in.

It can take many years to flush out all the security holes in software. The task is made easier if the software in question is small in size, and well commented. But systemd is huge, and it keeps growing all the time as the developers keep adding new features and dependencies. Systemd presents what's known to programmers as a "large attack surface."

So just how huge is systemd? I found a web site that offers comparison of Linux programs - [www.openhub.net](www.openhub.net) - and here is what they report for four popular Linux init systems, sysvinit, upstart, openrc and systemd. Please read the following, and take a moment to digest it...


=================

In a Nutshell, sysvinit...

...
has had 120 commits made by 2 contributors 
representing 8,054 lines of code
...
is mostly written in C 
with an average number of source code comments
...
has a codebase with a long source history 
maintained by by one developer 
with increasing Y-O-Y commits

took an estimated 2 years of effort (COCOMO model) 
starting with its first commit in September, 2009 
ending with its most recent commit 8 months ago

Reference:
[https://www.openhub.net/p/sysvinit](https://www.openhub.net/p/sysvinit)

==================

In a Nutshell, Upstart...

...
has had 2,523 commits made by 23 contributors 
representing 75,680 lines of code
...
is mostly written in C 
with an average number of source code comments
...
has a well established, mature codebase 
maintained by a large development team 
with decreasing Y-O-Y commits

took an estimated 19 years of effort (COCOMO model) 
starting with its first commit in May, 2006 
ending with its most recent commit about 1 month ago

Reference: [https://www.openhub.net/p/upstart](https://www.openhub.net/p/upstart)

=================

In a Nutshell, OpenRC...

...
has had 2,495 commits made by 81 contributors 
representing 13,016 lines of code
...
is mostly written in C 
with an average number of source code comments
...
has a well established, mature codebase 
maintained by a large development team 
with decreasing Y-O-Y commits
...
took an estimated 3 years of effort (COCOMO model) 
starting with its first commit in April, 2007 
ending with its most recent commit 6 days ago

Reference: [https://www.openhub.net/p/openrc](https://www.openhub.net/p/openrc)

==================

In a Nutshell, systemd...

...
has had 17,498 commits made by 578 contributors 
representing 277,929 lines of code
...
is mostly written in C 
with a low number of source code comments
...
has a codebase with a long source history 
maintained by a very large development team 
with increasing Y-O-Y commits
...
took an estimated 72 years of effort (COCOMO model) 
starting with its first commit in November, 2009 
ending with its most recent commit 4 days ago

Reference: [https://www.openhub.net/p/systemd](https://www.openhub.net/p/systemd)

====================

I probably need not point out the fact that Lennart Poettering is also the author of Pulseaudio. Now let me state that I like Pulseaudio. However, it's also pretty huge (149,924 lines of code), and it contained plenty of bugs when first released, plus new bugs which got introduced while fixing the old ones. Plenty of people had issues with Pulseaudio, including me. Ironically, first time I installed it, there were no problems...for about a year. Then after an update, it suddenly broke, leaving me with no sound. However, I was able to switch pretty easily back to Alsa, which I ran for a couple of months. Eventually, the issue with Pulseaudio was fixed, and I run it now. The bug that broke Pulseaudio on my computer was an inconvenience for me, but I was able to use an alternative for awhile and overall it was no big disaster.

But imagine what a critical security compromise in systemd could do. It's one thing to lose sound, it's another to lose your init system. And you can't just uninstall systemd and go back to Upstart or Sysvinit for a couple of months until the problem is fixed, because Lennart and Team have made that impossible.

If you think that shaving a couple of seconds off your boot time is worth risking your credit cards or bank accounts hacked, then fine. But I'd rather not take that gamble. And no doubt professional system administrators trying to run secure servers are more than a little concerned, which is a big reason why Debian is teetering on the edge of a fork.

I'm currently running Ubuntu 14.10 with Upstart as the init system, and I'm happy with it. But if systemd becomes mandatory in the future, I'll have to jump distros. It's nothing to do with "the UNIX philosophy," or with me being a Luddite (I'm not), or whether or not Lennart has bad breath. For me, it's just a matter of security, plain and simple.

I know that a lot of you love systemd. I'll bet you'll love it a whole lot less if it breaks. Of course, maybe it won't break. Or maybe it will. If you want to play Russian Roulette with your OS, more power to you.

---

### Post by vellon on 2014-10-28
I hope you looked at the kernel page on the same site....

---

### Post by MartyBuntu on 2014-10-28
> **Dog's_Breakfast said:**
> They write bug-free code. After all, they say so, thus it must be true.




Do you have a link to this alleged claim?

I'll be waiting.

---

### Post by Dog's_Breakfast on 2014-10-28
> **vellon said:**
> I hope you looked at the kernel page on the same site....

Of course I did. The kernel is huge. But Linus wouldn't go out of his way to make it even bigger. He could, of course, take the systemd philosophy and put xorg and pulseaudio into the kernel, making it are larger and more difficult to debug, and open up numerous new avenues of attack. Fortunately, he has better sense than to do such a foolish thing.

Every system administrator knows that when setting up a server, you keep it "bare bones." This creates a much smaller attack surface. Desktop users want more bells and whistles than a server would have, but the same KISS (Keep It Simple Stupid) principle applies.

When the Shellshock compromise was revealed, prudent system administrators immediately switched away from the bash shell (there are several others such as csh, tcsh and zsh) until the fix was in, then they switched back. With systemd, you can't switch init systems. There is actually no reason why you shouldn't be able to remove systemd and switch back to upstart or sysvinit, it's just that Lennart has deliberately added unnecessary dependencies to lock in users. That is a very Microsoft tradition, which has caused many experienced geeks to comment that systemd is turning Linux into Windows. As you are no doubt aware, Windows has had huge security problems over the years, and even now still relies on "security through obscurity" as it's first line of defense, something we can't do with open source.

You can be sure that the black hats are combing through the systemd source code right now, looking for exploits. And they will probably find them before Lennart does. Attacks on Linux servers have become highly sophisticated - google search for Linux/Cdorked.A to see just how sophisticated they've become. Or I'll just save you the trouble:

[http://www.welivesecurity.com/2013/04/26/linuxcdorked-new-apache-backdoor-in-the-wild-serves-blackhole/](http://www.welivesecurity.com/2013/04/26/linuxcdorked-new-apache-backdoor-in-the-wild-serves-blackhole/)

---

### Post by Dog's_Breakfast on 2014-10-28
> **MartyBuntu said:**
> Do you have a link to this alleged claim?

I'll be waiting.

You won't have to wait long:

[http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/](http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/)

Maybe Sievers didn't say "bug free," but then again he closed the bug report without fixing it, arrogantly deciding that the problem he caused wasn't his problem. A bug in systemd that causes kernel panics is not a bug?

---

### Post by MartyBuntu on 2014-10-28
> **Dog's_Breakfast said:**
> You won't have to wait long:

[http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/](http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/)

Maybe Sievers didn't say "bug free," but then again he closed the bug report without fixing it, arrogantly deciding that the problem he caused wasn't his problem. A bug in systemd that causes kernel panics is not a bug?

That doesn't answer the question I asked.

Back up your claim.

---

### Post by Dog's_Breakfast on 2014-10-28
I'm not playing this game. I don't care who said what. I'm interested in systemd's security, or lack thereof. If you can make a technical argument as to why systemd is just as secure as upstart or sysvinit, then I'd love to hear it. If you want to divert the discussion to he said/she said, then bye-bye.

---

### Post by vellon on 2014-10-29
I was trying to keep out, but...

So systemd is less secure than sys V because it is "larger and more difficult to debug, and open up numerous new avenues of attack", but the vastly larger kernel is not less secure, because it doesn't include (some ill-defined) extras? So is the code base size the critical factor (your first post) or not (your reply)?

---

### Post by Dog's_Breakfast on 2014-10-29
> **vellon said:**
> I was trying to keep out, but...

So systemd is less secure than sys V because it is "larger and more difficult to debug, and open up numerous new avenues of attack", but the vastly larger kernel is not less secure, because it doesn't include (some ill-defined) extras? So is the code base size the critical factor (your first post) or not (your reply)?

Hello Vellon. There's no reason for you to "keep out" unless you want to be out of the discussion. It's a reasonable question to ask.

The kernel is huge. If there was a way to make it smaller, I'm sure Linus would happily do so.  It's the core of the operating system and interacts directly with the hardware, and thus the need to constantly maintain drivers, which includes both adding new drivers and dumping old ones that no longer are needed.

You can't do without the kernel, but you would never want to do anything to make it even more complicated than necessary. You wouldn't stick xorg into the kernel, for example, even though you could. Doing so would create enormous security issues. You could probably stick the init system into the kernel too - that would also be an insane idea.

There are plenty of other big software projects - LibreOffice springs to mind. But LibreOffice isn't central to the operating system like init is, it runs unprivileged, and you would never install it on a server.

The big issue with systemd that has caused so much agonized debate is that it is NOT simply an init system. It has gone way beyond that, and the developers are determined to add even more bells and whistles. This code is all new, it keeps changing, and you can be sure that there are bugs in it which no one has yet discovered. Auditing it is made much harder by the fact that there is so much of it.

The most upsetting issue though is that you can't decide not to use it - once you've gone with systemd, there is no turning back. You are married to it for life. The developers seem to have a zeal for eliminating any possibility of installing another init system by putting dependencies in everything. I cannot see any reason for doing this, other than that they are striving for a lock-in. But if there is another good reason, then they ought to explain themselves. System administrators are particularly livid about this, and Debian is on the verge of a fork over this issue.

I don't want to repeat myself too much, so maybe I should pause here. The above is, to me, the main case against systemd. Other people may have personal gripes with the systemd developers (ie Lennart, Kay Sievers, Harald Hoyer, Daniel Mack, Tom Gundersen, David Herrmann) - I don't. An init system is not a religious crusade for me - I just want something that I know will be stable and secure. Maybe systemd will be all that, but I'm not convinced, and indeed the complexity and lock-in looks to me like systemd is more and more "faith based." About 1/3 of the Internet runs on Linux servers - I dread to think what would happen if they all went down at once, and there was no way to bring them back up.

This is an awful lot to risk just to shave two seconds off of boot-up time.

Good luck.

---

### Post by vellon on 2014-10-29
> **Dog's_Breakfast said:**
> The kernel is huge. If there was a way to make it smaller, I'm sure Linus would happily do so.  It's the core of the operating system and interacts directly with the hardware, and thus the need to constantly maintain drivers, which includes both adding new drivers and dumping old ones that no longer are needed.

You can't do without the kernel, but you would never want to do anything to make it even more complicated than necessary.

I picked the kernel as an example deliberately.

> **Dog's_Breakfast said:**
> The big issue with systemd that has caused so much agonized debate is that it is NOT simply an init system. It has gone way beyond that, and the developers are determined to add even more bells and whistles. This code is all new, it keeps changing, and you can be sure that there are bugs in it which no one has yet discovered. Auditing it is made much harder by the fact that there is so much of it.

The same arguments could be used against the kernel. I don't hear the old guard pushing for a microkernel. Additionally, bugs are not unique to new code; witness the ssh and bash flaws.

> **Dog's_Breakfast said:**
> The most upsetting issue though is that you can't decide not to use it - once you've gone with systemd, there is no turning back. You are married to it for life. The developers seem to have a zeal for eliminating any possibility of installing another init system by putting dependencies in everything. I cannot see any reason for doing this, other than that they are striving for a lock-in. But if there is another good reason, then they ought to explain themselves. System administrators are particularly livid about this, and Debian is on the verge of a fork over this issue.

Again, that argument could be levelled at many other components, kernel included. No sysadmins of enterprise server installations would seriously look at changing the init system (as an emergency fix - another story for the next upgrade cycle, perhaps) in the event of a bug. The risks would be massive and the testing to give an appropriate level of confidence far too time-consuming. What you actually do is lock down what you can and await the official patch.

> **Dog's_Breakfast said:**
> About 1/3 of the Internet runs on Linux servers - I dread to think what would happen if they all went down at once, and there was no way to bring them back up.

Have I missed something here? Have there been many large-scale security issues yet? Systemd has been in use by several distros for a while now. RHEL 7.0 must be in use on more than a few live-facing servers by now, and I've seen no news that systemd has caused trouble. Is there any reason to think "all" might go down at once? Even a single large corporation runs several different stacks as a result of changing direction, commercial decisions and upgrade cycles. Any vulnerability, especially in newer code, is not necessarily going to be on every server.

> **Dog's_Breakfast said:**
> This is an awful lot to risk just to shave two seconds off of boot-up time.

A happy side-effect only. Of more consequence is the introduction of some uniformity and compatibility between distros. No need for each to rewrite the plumbing.

---

### Post by 1clue on 2014-10-29
Dog's Breakfast, do you even use Ubuntu?  

While I see you joined in 2007, you haven't posted anywhere except this thread, and then you're posting like a long-time pro.  A zero-beaner is a new user no matter how you slice it.

I object on principle to someone joining just to post to a specific debate, I don't care if you're technically on my side or not.  Especially with the systemd debate, there are lots of people who google and join up just to muddy the water, when they aren't even affected by a distro's decision to use or not use any package.

---

### Post by 1clue on 2014-10-29
Regarding the kernel:

For those of you who might be reading and don't know, the kernel is Linux, and everything except the kernel is software which runs on Linux. This is by definition. Almost everything else you might put on Linux works also on other kernels. Software which runs only on Linux does not make it part of Linux. It only makes it a single-platform application.  The kernel is the software which runs directly on your hardware and which provides a consistent interface to any other software.
 
The kernel is by necessity large.  That said, the minimum kernel to run most processors with minimal hardware support is pretty small.  Most of it can be built as modules, which truly are not necessary unless they are being used.  Of the code which can't be compiled as a module, even more of it can be omitted from the core kernel.

I would like to point out that even though the kernel is all in one repository and contains a stunning amount of lines, it is also very modular and has an inordinate number of people testing it exhaustively.  Basically, everyone who uses or tests on Linux is testing the kernel whether they intend to or not.  While testing involves actually booting it from real hardware, mainstream hardware is thoroughly tested by the sheer volume of people using it.

If anyone is curious and don't know already, you might want to google 'Linus Torvalds Lennart Poettering" and sit down for a night or two of reading flames.  You might want to add "Kai Sievers" in there since Lennart and Kai collaborate a lot.  They go both ways.

Politically speaking systemd is an insanely hot topic.  Which is why I object to people who don't normally post on a distro's forum throwing their gasoline on the fire.

There are extremely valid technical issues to discuss here, and flames don't help anything.

---

### Post by JKyleOKC on 2014-10-29
> **1clue said:**
> Dog's Breakfast, do you even use Ubuntu?  

While I see you joined in 2007, you haven't posted anywhere except this thread, and then you're posting like a long-time pro.  A zero-beaner is a new user no matter how you slice it.

I object on principle to someone joining just to post to a specific debate, I don't care if you're technically on my side or not.  Especially with the systemd debate, there are lots of people who google and join up just to muddy the water, when they aren't even affected by a distro's decision to use or not use any package.Y'know, there are many, many folk who lurk these forums and almost never post any message themselves. Are you saying that their opinions are irrevelant, if they finally feel that they do have something worthwhile to contribute?

This happens to be the only thread on this subject that has stirred me to jump in, so perhaps the same objection would apply to me. Or perhaps the count of more than 2,000 beans displayed over in the left margin might make a difference...

I don't want to get off topic too far and risk violating the Code of Conduct, so I'll get back on subject: the big problem with systemd is simply that it (1) increases the risk of filesystem corruption and (2) prohibits the provision or use of any fallback process when (not if) that happens. Personally, I found the introduction of upstart to be more than a trifle upsetting. The original SysV approach was quite simple, easy to understand, and easy to customize. However I've not been responsible for a multi-user system for nearly 40 years, so the needs of today's system administrators are only theoretical to me. The parallel processing that upstart provides finally persuaded me to accept it (and more to the point, I've found Xubuntu to be much more to my taste than were its predecessors here, both SysV oriented: Slackware 2.0 and Mandrake 8.1).

Personally, I'll be able to exist with systemd if it takes over -- but I can easily see what makes it unacceptable to a system administrator, and for that reason maintain that its use **must** be optional, **not** mandated from on high. Were I still charged with keeping service up for a multitude of users, I'd be actively searching for distributions that provided that choice, right now, rather than waiting for an emergency. I learned long ago that Murphy was an optimist!

---

### Post by 1clue on 2014-10-29
> **JKyleOKC said:**
> Y'know, there are many, many folk who lurk these forums and almost never post any message themselves. Are you saying that their opinions are irrevelant, if they finally feel that they do have something worthwhile to contribute?

This happens to be the only thread on this subject that has stirred me to jump in, so perhaps the same objection would apply to me. Or perhaps the count of more than 2,000 beans displayed over in the left margin might make a difference...



This needs to be addressed.

First thing, if Dog's Breakfast is an actual Ubuntu user then I'll apologize profusely and sincerely.  I don't have any problems with people who actually use or intend to use, or even find out if they might want to use, a distro posting questions about that distro.  Whether they agree with me or not.  Dog's Breakfast was actually arguing on my side of the fence.

Second thing, the reason for that post.

Systemd is a very hot topic on the Gentoo forums, which is my other main distro.  There are a number of people who have joined that forum specifically to weigh in on systemd -- The join date matches their first few posts in a systemd thread, and some even say they joined just for that debate and had no intention of ever installing Gentoo -- and for that matter they seem to be there specifically to muddy the water and cause discord, not to actually resolve anything.

My objection is to that behavior.  People who actively google for systemd related threads, join forums or mailing lists and start trolling.

---

### Post by 1clue on 2014-10-29
Another thing I'd like to point out is that a typical lurker tends to make very different posts than a veteran poster.

A lurker generally makes short, to-the-point posts.  A veteran tends to ramble a bit (like I do.  :)  )

Dog's Breakfast posted several fairly involved posts in a short time.  This to me implies that he/she has done a whole lot of posting.  So why not post on Ubuntu until now?  Why stay quiet until now, when you are obviously comfortable posting a bunch of long posts in quick succession?  This does not seem to be the 'lurker' personality type, if you will.

---

### Post by Dog's_Breakfast on 2014-10-29
Hi all. Just to be clear: yes, I am a long time Ubuntu user, and I always install a new release even before it gets released and I make bug reports when necessary. I've been using Ubuntu 14.10 as my main desktop ever since beta2 was out. I have Ubuntu 14.04 installed on my wife's computer (I do all the sysadmin stuff for her, she's not a geek).

Ubuntu is not the only distro I use - I've got a Debian partition on my hard disk as well. I've experimented with a lot of different distros since I first started using Linux in 1998, among them Slackware, SUSE, Libranet (now defunct), Red Hat and Fedora. I also used FreeBSD and OpenBSD for about a year, but that was about 10 years ago.

I confess that I do very little posting on forums. My bad - I should contribute more. I do actually have a good deal of experience that I should be sharing with newbies, and I give the thumbs up to those of you who help out punters by answering their questions. On the other hand, I have installed Linux (many times) on the computers of friends who wanted to break free of Windows. I usually install Ubuntu for them, because I think it's overall the easiest desktop distro for a Windows refugee.

The systemd issue has really fired up my passions, and that's why I'm posting here now. A lot of us "old" Linux veterans are very concerned about systemd, and I think for good reason. It has the potential to break Linux in such a way that it may be unfixable - it's certainly creating a civil war within the community, as we can see right here on this forum. Again, that would not be the case it systemd was just another init system, but it's obviously much more than that.

The goals of the systemd developers seem to be constantly evolving, and I really don't know how far they will go. By now, it's fair to say that they have created a "Systemd/Linux" - in other words, systemd is central to the operating system since it is controlling vital components that have dependencies on it. Furthermore, changing log files from ASCII to binary makes me suspicious that their next goal will be to introduce a "Linux registry." Over the years I have read numerous times appeals by some programmers (who should know better) to add a Linux registry because it's "modern" and Windows has it, so Linux should too. That proposal has always been met with fierce hostility by experienced Linux sysadmins, but if systemd developers introduce it, you will have no choice but to use it because you can't uninstall systemd and switch back to sysvinit, upstart or openrc.

How the civil war is going to end, I don't know. There is one project that most of you have probably heard about, [uselessd](http://uselessd.darknedgy.net), which is an attempt to turn systemd back into just an init system. Not a bad idea since it would preserve the useful things that systemd does, but it's a one-man project and unless the developer gets a lot of support from the community, his effort will probably fizzle. A much more likely scenario will be that Debian will fork - that's being discussed heavily right now [here](http://debianfork.org) and the people talking about it have the technical skills to make it happen. However, Debian is a huge distro, so finding enough volunteers to repackage things may not be easy unless there is a mass migration away from mainstream Debian (that too could happen).

For now, I'll stick with Ubuntu as my main desktop because I still have it running with upstart, but I'm going to install both Gentoo and FreeBSD into a spare partition and start experimenting with those. Not really what I want to do, but I have to work with what is available. I will not simply roll over and accept systemd without a fight. I'll change my mind if/when the systemd developers wise up and change their ways (I don't expect that to happen though). Sad.

---

### Post by JKyleOKC on 2014-10-29
> **1clue said:**
> Second thing, the reason for that post.

Systemd is a very hot topic on the Gentoo forums, which is my other main distro.  There are a number of people who have joined that forum specifically to weigh in on systemd -- The join date matches their first few posts in a systemd thread, and some even say they joined just for that debate and had no intention of ever installing Gentoo -- and for that matter they seem to be there specifically to muddy the water and cause discord, not to actually resolve anything.

My objection is to that behavior.  People who actively google for systemd related threads, join forums or mailing lists and start trolling.Well, I share what I perceive to be your low opinion of astroturfers -- but the response from *Dog's Breakfast* sounds quite good to me and I agree with his sentiments. Let's see if the other recent zero-bean participant chimes in...

With the talk of a possible or even likely fork for Debian, I wonder which way the *buntu family might go if it happens. Personally, I think I'd follow them along a non-systemd path, but not going the other way. I agree with you that it seems to be the easiest for newcomers to become accustomed to; I originally chose Xubuntu because I was working at the time with near-obsolete hardware, but when the main line introduced Unity I was very glad that I had chosen so well. Eye candy is not my thing. I even began evalating Debian Wheezy just in case Xubuntu chose to go for the new and shiny.

Back in the early days, I even moderated a debate at Software Development '90 in Oakland about the pros and cons of the GUI, and the title was "GUI, Phooey!" Expounding the pros were a couple of top-level sales droids from Microsoft; the cons were presented by Stan Kelly-Bootle and Chip Rabinowitz. While as moderator I was supposed to be neutral, I was in fact firmly on the "phooey!" side. Nobody won, but it was an entertaining evening.

I've since come to realize that for many things, including such tasks as participating here, the GUI is actually better than the command line. However it's not the best for everything; I still prefer the CLI for intricate photo enhancement although I need the GUI to evaluate the results. IOW, the best tool is the one that best fits the immediate need; one size **never** fits all. So my objection to things like systemd is simply that they violate that axiom!

---

### Post by 1clue on 2014-10-29
Before I respond to anyone else, let me apologize to Dog's_Breakfast and to JKyleOKC.

I seriously do not have an issue with zero-beaners having opinions.  I have helped so many Linux n00bs get started I can't even give you a number, been in Linux pretty hard-core since 1996.  Usually a zero-beaner starts out in a different way though.

My suspicion is based most recently on 'astroturfers' (as JKyleOKC calls them) pouncing on Gentoo forums.  There, you offer criticism of systemd or openrc (Gentoo's normal init system) or of any number of other Redhat-sponsored packages, and the vultures start circling.  It's difficult to get a real support issue taken care of because they use any excuse to move the battlefield.  Here in Ubuntu-land it's obviously a bit more relaxed, and I'd like to keep it that way.

IMO a distro's future should be determined by someone who actually uses the distro.

Other than that, Dog's Breakfast's posts sound scarily close to my opinion.

Really I think damage inflicted by systemd will not be irreversible in the long run.  It only matters if somebody specifically hard-codes references to systemd into their code, which I can't imagine having happen that much.  Gnome is pretty much a goner for now since Redhat controls it, and that bodes ill for mainstream Ubuntu users if they care (probably most won't notice anything unless there's a really annoying bug or really bad security hole) but otherwise it could have a pretty small impact on code overall.

That's not to say it won't still cause problems.  Systems using systemd still have a large, ungainly init system where one is not needed, and any flaws will still effect them.

I can't say I understand the need for binary logs.  It's certainly possible to have a log file owned by a thread, allow exactly one thread to control it and pass in messages for it to write to.  Doing so could prevent the issues of multiple writers they claim a binary log fixes.

Registry:  Most commercial UNIXes I've seen have some sort of binary registry.  I do understand the attraction, don't know that I like it but frankly this is one of those places where I'm an old guy wailing about the old days.  If somebody were to introduce a binary equivalent of a registry with a really good editor, it would probably take off and I'd probably learn it and live with it.  Over the years you get to recognize what's a good idea even if you don't like it, and figure on going with the flow.  The key though is that it needs to solve a lot of problems, and it needs a really good editor.

Back on track to systemd,

If Redhat and Poettering would break systemd into truly independent modules one of which is an init system and nothing else, and if they'd get rid of /usr-on-root requirement then I'd probably be fine with it.  Of course doing that, they'd almost have to chop out most of their code as modules, and probably the part that is the init system would be no larger than upstart.

---

### Post by JKyleOKC on 2014-10-29
No apology needed so far as I'm concerned. I've not been quite as laid back as I usually prefer to be, having undergone a spot of near-heart surgery Monday afternoon and still being a bit strung out and impatient until today (it was quite minor, actually, and I was back home less than 6 hours after leaving for the hospital) so reacted a bit more snippily than I should have...

Yep, I could get used to systemd too if it were broken into modules and allowed /usr to be on its own partition rather than having to share that of / (which is a point I'll have to remember next time I do a clean install!)... However I suspect that part of the real reason it's being pushed so hard is to create lock-in; I'm almost certain that's the driving force behind Unity!

---

### Post by 1clue on 2014-10-29
Creating lock-in on Linux is going to have a limited amount of success IMO.  They can own Gnome and maybe a few more things, but they have to sell the kool-aid to the people who manage the software.

Considering the storming debate about systemd, there are sure to be some software projects in every category who don't buy the hype on systemd and will refuse changes requiring it.  You may not get exactly the window manager or whatever it is that you want, but you'll be able to have a working system.  And face it, when you pick whatever-piece-of-software you have a list of pros and cons and you pick the one with the biggest difference in the favorable direction.

If all else fails, you can fork the project you liked just before they started doing irreversible systemd commits, and surely somebody else will get on board to help you manage it.

Maybe I'm a bit lackadaisical about it, the software I depend on will surely not depend on systemd ever.  There's no reason for it to want specifics about anything like an init system, and most of it runs on anything from a raspberry pi to an IBM mainframe.

---

### Post by 1clue on 2014-10-29
[I]Darn it.  I somehow posted the above before I finished my post, and then didn't notice for awhile.  This is the second half of the above post.
[/I]
My interests in a windowing system are on the order of Xfce, i3 and fvwm -- not necessarily in that order.  That's hardly in line with an average computer user, and certainly not going to be interesting to Redhat, any of that.  All of these things focus on minimalism.  Firefox isn't going to make a hard dependency, it's a browser on pretty much any platform.  Apache surely won't drink the kool-aid, they're rock-solid developers and they run on pretty much any platform, UN*X or anything else.

So far, none of the apps and services which require systemd are in my list of required or even wanted/interesting apps.

I figure there will be a meeting in the middle at some point, and that meeting almost has to be improvement of systemd such that it ceases to be infectious, or they eventually find enough flaws that people who are in love with it fall out of love and regain sanity.

---

### Post by Dog's_Breakfast on 2014-10-30
No problem, 1clue (handshake extended)...

Glad to hear that you've helped many Linux n00bs get started. I feel guilty for not doing more.

*Registry: Most commercial UNIXes I've seen have some sort of binary registry. I do understand the attraction, don't know that I like it but frankly this is one of those places where I'm an old guy wailing about the old days. *

Interesting, I didn't know that. I just guess that the registry was just stuck in there as one means of keeping these commercial systems proprietary, but I could be dead wrong.

*If Redhat and Poettering would break systemd into truly independent modules one of which is an init system and nothing else, and if they'd get rid of /usr-on-root requirement then I'd probably be fine with it.*

Me too, but you'd better not hold your breath waiting.

cheers,
DB

---

### Post by vellon on 2014-10-30
As "the other recent zero-bean participant", I've been here since Feisty Fawn, but this thread was the first I felt interested in responding to since the forum security breach. I created a new id to do so.

The subject matter seems to have drifted, so carry on with the conspiracy theories and insults ("people who are in love with it fall out of love and regain sanity", "drink the kool-aid")

I don't use Debian directly, so which way it goes does not bother me unduly. I'd be interested to see it fork, however, as a test of the "diversity is good" attitude often displayed in the Linux world, but that's another subject.

---

### Post by JKyleOKC on 2014-10-30
My apologies to you, vellon, for being suspicious. Once 1clue raised the possibility of astroturfing, my not-very-hidden conspiracy-theorist persona crawled out of the woodwork. Too much time spent reading SlashDot, I suppose.

I'm a firm believer in the KISS principle and an opponent of bloat, wherever it occurs. However I also appreciate the "diversity is good" attitude, so I too will be interested to see what happens should I live long enough. My geezerhood should be quite obvious from some of the dates I've quoted, and that photo in my avatar was made almost 20 years ago -- but hanging out in these parts helps keep me mentally young despite the passage of time.

As somebody once observed, "On CompuServe, nobody knows you're really a cat!" Hang in here and keep sounding off. Discussion is good, until it turns into name-calling, so once more let me apologize for my implied slander.

---

### Post by mikodo on 2014-10-30
> **1clue said:**
> [I]Darn it.  I somehow posted the above before I finished my post, and then didn't notice for awhile.  This is the second half of the above post.
[/I]
My interests in a windowing system are on the order of Xfce, i3 and fvwm -- not necessarily in that order.  That's hardly in line with an average computer user, and certainly not going to be interesting to Redhat, any of that.  All of these things focus on minimalism.  Firefox isn't going to make a hard dependency, it's a browser on pretty much any platform.  Apache surely won't drink the kool-aid, they're rock-solid developers and they run on pretty much any platform, UN*X or anything else.

[B]So far, none of the apps and services which require systemd are in my list of required or even wanted/interesting apps.
[/B]
I figure there will be a meeting in the middle at some point, and that meeting almost has to be improvement of systemd such that it ceases to be infectious, or they eventually find enough flaws that people who are in love with it fall out of love and regain sanity.
Well, I couldn't stop reading at least here. And, I am happy to do so. This has been a tempered, informative thread. It provisions understanding for growth, moving forward. What young people of Linux need to hear, to guide them in continuing on, with what has been achieved to date, by much thought/debate/work.

Now, for my reason for posting. I hope that casual informed users, will have a place to go to see what apps and services are available for use, outside of systemd, if in fact it becomes all-encompassing, as it surely has the potential for and may be moving towards.

Addendum;

I had been reading discussions earlier, in Gentoo discussion forums, too. I am afraid installing and using it, is not in my future. I guess, my hope if systemd becomes totally unsafe to use, that a Debian fork resulting because of it, will become viable for casual/safe use. Or, how about an "ease of use distro" fork of Gentoo, like [Manjaro]("https://en.wikipedia.org/wiki/Manjaro_Linux") and [Chakra]("https://en.wikipedia.org/wiki/Chakra_%28operating_system%29") are for Arch. If in fact, the Gentoo devs, can keep it free of Systemd, (that seems to be in debate too!)  For now, I remain with 'buntu, to make these kind of "system" decisions for me.

---

### Post by vellon on 2014-10-30
Not a problem JKyleOKC. I too prefer KISS, but I'm also a pragmatist.

Someone else was thinking along the same lines as me :) - I've just found this (nothing to do with me, honest):
[http://boycottlinux.org/](http://boycottlinux.org/)

---

### Post by Dog's_Breakfast on 2014-10-30
> **mikodo said:**
> I had been reading discussions earlier, in Gentoo discussion forums, too. I am afraid installing and using it, is not in my future. I guess, my hope if systemd becomes totally unsafe to use, that a Debian fork resulting because of it, will become viable for casual/safe use. Or, how about an "ease of use distro" fork of Gentoo, like [Manjaro]("https://en.wikipedia.org/wiki/Manjaro_Linux") and [Chakra]("https://en.wikipedia.org/wiki/Chakra_%28operating_system%29") are for Arch. If in fact, the Gentoo devs, can keep it free of Systemd, (that seems to be in debate too!)  For now, I remain with 'buntu, to make these kind of "system" decisions for me.

Hi Mikodo. I agree that Gentoo looks scary. I actually installed and ran it years ago, and found it quite a challenge with hours of compiling every time I wanted to update or install anything. I'm just hoping that with my currently much faster computer, it won't be so bad. I will give it a try, but I'm only going to give it a 50% chance (at best) of becoming my Ubuntu replacement if systemd becomes unavoidable.

I considered Slackware. It was, in fact, my first Linux distro. I suspect that the lack of dependency checking and the small repository of packages that can be installed via [Slapt-get](http://www.slackwiki.com/Slapt-get) will leave me feeling deflated, but I'll give it a try anyway.

My most optimistic assessment is for FreeBSD, or rather its desktop spin-off PC-BSD. As I mentioned, I was a FreeBSD user about 10 years ago and liked it, but I felt that Linux was progressing faster and so I jumped ship. Hardware drivers have always been an issue for the BSDs - I'll be most anxious to see if my current setup will work. I never got any printer to work with FreeBSD, but I'm hoping that has changed now that they use CUPS.

One real dark horse is [Void Linux](http://www.voidlinux.eu/). I know little about it, except that it uses [runit](http://smarden.org/runit/) as its init system. I do plan to give it a try, but it seems to have a pretty small user base, so I suspect the available packages will be slim.

Like you, I hope for a Debian fork, with the possibility that it will inspire Mark Shuttleworth to keep upstart around so that I can keep using Ubuntu.

===============

*"Men, it has been well said, think in herds; it will be seen that they go mad in herds, while they only recover their senses slowly, and one by one."*
 - Charles MacKay, Extraordinary Popular Delusions and The Madness of Crowds, 1841

---

### Post by mikodo on 2014-10-30
> **Dog's_Breakfast said:**
> 
My most optimistic assessment is for FreeBSD, or rather its desktop spin-off PC-BSD. As I mentioned, I was a FreeBSD user about 10 years ago and liked it, but I felt that Linux was progressing faster and so I jumped ship. Hardware drivers have always been an issue for the BSDs - I'll be most anxious to see if my current setup will work. I never got any printer to work with FreeBSD, but I'm hoping that has changed now that they use CUPS.
Hey, thanks for that!

I was reading about, FreeBSD, for a replacement OS, just a short while ago. I had no knowledge of [PC-BSD]("https://en.wikipedia.org/wiki/PC-BSD"). It's something to keep in mind, being what it offers.

---

### Post by JKyleOKC on 2014-10-30
> **vellon said:**
> Not a problem JKyleOKC. I too prefer KISS, but I'm also a pragmatist.

Someone else was thinking along the same lines as me :) - I've just found this (nothing to do with me, honest):
[http://boycottlinux.org/](http://boycottlinux.org/)Now that site is downright interesting! It sounds like the old battle between Minix and Linux still goes on at least somewhere.

As it happens, I long ago became quite interested in operating-system design, and for a short time even marketed one for the TRS-80 that did all the necessary functions but nothing more. I called it XDOS as in "Brand X" and offered it through a local retailer as a medium for his "educational" software line. I think I may have sold five copies altogether. Building it was fun, though, and I learned at that time just how simple an o/s could be and still be fully functional. My "Fast Four" patch for the TRS-80 Model 4 that doubled its memory access speed was much more successful; I think it sold around 50 copies!

But that was for a single defined hardware platform, not the literally hundreds of "variations on a theme by IBM" (to paraphrase Rachmaninoff) that have flooded the market since 1981. Much of the criticism leveled at Linux by that site is due to the many different platforms on which it's expected to run, as is the integration of the device tree. At least Linux, unlike Windows itself, leaves the un-needed driver modules on its installation media rather than copying them all to the user's storage.

The system could undoubtedly be made much more modular and Unix-like were anyone willing to spend the effort. The multi-platform problem could be addressed in exactly the same way that 32- and 64-bit needs are handled now, by having platform-specific versions that share a common core set and API. The GPL makes this perfectly possible. But who's going to volunteer to fork the entire kernel for such a task, or spend the effort to keep it up to date once created?

So we start from where we happen to be, and choose the least objectionable alternatives from those that meet our needs, even though we know that better solutions are possible. If they ever become practical, we may choose them. Meanwhile, we get from here to there one byte at a time, just like eating an elephant...

---

### Post by 1clue on 2014-10-31
Vellon's posts don't come across as an astroturfer's style.  It seems they are prepared to argue, and flood you with information.  Actually if you check up on that information much of it is subjective or just plain wrong.

Vellon posts clearly and concisely, usually (in this thread) pointing out flaws in my logic.  :)

@JKyleOKC,

Diversity is good.  Diversity means that if one approach fails for some reason then other approaches are available.  The problem with systemd is it tries to force the distro maintainers into a no-diversity situation.  Going from systemd to non-systemd would take some coding, if you intend to maintain the apps that have attached themselves to systemd.  In Ubuntu's case, Gnome comes to mind.

@mikodo,

Gentoo is scary at first, but IMO it's very doable.  You need to follow instructions, and you need to read those instructions very carefully before you follow them.  If you don't, you still don't have an irretrievable situation, but you've probably wasted a lot of time.

IMO Gentoo wants an i7 or better.  I installed it on a Raspberry Pi but it took forever, never got the kernel right (stole the Raspbian one) and finally gave up on the whole idea.  On anything quad core and speedy, Gentoo is pretty sweet.  You'll learn more about Linux than you ever imagined.

After a few installs, most Gentoo users either skip or ignore certain parts.  I'm no exception, I like to do things my own way.  I still sort-of follow it, but change it up a bit.  It's important that you don't accidentally miss something, but you can add steps or use something completely different to achieve the same ends.  Most of the common approaches can be found on google, not necessarily on a Gentoo site.

My current Linux workstation has Gentoo, but no desktop.  I might have to change that soon, I'm debating either i3 or fvwm.  It's been years since I did fvwm, I might give it a try, it's so absolutely, delightfully configurable and now it would be so lightweight as to float on air.  There's a group that actually keeps it workable with current hardware and software.

---

### Post by 1clue on 2014-10-31
Void looks profoundly interesting.  Thanks for the link.  I'm gonna do that sometime soon, the all-source way I think.

---

### Post by vellon on 2014-10-31
> **1clue said:**
> Vellon's posts don't come across as an astroturfer's style.  It seems they are prepared to argue, and flood you with information.  Actually if you check up on that information much of it is subjective or just plain wrong.

That perspective is not unique amongst the posters here, naturally.

---

### Post by vellon on 2014-10-31
JKyleOKC, it might be worth rereading that site with a critical eye ;)

---

### Post by JKyleOKC on 2014-10-31
> **vellon said:**
> JKyleOKC, it might be worth rereading that site with a critical eye ;)I did read about halfway down the page, with that critical eye, and found that I actually agree with it in many ways. However I've not yet found a better alternative!

All that I want an o/s to do is very little more than that minimum which Gary Kildall achieved with CP/M: load programs, and mediate i/o between the needs of the CPU/RAM and those of the i/o devices. Add to this list the provision for multi-tasking, which in itself implies the possibility of, but not any necessity for, multiple simultaneous users, and you've got my personal functional requirements list. The final addition to the list would be reliability. 

Note that security appears nowhere in my list of requirements; I consider that to be a process rather than an attribute, to be supplied by the human operator and, probably, by high-priority task(s) invoked by that operator. Those tasks run under, but are not part of, the o/s itself.

Even the multi-task scheduling can be quite primitive, using high-priority processes that are not part of the o/s itself to provide any desired degree of elegance. The multi-user system I ran between 1967 and 1970 used a simple round-robin algorithm, running on a processor with no stack at all and only a single hardware interrupt to service all needs -- and it was able to mimic a full-sized mainframe of the day and support remote terminals. The hardware wasn't even considered by its maker to be a full-fledged computer, although it was fully Turing-compatible with any that existed at that time.

However getting back to the simplicity of the system that Ritchie and Thompson cobbled together in stolen time to mimic a single-user Multics site doesn't really seem very likely these days. Genius is a rather rare attribute among we humans, and in today's universe it seems to be spent on adding bells, whistles, and eye candy rather than any search for elegance. Who was it that said "Perfection is achieved not when nothing more can be added, but when nothing more can be taken away"? Definitely some old geezer like myself...

---

### Post by 1clue on 2014-10-31
> **vellon said:**
> ...[http://boycottlinux.org/](http://boycottlinux.org/)

While they do have some points, some of this is pure garbage IMO.

The first roadblock was them stating that CVS is in any way better than git.  Having been the administrator for several SCMs for years, including CVS, Subversion and Git, there's absolutely no contest.  Git kicks ass.

There are good arguments for and against microkernel architecture.  As with anything, the right answer depends on what you intend to do with it.

The above page is written by someone who has a strong personal preference and that needs to be taken into account.

Some of my use cases might benefit from microkernels, but their reference to minix is ridiculous.  It was written from the ground up as an educational tool, not for use as a real UNIX system.  In my work (and, sadly, in my play sometimes) I'm using 4 or more cores, running VMs and using sometimes in excess of 16g RAM on multiple systems.  Minix isn't even ported to x86_64, which means it doesn't even natively handle more than 4G, less depending on architecture.

Minix is probably a really good idea for ARM single-board computers, I see they're porting to BeagleBone.

If someone were to point out a viable microkernel-based POSIX system that can handle Enterprise-class hardware, I'm all ears.

BTW, parts of this discussion have fallen far from upstart and systemd.  Does anyone think maybe we should split off, maybe using the link above and posts referencing it as a guide?

---

### Post by vellon on 2014-10-31
Guys, it's a spoof of [boycottsystemd.org]("http://boycottsystemd.org").... :)


More relevant and informative, there is a story on slashdot, where a systemd sceptic asked for a list of good points re systemd. I found it interesting and useful, after the usual filtering required to read slashdot:

[URL="http://linux.slashdot.org/story/14/10/30/229221/ask-slashdot-can-you-say-something-nice-about-systemd"]http://linux.slashdot.org/story/14/10/30/229221/ask-slashdot-can-you-say-something-nice-about-systemd
[/URL]

---

### Post by 1clue on 2014-10-31
I'm terrible at spotting spoofs that try to look somewhat real.  Dunno why, but I always take things seriously unless it's on the order of Mars Attacks.

---

### Post by mikodo on 2014-11-01
I saw an update yesterday in Ubuntu 14.10, that offered systemd-shim. I installed it.

Looking in synaptic I have, 

libpam-systemd (208-8ubuntu8) installed.

"systemd is a replacement for sysvinit.  It is dependency-based and
able to read the LSB init script headers in addition to parsing rcN.d
links as hints.".

Is 14.10, the first release to get this?

Oh, I was playing with trying to update to ubuntu-next, yesterday. I had never done that, this early in a release. I was wondering it I could yet. So I tried:
> sudo apt-get install update-manager-core
sudo do-release-upgrade -d
update-manager -d

It was after above, that I was offered to install the systemd-shim. But, having run the above commands, probably had nothing to do with being offered systemd-shim in 14.10.

---

### Post by Dog's_Breakfast on 2014-11-06
> **mikodo said:**
> 
It was after above, that I was offered to install the systemd-shim. But, having run the above commands, probably had nothing to do with being offered systemd-shim in 14.10.

Hi Mikodo, I saw this too. I ran the following to see what systemd stuff is polluting my desktop:

bob@cool:~> dpkg --get-selections | grep systemd
libpam-systemd:amd64				install
libsystemd-daemon0:amd64			install
libsystemd-journal0:amd64			install
libsystemd-login0:amd64				install
systemd						install
systemd-shim					install

I've toyed with the idea of running "apt-get remove systemd" but I'm afraid this might break my setup. I'm really nervous now that systemd is weaseling itself into my computer uninvited, and I'm close to either going back to 14.04, or else jumping ship for PC-BSD.

---

### Post by vasa1 on 2014-11-06
> **1clue said:**
> ...
IMO Gentoo wants an i7 or better. ...
Can you elaborate? Is that because of all the compiling?

---

### Post by 1clue on 2014-11-06
> **vasa1 said:**
> Can you elaborate? Is that because of all the compiling?

Yes.  If you have just a single box, the compiling takes a considerable time even with a quad core.  If you have a bunch of Linux boxes, you can make a compile farm (distcc) and things are much better, then I suppose you could use something smaller.  But if all the boxes are compiling all their code, then you're still looking at a lot of CPU time spent compiling.  If you have an i7 or better, the actual compiling part doesn't take a huge amount of time.

For reference, on a Raspberry Pi a kernel compile takes at least 10 hours if nothing went wrong.  IMO that's not workable.

This is my opinion, not a Gentoo rule.  I'm not very patient and my hardware has other things to do besides compiling their own operating systems.  If I use Gentoo then it means I need things built in some way that normal binary distributions don't build them.  Otherwise I find a distro that is most like what I need and use that.

You guys who contemplate removing systemd from a distro that uses systemd, this is not a simple undertaking.  Find a distro that doesn't use it, or find a source-based distro, find a window manager/desktop that doesn't use it (Gnome uses it and is pretty much irretrievable now) and deal with it t that way.

Statement of fact:  If you have more than one Linux image (either on hardware on on VMs) then you are not required to stick to one distribution.  You can use Ubuntu of any flavor, and Gentoo, and Arch and Redhat and Suse and any other distro you want to try, limited only by your patience and by your available hardware.  There's no requirement of brand loyalty.  You don't get a prize for being all one distro.  I strongly encourage you 'one distro' guys to branch out and experiment, it can only help you understand Linux better and appreciate what makes everything distinct.

---

### Post by JKyleOKC on 2014-11-07
> **1clue said:**
> Statement of fact:  If you have more than one Linux image (either on hardware on on VMs) then you are not required to stick to one distribution.  You can use Ubuntu of any flavor, and Gentoo, and Arch and Redhat and Suse and any other distro you want to try, limited only by your patience and by your available hardware.  There's no requirement of brand loyalty.  You don't get a prize for being all one distro.  I strongly encourage you 'one distro' guys to branch out and experiment, it can only help you understand Linux better and appreciate what makes everything distinct.+1

When I went from Slackware to Mandrake, I was amazed to discover that I no longer needed a printer filter to avoid the stairstep effect. However, KDE on Mandrake 8.1 was unusably slow on my 80-MB of RAM system, so I switched over to IceWM to retain a GUI and get back to response almost as fast as Win95 was giving me.

Then making the switch from Mandrake to Xubuntu back around the time of Fiesty Fawn (2007) forced me to unlearn the SysV configuration rules, abandon RPM packages, and learn how to deal with upstart and Synaptic's *.deb files.

Along the way I got lots of help from the originator of Linux From Scratch, although I never went the full route. He did show me how to configure the powerful FTP server I still employ. And I've tried Mint and Puppy in VMs (neither of which fit my work habits, useful though they are for thousands of other folk -- but trying them was educational in its own right, and I don't regret the effort).

The more different approaches one tries, the more one learns about them all!

---

### Post by Dog's_Breakfast on 2015-05-07
Hello, back from the dead ;

OK, I know this thread hasn't seen any activity in a long time, nor have I posted anything on the Ubuntu forum since last year. But I've discovered something recently that is very relevant to this topic, and some might be interested...

First off, as you all know, Ubuntu has finally switched to systemd in the last release. And I'm a determined opponent of systemd (no, I don't want to debate it again, it's s done deal for me). I still have Ubuntu installed on my hard drive and was using it regularly up until last week, but the new release finally pushed me to make the jump to another distro. I guess that I probably will not be returning to Ubuntu unless Mark Shuttleworth has a change of heart and releases a non-systemd edition (I won't hold my breath).

But which distro? After looking at just about everything out there, I have for now settled on Manjaro-OpenRC, which is based on Arch. Note that regular run-of-the-mill Manjaro has followed Arch in moving to systemd, but thankfully at least someone at Manjaro recognizes the desire of some users to not follow that path. And so they've released a Manjaro version that inits with OpenRC, which as most of you probably know came from the Gentoo folks.

I am finding Manjaro-OpenRC very capable. Boots very fast, comparable to systemd I think. Manjaro boasts a huge software repository, easily rivaling Debian's. Syntax for using it is different - I'm now learning all about "pacman," Manjaro's answer to apt-get.

On the downside, Manjaro is a pretty geeky distro, not for newbies. It's a bit of work to install and configure, and there are a couple of pitfalls which sent me scouring the forums for answers. But now that I've got it set up, Manjaro is humming along nicely and even my non-geeky wife can use it. If somebody is coming directly from the point-and-click world of Windows or Mac, I'd still suggest Ubuntu as a first distro to learn about Linux. But for someone who isn't terrified of using the command line occasionally, Manjaro is quite alright. 

Anyone looking for more info about Manjaro-OpenRC (like where to download it, etc) should take a look at their forum:

[https://forum.manjaro.org/index.php?PHPSESSID=c8ta4vg2oi6j7hagn3o80kmc33&board=50.0](https://forum.manjaro.org/index.php?PHPSESSID=c8ta4vg2oi6j7hagn3o80kmc33&board=50.0)

I'm in the process now of writing an article about my experience, including some tips about installation and configuration. Good chance it will get published on Distrowatch, so look for it there (probably a few weeks from now).

I'll check back on this thread over the next week or so to see if anyone has got some comments, questions, abuse to hurl at me, etc. But after a bit, I'll be gone from this forum. Not that I was very much here anyway.

Best of luck to all of you, even you systemd folks. No animosity, OK? Linux is for fun, so nobody should give themselves high blood pressure over their init system. Hope you all agree.

cheers,
DB

P.S. I'm on the Devuan mailing list, and I'm very interested in what they're doing over there. But still not released, so no way to evaluate it yet. However, for those very committed to the Debian/Ubuntu way of doing things, Devuan is worth watching.

---

### Post by craig10x on 2015-05-07
What's your big problem with systemd?...it works fine...my boot up speed is the same as it was with upstart (maybe even a bit faster) and shut down is even faster....plus it will no doubt improve as the 15.04 updates come in...but even right now, it's fine...seems like a rather silly reason to leave ubuntu (especially when debian is using it too)...You act like it somehow destroyed the whole ubuntu ecosystem or something...if i didn't know, i wouldn't even be able to tell anything has changed....other then as i said, it shuts down faster...sorry, sounds kind of kooky to me...if anything, in the long run....it's probably a nice improvement not detrimental for ubuntu...

---

### Post by vellon on 2015-05-07
As Dog's_Breakfast says, it is probably not worth going over the arguments again, but I will point out that the internet hasn't broken :) since Ubuntu and Debian moved to systemd. The only articles I have seen about it have been news items pointing out the inclusion of systemd in these new releases.

I am still sceptical of Devuan. The announcement was in November, and six months later, no release and no news articles explaining the delays.  Either the team are not finding it as easy to do as they thought, or they are hopeless at communication and managing expectations. Either way, not good signs for a new distro to take over from Debian, as systemd opponents dreamed of.

---

### Post by monkeybrain20122 on 2015-05-07
> **craig10x said:**
> What's your big problem with systemd?...it works fine...my boot up speed is the same as it was with upstart (maybe even a bit faster) and shut down is even faster....plus it will no doubt improve as the 15.04 updates come in...but even right now, it's fine...seems like a rather silly reason to leave ubuntu (especially when debian is using it too)...You act like it somehow destroyed the whole ubuntu ecosystem or something...if i didn't know, i wouldn't even be able to tell anything has changed....other then as i said, it shuts down faster...sorry, sounds kind of kooky to me...if anything, in the long run....it's probably a nice improvement not detrimental for ubuntu...

Not sure if the problem is on the users' end. Most complaints I heard come from system admins.  As for boot speed, yeah it is actually a little faster for 15.04 than 14.04 even it is installed in an external drive, which never happened before (boots faster in external drive than in internal hard drive) In general I am quite impressed with the overall quality of 15.04 (now face the dilemma of whether to replace 14.04 :))

---

### Post by craig10x on 2015-05-07
do it...do it monkeybrain20122....ubuntu 15.04 is calling you...surrender! :mrgreen:
Seriously, yeah it's a terrific release...doesn't really look much different it's the stuff you don't see (underneath)...very smooth and snappy i find as compared to 14.04 and 14.10...and systemd is just fine.....

my own personal plan is to continue upgrading into each new version until ubuntu snappy personal (stable version) is ready for prime time (hopefully by 16.04) then i will finally have my ubuntu "rolling style" release ;)

---

### Post by monkeybrain20122 on 2015-05-07
> **craig10x said:**
> do it...do it monkeybrain20122....ubuntu 15.04 is calling you...surrender! :mrgreen:
Seriously, yeah it's a terrific release...doesn't really look much different it's the stuff you don't see (underneath)...very smooth and snappy i find as compared to 14.04 and 14.10...and systemd is just fine.....

my own personal plan is to continue upgrading into each new version until ubuntu snappy personal (stable version) is ready for prime time (hopefully by 16.04) then i will finally have my ubuntu "rolling style" release ;)

15.04 is great but for the short support cycle so installing 15.04 is actually a gamble on 15.10 (14.10 was really bad, at least on my hardware) My plan is to clone both and switch 15.04 to the internal hard-drive and 14.04 to the external which I can still keep up to date . If 15.10 turns out to be like 14.10 I can just move 14.04 back after 15.04 eof. :) Having a 500g external drive and fsarchiver is enough to pull that off painlessly.

Systemd isn't an issue for the end user I suppose. I dual boot Fedora and has been using it for quite some times (though the implementation is likely somewhat different), speed has never been an issue. It is the under the hood stuffs that people are complaining (too many things depend on it so not modular and one bug may screw a lot of things up etc)

---

### Post by Dog's_Breakfast on 2015-05-07
> **vellon said:**
> As Dog's_Breakfast says, it is probably not worth going over the arguments again, but I will point out that the internet hasn't broken :) since Ubuntu and Debian moved to systemd. The only articles I have seen about it have been news items pointing out the inclusion of systemd in these new releases.

Quite correct Vellon, on all points. The systemd debate has gone on *ad nauseum* with too much bitterness, so I don't want to restart it. And the world didn't end when Ubuntu released 15.04. Most users won't know and don't care what goes on beneath the surface, but some of us do, and especially those who run servers.

> I am still sceptical of Devuan. The announcement was in November, and six months later, no release and no news articles explaining the delays.  Either the team are not finding it as easy to do as they thought, or they are hopeless at communication and managing expectations. Either way, not good signs for a new distro to take over from Debian, as systemd opponents dreamed of.

I'm subscribed to the mailing list, and the consensus of opinion was to follow the Debian philosophy of "release when it's ready." So patience is required. Actually, more patience than I had, as I've moved to Manjaro-OpenRC, at least for now. From what I understand, much of the delay with Devuan was due to their development of vdev, which is an interesting thing. A lot more info about that here:

[https://github.com/jcnelson/vdev](https://github.com/jcnelson/vdev)

It's necessary to all non-systemd distros to find an alternative to udev, which has become part of systemd. Manjaro-OpenRC and Gentoo both use eudev, and there was a lot of discussion about adapting it to Devuan, but there are technical reasons why vdev should be a better long-term solution.

cheers,
DB

---

### Post by craig10x on 2015-05-07
@monkeybrain20122: Sounds like a very good plan for yourself...that way you are fully covered ;)
I'm sure 15.10 will be fine but i understand if you want to go the "cautious" route...

---

### Post by Elfy on 2015-05-07
[IMG]http://i0.kym-cdn.com/photos/images/original/000/176/749/74vOQ.jpg[/IMG]

you know that these circular arguments don't go very far 

thread closed

---

