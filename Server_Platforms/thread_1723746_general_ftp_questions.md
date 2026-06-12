---
title: "general ftp questions"
date: 2011-04-07
forum: Server Platforms
---

### Post by kief75 on 2011-04-07
Moving over from running a windows server to ubuntu 10.04 lts. Apache, network config, ssh all seems very easy to setup, had some sites up in a few minutes. Ready to tackle ftp setup and looking at the info for vsftpd it seems more complex then it should be. I would like to have 3 different kinds of users:

1- web hosting user that can access the folder and sub folders that handle their site only
2- user with a folder they own for backing up data, similar to user type 1
3- ftp file server user that can read lots of stuff but write noting except in a public upload folder maybe

None of these users should have a user name that enables them to log into anything other then ftp.

I am used to a simple ftp like bulletproof or filezilla. I do not have a gui installed on this server, just the stuff that comes with the setup disc.

My question is would there be a better program than vsftpd for accomplishing this? it seems in comparison to the rest of the server that setting up ftp should be easy....

---

### Post by usatonycuba on 2011-04-07
[http://linuxreviews.org/software/ftp-clients/](http://linuxreviews.org/software/ftp-clients/)

[http://www.ivankristianto.com/os/ubuntu/howto-install-ftp-server-with-user-management-in-ubuntu/1181/](http://www.ivankristianto.com/os/ubuntu/howto-install-ftp-server-with-user-management-in-ubuntu/1181/)

[http://www.net2ftp.com/](http://www.net2ftp.com/)

---

### Post by mikeygstl on 2011-04-07
Two options that I can think of off hand:

1: Combine vsftpd with xinetd

what you may want to do is install xinetd, and use that to fire up vsftpd servers on a per-virtual-host basis.  In this way you could specify that if someone connects to [ftp://www.mydomain.com/](ftp://www.mydomain.com/), xinetd sees the host 'mydomain.com' and fires up a vsftpd daemon to handle that request with the appropriate configuration file, such that the connection is chroot'd (restricted per se) to the website's root folder.

2: Use ProFTPD

It utilizes much of the same configuration syntax and terminology as apache, so may be more familiar and easier to maintain.  I know it supports virtual hosts out of the box, but may be more difficult to chroot users - been a while since I've used it.

reference:  [http://www.proftpd.org/docs/howto/Vhost.html](http://www.proftpd.org/docs/howto/Vhost.html)


At work we are restricted to using vsftpd, hence the reason I know of the xinetd trick ;)

---

### Post by kief75 on 2011-04-22
So far I did decide to use vsftp and i have set it up so that each user can only access the home folder. It seems to work fine except I have one problem. I want users to have ftp access but not ssh or other shell access. I was told this would do it....

sudo vi /sbin/nologin
sudo groupadd ftpusers
sudo useradd -s /sbin/nologin -d <home dir> -g ftpusers <username>

It works fine if I leave out the "-s /sbin/nologin" but then that user can log into anything. Also a side question can I set a user to be read only while leaving write access on for others?

Thanks much =)

PS I assume there is no problem making more then 1 user have the same home dir (read only users) and create links to things I would want users assigned to that home folder and in turn what users would be able to see in ftp?

---

### Post by kief75 on 2011-04-24
anyone?

---

### Post by netzion on 2011-04-25
consider using proftpd with database support and creating/administrating users in database?

---

### Post by cipherboy_loc on 2011-04-25
You want to disable SSH access except for a small list of admins? Try this:
[http://www.linuxquestions.org/questions/linux-security-4/howto-sshd-deny-all-users-except-for-one-368752/](http://www.linuxquestions.org/questions/linux-security-4/howto-sshd-deny-all-users-except-for-one-368752/)

See the 2nd article.

---

### Post by Lars Noodén on 2011-04-25
> **kief75 said:**
> 
My question is would there be a better program than vsftpd for accomplishing this? it seems in comparison to the rest of the server that setting up ftp should be easy....

Yes.  The better program is OpenSSH, you might already have it installed and configured.  It works with SFTP right out of the box.

If you can reach the machine with SSH then you already have all you need to use SFTP instead of FTP.  SFTP is a newer protocol and designed from the ground up to be secure. You can use regular [GUI clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) like Filezilla.  SFTP sup

---

### Post by kief75 on 2011-04-25
OK excellent info thanks guys. From my understanding the best and most elegant solution is the most simple solution. Im using Ubuntu 10 server install and the packages needed from that install. That was the reason for vsftp. It seems if there is no other security risk or reason to worry about excess users on the server then blocking ssh would be the simple way to go. Other then physical contact with the machine that makes it pretty safe? I also use an unusual port and currently dont have it open to the internet anyway.

I had though of proftpd with database but seemed overkill for 3-10 that need personal space and 10-20 read only users.

As for SSH and sftp as Lars mentioned that would actually make it so all those users were in via ssh and can do stuff then no?? That seems opposite of what I want. Also vsftp does offer a secure option I can investigate.

For read only users is the best option to create folders with links to the content I want to share? Set permissions to 744 and root as owner and they could then only read? Need to get that data to a linux partition its ntfs now.

---

### Post by Lars Noodén on 2011-04-26
> **kief75 said:**
> 
As for SSH and sftp as Lars mentioned that would actually make it so all those users were in via ssh and can do stuff then no?? That seems opposite of what I want.


Then you want to make the [accounts only use SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts) and not both SSH and SFTP.   It's easy enough that it is only to change a line or two in the SSH server configuration.

The following configuration forces all members of the group **sftponly** into SFTP.  They cannot access the shell.

```

Subsystem sftp internal-sftp

Match Group sftponly
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

---

### Post by kief75 on 2011-05-22
I would like to mention up front that I am grateful for the help here and the reason I log in only every couple weeks is I have little time for this project and also I do like to research and document all my stuff.

Anyway.....Very nice I assume I can combine that sftp limit with restricted users list to only let my one login ssh and the ones in the ftp group sftp only. Can you CHROOT someone in SFTP as well? I can manage files via sftp now with the default settings. Currently I do have FTP working the way I want (except some permission issues I think will be resolved by getting off ntfs off my storage drive) and with sftp I really should not have to do anything at all it should work as setup if I understand correctly.

On some other topics maybe someone can point me to a nice (simple) way to monitor this server? Really should just need to know if http and ftp are running correctly. Would be nice for a local or remote gui file manager without installing X on the server also.

Final question it seems ext4 is better but some peeps still suggest ext3. My OS drive was auto set to ext4 but I want to put some storage drives in what is best? Also when I do either I get a lost+found folder that I cant access whats that? And almost 200 megs are used space is that the lost and found? seems I should not be using 200 meg on a new drive.

Thanks again for all the helpful pointers everyone!

---

### Post by Lars Noodén on 2011-05-22
> **kief75 said:**
> ...Can you CHROOT someone in SFTP as well?...

Yes.  You can [chroot sftp](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) also.

---

### Post by Lars Noodén on 2011-05-22
> **kief75 said:**
> ... maybe someone can point me to a nice (simple) way to monitor this server? Really should just need to know if http and ftp are running correctly. Would be nice for a local or remote gui file manager without installing X on the server also.


[cfengine](http://www.cfengine.org/) might be overkill.  [cacti](http://www.cacti.net/) might be worth looking at.  Nagios and OpenNMS are short listed also.

---

### Post by kief75 on 2011-05-22
Lars you rock! Thanks much. Thought of 2 more questions. First is it ok to have a dir that is home dir to read only ftp users and mount a storage drive inside that directory? it seems to work fine but from security standpoint?

Also I thought updates were automatic in ubuntu? I actully fixed a problem by figuring out how to update samba after a power failure and it updated all my packages, but when it boots it says updates avail inc security updates. How do I force these to install or better auto install?

Thanks again!
Kief

---

### Post by Lars Noodén on 2011-05-22
> **kief75 said:**
> ... First is it ok to have a dir that is home dir to read only ftp users and mount a storage drive inside that directory? it seems to work fine but from security standpoint? ...


If I understand the set up, it should be ok.  Some of the thumb drives will be slow to read (and slower to write) but have a hardware switch that can set them to be read-only.

---

### Post by alfamuzjak on 2011-05-22
Have u followed this guide for vsftpd configuration...[http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd+easy](http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd+easy)

Great guide, u can find there all answers u need.

---

### Post by kief75 on 2011-07-18
OK, so I have some more time to play with this, all is working well via FTP. I am trying to lock things down and want to replace FTP with SFTP as suggested however I have run into a problem. When I chroot a user to their home directory I can no longer log in via SFTP with that user. Also if I set the user to have no shell (to prevent local login) it fails as well. I understand that users need a shell to use SFTP is there a way around that or to otherwise prevent local login? The main problem/issue is the chrooted users not being able to log in via SFTP, just gets booted as soon as it tries to login via filezilla.

---

### Post by Lars Noodén on 2011-07-18
Which server package are you using for serving SFTP?

---

### Post by kief75 on 2011-07-18
I am using OpenSSH that was installed during the ubuntu server setup. It was updated using apt-get.

Thanks in advance =)

---

### Post by Lars Noodén on 2011-07-18
What does the relevant part of your configuration look like?

---

### Post by kief75 on 2011-07-18
At the end of the file I entered this section:

Match Group ftpusers
        ChrootDirectory /var/www/ftpreadonly
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

If I comment out the chroot line it seems to work as expected, which is to say it lets you log in and go anywhere you want in the file system.

---

### Post by kief75 on 2011-07-18
I seem to have figured it out, the folder needs to be owned by root. I find that strange what is the logic/reason for that? Once chowned to root I can log in with the ftp user. The reason I thought it was strange is for some users I want them to own their home directory. 

Also any thoughts on disabling local access while still leaving sftp access?

---

### Post by kief75 on 2011-07-18
1

---

