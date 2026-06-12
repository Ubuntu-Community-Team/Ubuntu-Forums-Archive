---
title: "Best Way To Jail/Limit User's SSH Access"
date: 2012-10-19
forum: Server Platforms
---

### Post by sajanNOPPIX on 2012-10-19
There's quite a bit of talk about jails, ssh, etc.  However it's all over the place and am not sure what's the best, current way to go about doing this.

What I'm looking to do is create users that can ssh into the server and use sftp only in their home directory.  I'd like them not to be able to cd out to the filesystem or any other folders.

This is easily done with FTP using chroot.  While I've successfully accomplished what I'm looking for by removing all global permisions to other folders...there's got to be another way.

Also, I want to limit what commands they can run.  Only want them to be able to run things that I choose.

What's the best way to go about doing this?

Thanks.

---

### Post by cool110 on 2012-10-20
Set ChrootDirectory in the sshd_config file, remembering to include  essential files such as the user's shell, basic /dev files and the  commands you will allow them to run. You can use %u in the path to  represent the username.

---

