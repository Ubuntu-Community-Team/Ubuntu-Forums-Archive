---
title: "[gnome shell] multiple crashes when closing window"
date: 2013-01-14
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-01-14
hi,

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1094571](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1094571)

does not seem to get a lot of comments.
By the way this bug is the only one for me which makes me crazy.

Anyone has investigated more ? Does a workaround exist, before an official one ?

Thanks !

---

### Post by mc4man on 2013-01-14
I've several 'workarounds' for you, ranging from 100% to 99% to looking good effective.

100% - stop using ubuntu's gnome-shell till fixed, inadvertently or otherwise. (likely the former, this is the workaround I've chosen

99% - replace the login gnome-shell with one running in a terminal, works  quite well though has obvious slight downside. Can be done thru a delayed start up script

looking good - use Fedora 18 - I think it's using 3.6.2 or .3, no sign of this on a live session though a live session isn't conclusive

Otherwise keep updating, maybe it'll go away..

---

### Post by mc4man on 2013-01-16
It's possible that the GS issue is the same as seen here - 
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342)
(I believe these issues would be only or more likely seen on 64 bit

---

### Post by ft_ on 2013-01-16
This relation between Pulseaudio and closing windows exceeds by far my field of understanding. Was not a link I could have in mind !!

---

### Post by mc4man on 2013-01-16
Well - went ahead & re-built eglibc removing the old related patches & applying the upstream diff.
So far no hangs in Gs when closing windows & no unresponsive totem or on occasion audacious.

Because a local debian package build of eglibc is a total pita can't quite say this will be fixed with a new libc6 ect. upgrade down the road but it looks promising.

---

### Post by bmbaker on 2013-01-17
> **mc4man said:**
> It's possible that the GS issue is the same as seen here - 
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342)
(I believe these issues would be only or more likely seen on 64 bit

It does seem to be the case crashes and stall on my 64 bit setup but works just fine on my 32 bit ! go figure :-)

could you share your patched eglibc so i can have a look and test :-)
cheers :-)

---

### Post by mc4man on 2013-01-17
> **bmbaker said:**
> It does seem to be the case crashes and stall on my 64 bit setup but works just fine on my 32 bit ! go figure :-)

could you share your patched eglibc so i can have a look and test :-)
cheers :-)

I don't particulary 'trust' the build for some various reasons - short explain
Somehow in lauchpad an amd64  build only builds to 'I believe' build-tree/amd64-libc. In this case it built 2 others as seen in screen 1 which greatly extended the build time & complexity. (90 - 120 min. to the initial fail

Additionally the patch added a test(s) (there are thousands), some of which are expected to fail hence there is a whole dir., (screen shows some), of 'expected-results*' which contain a list of expected fails. So there where some new unlisted fails which I had to add to the appropriate list, re-build & check, then fix the next fail, ect..

To save **alot** of time I switched from dpkg-buildpackage to a fakeroot build which allows adjusting & then continuing current build from last successful entrant. (advisable method - unlikely

If inclined I'll make libc6 & libc-bin available thru some means other than here -  probably only need the libc6 package - ck pm. 
I put in a fresh install to 1st. ck. (built on this install), worked fine for the purpose of checking & noticed no ill effects, am going to install on my 'using' install to see also.
(to go back to current just mark for upgrade in synaptic as I built as same current version.

---

### Post by ft_ on 2013-01-28
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694962](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694962)

```
eglibc (2.17-0ubuntu1) raring; urgency=low

  * This upstream merge fixes a nasty hang in pulseaudio (LP: #1085342)

```

So : do you still experience hangs of gnome-shell ? I'll try to close all my windows. Let's be crazy !

---

### Post by ft_ on 2013-02-05
no more crashes since eglibc update

---

