---
title: "Problem with fail2ban"
date: 2007-05-24
forum: Server Platforms
---

### Post by Matl on 2007-05-24
Hi,

I have the following problem with fail2ban on our ubuntu-server.

I have it configured to use the hosts.deny. Thats the only way because of our configuration here. But if someone tried to get in it blocks the ip. Thats ok. But if that one tries again to get in it adds the same ip again to the hosts.deny file. 

Is there any way for the program to check whether the  ip is in the file and then not to block it again? I used fail2ban and denyhosts but they both have that issue - or is there any other program?

Thanks,

Martin

---

### Post by MJN on 2007-05-24
If a particular IP is banned how is it getting as far as attempting to login again (to be subsequently re-banned)...?

Mathew

---

