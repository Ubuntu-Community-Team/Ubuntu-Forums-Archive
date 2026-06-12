---
title: "My experience with KompoZer - Nvu fork"
date: 2007-01-13
forum: The Cafe
---

### Post by Phatfiddler on 2007-01-13
[Kompozer - Nvu's unofficial bug-fix release]("http://kompozer.net/")

After switching my laptop to Debian Sarge, I realized that I could not get Nvu, since it had been removed from the repositories.  The Nvu project seemed to be at a stand-still until the release of 2.0, so there was a fork, which is called KompoZer.  This new program boasts the ease of use and WYSIWYG editor seen in Nvu, but takes everything a step forward by implementing new features and stability.

However, KompoZer is NOT available as a .deb file.  It is only available as source, .rpm, and a few other specific formats.

**The Fun Begins**

While I understand that this install is on Debian, and not Ubuntu, I thought that members here could benefit from such knowledge since an Ubuntu version is unavailable as well, and is not available in the repositories.

So I decide to compile from source myself.  After downloading the tarball and unpack it, I notice that it is not like a normal source file.  SInce the Nvu project and KompoZer are licensed under the Mozilla project, you get a nice, confusing, document-free source directory.  Good lcuk finding what you need.  Not a single folder is labeled Nvu, kompozer, or anything similar.  So after googling around for a while, I find somewhat-readable directions for the compile.  I unpack the tar(did this in previous step), and make the file.  Uh oh, dependancies problems.  No biggie, just install them, right?  Well, maybe not.  While you are alerted that -lXt is missing, it does not tell you what library/dependancy contains it.

aptitude search -lXt turns up nothing.  More googling.  I finally find what I need, and install the required dependancy, make, and see what happens.  This happens about 8 times, with 8 different dependancies before I give up on the thing.  An hour wasted trying to get this thing to work.  I delete the tarball, and the folder that was extracted.

About this time, I notice that there is an .rpm available for use.  Hmm.  So I apt-get install alien to get the appropriate program, and transform the .rpm into a .dev in less than 1 minute.  I dpkg the .dev, watch it install, and then the terminal returns to normal awaiting my input.

Is it installed?  Did it work?

I type in "kompozer" in the termianl.  There is a pause........

Success!  In less than 5 miutes, the whole thing is up and running.  It's super fast, and doesn't seem to be nearly as buggy as Nvu was.  So how is KompoZer?  Excellent, and just as easy to use as Nvu.


So long story short - use the .rpm file and alien if you want KompoZer!!!

---

### Post by maddog39 on 2007-01-13
Looks like a good program. So I am going to install it and see what my results are.

---

### Post by claydoh on 2007-01-13
another option is to download the linux i686 binary tarball, extract it and click on the file called 'kompozer'

Of course this does not install it, but you can easily check it out.

---

### Post by shane2peru on 2007-09-24
There is now a deb for anyone interested click here:

[http://sourceforge.net/project/showfiles.php?group_id=170132]("http://sourceforge.net/project/showfiles.php?group_id=170132")

Shane

---

