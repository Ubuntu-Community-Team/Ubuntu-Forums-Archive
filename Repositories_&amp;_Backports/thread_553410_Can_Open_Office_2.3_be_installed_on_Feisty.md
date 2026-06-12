---
title: "Can Open Office 2.3 be installed on Feisty?"
date: 2007-09-17
forum: Repositories &amp; Backports
---

### Post by exploder on 2007-09-17
Is there a repo with OpenOffice 2.3 for Feisty? OO 2.3 final has been released and I understand it is more compatible with MS Office.

---

### Post by Mud.Knee.Havoc on 2007-09-17
I haven't tried it, but there's a .deb listed on the openoffice.org site.

---

### Post by Seisen on 2007-09-18
As of right now it will be available in Gutsy when it is released in October. You have two  options then wait till October or download the .deb file from the OpenOffice.org website.

---

### Post by exploder on 2007-09-18
I have the .deb's, just need some instruction on how to properly install them.

---

### Post by mitch00 on 2007-09-18
exploder, once you extracted all the debs to a folder (should be called something like DEBS), open up a terminal and type "sudo dpkg -i *.deb" without quotes of course. This will install it all for you. It install to /opt/openoffice.org2.3 so you may want to update your launcher icons. Don't forget to remove the old OO.o through synaptic or something.

---

### Post by exploder on 2007-09-18
Thanks mitch00! I will give it a try when I get home from work tomorrow

Thanks for the help!

---

### Post by xxd on 2007-09-18
See here:

[http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

---

### Post by Plutonium on 2007-09-18
Hi there,

MitchOO !!!  Thx for the instructions !!

In fact OpenOffice has made the translation to .deb and .rpm 

Once the package is exploded you go to the DEB directry in the exploded package or whatever applies for .rpm, then with

sudo dpkg -i *.ext 

you can properly install the package

To put icons in your system menu is quite simple: 
Go to: Sysyem-->Preferences-->MainMenu---> Office  and then right-click mouse and choose: 'Install New Item'. A new window will pop-up and by browsing to: /opt/openoffice.org2.3/program...  you can choose any of the application options, these are the s*** ones. Repeat the operation to add manually add each one of the different components of the OpenOffice platform.

Once done it, one by one they will appear in: Applications-->Office menu

Initially no icon is set... to me it is irrelevant, but also you can browse and fin them (I didn't check where are they; however may be someone else can check where to find these icons and add the instruction for these who want the distinctive icons).

I tested the OpenOffice2.3 using old files generated in OfficeXP and later worked out with OO2.1** ... they look great.. in fact at first sight I manage to catch several improvements. The interface, for my taste is friendlier, although I noticed that the uploading of the document is slower than previous versions... 

I hope this info is of any help for the Community

Plutonioum... ;o)

---

### Post by grantk86 on 2007-09-19
There is also another folder in .../DEBS/ which is called desktop-integration.  Inside you will find a self installer that will take care of putting all the icons in the main menu.

---

### Post by exploder on 2007-09-19
mitch00, the instructions worked perfectly! 

grantk86, your instructions put the icons in the menu!

Plutonium, your testing information was nice to see too!

Thanks everyone! This install went great! Now I should have less problems with MS documents. Thanks very much!

---

### Post by wersdaluv on 2007-09-19
> **exploder said:**
> mitch00, the instructions worked perfectly! 

grantk86, your instructions put the icons in the menu!

Plutonium, your testing information was nice to see too!

Thanks everyone! This install went great! Now I should have less problems with MS documents. Thanks very much!

I am using KDE. After following mitch00's instructions, it seems that I successfully installed oo.o 2.3 but I can't run it. Whenever I run it from KMenu, it does not come out. If I run it from the terminal...
```
:~$ oowriter
The program 'oowriter' is currently not installed.  You can install it by typing:
sudo apt-get install openoffice.org-writer
bash: oowriter: command not found

```

---

### Post by IanW on 2007-09-20
> **wersdaluv said:**
> I am using KDE. After following mitch00's instructions, it seems that I successfully installed oo.o 2.3 but I can't run it. Whenever I run it from KMenu, it does not come out. If I run it from the terminal...
```
:~$ oowriter
The program 'oowriter' is currently not installed.  You can install it by typing:
sudo apt-get install openoffice.org-writer
bash: oowriter: command not found

```

I have it running fine under Gnome-flavoured Ubuntu. The menu entry seems to issue the following command for OOWriter:-
 ```
openoffice.org2.3 -writer
```

Perusing the entries for the other OpenOffice elements shows that you now have to issue "openoffice.org2.3" with a suitable switch for the element you want to use ("-writer", "-impress", etc)

Hopefully, your KMenu entries can be suitably modified to reflect this?

---

### Post by Sayers on 2007-09-20
if you have a few hours you could compile it, and what is in 2.3 if you dont mind me asking?

---

### Post by lincolnlad on 2007-09-21
OO 2.3 runs fine on my Feisty but I initially had a bunch of dependency issues when trying to install over v2.2.  I uninstalled v2.2 and the installation of all the official debs went well.

---

### Post by Seisen on 2007-09-21
> **Sayers said:**
> if you have a few hours you could compile it, and what is in 2.3 if you dont mind me asking?

Here is link to all the new features.

[http://wiki.services.openoffice.org/wiki/New_Features_2.3]("http://wiki.services.openoffice.org/wiki/New_Features_2.3")

---

### Post by logoodnix on 2007-09-25
> **grantk86 said:**
> There is also another folder in .../DEBS/ which is called desktop-integration.  Inside you will find a self installer that will take care of putting all the icons in the main menu.

I used this method to install but I get no Icons. 
 System > preferences > main menus > :confused:office...gives me no options to check.

---

### Post by exploder on 2007-09-25
There is also another folder in .../DEBS/ which is called desktop-integration. Inside you will find a self installer that will take care of putting all the icons in the main menu.

grantk86, posted the solution above. That is how I got my menu icons.

---

### Post by Mamsaac on 2007-09-26
I prefer not to create a new topic, since it's very related: 

do language versions that differ from english take longer to be released?

---

### Post by ptn107 on 2007-09-29
If you would rather use the Ubuntu provided packages you can do it by temporarily changing your software repositories from feisty to gutsy, upgrading openoffice, and then changing your repositories back.  You can just copy and paste commands in a terminal if you wish...

1) Back up your current sources:
sudo cp /etc/apt/sources.list /etc/apt/sources.backup

2) Change repositories [Feisty Fawn 7.04 to Gutsy Gibbon 7.10 beta]:
sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list

3) Update package list and upgrade OpenOffice.org:
sudo apt-get update && sudo apt-get install openoffice.org -y

4) Change repositories back to Feisty Fawn and reload packages:
sudo cp /etc/apt/sources.backup /etc/apt/sources.list && sudo apt-get update

This way may be easier for you.  I felt safer doing it this way using Ubuntu's packages than installing the stock .rpm's from the website.  It also makes future upgrades easier.

---

### Post by gsoundsgood on 2007-10-05
i tried to make it the way ptn107 suggests out of curiosity...(use gutsy repositories)
well, it did install openoffice.org 2.3, which is good, but basically broke Gnome (nautilus closes and starts up again by itself, X restarts, and the likes...).
no big deal, i switched to kde, and everything works fine... i'll just have to downgrade, or wait a couple of weeks to dist-upgrade to gutsy...

to install openoffice 2.3, if you don't want to wait, just uninstall openoffice.org, and then install the deb files from the official website, it's much safer.

g.

---

### Post by gsoundsgood on 2007-10-05
i'm answering to my own post. 

updating with 

sudo apt-get update && sudo apt-get install openoffice.org -y

didn't work correctly, because it couldn't find updated automatix repositories. so after the update i just did 

sudo apt-get install openoffice.org -y

which of course installed also all suggested packages.

my mistake.

---

### Post by sylecn on 2007-10-05
I will wait for some time when simply Feisty asks me to update openoffice.:) Hope it won't be long from now.

---

### Post by rahimveron on 2007-10-06
> **exploder said:**
> There is also another folder in .../DEBS/ which is called desktop-integration. Inside you will find a self installer that will take care of putting all the icons in the main menu.

grantk86, posted the solution above. That is how I got my menu icons.

I downloaded the deb package but it does not have a folder desktop-integration.
However it has a deb for kde integration.
Can somene send me the gnome integration deb plz. or give me a solution for menu entries. I dont want to download another 120 mb rpm package

---

