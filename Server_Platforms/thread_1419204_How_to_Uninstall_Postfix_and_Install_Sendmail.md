---
title: "How to Uninstall Postfix and Install Sendmail"
date: 2010-03-01
forum: Server Platforms
---

### Post by schilders on 2010-03-01
Good Afternoon All,
 
I'm working on a Karmic cloud server and need to remove Postfix and install Sendmail so that OpenEMM will work. I am very new to Ubuntu and need some guidance regarding the uninstallation procedure. Can someone provide me with a link to this documentation? If you have a link to sendmail installation instructs, that would be a bonus!! Apparently only sendmail will work with OpenEMM which necessitates the Postfix uninstall.
 
Thanks,
Sid

---

### Post by skillllllz on 2010-03-01
Remove postfix...
```
sudo apt-get purge postfix
```
Install sendmail...
```
sudo apt-get install sendmail
```
Voilà!

---

### Post by schilders on 2010-03-01
> **skillllllz said:**
> Remove postfix...
```
sudo apt-get purge postfix
```
Install sendmail...
```
sudo apt-get install sendmail
```
Voilà!
 Wow!  Didn't realize it was that simple.  Does install sendmail include all the configuration prompts, or are there separate config commands to execute?
Thanks,
Sid

---

### Post by skillllllz on 2010-03-01
I'm not sure if sendmail's installer automatically prompts for configuration information. In the worst case scenario, it will not and you will have to edit the config by hand; no harm, no foul.

---

### Post by schilders on 2010-03-01
> **schilders said:**
> Wow! Didn't realize it was that simple. Does install sendmail include all the configuration prompts, or are there separate config commands to execute?
Thanks,
Sid
 
Sorry for a possibly dumb question - Does purge postfix also remove the MySQL table(s) if postfix was configured with MySQL support?  
Thanks,
Sid

---

### Post by skillllllz on 2010-03-01
"purge" not only removes postfix, but its config files too. I would be very surprised if it removed any MySQL tables in the process. If those tables are very important, you should be backing them up before you do anything, regardless of what else I or anyone tells you.

---

### Post by schilders on 2010-03-01
> **skillllllz said:**
> "purge" not only removes postfix, but its config files too. I would be very surprised if it removed any MySQL tables in the process. If those tables are very important, you should be backing them up before you do anything, regardless of what else I or anyone tells you.
I will definitely do a MySQL backup before purge postfix.  I might be paranoid, but was reading a tut where they talked about integrating Postfix with MySQL.  Since I didn't do the Postfix setup, I don't know if that's the case or not.  Better safe than sorry!  
Thanks much for your help!!

---

### Post by skillllllz on 2010-03-01
No prob. :-)

---

### Post by realpri on 2010-07-29
Please do the needful and explain detail manner

---

### Post by Jesua on 2012-01-13
> **skillllllz said:**
> Remove postfix...
```
sudo apt-get purge postfix
```
Install sendmail...
```
sudo apt-get install sendmail
```
Voilà!

Worked...

---

### Post by mörgæs on 2012-01-13
Moved to the server forum.

---

