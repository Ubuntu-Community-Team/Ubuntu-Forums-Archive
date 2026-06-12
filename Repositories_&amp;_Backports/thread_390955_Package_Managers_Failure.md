---
title: "Package Managers Failure"
date: 2007-03-22
forum: Repositories &amp; Backports
---

### Post by sdgreen on 2007-03-22
Yikes -- cannot process updates.

I have been using Ubuntu for the last three months or so, after abandoning MS Windows. As an totally new guy to Linux, I have been able to get Ubuntu to work with most features. Amazing.

However, all of a sudden, the various package managers have failed and updates or indeed new installs cannot be performed.

I always get the following message:

=====

<libmpeg2-4_0.4.0b-4ubuntu1_i386.deb' ;echo RESULT=$?
(Reading database ... dpkg: error processing ///var/cache/apt/archives/libmpeg2-4_0.4.0b-4ubuntu1_i386.deb (--install):
 files list file for package `libmpeg2-4' is missing final newline
ssing was Errors were encountered while processing:
 ///var/cache/apt/archives/libmpeg2-4_0.4.0b-4ubuntu1_i386.deb
Process halted because there were too many errors.
RESULT=1
=====

Went to the reference file folder, and indeed the archive file seems to be there. The above error indicates that the " file list is missing final new line"  I have absolutely no idea where that line might be or how to fix same.


My set up:

IBM Desktop 6792, 2GHz pentium 4, Mem=1.256 GHZ ram, 80 gig disk, USB Creative Extigy sound card, DWL-2000AP+ wireless (in client mode), Nvidia 6600GT 256meg video acceleration installed and working, Logitech MX wireless mouse, 

I would appreciate any assistance to fix this issue. Thanks

---

### Post by Rhadamanthos on 2007-03-25
Just a warning, I'm no expert, but I just solved a similar problem with some help from [This thread]("http://ubuntuforums.org/showthread.php?t=117087"). Try either using Synaptic to remove that package, or upgrade it (if there is one?). It sounds like somehow a broken package got submitted to the repository, my guess is that it's been fixed already.

You might want to do a "sudo apt-get update" before using synaptic to make sure you have the most recent package lists, that might help you see if there's been an update to it.

Hope this helps!

---

