---
title: "Windows XP Everyone Group"
date: 2007-12-18
forum: Windows
---

### Post by Black Mage on 2007-12-18
I'm helping out this non-profit organization with networking, and it turns out they do not actually have an actually DNS server, its a router acting as a DNS.
And I'm trying to create like a Drop Box on everyone computer where they type in the IP in the address bar, see a shared folder called drop box in which they can only write and not read, hence drop box. The problem is, the Everyone group only gives the option of if Full Control, Change, and Read.

So how can I add the options of Write to the Everyone Group?

---

### Post by Game_boy on 2007-12-18
This should be in a support category, not the Community Cafe.

---

### Post by koenn on 2007-12-18
"Change" == 'write"

---

### Post by Black Mage on 2007-12-18
But when I click on change, for allowing accessing, they can allow read  the contents, which I don't want them to do.

I'm trying to set up a drop where they drop files off into another persons computer and can't modify or read that folder.

---

### Post by koenn on 2007-12-18
from memory, so you may have to work out some details yourself :

- Disable "easy file sharing" (or something like that. (won't work on XP Home edition)

- right-click the folder
- click the tab "security"
- Select "Everyone"
- uncheck (disable) the relevant read  permissions for "Everyone"

These are filesystem (NTFS) access controls. 
The result will be the sum of NTFS security and share permissions : share permissions allow users th modify the contents of the folder (= add files), but NTFS will not allow them to read those files.

Tricky part : to be able to save a file to that folder, you probably also have to allow "execute" or "traverse".

---

### Post by Black Mage on 2007-12-18
I did that but the security tab with that options never appears. I guess the computers are not formatted in NTFS.

---

### Post by koenn on 2007-12-19
you could check that : Drive -> right-click -> properties

without NTFS, all you have are share permissions ...

---

