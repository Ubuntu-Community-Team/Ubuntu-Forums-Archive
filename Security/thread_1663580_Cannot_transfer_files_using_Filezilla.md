---
title: "Cannot transfer files using Filezilla"
date: 2011-01-09
forum: Security
---

### Post by toolmania1 on 2011-01-09
I was able to transfer files using Filezilla about 2 weeks ago.  Since then, I Have made changes to the iptables including this:

sudo iptables -A OUTPUT -p tcp --dport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --weekdays Sat, Sun -j ACCEPT

Do I need to add anything else to my iptables in order to get Filezilla to connect.  

The strange things is that Filezilla seems to connect to the site.  However, it stops at the password and then says that it fails.  I know the password is correct though.  I even went to the site and changed the password right now.

Any ideas as to what I can check to see if something is set up incorrect in FIlezilla or if there is something else like a Firewall, iptables, etc. blocking the file transfer?

Thanks in advance!

---

### Post by cariboo on 2011-01-09
What protocol are you using, sftp, or ftp? You need to open port 21 in your  iptables rules for ftp, or port 22 for ssh.

---

### Post by toolmania1 on 2011-01-09
Is this sufficient?

sudo iptables -A INPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -h ACCEPT[FONT=monospace]
[/FONT]

---

### Post by toolmania1 on 2011-01-09
Well, I added that line above.  I still get connection timed out error.

---

### Post by bodhi.zazen on 2011-01-09
Well, what protocol are you using ? FTP ? If so I believe you need to allow port 20 as well. ssh (scp) is port 22. http is port 80.

Are you sure it is a problem with iptables ? what happens if you turn iptables off ?

---

### Post by toolmania1 on 2011-01-09
Ok, I will add port 20 also.

No, I am not sure it is with iptables.  I will try to turn them off also if adding port 20 does not work.

---

### Post by toolmania1 on 2011-01-09
I am wondering if it has to do with none of the above.  I added port 20.  I was able to ftp into the site.  Then, I switched users to the limited user I have.  I was not able to ftp in.  So, I switched back to the master user.  This time, I could ftp to the site. I wonder if there is a timer since last log in from the site?  

So, it may have nothing to do with any of my settings.

---

### Post by toolmania1 on 2011-01-09
Ya, I just ftp in the limited user account.  I may have needed the port 21 and 20 added anyways since I was never allowed to log in today.  So, that would not have been the case about a time out since the last log in.  But, now it all looks good.  Thanks for the advice on adding the 2 ports, port 20 and 21, to the iptables.

---

### Post by bodhi.zazen on 2011-01-09
FYI FTP is not known for security, if you can try using scp.

---

### Post by toolmania1 on 2011-01-10
Would this be sftp in Filezilla?

---

### Post by bodhi.zazen on 2011-01-10
> **toolmania1 said:**
> Would this be sftp in Filezilla?

Yes , the "s" is ssh , ie scp and sftp.

---

### Post by toolmania1 on 2011-01-10
[FONT=Calibri]I remember seeingthat as an option in Filezilla.  Do Ineed to do anything different like hit a different port or set anything on theserver?  For some reason, I rememberreading something about port 22.[/FONT]

---

### Post by bodhi.zazen on 2011-01-10
> **toolmania1 said:**
> [FONT=Calibri]I remember seeingthat as an option in Filezilla.  Do Ineed to do anything different like hit a different port or set anything on theserver?  For some reason, I rememberreading something about port 22.[/FONT]

For sftp you need to install and secure a ssh server (hint user keys and disable passwords). You would then allow only port 22.

---

### Post by toolmania1 on 2011-01-10
I am using an external server to upload my files to.


I need to install an SSH server on my pc?
 
Like this?


[https://help.ubuntu.com/7.04/server/C/openssh-server.html](https://help.ubuntu.com/7.04/server/C/openssh-server.html)

---

### Post by bodhi.zazen on 2011-01-10
> **toolmania1 said:**
> I am using an external server to upload my files to.


I need to install an SSH server on my pc?
 
Like this?


[https://help.ubuntu.com/7.04/server/C/openssh-server.html](https://help.ubuntu.com/7.04/server/C/openssh-server.html)

You have to install ssh onto the server your are connecting to, not the client.

---

