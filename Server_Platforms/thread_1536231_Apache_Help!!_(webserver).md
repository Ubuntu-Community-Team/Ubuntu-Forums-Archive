---
title: "Apache Help!! (webserver)"
date: 2010-07-21
forum: Server Platforms
---

### Post by tottenham12712 on 2010-07-21
My boss has set me on a project to serve websites for customers, basically our webserver has 4 eth ports all with a static ip. This works fine when we had 4 websites but now more and more people want websites hosted and i cant figure out how to get more than one website on a single ip address. ive gone by this [http://httpd.apache.org/docs/2.0/vhosts/mass.html](http://httpd.apache.org/docs/2.0/vhosts/mass.html)

and im lost, im not a beginner at linux but im not a wizard or anything. Im using webmin with apache on it, any help would be greatly appreciated, i can send screenshots if needed.

Thanks in advance!!

I forgot to add that the httpd file is blank?

---

### Post by sfr on 2010-07-22
I am pretty sure your questions can be answered by [apache.org]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")

Basicly you serve sites by their DNS-registered names instead of IP's. In DNS you would have different websites refer to the same ip.

Apache2 does not use teh httpd.conf file anymore, instead the configuration is split into multiple files. 
The global part is now in /etc/apache2/apache.conf. You configure virtual hosts preferably in their own conf files in /etc/apache2/sites-available, look at the default-000 example for inspiration. After you have added a configuration file there you can activate it with a2ensite SiteName which will symlink your configuration file into the directory sites-enabled. The command will prompt you to restart/reload your apache process, which you should do after first running a configtest 'apache2ctl configtest' and correct eventual errors.

---

### Post by richardjh on 2010-07-22
This is covered in detail in the apache documentation.
To make it easier to find, you will need to look up information on apache virtual hosts

[This is a good starting point]("http://httpd.apache.org/docs/2.0/vhosts/examples.html") and should get you set up in no time with a little effort.

If you find you have specific problems in setting this up, post back and we will help you out.

---

### Post by tottenham12712 on 2010-07-23
ok thanks for your help guys, i gotta fool around with it a little and see if i get anywhere ill update you soon.

---

### Post by sylvester_0 on 2010-07-23
I highly recommend using a web control panel (such as ISPConfig) for such a task.

---

### Post by minhnghivn on 2010-07-25
This is an example that does work on my system. The idea is to provide each of your webapps with a particular port number (same IP)

   [FONT=&quot][/FONT][FONT=&quot]Listen 3000[/FONT]
  [FONT=&quot]Listen 5000[/FONT]
  
  [FONT=&quot]NameVirtualHost 127.0.0.1:3000[/FONT]
  [FONT=&quot]NameVirtualHost 127.0.0.1:5000[/FONT]
  
  [FONT=&quot]<VirtualHost 127.0.0.1:3000>[/FONT]
  [FONT=&quot]   DocumentRoot "C:\My Sites\Site1"[/FONT]
  [FONT=&quot]   [/FONT][FONT=&quot]</VirtualHost>[/FONT]
  
  [FONT=&quot]<VirtualHost 127.0.0.1:5000>[/FONT]
  [FONT=&quot]   DocumentRoot "C:\My Sites\Site2"[/FONT]
  [FONT=&quot]   [/FONT][FONT=&quot]</VirtualHost>[/FONT]
  
After all, you can access your first and second site at [http://127.0.0.1:3000](http://127.0.0.1:3000) and [http://127.0.0.1:5000](http://127.0.0.1:5000) accordingly

Good luck

---

### Post by sylvester_0 on 2010-07-25
OK guys, here is an example right out the link that richardjh provided:

```
NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.ubuntuforums.org
ServerAlias ubuntuforums.org
DocumentRoot /www/ubuntuforums
</VirtualHost>

<VirtualHost *:80>
ServerName www.ubuntu.com
ServerAlias ubuntu.com
DocumentRoot /www/ubuntu
</VirtualHost>
```

With the above config, you'll be able to access (for example) both ubuntu.com and ubuntuforums.org on any IP address of the box, without any port trickery etc.

---

