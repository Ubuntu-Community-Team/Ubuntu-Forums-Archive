---
title: "Ubuntu server LAMP files access"
date: 2013-10-18
forum: Server Platforms
---

### Post by Peter_Darbyshire on 2013-10-18
I have successfully set up a LAMP server and it is working as it should

But my question is what is the best way to access and save to the /var/www folder

Where i work is a windows based environment so if possible i would need to be map the /var/www folder and be able to open documents to edit and save straight back to the /var/www folder.

Thank you

---

### Post by Lars Noodén on 2013-10-18
If you are the only one using that machine you can [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1posix.html) it to give write permission to your acount.

About getting remote access from legacy systems you could try connecting using SSHFS.  That works via SFTP invisibly and has clients for many systems.  On the server side, you only need OpenSSH-server runnng.  That has the advantage of working even over the Internet.  

Otherwise, you might look at NFS or Samba, if you plan to only connect over the LAN.

---

### Post by bab1 on 2013-10-18
> **Peter_Darbyshire]
...my question is what is the best way to access and save to the /var/www folder
[/QUOTE]
To access the folder directly you can use Putty.  This will give you SSH access to the Ubuntu host.  You need to have the SSH server running on Ubuntu.  This is terminal access only.  You are logging in directly using an ssh encrypted tunnel.  From here you can set the proper permissions for you to access the directory and modify the files.
> 
Where i work is a windows based environment so if possible i would need to be map the /var/www folder and be able to open documents to edit and save straight back to the /var/www folder.
You can use the ssh equivalent of FTP.  This is called SFTP.  The free Windows client it called WinSCP.  It looks and acts just like a graphical FTP client.


[QUOTE=Lars Noodén said:**
> If you are the only one using that machine you can [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1posix.html) it to give write permission to your acount.

After the OP has access to the machine remotely I would assume; right? 
> 
About getting remote access from legacy systems you could try connecting using SSHFS.  That works via SFTP invisibly and has clients for many systems.  On the server side, you only need OpenSSH-server runnng.  That has the advantage of working even over the Internet.  

Otherwise, you might look at NFS or Samba, if you plan to only connect over the LAN.
Windows has problems with NFS and Samba is a mess unless you are on the same sbnet.  Samba is inferior to the SSHFS or SFTP solutions I would think.

---

### Post by Lars Noodén on 2013-10-18
> **bab1 said:**
> ...After the OP has access to the machine remotely I would assume; right? 

Windows has problems with NFS and Samba is a mess unless you are on the same sbnet.  Samba is inferior to the SSHFS or SFTP solutions I would think.

The chown needs to take place only once and can be done any time prior to when you actually need those directories.  

For most things I would use, SSHFS is superios to Samba or NFS.  In particular, I like the fact that you can connect securely from anywhere on the Internet not just on the same LAN.

---

### Post by SeijiSensei on 2013-10-18
If you are trying to enable multiple authors using Windows machines on your local network to post files to the server, then I would use Samba with the "force user" and "force group" directives.  In smb.conf, you would have:

```

[website]
path = /var/www
force user = www-data
force group = authors
create mask = 0460
{more stuff}

```

This creates files that are owned by the www-data user which is the username under which the Apache server is running.  Place all the authors into the authors group.  The create mask says that www-data can read the files, but only members of the authors group can write them.

---

### Post by bab1 on 2013-10-18
> **SeijiSensei said:**
> I... Place all the authors into the authors group.  The create mask says that www-data can read the files, but only members of the authors group can write them.
Set the sgid bit (with chmod) so the group inheritance is in effect too.

---

### Post by Peter_Darbyshire on 2013-10-21
> **SeijiSensei said:**
> If you are trying to enable multiple authors using Windows machines on your local network to post files to the server, then I would use Samba with the "force user" and "force group" directives.  In smb.conf, you would have:

```

[website]
path = /var/www
force user = www-data
force group = authors
create mask = 0460
{more stuff}

```

This creates files that are owned by the www-data user which is the username under which the Apache server is running.  Place all the authors into the authors group.  The create mask says that www-data can read the files, but only members of the authors group can write them.

I have setup the server when it asked for a username i choose administrator. I want the administrator account and just one other account full access to these files.

Would i create a new group called authors as you suggested.. would i have to run any commands to give the authors group full access to the files?

---

### Post by SeijiSensei on 2013-10-22
If you have more than one person who can own the files, you'll need to create a group to do this securely.  Otherwise you would need to allow anyone to write files there, which you clearly do not want.  

Another alternative, which I have used, is to create a user who owns the website, say "web", and create a Samba login for that user.  Then give everyone who needs to edit the files the password for the web user.  For example,

```

[website]
       comment = Our Website
        browseable = yes
        writable = yes
        path = /var/www
        valid users = web

```

You'd need to change the ownership of /var/www to match the username you set up.

The smb.conf file also offers this template for a shared directory that you could modify to fit your needs:

```

# A publicly accessible directory, but read only, except for people in
# the "staff" group
;       [public]
;       comment = Public Stuff
;       path = /home/samba
;       public = yes
;       writable = yes
;       printable = no
;       write list = +staff

```

---

