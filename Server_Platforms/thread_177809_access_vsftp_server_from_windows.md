---
title: "access vsftp server from windows"
date: 2006-05-16
forum: Server Platforms
---

### Post by cosmo1983 on 2006-05-16
Hi,

I have my vsftp server running and works fine. I want to be able to access the ftp server from windows when I type in the ip address on windows explorer. But this doesn't seem to be working, I can easily access it from command line using cygwin or putty. Any help would be appreciated. Thanks.

---

### Post by mrcowcow on 2006-05-17
Is anonymous access enabled? Check to see if anonymous_enable=YES. If it is set to no, then it cannot be accessed without logging in.

---

