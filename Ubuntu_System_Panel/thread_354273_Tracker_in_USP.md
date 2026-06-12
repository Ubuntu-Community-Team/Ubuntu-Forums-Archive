---
title: "Tracker in USP"
date: 2007-02-05
forum: Ubuntu System Panel
---

### Post by _linux_ on 2007-02-05
Is there a way to use Tracker in USP? If there is, how do you?

---

### Post by Malac on 2007-02-06
> **_linux_ said:**
> Is there a way to use Tracker in USP? If there is, how do you?
Which Tracker are you talking about, have you a link or screenie?

---

### Post by zekopeko on 2007-02-06
i think he's talking about Tracker that is similar to Beagle.

[http://live.gnome.org/Tracker](http://live.gnome.org/Tracker)

i would go for beagle is possible. it just looks more polished.

---

### Post by chanders on 2007-02-06
If you know the command for the search, you can create a custom .desktop file for Tracker. You can also set the run in terminal to true in the .desktop file (It runs in the terminal, doesnt it?)

You can even set the search_command in USPConfig to the one for Tracker.

---

### Post by Quikee on 2007-02-06
It still would be nice if USP would have "search-as-you-type" plugin with beagle or tracker back-end (both are in feisty repositories). 

This sounds quite like a challenge so I might brush up my python and do it myself.

---

### Post by Malac on 2007-02-06
> **Quikee said:**
> This sounds quite like a challenge so I might brush up my python and do it myself.Feel free, the more the better.
That's how I got involved in the usp project just writing a plugin and that turned into another then more and chanders was kind enough to invite me to work on usp itself.

---

### Post by chanders on 2007-02-06
> **Quikee said:**
> It still would be nice if USP would have "search-as-you-type" plugin with beagle or tracker back-end (both are in feisty repositories). 

This sounds quite like a challenge so I might brush up my python and do it myself.

Consider it a challenge ;-) Malac and myself will help you along the way. Believe me, the hardest part is getting it to work behind the scenes. The graphical part is the easiest..

---

### Post by Quikee on 2007-02-07
Thanks guys.

I've looked in deskbar applet how he interfaces with tracker so at least this won't be hard to figure out. The only problem that this weak I don't have much free time left so don't expect results very soon (I hope next week will be better).

---

### Post by _linux_ on 2007-02-07
Thank you all for your help! I hope you do well with your challenge!

---

### Post by Quikee on 2007-02-09
OK.. here is a quick first version of the tracker plugin. To make it work unpack the trackerPlugin.tar.gz in ./usp/plugins diretory (create if it does not already exist). [Tracker]("http://www.gnome.org/projects/tracker/") is also needed to make it work (it's already in feisty repository - sudo apt-get tracker).

Currently it can only search for files and can not filter file types yet. There is not much error checking so it might not work for everyone.

I took recent plugin as a base and worked on it (sorry.. I changed the name of variables to my likings :)  ).

to Malac & chanders: I don't know if it works with uspconfig because uspconfig doesn't work for me. I get the following error:
```
Traceback (most recent call last):
  File "/usr/bin/uspconfig", line 528, in <module>
    app=MainWindow()
  File "/usr/bin/uspconfig", line 88, in __init__
    self.lang=self.language[0:2]
TypeError: 'NoneType' object is unsubscriptable

```

I also have a question: How can I get the appropriate icon or path for the icon for a mime type?

---

### Post by Malac on 2007-02-20
Hi Quikee,
Just thought I'd send you my thoughts on the Tracker plugin and a few tweaks for you to consider.
Firstly, great work it's looking good.
The Clear button wasn't working on your version. The function name had not been set correctly in the Glade file.
I have changed this and altered the config window for use with uspconfig/Preferences.

Plus screenies of it working and the uspconfig section working.
I'm afraid I don't know why you're getting the subscript error on self.language[0:2] line 88 of uspconfig.
[ATTACH]25753[/ATTACH][ATTACH]25754[/ATTACH]

---

### Post by plun on 2007-02-20
Hi  Quikee and Malac...

Absolutely great...:)   Turbo search...

---

### Post by Quikee on 2007-02-20
> **Malac said:**
> Hi Quikee,
Just thought I'd send you my thoughts on the Tracker plugin and a few tweaks for you to consider.
Firstly, great work it's looking good.
The Clear button wasn't working on your version. The function name had not been set correctly in the Glade file.
I have changed this and altered the config window for use with uspconfig/Preferences.

I did actually fixed the clear button bug in the version I have on disk. I will merge the uspconfig changes. Thanx.


> **Malac said:**
> 
I'm afraid I don't know why you're getting the subscript error on self.language[0:2] line 88 of uspconfig.


I found the bug here -> self.language is None in my case. In this case I set self.lang to "en" and it works. I think my locale are screwed up.


Later today I will release a new tracker plugin version.

---

### Post by Malac on 2007-02-20
> **Quikee said:**
> I did actually fixed the clear button bug in the version I have on disk. I will merge the uspconfig changes. Thanx.

I found the bug here -> self.language is None in my case. In this case I set self.lang to "en" and it works. I think my locale are screwed up.
Later today I will release a new tracker plugin version.
Excellent.
I can add it to the Extra/Add-On plugins tar file along with the others if you want.

---

### Post by Quikee on 2007-02-20
Hello..

Tracker plugin is ready for the second release. 
Lot has changed:
[LIST]
[*] icons are now shown depending on the mime type of the file
[*] with right click on the file, applications that can execute the file can be chosen
[*] side menu for additional filtering
[*] gconf entry for maximum number of entries returned by tracker
[*] general cleanup
[/LIST]
Seems almost usable now. =)

Have fun.

> I can add it to the Extra/Add-On plugins tar file along with the others if you want.

Would be great. Thanx.

---

### Post by hanzomon4 on 2007-02-20
Is there a way to get deskbar functionality in a usp plugin so that we could just use the deskbar handlers for tracker, beagle, launch application X, etc?

---

### Post by Quikee on 2007-02-20
> **hanzomon4 said:**
> Is there a way to get deskbar functionality in a usp plugin so that we could just use the deskbar handlers for tracker, beagle, launch application X, etc?

Should be possible, but not an easy task to do. I wanted to add beagle backend in the future but maybe I should concentrate on including support for deskbar handlers instead.

---

### Post by plun on 2007-02-20
> **Quikee said:**
> Hello..

Tracker plugin is ready for the second release. 

Have fun.



Well,  me and my Feisty friend....:) 

It crashes during X-start... but USP and Tracker then works after adding it to the panel
after start is finished.

> ProcStatus:
 Name:	python
 State:	R (running)
 <Snip>
 Mems_allowed:	1
PythonArgs: ['/usr/bin/usp', '--oaf-activate-iid=OAFIID:GNOME_USP_Factory', '--oaf-ior-fd=33']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/usp", line 866, in menu_factory
     MenuWin(applet, iid)
   File "/usr/bin/usp", line 636, in __init__
     self.mainwin = MainWindow()
   File "/usr/bin/usp", line 59, in __init__
     self.PopulatePlugins()
   File "/usr/bin/usp", line 244, in PopulatePlugins
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
 DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/trackerd exited with status 0

Tracker is great anyway....:)

EDIT

About >gconf entry for maximum number of entries returned by tracker...  I changed this value to 20> reloaded plugins
but nothing happens...  "This key have no schema" ?

---

### Post by Quikee on 2007-02-21
> **plun said:**
> Well,  me and my Feisty friend....:) 

It crashes during X-start... but USP and Tracker then works after adding it to the panel
after start is finished.



Probably this happens because tracker daemon or dbus is not yet started when Gnome and USP starts. In Feisty I have such problems with Gnome, because dbus doesn't start yet when system boots. 

I will try to work around this. 

Thanx for reporting.

> **plun said:**
> 
About >gconf entry for maximum number of entries returned by tracker...  I changed this value to 20> reloaded plugins
but nothing happens...  "This key have no schema" ?

I will look into this (I hope with "nothing happens" you mean if you search that nothing happens).

---

### Post by plun on 2007-02-21
> **Quikee said:**
> 

I will try to work around this. 

I will look into this (I hope with "nothing happens" you mean if you search that nothing happens).

Hi Quikee..

Thanks.

About "nothing happens", my english...:oops:  I change the value to 20 but the search result output is still 10.  Also  inside gconf-editor this value has a warning "This key has no schema".   One more thing is that this also needs a scrollbar.

It might be good to handle larger amount of search results...  maybe...:) 

The dbus challenge is probably harder to solve..  :)

---

### Post by Quikee on 2007-02-21
> **plun said:**
> Hi Quikee..

Thanks.

About "nothing happens", my english...:oops:  I change the value to 20 but the search result output is still 10.  Also  inside gconf-editor this value has a warning "This key has no schema".   One more thing is that this also needs a scrollbar.


Heh.. I found the cause now. Stupid me - I did everything right, but in the end I forgot to tell tracker to actually return the number of results defined in gconf. Scrollbar is not a problem.. it shows itself when needed.

> **plun said:**
> 
It might be good to handle larger amount of search results...  maybe...:) 

Maybe.. but if there are too many results, typing in search box might be interrupted. 

> **plun said:**
> 
The dbus challenge is probably harder to solve..  :)
Not really - all I did was that you don't need dbus and tracker unless you want to search. 

However I discovered a bug that was a bigger problem - if a file had spaces in the name, executing an application on that file didn't worked or didn't worked correctly.

Everything should now be fixed in this new release.

---

### Post by plun on 2007-02-21
> **Quikee said:**
> 

Everything should now be fixed in this new release.

Great work !   Thanks  :)

---

