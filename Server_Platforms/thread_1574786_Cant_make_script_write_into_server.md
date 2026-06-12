---
title: "Cant make script write into server"
date: 2010-09-14
forum: Server Platforms
---

### Post by framos41 on 2010-09-14
i have installed ubuntu server and installed too LAMP, i want to use a script that uses database, i have created the user and the database and given all privileges to the user over the database, but there is a problem, i can not get the script to write the files that have to create, olso i have problems uploading remotelly files into /var/www i have no permission to do so, i think something like that happens too when i make a change in the script and it does not write into the server, the strange thing is that it writes into the 
database but when i try to enter the folder i have created from the script i cannot enter, what can this be, do i need to configure something so the script can write without problems?

thanks in advance!

pd: i have already tried chmod 777 to /var/www and i can create files with filezilla, but the script still cant create, same thing happens for example when i test wordpress, i can´t create new pages.

Thanks!

---

### Post by nicolasdiogo on 2010-09-14
you have to check which user is calling the script.

the webserver runs under www-data:

if your script (as i guess uses a different user) you will not be able to run anything on /var/www/ folder your script need to be run by ?apache2 or www-data user.

Nicolas

---

### Post by arrrghhh on 2010-09-14
Who owns the script?  Are you running it as root or as your user?  You shouldn't chmod /var/www/ to 777, that's very dangerous - unless the server is not accessible from outside your LAN, then it's just inadvisable ;)

---

### Post by framos41 on 2010-09-14
**arrrghhh** if i do not chmod 777 /var/www i cant upload anything to the folders! what should do for this?

**nicolasdiogo** wich user do you mean? the user that i have created in phpmyadmin for the table that writes the script is called web and it have all privileges. do i have to change that user to another one? why cant i just use that one?, i have installed before this same script in a paid server and i had no problems, is there a way to do this in a own server?

Thank you

---

### Post by arrrghhh on 2010-09-14
> **framos41 said:**
> **arrrghhh** if i do not chmod 777 /var/www i cant upload anything to the folders! what should do for this?

You can create an upload-specific folder... That's what most people do, only allow uploads to one folder, so you can control where stuff can be written.  Otherwise apache would have full write access, meaning it can muck things up!

---

### Post by framos41 on 2010-09-14
you mean like address points to a /home/user/uploadfolder that is 777? thanks i will try that for security, but the problem is not chmod 777 a folder, i think is more than that because i had tried chmoding all folders i tested and it does not work, i think a permission configuration is missing.

thank you again

---

### Post by framos41 on 2010-09-16
does anyone know something about this? i have tried installation in two computers and the same thing happens, oviously im missing a step, help please thank you!

---

### Post by arrrghhh on 2010-09-16
Hrm... it seems like you're trying to do something that is more advanced than your knowledge allows.  That's alright, it just means that you need to do A LOT of diligent reading & research.  You should probably read up on how permissions work, group & user related permissions, etc.  You need to know why you're chmodding everything to 777, and what the potential repercussions of that is.

We also probably need to know more about this script you're running.  What is it?  Can you run the commands manually?  What user is the script running as?  What permissions/ownerships does this script have?

---

### Post by framos41 on 2010-09-20
Hello thank you,

  The thing is that im not trying to Run any  advanced script is only a script that uses database and php but i cant make ot work it cant write into the server, for example a script like joomla doesnt work too because of this same problem it cant write into the server i can install it and everithing but it cant work trough the admin panel because it cant write to the server the only thing im looking for is for example when you rent a common shared hosting i can create databases and users for them without a problem and install scripts with database and they work without a problem isnt there a way to do that in ubuntu server? Only having a common server

---

