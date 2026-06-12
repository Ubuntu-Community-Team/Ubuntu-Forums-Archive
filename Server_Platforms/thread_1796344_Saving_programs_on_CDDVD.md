---
title: "Saving programs on CD/DVD"
date: 2011-07-03
forum: Server Platforms
---

### Post by mandza on 2011-07-03
hi,
i have a question.
i want to install server with full programs but every time i need to download them from internet.
i had downloaded programs with sudo apt-get download. but how can i install that programs from cd or dvd???

---

### Post by Lars Noodén on 2011-07-04
If you have the individual .deb files, and their dependencies, then you can use the program [dpkg](http://manpages.ubuntu.com/manpages/natty/en/man1/dpkg.1.html) to install them manually from CD or DVD.

---

### Post by LtPitt on 2011-07-04
You could also prepare a complete server and save it on cd using the wonderful Remastersys :)

---

### Post by mandza on 2011-07-04
Thank you very much.
sudo dpkg -i myprogramfile.deb
i installed like that.

---

### Post by mandza on 2011-07-04
> **LtPitt said:**
> You could also prepare a complete server and save it on cd using the wonderful Remastersys :)

Remastersys is also good thing. i will look about it.
when i finish my server configuration it will be helpfull.

---

### Post by Gyokuro on 2011-07-04
You can clone a whole disk via dd or use clonezilla.

---

