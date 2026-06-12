---
title: "File modified date is the update time."
date: 2010-04-08
forum: Ubuntu One (CLOSED)
---

### Post by sokam on 2010-04-08
I have been using Ubuntu One to sync some of my document.  however, one thing really bother me is that the modified date on all the file in my local Ubuntu One folder is being overwrited with the sync time when Ubuntu One being update and subsequently to other computers that I am in sync with Ubuntu One (also the sync time!).

Is there a way to preserve the local file modified date on my file when sync up with Ubuntu One?  This goes without saying that the same modified date would also preserve to other computers which are sync with Ubuntu One as well. 

(In some way, Ubuntu One must be doing it already or else it would not know which file is newer when there are many computer connecting to a single Ubuntu One account.)

---

### Post by joshuahoover on 2010-04-12
> **sokam said:**
> I have been using Ubuntu One to sync some of my document.  however, one thing really bother me is that the modified date on all the file in my local Ubuntu One folder is being overwrited with the sync time when Ubuntu One being update and subsequently to other computers that I am in sync with Ubuntu One (also the sync time!).

Is there a way to preserve the local file modified date on my file when sync up with Ubuntu One?  This goes without saying that the same modified date would also preserve to other computers which are sync with Ubuntu One as well. 

(In some way, Ubuntu One must be doing it already or else it would not know which file is newer when there are many computer connecting to a single Ubuntu One account.)

There is no way to preserve modified dates on folders and files. The reason for this is because we don't carryover any meta data on the files being synchronized. 

Thank you,

Joshua

---

### Post by sokam on 2010-04-20
Is there anyway I can sync my Ubuntu One files to Windows?

---

### Post by joshuahoover on 2010-04-21
> **sokam said:**
> Is there anyway I can sync my Ubuntu One files to Windows?

Not currently. Lucio Torre did some work at PyCon this year with a number of people to start porting the Ubuntu One syncdaemon to Windows. If you or others are interested, you can see this work (code) at: [https://code.edge.launchpad.net/~lucio.torre/ubuntuone-client/windows-port]("https://code.edge.launchpad.net/%7Elucio.torre/ubuntuone-client/windows-port") If you or anyone you know is interested in helping us port to Windows, please message me directly and I'll get you in touch with Lucio.

Thank you,

Joshua

---

