---
title: "Ubuntu Server: FTP Slow in certain folders"
date: 2010-07-21
forum: Server Platforms
---

### Post by Zylstra555 on 2010-07-21
I posted this yesterday, but my post completely disappeared (I looked high and low -- nothing.) 
I am using Ubuntu Server 10.04, all the latests updates. 
For an FTP Server, I use ProFTP. 

One specific directory, and it's subdirectories on my server will not download at a reasonable rate. They move at about 17-50KBPS. 
All other folders work fine, at around 1.5-2.5MBPS. 

What is going on? I have no idea how to troubleshoot this. The files being transfered are in a directory under home. They should have no permissions issues (I reapplied the permissions I want already), I tried restarting ProFTP, the files vary in sizes (from a few kilobytes to about 120 megabytes). 
I use Webmin for most web management. 

I am not having overload issues with my network card or CPU utilization while downloading these files. They are being accessed from the local network. 

This issue is taxing because the files in question are backup files. 

Thank you for your assistance,
- Jesse Zylstra

---

### Post by Zylstra555 on 2010-07-27
Well, it's been five days. 

No suggestions, eh?

---

### Post by drdos2006 on 2010-07-27
Is there any reason you are using FTP and not NFS to transfer files ?
regards

---

### Post by arrrghhh on 2010-07-27
> **drdos2006 said:**
> Is there any reason you are using FTP and not NFS to transfer files ?
regards

For once I agree with one of your posts drdos!  I thought you were just a machine that would repost that how-to you so adore :P

Anyhoo, I would agree that if it's local traffic NFS or Samba are preferred.

Have you accessed this FTP from outside your LAN?  Do you exhibit the same issues on other workstations within your LAN?  Are all of these folders you've tested on the same physical hard drive?  There's a lot of factors, I don't think it's a configuration issue... Stranger things have happened tho ;)

---

### Post by Zylstra555 on 2010-08-02
I just wanted to let you know that I am still on board here. 

I use FTP because FTP is easy, and I can access it from Windows computers without additional configuration on the server or client end. 

I attempted Samba a while back, it was a major pain. 

This week, I'll be going away and will be able to test from outside the network then. Thank you for your help, not having backups is a major concern.

---

### Post by Zylstra555 on 2010-08-13
Same problem occurs outside of the local network, as well as other workstations. 
All files tested are on the same physical drive, yes.

EDIT: I'd like to mention, when I use FileZilla to transfer the files on the client machine, it constantly locks up and becomes unresponsive. Also, the CPU usage goes to maximum.

---

### Post by arrrghhh on 2010-08-13
Hrm.  For troubleshooting purposes have you tried a different ftp server?  Personally I prefer vsftp, but I just want to rule out software basically.

Have you noticed what process pegs the CPU?  Is it proftpd or something different?

---

### Post by Zylstra555 on 2010-08-13
> **arrrghhh said:**
> Hrm.  For troubleshooting purposes have you tried a different ftp server?  Personally I prefer vsftp, but I just want to rule out software basically.

Have you noticed what process pegs the CPU?  Is it proftpd or something different?

I did not make myself clear, by the CPU reaching maximum, I meant to indicate the client computer. The server shows no significant CPU utilization. 

Just for fun, I entered the directory which I have been trying to access, and tried dir /mydirectory/ -R to see if it had any problems, and also opened a file from the server itself. Neither had any problem. 

I'll look in to another FTP server program this afternoon. I used to use vsftpd, I'll give it another go.

---

### Post by arrrghhh on 2010-08-13
Odd.  Let us know how vsftp works... I don't quite know how to explain CPU pegging on the client - especially different clients...

---

### Post by Zylstra555 on 2010-08-14
I tried Ubuntu's built in "Connect to Server" wizard for FTP with Login, and it copied all files in the directory fine. 
It paused a few times, but not for long. Everything copied at a reasonable rate. (At the end, the average speed was 1.9mbps) 

I tried changing FileZilla's transfer modes, passive to active, force binary transfers and force ASCII transfers, no difference. 

I'll give VSFTPD a try later this week

---

