---
title: "Ridiculously easy way to get latest Synfig installed on Intrepid"
date: 2009-01-10
forum: Ubuntu Studio
---

### Post by Ubuntiac on 2009-01-10
As some of you may have noticed, Synfig (the opensource 2d animation suite) in Intrepid is - well - broken.

On their forums and here there ar elong, lengthy threads on compiling it and it's required libraries. For those of us (like me) who loathe compiling HOPE IS AT HAND! Yes, there is an easier way:

1. In Adept / Synaptic add "deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main" to your sources (without the quotation marks).

2. Install synfig. (from Adept / Synaptic or by entering "sudo apt-get update && sudo apt-get install synfig" in the console).

Enjoy!

---

### Post by genete on 2009-01-11
Thanks for the link to the repository. I'm involved in synfig development and we're so pleased to see our last release available for Ubuntu.


Is this repository valid for the new Ubuntu Jaunty? If yes, dear Ubuntu developers, would it be possible to adapt this binaries to the official repository?. 

Or at last, would it be possible to have the new 0.61.09 version available into Jaunty?

Thanks

---

### Post by Ubuntiac on 2009-01-11
The normal Ubuntu process for getting something into the standard repo's is:

1. Get it packaged (preferably in Debian)
2. If it's not in Debian, file a bug report asking for it's inclusion.
3. Drum up encouragement on your bug report. See my now successful attempt in my signature to get Kdenlive updated from a year old, buggy SVN snapshot, to the slick, sexy version we have now. :) I must get around to changing my sig...

PS Thank you so much Genete for your work on Synfig. I'm just starting out with it at the moment, but already I can see massive potential.

---

### Post by rylleman on 2009-01-11
Thank you very much!

Is this repository for Synfig only or do you get a lot of other development versions of other apps as well?

---

### Post by Ubuntiac on 2009-01-11
Looking at the repo, it has some other packages but not many.

Video4Linux, libwebkit, curl and homebank. All the rest seem to be Synfig related (ETL, libsynfig0, synfigstudio etc)

So yes, if anyone is using any of these and *doesn't* want them updated to development versions, either don't use this, or learn to pin your versions.

---

### Post by Langsuyar on 2009-01-22
Well, it worked for me, thanks a lot. =)
One more question: is this rep safe ? There is no problem in mantaining it activated ? 

Thanks in advance;)

---

### Post by HuaiDan on 2009-02-12
Question:

I had a problem whereby I recently installed SS from synaptic and it closed whenever I tried to mouse a menu item. This issue was reproduced by several other users in UII 8.10.
In order to get it working correctly I had to compile the packages. Has this issue been fixed in this release?

Duh. Sorry. Never mind.

---

### Post by kang28345 on 2009-02-12
i did not work or you may need to dumb the instructions down more.

---

### Post by fraterm on 2009-03-07
Going over adding the key or referring to that step would be more helpful.

The key for the launchpad ppa repository specifically.

Seems that this way should work: 

[https://launchpad.net/~stemp/+archive/ppa](https://launchpad.net/~stemp/+archive/ppa) follow these instructions, and you should get the packages and the key will be imported properly.

Packages work well too, For the record. :)

---

