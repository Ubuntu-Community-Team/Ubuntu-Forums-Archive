---
title: "Unable to connect to server with PuTTY"
date: 2007-07-18
forum: Server Platforms
---

### Post by don_c on 2007-07-18
I have just done a LAMP installation which seems successful - I can access a phpinfo page which displays correctly.

I now want to connect using PuTTY - I followed the howto forge perfect setup and did:

 apt-get install ssh openssh-server

All seemed to install successfully - howto then says connect and use Putty.  Problem is that I constantly get "Access Denied" when trying to connect.  Any ideas?  Are there settings in sshd_config I should check?

Thanks

---

### Post by koenn on 2007-07-18
verify that sshd is running :```
/etc/init.d/ssh restart
``` or  (not sure ubuntu uses the same names as debian here) ```
/etc/init.d/openssh-server restart
``` and check output

Make sure you tell putty the correct ip address / server name, and connect to port 22.

---

### Post by don_c on 2007-07-18
Restarts ok:

* Restarting OpenBSD Secure Shell server...   [ok]

 I am using the correct IP address. 

Get "Access Denied" when i try to login.  I've double checked username/password.

---

### Post by don_c on 2007-07-18
How embarassing - just realised that the ubuntu server keyboard is US and my PC is UK....

Now need to work out how to reconfigure the keyboard.

---

### Post by codmate on 2007-07-19
Is IPtables running with default drop policies (and if not - why not? ;) )...

If so then you'll need to open up port 22 for ssh.

$ iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

...would probably do the trick.

---

