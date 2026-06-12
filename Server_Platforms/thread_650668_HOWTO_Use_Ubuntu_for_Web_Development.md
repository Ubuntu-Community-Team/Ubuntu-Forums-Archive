---
title: "HOWTO: Use Ubuntu for Web Development"
date: 2007-12-26
forum: Server Platforms
---

### Post by Josh1 on 2007-12-26
This tutorial written by Joshua Taylor for JoshuaTaylor.info and for UbuntuForums.org. Feel free to link here or there, but please don’t rip this guide as I will be providing updates etc. Thanks.

How to use X/Ubuntu as a free Web Development alternative Desktop (Part 1)

I won’t be going into the details on how to install either, as there is alot of tutorials on the net, I’ve even written one myself. So get it up and running, and I will guide you on installing the tools needed to commence Web Development.

Firstly, I will be installing the following software, all of which are free to use, and most can be obtained via apt-get.
You don’t have to install everything, or you can use different editors. For example, I will be using Quanta Plus but you can use an editor such as NVU, Eclipse, Bluefish, etc.

Section 1: List of Software

Web Server:
To test out your scripts. If you do just HTML/CSS, you can probably skip this if you want.
Apache2, MySQL5, PHP5 - We will be installing these to run as a webserver, same as most Linux Web Servers use.Editor:
For editing HTML, CSS & PHP.
Bluefish (1.0.7 Stable)- A free HTML/CSS/PHP editor. You can use whatever you like though. Alternatives: NVU, Quanta Plus, Eclipse, Screem, ScITE, Kate (KDE), gPHPEdit (GNOME)

SSH & FTP
Every Web Developer who needs to upload content either uses SSH or FTP.
Filezilla - A FTP client for Linux. Alternatives: FireFTP, gFTP.
Secpanel - A GUI SSH program, similar to WinSCP for Windows.Link Checker
Checks for broken links on your site.
KLinkStatus - The only link status I know of for Ubuntu. This is a KDE application though..Image Editing
I don’t really do much Image Editing, either in Windows or Ubuntu. But you can use the following:
GIMP - Basic image editing for Linux.
GIMPShop - A heavily modified version of GIMP, made to look like Photoshop.EMail
Any Web Developer who keeps in contact with Clients, Friends, Family, Work etc, would use email.
Thunderbird - An email client developed by Mozilla.
Kontact - A KDE Email client.
Section 2: Enabling extra repositories.
To install software, we need to enable extra repostries. There is a simple tool, simple use Source-o-matic , making sure that you tick the correct box for your version of Ubuntu. Then open your terminal and type:sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck sudo gedit /etc/apt/sources.listThen replace whatever is in sources.list with the result from source-o-matic.Then type:sudo apt-get update
sudo apt-get upgrade
And it should update and upgrade all your packages.
Section 3: Installing and Configuring Software

Webserver (Apache2, MySQL5 & PHP5)

Open a terminal box, and type in:
sudo apt-get install apache2
sudo apt-get install php5
sudo /usr/sbin/apache2 -k restart
sudo chown josh /var/www
sudo apt-get install mysql-server
mysql -u root -p
sudo apt-get install php5-mysql

You can view a screencast of installing Apache2, MySQL5, PHP5 here.
Now test your webserver by visiting [http://localhost](http://localhost) and if it loads, it works!

SSH & FTP

SecPanel:
Open a terminal box, and type in:
sudo apt-get install secpanel
View Screencast for Installing Secpanel

Filezilla:
Open a terminal box, and type in:
sudo apt-get install filezilla
To open Filezilla you can either open it from the Applications Menu or type:
sudo filezilla

Editor (Bluefish)

Open a terminal box, and type in:
sudo apt-get install bluefish
To open Bluefish you can either open it from the Applications Menu or type:
sudo bluefish
View Screencast for Installing Bluefish

Image Editing (GIMP, GIMPShop)

GIMP:
Ubuntu comes with GIMP already.
If it doesn’t, simply type
sudo apt-get install gimp
Into your terminal.

GIMPShop:
GIMPShop isn’t in the Ubuntu respositries, but I have uploaded a mirror if you want to download it (Because he uses rapidshare).
Once you have downloading the file, change directory to where you downloaded it via terminal, then type:
sudo dpkg -i gimpshop_2.2.11-1_i386.deb
Or you can learn to compile GIMPShop yourself.

Editor (Bluefish)

Open a terminal box, and type in:
sudo apt-get install bluefish
To open Bluefish you can either open it from the Applications Menu or type:
sudo bluefish
View Screencast for Installing Bluefish

Site Validator (w3c-markup-validator)

Open a terminal box, and type in:
sudo apt-get install w3c-markup-validator
You can now access the Validator by visiting:
[http://localhost/w3c-markup-validator](http://localhost/w3c-markup-validator)

---

### Post by K.Mandla on 2007-12-26
Moved to Servers and Security.

---

### Post by motin on 2008-01-01
Good initiative! I have been using Ubuntu for Web Development since Dapper, and I believe I can help out with this tutorial in many ways - and I believe I am not alone. 

Seeing you are on vacation and all, I got into writing a draft on a general web development guide on the Ubuntu Wiki: [https://wiki.ubuntu.com/WebDevelopmentHowto](https://wiki.ubuntu.com/WebDevelopmentHowto)

Hopefully, we can together use our experiences to make it easier for newcomers to quickly become as productive as never before using Ubuntu.

Cheers,

Fredrik

---

