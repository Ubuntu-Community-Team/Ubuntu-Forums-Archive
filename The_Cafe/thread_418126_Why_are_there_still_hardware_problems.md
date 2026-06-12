---
title: "Why are there still hardware problems?"
date: 2007-04-22
forum: The Cafe
---

### Post by FooBarWidget on 2007-04-22
Every time someone posts an Ubuntu article on Slashdot or OSNews (for instance, [this](http://linux.slashdot.org/article.pl?sid=07/04/20/1424223) and [this](http://osnews.com/comment.php?news_id=17739)), lots and lots of people are complaining about:
1. Their optimal monitor resolution not being detected. They had to edit xorg.conf.
2. Their video card not being detected. They had to edit xorg.conf.
3. Their wireless card not being detected.

I quote:
> and basic usability features like automatic determination of your video card and monitor specs are still unreliable, it isn't there yet. Fail.
> And what the hell is the deal with X11 anyway? Is it really that difficult to build in some fallback safe video modes for unidentified cards or screwed up config files, or to do whatever else is necessary to make sure that the user will ALWAYS be able to get back into his GUI desktop without expert help? That's a rhetorical question, the answer is no. It isn't that difficult to build in some simple fault tolerance in places where inexperienced users often get bitten, trapped and frustrated. How exactly is the user supposed to go search the wiki online for help fixing X11 when he only has one computer available and he can't figure out how to get X11 to start? Come on people. I should not be reading recent articles from users of the most recent and popular distros that talk about getting stuck at the command line. Fail.
> "Desktop Effects" is embarrassingly broken and simply shouldn't have been shipped. Turning them on shouldn't result in black windows under any circumstances. My Samsung monitor's 1440x900 resolution wasn't detected out-of-the-box and I had to resort to manually editing xorg.conf to get it working correctly. The fonts in OpenOffice.org are rendered differently to the way they're rendered by GTK+, and have been for two releases now.
(This latter problem, black screen when I enable desktop effects, applies to me as well.)

This isn't the first time that people have complained about this. Most of these complaints have existed for years. I'm wondering: why are these problems still not solved? Is it that hard to correctly detect monitor settings? And does X really not support falling back to SVGA if the current driver fails? Do all video cards support SVGA fallback mode?

---

### Post by OffHand on 2007-04-22
> And what the hell is the deal with X11 anyway? Is it really that difficult to build in some fallback safe video modes for unidentified cards or screwed up config files, or to do whatever else is necessary to make sure that the user will ALWAYS be able to get back into his GUI desktop without expert help? That's a rhetorical question, the answer is no. It isn't that difficult to build in some simple fault tolerance in places where inexperienced users often get bitten, trapped and frustrated. How exactly is the user supposed to go search the wiki online for help fixing X11 when he only has one computer available and he can't figure out how to get X11 to start? Come on people. I should not be reading recent articles from users of the most recent and popular distros that talk about getting stuck at the command line. Fail.

If it's not that difficult he should program it. Bulletproof X will be in Feisty+1 I think.

---

### Post by Ram Crammer on 2007-04-22
> **OffHand said:**
> If it's not that difficult he should program it. Bulletproof X will be in Feisty+1 I think.
Wanna bet?  People have been saying this for years.

The quotes listed by Foo Bar Widget are right on!  I too ended up with the blank screen of death after trying "Desktop Effects", found them broken, and tried to switch them off.  There seems to be no way for Joe Sixpack to get back to his original configuration.  At least I never found it.  Fortunately, I was able to edit the xorg.config file and get  X running again.  But for the newbee, its the end of the show, and back to Windoze.  

It certainly seems that a default fallback to basic VGA graphical mode should be easy enough to implement.  But if the Xorg folks haven't gotten the message yet, I despair of them ever getting it.  And Ubuntu should NOT have released with "Desktop Effects" included.  

Read the forum threads devoted to this topic.  There are probably 50 threads on this subject alone, and each with a dozen different post ID's, and many with hundreds of reads.  That adds up to a whole lot of frustrated Ubuntu users, and that doesn't even include those newbees who didn't post, due to they gave up  because they had no X.  Very Sad.  I expected more from Ubuntu developers.  And from Nvidia, too.  Nvidia is demonstrating token effort in their providing broken binary drivers for their cards.  And if they don't care to lavish the kind of attention of these drivers that they really need and deserve, they should at least make them open source and let the Linux community do so.   There is plenty of blame to go around on this issue, and I don't see anyone coming forward and saying they dropped the ball and will do something about it.  

This is exactly the kind of ammunition the anti-Linux community loves.  We are shooting ourselves in the foot with this kind of thing.  I love Linux, and will continue to support it, but  I'm not going to bury my head in the sand and deny that Linux is still not ready for prime-time.  "For Geeks Only -- All Others Beware!".

---

### Post by bonzodog on 2007-04-22
You need to read whats happening to X at the moment. X is undergoing a major change to eradicate the config file, and work from XRandR. It will hopefully Just work on most monitor configs, but some ATI graphics cards are difficult to work with due to closed standards and drivers. So, I cannot see us ever getting X working completely out of the box. Bulletproof X will drop you to the vesa driver, with only a basic resolution. After that, you will need to get the drivers working from ATI/Nvidia. 

The fglrx/ati free drivers kind of work, but ATI/AMD are making life very difficult for the linux FLOSS community at the moment, and there is possibly going to be a push by the linux community encouraging people not to use ATI gear with linux.

Wifi, again is about closed cards, and the manufacturers unwilling to release drivers for linux, leaving us to write our own. That takes a long time, as most are reverse engineered.

---

### Post by DoctorMO on 2007-04-22
Oh no propitiatory drivers are hurting our community what a surprise. and yet your response is to have a go at Linux instead of nVidia/ATI or Broadcom.

go away please before you do yourself an injury.

---

