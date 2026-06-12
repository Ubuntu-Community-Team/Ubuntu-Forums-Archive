---
title: "E: Package 'virtualbox' has no installation candidate"
date: 2022-08-13
forum: Virtualisation
---

### Post by chat-4432 on 2022-08-13
i cant install vitual box
when i try 
sudo apt update
 sudo apt install virtualbox
```
Package virtualbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'virtualbox' has no installation candidate




```
what should i do ??

---

### Post by ajgreeny on 2022-08-13
What version of Ubuntu are you using?
Virtualbox is available in the repos of all supported Ubuntu versions, though you must ensure that the multiverse repos are enabled.
Open up **software-properties-gtk** (Software and Updates) and check that they are enabled then try again.

When I used Virtualbox I always enabled the repos from Oracle and installed the version direct from them.
All info about that can be found at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) with the detailed info for Ubuntu in the section on ***Debian-based Linux distributions***

---

### Post by ajgreeny on 2022-08-13
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by &amp;KyT$0P# on 2022-08-13
> **chat-4432 said:**
> what should i do ??

Can you install the [official VirtualBox package .deb]("https://www.virtualbox.org/wiki/Downloads")?

Download the .deb for your version of Ubuntu, then do
```
sudo apt install [COLOR="#FF0000"]/full/path/to/virtualbox.deb[/COLOR]
```
replacing [COLOR="#FF0000"]/full/path/to/virtualbox.deb[/COLOR] with the actual full path to the downloaded .deb

---

### Post by ajgreeny on 2022-08-13
> **halogen2 said:**
> Can you install the [official VirtualBox package .deb]("https://www.virtualbox.org/wiki/Downloads")?

Download the .deb for your version of Ubuntu, then do
```
sudo apt install [COLOR="#FF0000"]/full/path/to/virtualbox.deb[/COLOR]
```
replacing [COLOR="#FF0000"]/full/path/to/virtualbox.deb[/COLOR] with the actual full path to the downloaded .deb
Much easier, however, to enable the Oracle repos, as I suggested in post #2, and then you will also update automatically along with everything else.

If you install the way you say here by manually downloading the .deb, you also have to remember to manually check regularly for updates.

---

### Post by &amp;KyT$0P# on 2022-08-13
> **ajgreeny said:**
> enable the Oracle repos

How do you update the Extension Pack to always match VirtualBox version using this method?

> If you install the way you say here by manually downloading the .deb

I said it here because that is the most minimal way to test installing VirtualBox to see if it will work on their system.  If that works without issue, then yes adding the Oracle repo could simplify staying up to date.

---

### Post by ajgreeny on 2022-08-13
With the vbox repos enabled you will get a notification of the need for an updated Extension Pack when you open a newer version of the VBox manager window and a click will download the new extension pack and allow you to install it with the instructions appearing stage by stage - very simple and quick.

If you simply wish to explore whether or not vbox will run on your hardware, then maybe you are correct.

---

### Post by &amp;KyT$0P# on 2022-08-13
> **ajgreeny said:**
> With the vbox repos enabled you will get a notification of the need for an updated Extension Pack when you open a newer version of the VBox manager window and a click will download the new extension pack and allow you to install it with the instructions appearing stage by stage - very simple and quick.

Nice, I'll look into switching to use the Oracle repo next time I want to update VirtualBox.  Thanks!

---

### Post by SeijiSensei on 2022-08-14
I always used the Oracle PPA when I used VirtualBox. Now I've moved on to the native VM manager in the Linux kernel.

[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor)

---

