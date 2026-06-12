---
title: "Virtualbox question."
date: 2009-12-26
forum: The Cafe
---

### Post by Cam42 on 2009-12-26
I recently got a massive external hard drive, and I want to move my Kubuntu vdi virtual hard disk file from my internal to my external drive, but I can't find where the stupid thing is. I'm on XP SP3.

Also, will I have to create a new Virtual Machine that uses the vdi off of my external, or can I edit the existing one to use it in a different location?

---

### Post by chriswyatt on 2009-12-26
It's probably in your .Virtualbox folder.  If for some reason it's not type 'locate .vdi' into a Terminal.

Also in VirtualBox it quite clearly tells you where the hard drive images are located.

---

### Post by CharlesA on 2009-12-26
I think it'll be located in a folder called .VirtualBox in your user profile.

EDIT: You can also use the virtual media manager (I think?) to find it as well.

---

### Post by Ichtyandr on 2009-12-26
on your second question, you can properly clone your vdi using "clonevdi" or "clonehd" command look here:

[http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/](http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/)

---

### Post by blueshiftoverwatch on 2009-12-26
What's the difference between the .vdi virtual hard drive image files and some of the other options that allow you to choose from when setting up a virtual machine?

---

### Post by chriswyatt on 2009-12-26
:confused:

Do you mean the other file types you can choose from?  They're just different image formats.

---

### Post by blueshiftoverwatch on 2009-12-26
> **chriswyatt said:**
> :confused:

Do you mean the other file types you can choose from?  They're just different image formats.
Yeah, but what are the advantages/disadvantages of using vdi versus other formats?

---

### Post by Cam42 on 2009-12-26
Found it.

---

### Post by chriswyatt on 2009-12-26
> **blueshiftoverwatch said:**
> Yeah, but what are the advantages/disadvantages of using vdi versus other formats?

Hmm, I'm not sure.  Though I doubt it really makes much of a difference.  Compatibility is the only thing I can think of off the top of my head.

---

### Post by 4partee on 2009-12-26
I am working on this as well.

From System Tools, Sun VirtualBox; try File Preferences.

HTH;
John

---

