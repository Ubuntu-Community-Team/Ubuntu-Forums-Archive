---
title: "Public Share file server with Samba 4.1.6 on Ubuntu 14.04"
date: 2014-04-29
forum: Server Platforms
---

### Post by prinz.w on 2014-04-29
I am quite new with Samba, and I just got a issue with Samba 4.1.6 on Ubuntu 14.04 (32bit)

I install a ubuntu 14.04 on one of my old laptop and make it work as a home file server. I want to build a public file share server without any login or password required. I was successfully implemented once on a 13.04 version. But once I upgraded to 14.04, the configuration is not working properly. I made some adjustment based on the new smb.conf base. but still not working properly.

Here is my smb.conf

    > [global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad Password
        obey pam restrictions = Yes
        guest account = sambaguest
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        guest ok = Yes
    
    [printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No
    
    [print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
    
    [Data]
        comment = data
        path = /home/peter/Documents/ShareData
        read only = No
        create mask = 0777
        guest only = Yes

So far no IPtables implemented, I tried with the old configuration but apparently the **security = share** is  deprecated. 

So far in no matter what client within the LAN, the list of the shares (Data folder and printer) are appeared, however, when accessing the folder, it will prompt :

"you do not have permission to access ...."

Deeply wish to get it solved asap. 

Thank you!

Edit: I killed the server role line and add 

    security = user

---

### Post by bab1 on 2014-04-29
> **prinz.w said:**
> I am quite new with Samba, and I just got a issue with Samba 4.1.6 on Ubuntu 14.04 (32bit)

I install a ubuntu 14.04 on one of my old laptop and make it work as a home file server. I want to build a public file share server without any login or password required. I was successfully implemented once on a 13.04 version. But once I upgraded to 14.04, the configuration is not working properly. I made some adjustment based on the new smb.conf base. but still not working properly.

Here is my smb.conf

    

So far no IPtables implemented, I tried with the old configuration but apparently the **security = share** is  deprecated. 

So far in no matter what client within the LAN, the list of the shares (Data folder and printer) are appeared, however, when accessing the folder, it will prompt :

"you do not have permission to access ...."

Deeply wish to get it solved asap. 

Thank you!

Edit: I killed the server role line and add 

    security = user
Ubuntu 13.04 uses Samba 3 and Ubuntu 14.04 uses Samba 4.  My experience is that the file sharing daemon smbd (process) is the same in both Samba versions.  I've configured 3 of these at this point.

You have made changes, but I'm not sure why.  Security = share has been deprecated for years now.  Security = user is what should be used for a standalone Samba server and it is the default setting.  Why create a guest user (smbguest) when you could have just as easily used the default guest user (nobody)?

Some of the beta versions of Ubuntu 14.04 had a bug in the Samba config file.  This had to do with commenting out the [homes] share definition correctly.  I think that's resolved now.  The only thing you need to do configure the file system directory that you're going to use and add the share definition at the bottom of the default smb.conf file.  Did you make a copy of the default smb.conf file?

---

### Post by prinz.w on 2014-04-30
> **bab1 said:**
> Ubuntu 13.04 uses Samba 3 and Ubuntu 14.04 uses Samba 4.  My experience is that the file sharing daemon smbd (process) is the same in both Samba versions.  I've configured 3 of these at this point.

You have made changes, but I'm not sure why.  Security = share has been deprecated for years now.  Security = user is what should be used for a standalone Samba server and it is the default setting.  Why create a guest user (smbguest) when you could have just as easily used the default guest user (nobody)?

Some of the beta versions of Ubuntu 14.04 had a bug in the Samba config file.  This had to do with commenting out the [homes] share definition correctly.  I think that's resolved now.  The only thing you need to do configure the file system directory that you're going to use and add the share definition at the bottom of the default smb.conf file.  Did you make a copy of the default smb.conf file?

Hi Bab1 

So far I changed owner to sambaguest and chmod 0777, but still have no luck for that. previously in 13.04, I used security = share and works perfectly. btw my system is 14.04 stable build 32 bit server, is that an issue?

Really get frustrating now... Thanks for the help!

---

### Post by LHammonds on 2014-04-30
I installed a fresh Ubuntu 14.04 server and public sharing works for me.

I'm working on refreshing my 12.04 documentation so the 14.04 version is not 100% complete but the section called "Configuring Ubuntu for File Sharing" works fine.

[How To Install and Configure Ubuntu Server 14.04 LTS]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=200#p363")

LHammonds

---

### Post by bab1 on 2014-04-30
> **prinz.w said:**
> Hi Bab1 

So far I changed owner to sambaguest and chmod 0777, 

What exactly did you do?  Where did you change the owner to sambaguest?
> 
but still have no luck for that. previously in 13.04, I used security = share and works perfectly. 

Read the documentation.  I believe you will find that *security = share * is no longer a valid parameter.  Post the output of ```
testparm -s
```
> 
btw my system is 14.04 stable build 32 bit server, is that an issue?
Really get frustrating now... Thanks for the help!
I don't see where you actually used *security = share * so why bring that up.  In fact Ubuntu 14.04 now uses Samba v4 instead of Samba v3 and that configuration parameter you are using is not available anymore.  It was originally used in Samba v2 and deprecated in Samba v3.  Now in Samba v4 it has been dropped.

Please explain in greater detail what you have done when you implemented the user *sambaguest*.

---

### Post by prinz.w on 2014-05-02
Hi BAB1

Thanks for the reply! here is my output for testparm
> Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad Password
    obey pam restrictions = Yes
    guest account = sambaguest
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Data]
    comment = data
    path = /home/peter/Documents/ShareData
    read only = No
    create mask = 0777
    guest only = Yes


Forget about the *share* thing.  I was mentioning that i was using that in 13.04 and worked somehow.

and the premission for the ShareData folder:
> # ls -l /home/peter/Documents/
total 4
drwxrwxrwx 2 sambaguest nogroup 4096 Apr 28 11:51 ShareData

Any suggestion?

---

### Post by prinz.w on 2014-05-02
Hi BAB1

I think i got that managed. 

The solution is to create and assign the share folder somewhere else other than the /home/...  I dont know the reason but that is how it fixed. 

I changed it to /srv/share, chmod 0777 and chown nobody:nogroup

restart smbd and nmbd 

then it works! 

For future reference I will repost the smb.conf tomorrow. 

BAB1 or anybody, any idea about why it cannot be setup under /home?

Cheers
Prinz

EDIT: I purged the samba and samba-common to redo the configuration. This time i did not assign the gust user.
regarding with the /home... folder thing, i also do chown nobody:nogroup to that folder and still not working.

---

### Post by bab1 on 2014-05-02
> **prinz.w said:**
> Hi BAB1

I think i got that managed. 

The solution is to create and assign the share folder somewhere else other than the /home/...  I dont know the reason but that is how it fixed. 

I changed it to /srv/share, chmod 0777 and chown nobody:nogroup

restart smbd and nmbd 

then it works! 

For future reference I will repost the smb.conf tomorrow. 

BAB1 or anybody, any idea about why it cannot be setup under /home?

Cheers
Prinz

EDIT: I purged the samba and samba-common to redo the configuration. This time i did not assign the gust user.
regarding with the /home... folder thing, i also do chown nobody:nogroup to that folder and still not working.

To vague for me to follow.  All of your problems are do to incorrect directory permissions.  You need to have eXecute permissions on** all directories along the path **  to the share.  Not just the directory that is the share root.

The only thing you need to reconfigure Samba is the smb.conf file.  To start over you just use the original untouched smb.conf file.  I always make a copy of that file before I modify it.  There is no reason in most cases to reinstall Samba.

---

### Post by prinz.w on 2014-05-12
Hi BAB1

Thank you for your kind reply and answers!

Just for further reference, here is my testparm output

[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[Data]
    comment = data
    path = /srv/samba/share
    read only = No
    create mask = 0777
    guest ok = Yes

And  what you mentioned 
> You need to have eXecute permissions on** all directories along the path **  to the share
is correct!

Again, Thank you BAB1 and everybody!

Regards

---

