---
title: "WinFF?"
date: 2008-06-12
forum: The Cafe
---

### Post by kevin11951 on 2008-06-12
I have been using [winff]("http://www.winff.org/") for over a month now, and have found it amazing! its very VERY easy to use, but i couldn't find it in the repos, and decided it was probably closed source, or something... but then i found this: [http://www.winff.org/index.php?option=com_content&view=article&id=44&Itemid=53](http://www.winff.org/index.php?option=com_content&view=article&id=44&Itemid=53) , its open source! so why isnt it in the repos, and how can i get it there?

---

### Post by Ub1476 on 2008-06-12
Just a guess, but maybe you can mail the WinFF dev(s) and ask why it's not there. 

I agree it's a very good program.

---

### Post by conscious on 2008-06-12
See this:
[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by kevin11951 on 2008-06-12
im not the only one who wants this: [https://bugs.launchpad.net/ubuntu/+bug/172804](https://bugs.launchpad.net/ubuntu/+bug/172804) :D:guitar::D:guitar::D:guitar:  Now I really cant wait for intrepid... for now, i will go compile it.

---

### Post by dje on 2008-06-12
> **kevin11951 said:**
> im not the only one who wants this: [https://bugs.launchpad.net/ubuntu/+bug/172804](https://bugs.launchpad.net/ubuntu/+bug/172804) :D:guitar::D:guitar::D:guitar:  Now I really cant wait for intrepid... for now, i will go compile it.

why compile it when there is a [deb package]("http://winff.googlecode.com/files/winff-0.41-i386.deb")?

---

### Post by kevin11951 on 2008-06-12
> **dje said:**
> why compile it when there is a [deb package]("http://winff.googlecode.com/files/winff-0.41-i386.deb")?

i thought someone would ask; i use 64bit, and here are the instructions for 64bit users:



The author is unable to provide 64-bit packages for winff but I can confirm that the latest version of winff (0.41 ATM) compiles and runs without any problem under Hardy x86-64. I couldn't find any instructions on how to compile winff in its docs but it pretty simple:

1 - Install

fpc
fpc-source
lazarus

2 - Download and uncompress zip of latest winff source code somewhere

3 - Run Lazarus IDE (Applications > Programming > Lazarus )

4 - Use File/Open menu to open the file called winff.lpi, in the top level of you winff source dir

5 - Choose 'Build All' from Lazarus' 'Run' menu and then you'll find a winff binary in the source folder

Be much nicer to have it in the Ubuntu repo tho so 64-bit users don't have to do all this!

---

### Post by billgoldberg on 2008-06-12
I agree winff is a great gui for ffmpeg.

To bad the ffmpeg version in the ubuntu repo's is lacking some features.

So before you install winff, you have to remove it and install the full one.

---

### Post by dje on 2008-06-12
> **kevin11951 said:**
> i thought someone would ask; i use 64bit, and here are the instructions for 64bit users:



The author is unable to provide 64-bit packages for winff but I can confirm that the latest version of winff (0.41 ATM) compiles and runs without any problem under Hardy x86-64. I couldn't find any instructions on how to compile winff in its docs but it pretty simple:

1 - Install

fpc
fpc-source
lazarus

2 - Download and uncompress zip of latest winff source code somewhere

3 - Run Lazarus IDE (Applications > Programming > Lazarus )

4 - Use File/Open menu to open the file called winff.lpi, in the top level of you winff source dir

5 - Choose 'Build All' from Lazarus' 'Run' menu and then you'll find a winff binary in the source folder

Be much nicer to have it in the Ubuntu repo tho so 64-bit users don't have to do all this!

fair enough, i don't run 64 bit

---

### Post by jonpackard on 2009-10-25
It seems 64-bit .deb's are available here:
[http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)

Edit: The repository at winff.org works fine in 64-bit now. My problem was that I needed to install libavcodec-extra-52. WinFF is working fine for me now on Karmic 64-bit.

---

### Post by stinger30au on 2009-10-25
im sure if you enable all repos in ubuntu you can install winff from shell cos thats how i have done it

---

### Post by chris200x9 on 2009-10-25
> **kevin11951 said:**
> i thought someone would ask; i use 64bit, and here are the instructions for 64bit users:



The author is unable to provide 64-bit packages for winff but I can confirm that the latest version of winff (0.41 ATM) compiles and runs without any problem under Hardy x86-64. I couldn't find any instructions on how to compile winff in its docs but it pretty simple:

1 - Install

fpc
fpc-source
lazarus

2 - Download and uncompress zip of latest winff source code somewhere

3 - Run Lazarus IDE (Applications > Programming > Lazarus )

4 - Use File/Open menu to open the file called winff.lpi, in the top level of you winff source dir

5 - Choose 'Build All' from Lazarus' 'Run' menu and then you'll find a winff binary in the source folder

Be much nicer to have it in the Ubuntu repo tho so 64-bit users don't have to do all this!

wouldn't it be easier to y'know compile it the normal way?

---

### Post by RichardLinx on 2009-10-25
You seem to not have noticed that this thread is over a year old. It doesn't bother me when an old thread resurfaces, but just so you know why WinFF wasn't available in the repos for the OP was because at the time of posting it wasn't available.

---

### Post by Excedio on 2009-10-26
<-------- Not a Mod but....

Necromancing.

```
Close Thread Code
```

---

### Post by cariboo on 2009-10-26
Winff is in the Jaunty and Karmic repositories. Check:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

if you're not sure where to get a package.

This thread is closed.

---

