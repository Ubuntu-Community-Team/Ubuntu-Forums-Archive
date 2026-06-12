---
title: "Old Release is better than the New One?"
date: 2006-09-26
forum: The Cafe
---

### Post by kenweill on 2006-09-26
I have just finished attending the seminar, RH133 - Red Hat Linux System Administration. 

And our instructor said, "Never use a new release of linux distribution." He want us to use an older release instead of using the new release. Example, using Fedora Core 2 or 3, instead of the latest Fedora Core 5, or 6. He was saying that new releases/versions contains bugs. An updated Older Linux Distro is far more stable than the latest/new release.

How about here in Ubuntu? Is this true?
Does Breezy, or lets say Dapper, even if its an old release as long as its updated/up-to-date, is far more stable than the new release? (eg. Edgy)

Everytime a new Ubuntu is released, i always use the latest release. Now, i dont know if i would go Edgy, or stay with Dapper or with Breezy. Up to date Dapper/Breezy.

---

### Post by Perfect Storm on 2006-09-26
Well...every versions have their own set of bugs, so I hardly see what you teachers point is. Well if he want to use something ultra stable, use Debian stable.

---

### Post by kenweill on 2006-09-26
Hes pointing to use the older(stable) release than the new(latest) release. 

Btw, whats the difference between using Dapper for 3 years and using Edgy for 18 months? Could Dapper be even better than Edgy after 3 years?

---

### Post by Perfect Storm on 2006-09-26
Hardly to say, depends how well the devs will do ;)

Personally I would say none, but again My systems have been rock stable since the early days of warty beta and up. Not that I have encountered bugs but nothing that makes my systems unstable.

---

### Post by Sushi on 2006-09-26
Simple, really: If it aint broke, don't fix it. If you have a server (for example), and it does what it needs to do, it there any reason to upgrade to a newer version?

---

### Post by prizrak on 2006-09-26
I agree with Sushi here, there is hardly any reason to upgrade a server if there is nothing wrong with it. Maintained older releases will be better as far as stability and security goes as more bugs have been taken care of. Newer releases come with new features that haven't been as thoroughly tested in the real world. 

For your home computer you can use an older release if you don't see any improvements you care about in the newer one. For instance the machine I'm on right now is very unlikely to be switched to Edgy as it can't take advantage of alot of the stuff in it. If you want the latest release you can do that too, after all if it is a release it has been tested and deemed stable by the developers so you won't have any real issues with it.

---

### Post by ago on 2006-09-26
> **kenweill said:**
> How about here in Ubuntu? Is this true?

It is simple really: for home use get the latest and fanciest. For production server or enterprise use, get a "stable" release. 

Each distribution handles the "stable" release differently. For fedora you use old version (or better RHEL), debian has an explicit "stable" release, ubuntu has LTS. 

It is important to understand that "stability" has a double meaning:  

1) are the packages going to crash/be insecure?
2) are the packages going to change/be upgraded often? 

Contrary to what people believe often (2) is more relevant than (1).

Even on "non-stable" distributions the stability (as in 1) is more than adequate for most users, and far better than other OSes. On a server you may have mission critical applications and cannot take any chances, so even if you can improve stability (as in 1) by 0.1% it is worth it.

As for (2), on a server, package upgrades are highly undesired, particularly the ones that simply introduce new features, but for home use they are quite welcome. Do you do want to use the new features of your favourite apps? I think so. Then you have to install the latest version of your favourite distro (systematic use of backports is not really worth it). 

Hence the simple rule of thumb above.

---

