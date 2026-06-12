---
title: "Segmentation faults"
date: 2007-08-20
forum: Server Platforms
---

### Post by Breki on 2007-08-20
Hi there!

I've got a fileserver at home running Ubuntu, then four 400Gb-drives in a software raid5. My system resides on a dedicated 100Gb-disc.

About a week ago, I was logging in (as root) over SSH from my laptop to run **apt-get update**, but kept getting stuff like this:

Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [11.8kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Sub-process bzip2 received a segmentation fault.
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [26.5kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Sub-process bzip2 received a segmentation fault.
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Sub-process bzip2 received a segmentation fault.

Confused at why I'd be getting segfaults, I tried some random commands to see if they'd give me segfaults as well. One of the commands that I ran was **netstat**, which gave me this:

root@hyuga:/# netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 0 hyuga.RP614v4:56867 irc2.saunalahti.fi:ircd ESTABLISHED
tcp 0 0 hyuga.RP614v4:55519 zagreb.hr.eu.under:9999 ESTABLISHED
tcp 0 0 localhost:41300 localhost:9092 ESTABLISHED
tcp 0 0 hyuga.RP614v4:56198 undernet.xs4all.nl:ircd ESTABLISHED
tcp 0 0 hyuga.RP614v4:56210 undernet.xs4all.nl:ircd ESTABLISHED
tcp 0 0 localhost:9092 localhost:41300 ESTABLISHED
tcp 0 68499 hyuga.RP614v4:9000 192.168.1.101:39926 ESTABLISHED
tcp 0 0 hyuga.RP61:microsoft-ds 192.168.1.101:2477 ESTABLISHED
tcp 0 0 hyuga.RP614:netbios-ssn 192.168.1.23:1789 ESTABLISHED
tcp 0 0 hyuga.RP614v4:3483 192.168.1.101:39813 ESTABLISHED
tcp6 0 1452 hyuga.RP614v4:ssh internet-gw-ext.e:63663 ESTABLISHED

Now, the lines accessing the IRC-servers are a known problem meaning that my account has been compromised and the computer is being used as an IRC bot of some sort. I checked my access logs:

root@hyuga:/home# cat /var/log/auth.log | grep Accept
Aug 19 12:37:06 hyuga sshd[14725]: Accepted password for root from 172.179.160.242 port 1534 ssh2
Aug 20 11:44:07 hyuga sshd[15428]: Accepted password for root from 194.237.142.3 port 63663 ssh2

The 194-address is me at work, the 172-address lands on AOL's network.

**Netstat -p** gave me the PID for the process that was performing the connections to foreign IRC servers, so I typed out a ps aux | grep 14751 and got:

root 14751 0.0 0.0 1968 912 ? Ss Aug19 0:00 sh

So; somebody'd created a shell as root. Ungood. A file called "just.tgz" existed in my home directory as well. I killed the process, but **rm just.tgz** gave me a segmentation fault. **bzip2** was still also giving me segmentation faults.

I've managed to fix all of the issues regarding the IRC bots and the insecurity of my system (I think), but I'm still running into segmentation faults. I can't log in as non-root, because **su** and **sudo** both give segfaults. I can't **apt-get** any updates or reinstall anything that way because of **bzip2** segfaulting. What do you think this is all about?

root@hyuga:/# su
Segmentation fault
root@hyuga:/# chmod
Segmentation fault
root@hyuga:/# rm
Segmentation fault
root@hyuga:/# bzip2
Segmentation fault
root@hyuga:/# lsmod
Segmentation fault

---

### Post by DMills on 2007-08-20
Sounds like someone has rooted your box and then done a poor job of installing modified binaries for common commands. 

Boot from a CD and (if you have the capability) check the MD5 sums of all the executables on the system match those in the packages. Often it is just plain easier to reinstall the system under these conditions (Keep /home and nuke the rest down to bedrock, it is the only way to be sure). 

Don't forget to compare the contents of configuration files with the backups to ensure no backdoors have been created that way. 

Boring but recovering a box that has been as utterly compromised as this one sounds to be, is normally more trouble then it is worth. 

BTW: Why do you allow root logins from ssh? Giventhe number of dictionary attacks being perpetrated out there, I am nervous of allowing password (but non root) logins from the net, a usb key with a crypographic key is safer IMHO.

God I hate crackers. :mad:

---

### Post by Breki on 2007-08-20
> **DMills said:**
> Boot from a CD and (if you have the capability) check the MD5 sums of all the executables on the system match those in the packages. Often it is just plain easier to reinstall the system under these conditions (Keep /home and nuke the rest down to bedrock, it is the only way to be sure). 

I can boot from CD, that's how I reinstalled the system last time this very same thing happened. I figured it was just a fluke back then, but now that the same thing happened a second time I figured there must be an underlying cause. First I suspected faulty memory or other hardware, but this time around, I noticed the unlawful logins as well.

What's the best way to compare MD5-sums when booting from the Ubuntu CD?

Also, keeping /home will be easy, since /home is my raid5-partition and isn't stored on the system disk. :) All I really have to do is repartition, reformat, then install mdadm and mount /dev/md0 as /home and I'm back to normal (more or less, just need to add/configure samba and slimserver)

Your guess that the files have been replaced seems reasonable, as they all have a different timestamp:

-rwxr-xr-x 1 root root  22240 2007-08-20 14:43 readlink
-rwxr-xr-x 1 root root  38696 2007-08-20 14:43 rm
-rwxr-xr-x 1 root root  14000 2007-03-05 07:25 rmdir

Of these three files in my /bin only **rmdir** works. The rest have been touched today, exactly while I was writing this message.. another **ls -l** showed that they'd been touched again just a minute later.

> **DMills said:**
> BTW: Why do you allow root logins from ssh? Giventhe number of dictionary attacks being perpetrated out there, I am nervous of allowing password (but non root) logins from the net, a usb key with a crypographic key is safer IMHO.

I'm asking myself the same question, really. :) Originally I set this server up to just be a little play-pen where I could practice my linux "skillz", but over time it grew into a webserver and internal fileserver with 1.2Tb storage. For some reason, I never bothered removing root access from ssh.

When I reinstall this time around, I'll make sure to do that and keep all the passwords long and complicated. What's the simplest way to remove permissions? Just add the group 'root' to users that aren't allowed to log in via SSH for any reason? Where do I do that?

***EDIT***: Never mind, found the "**PermitRootLogin yes**"-line in */etc/ssh/sshd_config* - is it enough to change that to 'no' or is there some other recommended way?

***EDIT2***: Would there be any way for me to log in via FTP and replace the files *rm* and *bzip2*? If I do that, I should be able to run a **apt-get install --reinstall coreutils** and replace the rest, no?

---

### Post by bapoumba on 2007-08-20
Moved to "Servers & Security".

---

