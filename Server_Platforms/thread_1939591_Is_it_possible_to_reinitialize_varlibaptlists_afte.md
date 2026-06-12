---
title: "Is it possible to reinitialize /var/lib/apt/lists after deleting it?"
date: 2012-03-12
forum: Server Platforms
---

### Post by vfclists on 2012-03-12
Is it possible to restore the functionality of /var/lib/apt/lists and /var/apt/cache after deleting them or minmizing them in some wa

I am trying to shrink down an Ubuntu VM to the smallest size and decided to delete /var/lib/apt/lists and /var/cache/apt with the intention of restoring them when the system needs to be updated. I have done /var/cache/apt without major side effects, simply recreating some directories reenables it. The /var/lib/apt/lists is the one I am unsure of. Is it possible delete it and restore its functionality by recreating like /var/cache/apt?

Does doing that destroy the knowledge apt and dpkg have of the systems configuration or is that stored elsewhere?

---

### Post by Irregular Joe on 2012-03-12
The /var/lib/apt/lists can be removed and recreated safely.  An 'apt-get update' will repopulate the necessary information.  This does not impact the history of installed packages.
```
  # Remove the directory
  sudo rm -fr /var/lib/apt/list

  # Recreate the necessary directory structure
  sudo mkdir -p /var/lib/apt/list/partial
```

Hope this helps.

---

### Post by peterlauri on 2012-08-14
> **Irregular Joe said:**
> The /var/lib/apt/lists can be removed and recreated safely.  An 'apt-get update' will repopulate the necessary information.  This does not impact the history of installed packages.
```
  # Remove the directory
  sudo rm -fr /var/lib/apt/list

  # Recreate the necessary directory structure
  sudo mkdir -p /var/lib/apt/list/partial
```

Hope this helps.

It helped me :) I was having these errors and it fixed it:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

