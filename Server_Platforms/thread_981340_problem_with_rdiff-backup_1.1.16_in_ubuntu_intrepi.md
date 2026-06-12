---
title: "problem with rdiff-backup 1.1.16 in ubuntu intrepid after upgrading from hardy"
date: 2008-11-13
forum: Server Platforms
---

### Post by linuxjohnny on 2008-11-13
Hi,

I'm having some troubles with rdiff-backup 1.1.16.

I hade a backup directory, which I had been using with version 1.1.15. After 
the upgrade, I wanted to do a backup. The backup directory ran out of space.

rdiff-backup --check-destination-dir fails with the error appended below. I 
tried this with verison 1.1.16 and 1.2.2. Could anyone give me a pointer, what 
to do?

Many thanks in advance,

Hans-Christian


# rdiff-backup --check-destination-dir /backup/mymachine
Exception '[Errno 0] Error: '/backup/mymachine'' raised of class '<type 
'exceptions.OSError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in 
error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 319, in 
Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 
78, in cmdpair2rp
    return rpath.RPath(conn, filename).normalize()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 767, in 
__init__
    else: self.setdata()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 791, in 
setdata
    self.data = self.conn.C.make_file_dict(self.path)

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in 
error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 319, in 
Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 
78, in cmdpair2rp
    return rpath.RPath(conn, filename).normalize()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 767, in 
__init__
    else: self.setdata()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 791, in 
setdata
    self.data = self.conn.C.make_file_dict(self.path)
OSError: [Errno 0] Error: '/backup/mymachine'






Next try with rdiff-backup 1.2.2





# /usr/local/bin/rdiff-backup -v4 --check-destination-dir /backup/mymachine
Using rdiff-backup version 1.2.2
Exception '[Errno 0] Error: '/backup/mymachine/'' raised of class '<type 
'exceptions.OSError'>':
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/Main.py", line 
304, in error_check_Main
    try: Main(arglist)
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/Main.py", line 
321, in Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/usr/local//lib/python2.5/site-
packages/rdiff_backup/SetConnections.py", line 78, in cmdpair2rp
    return rpath.RPath(conn, filename).normalize()
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
868, in __init__
    else: self.setdata()
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
892, in setdata
    self.data = self.conn.rpath.make_file_dict(self.path)
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
277, in make_file_dict
    return C.make_file_dict(filename)

Traceback (most recent call last):
  File "/usr/local/bin/rdiff-backup", line 30, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/Main.py", line 
304, in error_check_Main
    try: Main(arglist)
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/Main.py", line 
321, in Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/usr/local//lib/python2.5/site-
packages/rdiff_backup/SetConnections.py", line 78, in cmdpair2rp
    return rpath.RPath(conn, filename).normalize()
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
868, in __init__
    else: self.setdata()
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
892, in setdata
    self.data = self.conn.rpath.make_file_dict(self.path)
  File "/usr/local//lib/python2.5/site-packages/rdiff_backup/rpath.py", line 
277, in make_file_dict
    return C.make_file_dict(filename)
OSError: [Errno 0] Error: '/backup/mymachine'

---

### Post by billharris on 2008-12-17
I'm having problems with 1.1.16, too, as of about 4 days ago:

Exception '[Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-etc/rdiff-backup-data/rdiff-backup.tmp.0'' raised of class '<type 'exceptions.OSError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)

Exception '[Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-usr-local/rdiff-backup-data/rdiff-backup.tmp.0'' raised of class '<type 'exceptions.OSError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)

Exception '[Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-home-bill/rdiff-backup-data/rdiff-backup.tmp.0'' raised of class '<type 'exceptions.OSError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)
OSError: [Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-usr-local/rdiff-backup-data/rdiff-backup.tmp.0'
Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)
OSError: [Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-etc/rdiff-backup-data/rdiff-backup.tmp.0'
Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin, force)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 751, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/var/lib/python-support/python2.5/rdiff_backup/fs_abilities.py", line 144, in init_readwrite
    subdir.mkdir()
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 909, in mkdir
    self.conn.os.mkdir(self.path)
OSError: [Errno 95] Operation not supported: '/media/Ext Drive/backups/rdiff-backup-moenchweiler-home-bill/rdiff-backup-data/rdiff-backup.tmp.0'

That's the result of running a script with three rdiff-backup commands for different directories.  I haven't changed the script (well, except to comment out two for testing and then to re-enable them) in quite a while, and it has always worked successfully before.

Thoughts?  I'd like to do a backup again.

---

### Post by billharris on 2008-12-20
Someone on the rdiff-backup mailing list noted that the above error was likely due to not being able to execute mkdir /media/Ext Drive/backups/rdiff-backup-moenchweiler-etc/rdiff-backup-data/rdiff-backup.tmp.0.  Sure enough, that fails, even with sudo, and even with all the directories having permissions 777.

I thought [http://ubuntuforums.org/showthread.php?t=111131](http://ubuntuforums.org/showthread.php?t=111131) might help, but it only talks about things that show up in fstab, and my external drive doesn't show up there.

Any ideas how I can make that command work in an external USB drive that gets automounted when it's plugged in?  It used to work as recently as December 13, but something must have changed, and I can't figure out what it is.

---

