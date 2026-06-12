---
title: "Changed access to /home/me-can't login anymore."
date: 2006-04-16
forum: Server Platforms
---

### Post by peetsa on 2006-04-16
Hi All
In a moment of absent mindedness I have changed my permission on /home to I don't know what, and obviously can't login. I've booted in recovery mode and did:

root@bok:~#**chmod  644  /home/me **    and     
**chmod +r+w+x /home/me**     and
**chown me /home/me**      and    
**chgrp me /home/me**
It didn't return any error messages but when I tried to login as _me _it still says:
Unable to cd to "/home/me"
Also, when I boot normally I am presented with the command line login instead of the usual GNOME login screen. I've tried :
**sudo /etc/init.d/gdm star**t   but it just says "failed".

1) What can I do ???  ( I'm rather new to Linux )
2) Will re-installing Ubuntu wipe out my data and my Evolution inbox  ??
3) If there is no easy answer to (1), can I mount a Win partition from the command line and then copy /home/* to the Win partition and then re-install, and copy my data back ??

You advice is appreciated.
peetsa

---

### Post by RavenOfOdin on 2006-04-16
If you did:

> 
chown me /home/me


wouldn't it still be owned by the root group?

Try "chown me:me /home/me"

Also you might want to:

1) Boot normally to a console. 
2) Take pico (or whatever text editor happens to be on hand)
3) Look in your /etc/group file and check if you are present in it under the lines:

adm:x:4:me

or

admin:x:106:me

You should also have a group named after your account with a GID of 1000 or higher.
See if any of these apply and then get back to us.

---

### Post by peetsa on 2006-04-17
Hi

Both   _adm:x:4:me_   and   _admin:x:106:me_  are present in /etc/groups

In recovery mode I did:
chown -v me:me /home
chown -v me:me /home/me
and ls -l
shows that _me _is the owner and that /home and /home/me both has mode rwxr-xr-x
When I rebooted and tried login it still said Unable to cd to '/home/me'
As a test I tried
sudo -u me cd /home and the error was 
can't open /etc/sudoers : Permission denied

ls -l /etc/sudoers showed
    -r--r----- root root .......

nano /etc/sudoers showed
    Defaults    !lecture,tty_tickets,!fqdn
    root ALL=(ALL) ALL
    %admin ALL=(ALL) ALL

ls -l shows that Desktop is root root ( I suppose thats the owner and group)

Thanks for your effort.
Awaiting your reply.
---------------------

---

### Post by RavenOfOdin on 2006-04-17
First off, you want to use visudo for your sudoers file.

The main /home directory should be owned by and in the root group. Its only your subdirectory that you want.  This would go for whether multiple users are present on your computer or no.

Go back in and do:

> 
chown root:root /home
chmod 755 /home/me/Desktop
chmod 755 /home/me/Desktop/*


See what happens then.

---

### Post by peetsa on 2006-04-17
Hi RavenOfOdin
I did that
chown root:root /home
chmod 755 /home/me/Desktop
chmod 755 /home/me/Desktop/*     <--- Didn;t work
but 
chmod 755 /home/me/*   worked.

but when I login I still get "Unable to cd to /home/me"
I have at least managed to mount a Win drive and copy all my data to it and I'm
prepared to re-install Ubuntu as a last resort. Copying my Evolution mail-box to the Win drive would be a plus, if I knew how.
Alternatively, if you can figure a way out of this, it will be first prize.
Thanks,
peetsa

---

