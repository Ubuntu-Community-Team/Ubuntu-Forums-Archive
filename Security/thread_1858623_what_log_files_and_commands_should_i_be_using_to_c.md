---
title: "what log files and commands should i be using to check if someone is attacking my os"
date: 2011-10-12
forum: Security
---

### Post by mushy365 on 2011-10-12
I'm trying to learn about ubuntu. At the minute im just installing and configuring services like vsftpd, samba and apache. I realise having these processes running might make my system more vunerable. 

I dont know anything about security on ubuntu, so what do i need to be doing and looking out for to make sure my system is safe or at least not under attack?

---

### Post by CharlesA on 2011-10-12
/var/log/auth.log is always a good one to check.

---

### Post by bodhi.zazen on 2011-10-13
> **mushy365 said:**
> I dont know anything about security on ubuntu, so what do i need to be doing and looking out for to make sure my system is safe or at least not under attack?

Well, in my experience, if you are connected to the internet you are under attack.

Start with the security sticky, you are going to want to learn to read the logs 

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

You would watch the $service logs, apache if running apache

If at all possible , use ssh (sftp).

---

### Post by Lars Noodén on 2011-10-13
> **mushy365 said:**
>  At the minute im just installing and configuring services like vsftpd, samba and apache.

As bodhi.zazen points out, if you are connected to the net, then you are under attack.  

As far as using SFTP instead of FTP, look to the package [openssh-server](http://packages.ubuntu.com/natty/openssh-server).  It includes SFTP and it works out of the box.  No further configuration is needed.

---

### Post by CharlesA on 2011-10-13
> **Lars Noodén said:**
> As bodhi.zazen points out, if you are connected to the net, then you are under attack.  

As far as using SFTP instead of FTP, look to the package [openssh-server](http://packages.ubuntu.com/natty/openssh-server).  It includes SFTP and it works out of the box.  No further configuration is needed.
+1

Just remember to use a strong password for any account that has ssh access. ;)

---

### Post by Dangertux on 2011-10-13
> **mushy365 said:**
> I'm trying to learn about ubuntu. At the minute im just installing and configuring services like vsftpd, samba and apache. I realise having these processes running might make my system more vunerable. 

I dont know anything about security on ubuntu, so what do i need to be doing and looking out for to make sure my system is safe or at least not under attack?


I second all the other advice given in this thread it was all very good.

To answer your question about log files that can be useful in terms of determining if you're under attack or have been attacked here are my suggestions

/var/log/syslog - determining if someone is trying to , or has executed a buffer overflow (off by 1, rop , etc)

/var/log/debug - Stack tracing to determine nature of application and service based attacks.

/var/log/kern.log  - Application exploitation, local escalation and bypassing of MAC (Apparmor, SELinux)

/var/log/ufw.log - More direct method of auditing your firewall if you're using UFW, if you're not this won't help much.

/var/log/auth.log - Auditing of attacks on credentials and determination of unauthorized access.

/var/log/daemon.log - Auditing to see if services you are unaware of have been started.

dmesg - not a log file but great for determining anomalous activity from recent boots.

Service Specific logs

/var/log/apache2/access.log - Useful for detecting web based attacks (XSS, XSRF, SQL injection, remote file inclusion/upload etc)

/var/log/apache2/error.log - Same

/var/log/mysql.log - database attacks

/var/log/mysql.error - same

Hope this helps these are the big ones I look for on compromised systems.

---

### Post by mushy365 on 2011-10-13
Thanks for the list, really helpfull. I guess i need to decide what i want to do now, snort seems overly complex at this moment, not sure ill get the reward from installing it as i got from installing and configuring samba etc, but worth looking at. 

I dont like the idea of having to create a database for it,

---

### Post by Kinstonian on 2011-10-13
> **mushy365 said:**
> Thanks for the list, really helpfull. I guess i need to decide what i want to do now, snort seems overly complex at this moment, not sure ill get the reward from installing it as i got from installing and configuring samba etc, but worth looking at. 

I dont like the idea of having to create a database for it,

You don't need an IDS to detect attacks.  You're right Snort would be overkill.  You may be surprised how effective simple tools like grep, cut, sort, netstat, ps, lsof, etc. can be.

A big part of detecting attacks is understanding what is normal and benign for your computer, rather than what is bad (what an IDS detects).  IDSs certainly have their place, but are often overkill.  Cheap to setup, but expensive in time required to manage and investigate alerts.

A few minutes a day greping logs and investigating things that are unusual or you don't understand will help you find not just security problems, but typical admin problems.

---

### Post by mushy365 on 2011-10-13
I agree with what you said, but for the purposes of learning and from what ive read on the other thread. I might look into making my ubuntu computer as some sort of firewall running snort that inspects all traffic before reaching the laptops. 

The problem i have that might prevent me from doing it is this, my isp sent me a router that the laptops access via wifi. MY ubuntu computer does not have wifi so is connected to router by cable

if i want all the traffic to go through my ubuntu computer first, then surely id need to send the info to the laptops via wifi, which i wont be able to do as my ubuntu computer does not have wifi

---

