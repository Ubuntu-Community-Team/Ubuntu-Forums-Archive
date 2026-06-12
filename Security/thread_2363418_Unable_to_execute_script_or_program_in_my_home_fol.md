---
title: "Unable to execute script or program in my home folder"
date: 2017-06-09
forum: Security
---

### Post by mbogevik on 2017-06-09
I have removed my xubuntu 12.04/64 and installed xubuntu 16.04/64.  Then I mounted back my second drive as /home. (same user name as before)
After getting everything working my final problem is that I am not able to execute anything in my home folder like i did in 12.04.  Things like Conky and teamspeak-server-64 can not be executed from terminal or from any startup script (boot).  Running executable directly or a .sh script both fails:

user@PC:~$ ./startconky.sh
bash: ./startconky.sh: Permission denied
user@PC:~$

I have checked user rights and that flag "Allow this file to run as a program" is checked:

ls -l ~
-rwxrwxr-x 1 user users    31 okt.  10  2013 startconky.sh

The auto-mount line in /etc/fstab, unchanged from 12.04 :
UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home  ext4 auto,exec,users,rw,nodev,nosuid,noatime 0 2

Is there anything difference in setup on what you can do in home folder in 16.04 compared to 12.04 ?  Anything more I can check ?

---

### Post by mbogevik on 2017-06-10
Oh my... It turns out that there is a difference in how Fstab work in 16.04 compare to 12.04.  When I mount the second disk with parameter "users", then default then is "noexec".  Obviously I can no longer define "exec" parameter before "users" as then "users" will define "noexec"...

So changing line from
[COLOR=#000000]UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home ext4 auto,exec,users,rw,nodev,nosuid,noatime 0 2
to
[/COLOR]UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home  ext4 auto,users,exec,rw,nodev,nosuid,noatime 0 2[COLOR=#000000]
works ![/COLOR]

---

