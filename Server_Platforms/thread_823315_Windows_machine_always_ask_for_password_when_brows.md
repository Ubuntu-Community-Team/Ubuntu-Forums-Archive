---
title: "Windows machine always ask for password when browsing SAMBA share."
date: 2008-06-09
forum: Server Platforms
---

### Post by BMOE on 2008-06-09
Hello everyone.

I'm using Ubuntu 8.04 Server Edition.

I'm about to set up a fileserver at home using SAMBA and SWAT as GUI interface.

I have put in a new HDD as I have partitioned and mounted as /mnt/files and then CHMOD'ed /mnt/files to 777.

I have added two samba users, root and matias.

What I want is that everyone on my home network, wich is my girlfriend and I, will have full read/write access to the files without logging in as a specific user.

Now to my problem.
From my windows laptop at home I can see the server when I browse my Windows Network, but when I "double click" it I always need to login.
What can I do so that I(or anyone else) don't need to login to get access to my files on the server.

This is what my smb.conf file looks like.

```
# Samba config file created using SWAT
# from 192.168.0.4 (192.168.0.4)
# Date: 2008/06/08 21:50:37

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
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
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Share /mnt/files]
        comment = Share /mnt/files
        path = /mnt/files
        read only = No
        guest ok = Yes
```

---

### Post by jonandrews on 2008-06-09
I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


I hope it is helpful.

---

### Post by kamaji792 on 2008-06-09
The way I stop having to enter a user name and passoword when connecting to a Samba share is by having the same user name and passowrd on the windows PC and the Linux box.

Also make sure the users are added to Samba ( smbpasswd -a <user> ...er I think ).

---

### Post by BMOE on 2008-06-09
> **jonandrews said:**
> I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


I hope it is helpful.

Sorry, I should have told that I'm using Ubuntu Server Edition so I have no GUI. I have edited my firs post.

---

### Post by BMOE on 2008-06-09
> **kamaji792 said:**
> The way I stop having to enter a user name and passoword when connecting to a Samba share is by having the same user name and passowrd on the windows PC and the Linux box.

Also make sure the users are added to Samba ( smbpasswd -a <user> ...er I think ).

I want everyone that connect to my network from any computer and any user to be able to have full access to my files. Sorry.

---

### Post by sisco311 on 2008-06-09
Set the security option to share:
> [global]

   workgroup = ?HOME?
   security = share
   invalid users = root
[FONT=monospace]
[/FONT][printers]

...



---

### Post by BMOE on 2008-06-09
> **sisco311 said:**
> Set the security option to share:

Thank you very much.

Added security = share to the global section and now I can view the shared folder on my server without logging in, but now I got another little problem.

When I now want to open my shared folder(that I now can se without logging in) from my windows computer I get a login screen that wants me to type in the password for /server/guest.

Do I have to add a guest user account to my server?

Damn I'm glad that you guys know so much.

---

### Post by Vaderdarth211 on 2008-06-09
I'm finding this very helpful. Been trying to do this myself, however i'm a noob and don't have a working server right now. Having install glitches.
So once i get it set up, i'd like to try this.

---

### Post by samosamo on 2008-06-09
[http://ubuntuforums.org/showthread.php?t=720889](http://ubuntuforums.org/showthread.php?t=720889)

---

### Post by BMOE on 2008-06-10
> **samosamo said:**
> [http://ubuntuforums.org/showthread.php?t=720889](http://ubuntuforums.org/showthread.php?t=720889)

Sorry, not really what I was looking for.

---

