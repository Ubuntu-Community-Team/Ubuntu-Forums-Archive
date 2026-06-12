---
title: "Home Network - Samba Guest"
date: 2008-08-24
forum: Server Platforms
---

### Post by Just4Fun20 on 2008-08-24
Everything was working fine until I upgraded to Hardy Heron.  I'm still fighting a Samba problem.  

This is a home network.  I don't want passwords or userids for network shares.  The Ubuntu machine runs Samba and shares a "common" and "netbkup" directory just for storing files in a central spot.  Again it was working fine.  

Soon after the upgrade I tried to access the shares (from several Windows XP machines) and got an error saying I couldn't access the shares maybe it was an access problem.  I assumed this was just because I'd just changed everything.  

I went to the Ubuntu server and instead of using the /etc/samba/smb.conf file I used the file browser Nautilus and set up a share.  I did tell it to "Allow other people to write in this folder".  "Guest access (for people without a user account)" is greyed out and can't be selected.  

In my smb.conf file I have "restrict anonymous = no" and "security = share".  Under the share I have "guest ok = yes".  

I don't think the smb.conf file is being used anymore.  Is it?  Where is the samba share information for Nautilus stored?  I created a "new" folder and shared it and nothing shows up in the smb.conf file.  

Is it possible to have a share from a Ubuntu 8.04 Hardy Heron server that is wide open, with no userid's or passwords?  

I also tried adding the Samba configuration tool.  I read the known hardy bugs and installed the system-config-samba utility.  It said I'd need "sudo touch /etc/libuser.conf", which I did but the configuration utility won't open.  I start it and get two processes running.  One quits and then 30 seconds later the second quits.  

Any suggestions?

---

### Post by mbeach on 2008-08-25
don't have all your answers, but the usershares through Nautilus are probably located:
/var/lib/samba/usershares/
from:
[http://ubuntuforums.org/showthread.php?t=749765](http://ubuntuforums.org/showthread.php?t=749765)

I've found that using the 'old' way is easier for me to deal with (adding items to the smb.conf).  I've not setup a box for full wide open access - ie no passwords but this might help:
[http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/](http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/)

---

### Post by Just4Fun20 on 2008-08-27
Thank you mbeach.  That was perfect.  The shares, established through Nautilus, are kept where you said, so I've control of my shares again.  The do have a Guest=Y option listed as well although I'm not sure if it works.  

I messed around with the passwords for awhile.  I don't know if I've removed them or simply cached them but I'm now able to access this Samba server from all the machines that need access.  

Thanks again.

---

