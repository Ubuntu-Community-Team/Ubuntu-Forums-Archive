---
title: "Update Manager woes"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wolfen69 on 2011-12-20
Is the update manager working for anyone else? The app just hangs when I click "install". For now I have to use the terminal for updates.

---

### Post by psypher on 2011-12-20
Yeah i have the same issue. But eventually a box pops up:

The connection to the daemon was lost. Most likely the background daemon crashed.
It seems that the daemon died.

agt-get update/upgrade works fine though

---

### Post by fabricator4 on 2011-12-20
> **psypher said:**
> Yeah i have the same issue. But eventually a box pops up:

The connection to the daemon was lost. Most likely the background daemon crashed.
It seems that the daemon died.

agt-get update/upgrade works fine though

Same here, but I didn't get the popup; eventually the revolving wait icon disappeared and mouse-over was able select the buttons again.  I elected to close it and do apt-get upgrade rather than try again.

I'm currently seeing 49 packages held back and not upgraded.  We must be waiting for a new kernel release to come through or something?

Chris

---

### Post by psypher on 2011-12-20
Yeah i just used the cli instead, there is a new kernel

---

### Post by jerrylamos on 2011-12-20
> **wolfen69 said:**
> Is the update manager working for anyone else? The app just hangs when I click "install". For now I have to use the terminal for updates.

"Update Manager" has screwed me so many times over the last several releases I set it for "NEVER".  Ever.

I use

sudo aptitude update
sudo aptitude safe-upgrade

and if some packages that look O.K. don't get upgraded I do a

sudo aptitude full-upgrade

Now over time the disk space usage gets to be more and more so I do

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

which still doesn't remove all the old packages, so I'll so a 

sudo synaptic

and then do a complete remove example linux-image-generic-3.2.0.5 got left on /boot even though 3.2.0.6 was installed

My experience - NEVER - use Update Mangler.

Jerry

---

### Post by grahammechanical on 2011-12-20
If you wait long enough Update manager will sort itself out and the download will take place.

I have taken to using synaptic but two nights ago it informed me that it was going to remove Ubuntu-desktop. I did not let it do that. And last night (just after midnight - so early today) it again wanted to remove Ubuntu-desktop. But it did not show Ubuntu-desktop as marked for upgrade. In fact the present version is the same as the latest version. No need to change.

So, something funny is happening with updates. I now do not trust the "Mark all upgrades" option of synaptic. In comparison update manager did not want to remove Ubuntu-desktop.

Regards.

---

### Post by wolfen69 on 2011-12-20
I filed a bug report about this, but have not had any responses to it. Others having the same issue might want to add their 2 cents to the bug report [here.]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/902601")

---

### Post by zika on 2011-12-20
As far as update-manager is concerned, at this moment, I get just this in CLI:```
:~$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 116, in <module>
    app.main(options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1220, in main
    self.check_metarelease()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1207, in check_metarelease
    self.options.use_proposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/MetaReleaseGObject.py", line 37, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MetaRelease.py", line 71, in __init__
    self.current_dist_name = get_dist()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/utils.py", line 184, in get_dist
    p = Popen(["lsb_release","-c","-s"],stdout=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

---

### Post by wolfen69 on 2011-12-20
> **zika said:**
> As far as update-manager is concerned, at this moment, I get just this in CLI:```
:~$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 116, in <module>
    app.main(options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1220, in main
    self.check_metarelease()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1207, in check_metarelease
    self.options.use_proposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/MetaReleaseGObject.py", line 37, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MetaRelease.py", line 71, in __init__
    self.current_dist_name = get_dist()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/utils.py", line 184, in get_dist
    p = Popen(["lsb_release","-c","-s"],stdout=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

Have you reported your experience? I posted a link above if you would like to chime in. (and anyone else having an issue with it)

---

### Post by fabricator4 on 2011-12-20
> **zika said:**
> As far as update-manager is concerned, at this moment, I get just this in CLI:

```
:~$ update-manager 
```



I'm just wondering if that should be started with sudo?

I've added a "me too" to the bug report, but I'm guessing that the reason you may not have heard anything is that they already know about the problem.

Chris

---

### Post by cariboo on 2011-12-20
> **fabricator4 said:**
> I'm just wondering if that should be started with sudo?

I've added a "me too" to the bug report, but I'm guessing that the reason you may not have heard anything is that they already know about the problem.

Chris

Some times it takes a day or two to get a response to a bug report, if there was already a report about this problem, it would have been tagged as a duplicate.

---

### Post by mc4man on 2011-12-21
This looks like a new issue with U-M that would only affect a 64 bit install. Otherwise U-M still suffers from the long delay due to some deal with aptdaemon.

While I don't use too often to install do find U-M useful to see the updates, changelogs & active links to bug reports.
So a a workaround till fixed have switched the backend to synaptic from aptdaemon & U-M now opens/works fine with no delays, ect.

---

### Post by zika on 2011-12-26
> **zika said:**
> As far as update-manager is concerned, at this moment, I get just this in CLI:```
:~$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 116, in <module>
    app.main(options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1220, in main
    self.check_metarelease()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1207, in check_metarelease
    self.options.use_proposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/MetaReleaseGObject.py", line 37, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MetaRelease.py", line 71, in __init__
    self.current_dist_name = get_dist()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/utils.py", line 184, in get_dist
    p = Popen(["lsb_release","-c","-s"],stdout=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```It seems that [http://ubuntuforums.org/showpost.php?p=11563300&postcount=1](http://ubuntuforums.org/showpost.php?p=11563300&postcount=1) solved this... ;)

---

