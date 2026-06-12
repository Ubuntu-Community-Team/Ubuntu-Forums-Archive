---
title: "Ubuntu one - doesn't add my computer correctly. &lt;LOCAL MACHINE&gt;"
date: 2011-06-05
forum: Ubuntu One (CLOSED)
---

### Post by Matt Pellegrini on 2011-06-05
The devices tab under ubuntu one preferences lists only <LOCAL MACHINE> the staus at the top says disconnected, the connect button is grayed out and the reset button at the bottom right does nothing. 

Files don't sync etc but i think this is as a result of the situation described above.

I have tried on the advice of an older thread to delete the token for Ubuntu one from 'passwords and encryption keys' and then revisit Ubuntu one preferences in order to sign in again and grant my computer access but this made no difference.

Thanks

---

### Post by duanedesign on 2011-06-06
Could you please try opening a Terminal and running this command:

```
dbus-send --print-reply --dest=com.ubuntu.sso /credentials com.ubuntu.sso.ApplicationCredentials.login_to_get_credentials "string:Ubuntu One" "string:Workaround for LP:657850" int64:0
```

thank you,
duanedesign

---

### Post by Matt Pellegrini on 2011-06-06
> ```
dbus-send --print-reply --dest=com.ubuntu.sso /credentials com.ubuntu.sso.ApplicationCredentials.login_to_get_credentials "string:Ubuntu One" "string:Workaround for LP:657850" int64:0
```thank you,
duanedesign

Hopefully i did that right, here's what i got

method return sender=:1.73 -> dest=:1.120 reply_serial=2

---

### Post by duanedesign on 2011-06-06
That is the correct response. Does restarting Ubuntu One now show your credentials in the control panel?

thank you,
duanedesign

---

### Post by Matt Pellegrini on 2011-06-06
> **duanedesign said:**
> That is the correct response. Does restarting Ubuntu One now show your credentials in the control panel?

thank you,
duanedesign


Sorry, don't know what you mean here...
System>Preferences>UbubtuOne still looks like this the picture attached

In case you mean the passwords and Encryption keys window, that lists a token for Ubuntu One

---

### Post by Matt Pellegrini on 2011-06-09
Anyone? I'm keen to use Ubuntu one but this set up is taking ages.
Thanks to anyone for help

---

### Post by duanedesign on 2011-06-15
Which version of Ubuntu are you using? 10.10 Maverick, is that correct?

---

### Post by Matt Pellegrini on 2011-06-16
Yes, that's correct

---

### Post by duanedesign on 2011-06-17
Can you look in this directory ~/.cache/ubuntuone/log/ You may need to type Ctrl + h  or View > Show Hidden Files to see the .cache directory in nautilus.

First check the syncdaemon-exceptions.log and see if anything is in it. If not you will need to look in the syncdaemon.log to see if their are any clues to the failure. You can post the logs here if you would like some help deciphering what the log is telling you. Use the [ CODE ] tags to make the logs more readable. The logs do have filenames in them. If that is something you do not want to post you can email the log to  ubuntuone-support<at>canonical<dot>com along with a link to this thread so the person who receives the email will have some background on your issue.

thank you,
duanedesign

---

### Post by Matt Pellegrini on 2011-06-18
There is no 'syncdaemon-exceptions.log' the syncdaemon log is:

2011-06-12 23:22:51,657 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2011-06-12 23:22:51,864 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 2, idx_node_id: 0, shares: 1
2011-06-12 23:22:51,865 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2011-06-12 23:22:51,867 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2011-06-12 23:22:52,615 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2011-06-12 23:22:52,616 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/matt/Ubuntu One' as root dir
2011-06-12 23:22:52,616 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/matt/.local/share/ubuntuone/syncdaemon' as data dir
2011-06-12 23:22:52,616 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/matt/.local/share/ubuntuone/shares' as shares root dir
2011-06-12 23:22:52,617 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=2) ----
2011-06-12 23:22:52,618 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2011-06-12 23:22:52,618 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2011-06-12 23:22:52,637 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2011-06-12 23:22:52,650 - ubuntuone.SyncDaemon.local_rescan - INFO - processing move limbo
2011-06-12 23:22:52,668 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/matt/Ubuntu One/test'' | Calling new_local_file (got FS_FILE_CREATE:{})
2011-06-12 23:22:52,673 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 96b3ed55-7c31-4a92-8508-040e1049006b ['root'::marker:96b3ed55-7c31-4a92-8508-040e1049006b] ''Ubuntu One/test'' | Called new_local_file (In: F:NA:NA)
2011-06-12 23:22:52,676 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 96b3ed55-7c31-4a92-8508-040e1049006b ['root'::marker:96b3ed55-7c31-4a92-8508-040e1049006b] ''Ubuntu One/test'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2011-06-12 23:22:52,678 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 96b3ed55-7c31-4a92-8508-040e1049006b ['root'::marker:96b3ed55-7c31-4a92-8508-040e1049006b] ''Ubuntu One/test'' | Called calculate_hash (In: T:NONE:F)
2011-06-12 23:22:52,684 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2011-06-12 23:22:52,684 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2011-06-12 23:22:52,685 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 96b3ed55-7c31-4a92-8508-040e1049006b ['root'::marker:96b3ed55-7c31-4a92-8508-040e1049006b] ''Ubuntu One/test'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2011-06-12 23:22:52,687 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 96b3ed55-7c31-4a92-8508-040e1049006b ['root'::marker:96b3ed55-7c31-4a92-8508-040e1049006b] ''Ubuntu One/test'' | Called put_file (In: T:NONE:F)


I'm fairly sure the only filename in there in TEST which is a blank text file i used to test the process.

thanks,
Matt

---

