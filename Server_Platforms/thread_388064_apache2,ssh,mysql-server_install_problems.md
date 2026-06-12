---
title: "apache2,ssh,mysql-server install problems"
date: 2007-03-19
forum: Server Platforms
---

### Post by WhiteDragon4Ever on 2007-03-19
ok i am NEW to linux and ubuntu.
so i typed sudo apt-get install apache2               or ssh or mysql-server
and what it get is....
this one is for apache2
this is what i get...

reading package lists... Done
building dependancy tree... Done
Some packages could not be installed. This may mean that you have requested and impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

the following packages have unmet dependancies:
  apache2: Depends: apache2-mpm-worker (= 2.0.55-4ubuntu2.1) but it is not going to be installed or 
                               apache2-mpm-prefork (= 2.0.55-4ubuntu2.1) but it is not going to be installed or
                               apache2-mpm-perchild (= 2.0.55-4ubuntu2.1) but it is not going to be installed
E: Broken packages

above is apache2

below is ssh
sudo apt-get install ssh

Reading package lists... Done
Building dependancy tree... Done
Package ssh is not available, but is referred to by another package.
this may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
    openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate

above is ssh

bellow is mysql-server
sudo apt-get install mysql-server

reading package lists... Done
building dependancy tree... Done
Some packages could not be installed. This may mean that you have requested and impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

the following packages have unmet dependancies:
   mysql-server:  Depends: mysql-server-5.0 but it is not going to be installed
E: Broken packages


SO any one know what is going on? and how to fix it? and if this means anything yes i can serf the net right now so it has access to the net.

---

### Post by WhiteDragon4Ever on 2007-03-19
NVM I guess I didn't restart my computer bc it worked once i restarted my computer.

---

