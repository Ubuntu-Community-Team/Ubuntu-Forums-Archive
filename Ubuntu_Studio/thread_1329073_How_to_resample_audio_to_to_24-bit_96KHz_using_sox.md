---
title: "How to resample audio to to 24-bit 96KHz using sox"
date: 2009-11-17
forum: Ubuntu Studio
---

### Post by rac9876 on 2009-11-17
I am trying to resample some 16-bit, 44.1KHz WAV files to 24-bit, 96KHz using [SoX]("http://sox.sourceforge.net/"). From the [SoX man page]("http://sox.sourceforge.net/sox.html") I have pieced together this command:

```
sox zzzin.wav -b 24 zzzout.wav rate -v 96k norm
```

But that doesn't work - I get the following error:

> sox soxio: Can't open input file `24': No such file or directory

The SoX version is v14.0.0. Can anyone help me with the correct syntax? Thanks in advance.

---

### Post by Stochastic on 2009-11-17
Well that is the correct syntax (from what I know).  I even tried it on my machine just now and it worked fine (mind you the input file was at 48000 rather than 44100 - but that wouldn't cause the error you're getting).

In your user info to the left it says you're running Karmic (and so am I) but my version of sox is 14.3.0 (from the repositories).

I might guess that you have a late-night typo somewhere along the lines?  Maybe the input filename?

---

### Post by rac9876 on 2009-11-19
> **Stochastic said:**
> Well that is the correct syntax (from what I know).

Thanks for the advice. I tried it in version 14.3.0 and it did work. I use both Xubuntu 9.10 and, for music, a version of 64 Studio based on Linux Mint 5. In that distro I have an older version of sox, which seems to have a problem with this command. I'll just have to convert my samples using the newer version of sox.

---

