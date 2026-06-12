---
title: "Problem with PHP and websvn"
date: 2008-02-09
forum: Server Platforms
---

### Post by The Titan on 2008-02-09
I have a crappy built slow server running ubuntu 6.10 because it wont read the CDROM on any version newer.(any suggestions here?)  Anyways it has APACHE2 and PHP5 installed.  Everything was working great until i installed WebSVN through apt.  All of the sudden my server has PHP4! What the heck!  Any help is appreciated! 
Edit:
I've got a little bit more information here, i messed it up even more.  Now I did 
```
#apt-get install php5 libapache2-mod-php5
```
and now PHP doesn't work at all!  I have dug myself very far into a hole i think and am willing to just remove everything relating to Apache2 and reinstall it all.   So my new question is "How do i remove everything involved with, and including Apache2"

Thanks in advance,

Dan

---

### Post by manpaz on 2008-02-09
Hi Dan,

To search the dependencies you can try to install apt-rdepends, and then make a search for apache dependencies.

```

# sudo apt-get install apt-rdepends
# apt-rdepends -p apache2 | grep -v Depends
Reading package lists... Done
Building dependency tree... Done
apache2
apache2-mpm-event
apache2.2-common
apache2-utils
...

```

I used the 'grep -v' to put on screen only the dependencies that you need.  Then to remove the package and configuration files you can use

```

# sudo apt-get --purge remove apache2

``` 

Finally, I think a good idea to remove all in a short way should be

```

# apt-rdepends -p apache2 | grep -v Depends | grep -v Done > apache2remove
# apt-get --purge remove < apache2remove

```

I hope this will help you,

-Manuel

---

### Post by The Titan on 2008-02-09
i installed apt-rdepends and did 
```

# apt-rdepends -p apache2 | grep -v Depends | grep -v Done > apache2remove 
```
and everything is fine untill
```

# apt-get --purge remove < apache2remove


```
then i get this and nothing happens
```

# apt-get --purge remove < apache2remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzzip-0-12 php4-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.

```

---

