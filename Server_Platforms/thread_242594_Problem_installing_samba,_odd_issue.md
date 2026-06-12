---
title: "Problem installing samba, odd issue"
date: 2006-08-23
forum: Server Platforms
---

### Post by Niczi on 2006-08-23
Little background, I had samba up and running and for some reason the config files where corrupted.  So i deleted and removed samba and went to reinstall samba...when I did this, I recieved this message on trying to install it via apt-get:

> niczi@fileserver:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have searched but have not found anything similar to this issue..

Any pointers would be greatly appreciated.

---

### Post by chrisfay on 2006-08-23
How did you remove Samba?

If you did:
sudo apt-get remove samba

That will leave certain files.

Try running 
sudo apt-get --purge remove samba

Then reinstall

Just a thought...

---

### Post by Niczi on 2006-08-23
tried that but no luck...thanks for the suggestion though.

---

### Post by Niczi on 2006-08-23
one thing to note, i do have samba installed but it does not show up anything in the samba directory...

it is just a blank dir

---

### Post by Niczi on 2006-08-24
any one else?

---

### Post by Niczi on 2006-08-24
when i check the log file this is showing in it

> [2006/08/23 21:54:33, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/08/23 21:54:33, 0] param/params.c:OpenConfFile(538)
  params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
        No such file or directory
[2006/08/24 17:42:56, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/08/24 17:42:56, 0] param/params.c:OpenConfFile(538)
  params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
        No such file or directory

---

### Post by snooptodd on 2006-08-25
run this then post the output.
dpkg-query -s samba|grep Status

---

### Post by joehill on 2006-08-26
I just tried to install Samba and I have the same problem.  I haven't done anything strange with my packages and it's a relatively fresh install, so I can't think of what's wrong.  Could this be a bug?  I've tried all kinds of purging and nothing seems to work.

---

### Post by g0dbrz on 2008-05-06
Output:

# dpkg-query -s samba|grep Status
Status: install ok half-configured

---

### Post by dennister on 2008-05-08
I'm having the exact same problem, with the exact same result from querying the status of the installation (from the repos) as quoted below. Mine, too, is a relatively fresh/clean install; I used the server edition at first, and it seemed to install fine, but it then ran into problems, so it was finally simpler to purge and try to reinstall it than try to rectify the situation. That's when I began to experience the issues in this thread.

Anyone found a fix yet?

> **g0dbrz said:**
> Output:

# dpkg-query -s samba|grep Status
Status: install ok half-configured

---

### Post by snooptodd on 2008-05-11
try 

sudo dpkg-reconfigure samba

if samba dosent confgure check the output for errors or post the output.

---

