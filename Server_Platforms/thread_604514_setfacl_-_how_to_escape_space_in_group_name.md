---
title: "setfacl - how to escape space in group name?"
date: 2007-11-06
forum: Server Platforms
---

### Post by inselaffe on 2007-11-06
I am using Winbind to use Active Directory authentication and ACL to control access. Some of the AD groups I need to use contain one or more spaces, and the setfacl command doesn't like these. How do I escape these spaces?

This works:
setfacl -m g:groupname:rwx /dir

This deson't:
setfacl -m g:group with spaces:rwx /dir

"setfacl: Option -m: Invalid argument near character 3"

The usual "\ " to escape a space does not work.

---

### Post by MJN on 2007-11-06
Can you wrap the options in "     "   ? e.g. setfacl -m "g:group with spaces:rwx" /dir
 
Mathew

---

### Post by inselaffe on 2007-11-06
> **MJN said:**
> Can you wrap the options in "     "   ? e.g. setfacl -m "g:group with spaces:rwx" /dir
 
Mathew

Thanks for the suggestion, but that also fails with "Invalid argument near character 3"

---

### Post by MJN on 2007-11-06
I see from the setfacl man page that the -g option can use the GID instead of the groupname - can you do this? (I'm not familiar with setfacl or AD, nevermind using the two together, so perhaps this suggestion is way off the mark if the concept of GID makes no sense).
 
Mathew

---

### Post by inselaffe on 2007-11-06
Using the GID worked. Thanks a lot!

---

### Post by doublefrost on 2008-01-07
You can also use this format:

setfacl -m g:"group with spaces":rwx /dir

---

