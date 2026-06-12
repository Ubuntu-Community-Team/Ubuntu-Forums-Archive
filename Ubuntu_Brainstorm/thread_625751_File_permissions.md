---
title: "File permissions"
date: 2007-11-28
forum: Ubuntu Brainstorm
---

### Post by h4mx0r on 2007-11-28
The only thing you can't edit with a gui are the linux file permissions. When you copy a file there is ctrl v and ctrl c so I propose an alt v and alt c to copy file permissions in a sense transplanting permissions onto another file.

Changing a files permissions involves 5 things
1. deciphering what permissions are there? ( ls -n )
2. what permissions would work? (<insert security mumbo jumbo>)
3. using proper chmod command (-rw-r--r-- or 777? wait ls -n doesn't show 777)
4. using proper chown command (can be difficult on a system that generally has a dozen users running at once)
5. repeat next time you look in that directory

A few questions I have are
1. would alt c and alt v be appropriate shortcut?
2. what gui method could be used to signify different permissions?
3. can certain directories please have set file permissions for when things are copied there? (Ex. copying a new desktop background to /usr/share/xfce4/backdrops/)

Seems this problem has been mentioned several times in absolute beginner talk forum however it is not a beginner problem it is a gui limitation for the ubuntu desktop.

---

### Post by insane_alien on 2007-11-28
you can edit the permissions of a file with the GUI.

right click, properties, permissions tab. assuming you are the owner of the file you can edit the permissions to your hearts content.

---

### Post by smartboyathome on 2007-11-28
And when you don't have permission, you can open nautilus with alt-f2: gksudo nautilus and do the same thing.

---

### Post by tjagoda on 2007-11-28
I think we can (mostly) unanimously agree that no extra attention here is needed?

---

### Post by insane_alien on 2007-11-29
yeah, bet the OP feels quite silly now.

---

### Post by h4mx0r on 2007-11-29
alright say you gksudo nautilus or whatever your file manager and right click then choose permissions you still can't change the user can you? so either way your back to cli trying to figure stuff out.

---

### Post by insane_alien on 2007-11-29
yes you can. you can also change the group. 

did you even bother open the thing to see what options you get?

---

### Post by slimdog360 on 2007-11-30
and now even more silly after that last comment

---

### Post by coolen on 2007-12-01
I think there's possibly a gconf option to change to this behaviour.
As always, it's a matter of defaults, or making it easier to change the options (which is something we'll probably never see).

---

### Post by h4mx0r on 2008-03-26
either way no matter what you do your still working with only one file like a tiny spec of sand with no big picture gui method of viewing and changing file permissions on a larger level. I mean I got like a terabyte worth of a data its kind of hard to browse all that stuff.

---

