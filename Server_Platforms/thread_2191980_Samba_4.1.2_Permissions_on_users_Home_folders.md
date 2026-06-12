---
title: "Samba 4.1.2 Permissions on users Home folders"
date: 2013-12-05
forum: Server Platforms
---

### Post by JnPson on 2013-12-05
Hi.
I want to create a shared folder called **/Home** and use *Active Directory Users and Computers *to create **Home folders **for every user in my network. The problem is that every user is able to browse the other users home folder and this is not what I want. 

This is my smb.conf
```

# Global parameters
[global]
        workgroup = ARBETSFABRIKEN
        realm = arbetsfabriken.lan
        netbios name = DC02
        server role = active directory domain controller
        dns forwarder = 8.8.8.8
[netlogon]
        path = /usr/local/samba/var/locks/sysvol/arbetsfabriken.lan/scripts
        read only = No

[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No

[Profiles]
        directory_mode: parameter = 0700
        read only = no
        path = /Profiles
        csc policy = documents
        browseable = no
[Home]
#       directory_mode: parameter = 0700
        read only = no
        path = /Home
#       csc policy = documents
        browseable = yes
#       create mask = 0755


```
This is the **ls -l** from /:
```
drwxrwsrwx+  4 root users     4096 Dec  5 13:40 Home
```

This is how I created the folder:
```

mkdir -m 770 /Home
chmod g+s /Home
chown root:users /Home

```
How can I prevent other users from browsing all home folders and what are the correct permissions to set on **/Home**?

Thank you in advance.
//Additional info
I created the Home folder within properties/Profile with ```
\\DC02\Home\%USERNAME%
```

---

### Post by lingpanda on 2013-12-05
I use Folder Redirect but have you taken a look at the Wiki?

[https://wiki.samba.org/index.php/Setting_up_a_home_share](https://wiki.samba.org/index.php/Setting_up_a_home_share)

---

### Post by volkswagner on 2013-12-06
The reason every user can see other users is because you have not specified any restrictions, you also have browsable=yes.

Did you actually create a second /Home directory using capital 'H'?

What you are trying to accomplish is already built into SAMBA using the [homes] directive.  [homes] has special functions for hiding the source path /home and
only showing the username for authenticated users.  It also forces user credentials so other users can't simply type a path of a different user.

If the [homes] special share is not what you want, see this [samba doc]("https://wiki.samba.org/index.php/Setting_up_a_home_share") for setting up user home directory in domain environment.

As mentioned, folder redirection works well for your solution.  Just be aware a folder will be created with username appended with .V2 at the end.  So if you want
to use an existing folder you will need to rename it "username.V2" first.

---

### Post by JnPson on 2013-12-09
> **lingpanda said:**
> I use Folder Redirect but have you taken a look at the Wiki?

[https://wiki.samba.org/index.php/Setting_up_a_home_share](https://wiki.samba.org/index.php/Setting_up_a_home_share)

Your suggested link worked and solved this problem. Thank you.

---

