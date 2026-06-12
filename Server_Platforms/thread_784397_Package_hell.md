---
title: "Package hell"
date: 2008-05-06
forum: Server Platforms
---

### Post by yetanothername on 2008-05-06
I wonder if anyone can help me here. I'm trying to install libapache2-mod-perl2 (am running 7.1).

To install I run the command 
>sudo apt-get install libapache2-mod-perl2 

and I get the following error:
> Package libapache2-mod-perl2 has no installation candidate

I been through the /etc/sources.list file and even added resositories that have the package when I access the URLs directly through the browser. It still doesn't want to load.

I downloaded the package itself and tried installing with 'dpkg' but that's when it all fell apart and I slipped into the seventh circle of package hell.

Why am I unable to install the mod-perl package. The /etc/sources.list is the same one installed with the OS - it had not been edited before this.

Any help would be appreciated.
cheers

---

### Post by jimv on 2008-05-06
Try installing it from Synaptic Package Manager instead.  It's listed under the Perl PRogramming Language section.

EDIT
I just tried it and it seemed to work ok.

---

### Post by koenn on 2008-05-06
check if the security repo is enabled. Sometimes dependencies don't resolve because they require a version that's only available as security update.

make sure to run apt-get update
it re-reads the package lists from the server so your system knows what's available where (including newer versions that you may need to satisfy a dependency. It also shows warnings/errors if a repo server mentioned in sources.list isn't available or can't be reached. Lastly, it's required for changes in sources.list to become effective.

---

### Post by koenn on 2008-05-06
also see if this tells you something :
```
apt-cache policy libapache2-mod-perl2 
```

---

### Post by aysiu on 2008-05-06
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by yetanothername on 2008-05-06
For some reason the URL's in sources.list (which were all ca.archive.ubuntu.com) were not working properly. I had to change them all, removing the ca. for: archive.ubuntu.com. 

then as suggested:
sudo apt-get update - did the trick.

Many thanks for your responses, I'm impressed with both the speed and knowledge.

cheers

---

