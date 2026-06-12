---
title: "enable SSH/SCP/SFTP logging"
date: 2006-08-22
forum: Server Platforms
---

### Post by sysops on 2006-08-22
hi there,

I've got SSH/SCP/SFTP up and running using the following packages

$ dpkg -l | egrep "ssh|ftpd"
ii  openssh-client                         4.2p1-7ubuntu3                          
ii  openssh-server                         4.2p1-7ubuntu3                         
ii  vsftpd                                 2.0.4-0ubuntu4                          

Everything seems to be working fine and dandy except that I note that no activity is recorded to syslog.

I've looked in the sshd_config file

$$ cat /etc/ssh/sshd_config | grep -i syslog -A 1
SyslogFacility AUTH
LogLevel INFO

yet still no sign of life from sshd. Am I missing further configuration?

Also, since I'd really like to monitor the activities of users who use SSH/SCP/SFTP, so is there a way of 'teeing' messages from sshd to a file as well as syslog?

Thanks,
sysops

---

### Post by chonger on 2006-08-22
What's in your /var/log/auth.log? Are there references to sshd being logged in /var/log/? That is, what is the outcome of?

grep sshd /var/log/*

---

### Post by sysops on 2006-08-22
/var/log/auth.log reports logons but nothing else in detail, this is typically what i would see even if i were to download files, create directories, change permissions, etc.

$ cat /var/log/auth.log | grep sshd
Aug 22 04:35:25 cond0 sshd[7597]: Accepted password for user from 172.28.216.221 port 4998 ssh2
Aug 22 04:35:25 cond0 sshd[7599]: (pam_unix) session opened for user user by (uid=0)
Aug 22 04:35:25 cond0 sshd[7599]: subsystem request for sftp
Aug 22 05:07:55 cond0 sshd[7599]: (pam_unix) session closed for user user

I have vsftpd running and if i normally use FTP, i'd see activities in detail such as this

$ sudo tail /var/log/vsftp.log
MoMon Aug 21 22:27:05 2006 [pid 25875] CONNECT: Client "172.28.216.221"
Mon Aug 21 22:27:05 2006 [pid 25874] [user] OK LOGIN: Client "172.28.216.221"
Mon Aug 21 22:27:06 2006 [pid 25876] [user] FAIL DOWNLOAD: Client "172.28.216.221", "/", 0.00Kbyte/sec
Mon Aug 21 22:27:48 2006 [pid 25869] [user] OK DOWNLOAD: Client "172.28.216.221", "/pub/msft/adminpak.exe", 12836920 bytes, 3010.56Kbyte/sec
Mon Aug 21 22:27:56 2006 [pid 25869] [user] OK DOWNLOAD: Client "172.28.216.221", "/pub/msft/rktools.exe", 12337752 bytes, 3736.95Kbyte/sec

I'm sorry if my original post didnt convey my intentions right, maybe now you can see what i am after.

I would have assumed that vsftpd would be logging these activities because I have vsftpd 'chroot' ftp users to their home directories automatically and the same happens when i use SFTP, but apparently it doesn't.

After having googled a bit yesterday, i came across this [http://sftplogging.sourceforge.net](http://sftplogging.sourceforge.net) , a patch to get sshd to do SFTP logging. But i think I'll wait a few more hours to see if anyone's done this an easier way before applying this patch to the source and then compiling.

---

### Post by sysops on 2006-08-22
ok, a couple of hours has most definitely passed and no word yet (could be linked to what i notice -- much walk-in traffic down the security section of these forums).

I've decided to post this minature howto to get sftp logging done incase someone else needs it.

open up a terminal and log into a temporary directory.
$ mkdir /tmp/openssh; cd /tmp/openssh

here are the commands i used .. paste them into the terminal or create a bash script.

#!/bin/bash
# =============================================================
# begin of script

# uncomment the following line if you dont have these installed
# sudo aptitude install patch patchutils fakeroot

# remove existing package
sudo aptitude remove openssh-server

# purge configuration files
sudo dpkg --purge openssh-server

# build dependancy packages needed to compile source
sudo apt-get build-dep openssh-server

# verify no broken dependancies
sudo aptitude update
sudo aptitude upgrade

# download source packages
apt-get source openssh-server

# download patch, 'buntu currently installs openssh-4.2p1 so i use the
# appropriate patch, change accordingly if you use a different version
wget sftplogging.sourceforge.net/download/v1.5/openssh-4.2p1.sftplogging-v1.5.patch

# patch source
patch -p0 < openssh-4.2p1.sftplogging-v1.5.patch

# build package
fakeroot apt-get source -b openssh-server

# install package
sudo dpkg -i ./*.deb

# end of script
# ===========================================================

now verify sshd is running

$ sudo ps aux | grep sshd
root      1543  0.0  0.4   4756  1072 ?        Ss   21:00   0:00 /usr/sbin/sshd

verify you can connect to sshd
$ ssh localhost

(if you had sshd running before and the daemon is is running now you'll notice here warnings about how RSA keys have changed .. purge the ~/.ssh/ directory)

edit the sshd_config file (you might want to look into the sshd_config manpage for directives to match your requirements, also refer to [http://sftplogging.sourceforge.net/docs/installation.html](http://sftplogging.sourceforge.net/docs/installation.html))
$ sudo vi /etc/ssh/sshd_config

once you've saved changes, restart sshd
$ sudo /etc/init.d/ssh force-reload

if all went well, you're pretty much set now. Sftp activities are loggged to /var/log/auth.log under the sftp-server process name.

don't forget to cleanup the temporary directory you were working in..

cheers

sysops

---

### Post by chonger on 2006-08-22
Looks like SFTP does not support file transfer logging.

[http://www.derkeiler.com/Newsgroups/comp.security.ssh/2003-02/0133.html](http://www.derkeiler.com/Newsgroups/comp.security.ssh/2003-02/0133.html)

This guys makes a good point about the uselessness of making sftp log file transfers.

[http://www.derkeiler.com/Newsgroups/comp.security.ssh/2004-12/0151.html](http://www.derkeiler.com/Newsgroups/comp.security.ssh/2004-12/0151.html)

> Bear in mind that SFTP is only one of many ways to achieve file
transfer over SSH. If my server's SFTP client did logging and I
happened to want to perform an unlogged file transfer, I could just
do things like this:

  ssh remotehost 'cat > uploaded' < file-to-upload
  ssh remotehost 'cat file-to-download' > downloaded
  tar czvf - directory-to-upload | ssh remotehost 'tar xzf -'
  ssh remotehost 'tar czf - directory-to-download' | tar xzvf -

and since I never invoked the SFTP binary, it would never do its
logging.

I would _guess_ (although this is just a guess) that someone decided
there was no point in making an SFTP server log in most situations,
since there was no way to ensure the log was complete or reliable. 

For security's sake, why not use vsftpd? It supports encrypted FTP as well and you do not have to create a real account for the ftp user.

---

### Post by sysops on 2006-08-23
I didn't implement logging as a means of monitoring exactly what SFTP users are upto on the server, just to have a vague idea of what users are downloading and more imporartantly what they are uploading as i need to know what new contents coming in. I kinda repect my users' privacy so i don't log everything just the xfers.

I do use vsftpd-avec-TLS with chrooted ftp access for ftp users and no anonymous logon. The default shell for ftp users is rbash and their environment is further chrooted. At most, they only access to their home directories and a limited set of tools.

It's now upto the users to choose from SCP, SFTP, FTPS, SSH or webDAV. I still get to insist on a mandatory logon with and access over a secure channel however they go about accessing the server.

Thanks for the links, seems i already got Mike Martinez's patch directly from his server.

---

