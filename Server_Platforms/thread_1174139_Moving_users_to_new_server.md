---
title: "Moving users to new server"
date: 2009-05-30
forum: Server Platforms
---

### Post by kfleten on 2009-05-30
I want to move existing users on a Edubuntu server to a new server. Is there a easy way to to this, keeping the same credentials ?

---

### Post by bluefrog on 2009-05-30
/etc/passwd, /etc/group and /etc/shadow should do the trick (not the complete content though, only what you are interested in)

---

### Post by albinootje on 2009-05-30
> **bluefrog said:**
> /etc/passwd, /etc/group and /etc/shadow should do the trick (not the complete content though, only what you are interested in)

Indeed.
But perhaps the OP is also using Samba users, and perhaps even LDAP ?

---

### Post by kfleten on 2009-06-05
There is no Samba or LDAP users on the system, so I made a copy of /etc/passwd, /etc/group and /etc/shadow. I copied the files from a server running 8.10. Then I installed a new server with 9.04, and replaced /etc/passwd, /etc/group and /etc/shadow with the copies I had taken.

After this, any atempt of loging in with any passwords on any users failed :-(

Reboot did not solve the login problem. At this point keyboard and mouse still worked. Then I started 9.04 in recovery mode and changed password. After this, keyboard and mouse did not work anymore ! Seems like the same problem I had here:  [http://ubuntuforums.org/showthread.php?t=1138276](http://ubuntuforums.org/showthread.php?t=1138276)

How do I overcome this ?

---

### Post by albinootje on 2009-06-05
> **kfleten said:**
> I copied the files from a server running 8.10. Then I installed a new server with 9.04, and replaced /etc/passwd, /etc/group and /etc/shadow with the copies I had taken.

Here was your mistake. (This might have been OK when the Ubuntu release was the same and you have similar software running on both machines)

You should have removed all the other lines from those files *except* the lines that were strictly about your users. 
And after that you should have inserted those lines about your users into those files.

Backups in the form of /etc/passwd- are on your system, use a bootable cdrom or usb-stick to find out, and correct it.

But better.. there's backups in /var/backups/ which should be a copy of the original, see here.. unless after a reboot those would be overwritten too.. (I don't know how that is scheduled).
```

sudo diff /etc/passwd /etc/passwd-
38a39
> clamav:x:117:129::/var/lib/clamav:/bin/false

sudo diff /etc/passwd /var/backups/passwd

```
Check the differences yourself first!

---

### Post by kfleten on 2009-06-09
Thanks - I learned a lot from this, and finally got it working by copying and pasting various content from old and new passwd files. Unfortunately, my shadow file was not backed up, so I created a new and gave all the users the same password and told them to change it themselves as the first thing after login :o

---

