---
title: "growisofs to finalize a dvd-r"
date: 2008-07-02
forum: Ubuntu Studio
---

### Post by maclenin on 2008-07-02
I am having some compatibility/finalizing issues when I use growisofs, in Feisty, to burn digital photos to (Verbatim) DVD-R on a MATSHITADVD-RAM UJ-842S.

Essentially:

1. I have used (successfully) the following command for an initial data burn session:

```
growisofs -Z /dev/hda -J -R -V lngst_day_1 ~/Desktop/DSC_0267.JPG
```

2. I have then used (successfully) the following command (and variations thereof) to add additional files (.jpg and .nef (nikon proprietary format/label)) and folder structures to the same DVD-R:

```
growisofs -M /dev/hda -J -R ~/Desktop/june202008/*.*
```

3. When I try to view the contents of the DVD-R on a MacBook, the MacBook can see the DVD-R and read its label (created using growisofs), but it can't see any of the files or folders burned to the DVD-R.

4. On the other hand, when I load the same DVD-R into an Xbox360, the Xbox360 can see the DVD-R and read the DVD-R's files (.jpg not .nef) and folder structures.

5. To experiment, I used xfburn to burn .nef files to a (Philips) cd-r (using the same drive) and the MacBook is able to read and open the files copied to the cd-r.

**NOTE:** There is a **finalizing cd phase** as a part of the xfburn process - so, I am wondering whether the issue with the MacBook and its inability to read the DVD-R might be related to a need to execute a growisofs finalizing process (...though not having finalized didn't seem to affect the Xbox360's ability to read the DVD-R)....

In any event, 

6. I tried to finalize the DVD-R with growisofs using the following commands...

```
growisofs -M -dvd-compat /dev/hda
```

```
growisofs -M /dev/hda=dev/zero
```

...and received these errors:

```
:-( unable to open64("dev/zero",O_RDONLY): No such file or directory
```

```
:-( unable to open64("-dvd-compat",O_RDONLY): No such file or directory
```

How do I finalize the DVD-R using growisofs?

Might the inability to finalize the DVD-R be the source of the MacBook problem - or could there be other issues at play?

Thanks for whatever insight you might be able to pass along.

---

### Post by alegallo on 2008-07-03
There is a bug in genisoimage 1.1.6-1ubuntu6, which is the one installed by default in hardy.

I had a similar problem, I made video DVD's which could be read flawlessly by Ubuntu or a stand-alone player, but which were reported as empty or full "of nothing" by Windows (i.e., 2,4 Gb of data, but unrecognizable by the system).

I had to force the installation of genisoimage1.1.6-1ubuntu3 from gutsy, and to lock that version, and now everything works.

Check [here]("http://ubuntuforums.org/showthread.php?t=801400&highlight=genisoimage"), it is not the thread I meant, but the solution doesn't change ;)

---

### Post by maclenin on 2008-07-03
Grazie **alegallo**!

How would I determine the version number of genisoimage?

I am running Feisty - so, it seems that I should not be encountering the "Hardy" bug? No?

What command do you use to "finalize" your DVD-Rs? One of those I have described?

Thanks, again, for your comments!

---

### Post by fearevilleet on 2008-07-05
> **alegallo said:**
> There is a bug in genisoimage 1.1.6-1ubuntu6, which is the one installed by default in hardy.

I had a similar problem, I made video DVD's which could be read flawlessly by Ubuntu or a stand-alone player, but which were reported as empty or full "of nothing" by Windows (i.e., 2,4 Gb of data, but unrecognizable by the system).

I had to force the installation of genisoimage1.1.6-1ubuntu3 from gutsy, and to lock that version, and now everything works.

Check [here]("http://ubuntuforums.org/showthread.php?t=801400&highlight=genisoimage"), it is not the thread I meant, but the solution doesn't change ;)

I am having the exact issues when burning dl-dvds. Everything burned fine before I upgraded. How would I remove genisoimage1 from hardy and lock in the gusty version?

---

### Post by maclenin on 2008-07-13
...just to follow-up (generally) any other thoughts re: growisofs and/or viable alternatives for burning data/music/video DVD(-R)s?

---

### Post by alegallo on 2008-07-14
You're right, I didn't notice you are using feisty ... 

Hmm, you can check the genisoimage version by searching it on Synaptic, the version is reported in the list too.

As for the rest, sorry but this poor newbie won't be able to help you ;)

---

