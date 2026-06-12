---
title: "Connecting WinSCP to Ubuntu Server 16.04 as root."
date: 2016-10-15
forum: Server Platforms
---

### Post by ren1 on 2016-10-15
Please help me I'm stumped. I've been able to connect to Ubuntu Server 16.04 before as root using SFTP. I was able to edit files no problem.
Now all that happens is I get logged in after putting in my credentials for my Ubuntu user and it says starting session for a split second then it goes back to the login screen. And there's no explanation why.
Here's what I've done:

Re-installed WinSCP on Windows 7 64-bit,
Cleared the key cache,
Installed vsftpd,
Added my Ubuntu user to /etc/ftpusers,
Added my Ubuntu user to /etc/sudoers together with ALL = (ALL) NOPASSWD: ALL,
Restarted my server,
Used ssh-keygen to regenerate keys in /root/.ssh.
Configured WinSCP with my Ubuntu user credentials without password stored and using port 22,
Gone to WinSCP advanced site settings/environment/SFTP and typed in SFTP Server: sudo /usr/lib/openssh/sftp-server,
Enabled allow SCP fallback,
Gone to environment/shell and selected sudo su - in shell dropdown list and left all other settings and stored the site.

I have openssh-server installed and can connect using Putty just fine. I connect Putty using my Ubuntu user then doing sudo su.
I can connect WinSCP just fine without root but not with root.
Also it dosen't matter if I'm logged in with Putty at the same time or not.
This is really getting on my nerves and I could do with some help ASAP please.
Please excuse me as I'm a newbie to Ubuntu Server. Even Ubuntu as a whole.
Help would be appreciated.

Thank You.:lolflag:

---

### Post by TheFu on 2016-10-16
In ubuntu, root isn't meant to be used in this way. Not for ssh or sftp or any other remote connection.
I believe it is against forum policy to help with a question (root remote access), but others would need to confirm it.

Why use vsftp when openssh-server has ssh/sftp/scp built-in?  I've never understood why folks do that.  Seems like you are trying to mix these programs, which shouldn't be done.

Using NOPASSWD in the sudoers is really poor security. Lock that down to only the exact, specific, command, it needs to run ... which shouldn't be anything connected to remote access, BTW.

IMHO.

---

### Post by ren1 on 2016-10-17
I thought I might be mixing two programs of the same kind. You see I was watching a instructional video on how to do something else and it had you install openssh-server. But alot of the file editing was done on command line. So I thought I could use WinSCP to edit the files. I went to somewhere else on the web (I can't remember where) to find out how to setup Ubuntu Server for WinSCP and it had me install vsftpd. I still can't connect as root even with SCP. Should I uninstall vsftpd altogether? Again, I apologise as I'm new to Linux altogether really.

---

### Post by darkod on 2016-10-17
If you installed openssh-server, why would you modify files with winscp remotely? Simply open a ssh session (like with putty from windows), and edit the file you want to edit... Directly on your server.

As mentioned, ssh allows you scp and sftp too, that way you can copy files to/from the server.

And you need to be using your user, not root. In ubuntu root is disabled by default, so it is normal that you can't connect if you try using root user. Use your own user and work like that on the server...

---

### Post by ren1 on 2016-10-17
I just find WinSCP easier and more conveniant. I need to edit files that require root permission to do so. As I said before, I was previously able to connect with my Ubuntu user with elevated permissions before. I don't think I changed anything when this problem suddenly just started.

---

### Post by TheFu on 2016-10-17
> **ren1 said:**
> I just find WinSCP easier and more conveniant. I need to edit files that require root permission to do so. As I said before, I was previously able to connect with my Ubuntu user with elevated permissions before. I don't think I changed anything when this problem suddenly just started.

Check the timestamps on the config files. 

I don't use vsftp for a number of reasons. I would purge that package and only use openssh-server for all ssh/scp/sftp/sshfs and ssh-tunnel needs.  Plus rsync works over ssh by default as do many editors. Since you need ssh anyway, I don't see the purpose for another server.  Really wish all the guides would stop recommending plain FTP as well. It is a disservice to the community, since 98+% of the time, there are better solutions.

Use whatever editor you like on *nix systems, but use **sudoedit** to edit system files.

---

### Post by ren1 on 2017-03-04
Can somebody please help? I still haven't solved this problem and it's been months now.

---

### Post by darkod on 2017-03-04
Ubuntu has direct root login disabled by default. And that is for security reasons... So if you want to edit files directly as root/sudo, I don't know of an easy way to do that. I haven't even looked for it.

Use scp (or WinSCP) to upload/download files using your standard user, and then inside a ssh session to do files editing using sudo and your standard user.

Wouldn't that work for you?

---

### Post by TheFu on 2017-03-04
Is it possible that there is a different method to achieve the final results you want?  Mandating the use of WinSCP is pretty limiting. There could be multiple other options.  For example, using sshfs.

---

