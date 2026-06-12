---
title: "LXC - CPAN make fail"
date: 2010-07-04
forum: Virtualisation
---

### Post by jamie.nicholson on 2010-07-04
CPAN doesn't work on your lxc container? You get something like this?

> 
Running make install
  make had returned bad status, install seems impossible
Running make for D/DA/DAGOLDEN/ExtUtils-ParseXS-2.2205.tar.gz
  Is already unwrapped into directory /root/.cpan/build/ExtUtils-ParseXS-2.2205
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


Ensure you have the following,

```
sudo apt-get install build-essential autoconf automake libtool gdb
```

And then reconfigure CPAN

```

>cpan
o conf init
o conf commit
```

Then try again. Hope this helps.

-----------
background
-----------
Successfully installed lxc on Karmic and installed a guest/container Hardy image. About a weekend to setup if your new to lxc, bridging in Linux.

Used these instructions from [Stephane]("http://www.stgraber.org/2009/11/06/lxc-containers-or-extremely-fast-virtualization#comment-221") and  read bodhi.zazen [articles]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-karmic-containers/"). 

I was new to bridging so I also had to read some articles on bridging and understand that too. 

Next I got aptitude up and installed build-essentials and a whole host of other packages.

Then tried CPAN, CPAN downloaded packages but failed to make anything at all. 

So I searched around on it and found some articles leading me astray in different directions.  Until eventually I just tried to reconfigure CPAN and much to my surprise everything worked.  Sometimes the solutions are right in front of you.

---

### Post by juancarlospaco on 2010-07-05
I dunno whats Cpan, but LXC run all my headless software without any problem.

lxc is the future...

---

### Post by juancarlospaco on 2010-07-05
I dunno whats Cpan, but LXC run all my headless software without any problem.

*lxc is the future...*

---

