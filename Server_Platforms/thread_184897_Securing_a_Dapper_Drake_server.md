---
title: "Securing a Dapper Drake server"
date: 2006-05-30
forum: Server Platforms
---

### Post by Randomskk on 2006-05-30
Well, I'm taking the plunge and upgrading my server from EnGarde SELinux to Dapper Drake.
However, I want the server to be secure - as much as possible.
In EnGarde, there were a few nice things to facilitate this:

1. hosts.allow, hosts.deny
These two files are easily editable to give an ACL for accessing services. For instance, I only want two IPs to be able to access SSH.

2. Chroot for bind
Bind ran in a chroot, and I assume this is to stop people gaining access through a bind exploit.

3. SELinux
I never really used this, as there usually wasn't policy for programs I wanted to run.

4. chrooting FTP users
I could choose what users could get un-chrooted access to the system, and which users could only see their home folders. This is great if I'm giving FTP access to a friend.

Other things I've been considering:
1) Bastille Linux. Is this worth running on Dapper?
2) PHP's safe mode / chrooting Apache. I host a few different domains for people, and I've realised (although they haven't yet!) that PHP could erase other people's sites easily enough. I certainly don't want this, so in Dapper I'll make sure that's fixed. Does PHP's safe mode pull this off nicely, or is it possible to chroot a domain so that PHP will only access that domain's files?
3) Sudo. I'm not going to whine about not having root, but is it advisable to only give sudo access to a different user from my normal usage? I plan on doing this unless told otherwise.

I plan on using the server for web with PHP and MySQL, email, ftp, jabber, SSH, DNS, and potentially a Steam server.
Are there any security issues I should consider for my server?
I'd rather have something as secure as possible on this, as I host content for other people who therefore have FTP and PHP access.


Thanks a lot for any help!

PS: I originally posted this in the security thread, but it got no response after 53 views and so I figured this section is probably more suited.

---

### Post by Randomskk on 2006-05-31
..bump.. :(

I've looked into using PHP's OpenDir directive, and Safe Mode, which may work out for the PHP thing.

---

### Post by VDM on 2006-06-01
You might want to checkout AppArmor made by Novell.
I'm not sure how easly it would be to integrate or add it into ubuntu (if there isn't already ap ackage / kernel for it). However, it provides very good security so services cannot access files they are not supposed to.  
The big advantage is that it is a _LOT_ more easy to setup then SELinux.

[http://www.novell.com/products/apparmor/](http://www.novell.com/products/apparmor/)

---

### Post by hagen00 on 2006-06-02
[QUOTE=Randomskk]Well, I'm taking the plunge and upgrading my server from EnGarde SELinux to Dapper Drake.
However, I want the server to be secure - as much as possible.
In EnGarde, there were a few nice things to facilitate this:

1. hosts.allow, hosts.deny
These two files are easily editable to give an ACL for accessing services. For instance, I only want two IPs to be able to access SSH.

2. Chroot for bind
Bind ran in a chroot, and I assume this is to stop people gaining access through a bind exploit.

3. SELinux
I never really used this, as there usually wasn't policy for programs I wanted to run.

4. chrooting FTP users
I could choose what users could get un-chrooted access to the system, and which users could only see their home folders. This is great if I'm giving FTP access to a friend.

Other things I've been considering:
1) Bastille Linux. Is this worth running on Dapper?
2) PHP's safe mode / chrooting Apache. I host a few different domains for people, and I've realised (although they haven't yet!) that PHP could erase other people's sites easily enough. I certainly don't want this, so in Dapper I'll make sure that's fixed. Does PHP's safe mode pull this off nicely, or is it possible to chroot a domain so that PHP will only access that domain's files?
3) Sudo. I'm not going to whine about not having root, but is it advisable to only give sudo access to a different user from my normal usage? I plan on doing this unless told otherwise.

I plan on using the server for web with PHP and MySQL, email, ftp, jabber, SSH, DNS, and potentially a Steam server.
Are there any security issues I should consider for my server?
I'd rather have something as secure as possible on this, as I host content for other people who therefore have FTP and PHP access.


Thanks a lot for any help!

PS: I originally posted this in the security thread, but it got no response after 53 views and so I figured this section is probably more suited.[/QUOTE]
Honestly, I think the reason you're not getting many replies is that many of these things aren't really issues. Ubuntu is pretty secure out the box and while paranoia is good (I"m also on the paranoid side) it's sometimes not necessary. To answer the questions i'm able to answer...

1. Definitely possible. SSH is SSH is SSH, not matter what OS you use. 
4. I currently do that using vsftpd.

---

### Post by Randomskk on 2006-06-03
[QUOTE=hagen00]Honestly, I think the reason you're not getting many replies is that many of these things aren't really issues. Ubuntu is pretty secure out the box and while paranoia is good (I"m also on the paranoid side) it's sometimes not necessary. To answer the questions i'm able to answer...

1. Definitely possible. SSH is SSH is SSH, not matter what OS you use. 
4. I currently do that using vsftpd.[/QUOTE]
Yea, I guess, but as you say.. paranoia.. :P

I'll look into vsftpd, then - chrooting FTP users is certainly a big issue.
I've read a little more with the PHP stuff, and as far as I can see using the opendir directive should suffice, although I'll have to test it first.

Besides bind, what else could be chrooted? If I'm running one I may as well run some more, and I guess it can't hurt.

Thanks for the reply, anyway - I imagine I'll probably use vsftpd now :D

---

### Post by sclough on 2006-08-21
If you haven't already, you may want to look at suexec in apache.  If you have several people running php based sights, suexec runs sites with specific users.  The thing here is that a php script in one site will not have access to files owned by another user in another site if that makes sense.

---

