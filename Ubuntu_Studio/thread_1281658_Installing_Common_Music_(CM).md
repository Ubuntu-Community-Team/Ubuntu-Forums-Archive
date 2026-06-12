---
title: "Installing Common Music (CM)"
date: 2009-10-03
forum: Ubuntu Studio
---

### Post by mjertin on 2009-10-03
Hi!

I just managed to install [Common Music]("http://commonmusic.sourceforge.net/") on my Ubuntu 9.04 (amd64) after some struggling.

So here it how it worked for me:

Follow [these]("http://commonmusic.sourceforge.net/cm/readme.text") instructions.

Use Premake 3.7, NOT Premake4.

SndLib worked fine for me.

You'll need g++ and a whole bunch of additional libraries:

libfreetype6-dev
zlib1g-dev
libxcb-xinerama0
libxcb-xinerama0-dev
libasound2-dev
libxext-dev
libxinerama-dev
x11proto-xext-dev
x11proto-xinerama-dev
libgl1-mesa-dev
libglitz-glx1-dev
libglitz1-dev
libxcb-glx0
libxcb-glx0-dev
mesa-common-dev
xlibmesa-gl-dev
libglu1-mesa-dev


And I used Emacs-Snapshot.

I couldn't use *make install* for some reasons so I manually copied the binaries **~/.../cm/bin/cm**,** ~/.../cm/bin/Grace** and **~/.../cm/bin/GraceCL** into **/bin/**.

The *FIX pathname for your machine* in using CM in Emacs refers to the path where all the installation files live, NOT to the binaries in /bin/.

Hope this helps.
Cheers.
mjertin

---

### Post by ourfalli on 2011-08-09
Hello,

I couldn't find "libglitz-glx1-dev" & "libglitz1-dev" under Ubuntu's 10.10 Synaptic package installer but i found them on this link : [https://launchpad.net/ubuntu/maverick/i386/libglitz-glx1-dev/0.5.6-1build1](https://launchpad.net/ubuntu/maverick/i386/libglitz-glx1-dev/0.5.6-1build1)

Could someone kindly tell me where I can find a page explaining how to install these two packages, I am not expert in programming issues but If I had to learn to compile from source code I will do my best :)

Sincerely,
Ourfalli

---

### Post by jejeman on 2011-08-09
Did you try just to use binary from their site?

---

