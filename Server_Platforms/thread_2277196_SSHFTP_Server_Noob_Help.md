---
title: "SSH/FTP Server Noob Help"
date: 2015-05-07
forum: Server Platforms
---

### Post by keith42 on 2015-05-07
Hi Good People
I am trying to move away from windows and am trying to learn / get used to Linux. Ive installed lubuntu 14.04 on my laptop because from what i have read its the fastest booting. Anyways to my point.

On win 7 i used Filezilla Server to be able to remotely get files from my laptop. I also have an ftp folder for 4 family members to access with there individual folders inside it an each person is restricted to their own folders.

Is it possible to do this on lubuntu or would i be better just using ubuntu?

Any advice greatly appreciated

Keith

---

### Post by dino99 on 2015-05-07
some wiki/howto
[https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)
[https://apps.ubuntu.com/cat/applications/raring/filezilla/](https://apps.ubuntu.com/cat/applications/raring/filezilla/)  (user friendly, can be installed from ubuntu archive, via synaptic)
[http://askubuntu.com/questions/422812/is-ftp-accesible-outside-ssh-while-using-ftp-ssh](http://askubuntu.com/questions/422812/is-ftp-accesible-outside-ssh-while-using-ftp-ssh)
[http://www.krizna.com/ubuntu/setup-ftp-server-on-ubuntu-14-04-vsftpd/](http://www.krizna.com/ubuntu/setup-ftp-server-on-ubuntu-14-04-vsftpd/)

---

### Post by TheFu on 2015-05-07
Any linux version can run openssh-server. This provides sftp which is what almost everyone in the world should be using for authenticated access to files.  [Plain FTP should not be used by 99.999% of the world.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")  If you want access to files from outside the home, use sftp, not FTP and not samba.

The differences between most Linux distros are
a) the GUI
b) the default applications installed
c) the package manager used

You can swap any GUI you like in and out of most mainstream Linux distros. The GUI is just another program - it is NOT the OS.
You can install any applications you like in most linux distros.  You can remove any of the default applications - it is your choice.

It isn't hard to make Lubuntu look and work like normal Unity Ubuntu, if you like. It is easier to go the other direction, since Unity-Ubuntu has more programs loaded and loading LXDE is only about 3 min of time.

There is no need to install a new OS just to have a different GUI.

Almost any of the major Linux distros can be a desktop or a server or a desktop AND a server. There isn't any big difference - just install the programs you want.

---

### Post by Dennis N on 2015-05-07
> **keith42 said:**
> On win 7 i used Filezilla Server to be able to remotely get files from my laptop. I also have an ftp folder for 4 family members to access with there individual folders inside it an each person is restricted to their own folders. Is it possible to do this on lubuntu or would i be better just using ubuntu?

You would install openssh-server on your Lubuntu 14.04 laptop (It also works with ftp, sftp protocols). So, you can then connect to it from another Linux machine or even from a Windows machine on your local network. You can use owner and permissions settings to control access to folders in Linux.

---

### Post by keith42 on 2015-05-07
Thanks guys

Having a read and trying to get used to it...

---

### Post by keith42 on 2015-05-07
> **Dennis N said:**
> You can use owner and permissions settings to control access to folders in Linux.

Could u tell me how? or point me to a guide?

thanks

---

### Post by TheFu on 2015-05-07
web search for "*linux file permissions tutor*"

---

