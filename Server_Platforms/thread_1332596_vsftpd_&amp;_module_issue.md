---
title: "vsftpd &amp; module issue"
date: 2009-11-20
forum: Server Platforms
---

### Post by lafever on 2009-11-20
I was having a hell of a time with my vsftpd passive mode configuration. I figured out that I had to manually enter 


> 
modprobe ip_conntrack
modprobe ip_conntrack_ftp


That right there would get my ftp to work. Well a few days later, I noticed that the FTP was having the same problems again, so I went and tried debugging, and come to find out the modules weren't on. So I did some google searches and came across a way to show my mods by typing

> 
lsmod


In there I have nf_conntrack and nf_conntrack_ftp. It seems that I need to use ip_conntrack for my vsftpd to work. Is there anyway to add them to my modules in the kernel so that I won't have to re-enter modprobe ip_conntrack again?

Thanks for the help in advance.

---

### Post by dca on 2009-11-20
What version of Ubuntu are you running? In 8.04 I could've sworn it was just install FTP and use UFW to unlock firewall
 
sudo ufw allow ftp
 
..or something like that?

---

### Post by lafever on 2009-11-20
That command doesn't work but I'm running 8.04 and using iptables. Everything works fine with the iptables and passive ftp when I ran the modprobe manually [again]. 

I tried adding the modprobe to the top of my iptables and that doesn't work. I'm new to linux so I don't know if there's a file to add modules to load or what.

---

### Post by dca on 2009-11-20
Don't quote me, wait for someone to verify but I think you can add those statements to '/etc/sysctl.conf' file then reboot to test...

---

### Post by dca on 2009-11-20
It might be '/etc/modules'
 
...I gotta' look now...
 
See if this post is relative while I look...
 
[http://ubuntuforums.org/showthread.php?t=454177](http://ubuntuforums.org/showthread.php?t=454177)

---

### Post by lafever on 2009-11-20
Yes it was relevant. What I got out of that is that NF_* is the new framework and the rest is obsolete. So I don't know how I'm going to resolve this issue, it seems every time I need to reboot I need to run that module in order for me to not get a 425: Connection error and for passive mode to work. I appreciate all the help you've been thus far.

---

### Post by dca on 2009-11-20
No problem, I'm just hoping someone will chime in... I never had to do that on Server 8.04 but I know I did have to do something like this for a client who needed an FTP and ran CentOS 5.0 when it first came out.

---

