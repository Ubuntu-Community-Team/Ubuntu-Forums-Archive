---
title: "Slow SSH Login - 60 seconds"
date: 2012-11-13
forum: Server Platforms
---

### Post by buecker on 2012-11-13
SSH login hangs for 60 seconds after I enter in my password.

Running 12.04.1
Just installed samba and ldap
I think the issue started when I used a smbldap-groupmod command to change user 'buecker'.

However i ran the command again to add 'buecker' to the group 'administrators' and rebooted.

Can someone help me decipher this?(I edited out the FQDN)  This is from running SSH -vvv on

debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /.ssh/id_rsa ((nil))
debug2: key: /.ssh/id_dsa ((nil))
debug2: key: /.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /.ssh/id_rsa
debug1: could not open key file '/.ssh/id_rsa': Permission denied
debug1: Trying private key: /.ssh/id_dsa
debug1: could not open key file '/.ssh/id_dsa': Permission denied
debug1: Trying private key: /.ssh/id_ecdsa
debug1: could not open key file '/.ssh/id_ecdsa': Permission denied
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
[email]buecker@myvnc.com[/email]'s password: 
debug3: packet_send2: adding 48 (len 61 padlen 19 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Enabling compression at level 6.
debug1: Authentication succeeded (password).
debug1: getpeername failed: Permission denied
Authenticated to myvnc.com ([UNKNOWN]:-1).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug2: client_check_window_change: changed
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 100 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Failed to add entry for user buecker.

I should also note that when I sudo and enter in the password this happens:
[sudo] password for buecker: debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE
debug3: Received SSH2_MSG_IGNORE

---

### Post by CrucifiedEgo on 2012-11-13
```
 debug1: getpeername failed: Permission denied 
```

This seems to be the culprit.  The only question is what is being denied permission?  The dns lookup on one or the other end?  Try running it under strace and see if you can gather more information that way.

---

### Post by cjhabs on 2012-11-13
I had slow ssh logins to some hosts and the following fixed it for me:
On the Ubuntu client, edit * /etc/ssh/ssh_config * and add - **before the generic section**:
Host ip_address_of_server
GSSAPIAuthentication no

Maybe that will help you

---

### Post by buecker on 2012-11-13
I think I saw that fix in another thread.

Tomorrow I will get back to looking at this issue.


Thanks so far for everyone's responses.  I really appreciate it.

---

### Post by SeijiSensei on 2012-11-14
SSH uses DNS to resolve hostnames in both the forward and reverse directions.  One simple solution is to put the name and IP address of both the client and server in both machines /etc/hosts file.  You can also disable DNS lookups by adding the directive "UseDNS no" to /etc/ssh/sshd_config on the server.

---

### Post by buecker on 2012-11-14
My IP address will change constantly as I am logging in from multiple locations each day.

I'm running this as a VM so I rolled back to a previous snapshot where SSH was working fine.  Here is the tutorial I am following on Ryaz Khan's site.

[http://www.ryazkhan.net/?show=smb12]("http://www.ryazkhan.net/?show=smb12")

Whatever I am messing up is happening before I edit the example smb.conf file.


I did try the "useDNS no" option.  saved and rebooted and still have the issue.

I think the best thing for me to do is to rollback one more time and go step by step testing SSH along the way.  Looking through the guide I can only assume that there is an issue with me editing the smbldap.conf file?  Would that affect SSH?

---

### Post by buecker on 2012-11-14
I've narrowed the issue down to my smb.conf file.

Without changing the smb.conf.example file I get my SSH password delay issues.  It is suppose to look like this per the tutiorial:

[global]
        workgroup = TESTLAB
        netbios name = %h server (Samba, Ubuntu)

        deadtime = 10

        log level = 1
        log file = /var/log/samba/log.%m
        max log size = 5000
        debug pid = yes
        debug uid = yes
        syslog = 0
        utmp = yes

        security = user
        domain logons = yes
        os level = 64
        logon path =
        logon home =
        logon drive =
        logon script =

        passdb backend = ldapsam:"ldap://127.0.0.1/"
        ldap ssl = no
        ldap admin dn = cn=admin,dc=testlab,dc=dev
        ldap delete dn = no

        ## Sync UNIX password with Samba password
        ## Method 1:
        ldap password sync = yes
        ## Method 2:
        ;ldap password sync = no
        ;unix password sync = yes
        ;passwd program = /usr/sbin/smbldap-passwd -u '%u'
        ;passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"

        ldap suffix = dc=testlab,dc=dev
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap machine suffix = ou=Computers
        ldap idmap suffix = ou=Idmap

        add user script = /usr/sbin/smbldap-useradd -m '%u' -t 1
        rename user script = /usr/sbin/smbldap-usermod -r '%unew' '%uold'
        delete user script = /usr/sbin/smbldap-userdel '%u'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        add machine script = /usr/sbin/smbldap-useradd -w '%u' -t 1

[NETLOGON]
        path = /netlogon
        browseable = no
        share modes = no

[PROFILES]
        path = /profiles
        browseable = no
        writeable = yes
        create mask = 0611
        directory mask = 0700
        profile acls = yes
        csc policy = disable
        map system = yes
        map hidden = yes


The only changes I make are to the workgroup name, netbios, ldap ssl, passdb backend, ldap admin and ldap suffix lines.

I can confirm that it has to be this file because when I swap this out for the original smb.conf then SSH works fine.

What am I missing?

---

### Post by buecker on 2012-11-14
ugh.

Now I can't replicate and it works.  I set the smbpasswd and logged out and logged back in via ssh.

Thanks for helping with this.  I am going to go and close this thread.

---

