---
title: "Samba PDC access denied"
date: 2012-04-11
forum: Server Platforms
---

### Post by vitronix on 2012-04-11
Hello,

First let me tell you: I'm a newbie. I've got the Linux virus in my blood and it feels good.:p

Now for my problem: I created a smb.conf  file to let samba act as a PDC.
The testparm program doesn't protest.
Here are the contents of smb.conf

 [global]
        netbios name = ubuntu
        workgroup = VITRONIX
        encrypt passwords = yes
            
        domain master = yes
        local master = yes
        preferred master = yes
        os level = 65

        security = user
        domain logons = yes
        
        time server = yes
  
       add user script = /usr/sbin/useradd -m %u

    [netlogon]
        path = /etc/samba/net/netlogon
        writable = no
        browsable = no

    [homes]
        read only = no
        browsable = yes
        guest ok = yes
        map archive = yes
    
    [shared]
        path = /var/shared/test
        read only = no
        browsable = yes
        guest ok = yes

Now when I try to get XP to join the domain it gives Access Denied.
I logged on with a username and password created with smbpasswd

Can anybody help?

---

### Post by vitronix on 2012-04-16
> **vitronix said:**
> Hello,

First let me tell you: I'm a newbie. I've got the Linux virus in my blood and it feels good.:p

Now for my problem: I created a smb.conf  file to let samba act as a PDC.
The testparm program doesn't protest.
Here are the contents of smb.conf

 [global]
        netbios name = ubuntu
        workgroup = VITRONIX
        encrypt passwords = yes
            
        domain master = yes
        local master = yes
        preferred master = yes
        os level = 65

        security = user
        domain logons = yes
        
        time server = yes
  
       add user script = /usr/sbin/useradd -m %u

    [netlogon]
        path = /etc/samba/net/netlogon
        writable = no
        browsable = no

    [homes]
        read only = no
        browsable = yes
        guest ok = yes
        map archive = yes
    
    [test]
        path = /var/shared/test
        read only = no
        browsable = yes
        guest ok = yes

Now when I try to get XP to join the domain it gives Access Denied.
I logged on with a username and password created with smbpasswd

Can anybody help?

I found the problem: I did not set up a "user" account for the machine name (NetBIOS) name.
I gave the following command:

sudo useradd -d /dev/null -g 100 -s /bin/false -M virtual$

where virtual is the netbios name of the windows XP client. The useradd command creates a "user" without a shell and home directory.

Having done this everyting works fine.

Thing is: I don't know if you can set an ID of 100 for every machine (for testing I have only one client).
Can anybody tell me

---

