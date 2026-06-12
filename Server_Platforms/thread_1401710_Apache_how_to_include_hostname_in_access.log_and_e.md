---
title: "Apache how to include hostname in access.log and error.log file names"
date: 2010-02-08
forum: Server Platforms
---

### Post by andersvinther on 2010-02-08
Hello,

I am sure this information is out there somewhere, but Googling apache access.log and hostname does not give you any good leads... so I hope someone here might be able to provide me with a quick answer...

I am setting up a cluster of web servers, so I would like to name the access.log and error.log with the hostname of the individual servers to be able to distinguish one from another.

How can I do this?

Thanks!

Anders

---

### Post by yogesh.girikumar on 2010-02-09
Hi,
       You will have to change the apache configuration file to achieve this.```
$ sudo vim /etc/apache2/apache2.conf
```or```
$ sudo nano /etc/apache2/apache2.conf
```Find out the line that says something like this:```
ErrorLog /var/log/apache2/error.log
```Then change it to 
```
ErrorLog /var/log/apache2/<error_hostname>.log
```Then edit /etc/apache2/sites-enabled/000-default file if the following line is added. 
```
CustomLog /var/log/apache2/access.log combined
```Else add it to the end of the file. rename the access.log to the desired filename. Here I've named it hostname.log
```
CustomLog /var/log/apache2/<access_hostname>.log combined
```or something that you want it to be. Then restart apache for the changes to take effect.   

For more info on logging, see:[http://httpd.apache.org/docs/2.2/logs.html](http://httpd.apache.org/docs/2.2/logs.html)

---

### Post by andersvinther on 2010-02-09
Hello yogesh,

Thanks for your quick reply.

I am sorry, but I was not specific enough in my first post.

I would like the configuration file to automatically add the hostname of the current server to the log file name without manual intervention.

This is because I am using Amazon EC2 and use the autoscaling feature. Therefore I do not know beforehand how many servers will be running and what their hostnames will be.

Is is possible to do this automatically?

Thanks,

Anders

---

### Post by yogesh.girikumar on 2010-02-11
Hi,


       There are two things you can try:


       One: You can **write a bash script** to do that.[INDENT]        A script that can automatically modify the apache configuration file and modify the value of ErrorLog and CustomLog directives to the desired filename could help.
[/INDENT]Two: You can **use "mod_macro"** which is a third party module for apache that allows you to include macros inside apache runtime configuration files.


   To install mod_macro, type the following command in the terminal:
```
$ sudo apt-get install libapache2-mod-macro
```  Activate the module and restart apache for it to take effect
```
$ sudo a2enmod macro
``` ```
$ sudo /etc/init.d/apache2 restart
```      More on mod_macro in these links:
       
[LIST=1]
[*][http://cri.ensmp.fr/~coelho/mod_macro/]("http://cri.ensmp.fr/%7Ecoelho/mod_macro/")
[*][http://cri.ensmp.fr/~coelho/mod_macro/mod_macro/mod_macro.html]("http://cri.ensmp.fr/%7Ecoelho/mod_macro/mod_macro/mod_macro.html")
[/LIST]
       A good how-to here: [http://www.howtoforge.com/mod_macro_apache](http://www.howtoforge.com/mod_macro_apache)

Hope this helps !

---

### Post by andersvinther on 2010-02-11
Hi again,

This is a bit more complicated than I was hoping for, so I'll have to put it on the shelf until I get some more time...

Thanks again for your help and the links...

Have a great day!

Anders

---

