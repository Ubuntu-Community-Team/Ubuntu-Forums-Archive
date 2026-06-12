---
title: "Troubleshooting UNIX services"
date: 2010-09-07
forum: Virtualisation
---

### Post by Thund3rstruck on 2010-09-07
Hey guys, I have this nagging problem where my VMWare Server 2.0.2 running on Ubuntu 9.10 server keeps shutting off all my VMs at seemingly random times. 

I asked the VMWare folks about this and they suggested that the host OS (ubuntu 9.10) is likely restarting the service and that I should check the logs to see why the OS is restarting the VMWare service. 

I'm not sure how to do that exactly. I did a seach in /var/log for vmware* and nothing unusual was found. Can anyone give me some tips as to how I could go about trying to determine if Ubuntu is in fact restarting the VMware service and if so why its doing this?

---

### Post by Thund3rstruck on 2010-09-11
Just an update for anyone stumbling on this thread. After several days of analysis, I have determined that VMWare Server has nothing to do with this problem. The Ubuntu server itself is randomly restarting for no apparant reason, which is bringing down all the virtual machines with it. 

```
developer@VMWARE-SRV01:~$ last|grep reboot
reboot   system boot  2.6.31-14-server Sat Sep 11 13:49 - 16:06  (02:17)
reboot   system boot  2.6.31-14-server Thu Sep  9 09:39 - 16:06 (2+06:27)
reboot   system boot  2.6.31-14-server Tue Sep  7 06:08 - 16:06 (4+09:58)
reboot   system boot  2.6.31-14-server Sat Sep  4 09:06 - 16:06 (7+07:00)
reboot   system boot  2.6.31-14-server Wed Sep  1 10:47 - 16:06 (10+05:19)
reboot   system boot  2.6.31-14-server Wed Sep  1 06:47 - 16:06 (10+09:19)
```

So at least I know what the core problem is but I still have no idea how to determine why Ubuntu is randomly restarting.

Anyone have any hints?

---

### Post by dcstar on 2010-09-12
> **Thund3rstruck said:**
> 
.........
So at least I know what the core problem is but I still have no idea how to determine why Ubuntu is randomly restarting.

Anyone have any hints?

If it has nothing to do with VMs then post the question in a more appropriate forum.

---

### Post by Thund3rstruck on 2010-09-13
> **dcstar said:**
> If it has nothing to do with VMs then post the question in a more appropriate forum.

Seriously? That's your advise? Repost to another forum and wait for no one to post again. 

Thanks for nothing pal... 

I've had enough of this non-sense. Its time to move my solution to a stable server operating system.

---

