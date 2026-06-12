---
title: "Samba &quot;User&quot; Authentication"
date: 2007-10-18
forum: Server Platforms
---

### Post by SCSIMouse on 2007-10-18
I have a Ubuntu server running 7.04 with Samba 3.0.24.

It's serving a bunch of different Windows machines on a personal LAN.  Currently I have the file server setup with User authentication.  I created my user name on the server (as I'm the admin) and a user named "network".  Network has a home dir of /bin/true so it can't be used to login and it also has no password.  Using the username map command I have it setup so that if I browse to the server with my admin username from Windows I have full read/write access to all the shares on the server.  Anyone else is remapped to the "network" user which has read only access.  However, when browsing with a windows machine that isn't using the admin user name a login window pops up asking for a user/pass.  Entering the user name "network" with no password allows access.

My question is, without changing from User to Share, is there some option/config that would allow the non admin users to bypass the user/pass screen and be let right in?  Is there a way to have Samba map all unknown users to "network"?

----------------------------
Partial SMB.conf
-------------------------------------------------------------------------------
; [ User Configuration ]
                hide unreadable = no
                guest account = network
                map to guest = bad user
                invalid users = root
                username map = /home/(admin username)/SYSTEM/smbmap.txt

[Programs]
        locking = no
        valid users = (my admin username),network
        browseable = yes
        writeable = yes
        force create mode = 0755
        force directory mode = 0755
        path = /STORAGE/320WDP/SHARES/Programs
        Comment = Programs and Utilities

-------------------------------
Partial SMBMAP.txt (no, those aren't real usernames)
------------------------------------------------------------------------
!network = dummy1 dummy2 dummy3

---

### Post by vmikalinis on 2007-10-18
I believe you can map an outiside username to a local username using the /etc/smbusers file.  I just checked on my 7.04 system and it does not exist, but I know back when I used redhat it was there.  It may have been replaced by options in smb.conf but again, I'm not sure.  I think all users from the outside that don't exist are nobody by default.  I know you didn't want to change the share, but something like "guest account = nobody" would be general.

Syntax for smbsusers file

# Unix_name = SMB_name1 SMB_name2 ...
root = windoze1 windoze2
nobody = guest pcguest smbguest
mark = windoze3

---

### Post by SCSIMouse on 2007-10-18
Yea, I created that file (smbusers), and put that sort of information in it.  I figured that "guest account = network" would change all unknown users to be mapped to "network".  By default I believe that it's "guest account = nobody".  I never tried to put "nobody" or "guest" in the smbusers file...I thought that changing in smb.conf to "network" would take care of that for me.

I'm willing to change others things in my configuration as long as "security = users" doesn't change.

---

