---
title: "vsftpd wont start"
date: 2010-01-03
forum: Server Platforms
---

### Post by jprizzo on 2010-01-03
Hello,
I am trying to get vsftpd started on my server. I followed the steps outlined here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html) but for some reason, the daemon is not starting or throwing an error message. After making all of the changes to vsftpd.conf, if I execute the following commands, here is the result:
 
 
sudo /etc/init.d/vsftpd start
* Starting FTP Server: vsftpd [ OK ]
 
sudo /etc/init.d/vsftpd status
vsftpd is not running
 
I feel like I must have missed a step, but for the life of me, I can't figure out what. Can anybody offer any suggestions? Please help.
 
Thanks,
 
Jon

---

### Post by Lars Noodén on 2010-01-04
Unless you are planning on serving read-only connections over unencrypted FTP, try uninstalling vsftp and using openssh-server.  It has sftp support built-in.  Once openssh-server is installed, you can connect to it right away with an sftp client: FileZilla, Nautilus, Konqueror, Fugu, Fetch, Dolphin or others.  

sftp is more secure and less complicated than ftps

openssh-server is far easier to configure than vsftpd.  It is also trivial to chroot users to their home directories or other destinations.

---

### Post by jprizzo on 2010-01-04
Thanks.  I need to install a regular-old ftp server that can be accessed by clients which may or may not support sftp.  This server is behind a firewall and will be used for web development only.  I am trying to emulate the environment supplied by my hosting provider as closely as possible, which is ftp only.  Does openssh-server meet this requirement?  If not, I would really appreciate any assistance you can provide to help me resolve my current dilemna.  
 
Jon

---

### Post by Lars Noodén on 2010-01-04
Lots of tools you already have  support sftp.  But do your staff need read-only access and is it ok for the data to be read in transit?  If yes to both, then FTP is for you.  

If not, then sftp will save you and your users hours of work apiece.  
If you have openssh-server installed already, which you probably do if you're working on a server, then sftp is already there for you.  Give it a 10 minute test with a client of your choice.

Also, a secret about firewalls is that they can't really protect anything that is already vulnerable.  Sometimes they can add one extra step, though, enough to discourage the least persistent.  

What is you hosting provider and hosting package?  ssh/sftp is probably part of the deal and goes without saying.  Try asking your hosting support which version of ssh they provide.

---

### Post by jprizzo on 2010-01-04
*sigh*
 
I did not come here for an ftp vs ssh debate.  All I need to know is how to start vsftpd on my server.  I appreciate your opinion and I thank you for your advice, but I need to enable the ftp server, even if you think I don't.  Following the steps outlined in established Ubuntu documentation did not help, so I am begging for some assistance in completing what should otherwise be a simple task.  Can you help me?

---

### Post by commandergc on 2010-01-04
check VSFTP's log as that may give you a clue as to what could be causing to not run.

```
sudo nano /var/log/vsftpd.log
```

---

### Post by Lars Noodén on 2010-01-05
There is no debate anymore, what little there was dealt with the transition from ftp to sftp and that discussion was finished years ago.  

The problem you described is to "emulate the environment supplied by my hosting provider"  

If the hosting provider provides SFTP, as most do, then the configuration got orders of magnitude easier.  If it does not, then we can look at the onerous task of [FTP](http://ubuntuforums.org/announcement.php?a=54).

---

### Post by jprizzo on 2010-01-05
> **commandergc said:**
> check VSFTP's log as that may give you a clue as to what could be causing to not run.

Oddly enough, the log is empty (?)

---

### Post by commandergc on 2010-01-06
are you sure that vsftp isn't running? have you tried to connect to the ftp server? ie from the command line "ftp localhost"

also try using this command to start, stop and restart it
```
sudo service vsftpd stop
sudo service vsftpd start
sudo service vsftpd restart
```

---

### Post by jprizzo on 2010-01-06
> **commandergc said:**
> are you sure that vsftp isn't running?

Thank you for the suggestion.  I'm quite sure it isn't running.  Here is the output from the commands you suggested:

>ftp localhost
ftp: connect to address 127.0.0.1: Connection refused
Trying 127.0.0.1...
ftp: connect: Connection refused
>sudo service vsftpd stop
 * Stopping FTP server: vsftpd                                                  
No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
>sudo service vsftpd start
 * Starting FTP server: vsftpd                                           [ OK ] 
>sudo service vsftpd restart
 * Stopping FTP server: vsftpd                                                  
No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd   

>ftp localhost
ftp: connect to address 127.0.0.1: Connection refused
Trying 127.0.0.1...
ftp: connect: Connection refused

---

### Post by Tail on 2010-01-06
I'd suggest you try out Glftpd if you need more advanced features. If you're not, take a look at or ProFTPD. 
At least they run perfect for me.

---

### Post by Grim76 on 2010-01-06
You might want to post a copy of your configuration so that we can see if there is something wrong in your .conf file.

---

### Post by jprizzo on 2010-01-07
> **Grim76 said:**
> You might want to post a copy of your configuration so that we can see if there is something wrong in your .conf file.

the configuration is attached.  I added the .txt extension so the forum would let me post it.

---

### Post by Grim76 on 2010-01-07
Try commenting out the last line of your configuration.  The one dealing with the SSL Cert.  See if vsftpd starts then.  My guess is the SSL Cert is where you could be having issues.

---

### Post by jprizzo on 2010-01-09
> **Grim76 said:**
> Try commenting out the last line of your configuration.  The one dealing with the SSL Cert.  See if vsftpd starts then.  My guess is the SSL Cert is where you could be having issues.

Thank you for the suggestion.  I commented out the line about the ssl cert, but the service still does not start.

---

### Post by kewlrichie on 2010-01-10
I just recently setup vsftpd with no problem and not much configuring it should start right away very weird that the status is saying it's not running after the start says OK. Did you use that 6.06 LTS server guide because your using 6.06 ?? Why not use atleast 8.04 or something a bit newer ?

---

