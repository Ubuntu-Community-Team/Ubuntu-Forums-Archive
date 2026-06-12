---
title: "UEC access to controller behind NAT"
date: 2010-09-24
forum: Ubuntu Cloud and Juju
---

### Post by s3mt3x on 2010-09-24
I just build a proof of concept environment with UEC using this guide:
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

It uses a 192.168.2.x range, 2 server setup (controller&node) and works great internal.

I would now like to access the web page for the UEC Cloud Controller from the internet. Between the internet and the LAN is a NAT/firewall (so only 1 public ip address).

I enabled and forwarded the 8443 and 8773 ports to the Cloud Controller.

If I access the web-admin page (https://<public-ip-address>:8443) I get an SSL cert error, click oke, and get some of the page layout but not the login box.
If I access the web-admin page internal (https://<private-ip-address >:8443) it works great...

I don't need to access the running VM's via the internet, only the admin-web-page. 

What am I missing :confused:

Regards,

Jan.

---

### Post by Rusty au Lait on 2010-09-24
Your ssh key is not the same as the credentials (mykeys.priv) used by UEC. Open port 82 on your router if it is not already open. Open a CLI and SSH to your CLC. This will fail if you have a public key for the IP address set up for a different host. Find and delete the line in ~/.ssh/known_hosts being used for that IP. This should let you ssh to the CLC and also access admin. I don't know if port 82 needs to stay open.
Did that work?

---

