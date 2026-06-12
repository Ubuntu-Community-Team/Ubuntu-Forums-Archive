---
title: "Webmin updating packages changes permissions!"
date: 2012-02-01
forum: Server Platforms
---

### Post by Loggy on 2012-02-01
I have a curious problem that occurs from time to time.  I am running 10.04 LTS on a virtual server and to administer it, I am using Webmin which I find very useful.   I have the umask set to default in the advanced options but it appears that when Webmin updates a system package that is in /sbin (it may happen for other directories as well but I can't recall any), the updated program will end up with permissions 0000 ie no access at all.

This can be very embarrassing.  For example last night sysvinit-utils was updated and /sbin/killall5 ended up having its permissions reset.  So when my automatic script restarted apache at 3.30 - because I don't like the continued bloating that apache has - it didn't restart as the first thing it does is to use pidof which is symlinked to /sbin/killall5.  So all my websites fell over!

Does anyone know why Webmin update, which is running as root, does this?  If I do an apt-get update in a shell, it doesn't do this at all... :-[

[BTW I am running apache rather than nginx or lighttpd because most of the sites are Wordpress which requires .htaccess.  I realise litespeed would do as a dropin but all the same...  Webmin of course uses its own dedicated miniserv.pl on its dedicated port.]

---

