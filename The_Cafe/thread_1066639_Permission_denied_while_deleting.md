---
title: "Permission denied while deleting"
date: 2009-02-11
forum: The Cafe
---

### Post by siivet on 2009-02-11
I've been copying things from my old computer onto my laptop which uses Ubuntu, up until now I've always used XP but Ubuntu works better for this laptop.

I just dragged the files onto the desktop and then put them into my Documents file. One of them had an error saying "Permission denied". It's just a music folder like all the other folders but this one has a little padlock symbol in the upper right hand corner of the icon and won't let me delete, move or modify anything.

I'm not sure how to solve this problem and would like some help. :/

---

### Post by rootie on 2009-02-11
Permissions are a basic concept in Linux. Here's a tutorial on the subject that's easy and fun to go through: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by jespdj on 2009-02-11
A question like this does not belong in the Community Cafe forum.

You can change the ownership and permissions of files in Nautilus by right-clicking on the file and selecting Properties > Permissions. But you might need to run Nautilus as an administrator. You can do that by pressing Alt + F2 and running the command:
```
gksu nautilus
```
You can also do it with terminal commands: chown and chmod. Try "man chown" and "man chmod" for information on how these work.

Example:
```
# Make user 'jesper' (in group 'jesper') the owner of somefile
chown jesper:jesper somefile

# Make somefile read/write for the owner (u = user, +w = make writable)
chmod u+w somefile

```

---

### Post by howefield on 2009-02-11
You could try opening nautilus as root and deleting.

Open a terminal and type

```
gksu nautilus
```

---

