---
title: "securing SSH connection for SFTP server"
date: 2011-01-19
forum: Security
---

### Post by Ceiber Boy on 2011-01-19
I'm running an SFPT server which my clients logon to using an FTP client. at the moment each client has a user name and password.

Thus far to improve security I've disabled root login but an looking for futrhrt ways to protect it from attack, having researched using google some of the security features suggested prevent the FPT clients from connecting.

Questions
1, what further things can i do to secure my server that still allows it to be usable for FTP clients?
2, specifically is it possible to use non login pre-share key authentication?

How i set up the server is shown here:
[http://ubuntuforums.org/showthread.php?t=1660615](http://ubuntuforums.org/showthread.php?t=1660615)

Many thanks

---

### Post by amra.sonntag on 2011-01-20
I'm currently trying to learn how to set  up different kinds of server myself. So I can't give you a perfect solution or How-To or any guarantees - but maybe some pointers on where to start.

As far as I understand the security concepts for FTP, you are left with two choices SFTP and FTPS.

SFTP uses SSH and will requiere you to install the OpenSSH Sever on your vsftp Server. It would make automatic and secure connections with pre-shared keys (ssh-copy-id) possible. A drawback is that you will, by default, also give users a shell on your server. This however can be avoided - look at the Ubuntu Server Guide ( [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html) - nologin shell ) for information how.

There you will also find this link [http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329](http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329) for a comparission of SFTP and FTPS.

Using FTPS would involve creating SSL Certificates and I'm not yet sure how to do this. It also seems like "overkill" to me, if you intend to use the server only in a private fashion - not connecting it to the general public.

---

### Post by amra.sonntag on 2011-01-20
I apologize for making this a double post. But my solution might take up some space.

Make it possible to have different users login on a secure base and only see the users home directory.

Create a group sftp and add all your users (those that should have remote access this way) to it.
replace in /etc/ssh/sshd_config ```
Subsystem sftp /usr/lib/openssh/sftp-server
``` with ```
Subsystem sftp "internal-sftp"
```add at the end of /etc/ssh/sshd_config a rule to specify how to treat your sftp group ```
Match Group sftp
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
```

Now you need to setup the home directories for the users i use user test in group sftp as an example:
```
usermod -s /bin/false test #no shell for user test
usermod -d /home/test #set home dir

chown root:root /home/test #must belong to root for Chroot in sshd_config
chmod 755 /home/test       #test cannot write into this dir
mkdir /home/test/write     #here will be a place to upload data to for test
chown test:sftp /home/test/write #give the upload dir to test
```

This should prevent your users from logging into a console via SSH, but enable them to connect via SFTP to **only** home directories.

To make the login more comfortable, the users can log in via SSH Public keys. To do so - they only have to upload the Public key to the Server, where you take it from the users write directory and store it as "authorized_keys" in "/home/'username'/.ssh/".

If you follow those instructions, you basically don't need vsftpd anymore, since you handle everything with the sftp built in server from OpenSSH. However - in case you want to make data available to anonymous clients - you can still use vsftpd.

So - I hope this was helpful in some way or the other.

---

### Post by HellesAngel on 2011-02-11
Many thanks for the tips, Google landed me here while trying to get this working and I can say your tip works perfectly.  This [page]("http://singe.za.net/blog/archives/378-Linux-SSH-Jail-with-pam_chroot.html") is also useful for setting up the chroot jail but ignore all the stuff about PAM as that doesn't seem to play well with RSA keys.

---

