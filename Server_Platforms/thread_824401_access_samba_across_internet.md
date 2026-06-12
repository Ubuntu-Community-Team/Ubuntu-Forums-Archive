---
title: "access samba across internet"
date: 2008-06-10
forum: Server Platforms
---

### Post by tuaranoi on 2008-06-10
hi there,

is there anyway to setup a samba and enable it so that people can access from home? i have 1 samba running on ubuntu but now figuring how to enable it online for the users to logon.

thank you

---

### Post by HermanAB on 2008-06-10
It is called a Virtual Private Network.  You can use either OpenVPN  (which is multi-platform and easy to use) or SSH, but I suggest using OpenVPN [http://openvpn.net/](http://openvpn.net/)

---

### Post by hyper_ch on 2008-06-10
if the box you are connecting from is also linux, you can use SSHFS

I use that when I do webpages on my server, I just locally mount the remote directory with SSHFS into my /var/www

---

### Post by puelly on 2008-06-10
Setting up a ftp server could be another option.  vsftp is a good lightweight choice.  Google it and you'll find a few guides online.

---

