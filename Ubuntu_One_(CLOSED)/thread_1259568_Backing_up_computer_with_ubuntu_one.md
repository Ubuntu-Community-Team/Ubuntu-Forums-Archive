---
title: "Backing up computer with ubuntu one"
date: 2009-09-06
forum: Ubuntu One (CLOSED)
---

### Post by bdubsemail on 2009-09-06
this is somthing i have been trying today and i wanted to see what everyone thought about it, im running "back in time"  and when it asked where i would like  the save file to be stored i picked my ubuntu one folder. im hoping that this will make it easyer if my system crashes to backup. so what do you guys think about this,

---

### Post by gradysghost on 2009-09-07
I might be wrong, but Ubuntu One holds only 1 GB or something small like that.  I doubt it's enough to contain even a base installation of Ubuntu.  You can try, but I'd bet money that you'll run into a quota problem when you do.

On the other hand, you could probably do some compression (squash-fs, maybe?) and find a way to squeeze it all down very small before uploading, but that's probably more trouble than it's worth.  I can't imagine having to upload/download a full gig of data every time I wanted to backup/restore my OS.

As far as total data backup is concerned, it's a better idea, I think, to backup to an external device with more storage than Ubuntu One can offer.

One thing I do to reduce the number of restores I must do is install Ubuntu with /home on a different partition.  Later, I do clean installs of Ubuntu using the same username as last time, and without formatting the /home partition, only reusing it.  I get to keep all my data and settings intact (for my user) without having to do a backup every time I install the OS.

Just a few thoughts to get you going.  Any other tips from anyone on how Ubuntu One can benefit, or how to better back up your data, or even to reduce the frequency of restores?

---

### Post by gradysghost on 2009-09-07
Okay, I kinda take that back.  Rather, I need to correct myself.  It's 2 GB for free, or you can pay $10 per month to get 10 GB.  That's really not that bad, and it's especially cool since it's integrated into Nautilus so well.

However, I think my point still stands that it's time-consuming.  My lightest Ubuntu install is 12 GB (I have a lot of data and software), so it's still not viable for me.  My heaviest is over 500 GB (lots of media), and so it's **definitely** not viable for that.

Even if I had a base install (~2.5-4 GB), that would still take me far too long to upload.  I believe Ubuntu One (and other backup services like it) is designed to be used by people who use Ubuntu everywhere they go and just want to keep a backup of a handful of common items in the cloud (and don't get me started on the cloud).

---

### Post by oboedad55 on 2009-09-07
> **gradysghost said:**
> Okay, I kinda take that back.  Rather, I need to correct myself.  It's 2 GB for free, or you can pay $10 per month to get 10 GB.  That's really not that bad, and it's especially cool since it's integrated into Nautilus so well.

However, I think my point still stands that it's time-consuming.  My lightest Ubuntu install is 12 GB (I have a lot of data and software), so it's still not viable for me.  My heaviest is over 500 GB (lots of media), and so it's **definitely** not viable for that.

Even if I had a base install (~2.5-4 GB), that would still take me far too long to upload.  I believe Ubuntu One (and other backup services like it) is designed to be used by people who use Ubuntu everywhere they go and just want to keep a backup of a handful of common items in the cloud (and don't get me started on the cloud).

Do you ever run into problems reusing the /home partition with different versions of software being newly installed?

--Jon

---

### Post by bdubsemail on 2009-09-07
its 164 mb per backup

---

### Post by gradysghost on 2009-09-09
> **oboedad55 said:**
> Do you ever run into problems reusing the /home partition with different versions of software being newly installed?

--Jon

I haven't yet.  Since I'm not separating out my /bin or /usr/bin or anything like that, when I install the new OS, I still have to go reinstall software (it's better that way anyhow, so I get the newest versions without upgrade issues), but that software always picks up on my previous settings.  I even managed to install Empathy this way, and it picked up on old Pidgin settings that were laying around.  Just remember not to format the /home partition during the install, and you should be fine.

---

### Post by joshuahoover on 2009-09-09
> **bdubsemail said:**
> this is somthing i have been trying today and i wanted to see what everyone thought about it, im running "back in time"  and when it asked where i would like  the save file to be stored i picked my ubuntu one folder. im hoping that this will make it easyer if my system crashes to backup. so what do you guys think about this,

Ubuntu One isn't really meant to be used for a backup system. It's not to say that you couldn't find a way to make it work as a backup solution, but our goal is to make it really easy to store, share, and sync files across Ubuntu and the Internet.

---

### Post by zekopeko on 2009-09-09
> **joshuahoover said:**
> Ubuntu One isn't really meant to be used for a backup system. It's not to say that you couldn't find a way to make it work as a backup solution, but our goal is to make it really easy to store, share, and sync files across Ubuntu and the Internet.

I'm hoping that you plan to have an automated way of marking what applications the user has installed and backing up the list of said apps + their settings. That would simply be a huge plus for U1 since reinstalling or setting up a new machine would be super easy.
Imagine people installing Ubuntu and simply having their favorite applications and setting be installed/transfered with a single click.

---

### Post by joshuahoover on 2009-09-09
> **zekopeko said:**
> I'm hoping that you plan to have an automated way of marking what applications the user has installed and backing up the list of said apps + their settings. That would simply be a huge plus for U1 since reinstalling or setting up a new machine would be super easy.
Imagine people installing Ubuntu and simply having their favorite applications and setting be installed/transfered with a single click.

We have discussed functionality like this so it's definitely a possibility. We've also had several people request similar functionality.

---

### Post by rodrigo_ on 2009-09-10
Yes, once we have a DConf (GConf replacement, hopefully to be in for GNOME 2.30/3.0) backend that talks to the local CouchDB, all settings could be backed up to the Ubuntu One server. So, yes, this is planned, just waiting for DConf, which makes writing backends much easier than GConf, to become the settings storage for applications.

As for other settings backup, like dot files in your home, people have found nice ways to do it, just linking the dot files/dirs in their homes to the Ubuntu One folder, so you can do that already. Even, if you want, you could just link the ~/.gconf dir to ~/Ubuntu One to have the whole GConf database saved to UbuntuOne (although I don't recommend it for now, since writes from syncdaemon could confuse the GConf daemon, which is not prepared to have external apps writing to its database)

---

### Post by PhoHammer on 2009-10-06
> **oboedad55 said:**
> Do you ever run into problems reusing the /home partition with different versions of software being newly installed?

--Jon

I had a problem with that going from 9.04 to 9.10, but I'm still not sure if it wasn't just
the alpha-ness of Karmic at the time of the installation.

---

