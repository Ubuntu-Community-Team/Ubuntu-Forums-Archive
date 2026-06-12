---
title: "I've screwed up PHPMyAdmin"
date: 2009-09-06
forum: Server Platforms
---

### Post by WASHAD on 2009-09-06
I'm really, really confused. 

This all started when I couldn't get phpMyAdmin to work. I would go to firefox, point to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), and I would get the page not found error. 

I tried uninstalling and reinstalling, and changing some permissions but that doesn't seem to fix the problem. 

Next I downloaded it directly and followed the installation instructions. The first thing that I find odd is that I have to extract it into the servers root folder. I assume that means var/www. That means that I have tons of files already in www before I even start developing my web page. Is this the case?

I can get PHP my admin now, but only if I use 'http://localhost', which points me to the phpmyadmin index.php. It connects to my database OK, but I get the following error

> The additional features for working with linked tables have been deactivated. To find out why click here. 

When I click the link, I get the following messages

> 

$cfg['Servers'][$i]['pmadb'] ... 	not OK [ Documentation ]
$cfg['Servers'][$i]['relation'] ... 	not OK [ Documentation ]
General relation features: Disabled
 
$cfg['Servers'][$i]['table_info'] ... 	not OK [ Documentation ]
Display Features: Disabled
 
$cfg['Servers'][$i]['table_coords'] ... 	not OK [ Documentation ]
$cfg['Servers'][$i]['pdf_pages'] ... 	not OK [ Documentation ]
Creation of PDFs: Disabled
 
$cfg['Servers'][$i]['column_info'] ... 	not OK [ Documentation ]
Displaying Column Comments: Disabled
Bookmarked SQL query: Disabled
Browser transformation: Disabled
 
$cfg['Servers'][$i]['history'] ... 	not OK [ Documentation ]
SQL history: Disabled
 
$cfg['Servers'][$i]['designer_coords'] ... 	not OK [ Documentation ]
Designer: Disabled

I know that this means I need to change the config.inc.php file, but It is a bit greek to me as to what to change it to. 

Ideally, I'd just erase what I downloaded and use what I installed through synaptic - but I can't get that to work. 

Any suggestions?

Thanks, 

SteveJ

---

### Post by WASHAD on 2009-09-06
Crazy - its all working for me now and I'm not sure why. I changed the blowfish_secret setting in the config.inc.php in the files that I had in var/www.

Now all of a sudden [http://localhost/phpmyadmin](http://localhost/phpmyadmin) works. It didn't before. Strangly, I can now remove all phpadmin files from var/www and it still works. I gues it is using the install from synaptic. I'm really confused, but I guess I'm up and running now. 

SteveJ

---

### Post by WASHAD on 2009-09-15
I had this problem on another computer and found the solution (for me anyway) at this link. 

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

