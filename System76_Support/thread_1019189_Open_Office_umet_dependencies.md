---
title: "Open Office umet dependencies"
date: 2008-12-22
forum: System76 Support
---

### Post by guityler83 on 2008-12-22
Hello! I have recently run into a problem while trying to install OpenOffice.org 3.0 on a frineds ubuntu 8.04 system. it seams there are some unmet dependencies as the result of a 'sudo apt-get install openoffice.org' gets the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:3.0.0-6ubuntu0intrepid1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-writer2latex but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: liblucene2-java (>= 2.3.2) but 2.2.0-2ubuntu2 is to be installed
                  Depends: openoffice.org-java-common (> 2.2.0-4) but it is not going to be installed
E: Broken packages
tyler@tyler-laptop:~$ sudo apt-get install liblucene2-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblucene2-java is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have tried installing / uninstalling some of these dependencies, but thus far have not had any success.

Short of reinstalling Ubuntu is there any thing that I could try to solve this problem?

---

### Post by Chew N Tobacca on 2008-12-22
> trying to install OpenOffice.org 3.0 on a frineds ubuntu 8.04 system.
Is it possible that the dependencies you are lacking are elements of the 8.10 ubuntu? Given the following error:
> 
openoffice.org: Depends: openoffice.org-core (= 1:3.0.0-6ubuntu0intrepid1) but it is not going to be installed
Intrepid refers to 8.10...

---

### Post by Chew N Tobacca on 2008-12-22
Apparently openoffice.org 3.0 is not available through ubuntu repositories. You might look into it here:
[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

---

### Post by Heran Bago on 2009-04-12
To install all of Open Office 3 go to [www.openoffice.org](www.openoffice.org) and get the installer. If the setup doesn't work for Java runtime reasons, run:
```
sudo apt-get install rpm
```
Extract the archive, cd to it, then:
```
sudo ./setup
```
Use the custom install in the GUI installer if you just want specific applications.

---

### Post by jjacobs2 on 2009-04-12
I'm not really sure why but I've found that synaptic package manager can sometimes handle installs that don't work with apt-get.

---

### Post by Brian_Newbie on 2009-04-13
IF you are using 8.10 intrepid and not hardy 8.04 then the following link may work for you. It worked perfectly for me on my panp4n pangolin. 

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

The above site simply upgrades your open office 2.4 to 3.0 without the need to do a fresh install.

I now have openoffice 3.0.1 in my repositories. 

Also, once it's in synaptic, you can use "edit" then "fix broken packages" to fix dependency issues.

---

