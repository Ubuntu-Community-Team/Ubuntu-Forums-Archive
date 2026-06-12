---
title: "File / User Authentication Server"
date: 2009-04-28
forum: Server Platforms
---

### Post by AndyXS on 2009-04-28
I am setting up a file / user authentication server with Ubuntu. The server we have has have two 500GB drives. Can you please advise on the partitioning. Am I right to use this?

HDA1 100MB ext3 /boot
HDA1 4GB swap /swap
HDA1 10GB ext3 /
HDA1 486GB ext3 /home
HDA2 500GB ext3 /backup 

Which service is used to authenticate windows users? Is this called a domain controller? Is this samba that I need?

The second issue I have is which services needed to be installed. We want a shared drive in windows (s:\) which will be located at /home/shared on the server. We also want another drive (p:\) which will be linked to each users private account /home/<user>. Is this also a samba service?

---

### Post by HermanAB on 2009-04-28
Yup and yup.

Go to the samba project web site and read the Official Howto.

---

