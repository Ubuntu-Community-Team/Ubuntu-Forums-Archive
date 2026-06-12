---
title: "rdiff-backup remote site problems???"
date: 2008-07-23
forum: Server Platforms
---

### Post by neilevan814 on 2008-07-23
Hi I am trying to backup to my host server and I think there is a glitch in the script...don't know if this is the best place for this issue, but maybe someone can decipher this python code...much thanks for your help

neil@ubuntu:~$ rdiff-backup /home [email]xxxxxxx@74.xxx.yyy.zzz::/home/webwishd/Desktop/remote-dir/home.back[/email]up
[email]webwishd@74.xxx.yyy.zzz[/email]'s password: 
Exception 'long int too large to convert to int' raised of class '<type 'exceptions.OverflowError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 319, in Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 76, in cmdpair2rp
    if cmd: conn = init_connection(cmd)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 139, in init_connection
    check_connection_version(conn, remote_cmd)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 147, in check_connection_version
    try: remote_version = conn.Globals.get('version')
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 447, in __call__
    return apply(self.connection.reval, (self.name,) + args)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 367, in reval
    result = self.get_response(req_num)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 314, in get_response
    try: req_num, object = self._get()
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 239, in _get
    data = self._read(length)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 209, in _read
    try: return self.inpipe.read(length)

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 319, in Main
    rps = map(SetConnections.cmdpair2rp, cmdpairs)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 76, in cmdpair2rp
    if cmd: conn = init_connection(cmd)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 139, in init_connection
    check_connection_version(conn, remote_cmd)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 147, in check_connection_version
    try: remote_version = conn.Globals.get('version')
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 447, in __call__
    return apply(self.connection.reval, (self.name,) + args)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 367, in reval
    result = self.get_response(req_num)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 314, in get_response
    try: req_num, object = self._get()
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 239, in _get
    data = self._read(length)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 209, in _read
    try: return self.inpipe.read(length)
OverflowError: long int too large to convert to int
neil@ubuntu:~$

---

