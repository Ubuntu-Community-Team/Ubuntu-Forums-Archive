---
title: "Uninstalling VirtualBox 2.2.2 installing OSE"
date: 2009-05-16
forum: Virtualisation
---

### Post by coldReactive on 2009-05-16
After uninstalling Virtualbox 2.2.2, and reinstalling OSE, I can't start OSE. It gives the error "Could not find VirtualBox installation. Please reinstall."

Reinstalling virtualbox-ose doesn't fix the issue.

---

### Post by coldReactive on 2009-05-16
dpkg didn't work either, so I just reinstalled the entire Ubuntu OS, which of course fixed the issue.

purge didn't work either as it complained virtualbox-2.2 wasn't installed.

---

### Post by kentpend on 2009-05-17
I am getting the exact same problem, but would really prefer not to do a full reinstall of ubuntu.  Any insight to the problem would be appreciated.

---

### Post by Nadjme on 2009-05-18
asalam 3la men itaba3a alhoda...

try : 

sudo dpkg configure -a

or remove all virtual completley >> sudo apt-get remove [version of virtual] --purge

---

### Post by kentpend on 2009-05-21
Did that via synaptic, and it worked.  Thanks.

---

