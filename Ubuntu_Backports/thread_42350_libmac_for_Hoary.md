---
title: "libmac for Hoary"
date: 2005-06-17
forum: Ubuntu Backports
---

### Post by foxy123 on 2005-06-17
I need mac, which stands for Monkey Audio Codec to use shntool. There are libmac 2 and libmac2-dev in rarewares repository, but it requires libc6, newer that in hoary. As I understand it is not possible to update it. Is there any chance to have libmac and libmac-dev compatible with hoary in backports?

---

### Post by Slo Mo Snail on 2005-06-17
There are no source packages at rarewares so we have to build our own... maybe you can write one of the rarewares guys whether they can start distributing source packages. I wrote one a few weeks ago and got no answer :/

---

### Post by foxy123 on 2005-06-17
[QUOTE=Slo Mo Snail]There are no source packages at rarewares so we have to build our own... maybe you can write one of the rarewares guys whether they can start distributing source packages. I wrote one a few weeks ago and got no answer :/[/QUOTE]
As I understand they use mac, ported by SuperMMX:
[http://sourceforge.net/projects/mac-port/](http://sourceforge.net/projects/mac-port/)
or
[http://supermmx.org/linux/mac/](http://supermmx.org/linux/mac/)

---

### Post by xmixahlx on 2005-06-30
i'm the RW/D developer - what's the question?

also, RW/D has moved to a Unstable chroot and packages have been recompiled.

so.... try again :)


later

---

### Post by felix.rommel on 2005-10-14
[QUOTE=foxy123]I need mac, which stands for Monkey Audio Codec to use shntool. There are libmac 2 and libmac2-dev in rarewares repository, but it requires libc6, newer that in hoary. As I understand it is not possible to update it. Is there any chance to have libmac and libmac-dev compatible with hoary in backports?[/QUOTE]

There is a sourceforge project which ported the Windows source into a make friendly source:

[http://sourceforge.net/projects/mac-port/](http://sourceforge.net/projects/mac-port/)

Just install checkinstall so that you can create a deb package.

1. Extract the mac source
2. ./configure
3. make
4. sudo checkinstall

That's it :)

---

### Post by ariel on 2005-11-02
[QUOTE=foxy123]I need mac, which stands for Monkey Audio Codec to use shntool. There are libmac 2 and libmac2-dev in rarewares repository, but it requires libc6, newer that in hoary. As I understand it is not possible to update it. Is there any chance to have libmac and libmac-dev compatible with hoary in backports?[/QUOTE]


what i did to install libmac and be able to decompress .ape Monkey's Audio Codec files: 

   - Monkey's Audio Codec (MAC) (formato ape)

add the following repositories in /etc/apt/sources.list

      # RareWares Repository - Experimental
      deb [http://www.rarewares.org/debian/packages/experimental/](http://www.rarewares.org/debian/packages/experimental/) ./
      # RareWares Repository - Unstable
      deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
      deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) testing main contrib non-free

open synaptic, reload the package lists, search for "monkeys", install, enjoy.
this will install the "mac" utility to compress/decompress wav/ape files.

ps. as you see you will have to upgrade certain libraries (gcc, libstd6) with ones slighly newer. No problems whatsoever showed up in my home pc after i did it.

---

