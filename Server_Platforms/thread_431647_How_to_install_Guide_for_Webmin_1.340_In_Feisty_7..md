---
title: "How to install Guide for Webmin 1.340 In Feisty 7.04 server edition"
date: 2007-05-03
forum: Server Platforms
---

### Post by Bill007 on 2007-05-03
Kia Ora All

HOW TO INSTALL WEBMIN 1.340 IN FEISTY 7.04 server edtion

Some people don't like webmin and work completely from the command line good for them.

 I find Webmin gives me an overview  of the file structure of linux which has helped me with the understanding of the command line 

Webmin is not cheating Its a tool for new users to the linux world 

This is how I installed Webmin 1.340 There are other ways but this way worked for me 

How to  installed webmin 1.340 on feisty 7.04 server edition from the command line 


```
WEBMIN VERSION 1.340

-------------------------------------------------------------------------------------------------------------

# First things first Security get this mod libnet-ssleay-perl you can then use ssl https://xxxxxxxxxx:10010
 
apt-get install libnet-ssleay-perl

#Get the latest webmin and down load it

wget http://easynews.dl.sourceforge.net/sourceforge/webadmin/webmin-1.340.tar.gz

#Then unpack it

sudo tar xzvf webmin-1.340.tar.gz


#Change into the webmin directory

cd webmin-1.340

# This will start the installation and now it will prompt for several questions answer them as follows

sudo sh setup.sh


# Config file directory [/etc/webmin]:y
#Leave as default, or change as you wish

# Log file directory [/var/webmin]:y
#Leave as default, or change as you wish

# Full path to perl (default /usr/bin/perl):
#Leave as default, or change as you wish

## I have set my port to a different one 10010 As a device 
#was all ready using that port plus good to be different

Web server port (default 10010): # I have changed my port to 10010

#This is where you can start to make webmin more secure then the standard 
#install you get with apt-get, Synaptic, or RPM. Leave as default or 
#change it to what ever port you want.

Login name (default admin):

#It is &#8216;admin&#8217;, so you can leave it as that, or put in any name that you like.

Login password:

#By creating the user above and giving it a password, 
#you have now made it so you will not need to log into webmin with root.

Password again:

enter your password again

# If you did not install &#8216;libnet-ssleay-peyrl&#8217; you will get the following message:

# &#8216;The Perl SSLeay library is not installed. SSL not available.&#8217; You can continue 
# with the install, but it would be more secure if you install sslrelay.

Use SSL (y/n):y

#Choose yes here

Start Webmin at boot time (y/n):y


#At this point it is going to configure things, install things, and create things&#8230;

#It will then tell you that you can log in to https://hostipaddress:10000 and to accept the certificate.


#Webmin User Password Change


#If you want to change root password in webmin use this included Perl script:

sudo /usr/share/webmin/changepass.pl /etc/webmin root


#if you need to uninstall
/etc/webmin/uninstall.sh



#To start Webmin if you  need to
/etc/init.d/webmin start



-------------------------------------------------------------------------------------------------------
```

Hope this helps The new webmin is really different But likable

Regards Bill007 
NZ

---

### Post by sorryd on 2007-05-17
Great guide. Worked like a charm for me.

---

### Post by ChamPro on 2007-05-21
What's wrong with using the .deb available from the Webmin site? I would prefer using it for update purposes.

I did install the .deb on a clean system (after resolving some dependencies), but it's not working. I assume I can't contact the default website because of my settings in Apache.

Do I have to change something in Apache in a clean Ubuntu Server install before Webmin will work?

---

### Post by ChamPro on 2007-05-21
This guide worked for me:
[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

I had to change the root password for Webmin. I then created a user account for my regular user and used Unix authentication. I then went back and set root to Unix Authentication as well.

Works great.

---

### Post by i-Buntu-2 on 2007-05-27
There's also another article on the Webmin website about installing on Debian based distributions (which Ubuntu is).

The top half of the page details how to install the deb package using the dpkg command and, if necessary, installing required dependencies by editing the /etc/apt/sources.list

Personally I'd prefer to use apt-get which is detailed further down - remember to edit /etc/apt/sources.list first though

The page can be found at the following location:

[http://www.webmin.com/deb.html]("http://www.webmin.com/deb.html")

Enjoy!!

---

### Post by wolfear on 2007-05-29
> **i-Buntu-2 said:**
> There's also another article on the Webmin website about installing on Debian based distributions (which Ubuntu is).

The top half of the page details how to install the deb package using the dpkg command and, if necessary, installing required dependencies by editing the /etc/apt/sources.list

Personally I'd prefer to use apt-get which is detailed further down - remember to edit /etc/apt/sources.list first though

The page can be found at the following location:

[http://www.webmin.com/deb.html]("http://www.webmin.com/deb.html")

Enjoy!!

Whoohooo!!!!
I was about ready to pull my hair out trying to "wget" from sourceforge. No idea what the prob was (other than I am probably an idiot).
I thought I had been all over the Webmin site. No idea how I missed this.
Good job!

---

### Post by varchina on 2007-06-05
Hi i used this guide to install the new webmin version 1.350 on a machine running feisty server, all is working fine for the user i setup from the setup.sh script. Now i want to setup a more limited webmin user to only edit users, but when i get round to adding a new webmin user and then setting the password (i have tried both "set to.." and "unix authentication") i then try to log in to webmin as the new user i get  "Login failed, please try again".

 I have also tried setting up a user from within ubuntu ("useradd testuser" which works fine when i locally or over ssh login to ubuntu) i then login to webmin as the working user and try the "convert unix to webmin user" select the user i have just created (testuser) and tick the box which reads "Use same password as Unix user in future" (which i assume means it will use the unix password) logout as the working user, try logging in as the unix user i have just converted, same problem "Login failed, please try again". 

Am i being stupid or just missing a step any help would be much appreciated.

---

### Post by wolfear on 2007-06-05
> **varchina said:**
> Hi i used this guide to install the new webmin version 1.350 on a machine running feisty server, all is working fine for the user i setup from the setup.sh script. Now i want to setup a more limited webmin user to only edit users, but when i get round to adding a new webmin user and then setting the password (i have tried both "set to.." and "unix authentication") i then try to log in to webmin as the new user i get  "Login failed, please try again".

 I have also tried setting up a user from within ubuntu ("useradd testuser" which works fine when i locally or over ssh login to ubuntu) i then login to webmin as the working user and try the "convert unix to webmin user" select the user i have just created (testuser) and tick the box which reads "Use same password as Unix user in future" (which i assume means it will use the unix password) logout as the working user, try logging in as the unix user i have just converted, same problem "Login failed, please try again". 

Am i being stupid or just missing a step any help would be much appreciated.

The new user probably doesn't have the right privileges to use Webmin. You will either have to give the user the right permissions or add to a group which does. Find out which groups your "main" user is a member of and add the new user to the appropriate group.
Off hand I can't remember which one it is.

Just curious...why are you using startup.sh?

---

### Post by krolben on 2007-06-20
Great guide! It worked like a charm for me!
Thank you :p

---

