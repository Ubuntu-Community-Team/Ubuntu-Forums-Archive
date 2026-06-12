---
title: "Can't connect for file sync"
date: 2010-07-27
forum: Ubuntu One (CLOSED)
---

### Post by motorcity909 on 2010-07-27
Hi all

I've been happily using Ubuntu One for a few weeks now, synching some files and notes.

Today I inadvertently clicked another folder to 'synchronise with Ubuntu One'.  This was a 500mb folder containing work and personal files which I'm not ready to rely on the cloud for.

I must admit I panicked a bit as I attempted to stop the synch.  I deleted the entire folder (got it backed up on an external hd) and the synch stopped.  I then logged in to the U-One website and deleted the folders and files it had uploaded by that point.

When I restored the folder from the ext hd it started to synch again.  This time I removed my machine from the U-One preferences and eventually cancelled my account.

I have now restored that folder under a slightly different name so it doesn't try and synch it.  

Meanwhile I've re-started my U-One account and have added my machine so it appears on the webpage.  I've uploaded a file via the website.  I've also been able to successfully synch Tomboy notes in both directions.

However, I can't synch files with my Home/Ubuntu One folder.  I've attached screengrabs of the three tabs in U-One Preferences which show 'disconnected'.  If I click 'connect' on the Devices tab, it simply greys out and nothing else happens.

Files in my Home/Ubuntu One folder all have the Unsynchronized emblem against them (a cloud with a cross in a red circle).

 I ran:

```
u1sdtool -s
```and the result was 

State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

Any help will be much appreciated.
Dave

---

### Post by motorcity909 on 2010-07-27
Apologies, just adding some more info so hope this helps.

From within Applications>Accessories>Passwords and Encryption Keys, I can see a reference to Ubuntu One.

Could the connection problem be anything to do with the stored password for Ubuntu One as per the attached screengrabs?

Thanks as always
Dave

---

### Post by motorcity909 on 2010-07-27
I'm pleased to say I can now synch files again.  I followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=9604893&postcount=8") and removed the machine and the password key.  Upon opening the Ubuntu One app it went to the website and prompted me to add my machine.

Files in my U-One folder now synch with the website.

One trifle left to sort is the folder I inadvertently started to synchronise.  I've deleted that folder off my computer now and restored the subfolders and files under a new name.

However, that original folder remains on the U-One website.

I've run **u1sdtool --list-folders** to get the ID of the folder, followed by** u1sdtool --delete-folder=ID-**etc etc but it tells me the folder does not exist.

Anyone know a way to removed that folder from the U-One website?

Cheers
Dave

---

