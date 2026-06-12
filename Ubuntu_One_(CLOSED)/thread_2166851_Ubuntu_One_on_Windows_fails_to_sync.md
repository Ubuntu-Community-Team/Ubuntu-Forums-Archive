---
title: "Ubuntu One on Windows fails to sync"
date: 2013-08-11
forum: Ubuntu One (CLOSED)
---

### Post by tagMacher on 2013-08-11
Ubuntu One for Windows (ver 4.2.0 on Win 7 Prof SP1 64-bit) stopped working a few days ago. It looked initially like a network issue and I checked firewall etc. I am able to browse other sites and also Ubuntu One on the browser (am posting this from the same machine). This was with version 4.0.0. I have since upgraded to 4.2 and still have the same problem. Right-click on U1 icon in the system tray shows the usual popup menu except that the top two entries are "Loading" and "Please wait". Selecting "Open Ubuntu One" opens the client window which spends a long time with "Getting information, please wait...", gets the account information, free space etc (top panel) and after a long further time, times out with no folder list in the bottom pane. I ran u1sdtool --status and this is what I get:

-----
C:\Program Files (x86)\ubuntuone\dist>u1sdtool --status


Oops, an error ocurred:
('Could not connect to the syncdaemon ipc.', ActivationTimeoutError())
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
  File "twisted\internet\defer.pyc", line 422, in errback


  File "twisted\internet\defer.pyc", line 489, in _startRunCallbacks


  File "twisted\internet\defer.pyc", line 576, in _runCallbacks


  File "twisted\internet\defer.pyc", line 1127, in gotResult


--- <exception caught here> ---
  File "twisted\internet\defer.pyc", line 1069, in _inlineCallbacks


  File "twisted\python\failure.pyc", line 389, in throwExceptionIntoGenerator


  File "ubuntuone\platform\tools\perspective_broker.pyc", line 136, in call_afte
r_connection_inner


  File "twisted\internet\defer.pyc", line 1069, in _inlineCallbacks


  File "twisted\python\failure.pyc", line 389, in throwExceptionIntoGenerator


  File "ubuntuone\platform\ipc\ipc_client.pyc", line 794, in connect


ubuntuone.platform.ipc.ipc_client.SyncDaemonClientConnectionError: ('Could not c
onnect to the syncdaemon ipc.', ActivationTimeoutError())


C:\Program Files (x86)\ubuntuone\dist>
----

I have checked my anti-virus (no changes recently) and U1 continues to be a trusted application. 
Services list in Computer Management shows no service related to U1 syncdaemon - is this normal?
Under running processes, the following are present:
ubuntuone-control-panel-qt.exe *32, Mem ~37MB
9 processes of ubuntuone-syncdaemon.exe *32, Mem ~25MB each
ubuntu-sso-login *32, Mem ~19MB.

What can I do to troubleshoot
 and solve the problem?

---

### Post by eMKi on 2013-09-09
Same problem here using Windows XP and Ubuntu One 4.2.

---

