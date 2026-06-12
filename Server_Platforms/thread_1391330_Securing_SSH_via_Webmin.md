---
title: "Securing SSH via Webmin"
date: 2010-01-26
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-26
I installed OpenSSH via tasksel and am using Webmin for administration.  I'd like to be able to SSH externally and want to setup the necessary public/private keys to use in FileZilla.

In Webmin, under Servers > SSH Server I can click 'Host Keys' and see an RSA key.  Is this the public or private key for my server?  Do I need to copy this into a text file to import it into FileZilla on my remote PC (that I want to connect from)?  Is that all that needs to be done (aside from opening the port on my router/firewall)?

Or, is there an automated way to set this up via Webmin?

Thanks :)

---

### Post by bodhi.zazen on 2010-01-26
To set up ssh keys

On the client use ssh-keygen

ssh-keygen

Then transfer the key to your server with ssh-copy-id

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Then import the key to Putty, save it as a putty key.

[http://www.electrictoolbox.com/putty-rsa-dsa-keys/](http://www.electrictoolbox.com/putty-rsa-dsa-keys/)

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

You can then use the key with winscp or filezilla.

winscp is a portable application and very handy

[http://winscp.net/](http://winscp.net/)

[img]http://winscp.net/eng/docs/ui_commander[/img]

---

