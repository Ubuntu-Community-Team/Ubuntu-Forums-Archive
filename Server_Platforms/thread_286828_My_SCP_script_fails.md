---
title: "My SCP script fails"
date: 2006-10-28
forum: Server Platforms
---

### Post by aktiv on 2006-10-28
Hi

I'm working on a few scripts to backup my files and send them to another computer. My problem is that scp ends the file transfer before it is finished. The file i'm trying to send is 52 mb. When I write the command manually it works just fine. The script also sends a logfile half a mb in size with no problems. Any ideas?

Here is the script, which is really just copied from the intermediate linux course hosted on linux.org:

set password [lindex $argv 1]

spawn /usr/bin/scp /home/loke/Backup/today.backup.tar.gz [lindex $argv 0]
expect "password:"
send "$password\r"
# error occurs here
expect eof

spawn /usr/bin/scp /home/loke/Backup/today.backup.log [lindex $argv 0]
expect "password:"
send "$password\r"
expect eof

aktiv

---

### Post by MJN on 2006-10-28
Not quite the answer you're looking for I'd suggest using **rsync** instead - not only will it handle multiple files with ease (no need to tar them) but next time you back the files up it'll only send the ones that have changed since the last backup... indeed it'll only even send the *parts* of the those files that have changed! Speeds backups up no end! (Okay, so you're only sending 52MB but using SCP isn't really scalable - I backup a 30GB server every single day and it takes just a couple of minutes.... because only a small subset of the files are ever changing).

Mathew

---

