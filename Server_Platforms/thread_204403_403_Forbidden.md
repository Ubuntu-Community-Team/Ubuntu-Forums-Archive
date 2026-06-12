---
title: "403 Forbidden"
date: 2006-06-27
forum: Server Platforms
---

### Post by superpwnage on 2006-06-27
I have just set up a LAMP server and everything seems to be working.. exept when I try and access my [http://localhost](http://localhost), it gives me this:

```

Forbidden

You don't have permission to access / on this server.

```

I'm not sure how to fix this. Any help is appreciated.

EDIT-
Well.. Ive been fishing around on the Apache FAQ's section, and found this-
[http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden]("http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden")

It says..
"The underlying file system permissions do not allow the User/Group under which Apache is running to access the necessary files"

This is probably because of the folder is under the root user... but again, me being so new to Linux.. I am not sure how to change it to give the proper permissions. Again, any help is appreciated.
-Ben

---

### Post by Zimmer on 2006-06-27
[QUOTE=superpwnage]

EDIT-
Well.. Ive been fishing around on the Apache FAQ's section, and found this-
[http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden]("http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden")

It says..
"The underlying file system permissions do not allow the User/Group under which Apache is running to access the necessary files"

This is probably because of the folder is under the root user... but again, me being so new to Linux.. I am not sure how to change it to give the proper permissions. Again, any help is appreciated.
-Ben[/QUOTE]
The answer as to how is a bit further on in the paragraph, but as you are new to Linux it probably did not mean much to you...
> In the case where file system permission are at fault, remember that not only must the directory and files in question be readable, but also all parent directories must be at least searchable (i.e., chmod +x /directory/path) by the web server in order for the content to be accessible.
Basically, chmod +x  is a Terminal command that will change the permissions on directories and files to make them executable..
These two links will be of help for you to learn more about this.
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
..and other good stuff...
[http://www.linuxnewbieguide.org/chap11.php](http://www.linuxnewbieguide.org/chap11.php)

I did have Apache set up on my old Hoary install and remember reading lots about taking care where to store the content I WANTED it to access, so that I was not 'accidentally' granting permissions to other files on the system that I did NOT want people to access.

I hope this helps, I cannot be more specific at the moment as I do not have Apache set up on my machine to give you any direct comparisons..

---

### Post by superpwnage on 2006-06-27
[QUOTE=Zimmer]

Basically, chmod +x  is a Terminal command that will change the permissions on directories and files to make them executable..
These two links will be of help for you to learn more about this.
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
..and other good stuff...
[http://www.linuxnewbieguide.org/chap11.php](http://www.linuxnewbieguide.org/chap11.php)

[/QUOTE]

Thanks for the reply,

I am aware of the chmod command and what it is used for, and I did try to change the permissions and owner of the index file and the directories above it in the file hierarchy. However.. none of my efforts seem to have done anything. This is what the index looks like-

-rwxr-xr-x 1 root root   82 2006-06-27 00:50 index.php

The permissions are set to 755 as you can see.. clearly allowing anybody to read/execute it. Where is apache reading the file from exactly? I was never sure of this but understood that it was in the var/www directory (where this file is located).. is this right?

Also, I have not messed with the "VirtualHost" configuration for apache and left it as the default. I am not familiar enough with apache to change it as of yet.. maybe the problem lies there.

-Ben :confused:

---

### Post by MJN on 2006-06-27
Have a look in /var/log/apache2/access.log and error.log to see give you a better clue where it was looking. Then, if the location is correct, you need to make sure your permissions are correct (including the x for parent directories as Zimmer discussed).

Mathew

---

### Post by superpwnage on 2006-06-28
[QUOTE=MJN]Have a look in /var/log/apache2/access.log and error.log to see give you a better clue where it was looking. Then, if the location is correct, you need to make sure your permissions are correct (including the x for parent directories as Zimmer discussed).

Mathew[/QUOTE]

There seems to be nothing important there... the access log is blank and the error log has nothing but notices.

Which directories do I have to change directories for exactly? I did change the permissions for the var folder, www folder, and the index file to be executable by everybody, with no avail.

---

### Post by Zimmer on 2006-06-28
[http://www.joahua.com/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy](http://www.joahua.com/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy)


This link indicates Ubuntu uses a different config file( apache2.conf) to the standard httpd.conf.. is this still correct? If so, then in the Apache FAQ you mentioned in your first post the answer may be in the misconfigured Files container as per FAQ #15

---

### Post by superpwnage on 2006-06-28
[QUOTE=Zimmer][http://www.joahua.com/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy](http://www.joahua.com/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy)


This link indicates Ubuntu uses a different config file( apache2.conf) to the standard httpd.conf.. is this still correct? If so, then in the Apache FAQ you mentioned in your first post the answer may be in the misconfigured Files container as per FAQ #15[/QUOTE]

That is certainly good to know... however I havent even touched either of those files and am using the default configuration. This is actually the second time I've installed Apache, the first time was from the source and was installed in my user folder under the home folder. It worked when it was installed there... (](*,) ). What is installed now is Apache2, PHP5, and MySQL5 from the repositories after I uninstalled the first set.

Ahh..*deep breath*
I did find the non-malformed "Files" container in apache2.conf... so thats not it.. and, after rebooting my PC I now find that I can't even start Apache2. Well, I can start it, but I dont see any "httpd" processes running, only a string of "apache2"s. Also, the error and access logs still don't show anything of value. When I try to stop it I get-

```
admin@superpwnage01:~$ /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server... httpd (pid 5669?) not running

```

Hmm... perhaps today i'll shoot myself.

-Ben

---

