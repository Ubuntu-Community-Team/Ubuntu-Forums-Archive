---
title: "OSDev vs. Linux From Scratch"
date: 2015-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Mike_Gomez on 2015-03-25
I know that OSDev is very complicated, and I don't have any prior coding knowledge so I won't ask. But what are the limitations of creating a Linux distro from scratch as opposed to writing a custom kernel? Can it still be truly "yours" if you go the LFS route?

---

### Post by veddox on 2015-03-27
Writing a custom kernel... A quote from [osdev.org]("http://wiki.osdev.org/Beginner_Mistakes"): 
> "The Linux kernel took over one year of very dedicated work to get into a  semblance of usefulness, and all Linus Torvalds did was *mimic* existing and well-documented behaviour to get an already-existing userspace to run on it."

Basically, until you're a wizardly programmer with plenty of time (and preferably equally wizardly friends), don't even think about writing your own kernel, let alone a complete operating system.

LFS is all about combining other people's work to put together an OS which precisely mirrors what you want. In a sense, it's like publishing a poetry anthology: other people wrote the poems, but you get the credit for compiling them into one volume. 

Thousands of developers in the Linux community have been working for over 25 years to create the kernel and all the userspace programs you now have available. You will never be able to make an OS that is anywhere near as functional on your own. LFS is the next best thing.

For more information on writing your own OS, see [this]("http://wiki.osdev.org/Getting_Started").

---

