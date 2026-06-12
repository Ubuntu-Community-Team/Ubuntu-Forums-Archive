---
title: "Cant Logon to my new server"
date: 2009-06-01
forum: Server Platforms
---

### Post by TheMagician001 on 2009-06-01
Hello everyone.. I am having problems with my new server I have just installed it onto a machine and cannot logon to the  server

I am using Ubuntu server 9.04   with LAMP + OPEN Ssh

when  i try  ssh (ADDRESS) -p 22

it tells me connection refused...      can someone tell me how to fix this? also my firewall is open on port 22

Thanks
 mike

---

### Post by x22 on 2009-06-01
is the daemon running?  sshd

---

### Post by TheMagician001 on 2009-06-01
Not sure how do I check that...? I thought it came automatiically with ubuntu...

when I am local I get the above error in my first post... but when I goto a friends house and try I get this message here.....

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
2f:23:71:a3:5e:a8:49:ef:a8:d3:5a:ed:52:9c:44:32.
Please contact your system administrator.
Add correct host key in /home/mike/.ssh/known_hosts to get rid of this message.
Offending key in /home/mike/.ssh/known_hosts:3
RSA host key for mdsmallenginerepair.com has changed and you have requested strict checking.
Host key verification failed.

---

### Post by codysoyland on 2009-06-01
On your friend's machine: this is a common error if the remote key has changed (which happened because you made a fresh install of linux). All you need to do is remove line 3 from  /home/mike/.ssh/known_hosts and it should then work.

---

### Post by TheMagician001 on 2009-06-01
I found the solution to my problem at 

[http://ubuntuforums.org/showthread.php?t=1119372&highlight=Host+key+verification+failed](http://ubuntuforums.org/showthread.php?t=1119372&highlight=Host+key+verification+failed).

can anyone tell me how to delete this thread that I created

---

### Post by cariboo on 2009-06-01
We don't delete threads, as it may help someone else with the same problem. I would suggest you add solved to the title.

---

