---
title: "Issue with Samba client"
date: 2021-08-28
forum: Server Platforms
---

### Post by peter-1984 on 2021-08-28
Hi,
I followed the steps below
[https://kifarunix.com/install-and-configure-samba-file-server-on-ubuntu-20-04/](https://kifarunix.com/install-and-configure-samba-file-server-on-ubuntu-20-04/)


to create shared path on Ubunto 20.04 but after that, I also grant right to the client IP like


ufw allow from 10.0.2.15/24 to any app Samba


to access Samba remotely. But on Windows client, I cannot access it expectedly.

---

### Post by TheFu on 2021-08-31
Why not follow the instructions at help.ubuntu.com?  Just curious.  Following instructions from random sites is a way to get incomplete answers or answers for the wrong distribution.

Can your Win10 client ping the Ubuntu system by IP?  by name?

---

### Post by Morbius1 on 2021-09-02
> ufw allow from [COLOR=#ff0000]**10.0.2.15/24**[/COLOR] to any app Samba

I don't know much about ufw but I suspect the problem is you are specifying a IPv4 range of addresses. Windows 10 makes it's initial contact with the server using an IPv6 address so the way you are set up it will automatically be denied access even if it has an IPv4 address in that range.

The closest thing I have done personally to this situation is used the "hosts allow" parameter in smb.conf. If I set it to a range of IPv4 addresses Win10 is denied access. But if I set this up to a range of IPv6 address it works.

I run this command to find my ip address on the server:
```
hostname -I
```

For example:
> ~$ hostname -I
192.168.1.137 [COLOR=#ff0000]**2605:a601:a18d:9f00**[/COLOR]:a00:27ff:fe16:7607 

So in my example I would set "hosts allow" to:
```
hosts allow = 2605:a601:a18d:9f00::/64
```

See if ufw can handle IPv6 this way.

---

