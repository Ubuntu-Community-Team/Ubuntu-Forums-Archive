---
title: "Mozart/Oz on AMD64?"
date: 2007-10-08
forum: Repositories &amp; Backports
---

### Post by TheBlackNoodle on 2007-10-08
I'm trying to install the [Mozart](http://www.mozart-oz.org/) development environment on Ubuntu. I visited their site and it says that a stable release is available in the repositories. When I search for Mozart in synaptic, however, all I get is the documentation and the standard library. I have multiverse/universe enabled.

I found a .deb for Mozart in the Ubuntu packages list, but only for i386 and one other (I think PowerPC). I run an AMD64--I'm wondering if it just doesn't exist in that repo.

So, does anyone know how to get Mozart working on AMD64? I need to get this going pronto, as I have an assignment written in Oz due fairly soon.

---

### Post by alfredopaz7 on 2008-07-28
I have the same problem, anyone can help us!

---

### Post by N'Jal on 2008-08-15
You COULD try and download the RPM's and install them with alien (assuming of course alien is packaged for X86_64) also you could download the X86 versions and force the architecture, I am unsure how to do this as I do not run X86_64 but many websites should help you find out how to do this. Finally you could download mozart oz from it's svn and try to compile it yourself.

---

### Post by Keneo on 2009-02-26
*  Download the binary tarball here: [http://www.mozart-oz.org/download/view.cgi?action=tar&version=1.4.0](http://www.mozart-oz.org/download/view.cgi?action=tar&version=1.4.0)
    * make sure libc*-i386 is installed (this is libc6-i386 in ubuntu jaunty)
    * Unpack the tarball in /home/user/dev/mozart or something
    * Install emacs
    * add your executable oz files to your "path" 

export PATH=$PATH:/home/user/dev/mozart/bin/

You can add that line to your /home/user/.bashrc file to make it persistent (the path will be reset after closing the terminal) This last step isn't required, but it makes things easyer, you can always just start oz from within /home/user/dev/mozart/bin/ 

see [http://atomatix.net/wiki/index.php/Mozart-oz](http://atomatix.net/wiki/index.php/Mozart-oz)

---

### Post by MMXGN on 2010-05-12
OK, I know this is an old post, so sorry for bumping it, but I'm sure it will help whoever tries to do something with oz and complains about platform: **unknown-unknown**, or it will say that "**Oz exited abnormally with exit code 2**".

In mozart's path, there is a subdirectory named "platform". There, there exist some platform related files. For newer tarballs, it will be named "**linux-i486**" or something like that.

The only thing you have to do, is rename it (or copy with a new name, whichever fits you best) to "**unknown-unknown**" and try to start oz again.

Also, I found that step necessary if I wanted to install any oz extras (like Torsten's Strasheela).

Hope it helped.

---

### Post by jinisrolling on 2011-02-11
Thank you MMXGN, it helped.

---

### Post by blegat on 2012-10-15
I know this is an old post but it is always the first one Google shows
I have created [a wiki page]("https://help.ubuntu.com/community/Mozart") explaining how to install Mozart in Ubuntu 32-bit and 64-bit with a working deb file for 64-bit.

---

