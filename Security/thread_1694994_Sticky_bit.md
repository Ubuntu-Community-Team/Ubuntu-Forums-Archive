---
title: "Sticky bit"
date: 2011-02-25
forum: Security
---

### Post by honey_bee on 2011-02-25
I have ready from different web sites about sticky bit.Some things are clear and some not. I made a directory mydir and assign sticky bit to it.after taking ls -l it show me the permission
drwxr-xr-x

Now I apply sticky bit

chmod +s mydir
Now by taking list ls -l it show me permissions as
drwsr-sr-x

I want to clear it what will be the affect when the dir is set sticky bit.
Thnaks in advance,
honey

---

### Post by i.r.id10t on 2011-02-25
The sticky bit is used for executing the file as the owner or group or other - no matter who you are, if you can execute it, you will execute it as whoever has the sticky bit set.  Uses for this may be allowing a regular user or "the system" to use a dialup connection over a modem, since you have to have root permissions to change routing tables, etc.

Not sure how having the sticky bit set on a directory would work - you do need execute permissions on a directory to be able to change into it....

---

### Post by The Cog on 2011-02-25
According to several articles I've seen, the sticky bit has no effect on files in Linux.

It does have an effect on directories though. Here's a good description:
[http://linuxdevcenter.com/pub/a/linux/lpt/22_06.html](http://linuxdevcenter.com/pub/a/linux/lpt/22_06.html)
Note 1: Users who cannot delete or rename the files may still be able to edit their contents.
Note 2: Folders created inside a sticky folder will also be sticky - the property is inherited.

---

### Post by asmoore82 on 2011-02-26
> **The Cog said:**
> According to several articles I've seen, the sticky bit has no effect on files in Linux.
This is correct.

But the OP has the sticky bit confused with the setuid and setgid bits.
`chmod +s &#8230;` actually sets setuid bits
`chmod +t &#8230;` sets the sticky bit.

For modern Linux,
The sticky bit on a directory is now the *restricted deletion flag*.
This prevents users from deleting files from a directory unless they are
the owner of either/or, even if the have write permission on that directory.
Note here, that even with all of this in place, if they have write permission
on the file itself, they can still *truncate* ("blank") it; even if they
can't delete it.

The setgid bit on a directory causes newly made files in it to "inherit" the
same group ownership.

I'm not sure about setuid on a directory. I think it does nothing. But we
already know that setuid has huge implications on a binary executable.

---

