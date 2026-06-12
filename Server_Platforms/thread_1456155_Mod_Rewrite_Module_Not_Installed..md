---
title: "Mod_Rewrite Module Not Installed."
date: 2010-04-16
forum: Server Platforms
---

### Post by cusinndzl on 2010-04-16
I have an Apache2 Installation (I checked the LAMP server while setting up the Ubuntu 9.10 Server installation). I need the Mod_Rewrite module for something I'm doing. I have read to comment out a line from the httpd.conf. That file is empty so I added that line. Then the server said that the file was not found. I checked the installed modules in Webmin for Apache and the Mod_Rewrite was not found. I have searched around on the internet for a download for this module and can't find it. 

Can anyone help me install this module and get it enabled?

---

### Post by jhollinger on 2010-04-16
Aye that suggestion was probably for a Windows box or something. Anyway, I think Ubuntu includes the rewrite module by default, but has it disabled. Try 'sudo a2enmod rewrite'.

---

### Post by cusinndzl on 2010-04-18
Now I have the module enabled but it is not working. I'm using a file to test it and it's not working. The URL is: [http://zlstudios.net/rewrite.php]("http://zlstudios.net/rewrite.php") Is there anything I can do to fix it?

---

### Post by jhollinger on 2010-04-18
Can you post the contents of your .htaccess file? (This is usually where rewrite rules are stored.) What is it exactly you're trying to accomplish?

I also suggest you search around for mod_rewrite documentation, books, and tutorials; they abound online.

---

### Post by cusinndzl on 2010-04-18
I got it working myself, thank you for the help.

---

