---
title: "Firefox upgrading issues"
date: 2005-05-30
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-05-30
I was kinda lazy and didn't go directly to 1.04 of ff.  I was about to today and I notice there is an upgrade to pkg mozilla-firefox but also a new pkg simply entitled firefox has also appeared.

If I select mozilla-firefox for upgrade, it flags some stuff I wouldn't necessarily expect for a mozilla upgrade like gcc-4.0-base but without flagging gcc-4.0.  First off, I wasn't planning on going to 4.0 of gcc for a long time but I also don't get why one would need the base gcc pkg of a newer version.

Also, if I instead flag simply firefox for installation it says mozilla-firefox is to be removed.  I understand this happens with transitional pkgs, but I remember way back when going through some headaches in deb sid when phoenix switched to firefox.  Instead of treating firefox as an upgrade to phoenix, it was treated as a seperate new pkg and had a different home cfg dir etc, which caused some headaches of manually moving over profiles etc.  Later the debian maintainer corrected this and treated it as an upgrade.  This looks like a somewhat similar situation so just wanted to post here first before I proceed.  Btw, it also wants to install libcairo and and libpixman.  I didn't think 1.04 of ff was making use of those already.

---

### Post by McQuaid on 2005-05-31
Am I the only one seeing this?  First off, I think it was in error having pkgs firefox and mozilla-firefox, as it can cause profile issues as noted above.  And why would firefox flag gcc4.0-base as a dep?

---

### Post by ow50 on 2005-05-31
[QUOTE=McQuaid]Am I the only one seeing this?  First off, I think it was in error having pkgs firefox and mozilla-firefox, as it can cause profile issues as noted above.  And why would firefox flag gcc4.0-base as a dep?[/QUOTE]
Despite the name change, the files are still mostly installed to same old locations (e.g. /usr/lib/mozilla-firefox). It shouldn't cause profile issues. The purpose of the mozilla-* dummy transition packages to is to provide a smooth upgrade and avoid breaking mozilla-* dependent apps. As for the compiler, it's the way of the future. This firefox has been backported from breezy and once breezy is ready version 4 compilers will be the ones primarily used.

Did you actually install and encounter problems or are you just being suspicious? Because we haven't gotten much feedback on the new firefox packages and we'll of course fix any possible problems.

---

### Post by AndyAWS on 2005-06-01
McQuaid: If you have concerns then wait until testing is complete and the packages come out of 'staging' and hit the ubp main.

If you install anything that is still in staging then you take a chance of encountering problems...on the other hand this is how things get tested... :wink:

---

### Post by Mez on 2005-06-01
Ubunut decided to rename the package from mozilla-firefox to firefox in breezy.

The mozilla-forefox package is jhut a dummy transitional package.

I'm using the shineh new GCC4 package without any (noticable) problems

---

### Post by dodongo on 2005-06-01
All the above is right-on, as far as I can tell.  I've had zero problems with the migration to 1.04.  Apt-get should let you know that the old mozilla-firefox packages will be uninstalled, but that doesn't matter, because package 'firefox' is basically a drop-in replacement with bug fixes.  And GCC 4.0-compiled binaries :)

On a related note, the new FF alpha (code-named Deer Park) is not working so well for me...  and you think loading "staging" packages is risky!

---

### Post by jdong on 2005-06-01
This particular backport is from Breezy. As others have mentioned, the package has changed names, presumably because of Mozilla trademark restrictions.

In addition, it's now compiled with GCC4, because the Breezy firefox has been patched specifically for GCC4. As a result, it'll pull in some extra GCC4 libraries, which are pretty harmless.


This backport has worked wonderfully for me, and it's been a couple of weeks that I've used it.

---

### Post by kcy29581 on 2005-07-14
I'm confused.... I have backports enabled and I know it works, as packages have just been updated from backports.

However it kept back mozilla-firefox. Now my confusion is this: If I now reload the repos in Synaptic, and ask Synaptic to "Mark Available Upgrades" it says it has none.
If I now go to the "mozilla-firefox" package in Synaptic it has a green box with a yellow star which obviously means "I have an update!". I right click on this and what do you know, the little bugger is right, it has an update!

So why doesn't the "Mark Available Updates" catch this? I understand there is a transistion going on with firefox's package name, but does this mean that during EVERY name transition we'll have to worry about stuff like this? What if one doesn't actively search the forums for this kind of stuff?

I have Synaptic to use the latest versions in Preferences so I'm even more confused. I would appreciate a full answer as this is kind of serious if you want to keep up to date.

Thanks all.

---

### Post by jdong on 2005-07-14
Make sure you're using Smart Upgrades ("apt-get dist-upgrade"), which pick up on transitional packages.

Try marking "mozilla-firefox" for installation by hand. Note that mozilla-firefox is just a dummy package -- firefox holds the actual data.

---

### Post by kcy29581 on 2005-07-15
thanks for the reply jdong. I should've thought of trying dist-upgrade! :-\"

About dist-upgrade, I never actually got this answered out of a Debian guy for obvious reasons (RTFM...), is it ok to always use is rather than the normal upgrade?

Once again thanks! (and if you're an ex-Debian guy, you are unique!)

---

### Post by jdong on 2005-07-15
[QUOTE=kcy29581]
About dist-upgrade, I never actually got this answered out of a Debian guy for obvious reasons (RTFM...), is it ok to always use is rather than the normal upgrade?
[/quote]
Sure. I use it all the time. I can't remember the last time I ran a normal upgrade! The only time it could get you into trouble is in development versions, where a packaging BUG could make dist-upgrade go beserk and start removing hundreds of packages to update one. In all cases, APT/Synaptic tells you exactly what it's adding, removing, and upgrading. Look it over before blindly applying the changes, and you'll be fine.

> 
Once again thanks! (and if you're an ex-Debian guy, you are unique!)
[/quote]
Yeah, and would you believe I'm an ex-Gentoo, too ;) ?

---

### Post by kcy29581 on 2005-07-15
[QUOTE=jdong]Yeah, and would you believe I'm an ex-Gentoo, too ;) ?[/QUOTE] that I would believe actually! I still use Gentoo as well. I love the forums over there and here. Best of both worlds!:-P

---

### Post by aslagle on 2005-07-15
I've got a new Hoary install, and I've put in the backports, but when I try to upgrade firefox, it gives me this:

[I][INDENT]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc](http://us.archive.ubuntu.com/ubuntu/pool/main/libc) /libcairo/libcairo1_0.3.0-1_i386.deb MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/INDENT]
[/I]

So...what's wrong, and how do I fix it?

-Adam

---

### Post by jdong on 2005-07-15
search the board. In short, use archive.ubuntu.com, the us. mirrors are weird.

---

