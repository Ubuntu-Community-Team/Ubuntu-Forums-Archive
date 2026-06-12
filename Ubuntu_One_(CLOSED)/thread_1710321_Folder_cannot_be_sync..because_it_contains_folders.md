---
title: "Folder cannot be sync..because it contains folders"
date: 2011-03-19
forum: Ubuntu One (CLOSED)
---

### Post by mickcalcara on 2011-03-19
Hi, I am getting the following error when I am trying to sync a folder.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186579&stc=1&d=1300566088[/IMG]
 I was having problems and deleted several files from this folder earlier. Now I receive that message and cannot sync. There are no files in this folder so I am unclear by the message  ( as  seen in screenshot )"The folder cannot be synchronized because it contains one or mored folders that are already synchronized" 

When I go online to my ubuntu one account, I have 0 back up files but it still says I am using 119 megs. 

I am using Maverick. 

Can anyone help?

thanks!

---

### Post by duanedesign on 2011-03-21
could you please post the output of the command:

```
u1sdtool --list-folders
```

---

### Post by mtphr on 2011-05-22
hi.
i'm having the same problem with my ~/Documents folder.
here is the output of the u1sdtool folder :

```
marvin@marvin:~$ u1sdtool --list-folders
Folder list:
  id=f88a784c-bd9d-4f8a-b34b-dd9b9acc57ae subscribed=True path=/home/marvin/Documents
```

any suggestions?

---

### Post by duanedesign on 2011-05-23
The command *u1sdtool --list-folders* lists all User Defined Folders you have synced with Ubuntu One. So you can not sync a folder in your ~/Documents directory because that directory would already be synced by the fact that is is in a folder that is listed to be synced.

Please let me know if I have answered your question or if I am misunderstanding what your issue is.

thank you,
duanedesign

---

### Post by mtphr on 2011-05-23
that's right, ofc i can't sync a folder "in ~/Documents" but the problem is, "~/Documents itself is not being synched anymore"
and i don't know why? like i said, i get the error at the title.
here's the screenshot.

[IMG]http://i56.tinypic.com/2ep53zt.png[/IMG]

---

### Post by duanedesign on 2011-05-24
That message is confusing and I believe their is a bug filed on that issue. Let see if we can figure out why your ~/Documents folder is not syncing. Can you check to see if anything is in the following file:

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

You may need to View --> Show hidden Files (ctrl + h) to see the .cache folder in Nautilus.

respectfully,
duanedesign

---

### Post by mtphr on 2011-05-24
thanks for the replies btw.

interestingly, there's no exception log file in the directory.

```
marvin@marvin:~$ ls .cache/ubuntuone/log/
syncdaemon.log                      syncdaemon.log.2011-05-22_19-49-11  syncdaemon.log.2011-05-23_19-03-36  u1-prefs.log
syncdaemon.log.2011-05-22_12-23-48  syncdaemon.log.2011-05-23_13-21-37  syncdaemon.log.2011-05-24_11-29-39

```

and here's the last lines of the syncdaemon.log if needed.

```
marvin@marvin:~$ tail -n5 .cache/ubuntuone/log/syncdaemon.log
2011-05-24 17:26:19,083 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=27691 miss=2149) ----
2011-05-24 17:28:19,083 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=27691 miss=2149) ----
2011-05-24 17:30:19,083 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=27691 miss=2149) ----
2011-05-24 17:32:19,083 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=27691 miss=2149) ----
2011-05-24 17:34:19,083 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=27691 miss=2149) ----

```

---

### Post by duanedesign on 2011-05-26
It looks like from the syncdaemon.log things should be syncing for you. Could you try creating a test document in your Documents folder and seeing if it gets synced. You can create a blank document with the following command ran in the Terminal.

touch /home/marvin/Documents/testfile.txt

---

### Post by mtphr on 2011-05-26
it's interesting that it DOES actually sync.
so, why the error message then? why say it can't sync?
you think it's a bug?

---

### Post by duanedesign on 2011-06-02
Yes, I believe it is just a bug. I have seen a bug filed on this issue. If I come across it again I will post it here.

thank you,
duanedesign

---

