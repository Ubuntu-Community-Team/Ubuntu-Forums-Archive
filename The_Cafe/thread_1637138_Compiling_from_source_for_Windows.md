---
title: "Compiling from source for Windows"
date: 2010-12-04
forum: The Cafe
---

### Post by Oxwivi on 2010-12-04
For part of my time, I'd have to use Windows in a dual-boot system. Is there a way to compile programs I use on Ubuntu from source so I can run it in Windows as well?

---

### Post by Kimm on 2010-12-04
> **Oxwivi said:**
> For part of my time, I'd have to use Windows in a dual-boot system. Is there a way to compile programs I use on Ubuntu from source so I can run it in Windows as well?

Depends completely on the program. A lot of (most, actually) apps in Ubuntu have windows versions as well. Could you tell us which apps you want to run in Window?

---

### Post by Oxwivi on 2010-12-04
For now, I'm thinking of Empathy. I was thinking of some others I might need as well, but for now that's all I can think of.

What are the requirements and how do we compile it for Windows?

---

### Post by del_diablo on 2010-12-04
Are you thinking of cross compiling(compile Windows binaries under Linux), or are you thinking of compiling under Windows?

---

### Post by Oxwivi on 2010-12-04
I've never tried either of them, I'm willing to go for the one with the least hassle or the one recommended by experienced users.

---

### Post by Kimm on 2010-12-04
> **Oxwivi said:**
> For now, I'm thinking of Empathy. I was thinking of some others I might need as well, but for now that's all I can think of.

What are the requirements and how do we compile it for Windows?

Sorry, Empathy is one of the few apps that you wont be able to run in Windows(due to its dependency on Gnome-libraries and the telepathy framework), but you can have a look at Pidgin (which runs on both Linux and Windows), or Miranda (which is Windows only) for alternative clients that handle multiple accounts and protocols.

---

### Post by Oxwivi on 2010-12-04
Can't I compile those libraries for Windows? I never got used to Pidgin, and I don't like the other Windows-only alternatives.

---

### Post by Spice Weasel on 2010-12-04
Doesn't Pidgin save passwords in a plain text file? Doesn't sound like too much of a good choice for Windows...

---

### Post by Kimm on 2010-12-04
> **Oxwivi said:**
> Can't I compile those libraries for Windows? I never got used to Pidgin, and I don't like the other Windows-only alternatives.

Gnome 2 hasn't been successfully ported to Windows (although [it has been attempted]("http://cygnome.sourceforge.net/"), and seemingly abandoned) I'm afraid, so you wont be able to compile the libraries necessary on Windows.

> **Spice Weasel said:**
> Doesn't Pidgin save passwords in a plain text file? Doesn't sound like too much of a good choice for Windows...

You have a point there, though viruses and trojans would need to look for those files specifically, and since Pidgin is not very widely used on Windows I don't think it would be very risky. But I could be wrong...

---

### Post by KIAaze on 2010-12-04
Yes, it is possible to compile programs for Windows under GNU/Linux, if the code is already cross-platform and compilable with mingw-make. :)

Once you are able to compile something with mingw32-make (or mingw*-gcc/g++) in Windows, you should be able to compile it in Wine (after having installed the same libraries you installed in Windows of course).

You can notably use:
```
wine cmd
```
to run .bat scripts or any other command.

So it is doable, but it might take a lot of work depending on the number of dependencies and their ease of installation in Windows and Wine.

In principle using something else than the mingw compilers (like the visual studio compiler) should also work, but I haven't had any success with it.

Note:
I also managed to install and run Kate from KDE in Windows following instructions from here: [http://windows.kde.org/](http://windows.kde.org/)
But it was a bit slow to start and notepad++ is a good replacement anyway.
I don't know how far Gnome got in their port, but a lot of GTK apps like Gimp and Pidgin already have Windows installers.

edit:
Adding link: [http://www.mingw.org/](http://www.mingw.org/)
And yes, [cygwin]("http://cygwin.com/") mentioned in the following post might also be worth looking into. :)

---

### Post by fatality_uk on 2010-12-04
[http://cygwin.com/faq.html](http://cygwin.com/faq.html)

---

