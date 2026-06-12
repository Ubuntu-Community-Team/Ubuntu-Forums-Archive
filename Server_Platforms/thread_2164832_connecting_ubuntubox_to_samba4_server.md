---
title: "connecting ubuntubox to samba4 server"
date: 2013-08-02
forum: Server Platforms
---

### Post by antonello2 on 2013-08-02
I'm setting up a mixed lab with linux and windows clients.
For the purpose I chose an Ubuntu server with zentyal.
It uses the new samba4 as a substitutes of Acive  Directory.
It works fine with windows clients. It deploys centralized authentication with oaming profiles.
The problem is how should I connect the linux clients.
Likewise-open package let me join the domain I created, and my ubuntu boxes correctly authenticate.
But the question is: how do I deal with the users' homes?
Should I use samba shares for linux homes? How?
I used to use nfs in earlier times in only-linux systems, but it looks like it doesn't work in this situation.

TIA
Antonello

---

### Post by SeijiSensei on 2013-08-02
I don't think you can use CIFS to distribute the home directories because CIFS doesn't support Unix filesystem primitives like user/group IDs and permission masks.

I would run NFS alongside Samba to mount the homes if you can.  I run both Samba and NFS together on servers, but I use simple authentication mechanisms like /etc/passwd and a corresponding smbpasswd file.  There might be a PAM module that lets you have the server itself authenticate users against Samba.  I once used the hoary [pam_smb]("http://www.csn.ul.ie/~airlied/pam_smb/") module to authenticate users on a Linux box against an Active Directory server.

---

### Post by redmk2 on 2013-08-02
> **antonello2 said:**
> ....the question is: how do I deal with the users' homes?
Should I use samba shares for linux homes? How?


The [homes] share is just for this purpose.  You set up one [homes] share and it expands for all users.  You can make it browsable or not.  You can define where the home directories reside on the server (i.e. /home or /srv or even /smb).  On my Samba3 servers I use /smb/homes.  The /home directory is only for the local users on that server.

My experience is with Samba3 and this works perfectly for both Windows and Linux users.  Samba4 is pretty new so there is not much to Google at this point.  As is typical with Windows the SMB protocol has morphed into CIFS and then into SMB2.  All these changes are incorporated in Samba4 and the latest Samba3 code.

@ SeijiSensei -- " CIFS doesn't support Unix filesystem primitives like user/group IDs and permission masks."  The SMB/CIFS/SMB2 protocol deals only with the userland remote mounting of file systems.  The underlaying file systems (NTFS and EXT) are accounted for.  Specifically, NTFS file permissions are set at mount time.  Conversely EXT4 user permissions are set on a Windows machine at mount time when the shares are mounted into a NTFS configured host.

---

### Post by antonello-facchetti on 2013-08-03
> **redmk2 said:**
> The [homes] share is just for this purpose.  You set up one [homes] share and it expands for all users.  You can make it browsable or not.  You can define where the home directories reside on the server (i.e. /home or /srv or even /smb).  On my Samba3 servers I use /smb/homes.  The /home directory is only for the local users on that server.

My experience is with Samba3 and this works perfectly for both Windows and Linux users.  Samba4 is pretty new so there is not much to Google at this point.  As is typical with Windows the SMB protocol has morphed into CIFS and then into SMB2.  All these changes are incorporated in Samba4 and the latest Samba3 code.

@ SeijiSensei -- " CIFS doesn't support Unix filesystem primitives like user/group IDs and permission masks."  The SMB/CIFS/SMB2 protocol deals only with the userland remote mounting of file systems.  The underlaying file systems (NTFS and EXT) are accounted for.  Specifically, NTFS file permissions are set at mount time.  Conversely EXT4 user permissions are set on a Windows machine at mount time when the shares are mounted into a NTFS configured host.

I am actually experimenting samba4 and there's not much on the net. It seems that samba4 incorporates his hown ldap system. I got it work and I can authenticate in the client using "likewise-open" paskage. On a windows client it works fine and it serves a roaming-profile-system. I must find out how it works with linux clients: shall I use a similar roaming-profile sistem (btw it creates a directory called /home/likewise-open/domainname/... in the client) or can I point directly to the server (that's the sense of NFS).
I tried to mount via NFS in the directory above and it  mounted correctly the users' dirs fron the server, but the problem is that uid and gid are nowhere to be found: they are not in the server's password/groups file, thus the user can't access his home.

---

### Post by redmk2 on 2013-08-03
> **antonello-facchetti said:**
> I am actually experimenting samba4 and there's not much on the net.

It's all too new for there to be much out there.
> 
 It seems that samba4 incorporates his hown ldap system. I got it work and I can authenticate in the client using "likewise-open" paskage. 

You shouldn't need tho use Likewise-Open with Samba4.
> 
On a windows client it works fine and it serves a roaming-profile-system. I must find out how it works with linux clients: shall I use a similar roaming-profile sistem (btw it creates a directory called /home/likewise-open/domainname/... in the client) or can I point directly to the server (that's the sense of NFS).
I tried to mount via NFS in the directory above and it  mounted correctly the users' dirs fron the server, but the problem is that uid and gid are nowhere to be found: they are not in the server's password/groups file, thus the user can't access his home.
The password/groups files are used for the local host users, not the network users.  The network users information is in the LDAP.  The CLI tool getent should be able to query both the LDAP and the password/group files.

---

### Post by antonello-facchetti on 2013-08-04
> **redmk2 said:**
> It's all too new for there to be much out there.

You shouldn't need tho use Likewise-Open with Samba4.



That's what zentyal (with samba4) tells me to do.

---

