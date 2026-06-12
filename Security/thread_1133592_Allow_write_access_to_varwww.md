---
title: "Allow write access to /var/www?"
date: 2009-04-23
forum: Security
---

### Post by Drobbins on 2009-04-23
Hey,

I have installed apache last night along with proftpd i ftp'd into my server to upload some files to /var/www only to be told the directory i wanted to create could not be complted becuase 'Access Is Denied'. 

I tried to change the permissions from the FTP Application i was using but that didnt work, i also tried to change the permission from directly in the GUI but that didnt work either, do i need to command line to the folder and change it that way? 

If i do what is the command

> **At A Guess**
cd ~/var
chmod /www 755
exit

Many Thanks
Rich

---

### Post by davetv on 2009-04-23
sudo chmod 755 /var/www -R

---

### Post by Drobbins on 2009-04-23
Ah ha, thought it was something like that what does -R do?

Rich

---

### Post by tatw on 2009-04-23
-R = with subdirectories

O.

---

