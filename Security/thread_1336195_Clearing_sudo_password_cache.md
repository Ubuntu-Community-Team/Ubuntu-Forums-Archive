---
title: "Clearing sudo password cache"
date: 2009-11-24
forum: Security
---

### Post by Correnos on 2009-11-24
I know that in the sudoers file you can add a line to set the password timeout to 0, but I'm looking for a command that can be entered to clear the password cache (if that's the right term) manually. Is there such a tool? Thanks for any response.

---

### Post by sisco311 on 2009-11-24
When a user runs a command with sudo a file with the same name as the user's name is created in the /var/run/sudo directory or if the file already exist the last modification time of the file is updated to the current time. If the timestamp is set to a non-zero value, sudo checks the last modification time of the file to determine if the user is allowed to run the command without a password.

You can invalidate the user's timestamp by setting the time on it to the Epoch:
```
sudo -k
```
or by deleting the file:
```
sudo -K
```

for more info:
```
man sudo
```

---

