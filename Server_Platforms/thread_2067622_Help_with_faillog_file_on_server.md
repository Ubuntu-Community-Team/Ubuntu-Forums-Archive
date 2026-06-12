---
title: "Help with faillog file on server"
date: 2012-10-07
forum: Server Platforms
---

### Post by Bitwarx on 2012-10-07
Hello all,

My faillog file (/var/log/faillog) showed weird symbols and I deleted them. Now I get this response when running "faillog" command.

> 
faillog: Failed to get the entry for UID 0
faillog: Failed to get the entry for UID 1
faillog: Failed to get the entry for UID 2
faillog: Failed to get the entry for UID 3
faillog: Failed to get the entry for UID 4
faillog: Failed to get the entry for UID 5
faillog: Failed to get the entry for UID 6
faillog: Failed to get the entry for UID 7
faillog: Failed to get the entry for UID 8
faillog: Failed to get the entry for UID 9
faillog: Failed to get the entry for UID 10
faillog: Failed to get the entry for UID 13
faillog: Failed to get the entry for UID 33
faillog: Failed to get the entry for UID 34
faillog: Failed to get the entry for UID 38
faillog: Failed to get the entry for UID 39
faillog: Failed to get the entry for UID 41
faillog: Failed to get the entry for UID 65534
faillog: Failed to get the entry for UID 100
faillog: Failed to get the entry for UID 101
faillog: Failed to get the entry for UID 102
faillog: Failed to get the entry for UID 103
faillog: Failed to get the entry for UID 104
faillog: Failed to get the entry for UID 105
faillog: Failed to get the entry for UID 106
faillog: Failed to get the entry for UID 107
faillog: Failed to get the entry for UID 108
faillog: Failed to get the entry for UID 109
faillog: Failed to get the entry for UID 110
faillog: Failed to get the entry for UID 111


Please, how I can solve this?? Now faillog is empty...

Thanks in advance and sorry my english :(

---

### Post by 2F4U on 2012-10-07
The file /var/log/faillog is not in human-readable format. The command faillog can be used to read it.

[https://help.ubuntu.com/community/LinuxLogFiles#Non-Human-Readable_Logs](https://help.ubuntu.com/community/LinuxLogFiles#Non-Human-Readable_Logs)

---

### Post by Bitwarx on 2012-10-07
> **2F4U said:**
> The file /var/log/faillog is not in human-readable format. The command faillog can be used to read it.

[https://help.ubuntu.com/community/LinuxLogFiles#Non-Human-Readable_Logs](https://help.ubuntu.com/community/LinuxLogFiles#Non-Human-Readable_Logs)

Oh! I see... I really messed up!

Can original faillog be recoverable?

---

### Post by 2F4U on 2012-10-07
Why do you think you messed up? As far as I understand, you deleted the file. Now, it is just a log file, so deleting shouldn't do any harm to the system since it will be recreated. Of course, the old content is gone and if you need it, there are certainly ways to recover it (Google can help here).

---

### Post by Bitwarx on 2012-10-07
> **2F4U said:**
> Why do you think you messed up? As far as I understand, you deleted the file. Now, it is just a log file, so deleting shouldn't do any harm to the system since it will be recreated. Of course, the old content is gone and if you need it, there are certainly ways to recover it (Google can help here).

You're right. Thank you.

@[2F4U]("http://ubuntuforums.org/member.php?u=1357554")

Thank you too for give me the URL.

:P

---

