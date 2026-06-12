---
title: "Please Help, Urgent Samba Problem!"
date: 2005-01-06
forum: Server Platforms
---

### Post by mjpowersjr on 2005-01-06
Hello, I'm using samba as a simple file/imap server. after a dist-upgrade yesterday samba fails to start.  
/etc/init.d/samba restart 
fails but no log file is created in /var/log/samba for the problem. But if i let the computer sit for a few minutes, a log is generated wich is attached below. This server is used in a production enviroment, and I would greatly appreciate any help in bringing samba back to life. I am using samba 3.07ubuntu6.3 , oddly enough samba was working fine after the upgrade for a small period of time, because a client was able to open a few files off the server before i got in to work this morning.

less /var/log/samba/log.smbd

[2005/01/06 09:06:29, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:29, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:29, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:29, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:29, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:29, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:29, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:29, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:29, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:30, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:30, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:30, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:30, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:30, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:30, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:30, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:30, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:30, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:53, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:53, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:53, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:53, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:

   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:06:54, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:06:54, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:06:54, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:06:54, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:03, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:03, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:03, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:03, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:03, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:06, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:06, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:06, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:06, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 09:13:06, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 09:13:06, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 09:13:06, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 09:13:06, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
-------------Cut to save space, seems to be repeating anyway.

---

### Post by jdodson on 2005-01-06
[QUOTE=mjpowersjr]Hello, I'm using samba as a simple file/imap server. after a dist-upgrade yesterday samba fails to start.  
/etc/init.d/samba restart 
fails but no log file is created in /var/log/samba for the problem. But if i let the computer sit for a few minutes, a log is generated wich is attached below. This server is used in a production enviroment, and I would greatly appreciate any help in bringing samba back to life. I am using samba 3.07ubuntu6.3 , oddly enough samba was working fine after the upgrade for a small period of time, because a client was able to open a few files off the server before i got in to work this morning.

less /var/log/samba/log.smbd[/QUOTE]

i am sure you already know about this however i will mention something.  i think a good practice when you are running any production machine(s) is to have a "test" machine.  this machine could allow you to perform upgrades and updates so you know if they can be performed on the production machine.  as i am sure you well know starting with warty and dist-upgrade"ing" takes you to the lastest "test" version of ubuntu called hoary, which is still buggy and not ready for the production enviornment.

anyways, as to your question, i looked around for a "dist-downgrade" function and did not seem to find one.   perhaps removing the .debs and installing samba from source until the package can be fixed in hoary.

---

### Post by nocturn on 2005-01-06
I'm curious, are you using Samba as an IMAP server?

---

### Post by mjpowersjr on 2005-01-06
Yes, I use ubuntu Hoary and Warty as test machines at home, and have had no problems, I did not ubdate Ubuntu to the Hoary, it is still using the Warty tree, Yesterday I upgraded the packages to the newest releases.

Opps  I appologize, it was not a "dist-upgrade", it was just a plain ol "upgrade" sorry for the type. Could the thread be moved back to the server forums so it might be resolved sooner? thanks. -Mike Powers

---

### Post by jdodson on 2005-01-06
[QUOTE=mjpowersjr]Yes, I use ubuntu Hoary and Warty as test machines at home, and have had no problems, I did not ubdate Ubuntu to the Hoary, it is still using the Warty tree, Yesterday I upgraded the packages to the newest releases.[/QUOTE]

if you ran a "apt-get dist-upgrade" in warty then you now have hoary.  if you ran an "apt-get upgrade" from warty then you have upgraded warty packages.

---

### Post by jdodson on 2005-01-06
[QUOTE=mjpowersjr]Opps  I appologize, it was not a "dist-upgrade", it was just a plain ol "upgrade" sorry for the type. Could the thread be moved back to the server forums so it might be resolved sooner? thanks. -Mike Powers[/QUOTE]

yes because you are running warty, from what you said it looked like you were running hoary after a "dist-upgrade".  however i don't have access to move form this forum, it will have to wait until another admin can move it.

---

### Post by jdodson on 2005-01-06
[QUOTE=mjpowersjr]Yes, I use ubuntu Hoary and Warty as test machines at home, and have had no problems, I did not ubdate Ubuntu to the Hoary, it is still using the Warty tree, Yesterday I upgraded the packages to the newest releases.[/QUOTE]

a adequate test machine would be a clone of the original in terms of hardware.  plus the test machine would have the same config files the same everything.  this would allow for fielding this kind of problem.  my home machine is not setup the same way as my machine at work therefore it is not an adequate testbed for a production server.

---

### Post by nocturn on 2005-01-06
Could be that you have file system/hard disk corruption.

Maybe just try re-installing the upgraded samba package over the current one.

---

### Post by mjpowersjr on 2005-01-06
ok, thanks for the help (any help is very much appreciated), sorry about the typo. -Mike Powers

---

### Post by mjpowersjr on 2005-01-06
Ok, Progress Report, I put in the ubuntu install cd, navigated to the samba debs folder, and did a dpkg --install * and suscessfully downgraded samba. It seems like the problems may be something else on the system, as samba now doesnt report failure while starting...but the following happens:

 * Stopping Samba daemons...
start-stop-daemon: warning: failed to kill 8660: No such process         [ ok ]
 * Starting Samba daemons..                                              [ ok ]
root@workstation:~ #

root@workstation:~ # smbclient -L localhost
protocol negotiation failed

also the log seems a bit different.

less /var/log/samba/log.smbd

[2005/01/06 10:47:02, 0] smbd/server.c:main(760)
  smbd version 3.0.7-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[syncspace]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[jobs]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[adraw]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[art_pdfs]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[archive]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[digicam]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[office_pdfs]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[vncdirectory]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[Graphics]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[backuplogs]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[email]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[webpages]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[backup]"
[2005/01/06 10:47:02, 2] param/loadparm.c:do_section(3415)
  Processing section "[RPC]"
[2005/01/06 10:47:02, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:47:02, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:47:02, 2] lib/interface.c:add_interface(79)
  added interface ip=192.168.0.15 bcast=192.168.0.255 nmask=255.255.255.0
[2005/01/06 10:47:02, 3] smbd/server.c:main(790)
  loaded services
[2005/01/06 10:47:02, 3] smbd/server.c:main(805)
  Becoming a daemon.
[2005/01/06 10:47:02, 2] lib/tallocmsg.c:register_msg_pool_usage(57)
  Registered MSG_REQ_POOL_USAGE
[2005/01/06 10:47:02, 2] lib/dmallocmsg.c:register_dmalloc_msgs(71)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2005/01/06 10:47:02, 3] printing/printing.c:start_background_queue(1168)
  start_background_queue: Starting background LPQ thread
[2005/01/06 10:47:02, 0] lib/util_sock.c:open_socket_in(708)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2005/01/06 10:47:03, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/01/06 10:47:03, 2] smbd/server.c:exit_server(571)
  Closing connections
[2005/01/06 10:47:03, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2005/01/06 10:47:03, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2005/01/06 10:47:03, 3] smbd/server.c:exit_server(614)
  Server exit (Caught TERM signal)
[2005/01/06 10:48:17, 0] smbd/server.c:main(760)
  smbd version 3.0.7-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[syncspace]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[jobs]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[adraw]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[art_pdfs]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[archive]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[digicam]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[office_pdfs]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[vncdirectory]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[Graphics]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[backuplogs]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[email]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[webpages]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[backup]"
[2005/01/06 10:48:17, 2] param/loadparm.c:do_section(3415)
  Processing section "[RPC]"
[2005/01/06 10:48:17, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:48:17, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:48:17, 2] lib/interface.c:add_interface(79)
  added interface ip=192.168.0.15 bcast=192.168.0.255 nmask=255.255.255.0
[2005/01/06 10:48:17, 3] smbd/server.c:main(790)
  loaded services
[2005/01/06 10:48:17, 3] smbd/server.c:main(805)
  Becoming a daemon.
[2005/01/06 10:48:17, 2] lib/tallocmsg.c:register_msg_pool_usage(57)
  Registered MSG_REQ_POOL_USAGE
[2005/01/06 10:48:17, 2] lib/dmallocmsg.c:register_dmalloc_msgs(71)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2005/01/06 10:48:17, 3] printing/printing.c:start_background_queue(1168)
  start_background_queue: Starting background LPQ thread
[2005/01/06 10:48:17, 0] lib/util_sock.c:open_socket_in(708)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2005/01/06 10:48:17, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/01/06 10:48:17, 2] smbd/server.c:exit_server(571)
  Closing connections
[2005/01/06 10:48:17, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2005/01/06 10:48:17, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2005/01/06 10:48:17, 3] smbd/server.c:exit_server(614)
  Server exit (Caught TERM signal)
[2005/01/06 10:49:35, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:49:35, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:49:35, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:49:35, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:49:35, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:49:35, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:49:35, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:51:09, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:51:09, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:51:09, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:51:09, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:52:25, 0] smbd/server.c:main(760)
  smbd version 3.0.7-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[syncspace]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[jobs]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[adraw]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[art_pdfs]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[archive]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[digicam]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[office_pdfs]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[vncdirectory]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[Graphics]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[backuplogs]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[email]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[webpages]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[backup]"
[2005/01/06 10:52:25, 2] param/loadparm.c:do_section(3415)
  Processing section "[RPC]"
[2005/01/06 10:52:25, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:52:25, 3] param/loadparm.c:lp_add_ipc(2382)
  adding IPC service
[2005/01/06 10:52:25, 2] lib/interface.c:add_interface(79)
  added interface ip=192.168.0.15 bcast=192.168.0.255 nmask=255.255.255.0
[2005/01/06 10:52:25, 3] smbd/server.c:main(790)
  loaded services
[2005/01/06 10:52:25, 3] smbd/server.c:main(805)
  Becoming a daemon.
[2005/01/06 10:52:25, 2] lib/tallocmsg.c:register_msg_pool_usage(57)
  Registered MSG_REQ_POOL_USAGE
[2005/01/06 10:52:25, 2] lib/dmallocmsg.c:register_dmalloc_msgs(71)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2005/01/06 10:52:25, 3] printing/printing.c:start_background_queue(1168)
  start_background_queue: Starting background LPQ thread
[2005/01/06 10:52:25, 0] lib/util_sock.c:open_socket_in(708)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2005/01/06 10:52:26, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/01/06 10:52:26, 2] smbd/server.c:exit_server(571)
  Closing connections
[2005/01/06 10:52:26, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2005/01/06 10:52:26, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2005/01/06 10:52:26, 3] smbd/server.c:exit_server(614)
  Server exit (Caught TERM signal)
[2005/01/06 10:54:01, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:01, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:01, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:01, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:01, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:01, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:01, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:01, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:01, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:02, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:02, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:02, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:02, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:02, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:02, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]
[2005/01/06 10:54:02, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!
[2005/01/06 10:54:02, 0] smbd/server.c:open_sockets_smbd(420)
  tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1466)
  PANIC: tdb_reopen_all failed.
[2005/01/06 10:54:02, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 5 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x822edd0]
   #3 /usr/sbin/smbd(main+0x3bc) [0x822fb0e]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0x102) [0x401997b6]

---

### Post by mjpowersjr on 2005-01-06
Just wanted to give everyone a update, It seems to be bad Hardware causing the troubes, I setup a temporary file server for the company, while ubuntu installs on a new maxtor drive :) thanks for the help. - Mike Powers

---

### Post by jdodson on 2005-01-06
[QUOTE=mjpowersjr]Just wanted to give everyone a update, It seems to be bad Hardware causing the troubes, I setup a temporary file server for the company, while ubuntu installs on a new maxtor drive :) thanks for the help. - Mike Powers[/QUOTE]

i have personally had more harddrives go bad than anything else.  they are the most unreliable piece on a computer.  then again they move more than any other computer component.

---

### Post by nocturn on 2005-01-07
This looks strange to me:
[2005/01/06 10:54:02, 0] tdb/tdbutil.c:tdb_log(725)
tdb(/var/run/samba/gencache.tdb): tdb_reopen: file dev/inode has changed!

Maybe the directory has been corrupted, or there are problems with your filesystem/HD.
To rule this out, I recommend booting with the livecd and running an fsck on it.

What filesystem are you using?

---

### Post by siennalizard on 2006-02-27
Hello,
I've been having this problem, too (with Breezy, however). Superficial symptoms appear to be masses of "Segfault in Samba" e-mails every day, and obviously a very large logfile (as mentioned).

In a leap of faith (it's not really an essential production box, and I don't use Samba on it a great deal, anyway), I stopped the daemon, deleted all the runtime files under /var/run/samba/ and restarted the daemon. That seems to have stopped the segfaults, but I'll keep you all posted. All the required files were recreated.

Best wishes,
J.

---

