---
title: "git account infected with intruder SSH key and crontab"
date: 2020-06-23
forum: Security
---

### Post by holiday on 2020-06-23
I have the infection described here 

[https://ubuntuforums.org/showthread.php?t=2395684](https://ubuntuforums.org/showthread.php?t=2395684)


My git crontab was set to this :

1 1 */2 * * /home/git/.configrc/a/upd>/dev/null 2>&1
@reboot /home/git/.configrc/a/upd>/dev/null 2>&1
5 8 * * 0 /home/git/.configrc/b/sync>/dev/null 2>&1
@reboot /home/git/.configrc/b/sync>/dev/null 2>&1  
0 0 */3 * * /tmp/.X25-unix/.rsync/c/aptitude>/dev/null 2>&1
SSH access is by key only but somehow someone got in, set this crontab, and cleared the git authorized keys file to contain only their key.

<keydata> mdrfckr
I have set the firewall to deny SSH
set a non-standard port
cleared the crontab
removed the /home/git/.configrc directory
rebooted
checked for /tmp/.X25-unix directory but did not find it.


I am concerned that the infection is persistent on the gitserver or has infected one of the clients. 

It *looks* like the intruder did not acquire root access (git user has very limited privs on the server). None of the directories listed in the cron or in any of the files in the .configrc directory require root access, but still I am concerned. 

I understand that in the interest of absolute caution I should wipe the server. That would not be a big job/ I've already moved its BIND server to another host without difficulty. But I'd like to sleuth about a bit. I have time to do it  

What to do? Where to look?

---

### Post by TheFu on 2020-06-24
Do what the other thread says.

---

