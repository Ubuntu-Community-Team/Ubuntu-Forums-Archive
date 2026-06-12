---
title: "cifs - no encryption?"
date: 2012-01-13
forum: Security
---

### Post by floobit on 2012-01-13
After reading a fair bit of documentation, it sounds like cifs (and nfs for that matter) does not encrypt its data aside from authentication.  I wanted a unequivocal confirmation of this from the wonderfully knowledgeable people here.  If this is so, they should only be used in a DMZ, with or without VPNs, or perhaps passed through a tunnel.  How, then, is it a "common internet file system" if it should not be used on the internet?

---

### Post by CharlesA on 2012-01-13
CIFS is not encrypted as far as I know. I use it locally, but I wouldn't expose it to the internet as there are better ways to access files remotely (ssh comes to mind, which is encrypted).

I don't think NFS is encrypted either.

---

### Post by floobit on 2012-01-13
I suppose background might help.  Currently, file access to the server is achieved through FTP.  Samba/CIFS was suggested as a more secure alternative.  Certainly, authentication is more secure with CIFS, but is CIFS more secure than FTP in data transmission?  Because we want to restrict command line access using the forcecommand option from OpenSSH, we cannot use sftp or scp for file transfer.  

Thank you.

---

### Post by CharlesA on 2012-01-13
You are using SFTP instead of FTP, right? FTP sends data unencrypted.

---

### Post by Buntumatic on 2012-01-13
You mentioned NFS?

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

### Post by FuturePilot on 2012-01-13
CIFS isn't really ment to be used over the Internet. It's mainly used on a LAN. So, no, the data transmission is not encrypted.

---

### Post by cariboo on 2012-01-14
I have to ask why you can't use sftp or scp, but you do use ftp, especially when ftp is much less secure than sftp/scp. Most ftp clients also support sftp.

---

### Post by floobit on 2012-01-16
Thanks, all.  I cannot use scp or sftp because in a normal implementation, that server software is the ssh server.  My clients use ssh to connect to database frontend on the server.  I need to restrict ssh to only run this program.  The most secure way to do this is using the command "ForceCommand" in sshd.conf.  Because of the way ssh is set up, I can only list one command that can be accessed - so for a given user, for instance, I can set it up so they can either use the database frontend or sftp, but not both.  Thus, the need for samba/cifs.

---

### Post by CharlesA on 2012-01-16
I thought you might be able to set a specific group to be able to use sftp and another to just use the forced commands you need them to run.

sftp is only involved when you use sftp, not regular ssh, as far as I know.

I haven't tested this theory, but it might be something to try.

You are going to be using this to access files from the internet, right?

---

### Post by movieman on 2012-01-17
Personally I use IPSEC to ensure everything going to and from the CIFS/NFS server is encrypted. But I'd be highly reluctant to expose either to the Internet rather than a local LAN.

---

### Post by emiller12345 on 2012-01-17
I haven't used this too much but there is 'sshfs' which is a ssh file system.  It may work better for your needs.

EDIT: sorry, just read that you need cifs.

---

### Post by bodhi.zazen on 2012-01-17
> **floobit said:**
> Thanks, all.  I cannot use scp or sftp because in a normal implementation, that server software is the ssh server.  My clients use ssh to connect to database frontend on the server.  I need to restrict ssh to only run this program.  The most secure way to do this is using the command "ForceCommand" in sshd.conf.  Because of the way ssh is set up, I can only list one command that can be accessed - so for a given user, for instance, I can set it up so they can either use the database frontend or sftp, but not both.  Thus, the need for samba/cifs.

Seems like a horrible plan - you lock down ssh, but then open up a hole wide enough to drive a truck through with ftp / cifs.

Your best bet it to use ssh (scp or sshfs).

If you feel you need to somehow lock down your users, use apparmor or selinux.

If you *must* use cifs, take a look at kerberos.

---

### Post by SeijiSensei on 2012-01-18
You could run a second instance of sshd on a custom port and limit it to handling sftp requests.  The users would need to specify the custom port in their requests, of course.

---

### Post by CharlesA on 2012-01-18
> **SeijiSensei said:**
> You could run a second instance of sshd on a custom port and limit it to handling sftp requests.  The users would need to specify the custom port in their requests, of course.
That's what I was thinking, but I am not sure how you'd go about configuring it to do that.

---

### Post by SeijiSensei on 2012-01-18
> **CharlesA said:**
> That's what I was thinking, but I am not sure how you'd go about configuring it to do that.

Me, neither.  I was reacting to his comment about the ForceCommand option.  Perhaps there's a way to use that to resolve the problem?  Maybe some mix of xinetd and SSH with restrictions on the clients' IP addresses?

There are clearly other ways to accomplish what the OP wants.  One is a webdav implementation using HTTPS.  Another is to use OpenVPN to create tunnels between the clients and the server.  

Maybe he could reverse the process and set up the limited-access application he's now running on a custom port and let the regular sshd run on port 22?  

There's also the possibility of limiting access via users/groups.  Do the users need to have separate personal accounts with shell access or can they be restricted to /sbin/nologin?  Maybe the restricted application's users can share a single account?

---

