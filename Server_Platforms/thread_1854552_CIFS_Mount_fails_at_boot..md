---
title: "CIFS Mount fails at boot."
date: 2011-10-04
forum: Server Platforms
---

### Post by FrustratedFox on 2011-10-04
I'm trying to make an Ubuntu server 11.04 64bit server mount a CIFS share on boot. I started with */etc/fstab* and the following command:
```
//FS1/Data /FS1 cifs dir_mode=0755,file_mode=0755,user=domainid/legituser,password=validpassword
``` *sudo mount -a* works every time. However, when the server is rebooted, the share fails to mount without any indication is dmesg. syslog, the samba logs... nothing. It simply doesn't mount. *sudo mount /FS1* and I'm reconnected just fine.

I figured there might be a slow network issue, though there does not seem to be. I've tried the  *_netdev* option, mount commands in rc.local and after.local and nothing changes. It will not mount at boot time.

I've got a 10.4 server right next to this box and the same fstab works flawlessly. Can anyone tell me why it fails on 11.04?

---

### Post by collisionystm on 2011-10-04
Here is mine that works.


//172.16.66.137/C$ /media/usb0/QWServer/C cifs sec=ntlmv2,credentials=/root/.qwcred,iocharset=utf8,file_mode=0777,dir_mode=0777 0

---

### Post by FrustratedFox on 2011-10-04
Thanks for your input but, this did not resolve the issue. I'm confident that the fstab line is fine, as a *mount -a* works. But, I think that there is an issue with the mount occurring before the network is up. I would expect Upstart(Grrr) *mountall-net.conf* to take care of it. But, it does not seem to be taking care of it and I have no idea how to track/troubleshoot its activities. As I said, there is no indication of any problem in the logs. It fails silently.

---

### Post by collisionystm on 2011-10-04
Try the IP instead of the DNS name

//**IPADDRESS**/Data /FS1 cifs dir_mode=0755,file_mode=0755,user=domainid/legituser,password=validpassword

---

### Post by kgatan on 2011-10-04
Add "auto" to the mount options

```
//ip/folder   /mnt/target/        cifs    credentials=/path/to/file,**auto**
```Use a credentials file for authentication for more security. Content of file as below,

```
username=youruser
password=yourpsw
```Chmod the file to 600 and chown root:root

---

### Post by FrustratedFox on 2011-10-05
Thank you both for your suggestions. I have tried them all, to no avail. The server will NOT mount automatically at boot. After boot works every time.

What has Ubuntu changed this time? So frustrating.

---

### Post by Morbius1 on 2011-10-05
Back in the olden days you could add the option "_netdev" which told the system not to mount the remote share in fstab until the network is up. But it really doesn't seem to work anymore - though it might for you.

Another idea would be to surrender to the problem and automate a "mount -a":

Create a script:
```
gksu gedit /etc/network/if-up.d/fstab
```With this content:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstab
```Any script in if-up.d will execute only after the network is up. Of course if the target server is not up at that moment it will still fail but ...

---

### Post by FrustratedFox on 2011-10-05
Sadly, I think you may be right that I might have to surrender to the problem. Your solution or a cron *@reboot* script will have to do. I just hate crap like this.

---

### Post by FrustratedFox on 2011-10-06
This issue turned out to have nothing to do with Ubuntu or Samba/CIFS. The originally configured line in */etc/fstab* 
```
//FS1/Data /FS1 cifs dir_mode=0755,file_mode=0755,user=domainid/legituser,password=validpassword
``` does indeed work fine.

The issue turned out to be a misconfigured switch. The switch had spanning tree enabled. This was causing a lengthy blocking period(~30 seconds) on the port that the Ubuntu server was attached to when it was booted. The Ubuntu 11.04 server was booting and the CIFS mount was attempted before the 30 second spanning tree blocking period was over so it basically had no network connectivity and the CIFS mount failed.

The resolution was to accelerate the spanning tree process (Cisco - portfast) (Dell - Fast Link). Once this is done the port goes into forwarding mode immediately. This allows the CIFS mount to succeed.

There is still an issue in the sense that this failure could occur without any logging. It would appear that this is all happening (network activation, CIFS failure, etc.) before syslog has started properly.

The absence of log information made a fairy common networking issue into a far greater ordeal than needed.

Thanks to those that tried to help.

---

### Post by collisionystm on 2011-10-06
Wow. Now that is some technical troubleshooting!

This is actually good information for me to have. I am about to implement a new network with a Dell Powerconnect 3548P at the core. I will keep this in mind.

---

