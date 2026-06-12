---
title: "Openssh-server installation problem"
date: 2011-10-16
forum: Server Platforms
---

### Post by Andylau on 2011-10-16
After typing the command "apt-get install openssh-server", the message below pops up:
-------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
-------------------------------
I googled this message for a while and found this quite common when installing softwares.

Is there something not yet done so this problem is here? Any help appreciated. (fixed)

---

### Post by wojox on 2011-10-16
Which server version?

---

### Post by Andylau on 2011-10-16
Um...when I type
"sudo apt-get install openssh-server" to install the OpenSSH server application. It didnt specify the version. But to me, the latest would be great.

---

### Post by wojox on 2011-10-16
Sorry what Ubuntu version (number)? etc. 11.04, 10.04?

---

### Post by Andylau on 2011-10-16
Ubuntu version 11.04. Any help appreciated please

---

### Post by Andylau on 2011-10-21
When I typed this "sudo apt-get -y install openssh-server"
It works!

---

### Post by newbie-user on 2011-10-21
In my experience, if I ever get "Package 'openssh-server' has no installation candidate", that just means to run "apt-get update" first and then try to install.

---

