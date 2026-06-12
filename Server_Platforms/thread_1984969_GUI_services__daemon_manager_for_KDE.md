---
title: "GUI services / daemon manager for KDE?"
date: 2012-05-22
forum: Server Platforms
---

### Post by Javik on 2012-05-22
Is there a GUI equivalent to Microsoft's Services management console for KDE/Gnome?

I hate having to drop to a command line to do anything "serious" with unix, like stop and start system daemons. The status of daemons along with start/stop and enable/disable options should be readily visible directly in the GUI somewhere, but I don't see it in the LTS GUI.

---

### Post by SeijiSensei on 2012-05-23
You really find it faster to launch a GUI application, find the service in the list and manage it that way than opening a Terminal and typing "sudo service servicename restart"?  I always have a shell window open so it's not that big a deal for me.

I believe you can manage things like this with webmin, though I've never used it with Ubuntu, only RedHat-flavored machines like CentOS.  Still in the time it would take to open a browser, point to port 10000 on the local machine, log in, then find the service manager, I'd be all done using the command prompt.

---

### Post by Javik on 2012-05-24
Service / daemon names and control methods fall into the territory of "infrequently used random details I should not need to have to remember".

It's the same issue as trying to remember which of the 300 versions of unix this is and what particular way I need to be formatting my typed commands for this one. 

Some people love all memorizing all the randomly designed unix command line "short weird name so less characters to type" syntax complexity. Meanwhile, I just want to do a few mouse clicks, and get back to doing something else that's actually important.

No, I don't use or want to learn how to use vi. Yes, I use gedit as root to edit config files. :)

I thought this was supposed to be the user-friendly version of linux. :confused:

---

### Post by haqking on 2012-05-24
> **Javik said:**
> Service / daemon names and control methods fall into the territory of "infrequently used random details I should not need to have to remember".

It's the same issue as trying to remember which of the 300 versions of unix this is and what particular way I need to be formatting my typed commands for this one. 

Some people love all memorizing all the randomly designed unix command line "short weird name so less characters to type" syntax complexity. Meanwhile, I just want to do a few mouse clicks, and get back to doing something else that's actually important.

No, I don't use or want to learn how to use vi. Yes, I use gedit as root to edit config files. :)

I thought this was supposed to be the user-friendly version of linux. :confused:

Its not any of the 300 versions of Unix, it is Linux.

And in KDE, go to system settings, startup/shutdown and choose service manager, or task manager itself thats about as close as you are going to get unless you decide to Learn the OS you choose to use, if not Windows will welcome you back ;-)

Peace

---

### Post by SeijiSensei on 2012-05-25
Well, in defense of the OP, the KDE Service Manager doesn't control startup services that run after boot.  It only controls user-level services within the KDE environment.

OP, the list of service names can be found by listing the directory /etc/init.d.  The Apache server, for instance, is invoked by the apache2 script in that directory.  I'd say there are about a dozen services that I ever run on a routine basis, so it's not too hard to remember their names.

---

### Post by haqking on 2012-05-25
> **SeijiSensei said:**
> Well, in defense of the OP, the KDE Service Manager doesn't control startup services that run after boot.  It only controls user-level services within the KDE environment.

OP, the list of service names can be found by listing the directory /etc/init.d.  The Apache server, for instance, is invoked by the apache2 script in that directory.  I'd say there are about a dozen services that I ever run on a routine basis, so it's not too hard to remember their names.

I agree, which is why i said "as close as you are going to get" as it is not exactly what was asked for.

Peace

---

