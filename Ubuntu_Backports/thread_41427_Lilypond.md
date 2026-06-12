---
title: "Lilypond"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by dansoper on 2005-06-13
I have got Lilypond 2.2.6 from Universe, but was wondering if anyone knew how to get a more recent version of Lilypond working.  They are currently on 2.4.6 and about to release 2.6.

I tried using a repository from Debian and got a 2.4.n version, but it didn't run properly, giving a segmentation error.

Any help that can be given will be gratefully accepted!  The reason I am so keen on it is that the Syntax has changed between versions, and later versions are more powerful.

Thanks,

Dan

---

### Post by Seth on 2005-06-13
[QUOTE=dansoper]I have got Lilypond 2.2.6 from Universe, but was wondering if anyone knew how to get a more recent version of Lilypond working.  They are currently on 2.4.6 and about to release 2.6.

I tried using a repository from Debian and got a 2.4.n version, but it didn't run properly, giving a segmentation error.

Any help that can be given will be gratefully accepted!  The reason I am so keen on it is that the Syntax has changed between versions, and later versions are more powerful.

Thanks,

Dan[/QUOTE]
 They're on their last 2.6 release candidate, so the final should be out within two weeks at the very latest. This will also require some backported libraries as even the newer versions of 2.4 need some newer versions, but still shouldn't be too complicated. Bump this when 2.6 comes out :)

---

### Post by Gustav on 2005-06-14
[QUOTE=dansoper]I have got Lilypond 2.2.6 from Universe, but was wondering if anyone knew how to get a more recent version of Lilypond working.  They are currently on 2.4.6 and about to release 2.6.

I tried using a repository from Debian and got a 2.4.n version, but it didn't run properly, giving a segmentation error.

Any help that can be given will be gratefully accepted!  The reason I am so keen on it is that the Syntax has changed between versions, and later versions are more powerful.

Thanks,

Dan[/QUOTE]
 I totally agree, the syntax in the newer versions are much better.

If are trying the 2.4.5 version of Debian (sid) you have to upgrade some libraries from Debian as well.

After looking it seems that you only need to install ec-fonts-mftraced (wich can be found in breezy but not in hoary).

---

### Post by dansoper on 2005-07-02
As advised, I am now bumping this post.

Lilypond 2.6 has recently been released!!!

I would really love to see it appear in the backports.  Anyone interested?

Thanks,

Dan

---

### Post by dawynn on 2005-08-28
Check the lilypond website ([www.lilypond.org)](www.lilypond.org)).

They've chosen to go the autopackage route.  That means that, no matter what flavor of Linux you're using, you can use the latest Lilypond.  For flavors that choose not to use recent Lilyponds (Ubuntu -- 2.2, Debian -- 2.4) this is great news.

I've installed 2.6.3 using autopackage, and its working great!  As stated previously, the syntax is much nicer than 2.2, and the fonts are much better than the kludgy 2.4 ecfonts-mftraced work-around.

-- David

---

