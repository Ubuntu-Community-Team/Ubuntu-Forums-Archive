---
title: "joomla not loading correctly."
date: 2010-03-15
forum: Server Platforms
---

### Post by mongoose_za on 2010-03-15
Hi there,

I have seen a few posts with problems getting joomla working and I tried a few solutions but none of them worked for me so I'm starting my own thread. I have setup joomla on windows with no problems so I do understand how to install it. On UBUNTU 8.04 it is giving me endless hassles.
I setup joomla using the joomla install. I am using XAMPP. 

When I installed joomla I couldn't install the sample data so I skipped that part because I just want to get the site up and running.

Now once I've deleted the installation folder and run joomla for the first time it is giving me hundreds and hundreds of error lines or perhaps lines of code.
For Example: *"Strict Standards: Non-static method JLoader::import() should not be called statically in /home/darren/public_html/libraries/joomla/import.php  on line 29"*

I'm not too sure what I'm supposed to do. I've reinstalled PHP and I've turned ‘display_errors = Off’. I have "sudo chmod 777 -R /opt/lampp/htdocs/darren". I'm all outta ideas. I even copied a different joomla database that has the sample data to rule that out.

Any suggestions would be grand thanks!
I have attached a screenshot of how my homepage loads...

---

### Post by oj0kksn5 on 2010-03-16
what php version u using?

are you running it from /home/darren im assuming? 

is the screenshot post installation or pre?

---

### Post by mongoose_za on 2010-03-16
hey there.. 

I'm running desktop 8.04. I have don't know off hand I'll have to check when I get home but I have the most updated PHP that was avaliable in the Synaptic Package Manager. 

I was thinking of installing a newer version of Ubuntu to see if that'd help.

---

### Post by oj0kksn5 on 2010-03-16
how did you install apache2? through terminal?

---

### Post by mongoose_za on 2010-03-16
I followed this [guide]("http://ubuntuforums.org/showthread.php?t=223410") to get everything up and running.

---

### Post by mongoose_za on 2010-03-19
Ok so I have php 5.3.1 installed on my machine.
I'm using Ubuntu 9.10 now with the same issues as before with 8.04. 
I tried to run wordpress install but once i've configured the wp-config.php it can not run the install. It tell me that it can not create a conneciton to my database. I'm pretty sure these issues must be related somehow.
Joomla still has the same issue as previously posted. That screenshot was taken post install.
I current have a folder /home/darren/public_html which is linked to my htdocs in my /opt/lampp/htdocs
So when I visit a site hosted via XAMPP i goto [http://localhost/public_html/joomla/](http://localhost/public_html/joomla/) or [http://localhost/public_html/wordpress](http://localhost/public_html/wordpress) of [http://localhost/xampp](http://localhost/xampp) or [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

 I just don't understand, this stuff is supposed to be easy right?!

I'm running XAMPP for linux... I configured it using the guide I linked in my previous post. Any suggestions would be greatly appreciated.

---

### Post by mongoose_za on 2010-03-20
I solved it!

I removed lampp and I installed apache2, php and mysql all seperately. So far so good :)

---

