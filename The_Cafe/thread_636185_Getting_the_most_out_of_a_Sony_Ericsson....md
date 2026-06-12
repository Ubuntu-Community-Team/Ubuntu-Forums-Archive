---
title: "Getting the most out of a Sony Ericsson..."
date: 2007-12-09
forum: The Cafe
---

### Post by Jimmey on 2007-12-09
Does anyone know of anything funky I can install onto/do with a Java based Sony Ericsson v630i?

I've already been trying to use MidpSSH which looks like an amazing tool, I've just not had the time to do anything with it, yet.

Are there any other cool applications like this?

Have any of you done any crazy things with your Sony Ericssons? What about theming it yourselves? 

I know the .thm files are archives openable in Ubuntu by default, but I've not gotten round to making my own theme, just yet. Any requests for a theme you'd like to see made?

---

### Post by FuturePilot on 2007-12-09
Install [OperaMini]("http://www.operamini.com/") on it. Don't do it if you don't have an unlimited data plan or else your bill will go through the roof :shock:
I've also made a [few themes]("http://mysite.lasyk.net/FuturePilot/") myself.

---

### Post by Jimmey on 2007-12-09
I'm on a Pay As You Talk plan, so I can't really browse the internet much :-(

Cool Ubuntu theme, though!

**Downloads.

---

### Post by plun on 2007-12-09
Sony Ericssons theming tool for Linux

[http://developer.sonyericsson.com/site/global/newsandevents/latestnews/newnov07/p_linux_themescreator.jsp?link_general=article-linuxthemescreator](http://developer.sonyericsson.com/site/global/newsandevents/latestnews/newnov07/p_linux_themescreator.jsp?link_general=article-linuxthemescreator)

The challenge is gstreamer 0.8....Gutsy uses 0.10

A "dirty" solution for this

[http://no.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/libgstreamer-plugins0.8-0_0.8.12-6ubuntu3_i386.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/libgstreamer-plugins0.8-0_0.8.12-6ubuntu3_i386.deb)

Open deb file with Archive Manager

data.tar.gz >    /./usr/lib/

3 files and 3 symlinks to usr/lib

I dont want to install any 0.8 packages and mess up  gstreamer 0.1.0
therefore this solution.

:)

---

### Post by Palmyra on 2007-12-09
I am now using an LG Fusic, and if I could go back to Sony Ericsson, I would.  I used to own a w300i, but I'd take any Sony Ericsson.

---

### Post by FuturePilot on 2007-12-09
> **plun said:**
> Sony Ericssons theming tool for Linux

[http://developer.sonyericsson.com/site/global/newsandevents/latestnews/newnov07/p_linux_themescreator.jsp?link_general=article-linuxthemescreator](http://developer.sonyericsson.com/site/global/newsandevents/latestnews/newnov07/p_linux_themescreator.jsp?link_general=article-linuxthemescreator)

The challenge is gstreamer 0.8....Gutsy uses 0.10

A "dirty" solution for this

[http://no.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/libgstreamer-plugins0.8-0_0.8.12-6ubuntu3_i386.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/libgstreamer-plugins0.8-0_0.8.12-6ubuntu3_i386.deb)

Open deb file with Archive Manager

data.tar.gz >    /./usr/lib/

3 files and 3 symlinks to usr/lib

I dont want to install any 0.8 packages and mess up  gstreamer 0.1.0
therefore this solution.

:)

Whoa! When did they release that? 
Must give it a try :p

---

### Post by plun on 2007-12-09
> **FuturePilot said:**
> Whoa! When did they release that? 
Must give it a try :p

Well... a month ago, its just the gstreamer challenge...:^o  It works just fine to put mentioned files in /usr/lib and the app works.
:)

---

### Post by Jimmey on 2007-12-10
Theming is not a problem - The windows version of Sony Erricson's themer worked nicely for me in WINE, too.

What about other softwares?

---

### Post by Jimmey on 2007-12-10
I've just set up Midpssh, and can now SSH into my Ubuntu box from my phone. This is very cool.

I can execute quite an impressive range of commands - Obviously fancier ones (like top) won't work, but the basic utils are all there!

---

