---
title: "Puredata (Extended) dependencies (Installing help needed)"
date: 2009-12-22
forum: Ubuntu Studio
---

### Post by fgadea on 2009-12-22
Hi!

I am trying to install Puredata Extended, from  [http://puredata.info/downloads](http://puredata.info/downloads) in a "just installed and updated" Xubuntu.
I have tryed these versions: Ubuntu Hardy, Jaunty and Debian's Stable Lenny, and all of them gives me the following error.

Error: La dependencia no se puede satisfacer: ttf-bitstream-vera

After searching for it in the web, downloading and installing this font, several dependency errors follow, and the list seems unfinishable (I didn't finish it).
This problem does not show up with the vanilla version downloadable with "Install and Remove Applications".

Does anybody knows anything about this problem? Should I satisfy all dependencies? I mean, it sounds quite absurd that puredata would only work with a particular font.

Best! (and thankyou for any tip)

---

### Post by fgadea on 2009-12-22
> **fgadea said:**
> Hi!

I am trying to install Puredata Extended, from  [http://puredata.info/downloads](http://puredata.info/downloads) in a "just installed and updated" Xubuntu.
I have tryed these versions: Ubuntu Hardy, Jaunty and Debian's Stable Lenny, and all of them gives me the following error.

Error: La dependencia no se puede satisfacer: ttf-bitstream-vera

After searching for it in the web, downloading and installing this font, several dependency errors follow, and the list seems unfinishable (I didn't finish it).
This problem does not show up with the vanilla version downloadable with "Install and Remove Applications".

Does anybody knows anything about this problem? Should I satisfy all dependencies? I mean, it sounds quite absurd that puredata would only work with a particular font.

Best! (and thankyou for any tip)

I'm sorry, the error message is in spanish (as my Xubuntu version). It means "the dependency could not be satisfyed: ttf-bitsream-vera"

---

### Post by Stochastic on 2009-12-23
The trouble is that none of those packages are built for Karmic Koala, and the ttf-bitstream-vera package was dropped from the archives in Karmic (i.e. it no longer is distributed from Ubuntu).

What you should do to work around this is download the jaunty deb of ttf-bitstream-vera from packages.ubuntu.com and install that before attempting to install pd-extended.  Here's the direct download page for that package: [http://packages.ubuntu.com/jaunty/all/ttf-bitstream-vera/download](http://packages.ubuntu.com/jaunty/all/ttf-bitstream-vera/download)
It should only depend on deforma (which should already be on your system).

Hope that helps.

---

### Post by fgadea on 2009-12-26
Yes, you helped, at least to let me know where I was standing. I will try this: [http://autobuild.puredata.info/auto-build/latest/](http://autobuild.puredata.info/auto-build/latest/) and see what happens.
 
Thankyou, and Happy New Year.

---

