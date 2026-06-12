---
title: "Permissions correct access denied Samba 4"
date: 2019-07-16
forum: Server Platforms
---

### Post by elcidsps on 2019-07-16
I am in the middle of permissions chaos setting up my samba server and shares.  This is not a complicated setup but I cannot get the permissions to work:

Scenario:
Samba 4 on Ubuntu 19.04


5 users in the same group (company) need to access a Samba Share and have the ability to read, write, edit and delete files and folders in the share (regardless of the author).  The members of the group are the only individuals that have access to the share.  My SMB.CONF looks like this:


```
    [global]
       workgroup = PREMPROVSOL
       server string = %h server (Samba, Ubuntu)
       interfaces = 127.0.0.0/8 10.0.10.0/24
       bind interfaces only = yes
       log file = /var/log/samba/log.%m
       max log size = 1000
       logging = file
       panic action = /usr/share/samba/panic-action %d
       server role = standalone server
       obey pam restrictions = yes
       unix password sync = yes
       passwd program = /usr/bin/passwd %u
       passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
       pam password change = yes
       map to guest = bad user
       unix charset = UTF-8
       dos charset = CP932
       create mask = 0777
       directory mask = 2777
       force create mode = 0777
       force directory mode = 2777
    
    
    [Client-Billing]
        path= /server/Client-Billing/
        writeable = yes
        guest ok = no
        valid users = @company
        force group = company



```I created a folder called 'Test' and when I examined the owner, it has the user who created the folder but all the permissions look correct:


```
drwxrwsrwx+  2 theuser company 4.0K Jul 15 13:38  Test

```
I have issued the following modifications to the Client-Billing folder:
```
    sudo chmod g+s server/Client-Billing/
    sudo chown root:company server/Client-Billing/
    sudo chmod -R 0777 server/Client-Billing/

```
My problem is when a user creates a folder (from Win10 machines, another user cannot create, copy to, etc. a file in that folder. Users can VIEW files created by other users but cannot edit an save them in the same folder.
When the user copies a file (say a PDF) into the folder the permissions on the file look odd and do not correspond with the SAMBA configuration:
```
-rwxrwx---+ 1 theuser company 136K Jul 10 10:34 doc10284020190710104636.pdf
```
I'm at a bit of a loss where to go from here.  What is it that I am missing?

***EDIT***

Been tinkering with the smb.conf file and found that
```
    [Client-Billing]
        path= /server/Client-Billing/
        writeable = yes
        guest ok = no
        valid users = @company
        force group = company
        create mode = 0775
        directory mode = 2775

```and 
```

 [Corporate]
        path= /server/Corporate/
        writeable = yes
        guest ok = no
        valid users = @corporate
        force group = corporate
        create mode = 0775
        directory mode = 2775

```Have the exact same configurations; however, `Corporate` share works perfectly and the `Client-Billing` share has permission issues. Still befuddled.  Any insight?

---

### Post by Morbius1 on 2019-07-16
Hi. Seems like you can't get away from me. 

> Have the exact same configurations; however, `Corporate` share works 
perfectly and the `Client-Billing` share has permission issues.

I would be willing to bet that the extended permissions ( getfacl /server/Corporate ) - if there are any - don't look anything like this:

> Removing leading '/' from absolute path names
# file: server/Client-Billing/TargetFolder
# owner: theuser
# group: company
# flags: -s-
user::rwx
user:root:rwx
user:777:rwx
user:3000042:rwx
group::r-x
group:root:r-x
group:3000042:rwx
mask::rwx
other::rwx
default:user::rwx
default:user:root:rwx
default:user:777:rwx
default:user:3000042:rwx
default:group::r-x
default:group:root:r-x
default:group:3000042:rwx
default:mask::rwx
default:other::---
I have no idea who that user and group are or how - if you didn't set this up yourself - they got there. Is /server/Client-Billing under the control of another application or service?
Since this works without issue:
> [Corporate]
        path= /server/Corporate/
        writeable = yes
        guest ok = no
        valid users = @corporate
        force group = corporate
        create mode = 0775
        directory mode = 2775



Can't you just make another one with a path to a different folder /server/Client-Billing-2 or something. Just don't apply any exotic acl's to it.

---

### Post by elcidsps on 2019-07-16
@Morbius1:

Look like we hang out in the same places.  You've helped me quite a bit in the past and I have a lot of respect.  Thanks.

I am copying the folder into another folder.  I'll let you know how that goes.  Thanks again

Shawn

---

### Post by elcid91 on 2019-07-22
Morbius1:

Everything works as expected after re-creating the shares and re-copying the files/folders.  Thanks for the heads up on that.  Now that all my Win10 boxes properly connect to the shares, I am having an issue with my Linux Mint machine.  I am able to connect to the shares; however, I am not able to do anything in them from the Linux box.  My fstab entries look like this:

```
//10.0.10.240/Company /mnt/Company cifs uid=1001,gid=1004,iocharset=utf8,file_mode=0775,dir_mode=0775,credentials=/home/user/.smbcred  0       0
```

Though connection is made and I can browse the share, I cannot do anything inside the share.

IF I connect to the share view the "Connect Server" on the file explorer, it works perfectly.  So I am not sure how to get the linux to connect the share via fstab.

---

### Post by Morbius1 on 2019-07-22
Add one more option to your list: nounix

> //10.0.10.240/Company /mnt/Company cifs uid=1001,gid=1004,iocharset=utf8,file_mode=0775,dir_mode=0775,[COLOR=#0000cd]**nounix**[/COLOR],credentials=/home/user/.smbcred  0       0

---

