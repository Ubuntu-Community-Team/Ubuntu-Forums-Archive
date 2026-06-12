---
title: "Permissions"
date: 2012-10-23
forum: Server Platforms
---

### Post by carolinaed on 2012-10-23
New installation of Ubuntu Server for the sole purpose of running a company web site. 12.0.4.1 LTS. Standard LAMP installation so all is up and working.

Webmin is installed and within Webmin, created a user 'atlas' that has a home directory of /var/www and a group of FTP, that atlas is a member of. They are the company doing the site development. Can successfully log into the site using FTP with the user and defined password. I just can't upload files or create subdirectories as that user.

The permissions on the folder are:
drwxr-xr-x ftp root 4096 Oct 22 14:40 www

So, the user FTP (created from Webmin, I guess) is the only user with Write access on that WWW directory, right? That user is a member of root, and I don't want to make 'atlas' a member of root.

Checked into chmod command and can't figure out how to give either 'atlas' or the group 'ftp' write permissions on that directory. Would think this would be fairly simple as it is on Windows server, but so far, it has eluded me.

Any help would be greatly appreciated.

---

### Post by cool110 on 2012-10-23
To change a file/folder's owner and group you need to use chown e.g.
```
sudo chown atlas:ftp www
```
This will change the owner of www to atlas and the group to ftp.

---

### Post by carolinaed on 2012-10-24
Any way to just add the group 'ftp' to have write access?

---

### Post by Wim Sturkenboom on 2012-10-24
> **carolinaed said:**
> 
The permissions on the folder are:
drwxr-xr-x ftp root 4096 Oct 22 14:40 www

So, the user FTP (created from Webmin, I guess) is the only user with Write access on that WWW directory, right? **That user is a member of root, and I don't want to make 'atlas' a member of root.**

No, that user is NOT a member of root. So it's safe to make the folder owner 'atlas' as suggested in an earlier post.

The alternative is to use acl

```

setfacl -m u:atlas:rwx /var/www

```
This will keep the normal permissions and additionally grants the user 'atlas' rwx permissions.

As this website design company has no business whatsoever on your system, so make sure that they can't do anything outside /var/www. Disable their shell login if necessary and jail them to their home directory.

---

### Post by Lars Noodén on 2012-10-24
> **Wim Sturkenboom said:**
> The alternative is to use acl

```

setfacl -m u:atlas:rwx /var/www

```

Is there a way to make newly created directories within /var/www inherit the ACL settings automatically?

---

### Post by carolinaed on 2012-10-24
> **Wim Sturkenboom said:**
> As this website design company has no business whatsoever on your system, so make sure that they can't do anything outside /var/www. Disable their shell login if necessary and jail them to their home directory.

Would the ACL you provided accomplish this task?

---

### Post by carolinaed on 2012-10-24
For testing purposes, I ran the ```
chown atlas:ftp www
```and tested using a FTP client. Wasn't able to get connected. Changed it back to what it originally was, and could. However, back to the original problem of not being able to upload files or add directories as that user.

---

### Post by carolinaed on 2012-10-24
Got it working.

Insured that my user 'atlas' was a member of the group ftp in the /etc/group file.

Then I ran these.
```

cd /var
chown ftp:ftp www
chmod g+w

```

Ran a ls -l after that to check permissions and had:
drwxrwxr-x ftp ftp www

Tested and I was able to create my directories as atlas in the www folder. If what I have done is sufficiently secure, let me know please as I don't want to have inadvertently created an unnecessary risk.

Thanks for all the responses.
Ed

---

### Post by Wim Sturkenboom on 2012-10-24
> **Lars Noodén said:**
> Is there a way to make newly created directories within /var/www inherit the ACL settings automatically?

I don't know too much about acl, but after some 'trial and error' there seems to be ;)

```

wim@VirtualBox:~/website1/www$ setfacl -m u:testuser:rwx ../www
wim@VirtualBox:~/website1/www$ getfacl ../www
# file: ../www
# owner: wim
# group: wim
user::rwx
user:testuser:rwx
group::rwx
mask::rwx
other::r-x

```

Test if acl is inherited by creating a new directory
```

wim@VirtualBox:~/website1/www$ mkdir aftersetfacl
wim@VirtualBox:~/website1/www$ getfacl aftersetfacl/
# file: aftersetfacl/
# owner: wim
# group: wim
user::rwx
group::rwx
other::r-x

```
It's not inherited

Make current acl default (based on the example in the man page for setfacl)
```

wim@VirtualBox:~/website1/www$ getfacl --access ../www | setfacl -d -M- ../www

```

And test it by creating another directory
```

wim@VirtualBox:~/website1/www$ mkdir aftersetfacl2
wim@VirtualBox:~/website1/www$ getfacl aftersetfacl2/
# file: aftersetfacl2/
# owner: wim
# group: wim
user::rwx
user:testuser:rwx
group::rwx
mask::rwx
other::r-x
default:user::rwx
default:user:testuser:rwx
default:group::rwx
default:mask::rwx
default:other::r-x

```
And it seems to be inherited.

Please note that anything in www inherits, subdirectories of subdirectories of .... as well as files.

---

### Post by Lars Noodén on 2012-10-24
> **Wim Sturkenboom said:**
> 
Make current acl default (based on the example in the man page for setfacl)
```

wim@VirtualBox:~/website1/www$ getfacl --access ../www | setfacl -d -M- ../www

```

Thanks.  I guess there can only be one default at a time.

---

### Post by Wim Sturkenboom on 2012-10-25
I guess so too. After all, what is the meaning of the word 'default' ;)

---

### Post by koenn on 2012-10-25
> **Lars Noodén said:**
> I guess there can only be one default at a time.

IIRC you can have several defaults.

I looked into acl a couple years back, in an exercise of "can I replace a windows file server by samba" and one of the things you then have to solve is "can I get all of these (Domain) group permissions to propagate to newly created subdirs and files."
That seemed to work by setting multiple defaults.

Notes;
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by Wim Sturkenboom on 2012-10-26
I think that that becomes a word game about what 'default' exactly means.

---

