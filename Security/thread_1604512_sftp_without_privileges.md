---
title: "sftp without privileges?"
date: 2010-10-24
forum: Security
---

### Post by PJay3 on 2010-10-24
Hi
Forgive me for my total lack of knowledge but my question is this:

Ive been copying files to my server in terminal using ssh (scp) logging in as $user, however I just found out about sftp, so I opened up nautilus and point it towards 
"sftp://$user@server_ip" which opened up fine although I expected to just be in my $user directory (or limited to it) instead I was in the / directory with the option if i wanted, to delete any file or directory on the server without even a sudo password.
Is this normal practice to have root privileges with sftp? or is there a setting to only let me edit and delete files belonging to $user that logged in?

PJay

---

### Post by cariboo on 2010-10-24
You only have the same permissions as you would if you are working on the server directly. You don't have admin privileges when using sftp and nautilus as a normal user.

You can prove this, by trying to create a directory in / of the remote computer.

---

### Post by PJay3 on 2010-10-24
ah yes, your right. my mistake. I just didn't want to be able to actually delete something i shouldn't have. That's great sftp works like a charms for transferring music and keeping the place organised, and when I need access to a root directory, ill just ssh in and sudo :)

thank you for clearing that up for me

PJay

---

