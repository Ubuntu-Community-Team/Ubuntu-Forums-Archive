---
title: "Secure file server setup"
date: 2010-12-29
forum: Server Platforms
---

### Post by piranha124 on 2010-12-29
I am going to set up a file server on Ubuntu. I have searched a while, but can't seem to find a guide to what I want. The requirements specifications are the following:

[LIST=1]
[*]File server: possible to upload, change and download files
[*]Linux (Ubuntu) clients, Windows clients if possible
[*]Access restriction to deny access to other than registered users
[*]Only the user should be able to read the content of the files
[*]Ideally root should not be able to see the individual files, but in worst case it is ok for root to see the files.
[*]Root should not be able to open the files
[/LIST]
Point 1-3 is easy to find out how to set up. But I can't seem to find a way to deny root to view the files. The only solution I can think of is to encrypt files or a whole folder, but I don't know how to set it up.

The setup is for a home network, but the server used as a file server will have a web server as well. If someone manages to get access to the server I don't want them to be able to read the files.

If you have experience with this please provide me with a link to a guide, tutorial, manual or anything else that will help me out.

---

### Post by kidders on 2010-12-31
Hi there,

That level of security is probably excessive in a domestic environment. Preventing root from seeing individual files (ie reading filenames) or accessing their content requires client-side encryption. It's also the only way to guarantee data is protected against remote intrusion.

> **piranha124 said:**
> Point 1-3 is easy to find out how to set up.What protocols have you chosen?

> **piranha124 said:**
> If someone manages to get access to the server I don't want them to be able to read the files.Are you referring to physical/remote access?

---

### Post by piranha124 on 2011-01-02
Hi Kidders and thanks for your answer.

> **kidders said:**
> That level of security is probably excessive in a domestic environment. Preventing root from seeing individual files (ie reading filenames) or accessing their content requires client-side encryption. It's also the only way to guarantee data is protected against remote intrusion.
I know it may seem a bit much for a home environment. But after the verdicts of the Pirate Bay ($ 6 million / € 4.6 million for accessory of 15 torrents) I don't think it is excessive. Not that I have anything with copyright.

Anyway it seems to be as I thought, you have to handle it client side. Do you know any good way to handle it on Ubuntu without noticing it once you have typed the password?

> **kidders said:**
> What protocols have you chosen?
I haven't chosen anything yet, don't know what to use. I am open for any suggestions, as long as it is possible to read the files as if from a file system. Was thinking about SSH, but it is only because it is the only protocol I know that may act as a remote file system.

Have been looking a bit at Samba as a program, but I don't know if it is the best way to go. I am open for suggestions.

> **kidders said:**
> 
[QUOTE=piranha124]If someone manages to get access to the server I don't want them to be able to read the files.
 Are you referring to physical/remote access?[/QUOTE]
Mostly remote access, but if possible it would be good to stop them even if they have physical access. Of course you can never stop them from reading the actual files, but at least they should not be able to read anything but some encrypted files.

---

### Post by perspectoff on 2011-01-02
WebDAV with password authentication, and/or an FTP server such as vsftpd or proftpd. For an FTP client, use FileZilla (available on all OS platforms).

For FTP servers:
Ubuntuguide.org
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Maverick#FTP_Server)

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#FTP_Server](http://kubuntuguide.org/Maverick#FTP_Server)

---

### Post by kidders on 2011-01-02
Hey again,

> **piranha124 said:**
> Do you know any good way to handle it on Ubuntu without noticing it once you have typed the password?I'm not aware of an existing solution, I'm afraid. I recently set one up (for a client in work) based on WebDAV, as perspectoff suggested, but it involved writing some reasonably complex client software to handle the encryption.

> **piranha124 said:**
> I haven't chosen anything yet, don't know what to use.NFS would seem to be the obvious choice in a Linux environment. Using Samba wouldn't be great ... there's no reason to subject yourself to all the hassle & daft constraints of Windows when you don't have to.

> **piranha124 said:**
> Mostly remote access, but if possible it would be good to stop them even if they have physical access.Actually, physical access is far easier to protect against, and is the sole focus of most encrypted storage systems. The idea is to prevent someone breaking in and walking away with a hard disk full of private data under their arm. Encryption is not really an effective means of guarding against unauthorised *remote* access to data, which is why I was curious whether you really wanted to try it. Even banks, hospitals, governments, etc. rely on standard access control measures for that.

Anyhow, long story short, since you don't want unencrypted data being accessible even by authorised users of your server, and you need reasonably transparent access to files client-side, I think your only option is to write some software, eg a gvfs or fuse plugin.

---

### Post by kevinthecomputerguy on 2011-01-02
May i suggest [http://woodel.com](http://woodel.com)
 
-KevinTheComputerGuy
:- )

---

