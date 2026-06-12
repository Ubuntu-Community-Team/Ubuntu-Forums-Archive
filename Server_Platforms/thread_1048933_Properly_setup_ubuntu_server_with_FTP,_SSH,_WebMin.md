---
title: "Properly setup ubuntu server with FTP, SSH, WebMin"
date: 2009-01-24
forum: Server Platforms
---

### Post by AegisTalons on 2009-01-24
Hey everyone,

So I have a small shuttle PC computer that I repurposed to be my server. This server I intend to be mainly my backup server for both my desktop and laptop. I also may want to do some sort of media streaming to these computers and my hacked Xbox running XBMC.

Now I have basic functionality running, but I feel that this is not enough. For example, the server has two physical drives, a 20 gig and 750 gig. The 20 gig one is what it came with and the swamp and / partitions are setup on this partition. I want to setup all users onto the 750 gig hard drive, but I do not know how. Currently, the /home/user/ is setup on the 20 gig, and there is a folder in there called big_HD linking to the 750 gig.

I also want to setup a FTP server using port 22 for SFTP, I'm currently using ProFTPD. Does anyone know how to do it with ProFTPD or is there a better FTP server out there? Keep in mind that I would like for it to have a WebMin Module so it is easier for me to configure.

Also any sites with this information clearly laid out would greatly be appreciated.

---

### Post by hyper_ch on 2009-01-24
why not just use sftp/scp by instlling openssh-server and mysecureshell to chroot system accounts?

---

### Post by redroad55 on 2009-01-24
Hi, this sounds alot like what I'm trying to do..Hyper_ch could you elaborate a little more , maybe sources and documentation ..I would greatly appreciate it ..

---

### Post by Kelmas on 2009-01-24
As far as I know, Pure-FTPd is able to work with SFTP fine. I am using it on a cPanel-powered server but yet not sure how to install it on Ubuntu Server.

I had my Ubuntu Server up today, this is my first forum post here... :oops:

---

### Post by hyper_ch on 2009-01-25
for scp you just need to install openssh-server and then add system users. Then also install mysecureshell and change the shell of the system users to mysecureshella nd properly configure it.

you can then use: [http://www.winscp.com](http://www.winscp.com) or other tools that support scp

---

### Post by AegisTalons on 2009-01-26
So currently the server that I do have up, does have SSH and it does have a FTP server running. While I'm typing this up, my laptop is transferring pictures that I took to the server for backup. I would like something that is easy to manage, preferably with a Webmin module. How do you make ProFTPD running in SFTP mode on port 22?

---

### Post by pdtpatrick on 2009-01-26
say that again? are you asking how do you make proftd only work on port 22? You edit the .conf file in the /etc directory and change the ports that the ftpd listen on ..

---

### Post by hyper_ch on 2009-01-26
you can only run one daemon on a given port... so I'd deinstall proftp and just use openssh server and create a new shell with mysecureshell to chroot people accordingly.

---

