---
title: "Acroread Error - libpixbufloader-xpm.so"
date: 2011-06-23
forum: System76 Support
---

### Post by sgy on 2011-06-23
I recently bought the Wild Dog Performance with Ubuntu 11.04 64-bit pre-installed.  When I open a pdf with acroread I get a long list of errors, of which the most important one seems to be:

(acroread:3785): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

How do I go about installing the missing module?  I have found the following resource:

[http://rpmfind.net/linux/rpm2html/search.php?query=libpixbufloader-xpm.so&submit=Search+...&system=&arch=x86_64](http://rpmfind.net/linux/rpm2html/search.php?query=libpixbufloader-xpm.so&submit=Search+...&system=&arch=x86_64)

but I am unsure which of the packages to install, as well as how to install it.  I tried once with rpm and received a slew of failed dependencies along with a warning that I should use alien instead.  It didn't install.

I can view the pdf file, but I don't like the errors, and the icon when alt-tabbing is a red circle with a line through it.  Neither of these problems prohibit me from viewing files in Acrobat, but I would like to learn how to fix this nuisance.

Any help you have to offer is appreciated.

Thanks,

Sam

---

### Post by isantop on 2011-06-23
RPM files are packages for a different type of distribution. They are designed for distros that use the Red Hat Package Manager and Yum, while Ubuntu uses Debian's packaging system and Advanced Packaging Tool (APT). Packages for Ubuntu will end in .deb instead of .rpm.

Ubuntu also uses something called the Ubuntu Software Center to manage software. You can find system tools, add-ons, and whole applications there. Essentially, it uses APT to automatically download and install .deb files.

Which RPM package did you try to install? There is probably a .deb package available somewhere, and it may be available through the software center.

---

### Post by sgy on 2011-06-23
I downloaded gtk2-32bit-2.20.1-2.13.x86_64.rpm, installed rpm through the Ubuntu Software Center, and then ran:

```
rpm -i gtk2-32bit-2.20.1-2.13.x86_64.rpm
```

This is when I got all the failed dependencies.

I'm not intent on using rpm it was just the format that I found when I searched online.  I looked in the Synaptic Package Manager for things like gtk2 and libpixbufloader-xpm but found too many results and I couldn't sort through them to find the right one.

If you can point me to the right deb package, either online or through Synaptic I think I will have no problem installing it.

Am I correct in believing that this problem is a result of running the 64 bit version of Ubuntu?

Also, I added a signature that mimics yours.  Please let me know if you have any comments about it.  I'm not sure if I included everything, or too much, or whatever.

Thanks again.

---

### Post by isantop on 2011-06-23
Do you need to use acroread to view PDF's? Ubuntu includes an open source program for reading them. It's officially called Evince, but it typically shows up in Ubuntu as "Document Viewer". It reads PDF files just fine.

As for the signature, it's really not a required bit, and you can really put just about anything you want to in there, even if it has nothing to do with your system.

---

### Post by sgy on 2011-06-23
I am trying to improve my Ubuntu/Linux knowledge by dealing with all problems, including ones for which it is possible to ignore or work around.  I suppose I have been using Acrobat instead of evince simply out of habit, and perhaps switching over to an exclusive use of evince is desirable.  I was aware of evince, and it does work fine for me.  Does evince handle hyper-links the same way as Acrobat?

I was worried initially that it was a 64-bit problem and if I am going to encounter problems like this in the future I would like to be more capable of dealing with them head on.

Your comments about rpm and deb have already been very helpful.

Any thoughts on how to fix Acrobat, or should I just avoid it?

Thanks.

ps Should I, and can I, move this thread out of the System76 Support subforum?  Perhaps this isn't the right place for it.

---

### Post by isantop on 2011-06-23
I would just avoid it. I personally tend to stick with the applications that come with Ubuntu, since they're generally the most tested and integrated. There are a couple of exceptions, but typically the defaults all work fine for me. As for how Evince handles hyperlinks, I've never had a problem, but then, I don't know how Acroread does it.

---

