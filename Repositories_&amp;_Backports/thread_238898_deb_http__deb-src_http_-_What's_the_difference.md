---
title: "deb http / deb-src http - What's the difference?"
date: 2006-08-18
forum: Repositories &amp; Backports
---

### Post by Uncle Spellbinder on 2006-08-18
Just curious as to what the difference is between *deb http* and *deb-src http* in the repos. Are they both necessary? I heard/read somewhere that it has something to do with download speed. As I'm on an 8 MBPS cable internet, speed is not an issue. Any other difference?

---

### Post by matthew on 2006-08-18
The deb-src repos contain the source code files for all the software contained in binary form in the deb repos. If you don't plan to download the source code you can safely comment out the deb-src repos and not lose access to anything.

EDIT: this could be a bit faster because there are fewer repos to check for updates when using Synaptic, aptitude, apt-get, etc. The speed difference isn't usually significant, but it can exist.

---

### Post by ciscosurfer on 2006-08-18
It has to do with whether or not you would just like to download a pacakge (deb) or would like the source code (deb-src) to compile a package as well...

Unless you are accustomed to compiling packages (literally building them from source code), there is no reason and/or no need to grad the deb-src files as well.  Additionally, when it comes time to remove a program, and you're using a package instead of compiled code, you can get rid of it quite easily as Aptitude (or front-end Synaptic) keeps track of your files and depencies.  This is not true of compiled code.

So yes, if you comment out your deb-src files, your updates will go quicker because apt will not need to grab the souce code.  In your /etc/apt/sources.list file, simply place an "#" in front of any line with deb-src (do it from within Synaptic...unchecking the lines that say 'source' at the end (you may have to widen the repository window to see whether or not it is a binary line (deb, packages) or a source line (deb-src, source code), save the file, and/or check "OK" and then reload your list at the command line by issuing the 'update' command```
sudo aptitude update
```in order to refresh you repository list....click the Reload button in Synaptic to do the same.

You will get a speed increase as you update/download b/c you're not searching/donwloading the sources files.

---

### Post by Uncle Spellbinder on 2006-08-18
@ matthew

 :D Thanks. Appreciate the quick response.

---

