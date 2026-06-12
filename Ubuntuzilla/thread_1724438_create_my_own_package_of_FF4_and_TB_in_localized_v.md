---
title: "create my own package of FF4 and TB in localized version"
date: 2011-04-08
forum: Ubuntuzilla
---

### Post by artynet on 2011-04-08
I'd like to create my own packages of Firefox 4.0 and Thunderbird 3.1.9 starting from the binaries in my language (italian) and eventually open my PPA for italian users. Which are the steps to follow to make a deb like nanotube does ? I hope you can help me

    thx in advance

           Arturo

---

### Post by Karlchen on 2011-04-08
Hello, Arturo.

Guess a good approach is by

[LIST]
[*]inspecting a few of  the .DEB packages created by nanontube.
You may be lucky and still find some such .DEB packages in the folder /var/cache/apt/archives.
[*]downloading the corresponding original Mozilla .tar.bz2 files and compare their content to nanotube's .DEB packages
[*]reading a few tutorials on how to create .DEB packages like e.g.
+ [Ubuntu Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete")
+ [How To Create A .DEB Package [Ubuntu / Debian]]("http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html")
[*]converting the Mozilla .tar.bz2 files into .DEB packages and testing what happens when the are processed and installed by Synaptic on a dedicated Ubuntu testing machine.
[/LIST]
I am somewhat afraid it may be necessary to have a testing environment for each supported Ubuntu release once you start releasing your .DEB packages to the public.

HTH,
Karl

---

### Post by lovinglinux on 2011-04-08
Talk to [SilverWave]("http://ubuntuforums.org/showthread.php?t=1352580"). He is currently providing his own Firefox ppa repositories.

---

### Post by arty.net on 2011-04-11
i think it should be a trivial thing.....after all nanotube puts the binary version of firefox in the deb and decides the folder of installation. Is there a way to contact nanotube himself ?

---

### Post by artynet on 2011-04-13
OK i did it ! ! ! i slightly modified nanotube's script and now i am able to get the localized version of firefox and thunderbird ! ! ! I have an x64 version too ! ! ! I'll soon open my ppa ! ! ! Stay tuned

---

### Post by nanotube on 2011-04-14
karlchen, lovinglinux: fyi, the mozillapackager.py script that's in the ubuntuzilla code repo automates the .deb creation...

as arty.net discovered, it is fairly easy to tweak to make it work for other locales and machine arch.

---

### Post by Karlchen on 2011-04-14
Hello, nanotube.

Thank you for this hint. I will sure have a look at the mozillapackager.py script.

Cheers,
Karl

---

