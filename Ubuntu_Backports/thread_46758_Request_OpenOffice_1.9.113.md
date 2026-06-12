---
title: "Request: OpenOffice 1.9.113"
date: 2005-07-06
forum: Ubuntu Backports
---

### Post by buellman on 2005-07-06
hi!

could openoffice 1.9.113 be backported? it's allready in breezy.
[http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org2/](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org2/)

thanks and greets.
buellman

---

### Post by abandoned_hussam on 2005-07-06
I would really love to see that as well. If not this build, at least the final version when it is out.

---

### Post by rykel on 2005-07-06
Why can't OpenOffice.org simply be made available as an [**autopackage**](http://www.autopackage.org)  file?

That way, all of us can simply download the latest version and install it easily.

---

### Post by davegod75 on 2005-07-06
[QUOTE=rykel]Why can't OpenOffice.org simply be made available as an [**autopackage**](http://www.autopackage.org)  file?

That way, all of us can simply download the latest version and install it easily.[/QUOTE]
 autopackage looks pretty cool

---

### Post by jdong on 2005-07-06
ooh, finally Breezy gets a new Openoffice.

Sure, I'll take on the task of compiling this beast for i386, using my Athlon64 beast. Of course, there's a pretty solid chance that dependency problems won't allow us to get this backport.

In the meantime, there are ways to convert Openoffice.org official binaries to debs (google ooo-debianize), and I've had good luck getting those scripts to work with newer versions with just a few hacks.

---

### Post by jdong on 2005-07-06
[QUOTE=rykel]Why can't OpenOffice.org simply be made available as an [**autopackage**](http://www.autopackage.org)  file?

That way, all of us can simply download the latest version and install it easily.[/QUOTE]

Because Linux distros are STILL too diverse, especially when dealing with huge programs like Openoffice, to install with autopackage.

In this case, Openoffice.org must link to specific versions of GNOME libraries, amongst its other 20+ build dependencies, and the chances of those versions being binary-compatible across distributions... heck even within versions of the same distribution, are VERY VERY slim.

It'll take a miracle in order for Autopackage to start working with packages of this enormousity.

---

### Post by jdong on 2005-07-06
Ok, OOo2 in Breezy uses the GCJ 4.0 native Java environment... The GCC4.0 backports for Hoary that I made are currently insufficient for these purposes.

As of now, I'll DEFER this backport, as there's parts of the distro (Firefox backport) that could break if I mess with the GCC toolchain.

---

### Post by shidai.liu on 2005-07-09
Is openoffice2 1.9.79 in hoary?

---

### Post by Seth on 2005-07-09
Yes, it is in universe.

---

### Post by shidai.liu on 2005-07-09
[QUOTE=jdong]Ok, OOo2 in Breezy uses the GCJ 4.0 native Java environment... The GCC4.0 backports for Hoary that I made are currently insufficient for these purposes.

As of now, I'll DEFER this backport, as there's parts of the distro (Firefox backport) that could break if I mess with the GCC toolchain.[/QUOTE]

I'm eager to see OpenOffice 2. It's pretty stable and has so many new features compared to 1. Besides, it starts up much faster.

I've used openoffice 2 in windows to create my thesis. Just like its PDF function. All the cross references and bookmarks become links in pdf. Very impressive.

Hope you can find a walkaround to this problem! Many thanks.

---

### Post by SpEcIeS on 2005-07-10
I am currently using OpenOffice 1.9.113, and it is pretty nice. Try this as a possible solution to the craving: **[Ubuntu Message Board - OpenOffice 2 Beta Installation](http://ubuntuforums.org/showthread.php?t=30866&highlight=OpenOffice+2.0)**.  :grin:

---

