---
title: "Newb: What owner/permissions should www have?"
date: 2007-11-28
forum: Server Platforms
---

### Post by Smartin on 2007-11-28
Hi,

I'm trying to install Joomla on a feisty box.

To do the install I download joomla and unpack it in my home folder.

I then go to the terminal and do a 'gksudo nautilus' , navigate to the www folder and drag the joomla folder from my home folder into it.

The problem is that I still own the joomla folder within the www folder.

Permissions for the joomla folder during installation should apparently be 777 but, generally speaking, who should be the owner of anything in the /var/www folder? 

apache? root? www-data?

Thanks! :-)

Simon

---

### Post by p_quarles on 2007-11-28
If you have the default version of Apache the owner (user and group) should be www-data. 

Also, there's no reason for a permissions level higher than 774.

---

### Post by Smartin on 2007-11-28
> **p_quarles said:**
> If you have the default version of Apache the owner (user and group) should be www-data. 

Also, there's no reason for a permissions level higher than 774.

p_quarles,

Thank you so much!

Once I have the install done I'll change the permissions to 774.

Simon

---

