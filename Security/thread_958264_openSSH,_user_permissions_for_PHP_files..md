---
title: "openSSH, user permissions for PHP files."
date: 2008-10-25
forum: Security
---

### Post by enzo12345 on 2008-10-25
Is it possible to allow a user to have execute permissions, but then block them from reading, writing, moving and copying that same file?

Thanks.

---

### Post by enzo12345 on 2008-10-25
anyone?

---

### Post by KeyserSoze93 on 2008-10-27
Chmod is your friend:

```
chmod 711 file.php
```

The format is owner, group, other and the numbers are:

7 = read, write exec

6 = read, write

4 = read

2 = write

1 = exec

So it means you can do anything, any anyone else can one execute the file.

---

### Post by tomchuk on 2008-10-27
No, the user will need read permission to be able to execute the script. You could make the file owned by root:root (chown root:root file.php) and set its permissions to 0700 (chmod 0700 file.php), then add a sudo rule that would let users run the script through sudo. visudo and add a line like "user1,user2 ALL = NOPASSWD:/path/to/file.php". Just make absolutely sure that the script you are running is safe to run as root, and properly escapes all user input.

---

### Post by jerome1232 on 2008-10-28
KeyserSoze93 is correct they don't need read permissions. (I just removed read permissions from /usr/bin/nmap and I can still run it).

---

### Post by hyper_ch on 2008-10-28
you forgot

5 = read, exec

---

### Post by tomchuk on 2008-10-28
> **jerome1232 said:**
> KeyserSoze93 is correct they don't need read permissions. (I just removed read permissions from /usr/bin/nmap and I can still run it).

Read the thread title - we're talking about a php script. In order for the php interpreter (running as the user) to run the script, the user needs read access to the script.

---

### Post by hyper_ch on 2008-10-28
an option I see is to precompile the php scripts with zend or something.

---

