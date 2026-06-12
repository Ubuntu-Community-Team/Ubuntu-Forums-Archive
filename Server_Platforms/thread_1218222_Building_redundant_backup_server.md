---
title: "Building redundant backup server"
date: 2009-07-20
forum: Server Platforms
---

### Post by Fliggerty on 2009-07-20
Hello!
 
I'm still relatively new to this fantastic thing called Linux.  I've been working with Ubuntu Server for about 3 months now.  Over that time, I've installed and reinstalled everything on my server half a dozen times.  Each time I have gone a bit further and done a bit more and learned a lot more.
 
I finally have it to where things are running really well overall.  I have a live site running on it, as well as some other applications.  I want to still play around with it and learn more, but don't want to jeopardize the condition I have now....it is the result of many long hours of nano-ing conf files and apt-geting.
 
What I would like to do is piece together something out of my PC boneyard and get it running with Ubuntu, then use it as a redundant backup.  I would like it to basically be a snap-shot of my primary server now, and yet I will still update the www data on it each day just in the case that I mess up my primary.  In that case, I would like to use the backup server to restore the settings and data on main.
 
So my question is this: what directories would I need to copy from the primary server to the secondary?  The only thing I want to be different between the two is the hardware support.  Are all of the drivers (if there are drivers in Linux as we "Windowers" know them) contained in a single directory?  If so, is that the only directory that I would need to have different?
 
TIA!
 
--Fligg

---

### Post by HermanAB on 2009-07-20
Just copy the whole disk.  When you boot up, all hell will break loose because the hardware is different, but the system will very likely figure it out and work regardless.
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

---

### Post by koenn on 2009-07-20
I'd use rsync, and exclude files and directories that would most likely cause trouble or are volatile : the kernels, /boot, /tmp, /proc, /dev, probably also /var/log, /var/lock, ....

it might be easier to only do the direcetories that have data you need :
/etc; parts of /var, possibly /opt or /usr/local of you've installed extra software there

to avoid having to deal with subdirs of /var, it might be a good idea to move your data (www, mysql, ...) out of there, eg to /srv

---

### Post by FakeOutdoorsman on 2009-07-20
You might be interested in [rdiff-backup](http://www.nongnu.org/rdiff-backup/) to make remote incremental mirrors of your live server.  It's free, bandwidth friendly because it uses rsync, and preserves file ownership, permissions, etc.  It is in the Ubuntu repository.  I currently use [duplicity](http://duplicity.nongnu.org/) for my backups and is written by the same author as rdiff-backup.  Duplicity is similar to rdiff-backup, but creates encrypted archives.  I rent my backup space so I need encryption.

---

### Post by Fliggerty on 2009-07-21
Perfect, that gives me some things to look at.  Thank you very much, I really appreciate the comments!

--Fligg

---

