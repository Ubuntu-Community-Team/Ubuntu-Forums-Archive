---
title: "There is no application installed for PGP/MIME-encrypted message header files"
date: 2010-05-22
forum: Security
---

### Post by Lithium Rain on 2010-05-22
Hi,

I recently had to reinstall ubuntu, so I backed up both my ~.gnupgp and ~.gnome2 folders and copied them over in the new installation. My old keys show up just fine in the password manager, but when I attempt to open a file encrypted with one of them, I get the error:

"Could not display (name of file): There is no application installed for PGP/MIME-encrypted message header files"

How do I rectify this?

---

### Post by jrolland on 2011-06-15
This has a easy fix:

Open a terminal and type

```
sudo apt-get install gnome-gpg
```

After it installs, type

```
which gnome-gpg
```

and then enter that full path to the command into the "Choose Application" option.

Hope this helps.

---

