---
title: "Changing apache user and group for multiboot- too ambitious?"
date: 2014-01-21
forum: Server Platforms
---

### Post by kylehughes1 on 2014-01-21
Hi, I posted this over at the owncloud forums; it may be better that I post it here:

I have a server with owncloud for file delivery for my small sound design business. I'm a one-man operation, so it doesn't require much. It's running mainly on mavericks, multibooting mavericks 10.9.1, windows 7, and ubuntu server 13.10.

Now, and I know this may be too ambitious, but ideally, I would like all three OSes to keep the same server alive every time I reboot. I haven't figured a way to make that happen, so I've long considered it a lost cause; however, I'm wondering if it's possible with just OS X Server and Ubuntu Server. All 3 OSes have permission to read and write on all filesystems (ntfs, hfs+ and ext4) via paragon's drivers. Owncloud's data dir is on a separate internal hfs+ drive with only one partition.

Under OS X, it works fairly well, but the console is giving me loads of errors that are, as I understand it, unrelated to owncloud (recent OS X server update). The errors aren't what I'm here about (I'm getting there, I promise). This is leading to somewhat sluggish performance, so it's motivated me to look into using Ubuntu.

The question I have is:
**Under Ubuntu, apache runs as user www-data. In OS X, it runs as user _www. Is it safe (or possible) to change the username and group for apache in Ubuntu to _www?** If I do so, is it possible that it will be granted permissions on the data drive?

Since Ubuntu can read and write to hfs+, I don't anticipate many problems mounting the drive except for the fact that apache uses a different name in each OS. Is it possible to give apache permission to access via fstab?

In my head, it kinda makes sense, but it if I'm guessing correctly, I'd also have to grant Ubuntu access to the MySQL database used by OS X for owncloud to work. I don't want to screw up or corrupt anything on the mac side by prying in from linux, so would it be possible to move the database to the same drive as the data (or another shared partition of whatever format), so that both can access it with correct permissions?

In Ubuntu, the only things currently installed besides the default installation are filesystem drivers, apache, php, mysql, and owncloud (not setup yet). I can wipe and reinstall the entire partition if I need to do so.

I really think it's possible, but may not be worth the massive headache. Anyone tried a similar setup or have suggestions as to using either system? My workstation is a (real) mac, and I'm in the process of procuring a new mac pro to work on, so keeping the entire local network on OS X would be ideal. I also like the simplicity of the OS X Server application- I am a sound designer, not a software engineer, so it suits me well. I wouldn't be totally opposed to using Ubuntu server exclusively, but I'd like to stay away from Windows (more of a utility partition, as well as some light gaming).

There's more to do with syncing to external servers (dropbox, gdrive, and so on), but it doesn't seem relevant, so I'll go ahead and stop. My thanks to anyone who has advice [IMG]http://forum.owncloud.org/images/smilies/icon_e_smile.gif[/IMG] 
Kyle Hughes

Environment: HomeServer maybe?
Server: Apache
Database: MySQL
Client: Safari, Finder, whatever my client's client is [IMG]http://forum.owncloud.org/images/smilies/icon_e_wink.gif[/IMG]
OC-Version: 6.0.0a
PHP-Version: 5.4.17

---

### Post by QIII on 2014-01-21
Bearing in mind that we do not condone the cirucumvention of EULAs and TOSs on the Forums -- into which category Hackintosh falls -- I am disposed to leave this open only if the discussion ***remains strictly related to the Ubuntu question regardless of how that may or may not have a delitorious effect on the other OS.***

If it strays, the thread will be closed.

---

### Post by kylehughes1 on 2014-01-21
Ah- that makes sense.  Thanks for the consideration.  I've edited the post.

Anyone successfully attempted to change the user or group that other services operate under; eg, will changing the name of the 'wheel' group cause the system to freak out?

kyle

---

### Post by sandyd on 2014-01-21
You can change the running user for apache if you want

Just add a new system user (-s flag in useradd), and name it _www-data
Then, switch Apache to use the _www-data user/group, and all should be fine

---

### Post by volkswagner on 2014-01-22
Perhaps multi-boot is not the best solution.  Have you considered using a virtual machine to host?  Simply Choose Mac OSX as your main flavor, install VirtualBox then install Ubuntu and/or Windows as VM's.

---

