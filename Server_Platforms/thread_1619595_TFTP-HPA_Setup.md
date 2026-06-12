---
title: "TFTP-HPA Setup"
date: 2010-11-12
forum: Server Platforms
---

### Post by m.dr on 2010-11-12
I am trying to setup a TFTP server and followed these instructions in setting up TFTP-HPA.
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I pretty much followed every step but commented out these two lines from the /etc/xinet.d/tftp.
        # only_from   = 172.31.0.240/28
        # interface   = 172.31.0.252

Do we really need the lines if I am allowing any machine to connect? And I have only 1 network card. This is acting as a dedicated TFTP server.

I ask as I get an error on the get and put commands as below:
tftp> get xxx.txt
tftp: error received from server <File not found>
tftp: aborting

However although it gives an error it DOES GET the file.

The put command however does NOT put the file. I have nobody / nogroup setup for the directory permissions as well.
tftp> put .vimrc
tftp: error received from server <File not found>
tftp: aborting

Any help or a link to a good setup tutorial is much appreciated.
Thanks very much for your help.

---

### Post by Z.K. on 2010-11-12
> **m.dr said:**
> I am trying to setup a TFTP server and followed these instructions in setting up TFTP-HPA.
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I pretty much followed every step but commented out these two lines from the /etc/xinet.d/tftp.
        # only_from   = 172.31.0.240/28
        # interface   = 172.31.0.252

Do we really need the lines if I am allowing any machine to connect? And I have only 1 network card. This is acting as a dedicated TFTP server.

I ask as I get an error on the get and put commands as below:
tftp> get xxx.txt
tftp: error received from server <File not found>
tftp: aborting

However although it gives an error it DOES GET the file.

The put command however does NOT put the file. I have nobody / nogroup setup for the directory permissions as well.
tftp> put .vimrc
tftp: error received from server <File not found>
tftp: aborting

Any help or a link to a good setup tutorial is much appreciated.
Thanks very much for your help.

Well, I am not sure how much help I can be though I am trying to something similar.  I have not yet gotten my tftp server to work.  What tutorial did you use?

As for your problem, it looks to me like the path to your image or whatever file you are trying to access is either not where it is supposed to be or the permissions on your folder are not correct.  You should check the config files for the tftp and the dhcp server.

:)

---

