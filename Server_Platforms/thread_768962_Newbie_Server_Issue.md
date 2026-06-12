---
title: "Newbie Server Issue"
date: 2008-04-26
forum: Server Platforms
---

### Post by Derspankster on 2008-04-26
I recently built a server for use at home. It runs Hardy and I also installed gnome desktop because of my unfamiliarity of the Linux command line. When I installed the system I partitioned the hard drive into one partition. I then added folders for the various files that I wanted to serve and set permissions and sharing using gksudo nautilus.

My issue is this, when I boot the system I get the following error.

Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by others.

Does this mean that I have some of my permissions wrong? Or, is the fact that I formatted the drive into one partition? Do I need to create another logical disk and move my shared folders into it?  

I want to be able to move files from my other computers to the server from all of my computers. 

Guess I'm just a nOOb at this and need some guidance. Even though I can move past this warning when I boot, I want to run the server headless and I can't because I can't "OK" my way past this warning. I can't connect via ssh before the server actually boots.

---

### Post by Monicker on 2008-04-26
Looks like a simple permissions problem.

What does "ls -lh ~/.dmrc" show?

---

### Post by Derspankster on 2008-04-26
> **Monicker said:**
> Looks like a simple permissions problem.

What does "ls -lh ~/.dmrc" show?

It shows:

 No such file or directory

---

### Post by Monicker on 2008-04-26
Hmm. I gues you could create it and see if you still get errors.

Mine only has the following in it:

```
<blank line>
<blank line>
[Desktop]
Session=default
```

---

### Post by Derspankster on 2008-04-27
> **Monicker said:**
> Hmm. I gues you could create it and see if you still get errors.

Mine only has the following in it:

```
<blank line>
<blank line>
[Desktop]
Session=default
```

Thanks for your input but it turned out to be a permissions issue in my home folder. Fixed now.

---

