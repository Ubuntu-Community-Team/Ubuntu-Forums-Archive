---
title: "Samba as PDC"
date: 2005-10-27
forum: Server Platforms
---

### Post by billiejoex on 2005-10-27
Hi all. I have a samba server running as PDC that authenticates 15 windows clients in my network.
Now I plan to add some other client machines running Suse and I would like to authenticate on PDC them too.
How con I do it? Do I have to apply some changes on smb.conf file on the server?
What should I do on client machines? Does it is possible to have a "windows-like logon screen" on every boot (maybe do I have to modify pam?)?
This is my smb.conf:
[http://pastebin.com/407650](http://pastebin.com/407650)

Thanks in advance

---

### Post by billiejoex on 2005-10-29
up! :(

---

### Post by Glut on 2005-10-30
You can use pam, with the smb module. Your windows like login screen would be the normal gnome login screen, pam can handle this.

---

### Post by billiejoex on 2005-10-30
I imagined that. 
Do you know where I can find a tutorial about that?

---

### Post by billiejoex on 2005-10-31
If it can helps this is my smb.conf file:

```
#
[global]
    workgroup = intranet
    netbios name = server
    server string = SAMBA PDC
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 
    os level = 64
    preferred master = yes 
    local master = yes 
    domain master = yes 
    security = user 
    encrypt passwords = yes 
    domain logons = yes 
    hosts allow = 127.0.0.1 192.168.1.0/255.255.255.0
    bind interfaces only = yes  
    interfaces = eth1
# full priviledges group
    admin users = @samba_admin
#logs
    debug timestamp = no
    log file = /var/log/samba/log.%m 
    log level = 2
    max log size = 1000
#paths
    logon home = \\%L\%U\.profile 
    logon path = \\%L\profiles\%U 
# automatically mount shares on windows client
    logon script = mount.bat 
   logon script = %G.bat
#scripts
    add machine script = /usr/sbin/useradd -d /dev/null -g machines -s /bin/false -M %u

#
# Condivisioni risorse______________________________________________________
#

[Pubblic]

    path = /home/public_share
    comment = Risorsa pubblica full access

    writable = yes
    browsable = yes
    #ricordarsi del chmod 777 /path/directory

[profiles]
    path = /home/profiles
    comment = Directory personali
    writeable = yes 
    browseable = yes
    create mask = 0600
    directory mask = 0700

#
# Admin shares
#


[netlogon] 
    path = /home/netlogon 
    read only = yes 
    write list = @admin @prof
    browseable = no

[system]
   valid users = @teachers
   writeable = no
   browsable = no
   path = /home/netlogon 
   comment = script share
   root preexec = "sh /home/netlogon/iptables_open.sh %I"
   root postexec = "sh /home/netlogon/iptables_close.sh %I"

```

---

### Post by LordHunter317 on 2005-10-31
Read the Official Samba HOWTO on samba.org  Then come back with specific questions.

---

### Post by Glut on 2005-11-01
There is also an already-done ubuntu howto: [http://www.ubuntuforums.org/showthread.php?t=5409](http://www.ubuntuforums.org/showthread.php?t=5409)

---

### Post by billiejoex on 2005-11-02
I got a doubt: looking at that tutorial it seems to me that it regards the joining of a Linux workstation onto a Windows server system (NT/2000/2003). In my case the DC server is managed by samba. Does it makes differences?
Anyway, I followed the instructions and I encountered problems when I tried to join the domain. I can join the domain with the root account:
net rpc join -D MYDOMAIN -U root
...but if I try to log in with a different user I get the following error:
error setting trust account password: NT_STATUS_ACCESS_DENIED

This is the smb.conf of the linux client that wants to join the domain:

[global]
security = domain
netbios name = nix
workgroup = MIDEARTH
password server = PDC_server_name

---

### Post by Glut on 2005-11-02
It sounds like your root user isn't a domain administrator. You need to have an administrator join the domain.

---

### Post by billiejoex on 2005-11-03
Maybe I explained badly. I CAN join the domain with the domain administrator (root). I CAN'T join with user accounts.

---

### Post by LordHunter317 on 2005-11-03
Right, because you're not supposed to be able to.   You only join once.

You're joined, did you configure the client Linux box to use Winbind or similar to authenticate off the PDC now?

---

### Post by billiejoex on 2005-11-04
Yes, I tried it, but I received this error:
"The system administrator has disabled access to the system temporarily."
Maybe, do I have to use LDAP?

---

