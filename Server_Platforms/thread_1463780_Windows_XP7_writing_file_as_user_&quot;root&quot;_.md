---
title: "Windows XP/7 writing file as user &quot;root&quot; on Samba"
date: 2010-04-27
forum: Server Platforms
---

### Post by narsaw on 2010-04-27
I have several windows XP/7 machines on my LAN. I also have Ubuntu server running Samba for file sharing. All XP/7 computers can access (read/write) to the file server without problems.

However, I noticed that when Windows XP/7 writes a write to a Samba share on my Ubuntu server it's written with the following ownership iformation.

```
-rwxrw----  1 root     users
```

On my Windows machines my username is "mharris" and I am logged in as an "Administrator". I suspect this is where the problem is.

On my ubuntu server, my username is "mharris" and I belong to the "users" group.

What I want is when I write a file from Windows to Samba the ownership info should look like:
```
rw-rw-r--  1 mharris    users
```

I would seem like some form of mapping might be appropriate. I have read Chapter 12 ( and others) of the Samba users guide but still cannot figure it out.

Can some explain to me how to do this?

---

### Post by arrrghhh on 2010-04-27
> **narsaw said:**
> I have several windows XP/7 machines on my LAN. I also have Ubuntu server running Samba for file sharing. All XP/7 computers can access (read/write) to the file server without problems.

However, I noticed that when Windows XP/7 writes a write to a Samba share on my Ubuntu server it's written with the following ownership iformation.

```
-rwxrw----  1 root     users
```

On my Windows machines my username is "mharris" and I am logged in as an "Administrator". I suspect this is where the problem is.

On my ubuntu server, my username is "mharris" and I belong to the "users" group.

What I want is when I write a file from Windows to Samba the ownership info should look like:
```
rw-rw-r--  1 mharris    users
```

I would seem like some form of mapping might be appropriate. I have read Chapter 12 ( and others) of the Samba users guide but still cannot figure it out.

Can some explain to me how to do this?

I think it actually relates to the mask you have on your samba conf file, not which user you're using from Windows.

Let me see if I can dig up an answer for ya...

I'd read over the official [Samba Guide](https://help.ubuntu.com/community/SettingUpSamba) for Ubuntu.  If you're still stuck, we can look at your conf file more closely.

---

### Post by narsaw on 2010-04-27
Thanks for the reply...

Very simple smb.conf as seen below:

```

[global]

workgroup = WORKGROUP
netbios name = networkserver
interfaces = eth1 lo
bind interfaces only = yes
security = user

[NETWORK MEDIA]

path=/media/netdisk/networkshare/media
browseable=yes
writeable=yes
users = mharris,jharris
admin users = mharris.jharris

```

I have a file called **smbusers **in /etc/samba/ that has the following in it. But I dont see any references to this file in smb.conf

```

root = Administrator

```

---

### Post by arrrghhh on 2010-04-27
I believe you have to setup the smbusers... Did the guide not mention that?

---

### Post by narsaw on 2010-04-27
> **arrrghhh said:**
> I believe you have to setup the smbusers... Did the guide not mention that?

No mention of smbusers.

My smb.conf does not reference this file, it samba loading it behind the scenes? If so, what should it look like:

```

root = Administrator
mharris = mharris

```

??

PS: This samba server is setup just for file sharing, not looking for some fancy domain login, etc.

---

### Post by arrrghhh on 2010-04-27
So you did this part?

```
Add users who can access your shares with the 'smbpasswd' command.
```

---

### Post by narsaw on 2010-04-27
> **arrrghhh said:**
> So you did this part?

```
Add users who can access your shares with the 'smbpasswd' command.
```

Yes I did do that:

Contents for smbpasswd file:

```

mharris:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:9458940FD24A6798075EB5F26D8A0C77B5:[U          ]:LCT-4BD77525:

```

---

### Post by narsaw on 2010-04-27
I can verify that this only happens on Windows XP/7 machines. From my wife's macbook (running Leopard), files created with that machines are owned appropriately on my samba server.

I tried creating a "standard" account in Windows 7, but same problem, files are owner by root.

---

### Post by capscrew on 2010-04-28
> **narsaw said:**
> I have several windows XP/7 machines on my LAN. I also have Ubuntu server running Samba for file sharing. All XP/7 computers can access (read/write) to the file server without problems.

However, I noticed that when Windows XP/7 writes a write to a Samba share on my Ubuntu server it's written with the following ownership iformation.

```
-rwxrw----  1 root     users
```


I have read the entire thread.  I think there are concepts that are unclear.  My comments are not meant to be chiding and all the pieces will fit together in the end.  With that being said, let me comment as it is needed.  

> 

On my Windows machines my username is "mharris" and I am logged in as an "Administrator". I suspect this is where the problem is.


Think of it as you have an account named "mharris" and an account  named Administrator".  They are to different accounts and the login/password ***authenticates ***you and which account you are using.
> 

On my ubuntu server, my username is "mharris" and I belong to the "users" group.

The account has many user groups and you can add more.
> 

What I want is when I write a file from Windows to Samba the ownership info should look like:
```
rw-rw-r--  1 mharris    users
```

This is doable.  But there are many pieces to the puzzle.
> 

I would seem like some form of mapping might be appropriate. I have read Chapter 12 ( and others) of the Samba users guide but still cannot figure it out.
It is not really mapping that is needed.  Can you provide a URL for the users guide?  That way way will be on the same page.> 
Can some explain to me how to do this?

When you are logged in to a Windows (or Linux) host and you connect to a share, that login information is seen by Samba (and if setup, your keyring).  The share will "authenticate" you based on your client login or if it can't, it will treat you as a guest.

From here on you are "authorized" to do what the underlaying file systems permissions allow you to do.  This will mean that you will have to control the group primarily rather than the user individually.

I use a group specifically for samba users (named *[COLOR="Blue"]smbusers[/COLOR]*). 

The first thing is to configure smb.conf correctly.  The parameter is "force group"

This means anybody that has an Samba user account (via smbpasswd) will also create files with the group "smbusers".

I used create mode to set the permissions.  The parameter is "create mode = 0775"  I actually go one step further and force the uid/gid to be permanent with extended chmod (some call this sticky bit).  This insures that your file can't be deleted by someone else with group rights to do so.  My create mode is 3775

Now all you need to so is set the group (chgrp) on the directory that is the root of you Samba share.

Here are some examples.  The directory might look like this:```

drwxrwsr-t  4 root   smbusers 4.0K 2008-10-30 00:23 share

``` 
Note the permissions at the far left the s and the t are the sticky bits.

The directories inside would look like this```

drwxr-sr-x 15 bill smbusers 4.0K 2010-01-05 07:14 bill
drwxr-sr-x  2 john smbusers 4.0K 2008-10-30 10:59 john
drwxr-sr-x  2 lilly smbusers 4.0K 2009-09-15 10:59 lilly
bruce@rincon:/smb/home>

```
Once again note the permissions.

Here are some pictures for bills directory (folder)
```

-rwxr--r-- 1 bill smbusers 211K 2007-09-17 11:27 anemones.jpg
-rwxr--r-- 1 bill smbusers 610K 2007-08-19 21:20 archipelago.jpg
-rwxr--r-- 1 bill smbusers 382K 2007-08-19 21:20 desertsnow.jpg
-rwxr--r-- 1 bill smbusers 202K 2007-08-20 10:23 haiku.jpg
-rwxr--r-- 1 bill smbusers 2.9M 2007-09-17 12:48 Jelly.bmp
-rwxr--r-- 1 bill smbusers 219K 2005-05-26 16:58 ripples.jpg
-rwxr--r-- 1 bill smbusers 852K 2007-09-14 18:04 sakura.jpg
-rwxr--r-- 1 bill smbusers 480K 2007-09-17 11:28 satori.jpg
-rwxr--r-- 1 bill smbusers 150K 2000-03-05 17:37 sierramoon.jpg

```

Here is the pertinent parts of the /etc/samba/conf file.

The [global] section could contain
```

#  Bad user means "user not found in unix passwd" and
#  we will default to the guest accout that we have defined
        map to guest = bad user
        guest account = smbguest

```

And the share definition looks like this```

[Share]
        comment = Public Share
        path = /smb/share
        browseable = yes
        force group = smbusers

        guest ok = yes
        writeable = yes
        create mask = 0775
        force create mode = 3775
        directory mask = 3775

```

---

### Post by capscrew on 2010-04-28
> **narsaw said:**
> I can verify that this only happens on Windows XP/7 machines. From my wife's macbook (running Leopard), files created with that machines are owned appropriately on my samba server.

I tried creating a "standard" account in Windows 7, but same problem, files are owner by root.
Show us the whole smb.conf file and the directory structure.

---

