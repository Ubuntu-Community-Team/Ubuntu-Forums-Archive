---
title: "Restricting directory access with .htaccess"
date: 2009-07-16
forum: Server Platforms
---

### Post by Zyndrof on 2009-07-16
Hey there,

Is there a .htaccess directive in Apache that allows me to restrain scripts in selected subfolders from accessing it's parents?

In my case I have an application that allows third-party scripts to be run from their own folders. The structure looks like this:

projects_folder
|-- script_folder_1
|-- script_folder_2
|-- script_folder_3
|-- etc...

I want each script_folder to act as it's own website. Their root is the folder itself. Meaning that if I run a script in any one of the script folders they will not be able to manipulate data in any other script folder, nor the projects_folder or the application itself.

How can this be solved?

Thank you very much for your time.
Chris

---

### Post by cpetercarter on 2009-07-16
I am not sure I understand why you want to achieve this through an .htaccess file. Can you not write the script for each folder so that it does not access any of the others?

---

### Post by Zyndrof on 2009-07-16
The folders are created by my applications users and not me, therefore I won't have any control of their contents.

This is why I would like to control it dynamically through the web server.

---

### Post by cpetercarter on 2009-07-17
If you google for "user authentication .htaccess" you will find a number of resources which should point you in the right direction.

---

### Post by Zyndrof on 2009-07-17
> **cpetercarter said:**
> If you google for "user authentication .htaccess" you will find a number of resources which should point you in the right direction.

I do not want to password protect these folders. Authentication is made in the application itself. These folders however are supposed to be accessed from the outside.

What I would like to restrict is if say:

A user writes a PHP script which lists all files in "../../". From their folder that would mean the script will list all files in my application.

So for each subfolder in projects_folder I want the settings for the root to be that folder. So if someone is using said script they would never reach beneath "projects_folder/the_script_folder".

---

### Post by cpetercarter on 2009-07-17
I think your solution is to set an open_basedir restriction for script_folder1, script_folder2 etc. This will prevent the script from opening any file outside the path or paths which you specify in the restriction. You can do this in php.ini, or in the Apache config file, or in an .htaccess file. If you want to use .htaccess, Apache must of course be configured for AllowOverride All or AllowOverride Options.

Edit : see [http://www.php.net/manual/en/ini.sect.safe-mode.php](http://www.php.net/manual/en/ini.sect.safe-mode.php). It seems that in php < 5.3.0, you can set the open_basedir restriction only in php.ini or httpd.conf.

---

### Post by Zyndrof on 2009-07-18
Thank you. I will have a look at that :)

Is it going to be enough to restrict access with open_basedir for scripts written in Rails or Python (which will be allowed also) or do I need one restriction for each allowed programming language?

/Chris

---

### Post by cpetercarter on 2009-07-18
No, open_basedir is a php configuration setting. It will affect only php scripts. WScripts written in other languages will be unaffected by it.

I have done some reading/googling and I guess that mod_access directives in the .htaccess file may (finally!) be the answer. Have a look at [http://httpd.apache.org/docs/1.3/mod/mod_access.html]("http://httpd.apache.org/docs/1.3/mod/mod_access.html")

---

### Post by Zyndrof on 2009-07-19
Thanks, that seems to be it! :)

---

