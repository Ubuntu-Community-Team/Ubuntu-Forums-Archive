---
title: "Samba outsite LAN, over internet?"
date: 2009-02-02
forum: Server Platforms
---

### Post by indispus on 2009-02-02
Hello!

It is possible to use Samba over internet, outsite LAN?

I have a Ubuntu Server machine running Samba in order to share various data. I want to be able to connect to that server from work, over internet. Is it possible to mount Samba shared directory in this way? If so, how?

Thank you!

---

### Post by ghettofreeryder on 2009-02-02
I would run Samba over a VPN, not straight over a WAN.  Another option would be using SSH or SFTP.  You could do either of those without the VPN.  

As for mounting the partition, I think you could "mount smb://path-to-share/folder /media/sambashare"

Might need to add the file system in there somehow

---

### Post by lykwydchykyn on 2009-02-02
I will second the recommendation to to sftp rather than opening SAMBA to the internet.

If you want to do it that way, though, you will probably just need to forward all samba ports on your router (I think it's 137-139 and 443), then the mount command is:
```

smbmount //router_external_ip/sharename /local/mountpoint

```
naturally, you replace "router_external_ip" with the WAN address of your router, "sharename" with the name of the share, and "/local/mountpoint" wiht the path to the folder you want to mount the share on.

---

### Post by Thirtysixway on 2009-02-02
sftp or ssh would be the better way to go.  Don't want to open up your files to the world to crack at.

---

### Post by indispus on 2009-02-03
Thank you guys for your answers!

:popcorn:

---

### Post by HermanAB on 2009-02-03
Maybe see this:
[http://aeronetworks.ca/samba-ssh-tunnel-howto.htm](http://aeronetworks.ca/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

### Post by jamesrfla on 2009-02-03
If you are trying to get you files over a WAN I would suggest using SCP. This runs through SSH and is very secure.

---

