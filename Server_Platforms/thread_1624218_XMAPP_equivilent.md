---
title: "XMAPP equivilent?"
date: 2010-11-17
forum: Server Platforms
---

### Post by DanHorniblow on 2010-11-17
Hi, I currently have a windows server running with XAMPP installed.

I want to try out ubuntu server, I am a complete linux newbie and was wondering if there was a similar package to XAMPP out there with:

Apache
PHP
MySQL
And some form of ftp server

Anyone know of anything?

---

### Post by craigp84 on 2010-11-17
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

or for a native solution:

[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by syvil on 2010-11-17
If you really want to learn try this: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Ubuntu comes with a LAMP (Linux, Apache, MySQL, PHP) package but that tutorial teaches YOU how to do it.

---

### Post by DanHorniblow on 2010-11-24
> **syvil said:**
> If you really want to learn try this: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Ubuntu comes with a LAMP (Linux, Apache, MySQL, PHP) package but that tutorial teaches YOU how to do it.
Thanks alot this work a treat :)

---

### Post by drdos2006 on 2010-11-24
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by aboutell on 2010-12-08
Dan,

I am in a similar situation as you, I to run XAMPP on a windows server and was wanting to make the switch.  However, XAMPP was originally designed for Linux and has been modified to run in Windows environments.

Once you are up and running with your Linux environment, you can just go [here]("http://www.apachefriends.org/en/xampp-linux.html#374") and download XAMPP.  Then extract it into the opt folder and start the service.  You should be good to go from that point.

Below is a good tutorial for extracting XAMPP and getting started.  Please note I didn't create this tutorial, it was created by TechInTrench.

**[B]Installation Steps:**[/B]

 _**Installing XAMPP:**_
 
[LIST]
[*]Locate the downloaded XAMPP archive file to the desktop if it is not already there.[[IMG]http://yogeshrawal.files.wordpress.com/2010/11/desktop.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/desktop.png")
[*]Open the terminal by selecting  Application->Accessories->Terminal and execute the following  command (It will install the XAMPP to the folder /opt)
[/LIST]
[INDENT]*sudo tar -xzf xampp-linux-1.7.3a.tar.gz -C /opt*
[/INDENT]*[[IMG]http://yogeshrawal.files.wordpress.com/2010/11/xampp-installation.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/xampp-installation.png")*
*Congrats!!! Now XAMPP is installed under /opt/lampp directory.*
 _**Starting XAMPP:**_
 After the successful installation of XAMPP, now is the time to start the XAMPP.
 
[LIST]
[*]Open the Terminal again and type the following command.
[/LIST]
[INDENT]*sudo/opt/lampp/lampp start*
[/INDENT]* 2. *After starting the XAMPP, you should see the following lines in the Terminal.[INDENT]*Starting XAMPP for Linux 1.7.3a&#8230;*
 *XAMPP: Starting Apache with SSL (and PHP5)&#8230;*
 *XAMPP: Starting MySQL&#8230;*
 *XAMPP: Starting ProFTPD&#8230;*
 *XAMPP for Linux started.*
[/INDENT][[IMG]http://yogeshrawal.files.wordpress.com/2010/11/starting-xampp.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/starting-xampp.png")
 _**Testing XAMPP:**_
 If till now everything work fine, you can easily check whether XAMPP is running on your system or not.
 
[LIST]
[*]Type the following url in the address bar of the browser you are using:
[/LIST]
[INDENT]*[http://localhost](http://localhost)*
[/INDENT]This will result in the following login page of XAMPP.
 [[IMG]http://yogeshrawal.files.wordpress.com/2010/11/xampp-login.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/xampp-login.png")
 2.   Select your preferred language on the login page and it will redirect you to the following index page of the XAMPP.
 [[IMG]http://yogeshrawal.files.wordpress.com/2010/11/xampp-index.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/xampp-index.png")
 3.    Click the status link to check the activated components of XAMPP.
 [[IMG]http://yogeshrawal.files.wordpress.com/2010/11/xampp-status.png?w=300&h=187[/IMG]]("http://yogeshrawal.files.wordpress.com/2010/11/xampp-status.png")
 This is all about the Installation,  Start and Testing of XAMPP on your system.

The details of this tutorial can be found [here]("http://yogeshrawal.wordpress.com/2010/11/11/installing-drupal-with-xampp-in-ubuntu-10-10/").

Thanks, Andrew

---

