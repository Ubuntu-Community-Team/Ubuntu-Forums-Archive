---
title: "Backup with Clonezilla"
date: 2010-04-22
forum: Server Platforms
---

### Post by X1R1 on 2010-04-22
Hi, I wanna backup the corporate server in a weekly basis, and I was wondering if clonezilla can make the job. I downloaded the live cd version of the software and made the backup. BUT, I want a way to backup the server (all disk) without user interaction in a weekly basis (say fridays at 8pm start).

How can I achieve this?

Servers are 1 windows server 2008 and the other is a Linux one with squid and shorewall on it.

If clonezilla cant do what I need, is there another open source/free solution?

regards and thanks in advance.

---

### Post by dragos2 on 2010-04-22
> **X1R1 said:**
> Hi, I wanna backup the corporate server in a weekly basis, and I was wondering if clonezilla can make the job. I downloaded the live cd version of the software and made the backup. BUT, I want a way to backup the server (all disk) without user interaction in a weekly basis (say fridays at 8pm start).

How can I achieve this?

Servers are 1 windows server 2008 and the other is a Linux one with squid and shorewall on it.

If clonezilla cant do what I need, is there another open source/free solution?

regards and thanks in advance.

Whatever you do make sure that you can restore too. For example I wanted to get a file out of a lzo clone without restoring the whole image but it seems impossible:
[http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/43_read_ntfsimg_content.faq#43_read_ntfsimg_content.faq](http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/43_read_ntfsimg_content.faq#43_read_ntfsimg_content.faq)

Make sure its the right tool for your needs.

---

### Post by X1R1 on 2010-04-23
I just want complete backup/restores (including MBR), hopefully that it can be shceduled but its not a must

---

### Post by HermanAB on 2010-04-23
The problem is that in a few years when your server breaks down, your new hardware is going to be different and your backup will be useless.

It is better to backup just the data and forget about the system.  At most, I keep a tar ball of /etc.

A better way is to install all your servers on VMware and then save the VMs to DVDs.  If all the data is saved outside the VM on a networked storage device, then you only need to backup the data from that point on.

---

### Post by trig on 2010-04-23
how often do you update your back up, im sure that alot of data maybe expanded upon or change altogether.

---

