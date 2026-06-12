---
title: "Ubuntu file server with Samba in Windows Active Directory network"
date: 2009-05-20
forum: Server Platforms
---

### Post by NyteWyyrm on 2009-05-20
I realize that there are numerous posts around this topic but I just can't seem to be able to pull together everything I am looking to accomplish.  I am hoping for some insight and help.

I have a Windows network (Server 2003 mostly) setup with the Active Directory to control user logins.  I am trying to slowly introduce Linux (Ubuntu preferred) into my network to take up jobs that do not require Windows.  My first step was a LAMP server for our intranet and that has met with good success so far.  My second is a File Server.  

So here is where I'm at so far:  I have a server up and installed with likewise-open, Samba, AMP (for supporting the main intranet) and configured with the static IP structure.  I have managed to integrate the Ubuntu server with the Active Directory and DNS.  I am even able to log in to the Ubuntu server using my Windows account.  Next step was to build the file share.  I was able to share a folder to the Windows network with no user security, but I have not been able to share a folder using any method of security.  I think my problem is a lack of understanding of the Samba authentication configurations.

Ultimately, is it even possible and can anyone help me configure.  I would like to set user/group permissions on Ubuntu folders so that Windows users can access them.  I would prefer an integrated 'single sign-on' approach.  In lieu of that, is there another method to achieve a Linux file server in a Windows environment?  The most important part to this may be in making the fact that the file server is Linux "invisible" to the users but providing security that prevents users from accessing shares they are not authorized to access.  The users obviously don't care what their file server is, as long as it performs in a manner to which they are currently accustomed to.

Sorry for the long post and thanks in advance for any help.

---

### Post by wolfteeth on 2009-05-20
May I know how you realize the feature for : "I am even able to log in to the Ubuntu server using my Windows account"

how can you login Ubuntu via Windows account? do you mean GUI or just SSH? could you provide some more details?

thanks.

---

### Post by BadBoy4Live on 2009-05-20
> **wolfteeth said:**
> May I know how you realize the feature for : "I am even able to log in to the Ubuntu server using my Windows account"

how can you login Ubuntu via Windows account? do you mean GUI or just SSH? could you provide some more details?

thanks.

He realised that feature with likewise-open, its a package wich you can install on your ubuntu pc and can use to join the domein as a client PC. use

```

sudo apt-get install likewise-open

```
And wolfteeth, to make shares invisible to users you can use

```

[sharename]
path = /....
browseable = no

```To the permission problem i got a solution, 

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

This manual makes your ubuntu machine join the domain. If you followed all the steps, you should be able to grant windows users and groups permissions on the share.

Hope this helps

Greetz,
BadBoy4Live

---

### Post by NyteWyyrm on 2009-05-20
BadBoy4Live:  Thanks for the post.  Very helpful.  It got me almost all the way there.  Now I am able to share out a folder and when a user creates their own folder, Linux recognizes the username and a group.  It doesn't quite seem to recognize the correct group, I don't think.  

In general, I'm still a little unfamiliar with the Samba permissions and Linux permissions precedences.  I tried setting a valid user and write only in smb.conf, but it didn't seem to restrict any access.  I will keep poking around, but I appreciate any help I can get.

If I can get this to work how I envision it will, I'll post back a small HowTo on what I did.  Hopefully it'll provide a good base for anybody else in this situation.

And yes, I did use the likewise-open package for ADS integration.  That part went rather smoothly.  Again, I'll include some documentation in another post here soon . . .

---

### Post by BadBoy4Live on 2009-05-21
Ok i'm glad to hear that it helped. beneath you will see a example of my smb.conf

```

[global]

security = ads
realm = AMSTERDAM.NL
password server = 192.168.0.1
workgroup = AMSTERDAM
winbind separator = \
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
winbind use default domain = yes
restrict anonymous = 2
**acl map full control = yes**
server string = FILESERVER AMSTERDAM
netbios name = FILESERVER


[HOME]

path = /FILES/AMSTERDAM/HOME
comment = Home Share
directory mask = 0700
create mode = 0700
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = yes
printable = no
share modes = no
locking = no
force create mode = 0700
force directory mode = 0700
**nt acl support = yes**

# bold parts only work after enabeling ACL on the filesystem, look beneath

```Permission on my share used for roaming profiles:
/FILES 770
/FILES/AMSTERDAM 770
/FILES/AMSTERDAM/Home 770

now about the permissions, there is a way to enable a feature on linux wich gives you the chance to change permissions from windows on linux directories. This is ACL's. Beneath a link to a good manual.

[http://aisalen.wordpress.com/2007/08/10/acls-on-samba/](http://aisalen.wordpress.com/2007/08/10/acls-on-samba/)

You also say that the right group is not shown, try the next command to see if your ubuntu machine actualy sees the groups

```

wbinfo -g

```

---

### Post by frenchn00b on 2010-01-25
> **BadBoy4Live said:**
> Ok i'm glad to hear that it helped. beneath you will see a example of my smb.conf

```

[global]

security = ads
realm = AMSTERDAM.NL
password server = 192.168.0.1
workgroup = AMSTERDAM
winbind separator = \
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
winbind use default domain = yes
restrict anonymous = 2
**acl map full control = yes**
server string = FILESERVER AMSTERDAM
netbios name = FILESERVER


[HOME]

path = /FILES/AMSTERDAM/HOME
comment = Home Share
directory mask = 0700
create mode = 0700
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = yes
printable = no
share modes = no
locking = no
force create mode = 0700
force directory mode = 0700
**nt acl support = yes**

# bold parts only work after enabeling ACL on the filesystem, look beneath

```Permission on my share used for roaming profiles:
/FILES 770
/FILES/AMSTERDAM 770
/FILES/AMSTERDAM/Home 770

now about the permissions, there is a way to enable a feature on linux wich gives you the chance to change permissions from windows on linux directories. This is ACL's. Beneath a link to a good manual.

[http://aisalen.wordpress.com/2007/08/10/acls-on-samba/](http://aisalen.wordpress.com/2007/08/10/acls-on-samba/)

You also say that the right group is not shown, try the next command to see if your ubuntu machine actualy sees the groups

```

wbinfo -g

```

hello, 

are we obliged to use windbind?

just changing smb.conf?

here is my example on the client of smb.conf:
```

[global]
   guest account = nobody
   invalid users = root
   encrypt passwords = yes
   security = server
   password server = 192.168.10.100   #server
   workgroup = WORKGROUP
   server string = %h server (Samba %v)
   preserve case = yes
   short preserve case = yes
   unix password sync = yes

[homes]
  comment = Home Directories
  read only = No
  create mask = 0700
  directory mask = 0700
  browseable = no




```

---

