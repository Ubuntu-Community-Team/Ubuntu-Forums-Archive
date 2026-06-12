---
title: "Samba as a WINS server"
date: 2005-09-13
forum: Server Platforms
---

### Post by bkthomas18 on 2005-09-13
I have Ubuntu 5.1 installed and I am running it as a network file server.  I also want to have it as a WINS server for the entire network.  From what I have read that seems possible but I'm not quite sure how to configure samba and my windows clients to make this work.  Doesn anybody know how to do this??  Thanks.

---

### Post by mlomker on 2005-09-13
It cannot be done--linux is not a WINS server.  SAMBA can serve as a master browser, but not a WINS server.

---

### Post by doogy2004 on 2006-08-29
Can a SAMBA server be used to allow Windows to browse the network neigborhood?

---

### Post by Xanthomryr on 2006-08-29
> **mlomker said:**
> It cannot be done--linux is not a WINS server.  SAMBA can serve as a master browser, but not a WINS server.
That isn´t right, of course can Samba run as a Wins server.

> 
**Setting Up Samba as a WINS Server**

You can set up Samba as a WINS server by setting the wins support parameter in the configuration file, like this:

    [global]
        wins support = yes

Believe it or not, that's all you need to do! The wins support option turns Samba into a WINS server. For most installations, Samba's default configuration is sufficient.

[http://de4.samba.org/samba/docs/using_samba/ch07.html](http://de4.samba.org/samba/docs/using_samba/ch07.html)

---

### Post by doogy2004 on 2006-08-29
thanks for the help, now I can finish setting up my linux box

---

### Post by doogy2004 on 2006-08-30
After doing all that in the guide, I assume that wins is working.  But it takes a while to browse the network using windows xp. Is there anything that I can do to speed it up?

---

### Post by Xanthomryr on 2006-08-30
Did you enter the name resolve order entry in the [global] section?

```
[global]
    name resolve order = wins lmhosts hosts bcast
```

Another thing you can try is making the samba server the local master browser by adding the following to your smb.conf:

```
[global]
    local master = yes
    os level = 255
    preferred master = yes
```

---

### Post by doogy2004 on 2006-08-30
here are the settings that I have in my smb.conf

```

name resolve = wins lmhosts host bcast
netbios name = ubuntu
wins server = yes
wins support = yes
wins proxy = yes
dns proxy = yes
browse list = yes
browseable = yes
security = share
domain master = yes
local master = yes
preferred master = yes
os level = 255
```

---

### Post by Xanthomryr on 2006-08-30
Are yo using samba as an PDC or why are using the domain master setting and no workgroup?

The wins server = yes setting is wrong, it must be an IP address or DNS name (of another Wins server on the network)

[http://de4.samba.org/samba/docs/using_samba/ch07.html#samba2-CHP-7-TABLE-1](http://de4.samba.org/samba/docs/using_samba/ch07.html#samba2-CHP-7-TABLE-1)

The browseable option is also wrong.
This option must be set in the disk shares sections if you want to make a share browseable. 
It´s not a setting for the global section.

Are you sure that you need the two proxy settings? 
Do you have a DNS server and another Samba Server in a different subnet on your network?
 
I would try a minimal config first, then add another option and test it, then add the next option and so on.

By the way, Samba can check your smb.conf with the command testparm.
It will show you if your smb.conf is okay or if there are any errors in it.

Here are my global section:
```

[global] 
   workgroup = ARBEITSGRUPPE
   server string = Server
   security = user

   interfaces = 127.0.0.1 192.168.1.0/24
   bind interfaces only = yes
   hosts allow = 127.0.0.1 192.168.1.0/24
   encrypt passwords = true

   log file = /var/log/samba/log.%m
   log level = 2
   syslog = 0
   syslog only = no
   max log size = 50

   wins support = yes
   name resolve order = wins lmhosts hosts bcast
   local master = yes
   os level = 255
   preferred master = yes

```

---

### Post by doogy2004 on 2006-08-30
I started with the default smb.conf that comes loaded with samba and made changes from there. Then, I updated my smb.conf and ran testparm, here is the output

```

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = DOOGY2004
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = wins lmhosts host bcast
        os level = 255
        preferred master = Yes
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
```

I am using a workgroup.

There is no other WINS or DNS server on the network.

I had the proxys in there because I read somewhere that they would help resolve NetBIOS names.

Thanks for the tip about testparm.

Please let me know if I can take any of the settings out without affecting what I am trying to do, Thanks in advance.

---

### Post by preymond on 2006-09-13
I had the same problem, running Ubuntu 6.06, adding:

    wins support = yes

in the [Global] section AND changing

    security = user

to:

    security = share

in the Authentication section, and adding at the ens of the file:

[Samba]
path = /home
available = yes
browseable = yes
public = yes
writable = yes

made all my /home/ directories available on the LAN.

---

### Post by doogy2004 on 2006-09-14
here is what i have in my smb.conf as of right now

```

[global]
netbios name = ubuntu
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
wins support = yes
name resolve order = wins lmhosts host bcast
browse list = yes
preferred master = yes
local master = yes
os level = 255
security = share

```

When adding shares i find that it is easiest to go into the system menu and find shared folders and add new shares in there.  It will edit the smb.conf and refresh everything.


if you are having a problem with xp being slow to browse the network, then the solution to that is that that is an xp problem, that i have not found a solution for.

---

