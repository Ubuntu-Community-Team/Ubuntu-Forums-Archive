---
title: "Moodbar?"
date: 2006-11-11
forum: The Cafe
---

### Post by maniacmusician on 2006-11-11
I was playing around with my new amarok in edgy, and noticed this moodbar thing. It looks pretty neat, but the installing from source isn't working so well for me. So, can anybody build a package of it? or help me with building it from source if that's easier. If that's the case, I'll probably have to get the thread moved as well. 

I'd obviously prefer a package for ease of use and speed but I don't mind wading through compiling either. I've attached the output from the ./configure. I got instructions from [http://amarok.kde.org/wiki/Moodbar](http://amarok.kde.org/wiki/Moodbar) . Thanks.

---

### Post by .t. on 2006-11-11
I'll have a look-see.

---

### Post by .t. on 2006-11-11
Well it configures alright for me. What gcc version do you have? I think it used gcc-3.4 for me (I have that and 4 installed).

EDIT:
Builds and installs fine. Now... how do I use it?

---

### Post by maniacmusician on 2006-11-11
It's in newer versions of amarok...the one in edgy is new enough. settings > configure amarok and the option is halfway down the dialog box. 

I have gcc-4.0, 3.4, and 3.3 installed, and its still not working. I think it's still giving me the same error, I didn't read every single line though.

if it helps, I seem to be running the i686 kernel. uname-r shows "generic" but the config.log for moodbar shows that it's compiling for i686 so that must be what I'm running.

---

### Post by .t. on 2006-11-11
Do you have build-essential installed? This is very weird.

I've worked out how to use it now, thanks. I don't get what it's supposed to represent though... The "mood"? In what fashion?

---

### Post by maniacmusician on 2006-11-11
Wow, I feel like kicking myself. Really hard. I didn't have build-essential installed! I totally forgot that it didn't come preinstalled. [sigh] another stupid mistake. At least that wasn't the only thing; I also had to install the fftw3-dev and libgstreamer0.10-dev packages. So yeah, it's installed. I don't really know what it does either, I was just mucking about. I don't see how to use it though...I see it showing up along the track-line or whatever its called. I don't get the point of it. Oh well. 

Thanks for the help. I still can't believe I did that[-(

as for what it represents, I assume the lighter colors are happy moods and the darker colors are bad moods.

---

### Post by .t. on 2006-11-12
Eh, we all do it! And, yeah, I needed those dev packages as well.

EDIT:

And also!: It seems to change colour during an ostinato, where none of the tune or accompaniment changes.

---

### Post by Phoenix128zx on 2006-12-30
Hello! I got another way to compile moodbar and achieve maximum speeds(really):
- Download the latest moodbar source and the latest FFTW source from [http://www.fftw.org/]("http://www.fftw.org/")
- Install FFTW3 and FFTW3-DEV from SYNAPTIC, not SOURCE
- Compile moodbar using:
```

./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-k7
If you have an AMD K7, Athlon XP, or a non x64 Sempron
./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-sse
If you have a Pentium 3
./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-sse2
If you have a Pentium 4 or an Athlon64 or Core2

```
I have an Athlon XP, so I dunno if sse or sse2 are supported options in moodbar source, just try it!

Now moodbar will run perfect, but I got another step to perform:

- Extract and compile FFTW3:
```

./configure --enable-k7
If you have an AMD K7, Athlon XP, or a non x64 Sempron
./configure --enable-sse
If you have a Pentium 3
./configure --enable-sse2
If you have a Pentium 4 or an Athlon64 or Core2
Add --enable-threads If you have a Pentium 4 with hyper-threading, multiple CPU or a multi-core CPU

```
This last step is VERY important, because FFTW3 is the main library that moodbar use to perform calculations, so it will be very fast after this optimization.

You may ask why install FFTW3 from Synaptic and then compile it from source:
Because I don't know how to install dev package from source, if anyone knows...Let me know it!

P.S. Compile FFTW3 always AFTER installing it from Synaptic, because during moodbar configuration you may get version error(FFTW3 from synaptic is actually older than FFTW3 source, so moodbar checks dev version and installed version). But it seems that moodbar supports any FFTW3 version after being compiled.
...Oh, and excuse me for my bad english!
Good-bye!!

---

### Post by durand on 2007-02-03
bit confused about what moodbar is but it compiled properly after installing fftw3-dev:
```
sudo apt-get install fftw3-dev
```
Anyway, attached moodbar deb though I compiled it in feisty. Might work in previous versions of ubuntu.

---

### Post by deadlydeathcone on 2007-02-03
There's also a repository here:
```
deb http://cl.naist.jp/~eric-n/ubuntu-nlp edgy misc
```

There's also a repository for the newest Amarok:
```
deb http://kubuntu.org/packages/amarok-144 edgy main
```

---

### Post by durand on 2007-02-04
i think the newest amarok is in feisty repos.

---

### Post by phido on 2007-02-23
Amarok 1.4.5 can be found here
```
deb [http://kubuntu.org/packages/amarok-latest]("http://kubuntu.org/packages/amarok-144") edgy main    *or*
deb [http://kubuntu.org/packages/amarok-145]("http://kubuntu.org/packages/amarok-144") edgy main

```

---

