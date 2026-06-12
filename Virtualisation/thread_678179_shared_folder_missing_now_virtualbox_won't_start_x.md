---
title: "shared folder missing now virtualbox won't start xp"
date: 2008-01-25
forum: Virtualisation
---

### Post by lime4x4 on 2008-01-25
I had a hard drive fail in my gutsy box which was a shared folder thru virtualbox.Now virtualbox won't start that machine cause it's missing. It won't let me delete it thru the gui. How can i delete it from the command line so that i may start the virtual xp system?

---

### Post by Elle Stone on 2008-02-06
The quick and easy way is to recreate the missing shared folder (just has to have the same path, doesn't need to contain anything) so that virtualbox can find it.  Then remove it from the shared folder list while the machine is running.     

Search [http://forums.virtualbox.org/](http://forums.virtualbox.org/) for other ways of dealing with this problem.  If you can't recreate the original folder and path, then you can edit the xml file to remove all references to the now-missing shared folder, but this approach is more dangerous because if you mess up the syntax, you will have a difficult time recovering.  Make a backup before modifying.

Also, see my post: [http://forums.virtualbox.org/viewtopic.php?t=4096](http://forums.virtualbox.org/viewtopic.php?t=4096)
for advice on avoiding a couple of other "gotchas" that vbox will hand to you if you aren't careful.  

Elle

---

### Post by doggiedoll on 2008-05-08
What I did and it success is edit the .VirtualBox/Machines/vbox.xml file.

My virtual machine name is vbox. For you it is probably different.

---

