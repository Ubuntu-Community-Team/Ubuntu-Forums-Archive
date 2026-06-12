---
title: "Set up a secure FTP server with VPN"
date: 2009-07-27
forum: Server Platforms
---

### Post by ade234uk on 2009-07-27
I would like to set up a basic FTP server that is secured only for my access, could you please tell me what packages I would need to install. I have files scattered across 3 external hard drives, so it is better to get these on to one drive.

or alternatively

Set up a VPN connection to my server, the directory where the files are stored is shown on a webpage so they can be clicked and downloaded.

What offers the best security?

---

### Post by NoReflex on 2009-07-27
If you have ssh on the server (I guess you do) you can use sftp (Secure FTP).
```
sftp username@server_ip
```

Best wishes,
NoReflex

---

### Post by jhannah on 2009-07-27
Depending on how much of a hassle you want to go through, you have a few options. Simply sticking with SSH/SFTP would probably be the best way to go. This will provide you an encrypted means to access your data while also providing some compression for your file transfers. You could even use it in conjunction with rsync if you have a large amount of data to keep synchronized. SFTP is well supported in many clients on many operating systems so it is pretty flexible as well (I would recommend checking out WinSCP or FileZilla for any Windows machines that might need to access your files). A vanilla install of openssh-sever should give you everything you need to get SSH and SFTP up and running but you can find some more details at [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html) which also includes a bit of information on SSH keys which might make your life a lot easier.

If you wish to explore the hard way, you indeed could setup a VPN. For simplicity I would recommend looking into OpenVPN ([https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)) but any IPSec VPN (ie racoon or openswan) would work as well. However, when it comes to VPNs it's usually best to leave it to network hardware as the client configurations can be fairly involved.

---

### Post by ade234uk on 2009-07-27
I may as well go with option one. Sounds like VPN would become messy. As long as my files are secure through VPN I would happy.

---

