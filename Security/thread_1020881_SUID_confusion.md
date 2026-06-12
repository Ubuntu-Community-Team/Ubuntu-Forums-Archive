---
title: "SUID confusion"
date: 2008-12-24
forum: Security
---

### Post by mantas1969 on 2008-12-24
I just recently installed Ubuntu on my laptop after using Fedora for a while.  Here is my situation:
I have wireless working except that it won't work after a reboot.  I then have to ifdown, ifup wlan0 which fixes the problem.
So I wrote bash script that simply runs the above code.  I have changed the owner of the script to root and I have set the SUID.
But when I run the script I still get a permission error on the var/run/network/ifstate file.
Shouldn't the script be running as root and therby have permission to var/run/network/ifstate?

Thanks

---

### Post by bodhi.zazen on 2008-12-26
I am not sure I have an answer to your question, but as you know Ubuntu uses sudo.

So, rather then setting the SUID, consider either call the script with sudo or add it to /etc/rc.local

---

### Post by mantas1969 on 2008-12-28
Thank you for responding to my question.

Will scripts executed in /etc/rc.local have root permission?
The problem is that I as a privileged user can manually re-establish the wireless connection but a standard user can not, so I would like to set up the wireless connection for them

---

### Post by bodhi.zazen on 2008-12-28
yes, /etc/rc.local is executed as root.

---

