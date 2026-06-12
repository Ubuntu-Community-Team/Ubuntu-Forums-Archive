---
title: "[SOLVED] Application Virtualisation Platform for Linux?"
date: 2008-03-17
forum: Virtualisation
---

### Post by ibuclaw on 2008-03-17
Hi all, to give a brief introduction, I've been playing with the trial version of a product called[ Thinstall ]("http://www.thinstall.com/products/virtualization_suite.php")(for Windows), which can be described at its very bare state a program that takes a "snapshot" of your filesystem before and after an installation of a program, then collects/copies the difference (newly placed files) into an isolated folder (sandbox) on your userspace.
Here you can configure how isolated you want the program to be (can/can't write to registry. can/can't write to filesystem, or can only have access to non-system files/regkeys) along with removing any unwanted packages/files (ie: the installer) and set how many binaries can be executed from the application (if more than one binary was installed).
[IMG]http://www.thinstall.com/products/images/vos_FIN_000.jpg[/IMG]
Once all is set, you compile the entire folder into a single executable (or one main executable with child executables linked to it if more than one binary was selected).
This can then be copied to any computer and be run on it without installation required.
This can be useful if you want to keep a clean system (freshly installed OS), or don't want unwanted files scattered across the filesystem.
[IMG]http://www.thinstall.com/products/images/compare_FIN_001.jpg[/IMG]
One of my favourite features of this product is the fact that you can put the finishing executable where-ever you want and when run, it still thinks it was executed from the C/Program Files/ directory.

I've also managed it to get some apps working with wine where installation failed. Miraculously enough, they run when installed, but don't install under wine. :) Explain that!

Anyway, is there similiar technology to this on Linux?
One reason I can think of myself having use for it is keeping a track on all the ".dot" folders in my userspace, half I swear are from programs that are long gone, but I don't really want to remove it just incase. Plus the fact that some programs generate unwanted empty folders in my userspace too. Must notably one called "file:".
And lastly I don't need to install thirteen different versions of gcc! :lolflag:

Anyways, send us your thoughts on this, and if there are any programs similiar for Linux, posting them would be grateful.

Regards
Iain

---

### Post by ibuclaw on 2008-03-17
Okay, I've found one...

I'm just about to try it, so I couldn't say what they're like.
But its a software called [KLIK.]("http://klik.atekon.de/")

The general aim is to run software across any distribution without installing it.
[IMG]http://klik.atekon.de/presentation/img36.jpg[/IMG]
[IMG]http://klik.atekon.de/presentation/img38.jpg[/IMG]

And they follow the same "One File per Application" philosophy that Thinstall does.

Probably worth a try for any enthusiasts.

Iain

---

