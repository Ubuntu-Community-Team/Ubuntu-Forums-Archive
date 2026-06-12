---
title: "Printer redirection in rdesktop"
date: 2012-11-06
forum: Virtualisation
---

### Post by choppyfireballs on 2012-11-06
Hello,

   Currently I have an hp laserjet p3015 printer installed in ubuntu 12.04 and it;s working just fine, I can print whatever I need to and I have to admit the installation of the printer in ubuntu was easier than it was in windows. Anyway that aside I am trying to remote desktop into a windows machine. I am using rdesktop to connect because it's easy to create a script file for a user to click and automatically run the program and login to the remote session.

Currently i am using this code rdesktop -r hplaserjet -f  -u username -p password (ip address here)

hplaserjet is the name of the printer, ( I set it when I installed it) and I cannot get the printer reidrection to work properly. It's not even showing me the printer in the remote connection. 

I was wondering if there is another program that I can use, must be able to run it automatically, that will allow me to redirect this printer.

---

### Post by CaptainLinux on 2012-11-06
Can you try the following?

rdesktop -f -r printer:hplaserjet -u username -p password (ip address here)

---

### Post by choppyfireballs on 2012-11-06
Sorry for the mixup thats the syntax I am using i forgot to use the printer:hplaserjet in the rdesktop command. My bad. And no it did not work sorry. =-(

---

### Post by CaptainLinux on 2012-11-06
Does the "Share local printers" option in a client like Remmina work?

---

### Post by choppyfireballs on 2012-11-06
> **CaptainLinux said:**
> Does the "Share local printers" option in a client like Remmina work?

It did indeed now I have to find a way for the client to log in easily without having to memorize all the settingzs

---

### Post by CaptainLinux on 2012-11-06
> **choppyfireballs said:**
> It did indeed now I have to find a way for the client to log in easily without having to memorize all the settingzs

The graphical interface for Remmina supports creating profiles that should store all the settings for a connection.

---

### Post by choppyfireballs on 2012-11-06
> **CaptainLinux said:**
> The graphical interface for Remmina supports creating profiles that should store all the settings for a connection.

That's exactly what I did, thanks for the help guys ill mark the thread as solved

---

