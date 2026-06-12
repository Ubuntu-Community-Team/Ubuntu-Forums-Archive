---
title: "cannot enable Contacts in Ubuntu One Preferences"
date: 2011-01-08
forum: Ubuntu One (CLOSED)
---

### Post by GLiBERN on 2011-01-08
I have a laptop and a desktop computer, each running Ubuntu 10.10.
On my laptop, file and contact synchronization with Ubuntu One works fine. File synchronization works on my desktop computer, too, but contact synchronization does not work - in two ways:

1) Evolution says "unable to open address book" when trying to access the "CouchDB > Ubuntu One" address book. This is a problem which, from what I read here, apparently many people have in one way or another.

2) In the Ubuntu One Preferences dialog, I cannot even enable Contact syncing (maybe this is the main cause for problem 1). See attached screenshot.

Why can't I check "Contacts"? I can do it on my laptop, why not on the desktop PC?
[IMG]http://img217.imageshack.us/i/screenshotubuntuonepref.png/[/IMG]

---

### Post by Docaltmed on 2011-01-09
The regrettable answer is that this service simply doesn't work.

---

### Post by GLiBERN on 2011-01-10
It does work on my laptop.

---

### Post by duanedesign on 2011-01-10
Could you please close Evolution and try the steps under ['Killing and Restarting Desktopcouch']("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting")

Are you able to see Futon (Couch interface)in step 4? If so is Contacts still greyed out in U1 Preferences?

---

### Post by GLiBERN on 2011-01-10
okay, so I tried the four steps:

1) for *beam.smp* as well as *beam* it said "no process found"
2) ~/.config/desktop-couch was empty
3) returned "Error org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/desktopcouch/desktopcouch-service exited with status 1" (I ignored that :P)
4) couldn't open the page

Then I thought, maybe *desktopcouch* isn't installed, but it was. So I purged and reinstalled it. After that, steps 3 and 4 worked!

Now I can check all the boxes that were grayed out before. And selecting the CouchDB address book at least doesn't give an error message anymore, although there are still no contacts. Maybe I should wait a while until they are synchronized.

Thank you for your help! Esp. for pointing me to those four steps, I didn't find them before.

---

### Post by duanedesign on 2011-01-17
Thank you for updating the thread with your results. That is great. I hope the Contacts get synced. If not let us know.

---

### Post by bford16 on 2011-04-30
I had this same problem after reinstalling Ubuntu 11.04 (to fix an unrelated problem).  After the reinstall, I had to manually install the following packages.  I think this is because the configuration was saved for UbuntuOne, but the packages were not installed.

evolution-couchdb
desktopcouch-ubuntuone
xul-ext-bindwood

Once done, I was able to use all the functions of the Ubuntu-one applet.

---

