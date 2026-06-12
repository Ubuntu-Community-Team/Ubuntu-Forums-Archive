---
title: "FTP server issues"
date: 2011-05-03
forum: Server Platforms
---

### Post by clegends on 2011-05-03
Hi, I'm having issues with using vsftpd on my Ubuntu 10.04.2 server. I can ssh into my box, send/receive emails, host my dns, access websites served on it, but I can't figure out vsftpd. 

The issue is weird... after configuring the /etc/vsftpd.conf file, I was able (as a local user) to ftp into the system fine. But when I tried a different user, it hung from my gftp client with 'Connected', but nothing happened. No files on the server, nada, zilch. When I tried the original account that worked, I got the same thing. I rebooted the machine, and got similar behaviour. I also just realized that my firewall was not configured to be up at boot (oops - fixed that now), so even without the firewall up I still had issues. Is anyone able to help me take a look at this? Thanks very much in advance.

---

### Post by hawk2010 on 2011-05-03
My best guess is that you have folder non-existence or folder/file permission issues. When a new user is created with useradd command : useradd newuser it doesn't create the home folder. You have to explicitly say useradd -m newuser for the user's home folder to be created. Also do a ls -l on /home and see if the newuser's home directory has ownership and permissions set to the newuser. Also check the vsftp logs for possible errors. hope this helps.


> **clegends said:**
> Hi, I'm having issues with using vsftpd on my Ubuntu 10.04.2 server. I can ssh into my box, send/receive emails, host my dns, access websites served on it, but I can't figure out vsftpd. 

The issue is weird... after configuring the /etc/vsftpd.conf file, I was able (as a local user) to ftp into the system fine. But when I tried a different user, it hung from my gftp client with 'Connected', but nothing happened. No files on the server, nada, zilch. When I tried the original account that worked, I got the same thing. I rebooted the machine, and got similar behaviour. I also just realized that my firewall was not configured to be up at boot (oops - fixed that now), so even without the firewall up I still had issues. Is anyone able to help me take a look at this? Thanks very much in advance.

---

### Post by clegends on 2011-05-03
Hmmm. That makes since. My users permissions are all fine (the ones I've been trying to log in with), but I noticed that the ftp home folder I created was root:root ownership. Wonder if this was a problem? I have changed it, but now can't connect at all. i think this is a firewall issue now, as it is back up. What ports do I need to open? It would be nice to have both Windows and Linux machines able to access the FTP. (so both passive and active I guess) Thanks for such a speedy reply. Mitchell

---

### Post by hawk2010 on 2011-05-04
Ok great. Yes. If you are logging as the "newuser" and that user's home directory has root.root ownership then it would be problematic. Make sure that the owner of the home dir can read/write and execute enabled. 

chmod -R 750 /home/newuser (this should take care of that)

Also check on your vsftpd.conf that you allow the "newuser" l Please check your ufw logs or /var/log/messages /var/log/auth.log to see if you can see any traffic inbound to port 21 . on your ftp server you only need allow port 21 : ufw allow 21 (this will enable both ur windows and linux cilents connectin)

> **clegends said:**
> Hmmm. That makes since. My users permissions are all fine (the ones I've been trying to log in with), but I noticed that the ftp home folder I created was root:root ownership. Wonder if this was a problem? I have changed it, but now can't connect at all. i think this is a firewall issue now, as it is back up. What ports do I need to open? It would be nice to have both Windows and Linux machines able to access the FTP. (so both passive and active I guess) Thanks for such a speedy reply. Mitchell

:guitar:

---

