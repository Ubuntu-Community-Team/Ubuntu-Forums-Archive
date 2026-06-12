---
title: "How do I install a newer version of Inkscape?"
date: 2009-03-16
forum: Ubuntu Studio
---

### Post by potiphera on 2009-03-16
I'm using Ubuntu Studio Gutsy, and the version of Inkscape in the repository is 0.45.1.  I'd like to install 0.46 -- how do I do that?  Will I have to compile from the source on the Inkscape site, and if so, could someone explain to me how that is done?  Thanks so much!

---

### Post by buldozerceto on 2009-03-16
From inscape documentation:
   sudo apt-get install inkscape
will install the latest svn version.

---

### Post by potiphera on 2009-03-16
That doesn't do anything, though, because I already have the latest version in my repository (0.45.1) installed.  I'd like to install 0.46.

Are you getting this from [here]("http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu")?  I think that would work if I could add their repository, but they only list nightly builds for Hardy, Intrepid, and Jaunty.

---

### Post by potiphera on 2009-03-16
(bump)

I've been trying to compile following [these instructions]("https://help.ubuntu.com/community/CompilingEasyHowTo"), but when I do sudo apt-file update, it tells me "cannot stat '/cdrom/dists/gutsy/Contents-i386.gz': No such file or directory."  What should I do about that?

---

### Post by Guruji on 2009-03-16
try these instructions:
[http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)
check " Compiling unstable developement version "
the instructions are for hardy, intrepid and jaunty but might work on gutsy.

but.. why not simply upgrade your ubuntu to hardy or intrepid?

---

### Post by potiphera on 2009-03-16
OK, I finally figured out how to compile from source by reading the instructions in the INSTALL file that was in the source tarball.

> **Guruji said:**
> but.. why not simply upgrade your ubuntu to hardy or intrepid?

I was under the impression that this was difficult.  Is it?

---

### Post by vhof on 2009-03-18
> **potiphera said:**
> OK, I finally figured out how to compile from source by reading the instructions in the INSTALL file that was in the source tarball.



I was under the impression that this was difficult.  Is it?

There is a good reason to stay with a previous Ubuntu version, and it's *stability*.
[Hardy is more stable than Intrepid or Gutsy (since the former hasn't been stable for as long and the latter is only updated for security issues).]("http://digg.com/linux_unix/Time_For_Ubuntu_To_Move_To_Stability?t=21825942")

Yesterday I installed Inkscape from source using [these instructions]("http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu") and it's working, although crashing. 

I wonder if anyone has successfully installed Inkscape from SVN.

---

### Post by Roanoke on 2009-03-18
[https://launchpad.net/~inkscape.testers/+archive/ppa](https://launchpad.net/~inkscape.testers/+archive/ppa)
You can find an SVN PPA there. I would recommend upgrading to hardy, because it's an LTS release (meaning it's stable and it's supported for a long time) and because it has newer packages in the repos.
Oh, and I have managed to compile and install inkscape's SVN manually.

---

