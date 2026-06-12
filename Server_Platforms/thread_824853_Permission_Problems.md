---
title: "Permission Problems"
date: 2008-06-10
forum: Server Platforms
---

### Post by SeanDavila on 2008-06-10
Hello,

Im a new user to Ubuntu and linux in general.
I have installed ubuntu server on a computer i have laying around with the intention to use it as a simple file server. 
When prompted durring the install i chose OpenSSH and Samba

using ssh i installed webmin from my desktop.
I can set up shares no problem using the samba plugin in webmin and have read access on both windows and ubuntu computers on my network.

my intention was to use the connect under places in my ubuntu desktop to be able to add and remove files from the shares as needed. Doing that i dont have the permissions to write to the folder. I right click and choose permissions it says owner root and group root with the group only having access permissions


The same issue happens when i attempt to use sshfs using these directions
[http://ubuntuforums.org/showthread.php?t=103860&highlight=ssh+permissions]("http://ubuntuforums.org/showthread.php?t=103860&highlight=ssh+permissions")

ive sepent the last two days in front of google attempting to get this working with no help any suggestions would be most welcome



ssh'ing into the server using my terminal i can gain read and write access to it by 
sudo chmod 777. is this the correct way of doing it?

---

### Post by mbeach on 2008-06-10
I don't think chmod 777 is the best way to go.

I also don't use webmin, so I'm not sure where it's keeping its configuration on the shares.

The gui in Hardy seems to store some stuff in:
/var/lib/samba/usershares

but typically I'm used to using 
/etc/samba/smb.conf

When you ssh into your server, and do an "ls -la" on the folder, which should list the folder, along with the owner, make note of the owner.  If it's root, then perhaps I'd question why that folder is being shared, otherwise, create a folder as a less privileged user in their home directory and share it.  Then I'd suggest editing the appropriate section of 
/etc/samba/smb.conf 
likely toward the very end for that particular folder.

For example you might use:
```

[mysharename]
path = /home/myuser/shared
available = yes
browseable = yes
public = yes
writeable = yes
create mask = 0755
directory mask = 0755
force group = thenameofgroup
force user = thenameoftheUserFromPreviousDirectoryListing

```

I ssh to the server, and use vi to edit these types of files, but not knowing how you've got things hooked up, all I can say is to 'edit' that file.  Do you have access to the desktop at all, or is this machine completely headless.  If you installed the desktop version, I'd turn on remote desktop and use vnc to connect to it for a graphical editor.

restart samba after making configuration changes with
sudo /etc/init.d/samba restart

---

### Post by molotov00 on 2008-06-10
On the surface I don't think your issue is samba related. It's a filesystem file permission issue.

You haven't given enough information about the number of users on the system. If there are multiple users who have access to multiple folders then using chown would be helpful.

If there's one user:
 - either configure Samba to let you log in as that user, then you'll be able to have the same file permissions (read/write) as if you log in via ssh.
 - and you are not 'logging in' to the share from Windows, (i.e. you're a guest as far as Samba is concerned) then you should chmod 777. But realize that anyone on your network can read/write.

Hope that helps. If you want specific advice then we need the Samba config file and more info about the folders and users.

---

### Post by hyper_ch on 2008-06-11
try:

```

sshfs user@remote:/path/to/remote/dir /path/to/local/dir -o uid=xxx -o gid=yyy

```

xxx = userid that owns the remote folder
yyy = groupip that owns the remote folder

---

