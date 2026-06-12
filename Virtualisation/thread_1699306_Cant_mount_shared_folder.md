---
title: "Cant mount shared folder"
date: 2011-03-03
forum: Virtualisation
---

### Post by anton706 on 2011-03-03
Hi I have a windows host and ubuntu 10.10 guest using VM virtual box I can't mount the folder i want in ubuntu.
First I used the command :"sudo mount -t vboxsf shared ~/host"
and it worked but when I checked the option to make permanent and used the same command it couldn't mount the folder and print the error:invalid argument 

how can I mount the folder with the "make permanent" option checked?

---

### Post by anton706 on 2011-03-05
83 views and 0 comments!?
comment please

---

### Post by kleskjr on 2011-03-06
Hi, I had the same problem until now. I had to reinstall Guest Additions through the virtual CD (VBOXADDITIONS) each time before I run the mount command.

I am not sure why it works now..I removed the shared folder from the Vbox menu, and added it again. I checked just the make permanent option (no auto-mount), and now it works!

I also edited /etc/rc.local , so now the shared folder is mounted automatically now.

I would suggest you to reinstall the Guest Additions, then add the shared folder in the VBox menu once again (use just permanent option), and hope that it works.

---

### Post by anton706 on 2011-03-07
I fixed it the folder I wanted to mount was in my dropbox folder after I copied the folder Iwanted to mount out off dropbox ubuntu successfully mounted it.

---

