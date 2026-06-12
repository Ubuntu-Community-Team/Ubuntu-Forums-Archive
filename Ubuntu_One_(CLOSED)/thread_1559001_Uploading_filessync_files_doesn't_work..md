---
title: "Uploading files/sync files doesn't work."
date: 2010-08-23
forum: Ubuntu One (CLOSED)
---

### Post by ubto66 on 2010-08-23
OS: ubuntu10.04 LTS running on latest oracle virtualbox.

This works: I have opened a ubuntu one account. And I can log into that account.
But I have to do so by: clicking 'ubuntu one' in top bar, and click 'account' in 
prompt that appears. Shouldn't log in take place automatically?

Being logged in I'm able to make new folders. And appearently able to enter
them (they are empty I quess)

If I try to upload a file clicking 'upload file' in ubuntu one. A prompt appears and I
choose the file to upload and click 'continue'.  The prompt says "uploading" but
nothing happens.

If I choose a document folder and click 'mouse click right'. And then click
'sync with ubuntu one'. It prompts that it syncs the folders. But nothing 
happens.
Have I forgot some settings?
Thanks

At one time it began to work.
Thank you for answering.

---

### Post by ellis rowell on 2010-08-23
I have no experience of the "Oracle " box although a friend works for Oracle, I use an IBM type PC. On my system (Ubuntu/Linux) I have a folder named Ubuntu One, I put my data files in this and the corresponding folder on Ubuntu One gets updated when I update the data files (these are spreadsheets but I expect other data files like database files would do the same). When I go online with my laptop that also gets updated.

One thing I have found (by experiment) is that if you put a full application on there which runs under Wine, the .exe file is neutralised to read only (so does not work).

I believe the folder on my desktop was placed there by Ubuntu One when I set it up.

Edit: Just a thought. Are you using an FTP client to upload, it doesn't need that.

---

### Post by afrowildo on 2010-08-26
One little drawback of the current implementation of Ubuntu One is that there is little indication that is it actually doing anything, even though it is. Once you've selected "Synchronise to Ubuntu One", wait aroud 30-60 seconds then navigate into the folder in question. If the files in there are being synced, then a little circular arrow will appear in the lower right of the icon, and fully synced file/folder will boast a green tick in the same location.

You can also verify which files/folders are currently being synced by checking your Ubuntu One dashboard at [https://one.ubuntu.com/dashboard/](https://one.ubuntu.com/dashboard/) and selecting the "Files" tab from the navigation menu at the top.

The lack of indication could also be why you're not appearing to automatically log in, when you might very well be. Have you tried syncing a file or folder without going through the login process you described?

---

