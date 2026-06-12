---
title: "start application as root in Ubuntu Lucid SERVER version"
date: 2011-11-13
forum: Server Platforms
---

### Post by furia on 2011-11-13
I'm running a Ubuntu Lucid 10.04 SERVER version - 64-bit.
 
I have an application (MyApp) which needs to be started as root, and it does fine while launching it via a console using sudo : sudo /usr/local/sbin/MyApp
 
In order to autmatically start it at boot, I tried via upstart script, so this is my MyApp.conf in /etc/init folder: 
 
 
*# MyApp*
*#*
*start on runlevel [2345]*
*stop on runlevel [!2345]*
***exec sudo /usr/local/sbin/MyApp***
 
 
Furthermore I did add a line at the end of Visudo in order to avoid needing a password for starting it:
 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#
Defaults env_reset
# Host alias specification
# User alias specification
# Cmnd alias specification
# User privilege specification
root ALL=(ALL) ALL
# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
**root ALL=NOPASSWD: /usr/local/sbin/MyApp**
 
 
 
Maybe there's another way - but that's what I found for DESKTOP ubuntu version 
[http://greeennotebook.com/2010/06/run-application-as-root-at-startup/](http://greeennotebook.com/2010/06/run-application-as-root-at-startup/)
 
Problem is that although MyApp indeed starts at boot, it still does not seem to start as root. MyApp needs to connect to another root service (Dialogic Capi service), which it does fine via console, but not via upstart.
 
anyone has suggestion ?

---

### Post by furia on 2011-11-15
additional info:
 
when using ps  -C MyApp -f
 
I noticed that MyApp is indeed running as root, and this whether or not I put sudo in the upstart script.
 
But nevertheless MyApp does not work properly via upstart  - while starting it via console with sudo (or as root) works fine.

---

### Post by Wayne_V on 2011-11-15
you want it to run at boot or at login?  if at boot, just add it to /etc/rc.local (no sudo required).  You may have to nohup it if it doesn't like running without a terminal.   If you need to delay the startup you can add this to rc.local:

echo "/usr/local/sbin/MyApp" | at now+1m

---

### Post by furia on 2011-11-15
helllo Wayne,
 
Not being a Linux expert I probably did something wrong, because now the reboot does indeed try to start MyApp, but the booting screen is now hanging there just after starting MyApp - so my system is not further starting up...
 
so first question : how do I do quit it (CTRL C does not have effect) and second question how to make it work - MyApp is just a binary, which is reading a kind of config file (infact the execution is done as follows:  exec /usr/local/sbin/MyApp /etc/MyApp.conf     (MyApp is not using a console).
 
This is my actual rc.local content (I don't really understand the comments in it and the exit 0 line either - but actually I can't show you the original file - besides comments it was empty except for the exit 0 line), so this is how it is now:
 
exec /usr/local/sbin/MyApp /etc/MyApp.conf
exit 0

---

### Post by Wayne_V on 2011-11-15
can you ctrl-alt-F1 or F2 and get a login screen?   or maybe ssh in from another system?  if so, just kill MyApp.  if not, you will probably have to boot recovery mode and remove the upstart config.  [http://ubuntuforums.org/showthread.php?t=1510133](http://ubuntuforums.org/showthread.php?t=1510133)

Note, you don't need the exec in the rc.local, just the command itself.

and you should push MyApp into the background:

/usr/local/sbin/MyApp /etc/MyApp.conf &

otherwise rc.local will never exit

---

### Post by furia on 2011-11-15
via second console I managed indeed to rollback the rc.local to the original, so I tried then without exec and with the & at the end of the command - booting is fine now.
 
but the result is still that the MyApp program doesn't work properly. It behaves exactly as when I run it from console WITHOUT sudo - then it also doesn't work properly (in fact does not connect to a CAPI interface of a Dialogic Card) - so the final result is still the same as how it behaves via upstart. Bus as said, via console with sudo it works perfectly !?!?!
 
And as already said before : ps -C MyApp -F shows UID root  - so I'm still stuck ...

---

### Post by furia on 2011-11-15
additional info :  I'm running 64-bit version of Lucid, but MyApp is still 32-bit, so it is running via the ia32-libs package that I have installed. Not sure it this makes any difference, but like to give complete information....

---

### Post by furia on 2011-11-15
correction: MyApp does only start when logging in as root and then starting MyApp !  When logging in as other user and using sudo then I have the same problem - so my previous statement was not correct. 
 
Meanwhile I also rolled-back visudo to exclude sudo conflicts from there, but no change.
 
Anyhow the key must be somewhere in how root user differs from sudo.

---

### Post by Wayne_V on 2011-11-15
the only difference would be in the user environment.  try this in /etc/rc.local:

echo "nohup /usr/local/sbin/MyApp /etc/MyApp.conf" | at now+1min

that will schedule it to start 1 minute after boot and also tell it to ignore hangup signals (for instance, if the parent shell were to exit)

---

### Post by iissmart on 2011-11-16
chown root:root MyApp

chmod u+s MyApp

Now anyone that runs it (even without sudo) will run it as root.

---

### Post by CharlesA on 2011-11-16
> **iissmart said:**
> chown root:root MyApp

chmod u+s MyApp

Now anyone that runs it (even without sudo) will run it as root.

The sticky bit should only be used very rarely.

Using sudo would work fine.

---

### Post by hawkmage on 2011-11-17
Any app that is started by upstart should already be root.  

Will the app you are trying to start with Upstart run without the Dialogic Capi service running?  If not is Upstart starting your app too soon?  If so you may want to change the start on setting in your upstart script and have the startup of the Dialogic Capi service emit a upstart signal that is used to trigger you upstart script.

---

### Post by furia on 2011-11-19
Thanks a lot for your hint Wayne - problem was the timing :  MyApp should start later than Dialogic card. 
 
P.S. My statement about sudo behaving different as root was not correct - I made a fault in the path of MyApp config file when trying via sudo.

---

