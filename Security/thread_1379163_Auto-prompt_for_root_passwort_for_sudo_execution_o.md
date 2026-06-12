---
title: "Auto-prompt for root passwort for sudo execution of script after doubleclick?"
date: 2010-01-12
forum: Security
---

### Post by pstein on 2010-01-12
Assume I am logged in as a normal user. 
Now in Nautilus File Browser  I doubleclick on a *.run script which requires root/admin privileges to run. In a window I got the info: "This command requires admin privileges".
 
I want to avoid to open a terminal, navigate to the directory and to enter
sudo ./myscript.run
 
Instead I want to get a prompt for the root/admin password after the doubleclick and to execute the script AUTOMATICALLY with sudo.
 
How can I tell the FileBrowser: "If insufficient privileges prompt for root passwort and execute automatically with sudo" ?
 
Peter

---

### Post by cdenley on 2010-01-12
You can install nautilus-actions then create a right-click option such as "run as root" for certain file extensions, but I don't think you can make it conditional on the permissions of the file.

---

### Post by Sarmacid on 2010-01-12
You can create a variable called user and assing it the value of the current user```
user=`whoami`
```
Then use a conditional to find out if the user is root or not, after that, if the user isn't root, use gksu to escalate privileges```
gksu command
```

---

### Post by sisco311 on 2010-01-12
You can install [nautilus-gksu]("apt://nautilus-gksu") (<- click the apturl link to install it) an extension for nautilus (file manager) which allows you to open files with administration privileges using the right click menu.

NOTE: After installing it you may have to log out and log back in.

---

### Post by pstein on 2010-01-14
> **cdenley said:**
> You can install nautilus-actions then create a right-click option such as "run as root" for certain file extensions
 
How do I install "nautilus-actions" ?
 
Is it the same as gksu mentioned in other postings?
 
Peter

---

### Post by cdenley on 2010-01-14
> **pstein said:**
> How do I install "nautilus-actions" ?
 
Is it the same as gksu mentioned in other postings?
 
Peter

It is not the same as the nautilus-gksu extension (which I'm not familiar with) or the gksu command. It is a utility which allows you to create your right-click options for files and/or directories in nautilus.
```

sudo apt-get install nautilus-actions
nautilus-actions-config

```
It sounds like nautilus-gksu may be easier.

---

