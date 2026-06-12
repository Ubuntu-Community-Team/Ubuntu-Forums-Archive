---
title: "ubuntu syncing problem"
date: 2011-08-22
forum: Ubuntu One (CLOSED)
---

### Post by shubham1 on 2011-08-22
there is endless file sync it took years to sync one 30mb file and still not uploaded.even after uploading form online.i want a plugin or software that can show how much is uploaded and time left also curently i removed and again installed it first it opens then a again open my system it is not opening.

---

### Post by shubham1 on 2011-08-23
no one

---

### Post by duanedesign on 2011-08-23
Their is a thread I stuck about [getting more information from Ubuntu One]("http://ubuntuforums.org/showthread.php?t=1594301").

Can you open a Terminal and run the following command, posting the output:

```
u1sdtool -s
```

If you get state:Ready you need to connect. Run the following command, wait a couple minutes and run u1sdtool -s again.

```
u1sdtool -c

```
```
u1sdtool -s
```

---

### Post by shubham1 on 2011-08-24
Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 33, in <module>
    from ubuntuone.platform.linux.tools import (
ImportError: No module named platform.linux.tools

---

### Post by shubham1 on 2011-08-24
u1sdtool -c 
 File "/usr/bin/u1sdtool", line 33, in <module>
    from ubuntuone.platform.linux.tools import (
ImportError: No module named platform.linux.tools

---

### Post by shubham1 on 2011-08-24
Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 33, in <module>
    from ubuntuone.platform.linux.tools import (
ImportError: No module named platform.linux.tools

---

### Post by shubham1 on 2011-08-25
i have tried to reinstall ubuntu one many times still it does not opens.
any help!

---

### Post by Luwe on 2011-08-25
I'm having the same problem since two days. At first, Ubuntu one was very slow or didn't connect at all anymore, but now it gives me this error:

> Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 33, in <module>
    from ubuntuone.platform.linux.tools import (
ImportError: No module named platform.linux.toolsI have the latest version, Ubuntu One 1.6.2

---

### Post by shubham1 on 2011-08-26
> **Luwe said:**
> I'm having the same problem since two days. At first, Ubuntu one was very slow or didn't connect at all anymore, but now it gives me this error:

I have the latest version, Ubuntu One 1.6.2
did ubuntu one uploaded any file before the probelm.

---

### Post by apacketofsweets on 2011-08-26
Have you tried turning it off and back on again? Seriously.

---

### Post by shubham1 on 2011-08-26
> **apacketofsweets said:**
> Have you tried turning it off and back on again? Seriously.
yes many times

---

### Post by Remi78 on 2011-08-26
For a while i was happy with Ubuntu One. However now i have issues, ubuntu one keeps connecting and disconnecting. Using u1sdtool shows that the "description field" flips continuously from checking protocol version to wating before try connecting again.

I am using Ubuntu 10.04 and performing the suggested updates.

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: CHECK_VERSION
    connection: With User With Network
    description: checking protocol version
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

---

### Post by shubham1 on 2011-08-27
> **Remi78 said:**
> For a while i was happy with Ubuntu One. However now i have issues, ubuntu one keeps connecting and disconnecting. Using u1sdtool shows that the "description field" flips continuously from checking protocol version to wating before try connecting again.

I am using Ubuntu 10.04 and performing the suggested updates.

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: CHECK_VERSION
    connection: With User With Network
    description: checking protocol version
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH
so what is the solution.

---

### Post by Remi78 on 2011-08-27
Sorry if i wasn't clear
I've got a syncing problem with ubuntu one and no solution yet!

---

### Post by shubham1 on 2011-08-28
my also not working but i have reintsalled the ubuntu one software many itmes but it is bnot opening.
my net is coming horrible with 1mbps.

---

### Post by Mud.Knee.Havoc on 2011-10-23
> **Remi78 said:**
> For a while i was happy with Ubuntu One. However now i have issues, ubuntu one keeps connecting and disconnecting. Using u1sdtool shows that the "description field" flips continuously from checking protocol version to wating before try connecting again.

I am using Ubuntu 10.04 and performing the suggested updates.

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: CHECK_VERSION
    connection: With User With Network
    description: checking protocol version
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

remi@AsusX58Le:~/Ubuntu One$ u1sdtool -s
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

I'm having this same problem on 11.10.  I've spent about four hours now trying to get it working.  Of course, I put the files onto Dropbox and had everything synced within about 2 minutes, but I just never learn my lesson. :)

I can't find any solutions on the bug tracker.  Anybody?

---

### Post by shubham1 on 2011-10-24
> **Mud.Knee.Havoc said:**
> I'm having this same problem on 11.10.  I've spent about four hours now trying to get it working.  Of course, I put the files onto Dropbox and had everything synced within about 2 minutes, but I just never learn my lesson. :)

I can't find any solutions on the bug tracker.  Anybody?
i also cant upload to ubuntu on i also use drop box and it works

---

### Post by theSshow on 2011-10-26
Sorry, I posted this on a different thread ([http://ubuntuforums.org/showthread.php?t=1402888&page=2](http://ubuntuforums.org/showthread.php?t=1402888&page=2)), but perhaps this thread is more appropriate...

Don't know if anyone is still experiencing problems, but when I try to upload a file via the client on 11.10 it seems to be taking forever.

The command line seems to indicate that the file has finished uploading: 
```
$ u1sdtool --current-transfers
Current uploads:
  path: /home/XXX/Ubuntu One/XXX.zip
    deflated size: 41745048
    bytes written: 41745048
Current downloads: 0

```

But the Ubuntu One control panel still says "File Sync in progress...".  Moreover, the file is not there when logging in to Ubuntu One via the browser.  I've been waiting for over an hour now.

Man, I want to love Ubuntu One, but it seems like there are a lot of problems with it; in my experience, even the "native" client for the Ubuntu OS can't handle syncs.

---

### Post by shubham1 on 2011-10-26
> **theSshow said:**
> Sorry, I posted this on a different thread ([http://ubuntuforums.org/showthread.php?t=1402888&page=2](http://ubuntuforums.org/showthread.php?t=1402888&page=2)), but perhaps this thread is more appropriate...

Don't know if anyone is still experiencing problems, but when I try to upload a file via the client on 11.10 it seems to be taking forever.

The command line seems to indicate that the file has finished uploading: 
```
$ u1sdtool --current-transfers
Current uploads:
  path: /home/XXX/Ubuntu One/XXX.zip
    deflated size: 41745048
    bytes written: 41745048
Current downloads: 0

```

But the Ubuntu One control panel still says "File Sync in progress...".  Moreover, the file is not there when logging in to Ubuntu One via the browser.  I've been waiting for over an hour now.

Man, I want to love Ubuntu One, but it seems like there are a lot of problems with it; in my experience, even the "native" client for the Ubuntu OS can't handle syncs.
yes my 30mb file was uploading for 60 days and still it was npt uploaded
even when the system was running 2 hrs a day

---

