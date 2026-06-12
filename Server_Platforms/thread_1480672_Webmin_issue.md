---
title: "Webmin issue"
date: 2010-05-11
forum: Server Platforms
---

### Post by tottenham12712 on 2010-05-11
hey everyone, so i got my server all set up with apache2 and php5 and when i try and use webmin in comes up with this error: 

The Apache server executable /etc/apache2/httpd.conf does not exist. If you have Apache installed, adjust the module configuration to use the correct path.

The Apache Webserver package can be automatically installed by Webmin. Click here to have it downloaded and installed using APT.

I have tryied every possible route i know and nothing, and i have tried the "click here" but its the old apache and doesnt exist on the server anymore.

Thanks in advance!!

---

### Post by HermanAB on 2010-05-11
Well, this is an Apache problem, not a Webmin problem.

Restart Apache and look at the log files to see why it is not working, then test it with a browser and you should get the default Apache "It Works!" page.  If not, then scan the logs again.

---

### Post by tottenham12712 on 2010-05-12
this might sound like a stupid question but where are the apache logs? i cant find them

---

### Post by kmai on 2010-05-12
If you installed everything using apt, it'd be easer to install webmin and let apt install apache and php as dependencies.

Now, if you're trying to fix this already, the logs should be at /var/log/

---

### Post by windependence on 2010-05-12
This is just because Webmin cannot find the httpd.conf where it is expecting it to be. You need to go into the Webmin Apache module configuration GUI and tell it what the path is to your configuration file. Most likely there will already be a path in the box, but it is incorrect. Overwrite it with the correct path and the Apache module will work. Right now, Webmin thinks you don't have Apache installed because it can't find the config file.

-Tim

---

### Post by tottenham12712 on 2010-05-13
i told webmin where the httpd.conf file is, im not at the server now but i believe its in /etc/apt/apache2. Webmins auto apache install doesnt work bc it uses apt-get install apache and it needs to be apache2 not apache. when i try and run the command for a stop of apache it says command not found. Any ideas? Thanks in advance! (havent looked at the logs yet im crazy busy)
 
/etc/init.d/httpd restart <-----command i used
[FONT=Courier New]apachectl -k restart[/FONT] <-----also tried that
^^^^^^^^^^^^^^^^
does something need to go before these commands?

---

### Post by windependence on 2010-05-14
> **tottenham12712 said:**
> i told webmin where the httpd.conf file is, im not at the server now but i believe its in /etc/apt/apache2. Webmins auto apache install doesnt work bc it uses apt-get install apache and it needs to be apache2 not apache. when i try and run the command for a stop of apache it says command not found. Any ideas? Thanks in advance! (havent looked at the logs yet im crazy busy)
 
/etc/init.d/httpd restart <-----command i used
[FONT=Courier New]apachectl -k restart[/FONT] <-----also tried that
^^^^^^^^^^^^^^^^
does something need to go before these commands?
Have you ever actually installed Apache since the Webmin install didn't work? You can install it using 
```
sudo apt-get install apache2 
```
This is one reason you should learn a little command line if you can. You can't always rely on Webmin to work properly for you.

Let me know if you already have Apache installed and how you installed it.

-Tim

---

### Post by tottenham12712 on 2010-05-14
I installed apache, php5, webmin through the apt-get command.
 
EDIT: So the server works i get the "it works" page i googled how to set it up with webmin and its really odd how the files dont seem like they would work but they do. im not at the server now but i will give a list of what i used later, but when i try and make webmin set up a site it doesnt work :/ im going to continue to google it, but if anyone has anyideas or links it would be much apreciated!

---

### Post by sligoman on 2010-05-14
I have not long set-up Ubuntu server and found the best way to install webmin was by following these instruction from the command line..

**Using the Webmin APT repository**

If you like to install and update Webmin via APT, edit the **/etc/apt/sources.list** file on your system and add the line: 

**deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib **

You should also fetch and install my GPG key with which the repository is signed, with these commands : 

**cd /root**

**wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)**

**apt-key add jcameron-key.asc **

You will now be able to install with the commands : 

**apt-get update**

**apt-get install webmin **

All dependencies should be resolved automatically.



Regards

Liam

---

### Post by tottenham12712 on 2010-05-14
sligoman so by doing that everything gets installed? php and apache?

---

### Post by tottenham12712 on 2010-05-14
Apache server root directory: /etc/apache2
Path to httpd executable: /usr/sbin/apache2
Command to start apache: /etc/init.d/apache2 start
Command to stop apache: /etc/init.d/apache2 stop
Path to httpd.conf: /etc/apache2/apache2.conf

settings i used to get webmin to work

---

### Post by sligoman on 2010-05-15
> **tottenham12712 said:**
> sligoman so by doing that everything gets installed? php and apache?

OH!! :shock:

Well it was just a suggestion as that it what I did when I first installed ubuntu server..

I am still on a learning curve at the moment  :wink:

---

### Post by tottenham12712 on 2010-05-16
Well either way you are a savior worked like a charm, the only thing i had to do was install php5 ( btw i did a clean install and started from scratch) everything is up and working fine and i won a few points with my boss :D. Thank you to everyone that helped out!

---

