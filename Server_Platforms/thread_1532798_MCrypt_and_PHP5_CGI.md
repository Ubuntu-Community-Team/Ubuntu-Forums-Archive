---
title: "MCrypt and PHP5 CGI"
date: 2010-07-17
forum: Server Platforms
---

### Post by brwarner on 2010-07-17
I am trying to install mcrypt for use in phpMyAdmin but am having some trouble. I apt-get'd the mcrypt-php5 package and it installed, but it seems to only function on the Apache Module version of php5 and not the CGI version. Both versions show the mcrypt extension installed in phpinfo, but in phpMyAdmin only one of them removes the error about mcrypt. Other extensions (such as cURL) which I installed with apt-get have worked, so I'm not sure why this one does not.

EDIT: I also compared the CGI php.ini and the apache2 php.ini and there were no differences there. I also confirmed that the php.ini file for the CGI version is loading from that location.

---

### Post by Lloyd_mcse on 2010-07-18
I had an mcrypt issue, I had to make an mcrypt.ini file containing 

extension=mcrypt.so 

and make sure I had the mcrypt.ini (I created) and mcrypt.so files in...

etc/php5/apache2/conf.d/

etc/php5/cgi/conf.d/

etc/php5/cli/conf.d/

etc/php5/conf.d/

Then it worked.
I hope that helps

Oh and if you get a php error "mcrypt" already loaded on line 0 check all the php.ini files in etc/php5/ for the line extension=mcrypt.so and remove it.

This was on Ubuntu 8.04 server.
I should point out that I am very new to ubuntu and linux but this has worked and I don't get any errors :D

---

