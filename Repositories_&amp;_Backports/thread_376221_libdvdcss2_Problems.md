---
title: "libdvdcss2 Problems"
date: 2007-03-04
forum: Repositories &amp; Backports
---

### Post by CompCrasher86 on 2007-03-04
Hi I'm pretty much a novice with Linux, and I've gotten this far without help...

I am trying to install libdvdcss2 (So that I can watch DVDs in VLC) through Synaptics Package Manager and unfortunately it gives me the following error message:

libdvdcss2:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed

Now I searched for libc6 and found I have version: "2.3.6-0ubuntu20.4" installed, and it does not intend to update it to a higher version. 

I am confused because libdvdcss2 seems to me like its asking for a version of libc6 that seems to be nonexistent to my Package Manager (Something greater than or equal to 2.5-0?).

Now I may be misconceived by the error message, so any help would be appreciated, I'd love to start watching DVDs on my laptop! :)

---

### Post by floke on 2007-03-04
You can get it from medibuntu - just go to their website at [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) and follow the instructions - add the repo key etc. get the files and away you go.

BTW: Usual disclaimers on third party repos apply here - and you should read up on 3PRs before you do this. Personally, I used the medibuntu repos to set up VLC a few days ago and everything's fine (though I've unchecked the repos from installing further software, since the only thing I needed was the libcvsdvd2 file thing).

Hope this helps.

---

### Post by CompCrasher86 on 2007-03-04
Now that is what I call support!

Thank you so much Steve.k for making my first forum post successful! I got the package from Medibuntu, installed it, and am watching DVDs as I type. Quick 23 minute response time too!
:popcorn:

---

### Post by floke on 2007-03-05
Glad it all worked. BTW: VLC won't work properly with Beryl unless you change the output to X11 - I can't remember the exact path to it - so if you have trouble then do a quick search for VLC and Beryl and you should be fine.

---

