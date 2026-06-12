---
title: "What commands are in need of a front-end?"
date: 2011-09-14
forum: The Cafe
---

### Post by undecim on 2011-09-14
I'm teaching python to my little brother, and he's learned on his own how to do GUI's, but has no idea what kind of program to write for practice.

So I figure the two of us could write some descent front-ends in python for CLI programs, and I'd get some input from the community on what programs are in need of a front-end?

Or does everything anyone would want to use already have a good frontend?

---

### Post by RiceMonster on 2011-09-14
yes

---

### Post by aaaantoine on 2011-09-14
How about espeak?

Most commands probably already have a front end, but this would be strictly a learning experience.

---

### Post by koenn on 2011-09-14
wget ?

I imagine rather than presenting a long list of options with checkboxes, you could think about common tasks (single file download, backup a site, build a browsable mirror,  ....) with options (with/without authentication, ...) etc. Your GUI would then need some logic to call wget with the appropriate options and possibly prompt for additional data required for that specific task, with sane defaults where possible. 

Additionally, it would be a exercise in good programming practices, because you're likely to start small and add on more stuff later. Your initial GUI and its code should be designed so that expanding it would be easy and doesn't clutter your code.

---

### Post by apmcd47 on 2011-09-14
As a first go I *may* be inclined to re-implement something like the archive managers. My point is not that we *need * another archive manager, but you have not only a challenge to write one, but there are a plethora of managers out there you can compare yours to. 

For something more original: currently if I want to view a set of text files I can use *more*, *less*, or a file editor. But that stops at text files. If you have a directory full of image files you can view them with gwenview or some other tool designed to view images. But that's it. Twenty years ago I had a tool called *vf*. It recognised certain image formats and could be extended to recognise, convert and display other image formats with for instance **pbm** or *imagemagick*. It also displayed text files. Point it at a tar or zip file and it could list the contents. Give it an executable or a library file and it could display the output of *nm* or *strings.* Failing that it could display a hexadecimal listing of the file.

I once attempted to re-implement that tool in perl with the tk extension but only got as far as a text lister. I have never had the time to take it further or port it to a newer toolkit.

Problems to solve:
[LIST]
[*]Using it from a command line (easy)
[*]Using it from a gui file manager such as dolphin
[*]Recognising filetypes and extending it to recognise more
[*]Searching for text in the text view
[*]Reusing it when you want to look at more files
[*]Moving to another tool if you want to edit a text file or extract a file from an archive
[/LIST]
The original tool could do the first four points above.

So what do you think?

Andrew

---

### Post by gordintoronto on 2011-09-14
Folding@home

---

### Post by ki4jgt on 2011-09-14
Shreading a file. Allow him to drag a file onto a window (trash can design) and when the file gets drug to the window, shread it. Better yet, it could be in the notifications area so people could have it open constantly.

---

### Post by ninjaaron on 2011-09-14
if you have a computer with a wireless card, you could have him write a gui that uses iwconfig, iwlist, and dhcp to find and configure new wifi connections.

There are already gui apps for wicd and Network manager, so it's kinda redundant, but there isn't anything good for Network Daemon.

[edit]
thought of a much better one for this job:  imagemagick!  Something light to let you preform all kinds of tasks on images without having to load a full editor.

---

### Post by Primefalcon on 2011-09-15
> **aaaantoine said:**
> How about espeak?

Most commands probably already have a front end, but this would be strictly a learning experience.
already has one... gespeak

---

### Post by capink on 2011-09-15
Why not a GUI to manage partitions instead of manually editing fstab?

---

### Post by 3rdalbum on 2011-09-15
dd would be a good one, because it's such a magical tool - you can destroy data, make a disk image, or even restore data with it. Dd is also a pain to use in the terminal because its syntax is so different to everything else.

When testing the dd frontend I'd advise using a virtual machine so any bugs in the frontend don't cause you to wipe your hard disk :-)

---

