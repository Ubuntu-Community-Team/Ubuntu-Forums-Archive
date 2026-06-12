---
title: "rkhunter: Should I be concerned about any of these warnings?"
date: 2012-02-26
forum: Security
---

### Post by donsy on 2012-02-26
```
sudo cat /var/log/rkhunter.log | grep Warning

[14:51:41]   /usr/bin/unhide.rb                              [ Warning ]
[14:51:41] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: a /usr/bin/ruby -w script text executable
[14:53:02]   Checking for passwd file changes                [ Warning ]
[14:53:02] Warning: User 'postfix' has been added to the passwd file.
[14:53:02]   Checking for group file changes                 [ Warning ]
[14:53:02] Warning: Group 'postfix' has been added to the group file.
[14:53:02] Warning: Group 'postdrop' has been added to the group file.
[14:53:03]   Checking for hidden files and directories       [ Warning ]
[14:53:03] Warning: Hidden directory found: /etc/.java
[14:53:03] Warning: Hidden directory found: /dev/.udev
[14:53:03] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

```

---

### Post by Gremlinzzz on 2012-02-26
All ways iv gotten warnings from rkhunter.
try a scan with chkrootkit and see if you get any thing.

---

### Post by CharlesA on 2012-02-26
Sounds like you installed postfix. Other than that, it looks fine.

---

### Post by Dangertux on 2012-02-26
Line by line

```

[14:51:41]   /usr/bin/unhide.rb                              [ Warning ]
[14:51:41] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: a /usr/bin/ruby -w script text executable

```

This is just saying you have a script that is in your path -- this is often the sign of compromise (hooking a command), however in this particular case that's not true this application just happens to be a ruby script.
```

[14:53:02]   Checking for passwd file changes                [ Warning ]
[14:53:02] Warning: User 'postfix' has been added to the passwd file

```

Looks like a Charles said you installed postfix since the baseline file for rkhunter was created, doing so modified /etc/passwd (if you didn't install postfix than something is up, otherwise don't sweat it).

```

[14:53:02]   Checking for group file changes                 [ Warning ]
[14:53:02] Warning: Group 'postfix' has been added to the group file.
[14:53:02] Warning: Group 'postdrop' has been added to the group file.

```
Same as the last.

```

[14:53:03]   Checking for hidden files and directories       [ Warning ]
[14:53:03] Warning: Hidden directory found: /etc/.java
[14:53:03] Warning: Hidden directory found: /dev/.udev
[14:53:03] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

```

These are standard warnings given when running rkhunter on a Ubuntu system. Ubuntu does things slightly different than other more traditional distros like RHEL, so rkhunter isn't expecting hidden files in these places, however these are normally present in any Ubuntu install by default.

Hope this helps

---

### Post by fonsi2099 on 2012-03-30
I'm concerned cause, today I get this, 

Warning: The file properties have changed:
[13:50:10]          File: /usr/bin/ldd
[13:50:10]          Current hash: f57677684caef9ea334e8ec238537703e3bbc616
[13:50:10]          Stored hash : d61d46508e2138f4cc8e1713a0fbad2bdfdec315
[13:50:10]          Current inode: 677294    Stored inode: 657244
[13:50:10]          Current size: 5281    Stored size: 5279
[13:50:10]          Current file modification time: 1331086340 (07-Mar-2012 03:12:20)
[13:50:10]          Stored file modification time : 1317761742 (04-Oct-2011 22:55:42)
[13:50:10] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

shall I do what?

Thank you ver much

---

### Post by haqking on 2012-03-30
> **fonsi2099 said:**
> I'm concerned cause, today I get this, 

Warning: The file properties have changed:
[13:50:10]          File: /usr/bin/ldd
[13:50:10]          Current hash: f57677684caef9ea334e8ec238537703e3bbc616
[13:50:10]          Stored hash : d61d46508e2138f4cc8e1713a0fbad2bdfdec315
[13:50:10]          Current inode: 677294    Stored inode: 657244
[13:50:10]          Current size: 5281    Stored size: 5279
[13:50:10]          Current file modification time: 1331086340 (07-Mar-2012 03:12:20)
[13:50:10]          Stored file modification time : 1317761742 (04-Oct-2011 22:55:42)
[13:50:10] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

shall I do what?

Thank you ver much

I suspect you have just upgraded your ldd package and hence the hash issue, good idea to use rkhunter to regenerate hashes before and after updates.

---

### Post by needhelppeeps on 2012-03-30
Why would the database be stored on the machine that is being checked? I would think if someone were in a position to replace files, they could simply update the database, too? Seems like a silly system to me. Surely there is a better way to implement integrity management?

---

### Post by CharlesA on 2012-03-30
Yeah, don't let your box get owned.

If someone has access to your box and can replace the rkhunter database, then you have bigger problems.

---

