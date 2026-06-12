---
title: "Remove history in bash for root, how?"
date: 2012-07-26
forum: Security
---

### Post by Bufeu on 2012-07-26
I wanted to delete my command history in bash, so I ran *history -c*. Everything was fine. But when I did that as root, the history "disappeared temporary". When logging out from root and logging in again, the history was still left. How can I delete the commands I've written when I have been using *sudo*?

---

### Post by ajgreeny on 2012-07-26
Using a sudo command from your own user login will not be in the root system files but still in your own hidden user's .bash_history file.  As there is no enabled root user account in ubuntu, there will be no root version of bash history, as far as I'm aware.

Use gedit to open that hidden file which is in your own home folder, and if you want to you can delete the lines which were sudo commands, and then save the file.  I'm sure it will be possible to use grep and pipe to sed or awk to delete those lines with a single command, but I am not a bash guru so I'm afraid I can not tell you how to do that.

EDIT:
For my own edification I have just found out how.  This command will delete all lines starting with sudo in your user bash history file when run from your user terminal; no need for **grep**.
```
sed -i '/sudo/d' .bash_history
```

---

### Post by Bufeu on 2012-07-26
Many thanks! I love the community here! :D

---

### Post by steeldriver on 2012-07-26
just an fyi recent sudo commands will also be visible in /var/log/auth.log

---

