---
title: "Purge unsynced files from Ubuntu One web account"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by Jim Danner on 2010-05-03
After several settings changes and (failed) troubleshooting steps, I would like to empty my online Ubuntu One storage. It contains many files, but none have actually been uploaded: they show in gray font with the label "uploading". The folders have a "More" link next to them, but that only reveals a "Share folder" option and no "Delete".

How do I empty the online storage when I've got these untouchable items? By the way, they aren't really uploading; after 3 days I still have "0 bytes Used (0.0%)".

---

### Post by laoshi on 2010-05-03
I'll second that. I have the same problem, and have tried to ask for a solution through lp-question [https://answers.launchpad.net/ubuntuone-client/+question/108995](https://answers.launchpad.net/ubuntuone-client/+question/108995)
but as yet there is no answer.
It seems that there is an item in the list that blocks the entire synchronization process - it is not simply ignored.
A couple of bugs have been filed that seem to point to a problem with conversion of ascii-characters in filenames (e.g. #515920) but as far as I know no solution has been provided.

So I, too, would appreciate some hints as to make sync'ing work again

---

### Post by elkikin on 2010-05-03
I have the same problem. There are several files that show up in the web  interface that I tried to upload back in 2009 I think. I have since stopped using U1, until now with Lucid. I don't even have a ~/.conkyrc anymore, but it's still there, it seems: "uploading". I can't delete any of them, neither the folders ~/.mozilla and ~/Imagens/fotos, which I'm no longer syncing...

EDIT: I tried everything, including the --unsubscribe-folder flag, to stop syncing those two folders, but they still show up in the output of "u1sdtool --list-folders":

 [B] id=484598df-2e91-4b6a-9e69-170859b1de21 subscribed= path=/home/bruno/Imagens/fotos
  id=34bde42f-70c7-42d5-8ecf-548819ea5799 subscribed= path=/home/bruno/.mozilla[/B]
  id=3c3962ba-5171-4c41-be7e-a2f7a0bef105 subscribed=True path=/home/bruno/.ubuntuone/Purchased from Ubuntu One

Still, it seems that at least the client stays idle, and isn't trying to sync them. In Nautilus the icons of those folders are back to normal, with no hint of U1-related activity. I even have the option to "Sync using ubuntu one" those folders in Nautilus context menu.

---

### Post by Jim Danner on 2010-05-03
> **elkikin said:**
> I have the same problem. There are several files that show up in the web  interface that I tried to upload back in 2009 I think. I have since stopped using U1, until now with Lucid. I don't even have a ~/.conkyrc anymore, but it's still there, it seems: "uploading". I can't delete any of them, neither the folders ~/.mozilla and ~/Imagens/fotos, which I'm no longer syncing...That looks like the same problem I have. However, I am not looking for a 'local' solution (in the sense of issuing some commands/making some changes in Ubuntu). The problem seems to be on the server, so I'd hope there is a solution on the server. The web interface doesn't seem to have that, though...

---

### Post by joshuahoover on 2010-05-03
> **elkikin said:**
> I have the same problem. There are several files that show up in the web  interface that I tried to upload back in 2009 I think. I have since stopped using U1, until now with Lucid. I don't even have a ~/.conkyrc anymore, but it's still there, it seems: "uploading". I can't delete any of them, neither the folders ~/.mozilla and ~/Imagens/fotos, which I'm no longer syncing...

EDIT: I tried everything, including the --unsubscribe-folder flag, to stop syncing those two folders, but they still show up in the output of "u1sdtool --list-folders":

 [B] id=484598df-2e91-4b6a-9e69-170859b1de21 subscribed= path=/home/bruno/Imagens/fotos
  id=34bde42f-70c7-42d5-8ecf-548819ea5799 subscribed= path=/home/bruno/.mozilla[/B]
  id=3c3962ba-5171-4c41-be7e-a2f7a0bef105 subscribed=True path=/home/bruno/.ubuntuone/Purchased from Ubuntu One

Still, it seems that at least the client stays idle, and isn't trying to sync them. In Nautilus the icons of those folders are back to normal, with no hint of U1-related activity. I even have the option to "Sync using ubuntu one" those folders in Nautilus context menu.

The problem you and others are seeing in the web UI is a result of the problems we're experiencing with the spike in new users and overall use of the system right now. We're working on fixing this. I'm working with the developers on figuring out why folders appear to still be attempting to synchronize after they've been "unsubscribed". This is a bug, as we shouldn't attempt to sync folders after they've been unsubscribed from Ubuntu One. I'll be filing a bug report shortly on this and providing debug logs so the devs can look into this closer.

There are two places to look at to see how things are running as we furiously work on fixing the core issues:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

My apologies for the inconvenience the current state of the service is causing and thank you for your patience.

Thank you,

Joshua

---

### Post by laoshi on 2010-05-04
Your efforts are greatly appreciated. I seems like you have solved some major issues. My files are merrily sync'ing now after days of no-go - the ascii-bug does not have any influence anymore - and the queued files are uploading as expected.

---

### Post by laoshi on 2010-05-04
Well, I might have been a little optimistic, after all. 
Having added new folders to sync, again a warning pops up in
u1sdtool --waiting-metadata:

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Python.UnicodeEncodeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 204, in waiting_metadata
    waiting_metadata.append(str(cmd))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1442, in __str__
    for attr in str_attrs]
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe6' in position 2: ordinal not in range(128)

And consequently all uploads run to a halt.

I have checked filenames using the utf8-filename-check.py script -and it reports that no invalid filenames are found.

So maybe I need to know how to purge the unsynced files after all.

---

### Post by joshuahoover on 2010-05-04
> **laoshi said:**
> Well, I might have been a little optimistic, after all. 
Having added new folders to sync, again a warning pops up in
u1sdtool --waiting-metadata:

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Python.UnicodeEncodeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 204, in waiting_metadata
    waiting_metadata.append(str(cmd))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1442, in __str__
    for attr in str_attrs]
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe6' in position 2: ordinal not in range(128)

And consequently all uploads run to a halt.

I have checked filenames using the utf8-filename-check.py script -and it reports that no invalid filenames are found.

So maybe I need to know how to purge the unsynced files after all.

Actually, the error you got is because of a bug in the u1sdtool not handling utf8 valid characters properly: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/561638](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/561638)

You should be able to sync files, as this error should have no impact on syncing. I'm guessing you've run into another problem. If you could file a bug following these instructions it would be helpful so we can see what is causing this problem:

[LIST=1]
[*]File a new bug report at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)
[*]Run the following command in a terminal session: apport-collect -p ubuntuone-client ######
(Replace ###### with the bug number from step 1)
[*]Be sure to attach ~/.cache/ubuntuone/syncdaemon.log to the bug report if the apport-collect command does not attach it
[/LIST]
Thank you,

Joshua

---

### Post by laoshi on 2010-05-05
This is getting a little weird. Last night when the ascii-error returned I also encountered other errors, e.g. was not able to unsubscribe a folder.

This morning as I was preparing to gather info for a bug report sync'ing has suddenly resumed.

So this leads me to believe that the issue must be on the server side, as the client has not been updated.

Btw I am not able to log in to bugs.launchpad.net - I encounter what looks like a loop on login - but can log in to my launchpad account.

---

### Post by joshuahoover on 2010-05-05
> **laoshi said:**
> This is getting a little weird. Last night when the ascii-error returned I also encountered other errors, e.g. was not able to unsubscribe a folder.

This morning as I was preparing to gather info for a bug report sync'ing has suddenly resumed.

We're still tweaking things on the server side to improve performance and stability.

> Btw I am not able to log in to bugs.launchpad.net - I encounter what looks like a loop on login - but can log in to my launchpad account.

You might need to delete any cookies for login.ubuntu.com and then try to login again.

Thank you,

Joshua

---

### Post by laoshi on 2010-05-06
> We're still tweaking things on the server side to improve performance and stability.
Yes - and that is greatly appreciated. At the moment I get no faults, although syncing is still a bit slow.
> You might need to delete any cookies for login.ubuntu.com and then try to login again.
It turns out I had a password mismatch (pw was correct, but too weak - after changing to a stronger pw everything is ok)

---

### Post by ruffneck on 2010-05-06
I'm experiencing these issue also. Thanks for the updates joshuahooever.

---

### Post by Jim Danner on 2010-05-12
For me everything is syncing now. However, to purge the stuff off the server side, I first had to select 'Stop syncing on Ubuntu One' for each of the synced folders. Then, after the server had been emptied, I selected them for syncing again.

Before doing this little purge operation, I kept seeing files 'uploading' on the website which had long been deleted from my computer, and I kept getting files downloaded with names with 'conflict' appended. After the purge it has been working well.

---

