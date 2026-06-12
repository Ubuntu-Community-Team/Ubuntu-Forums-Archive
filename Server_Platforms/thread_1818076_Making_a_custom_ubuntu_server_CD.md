---
title: "Making a custom ubuntu server CD"
date: 2011-08-04
forum: Server Platforms
---

### Post by Metallion on 2011-08-04
I'm making a lucid server CD that adds a couple of packages to the installation. I've followed [this guide](https://help.ubuntu.com/community/InstallCDCustomization) and succeeded as long as I'm connected to the internet during the install.

Why do I need the internet? Because the packages I added require newer versions of the packages included in the standard CD. If apt can't connect to an online repo, the installation fails.

I would like to upgrade all packages on the CD to their current versions in the repos. Replacing the debs themselves is easy enough but I'd probably need to make several other changes to the repository stored on the CD. Could anyone point me to some documentation about this? Thanks.

---

