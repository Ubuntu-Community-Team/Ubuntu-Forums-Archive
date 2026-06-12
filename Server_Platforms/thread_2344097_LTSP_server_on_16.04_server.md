---
title: "LTSP server on 16.04 server"
date: 2016-11-22
forum: Server Platforms
---

### Post by dshah on 2016-11-22
I have installed Ubuntu 16.04 x64 server, Is there any working guide/tutorial to install ltsp server with x32 bit thin clients? 

p.s i am new to ubuntu/server setup, any help appreciated. thanks

---

### Post by slickymaster on 2016-11-22
*Thread moved to **Server Platforms**.*

---

### Post by deadflowr on 2016-11-22
From here: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")
> If you are on a 64-bit system but your clients have another architecture use the --arch option eg. sudo ltsp-build-client --arch i386 

---

### Post by dshah on 2016-11-22
> **deadflowr said:**
> From here: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
Thanks, but I dont want to reinstall whole system with the linked URL, it's not latest Ubuntu server version.

---

### Post by dshah on 2016-12-04
ok,
 i was able to install it but I was having issue with a blank screen on thin client, After a lot of googling I was able to see login screen and login by adding nomodeset in file

/varlib/tftpboot/ltsp/i386/pxelinux.cfg/default

in ltsp-NBD append line 

Now my thin client boots and login correctly, But the resolution is issue now. I checked with lspci command and it states my VGA is:

VGA Compatible controller: Intel corporation Device 191d ( rev 06)

But on my thin client vga is ati radeon x1200 , I think its picking the server's VGA?

Both thin client and server uses same company's monitor.

I tried to update [lts.conf ]("http://manpages.ubuntu.com/manpages/xenial/man5/lts.conf.5.html")with different options for VGA resolution but no success .

I checked my video driver is supported by radeon on Ubuntu 16.04, 

I updated my server and client both kernel's to 4.8.12-040812-lowlatency

I created again thin client image 'sudo ltsp-build-client --arch i386'

than again I had to add 'nomodeset'in pxelinux.cfg/default file to be able to login on X.

still same issue with resolution. any help please?

---

