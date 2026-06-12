---
title: "unreachable /etc/fstab cifs/smbfs mount halts boot"
date: 2011-01-16
forum: Server Platforms
---

### Post by fragtion on 2011-01-16
Hi guys,

I have the following two lines at the bottom of my /etc/fstab
> 
//172.16.6.15/e /tmp/e cifs _netdev,iocharset=utf8,credentials=/root/.smbcredentials,gid=0 0 0
//172.16.6.15/e/Public /var/www/index/pub cifs _netdev,iocharset=utf8,credentials=/root/.smbcredentials,gid=0 0 0

My server address is 172.16.6.1.
If the destination (which is my workstation desktop) 172.16.6.15 is offline when the server tries to boot, the entire boot procedure halts with the following message:
> 
Unable to find suitable address.
mountall: mount <destination> terminated with status 2

The problem is that my server runs headlessly, and every time something silly like this happens where you'd normally expect the OS to continue regardless, I'm forced to plug a monitor in and diagnose on console

So my question: Is there any way to make it proceed with the boot normally despite the host being unreachable? I could probably chuck a mount command into crontab or /etc/rc.local or a /etc/network/if-up.d script, but isn't this the way it really should be done (/etc/fstab)? If so, then we shouldn't expect the entire boot to halt just because a network share can't be mounted, right? ...

While on the topic of a headless ubuntu server 10.10 not booting without some kind of intervention, I have yet another issue: If the server goes down without proper shutdown (power failure, for example) the grub menu displays the kernel choices and there's no countdown timer. Instead, I have to manually press enter to continue the boot. Is there any way around this? Clearly this should not be the case for a server distribution ...

Any feedback would be great. Cheers =)

---

### Post by SeijiSensei on 2011-01-17
Remove the lines from fstab and write a short script that pings the fileserver then mounts the shares if the server responds.  Run the script in /etc/rc.local.

---

### Post by MockY on 2011-08-28
I would like to know how such script looks like since I have the same issue. The difference being, the target servers are already running but boot still is refused. I always have to uncomment the lines in fstab before rebooting and then manually do a mount -a

So yeah, such script is of great interest.

---

### Post by fatbotgw on 2011-08-29
What happens if you take the "_netdev" out of it?  

I mount samba shares when my desktop boots and it will complain about not being able to find the location, but that's because the network isn't up yet.  Once the network comes up, it mounts them.  My boot sequence is never halted if my server is turned off.

I use the following:
```
//phoenix/store	/media/store	cifs	guest,rw,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777	0 0
```

It may not be the "perfect" way to do it, but it's what works for me...

Edit:
Also, I have my server's name added to my /etc/hosts file so I don't have to know the IP address.

---

