---
title: "Ubuntu One stuck at File Sync Starting"
date: 2014-02-16
forum: Ubuntu One (CLOSED)
---

### Post by Lars_Hansen on 2014-02-16
I have been running ubuntu on my home laptop for the last five years or so. I recently setup a new ubuntu desktop at my office and wanted to have it synced with the laptop at home. I purchased 40 GB of storage on UbuntuOne and synced 35 GB of data from my home laptop. I then synced my office desktop and all the files were download as they should be. I was really quite impressed at the simplicity of this operation. At this point, whenever I save a file on the desktop, I get a notification that the file has been uploaded to Ubuntu One. All seems good. 

However, I'm now having trouble syncing my laptop. When starting up the laptop and then opening the Ubuntu One gui, Ubuntu One sits at "File sync starting..." until I get impatient (I've waited as long as a couple of days). Ouput from u1sdtool is as follows:

u1sdtool --status

State: LOCAL_RESCAN
    connection: With User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING


u1sdtool --current-transfers

Current uploads: 0
Current downloads: 0


I am running Ubuntu 13.10 and the latest version of Ubuntu One on both machines.

Most previous forum posts seem to suggest that this is a bug that has been resolved in an earlier version of Ubuntu One. I have tried disconnecting and restarting UbuntuOne via u1sdtool with no change in the result.

Importantly, I have have completely removed and reinstalled Ubuntu One from the laptop, and this DOES resolve the issue. Upon reinstallation, Ubuntu One completes the syncing of my laptop (takes 5 hours or so). However, as soon as I restart the laptop, UbutnuOne hangs at "File sync starting..." as before. I've gone through this cycle three times at this point. 

Any help would be greatly appreciated.

---

### Post by tuuk on 2014-02-20
Since some time after Tuesday (18/2/14), I have been having trouble with Ubuntu One as well. In my case, it just stopped working. In particular, UbuntuOne clients I have on the two Ubuntu machines I use cannot connect to the server.  It tries to connect and keeps displaying "File sync starting" for a while. And, eventually, it gets disconnected. The sync client reports:

> 
~$ u1sdtool --status
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE


Rebooting, stopping and restarting the client do not help.

Is there a general problem with U1?

tuuk

---

### Post by tuuk on 2014-02-21
Now, my U1 client is connected but stuck at syncing.

> 
~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING


The GUI also shows "File Sync in progress..."

As before, stopping and restarting the client does not help.

Any ideas?

---

### Post by ElmoOnLSD on 2014-02-21
UbuntuOne has been spotty for me as well since yesterday. I submitted a support request informing them of the issue, but have yet to receive a response.

---

### Post by Shiba on 2014-02-21
Same for me. A couple of days ago it was totally off, today is just very slow.

---

### Post by Roo8choo on 2014-02-21
Same problem here, I think there something wrong with uploading. If I download a file from the Ubuntu One server it works but its really slow. Uploading doesn't work on my system. Unlinked my computers and added them again, even did a full reinstall but it didn't work. I'm using Ubuntu 12.04.4 LTS.

A user created a [bug]("https://bugs.launchpad.net/ubuntuone-client/+bug/1282759") report on launchpad.

---

### Post by Salva666 on 2014-02-23
Same here. I also submit resquest to ubuntu support and also no answer.

---

### Post by retrogarde on 2014-02-23
I've got the same problem. Ubuntu One starts syncing, interrupts almost immediately, and resumes syncing only for a few seconds (if at all) before the process is aborted once again. Yet, this issue only shows up on my desktop (os: lubuntu 13.10), while my notebook (os: ubuntu 12.04) remains unaffected.

---

### Post by robertmf on 2014-02-23
Ubuntu 12.04 LTS 
**Backup failed** with status code 502
:(

[COLOR="#0000FF"][SOLVED]  After 3 tries, U1 sync'd [/COLOR]

---

### Post by Irihapeti on 2014-02-24
Ubuntu One seems to be working properly again on both my machines (Xubuntu 14.04). You might need to reboot or restart the syncdaemon before it will behave properly.

---

### Post by Roo8choo on 2014-02-24
Here too, uploading and downloading files with Ubuntu One seems to be working again. ;)

---

### Post by paganchef on 2014-02-24
my phone is syncing and up loading but my deskstop xubuntu 12.04 will not sync keep: getting file sync error auth failed. 
i have reinstalled the certificates shut down comp and rebooted but still have no conection any one help pls

---

### Post by tuuk on 2014-02-24
Following the instructions in the following page solved my "auhentication" problem in Ubuntu One.

[https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/](https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/)

Basically, start seahorse and delete all Ubuntu One related stored passwords (perhaps not all is needed, but I deleted all). Reconnect. You will be asked for usename/password.

Hopefully, this helps others who are having problems.

It would have been good to know what caused the problem, because I have not had made any changes when the problem had occurred.

Cheers.
tuuk

---

