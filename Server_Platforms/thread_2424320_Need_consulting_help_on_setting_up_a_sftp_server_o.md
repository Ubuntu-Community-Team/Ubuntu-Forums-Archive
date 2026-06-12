---
title: "Need consulting help on setting up a sftp server on Ubuntu 16.04."
date: 2019-08-06
forum: Server Platforms
---

### Post by roadrawts on 2019-08-06
I need help on setting up a sftp server on Ubuntu 16.04.  openssh_server is installed and the sshd_config is backed up.  But there are too many choices to make to be secure.  The client is a company on the web that we need to transfer many files from to an external drive on my computer.  I would need to do port forwarding, setting up a user account for the client, limiting the destination to the external drive, and so on.  Even though I've been using Ubuntu for many years I am nowhere near having admin capabilites.
Thank you in advance.

---

### Post by wildmanne39 on 2019-08-06
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by volkswagner on 2019-08-06
Can you further explain the scenario (can you pull the data from them vs them pushing it to you)?

You'll want to limit your ssh server to key pairs (turn off password access), make sure root login is disabled.
When you open the port on your router, make sure you can limit the source address to the customer's public ip.
If your router can't do this, get one that can.

---

### Post by CharlesA on 2019-08-06
> **volkswagner said:**
> Can you further explain the scenario (can you pull the data from them vs them pushing it to you)?

You'll want to limit your ssh server to key pairs (turn off password access), make sure root login is disabled.
When you open the port on your router, make sure you can limit the source address to the customer's public ip.
If your router can't do this, get one that can.

In addition to this, you can find some good info about how to disallow weak ciphers here:
[https://cipherli.st/](https://cipherli.st/)

Here's some more info about hardening SSH in general:
[https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

FWIW, I prefer to pull to my server than than push files to my server. This means if the remote host is compromised, I don't have to worry about it having access to my server.

That is not always feasible, though, of course.

---

### Post by LHammonds on 2019-08-07
I used vsftpd when I wanted to setup FTP over SSL to allow communication with various banks and vendors.  This allowed secured file transfers with the most compatible option (most vendors could automate connections to it or use popular clients manually such as Filezilla and WinSCP)

But rather than letting them READ and WRITE to my final destination, I instead used a backend script to push files around to ensure ftp users had extremely limited access to my network resources.

If people from my company needed files made available to ftp users, there was a specific place they placed files and my server would automatically pick them up and move them to the ftp user's folder so they could see them when they logged in.

If files were inbound from ftp users, my scripts would move the files from their home directory and place them where my internal users could access them.

For my internal users, I simply had a samba share on my Ubuntu server they could access.  For data being feed into databases, my scripts would push them directly into an import folder on a database server that would get imported.

The design was such that files never sat on the ftp users home folder for very long.

I documented [how I setup my FTP server for Ubuntu 16.04 here]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=228").

LHammonds

---

### Post by roadrawts on 2019-08-07
Thank you.  I'll check out your documented "how I setup my FTP server".  
Mel

---

### Post by roadrawts on 2019-08-07
They will be pushing data to my server.  They don't accept key pairs, just passwords.  This is going to be a one-time move of 160GB of files to an external drive.  Then I'm getting rid of the SFTP all together.  I won't have a need for it in the future. They did give me their ip address so I can limit it to that site.
Thanks for your suggestions.  
Mel

---

### Post by TheFu on 2019-08-07
For a 1-time move, never underestimate the simplicity of a 256GB Flash drive using encrypted storage and FedEx delivery.
Kinston sells HW encrypted flash storage of the size needed.

---

### Post by roadrawts on 2019-08-07
why did you use vsftpd instead of sshd for the sftp services?

---

### Post by roadrawts on 2019-08-07
That would be a good idea but we're using a cloud based data mover that allow sftp services.  I doubt that they would consider dumping our files to a flash drive.  But I'll ask.  Thanks for the suggestion.
Mel

---

### Post by TheFu on 2019-08-07
> **roadrawts said:**
> why did you use vsftpd instead of sshd for the sftp services?

Probably a personal preference for people formerly using plain FTP, since vsftpd has been used for that for decades.

OTOH, for people comfortable using openssh, knowing that sftp-server is built-in and can be massively secured with little effort, provided you don't allow passwords, block brute force attacks, lock down the sourced IPs and limit the drop-off directory (all easily handled in the sshd_config file.  sftp uses 1 open port to the internet. Plain FTP uses multiple ports that chance, which isn't firewall friendly. I don't know about ftps. 

I wrote a not-great, but good enough ssh-security article a few years ago.
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

You really should push using ssh-keys, not passwords.  On the client-side:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
Failing that, you can allow passwords from specific IPs.```

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no
Match Address  172.21.21.0/24,172.22.21.0/24
      PasswordAuthentication yes
```
I like passwords available from my LAN into some systems, but never from outside outside.

Use a non-standard port for ssh/sftp/scp/rsync ... I leave the default for LAN access but have the router to port translation for access from the outside world.  It really helps keep attacks from spamming our log files, though it isn't really much security. Just setup the ~/.ssh/config file with the other port and forgetaboutit.  You'll never need to know it again for any ssh-based connection.
```
host funny-remote_name_for_server
  user pete
  hostname remote5433.dyndns.org
  port 34022
```

Block remote root - this really should be the default on all Ubuntu installs.
```
PermitRootLogin no
```

Install **fail2ban** whenever, where ever you install openssh. The default config blocks brute force attacks on port 22.  If you use the router for WAN-to-LAN port translation, nothing more than installing it is needed.

You can use the built-in Linux firewall to block WAN IPs from accessing whatever port you've decided to use on the internet.  Probably best to do this at the WAN firewall machine, not on the ssh/sftp server.

If you only want sftp access and want to limit which users can do it and where they can drop files, I remember the sftp-server settings were fairly simple to accomplish that.  ChrootDirectory is one of the settings.  The sftp-server manpage spells out different options and were to enter them in the sshd_config file.  I really should setup an sftp-only server somewhere. It has been a long time since I needed one.   
```
sudo mkdir -p /var/sftp-chroot-dir/uploads
sudo chown thefu:thefu /var/sftp-chroot-dir/uploads
```
Add this to the bottom of the sshd_config
```
Match User thefu
   ForceCommand internal-sftp
   PasswordAuthentication yes
   ChrootDirectory /var/sftp-chroot-dir
   PermitTunnel no
   AllowAgentForwarding no
   AllowTcpForwarding no
   X11Forwarding no

```
This only allows sftp for that single userid.

---

### Post by LHammonds on 2019-08-07
> **roadrawts said:**
> why did you use vsftpd instead of sshd for the sftp services?
#1 It was a requirement from the initial source (bank) that wanted us to host an FTP over SSL server.
#2 Compatibility issues with specific FTP clients (I cannot remember the details now but I could not make it work until I used vsftpd.  My inexperience back then might have contributed to issues)
#3 When I find a workable solution, I tend to stop looking for other solutions and refine what I have.
#4 It needed to be rock solid, reliable, secure and capable of supporting many different vendors.

But as TheFu said, it comes down to preference and use cases.  vsftpd fit the bill and was rock solid when I implemented it back on Ubuntu 12.04 up until the end of last year when I lost my job.  It was the central file transfer service for external vendors, banks and internally for databases and EMRs for various remote sites.

LHammonds

---

### Post by roadrawts on 2019-08-08
Thank you all for your help but I've abandoned using SFTP.  The source system tells me that large files will probably fail.  That means that I would have to do a lot of monitoring and fixing.  So I'm looking at other alternatives.
Mel

---

### Post by LHammonds on 2019-08-08
> **roadrawts said:**
> The source system tells me that large files will probably fail.Eh...why is that?  Do they have bad Internet connection?  Is there a bandwidth limiter?   Or does their xfer system timeout if a file does not finish within a specific amount of time?  If they think SFTP will fail, then what will work?

---

### Post by CharlesA on 2019-08-08
> **roadrawts said:**
> Thank you all for your help but I've abandoned using SFTP.  The source system tells me that large files will probably fail.  That means that I would have to do a lot of monitoring and fixing.  So I'm looking at other alternatives.
Mel

What? How large of a file are they talking about?

There are several FTP programs that support resuming interrupted downloads and uploads if an unstable internet connection is the problem.

---

