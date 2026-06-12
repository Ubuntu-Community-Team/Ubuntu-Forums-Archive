---
title: "Introducing pdf2htmlEX: converts PDF to HTML without losing format"
date: 2012-09-06
forum: The Cafe
---

### Post by coolwanglu on 2012-09-06
Demo comes first:
[http://coolwanglu.github.com/pdf2htmlEX/demo/demo.html](http://coolwanglu.github.com/pdf2htmlEX/demo/demo.html)

Another (with CJK):
[http://coolwanglu.github.com/pdf2htmlEX/demo/chn.html](http://coolwanglu.github.com/pdf2htmlEX/demo/chn.html)

Home page:
[https://github.com/coolwanglu/pdf2htmlEX](https://github.com/coolwanglu/pdf2htmlEX)

Ubuntu PPA
[https://launchpad.net/~coolwanglu/+archive/pdf2htmlex](https://launchpad.net/~coolwanglu/+archive/pdf2htmlex)


There are bascially 2 types of pdf-to-html converters:
One is roughly a pdf-to-text converter with a few pre-defined formats in HTML.
The other is render-everything-as-images converter, which loses all text and generated huge files.

But pdf2htmlEX takes advatanges of both, retaining both Text and Styling.
Features:
1.Extract and embed fonts from PDF
2.Optimizing for web while making sure render is precise
3.Non-text objects are rendered as images.
4.Single-file output mode -- I know you hate spearated font/image files

To compile & install
grab a recent poppler (>=0.20.3), make sure '--enable-xpdf-headers' is used for configure
grab the latest git version of fontforge [https://github.com/fontforge/fontforge](https://github.com/fontforge/fontforge), because I submitted a few features/bugs for pdf2htmlEX
the boost c++ library. (See detailed depended components in the project home page)
cmake
GCC that supports c++11

Any suggestion, fork/star-at-gihub, bug-report is appreciated.

---

### Post by coolwanglu on 2012-09-16
[0916 Update]
Added 2 more demo pages:
[http://coolwanglu.github.com/pdf2htmlEX/demo/cheat.html](http://coolwanglu.github.com/pdf2htmlEX/demo/cheat.html)
[http://coolwanglu.github.com/pdf2htmlEX/demo/geneve.html](http://coolwanglu.github.com/pdf2htmlEX/demo/geneve.html)

* Completed removed Boost
* Relaxed dependency of C++11, supports GCC no earlier than 4.4.6
* Links are now supported (In-document jumping is accurate to pages)
* Fixed an encoding problem for some fonts.

---

### Post by blaz_boy on 2013-04-26
does it contain a feature to preserve PDF Bookmarks?

---

### Post by coolwanglu on 2013-04-26
Depends on what do you mean by 'bookmarks'

If you mean the quick links to chapters, sections etc, they are called 'outlines' in PDF spec, and they are supported by pdf2htmlEX.

If you mean marks that you can create yourself, which should be supported by individual PDF viewers I think, they are not supported.

Why not just try it out and see?

---

### Post by blaz_boy on 2013-04-26
yes, i mean outlines, do you have a demo for it?, couldn't find any sign of outlines in the previous demos

---

### Post by coolwanglu on 2013-04-26
There is a guy using pdf2htmlEX for his resume:
[http://cv.raphink.info/](http://cv.raphink.info/)
the sidebar shows the outlines in it.

---

### Post by blaz_boy on 2013-04-26
this is great, thanks you.
also our PDF files will have over 1000 pages with more than 1.5GB this will be eatup 
memory for does the app support multi pages ? or it'll load up all pages at the same time?

---

### Post by coolwanglu on 2013-04-26
Yes, pages can be splitted, there is a switch `--split-pages`
You may find more info in the project page

---

### Post by urukrama on 2013-04-27
This looks fantastic!

I'm trying to compile this (from git) on Debian Testing, but I get the following error message:

```

-- checking for module 'poppler>=0.20.0'
--   package 'poppler>=0.20.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:279 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:333 (_pkg_check_modules_internal)
  CMakeLists.txt:18 (pkg_check_modules)


-- checking for module 'libfontforge>=2.0.0'
--   package 'libfontforge>=2.0.0' not found
Trying to locate old versions of fontforge...
Found fontforge.h: /usr/include/fontforge/fontforge.h
Found config.h: /usr/include/fontforge/config.h
Found fontforge: /usr/lib/libfontforge.so
Found gunicode: /usr/lib/libgunicode.so
Looking for libraries of python, which is required by fontforge, if you can link fontforge without python, you may disable this
-- Configuring incomplete, errors occurred!

```

I have python 2.7.3 installed (with dev packages), as well as python-fontforge. The [documentation]("https://github.com/coolwanglu/pdf2htmlEX/wiki/QuickStart") says "git version [of fontforge] is recommended to avoid annoying compilation issues". Is that a polite way of saying that without the git version of fontforge you can't compile this?

---

### Post by coolwanglu on 2013-04-28
> **urukrama said:**
> This looks fantastic!

I'm trying to compile this (from git) on Debian Testing, but I get the following error message:

```

-- checking for module 'poppler>=0.20.0'
--   package 'poppler>=0.20.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:279 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:333 (_pkg_check_modules_internal)
  CMakeLists.txt:18 (pkg_check_modules)


-- checking for module 'libfontforge>=2.0.0'
--   package 'libfontforge>=2.0.0' not found
Trying to locate old versions of fontforge...
Found fontforge.h: /usr/include/fontforge/fontforge.h
Found config.h: /usr/include/fontforge/config.h
Found fontforge: /usr/lib/libfontforge.so
Found gunicode: /usr/lib/libgunicode.so
Looking for libraries of python, which is required by fontforge, if you can link fontforge without python, you may disable this
-- Configuring incomplete, errors occurred!

```

I have python 2.7.3 installed (with dev packages), as well as python-fontforge. The [documentation]("https://github.com/coolwanglu/pdf2htmlEX/wiki/QuickStart") says "git version [of fontforge] is recommended to avoid annoying compilation issues". Is that a polite way of saying that without the git version of fontforge you can't compile this?

As you can see in the message, (an old version of) fontforge has been found. The problem is that you don't have a recent version of poppler.

---

