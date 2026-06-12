---
title: "SWAT inaccessible"
date: 2006-08-23
forum: Server Platforms
---

### Post by jobertel on 2006-08-23
I have installed SWAT and made the necessary charges to the inetd.conf file and rebooted. When I try to access SWAT from a remote machine I get the error message:

403 Forbidden
Samba is configured to deny access from this client
Check your "hosts allow" and "hosts deny" options in smb.conf

Thinking that the remote access is the problem I installed lynx on the server and attempted [http://localhost:901](http://localhost:901) and got the same result.

Samba works, so I don't think there are any problems with the "hosts allow" or "hosts deny" settings. I want to use SWAT to tweak some settings. Furthermore I find the help in SWAT  very useful.

Any ideas out there?

John B.

---

### Post by jobertel on 2006-08-24
Hey everyone, I found the instruction to

apt-get install netkit-inetd

and like magic SWAT is accessible over the network.


John B.

---

### Post by DFNC on 2006-08-27
Thanks dude

> apt-get install netkit-inetd

really saved me a lots of headaches... Huge thanks!

---

### Post by jtrickey on 2006-09-12
Helped me out too - a big thanks from this Ubuntu noob.  :)

---

### Post by Pastorn on 2006-09-12
Many thanks from sweden...
now it's going to be a long night :-\"


/Pastorn

---

### Post by Zendarin on 2006-10-14
Thanks man!  This helped me alot :)

---

### Post by tofuconfetti on 2006-11-05
I forget that one every time :-(  They might want to install that on by default.

---

