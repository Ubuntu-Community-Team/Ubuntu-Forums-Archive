---
title: "ogg dvd rip tool"
date: 2004-12-02
forum: The Cafe
---

### Post by ubuntu_demon on 2004-12-02
Hi,

Is there a nice and easy dvd ripping tool that creates ogg files ?

Maybe if there were such an easy tool available in ubuntu we as a community could help make ogg more popular. And we would be able to watch more content out-ot-the-box.

---

### Post by p!=f on 2004-12-02
DVD (video) ripping tool which creates OGG (sound) files?

---

### Post by Lovechild on 2004-12-02
Thoggen ([http://thoggen.net/](http://thoggen.net/)) looks promising, and much in line with GNOME2 design rules - I tried CVS and it sorta works already.

---

### Post by p!=f on 2004-12-02
Ok... got it... :)
How about this package?
```

Package: video-dvdrip
Priority: optional
Section: multiverse/graphics
Installed-Size: 68
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 1:0.50.18-0.1
Depends: dvdrip
Filename: pool/multiverse/v/video-dvdrip/video-dvdrip_0.50.18-0.1_i386.deb
Size: 26654
MD5sum: 54c1448f7f58009315ef26dfeaf78ff7
Description: Perl front end for transcode - dummy package
 This package is simply an empty package to install the real dvdrip package
 who reflect the real name for this tool.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: dvdrip
Priority: optional
Section: multiverse/graphics
Installed-Size: 1200
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Source: video-dvdrip
Version: 1:0.50.18-0.1
Depends: perl (>= 5.6.0-16), perl-modules (>= 5.8.1-1) | libstorable-perl, libgtk-perl, libgtk-pixbuf-perl, transcode (>= 2:0.6.6), imagemagick, fping, libevent-perl
Recommends: xine-ui, subtitleripper, dvdrip-doc
Suggests: mjpegtools, ogmtools (>= 0.972), cdrdao, mkisofs, cdrecord, vcdimager, mplayer, rar-2.80
Conflicts: video-dvdrip (<= 0.50.18-0.0)
Filename: pool/multiverse/v/video-dvdrip/dvdrip_0.50.18-0.1_i386.deb
Size: 226096
MD5sum: 688b358a3a88fbd22a8526dcaa228c82
Description: Perl front end for transcode
 dvd::rip is a full featured DVD copy program written in Perl. It provides
 an easy to use but feature-rich Gtk+ GUI to control almost all aspects of
 the ripping and transcoding process. It uses the widely known video
 processing swissknife transcode and many other Open Source tools.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by ubuntu_demon on 2004-12-03
Please try it out and see whether those tools are easy and sufficient.

Too bad thoggen isn't ready for end-users yet (according to the site).
Too bad dvdrip is in multiverse. 

I would like one in the main repository in the future.

The next time I've got a nice DVD in my hands I'll try out ripping also :)

---

### Post by p!=f on 2004-12-03
I think everyone would like to see everything in main but unfortunately due to the patent issues it's not possible and I doubt it will be in near future.

---

### Post by ubuntu_demon on 2004-12-03
I wasn't very clear. The point I was trying to make :

there should be an dvd-rip tool that has no problems with patents. The user needs to manual install libdvdcss2 but other than that it just works. Like it uses ogg instead of mpeg4. So it could be put into main.

Ubuntu has to focus a bit more on making things easy for end-users.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-23
> **ubuntu_demon said:**
> I wasn't very clear. The point I was trying to make :

there should be an dvd-rip tool that has no problems with patents. The user needs to manual install libdvdcss2 but other than that it just works. Like it uses ogg instead of mpeg4. So it could be put into main.

Ubuntu has to focus a bit more on making things easy for end-users.

i like the way you think
i am currently trying to do this exact thing was going to use vlc but its broken for transcodeing to ogg

---

### Post by grikdog on 2009-09-29
I second the emotion!

---

