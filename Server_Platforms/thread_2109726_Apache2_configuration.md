---
title: "Apache2 configuration"
date: 2013-01-28
forum: Server Platforms
---

### Post by whtemple1959 on 2013-01-28
To be honest I have practically no real experience with Apache and am intimidated about making changes to any of the files.

But, I need to get a web based application up and running for my business.

I have Ubuntu 12.04 and LAMP installed on pc1.

I have the web application located at /var/www/wkhmk
I can access the site and perform all tasks  from pc1 via localhost/wkhmk
I can access the login screen from pc1 via 192.168.1.113/wkhmk but get a blank screen after typing in the log in credentials.
I  can access the login screen from pc1 via the machine's name...  ubuntu/wkhmk but again get a blank screen after typing in the login  credentials
From pc2 I can access the website application via the ip  address 192.168.1.113/wkhmk but after typing in the log in credentials I  get sent to a web based error page.
From pc2 I cannot access the website using the machine name... ubuntu/wkhmk again being redirected to a web based error page.

I  am somewhat  confused as to which file needs to be changed to allow  access via the ip address or the machine name but what confuses me is  why I can get to the log in screen but no further.

I have  searched but have not found any references to this particular situation.  To be honest I have not been able to frame the Google search parameters  in such a way to get a qualifying response.

I admit to being  intimidated by altering any configuration files and of not fully  understanding the apparent explanations I have found so far.

So could some one please supply guidance?

---

### Post by hydn79 on 2013-01-28
Edit php.ini and change:
```
display_errors = Off
```

to 

```
display_errors = On
```

Then paste the error here if any.

---

### Post by chrisguk on 2013-01-28
Hey there and welcome to the world of Ubuntu.

Take a look at this post I replied to and see if the steps help you at all.

Generally you are probably getting a blank page because the POST action is not redirecting you to the correct path I believe.

Here's the link:

[http://ubuntuforums.org/showthread.php?t=2109364]("http://ubuntuforums.org/showthread.php?t=2109364")

---

### Post by chrisguk on 2013-01-28
Sorry double post in error

---

### Post by whtemple1959 on 2013-01-29
hydn79 -
 

 I edited the php.ini file found in /etc/php5/apache2/
 restarted apache  
 after logging in to my web app I got a blank screen
 

 Returned the php.ini to it's original state
 

 chrisguk -
 

 my /etc/hosts file looks like this...
 127.0.0.1	localhost 
 127.0.1.1	ubuntu
  
 # The following lines are desirable for IPv6 capable hosts 
 ::1     ip6-localhost ip6-loopback 
 fe00::0 ip6-localnet 
 ff00::0 ip6-mcastprefix 
 ff02::1 ip6-allnodes 
 ff02::2 ip6-allrouters
 

 I added...
 127.0.1.2	wkhmk 
 directly below 127.0.1.1	ubuntu
 this file has rw for root and r for every one else
 

 I created a file /etc/apache2/site-available/wkhmk and inserted..
 <VirtualHost 127.0.1.2:80> 
         ServerName wkhmk 
         ServerAlias [www.wkhmk](www.wkhmk) 
         ServerAdmin admin@wkhmk 
         DocumentRoot /var/www/wkhmk 
         <Directory /var/www/wkhmk> 
                 Options FollowSymLinks 
                 AllowOverride All                                                                                              
         </Directory>                                                                                                           
                                                                                                                                
 </VirtualHost>
 

 this file has rw for root and r for every one else
 

 I have no idea what a2enmod does but I followed your instructions and did a sudo rewrite.
 I then did the sudo a2ensite wkhmk
 I then did sudo service apache2 restart
 

 I then created a file .htaccess in /var/www/wkhmk and inserted …
 RewriteBase /  Now...
 

 I can get to my web application form my pc using localhost/wkhmk, ubuntu/wkhmk, 192.168.1.113/wkhmk, even wkhmk/index.php ...and ... I can get into my web application after logging in so that aspect has been resolved.
 

 Thank you!
 

 But, I am still unable to reach the web application after typing in my credentials from pc2.
 

 So now the question...
 

 If from pc2 I type 192.168.1.113/wkhmk I can get to the web app's log in screen what is blocking pc2 from “entering” the web app?
 In layman's terms...I can get to the house, I can unlock the door, but the door ain't opening.
 Why?
 

 I look forward to more advice.
 

 Thank you both.

---

### Post by SeijiSensei on 2013-01-29
This sounds more like a problem with the application itself rather than Apache.  Have you asked for support at the application's website?

---

