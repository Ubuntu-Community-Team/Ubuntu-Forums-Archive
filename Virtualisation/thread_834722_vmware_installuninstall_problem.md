---
title: "vmware install/uninstall problem"
date: 2008-06-19
forum: Virtualisation
---

### Post by Meow27 on 2008-06-19
errr hi.

i tried installing vmware with the vmware-install.pl command and it supposedly worked. i wasn't asked for anything and nothing worked.

i tried doing it again but accidentally closed the terminal :S

whenever i try to do something with this vmware it always fails for some reason........ 
can anyone help?

when i try to run vmware-install.pl again i get this

```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.


```
and whenever i try 
```
sudo vmware-uninstall.pl
sudo: vmware-uninstall.pl: command not found

```

---

### Post by bgoody on 2008-06-19
Hi. Perhaps you should try:

sudo /usr/bin/vmware-uninstall.pl    assuming that's actually where it lives.

> **Meow27 said:**
> errr hi.

i tried installing vmware with the vmware-install.pl command and it supposedly worked. i wasn't asked for anything and nothing worked.

i tried doing it again but accidentally closed the terminal :S

whenever i try to do something with this vmware it always fails for some reason........ 
can anyone help?

when i try to run vmware-install.pl again i get this

```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.


```
and whenever i try 
```
sudo vmware-uninstall.pl
sudo: vmware-uninstall.pl: command not found

```

---

### Post by Meow27 on 2008-06-19
```
sudo /usr/bin/vmware-uninstall.pl
[sudo] password for username: 
sudo: /usr/bin/vmware-uninstall.pl: command not found
```
is there any way i can fix this? (and i mean fixing not wiping my OS ^^)

---

### Post by Fungyo on 2008-06-20
> is there any way i can fix this? (and i mean fixing not wiping my OS ^^)

```
sudo rm -R /etc/vmware
```

EDIT:
You shouldn't need to uninstall. Just run the above command then run the install command again. worked for me after getting the same errors as mentioned in your first post.

---

### Post by milamoto3 on 2008-10-23
hey Fungyo,

Thanx alot. I was able to proceed after reading your post.

Thank you.

-=OPeN Source can Save the world=-

---

