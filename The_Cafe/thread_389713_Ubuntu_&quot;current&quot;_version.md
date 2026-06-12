---
title: "Ubuntu &quot;current&quot; version?"
date: 2007-03-21
forum: The Cafe
---

### Post by mahy on 2007-03-21
Hello everybody!

As you probably know, there are many distros out there that provide some form of "current" version to their users. Of all i tried, Gentoo and Slackware did this. E.g. if you set the repositories to slackware-current, you can have your system kept incrementally up-to-date as long as you wish. My NetBSD friends also report the same option. Why is no such thing possible in Ubuntu? Can anybody explain this to me? (Please don't tell me it's because of Debian...) THX

---

### Post by Mr. C. on 2007-03-21
Is this a question about naming schemes, or about certain packages being older than perhaps those on other distros?

The system will keep itself up to date with what Ubuntu has qualified.

What is it that you're after that you don't have ?

MrC

---

### Post by mahy on 2007-03-21
Well, i've got Edgy now. As soon as Feisty comes out, Edgy's development will come to sort of a stall, only receiving security updates and a handful of backported packages. Similarly, Dapper users have to use Firefox 1.5. Let's say i'd like to install Feisty's kernel and ALSA drivers, but i'm not up for a total (and risky) upgrade. What should i do?

---

### Post by mostwanted on 2007-03-21
There is. Instead of "edgy" or "feisty" set your repositories list to update from "grumpy".

---

### Post by fuscia on 2007-03-21
> **mahy said:**
> Well, i've got Edgy now. As soon as Feisty comes out, Edgy's development will come to sort of a stall, only receiving security updates and a handful of backported packages. Similarly, Dapper users have to use Firefox 1.5. Let's say i'd like to install Feisty's kernel and ALSA drivers, but i'm not up for a total (and risky) upgrade. What should i do?

i'm guessing it's not a good idea to use a feisty source list on either dapper, or edgy (is that true?). does one update source lists in slackware and gentoo, or netbsd?

---

### Post by depele on 2007-03-21
> **mostwanted said:**
> update from "grumpy".

Can you explain that pleas?

I don't know what that is or how it works. 
Is it something like the LTS version of ubunu? 

grtz

---

### Post by mahy on 2007-03-21
> **fuscia said:**
> i'm guessing it's not a good idea to use a feisty source list on either dapper, or edgy (is that true?). does one update source lists in slackware and gentoo, or netbsd?

I'm no expert in this field. However, the fact is that many people with Gentoo or NetBSD don't have to reinstall their system for ages, coz it constantly keeps itself up-to-date, no maintenance necessary. Ubuntu is far cry from that...

---

### Post by mahy on 2007-03-21
> **depele said:**
> Can you explain that pleas?

I don't know what that is or how it works. 
Is it something like the LTS version of ubunu? 

grtz

Grumpy is a bleeding-edge branch of Ubuntu targeted at developers. Not exactly my cup of tea. What i'd like to have is current AND stable branch.

---

### Post by depele on 2007-03-21
hmmmz...

May be I will have to go to Gentoo. Because of the install and never reinstall unless you buy a new computer. 

But gentoo is so much compiling for the same effect as ubuntu. Doh.

And what about debian?  Is debian usable as a stable desktop environment? 
For servers it is the best but for desk or laptop's?

grtzz

---

### Post by mahy on 2007-03-21
> **depele said:**
> hmmmz...

May be I will have to go to Gentoo. Because of the install and never reinstall unless you buy a new computer. 

But gentoo is so much compiling for the same effect as ubuntu. Doh.

And what about debian?  Is debian usable as a stable desktop environment? 
For servers it is the best but for desk or laptop's?

grtzz

Yeah, Gentoo's all about compiling. You may wanna try Arch Linux instead. I wouldn't recommend Debian if you're not satisfied with Ubuntu. Definitely not. It is stable, but nowhere near current.

---

### Post by blueturtl on 2007-03-21
> As you probably know, there are many distros out there that provide some form of "current" version to their users. Of all i tried, Gentoo and Slackware did this. E.g. if you set the repositories to slackware-current, you can have your system kept incrementally up-to-date as long as you wish. My NetBSD friends also report the same option. Why is no such thing possible in Ubuntu? Can anybody explain this to me? (Please don't tell me it's because of Debian...) THX

Well... it sort of works like that with Ubuntu automatically. You have the latest version of the system on the hard-disk and it is being updated through the repositories. Just think of the latest stable repos as "gentoo current" or what ever. When a new stable release is out, you can upgrade your running system by switching the repository addresses to point to the new stable distribution and doing a sudo apt-get dist updgrade or something of the sort (I personally prefer to clean-install a new system every time).

If you want bleeding edge, you can do the former before the new system's release, but that can lead to things breaking, since the latest system (currently Feisty) is still in development.

---

### Post by darkhatter on 2007-03-21
I've used slackware, and ubuntu doesn't have anything like that, you can go to the Feisty files and copy the kernel out of there, ubuntu really doesn't have a "current" version kind of out of luck

---

### Post by bonzodog on 2007-03-21
You can always stay on the bleeding edge of devel by simply changing your sources list to the current development version of Ubuntu - in this case, Feisty. As the cycle goes in six month spurts, so do the release versions of various bits of software. Want the latest piece of software?

Either get it backported, or run the devel unstable branch of Ubuntu.

---

### Post by prizrak on 2007-03-21
> **blueturtl said:**
> Well... it sort of works like that with Ubuntu automatically. You have the latest version of the system on the hard-disk and it is being updated through the repositories. Just think of the latest stable repos as "gentoo current" or what ever. When a new stable release is out, you can upgrade your running system by switching the repository addresses to point to the new stable distribution and doing a sudo apt-get dist updgrade or something of the sort (I personally prefer to clean-install a new system every time).

If you want bleeding edge, you can do the former before the new system's release, but that can lead to things breaking, since the latest system (currently Feisty) is still in development.

You don't need to edit your sources.list anymore. Only need to do it if you want to upgrade a final to an alpha/beta. 

It's basically a decision made by Ubuntu devs. They decided to provide a new stable version every 6 months. Each stable version is "frozen" that is you only get security updates and nothing more. New software/features gets introduced every 6 months (generally nothing new is introduced after 4 month of development). I would assume that makes it a bit easier on testing and bug reporting as all packages are the same and there is no guessing what was held back and not upgraded for some reason.

---

### Post by macogw on 2007-03-21
As soon as it was released, Edgy ceased development and turned into security-updates only (with the exception of a few kernel updates).  That status will remain with it for a year after Feisty's release.  On the day Feisty is released, your update notifier will inform you and if you click the "upgrade" button, it will change your sources.list and update everything.  No fresh installs are required.  And Feisty is shaping up very nicely.  The laptop users will be very pleased with the new (as in, automated) way of handling wireless and wireless drivers.

---

### Post by bruce89 on 2007-03-21
> **mahy said:**
> Grumpy is a bleeding-edge branch of Ubuntu targeted at developers. Not exactly my cup of tea. What i'd like to have is current AND stable branch.

Grumpy doesn't exist yet, it's just a theory.

---

### Post by Adamant1988 on 2007-03-21
> **depele said:**
> hmmmz...

May be I will have to go to Gentoo. Because of the install and never reinstall unless you buy a new computer. 

But gentoo is so much compiling for the same effect as ubuntu. Doh.

And what about debian?  Is debian usable as a stable desktop environment? 
For servers it is the best but for desk or laptop's?

grtzz

Oh I see what you're saying.  Perhaps you should try Arch Linux or Foresight linux as I believe that both of those use rolling releases.

---

