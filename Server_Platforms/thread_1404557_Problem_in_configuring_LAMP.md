---
title: "Problem in configuring LAMP"
date: 2010-02-11
forum: Server Platforms
---

### Post by ratanv on 2010-02-11
i have ubuntu (updated) on my machine and i have installed apache 2, php5 and mysql using apt-get.
all well but i am not able to open phpmyadmin or even test.php page (containing phpinfo())
though i can open the default page of apache "It Worked".
Please someone help.

---

### Post by yogesh.girikumar on 2010-02-12
Hi,


       What error do you see?. You mentioned that your apache configuration works fine and that the phpinfo() page did not.


 So, are there any errors displayed in the browser page when you try to access the test php page?? Also try checking if the package "libapache2-mod-php5" package is installed from the synaptic package manager.
```
System -> Administration -> Synaptic Package Manager
```      Also go to the directory "/etc/apache2/mods-enabled/" and check if a file named php5.load is present. If it is present it's an indication that PHP5 has been installed. Please post the contents of the php5.load file to make further troubleshooting easier.

---

### Post by wojox on 2010-02-12
[Read this on LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Porter200el on 2010-02-12
> **ratanv said:**
> i have ubuntu (updated) on my machine and i have installed apache 2, php5 and mysql using apt-get.
all well but i am not able to open phpmyadmin or even test.php page (containing phpinfo())
though i can open the default page of apache "It Worked".
Please someone help.

I believe you need to apt-get phpmyadmin seperately unless you installed the lamp package during the server install.  If you cannot open test.php, try restarting apache.  If you are going to run LAMP on Ubuntu Server, I would highly recommend reinstalling ubuntu server and configuring LAMP during the install, it will be a lot smoother, you don't have to do that, but I have noticed there are some snafu's with installing LAMP after the install.

---

