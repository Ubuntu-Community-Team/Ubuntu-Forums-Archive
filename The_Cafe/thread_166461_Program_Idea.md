---
title: "Program Idea"
date: 2006-04-26
forum: The Cafe
---

### Post by bonzodog on 2006-04-26
I'm posting this here as I have no idea about how to build a Gtk GUI front end to a terminal app. 

The application in question already exists, and I think it is very useful;
It is called sysv-rc-conf. 
It's purpose is to enable you to turn off certain startup services and enable others, to fine tune the boot process. This program is also the one the debian people recommend, as it works even in dapper very well.

Currently, the program presents an ncurses front end in a terminal, and you use the arrow keys and space bar to disable and enable things in the different runlevels.
What I envisage is a graphical representation of that where it presents a series of boxes that can be checked or unchecked.
Anyone interested in this little project?

---

### Post by mostwanted on 2006-04-26
Something like this?

[http://www.ubuntuforums.org/showthread.php?t=82783](http://www.ubuntuforums.org/showthread.php?t=82783)

---

### Post by bonzodog on 2006-04-26
BUm almost does what I want, but doesn't allow editing of base level services such as RAID, EVMS, LVM, and pcmcia.

---

### Post by teet on 2006-04-26
[QUOTE=bonzodog]BUm almost does what I want, but doesn't allow editing of base level services such as RAID, EVMS, LVM, and pcmcia.[/QUOTE]

I agree.  I would like to see a gui for this program as well.  I've drastically cut (about in half) my boot time using it.

BUM is okay, but not as powerful.  I want to be able to turn off ALL services that I don't use...like Logical Volume Management.  Why the crap is this on by default?  And RAID?  And pcmcia on a desktop?  Why why why?  

-teet

---

