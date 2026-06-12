---
title: "Ubuntu One don't creat a folder"
date: 2011-06-09
forum: Ubuntu One (CLOSED)
---

### Post by Juan Manuel Rivero on 2011-06-09
Hello,

I have the 11.04 version.

I've tried to run Ubuntu One from the Launcher, but it doesn't do anything, so I have to go to the terminal and write [I]sudo ubuntuone-control-panel-gtk
[/I]Once it runs, the window opens, and where it should say *_File Sync is up-to-date _*it appears in red letters this error:
[COLOR=Red]File Sync error. (org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1)[COLOR=Black], next to it I have the option [COLOR=DarkOrange]Restart[COLOR=Black], but it doesn't do anything if I click it.[/COLOR][/COLOR][/COLOR]

[COLOR=Black]If I go to the section "Cloud Folders" it appears:

[COLOR=Red]Value could not be retrieved. (DBus exception: [/COLOR][/COLOR][/COLOR][COLOR=Red]org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1)

[COLOR=Black]The folder Ubuntu One that should appear in my Home Folder, doesn't exist.

I've tried to find an answer to this problem in many forums, bug reports, and despite theres one or two  that shows a similar problem ([http://ubuntuforums.org/showthread.php?t=1602806](http://ubuntuforums.org/showthread.php?t=1602806), [http://askubuntu.com/questions/9486/why-wont-ubuntuone-service-start-automatically-at-boot](http://askubuntu.com/questions/9486/why-wont-ubuntuone-service-start-automatically-at-boot)) I  can't fix the problem.

Does anyone have an idea of what to do?

I'm new in Linux, so there's a lot of things I don't know how to do.

Thanks
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
Juan Manuel
[/COLOR][/COLOR]

---

### Post by nickyspag on 2011-08-05
I am also experiencing this problem.

I looked at this thread:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10946349](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10946349)

And tried running this command:

```
killall ubuntuone-syncdaemon; /usr/lib/ubuntuone-client/ubuntuone-syncdaemon --debug
```

The output of which is:

```
ubuntuone-syncdaemon: no process found
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 21, in <module>
    from twisted.internet import glib2reactor
  File "/usr/lib/python2.7/dist-packages/twisted/internet/glib2reactor.py", line 23, in <module>
    from twisted.internet import gtk2reactor
  File "/usr/lib/python2.7/dist-packages/twisted/internet/gtk2reactor.py", line 26, in <module>
    from zope.interface import implements
ImportError: No module named interface
```

---

### Post by kapa77 on 2011-11-16
I did:

```
sudo pip install zope.interface --upgrade
```and it fixed this problem.

---

### Post by paladin_knight on 2011-11-17
I am facing a similar problem with UbuntuOne. In Ubuntu One, it says that my files already synchronized. But when I checked online, I only found 1 or two files uploaded. Since then, I never use Ubuntu One. :(

---

### Post by munifsudaryono on 2011-11-17
*Contains toolkits to upload your page, build forms, and create web albums.*
  Make link from this topic to the following address:
  **[http://munif.mastercomputertools.com/stores/munif/236355pgabout.html](http://munif.mastercomputertools.com/stores/munif/236355pgabout.html)**

---

### Post by vanhenryjr on 2011-11-18
> **paladin_knight said:**
> I am facing a similar problem with UbuntuOne. In Ubuntu One, it says that my files already synchronized. But when I checked online, I only found 1 or two files uploaded. Since then, I never use Ubuntu One. :(

I too had this problem, but read the ubuntu 1 info and finally figured it out. It will sync all files in the Ubuntu One folder on my computer. Move the files you want to save there and keep them there and (I think) they will be saved in the cloud AND on your computer).

---

