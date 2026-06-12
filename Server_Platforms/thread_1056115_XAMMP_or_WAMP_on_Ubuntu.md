---
title: "XAMMP or WAMP on Ubuntu?"
date: 2009-01-31
forum: Server Platforms
---

### Post by Ahren75 on 2009-01-31
Hi, I'm new to Ubuntu - just switched from Windows.

Is there an equivalent of WAMP or XAMPP for Ubuntu Hardy Heron?

And where and how do I go about installing it?

I hope I'm posting in the right forum.


Thanks much

---

### Post by Iowan on 2009-01-31
XAMPP exists, LAMP would be Linux version of WAMP. Server install disk should offer it as option.  **tasksel** should let you install it after-the-fact.

---

### Post by Ahren75 on 2009-01-31
Thanks but where do I go to get it - wampp or lamp ?

And how do I install it?

I don't see them in the remove/add applications funtion or the synaptic package manager.

---

### Post by Rinzwind on 2009-01-31
> **Ahren75 said:**
> Thanks but where do I go to get it - wampp or lamp ?

And how do I install it?

I don't see them in the remove/add applications funtion or the synaptic package manager.

sudo apt-get install tasksel

this will install tasksel and if you start it it will show a menu with a lot of options including a LAMP install.

Or you can do it all yourself with a tutorial like this:
[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

---

### Post by Ahren75 on 2009-01-31
great thanks!

---

### Post by Ahren75 on 2009-01-31
I've run into a little problem...

the latest version of Tasksel is apparently already installed...but I don't know where to go to open it - it's nowhere to be found in the Applications Tab and drop-down categories...

---

### Post by unixeducation on 2009-01-31
> **Ahren75 said:**
> I've run into a little problem...

the latest version of Tasksel is apparently already installed...but I don't know where to go to open it - it's nowhere to be found in the Applications Tab and drop-down categories...
Start a terminal by clicking "Applications -> Accessories -> Terminal". In the terminal window, type "synaptic" to start the package selector. This will give you the text-based version of the application found in "System -> Administration -> Synaptic Package Manager", which is equivalent to launching tasksel.

---

### Post by RuleMaker on 2009-01-31
> **Ahren75 said:**
> I've run into a little problem...

the latest version of Tasksel is apparently already installed...but I don't know where to go to open it - it's nowhere to be found in the Applications Tab and drop-down categories...

Just type in terminal:
```
sudo tasksel
```

---

### Post by drubin on 2009-01-31
> **Iowan said:**
> XAMPP exists, LAMP would be Linux version of WAMP. Server install disk should offer it as option.  **tasksel** should let you install it after-the-fact.

This is not the same as a lamp server.

XAMPP is a pre bundled application that has mysql, apache... and other things all bundled into one "package" (by windows terms) 

I would suggest using the tasksel command to install php mysql apache but just know this is not XAMPP but rather LAMP (Linux Apache Mysql Php) :)

---

### Post by Ahren75 on 2009-01-31
okay

I type **sudo tasksel** in terminal

a little blue window came up -- I selected LAMP, then pressed ENTER

and nothing happens. it just takes me back to the terminal prompt.

How do I know if it's been installed?

---

### Post by drubin on 2009-01-31
> **Ahren75 said:**
> 
How do I know if it's been installed?

On the command line type 
```
php -version

```

---

### Post by Ahren75 on 2009-01-31
> **drubin said:**
> This is not the same as a lamp server.

XAMPP is a pre bundled application that has mysql, apache... and other things all bundled into one "package" (by windows terms) 

I would suggest using the tasksel command to install php mysql apache but just know this is not XAMPP but rather LAMP (Linux Apache Mysql Php) :)


good to know. thanks!

---

### Post by Ahren75 on 2009-01-31
> **drubin said:**
> On the command line type 
```
php -version

```

I get this :
ahren@xxxxx:~$ php - version
The program 'php' is currently not installed.  You can install it by typing:
sudo apt-get install php5-cli
bash: php: command not found
ahren@xxxxx:~$

---

### Post by Ahren75 on 2009-01-31
I tried installing LAMP again and got this

ahren@xxxxx:~$ tasksel
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied
tasksel: debconf failed to run

ahren@xxxxx:~$

---

### Post by drubin on 2009-01-31
> **Ahren75 said:**
> I tried installing LAMP again and got this

ahren@xxxxx:~$ tasksel
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied
tasksel: debconf failed to run

ahren@xxxxx:~$

I type in terminal ```
**sudo** tasksel 
```
You forgot the sudo

---

### Post by Ahren75 on 2009-01-31
> **drubin said:**
> I type in terminal ```
**sudo** tasksel 
```
You forgot the sudo

Okay I sudo tasksel and get the window in blue below . I select LAMP and enter and nothing happens. It just takes me back to the command line in terminal.

Package configuration

    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Software selection &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; You can choose to install one or more of the following predefined   &#9474; 
    &#9474; collections of software.                                            &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474; Choose software to install:                                         &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;    [ ] DNS server                                               &#8593;   &#9474; 
    &#9474;    [ ] Edubuntu server                                          &#9646;   &#9474; 
    &#9474;    [ ] LAMP server                                              &#9618;   &#9474; 
    &#9474;    [ ] Mail server                                              &#9618;   &#9474; 
    &#9474;    [ ] OpenSSH server                                           &#9618;   &#9474; 
    &#9474;    [ ] PostgreSQL database                                      &#9618;   &#9474; 
    &#9474;    [*] Print server                                             &#9618;   &#9474; 
    &#9474;    [ ] Samba File server                                        &#9618;   &#9474; 
    &#9474;    [ ] 2D/3D creation and editing suite                         &#8595;   &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;                               <Ok>                                  &#9474; 
    &#9474;                                                                     &#9474; 
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Ahren75 on 2009-01-31
getting way late here for me on the other side of the globe...maybe I'll be more clearheaded tomorrow after a good night's sleep...

thanks you guys

---

### Post by Iowan on 2009-01-31
> **drubin said:**
> This is not the same as a lamp server.
 I hope I didn't suggest that XAMPP is the same as LAMP *or* WAMP.  WAMP is Windows, Apache, MySQL and PHP - LAMP is the Linux version (as mentioned).  XAMPP is supposed to be cross-platform, but I've seen warnings about stability... but I've also seen How-To's for XAMPP on Ubuntu.

---

### Post by drubin on 2009-02-01
> **Iowan said:**
> I hope I didn't suggest that XAMPP is the same as LAMP *or* WAMP.  WAMP is Windows, Apache, MySQL and PHP - LAMP is the Linux version (as mentioned).  XAMPP is supposed to be cross-platform, but I've seen warnings about stability... but I've also seen How-To's for XAMPP on Ubuntu.

XAMPP is not a cross platform version of LAMP. it is just a pre-packaged version of all the above products into one downloaded app. Now this is great for windows since windows doesn't have package management but on linux it is *very* easy to install all the above with a single command.

XAMPP is ***not*** i repeat not designed for production servers!!! this is very important. It has security issues in its design. it was intentioned to make an easy platform for testing/development. (I assume mainly for windows) but since php/phpmyadmin/mysql/apache are cross platform the wrapper of xampp was trivial to port over.

---

### Post by kiswa on 2009-02-01
> **Ahren75 said:**
> Okay I sudo tasksel and get the window in blue below . I select LAMP and enter and nothing happens. It just takes me back to the command line in terminal.

Package configuration

    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Software selection &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; You can choose to install one or more of the following predefined   &#9474; 
    &#9474; collections of software.                                            &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474; Choose software to install:                                         &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;    [ ] DNS server                                               &#8593;   &#9474; 
    &#9474;    [ ] Edubuntu server                                          &#9646;   &#9474; 
    &#9474;    [ ] LAMP server                                              &#9618;   &#9474; 
    &#9474;    [ ] Mail server                                              &#9618;   &#9474; 
    &#9474;    [ ] OpenSSH server                                           &#9618;   &#9474; 
    &#9474;    [ ] PostgreSQL database                                      &#9618;   &#9474; 
    &#9474;    [*] Print server                                             &#9618;   &#9474; 
    &#9474;    [ ] Samba File server                                        &#9618;   &#9474; 
    &#9474;    [ ] 2D/3D creation and editing suite                         &#8595;   &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;                                                                     &#9474; 
    &#9474;                               <Ok>                                  &#9474; 
    &#9474;                                                                     &#9474; 
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

Just to make sure... when you have LAMP highlighted, hit spacebar to get a * in the box, then hit enter.

If you're already doing that, never mind.

---

### Post by Ahren75 on 2009-02-02
> **kiswa said:**
> Just to make sure... when you have LAMP highlighted, hit spacebar to get a * in the box, then hit enter.

If you're already doing that, never mind.

Thanks kiswa! that did it! That was all I needed to do.

---

### Post by Ahren75 on 2009-02-02
> **Ahren75 said:**
> Thanks kiswa! that did it! That was all I needed to do.

Only now - this thing has turned into a real NIGHTMARE!

After the install process ran, I went to look for LAMP in the applications TAB (am still in Windows mindset). I didn't find it. 

So I figured I must not have done it right. I returned to sudo tasksel and repeated the process. Highlight LAMP hit space and enter. The "install" process began or so I thought. And as I watch the thing run to my HORROR I realized that it was in the process of UNINSTALLING EVERYTHIING! and I mean EVERYTHING the other programs too that has nothing to do with LAMP. Unlike Windows there are no pop-up warnings to say - are you sure you want to do this?!!! Unlike windows there are no button option to interrupt and undo or cancel the process. The thing just kept on running, uninstalling everything...looked like it would take a long time...I panicked and closed the window. By then it was too late. Half the applications were missing, functions weren't working. I shut down the computer and tried to start in RECOVERY MODE - that doesn't work. Looks like I just killed Ubuntu with all my important files in it.

PLEASE tell me I have NOT lost all my files in there and that it is recoverable.

ANYBODY - HELP?

---

### Post by kimeunice on 2011-11-24
(gedit:3918): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
itcenter@itcenter-System-Product-Name:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


help this is the error that always popping up..

can anyone help me with this?
please[-o<

---

