---
title: "Can't view INSTALLED category in software-center"
date: 2013-02-13
forum: Ubuntu Development Version
---

### Post by mgngapyin on 2013-02-13
I'm trying 13.04 - i386, and Software Center is not working properly. I can't view the "*Installed*" category. 

# When I click on it, it displays just the loading circle, loading forever. 
# Then, I  click on '*All Software*' category, but it quickly returns to '*Installed*' tab again. 

All I can do is quit the software-center, and reopen again. There is no problem if I don't click the 'Installed' tab. Are you experiencing the same problem?

**Update: I installed 'oneconf', and the issue is resolved. **

---

### Post by nomenkultur on 2013-02-13
I am experiencing the exact same problem + crashes

 I have reported and they seem to already know about this...

 it started when I manually did some apt get removes of packages

 edit: and there you go, your oneconf fix worked


 so this happens when you remove stuff using the terminal and the software center doesn't know about it so when it tries to check your packages it crashes.

---

### Post by cariboo on 2013-02-13
> **nomenkultur said:**
> I am experiencing the exact same problem + crashes

 I have reported and they seem to already know about this...

 it started when I manually did some apt get removes of packages

 edit: and there you go, your oneconf fix worked


 so this happens when you remove stuff using the terminal and the software center doesn't know about it so when it tries to check your packages it crashes.

I think you are suffering from something else, as the software centre is just a front-end for apt and dpkg.

Are you seeing the same problem, using synaptic?

---

### Post by nomenkultur on 2013-02-13
The oneconf fixes software center immediately and I've been removing a lot of stuff and never had that problem again.

 I don't use synaptic since software center seems to be all I need

---

### Post by mcellius on 2013-02-13
I'm having the exact same problem here.  I haven't tried insalling oneconf yet so I don't know if that will fix it on my computer.  

I didn't try choosing "Installed" until I saw this thread.  The first time I tried it, I got a problem notification (apport) and tried to report it, but for some reason that crashed, too, as I reached Launchpad.  Now when I select "Installed," I just get the continuing indicator, as was reported above.

---

### Post by nomenkultur on 2013-02-13
oneconf made it work


 I then connected a HFS+ external volume and now this happens


[http://youtu.be/7j-4f84ER_4](http://youtu.be/7j-4f84ER_4)

---

### Post by cariboo on 2013-02-13
What error message do you get when trying to start the software-centre from a terminal?

---

### Post by mcellius on 2013-02-13
Software-center seems to start all right from the terminal, but when I click on "installed" I get a never-ending error message in the terminal window.  That is, it goes on and on and I can never reach the end of it, which I assume means it just keeps receiving the error.  It's probably repeating but I don't know where it begins or ends.

---

### Post by nomenkultur on 2013-02-14
[http://youtu.be/rGAKy_yjYQ0](http://youtu.be/rGAKy_yjYQ0)


 I bricked ubuntu  :( 

 nothing works anymore, not apt-get not software center and not oneconf

 I try to report problems and the report app crashes.

 it goes into a loop

 system problem detected

 report

 crash

 system problem detected

 I think the multiple kernel updates/updates finally did it for me or connecting that hfs+ hard drive


" software-center
2013-02-14 11:25:28,263 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:799: PyGIDeprecationWarning: Calling child_watch_add without priority as first argument is deprecated
  PyGIDeprecationWarning)
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:667: PyGIDeprecationWarning: Calling io_add_watch without priority as second argument is deprecated
  PyGIDeprecationWarning)
2013-02-14 11:25:29,096 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-02-14 11:25:29,098 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-02-14 11:25:29,106 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-02-14 11:25:29,106 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-02-14 11:25:29,293 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Bus error (core dumped)
"


 anyway gonna have to stop using it now since I get crash ater crash after crash

---

