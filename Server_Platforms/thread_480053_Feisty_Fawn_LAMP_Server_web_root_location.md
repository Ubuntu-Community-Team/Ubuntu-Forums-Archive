---
title: "Feisty Fawn LAMP Server web root location"
date: 2007-06-21
forum: Server Platforms
---

### Post by petersfreeman on 2007-06-21
I have just installed Feisty Fawn Ubuntu 7.04 Desktop and Ubuntu 7.04 Server in separate partitions.  I have chosen a LAMP install as I want to run a web server.  I plan to use Joomla as the Content Management System.

I thought that I could use the graphical interface of Ubuntu Desktop to reach over to the other partition and set up the web service at least initially.  Is this possible?

I have come from the Windows world of using XAMPP, Apache, PHP and Joomla so I am groping around trying to figure out where things are.  Can you tell me in what folder I should install Joomla?  When I did the LAMP Ubuntu server install, where did it put the web root?

Thank you,

Peter Freeman

---

### Post by pkarjala on 2007-06-21
The default **web root** for Apache is located at **/var/www** on your LAMP install.  Note that you can only move files into this directory using **sudo [command]**; the same goes for editing files stored in this directory.

As to whether you can use your GUI install to mess around with the other partition--I honestly don't know.  I'd imagine you can mount the second partition, and can manipulate it.  Let us know if you can--it'd be interesting to know!

---

### Post by petersfreeman on 2007-06-21
Thanks Pkarjala!  When I get home this afternoon, I'll try it out and let you know.

Cheers,

Peter

---

### Post by Widodh on 2007-06-21
Indeed, /var/www is your webroot by default.

You can change this to any directory you whish by changing the paths in /etc/apache2/sites-available/default

---

### Post by petersfreeman on 2007-06-22
Hi Widohd and Pkarjala,

Thank you for your help.  So far it looks as though I can do what I initially stared out to achieve (set up and configure files in my 7.04 server partition using the 7.04 desktop partition).  It now appears that I won't need to do that.  Here is what I have done so far:

 1. Installed Ubuntu 7.04 Server in one (primary) partition and installed LAMP option
 2. Installed Ubuntu 7.04 Desktop in another (secondary) partition
 3. Boot and log into the Server partition
 4. Followed the instructions in [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) from "Get the most recent version of Joomla!" onwards.

Everything went well with no errors until I got to "Joomla needs a database, user and password".  I first tried the command line "mysqladmin -u root -p create joomla".  It asked me for the password and I entered it (there is only one password which I use).  I received this error:

mysqladmin:  connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

Dismayed, I next went to my laptop on my network and accessed phpmyadmin by http access to the 7.04 Server ([http://192.168.1.55/phpmyadmin](http://192.168.1.55/phpmyadmin)).  I received this error:

#1045 - Access denied for user 'peter'@'localhost' (using password: YES)

I tried it again using root instead of peter as the user name with the same result.  I thought it might be due to a folder or file being read only or another restrictive attribute, so I tried the default Joomla web page that had been installed by typing [http://192.168.1.55/joomla/installation/index.php](http://192.168.1.55/joomla/installation/index.php) in the browser on my laptop.

In the "Required Settings" box one item was red:

configuration.php  	 Unwriteable
You can still continue the install as the configuration will be displayed at the end, just copy & paste this and upload.

There was another red item:   

Register Globals Emulation:  	 OFF:  	  ON  

I don't believe that this is an issue at this time.  All other settings look good and the "Directory and File Permissions Check" shows all folders as "Writeable" 

Questions:

Is it an ownership or file permission problem with file(s) or folders(s) or is it something else.
Have I missed anything?

I'll post this in the Joomla forum as well

Thanks,

Peter

---

### Post by silverglade00 on 2007-06-22
The default install of mysql has user root with no password. Type in your mysqladmin -u root -p create joomla command and just push enter when you get the password prompt.

---

### Post by petersfreeman on 2007-06-22
Thanks Silverglade,  

I came to the same conclusion myself about a half an hour ago, when I re-read the documentation thinking that I probably missed a step when shortcutting the process.  I just did as you suggested and it worked.

Cheers,

Peter

---

