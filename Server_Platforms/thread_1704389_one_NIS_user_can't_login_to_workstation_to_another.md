---
title: "one NIS user can't login to workstation to another"
date: 2011-03-10
forum: Server Platforms
---

### Post by Percle on 2011-03-10
Hi,
network in my lab is running NIS and NFS.
one of our workstations (say, workstation A) died, so we replaced it with a new computer.

A user emailed me saying that he can't login to the new workstation A. I instructed him to do:

mv ~/.ssh/known_hosts ~/.ssh/known_hosts_old

He did it, and then got back to me with the following message:


===========starting user's email=====================
Starting from my login to Workstation B, this is what I get:

% mv ~/.ssh/known_hosts ~/.ssh/known_host_old
% WORKSTATIONA
The authenticity of host 'WORKSTATIONA)' can't be established.
RSA key fingerprint is c2:b9:d9:64:b3:03:f2:bc:2d:4f:7c:4f:c7:cb:2f:b6.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'WORKSTATIONA,' (RSA) to the list of known hosts.
USERNAME@WORKSTATIONA's password: 
Permission denied, please try again.
USERNAME@WORKSTATIONA's password: 
Permission denied, please try again.
USERNAME@WORKSTATIONA's password: 
Permission denied (publickey,password).
% 

So, as I mentioned before, I just need a new password for WORKSTATIONA
===============end of email===================================

I changed the actual name to the capital WORKSTATIONA.


The first thing caught my eye is that he didn't type "ssh WORKSTATIONA". Instead, he simply typed "WORKSTATIONA".  I assume there is some alias or something, but i can't find it. I remember that he use something other than bash (maybe csh?)


The second thingis that,  he was trying to login to WORKSTATIONA from WORKSTATIONB  so obviously he can login to our system because (WORKSTATIONA and WORKSTATIONB ) link to the same NIS and NFS server. Does anybody have any idea about this? 

thank you very much


Besides, just FYI, I can ssh from WORKSTATIONB TO WORKSTATIONA using my non-administrative account without any problem.






Thanks for reading this post!

---

### Post by Percle on 2011-03-13
Turn out that the user is the only one in my lab who uses tcsh instead of bash, and i forgot to install tcsh. problem solved.

---

