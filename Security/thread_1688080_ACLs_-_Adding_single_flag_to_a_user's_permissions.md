---
title: "ACLs - Adding single flag to a user's permissions"
date: 2011-02-14
forum: Security
---

### Post by unsound on 2011-02-14
Hi,

I'm wondering if there's any equivalent in setfacl of the chmod way to set or unset single flags in an rwx permission set.
For instance with chmod I can grant the group execute permission without touching the other two bits by doing:
```
chmod g+x <file>
```In setfacl the '+' syntax is not accepted. Is there a workaround? The expressions
```
setfacl -m u:<user>:x <file>
```and
```
setfacl -m u:<user>:--x <file>
```seem to be equivalent.
I want to use this in a script that makes sure that the execute bit is set on a few files for an arbitrary user without touching any other bits that have been set for the user previously.

---

