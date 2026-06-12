---
title: "Mounting Win7 shared drive issue"
date: 2012-01-04
forum: Server Platforms
---

### Post by garfonzo on 2012-01-04
I have a Ubuntu box running in a windows LAN. The Ubuntu box has the following line in /etc/fstab:

```
//192.168.47.130/Data    /hqserver    cifs      credentials=/etc/cifspw,iocharset=utf8,file_mode=0777,dir_mode=0777     0       0

```

This has been working just fine for weeks. My purpose for mounting this is to make backups of the windows folder. 

However, for some reason this mount was disconnected, or dropped, or something. I no longer have access to the windows share at the linux location /hqserver . I ran the mount -a command and there was no output -- no errors, nothing. I pinged the Windows server at 192.168.47.130 and it is reachable. I did an "ls -alF" on root  and this is the output for the /hqserver location 

```
d?????????   ? ?      ?        ?                ? hqserver/
```

Then "cd" into /hqserver and do an "ls -alF" gives me:

```
ls: cannot access .: Cannot allocate memory
total 4
d?????????  ? ?    ?       ?                ? ./
drwxr-xr-x 25 root root 4096 2011-12-19 07:01 ../

```

What the heck is going on!?

---

### Post by garfonzo on 2012-01-04
I found [this ]("http://ubuntuforums.org/showthread.php?t=869994")discussion about precisely the same issue.

---

### Post by garfonzo on 2012-01-04
Fixed!

I followed the instructions on [this]("http://jlcoady.net/windows/how-to-resolve-mount-error12-cannot-allocate-memory-windows-share") site. As pointed out in the discussion linked in the page, the Windows machine needs to be told to act like a file server. I'm glad it worked. If the link goes down, here are the instructions:

[LIST=1]Set “HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\LargeSystemCache” to “1&#8243;.
[/LIST]
[LIST=2]Set “HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\Size” to “3&#8243;.
[/LIST]
[LIST=3]
Restart the “server” service on the windows machine.
[/LIST]

Viola!

---

