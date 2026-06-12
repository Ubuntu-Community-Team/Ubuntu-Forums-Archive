---
title: "Ubuntu One Doesn't Automatically Sync"
date: 2009-08-13
forum: Ubuntu One (CLOSED)
---

### Post by sblunix on 2009-08-13
First off, Ubuntu One doesn't automatically sync for me, so whenever I upload a file to the online service, I have to disconnect and reconnect to get it, and just as a note, It would be useful if they allowed you to set a frequency for how often it synced with the server in the options... Anyone else having this problem? Comments?

---

### Post by andrea000 on 2009-08-13
ubuntu one automatically syncs for me but it
takes over the Internet.I would also like to
see a way to control how fast it uploads.

---

### Post by Inevitable Glitch on 2009-09-20
> **andrea000 said:**
> ubuntu one automatically syncs for me but it
takes over the Internet.I would also like to
see a way to control how fast it uploads.

There is actually an option in the preferences (right click on the icon and click on preferences) to set upload and download speed limits.

What would be nice is a "Sync Now" button.

---

### Post by Philip Farrugia on 2009-09-28
Sync Now! button would be great!

---

### Post by andrea000 on 2009-09-28
> **Philip Farrugia said:**
> Sync Now! button would be great!

Mine syncs now but i cant delete folders from the web and when i delete it from the ubuntu
one app it doesn't get deleted from the web.But i agree a sync now button would be great.

---

### Post by jdeslip on 2009-10-16
Is there an LP bug for this? (the fact that you need to disconnect/connect to get files that were added on other machines) -  I just looked and couldn't find one, but there must be one because it is in the ubuntuone FAQ.  I just want to subscribe to it so I can keep up...

This is the major thing missing in UbuntuOne that Dropbox has.

---

### Post by wayeast on 2010-02-04
Yes, a "Sync Now" button should be imperative.  While we're at it, shouldn't Ubuntu One also sync as part of the shutdown sequence?  This way, no files will be missed if a user shuts down quickly after modifying a document.

---

### Post by ricarrod on 2010-07-10
I have been using dropbox for a year more or so, and without (almost) any problem.

I am now trying ubuntu one (I am using 3 computers, 2 of them with karmic and a third one with lucid) and unfortunately I will have to rely solely on dropbox for serious matters, as my impression is that ubuntu one is far less reliable.

... And yes, a "sync now" button may help make it more usable, although it shouldn't be necessary if it sync'd everything correctly on the fly (as does dropbox).

---

### Post by juliobahar on 2010-09-26
I find a sync now button would be redundent. Yet, it might solve the current inconsistency in Ubuntu One.

I do like the concept of Zumodrive. I guess it is more reliable.

---

### Post by duanedesign on 2010-09-28
> **sblunix said:**
> First off, Ubuntu One doesn't automatically sync for me, so whenever I upload a file to the online service, I have to disconnect and reconnect to get it, and just as a note, It would be useful if they allowed you to set a frequency for how often it synced with the server in the options... Anyone else having this problem? Comments?

You should not have to disconnect/reconnect for U1 to detect that a new file has been added to your Ubuntu One folder or the cloud. It should detect a file has been added and syncs should happen automagically. I recommend you file a bug as that would be the easiest way to get your logs viewed by someone who can help you. To help in determining the root cause you can zip your ~/.cache/ubuntuone/log/ directory and attach it to the bug report.

If you do not want a sync to happen you can open the Ubuntu One Preferences (Me Menu --> Ubuntu One or System --> Preferences --> Ubuntu One) and under the Services Tab you can uncheck the box next to 'Files'. This would effectively act as a sync now button as checking it would cause the syncdaemon to start and sync any files/folders you have added to your Ubuntu One Folder or any User Designated Folder (UDF)

thank you,
duanedesign

---

### Post by mathgeek2000 on 2010-09-28
> **juliobahar said:**
> I find a sync now button would be redundent. 

I've found disconnecting, and reconnecting will generally ensure an upload takes place. -- Occasionally I've found the emblems aren't updated as quickly as I'd like. -- but the file in question is going up to the site.

---

### Post by juliobahar on 2010-09-28
> **duanedesign said:**
> 
If you do not want a sync to happen you can open the Ubuntu One Preferences (Me Menu --> Ubuntu One or System --> Preferences --> Ubuntu One) and under the Services Tab you can uncheck the box next to 'Files'. This would effectively act as a sync now button as checking it would cause the syncdaemon to start and sync any files/folders you have added to your Ubuntu One Folder or any User Designated Folder (UDF)

Yup, This worked for me Thanks a million. I guess it was also my stupidity that I unchecked all boxes last time when I had this issue. Forgot to recheck them back again

---

### Post by moore.bryan on 2010-10-12
This is still a major issue on Maverick. Why wouldn't Ubuntu One have a "Sync Now" button by default? Why wouldn't Ubuntu One's daemon recognize a newly saved file in the Ubuntu One folder? Is there an open Launchpad bug for this; if so, could someone post the link to it because I couldn't find one in LP?

---

### Post by juliobahar on 2010-10-12
> **moore.bryan said:**
> This is still a major issue on Maverick. Why wouldn't Ubuntu One have a "Sync Now" button by default? Why wouldn't Ubuntu One's daemon recognize a newly saved file in the Ubuntu One folder? Is there an open Launchpad bug for this; if so, could someone post the link to it because I couldn't find one in LP?

Ubuntu One should automatically sync. 
If you want to hasten the process - I guess- try unchecking and then checking the file sync option in your Ubuntu One-->Services section

---

### Post by moore.bryan on 2010-10-12
> **juliobahar said:**
> Ubuntu One should automatically sync. 
If you want to hasten the process - I guess- try unchecking and then checking the file sync option in your Ubuntu One-->Services section

I know it *should*, unfortunately it doesn't. :-(

---

### Post by harmus on 2010-11-02
I've used Ubuntu One for 2 months now. The Maverick version seems to be worse than the Lucid version (at least on my 2 computers). When I want to sync a new file I have to restart the service and then reconnect. Most of the time I have to click the 'restart' button like 3 times before it even restarts the service (no, it's not impatience, it does not restart when 1 click the first 2 times, the 3rd click makes it restart in like 10 seconds). After that I have to press connect 2 times and there we go...

So I'm looking for an alternative now, I'll give dropbox a try. I do not understand why they're working on a Windows-version if the Linux-version isn't there yet. I'd say: get this done first.. Anyway, I've been waiting for things to get fixed and they didn't, bye bye One, you should've saved me time and you didn't.

---

### Post by Carl Hamlin on 2010-11-03
> **harmus said:**
> So I'm looking for an alternative now, I'll give dropbox a try. I do not understand why they're working on a Windows-version if the Linux-version isn't there yet. I'd say: get this done first.. Anyway, I've been waiting for things to get fixed and they didn't, bye bye One, you should've saved me time and you didn't.

I moved to Dropbox after Ubuntu One gave me repeated issues as well. No complaints, so far. It works as advertised.

At first, I was a little bummed to be missing contacts synchronisation, but then I realized that I could put .evolution into my dropbox and build a symlink in ~ to it titled '.evolution' and it worked just as well, *and* my contacts get synced across machines.

---

### Post by Orfintain on 2011-11-10
never-mind

---

