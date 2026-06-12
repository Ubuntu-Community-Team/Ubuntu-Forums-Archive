---
title: "Linux  and SAMBA user password"
date: 2013-02-13
forum: Server Platforms
---

### Post by SAngeli on 2013-02-13
Hi,
I run a ubuntu server with samba running for accessing from a Windows 7 stand alone PC some shares.

I know I have to create a linux user first.
Than, I have to add a linux user to the samba database
Last, I have to assign a samba password to the user.

The problem is that from windows when i try to access the share it only works using the linux password and not the samba one.

What is that I do wrong?
Is it possible to have this scenario working?
User A has administrtive priviledges and has password "abc"
User A is added to SAMBA
User A Samba password is "def"

I wish to access from windows this way:
UserName: A
Password: def

Can this be done?

Also, I forgot: how to assign a linux user admin priviledges and how to verify of this? I believe there should be a file for usres.

Thanks,
Spiro

---

### Post by ranger12 on 2013-02-13
What version of samba are you using?  Did you use -a with smbpasswd? The first time you add a new samba user to the database you have to use -a. 

sudo smbpasswd -a <user>

---

### Post by schragge on 2013-02-13
> **SAngeli said:**
> how to assign a linux user admin priviledges and how to verify of this?
```
sudo adduser [color=green]username[/color] sudo
```Or do you mean Samba domain administrator?

---

### Post by Morbius1 on 2013-02-13
> The problem is that from windows when i try to access the share it only works using the linux password and not the samba one.

What is that I do wrong?
Is it possible to have this scenario working?
User A has administrtive priviledges and has password "abc"
User A is added to SAMBA
User A Samba password is "def"The only thing I can think of that would explain all of those symptoms is if you have the following package installed: 
```
libpam-smbpass
```It has only one function in life and that is to force the samba password to equal the user's linux login password and not the one you set with smbpasswd. It's safe to remove the package if you have it installed.

---

### Post by Doug S on 2013-02-13
Just F.Y.I.: During installation of Ubuntu server edition, if one selects the "Samba Server" task during the select stuff phase of the installation, then libpam-sampass will be installed.
Reference: [https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html#samba-user-security](https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html#samba-user-security)

---

### Post by SAngeli on 2013-02-14
Hi,

yes, I have **libpam-smbpass** package installed.
```
Package: libpam-smbpass
Architecture: amd64
Source: samba
Version: 2:3.6.3-2ubuntu2.3
Depends: libc6 (>= 2.15), libcap2 (>= 2.10), libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libwbclient0 (>= 2:3.6.0~pre3), samba-common (= 2:3.6.3-2ubuntu2.3), libpam-runtime (>= 1.0.1-6)
Suggests: samba
Conffiles:
 /etc/logcheck/ignore.d.server/libpam-smbpass 9556182e52651dbf9682804c536ac543
Description: pluggable authentication module for Samba
 This is a module for PAM that enables a system administrator to migrate
 user passwords from the Unix password database to the SMB password
 database as used by Samba, and to subsequently keep the two databases in
 sync.  Unlike other solutions, it does this without needing users to log
 in to Samba using cleartext passwords, or requiring them to change their
 existing passwords.

```

I do not remember if the first time I added the user to samba I used the "-a" switch. Should I remove it from samba and add it again witht he "-a" switch?

Thank you,
Spiro

---

### Post by Morbius1 on 2013-02-14
If you want to have a samba password that is different from the login password then you have to remove libpam-smbpass.

Any yes you need to reset the samba pasword again:
```
sudo smbpasswd -a user-name
```

---

### Post by ranger12 on 2013-02-14
If you look in the man page for smbpasswd, it gives a good explanation of the -a switch and when it should be used.

---

### Post by SAngeli on 2013-02-15
Yes,
I confirm that I was able to solve this issue by removing libpam-smbpass package.

I also confirm that I used, in the past the "-a" switch otherwhise it would have not created the user.

So, this case is solved.
Thank you,
Spiro

---

### Post by brent1975 on 2013-02-15
Dont forget

```
sudo smbpasswd -e your-user-name
```
after you run
```
sudo smbpasswd -a your-user-name
```

---

### Post by ranger12 on 2013-02-15
This is taken straight from the man page concerning the -e switch:

-e
           This option specifies that the username following should be enabled
           in the local smbpasswd file,[B] if the account was previously
           disabled[/B]. If the account was not disabled this option has no
           effect. Once the account is enabled then the user will be able to
           authenticate via SMB once again.

When you add a new user to the smbpasswd file, the account is enabled by default. So running it with the -e switch would have no effect.

---

### Post by brent1975 on 2013-02-15
> **ranger12 said:**
> This is taken straight from the man page concerning the -e switch:

-e
           This option specifies that the username following should be enabled
           in the local smbpasswd file,[B] if the account was previously
           disabled[/B]. If the account was not disabled this option has no
           effect. Once the account is enabled then the user will be able to
           authenticate via SMB once again.

When you add a new user to the smbpasswd file, the account is enabled by default. So running it with the -e switch would have no effect.

I guess I was wrong, for some reason I thought -e was to enable the account. I wasn't aware it was for previous disabled accounts.

---

### Post by ranger12 on 2013-02-15
A lot of good info in those man pages.

---

