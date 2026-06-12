---
title: "W7 &gt; Samba &gt; USE 10.04.2 Won't Connect"
date: 2011-07-01
forum: Server Platforms
---

### Post by takisan on 2011-07-01
Alright, here goes. I'm trying to connect to my [homes] share on my downstairs computer, and it won't connect; Credentials refused.

And just so I don't have people asking for this later:

Laptop:
[list]
[*]Windows 7 Home Premium
[/list]

Server:
[list]
[*]Named *John* on the network (no, my name isn't John)
[*]Fresh install of Ubuntu Server 10.04.2
[*]*sudo apt-get install samba*
[/list]

Here's my smb.conf file.
```
[global]
workgroup = JWG
netbios name = John--Samba
encrypt passwords = yes

[homes]
read only = no
browseable = no
```

And if you're going to ask, I do *not* want to set it up as a domain controller just yet.

Thanks in advance for the help.

---

### Post by pawhtiobo on 2011-07-01
Hi, 

You can always set the security to "share" instead of "user" or if you dont want any passwords to access the share, just add the "guest ok = yes" option.

Check this:

[http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto)

See ya...

---

### Post by Morbius1 on 2011-07-01
You did create users with home directories and set samba passwords for those users right?

---

### Post by Morbius1 on 2011-07-01
> **pawhtiobo said:**
> You can always set the security to "share" instead of "user" or if you dont want any passwords to access the share, just add the "guest ok = yes" option.
I wouldn't advise using either share level security or allowing guests to a [homes] share. 

A "homes" share is a special share definition that creates a share "on the fly" when asked to do so by the client. The whole point of it is to create a place on the server for just that specific user to access. It has 2 requirements:

* There's a /home/$USER for the remote user to access.
* There's a samba password for that user.

---

### Post by capscrew on 2011-07-01
> **Morbius1 said:**
> I wouldn't advise using either share level security or allowing guests to a [homes] share. 

A "homes" share is a special share definition that creates a share "on the fly" when asked to do so by the client. The whole point of it is to create a place on the server for just that specific user to access. It has 2 requirements:

* There's a /home/$USER for the remote user to access.
* There's a samba password for that user.

Respectfully Morbius1; this is not exactly correct.  From the Samba documentaition:```
    * If no path was given, the path is set to the user's home directory. 

If you decide to use a path = line in your [homes] section, it may 
be useful to use the %S macro. For example:  path = /data/pchome/%S

```
See [**_[COLOR="DimGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") (under [homes]) for the complete info.

My users [homes] directory is at: /srv/smb/home/%S

I do agree that the OP should not use *share* level security.  I believe the default is now *user* level anyway.

---

### Post by CharlesA on 2011-07-01
Did you add your users with:

```
sudo smbpasswd -a user
```

---

