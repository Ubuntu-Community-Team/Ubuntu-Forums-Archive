---
title: "Request: working transcode"
date: 2005-04-22
forum: Ubuntu Backports
---

### Post by RastaMahata on 2005-04-22
Is it necessary we must depend on marillat? I mean, sometimes it breaks our other repositories. It would be AWESOME if I could just depend on backports to have extra packages for ubuntu :D

Please, please give us a working transcode package, so I can get my avi files into vcd :(

---

### Post by brickbat on 2005-04-23
i agree.  please someone with some knowledge help us.

btw, version1 beta 2 of transcode is out.  i tried to compile it myself.

it was harder than compiling gentoo.

ciao
bb

---

### Post by marxist on 2005-05-23
*push*
i second this.

i was able to circumvent some of the problems with the marillat repository by using it's testing branch rather than unstable. but there ist still no transcode availlable :( (and i can't install cinelerra-cvs as long as i can't install those packages from marillat, but that's another story).

i'm rather new to (k)ubuntu and while i like it, it had never problems like these with mepis...

would it be a solution to update to the unstable version of ubuntu (and how unstable is it) or is it possible to add debian repositories to fix the problems with marillat?

---

### Post by brickbat on 2005-05-23
There are instructions for getting transcode working at the unofficial guide.  They weren't there when hoary came out but I went there a month later and there they were.  I tried them and they worked perfectly.

[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)

ciao
bb

---

### Post by patsissons on 2005-10-30
I was having a very similar problem recently.  After being fed up with the lack of an ubuntu deb for transcode, i decided that i might as well just make my own.  My deb *should* work with ubuntu hoary (and possibly others) but i cannot guarantee anything.  It is working for me currently, and i would love to hear success stories from others if they can get it to work on their system as well.  The deb(s) can be downloaded here:

[http://box.go.dyndns.org/dev/transcode_1.0.1-0ubuntu_i386.deb](http://box.go.dyndns.org/dev/transcode_1.0.1-0ubuntu_i386.deb)
[http://box.go.dyndns.org/dev/transcode-doc_1.0.1-0ubuntu_all.deb](http://box.go.dyndns.org/dev/transcode-doc_1.0.1-0ubuntu_all.deb)

if you want to build your own deb, take a quick look at the tutorials for building debs from source.  Go grab the latest source package for transcode and then do a apt-get source for transcode from marillat or debian repos, then simply copy the debian directory into the downloaded transcode source directory.  From here, just modify the control file and changelog and you should be set up quite nicely for a `fakeroot debian/rules binary` to build your deb files.

NOTE: remember to update the dependencies properly or you'll run into the same dependency hell that you do with the marillat repos.

---

### Post by reuben on 2005-11-13
Adding my vote. Transcode is ultra powerful -- it would be great to have a working version in the repositories.

---

### Post by ossi on 2005-11-14
There is a source for transcode - you can install it via apt-get. I guess it should be here, but havent got my notebook here to look i t up. Try adding that line to sources.list:

 deb [http://www.kiberpipa.org/~gandalf/ubuntu/](http://www.kiberpipa.org/~gandalf/ubuntu/) ./ .

---

### Post by liontooth on 2005-11-19
Transcode and other packages from Marillat's repositories appear be all be ported to Ubuntu in the multiverse repositories:

## Multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

Dave

---

### Post by liontooth on 2005-11-19
A few additional Marillat packages not available through the multiverse repository can be fetched directly from his own repository:

   deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

Dave

---

### Post by angrykeyboarder on 2005-11-22
[quote=liontooth]A few additional Marillat packages not available through the multiverse repository can be fetched directly from his own repository:

   deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") sid main

Dave[/quote]

Or better yet, packages built for Ubuntu...

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

OR

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

---

