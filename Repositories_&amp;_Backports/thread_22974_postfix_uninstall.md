---
title: "postfix uninstall"
date: 2005-03-30
forum: Repositories &amp; Backports
---

### Post by brianglass on 2005-03-30
I'm presuming this is a bug and should be repaired in Hoary.

We recently tried to upgrade a machine from Warty to Hoary. We had installed a couple non-Ubuntu packages (Legato for backups) using Alien. I don't know if this had any affect in regard to the said problem. Some customizations had also been made to the Postfix configuration.

We changed all occurances of warty to hoary in the sources.list file and did and apt-get update and then an apt-get dist-upgrade. This is when the problems occured.

When trying to remove Postfix (presumably to upgrade it) we apt-get spewed an error (I don't have the exact error anymore) about the prerm script failing and then bombed out and would not remove postfix.

I edited the prerm script for postfix and added exit 0; near the beginning of the script and then postfix was removable.

After that I installed ubuntu-base and now everything seems to be OK.

---

### Post by DJ_Max on 2005-03-30
Don't think this is a bug when you've modified the Postfix install. As I uninstalled Postfix with no problem.

---

### Post by az on 2005-03-31
"We had installed a couple non-Ubuntu packages (Legato for backups) using Alien"

That is your problem.  You created a situation that the package manager could not fix.

---

