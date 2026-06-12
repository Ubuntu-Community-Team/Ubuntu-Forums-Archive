---
title: "[SOLVED] Software update policy on Ububtu LTS versions"
date: 2007-07-11
forum: Repositories &amp; Backports
---

### Post by Skilly on 2007-07-11
Due to the fact that I use my notebook daily while performing a Business Analyst role at my only client, I had elected to keep my notebook on Dapper. My reason for doing so is that I thought that the Long Term Support offered a level of stability while still providing access to the latest versions of installed software. 

I have since come to realise that I don't neccesarily understand the meaning of LTS.

[LIST=1]
[*]While version 1.6.3 of pgadmin is out, only version 1.2.2 (which has a specific bug that effects me hugely) is available via the Dapper repositories. 
[*]While OpenOffice has developed more recent versions, only version 2.0.2 is available via Dapper repositories meaning that it is not possible to configure OpenOffice to view the MS Office docs that have been saved in the docx format (an important issue for me, regardless of whether this is a trivial issue for others or not).
[/LIST]
I gather therefore that LTS doesn't mean that I will get the latest versions of available software? If so, what benefit DOES LTS give me? If having the latest bug fixes and up-to-date features is important to me, does this mean that I have to do a dist-upgrade every six months whenever a new version of Ubuntu is released?

---

### Post by Nekiruhs on 2007-07-11
> **Skilly said:**
> Due to the fact that I use my notebook daily while performing a Business Analyst role at my only client, I had elected to keep my notebook on Dapper. My reason for doing so is that I thought that the Long Term Support offered a level of stability while still providing access to the latest versions of installed software. 

I have since come to realise that I don't neccesarily understand the meaning of LTS.

[LIST=1]
[*]While version 1.6.3 of pgadmin is out, only version 1.2.2 (which has a specific bug that effects me hugely) is available via the Dapper repositories. 
[*]While OpenOffice has developed more recent versions, only version 2.0.2 is available via Dapper repositories meaning that it is not possible to configure OpenOffice to view the MS Office docs that have been saved in the docx format (an important issue for me, regardless of whether this is a trivial issue for others or not).
[/LIST]
I gather therefore that LTS doesn't mean that I will get the latest versions of available software? If so, what benefit DOES LTS give me? If having the latest bug fixes and up-to-date features is important to me, does this mean that I have to do a dist-upgrade every six months whenever a new version of Ubuntu is released?
I haven't seen any benefits to Dapper. All the advances are going into the non-LTS releases. Feisty has the Desktop Effects, network manager, easy install codecs, and restricted drivers manager. Feisty really makes it easy. Fiesty is also very stable. You may have to  upgrade every 6 months.  Of cousre Gutsy + 1 is going to be an LTS release

---

### Post by 3rdalbum on 2007-07-12
> **Skilly said:**
> 
I gather therefore that LTS doesn't mean that I will get the latest versions of available software? If so, what benefit DOES LTS give me? If having the latest bug fixes and up-to-date features is important to me, does this mean that I have to do a dist-upgrade every six months whenever a new version of Ubuntu is released?

In a word: Yes.

In multiple words: You can still compile new versions of essential software yourself, if they support the versions of the essential system software included with Ubuntu (i.e. the kernel, Xorg, glibc etc).

By the way, Openoffice.org does not yet have support for .docx. Novell's OOo has a translation plugin preinstalled, but Novell is not distributing it to anyone who isn't a customer of theirs.

I am starting a new project called LTS Backports, which will probably backport OOo as soon as it has an Office Open XML translator.

---

### Post by Contrast on 2007-07-13
I'm pretty much in agreement with Nekiruhs. It's worth mentioning that upgrading only takes around 1-2 hours for most people, and that's upgrading *all the software on your system*.

---

### Post by vanadium on 2007-07-13
The idea of the LTS version, in my understanding, is that patches, bug fixes and and safety fixes will be continued to be provided for a longer period than for the other versions. As for any Ubuntu version, this does not involve major application upgrades. Application upgrades means upgrading your distribution (eg from Dapper to Feisty).

Obviously, you can upgrade and install yourself, but then you are loosing the convenience of applications being installed and configured for you by your distribution and, more importantly, system stability is not anymore guaranteed. Moreover, you will increasingly need to have good technical knowledge because increasingly, you will need to solve compatibility and dependency issues.

---

### Post by baustiech on 2007-07-15
What happened to all the information about Breezy 5.10 ??

The repositories are gone.  The forums are gone.  It's almost like 5.10 never existed.

I think this "policy" is faulty.

There should be an historical archive of the old repositories, messages and information, even if it's not "supported" any more.  Erasing information gathered and shared (and sufgfered) byt he group undermines Ubuntu's credibility as anything dependable over the long term.  Even Red Hat still has information about its oldest releases.

There are _many_ of us who want stability and do not want to jump from version to version.  LTS is a good idea, but some aspects of it (keeping the old information online, for example) should apply to all versions of Ubuntu.  Unfortunately, for whatever reason, that is not presently the case.

---

### Post by az on 2007-07-15
> **Skilly said:**
> 
I gather therefore that LTS doesn't mean that I will get the latest versions of available software? If so, what benefit DOES LTS give me? If having the latest bug fixes and up-to-date features is important to me, does this mean that I have to do a dist-upgrade every six months whenever a new version of Ubuntu is released?

You actually get a lot of bug fixes in the LST release, if they are in software from main.  The advantage is that newly released software can contain more bugs.  Software that was released a long time ago has been more thoroughly bug-tested and fixed.

When a bug fix is available to a package and it can be brought to the version of the package in LST, then LST gets the bug-fix as well.

That being said, there are two ways to look at it.

If you absolutely need software that is more current than what is in Dapper, you should dist-upgrade to the latest stable release.  If you absolutely need your software to work and are not interested in the newest version of apps and you want a clean upgrade-experience from one LST release to the next, stick with Dapper.  

If you are in between, you are faced with the same problem that every single computer owner/IT manager has to face every single day regardless of operating system.

---

### Post by Skilly on 2007-07-15
Many thanks to all for your comments. I guess the benefit of LTS is that you do continue to get bugfixes even if you don't get new versions of the software, as az points out.

For your info, sometimes it helps to contact the product developers directly. I dropped a note to postgresql and Raphaël Enrici has subsequently made version 1.6.3 available for Dapper (refer [http://ftp7.us.postgresql.org/pub/postgresql/pgadmin3/release/ubuntu]("http://ftp7.us.postgresql.org/pub/postgresql/pgadmin3/release/ubuntu")). **I've yet to see the vendors of well known commercial competitors match that kind of service!**

---

### Post by Skilly on 2007-07-22
I was re-reading this thread and noted a comment made by AZ that I would like to clarify, namely "*... and you want a clean upgrade-experience from one LST release to the next ...*".

I've been told in no uncertain terms by many, including my local Linux User Group, that I should not bypass an Ubuntu version when doing a dist-upgrade, regardless of whether I am upgrading from a LTS version to another LTS version. Am I correctly informed? A clean upgrade from Dapper to Gutsy will be a real feature, in my book!

---

### Post by mbp on 2007-08-01
Skilly,

It's correct that you should upgrade one step at a time through Ubuntu releases.  It's not physically impossible to jump forward, but this is not a supported or tested operation and you'd want to be pretty confident in fixing things by hand if it breaks.

However, the Ubuntu developers have also promised that you'll be able to upgrade from one LTS release to the next.  I understand Gutsy won't be an LTS release but Gutsy+1 will be.  The same rule applies: you can go from one LTS release to the next, but you can't skip them.  You wouldn't want to since Dapper will probably be out of support by the time the third LTS comes out.

So in summary, the supported upgrades will be: Gutsy->Gutsy+1, and Dapper->Gutsy+1.  You can and should move LTS machines direct from Dapper to Gutsy+1 when it comes out.

---

### Post by UbuWu on 2007-08-02
> **baustiech said:**
> What happened to all the information about Breezy 5.10 ??

The repositories are gone.  The forums are gone.  It's almost like 5.10 never existed.

I think this "policy" is faulty.

There should be an historical archive of the old repositories, messages and information, even if it's not "supported" any more.  Erasing information gathered and shared (and sufgfered) byt he group undermines Ubuntu's credibility as anything dependable over the long term.  Even Red Hat still has information about its oldest releases.


No problem. Here you are: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by Skilly on 2007-08-02
> So in summary, the supported upgrades will be: Gutsy->Gutsy+1, and Dapper->Gutsy+1

Thanks mbp - that's great news! I was expecting to re-install my machine from scratch!

---

### Post by Gremlinzzz on 2007-08-03
why not just take what you need from the newest repositories and add them too your system.I all ready have gutsy kernel i'm using feisty.the kernel runs great 
went from 2.6.20-15 to 2.6.20-16 which i removed both to 2.6.22-9-generic which works a lot better. why cant it be a feisty update ? 2.6.20.16 is buggy.
:guitar:

---

### Post by mbp on 2007-08-06
> **Gremlinzzz said:**
> why not just take what you need from the newest repositories and add them too your system.

Because those packages are not tested to work together.  You're certainly welcome to try, but if they won't install or don't work don't be surprised.  Specific backports are a better bet.

As a case in point at various times in Debian there have been upgrades to libc and the kernel that need to be done together...

---

### Post by ThrobbingBrain66 on 2007-08-06
> **Gremlinzzz said:**
> why not just take what you need from the newest repositories and add them too your system.I all ready have gutsy kernel i'm using feisty.the kernel runs great 
went from 2.6.20-15 to 2.6.20-16 which i removed both to 2.6.22-9-generic which works a lot better. why cant it be a feisty update ? 2.6.20.16 is buggy.
:guitar:

You're just asking for trouble if you do that.  Dependency problems, version mismatches and general unpleasantness are almost guaranteed.  Just don't do it....disaster is almost sure to follow.

---

### Post by yopnono on 2007-08-08
You can also use to backport
[https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu)

---

### Post by igoddard on 2007-08-26
> **Contrast said:**
> I'm pretty much in agreement with Nekiruhs. It's worth mentioning that upgrading only takes around 1-2 hours for most people, and that's upgrading *all the software on your system*.

Upgrading's a great idea provided you prefer what's new to what works.  My experience of upgrades is that they break things faster than updates.

Ian

---

