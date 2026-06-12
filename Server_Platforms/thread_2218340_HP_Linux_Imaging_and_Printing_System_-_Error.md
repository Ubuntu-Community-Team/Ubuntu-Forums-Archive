---
title: "HP Linux Imaging and Printing System - Error"
date: 2014-04-20
forum: Server Platforms
---

### Post by Jordan_Hickin on 2014-04-20
Hi guys

I am trying to connect to my HP Wireless Printer on my server.

I have installed hplip and hplip-gui

and yet whenever i run

```
sudo hp-setup
```

i get this error:
```

HP Linux Imaging and Printing System (ver. 3.12.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: No display found.
error: hp-setup requires GUI support (try running with --qt3). Also, try using interactive (-i) mode.

```


And when i run 

```
sudo hp-setup -i
```

it can't find my printer... so i tried

```
sudo hp-setup 192.168.0.6
```

and get the orignal error (No Display FOund)


Please help

---

### Post by SeijiSensei on 2014-04-20
The hplip-gui package [contains]("http://packages.ubuntu.com/precise/all/hplip-gui/filelist") these executables:
```

/usr/bin/hp-fab
/usr/bin/hp-faxsetup
/usr/bin/hp-linefeedcal
/usr/bin/hp-makecopies
/usr/bin/hp-pqdiag
/usr/bin/hp-print
/usr/bin/hp-printsettings
/usr/bin/hp-sendfax
/usr/bin/hp-systray
/usr/bin/hp-toolbox
/usr/bin/hp-wificonfig

```
I'd guess hp-toolbox might be the best place to start.

---

### Post by Jordan_Hickin on 2014-04-20
hi seijisensei

Maybe my coding is bad

I run 

```
 hp-toolbox 
```

and all i got was

```

administratorjah@my-server:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 3.12.2)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: No display found.
error: hp-toolbox requires GUI support. Exiting.


```

This GUI is annoying

---

### Post by Jordan_Hickin on 2014-04-20
i just ran hp-check and it has 14 errors... neew to find out why....

---

### Post by oldfred on 2014-04-20
If you want to run hplip-gui, you need a gui. Servers do not have a gui, but many users who are not command line experts may install a gui but not the entire desktop with all the gui applications.

Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

[https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation](https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation)

Lightweight Desktop environment
Ubuntu Server + lxde
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce

---

### Post by Jordan_Hickin on 2014-04-20
apparently ubuntu server doesn't support the gui :/

[TABLE]
[TR]
[TD]**Distro**[/TD]
[TD]**Version**[/TD]
[TD]**Installer**[/TD]
[TD]**GUI[[SUP]14[/SUP]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6600.html#note14")**[/TD]
[TD]**Scan[[SUP]3[/SUP]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6600.html#note3")**[/TD]
[TD]**Fax[[SUP]5[/SUP]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6600.html#note5")**[/TD]
[TD]**Status**[/TD]
[TD]**Photo Card[[SUP]4[/SUP]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6600.html#note4")**[/TD]
[TD]**USB**[/TD]
[TD]**Parallel**[/TD]
[TD]**Network[[SUP]1[/SUP]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6600.html#note1")**[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]11.10[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]12.04[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]12.10[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]13.04[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]13.10[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
 [TR]
[TD]Ubuntu[/TD]
[TD]14.04[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[TD]No[/TD]
[TD]Yes[/TD]
[/TR]
[/TABLE]

---

### Post by Jordan_Hickin on 2014-04-20
No i got nothing... i have gone back to the system before i even started trying to connect to the printer... do you know of any suitable tutorials (Or could you help me) set up the connection to my printer.. Lets say i have nothing installed that i need yet.

---

### Post by SeijiSensei on 2014-04-20
On the server, edit as root with sudo the file /etc/cups/cupsd.conf and replace the line
```
Listen localhost:631
```
with
```
Listen 631
```
then restart cups with "sudo service cups restart".

Now try opening [http://ip.of.your.server:631/](http://ip.of.your.server:631/) from another machine on the network with a browser.  You'll see the web-based CUPS administrator.  Choose "Adding Printers and Classes" then press the "Add Printer" button. You'll be walked through the process.

If you are concerned about security, or your server is visible on the public Internet, you should restore the "localhost" entry after you are done and restart CUPS once again.

---

### Post by Jordan_Hickin on 2014-04-20
it keeps asking for a username and password?

---

### Post by SeijiSensei on 2014-04-20
Use your own credentials just like you would if you ran a process with "sudo" at the command prompt.

---

### Post by Jordan_Hickin on 2014-04-20
i just ran [http://192.168.0.7:631](http://192.168.0.7:631) and got the FORBIDDEN page... and i did change the listen line to listen 631

---

### Post by Jordan_Hickin on 2014-04-20
I shoudl point out my printer is an all in one. I want to be able to tell the server (When all this is done) to scan all pages in the scanner and save them onto its serve folfer (The folder is already setup and i can use it from a remote desktop :)

---

### Post by SeijiSensei on 2014-04-20
> **Jordan_Hickin said:**
> i just ran [http://192.168.0.7:631](http://192.168.0.7:631) and got the FORBIDDEN page... and i did change the listen line to listen 631

And restarted CUPS with "sudo service cups restart"?  And entered your own username and password when prompted?  You're the user with sudo privileges on the box, yes?

---

### Post by Jordan_Hickin on 2014-04-20
Yes i am... i ran the restart.. but when i enter [https://192.168.0.7:631/](https://192.168.0.7:631/) it doesnt ask for details just says forbidden.

I have no chence to log in :/

I just tried scanning for the printer on command line via hp-probe... it didn't find it yet when i ran an nmap -sP it can locate the printer... and hp-makeuri can find it as well... bu all other hp commands don't know it :/

---

### Post by SeijiSensei on 2014-04-20
On systems that don't use sudo, like RedHat flavors of Linux, I've logged in as the root user with root's password.  If you know [how to add a password for root]("https://help.ubuntu.com/community/RootSudo"), you can give that a try.

---

### Post by Jordan_Hickin on 2014-04-20
I thought that the sudo was giving me root access...

---

### Post by Jordan_Hickin on 2014-04-20
im lost now... completely confused... all i want is the stupid printer installed onto the server. Why is it so difficult :/ maybe i should just reinstall the server.. give it a clean look

---

### Post by SeijiSensei on 2014-04-20
> **Jordan_Hickin said:**
> I thought that the sudo was giving me root access...

Yes, it should.  I'm just trying to suggest alternatives since that didn't work for you.

As I said, I prefer CentOS to Ubuntu on servers, so I'm reaching the end of things to suggest here.  I like Ubuntu as a desktop operating system, but it's not my first choice for servers.

---

