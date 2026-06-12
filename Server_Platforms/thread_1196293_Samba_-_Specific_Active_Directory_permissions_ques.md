---
title: "Samba - Specific Active Directory permissions question"
date: 2009-06-24
forum: Server Platforms
---

### Post by dave562 on 2009-06-24
I originally posted this in the "Networking" section, but that seems to be a forum dedicated to basic networking questions.  Sorry for the cross-post.  Here is the link to my original question.

[http://ubuntuforums.org/showthread.php?p=7512031#post7512031](http://ubuntuforums.org/showthread.php?p=7512031#post7512031)

Thanks to a lot of great documentation provided by the community I have been able to get my Ubuntu box (8.04 LTS) joined to my Active Directory domain. With a combination of Kerberos, PAM and WinBind I can log onto the Ubuntu box with accounts from the domain. I'm having a problem configuring the Samba share though.

I specifically want to control access to the Samba share, and limit access to a particular Active Directory account. I have seen a lot of different smb.conf examples regarding this issue, but I haven't been able to get any of them to work.

Can someone share an example that shows how to limit read/write access to a share based on Active Directory user accounts?

So far I have tried the following

read list = <account name>
read list = @<domain>+<account name>
Valid Users = <account name>
Valid Users = @<domain>+<account name>

With "Valid Users", when I attempt to connect to the share I am prompted for a user name and password. I've tried every possible permutation of valid combinations and I can't access the share. With "read list", I just get the standard Windows error message about not having permission to access the share.

Thanks in advance for any help.

----

smb.conf file contents


[global]
security = ads
realm = (domain name in caps)
password server = (FQDN of domain controller)
workgroup = 2CP
winbind refresh tickets = yes
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
winbind use default domain = yes
restrict anonymous = 2

[test]
path = /home/2CP/darmstrong
valid users = test, itadmin
write list = test, itadmin
read list =

---

### Post by wolfteeth on 2009-06-25
you didn't indicate the winbind separator 

for me, I am using winbind separator = /

then my sharing folder permission set to:

[sharing]
comment = sharing folder
path = /usr/sharing
public = no
valid users = domain/userA, domain/userB
write list = domain/userA

---

### Post by dave562 on 2009-06-25
Thanks for the reply.  The winbind separator did the trick for connecting to the share.  I got confused when reading the documentation and made the assumption that when it talked about the default value, it just used that value even if it wasn't specified.  That was my mistake.  It actually has to be explicitly declared.

Now I can connect to the share, but I can't copy data to or from it.  Any suggestions?

---

### Post by dave562 on 2009-06-25
I answered my own question, sort of.  I couldn't read from or write to the share from within a virtual PC instance of WinXP.  On a regular workstation it worked just fine.

---

### Post by wolfteeth on 2009-06-25
> **dave562 said:**
> I answered my own question, sort of.  I couldn't read from or write to the share from within a virtual PC instance of WinXP.  On a regular workstation it worked just fine.

it would be a same and should be no problem to access it as well, only thing need to check is the network mode, if you are using NAT should be no problem at all.

---

### Post by dave562 on 2009-07-08
*Bump*

Rather than start a new topic, I'm replying to this one.  I'm just about ready to pull my hair out.  I got everything setup on a test box.  On the test box, I can connect to the server share using the UNC path \\<server name>\<share name> just fine.

I copied the configuration over to my production server and although I can connect to the server \\<server name>, I can't connect to the share \\<server name>\<share name>.  When I try to connect, I am prompted for a user name and password.

I recreated the following files as identical copies from the test box onto the production box

/etc/samba/smb.conf
/etc/nsswitch.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-session
/etc/pam.d/sudo
/etc/ntp.conf
/etc/krb5.conf

Here are the contents of my smb.conf file.

[global]
        security = ads
        realm = <censored, ALL CAPS>
        password server = <censored, FQDN to domain controller>
        workgroup = 2CP
        winbind separator = '\'
        winbind refresh tickets = yes
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2

[test]
        path = /home/2CP/darmstrong
        valid users = 2CP\darmstrong,2CP\buexec,2CP\test,itadmin
        write list = 2CP\darmstrong,2CP\buexec,2CP\test,itadmin
        read list =


The /home/2CP/darmstrong directory is set 777.

Any insights as to why Samba is asking for credentials when connecting to the share?

---

