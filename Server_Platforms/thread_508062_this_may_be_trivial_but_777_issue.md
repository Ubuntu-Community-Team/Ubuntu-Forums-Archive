---
title: "this may be trivial but 777 issue"
date: 2007-07-23
forum: Server Platforms
---

### Post by ratbastard on 2007-07-23
I have NFS set up and working 
I want to make the /var folder and all of its sub directories to be able to be written to 


sudo chmod 777 /var is what I am doing but it does not seem to work -- 

How do I go about this -- 

I am accessing the /var file on the NFS client.   I want to put web-pages in the /WWW folder but I Am being denied --  

I know this is easy but for me it is not --

---

### Post by dreadlord_chris on 2007-07-23
> **ratbastard said:**
> I have NFS set up and working 
I want to make the /var folder and all of its sub directories to be able to be written to 


sudo chmod 777 /var is what I am doing but it does not seem to work -- 

How do I go about this -- 

I am accessing the /var file on the NFS client.   I want to put web-pages in the /WWW folder but I Am being denied --  

I know this is easy but for me it is not --

why would you want to do that to the whole /var tree? Just chmod the /var/WWW folder...

---

### Post by lugos on 2007-07-23
> **ratbastard said:**
> I have NFS set up and working 
I want to make the /var folder and all of its sub directories to be able to be written to 


sudo chmod 777 /var is what I am doing but it does not seem to work -- 

How do I go about this -- 

I am accessing the /var file on the NFS client.   I want to put web-pages in the /WWW folder but I Am being denied --  

I know this is easy but for me it is not --

I had a similar question, check this thread out: [http://ubuntuforums.org/showthread.php?t=506545](http://ubuntuforums.org/showthread.php?t=506545).

Hope that helps.

---

### Post by meatpan on 2007-07-24
chmod needs the -R flag to operate recursively.  Otherwise you will only change the permissions of the file or directory supplied to the command line.

Consider the implications of allowing everyone access to add, delete, and update the information under /var.  There is potentially a substantial amount of useful information in this file tree, such as database caches and email files.

Learning the proper use of permission policies takes a while, so be patient and continue to ask questions.

---

### Post by ratbastard on 2007-07-24
Thanks much to all !!!


 I will stick with the single file just the /www for now.

---

### Post by dreadlord_chris on 2007-07-24
> **ratbastard said:**
> Thanks much to all !!!


 I will stick with the single file just the /www for now.

good idea.... 

btw, /www is a folder is a folder (or directory) not a file.

---

