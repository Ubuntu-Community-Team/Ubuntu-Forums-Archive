---
title: "Installing Virtualbox without Lucid CD"
date: 2010-08-26
forum: Virtualisation
---

### Post by Paulgirardin on 2010-08-26
I'm trying to install Virtualbox from the repos,but it asks for the Lucid CD which I don't have.
Is there a work around for this?

---

### Post by lukeiamyourfather on 2010-08-26
The sources for apt are setup to include the install discs. Sounds like you need to remove those sources and enable the online repositories. Search for the forums or the Ubuntu site for adding and removing sources from apt.

---

### Post by Paulgirardin on 2010-08-27
Apparently it's looking for dkms which is on the cd

---

### Post by Paulgirardin on 2010-08-27
> **lukeiamyourfather said:**
> The sources for apt are setup to include the install discs. Sounds like you need to remove those sources and enable the online repositories. Search for the forums or the Ubuntu site for adding and removing sources from apt.

Yes,This sorted it.

Many thanks

---

