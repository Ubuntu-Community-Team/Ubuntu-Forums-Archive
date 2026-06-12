---
title: "multiple samba machines one ldap"
date: 2008-09-24
forum: Server Platforms
---

### Post by doug2168 on 2008-09-24
looking for a how-to on this. anyone have anything better than what's on the MAN pages over @ samba?

---

### Post by kamaji792 on 2008-09-25
> **doug2168 said:**
> looking for a how-to on this. anyone have anything better than what's on the MAN pages over @ samba?

I do know you can make one Samba install look like several samba server.  That might be a direction to look in.

---

### Post by doug2168 on 2008-09-25
ok, here's some details as to what i'm running and trying to do.

have a deall power edge 840 running ubuntu server 6.06 lts. it's setup as a LAMP server with samba and LDAP server. samba works well here as a PDC and with windows boxes joined to the domain.

i have another desktop that's running ubuntu 8.04 desktop that i've setup with samba and LDAP client. i can get as far as having a share show up from this machine on a windows box but i'm having problems with access due to permissions problems.

i had found something on the samba man pages that explains and gives vague examples of how to setup one samba server to act as many and toward the bottom it gives an example of multiple samba servers on same workgroup. i believe the problem to be what's going into the smb.conf files because when i set things up the way this doc shows me things show up but with shares all screwed up. i'll have my "my stuff" folder showing up as a share but can't access it. can't even read it. or the other box shows up in the right workgroup but with sahres listed from the PDC.

there's got to be someone out there that knows an easier way to do this or knows where i might find better, more thorough documentation on how to do this.

tia

doug

---

### Post by bab1 on 2008-09-25
Multiple hosts (boxes) with Samba servers are perfectly fine in either workgroups or domain situations.

The permissions should be edited in the smb.conf file and on the underlying FS on the 8.04 host.  The 6.06 Ubuntu host is different from the 8.04 in that the GUI interface (Gnome/Nautilus) works to setup "shares".  The 8.04 version of the GUI is broken and won't be fixed.

Did you setup the shares on the 8.04 via the GUI?

---

### Post by doug2168 on 2008-09-25
> **bab1 said:**
> Multiple hosts (boxes) with Samba servers are perfectly fine in either workgroups or domain situations.

The permissions should be edited in the smb.conf file and on the underlying FS on the 8.04 host.  The 6.06 Ubuntu host is different from the 8.04 in that the GUI interface (Gnome/Nautilus) works to setup "shares".  The 8.04 version of the GUI is broken and won't be fixed.

Did you setup the shares on the 8.04 via the GUI?

no i did not do anything on the 8.04 machine in a gui. do you know where there may be some documentation on how to do this?

the 6.06lts host is a server with the server edition of 6.06. it's a pdc named 'linuxlan' with host name linuxlan-pdc. the 8.04 host has the desktop version on it and has been joined to the linuxlan domain. it's host name is desktop.

when i go browsing in windows explorer, i expand network places, go to entire network/microsoft windows network and i see linuxlan. i expand the tree for linuxlan and under there is both linuxlan-pdc and desktop. desktop is either inaccessible, or shows the wrong shares. when it shows the wrong ones it is displaying shares from the pdc. if the shares from the desktop are shown under desktop, they are not readable. 

i use webmin and editing of the smb.conf file to set everything up. the smbldap-installer script was used to configure ldap and samba on the pdc. i've tried the same script with the ldapclient install and it doesn't seem to do the job. i'm now at a point where the desktop os needs to be re-installed again because samba is no longer showing a list of users in the webmin interface where as it was before. it would show all of the ldap users but no longer does because i've changed something to try and get this to work and it is now non-functional.

as i keep asking...is there a config script for both samba and ldap client to join the machine to the domain and have accessible shares?

---

