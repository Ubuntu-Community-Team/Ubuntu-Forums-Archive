---
title: "Synchrorep, a one click folders synchronization"
date: 2009-03-11
forum: Ubuntu Dev Link Forum
---

### Post by sebkfr on 2009-03-11
Hi,

I have released an english version of Synchrorep, a one click folder synchronization for ubuntu.

If you want to try it or get source, visit [http://www.iceberg.0rg.fr](http://www.iceberg.0rg.fr)

---

### Post by tezer on 2009-03-13
Thank you. It seems what I've been looking for. But is it possible to schedule it to run automatically?

---

### Post by sebkfr on 2009-03-13
My software don't have scheduling for now but you can use a cron by using the following command :
```
synchrorep --execute [full path to directory to synchronize]
```

Note that the folder must be already registered otherwise the program will showing the window to choose the alter ego folder (and a cron have not graphical interface).

You must also configure the behavior of the synchronization setting to avoid asking. In case of deletion for example, uncheck "confirm removes option" and choose to put the file to trash.

---

### Post by Vadi on 2009-03-13
Great start!

Some suggestions...

a) allow a downloadable version of the .py file, or even better, package it.

b) look at the [Gnome HIG]("http://library.gnome.org/devel/hig-book/stable/") to improve the interface

c) consider opening a project in [launchpad for translations]("https://launchpad.net/+tour/translation")

---

### Post by sebkfr on 2009-03-14
> **Vadi said:**
> Great start!

Some suggestions...

a) allow a downloadable version of the .py file, or even better, package it.

b) look at the [Gnome HIG]("http://library.gnome.org/devel/hig-book/stable/") to improve the interface

c) consider opening a project in [launchpad for translations]("https://launchpad.net/+tour/translation")

Thank you Vadi for your suggestions.

I have set a downloadable version of the source. In fact, the source is in the package : in the /usr/bin directory the synchrorep command is the source.

I will read the HIG for next improvements.

I am a newbie in launchpad and I am examining to open a project.

---

### Post by sebkfr on 2009-06-04
Hi,

I have released version 1.3 of synchrorep.

The new fonctionnalities are :
- Automatic start of synchronization when a concerned disk is mounted (If you want so)
- Gvfs is now supported for ssh, samba and ftp but not webdav because of gnome bug on this type of connection (I will implement it when the bug will be resolved)

There is 5 new string and they are not again translated in rusian, polish and spain (english and french translations are done) and all new languages are welcome. Visit launchpad if you want help.

---

### Post by Vadi on 2009-06-04
Good stuff. Add it to gnomefiles: [http://www.gnomefiles.org/devs/index.php?login](http://www.gnomefiles.org/devs/index.php?login)

---

### Post by sebkfr on 2009-06-04
> **Vadi said:**
> Good stuff. Add it to gnomefiles: [http://www.gnomefiles.org/devs/index.php?login](http://www.gnomefiles.org/devs/index.php?login)

Thanks again for advice.

I will set it on gnomefiles.

---

### Post by durand on 2009-06-04
Looks like a great program!

---

### Post by sebkfr on 2009-06-05
> **durand said:**
> Looks like a great program!

I'me happy you like it. :)

---

### Post by tesi999 on 2009-06-12
Hi. I'm new in Linux-Ubuntu and enjoying it so far. Synchrorep seems to be the program I need but .... when I right click on a folder and click on the sinchroniser option nothing happens. I think it should take me to an option to choose the folder to sync to but nothing appears. The same happens when I click on the create an icon in the desktop: the icon does not appear. 
Am I missing something? Any suggestion? 
Thanks.

---

### Post by sebkfr on 2009-06-12
> **tesi999 said:**
> Hi. I'm new in Linux-Ubuntu and enjoying it so far. Synchrorep seems to be the program I need but .... when I right click on a folder and click on the sinchroniser option nothing happens. I think it should take me to an option to choose the folder to sync to but nothing appears. The same happens when I click on the create an icon in the desktop: the icon does not appear. 
Am I missing something? Any suggestion? 
Thanks.

Can you give me the version of synchrorep you have downloaded ?

Have you restarted your session before using it ?

If you have done that, can you open a terminal, and type :
synchrorep --config

This will show you the same window that when you use the application menu.

Check the box to activate the contextual menu and click on the button to create a desktop icon and close then window.

After that can you copy the content of the terminal and post it in the forum. This will give me the informations I need to fix an eventual bug.

---

### Post by tesi999 on 2009-06-14
Hi,
The version is 1.3.3 from iceberg.org.fr

I've installed it also in my laptop and restarted after the installation, (not quite sure if I did it in my desktop), and also restarted when I clicked to activate the contextual menu. It happens the same. Nothing occurs when I click on the synchroniser option.

In the terminal when I wrote "synchrorep --config" it opened the same window that in the application menu, clicked again to activate the contextual menu but nothing changes in the terminal. 

Thanks.

---

### Post by sebkfr on 2009-06-14
Can you check the folder "/home/[user]/.nautilus/python-extensions" ?

Is there a file "synchrorep_contextual_menu.py" ?

---

### Post by tesi999 on 2009-06-14
yes: 2 files with that name. Extensions .py and the other one .pyc

---

### Post by sebkfr on 2009-06-14
I don't understand...

The .py is the program of the contextual menu and the .pyc is generated by python-nautilus. That mean that nautilus have registered it (to be quick).

Have you clicked on folder icon. I mean that the menu don't appear when you click in a window itself.

---

### Post by tesi999 on 2009-06-15
yes. Right click on the folder, click on the synchroniser option but nothing happens. What should the program do after that?

---

### Post by somewhere2go on 2009-06-15
> **tesi999 said:**
> Hi. I'm new in Linux-Ubuntu and enjoying it so far. Synchrorep seems to be the program I need but ...

Why not try [Grsync]("http://www.opbyte.it/grsync/")?

---

### Post by sebkfr on 2009-06-15
> **tesi999 said:**
> yes. Right click on the folder, click on the synchroniser option but nothing happens. What should the program do after that?

I understand, I thought the menu don't appear.

Can you type in a terminal :
synchrorep --execute [full path to your folder]

and report here the terminal result ?

---

### Post by sebkfr on 2009-06-15
> **somewhere2go said:**
> Why not try [Grsync]("http://www.opbyte.it/grsync/")?

Thanks for your support :(

---

### Post by tesi999 on 2009-06-15
usage :
synchrorep [option] [folder]
options :
   --help       : display this help text
   --execute    : Start a synchronization. The parameter "folder" must be filled
   --config     : Display setting screen

---

### Post by sebkfr on 2009-06-15
> **tesi999 said:**
> usage :
synchrorep [option] [folder]
options :
   --help       : display this help text
   --execute    : Start a synchronization. The parameter "folder" must be filled
   --config     : Display setting screen

Can you post me your command ?

If there is spaces in your path, you must quote the folder parameter.

Example : synchrorep --execute "/home/xxx/my folder"

---

### Post by tesi999 on 2009-06-15
sorry,

vaio-paco@vaio-ubuntu-laptop:~$ synchrorep --execute [/home/vaio-paco/Escritorio/11]
Warning : the user have no active X11 session
vaio-paco@vaio-ubuntu-laptop:~$ 

11 is the name of the first folder for the sincronisation
Thanks

---

### Post by tesi999 on 2009-06-15
vaio-paco@vaio-ubuntu-laptop:~$ synchrorep --execute /home/vaio-paco/Escritorio/11
Warning : the user have no active X11 session
vaio-paco@vaio-ubuntu-laptop:~$

---

### Post by sebkfr on 2009-06-15
Thank you for your patience.

I think the error come from your user have some no alphabetic numbers.

If I'me right (I can't check now because I'm at work), I will put  a new version online this night.

I will post a message as soon as the new version is online.

---

### Post by tesi999 on 2009-06-15
Thank YOU

---

### Post by sebkfr on 2009-06-15
I have prepared a new debian package for next release.

It is at the adress below :
[http://www.iceberg.0rg.fr/packages/synchrorep-1.3.4.deb](http://www.iceberg.0rg.fr/packages/synchrorep-1.3.4.deb)

I will publish it officialy tomorrow if your problems are resolved.

---

### Post by tesi999 on 2009-06-16
New version now works and does it really well. 

Thanks for your time.

---

### Post by sebkfr on 2009-06-16
The new version is now downloable from iceberg website, GnomeFiles and SourceForge will be updated in the evening.

---

### Post by KingKen on 2009-11-27
New to ubuntu and need some help.  I tried installing the programme under hardy.  Synchrorep shows up in the system tools menu but nothing happens when I click on it.  Right clicking on a folder does not bring up any options to sync. Thanks, Ken.

---

### Post by sebkfr on 2009-11-27
> **KingKen said:**
> New to ubuntu and need some help.  I tried installing the programme under hardy.  Synchrorep shows up in the system tools menu but nothing happens when I click on it.  Right clicking on a folder does not bring up any options to sync. Thanks, Ken.

Can you type in a terminal :
synchrorep --config

and copy the result in the forum

I need that to see what hapend

---

### Post by KingKen on 2009-11-30
> **sebkfr said:**
> Can you type in a terminal :
synchrorep --config

and copy the result in the forum

I need that to see what hapend

Is this what you need?

synchrorep --config
Traceback (most recent call last):
  File "/usr/bin/synchrorep", line 21, in <module>
    import gio, glib, urllib
ImportError: No module named gio

---

### Post by sebkfr on 2009-11-30
> **KingKen said:**
> Is this what you need?

synchrorep --config
Traceback (most recent call last):
  File "/usr/bin/synchrorep", line 21, in <module>
    import gio, glib, urllib
ImportError: No module named gio

Can you type in a terminal :
sudo apt-get install python-gobject

and retry ?

---

### Post by KingKen on 2009-11-30
> **sebkfr said:**
> Can you type in a terminal :
sudo apt-get install python-gobject

and retry ?

This is what I got:
sudo apt-get install python-gobject
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gobject is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic kdelibs-data liblualib50 cryptsetup libksba8
  liblua50 linux-headers-2.6.24-24 liblockfile1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by sebkfr on 2009-12-01
> **KingKen said:**
> This is what I got:
sudo apt-get install python-gobject
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gobject is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic kdelibs-data liblualib50 cryptsetup libksba8
  liblua50 linux-headers-2.6.24-24 liblockfile1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

can you see if the following files are present in your filesystem :
/var/lib/python-support/python2.5/dbus/glib.py
/var/lib/python-support/python2.5/dbus/mainloop/glib.py

---

### Post by KingKen on 2009-12-02
> **sebkfr said:**
> can you see if the following files are present in your filesystem :
/var/lib/python-support/python2.5/dbus/glib.py
/var/lib/python-support/python2.5/dbus/mainloop/glib.py

This is what I get back:

 /var/lib/python-support/python2.5/dbus/glib.py
bash: /var/lib/python-support/python2.5/dbus/glib.py: Permission denied

 /var/lib/python-support/python2.5/dbus/mainloop/glib.py
bash: /var/lib/python-support/python2.5/dbus/mainloop/glib.py: Permission denied

---

### Post by sebkfr on 2009-12-02
> **KingKen said:**
> This is what I get back:

 /var/lib/python-support/python2.5/dbus/glib.py
bash: /var/lib/python-support/python2.5/dbus/glib.py: Permission denied

 /var/lib/python-support/python2.5/dbus/mainloop/glib.py
bash: /var/lib/python-support/python2.5/dbus/mainloop/glib.py: Permission denied

I will install a new ubuntu 8.4 in my computer tomorrow (I can't today) to test if a package is missing. I will tell you what to do if I found something.

---

### Post by KingKen on 2009-12-02
> **sebkfr said:**
> I will install a new ubuntu 8.4 in my computer tomorrow (I can't today) to test if a package is missing. I will tell you what to do if I found something.

Thanks.  I appreciate the time you are taking on this.  Ken

---

### Post by sebkfr on 2009-12-03
I'm sorry but the gio library for python is not implemented in ubuntu 8.04

I will correct my site to inform users.

I'm currently working in a new version in C++ and I will try to make it work on ubuntu 8.04 but at the moment, I can't suggest other way that you upgrade your ubuntu to make my software work for you.

---

### Post by KingKen on 2009-12-04
> **sebkfr said:**
> I'm sorry but the gio library for python is not implemented in ubuntu 8.04

I will correct my site to inform users.

I'm currently working in a new version in C++ and I will try to make it work on ubuntu 8.04 but at the moment, I can't suggest other way that you upgrade your ubuntu to make my software work for you.

Thank you anyway, for the software and for trying to help me.  I will look into updating but I would prefer to stick to LTS versions if possible.  Maybe I will just wait until April next year.

---

### Post by sebkfr on 2010-02-19
Synchrorep 1.4.1 is arrived

- Porting to C/C++ improving synchronization performances
- Now detect differences to time set between local system and distant systems
- Revoke automatic synchronization on usb disk insertion

Download at [http://www.iceberg.0rg.fr//index.php?menu=synchrorep&sub=download]("http://www.iceberg.0rg.fr//index.php?menu=synchrorep&sub=download")

---

### Post by Pantcon1 on 2010-02-23
Bonjour Sebkfr, I have just installed 1.4.1 on Kubuntu 9.10  
It works okay except that the contextual 'Synchrorep' right-click is not present, probably due to this being KDE. Would it be possible to support the KDE fan-club as well as Gnome? Thanks for building this handy tool.

---

### Post by sebkfr on 2010-02-23
> **Pantcon1 said:**
> Bonjour Sebkfr, I have just installed 1.4.1 on Kubuntu 9.10  
It works okay except that the contextual 'Synchrorep' right-click is not present, probably due to this being KDE. Would it be possible to support the KDE fan-club as well as Gnome? Thanks for building this handy tool.

Hello Pantcon1,

You are not the first who ask for kde compatibility. You're the first who said it work fine, so I have made some tests on a virtual kubuntu 9.10.

In fact, it is working for local folders only which limit a lot synchrorep possibilities.

Neverless, I search a bit about kde and found how to create a contextual menu (in actions submenu). you can donwload it [here]("http://www.iceberg.0rg.fr/all_packages/launch_synchrorep.desktop").

Put this file in the folder "/usr/share/kde4/services/ServiceMenus" and it will bring the contextual menu after reboot.

I will soon make this tip online to explain how to. But I don't want to include it in a package.

This for two reasons :
- Network shares don't work for kde
- Make it fully work need a new application development, that will slow down next features

If someone want to create a "ksynchrorep" project, the open source rules allow that and I'm not against that.

---

### Post by sebkfr on 2010-03-03
A new version 1.4.2 is online :
- bug fix : synchronizations didn't start if name of synchronization folder contains quotes
- New feature : group of synchronizations management allow to start several synchronizations in one click from applications menu

---

### Post by sebkfr on 2010-03-06
A new version is online : [URL="http://www.iceberg.0rg.fr//download.php?version=1.4"]1.4.3
[/URL]- Bug fix : database get busy on multi launch
- Now possible to launch a group from contextual menu
- Now show synchronization card before first launch
- Adding lock on synchronization avoiding launching more that once in same time the same folder

---

### Post by sebkfr on 2010-03-15
A new version of synchrorep online : [1.4.4]("http://www.iceberg.0rg.fr//download.php?version=1.4")

Implementation of md5sum to improve reliability

---

### Post by sebkfr on 2010-03-22
New version of synchrorep released : [1.4.5]("http://www.iceberg.0rg.fr//download.php?version=1.4")

Add logs to trace synchronizations result

---

