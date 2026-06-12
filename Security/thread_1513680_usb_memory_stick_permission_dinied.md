---
title: "usb memory stick permission dinied"
date: 2010-06-19
forum: Security
---

### Post by aprilie on 2010-06-19
Hi all
 I have an ubuntu 10.4 installed on my laptop
I had an ubuntu 9.4 on bootable usb memory stick and I thought to install ubuntu 10 .4 on bootable usb memory stick. I format it into fat16 and after that I can not write anything on my memory stick. It says permission denied 
I tried sudo chmod 777 /dev/sdb1 also I tried same command on the folder
where I mounted it. After I tried chown command in order to change ownership  from root to my-username it failed too. Please someone tell me how to make my usb memory stick again writeable ?? Also startup disk creator does not fix it too

---

### Post by Revolutionary101 on 2010-06-19
Go to "System>Administration>Users and Groups". When that window pops up select your user name and click on "Advanced Settings" then click on the "Privileges" tab. Make sure that all the check boxes are checked, especially the "Mount user-space filesystems"

---

### Post by aprilie on 2010-06-19
I did it not working
the "Mount user-space filesystems" was checked before 
thanks anyway

---

