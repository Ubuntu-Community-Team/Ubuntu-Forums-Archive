---
title: "var/www / LAMP trouble."
date: 2011-01-23
forum: Server Platforms
---

### Post by Edubuntu on 2011-01-23
Hi mates,

I just installed LAMP to mess around with some php etc. When i try to run a php file from anywhere else except for var/www it doesn't run. I don't have access to var/www although i am logged in as the only user (the one that i setup Ubuntu, it's administrator i presume) but i get permission to save there denied.


Please advice.

---

### Post by Vegan on 2011-01-23
You will need to create a virtual host for a web site and you are advised to read the manuals. It takes a fair bit to learn how to use Apache2 with PHP effectively.

---

### Post by Edubuntu on 2011-01-23
> **Vegan said:**
> You will need to create a virtual host for a web site and you are advised to read the manuals. It takes a fair bit to learn how to use Apache2 with PHP effectively.

Is there an easier way to just run PHP files on this computer?

---

### Post by wojox on 2011-01-23
> **Edubuntu said:**
> Hi mates,

I just installed LAMP to mess around with some php etc. When i try to run a php file from anywhere else except for var/www it doesn't run.

Apache loads php and looks to /var/www/ to parse it, unless you have created a link to your /home directory.

> **Edubuntu said:**
> Hi mates,

I don't have access to var/www although i am logged in as the only user (the one that i setup Ubuntu, it's administrator i presume) but i get permission to save there denied.

You need sudo to edit anything outside of your /home directory.

---

### Post by Edubuntu on 2011-01-23
I must use the terminal for every file i create? If so, i am not liking it :(.

I am following some PHP tutorials and therefor have to write many, + with many mistakes made it will take me a lot of time that way.

---

### Post by wojox on 2011-01-23
> **Edubuntu said:**
> I must use the terminal for every file i create? If so, i am not liking it :(.

I am following some PHP tutorials and therefor have to write many, + with many mistakes made it will take me a lot of time that way.

Like vegan stated you can create a [Virtual Host]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts")

---

### Post by kgatan on 2011-01-26
If i understand your problem right its that you cant create files directly in /var/www from ubuntu desktop?
 
This is a permission issue, /var/www is set to root as owner and group, because of that you need to "sudo" anything inside that folder.
 
Change the folder permissions for the www folder and you can edit and create files.
If you use the server just for testing then i guess its OK but its not recommende if its "active".
 
Another option is to change the apache "document root" to your home folder where you have read/write access.
Its fairly easy and there are alot of guides out there on how to edit the apache config.
 
Note that if you want to write stuff to the harddrive from PHP you need to give "www-data" permissions to your "document root" folder.
 
For testing i guess this is ok but if you want to go live with the server be carful with messing around with the permissions.

---

