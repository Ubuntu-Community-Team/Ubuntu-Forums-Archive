---
title: "Unable to get the access rights"
date: 2008-09-04
forum: Virtualisation
---

### Post by rwilhoi on 2008-09-04
So I am installing VMware Server v. 1.0.6 on Ubuntu 8 and I am repeatedly arriving at this error

In which directory do you want to install the manual files? 
[/var/lib/vmware/man] 

The path "/var/lib/vmware/man" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] y

In which directory do you want to install the documentation files? 
[/var/lib/vmware/doc/vmware] 

The path "/var/lib/vmware/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] y

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

Has anyone seen anything similar and have any beta?

---

### Post by lucho64 on 2008-09-04
you are running the installation as root, right? (I mean, with sudo in front)
BTW, 1.0.7 is out already, you should install that (Security patches). And I think that Hardy finally put vmware on the repositories, so you could use either synaptic or apt-get (I'm still running gutsy here at home)

---

### Post by rwilhoi on 2008-09-04
Will try, somehow I overlooked the new version at the top of the page.

---

### Post by rwilhoi on 2008-09-04
and yes and running with sudo ./vmware--install.pl, which i think is correct. (At least according to my guide)

---

### Post by rwilhoi on 2008-09-05
It did not work, the same message repeated once again

---

### Post by veloce on 2008-09-05
My first thought was that your installation package has been corrupted - the error message suggests that it is a *source* file that it is having difficulty with.

Does that file exist?  Try

ls -l ./vmware-vix/

That should tell you whether "bin" exists there and what it's permissions are.  (Though I would have expected "bin" to be a directory.

---

### Post by msoultane on 2008-12-06
make a symbolic link in the folder vmware-vix to the ..bin directory
cd vmware-vix
ln -s ../bin bin

---

