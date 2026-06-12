---
title: "Webmin 1.340 doesn't work under Feisty Fawn?"
date: 2007-04-12
forum: Server Platforms
---

### Post by hamdodger on 2007-04-12
I have tried installing the latest version of Webmin on Fawn Beta Server 7.04, and it appears that a number of functions now are broken.  Can anyone else confirm this?

I have been able to install webmin 1.340 under Edgy 6.10 server and it works fine.

---

### Post by truptrup on 2007-04-16
I have noticed this as welll just installed it today by deb package. might try it with tar and see if that works. Anybody had luck with this?

---

### Post by Gladden on 2007-04-16
I tried Webmin ver 1.340 as well.  Did not even come up.  I backed it up a little to version 1.320.  Seems to be fine.

---

### Post by truptrup on 2007-04-20
> **Gladden said:**
> I tried Webmin ver 1.340 as well.  Did not even come up.  I backed it up a little to version 1.320.  Seems to be fine.

This is working perfectly for me too. 1.340 did not have all the features enabled like samba and mysql but 1.320 seems to have everything.

---

### Post by hise0001 on 2007-04-22
Hi,

I'm running into the same thing with Edgy Server.  I'm new to the server edition and to the command line only environment so I hope I'm doing everything right....

1- Fresh install

2- edit /etc/apt/sources.list and uncomment the universe and multiverse servers

3- apt-get update

4- sudo mount /dev/cdrom /media/cdrom

5- sudo dpkg -i /media/cdrom/webmin<whatever> (I can't remember the exact filename)

It fails to install one of webmin's dependencies.


I couldn't find 1.32 on the webmin site.

Any input would be greatly appreciated.

Thanks,

--Hise

---

### Post by imon9 on 2007-04-22
in my machine with Feisty, webmin 1.340 work just fine

---

### Post by hise0001 on 2007-04-23
> in my machine with Feisty, webmin 1.340 work just fine

Are you running the server edition?  Webmin 1.34 runs fine on my fiesty desktop it just wont install on my edgy server edition.

Or.. maybe you've installed a desktop on the server edition?    I installed xubuntu-desktop on the server edition and webmin 1.34 installed fine... but, I don't want all the overhead of the desktop running on my server.


> I tried Webmin ver 1.340 as well. Did not even come up. I backed it up a little to version 1.320. Seems to be fine.

Anybody, know where I can get 1.320?  I can seem to find it on the webmin site.

Thanks,
--Hise

---

### Post by imon9 on 2007-04-23
yah, i am using fiesty desktop, not server edition (but i have LAMP/apapche php mysql install anyway...if ever that matters)

so sorry i couldnt be of any help

---

### Post by ruibernardo on 2007-04-25
Hi, 

my webmin also seemed to be broken, but in it wasn't. Check if you have javascript enabled in your browser or some javascript blocker plugin blocking your webmin.

Hope it helps

---

### Post by jiminycricket on 2007-04-27
> **hise0001 said:**
> 

Anybody, know where I can get 1.320?  I can seem to find it on the webmin site.

Thanks,
--Hise

Hi,
Webmin has all their releases listed on sourceforge: [http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391](http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391)  

Direct link to 1.320 deb:  [http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.320_all.deb&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.320_all.deb&use_mirror=internap)

---

### Post by black_ice on 2007-04-29
i have tried to install .deb packages but it refuse to continue the installation but i tried the tar package it done . 

but  i had an error with the authentication it deny to enter with the root and the root password  it deny me 


i changed my password with changepass.pl but it didnot work also it seems to be some thing like abug ?!

---

### Post by Bill007 on 2007-05-03
Kia Ora 

Sorry Guys I just installed webmin 1.340 on feisty server edition from the command line 
#absolutely flawless install

Here is how Ive done it

```
WEBMIN VERSION 1.340

-------------------------------------------------------------------------------------------------------------
## Download &#8216;webmin-1.340.tar.gz&#8217; (at the time of writing) to some location in your machine 

# get the 

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

## I have set my port to a different one 10010 As a divce 
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

Hope this helps you guys and anyone else The new webmin is really different But likable

Regards Bill

---

### Post by willough on 2007-05-03
I followed the instructions provided by Bill007 and the installation of Webmin 1.340 came off without a hitch.  Thanks.

---

### Post by hbchrist on 2007-05-05
I concur. Bill007's directio worked flawlessly for Ubuntu Server 7.04. 

Excellent job, and my thanks!!

---

### Post by Knightwise on 2007-05-06
I wrote up a little article about installing feisty for the family (using webmin) , it might be of help. 

[http://www.knightwise.com/content/blogsection/4/9/](http://www.knightwise.com/content/blogsection/4/9/)

greeyz

knightwise.

---

### Post by VorDesigns on 2007-05-30
> **Knightwise said:**
> I wrote up a little article about installing feisty for the family (using webmin) , it might be of help. 

[http://www.knightwise.com/content/blogsection/4/9/](http://www.knightwise.com/content/blogsection/4/9/)

greeyz

knightwise.

Thanks, I used your blog and it worked although, I went ahead and installed the dependencies post which, finished the webadmin install without prompting.  I reran the install anyway.
```
 sudo apt-get install libnet-ssleay-perl libauthen-pam-perl libio-pty-perl libmd5-perl
```

Did need to reboot but that may be a server issue or may a force reload of apache2 would have done it.

Anyway, thanks.

---

