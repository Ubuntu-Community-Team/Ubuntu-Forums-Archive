---
title: "No idea how to search for this..."
date: 2007-03-01
forum: The Cafe
---

### Post by PartisanEntity on 2007-03-01
Right, so I run a small private forum for some of my friends using phpbb

On windows I installed a program which allowed me to patch files from the forum in order to update them. Then I would copy them back to the forum and it would be up to date.

In other words this is what I would do:

1. Download the patch files from here:
[http://www.phpbb.com/downloads.php](http://www.phpbb.com/downloads.php)

2. Download the files that need to be patched from my forum (i have a hosted account).

3. Execute a patching application on my computer which would read the instructions from the patch files and add the changes to my files from the forum.

4. Then I would upload my files back to the hosted server and my forum would be up to date.


Can I do this in Ubuntu? What packages would I need to install and how would I use them?

Thanks very much.

---

### Post by Mr. C. on 2007-03-01
I have no I idea what ubuntu/debian package this will be contained in, but you want the "patch" program by Larry Wall.

---

### Post by SSTwinrova on 2007-03-02
Try 'aptitude install patch'

[http://packages.ubuntu.com/edgy/utils/patch](http://packages.ubuntu.com/edgy/utils/patch)

---

### Post by PartisanEntity on 2007-03-02
hmm just checked and it is already installed.

Okay, I understand how this utility works, but from the man pages I was not able to find out whether I can upload the patch file to my hosted website and then execute it from the terminal? That would save me having to download all the files to my computer to patch them there, anyone have experience with this?

---

### Post by Mr. C. on 2007-03-02
Nobody can intuit what your webhost provides; you need to find how if they have the required utilities, libraries, etc. to run the patch program.  You'll have to compile it for their system, which means you have to have the native tools either there, or on a clone system.

Here's something you should consider.   Webhosts really support only so much, and I can attest from first-hand experience what happens when a webhost loses your data or closes shop.  You can lose your your site.

Instead of thinking of doing work on their host, do the work on your own, and upload data and files.  There are good FTP clients that make this trivial.

This way, you have completed control of testing the site changes offline, and can push them online when all your patches, mods, etc. are complete.

As a benefit, you can backup your entire site much more easilly, and *be sure* the backups are done to your specifications.

MrC

---

