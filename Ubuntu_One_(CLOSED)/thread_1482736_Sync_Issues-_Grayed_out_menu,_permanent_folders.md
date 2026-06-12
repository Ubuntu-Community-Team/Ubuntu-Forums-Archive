---
title: "Sync Issues- Grayed out menu, permanent folders"
date: 2010-05-13
forum: Ubuntu One (CLOSED)
---

### Post by kid1000002000 on 2010-05-13
**The Background**
I created a dummy folder on my desktop to try to test ubuntuone sync.  I right clicked on the folder on my desktop and selected "Synchronize on Ubuntu One."  The folder synced right away, and was visible if I checked it online in my browser via "Ubuntu One: My Storage."

The problem is, now I can't get it to stop.  If I right click on the folder from my desktop, the options to do so are grayed out.  Tried a restart of my computer, and the folder currently syncing once again shows only one option from the desktop menu: "Synchronize on Ubuntu One" with no hint of ever being previously enabled.  Now, the options are not even grayed out.

So I clicked "Synchronize on Ubuntu One" again.  Nothing seemed to happen. 

Logged out, then back in.  That seemed to fix the problem for most of my folders.  The proper menu options (share, stop) appeared correctly.But the issue is recurring if I create a new folder.

There is no option online to stop syncing/delete any synced folders for me either (this is probably standard).  Tried just deleting a folder from my desktop.  Now its permanent on the server, and non-existent on my pc.  Will it eventually disappear in a day or so?

I have followed this link ([https://wiki.ubuntu.com/UbuntuOne/FA...20One%20folder]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20%7E/Ubuntu%20One%20folder")) but to no avail (running the --unsubscribe-folder command doesn't remove the folder from --list-folders).  I have also tried restarting and disconnecting/connecting from System>Preferences.

Reinstalling ubuntuone-client-tools from synaptic did not solve the issue.

[B]The Problems
1.  How do I solve the issue of grayed out/nonexistant menus
2.  How do I remove said folder from the server?

[/B] Thank you in advance.

Help!

---

### Post by duanedesign on 2010-05-14
Open a Terminal and run:

```
u1sdtool --list-folders
```

That command will show you all your (UDF)User Designated Folders. The entries will look something like this.

```
[COLOR="Green"]id=[/COLOR][COLOR="Red"]c4d1e6f9-931b-45c6-8fac-830390815242[/COLOR] subscribed=True path=/home/jhoover/Documents
```

Copy the part that comes after "[COLOR="Green"]id=[/COLOR]", which in the example above would be "[COLOR="Red"]c4d1e6f9-931b-45c6-8fac-830390815242[/COLOR]" and put it in the next command where it says [COLOR="Red"]ID-FROM-COMMAND-ABOVE[/COLOR].

```

u1sdtool --unsubscribe-folder=[COLOR="Red"]ID-FROM-COMMAND-ABOVE[/COLOR] 
```


That should stop synchronizing that folder.

**Edit:** To remove the folder as joshuahoover mentions below, the command is
```
u1sdtool --delete-folder=FOLDER-ID
```
 
-
--

---

### Post by kid1000002000 on 2010-05-14
Followed your instructions exactly.  When I run *u1sdtool --list-folders* again, however, the folders I tried to stop synchronizing are again listed in the terminal.

I have copied and pasted carefully to avoid making any mistakes.

---

### Post by joshuahoover on 2010-05-14
> **kid1000002000 said:**
> Followed your instructions exactly.  When I run *u1sdtool --list-folders* again, however, the folders I tried to stop synchronizing are again listed in the terminal.

I have copied and pasted carefully to avoid making any mistakes.

If you want the folders completely removed, you'll need to run this command with the appropriate folder-id's listed from u1sdtool --list-folders:

```
u1sdtool --delete-folder=FOLDER-ID
```

This will remove the folder from the cloud storage, but leave it untouched on your computer. :)

Thank you,

Joshua

---

### Post by kid1000002000 on 2010-05-14
joshua's right.

Issuing the command u1sdtool --list-folders returend the following for me.  Notice that in two of these folders, the value for subscribed (TRUE) is missing after running, hence (perhaps) why the second command is needed.:

    Folder list:
      id=6028fa3d-bdbc-42...7 subscribed= path=/home/zzz/Desktop/asdf
      id=3cdd7094-d566-4e...4 subscribed=True path=/home/zzz/.ubuntuone/Purchased from Ubuntu One
      id=c7d59...0 subscribed= path=/home/zzz/Desktop/untitled folder

Had to log out and then back in again to get it to process the code.  Futures readers could try reconnecting and connecting (or restarting) ubuntuone to solve the issue should their terminal not process the entire code the first time.

Following duanedesign's instructions and then joshuahoover's consecutively solves issue 2.

However, there is still the issue with grayed out menu's.  A basic user would not be expected to type so much code in.

Thank you, by the way :)

---

### Post by joshuahoover on 2010-05-17
> **kid1000002000 said:**
> 
Following duanedesign's instructions and then joshuahoover's consecutively solves issue 2.

However, there is still the issue with grayed out menu's.  A basic user would not be expected to type so much code in.

Thank you, by the way :)

You're right, this should all be done via the UI, not at the command line. I'll chat with the devs to see what we can do to fix this problem. 

Thank you,

Joshua

---

### Post by pauljoseph on 2010-12-03
Hi,
I am having this same problem also, I tried the delete-folder, but it says folder does not exist, I am sure I have copied and paste the ID. please help to advise. Thanks.


```
oka@oka-mini:~$ u1sdtool --list-folders
Folder list:
  id=de99a01a-8bb4-47b8-a0ee-452ea2bd757c subscribed=True path=/home/oka/Desktop
  id=55d6d42b-5511-4d0a-a977-4c07e455c308 subscribed=True path=/home/oka/Documents
oka@oka-mini:~$ u1sdtool --delete-folder id=de99a01a-8bb4-47b8-a0ee-452ea2bd757c
FolderDeleteError: DOES_NOT_EXIST (volume_id=id=de99a01a-8bb4-47b8-a0ee-452ea2bd757c)

```

---

### Post by angus73 on 2010-12-13
Hi pauljoseph,
I think your command fails because it contains an " id" that shouldn't be there.
Try this:

oka@oka-mini:~$ u1sdtool --delete-folder=de99a01a-8bb4-47b8-a0ee-452ea2bd757c

hope this helps
Angus

---

### Post by pauljoseph on 2010-12-18
I tried without the id, and it says folder does not exist:
```

oka@oka-mini:~$ u1sdtool --delete-folder 55d6d42b-5511-4d0a-a977-4c07e455c308 
FolderDeleteError: DOES_NOT_EXIST (subscribed=True, suggested_path=~/Documents, generation=31, node_id=1e90c292-db96-4d05-a611-a2691290fead, volume_id=55d6d42b-5511-4d0a-a977-4c07e455c308, path=/home/oka/Documents, type=UDF)

```

---

### Post by angus73 on 2010-12-18
if I'm not wrong, you're missing a  "=": try

u1sdtool --delete-folder=55d6d42b-5511-4d0a-a977-4c07e455c308
instead of

u1sdtool --delete-folder 55d6d42b-5511-4d0a-a977-4c07e455c308 

regards,
Angus

---

### Post by pauljoseph on 2010-12-18
alright, thanks. I tried that, but now it seems processing something, but it never ends. I check using ps aux, and it still doing something after 30 minutes. So I ctrl-c to stop it. Is there any way to check what happens whether it's working or not?

---

### Post by angus73 on 2010-12-19
Hi pauljoseph. You can look at the u1sdtool man page, which describes some options that can show what the daemon is doing:
```
u1sdtool --current-transfers
u1sdtool --status
u1sdtool --waiting-metadata
u1sdtool --waiting-content
```BTW, you could also try to refresh some information with
```
u1sdtool --refresh-volumes
u1sdtool --rescan-from-scratch=VOLUME_ID
```Also, did you try to unsubscribe the folder first, using --unsubscribe-folder option? I am not sure it's important, though.

Regards,
Angus

---

### Post by duanedesign on 2010-12-20
+1 on what angus says.

If you run the folowing commands you will get the number of items in the queue. You can tell if it is stuck because the number will not get smaller over time. Also note Ubuntu One processes the metadata queue before the content queue.

```
u1sdtool --waiting-metadata | wc -l
```
```
u1sdtool --waiting-content | wc -l
```

Also check out the sticky about [getting more info from Ubnutu One.]("http://ubuntuforums.org/showthread.php?t=1594301")

---

### Post by pauljoseph on 2010-12-24
alright, I tried to unsubsribe first, it doesn't give anything, and then when I tried delete folder, it says, folder delete error.

```

oka@oka-mini:~$ u1sdtool --unsubscribe-folder=de99a01a-8bb4-47b8-a0ee-452ea2bd757c
oka@oka-mini:~$ u1sdtool --delete-folder=de99a01a-8bb4-47b8-a0ee-452ea2bd757c
FolderDeleteError: DOES_NOT_EXIST (subscribed=, suggested_path=~/Desktop, generation=495, node_id=35b438c9-74f6-4b1f-822b-19a89144bd6f, volume_id=de99a01a-8bb4-47b8-a0ee-452ea2bd757c, path=/home/oka/Desktop, type=UDF)

```

---

