---
title: "adding everyone to a group?"
date: 2009-02-25
forum: Server Platforms
---

### Post by kooldino on 2009-02-25
Is there a way to add all of my users to a special group without doing them all individually?

---

### Post by pdtpatrick on 2009-02-25
use 

> groupmod 

[http://www.computerhope.com/unix/groupmod.htm](http://www.computerhope.com/unix/groupmod.htm)

---

### Post by capscrew on 2009-02-26
> **kooldino said:**
> Is there a way to add all of my users to a special group without doing them all individually?

Groupmod can be used to create a group.  After you have created the group you would need to export to a file a list of users.  Then you could create a script to add them to a new group.  An example of a script would be like this:[http://nixcraft.com/linux-software/8498-add-multiple-users-group.html]("http://nixcraft.com/linux-software/8498-add-multiple-users-group.html")

---

### Post by bluefrog on 2009-02-26
this is for ubuntu as the regular users have a uid >= 1000

group=your-group; for i in $(awk 'BEGIN{FS=":"} {if ($3 >= 1000) print $1}' /etc/passwd | sed '/nobody/d'); do sudo gpasswd -a $i $group; done

---

### Post by kooldino on 2009-02-26
> **bluefrog said:**
> this is for ubuntu as the regular users have a uid >= 1000

group=your-group; for i in $(awk 'BEGIN{FS=":"} {if ($3 >= 1000) print $1}' /etc/passwd | sed '/nobody/d'); do sudo gpasswd -a $i $group; done

Interesting...so could you explain to me a little bit about how this works?  I just read up on sed and awk a little bit, so I have the basics down...

---

