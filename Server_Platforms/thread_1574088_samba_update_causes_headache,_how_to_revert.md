---
title: "samba update causes headache, how to revert?"
date: 2010-09-13
forum: Server Platforms
---

### Post by mons00n on 2010-09-13
Hi there!

I'm having a slight issue with my file server.  Last night I ran all  available updates, one of which included Samba.  The update according to  the /var/log/apt/term.log was:

Preparing to replace samba 2:3.3.2-1ubuntu3.4 (using .../samba_2%3a3.3.2-1ubuntu3.5_amd64.deb) ...
 * Stopping Samba daemons
   ...done.

This morning I went to listen to some music (hosted on my file server)  on my main PC (win7) through iTunes and I noticed that the response was  horrendously slow.  When clicking on any song there was a considerable  amount of lag before I could play the music or get any info about it.   For the last year or so I've had zero problems with listening to music  like this so I am attributing this new issue to the samba update.  With  all of that being said I wanted to downgrade to samba2:3.3.2-1ubuntu3.4  but I cannot find the .deb file anywhere!  All I can find is the [source]("https://launchpad.net/ubuntu/+source/samba/2:3.3.2-1ubuntu3.4") which scares me because I wouldn't know what to do with it.

The other option I just noticed would be to force version 3.3.2-1ubuntu3  via Synaptic Package Manger, but after marking that it doesn't give me  an option to apply changes.  If I am to go this route would I need to  completely remove the samba package and then reinstall the forced  version?

Which way/method would you take to downgrade?  And how will this effect any of the other dependencies of samba?

(my file server is currently running ubuntu 9.04 64bit and I have little interest or need to upgrade to 10.04 since almost everything is working great)

Thanks for your time.

EDIT:  I also just found that copying TO or FROM the file server yields horrible performance (especially over a gigabit network).  I tried to remove samba and samba-common but when trying to remove samba-common it says that I must also remove 'ubuntu-desktop'...and I don't want to kill the gui.  Idea's on how to proceed in resolving this issue?

-Robert

---

### Post by CharlesA on 2010-09-13
Are you running the desktop or server install (with GUI) installed?

I just checked my sources and the only samba*.deb I have are:

```
samba_2%3a3.4.7~dfsg-1ubuntu3.1_amd64.deb
samba-common_2%3a3.4.7~dfsg-1ubuntu3.1_all.deb
samba-common-bin_2%3a3.4.7~dfsg-1ubuntu3.1_amd64.deb
```

I haven't experienced any problems. Granted I am running 10.04.1, but I never had problems with an up-to-date 9.04.

Try sending a file via sftp or something to see if the transfer rate is still low. That would rule out if it was the update or not.

---

### Post by mons00n on 2010-09-14
thanks Charles.  I'm an idiot and forgot to try different methods of file transfer and different computers.  SSH transfer was also slow so I gave it a shot on my mac and all was well.  oddly enough rebooting the windows box made the problem disappear...now if I can figure out what caused it in the first place.

---

### Post by CharlesA on 2010-09-14
Glad you got it resolved.

Gogo magic reboot. :D

You might want to check the event viewer logs to see if there are any errors related to networking or disk access.

---

