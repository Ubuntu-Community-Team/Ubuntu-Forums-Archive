---
title: "Ubuntu One not Autostarting"
date: 2010-04-25
forum: Ubuntu One (CLOSED)
---

### Post by belkinsa on 2010-04-25
I have Ubuntu 10.04 and when I start up the system, Ubuntu One is not starting up.  I have checked if it is, and it is.  And I think it's linked to [my other]("http://ubuntuforums.org/showthread.php?t=1461624") problem (not syncing the notes).  My problem started on Ubuntu 9.10 about five days after I fresh installed Ubuntu 9.10 and it still persists on Ubuntu 10.04 (I juts upgraded to it, not a fresh install).  How to fix this?

Thanks

---

### Post by nanonils on 2010-04-25
I have the same problem. While I've already filed a launchpad bug ([https://bugs.launchpad.net/ubuntuone-client/+bug/567194](https://bugs.launchpad.net/ubuntuone-client/+bug/567194)) it'd be great to get some suggestions by users or developers who happen to read the forums as well. I'd love to fix this sooner rather than later. 
Thanks!

Here is a copy paste from the above bug: 
After having booted up and logged in (latest updates 4/30/10 Lucid 64bit) I can see with the system monitor that both the ubuntuone-syncdaemon and -preferences start, then preferences disappears.

My problems:
- the ubuntuone folder is not synchronized but shows the names of directories (deleted a log file in order to encourage incomplete synchronization after an update about 2 weeks ago).
- after manually starting -preferences from the pull down menu it will briefly show that it is starting in the system monitor but not open a window and then disappear again
- I removed the affected desktop machine online hoping that I could add it again to start from scratch but there is no request to "add machine" anywhere
- I added the ubuntuone-beta PPA to see whether that changes behavior but it doesn't so I reverted back to the regular version

---

### Post by belkinsa on 2010-04-25
Thanks for creating a bug report.  But I have 10.04 32bit, should I report it also?

---

### Post by nanonils on 2010-04-25
Yes, that is the appropriate way of getting something fixed and also our "duty" as a beta tester. That's the power of open source software: you report and anyone with enough computer know-how can fix it immediately.

---

### Post by belkinsa on 2010-04-25
Right, I will report it.

---

### Post by nanonils on 2010-04-25
Holy smokes: 667 open bugs in ubuntuone ([https://bugs.launchpad.net/ubuntuone-client/+bugs](https://bugs.launchpad.net/ubuntuone-client/+bugs)) That will require an army already to look through. May I should just reinstall. 

I burnt the last build (4/19) and ran the live CD: no problem registering this machine and running ubuntuone preferences. Once I boot back into my presently installed 10.04 it still doesn't work (different machine ID assigned). Maybe I can change the ID manually somewhere?

---

### Post by nanonils on 2010-04-25
When I run ubuntuone-preferences in a terminal I get the message:

desktop:~$ ubuntuone-preferences
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1142, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 534, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 974, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 376, in list_devices
    token = get_access_token(self.keyring)
  File "/usr/bin/ubuntuone-preferences", line 124, in get_access_token
    'oauth-consumer-key': 'ubuntuone'})
gnomekeyring.IOError

---

### Post by nanonils on 2010-04-25
Looks like an upstream/Gnome problem.

Something is wrong with my keyring daemon ("couldn't communicate with keyring daemon" when I open Passwords and Encryption). I tried resetting this keyring without luck following [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

I reinstalled all things seahorse related and keyring but still the same problem. Seems to be related to: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/569667](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/569667)

OK - enough tinkering. Got better things to do...

---

### Post by belkinsa on 2010-04-25
[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/) <--- Link does not work.

---

### Post by nanonils on 2010-04-25
Can you try again? It does work for me now. I just clicked it after your post and all I got was a tiny smiley. You can also Google search it and pull it up in the search engines cache when the site itself is overloaded.

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

---

### Post by joshuahoover on 2010-04-27
> **nanonils said:**
> Looks like an upstream/Gnome problem.

Something is wrong with my keyring daemon ("couldn't communicate with keyring daemon" when I open Passwords and Encryption). I tried resetting this keyring without luck following [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

I reinstalled all things seahorse related and keyring but still the same problem. Seems to be related to: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/569667](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/569667)

OK - enough tinkering. Got better things to do...

Do you by any chance have auto-login turned on? If so, you may be experiencing the problem discussed in this thread: [http://ubuntuforums.org/showthread.php?t=1459804](http://ubuntuforums.org/showthread.php?t=1459804) In particular, see this comment: [http://ubuntuforums.org/showpost.php?p=9174514&postcount=7](http://ubuntuforums.org/showpost.php?p=9174514&postcount=7) 

Joshua

---

### Post by nanonils on 2010-04-27
Noooo auto-login for me. I know this problem well though because I did experience it on my eeePC 900 that I use as a Pandora jukebox in our living room's sideboard.

- I do have encryption turned on (as I do on all my Lucid machines).

- I only experienced this problem a few weeks ago after an update and only on my office computer.

If this ubuntuone problem is more of an academic question and it's not affecting anyone else I'd be happy to simply raze my HD again and start over (always ready for that as a beta-tester). Still have my most recent backup - looking at my frozen Ubuntuone folder it occurred on April 14 and I haven't created too much stuff since.

Thank you much! I know you are currently overwhelmed with all the exciting Amazon EC2 cloud business going on ([http://www.ubuntugeek.com/ubuntu-floats-12000-clouds-and-counting.html](http://www.ubuntugeek.com/ubuntu-floats-12000-clouds-and-counting.html) [http://en.wikipedia.org/wiki/Amazon_S3](http://en.wikipedia.org/wiki/Amazon_S3))!

---

### Post by belkinsa on 2010-04-27
I think mines is still on after I turned it off an hour ago.  How to change that again?

Or it could be another problem.

---

### Post by nanonils on 2010-04-28
Uh - lovely: the local Ubuntuone folder still won't sync.

I reinstalled Lucid 64bit 4/27/10 this AM and at least the ubuntu preferences are working now. I was able to add this machine with a new ID. Syncing starts but then shows "complete" after 1 minute or so but my online 1.3 GB files are not copied to my local HD. The exclamation mark remains indicating no sync and no files or file names show up.

When I move a new file into the Ubuntuone folder it does synchronize. Only the 1.3 GB online won't show up.

desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

---

### Post by belkinsa on 2010-04-28
No offense, but I give.  I will use the web one and my flashdrive at the moment.  I will wait til Ubuntu One will be better and out of beta.  Sorry.

---

### Post by joshuahoover on 2010-04-29
> **nanonils said:**
> Uh - lovely: the local Ubuntuone folder still won't sync.

I reinstalled Lucid 64bit 4/27/10 this AM and at least the ubuntu preferences are working now. I was able to add this machine with a new ID. Syncing starts but then shows "complete" after 1 minute or so but my online 1.3 GB files are not copied to my local HD. The exclamation mark remains indicating no sync and no files or file names show up.

When I move a new file into the Ubuntuone folder it does synchronize. Only the 1.3 GB online won't show up.

desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

You mentioned that you added the machine with a new ID. I'm assuming you added it to the same Ubuntu One account and not a new one, right? So when you go to [https://one.ubuntu.com/](https://one.ubuntu.com/) you see your 1.3 GB of data there? 

Also, you mentioned "The exclamation mark remains indicating no sync and no files or file  names show up." Where do you see the exclamation mark? On the file emblems? You shouldn't see that in the task bar with 10.04 (Lucid).

We made some significant improvements on the server side late yesterday. Can you disconnect and reconnect? From a terminal session: 

u1sdtool -d
u1sdtool -c

Thank you,

Joshua

---

### Post by nanonils on 2010-04-29
> **joshuahoover said:**
> You mentioned that you added the machine with a new ID. I'm assuming you added it to the same Ubuntu One account and not a new one, right? 

Yes, that's exactly what I did.

> **joshuahoover said:**
> So when you go to [https://one.ubuntu.com/](https://one.ubuntu.com/) you see your 1.3 GB of data there? 

I was scared for a second when I read your question but it all seems to be nicely sitting online. Just pulled some Vista fonts from there and installed them...

> **joshuahoover said:**
> Also, you mentioned "The exclamation mark remains indicating no sync and no files or file  names show up." Where do you see the exclamation mark? On the file emblems? You shouldn't see that in the task bar with 10.04 (Lucid).

Yes, they were on the file emblems. As of about 2 hours ago they changed to green check marks but the folders are empty. There are a few subfolders with an exclamation mark remaining. 

> **joshuahoover said:**
> We made some significant improvements on the server side late yesterday. Can you disconnect and reconnect? From a terminal session: 

u1sdtool -d
u1sdtool -c

Thank you,

Joshua

Nice terminal command. I think I have a problem reconnecting with the command line tool. However, I can get a rescan by opening the GUI ubuntuone preferences (last copy paste in the following):

desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

desktop:~$ u1sdtool -d
then: desktop:~$ u1sdtool -s
State: WAITING
    connection: Not User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

desktop:~$ u1sdtool -c
then: desktop:~$ u1sdtool -s
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

after opening GUI preferences:
desktop:~$ u1sdtool -s
State: SERVER_RESCAN
    connection: With User With Network
    description: doing server rescan
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

Unfortunately, the empty folders remain.

---

### Post by nanonils on 2010-04-30
After rebooting this AM all folders are empty but have exclamation marks on them. Ubuntuone preferences seems unable to get a connection, command line won't connect either:

"desktop:~$ u1sdtool -s
Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."


The other curious observation is that after selected to sync a single file in my Documents folder the entire folder is suddenly selected to sync and I can't stop it (option grayed out).
The single file has long been moved to the Ubuntuone folder on my disk and is currently in a non-synchronized state.

My hard drive is spinning non-stop and when I kill Ubuntuone-syncdaemon it comes right back.

Guess there is a reason why even Apple licensed ActiveSync from Microsoft: it's hard to do.

---

### Post by joshuahoover on 2010-04-30
> **nanonils said:**
> After rebooting this AM all folders are empty but have exclamation marks on them. Ubuntuone preferences seems unable to get a connection, command line won't connect either:

"desktop:~$ u1sdtool -s
Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Our servers are getting hammered today. No excuses. We're trying to remedy this. Something you might want to try to fix this error (in a terminal session):

killall ubuntuone-login ubuntuone-preferences ubuntuone-syncdaemon
u1sdtool -c
u1sdtool -s

> 
The other curious observation is that after selected to sync a single file in my Documents folder the entire folder is suddenly selected to sync and I can't stop it (option grayed out).
The single file has long been moved to the Ubuntuone folder on my disk and is currently in a non-synchronized state.

My hard drive is spinning non-stop and when I kill Ubuntuone-syncdaemon it comes right back.I'm assuming you meant that you selected to sync a folder and not a file. Right now you can't synchronize a single file, only folders. If you selected a folder to synchronize, it should only attempt to synchronize that one folder. If the folder has a lot of data then it can take a while to process. If you want to stop this and can't do it via right-clicking on the folder and selecting "Stop synchronizing on Ubuntu One", try following this FAQ:

[https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20%7E/Ubuntu%20One%20folder") 

> Guess there is a reason why even Apple licensed ActiveSync from Microsoft: it's hard to do.Heh. I think they did that to get native sync support with Microsoft Exchange to appeal to more "enterprise" customers. But, yes, sync can be difficult to do and especially at Internet scale. :)

Thank you,

Joshua

---

### Post by toupeiro on 2010-04-30
I am having a slightly different issue.  I can get ubuntu-one to seemingly work on gnome, but not kde.

```
u1sdtool -sState: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
```

```
 ubuntuone-launch 
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
```

```
ps -ef | grep ubuntuone
toupeiro 25562     1  0 19:02 ?        00:00:01 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
toupeiro 26133 25360  0 19:10 pts/1    00:00:00 grep ubuntuone

```

---

### Post by nanonils on 2010-05-03
Hi Joshua,

Unfortunately, none of your suggestions are working (see below).

I really appreciate your effort in helping people here in the forum. Thank you very much. Great that you are getting so many new users (too bad the volume was a suprise and is now overrunning your servers). 

> **joshuahoover said:**
> 
killall ubuntuone-login ubuntuone-preferences ubuntuone-syncdaemon
u1sdtool -c
u1sdtool -s


Odd, despite following your steps I'm still getting the error message:

desktop:~$ u1sdtool -c

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


> **joshuahoover said:**
>  I'm assuming you meant that you selected to sync a folder and not a file. Right now you can't synchronize a single file, only folders. If you selected a folder to synchronize, it should only attempt to synchronize that one folder. If the folder has a lot of data then it can take a while to process. If you want to stop this and can't do it via right-clicking on the folder and selecting "Stop synchronizing on Ubuntu One", try following this FAQ:

[https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20%7E/Ubuntu%20One%20folder") 


No, I selected only one file in "Documents" to synchronize but then moved it to the Ubuntuone folder. 
When I follow the instructions above, I get another error message and am unable to unsubscribe my several GB "Documents".  

desktop:~$ u1sdtool --unsubscribe-folder=f0024d75-3f19-454a-a823-e698ecba440a

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 307, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 354, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 123, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 763, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by nanonils on 2010-05-03
Update: for the first time I was just able to restart syncing with the Ubuntuone Preferences (GUI). The button was previously non-responsive. Unfortunately, it is showing "online: False"
desktop:~$ u1sdtool -c
desktop:~$ u1sdtool -s
State: SERVER_RESCAN
    connection: With User With Network
    description: doing server rescan
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_METADATA

---

### Post by nanonils on 2010-05-03
I guess I simply need more patience: 

desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

---

### Post by joshuahoover on 2010-05-03
> **nanonils said:**
> Hi Joshua,

Unfortunately, none of your suggestions are working (see below).

I really appreciate your effort in helping people here in the forum. Thank you very much. Great that you are getting so many new users (too bad the volume was a suprise and is now overrunning your servers). 

Thank you for your support and patience! Trust me, we don't want to have a service that isn't working properly and are doing everything we can to get things working optimally ASAP.

> 
Odd, despite following your steps I'm still getting the error message:

desktop:~$ u1sdtool -c

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.




No, I selected only one file in "Documents" to synchronize but then moved it to the Ubuntuone folder. 
When I follow the instructions above, I get another error message and am unable to unsubscribe my several GB "Documents".  

desktop:~$ u1sdtool --unsubscribe-folder=f0024d75-3f19-454a-a823-e698ecba440a

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 307, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 354, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 123, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 763, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

OK, I know in your last post you showed it's now connected and online but I think there's a bug in unsubscribing folders from syncing with the service, as it seems like the Ubuntu One syncdaemon may be too busy cranking away on syncing that it doesn't respond to the unsubscribe request and even when it does, it doesn't appear to unsubscribe the folder and stop syncing as you would expect it to. I'm going to try to reproduce this behavior and file a bug with debug logs our developers can use to help pinpoint the root cause of the problem. If you can try running the unsubscribe command again, please do. 

You can get updates on the system and our progress on fixing things in two spots:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Again, my apologies for the inconvenience and thank you for your patience.

Joshua

---

### Post by nanonils on 2010-05-04
Update: first 100 MB of my 1.3 GB ubuntuone files have trickled through overnight back onto my recent Lucid install after I scraped Karmic. 

Too bad the connection always terminates when idle. I'm wondering why there even could be a server overload. I thought the idea behind the "elastic cloud" was to allow to immediately "burst" elastically to accommodate larger demands using Amazon's server farm without having to do it yourself.

Reason I have to suck my Ubuntuone files back onto my computer is that I've started to do clean installs after coming across this CNet writer's site: [http://sites.google.com/site/easylinuxtipsproject/upgrade]("http://sites.google.com/site/easylinuxtipsproject/upgrade") 
Clean installs really are much faster and fix self inflicted system setting screw-ups. E.g. For the the last 2 Ubuntu releases I never got my microphone to work for voice recognition-dictating in Win7 via Virtualbox and hopelessly ruined all audio-in. I also had problems with Grub that are now gone. It was useful to being forced to backup my documents on a separate drive. Always was too lazy for that.

---

### Post by joshuahoover on 2010-05-04
> **nanonils said:**
> Update: first 100 MB of my 1.3 GB ubuntuone files have trickled through overnight back onto my recent Lucid install after I scraped Karmic. 

Too bad the connection always terminates when idle.

Hmmm... this shouldn't happen. If it continues, can you please file a bug by doing the following:

1. File a bug here: [https://bugs.launchpad.net/ubuntuone-client/+filebug](https://bugs.launchpad.net/ubuntuone-client/+filebug)
2. Run the following from a terminal session:  apport-collect -p ubuntuone-client ######
(Replace ###### with the bug number from the first step)

> I'm wondering why there even could be a server overload. I thought the idea behind the "elastic cloud" was to allow to immediately "burst" elastically to accommodate larger demands using Amazon's server farm without having to do it yourself.

In theory, yes. In practice, no. There are lots of "gotchas" along the way that make elastic scaling a difficult nirvana to reach. We're doing our best to get there but we're still a ways away.

Thank you,

Joshua

---

### Post by nanonils on 2010-05-05
Excellent! Syncing is now flawless and instant, my 1.3 GB are all back on my local HD. 
Congrats Ubuntuone-team for surviving the onslaught and thank you Joshua for your frequent advice and updates!

---

### Post by belkinsa on 2010-05-05
> **nanonils said:**
> Excellent! Syncing is now flawless and instant, my 1.3 GB are all back on my local HD. 
Congrats Ubuntuone-team for surviving the onslaught and thank you Joshua for your frequent advice and updates!

So, it's fixed?  W00t!

---

### Post by nanonils on 2010-05-05
Looks like there are bottlenecks. Right now a new file doesn't want to make it through...

---

### Post by joshuahoover on 2010-05-05
> **nanonils said:**
> Looks like there are bottlenecks. Right now a new file doesn't want to make it through...

Right, we're still making adjustments on the server side to perform better and stabilize. We're getting closer but still seeing fluctuations in performance.

Joshua

---

### Post by duanedesign on 2010-06-17
> **nanonils said:**
> When I run ubuntuone-preferences in a terminal I get the message:

desktop:~$ ubuntuone-preferences
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1142, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 534, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 974, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 376, in list_devices
    token = get_access_token(self.keyring)
  File "/usr/bin/ubuntuone-preferences", line 124, in get_access_token
    'oauth-consumer-key': 'ubuntuone'})
gnomekeyring.IOError

If you receive this error run the following command:

```
gnome-keyring-daemon; ubuntuone-preferences
```

---

