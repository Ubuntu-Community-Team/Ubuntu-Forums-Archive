---
title: "USP2 Alpha on Feisty"
date: 2007-02-19
forum: Ubuntu System Panel
---

### Post by Malac on 2007-02-19
Here are some screenshots of USP running on a standard, off the CD, install of Feisty(metacity, no beryl) with all updates applied as of today(Monday, 19 February 2007).
I have run this now for several hours with no crashes I will report back with any problems and when they will be fixed.
Unfortunately this machine won't run  beryl so if there are any problems specific to that I'll have to wait until I upgrade my main machine.
The Feisty application crash report has been causing problems as it is a little "sensitive", as the calrem and recent plugins were causing a lot of crash reports to be generated, even though these weren't actually crashes or stopped the program working.
Hopefully these are now fixed. :)

Anyway here are some screenshots of all the Standard plugins and all the Extra/Add-On plugins working.
[ATTACH]25667[/ATTACH][ATTACH]25668[/ATTACH][ATTACH]25669[/ATTACH][ATTACH]25670[/ATTACH]

These are all done whilst running the latest SVN copy if you have installed from the alpha .deb file then you will still have some of the errors being reported until the .deb is updated. If it bothers you just tick the "Don't notify for this application" option(or whatever it says).

For future reference the part of the error report that is most useful is the "Traceback" section when posting errors.
Most of the rest of it is too machine specific to be of any use to the debug process.

And please remember Feisty is, itself, in testing. So you are running Test software on a Test OS, please don't get put off using USP because it fails at this stage. It may not be USP which is failing. ;)

Thanks, Malac.

---

### Post by plun on 2007-02-19
Thanks Malac  :) 

Is it difficult to fix active fields for inputs when Beryl is running ?

Notes, Search, Terminal is out of order..:-k 

Also found this search tool...Tracker  :) 

[http://www.gnome.org/projects/tracker/index.html](http://www.gnome.org/projects/tracker/index.html)

It would be really nice to connect this "jet" to USPs search field... :)

EDIT about searches:-\"   "Instant search"

[http://www.microsoft.com/windows/products/windowsvista/features/details/instantsearch.mspx](http://www.microsoft.com/windows/products/windowsvista/features/details/instantsearch.mspx)

---

### Post by chanders on 2007-02-19
>  Is it difficult to fix active fields for inputs when Beryl is running ?
Can you explain a little more?

> Also found this search tool...Tracker  :) 
Working on this plugin for USP3, and will definitely backport to USP2 ;-)

---

### Post by plun on 2007-02-19
> **chanders said:**
> Can you explain a little more?


Working on this plugin for USP3, and will definitely backport to USP2 ;-)

All textboxes are "dead" impossible to write something.  But a strange thing is that
this also sometimes occurs with Firefox 3.

Firefox 3 is also using Cairo so maybe its something with Cairo libs  ?

If I change Beryl to use Metacity as Windowsmaker everything works.

Strange...    or Feisty, Xorg 7.2, USP2 and Beryl is maybe too much..:) 

It must be more users running at least Feisty, Beryl and USP2 ?

I  found Murrines GTK engine and USP is alive ...:) 

[[IMG]http://img510.imageshack.us/img510/3641/snapshot21ek9.th.png[/IMG]](http://img510.imageshack.us/my.php?image=snapshot21ek9.png)

---

### Post by hanzomon4 on 2007-02-19
Good work, after getting the hang of configuring this thing it's become my default menu-"jack of all trades" panel thingy. As for tracker just put tracker-search-tool SEARCH_STRING as the search command.

---

### Post by PWill on 2007-02-19
> **plun said:**
> All textboxes are "dead" impossible to write something.  But a strange thing is that
In beryl settings manager, General > Main, make sure, Level of Focus Stealing Prevention is set to "None"

---

### Post by plun on 2007-02-20
> **xiamcitizen said:**
> In beryl settings manager, General > Main, make sure, Level of Focus Stealing Prevention is set to "None"

Thanks....:)    textboxes are alive...:) 

Strange function, default is "low",  with "none" it works...

---

### Post by plun on 2007-02-20
> **hanzomon4 said:**
> Good work, after getting the hang of configuring this thing it's become my default menu-"jack of all trades" panel thingy. As for tracker just put tracker-search-tool SEARCH_STRING as the search command.

Very nice  !

Changed to Tracker and USP rocks...:)  It would be really nice to integrate
the Tracker window....Chanders is probably already working on it :)

---

### Post by Quikee on 2007-02-20
> **plun said:**
> 
Also found this search tool...Tracker  :) 


> **chanders said:**
> 
Working on this plugin for USP3, and will definitely backport to USP2 ;-)

I am already working on a plugin for tracker. I published the plugin "beta" but no response, however I did made some progress since then. I hope our efforts will not overlap. 

Currently I'm working on a new sort "Applications" plugin which is more search centric (with file search using tracker, application search, recent filtering,...). I will also make the search box more powerful. I will move the favorites applications in shortcut plugin - this way favorites items and search will be separate which I for me is a more logical choice.

I hope for better communication with you and malac so we could share efforts.

---

### Post by hanzomon4 on 2007-02-20
I'm looking forward to all of this new search hotness, good luck.

---

### Post by Malac on 2007-02-20
> **Quikee said:**
> I am already working on a plugin for tracker. I published the plugin "beta" but no response
Sorry Quikee I missed it. I'll track it down and take a look.
> **Quikee said:**
>  I hope for better communication with you and malac so we could share efforts.
If you need to contact me feel free to pm me.
Maybe we'll get a developer session going on IRC when we can.

---

### Post by chanders on 2007-02-20
^^ Hey Quikee, I looked at you tracker plugin and I saw that Malac did a little editing too. It looks great, so I wont bother to duplicate your efforts ;-) Later when it is comitted to SVN we can all work to make it better..

I am also looking forward to your other plugins..

---

### Post by plun on 2007-02-20
More Feisty challengies...   "big bang" impossible to run from panel...

```
plun@dunder:~$ usp run-in-window
/usr/bin/usp:30: RuntimeWarning: Python C API version mismatch for module _keybinder: This Python has API version 1013, module _keybinder has version 1012.
  from _keybinder import tomboy_keybinder_bind as bindkey
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'usptime' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
No recent applications
Loading plugin 'recent' : successful
Loading plugin 'internet' : successful
Loading plugin 'notes' : successful
Loading plugin 'terminal' : successful
Loading plugin 'tracker' : successful
Static User Image Used

```

The same API fault occurs with Beryl and that can be handle in this way

> plun@dunderII:~$ sudo ln -s /var/lib/python-support/python2.4/berylsettings.so /var/lib/python-support/python2.5/berylsettings.so
Password:
plun@dunderII:~$ python2.5
Python 2.5 (release25-maint, Feb  5 2007, 02:52:52)
[GCC 4.1.2 20070129 (prerelease) (Ubuntu 4.1.1-31ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import berylsettings
__main__:1: RuntimeWarning: Python C API version mismatch for module berylsettings: This Python has API version 1013, module berylsettings has version 1012.
>>> import berylsettings
>>> 

I cannot figure out what to import and also make symbolic links to Python 2.5..:confused:

---

### Post by Malac on 2007-02-20
@plun and anyone running USP on Feisty to get round the Python C API version here is a temporary fix.
Replace the _keybinder.so in /usr/lib/python2.4/site-packages/**usp**/plugins with the attached version and let me know if this sorts it.

EDIT: Thanks Quikee. :)

---

### Post by Quikee on 2007-02-20
> **malac]Maybe we'll get a developer session going on IRC when we can.[/QUOTE]

Would be great.  said:**
> ^^ Hey Quikee, I looked at you tracker plugin and I saw that Malac did a little editing too. It looks great, so I wont bother to duplicate your efforts ;-)

OK.. if you have any suggestions for the plugin, just go ahead.

---

### Post by Quikee on 2007-02-20
> **Malac said:**
> 
Replace the _keybinder.so in /usr/lib/python2.4/site-packages/plugins with the attached version and let me know if this sorts it.

"/usr/lib/python2.4/site-packages/plugins" should be "/usr/lib/python2.4/site-packages/**usp**/plugins"

Yes.. it doesn't display the warning anymore.

---

### Post by plun on 2007-02-20
> **Malac said:**
> @plun and anyone running USP on Feisty to get round the Python C API version here is a temporary fix.
Replace the _keybinder.so in /usr/lib/python2.4/site-packages/**usp**/plugins with the attached version and let me know if this sorts it.

EDIT: Thanks Quikee. :)

Well... this is service   :) 

Thanks  !

I also found Murrines configurator so this is fun now.

---

### Post by plun on 2007-02-21
Strange.....  with revision 144 I have borders and everything follows my theme..:)

---

### Post by plun on 2007-02-23
Hi

"Crash man" calling again with rev 156  :) 

> PythonArgs: ['/usr/bin/usp', 'run-in-window']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/usp", line 891, in <module>
     menu_factory(app, None)
   File "/usr/bin/usp", line 881, in menu_factory
     MenuWin(applet, iid)
   File "/usr/bin/usp", line 647, in __init__
     self.mainwin = MainWindow()
   File "/usr/bin/usp", line 66, in __init__
     self.PopulatePlugins()
   File "/usr/bin/usp", line 425, in PopulatePlugins
     self.plugins[plugin].do_plugin()
   File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 425, in do_plugin
     self.do_mounted_volumes()
   File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 251, in do_mounted_volumes
     URI = gnomevfs.get_local_path_from_uri( volume.get_activation_uri() )
 RuntimeError: unknown error

---

### Post by Malac on 2007-02-24
> **plun said:**
> Hi

"Crash man" calling again with rev 156  :)
Hi "Crash man", :)
This was occurring for me in the bookmarks section. It turns out to be that 
gnomevfs.get_local_path_from_uri() doesn't like anything that doesn't start with file:// so this may be happening here. Have you got some remote drives mounted?
Okay I've put in a reversion to check for file at the beginning, Revision 158.
For debugging purposes there is a print statement on line 251 in places.py.
If you could open places.py in your editor and remove the # from it plun and then run usp in terminal and paste the list of uri's here to see what uri's you're system is trying to convert it would be helpful.
It will probably "fall-over" still but the first uri is the one that's important.
You can put the # back in or delete the line 251 once you've done this, thanks.

---

### Post by plun on 2007-02-24
Well.. a little confusing..

First my fstab, Feisty on one partition, Home separated and one NTFS partion
automagic with ntfs-config.

One strange thing is that my NTFS partition don't shows up as a volume, Feisty
just mount it.

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=e1536a7a-598c-4206-bcea-30be3aaae9a7 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda4 :
UUID=ea60a35d-3a50-4b02-8eda-60da18ad08fd /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=1AA884C7A884A2BD /media/hda1 ntfs-3g defaults,locale=sv_SE.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=0769cff9-2ffe-481c-b6d3-0a1d1df81900 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Print statement, nearest line I can find is 318  ??

print volume.get_display_name(),"  ",volume.get_device_type()," ",volume.get_volume_type()

> plun@dunder:~$ usp run-in-window
*********** PLEASE IGNORE THE ABOVE WARNING **************
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'usptime' : successful
Loading plugin 'computer' : successful
Loading plugin 'system_management' : successful
Loading plugin 'notes' : successful
Loading plugin 'terminal' : successful
Loading plugin 'places' : successful
Beagle not found..
Loading plugin 'tracker' : successful
No recent applications
Loading plugin 'recent' : successful
Loading plugin 'applications' : successful
Loading plugin 'internet' : successful
Static User Image Used
Traceback (most recent call last):
  File "/usr/bin/usp", line 891, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 881, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 647, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 66, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 425, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 428, in do_plugin
    self.do_mounted_volumes()
  File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 261, in do_mounted_volumes
    PlaceURI = gnomevfs.get_local_path_from_uri( volume.get_activation_uri() )
RuntimeError: unknown error


and /var/crash report

> PythonArgs: ['/usr/bin/usp', 'run-in-window']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/usp", line 891, in <module>
     menu_factory(app, None)
   File "/usr/bin/usp", line 881, in menu_factory
     MenuWin(applet, iid)
   File "/usr/bin/usp", line 647, in __init__
     self.mainwin = MainWindow()
   File "/usr/bin/usp", line 66, in __init__
     self.PopulatePlugins()
   File "/usr/bin/usp", line 425, in PopulatePlugins
     self.plugins[plugin].do_plugin()
   File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 428, in do_plugin
     self.do_mounted_volumes()
   File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 261, in do_mounted_volumes
     PlaceURI = gnomevfs.get_local_path_from_uri( volume.get_activation_uri() )
 RuntimeError: unknown error

Thats it from "crashman"...  :)

---

### Post by Malac on 2007-02-24
> **plun said:**
> Well.. a little confusing..

First my fstab, Feisty on one partition, Home separated and one NTFS partion
automagic with ntfs-config.

One strange thing is that my NTFS partition don't shows up as a volume, Feisty
just mount it.



Print statement, nearest line I can find is 318  ??

print volume.get_display_name(),"  ",volume.get_device_type()," ",volume.get_volume_type()



and /var/crash report



Thats it from "crashman"...  :)
Okay it looks like it's the same error propagating to the PlaceURI as well.
I'll change that too.
It looks like it is probably the ntfs volume mounted strangely.
Until I can get a printout of the URI I'm a bit stuck. (I don't use NTFS at all, too much hassle. :) )
EDIT: Revision 161
The print statement is definitely at line 251 and reads like follows:```
                [COLOR=Blue]#print volume.get_activation_uri()[/COLOR]
```Just remove the # from the front.

---

### Post by plun on 2007-02-24
> **Malac said:**
> Okay it looks like it's the same error propagating to the PlaceURI as well.
I'll change that too.
It looks like it is probably the ntfs volume mounted strangely.
Until I can get a printout of the URI I'm a bit stuck. (I don't use NTFS at all, too much hassle. :) )
EDIT: Revision 161
The print statement is definitely at line 251 and reads like follows:```
                [COLOR=Blue]#print volume.get_activation_uri()[/COLOR]
```Just remove the # from the front.

Well...  I have a mission impossible scanner and printer from Lexmark which
needs Windoze..:redface:  also some other useful stuff.

Nothing strange with ntfs-3g and mounts, it just works.

With rev 161 all crashes is gone...:) 

I dont have that print statement...:confused: 

line 244 > 255

>         Stack=gnomevfs.VolumeMonitor().get_mounted_volumes()
        Stack.reverse()
        for volume in Stack:
            if ( volume.is_user_visible() and volume.is_mounted() and volume.get_activation_uri() ):
                Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, volume.get_icon(), self.iconsize, 48, -1, [volume.get_display_name()], [""] )

                URI = string.join( volume.get_activation_uri().split( "//" )[1].split( "%20" ) )
                URI = string.replace(URI,"%23","#")
  
                Button1.connect( "button_press_event", self.ButtonClicked, [self.execapp, URI] )
                Button1.connect( "button_release_event", self.ButtonReleased )
                self.wTree.get_widget( "places_button_holder" ).pack_start( Button1, False, False, 10 )

:)

Edit, run in Windows and a reload crashes........

> plun@dunder:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'usptime' : successful
Loading plugin 'computer' : successful
Loading plugin 'system_management' : successful
Loading plugin 'notes' : successful
Loading plugin 'terminal' : successful
Loading plugin 'places' : successful
Beagle not found..
Loading plugin 'tracker' : successful
No recent applications
Loading plugin 'recent' : successful
Loading plugin 'applications' : successful
Loading plugin 'internet' : successful
Static User Image Used
No recent applications

** (usp:5073): WARNING **: Binding '<Ctrl><Alt>U' failed!


(usp:5073): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
Beagle not found..

Reloading Plugins...
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'usptime' : successful
Loading plugin 'computer' : successful
Loading plugin 'system_management' : successful
Loading plugin 'notes' : successful
Loading plugin 'terminal' : successful
Loading plugin 'places' : successful
Loading plugin 'tracker' : successful
No recent applications
Loading plugin 'recent' : successful
Loading plugin 'applications' : successful
Loading plugin 'internet' : successful
Static User Image Used
No recent applications
USP reloaded


a bash crash occurs...

---

### Post by Malac on 2007-02-24
> **plun said:**
> Well...  I have a mission impossible scanner and printer from Lexmark which
needs Windoze..:redface:  also some other useful stuff.

Nothing strange with ntfs-3g and mounts, it just works.

With rev 161 all crashes is gone...:) 

I dont have that print statement...:confused: 

line 244 > 255



:)

Edit, run in Windows and a reload crashes........



a bash crash occurs...
I still use WindowsXP just fat32.
It looks like the /usr/bin/usp file you have is not the latest one, it's probably not getting updated.
Try manually copying it over using the line from the usp_update script.
Or sudo nautilus and copy/paste it.

---

### Post by delfick on 2007-02-25
i have a new bug.....

when i click the "sticky" button at the top of the sidepane (to turn stickiness on or off), the usp closes.....

---

### Post by plun on 2007-02-25
> **Malac said:**
> I still use WindowsXP just fat32.
It looks like the /usr/bin/usp file you have is not the latest one, it's probably not getting updated.
Try manually copying it over using the line from the usp_update script.
Or sudo nautilus and copy/paste it.

FAT32... :confused:  Windoze must be run with NTFS...:)

I cleaned out everything followed  kobewans howto.

One thing with install is an error in line 74

> plun@dunder:~/ubuntu-system-panel$ ./usp_update install

./usp_update: line 74: [: saknar "]"      [COLOR="Red"]note "saknar" > missing in swedish[/COLOR]

Creating directories if needed...
Password:
Installing USP 1.92+svn_...
Installation is complete!
Remove and re-add USP from panel to register updates.
However, you may need to logout or restart gnome-panel
for updates to take affect.

Update OK

plun@dunder:~/ubuntu-system-panel$ ./usp_update update
USP is up-to-date
plun@dunder:~/ubuntu-system-panel$ 

Or am I doing something wrong....:confused: 

places.py is dated  **thu 22 feb 2007 12.30.47**

Inside /usr/bin/usp  it is 2 usp files usp and uspconfig.

It&#347; up and running anyway without crashes...:)

---

### Post by PsyberOneZero on 2007-02-25
I just sent a patch in, try updating to the latest version (165). it should fix you line 74 error.

Also is there anyone willin to test the "install fresh" and "uninstall complete" for me? It will reset all of you settings in USP.

---

### Post by plun on 2007-02-25
More clues about Feisty and "places"...  its a bug...:-$ 

[https://launchpad.net/ubuntu/+source/hal/+bug/73227](https://launchpad.net/ubuntu/+source/hal/+bug/73227)

[http://www.ubuntuforums.org/showthread.php?t=369752](http://www.ubuntuforums.org/showthread.php?t=369752)

:)

---

### Post by Malac on 2007-02-25
> **plun said:**
> More clues about Feisty and "places"...  its a bug...:-$ 

[https://launchpad.net/ubuntu/+source/hal/+bug/73227](https://launchpad.net/ubuntu/+source/hal/+bug/73227)

[http://www.ubuntuforums.org/showthread.php?t=369752](http://www.ubuntuforums.org/showthread.php?t=369752)

:)
Thanks plun, I caught that one apparently one way round it is to restart dbus once logged on and they all magically appear. :)
```
sudo /etc/init.d/dbus restart
```If you want to do it.

[RANT]
Apparently this is some new policy though what the rational behind it is I don't know. It makes absolutely no sense to me. What's the point of having users option in fstab if the partitions don't show up when a user logs on. This is the sort of thing that puts new users off because it just isn't common sense or the "obvious" thing to happen. So they think "I can't see my drives, this is broken, back to Windows".
[/RANT]

---

### Post by plun on 2007-02-25
> **Malac said:**
> 

```
sudo /etc/init.d/dbus restart
```If you want to do it.

[RANT]
Apparently this is some new policy though what the rational behind it is I don't know. It makes absolutely no sense to me. What's the point of having users option in fstab if the partitions don't show up when a user logs on. This is the sort of thing that puts new users off because it just isn't common sense or the "obvious" thing to happen. So they think "I can't see my drives, this is broken, back to Windows".
[/RANT]

Well.. who knows.. with modern fileservers everything is just files, add one disk or two
and everything looks like one volume...:) 

About dbus it works but rev 165 is a real crasher...

> plun@dunder:~/ubuntu-system-panel$ ./usp_update update
USP is up-to-date
plun@dunder:~/ubuntu-system-panel$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Loading plugin 'places' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 895, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 885, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 647, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 66, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 254, in PopulatePlugins
    MyPlugin = X.pluginclass( self )
  File "/home/plun/.usp/plugins/tracker.py", line 54, in __init__
    self.tracker = Tracker()
  File "/home/plun/.usp/plugins/tracker.py", line 25, in __init__
    self.tracker = bus.get_object('org.freedesktop.Tracker','/org/freedesktop/tracker')
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/trackerd exited with status 0


I am using the special "keybinder.so" file for Fiesty...

:confused:

EDIT, after a complete reboot...

> plun@dunder:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Loading plugin 'places' : successful
Loading plugin 'tracker' : successful
No User Picture Specified or File Not Found

(usp:6281): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition


---

