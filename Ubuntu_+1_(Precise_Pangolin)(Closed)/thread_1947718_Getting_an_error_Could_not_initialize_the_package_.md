---
title: "Getting an error: Could not initialize the package information"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-27
Since a yesterday's update, I am not able to run Update Manager. Synaptic and Software Centre also crash with the same error message:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

How can I fix that?

---

### Post by paul_in_london on 2012-03-27
> **&#1058 said:**
> Since a yesterday's update, I am not able to run Update Manager. Synaptic and Software Centre also crash with the same error message:



How can I fix that?

First try this:

```
sudo rm -vf /var/lib/apt/lists/*
```

and then see if you can update/upgrade as normal.

If that doesn't work, try:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgrade # or sudo apt-get dist-upgrade if no dependency issues
```

EDIT: it's possible that you'll need to revert to an earlier status file, but I can talk you through that if necessary.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-27
Thanks for the quick solution Paul. The first option did the trick. IT's all fine now.

---

### Post by paul_in_london on 2012-03-27
> **&#1058 said:**
> Thanks for the quick solution Paul. The first option did the trick. IT's all fine now.

Glad to help. :smile:

---

