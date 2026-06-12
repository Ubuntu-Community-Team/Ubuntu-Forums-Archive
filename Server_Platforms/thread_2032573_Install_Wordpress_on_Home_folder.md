---
title: "Install Wordpress on Home folder"
date: 2012-07-24
forum: Server Platforms
---

### Post by Jacob72 on 2012-07-24
Hello,

I am trying to install Wordpress via the terminal following [help.ubuntu.com/community/WordPress]("https://help.ubuntu.com/community/WordPress") guide, my problem is I have moved my localhost folder to my home folders to avoid permissions. 

> 
So that Apache2 knows where to find the installation folder, make a symbolic link to the Apache2 www folder: 

sudo ln -s /usr/share/wordpress /var/www/wordpress I changed the path to my home localhost folder, this worked fine but I still have the problem on the next step:

> sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost  The terminal directed me to open the browser showing: '/var/www/localhost' to continue the setup of wordpress.
What do I need to do?

Thanks

---

### Post by Habitual on 2012-07-24
> **Jacob72 said:**
> ...I have moved my localhost folder to my home folders to avoid permissions. ...

I wouldn't.
Those who sacrifice Security for Convenience get neither.

---

### Post by sandyd on 2012-07-24
> **Jacob72 said:**
> Hello,

I am trying to install Wordpress via the terminal following [help.ubuntu.com/community/WordPress]("https://help.ubuntu.com/community/WordPress") guide, my problem is I have moved my localhost folder to my home folders to avoid permissions. 

I changed the path to my home localhost folder, this worked fine but I still have the problem on the next step:

 The terminal directed me to open the browser showing: '/var/www/localhost' to continue the setup of wordpress.
What do I need to do?

Thanks
Thats not a good idea.
Apache runs under the www-data:www-data user. Since it is in your home folder, Apache CANNOT write to the wordpress folder.

---

### Post by Jacob72 on 2012-07-24
OK, I take your points. 

I would be grateful to know how you manage your sites as the root user. I am not used to dealing with permissions.

Thanks

---

### Post by LHammonds on 2012-07-26
> **Jacob72 said:**
> OK, I take your points. 

I would be grateful to know how you manage your sites as the root user. I am not used to dealing with permissions.

Thanks
By using the chown and chmod utilities.  Use "man chmod" or "man chown" for the manuals on how they are used.  For better examples, search the Internet for better explanations such as [the catcode site]("http://catcode.com/teachmod/").

**[SIZE=3]The following examples should not actually be used for your site.  They are examples to understand the process.[/SIZE]**

This example will set the ownership (individual and group-level) to be owned by the user "root" and the group called "www-data" for all .html files in the current working directory.
```
chown root:www-data *.html
```This example sets the file permissions for every .html in the corrent working folder to Read/Write (6) for the specific owner, Read-Only (4) for the owned group and Read-Only (4) for everyone else.
```
chmod 0644 *.html
```Here are the same commands but instead of assuming the current directory, the exact path is used to ensure the action is not performed on the wrong files.
```
chown root:www-data /var/www/*.html
chmod 0644 /var/www/*.html
```If all the files in the specified folder and all sub-folders need to be set, this is how it can be done using the recursive option:
```
chown -R root:www-data /var/www/*.html
chmod -R 0644 /var/www/*.html
```Great care should be taken whenever you use wild cards (*) and recursion (-R).  In some cases, you might need to run multiple commands to make sure all permissions are set correctly.  For Example:

```
chown -R www-data:www-data /var/www/*
chmod -R 0664 /var/www/*
chmod 0666 /var/www/uploads
chmod -R 0444 /var/www/images/*
chmod -R 0444 /var/www/*.html
chmod -R 0444 /var/www/*.htm
```The above sets ownership for all files under the /var/www folder to www-data.
It then sets permissions for all files under the /var/www to Read/Write for www-data and Read-Only for everyone else.
It then sets the upload folder to be Read/Write for anyone.
Then all images and html files are set to Read-Only for everyone.

Once I have my permissions setup correctly to ensure the site is usable with the least amount of permission necessary, I then write a bash script to set those permissions and schedule them via cron to run on a normal basis to ensure the permissions remain correct even if somebody messes them up.

LHammonds

---

