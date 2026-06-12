---
title: "How do you Reinstall a program?"
date: 2007-08-28
forum: Repositories &amp; Backports
---

### Post by Richardinho on 2007-08-28
I'm having problems with a program, and someone has suggested that I try reinstalling this. It's one that's in the Ubuntu repositories, which is where I installed it from in the first place. I've done various searches on this forum and elsewhere, and had a look at Synaptic, but I can't work out how to do this, and if it is actually possible.

Any ideas?

---

### Post by Zootropo on 2007-08-28
From the console you can use:
sudo aptitude reinstall package

I don't know about synaptics, because I don't use it.

---

### Post by Richardinho on 2007-08-28
So presumably I'd have to find out every package that made up the program (it's Blender btw) and use that code for each one?

---

### Post by Seisen on 2007-08-28
No you would just have to reinstall Blender if that is the package that you are having problems with.

---

### Post by IanW on 2007-08-29
Open Synaptic

Repeat (
Search for package you wish to reinstall
Right-click on package
Select Re-install
) Until all done

Click Apply

---

### Post by techunit on 2010-05-03
Thanks a ton this helped immensely. I didn't get why sudo apt-get reinstall gwibber wasn't working... know I know

---

