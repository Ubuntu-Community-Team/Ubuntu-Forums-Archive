---
title: "vmware server console with vmware server 64-bit gutsy"
date: 2008-01-10
forum: Virtualisation
---

### Post by Erik-NA on 2008-01-10
Have installed vmware server from the canonical partner repository on a 64-bit gutsy host

Could not connect with vmware server console from my windows machine. After a lot of hours, a friend of mine found out that the pam-libs from vmware install are 32-bits, not 64-bits!

We changed /etc/pam.d/vmware-authd to the following, and now it works!
[PHP]#%PAM-1.0
auth required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok
account required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_acct.so
[/PHP]

---

### Post by justinflavin on 2008-01-11
i can confirm that worked for me too

ubuntu server 7.10 , 64bit

vmware console on another machine would refuse to login until i changed /etc/pam.d/vmware-authd as specified above.

---

### Post by rtwick on 2008-01-11
Thanks 
This worked for me too.

---

### Post by fjgaude on 2008-01-11
Funny, I installed using the binary from the vmware.com site and the lines you fellows mention are already in my /etc/pam.d/vmware-authd file. Interesting.

Never had a problem.

---

