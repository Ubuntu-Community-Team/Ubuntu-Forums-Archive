---
title: "LDAP replacement for NFS/NIS?"
date: 2006-08-02
forum: Server Platforms
---

### Post by eayars on 2006-08-02
Here's my situation, and I hope someone here can help. For the last couple years I've run the computing facilities for our physics department using Slackware. Logins were via NFS/NIS, so students could log in to any computer in the lab and have the same home directory, which actually resided on a Slackware box in my office. I also had some shared volumes available with the same system, so for example any student in course 'x' could access the server's course-specific volume as /exports/x on whatever machine they logged in to.

Last spring one bright student (you get them occasionally in a physics department) convincingly demonstrated that NFS/NIS was unacceptably insecure. This summer I got new computers for the lab, so I started over. I chose to use Ubuntu with the new setup rather than Slackware -- for most of what I'm doing it's very slick and easy to use, and apt-get sure beats installpkg.

What I need at this point is a reasonably secure system that allows what I had previously with NFS/NIS. I have a ubuntu box with a big hard drive in my office which can physically hold the home directories and shared volumes, and I have 10-15 lab machines on which students will need to log in. 

I am told I need LDAP, but I'm having a rough time getting it going. I've found some howto's with Google, but I can't seem to get them translated to my particular setup. Anyone here willing/able to help? Is LDAP actually what I need, or is there a better option for this?

Thanks in advance,
Eric

---

### Post by Glut on 2006-08-03
IT very much depends on how many students that you need to deal with. If you have a large student body then ldap can help. NIS+ isn't all that bad though NFS is certainly insecure. If NIS is working for you and you're happy with your security I'd stick with that. NFS is a different kettle of fish. You will want an authenticated protocol, so your choices are limited:
SMB - fairly fast, authenticated - but not encrypted, easy to setup, tainted by microsoft.
SSHFS - Slow as a wet week (I'm getting a steady 10MB/s with some fairly speedy machines), encrypted and authenticated, Ubuntu's FUSE doesn't play well with mount (only an issue in very limited circumstances). The simplest to get going under most circumstances.
NFS4 - Linux implementation leaves a lot to be desired. Like stability.
AFS - A complete bastard to setup, Encrypted and authenticated, relatively fast

This may be incomplete, others may be able to add. Given the above, we've chosen SMB and run our lab machines with pam_mount mounting SMB home directories. Having windows compatibilty was a deciding factor in our case. Someone with a network sniffer could have fun, but our labs are physically separated by switches from our real network.

---

### Post by fnjordy on 2006-08-03
> **Glut said:**
> 
NFS4 - Linux implementation leaves a lot to be desired. Like stability.

Any NFS with Kerberos will be secure, its possible to setup NFS v3, but this nice warning message:

> 
Because of bugs and missing features, for now support for Linux NFS with Kerberos is appropriate only for early adopters, and not for production use.

---

### Post by Vincosmo on 2006-08-03
Quite fun, I also use NIS for my physics research unit. I'd like to jump to LDAP (it seems easier to interface it with a lots of applications (eg with php to list members of the lab with their name, phone, webpage, email... )).

Is it easy to insert a "ypcat passwd" in a new LDAP directory?

Vincent

---

### Post by garba on 2006-08-29
i went the "NIS way" a while back when setting up a few linux clients for a school lab and boy, that thing is the worst pile of crap i've ever come across: terrible packaging, configuration files spread all over the place, you name it... hence i decided to take out some extra time to learn my way around LDAP, and I love it, and thanks to PAM, you won't even notice auth data is being fetched from a remote server. And if you need security, it comes with SSL/SASL support. Do yourself a favor and ditch that pile of crap that NIS is.

---

