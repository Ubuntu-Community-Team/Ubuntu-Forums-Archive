---
title: "Apache2 Install error"
date: 2012-01-11
forum: Server Platforms
---

### Post by PallabBhowmick on 2012-01-11
Hi all ubuntus
              I am trying to install Apache2 and Php5 but when ran ´sudo apt-get install apache2´ from my terminal and I got error like this-

* Starting web server apache2                                                                                                                                                                                                                Syntax error on line 2 of /etc/apache2/conf.d/fqdn:
Invalid command 'echo', perhaps misspelled or defined by a module not included in the server configuration
Action 'start' failed.
The Apache error log may have more information.
                                                                                                                                                                                                                                       [fail]
invoke-rc.d: initscript apache2, action "start" failed.
Setting up apache2 (2.2.16-1ubuntu3.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
 :confused:

As usual [http://localhost](http://localhost) is not working!!! if anyone helps me to fix this problem that be will be perfect for me.:p

Thank you in advance.

Cheers

---

### Post by richardjh on 2012-01-20
* Starting web server apache2                                                                                                                                                                                                                   Syntax error on line 2 of /etc/apache2/conf.d/fqdn:
Invalid command 'echo', perhaps misspelled or defined by a module not included in the server configuration


From the error message above, you have an error in the file /etc/apache2/conf.d/fqdn:
On line 2 you have the word "echo" which should not be there.

If possible you need to put in the correct fqdn into /etc/apache2/conf.d/fqdn. 

On my machine I do not have that file so it may well be that you can move it to your home directory ( out the way ) and try restarting apache again. If that works you can delete the file, if it doesn't you will have to fix the config file and move it back in place.

Another alternative, depending on your set up is to completely remove apache using the package manager ( use the option to remove configuration files too ) and reinstall it.

---

### Post by PallabBhowmick on 2012-01-24
Hey 
   Thanks for your feedback regarding my problem and I solved my problem. :)

---

