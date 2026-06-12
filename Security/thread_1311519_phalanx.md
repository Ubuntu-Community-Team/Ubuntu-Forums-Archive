---
title: "phalanx?"
date: 2009-11-02
forum: Security
---

### Post by tristan@Ubuntu on 2009-11-02
Hello,
I have been receiving CRON emails for some time now that first looked like that: 


Date: Thu,  8 Oct 2009 11:00:01 -0400 (EDT)
From: Cron Daemon <root@################>
To: root@##############
Subject: Cron <root@##########> /usr/share/ixscEYMlmLxu.p2/.p-2.4c i &> /dev/null

(_-  phalanx 2.4d -_)
; mmap failed..bypassing /dev/mem restrictions
; locating sys_call_table..
; sys_call_table_phys = 0x6a88e0
; phys_base = 0x0
; sys_call_table = 0xffffffff806a88e0
; hooking.. ################
; locating &tcp4_seq_show..
; &tcp4_seq_show not found
>>injected

I was kind of worried, and I removed the /usr/share/ixscEYMlmLxu.p2/.p-2.4c file (I know this is a somewhat brutal approach...). Since then, I now receive, every minute, emails that look like that:



Date: Mon,  2 Nov 2009 14:08:01 -0500 (EST)
From: Cron Daemon <root@############>
To: root@####################
Subject: Cron <root@##########> /usr/share/ixscEYMlmLxu.p2/.p-2.4c i &> /dev/null

/bin/sh: /usr/share/ixscEYMlmLxu.p2/.p-2.4c: not found


I tried rkhunter and chkrootkit, but found nothing wrong. I also looked into cron and crontab to see what was scheduled every minute, but found nothing... Except these emails, the computer seems to behave normally. Any idea? Should I worry? Thanks.


--Tristan

---

### Post by __p1n__ on 2009-11-02
Your machine is infected with an out-of-date version of the phalanx rootkit.  Good job sharing your SSH keys around.

Try upgrading to the current 2.4g version (aka phalanx2) to both:

1. eliminate the 1-a-minute error e-mails
2. ensure that the rootkit operates normally

edit: The intercept-syscall logic in phalanx still works as of 2.6.29-1.  A kernel bug is open and a quick perusal of the maintainer's forum indicates that this is working as designed and there's lots of quibbling over the status of the vulnerability.  In any event the logic only works if the process has obtained uid=0 priviledge.

---

### Post by TaTaE on 2009-11-02
Sorry , dude

[CERT: Linux servers under 'Phalanx' attack]("http://www.google.ro/url?sa=t&source=web&ct=res&cd=2&ved=0CA0QFjAB&url=http%3A%2F%2Fwww.theregister.co.uk%2F2008%2F08%2F27%2Fssh_key_attacks_warning%2F&ei=fkHvSpTYLNTGsgas273lCA&usg=AFQjCNH4wP0Cd1M65ZROMDnSHm2dF4M_Ag&sig2=z84ztycNMf8ltsmP3tDB5g")


Your system could be infected with a rootkit. Save your personal files and reinstall it all over again.

---

### Post by tristan@Ubuntu on 2009-11-02
> **TaTaE said:**
> Sorry , dude

Your system could be infected with a rootkit. Save your personal files and reinstall it all over again.

Thanks for your help.

I have several drives on this machine, with one only being used for / (and, for example, another one for /home). Should I format everything, or just reinstalling the system will be enough? In other words, is the rootkit also potentially hiding in the user folders?

---

### Post by __p1n__ on 2009-11-02
> **TaTaE said:**
> ... Your system could be infected with a rootkit ...

Not "could be" but rather "is."  Mitigating this is the fact that it appears to be both broken (deleted p-2.4.c client) and out of date version.

---

