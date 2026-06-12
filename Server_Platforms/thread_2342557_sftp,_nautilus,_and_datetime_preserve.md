---
title: "sftp, nautilus, and date/time preserve"
date: 2016-11-07
forum: Server Platforms
---

### Post by aeronutt on 2016-11-07
Server: running Ubuntu 16.04.1 server
Laptop: running Ubuntu 16.04.1 gnome-shell

-Is there a way to get nautilus to preserve date/time when connecting & copying files to a server via sftp?

Details:
I connect to server in nautilus with sftp://servername.domain/directoryname
But when I drag/drop from client (laptop) to my server, date/time isn't preserved.

"scp -p localfile serverlocation" works just fine (preserves date/time)

I've looked at man ssh_config to see if there was something there, but didn't see anything.
I saw some thread on the webs about a 'bug' in ssh  and nautilus which causes this, but that thread was dated 2012

- Alternatively, is there a GUI other than Nautilus that I can run locally, connect to server, and easily copy files to the server and preserve date/time?
Filezilla is a bit cumbersome, but does seem to preserve date/time with sftp transfers if the right switches are set. Which makes me believe it'd be possible in Nautilus!

---

### Post by TheFu on 2016-11-07
Use rsync instead. By default, rsync uses ssh.  Don't know how to use a GUI for this. Sorry.  My servers don't have GUIs and I haven't seen nautilus in years.

---

### Post by aeronutt on 2016-11-07
Yet your avatar is a GUI. :)

Ok, I'll use rsync rather than scp if I have to use CLI.

Still, would like to use Nautilus on my laptop to copy from various devices to server, and retain date/time. Filezilla isn't terrible, but we have Nautilus for a reason.

---

### Post by TheFu on 2016-11-08
> **aeronutt said:**
> Yet your avatar is a GUI. :)

Ok, I'll use rsync rather than scp if I have to use CLI.

Still, would like to use Nautilus on my laptop to copy from various devices to server, and retain date/time. Filezilla isn't terrible, but we have Nautilus for a reason.

Just providing an option that works, I use rsync all the time, usually in scripts that run automatically. Not necessarily the option you prefer, but nautilus can be extended (I've heard). 

Would another file manager work? Perhaps thunar or caja?  I don't know. 

I've heard of a GUI for rsync, grsync. Never used it myself. GUIs are hard to script.

BTW, doesn't **cp -p** have limitations?  Like it has to be running as root or as the owner of the files to work?  Files owned by others don't retain anything besides the content.  I believe.

OT:
That isn't my preferred avatar. I was told (strongly) to change the one I'd had for 5 yrs because someone took offense at my tagline and looked closely at the avatar.

---

### Post by aeronutt on 2016-11-08
Now you have me interested in what your avatar WAS.

I'll keep hope open for a GUI filemanager that preserves date/time/etc over remote connection, but I do see the allure of a script, even in my case. I mostly plan to store video on my file server, and most of that is from a garmin virb from my track car. (Plus 'system' backups, which won't have this date/time issue.) I see a script in my future that automagically creates/names directories and copies new files all based on date stamps of the videos and if they are new.  Filezilla will work until then.

On a side note, hopefully won't need a new thread.....
sftp via nautilus copied at about 12Mb/s, while sftp via filezilla was at about 6Mb/s. 
Any thoughts?

---

### Post by TheFu on 2016-11-08
> **aeronutt said:**
> 
sftp via nautilus copied at about 12Mb/s, while sftp via filezilla was at about 6Mb/s. 
Any thoughts?

Different libraries implementing sftp?  Different default settings for the crypto method used?  12Mbps ... ouch.  I see 70-127MBps (about 560-1016 mbps) transfers here through rsync scripts, but these are disk-to-disk, with lots of disk buffering, no slow flash storage involved.  Also, the processing required for the different crypto can tax low-end CPUs.  Check the settings. I use trival crypto for LAN transfers ... *-c arcfour*.

GUI tool developers often don't update the underlying libraries. They are lazy. It is an issue across all languages - perl, go, python, java, C, C++, whatever. Doesn't matter.  OTOH, I dunno about filezilla or nautilus sftp implementations. Probably would need to use "the source" to figure it out.

---

### Post by aeronutt on 2016-11-08
Yea, slow. But I'm pretty sure that's a limitation of the Virb USB device. When connected via USB directly to server, all I got was 12Mb/s. It's a new server though, and I need to double check everything before I assume 12Mb/s is the baseline rate of the USB device.

---

