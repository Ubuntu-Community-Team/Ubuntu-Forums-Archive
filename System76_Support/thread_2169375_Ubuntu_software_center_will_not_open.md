---
title: "Ubuntu software center will not open"
date: 2013-08-21
forum: System76 Support
---

### Post by Than Man on 2013-08-21
When I click on the Ubuntu Software Center Icon It will not open and when I X it out it says this:

The window "Ubuntu Software Center" is not responding.

Forcing this application to quit will cause you to lose any unsaved changes.

I have been force quiting. Any answers for a beginner?

---

### Post by ibjsb4 on 2013-08-21
Try opening it [in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and see if you get any errors.

```
software-center
```

Check in with you after dinner :)

---

### Post by mdams on 2013-08-21
Thank you for that assistance.  I had just done a search and found exactly what I needed.  Mike

---

### Post by ibjsb4 on 2013-08-21
Congradulations :)  This is one question that has come up before, could you please post your solution for others. and ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**AND** welcome to the forums :)

---

### Post by mdams on 2013-08-21
Thanks for the welcome.  I am new to the forum and newish to Ubuntu.  I resell used computer parts and have a tower dedicated to testing hard drives.  It was assembled by a shop, the OS is one of the older versons of Ubuntu and did not come with the software center app like 12.04 LTS which is on two of my lap tops.  I want to download some additional test type programs to that "testing" tower and did not know how to do it.  

Using your advise I opened the terminal and entered    software-center
I pressed the enter key on my keyboard,  I was prompted to enter my password which I did and again pressed the enter key and the software center opened for me.

This was the first time I had used the terminal.  Again thank you for the clear instructions.  Its a learning process for me and am enjoying it.mostly, Mike.

ps as I am not the one who started this thread and only  benifited by his question I hope he will report backwith good news as well.  Mike.

---

### Post by ibjsb4 on 2013-08-21
I did not catch that, funny.

---

### Post by Than Man on 2013-08-22
> **ibjsb4 said:**
> Try opening it [in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and see if you get any errors.

```
software-center
```

Check in with you after dinner :)

ibjsb4,
I am running Ubuntu 13.04 which was a clean install.  Softwarte Center worked when I first installed it.
Thanks for the advice but it did not work. 
Here is what I got in my terminal. Hopefully you can understand what it means and can lead me in the right direction.

than@than-Wild-Dog-Performance:~$ software-center
2013-08-22 19:49:37,148 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-08-22 19:49:37,278 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-08-22 19:49:37,436 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-08-22 19:49:37,438 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-08-22 19:49:37,444 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-08-22 19:49:37,444 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-08-22 19:49:37,478 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

---

### Post by ibjsb4 on 2013-08-22
The WARNINGs are not a problem, but the error:

> ERROR - Could not find any typelib for LaunchpadIntegration

A search came up with many hits

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Could+not+find+any+typelib+for+LaunchpadIntegration&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Could+not+find+any+typelib+for+LaunchpadIntegration&sa=Search&cof=FORID:9)

I would suggest that until you get this figured out, to use another package manager.

[Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager&sa=Search&cof=FORID:9") works well.

To install it in terminal:
```
sudo apt-get install synaptic
```

---

### Post by Than Man on 2013-08-23
> **ibjsb4 said:**
> The WARNINGs are not a problem, but the error:



A search came up with many hits

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Could+not+find+any+typelib+for+LaunchpadIntegration&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Could+not+find+any+typelib+for+LaunchpadIntegration&sa=Search&cof=FORID:9)

I would suggest that until you get this figured out, to use another package manager.

[Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager&sa=Search&cof=FORID:9") works well.

To install it in terminal:
```
sudo apt-get install synaptic
```

ibjsb4,

I installed the Synaptic package manager and that works for me and I will probably just use that from now on. I thank you for helping a beginner like me. 

When I have time I may reinstall Ubuntu 13.04 and see if the Software Center will work again.

---

### Post by ibjsb4 on 2013-08-23
Welcome :)

---

### Post by isantop on 2013-08-26
Try installing these packages in synaptic:

```
python-gobject-cairo
gir1.2-launchpad-integration-3.0
```

These were mentioned in a bug report as causing this issue. They may have been inadvertently removed.

---

