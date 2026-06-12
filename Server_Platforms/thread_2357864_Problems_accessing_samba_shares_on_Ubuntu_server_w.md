---
title: "Problems accessing samba shares on Ubuntu server with Windows 10"
date: 2017-04-06
forum: Server Platforms
---

### Post by psking on 2017-04-06
Hi,

I've recently had to restore my Windows 10 system from a working image but since I did it my Samba shares no longer work.

The server has been installed for a couple of years with a stable /etc/samba/smb.conf which always just worked!  Since I restored my Windows 10 PC, which has the server name in the hosts file and can connect to the server via ssh2 in a terminal session, just cannot maintain a stable connection to the shared folders in Windows Explorer. For starters it takes a long time for it to list the shared directories, then when you click into one of them, it lists the contents, then seems to want to keep refreshing the display!  If you try and descend into directories within the share it will typically lose all contact saying "Windows cannot access \\Server". Bizarre.  If I then restart samba service on the server I can then see the shares again but can't get as far as copying a file to the Windows machine.

This is really perplexing me - seems like a problem at the windows end, but i'm really out of ideas.

Here's a section from my smb.conf:

```
[homes]
   comment = Home Directories
   browseable = yes


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775




[data]
   comment = Data
   path = /data
   browseable = yes
   create mask = 0775
   directory mask = 0775
   read only = no


[data2]
   comment = Data2
   path = /data2
   browseable = yes
   directory mask = 0775
   create mask = 0775
   read only = no
``` 

Anyone have any ideas?

Thanks.

Phil

Sorry, meant to say :  Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic x86_64)

---

### Post by psking on 2017-04-09
anyone?

---

### Post by nihvel on 2017-04-10
Hello, it is a known problem and I some times face it too. Windows does not really like Samba, therefore problems like these may appears.
I can suggest my Samba configuration and Windows trick I applied on the eth card.

**About Samba**, I would use (and I do) the cache and oplock (read both on the manual).
One of my typical share is:
```

[Frank]
        path = /home/samba/frank
        valid users = @frank
        force group = frank
        read only = No
        directory mask = 0770
        force directory mode = 0770
        create mask = 0660
        force create mode = 0660
        write cache size = 2621440
        veto oplock files = /*.tmp/
```

[B]On Windows:
[/B]The problem is that Windows 7 (and latest) incorporates some features that can slow down connections with other operating systems.With these changes, Windows can gain speed connections to shared resources on Linux.

***1. Disable autotuning***
Open the cmd as administrator and type:
```
netsh interface tcp show global
```

check the row that says about autotuning, it should be on "normal". Deactivate it:
```
netsh interface tcp set global autotuning=disabled
```

Should just say "OK.".
Check it again with the "show" command and see if it is deactivated now. If it is...

***2. Disable RDC (remote differential compression)***Go to control panel -> programs and feature and "turn windows feature on/off".
Uncheck "Remote differential compression".


Reboot Windows and restart Samba after its new setting and should be solved.

Not saying it works 100%, I can tell you this is the configuration I apply to all of my clients (Under OpenVPN) and no one have bad downtimes with it like those you described (and they/me had before).

---

### Post by psking on 2017-04-10
Hi nihvel

Thank you so much for this. I have made the changes to my smb.conf and the Windows 10 changes.  After a reboot and a samba restart I now get the Windows Security "Enter network credentials" which I didn't before. However, despite definitely typing the correct server password for the user I am getting "Access is denied".


[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   valid users = @phil
   force group = phil
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/
   create mask = 0770
   directory mask = 0770

My Windows username is "phil" - so I used that in the valid users and force group - correct?

I haven't done anything with cache and oplock - bit beyond me I'm afraid!

So, I am not sure why I am getting access denied.

Phil

---

### Post by nihvel on 2017-04-11
you should add phil to samba users:
```

smbpasswd -a phil
```
And restart samba.

and, chmod 775 the root of samba to allow users,group and others to e**X**ecute folders (enter):
```
chmod 755 /home/samba
```

your "phil" shared folder will be created with following permission:
```
mkdir -m 770 /home/samba/phil
chown -R phil:phil /home/samba/phil
```

and on your windows, if you resetted the password, you may want to wipe the windows shares cache:
```
net use * /delete
```


Wait a couple of minutes (windows is slow..) and your shared folder should be accessible ;)


About the oplock and tmp, if your share is opened by more users at the same time and they both are opening/working on a document, say "MS Word", this samba option allows the file to be opened by one user only and cached for as long as the user works on it. Avoiding problems where the file remains "stuck" when one user closed it but still appears as it is still in use.. shortly, this is what.


```
valid users = @phil
force group = phil
```

yes it is correct! best way (IMHO) to allow the user in the share.
Of course if the owner is phil but the whole "finance" department must access, then:

```
valid users = @finance
force group = finance
```


And
```
chown -R root:finance /home/samba/finance
```

_Be careful though_, you used **create mask **twice in your definition, use the **0660** version ;)

---

### Post by Morbius1 on 2017-04-11
> **psking said:**
> 
[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   valid users = @phil
   force group = phil
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/
   create mask = 0770
   directory mask = 0770
[COLOR=#0000cd]Just a note[/COLOR]: You've created a chimera - an odd hybrid between a classic [homes] share which has an implied path ( /home/$USER ) and is by design accessible by only one user and the kind of classic share that          nihvel was suggesting. Your "valid users" in this context is also unconventional since it implies that you have multiple users who are members of "phil"'s primary group. Do you really want multiple users to have access to phil's home directory?
> My Windows username is "phil"
Unless that is also your user name on the Linux box you will have to create that user on the Linux box first so that a /home/phil is created and before you can add him to the samba password database ( smbpasswd ).

---

### Post by nihvel on 2017-04-11
_Morbius1 is 100% right._

On your Linux box (where Samba server is):

**1.** Create the user:
```
useradd phil
passwd phil

```

**2.** Sync it to Samba, no need for the passwords to match:
```
smbpasswd -a phil
```

**3.** Create phil's shared folder:
```

mkdir -p -m 770 /home/samba/phil
chown -R phil:phil /home/samba/phil

```

**4.** Allow everybody to access samba (If you are not using groups to limit the access):
```

chmod 755 /home/samba

```

**5.** Edit your share_ to allow phil only_ to access it:
```

[Phil]
   path = /home/samba/phil
   valid users = phil
   force group = phil
   read only = No
   directory mask = 0770
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/

```

Restart Samba.

On Windows you applied already what I suggested, simply try to enter this share.

[B]In the case you want a group share, where phil and other users have access:
6. [/B]Create the group and add phil:
```
groupdd mygroup
usermod -a -G mygroup phil

```

**7.** Create another folder for this group:
```

mkdir -m 770 /home/samba/mygroup
chown -R root:mygroup /home/samba/mygroup

```

**8.** Add the new share definition in smb.conf:
```

[MyGroup]
   path = /home/samba/mygroup
   valid users = @mygroup
   force group = mygroup
   read only = No
   directory mask = 0770
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/

```

Phil can now access both his share and mygroup.
Phil is the user on Linux, it does not matter which user you are in Windows, you will always use Linux user to access this share (unless you activate other logins methods).

---

### Post by psking on 2017-04-11
Hi both,

Thank you for the addition explanation and steps.  I went through the process of adding a new user "Phil" on the Ubuntu server and then adding as a Samba user and the new section in smb.conf.  However I am still getting access denied.

I should say that both the Windows 10 PC and the Ubuntu server are accessible and used only by myself so security is not really an issue.  I have 3 directories I need to be able to see in Windows, two are data areas mounted from root - /data and /data2 and the other is my home directory where everything else is (/home/psk).  So I think I need to configure this all to work with the user "psk" on Linux since the vast majority of what I need to access is in /home/psk and not /home/phil.  Are you saying that it is not possible for my user "phil" on Windows to access my Linux server via user "psk" ?   This has worked up until recently fairly flawlessly under Windows 10 - maybe an update cause it to fail?

Thanks for your help!

---

### Post by nihvel on 2017-04-12
"phil" is just a name I saw you were using, I also made examples with "Frank". Of course you can use any user you want, just remember to _sync the ubuntu user with samba_, and this is the user that will access your share from windows.

You can create 3 shares definition in smb.conf, one for /home/psk and the other for the data(s), i would suggest you again to use a path that is not /root. The best would be /home/samba/.
Check the permissions on the folders, "others" must be able to execute the folder, which means enter in them.

I too have Samba, on a Ubuntu 14 before and since last month on Ubuntu 16, on 4 diffefent pc with windows 10 (and also at office, through vpn on windows 7).
For _/home/samba/user1_
```
drwxr-xr-**x**   8 root root  4096 Mar 29  2016 home/
...
drwxr-x--**x** 18 root       root       4096 Nov 21 11:01 samba/
...
drwxrwx---   2 user1   user1                  4096 Nov 29 10:29 user1/
```
A view on the permission on one of the shares.

And the samba conf. for this user is:
```
[User1]
        path = /home/samba/user1
        valid users = @user1
        force group = user1
        read only = No
        directory mask = 0770
        force directory mode = 0770
        create mask = 0660
        force create mode = 0660
        write cache size = 2621440
        veto oplock files = /*.tmp/

```
Which is exactly what we've been repeating for the lasts messages. I tend to use the @user instead of @group, which is not 100% correct but it works. Follow my previous post to setup your own user.

It is true that there is nothing else to check. I wonder if your```
[global]
``` section of samba is correct.
I paste here mine:
```
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
        deadtime = 45
        socket options = TCP_NODELAY IPTOS_THROUGHPUT
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        idmap config * : range = 
        idmap config * : backend = tdb
        map acl inherit = Yes
        csc policy = documents
#       interfaces = 192.168.10.0/24 eth1 # is you want to serve samba on a specific interface
#       hosts allow = 192.168.10.0/24 # and specific network

```


It is not a firewall problem, because you are able to get the login window on Windows. Just to complete this whole post for anyone else wanting to setup a share easily, the port to open is the 445.

---

### Post by psking on 2017-04-12
Hi nihvel,

I checked through all of this again, and made some changes to my [Global] section - most of my entries were the same as yours but I added the deadtime, then idmap thro' csc policy entries.

I managed to get this command to work tonight, it failed last night:

smbpasswd -a psk
I have changed all my shares to :

```
[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   valid users = @psk
   force group = psk
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/
   create mask = 0770
   directory mask = 0770




[data]
   comment = Data
   path = /data
   valid users = @psk
   force group = psk
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/
   browseable = yes
   directory mask = 0770
   read only = no


[data2]
   comment = Data2
   path = /data2
   valid users = @psk
   force group = psk
   force directory mode = 0770
   create mask = 0660
   force create mode = 0660
   write cache size = 2621440
   veto oplock files = /*.tmp/
   browseable = yes
   directory mask = 0770
   read only = no
```


After a samba restart and a reboot of my Windows PC, if I double-click my server name in explorer I see the familiar 4 shared directories: data, data2, homes and psk.

data and data2 go away searching for quite a while before coming back with the dreaded \\Servername\data is not accessible.
homes and psk sometimes show a directory listing but if I try to drag and drop a file to Windows desktop I get this strange operation interrupted error and the file doesn't copy.

I am just running the update to 16.04 now, then might roll all the settings back and try again.

Thanks for your patience!

Phil

---

### Post by psking on 2017-04-13
Well, I upgraded to 16.04 overnight and it all works again!

Thanks very very much for you help in resolving this issue.

Phil

---

### Post by nihvel on 2017-04-13
Hi! I started with a fresh 16.04 some weeks ago using my backup of the 14.04 version, and it worked at first try. I was astonished that the same configuration I was using was giving you troubles! But yeah, glad it's solved  now ;)

nb. If "phil" is not a group, and it isn't, you can remove the @ sign from the valid users (I don't bother too much in removing it from mine though)

---

### Post by psking on 2017-04-18
Thanks again nihvel... all still working thankfully!

---

