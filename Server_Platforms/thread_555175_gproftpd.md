---
title: "gproftpd"
date: 2007-09-19
forum: Server Platforms
---

### Post by count23 on 2007-09-19
I have a question for you folks, I've set up a server using gproftpd. Is there a way to configure this by SSH? I used gproftpd because i was in a hurry and hadn't used proftp before (GUI = simple to configure, usually). Now when i put this server back in it's rack, I will no longer have any KVM access to it, only SSH. My goal is to be able to configure the server through SSH, adding and removing users as necessary. Do I need to uninstall gproftpd and install proftpd to use it through SSH or is there a CUI  i can configure it with?

---

### Post by HermanAB on 2007-09-19
Ensure that SSH is configured for X forwarding by default (/etc/ssh/ssh_config).  Then if you log in from a machine that has a X server running (Linux or Windoze with Xming+PuTTY) then you can run any program and it should display properly on your terminal, just as if you were right at the server.

Otherwise you can request X forwarding from the command line:
$ ssh -X user@server
password
$ xcalc
or
$ gproftpd

Cheers,

H.

---

