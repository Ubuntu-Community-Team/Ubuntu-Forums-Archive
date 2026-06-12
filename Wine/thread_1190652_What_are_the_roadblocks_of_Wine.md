---
title: "What are the roadblocks of Wine?"
date: 2009-06-18
forum: Wine
---

### Post by houseonfire on 2009-06-18
I am a very big fan of linux, mainly Ubuntu.
I love the idea and concept of Wine, but personally I wonder why it can't be more advanced/compatible.
Are there legal ramifications? Why can't a windows disk be popped in to load all the important files that are needed to run all the programs that can work in XP?
Or is it more of a programming set back? A lack of (not meaning to sound insulting) programming skills to get it to completely work.

Is it possible to do this?

---

### Post by donkyhotay on 2009-06-18
The biggest roadblock is the fact that all the wine developers are trying to reverse engineer the windows API without access to the source code. Thats like trying to rebuild the pyramids of egypt with no knowledge about them beyond what you read in a 3rd grade history book.

---

### Post by NightMKoder on 2009-06-18
Not entirely true, but generally reflects the idea. Windows api is fairly documented (ie msdn), but certain "hidden" features are widely used and hence have to be reverse engineered.

The biggest roadblock is simply lack of manpower. But to be honest, at this point wine runs a lot of windows apps very well. Right now, the biggest problem for linux is video drivers. Once GEM/TTM/modesetting code is stabilized for intel/ati/(maybe) nvidia (note: not proprietary, noveau), then we can talk about things working.

---

### Post by ad_267 on 2009-06-18
Besides those points, Wine isn't really the end solution. For most Windows applications there are open source alternatives that are just as good or better.

For the few applications people do use Wine for, it would be much better to have the software vendors support Linux and provide native Linux versions, or even better, support open file formats so that someone else may create a compatible open source application for Linux.

---

### Post by Meow27 on 2009-06-19
open office < MS word
Gimp < photoshop


thats two counter examples

they may be free, but that doesnt make them better

---

### Post by 3rdalbum on 2009-06-19
> **houseonfire said:**
> Why can't a windows disk be popped in to load all the important files that are needed to run all the programs that can work in XP?

Good question. For some programs, you can put in some native Windows DLLs and they will work.

However, Wine needs to map Windows system commands to Linux equivilants - that's how it works. You can't use Windows DLLs that access the underlying operating system directly, you need DLLs that know how to access Linux functions. So, if you have libA.dll, where it just calls libB.dll, and libB.dll calls the hardware; then libA can be a native Windows DLL and libB must be a Wine equivilant so it can call a Linux function.

Somebody correct me if this is totally wrong, but that's my understanding of it. Oh, and of course, the DLLs that call the hardware or underlying system directly are the difficult ones with undocumented features or bugs.

---

### Post by ad_267 on 2009-06-19
> **Meow27 said:**
> open office < MS word
Gimp < photoshop

thats two counter examples
they may be free, but that doesnt make them better

That wasn't my point. I wasn't saying Open Source applications are better so we don't need Wine, I was saying that it would be better if we didn't need Wine and commercial apps were compatible with open source ones.

For me, LaTeX > MS Word, and who can actually afford photoshop unless they pirate it or are a professional graphic designer? For most people Gimp is just fine. And if we continue to be happy running Photohsop in Wine there's no incentive for Adobe to release a Linux version.

---

### Post by Ojustaboo on 2009-06-19
> **ad_267 said:**
> and who can actually afford photoshop unless they pirate it or are a professional graphic designer? 

Lots of people.

Any student can buy the latest CS4 Photoshop extended for £155 (instead of the normal £557)

Or for £270 (instead of the normal £1436) can buy CS4 Design Premium which contains Adobe InDesign® CS4, Photoshop® CS4 Extended, Illustrator® CS4, Flash® CS4 Professional, Dreamweaver® CS4, Fireworks® CS4, and Acrobat® 9 Pro with additional tools and service

Any charity also gets a substantial discount, Photoshop CS4 ext would cost them £228.

£270 seemed a very good deal to me for the design suite hence I brought it. When you consider how often I spend say £40 on a game or how much my graphics card cost etc, for something I'm going to get a lot of use out of and does what I want, personally I don't think it's that bad a price.

---

### Post by ad_267 on 2009-06-19
> **Ojustaboo said:**
> Lots of people.

Ok, so besides pirates, graphic designers and students... 

Anyways, I wasn't trying to argue about open source software being better or Photoshop being too expensive. I was just pointing out that ideally we wouldn't need Wine, and should be aiming to move away from depending on it where we can.

---

### Post by Meow27 on 2009-06-29
> **ad_267 said:**
> Ok, so besides pirates, graphic designers and students... 

Anyways, I wasn't trying to argue about open source software being better or Photoshop being too expensive. I was just pointing out that ideally we wouldn't need Wine, and should be aiming to move away from depending on it where we can.

i disagree. even if we did have all of the above, it is unavoidable that someone will make a [good] windows program that people will want to try out. Wine lets us run these programs in linux, so it gives the host OS more compatibility with cross platform stuff. It also lets developers who originally designed their games for windows, port it to wine, saving lots of time and money instead of trying to completely port it to linux [or mac]

---

### Post by estyles on 2009-06-29
> **Meow27 said:**
> open office < MS word
Gimp < photoshop


thats two counter examples

they may be free, but that doesnt make them better

They may be free, but that doesn't make them worse either.  Open Office is more intuitive for me, despite the fact that I've worked with MS Office for 15+ years and OOO for 1+ year.  Not to mention that OOO can open Office documents that the last version of MS Office cannot open (without a converter that you *might* be able to download and install if you run as admin, but which is a huge pain to try to get if you run as a limited user).

And Photoshop can do some things better than GIMP, but if something is possible in GIMP, I find it a lot easier to use than Photoshop.

---

### Post by Th3_uN1Qu3 on 2009-07-02
OpenOffice is just as good as MS Office, yes. But GIMP is nowhere near Photoshop - and the reason why Photoshop is the only proper graphics app available is because Corel ruined Paint Shop Pro when they bought it from Jasc. Paint Shop Pro used to whip Adobe *** any day, and i believe the good ol' 9.0 runs in Wine.

However, i do agree that the Wine project needs more manpower and better verifications - for example, program ratings in the AppDB can be very misleading. FL Studio runs, yes. Does it run fast enough and bug-free enough to be actually usable, no. Also its copy protection does not work with Wine so it's stuck in demo mode even if you patch it. Thus, it cannot be used at all, be it legally or not really legally, and the only option is VirtualBox, and all that virtualization besides the craptacular thing that is ALSA, adds in a significant amount of audio latency. Again, enough for the software to become not-so-usable. It's like trying to run it on a Pentium II.

---

### Post by del_diablo on 2009-07-02
I would say GIMP works, the real problem is that the interface is a complete mess.
Its par with photoshop, but not in the exact same lane either.

---

### Post by HavocXphere on 2009-07-02
> **houseonfire said:**
> Why can't a windows disk be popped in to load all the important files that are needed to run all the programs that can work in XP?
WINE runs in userspace. i.e. it does not have direct access to hardware...which your above scenario would require.

Ubuntu internals ---- WINEserver ----WINE files ----- Windows software

So you can replace some of the WINE files with originals but this can make things worse. Say the original wine files request something that WINEserver does not support.

As 3rdalbum pointed out, there are undocumented feature in the original files. Lots. Sometimes they are put there and left undocumented on purpose.

> **houseonfire said:**
> A lack of (not meaning to sound insulting) programming skills to get it to completely work.
lols. No the devs are very skilled. This particular area is just a hell of a lot more difficult than you think.

In other areas you figure out what you want and write the code. With WINE you have a block-box. Think of it like this: Someone else built the front half of the car. You have to build the back half. Only you can't see the front half, you can only ask questions about it. A lot of the times the answer is just "no" with no info no error codes...nothing. The builder of the front half might also have made a few mistakes. Or he might give you a flat out lie as an answer (undocumented features).

See why its not lack of skill that the problem?

---

### Post by houseonfire on 2009-07-04
> **HavocXphere said:**
> WINE runs in userspace. i.e. it does not have direct access to hardware...which your above scenario would require.

Ubuntu internals ---- WINEserver ----WINE files ----- Windows software

So you can replace some of the WINE files with originals but this can make things worse. Say the original wine files request something that WINEserver does not support.

As 3rdalbum pointed out, there are undocumented feature in the original files. Lots. Sometimes they are put there and left undocumented on purpose.


lols. No the devs are very skilled. This particular area is just a hell of a lot more difficult than you think.

In other areas you figure out what you want and write the code. With WINE you have a block-box. Think of it like this: Someone else built the front half of the car. You have to build the back half. Only you can't see the front half, you can only ask questions about it. A lot of the times the answer is just "no" with no info no error codes...nothing. The builder of the front half might also have made a few mistakes. Or he might give you a flat out lie as an answer (undocumented features).

See why its not lack of skill that the problem?

Thank you for your explanation.
I didn't mean to sound like a jerk or anything, I was just including it as a possible variable as to why the it isn't *as* compatible in linux.
It makes more sense to me now.

---

