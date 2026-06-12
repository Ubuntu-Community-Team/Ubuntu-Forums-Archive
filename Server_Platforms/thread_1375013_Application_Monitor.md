---
title: "Application Monitor"
date: 2010-01-07
forum: Server Platforms
---

### Post by Niets on 2010-01-07
I am disappointed at the lack of simple application monitoring software. Yes, I am aware of cron, Upstart, monit, runit, and others, but they are either enterprise class or require so much console effort and learning just to monitor a few simple applications that they are hardly worth it. Upstart requires something like-
 
$ **cat /etc/event.d/rc2 **
# rc2 - runlevel 2 compatibility 
# 
 
start on runlevel 2 
 
stop on runlevel [!2] 
 
console output 
script 
set $(runlevel --set 2 || true) 
if [ "$1" != "unknown" ]; then 
PREVLEVEL=$1
RUNLEVEL=$2 
export PREVLEVEL RUNLEVEL 
fi 
 
exec /etc/init.d/rc 2 
end script
 
 
Where the Windows equivalent is-
 
[IMG]http://www.softpedia.com/screenshots/Application-Monitor_1.png[/IMG]
 
 
Now I don't mind dropping into the console, but am really disappointed that there is such a large disparity between the two enviroments. You don't see the DOS prompt being used to monitor applications in the Windows world.
 
Am I missing something or will application monitoring under Ubuntu remain something written by geeks for geeks and the casual server owner will remain a Windows user?
 
@edit-
I am aware that Ubuntu server is not GUI based, but thought I would post here as most desktop users do not need to monitor applications.  If there is a better place for this post please move this thread.

---

### Post by cdenley on 2010-01-07
Application monitor? You mean like: System>Administration>System Monitor?

---

### Post by Niets on 2010-01-07
> **cdenley said:**
> Application monitor? You mean like: System>Administration>System Monitor?
 
I believe you can only view applications with System Monitor and it has some control over services. What I would like to see is a application that watches different applications (preferably on a time table of my choosing) and if the application dies it is automatically restarted. There are a dozen or so little applets in the Windows world that does this, but I haven't been successful finding the equivalent in the Ubuntu/Linux world. I am transitioning some of my servers away from Windows to Linux and this is one of the deficiencies I have found.

---

### Post by BkkBonanza on 2010-01-07
You may want to look into respawn. This used to be done with inittab but now since upstart is the new system it's used in a conf file in /etc/init.

For example, /etc/init/tty1.conf shows how it is used. 

respawn watches the daemon and restarts it if it ever goes down.

The thing that makes it a bit tricky is that most services are still started the old way using rc init scripts and upstart uses the rc.conf to initiate that process. I don't think respawn will work in the rc scripts (not sure). So for example to get apache to respawn I think you would now have to make a conf file for it and remove it from the normal rc system.

This page has some info about respawn in upstart,
[http://upstart.ubuntu.com/wiki/Stanzas](http://upstart.ubuntu.com/wiki/Stanzas)

I have to comment,  despite this, I haven't had issues with daemons dying in my experience with my server. Even after running the current one for more than a year none of them have died. Maybe that's a windows thing, <big grin>.

---

### Post by Niets on 2010-01-07
> **BkkBonaza said:**
> Maybe that's a windows thing, <big grin>.
 
8-)
 
More like a user thing from clients coming in from the internet but that is one of the reasons I am transitioning some things to Linux is the stability.
 
Thanks for the pointer.  I will read up on respawn.

---

### Post by Digger9 on 2010-01-07
> **BkkBonaza said:**
> 

This page has some info about respawn in upstart,
[http://upstart.ubuntu.com/wiki/Stanzas](http://upstart.ubuntu.com/wiki/Stanzas)



That is back to Upstart again which requires an inordinate amount of scripting for a simple task.

To my knowledge, Linux and Ubuntu have nothing even close to Application Monitor (Free - shareware) that is shown above.  With that application you just identify the program you want it to watch and how often to check it and click create-

[IMG]http://www.softpedia.com/screenshots/Application-Monitor_3.png[/IMG]

Strange there isn't a simple equivalent in Linux with all the server applications.  The same thing can be scripted through Upstart, monit, etc. but it is really a PITA comparatively.

---

### Post by BkkBonanza on 2010-01-08
I think there's a few reasons for this. Traditionally Linux server admin has been mostly command line oriented. This is changing over time and no doubt someday (if not already) some Python programmer will make a small app to do this. It would be a fairly trivial thing to write in comparison to other apps around.

Nonetheless there are fairly simple ways for doing this even without a special app. Maybe the simplest possible way for just one app is to add a cron line as follows,

* * * * * pgrep apache || /etc/init.d/apache start

(this uses the OR operator to run the start only if the first test fails)
(would have to be in root's cron not yours)

If you want to do this from a gui you can install gnome-schedule, then add a line like above as your monitor test. One line per app. This gets you fairly close to what you have in Windows just using cron/schedule. 

(I think schedule runs as "you" by default, so to run as root in gui you would need to alter the menu item properties to prefix gksudo to the command. It will authenticate for root privileges.)

---

### Post by Niets on 2010-01-08
Good thoughts Bkk.  Very close to what I was looking for.
 
Many thanks!

---

