---
title: "MySQL Admin crashes on successful login"
date: 2008-02-04
forum: Server Platforms
---

### Post by bluedalmatian on 2008-02-04
I have never been able to get MySQL Administrator to work on a Linux workstation - I've tried different workstations connecting to different servers and the following always happens:

Login box appears, I enter server, username & password
Click Connect, window disappears.....then nothing

Monitoring the process list I can see that MySQLAdministrator is crashing completely when I click connect but heres the intersting part...

if I enter an incorrect uername or password, it connects to the server, the server rejects it and I get a dialog saying cannot login...it only crashes if the username & password are OK and the server authenticates it.


Its not the server because I've tried connecting to several, also I can connect to those servers using MySQLAdmin on Mac OS X no problem, but the linux version just appears to be permentantly broken no matter which machine i put it on.

Is this a known issue, is there a workaround?

Thanks
Andrew

---

### Post by bluedalmatian on 2008-02-04
Just tried starting it from the terminal to see if it gave any info

WHen I start it up and the login window appears it says

(mysql-administrator-bin:6100): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Fontconfig warning: line 32: unknown element "cachedir"
Fontconfig warning: line 33: unknown element "cachedir"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 18: invalid match target "scan"

but the login window appears and it seems fine.  when i login it crashes with the following:

/home/andrew/mysql-gui-tools-5.0/mysql-administrator-bin: symbol lookup error: /usr/lib/libbonoboui-2.so.0: undefined symbol: g_type_register_static_simple

---

### Post by lobster1234 on 2008-03-12
I was able to get this to work by uninstalling what I had (I downloaded the binaries from mysql site) and re-installing via Synaptic. Search for 'mysql' and install the mysql admin, mysql query browser from the list. While you're at it, install phpMyAdmin too just in case. This procedure worked for me.

---

