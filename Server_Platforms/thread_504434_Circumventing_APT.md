---
title: "Circumventing APT"
date: 2007-07-19
forum: Server Platforms
---

### Post by codmate on 2007-07-19
The versions of libtorrent and rtorrent in the default APT repositories are rather old and I would like to use the latest stable versions for security and features.
[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

The latest stable versions are:
libtorrent-0.11.4
rtorrent-0.7.4

I am happy to track down the dependencies and install them myself with the old configure/make system - but I'm a bit worried about how this might affect APT.

I would like to continue to use APT to manage all other packages, as other software I use (such as SlimServer) often has its own repository (deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main for SlimServer).

How can I manage this? I don't want APT to touch libtorrent, rtorrent or any of their respective dependencies. What do I need to do to achieve this, and what issues might I run into?

If it makes any difference; my box is very light - only running the default Ubuntu server stuff plus MusicIP Mixer, SlimServer and rtorrent/libtorrent. I hope to keep it this way.

Many thanks for any help  :)

---

### Post by codmate on 2007-07-19
Hmmm - I just found some 'unofficial Debian packges', here:
[http://debian.ghostbar.ath.cx/rtorrent/0.7.4-1/](http://debian.ghostbar.ath.cx/rtorrent/0.7.4-1/)

...and here:
[http://debian.ghostbar.ath.cx/libtorrent/0.11.4-1/](http://debian.ghostbar.ath.cx/libtorrent/0.11.4-1/)

How might I go about using and maintaining these via APT?

Cheers  :)

---

### Post by splintercellguy on 2007-07-19
You could just do sudo dpkg -i package.

---

### Post by codmate on 2007-07-19
> **splintercellguy said:**
> You could just do sudo dpkg -i package.

Would I do this on a downloaded Debian package - or would this try and install a default version from the repository (not what I want as the default versions are too old)?

If this command is to be used on a downloaded package, from [http://debian.ghostbar.ath.cx/libtorrent/0.11.4-1/](http://debian.ghostbar.ath.cx/libtorrent/0.11.4-1/), for instance; would I need to download all the files in the directory, or just the .deb file representing the version of the software that I want (libtorrent10_0.11.4-1_i386.deb for instance)?

Also, does this command enter software into the APT system so that I can continue to manage all packages with APT?

I notice that the packages are all i386 - is it safe to assume that these will be OK with my amd-64 install and will use multilib automatically?

Cheers.

---

### Post by koenn on 2007-07-19
you'd have to download it before you dpkg -i . wget can be used for to dopwnload from a command line.
apt and dpkg understand each other so probably apt will be aware of the install. If not, make apt aware with the equivs tool. (man equivs)

you'd only need the deb file your after, but might have to go looking for additional deb packages to satisfy dependencies. It would be unadvisable to use apt-get (or aptitude, sunapyic, ...) to install additional packages unless you've verified that they in turn don't pull in new dependencies - you might be upgrading core system files / C compiler; librarioes without knowing it.
This partially depends on how much non-standard sources you have in sources.list. You can simulate an install by running ```
apt-get -s install package
```. Shows you wat *would* happen. 
I wouldn't assume a i386 package to work on anything else than intel 386c compatible processors. Is your amd-64 i386 architecture ?


--------------
An other approach, but equally complicated , is to modify apt's behaviour by means of a preference file. This is called apt-pinning. 
Here's a small introduction : 
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by codmate on 2007-07-20
Many thanks for that.

Looks like most processors are i386 - I just looked it up and it turns out to be a synonym for x86.
[http://en.wikipedia.org/wiki/Category:X86_microprocessors](http://en.wikipedia.org/wiki/Category:X86_microprocessors)

I'm guessing the 32 bit binaries will be fine.

I'm looking forward to using the new rTorrent  :)
I highly reccomend it if anybody is after a simple ncurses based torrent client!
I tend to log into my machine and run it in a screen session.
It's set up to watch a folder. I download .torrent files from my Windows machine, dump them in the folder, and rTorrent just starts to download 'em  :)

---

### Post by Eddy DaKillaBee on 2007-07-22
**codmate**, looks like we might be in the same camp. I just downloaded the two .deb files today (prior to finding this forum topic) and did a dpkg -i [.debs here]... no luck:
```
# dpkg -i libtorrent10_0.11.5-1_i386.deb rtorrent_0.7.4-2_i386.deb
(Reading database ... 83419 files and directories currently installed.)
Preparing to replace libtorrent10 0.11.5-1 (using libtorrent10_0.11.5-1_i386.deb                                              ) ...
Unpacking replacement libtorrent10 ...
Preparing to replace rtorrent 0.7.4-2 (using rtorrent_0.7.4-2_i386.deb) ...
Unpacking replacement rtorrent ...
dpkg: dependency problems prevent configuration of libtorrent10:
 libtorrent10 depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 libtorrent10 depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 libtorrent10 depends on libssl0.9.8 (>= 0.9.8e-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.3.
 libtorrent10 depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing libtorrent10 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rtorrent:
 rtorrent depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 rtorrent depends on libcurl4-openssl (>= 7.16.2-1); however:
  Package libcurl4-openssl is not installed.
 rtorrent depends on libgcc1 (>= 1:4.1.2); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 rtorrent depends on libkrb53 (>= 1.6.dfsg.1); however:
  Version of libkrb53 on system is 1.4.3-5ubuntu0.4.
 rtorrent depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.3.
 rtorrent depends on libstdc++6 (>= 4.1.2); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 rtorrent depends on libtorrent10; however:
  Package libtorrent10 is not configured yet.
dpkg: error processing rtorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libtorrent10
 rtorrent

```If you happen to figure out where and how we can install those newer libraries without breaking anything please reply back to the thread so I can try it out!

I should also add (in case anyone is about to suggest this) that I can not upgrade from Dapper. Virtualmin Pro currently doesn't support versions of Ubuntu newer than Dapper...

---

### Post by codmate on 2007-07-23
> **Eddy DaKillaBee said:**
> **codmate**, looks like we might be in the same camp. I just downloaded the two .deb files today (prior to finding this forum topic) and did a dpkg -i [.debs here]... no luck:
```
# dpkg -i libtorrent10_0.11.5-1_i386.deb rtorrent_0.7.4-2_i386.deb
(Reading database ... 83419 files and directories currently installed.)
Preparing to replace libtorrent10 0.11.5-1 (using libtorrent10_0.11.5-1_i386.deb                                              ) ...
Unpacking replacement libtorrent10 ...
Preparing to replace rtorrent 0.7.4-2 (using rtorrent_0.7.4-2_i386.deb) ...
Unpacking replacement rtorrent ...
dpkg: dependency problems prevent configuration of libtorrent10:
 libtorrent10 depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 libtorrent10 depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 libtorrent10 depends on libssl0.9.8 (>= 0.9.8e-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.3.
 libtorrent10 depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing libtorrent10 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rtorrent:
 rtorrent depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 rtorrent depends on libcurl4-openssl (>= 7.16.2-1); however:
  Package libcurl4-openssl is not installed.
 rtorrent depends on libgcc1 (>= 1:4.1.2); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 rtorrent depends on libkrb53 (>= 1.6.dfsg.1); however:
  Version of libkrb53 on system is 1.4.3-5ubuntu0.4.
 rtorrent depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.3.
 rtorrent depends on libstdc++6 (>= 4.1.2); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 rtorrent depends on libtorrent10; however:
  Package libtorrent10 is not configured yet.
dpkg: error processing rtorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libtorrent10
 rtorrent

```If you happen to figure out where and how we can install those newer libraries without breaking anything please reply back to the thread so I can try it out!

I should also add (in case anyone is about to suggest this) that I can not upgrade from Dapper. Virtualmin Pro currently doesn't support versions of Ubuntu newer than Dapper...

I've given up on it for now, as I couldn't find amd_64 versions of all the libraries I needed  :(
I just don't have the time to deal with dependency hell manually...

It's a shame, as they've made significant strides with both libtorrent and rtorrent since the versions currently in APT by default for Feisty.

---

