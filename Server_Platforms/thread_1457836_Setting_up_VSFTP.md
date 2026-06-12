---
title: "Setting up VSFTP"
date: 2010-04-19
forum: Server Platforms
---

### Post by smay84 on 2010-04-19
Hi

I'm fairly new to Linux but have so far managed to do the following.

- Setup VSFTPD
- Install and setup Webmin with VSFTP module

I'm running my server in VirtualBox in order to test it and figure out how you setup the FTP server before i start messing with our live ftp server.

I'm not sure what my next step is.  I just want to be able to test the FTP server using the current host machine.  I can get to the Webmin page with the virtual machines IP but not the FTP server.

If i type ftp localhost into the terminal it connects ok.

I'm guessing this is something simple that i've overlooked.

Anyone able to point me in the right direction?

Si

---

### Post by cdenley on 2010-04-19
You're able to connect to vsftpd from within the virtual machine?
```

sudo netstat -tlnp
nc -z -v -w 5 localhost 21

```
but not from outside the virtual machine, even though you can connect to webmin
```

nc -z -v -w 5 vboxip 21
nc -z -v -w 5 vboxip 10000

```

---

### Post by smay84 on 2010-04-19
nevermind, in the end i installed proftpd and realised it was due to the way virtualbox was connecting it to the network.  Thanks anyway

---

