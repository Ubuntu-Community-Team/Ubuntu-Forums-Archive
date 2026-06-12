---
title: "Review my smb.conf"
date: 2011-06-25
forum: Server Platforms
---

### Post by doas777 on 2011-06-25
So, I was adding a share to my smb.conf today, and realized its been a few years since I last reviewed it. Everything is working fine (and testparm has no complaints), but I wanted to get some peer review on my config.

```

[global]

    #server settings
    bind interfaces only = yes
    interfaces = 127.0.0.0/8 eth1
    #Socket options set buffers to 65355 for optimization
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
    create mask = 2774
    directory mask = 2770
    preserve case = yes
;    follow symlinks = yes
    read raw = no
    winbind enum groups=yes
    winbind enum users=yes
    name resolve order = wins lmhosts hosts bcast
    panic action = /usr/share/samba/panic-action %d

    #smb settings
;    netbios name = Files
    workgroup = MyNet
;    #never enable this for client
    wins support = yes
;       #never enable this for server     
;       #wins server = 192.168.XX.YY  
    server string = %h server (Samba, Ubuntu)
;    disable netbios = no
;    dns proxy = yes
    os level = 32
    domain master = yes
;    local master = yes
    prefered master = yes
    load printers = no
    max connections = 20
    
    #Security
    security = user
    smb passwd file = /etc/smbpasswd
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    client NTLMv2 auth = yes
    encrypt passwords = true
;    guest ok = no
;    usershare allow guests = yes
    hosts allow = 192.168.XX.0/24 127.0.0.1
    hosts deny = 0.0.0.0/0
    invalid users = root
    map to guest = bad user
    obey pam restrictions = yes
    pam password change = yes
    unix password sync = yes

    #Logging
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 2000

#============ Share Definitions =======================#

[pub]
    comment = Users's Public
;    browsable = yes
    read only = no
    locking = no
    path = /home/User/Public

```

Notes: 
wins should be enabled
guest is not allowed
create permissions should use setgid 
user security (with smbpasswd -a).
encrypted authentication
encrypted passwd storage

so, see any obsolete settings, or conflicts? any advice on the ; lines?
What do you think?

Thanks all!

---

### Post by doas777 on 2011-06-26
ok, lets try some more specific questions then.

1) do I need tdbasm? will the combo of:
```

security = user
smb passwd file = /etc/smbpasswd
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
unix password sync = yes
encrypt passwords = true
obey pam restrictions = yes

```give me strong encryption on passwords at rest and on the network? without tdbasm? Somthing commented out the passwd backend setting so any idea why?

2) Netbios name is commented out, but I certianly didn;t do it. any idea why? is it obsolete?

3) I want the server to win all browser elections and basically always be masterbrowser. will this config do all that is needed?
```

os level = 32
    domain master = yes
;    local master = yes
    prefered master = yes

```I wonder what commented out local master.

4) I have uit configured as a wins server, and have the clients point to it. does this config seem rational?
```

wins support = yes
winbind enum groups=yes
winbind enum users=yes

```
Thanks All!

---

### Post by doas777 on 2011-06-27
bump

---

### Post by bab1 on 2011-06-27
> **doas777 said:**
> ok, lets try some more specific questions then.

1) do I need tdbasm? will the combo of:
```

security = user
smb passwd file = /etc/smbpasswd
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
unix password sync = yes
encrypt passwords = true
obey pam restrictions = yes

```
give me strong encryption on passwords at rest and on the network? without tdbasm? Somthing commented out the passwd backend setting so any idea why?

2) Netbios name is commented out, but I certianly didn;t do it. any idea why? is it obsolete?

3) I want the server to win all browser elections and basically always be masterbrowser. will this config do all that is needed?
```

os level = 32I 
    domain master = yes
;    local master = yes
    prefered master = yes

```
I wonder what commented out local master.

4) I have uit configured as a wins server, and have the clients point to it. does this config seem rational?
```

wins support = yes
winbind enum groups=yes
winbind enum users=yes

```


Thanks All!

So is this a domain situation or just a workgroup on a LAN?

---

### Post by doas777 on 2011-06-27
> **bab1 said:**
> So is this a domain situation or just a workgroup on a LAN?
just a workgroup. 

my needs are reasonably simple at present. I should probably try ldap at some point, but I feel comfortable with my network services as they are now. I'll be reinstalling the whole server when the next LTS comes out, so maybe then.

---

### Post by bab1 on 2011-06-27
> **doas777 said:**
> So, I was adding a share to my smb.conf today, and realized its been a few years since I last reviewed it. Everything is working fine (and testparm has no complaints), but I wanted to get some peer review on my config.

```

[global]

    #server settings
    bind interfaces only = yes
    interfaces = 127.0.0.0/8 eth1
    #Socket options set buffers to 65355 for optimization
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
    create mask = 2774
    directory mask = 2770
    preserve case = yes
;    follow symlinks = yes
    read raw = no
    winbind enum groups=yes
    winbind enum users=yes
    name resolve order = wins lmhosts hosts bcast
    panic action = /usr/share/samba/panic-action %d

    #smb settings
;    netbios name = Files
    workgroup = MyNet
;    #never enable this for client
    wins support = yes
;       #never enable this for server     
;       #wins server = 192.168.XX.YY  
    server string = %h server (Samba, Ubuntu)
;    disable netbios = no
;    dns proxy = yes
    os level = 32
    domain master = yes
;    local master = yes
    prefered master = yes
    load printers = no
    max connections = 20
    
    #Security
    security = user
    smb passwd file = /etc/smbpasswd
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    client NTLMv2 auth = yes
    encrypt passwords = true
;    guest ok = no
;    usershare allow guests = yes
    hosts allow = 192.168.XX.0/24 127.0.0.1
    hosts deny = 0.0.0.0/0
    invalid users = root
    map to guest = bad user
    obey pam restrictions = yes
    pam password change = yes
    unix password sync = yes

    #Logging
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 2000

#============ Share Definitions =======================#

[pub]
    comment = Users's Public
;    browsable = yes
    read only = no
    locking = no
    path = /home/User/Public

```

Notes: 
wins should be enabled
guest is not allowed
create permissions should use setgid 
user security (with smbpasswd -a).
encrypted authentication
encrypted passwd storage

so, see any obsolete settings, or conflicts? any advice on the ; lines?
What do you think?

Thanks all!

Why do you feel you need a WINS server running in a workgroup environment?  What advantage does it provide?  Samba does not recommend running a WINS server on a single segment network (one subnet) *[COLOR="Blue"]Wins support = ... "You should not set this to yes unless you have a multi-subnetted network and you wish a particular nmbd to be your WINS server." [/COLOR]*  You can check it out [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

Why do you have Winbind (which is not part of WINS) running without being in a domain?

In a LAN situation most of the defaults are fine for me.  I guess you can tighten up the security as you have, but i have never had any problems with just setting the workgroup name (for my visual convenience) and then adding the shares.  Pretty simple.

I think the most important part is having local the /etc/hosts file properly configured.  I learned this from @capscrew and @morbius1.  

Then I just add the shares. The group on all shares is smbusers.  I do use the setgid and sticky bit.  That way I don't have to change chgrp on the files and no one deletes the others work.  

I only allow guests on the share Public (/srv/Public).  This allows guests and has the same group as the other shares.  I did change the guest from the user nobody to smbguest.

---

### Post by Dangertux on 2011-06-28
It's a PITA to do it (tends to break things)

However, I would suggest disabling winbind user and group enumeration. Your choice though , I also agree with not running WINS on a workgroup . Also to answer one of your above question WINS should override the netbios name parameter in the samba configuration file, which is probably why it is commented.

The other recommendation would be using LDAP for authentication, however you already addressed your plans for that.

---

### Post by doas777 on 2011-06-28
Wonderful guys, 
that is exactly why I wanted to ask. Thanks

this config goes back to Feisty, and I had to fight with it a good bit to get it going. I am no longer certian what config was there originally, and what I have added over the years. I got a good chunk of it from Camel.org.

I have had multiple subnets in past (don't right now) but the server has never been multihomed. 

so your recommendations are to remove the Winbind settings, and disable wins. seems reasonable.

is winbind nmbd?

---

### Post by bab1 on 2011-06-29
> **doas777 said:**
> Wonderful guys, 
that is exactly why I wanted to ask. Thanks...
so your recommendations are to remove the Winbind settings, and disable wins. seems reasonable.

is winbind nmbd?

No Winbind is not nmbd.  Winbind is winbindd and it maps Windows SID to Linux uid/gid.  It is used in NT domain and Windows AD environments (centralized users).

The nmbd is for Samba name services.  It will map hostnames (/etc/hosts or DNS) to NETBIOS names or run as a WINS server.  If you use it to map host names to NETBIOS names it will do this through b'cast so you don't even need and DNS or WINS server.  This is how Windows does it.  There is a NETBIOS helper service running.  The difference is Windows runs the helper service all the time.  In Ubuntu you need to configure the /etc/hosts file or run DNS on the LAN.

At one time Windows claimed they were done with NETBIOS.  Then they found out that many apps relied on the service so now the service runs all the time.  In NETBIOS speak it is a "hybrid node".

---

