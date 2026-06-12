---
title: "how to autostart Coldfusion 9 ?"
date: 2010-02-11
forum: Server Platforms
---

### Post by whitetimer on 2010-02-11
Hi All

I have coldfusion installed on a guest ubuntu server in virtualbox, it is configured with apache2 & everything works great.

But how do i get Coldfusion to autostart when i boot up the guest ubuntuserver ?

Many thanks ;)

---

### Post by joberly on 2010-02-11
You can use the VBoxManage CLI.

Terminal: VBoxMange startvm "coldfusion"

Where the quotes contain the same name you see in the GUI list of VBox. Or use the UUID without quotes.

You can create a script that runs that code when the machine boots, and put it in rc.local for example.

---

### Post by whitetimer on 2010-02-11
> **joberly said:**
> You can use the VBoxManage CLI.

Terminal: VBoxMange startvm "coldfusion"

Where the quotes contain the same name you see in the GUI list of VBox. Or use the UUID without quotes.

You can create a script that runs that code when the machine boots, and put it in rc.local for example.

Hi ... Thanks for that, not sure i understand as still quite new to Linux/Ubuntu and this is my first few days of using Virtualbox etc 

Many thanks

---

### Post by joberly on 2010-02-11
Ok, for starters, open up a terminal and type:

VBoxManage list -l vms

That will list all of your Virtual Machines you have setup along with all settings you have for them. 

Assuming they are setup and working (which you say they are) you only need to be concerned with the Name or UUID fields.

When you want to RUN a virtual machine, you can type from the command line:

VBoxMange startvm "name of virtual machine"

or

VBoxMange startvm UUID.

---

### Post by whitetimer on 2010-02-11
> **joberly said:**
> Ok, for starters, open up a terminal and type:

VBoxManage list -l vms

That will list all of your Virtual Machines you have setup along with all settings you have for them. 

Assuming they are setup and working (which you say they are) you only need to be concerned with the Name or UUID fields.

When you want to RUN a virtual machine, you can type from the command line:

VBoxMange startvm "name of virtual machine"

or

VBoxMange startvm UUID.

Hi Thanks for that explanation, but i think you may have misunderstood what i want to do.  I have ubuntuserver installed as a guest on virtualbox.  I have lamp etc setup on the server and i have just installed coldfusion 9 and configured it with apache2.  That all works great.  When i boot up the ubuntuserver, coldfusion does not automatically start, but apache2, tomcat, mysql do.  So i wanted to set coldfusion to autoboot when apache etc boots

Many thanks

---

### Post by joberly on 2010-02-11
Gotcha! Does coldfusion have a startup script already?

ls /etc/init.d

If not, you should edit /etc/rc.local and add the command you use to run coldfusion.

sudo nano /etc/rc.local

add the command before exit 0

ctrl + o to save
ctrl + x to exit

reboot.

---

### Post by whitetimer on 2010-02-11
> **joberly said:**
> Gotcha! Does coldfusion have a startup script already?

ls /etc/init.d

If not, you should edit /etc/rc.local and add the command you use to run coldfusion.

sudo nano /etc/rc.local

add the command before exit 0

ctrl + o to save
ctrl + x to exit

reboot.

Thats great, many thanks, will try in the morning :D

---

### Post by whitetimer on 2010-02-12
> **whitetimer said:**
> Thats great, many thanks, will try in the morning :D


I just tried what was suggested and that does not work on my system.  Any thoughts ?
:popcorn:

---

### Post by rivey on 2010-10-27
I created a script for auto startup and shutdown of coldfusion in init.d.  

/etc/init.d/coldfusion

> 
#! /bin/sh

case "$1" in
  start)
        echo "Starting ColdFusion9" >&2
        /opt/coldfusion9/bin/coldfusion start
        exit 3
        ;;
  restart)
        echo "Restarting ColdFusion9" >&2
        /opt/coldfusion9/bin/coldfusion restart
        exit 3
        ;;
  stop)
        echo "Stopping ColdFusion9" >&2
        /opt/coldfusion9/bin/coldfusion stop
        exit 3
        ;;
  *)
        echo "Usage: $0 start|stop|restart" >&2
        exit 3
        ;;
esac

:


Its not much, but it gets the job done.  After creating that file, run:

> sudo update-rc.d coldfusion defaults

Bounce the box, should now autostart and autostop for you.  Enjoy!

rivey
blog.robertivey.org

---

