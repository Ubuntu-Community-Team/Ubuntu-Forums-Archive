---
title: "Kde4"
date: 2007-08-08
forum: The Cafe
---

### Post by LaRoza on 2007-08-08
I know many people that are interested (excited, joyful ,aroused...) in the new KDE, KDE 4.

I tried out the live cd, [http://home.kde.org/~binner/kde-four-live/](http://home.kde.org/~binner/kde-four-live/), and here is my review:

A few notes first:

* I like GNOME
* I don't disklike KDE, and use it on my other computers
* I realize that KDE4 is beta

The look is pretty, and sleak. The effects and transitions are nice, even running live on a computer with less than 512 MB of RAM.

It's useabiltiy is not compromised, and it is pretty stable, even in the shaky conditions in which I tested it (and the fact it is still beta).

KDE4 is pretty nice, but it is nothing I would make a point of using it over GNOME, but for people who want a nice, fancy GUI, KDE4 is something you might want.

One note, it didn't crash at all, although I did get two messages telling me of *something* going wrong, although I couldn't figure out what. Vista is much less stable, even with all the effects disables, experience here.

---

### Post by miggols99 on 2007-08-08
With the live cd (well in the VM) it crashed frequently and some apps didn't open. After a while none of them did. Maybe I'll have better luck with it on a cd...

---

### Post by happysmileman on 2007-08-08
I'm getting the LiveCD now but frankly I'm surprised... i have KDE4 installed on Kubuntu and it doesn't crash much...

---

### Post by LaRoza on 2007-08-08
I was surprised by the stability of KDE4.

---

### Post by miggols99 on 2007-08-08
I'm guessing it would be much more stable if you install it to your HD. The openSUSE base doesn't help...

---

### Post by SeanTater on 2007-08-08
Open Konqueror. Go to the "Window" menu - press the "Show terminal emulator" button. When I did that, I got the Printing configuration dialog. Is that any indication of it's current stability? But Konsole died on me saying it could not connect to d-bus. I reset dbus and it still did not work.. I think I will wait until a beta or two from now to make any opinions..

---

### Post by proalan on 2007-08-09
i was going to give it a go but 880MB+ space required!

I'm expecting it to live to its hype when i finally try it out in the future.

---

### Post by stmiller on 2007-08-09
Check out this ars article that has some good info:

[http://arstechnica.com/journals/linux.ars/2007/08/06/the-first-kde-4-0-beta-hits-the-streets](http://arstechnica.com/journals/linux.ars/2007/08/06/the-first-kde-4-0-beta-hits-the-streets)

The Phonon multimedia/audio API will be incredible.

---

### Post by awakatanka on 2007-08-10
here is also a livecd from Mepis with KDE4 beta 1.

> Warren Woodford of MEPIS has built KDE4-Beta1 Live DVDs to verify the compatibility of KDE 4 with SimplyMEPIS 7.x. The 32 and 64 bit DVD isos are available from the testing directory of the MEPIS subscriber site and the MEPIS public mirrors.
Warren said "I decided to share my KDE 4 Beta 1 isos, so others could take a first look at KDE 4 and also to demonstrate that I'm serious about the commitment that MEPIS 7.x will be incrementally upgradable. We plan to do another KDE 4 integration every few weeks. We expect that KDE 4 will not be final in time for the MEPIS 7.0 release, but by integrating KDE 4 now, we can insure that 7.0 will be "KDE 4 ready."

Source : [http://www.mepis.org/node/13929](http://www.mepis.org/node/13929)
Download : [ftp://ftp.ibiblio.org/pub/linux/distributions/mepis/testing](ftp://ftp.ibiblio.org/pub/linux/distributions/mepis/testing) 
Our a other link on the download page of mepis.org

---

### Post by dantrevino on 2007-08-12
> **stmiller said:**
> Check out this ars article that has some good info:

[http://arstechnica.com/journals/linux.ars/2007/08/06/the-first-kde-4-0-beta-hits-the-streets](http://arstechnica.com/journals/linux.ars/2007/08/06/the-first-kde-4-0-beta-hits-the-streets)

The Phonon multimedia/audio API will be incredible.


Er.... phonon is only as powerful as the underlying library.  I personally still dont understand why you wouldnt just write to gstreamer instead.  Phonon just sits on top of gstreamer (among others).

dan

---

### Post by GeneralZod on 2007-08-12
> **dantrevino said:**
> Er.... phonon is only as powerful as the underlying library.  I personally still dont understand why you wouldnt just write to gstreamer instead.  Phonon just sits on top of gstreamer (among others).

dan

Phonon is slightly more powerful, as it automatically grants network transparency to any of the underlying libraries it wraps via kio_slaves.   I believe it also supports features such as gapless playback, per-application volume control and transparent switching of sound output devices mid-playback, although I don't know whether gstreamer has these already.  

Anyway, the primary reason is that gstreamer is not guaranteed to have a stable API/ABI, which means that any apps written against it in its current form may not work with later versions: Phonon makes this a non-issue.  It's also not guaranteed that all of KDE's supported platforms will have a mature and supported gstreamer port, in which case it makes more sense for Phonon to wrap the platform's native multimedia API instead.

---

