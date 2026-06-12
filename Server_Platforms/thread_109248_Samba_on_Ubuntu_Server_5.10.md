---
title: "Samba on Ubuntu Server 5.10"
date: 2005-12-28
forum: Server Platforms
---

### Post by Novastorm on 2005-12-28
Ok firstly my hardware,

Celeron 533mhz
128mb (2 x 64mb, all slots full) SD-RAM
Gigabyte 6VM7-4L Mobo
80gb system drive
120gb data drive
2 x 3Com Cyclone 10/100 NIC

I've got ubuntu server 5.10, up to date as of 28/12/2005 10:00pm AEST running the standard server installation (CLI only, no GUI), with samba and ssh. For some reason, using my windows xp pro client to access samba shares, mounted in my computer, all works great, however at a random interval, (between 20 mins and a day), samba will for some reason drop the connection and thus windows complains it couldn't finish writing data (large ftp transfers from the internet onto this networked drive from the windows machine). Anyone have suggestions as to where i need to start looking? Oh also, this problem doesn't only occur in ubuntu, its also repeatedly occurs with CentOS 4.2, SUSE 10. So does it look like I have a hardware issue? Could it be lack of RAM?

Thanks in advance guys and gals.

---

### Post by Novastorm on 2005-12-28
Oh forgot to add, when this occurs, it appears sometimes the connections from my laptop remain ok (connecting with the same username), but sometimes not. And usually waiting a few minutes fixes it, as does restarting the samba daemons.

---

### Post by Gowator on 2005-12-28
Look in your /var/log/samba

each machine is listed and has a log.

---

### Post by Novastorm on 2005-12-28
Ok heres the log cut down for the offending machine.

Appears that the samba daemon is requesting a release on oplocks causing everything to go haywire. I haven't got much understanding of oplocks, am i right in guessing its about making sure files don't get written to concurrently by two users? Will go read up on it now.

```
[2005/12/28 20:41:49, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service shared initially as user shane (uid=1000, gid=100) (pid 8164)
[2005/12/28 20:42:01, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service ISOs initially as user shane (uid=1000, gid=100) (pid 8164)
[2005/12/28 20:42:59, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service home initially as user shane (uid=1000, gid=100) (pid 8164)
[2005/12/28 20:42:59, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service music initially as user shane (uid=1000, gid=100) (pid 8164)
[2005/12/28 20:42:59, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service software initially as user shane (uid=1000, gid=100) (pid 8164)
[2005/12/28 21:23:55, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service home initially as user shane (uid=1000, gid=100) (pid 8188)
[2005/12/28 21:23:55, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service music initially as user shane (uid=1000, gid=100) (pid 8188)
[2005/12/28 21:24:30, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337776, file_id = 1579
[2005/12/28 21:24:30, 0] smbd/open.c:open_mode_check(743)
  open_mode_check: exlusive oplock left by process 8164 after break ! For file ###HIDDENFILENAME###, dev = 341, inode = 11337776. Deleting it to continue...
[2005/12/28 21:24:30, 0] smbd/open.c:open_mode_check(747)
  open_mode_check: Existent process 8164 left active oplock.
[2005/12/28 21:25:02, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337733, file_id = 1582
[2005/12/28 21:25:02, 0] smbd/open.c:open_mode_check(743)
  open_mode_check: exlusive oplock left by process 8164 after break ! For file ###HIDDENFILENAME###, dev = 341, inode = 11337733. Deleting it to continue...
[2005/12/28 21:25:02, 0] smbd/open.c:open_mode_check(747)
  open_mode_check: Existent process 8164 left active oplock.
[2005/12/28 21:25:34, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:26:06, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:26:38, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:27:10, 0] smbd/oplock.c:request_oplock_break(1054)
  request_oplock_break: no response received to oplock break request to pid 8164 on port 1037 for dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:38:33, 0] lib/util_sock.c:read_socket_data(384)
  read_socket_data: recv failure for 44542. Error = Connection timed out
[2005/12/28 21:38:33, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service software
[2005/12/28 21:38:33, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service music
[2005/12/28 21:38:33, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service home
[2005/12/28 21:38:33, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service ISOs
[2005/12/28 21:38:33, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service shared
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337776, file_id = 1579
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337733, file_id = 1582
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337789, file_id = 2015
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(420)
  process_local_message: Received unsolicited break reply - dumping info.
[2005/12/28 21:38:33, 0] smbd/oplock.c:process_local_message(435)
  process_local_message: unsolicited oplock break reply from pid 8188, port 1037, dev = 341, inode = 11337789, file_id = 2015

```

---

### Post by Novastorm on 2005-12-28
Ok, read up on oplocks at the trusty samba home site, [http://www.oreilly.com/catalog/samba/chapter/book/ch05_05.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_05.html)

appears that because these files are large, samba gets impatient, asks for the cached copy to be sent back for synchronisation, but windows doesn't reply timely, and everything goes haywire, so am i right in using ```
oplocks = no
``` to fix this issue?

Going to try it anyways until someone replies.

---

### Post by Novastorm on 2005-12-28
Ok, by adding oplocks = no to each share, we have eliminated the oplocks errors, however the dropout persists, heres the relevant log dump. This is the log from the initiation of the shares, to what was in the log a few minutes after the drop out.

```
[2005/12/28 23:19:43, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service home initially as user shane (uid=1000, gid=100) (pid 8251)
[2005/12/28 23:19:58, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service music initially as user shane (uid=1000, gid=100) (pid 8251)
[2005/12/28 23:19:58, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service shared initially as user shane (uid=1000, gid=100) (pid 8251)
[2005/12/29 01:20:38, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service home initially as user shane (uid=1000, gid=100) (pid 8267)
[2005/12/29 01:20:38, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service music initially as user shane (uid=1000, gid=100) (pid 8267)
[2005/12/29 01:20:53, 1] smbd/service.c:make_connection_snum(642)
  prescott (192.168.0.12) connect to service music initially as user shane (uid=1000, gid=100) (pid 8268)
[2005/12/29 01:21:01, 1] smbd/service.c:close_cnum(830)
  prescott (192.168.0.12) closed connection to service music

```

Is there some sort of limitation to the amount of time a connection can exist even when its in use? Because fair enough it drops the connection to the music share, as it wasn't in use at the time, however the home share was in use, transferring CD ISOs onto it.

---

### Post by Gowator on 2005-12-29
Hmm noone else....
I wonder if your mounts are being automatically dropped and perhaps samba is just repsonding ?  What does your 
/etc/fstab look like?

Are the disks perhaps powering down? 
Lastly your first idea on memory might be correct .. what filesystem is it using?  
Also do you perhaps have a firmware RAID card?  Its possible it is set up to agressively cache but the cache size is smaller than the files.  

Sorry don't use Windows at all so Samba is not an area of expertise here :D I do all  my sharing via NFS.

---

### Post by Novastorm on 2005-12-29
Ok update,

the oplocks stuff doesn't affect this whatsoever, problem persists.

answers to questions: Filesystem is EXT3. My /etc/fstab is as follows.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I'm not sure about the powering down idea, is there any logs or something that may log these events? Thanks for your help by the way gowator

---

### Post by LordHunter317 on 2005-12-29
What are these files?  What are the links?  Post your smb.conf and the output of:```
sudo testparm -v | grep sendfile
```

---

### Post by Novastorm on 2005-12-29
[QUOTE=LordHunter317]What are these files?  What are the links?  Post your smb.conf and the output of:```
sudo testparm -v | grep sendfile
```[/QUOTE]

These files are from a private FTP server, sorry can't let u see them. However its not only these FTP files having trouble, ripping DVD's using DVD-Shrink also fails.

Output of "testparm -v | grep sendfile"
```
root@MENDOCINO:~# testparm -v | grep sendfile
Load smb config files from /etc/samba/smb.conf
Processing section "[home]"
Processing section "[ISOs]"
Processing section "[shared]"
Processing section "[software]"
Processing section "[music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

        use sendfile = No
root@MENDOCINO:~#

```

---

### Post by LordHunter317 on 2005-12-29
You can still give details on size, content type, and the link speeds used to share this.  If you won't, no one can help you.  I need some reference before I go assuming issues.

---

### Post by Novastorm on 2005-12-30
[QUOTE=LordHunter317]You can still give details on size, content type, and the link speeds used to share this.  If you won't, no one can help you.  I need some reference before I go assuming issues.[/QUOTE]

Ok, files are zips or rars, size, between 2mb and 2gb. The link speed 256/64 ADSL. The upload end is 155mbps ATM. I don't believe its an issue with the FTP client or the internet links though. The issue is that any transfer from my machine, across the 100mbps network to my server in the next room, dies after an hour or so of transferring. And also storing DVD ISOs as they are re-encoded by DVD Shrink causes this problem.

---

### Post by Gowator on 2006-01-03
Hmm sorry back after New Year with parents in internet free zone!  
Where abouts are the samba shares shares mounted ?  

The hdparm prog controls powering down etc.  (worth checking)

[http://www.die.net/doc/linux/man/man8/hdparm.8.html](http://www.die.net/doc/linux/man/man8/hdparm.8.html)
```

-v
    Display all settings, except -i 
```

```

-B
    Set Advanced Power Management feature, if the drive supports it. A low value means aggressive power management and a high value means better performance. A value of 255 will disable apm on the drive.
```
```

-C
    Check the current IDE power mode status, which will always be one of unknown (drive does not support this command), active/idle (normal operation), standby (low power mode, drive has spun down), or sleeping (lowest power mode, drive is completely shut down). The -S, -y, -Y, and -Z flags can be used to manipulate the IDE power modes.
```
```

-S
    Set the standby (spindown) timeout for the drive. This value is used by the drive to determine how long to wait (with no disk activity) before turning off the spindle motor to save power. Under such circumstances, the drive may take as long as 30 seconds to respond to a subsequent disk access, though most drives are much quicker. The encoding of the timeout value is somewhat peculiar. A value of zero means "timeouts are disabled": the device will not automatically enter standby mode. Values from 1 to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes. Values from 241 to 251 specify from 1 to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours. A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined timeout period between 8 and 12 hours, and the value 254 is reserved. 255 is interpreted as 21 minutes plus 15 seconds. Note that some older drives may have very different interpretations of these values.
```

What I was trying to determine earlier is how the samba shares themselves are presented to the server.  Are they local, are they seperate partitions etc. ?  
If they were USB disks etc. they might be unplugging and replugging.

---

### Post by Novastorm on 2006-01-06
Hey Gowator,

Hope you had a good new years, well i've spent the last 3 days with a mate at his grandparent's place without internet, anyways in that time i've discovered what the problem is. I took my server and desktop machine with me, as we played LAN games there, and the problem is windows xp sp2's 10 connections per second limit. I noticed that an event was logged (4226),

```
TCP/IP has reached the security limit imposed on the number of concurrent TCP connect attempts.
```

This doesn't always show up however, but it appears its the problem, as i noticed that every time it crashed is whenever i'm doing an operation to 10 files or more, thus creating 10 connections and causing windows to complain, so i've just resorted to storing my downloads locally and then moving them to my server, a pain, but no way around it without hacking up a windows DLL. I would like to thank everyone for their help, especially you Gowator, been a fantastic help.

---

