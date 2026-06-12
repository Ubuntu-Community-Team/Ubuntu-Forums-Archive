---
title: "Confused about Samba member server"
date: 2013-01-13
forum: Server Platforms
---

### Post by MezzFA0 on 2013-01-13
Hi all,

I'm working in a mixed Windows/Linux environment with about 50machines.  

I successfully set up a Samba PDC backed by Open LDAP, hooked postfix, dovecot etc into it and all is gravy.  Machines join the Samba domain, people log in, all is well.

So now all that was left to do was the "simple" share some directories on the server and lock them down to certain user groups.

To complicate things a little, I didn't want to handle the shares on the PDC, instead I have another server that has the shares on them.

So after reading lots of info on samba.org and other places I set samba to security = domain on the fileserver, joined the domain and all seemed ok until I tried to access the shares.

I can see the shares themselves but I get prompted for passwords and then access denied.

Testing with smbclient I get the same denied errors.  

Finally (not sure if this is related) running getent on the file server returns none of my LDAP users but on the PDC it returns them as expected.

If I set the shares to guest ok = yes.  I can do what I need to do but its not secure in any sense.

What am I missing?
Is security = domain correct for a pure Samba domain or does it only work with Windows domains? 
Should I just give up and mount the shares via NFS on the PDC? I'm not sure what impact this has network traffic wise.
I've read a bit about using nss to authenticate directly with Open LDAP but can't find a decent starting point, does anyone know of a good tutorial?

Heres my samba config:

[global]
        workgroup = MYDOMAIN
        server string = %h server (Samba, Ubuntu)
        security = DOMAIN
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        logon script = logon.bat
        logon drive = Z:
        logon home = \\FILESERVER\user$\%U
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Technical]
        comment = Technical Users
        path = /data/Technical
        read list = @uk-technical
        write list = @uk-technical
	read only = No
        directory mask = 0775

Any hints would be appreciated.

---

### Post by volkswagner on 2013-01-14
You mention LDAP backend, yet you have pointed the password program to the local linux machine.  I have not done this, but from what I can see, it seems you need to point the fileserver at the LDAP backend for authentication.

This [link]("http://serverfault.com/questions/440177/samba-with-remote-ldap-authentication-doesnt-see-users-properly") may help get you started.

---

### Post by MezzFA0 on 2013-01-14
Hi,

I was under the impression that security = domain passes the authentication off to the PDC but either way I couldn't get it to work.

The NFS Share route is working which is a good work around and buys me some time to figure out the real issue.

I did try configuring the file server as a standalone as per the link given but that didn't work either.

Thanks for the info either way volkswagner

---

### Post by MezzFA0 on 2013-02-13
Hi again all,

After dealing with the hassles of NFS shares over Samba I decided to give this another go and hit similar walls.

Heres my current method for trying to get things to play nice:

SAMBA PDC authenticating via LDAP running locally
SAMBA BDC authenticating via LDAP on the PDC

I have shares mainly on the BDC as this is the machine with all the storage, my problem is that that the BDC doesn't seem to be trying to authenticate via LDAP at all.

If I run getent passwd on the PDC I get a nice list of all my LDAP users, if I run the same on the BDC I just get local linux accounts.

Heres the highlights of the BDC smb.conf which hopefully will give someone some hints:

passdb backend = ldapsam:ldap://ip_address_of_PDC
ldap admin dn = cn=admin,dc=madeup,dc=domain
ldap group suffix = ou=Groups
ldap idmap suffix = ou=Idmap
ldap machine suffix = ou=Computers
ldap passwd sync = yes
ldap suffix = dc=madeup,dc=domain
ldap ssl = no
ldap user suffix = ou=People

I've added the ldap admin password to the secrets file with:

smbpasswd -W

I've also added ldap to the nsswitch.conf file.

Apologies for what must be the stupid questions but I'm going around in circles at the moment a cursory look through /var/log/ doesn't even seem to be registering any failed attempts, although I Feel like I'm missing a log file somewhere.

Once again any help is appreciated, its obviously something silly that I've over looked but google is refusing to co-operate for a change.

---

