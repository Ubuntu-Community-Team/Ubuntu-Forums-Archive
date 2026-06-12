---
title: "Can't stop synchronizing folder"
date: 2010-04-30
forum: Ubuntu One (CLOSED)
---

### Post by Commander_Bob on 2010-04-30
I installed 10.04 today and while messing around with it I decided to try syncing a folder. While it worked and the file in it was uploaded and removed when deleted I can't stop syncing the folder. If I right click it the option is grayed out. Any ideas?

---

### Post by x-shaney-x on 2010-04-30
It does actually stop syncing, it just seems to take forever to change the status.
I found it wasn't until after a reboot it showed it wasn't syncing anymore.

<EDIT>

Sorry, I misread.  You may need to disconnect from ubuntu one using the preferences while you un-sync it

---

### Post by Lord_Devi on 2010-04-30
I noticed this exact problem myself. It is actually a very cool feature, but without any kind of status indicator like Dropbox has, it can be very difficult to tell what is going on. It seems to me that if Ubuntu One thinks it is currently busy syncing the contents of a folder the status will be greyed out. The problem comes from how long this takes for even simple text files. If you share two Documents folders on seperate computers, you'll find that the Stop Syncing submenu options will be greyed out for nearly half an hour after first enabling.

I find if you just let them sit there for a long time and ignore it's progress Ubuntu One DOES seem to eventually work things out.

(Just make sure to keep your DEVICES in Ubuntu One trimmed. It will sometimes spawn multiple instances of any given machine.)

---

### Post by joshuahoover on 2010-04-30
> **Commander_Bob said:**
> I installed 10.04 today and while messing around with it I decided to try syncing a folder. While it worked and the file in it was uploaded and removed when deleted I can't stop syncing the folder. If I right click it the option is grayed out. Any ideas?

This is a bug. You should be able to right-click on a folder and select "Stop synchronizing on Ubuntu One" even if the syncdaemon is busy processing your files. I'll make sure this is on the list to fix as this is the 3rd thread in less than an hour where I've had to address this issue. In the mean time, can you try following the instructions in this FAQ I just added?

[https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder)

Thank you,

Joshua

---

### Post by Geomas on 2010-07-08
It seems that this bug persists as of today (8 July 2010).
:(

---

### Post by I, the Deceiver on 2010-11-07
really?
who implements a "feature" the you can't stop using?
wow. ](*,)
it still happens 10.10 btw

---

### Post by gamhead on 2011-01-06
Josh the link you have provided doesnt work.

Guys there is an FAQ [here]("https://wiki.ubuntu.com/UbuntuOne/FAQ#Files") and [here is a tip]("http://tuxtweaks.com/2010/12/check-the-status-of-ubuntu-one-synchronization/")

Also if you want an indicator of whether syncing is occuring you can follow [this discussion]("http://askubuntu.com/questions/19067/does-the-ubuntu-one-sync-work")

Mods: Please feel free to override with the latest info if this approach is dated

It's a nice idea to make revenue for Ubuntu but poorly executed. Im only using it because Dropbox is banned at work. But as always good luck Ubuntu guys!

---

