---
title: "Samba Server"
date: 2008-09-12
forum: Server Platforms
---

### Post by rameshkumarav on 2008-09-12
Hi, 
I have installed samba server on RED-HAT-4, After sharing a folder and making the configuration in samba.conf file i can see it on my machine in GUI, but i can't access it on windows network, what is the problem?

I have made the following configuration.

Workgroup=microhome

[kumar]
        comment = testshare
        guest ok = yes
        path = /home/guru/songs
        browseable = yes
        writeable = yes

encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd

I can access those files using smbclient, but i was unable to access it in windows network, my friend said i have to disable selinux i have also done it but it still does not works. 
i have also disabled iptables in my machine, but still i cant access it on windows network.

but the same config works in my friends machine, we have tried it for more than some 40 times. please help..

---

