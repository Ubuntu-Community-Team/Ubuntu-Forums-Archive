---
title: "php 5.2.4?"
date: 2007-10-29
forum: Server Platforms
---

### Post by simon_w on 2007-10-29
Hi folks,

I can't find any mention of this anywhere, which makes me think it may be a stupid question in which case I apologise, but does anyone know if/when php 5.2.4 will be available in the repositories?

My hosts are chewing my ear about upgrading, given the exposed vulnerabilities with 5.2.3 (i'm pretty confident none of my code is vulnerable, but they won't take my word for it!), and given that php 5.2.4 has been out for coming up 2 months.

Any one have any info, or perhaps can point me at a good tutorial on compiling it from source (i'm pretty inexperienced in this, but ready to get stuck in and learn!).

Thanks for reading!

Simon
:)

p.s. I'm using gutsy...

---

### Post by simon_w on 2007-11-02
:confused:

I'm intrigued - am I the only person who cares about this?

If so, is there anyone who would take the time to explain to me why?

I guess I'll get on with compiling it from source...

Apologies if I've missed the point somewhere... :?

Simon

---

### Post by twistedtwig on 2007-11-02
cant say I know but GL

---

### Post by Wallace on 2007-11-02
Has PHP ever been upgraded within a Ubuntu release? I'm sure I've only seen the PHP version change with Ubuntu releases, which would suggest it'll come with Hardy Heron (8.0x). A backported version might be available before then though.

---

### Post by simon_w on 2007-11-02
> Has PHP ever been upgraded within a Ubuntu release? I'm sure I've only seen the PHP version change with Ubuntu releases, which would suggest it'll come with Hardy Heron (8.0x). A backported version might be available before then though.

I see, I see.  That makes some sense, I suppose.  So, in the event of a security release like php 5.2.4, everyone scrambles to compile their own apache modules / cgi extensions.

I'm a little surprised, I admit (showing my greenness), but at least I now have an answer I can understand - thank you Wallace!  I was going mental for a short while there.

I've managed to compile it myself successfully on a spare old machine that I set up for the purpose - guess I'll have to be brave and do it for real now!

Thanks again,

Simon

---

### Post by az on 2007-11-02
> **Wallace said:**
> Has PHP ever been upgraded within a Ubuntu release? I'm sure I've only seen the PHP version change with Ubuntu releases, which would suggest it'll come with Hardy Heron (8.0x). A backported version might be available before then though.

The version wouldn't get increased, but the version in the repos gets patched.  That's what the security-updates repo is for.

---

### Post by simon_w on 2007-11-02
Hi az,

Thanks for your response, but I'm confused again now!

> The version wouldn't get increased, but the version in the repos gets patched. That's what the security-updates repo is for.

Does this mean that I can expect updated php binaries to appear in the repos at some stage?  or does it mean that they're already there, I just can't see for looking?  or neither?  :confused:

Please excuse my ignorance - your help is greatly appreciated, I assure you!

Thanks,

Simon
:)

---

### Post by az on 2007-11-02
> **simon_w said:**
> Hi az,

Thanks for your response, but I'm confused again now!



Does this mean that I can expect updated php binaries to appear in the repos at some stage?  or does it mean that they're already there, I just can't see for looking?  or neither?  :confused:

Please excuse my ignorance - your help is greatly appreciated, I assure you!

Thanks,

Simon
:)

A new version should appear in the gutsy-security repo.  It has not yet.

---

### Post by deuce868 on 2007-11-02
Welcoem to ubuntu on the server. First, as you've found out, packages are updated on new releases. You'll not get the update you're looking for until the Hardy release. 

Now when it comes to packages, the best thing to do is to get yourself aquainted with launchpad. It's the place where all the details of these packages are handled. 

For instance, let's check out the PHP5 package in launchpad. 
[https://launchpad.net/ubuntu/+source/php5](https://launchpad.net/ubuntu/+source/php5)

Notice down the page you can see recent activity. You can see which versions of the packages were updated and for what reasons, including bug/security issues, You can also view existing bug reports and the status of them. I would start there and see if you can reassure your hosts that the security issue isn't an issue. 

If you really need software that is only two months old, it's going to be time to deal with compiling your own binary. It's not horrible with PHP, but I'll take the packages. 

HTH

---

### Post by Brazen on 2007-11-02
If you stick with the LTS release of Ubuntu, then any security vulnerabilities will get patched.  My guess is though, you are using Feisty, which is a horrible idea on a production server, and you will probably be out of luck on getting a security exploit patched.  Some get patched in the non-LTS releases, but from what I've seen the devs are not nearly as dedicated to it as to patching Dapper (and for very legitimate reasons).

---

### Post by ruibernardo on 2007-11-02
Packages get updates between releases, as az said. Feisty was launched in April, and php5 [got updates since then]("http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.1-0ubuntu1.4/changelog").

Even if Launchpad doesn't show anything, there is upstream, and upstream is Debian and php. Debian is already taking care of this, as you can see it [here]("http://packages.debian.org/changelogs/pool/main/p/php5/php5_5.2.3-1+lenny1/changelog"). Sooner or later, Ubuntu will have this updates too, on the security repository, as az said on his post.

---

### Post by simon_w on 2007-11-03
Thanks to everyone for taking the time to educate me... :smile:  The reference to launchpad will certainly be helpful too.

I appreciate the entirely legitimate concept of LTS versions.  I suppose I just figured that a security release of a package as important as php would have made it into the repositories for all supported releases in ten weeks or so.

When I made the choice to go with a later release than 6.06 I realised I may be laying some problems in store for myself, but I needed (wanted?) some of the more recent features.  Besides, I reckon I could reasonably describe myself as 'feisty' or 'gutsy', but I could never pass myself off as 'dapper', I'm afraid!

I'm (as is obvious) fairly new to Ubuntu/Linux and to looking after my own server, but I'm far from useless in general.  I've managed to compile php successfully on a test platform, and I'm ready to do it again, now that I know there isn't an easier way I've overlooked. 

Thanks again to all - I appreciate your time!

Cheers,

Simon

---

### Post by oggiestirfry on 2007-11-13
Simon,
Were you successful?  I need to upgrade to PHP 5.2.4 or higher also (on edgy) but I've never compiled from source before as there's always been an up-to-date package for my update needs.  I guess I'll try it out on a test machine before taking the plunge in production.  Not looking forward to it :-(

-Shaun

---

