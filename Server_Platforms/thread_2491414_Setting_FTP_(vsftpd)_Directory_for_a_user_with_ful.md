---
title: "Setting FTP (vsftpd) Directory for a user with full write permissions?"
date: 2023-10-07
forum: Server Platforms
---

### Post by jderosa32 on 2023-10-07
I setup an FTP (vsftpd) server so I can gain access to my website files on my Ubuntu Server. I can login but it is to an empty directory for the user. However, I want to be able to FTP to the /srv directory so I have access to the root of my site files.

I am not sure how to do this. Any advice?

---

### Post by darkod on 2023-10-08
Did you consider using scp instead? The thing is that ftp is very old and quite unsecure protocol. You should never open ftp to your web server over the internet, and not to the /srv directory.

Probably a better recommendation is to use scp and to upload files first to a different directory, and then connect by ssh to the server and move the files where ever you want.

scp is also much easier to set up through firewalls because it works only on one port, tcp/22. And it can work with ssh keys, much safer against attacks.

---

### Post by jderosa32 on 2023-10-08
I agree that it is old. I only amd using this locally and it is not open to the internet. If I wanted to use this outside of my network I would have to VPN into my network so I feel confident it is safe. What I can do is learn how to move files from the ftp home of the ftp user to the directory I want in the srv/www folder when needed. I will look into scp as well. Thanks.

---

### Post by darkod on 2023-10-08
Even for local connections I would suggest you get used to use scp and then you will have more experience with it when you need to use it in other situations.

To move or copy files within the same server it is very easy. And since you will be working with web server files usually will need to do it as sudo or add your user to the group that has write access to the directory (not sure if the group was called www-data).

Lets say you upload the file by scp to your home folder on the server. To copy:
```
sudo cp /home/path1/file1 /path2/file1
```

To move it (this will make it disappear from your home folder):
```
sudo mv /home/path1/file1 /path2/file1
```

---

### Post by jderosa32 on 2023-10-08
Thank you for your feedback. It's appreciated.

---

### Post by TheFu on 2023-10-09
> **jderosa32 said:**
> I agree that it is old. I only amd using this locally and it is not open to the internet. If I wanted to use this outside of my network I would have to VPN into my network so I feel confident it is safe. What I can do is learn how to move files from the ftp home of the ftp user to the directory I want in the srv/www folder when needed. I will look into scp as well. Thanks.

Use rsync, not plain FTP.

$ rsync {source} {target}
Either the {source} or the {target} can be remote, but not both.  Also, different userids can be used for the remote location. So you can either "push" files where you need them or "pull" the files where you need them.  

For example, I push my keepass db nightly to a few different locations, before my backups start. Part of the script is this:
```
scp "$DB_FILE" hadar:
scp "$DB_FILE" istar:
scp "$DB_FILE" posc:

```
I also mount the webdav storage under nextcloud and push it there, which let's my android devices get the updated file daily, automatically. That's a little more complicated, as webdav is a terrible protocol.

rsync uses ssh tunnels by default, so ssh credential should be used.  Plus, if there are any issues, rerunning the same rsync will pick up where it left off.  This is how professionals manage a website.  There are about 50 tools that leverage ssh credentials and tunnels. ssh is how Unix people do remote anything.  The main ssh-based tools are scp, sftp, rsync, sshfs, and ssh, of course.  ssh can be setup to provide a SOCKS5 http proxy, if you like as well.  ssh is the only tool that I know which is both **more secure** AND **more convenient** to use. This assumes you use strong enough ssh-keys which are setup 1 time and only need to be unlocked from your workstation once per session.  I have multi-day sessions, often 7-21 days long, so unlocking my ssh credentials once in that time is not exactly a hardship. From that point on, all ssh-based connections/transfers are key-based and I don't have to enter any credentials. Extremely convenient. Setting up ssh-keys is about 30 seconds and 2 commands.

```
sudo apt install ssh rsync fail2ban
```
That will get most of the ssh tools and setup the ssh+sftp server with reasonable defaults. Easy. AND secure, assuming you don't use passwords.

As for permissions.  Standard Unix permissions apply. Nothing new.  It is a best practice for website files that don't need to be written by the website while running should be owned by some other account and that the web-server account, typically www-data on Ubuntu, should have read-only access to any files.  If you do allow uploads through the webapp, it is best practice to have a separate upload directory with w-x permissions, so the uploads can happen, but the www-data account cannot actually see the list of files inside it and other users cannot access the uploaded file through the webapp.  Always perform some error checking on uploaded files. Never trust uploaded files through webapps.  Typically, the way to ensure that happens and that nefarious data is removed is to transcode/convert any uploaded files to a different format.

Tools like vsftpd really shouldn't have been used since around 2002. We have better tools now.  Nobody should assume their LAN is secure. It probably isn't.

---

