---
title: "Monitoring User Activities"
date: 2010-06-06
forum: Server Platforms
---

### Post by PyrexKidd on 2010-06-06
I am currently running Ubuntu Server 9.10 as an FTP server.

It has become a necessity to allow users access via SSH terminal or sftp via WinSCP.  I need to be able to monitor what users are doing at any given time and be able to pull up each users activity history.  Essentially I need to be able to pinpoint who modified a file at what time.

Also what is the best method to monitor things like nmap probes?

Thanks in advance for the assist?

---

### Post by BoneKracker on 2010-06-06
NMAP probes you can identify in your firewall logs.  You can use a firewall log analysis program to make that easier.  You can go one step further and use a Network Intrusion Detection System (NIDS) to try to respond to such events.  Look at snort, snort-inline, and similar things.

Basic user monitoring is built into Linux, but if you need to be able to tell who modified certain files, I think you need something like SELinux or GRSecurity.  On Ubuntu (which I don't use), I would assume your easier option is SELinux.  These enhanced security architectures provide detailed auditing of such things as actions taken under sudo root privileges, mounting and unmounting of drives, all kinds of stuff.

They also give you fine-grained control over what users are able to do.  There are many ways to achieve enhanced control and auditing, but SELinux is packaged, documented, and as I understand it, a certain amount of support for it is built into Ubuntu.

That's a response to what you have stated as your requirement.  However, not fully understanding your issue, I suspect you might be able to do something simpler, such as restrict access through SSH and FTP to certain directories, or assign SSH and FTP users a UID with few or no privileges (unless they are account-holding users).  You could also run SSH and FTP in a virtualized environment or a linux container, which would isolate all their activities from the real system.

---

