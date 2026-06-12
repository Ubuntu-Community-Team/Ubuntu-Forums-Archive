---
title: "What does Ubuntu server version have?"
date: 2005-12-15
forum: Server Platforms
---

### Post by harisund on 2005-12-15
Right now at home I have installed Ubuntu using the server option from the Breezy Badger Install CD. 

Today I came across a special version of Ubuntu, the server version, which is supposed to come with all server related programs already installed. 

Does anybody have a listing of what it contains? And what configurations I need to do? Does it too have the concept of using sudo for everything? Does it automatically listen on standard ports like 80 (using apache?) , 22 (using openssh-server?) and so on? 

Thanks 
Hari

---

### Post by UbuWu on 2005-12-15
The server install cd will do the same installation as the normal cd with the server option. Programs such as apache are included on the cd but not installed by default and after installation you will not have any open ports.

---

### Post by bjweeks on 2005-12-15
[QUOTE=UbuWu]The server install cd will do the same installation as the normal cd with the server option. Programs such as apache are included on the cd but not installed by default and after installation you will not have any open ports.[/QUOTE]
[Wrong.]("http://ubuntuforums.org/showthread.php?t=79093")

---

### Post by nocturn on 2005-12-15
[QUOTE=bjweeks][Wrong.]("http://ubuntuforums.org/showthread.php?t=79093")[/QUOTE]

Cool, thanks for the link

Do you know if and how I can upgrade from 5.04 server-install to this version?  Does it have any difference in repositories to accomodate the server-kernels?

---

### Post by bjweeks on 2005-12-15
[QUOTE=nocturn]Cool, thanks for the link

Do you know if and how I can upgrade from 5.04 server-install to this version?  Does it have any difference in repositories to accomodate the server-kernels?[/QUOTE]

No, but there is no point.

---

### Post by nocturn on 2005-12-15
[QUOTE=bjweeks]No, but there is no point.[/QUOTE]

How do you mean?  The page said that the server version has a different set of kernels which are better tuned for server use (a.o. no bootsplash).

Now, I have a working server on Hoary which I was contemplating of moving to  Breezy soon.  It would be nice to have it use the set of kernels that are build for the server instead of the desktop ones...

---

### Post by bjweeks on 2005-12-15
[QUOTE=nocturn]How do you mean?  The page said that the server version has a different set of kernels which are better tuned for server use (a.o. no bootsplash).

Now, I have a working server on Hoary which I was contemplating of moving to  Breezy soon.  It would be nice to have it use the set of kernels that are build for the server instead of the desktop ones...[/QUOTE]

I didn't see the boot splash thing my bad. The things I saw was cluster, lstp and 4 gb of ram.

---

