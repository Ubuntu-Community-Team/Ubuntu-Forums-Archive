---
title: "problem with samba - cannot access Via hostname"
date: 2006-08-11
forum: Server Platforms
---

### Post by psylvester on 2006-08-11
Hi,
Im using ubuntu server edition on my server. I have Installed samba on it, so that windows users can access it. Its working fine, the only problem I have is,

When ever some users try to access the machine via hostname (e.g. \\hostname\<share-folder>\ they get error. (the account is not authorise to login from this station), however if the same user tries with IP, it works fine. (e.g. \\ip-address\shared-drive)

Can some one tell me what could be wrong?

---

### Post by psylvester on 2006-08-11
Im sure it has something to do with permission, since some users can login. I really dont know how those users are loggin in. I havnt done anything which allows some users in & some not.

this is my smb.conf

[global]
workgroup = abc
;server string = %h
;guest only = no
security = share
guest account = nobody

[support]
                path = /disk2/support
                guest ok = true
                read only = yes
[home]
                path = /disk2/home
                guest ok = true
                read only = no

---

### Post by bbfuller on 2006-08-11
I don't have a server situation here, I just use SAMBA peer to peer between windows and linux, and linux to linux.

I can list for you what I needed to do to get mine working including being able to use name resolution as well as ip addresses.

In the file '/etc/nsswitch.conf' add 'wins' and 'bcast' to the hosts line

Uncomment the line 'name resolve order' in 'smb.conf' make sure 'bcast' is in the line.

I installed the package 'winbind' on the Linux machines.

Added all the necessary users to the Linux machines with 'smbpasswd -a bbfuller' That is just my specific name, obviously do this for each of your users.

With the firewall running, apart from allowing SAMBA through it, you will also need to add the line 'ip_conntrack_netbios_ns' to the file '/etc/modules' otherwise name lookups fail.

Also, if using Firestarter as the firewall manager I needed to remove the ticks from both the 'Broadcast Traffic' boxes on 'Edit - Preferences - Advanced Options'.

All the inverted commas in this message are for clarity and don't need to be typed if you are adding these commands.

Some of this may be unnecessary, I was so relieved to get it going I haven't yet had the heart to go back and undo things to see when it stops working. If you see any unnecessary steps please let me know.

Hope this helps.

---

### Post by bbfuller on 2006-08-11
Actually, I also previously found the access by hostname intermittent.

If I had accessed a machine by ip address, then I would be able to access it by hostname until the machines were restarted.

---

### Post by dgray_from_dc on 2007-01-11
Does your Ubuntu server act as a WINS server?  WINS provides name resolution for samba/Windows networking.

Add the following line to smb.conf.
```
wins support = yes
```

---

