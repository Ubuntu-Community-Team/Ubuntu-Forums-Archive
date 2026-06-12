---
title: "Commands not executing"
date: 2008-07-08
forum: Server Platforms
---

### Post by boeman on 2008-07-08
I got a 7.04 server running (bind9, samba, apache2, mysql) that doesn't respond to some commands. First time I noticed it, was when trying to reload bind9. Everytime I needed to reload my zones I had to kill the named process and start it up again.
Yesterday I was fiddling with it through webmin to inspect some suspicious traffic and after setting up monitoring with iptables, the reading of the logfiles failed also.

Now, when I mean failed, I mean the command is launched, you can see it with ps -ax, but it just never ends. The only way to end it, is killing it. I figured an apt-get upgrade and then a reboot might solve some issues, the server wouldn't shutdown. The shutdown -r now will remain in the process list, but the system will not reboot. Since this machine is colocated, I cannot just reach over and press the reset button :)

What could be the problem here? So I might be able to solve it before I call the hostinng company to ask them to reboot the machine.

---

### Post by jamesapnic on 2008-07-08
Hmm I would scan it for rst.b, or other backdoors.  Try running chkrootkit and rkhunter or f-secure.
It seems highly suspect to me.

---

### Post by dca on 2008-07-08
Hmmm, does Ubuntu allow reboot if someone else is logged or TTYed (shelled, SSH) in to the system???  type: _users_ at CLI
 
However, I concur w/ the above post, it does sound suspect.  How many HDD(s) does this server have and how is its RAID set?  Has it been fsck'd?

---

### Post by boeman on 2008-07-08
dca: as far as I know Ubuntu does allow rebooting when ppl are logged in, I always reboot my machines through ssh... About HDDs: I believe there are 5 146Gb SAS disks on a PERC5/i controller in RAID 5. How do you fsck it while mounted?

jamesapnic: I was afraid to get an answer like that. Gonna try to scan the system, but I might have to get back on that :)

---

### Post by boeman on 2008-07-08
chkroot and rkhunter both found the system to be ok...

---

### Post by boeman on 2008-07-09
OK, some more info: the reading of the logfiles didn't fail, it just took forever.

The only important thing atm is that the system will not reboot.

---

### Post by windependence on 2008-07-09
Take a look at the log files using tail.

I seriously don't think you have been hacked. I would bet you have a process somewhere that is hogging resources. Check your process table in top.

-Tim

---

