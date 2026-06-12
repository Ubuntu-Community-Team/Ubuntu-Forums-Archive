---
title: "Apache2 server configurations for a Noob"
date: 2014-03-08
forum: Server Platforms
---

### Post by Weedy101 on 2014-03-08
For a few years now my hobby has been learning all things web, for this I was using the IIS7.5 server on a windows 7 64bit systems until recently when I got fed up with the way MS updates tend to mess with my set up all the time for my local host and general software. So I installed Ubuntu 12.04LTS with the lamp stack installed through *tasknel*.

Things have been great until I started working on a small project that has an image upload facility in the backend. My project is in PhP5.4, using MySql5.6, and is built in the Eclipse Indigo package. As far as I can see the correct PHP libraries are being loaded at runtime but when I try and upload an image file my script calls the **gd.php::imagecreatefromjpeg()** and I get a server response of "Fatal Error: Undefined function 'imagecreatefromjpeg()' in ${sript_path} line nn".

I cannot find why I am getting this error, there is nothing in my server logs for this problem in my project. I am assuming that the project build configuration is not matching, or is conflicting with the servers PHP configuration and thus the server is not using the same library for PHP at run time as Eclipse is for the build. So my question is; **How and where can I look up what libraries are being referenced and make sure they are the same ones?** Plus if they are not the same; **How can I update my apache2 server's configuration to use the same libraries as my Eclipse package?**

Please remember in any response that I am new to Ubuntu and will need to know where to look for any files you reference. :)

---

### Post by SeijiSensei on 2014-03-09
Ubuntu distributes many PHP modules as separate packages.  The one you're looking for is called **php5-gd**.  To install it, run "sudo apt-get install php5-gd" from the command prompt or use your graphical package manager.  You can see a list of all the modules and some related libraries by running "apt-cache search php5-*".

You'll need to restart Apache after installing the gd package with the command "sudo service apache2 restart".

I recommend creating a script called info.php with the single line
```
<?php phpinfo()?>
```
and placing it in the server's DocumentRoot.  If you then view that file with a browser, you'll see a complete description of the PHP configuration on your machine including all installed modules.

---

### Post by Weedy101 on 2014-03-09
Thanks,

So that means that even when Eclipse has the library installed my server does not have access to it and I have to instal the library myself. will this be the case with many of the php libraries?

---

