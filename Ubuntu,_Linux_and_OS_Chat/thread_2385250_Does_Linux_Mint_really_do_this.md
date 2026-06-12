---
title: "Does Linux Mint really do this?"
date: 2018-02-18
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2018-02-18
From [https://www.ghacks.net/2018/02/17/linux-mint-software-manager/](https://www.ghacks.net/2018/02/17/linux-mint-software-manager/)>     If you prefer to use the Terminal, run the command sudo apt-get install packageName to install the specified package directly.
    To install .deb packages, run sudo dpkg -i filename.deb.
    **To install .rpm packages, run sudo rpm -i filename.rpm**.:???:

---

### Post by ajgreeny on 2018-02-18
A search of the mint forum has brought up absolutely nothing that would lead me to believe that it will work.

There is one reference only to my search term "**sudo rpm -i**" but that did not relate to an installation of Mint but went back to a discussion of an old Acer netbook with Linpus on it.
I can not recall what Linpus was based on but suspect it used the rpm package management system, not deb.

---

### Post by jeremy31 on 2018-02-18
There is the rpm package in Ubuntu repos so it is possible [https://packages.ubuntu.com/xenial/rpm](https://packages.ubuntu.com/xenial/rpm)
The package description says
> The RPM Package Manager (RPM) is a command-line driven package
management system capable of installing, uninstalling, verifying,
querying, and updating computer software packages.

On Debian and derived systems it is recommended to use "alien" to
convert RPM packages into .deb format instead of bypassing the Debian
package management system by installing them directly with rpm.

Not much talk on the Mint forums about alien and neither rpm or alien is installed by default

---

### Post by vasa1 on 2018-02-18
Thanks for the feedback! I didn't know about the rpm package although I've seen mention of *alien*.

---

