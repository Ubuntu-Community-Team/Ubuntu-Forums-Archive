---
title: "SSH Server - SFTP - Remote CIFS Share"
date: 2013-03-19
forum: Server Platforms
---

### Post by Gozzgug on 2013-03-19
I have a windows server running an FTP server and the root of the FTP server is a remote share on another windows server. I want to create an SFTP(SSH) server in ubuntu and have the home directories for the users be on a remote windows server. Is this something that can be done? I know how to install the SSH server and get SFTP going but how can I get the SFTP user redirected to the remote windows share where their files exist? The files must be on the remote windows server because there is an application that runs and puts them there so it can't be a different location.

Should I make a permanent CIFS mount to the windows share for the SFTP home folder? (How?)
Is there a way to have each user mapped to a different folder on the mounted CIFS folder? (How?)
The last question I have is if there is any way to get their AD usernames and passwords to work for SFTP access?

Thanks for the help!

---

### Post by prodigy_ on 2013-03-19
You can [mount CIFS at boot using /etc/fstab](http://ubuntuforums.org/showthread.php?t=288534) like any other FS. For AD-based auth you need to [add your Ubuntu server to the AD domain](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto).

As for home folders I'm not sure. Never used Linux with AD auth myself.

---

### Post by kevdog on 2013-03-20
I'm sure its possible to do what you want be mounting the remote directories with cifs (samba). Wouldn't it just be easier however to run cygwin on the windows box and have the users log in directly?

But I do have a similar setup:
Linux Box1 >>>>sshfs mount>>>>Linux Box2>>>>cifs mount>>>Windows box

There is a subdirectory on Linux Box 1 which I can directly access those files on the Windows box.  
On the Linux Box 2 I mounted the cifs shares with the following:
#Network LapTopShare
//10.0.1.115/Downloads  /media/BJPDR10-Downloads  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

---

