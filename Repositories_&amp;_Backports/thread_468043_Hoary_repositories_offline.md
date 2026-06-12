---
title: "Hoary repositories offline?"
date: 2007-06-08
forum: Repositories &amp; Backports
---

### Post by PatrickMay16 on 2007-06-08
Hey guys. I know it's had support dropped, but I still have a computer running hoary. Yesterday I tried to run apt-get update and got 404 errors. 

I thought the end of support meant they just wouldn't release new updates. Does it also mean that the repository for hoary is gone, too? Or is this just a tempoary problem?

---

### Post by bapoumba on 2007-06-08
Which repos are you using? The main ubuntu ones ? (You've spotted another thread with the same problem I was about to mention ;))
Packages still look listed [here]("http://packages.ubuntu.com/hoary/").

---

### Post by PatrickMay16 on 2007-06-08
Hi bapoumba,

The repositories I'm using are these ones:

> 

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse



I guess that those are the main ubuntu ones, but I dunno. That's just what it was like after installing hoary from the CD.

---

### Post by bapoumba on 2007-06-09
Hello :)
Please look here:
[http://gb.archive.ubuntu.com/ubuntu/dists/]("http://gb.archive.ubuntu.com/ubuntu/dists/")
Looks like the gb repos dropped hoary??

[http://archive.ubuntu.com/ubuntu/dists/]("http://archive.ubuntu.com/ubuntu/dists/")
And the main ones too? :confused:

Did not find any bug report about this, has anyone seen an announcement?

Edit: are you still using hoary for a special reason? (enjoyed hoary much, BTW).

---

### Post by PatrickMay16 on 2007-06-09
[quote=bapoumba]
Edit: are you still using hoary for a special reason? (enjoyed hoary much, BTW).
[/quote]

Heh heh heh. Part of the reason I'm still using hoary is that it's the first release of Ubuntu I used... back in July/August/September of 2005. So, I use it in memory of old times.
Another reason is that I have a computer that just serves files, which does its job just fine, running hoary... and I'm too lazy to update it to anything newer at the moment.

---

### Post by legume on 2007-06-16
So have these repositories been taken offline forever? I haven't upgraded my mom's computer because I like to keep disruptions there to an absolute minimum, but it's still occasionally useful to install a package. Even if it's old, it's usually still quite usable.

(I also thought that only updates and such would end with the end of support; I sure hope that we aren't losing all access to the repositories!)

Thanks for any info!
Laz

---

### Post by vector on 2007-07-13
Hey all  I have an old laptop. I was told after trying to install brezzy one day and it wouldnt even boot to stick with the old hoary,, The laptop doesnt have the guts to run the latter distros..

Now I have lost all repos because Hoary has been dropped... so what do I do??

attempt an upgrade from disk and loose a working system ?

Laptop is an old Toshiba Satellite 2540XCDT

---

### Post by PatrickMay16 on 2007-07-14
> **vector said:**
> Hey all  I have an old laptop. I was told after trying to install brezzy one day and it wouldnt even boot to stick with the old hoary,, The laptop doesnt have the guts to run the latter distros..

Now I have lost all repos because Hoary has been dropped... so what do I do??

attempt an upgrade from disk and loose a working system ?

Laptop is an old Toshiba Satellite 2540XCDT

You're running breezy, right? You can update that to Dapper, which should run OK on your old laptop. If you're running hoary, I can mail you a breezy CD which you could use to upgrade your system to breezy, and then you can upgrade your breezy system to Dapper. 
Upgrades almost always work fine... unless you've been using Automatix.

---

### Post by baustiech on 2007-07-15
Wow, this is severe lameness.  They actually take down all repositories, remove all documentation, links and historical information, and totally eradicate old versions.

I have several servers at 5.10 breezy, and now I appear to be stuck.

Except for version-by-version upgrade using CDROM.

That's severe lameness.  Not even Red Hat is that lame.



EDIT::

What this erasure does is to make ubuntu seem much less established.  Undermining history undermines credibility.

Also, erasing all the old experiences, complaints, tricks, and other globally-collected information basically sends a blanket message to eveyone on the planet that their comments, ideas, gripes, time taken to share and post, and --ultimately-- their lifetimes don't matter for crap and will be deleted like clockwork every 18 months.

This can only result in a "future shocked" aura around ubuntu, an always-new, always-hyper excited, but never old, never historically based, baseless toy OS.

This will in turn attract a demographic age-group of 'teen OS punks', who generally don't mind playing around on the newest version, rather than attracting old school and serious business users and supporting them with full historical information.

Or am I just old and dumb and completely wrong?

---

### Post by ChrisNiemy on 2007-07-15
I'm wondering why there was no pre-warning or announcement that the repos would be taken offline. :confused:

At least, the repository should remain on only a few mirrors, even not official. But taken it completely away is annoying, though I'm using feisty. I loved hoary. :-) :(

---

### Post by bapoumba on 2007-07-15
Once again, may I suggest someone files a bug report? That all the repos disappear does sound like a bug to me.
(sorry if a bug has already been filed, please provide a link).

---

### Post by PatrickMay16 on 2007-07-15
I would file a bug report, but I have not the capability to do so. If someone else could do it, that would be great. I think Mr Shuttleworth should think this matter over very carefully.

---

### Post by wgrant on 2007-07-16
All obsolete versions are now removed from the main archive (ie. archive.ubuntu.com and its mirrors) not long after they become unsupported. Keep in mind that mirror space is limited, and one architecture of one release is about 12GiB. Assuming four supported architectures over three releases, that's about 144GiB, plus the source packages. That's not insignificant, and there's no point in burdening mirrors with it as nobody should be using unsupported releases any more.

That said, if you *really* want to be using a completely unsupported and likely insecure release, you can replace archive.ubuntu.com with old-releases.ubuntu.com, which still hosts the (no longer updated) repositories for warty, hoary and breezy.

---

### Post by ChrisNiemy on 2007-07-16
Thanks a lot for the link. :-) Now I see that it is also linked on this site here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
> For old releases, see old-releases.ubuntu.com

I guess the URL-Syntax is a litte different in /etc/apt/sources.list it must be old-releases.ubunutu.com/releases and so on. (not sure)

I also want to mention, that newer releases of ubuntu in fact run faster than the prevoius ones. Even on old machines. For machines with less than 256 MB RAM the alternate install CD (or the DVD) is needed - just for the installation.

So if someone has e.g. an old laptop and no kernel problems, feisty will run faster than breezy or hoary.

Maybe consider a minimal installation and then install just the things you need, because the newer releases might seem slower because of more feautures. (Or installing default an deinstalling all that stuff) But im my experience the base system (incl. Gnome) is getting faster and cares more about resources than the older ones.

---

### Post by bapoumba on 2007-07-16
Thanks a lot fujitsu :)
Sorry I did not look at the proper places.

---

### Post by PatrickMay16 on 2007-07-16
> That said, if you really want to be using a completely unsupported and likely insecure release, you can replace archive.ubuntu.com with old-releases.ubuntu.com, which still hosts the (no longer updated) repositories for warty, hoary and breezy.

Oh man YEEEEEAAAAAHHHH!!!!! C'MON!!!!!!!!!!!!!

Thanks! I'm off to install UBUNTU HOARY on some computars.

---

### Post by demibee on 2007-07-17
> **fujitsu said:**
> That said, if you *really* want to be using a completely unsupported and likely insecure release, you can replace archive.ubuntu.com with old-releases.ubuntu.com, which still hosts the (no longer updated) repositories for warty, hoary and breezy.

How long will each release stay on the "old-releases" site?  It'd be nice to know that hoary won't be erased from history.

Also, I'm on dialup, and a full release upgrade is pretty much out of the question.  I stick with software as long as it works for me (although I did recently order feisty from the shipit page)...  Win98, on my other partition, is no longer supported in any way, shape, or form; I can't even download a driver from Microsoft.  I'd hate to see Ubuntu -- the best Linux distro I've tried in many years -- go the same route in that regard, (even if for different reasons than Microsoft's).

db

---

### Post by vector on 2007-07-17
Thanks all 
I gully understand the "it takes up space which costs us money" scenario.
the reason why im dubious about updating the laptop was that i once tried just that...the one after hoary..It just died wouldnt intsall at all and was told, on this site!! to not attempt such things on such lame computers.
I know some have had things run well on the the toshiba satelites but I no smarty popcorn and settled for something that at least worked if not very very slow.


However! It seems i have secured another laptop..old but not as old as the last one :)

so I intend on putting ubuntu on the newy and then that will allow me to play around with the oldie without fear of loosing anything.

Yeah!!

---

### Post by demibee on 2007-07-17
> **ChrisNiemy said:**
> I guess the URL-Syntax is a litte different in /etc/apt/sources.list it must be old-releases.ubunutu.com/releases and so on. (not sure)

Has anyone out there been able to access old-releases.ubuntu.com/releases??  I'm able to view Google's cached version of the site to see what's there, but the site itself hasn't responded at all in the past day.

db

---

### Post by agurk on 2007-07-17
works for me

---

### Post by wgrant on 2007-07-19
> **demibee said:**
> How long will each release stay on the "old-releases" site?  It'd be nice to know that hoary won't be erased from history.

I don't see any reason why they wouldn't be kept around eternally. It's always nice to be able to look back at the old releases and see how Ubuntu has evolved.

---

### Post by agurk on 2007-07-19
GPL v2 paragraph 3b stipulates three years, the same goes for GPL v3.

---

