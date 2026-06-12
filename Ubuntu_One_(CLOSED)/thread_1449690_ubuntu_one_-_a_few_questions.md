---
title: "ubuntu one - a few questions"
date: 2010-04-08
forum: Ubuntu One (CLOSED)
---

### Post by plaurits on 2010-04-08
1: So, what does one do when Ubuntu One decides to overwrite your work files with one month old copies? How do I retrieve my work files?

2: Why does the ubuntu one applet tell me that it is connected, while when I navigate to the ubuntu one folder it tells me that it isn't connected?

3: Why does the ubuntu one applet tell me that my files are up to date, while they are not?

4: Why is Ubuntu One so painfully slow to update my files?

5: Is there any kind of quality control on Ubuntu One, other than us users?

6: Will all these problems be fixed in Ubuntu 10.4 ?

7: Since this product clearly doesn't work at all, where does one go to get a refund?

Thanks.

---

### Post by joshuahoover on 2010-04-08
I'll attempt to answer your questions below. My assumption is that you're using Ubuntu 9.10 and you have all the latest updates. If this is not the case, please let me know.

> **plaurits said:**
> 1: So, what does one do when Ubuntu One decides to overwrite your work files with one month old copies? How do I retrieve my work files

This should never happen. If it's happened to you, please do the following so we can track down the issue and get the problem remedied:

[LIST=1]
[*]Right-click on the Ubuntu One client and select "Report a problem"
[*]Describe your setup (multiple computers syncing with Ubuntu One?) the steps you took and the results (files got replaced by month old version).
[*]Attach all ~/.cache/ubuntuone/log/syncdaemon.log files you may have
[/LIST]
If you can, please hop on #ubuntuone on Freenode IRC. I'm normally available from Monday-Friday 13:00-21:00 UTC as joshuahoover.

> 2: Why does the ubuntu one applet tell me that it is connected, while when I navigate to the ubuntu one folder it tells me that it isn't connected?

It's hard to say without seeing log files. It may be a UI glitch or something deeper.

> 3: Why does the ubuntu one applet tell me that my files are up to date, while they are not?

How do you know the files are not up-to-date? Is this based on your first question? Please run the script found here to show which files are synced on your machine: [http://launchpadlibrarian.net/36063440/u1sdstatus.py](http://launchpadlibrarian.net/36063440/u1sdstatus.py) (from a terminal session: python u1sdstatus.py)

> 4: Why is Ubuntu One so painfully slow to update my files?

If you are updating a lot of files then this will be slow and we're working on fixing this problem. It's not a simple fix but one that we've been working on and hope to have some significant improvements on in the not too distant future.

> 5: Is there any kind of quality control on Ubuntu One, other than us users?

Yes there is quality control on Ubuntu One. We are continually improving our quality control processes and welcome the contributions from those in the community that have helped raise the overall quality of the Ubuntu One software.

> 6: Will all these problems be fixed in Ubuntu 10.4 ?

No, at least one problem will still remain and that is if you're attempting to synchronize thousands of files and folders it will be relatively slow.

> 7: Since this product clearly doesn't work at all, where does one go to get a refund?

If you have paid for the service please email me privately joshua dot hoover at canonical dot com. 

Thank you,

Joshua

---

### Post by plaurits on 2010-04-09
Thank you very much for answering my questions so fast.

> **joshuahoover said:**
> My assumption is that you're using Ubuntu 9.10 and you have all the latest updates.


Yes, that is the case.


> **joshuahoover said:**
> 
This should never happen. If it's happened to you, please do the following so we can track down the issue and get the problem remedied:

[LIST=1]
[*]Right-click on the Ubuntu One client and select "Report a problem"
[*]Describe your setup (multiple computers syncing with Ubuntu One?) the steps you took and the results (files got replaced by month old version).
[*]Attach all ~/.cache/ubuntuone/log/syncdaemon.log files you may have
[/LIST]
If you can, please hop on #ubuntuone on Freenode IRC. I'm normally available from Monday-Friday 13:00-21:00 UTC as joshuahoover.




The thing is, I have no idea where things went wrong. And to be honest I can't remember all my file activities over the past weeks in great detail... How detailed should this description be? 

Things might have gone wrong when I tried to sync a large video folder and had to disconnect from the internet from time to time. But again, I have no idea really.


> **joshuahoover said:**
> 
How do you know the files are not up-to-date? Is this based on your first question? 


when I log into the web interface it tells me that I'm using 3.5GB (7.1%) while the Ubuntu one folder on my computer is 19.3GB.

> **joshuahoover said:**
> 
Please run the script found here to show which files are synced on your machine: [http://launchpadlibrarian.net/36063440/u1sdstatus.py](http://launchpadlibrarian.net/36063440/u1sdstatus.py) (from a terminal session: python u1sdstatus.py)


It throws out a lot of errors like this:
```
Error: [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 635, in get_metadata
    mdobj = self.fs_manager.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 521, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/motoko/Ubuntu One/inspiration/3D/subdivisionmodeling.u1conflict/KingKONG_AV.jpg'
```



Also, I would like to apologize for the rude tone in my first post. Please don't take it as a personal attack, I know you guys are working hard on all this. I was just very frustrated by the thought of having lost some important files.

Luckily I managed to save the important files from the u1conflict copies.

---

### Post by joshuahoover on 2010-04-12
> **plaurits said:**
> The thing is, I have no idea where things went wrong. And to be honest I can't remember all my file activities over the past weeks in great detail... How detailed should this description be?

You can just try to describe the problem the best you know how and provide the log files. The more info we have, the better we can probably troubleshoot things. :)

> Things might have gone wrong when I tried to sync a large video folder and had to disconnect from the internet from time to time. But again, I have no idea really.

This is a likely culprit due to how larger transfers are handled but it's hard to say for sure. Your log files will likely tell us more.

>  when I log into the web interface it tells me that I'm using 3.5GB (7.1%) while the Ubuntu one folder on my computer is 19.3GB.

Right. Based on what you've described, it sounds like only some of the files have synchronized to the server, thus the difference between the size on the server and the size on your computer.

> It throws out a lot of errors like this:
```
Error: [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 635, in get_metadata
    mdobj = self.fs_manager.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 521, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/motoko/Ubuntu One/inspiration/3D/subdivisionmodeling.u1conflict/KingKONG_AV.jpg'
```

OK. We'll have to have one of our devs look into this further but it's likely a result of the other issues you've described/been seeing.

> Also, I would like to apologize for the rude tone in my first post. Please don't take it as a personal attack, I know you guys are working hard on all this. I was just very frustrated by the thought of having lost some important files.

No apologies necessary. I wanted to make sure you knew that we don't take potential data losses lightly and want to get to the bottom of the problems you're experiencing.

> Luckily I managed to save the important files from the u1conflict copies.

Good to hear! If the files are being marked as .u1conflict then they are not loss. It just means Ubuntu One thinks there is a conflict between the local file and the file on the server. It sounds like the syncdaemon is getting confused by partial syncs but I'm not sure.

Thank you,

Joshua

---

### Post by rednasflor on 2010-06-07
I'd like to report a (maybe) similar problem.

I have freshly installed 10.4 and I'd like to switch from dropbox to
Ubuntu One now. However, when I click on "Ubuntu One..." in the Me Menu,
nothing happens. Running u1sdstatus.py from a terminal session, I get an
error somewhat similar to the one posted by plaurits:

Error: [Failure instance: Traceback (failure with no frames): <class
'dbus.exceptions.DBusException'>:
org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with
unknown return code 1 ]

I'm happy to test further diagnostics and to provide further information
that could be helpful...

---

### Post by snahrck on 2011-01-04
I'm also having files replaced by outdated versions. This is very anoying! I have lost a day of work because of that :( 
I'm not sure how this happens but here are some log files in attachment. Some files that have been replaced:

Doutorado/ArtigoNECO/references.bib
Doutorado/ArtigoNECO/neural-modules-for-false-memory.tex

In syncdeamon.log I believe we can see the moment when "references.bib" got replaced by an outdated version:

2011-01-04 13:22:07,437 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4584bb40-fcbb-4d3c-84cf-06388504f53a ['5d618247-290a-48cd-be52-59f0f9f63385'::'c3455292-8f46-4c2a-b358-f03202ef69cb'] ''Doutorado/ArtigoNECO/references.bib'' | Calling commit_file (got AQ_DOWNLOAD_FINISHED:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'T'})
2011-01-04 13:22:07,450 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 4584bb40-fcbb-4d3c-84cf-06388504f53a ['5d618247-290a-48cd-be52-59f0f9f63385'::'c3455292-8f46-4c2a-b358-f03202ef69cb'] ''Doutorado/ArtigoNECO/references.bib'' | Called commit_file (In: T:SERVER:F)

I'm telling this because I worked on these files the day before.

There are also some exceptions related with the folder in attached files.

---

