---
title: "Cannot Install PHP Myadmin on 11.04"
date: 2011-07-27
forum: Server Platforms
---

### Post by patdundee on 2011-07-27
Hi Guys I have gone through each upgrade to move from Server 8.1 to Server 11.04 I have done this on three servers which work fine.

On the next server PHPMadmin would not work. So i went through the removal of any existing parts of PHPMadmin and I am trying to re install it again.

This is what I get everytime I try to install using APT 
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

 
So I have logged in Via webmin and completed a search of the APT repository and it cannot find PHPMyadmin
 
Has anyone got any deas on how i can fix this issue please
 
Many thanks

---

### Post by wt8008 on 2011-07-29
Do you have the universe section enabled?

I do see the package is available 

[http://packages.ubuntu.com/natty/phpmyadmin](http://packages.ubuntu.com/natty/phpmyadmin)

---

### Post by patdundee on 2011-08-03
Hi Guys
 
I have upgraded my server to 11.04 (Natty) I have got around the php issues where it upgraded PHP and i have changed all the depreciated php items  but I am left with a probem installing PHPMyadmin

I have done the python install and re innatlled all mysql5 php5 content

Every time I try to install PhpMyadmin I keep getting the followng error 
 
'PHPMYADMIN has no installation candidate'

Any ideas please
 
Many thanks

---

### Post by patdundee on 2011-08-03
Hi 
Thanks I have actually just added that to the sources list Natty commens out all the previous  sources lists and just lists its own
 
After adding the repo i just did an apt update and then apt get for phpmyadmin and it works again now
 
Many thanks for the response 

The E: was throwing me out as I had not selected any drives to check but for some reason even though a drive was not in the list Natty shows it as E:

Regards

---

### Post by wt8008 on 2011-08-03
Make sure you mark the thread solved now. :)

---

### Post by uRock on 2011-08-04
Bump for merging and moving to *Server Plaforms*.

---

