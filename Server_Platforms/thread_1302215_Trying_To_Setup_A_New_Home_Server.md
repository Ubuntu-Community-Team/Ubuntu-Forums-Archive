---
title: "Trying To Setup A New Home Server"
date: 2009-10-26
forum: Server Platforms
---

### Post by ToddAP79 on 2009-10-26
i recently upgraded my parents computer, so i know i have their old one and would like to install ubuntu on it.

i would to be able to use the computer as a internal web server and a file server.

i would like to install
Apache
MySQL
phpMyAdmin
PHP5
Samba
WebMin

i would like to run the websites in different ip's, not sure i am going to need DNS.

any help will be nice.
thank you.

---

### Post by nsche on 2009-10-26
Looks like a reasonable objective.  You can install the Ubuntu server version off of the alternative cd and I think a lot of what you are looking for would be installed by default.  All of the things you mention are easily available on Ubuntu and run well.  I do not have experience with Samba or WebMin but have run the rest of the stuff and find it works well.

For the websites you can use virtual hosts (on Apache) and use the same ip for all of them or you can use multiple ip addresses.  I do not have experience with multiple ip addresses on one interface in Ubuntu but it used to work fine on Solaris.  I am running a couple of web sites on apache using virtual hosts.  There is one ip and multiple names.  If I connect to OC_dev I get a development server if I connect to OC_prod I get a production server.  These are both web sites (really ruby on rails) on one ip with different names.  I had to put the names in the /etc/hosts files on the systems I want to connect to/from because I was not interested in screwing with DNS.

Do you have some other specific question or problem?

---

### Post by nsche on 2009-10-26
Looks like a reasonable objective.  You can install the Ubuntu server version off of the alternative cd and I think a lot of what you are looking for would be installed by default.  All of the things you mention are easily available on Ubuntu and run well.  I do not have experience with Samba or WebMin but have run the rest of the stuff and find it works well.

For the websites you can use virtual hosts (on Apache) and use the same ip for all of them or you can use multiple ip addresses.  I do not have experience with multiple ip addresses on one interface in Ubuntu but it used to work fine on Solaris.  I am running a couple of web sites on apache using virtual hosts.  There is one ip and multiple names.  If I connect to OC_dev I get a development server if I connect to OC_prod I get a production server.  These are both web sites (really ruby on rails) on one ip with different names.  I had to put the names in the /etc/hosts files on the systems I want to connect to/from because I was not interested in screwing with DNS.

Do you have some other specific question or problem?

---

### Post by ToddAP79 on 2009-10-27
> **nsche said:**
> Looks like a reasonable objective.  You can install the Ubuntu server version off of the alternative cd and I think a lot of what you are looking for would be installed by default.  All of the things you mention are easily available on Ubuntu and run well.  I do not have experience with Samba or WebMin but have run the rest of the stuff and find it works well.

For the websites you can use virtual hosts (on Apache) and use the same ip for all of them or you can use multiple ip addresses.  I do not have experience with multiple ip addresses on one interface in Ubuntu but it used to work fine on Solaris.  I am running a couple of web sites on apache using virtual hosts.  There is one ip and multiple names.  If I connect to OC_dev I get a development server if I connect to OC_prod I get a production server.  These are both web sites (really ruby on rails) on one ip with different names.  I had to put the names in the /etc/hosts files on the systems I want to connect to/from because I was not interested in screwing with DNS.

Do you have some other specific question or problem?

thanks for the help, i will post something later if i have any problems.

---

### Post by joys666 on 2009-10-29
Hi! I'm about to do the same thing, I'm well familiar with win2k and win2k3 servers. But I've never done a Linux setup. I got hold of two pdf doc's how to configure and setup 'ubuntu server'-version - not alternative which is recommended here - but those 'pdf's' are for 6.06 (drapper drake), but the basic ought be the same, or?
And should I use the 'alternative CD' instead of the server, or can I transform the Desktop version to such a server (look at the quote), I ave the same goals with my server as ToddAP79...
  
> ToddAP79              **Trying To Setup A New Home Server**
         i recently upgraded my parents computer, so i know i have their old one and would like to install ubuntu on it.

i would to be able to use the computer as a internal web server and a file server.

i would like to install
Apache
MySQL
phpMyAdmin
PHP5
Samba
WebMin

i would like to run the websites in different ip's, not sure i am going to need DNS.

any help will be nice.
thank you.     ..has!

As i mentioned I have some experience setting up Windows server, mostly Win2000SP4, but I have an AMD62x2 based computer with 2Gb of RAM and half a T-bite of HDD space, so it would be an excellent, back up server and I do a lot of web-based programming, and here I get to use a 'real' domain, mail, php, sql, etc. server. Instead of the 'local-host'-set up! I can use mail 'locally' from my Windows based system as well as Linux and Mac OS X SL(10.6), where you can use the 'local-host' and get the 'mail()' function to work....  

And I want of course to manage the server from my Mac (I have a portable mini-PC as well and a Phenom 8550 x3 based 'gaming PC' - I use dual OS on all my PC's, Ubuntu and XP or Vista64, but when I work I prefer my Mac, probably because it's a UNIX-baed system much like Linux...) and PC's.

I'm need of help to, I think I can manage it on my own but this way is faster and better, I don't need to invent the wheel again, if you catch my drift...

I am thankful for all and any help, pointers or site I can use, I really want to learn how to set up a Linux based server with the above mentioned functions and settings.

Be well!

//joys666

---

### Post by confusedstingray on 2009-10-30
Here is a good start 
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
if you are using a different release just do a search at howtoforge.com

---

