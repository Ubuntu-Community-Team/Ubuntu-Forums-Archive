---
title: "samba issues"
date: 2012-11-10
forum: Server Platforms
---

### Post by andrewjs18 on 2012-11-10
Hi there,

I was having some issues with samba earlier so I decided to remove it using the following command: sudo apt-get purge samba smbfs

I then reinstalled it using the command: sudo apt-get install samba smbfs

now the /etc/samba directory doesn't exist so I can't modify the config file and add users..  what's going on here?

---

### Post by Morbius1 on 2012-11-10
/etc/samba doesn’t come from the "samba" package:
```
sudo apt-get install samba-common
```There are other "samba" related packages that you may have removed:
samba-common-bin
smbclient

---

### Post by andrewjs18 on 2012-11-10
> **Morbius1 said:**
> /etc/samba doesn&#8217;t come from the "samba" package:
```
sudo apt-get install samba-common
```There are other "samba" related packages that you may have removed:
samba-common-bin
smbclient

ok, I ran apt-get install on all of the packages you mentioned above and apparently they're already installed.

here's what it said for the  samba-common, which was similar for the other two:

```

$ sudo apt-get install samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```/etc/samba is still nonexistent.

---

### Post by Morbius1 on 2012-11-10
Either reinstall samba-common:
```
sudo apt-get --reinstall install samba-common
```Or create a /etc/samba folder and copy the smb.conf file from /usr/share/samba/smb.conf to that folder.

You'll need to make a correction in that file: Find the line:> encrypt passwords = false[COLOR=#0000FF]*Could also be listed as "no"*[/COLOR]

and change it to:
> encrypt passwords = trueThe restart samba:
```
sudo service smbd restart
```

---

### Post by kevinthecomputerguy on 2012-11-10
Here is a long shot
I had a similar issue once with a different package, and running sudo -i fixed it.

Once you run sudo -i, your basically root, instead of just running apt as root.

To recap, run sudo -i

Then do what Morbius1 said, but without the sudo part. Good luck.

---

### Post by andrewjs18 on 2012-11-10
> **Morbius1 said:**
> Either reinstall samba-common:
```
sudo apt-get --reinstall install samba-common
```Or create a /etc/samba folder and copy the smb.conf file from /usr/share/samba/smb.conf to that folder.

You'll need to make a correction in that file: Find the line:[COLOR=#0000FF]*Could also be listed as "no"*[/COLOR]

and change it to:
The restart samba:
```
sudo service smbd restart
```

thank you.

reinstalling samba-common created the /etc/samba directory.  I had to copy the smb.conf file from /usr/share/samba to the /etc/samba directory and modify that line, as you suggested.

---

