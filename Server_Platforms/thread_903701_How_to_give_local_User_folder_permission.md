---
title: "How to give local User folder permission?"
date: 2008-08-28
forum: Server Platforms
---

### Post by bad8174 on 2008-08-28
OK, heres what Im wanting to do and Im a newbie. I have set up a simple website using Apache ruuning on Ubuntu server. I have left the default web folder to /var/www/. I have created a FTP site on this server for local logins to redirect to the web folder so our developer can publish changes to the site via ftp. I have created a local user, however when I login to the ftp site it will not allow me to create files in the /var/www/ directory. I assume this is a simple permission issuse. Can someone give me the sudo code I need to use? Thanks!

---

### Post by de0xyrib0se on 2008-08-28
This is a simple issue indeed you want user X to write to a folder most likely owned by root. The command to make user X owner of that folder is:

> sudo chown X /var/www -R

Where X is the username. However this is **extremely bad practice**! I would suggest you create a subfolder in the /var/www folder and give the user rights to that folder not the root www folder. Or better yet use a Virtual Host with a local DNS entry for testing.

---

### Post by bad8174 on 2008-08-28
Thanks man. How do I create a folder inside of the www directory?

---

### Post by de0xyrib0se on 2008-08-28
> 
sudo mkdir /var/www/<foldername>
sudo chown X /var/www/<foldername>


Then you can reach this as:

http://<server_ip>/<foldername>

Goodluck.

---

### Post by de0xyrib0se on 2008-08-28
Also keep in mind Apache needs to have /var/www as its root, most Ubuntu installs have /var/www/apache2-default as their root http folder for non virtual host requests.

In that case you need to create the folder inside apache2-default.

---

### Post by hrod beraht on 2008-08-28
> **de0xyrib0se said:**
> This is a simple issue indeed you want user X to write to a folder most likely owned by root. The command to make user X owner of that folder is:

> sudo chown X /var/www -R 

Where X is the username. However this is **extremely bad practice**! I would suggest you create a subfolder in the /var/www folder and give the user rights to that folder not the root www folder. Or better yet use a Virtual Host with a local DNS entry for testing.

Rather than change the ownership of /var/www from root, couldn't you just change the group name/permissions and make sure the user is part of that group?

Bob

---

### Post by de0xyrib0se on 2008-08-28
Either way works and either way is the wrong way to do this, subfolder or virtual hosts is the way to go.

---

### Post by affableindia on 2009-11-29
thank you brothers this helped me a lot. 

i'm sick in using gksudo nautilus

---

