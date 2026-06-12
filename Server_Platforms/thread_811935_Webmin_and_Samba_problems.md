---
title: "Webmin and Samba problems"
date: 2008-05-29
forum: Server Platforms
---

### Post by Twizzle on 2008-05-29
I have just installed 8.04 server edition and Webmin for the first time and am trying to setup an NTFS drive in the server as a share so a number of computers can access it on my home server. I followed [this]("http://www.webmin.com/samba-howto.html") guide but for some reason, while I can see the share from both XP and Ubuntu, I can not log in as I keep being told my password in incorrect.

My server is setup with a single user 'administrator' and my Ubuntu box has a single user 'john'. XP also has a single user 'john'.

I know the password I am trying to use works as I have run smbapasswd and changed it for user 'administrator'.

When I get the login prompt from Ubuntu I try both names (john and administrator) with my password with no luck. I know that the workgroup is correct.

When I try to view from XP, the 'user' field is greyed out but I tried with the right password and still no luck.

I am sure I am missing / have done something silly here!

---

### Post by NateMan on 2008-05-29
Have you tried making a new samba user to test and see if it is possible to connect to that fileshare? (you can always delete when done) What about your user settings? Have you gone in and set the samba user for the individual account? I personally don't recommend using a root-type user for your samba shares, just making a separate user for the share.

---

### Post by Twizzle on 2008-05-29
I created a new user for Samba as you reccomended and Windows share worked (Thanks :) )but Ubuntu did not.

I did a bit more playing around and I think I have just figured it out - I had the security in webmin set to share level instead of user level. Once I changed it, everything worked!

Not sure if that was the only thing wrong because I changed a few settings in my frustration!

Thanks for the help.

---

### Post by NateMan on 2008-05-29
No problem. I've dealt with quite a few samba issues. They can be annoying, but are normally not a problem. There are better file sharing systems (such as nfs) for unix-based systems fyi.

---

### Post by sDoky on 2008-05-29
Well I created completely new smb.conf with user = public and read/write restricted folder by folder. It does the writeable = [yes/no] anyone can access it now, it can't be misused this way, as long as those r/w permissions are correctly set.

my smb.conf
```
[global]
        workgroup = WORKGROUP
        server string = Ubuntu
        netbios name = server
        hosts allow = 10.0.0.2 10.0.0.3 10.0.0.4
        security = share
        smb passwd file = /etc/samba/smbpasswd

[Multimedia]
        guest ok = yes
        guest only = yes
        guest account = nobody
        path = /media/sda1
        browsable = yes
        writeable = no
[Data]
        guest ok = yes
        guest only = yes
        guest account = nobody
        path = /media/sdb1
        browsable = yes
        writeable = no
[Share]
        guest ok = yes
        guest only = yes
        guest account = nobody
        path = /share
        browsable = yes
        writeable = yes
```

EDIT: the folder you want to share must be read/write/execute enabled for the owner and owner set to 'nobody'

---

