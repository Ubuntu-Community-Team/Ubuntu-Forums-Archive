---
title: "b2evolution blogging software, post install set up"
date: 2008-09-11
forum: Server Platforms
---

### Post by bbrand on 2008-09-11
After installing b2evolution from the repos it does not work "out of the box", some post installation set up needs to be done. Here is what I did.

1. Find the document root of your webserver. That can be found in /etc/apache2/sites-enabled and then the config file for your virtual server. That has a "DocumentRoot" directive. In this example "/server/www" Also, make sure that the option FollowSymLinks is activated (that is the way I use the webserver, if you do not want this then where I talk about setting up symbolic links you will have to copy the contents from that directory to your document root)
2. Navigate to that document root: **cd /server/www**
3. Create a symbolic link to the b2evolution root in the document root director of the webserver. 
This root is "/usr/share/b2evolution" in the default install. I am going to call my directory "blogging". **sudo ln -s /usr/share/b2evolution blogging**
4. Navigate to this directory: **cd blogging**
5. Change the permission of the config file: **sudo chmod 666 _config.php**
6. Now start a browser and go to **http://<server ip or name>/blogging**
7. From here on in follow the post installation instructions that b2evolution provides.

Done!!

---

