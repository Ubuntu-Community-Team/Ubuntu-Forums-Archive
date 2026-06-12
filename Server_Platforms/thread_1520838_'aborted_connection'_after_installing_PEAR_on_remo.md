---
title: "'aborted connection' after installing PEAR on remote server"
date: 2010-06-30
forum: Server Platforms
---

### Post by naiquevin on 2010-06-30
Hi, 

I was trying to install PEAR on a remote Ubuntu server using putty. I ran an apt-get install php-pear command and everything went smoothly, but now i cannot access the website as it says 'can't establish a connection to the server' and in firebug, it shows the status 'aborted'. I even tried adding the pear path in php.ini file and restarting the apache server but no luck. What might be wrong ? Kindly help.

Thanks,
Vineet

---

### Post by naiquevin on 2010-06-30
I checked the apache2 logs and it showed the error that ioncube and zend optimizer could not be loaded .. 
I checked the dir structure and there was no ioncube dir inside the /usr/local/lib 
so i commented out these lines in php.ini .. 
After that it logged the error that eaccelerator could not be loaded .. so commented out that line as well . And after that , the site now loads properly .. 

But now i am confused that if these extensions were on in the php.ini before the pear installation why it didnt give the error before. 
and now even these directories cannot be found in usr/local/lib (the path thats shown in the php.ini file) . So does it mean that pear installation and apache restart either deleted these files or added lines to the php.ini file? 

Searching else where i found out that ioncube gives error after restarting apache and then it needs to be 'recompiled with ioncube for fixing the problem'. Although every thing is working properly now.. how do i find out if ioncube, zend optimiser and eaccelarator were working before ?

---

