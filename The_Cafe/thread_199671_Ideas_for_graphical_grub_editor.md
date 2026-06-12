---
title: "Ideas for graphical grub editor"
date: 2006-06-19
forum: The Cafe
---

### Post by siimo on 2006-06-19
Hi

As i have been trying to learn programming for Linux I have decided to write a graphical grub editor that I am going to call Grubby for now, just looking for some ideas.

so far the plan is:
1) read in a grub menu.1st on start and showing it to the user in some way
2) read in any lines that aren't a comment starting with #
3) assume lines starting with "title" start a new kernel image and read in all the images and show them to the user: kernel title, image, initrd image (if any), and boot arguments. 
4) copy original file to menu.1st.grubbybackup and write an entirely fresh menu.1st from what the program knows
5) provide an interface for adding new images via the user interface and deleting images as well

I haven't considered many things yet and theres other complications too such as - some distros use /etc/grub.conf instead of menu.1st and symbolically link it there.

[img]http://members.lycos.co.uk/siimo2005/grubby/grubby_concept.png[/img]

so far a rough UI ^,  though I know this is ugly and things are not in their correct place also missing many of the UI (such as a row of checkboxes for displaying/setting the default boot image) and the adding and deleting kernel images.  I am just trying to get familiar with GTK+ as you can see.  I am considering changing the Kernel and Initrd image text fields above to drop down menus and populating them with everthing in /boot/  what do you think about that?

Feedback is welcome.

---

### Post by TLE on 2006-06-19
Well first of all I think many would welcome a graphical grub editor. That being said I think I read somewhere that somebody was already considering this (Don't rememnber if they had startet or if it was JUST considerations). Even if this is the case that does of course not mean that you can't make one also, that depends on your intentions.

Ok If you are going to write it I have a few suggestions/advices.

1. In Ubuntu (and therefore probably also Debian) it is so that there is a section, which apt is allowed to write to and it does so when a new kernel gets out in the repos. I think it would be a good idea if your program can account for this*. That would mean that is should be able to detect the beginning and end of that section, and maybe a) Look it so that it is not possible to edit (this is probably not the Linux way) or b) Make it available only if the user has checked some "advanced" or "Ok to make my menu.lst incompatible with apt udgrades" checkbox.

2. As far as I remember the standard Windows grub entries are pretty standard, so perhaps it would be nice with a automated windows entry generator, where the user would only have to input the partition where the windows OS is on and the kind (XP, 2000 or 98 ....) and then it would do the rest.

3. Perhaps 2 could be expanded to other Ubuntus(Linuxes) also. That seem to be one of the problems that people have from time to time. So the user provide the partition of the lost Ubuntu (which then of course must be mounted), search for kernels on this partition and, either just automaticly choose the newest one or present the user with a list and let her choose.

Really good initiative, I hope you get it going, since editing the menu.lst have always scared newbies (including me) a little.

Regards TLE.

Ups have one more

4. Instruct the user in how to download and burn an .iso for a live system cd and how she would use that to recover the menu.lst from the backup if something goes wrong.

* Since if you edit the apt section manually apt will replace your entire menu.lst, or at least that was the way it was in breezy. I've tried it because I triple booted with an 64 bit version of breezy also.

---

### Post by Lux Perpetua on 2006-06-19
siimo - good idea. Just a couple of suggestions:

- Allow users not only to add, delete, and change entries, but also to copy existing entries and then modify the copies. (Consider a user who wants to have several menu lines with the same kernel but different boot options.) 

- The "kernel" line of an entry has several logically distinct pieces: which kernel to run, which partition or volume to take as root, and which other options to boot with. None of those three really want to be straight text entry boxes. "Which kernel" should be a drop-down menu (as you mention; good idea); "which root" should also be a drop down menu (possibly followed by a text entry to manually override the menu options); and "which options" should be a series of check boxes listing the most common options followed by a text entry for the leftovers. 

Also, if you have the time and space and you want ideas (or want to see what you're up against), you can check out SUSE's boot configuration program.

---

### Post by dataphile on 2006-06-24
Gnome has had a graphical Grub editor for a while, **boot-admin** from the **gnome-system-tools** package:

[http://cvs.gnome.org/viewcvs/gnome-system-tools/](http://cvs.gnome.org/viewcvs/gnome-system-tools/)

It's currently installed as part of the base Gnome packages on Gentoo. My advice is to start with **boot-admin** and save yourself some programming effort. :)

---

