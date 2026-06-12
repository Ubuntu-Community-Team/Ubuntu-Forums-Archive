---
title: "moving default dircectory from /var/www"
date: 2008-04-09
forum: Server Platforms
---

### Post by ianb72 on 2008-04-09
I want to change the directory I store all my PHP files from /var/www to /home/ian/hmtl_files

Now I have read some of the other posts and I believe I have to change the permissions and group of the folder /home/ian/html_files and add to www-data, but how do I go about do this, or have I got it completely wrong??

Any help would be great

Ian

---

### Post by Belak on 2008-04-09
Here's the easiest way (In my opinion)
Open a terminal and run the following commands:
```
sudo chown -R ian /var/www
ln -s /var/www ~/html_files
```

I think this will work.

Basicly, it changes the ownership of the /var/www directory to your username (You might not want to use ian) and then creates a symbolic link, basicly making it so all files in the html_files directory are going to be the same as what's in the /var/www directody.

---

### Post by usernameomar on 2008-04-09
sudo cp -pr /var/www/ /home/ian/hmtl_files/

cp -pr = "p" means copy all files with the same owenrship, permissions

---

### Post by Belak on 2008-04-09
> **usernameomar said:**
> sudo cp -pr /var/www/ /home/ian/hmtl_files/

cp -pr = "p" means copy all files with the same owenrship, permissions
This method will break apache... none of the files will be updated when you change them in your folder...

---

### Post by ianb72 on 2008-04-09
> **Belak said:**
> Here's the easiest way (In my opinion)
Open a terminal and run the following commands:
```
sudo chown -R ian /var/www
ln -s /var/www ~/html_files
```

I think this will work.

Basicly, it changes the ownership of the /var/www directory to your username (You might not want to use ian) and then creates a symbolic link, basicly making it so all files in the html_files directory are going to be the same as what's in the /var/www directody.

Thanks you I will give that a go
Many thanks
Ian

---

### Post by koenn on 2008-04-09
> **usernameomar said:**
> sudo cp -pr /var/www/ /home/ian/hmtl_files/

cp -pr = "p" means copy all files with the same owenrship, permissions
this should work, if you also edit apache's site configurations : eg document root should be changed to /home/ian/hmtl_files/ ,

---

