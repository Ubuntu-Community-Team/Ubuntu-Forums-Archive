---
title: "Installation of AMP (LAMP) A Very Easy Guide by Sacchu"
date: 2010-08-13
forum: Server Platforms
---

### Post by Sacchu on 2010-08-13
Installing LAMP On Ubuntu For Newbies. Cover Ubuntu 10.4. Can also be applied to lower or higher version of Ubuntu :D:D:D

In this guide I will show you how to install a LAMP system. LAMP stands for Linux, Apache, MySQL, PHP. The guide is intended to help those who have very little knowlegde of using Linux.

Step No: 1
Install Apache:
To start off we will install Apache.

1. Open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line of code into Terminal and then press enter: sudo apt-get install apache2

3. The Terminal will then ask you for you're root password, type it and then press enter.

4. Now Apache is installed

Testing Apache:
To make sure everything installed correctly we will now test Apache to ensure it is working properly.

1. Open up any web browser and then enter the following into the web address: [http://localhost/](http://localhost/)

You should see a "It works!" on your preffered browser


Important Note: After installation when you restart Apache by typing "sudo /etc/init.d/apache2 restart" you get the following message “Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName” error on Ubuntu

1. To fix that problem, you need to edit the httpd.conf file. Open the terminal and type: sudo gedit /etc/apache2/httpd.conf

2. By default httpd.conf file will be blank. Now, simply add the following line to the file: ServerName localhost

3. Save the file and exit from gEdit.

4. Finally restart the server by typing: sudo /etc/init.d/apache2 restart



Step No: 2
Install PHP:
In this part we will install PHP 5.

1. Again open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line into Terminal and press enter: sudo apt-get install php5 libapache2-mod-php5

3. In order for PHP to work and be compatible with Apache we must restart Apache. Type the following code in Terminal to do this: sudo /etc/init.d/apache2 restart

Test PHP:
To ensure there are no issues with PHP let's give it a quick test run.

1. In the terminal type the following line: sudo gedit /var/www/testphp.php
This will open up a file called phptest.php.

2. Copy/Paste this line into the phptest file: <?php phpinfo(); ?>

3. Save and close the file.

4. Now open you're web browser and type the following into the web address: [http://localhost/testphp.php](http://localhost/testphp.php)
Your browser will display detailed PHP configeration

Congrats you have now installed both Apache and PHP!


Step No: III

Install MySQL:

1. In terminal type this line: sudo apt-get install mysql-server

2. Now MySql will ask you to type root password, type your preffered root password in next screen type the root password again 

2. Optional Step: In order for other computers on your network to view the server you have created, you must first edit the "Bind Address". Begin by opening up Terminal to edit the my.cnf file:
type: gksudo gedit /etc/mysql/my.cnf
Find and change the line: bind-address = 127.0.0.1 to your IP address.


Step No: IV

Install phpMyAdmin:

Until now you have installed AMP if we include your Linux installation it become LAMP. Don't hurry we are not yet done now we are going to install a program called phpMyAdmin which is an easy tool to edit your databases. 

1. Type the following line into Terminal: sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

2. Now the installation ask for password please type your preffered password.

After installing phpMyAdmin if you type "http://localhost/phpmyadmin you get Error 404 to over come this problem follow these steps

1. First type the following command to open up this file: gksudo gedit /etc/apache2/apache2.conf

2. Add the following line of code at bottom inside apache2.conf: Include /etc/phpmyadmin/apache.conf

3. Save it and restart Apache: sudo /etc/init.d/apache2 restart

Now you think it is done the answer is NO. Offcource you have installed LAMP successfuly by following above steps, but one final steps is still pending

1. Open terminal and type: gksudo gedit /etc/phpmyadmin/config.inc.php

2. Find and edit this line 
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysqli'; To $cfg['Servers'][$i]['extension'] = 'mysql';

3. Now find and add "$cfg['Servers'][$i]['tracking'] = 'pma_tracking';" bellow "$cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';"

If things go well you have now successful LAMP running

Important Note: Things are not over yet! One final step is still pending. If you happen to come to India you must get me my fix (Drinks):popcorn::popcorn::popcorn:

End!!

---

### Post by Sacchu on 2010-08-13
Installing LAMP On Ubuntu For Newbies. Cover Ubuntu 10.4. Can also be applied to lower or higher version

In this guide I will show you how to install a LAMP system. LAMP stands for Linux, Apache, MySQL, PHP. The guide is intended to help those who have very little knowlegde of using Linux.

Step No: 1
Install Apache:
To start off we will install Apache.

1. Open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line of code into Terminal and then press enter: sudo apt-get install apache2

3. The Terminal will then ask you for you're root password, type it and then press enter.

4. Now Apache is installed

Testing Apache:
To make sure everything installed correctly we will now test Apache to ensure it is working properly.

1. Open up any web browser and then enter the following into the web address: [http://localhost/](http://localhost/)

You should see a "It works!" on your preffered browser


Important Note: After installation when you restart Apache by typing "sudo /etc/init.d/apache2 restart" you get the following message “Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName” error on Ubuntu

1. To fix that problem, you need to edit the httpd.conf file. Open the terminal and type: sudo gedit /etc/apache2/httpd.conf

2. By default httpd.conf file will be blank. Now, simply add the following line to the file: ServerName localhost

3. Save the file and exit from gEdit.

4. Finally restart the server by typing: sudo /etc/init.d/apache2 restart



Step No: 2
Install PHP:
In this part we will install PHP 5.

1. Again open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line into Terminal and press enter: sudo apt-get install php5 libapache2-mod-php5

3. In order for PHP to work and be compatible with Apache we must restart Apache. Type the following code in Terminal to do this: sudo /etc/init.d/apache2 restart

Test PHP:
To ensure there are no issues with PHP let's give it a quick test run.

1. In the terminal type the following line: sudo gedit /var/www/testphp.php
This will open up a file called phptest.php.

2. Copy/Paste this line into the phptest file: <?php phpinfo(); ?>

3. Save and close the file.

4. Now open you're web browser and type the following into the web address: [http://localhost/testphp.php](http://localhost/testphp.php)
Your browser will display detailed PHP configeration

Congrats you have now installed both Apache and PHP!


Step No: III

Install MySQL:

1. In terminal type this line: sudo apt-get install mysql-server

2. Now MySql will ask you to type root password, type your preffered root password in next screen type the root password again 

2. Optional Step: In order for other computers on your network to view the server you have created, you must first edit the "Bind Address". Begin by opening up Terminal to edit the my.cnf file:
type: gksudo gedit /etc/mysql/my.cnf
Find and change the line: bind-address = 127.0.0.1 to your IP address.


Step No: IV

Install phpMyAdmin:

Until now you have installed AMP if we include your Linux installation it become LAMP. Don't hurry we are not yet done now we are going to install a program called phpMyAdmin which is an easy tool to edit your databases. 

1. Type the following line into Terminal: sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

2. Now the installation ask for password please type your preffered password.

After installing phpMyAdmin if you type "http://localhost/phpmyadmin you get Error 404 to over come this problem follow these steps

1. First type the following command to open up this file: gksudo gedit /etc/apache2/apache2.conf

2. Add the following line of code at bottom inside apache2.conf: Include /etc/phpmyadmin/apache.conf

3. Save it and restart Apache: sudo /etc/init.d/apache2 restart

Now you think it is done the answer is NO. Offcource you have installed LAMP successfuly by following above steps, but one final steps is still pending

1. Open terminal and type: gksudo gedit /etc/phpmyadmin/config.inc.php

2. Find and edit this line 
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysqli'; To $cfg['Servers'][$i]['extension'] = 'mysql';

3. Now find and add "$cfg['Servers'][$i]['tracking'] = 'pma_tracking';" bellow "$cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';"

If things go well you have now successful LAMP running

Important Note: Things are not over yet! One final step is still pending. If you happen to come to India you must get me my fix (Drinks).

End!!

---

### Post by Sacchu on 2010-08-13
Installing LAMP On Ubuntu For Newbies. Cover Ubuntu 10.4. Can also be applied to lower or higher version

In this guide I will show you how to install a LAMP system. LAMP stands for Linux, Apache, MySQL, PHP. The guide is intended to help those who have very little knowlegde of using Linux.

Step No: 1
Install Apache:
To start off we will install Apache.

1. Open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line of code into Terminal and then press enter: sudo apt-get install apache2

3. The Terminal will then ask you for you're root password, type it and then press enter.

4. Now Apache is installed

Testing Apache:
To make sure everything installed correctly we will now test Apache to ensure it is working properly.

1. Open up any web browser and then enter the following into the web address: [http://localhost/](http://localhost/)

You should see a "It works!" on your preffered browser


Important Note: After installation when you restart Apache by typing "sudo /etc/init.d/apache2 restart" you get the following message “Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName” error on Ubuntu

1. To fix that problem, you need to edit the httpd.conf file. Open the terminal and type: sudo gedit /etc/apache2/httpd.conf

2. By default httpd.conf file will be blank. Now, simply add the following line to the file: ServerName localhost

3. Save the file and exit from gEdit.

4. Finally restart the server by typing: sudo /etc/init.d/apache2 restart



Step No: 2
Install PHP:
In this part we will install PHP 5.

1. Again open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line into Terminal and press enter: sudo apt-get install php5 libapache2-mod-php5

3. In order for PHP to work and be compatible with Apache we must restart Apache. Type the following code in Terminal to do this: sudo /etc/init.d/apache2 restart

Test PHP:
To ensure there are no issues with PHP let's give it a quick test run.

1. In the terminal type the following line: sudo gedit /var/www/testphp.php
This will open up a file called phptest.php.

2. Copy/Paste this line into the phptest file: <?php phpinfo(); ?>

3. Save and close the file.

4. Now open you're web browser and type the following into the web address: [http://localhost/testphp.php](http://localhost/testphp.php)
Your browser will display detailed PHP configeration

Congrats you have now installed both Apache and PHP!


Step No: III

Install MySQL:

1. In terminal type this line: sudo apt-get install mysql-server

2. Now MySql will ask you to type root password, type your preffered root password in next screen type the root password again 

2. Optional Step: In order for other computers on your network to view the server you have created, you must first edit the "Bind Address". Begin by opening up Terminal to edit the my.cnf file:
type: gksudo gedit /etc/mysql/my.cnf
Find and change the line: bind-address = 127.0.0.1 to your IP address.


Step No: IV

Install phpMyAdmin:

Until now you have installed AMP if we include your Linux installation it become LAMP. Don't hurry we are not yet done now we are going to install a program called phpMyAdmin which is an easy tool to edit your databases. 

1. Type the following line into Terminal: sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

2. Now the installation ask for password please type your preffered password.

After installing phpMyAdmin if you type "http://localhost/phpmyadmin you get Error 404 to over come this problem follow these steps

1. First type the following command to open up this file: gksudo gedit /etc/apache2/apache2.conf

2. Add the following line of code at bottom inside apache2.conf: Include /etc/phpmyadmin/apache.conf

3. Save it and restart Apache: sudo /etc/init.d/apache2 restart

Now you think it is done the answer is NO. Offcource you have installed LAMP successfuly by following above steps, but one final steps is still pending

1. Open terminal and type: gksudo gedit /etc/phpmyadmin/config.inc.php

2. Find and edit this line 
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysqli'; To $cfg['Servers'][$i]['extension'] = 'mysql';

3. Now find and add "$cfg['Servers'][$i]['tracking'] = 'pma_tracking';" bellow "$cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';"

If things go well you have now successful LAMP running

Important Note: Things are not over yet! One final step is still pending. If you happen to come to India you must get me my fix (Drinks).

End!!

---

### Post by Sacchu on 2010-08-13
Hi, sorry a lot to post same thread twice. I got confused. Thanks a lot

---

### Post by Sacchu on 2010-08-13
Hi, sorry a lot to post same thread twice. I got confused. Thanks a lot

---

### Post by spynappels on 2010-08-13
Well done, however typing ```
tasksel
``` in the terminal is even easier. In the resulting window just select "LAMP server". 

Robert is very much your mother's brother!

---

### Post by Sef on 2010-08-13
Merged.

---

### Post by cariboo on 2010-08-13
Merged another thread with the two already merged. To keep from creating duplicate threads, it may be an idea to use a text editor first to create the post, especially for longer threads.

---

