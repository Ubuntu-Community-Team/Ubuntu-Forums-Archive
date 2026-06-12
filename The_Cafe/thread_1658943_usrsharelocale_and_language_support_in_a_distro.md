---
title: "/usr/share/locale and language support in a distro"
date: 2011-01-03
forum: The Cafe
---

### Post by jhsu802701 on 2011-01-03
I recently started a new distro called Swift Linux ([www.swiftlinux.org](www.swiftlinux.org)), which is lightweight, has a superior repository, and is user-friendly.  Swift Linux is based on antiX Linux.

I'm looking for things to cut from antiX Linux in the process of creating Swift Linux.  Without cutbacks, the addition of more features and the tendency for the base distros (antiX, MEPIS, and Debian) to get bigger over time will make the ISO file too big to fit onto a CD.  Given that Swift Linux is targeted to low-end users and competes with Puppy Linux, that is not acceptable.

I noticed that the /usr/share/locale directory in antiX Linux is over 180 MB, which is at least 10% of the size of the installed distro.  I'm considering cutting everything but the English language support.  Should I cut this in Swift Linux?

The case against the cut:
1.  I want Swift Linux to have worldwide appeal.  I don't want it to be limited to the English language world.  In the places where lightweight Linux distros are needed (because the people can only afford old computers), most people aren't fluent in English.

The case for the cut:
1.  I'm not sure that antiX Linux as is really supports non-English languages.  I just tried booting up the ISO in VirtualBox with German.  I found that some of the menu entries are still in English.  The "man" pages are in English.  Even the online support is only in English.  A Google search of antiX Linux yields 7680 results in English but only 55 in German.
2.  I am fully fluent only in English, and I am only partially fluent in German (the foreign language I studied in high school).  Thus, until I attract developers who are fully fluent in other languages, I do not have the capacity to support other languages.
3.  Is it really possible for anybody other than the very biggest distros (like Ubuntu) to offer good support in a wide variety of languages?
4.  Wouldn't non-English-speaking people prefer a distro that specializes in their own language rather than a distro that pretends to support their language?  If I lived in a world where Spanish instead of English dominated the Linux world, wouldn't I tend to gravitate towards an English-based distro?

---

