---
title: "chpasswd in sudoers"
date: 2012-01-16
forum: Server Platforms
---

### Post by cdspace on 2012-01-16
I've searched everywhere I can think of, and am not able to get this to work. I need to add the user "www-data" to the sudoers file to run two commands with no password, namely "/usr/sbin/useradd" and "usr/sbin/chpasswd". I need this for a script that will automatically create a user and set their password. the line I'm using in the sudoers file is below. I've tested removing the useradd references, and the script fails. However, I can't get the chpasswd command to work without the password.

sudoers line
```
www-data hostname=NOPASSWD: /usr/sbin/useradd, /usr/sbin/chpasswd
```

test.sh
```
#!/bin/sh
sudo useradd -m $1
echo 1 - user added
sudo echo "$1:$2" | chpasswd
echo 2 - pass changed

```

---

### Post by cdspace on 2012-01-17
Just to wrap this up, I found a workaround. Instead of using the chpasswd command, I tweaked it to use mkpasswd in the useradd statement, as below. Cheers!

```
sudo useradd -p $(mkpasswd -s -m sha-512 $password) -m $username
```

---

