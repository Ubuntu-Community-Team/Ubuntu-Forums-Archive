---
title: "Ubuntu 12.04 samba issue"
date: 2012-06-09
forum: Server Platforms
---

### Post by brent1975 on 2012-06-09
Hello, I am testing out version 12.04 and I am stumped with just "1" of my shares called music. All my other shares Brent,Jessica,movies, and WWW is seen and connected through windows 7 with no problems at all. all my shares appear to be identical outside of path naturally. and yes the music directory is in /home/music. When I try to connect to \\192.168.2.106\music I get access denied. I have done all the same steps for the other shares I created.



[global]
   server string = %h server (Samba, Ubuntu)
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
   valid users = brent, brian, jessica
   admin users = brent, brian, jessica
   write list = brent, brian, jessica

[printers]
   comment = All Printers
   path = /var/spool/samba
   create mask = 0700
   printable = Yes
   browseable = No

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers

[www]
   path = /var/www
   username = brent,root
   write list = brent, root

[Brent]
   path = /home/brent
        valid users = brent
        write list = brent

[Jessica]
   path = /home/jessica
        valid users = brent, jessica
        write list = brent, jessica

[movies]
   path = /home/movies
   valid users = brent, jessica
   write list = brent, jessica

[music]
   path = /home/music
   valid users = brent, jessica
   write list = brent, brian

also when I run I get an interesting result
```
testparm -s [/code

[code]
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[www]
        path = /var/www
        username = brent,root
        write list = brent, root

[Brent]
        path = /home/brent
        valid users = brent
        write list = brent

[Jessica]
        path = /home/jessica
        valid users = brent, jessica
        write list = brent, jessica

[movies]
        path = /home/movies
        valid users = brent, jessica
        write list = brent, jessica

[music]
        comment = Home Directories
        path = /home/music
        valid users = %S
        write list = brent, brian
        read only = No
        browseable = No

```

in smb.conf the music config that I show does not have the last two lines "read only = No, and browseable = No" So why is that populating this? I am amusing this is what my hangup is.

---

### Post by Doug S on 2012-06-09
Just an observation (as opposed to an in depth look at the file): "music" is the only one where the valid users and write list do not match. Is that last line terminated correctly? I.E. if you move "music" ahead of "movies" does "movies" become the issue?

---

### Post by Morbius1 on 2012-06-09
This may not be a Samba issue.
> ls -dl /home/music
Who has permissions to access /home/music?

---

### Post by brent1975 on 2012-06-09
> **Doug S said:**
> Just an observation (as opposed to an in depth look at the file): "music" is the only one where the valid users and write list do not match. Is that last line terminated correctly? I.E. if you move "music" ahead of "movies" does "movies" become the issue?

Yes, I switch out the two now I am able to connect to music but not movies. and now when I run  
[FONT=monospace]testpam -s

the results have switched

[music]
        path = /home/music
        valid users = brent, jessica
        write list = brent, jessica

[movies]
        comment = Home Directories
        path = /home/movies
        valid users = %S
        write list = brent, jessica
        read only = No
        browseable = No
 
[/FONT]

---

### Post by brent1975 on 2012-06-09
I even went into the smb.conf and add those lines and changed the value to yes

testparm -s is not getting those changes.

---

### Post by Morbius1 on 2012-06-09
I just saw your last edit. You know what this looks like:
> 
[music]         
[COLOR=Blue]comment = Home Directories[/COLOR]
path = /home/music         
[COLOR=Blue]valid users = %S         [/COLOR]
write list = brent, brian         
read only = No 
        [COLOR=Blue]browseable = No[/COLOR]It looks like a mix of a classic samba [homes] share:
> [homes]
[COLOR=Blue]comment = Home Directories
valid users = %S
read only = No[/COLOR]
create mask = 0700
directory mask = 0700
[COLOR=Blue]browseable = No[/COLOR]Intermixed with something else.

Was your post of smb.conf from a "cat /etc/samba/smb.conf" ?

---

### Post by brent1975 on 2012-06-09
> **Morbius1 said:**
> I just saw your last edit. You know what this looks like:
It looks like a mix of a classic samba [homes] share:
Intermixed with something else.

Was your post of smb.conf from a "cat /etc/samba/smb.conf" ?


Yes I am not sure where some of these lines are coming from.

Here is my conf file from /etc/samba/smb.conf

 [print$]
       comment = Printer Drivers
       path = /var/lib/samba/printers

    [www]
       path = /var/www
       username = brent,root
       write list = brent, root

    [Brent]
       path = /home/brent
            valid users = brent
            write list = brent

    [Jessica]
       path = /home/jessica
            valid users = brent, jessica
            write list = brent, jessica

    [music]
        path =/home/music
        valid users = brent, jessica
        write list = brent, jessica

    [movies]
       path = /home/movies
       valid users = brent, jessica
       write list = brent, jessica

---

### Post by brent1975 on 2012-06-09
> **Morbius1 said:**
> I just saw your last edit. You know what this looks like:
It looks like a mix of a classic samba [homes] share:
Intermixed with something else.

Was your post of smb.conf from a "cat /etc/samba/smb.conf" ?

and then when I run testparm -s 

this is what I get

[www]
        path = /var/www
        username = brent,root
        write list = brent, root

[Brent]
        path = /home/brent
        valid users = brent
        write list = brent

[Jessica]
        path = /home/jessica
        valid users = brent, jessica
        write list = brent, jessica

[music]
        path = /home/music
        valid users = brent, jessica
        write list = brent, jessica

[movies]
        comment = Home Directories
        path = /home/movies
        valid users = %S
        write list = brent, jessica
        read only = No
        browseable = No

---

### Post by volkswagner on 2012-06-09
Examine the entire smb.conf file.

Likely you will find those two directives dangling somewhere not associated with a specific [share].

Use the less command to read through the file... to find a particular string start with /
Commands would look like the following:

```
less /etc/samba/smb.conf
```

then type
/browseable = No
hit enter
use the n key to find the next entry with the same value
n
n
n


Hope this helps.

---

### Post by brent1975 on 2012-06-10
Thanks everyone. I decided to just blow the smb.conf file away and create a new one. The shares are working properly.

---

