---
title: "Securing a Dapper Drake server"
date: 2006-05-28
forum: Server Platforms
---

### Post by Randomskk on 2006-05-28
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



EDIT: 53 views and no reply, I'm going to repost this in the "server" area as it's probably better suited there.
Sorry for any confusion or anything.

---

