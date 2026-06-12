---
title: "[idea] Easy home networking"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by Turgon on 2007-10-25
Today, sharing files are an okey task as long as you do it with another linux based computer (you need to set a smb password to make windows computers get access to you files), but it can be easier than go to network places and then hope that your other computer shows up there.

Printers are however harder to share. This could be made easier.

My idea: make network places display all the computers on the network (a user must manualy activate "sharing" on the given computer). Under each computer the shared files and printers are displayed. By doing this it will easily be accessible to the user.

By doing this, ubuntu also picks up the different users on the network, which is very useful when you deal with access control. Lets say that mark wants to share one folder with two out of four on his network. He could then add them as people with access in the sharing menu or perhaps drag and drop the folder to the given users (and then default with read access only). Printers could be shared in the same way.

What do you think?

PS: I will write a better and more thought-trough spec soon.

---

### Post by F for Fragging on 2007-10-26
Totally agree, I also figured out that network shares are easily accessible on other Ubuntu boxes, but if you try to access network shares from a Windows box it asks for a password. After googling a bit I figured out that you have to use the terminal to set a samba username and password, which makes this feature very difficult to use.

What I also thought to be a poor decision is that Ubuntu does not have Samba and a few other packages (don't remember exactly, NFS maybe?) installed by default, as soon as you open the "System" -> "Administration" -> "Shared Folders" menu entry on a fresh installation of Ubuntu you are asked to install them. Network shares are an important feature, so those packages should be installed by default, if there's not enough space on the CD they'd better ditch the Windows software on the CD's. I'm looking forward to the specification you are goign to write. Maybe it would also be a good idea to propose it for discussion on the next UDS so that this problem will get noticed by the developers? However, I'm not sure if that's still possible, because [UDS Boston]("https://wiki.ubuntu.com/UDS-Boston") already starts at the 29th of October.

---

### Post by rahulthewall3000 on 2007-10-26
Could not agree more, file sharing is very important on a university campus and is of great use. However, though I can access the files that others are sharing, I have not yet been able to configure my computer to be able to share with Windows Computers. Tried  editing samba.conf, but just did not work. 
Also, another important fact that is that I cannot share from my external hard drive as it is FAT32 and somehow there is always a problem with permissions when I try to share from my external. 

If a solution to both of my above problems is shipped with Hardy Heron, then I will be as happy as a kid set loose in a candy store.

Cheers
Rahul

---

### Post by skotadi on 2007-10-26
Yes!  this is a big problem.  If this problem could be solved, that would be one more reason for the desktop user to stop using Windoze.  

Turgon, I like the idea of dragging 'n' dropping to set sharing permissions, but it may need more thought as to the specifics.

---

### Post by Turgon on 2007-10-26
> **skotadi said:**
> Yes!  this is a big problem.  If this problem could be solved, that would be one more reason for the desktop user to stop using Windoze.  

Turgon, I like the idea of dragging 'n' dropping to set sharing permissions, but it may need more thought as to the specifics.

I will make clearer specifics in the spec im going to write and try to add some more things into it (backup over network, and syncing of settings, contacts, notes ect).

---

### Post by 23meg on 2007-10-26
Moved to Ubuntu Idea Pool.

---

