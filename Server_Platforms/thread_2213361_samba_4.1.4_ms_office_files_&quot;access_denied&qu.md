---
title: "samba 4.1.4 ms office files &quot;access denied&quot;"
date: 2014-03-26
forum: Server Platforms
---

### Post by tadewosa on 2014-03-26
I've managed to install and configure samba 4.1.4 on Ubuntu 12.04 server.
10 Users are created and full permissions are given to users to different folders.
Each user is assigned to groups, some users are members of 2 or more groups
and some are members of only one group.
But there is a problem in accessing ms office documents word and excel.
The folder in which this office documents are found, is so configured that a definite user or group
has a full access.
When a user attempts to open this documents he/she gets "access denied" message.
Sometimes a user can open a word or excel document for the first time, make changes and cab save.
But when he/she tries to open the second time he/she gets the same "access denied" message for this file.
There is no such problem with other files except ms office documents.
Can any one help?
Background:
All files were on windows machine. After installing and configuring the ubuntu server and samba4, files were
transferred to the corresponding folders (with admin account) on the linux machine.
What makes this problem very peculiar is that not all ms-office files have this error message but some files.
But all files were originally accesseble for every one, when they were on windows machine.
Client machines are windows 8 pro.
thank you

---

### Post by lingpanda on 2014-03-26
How did you assign the groups? Did you use computer management tool on windows or in the smb.conf file? I've had this problem when not setting the ACL correctly.

---

### Post by tadewosa on 2014-03-26
I used samba-tool to assign users to groups. For some users I used Remote Server Administration Tools - Active Directory Users and Computers.

[h=1][/h]

---

### Post by lingpanda on 2014-03-27
> **tadewosa said:**
> I used samba-tool to assign users to groups. For some users I used Remote Server Administration Tools - Active Directory Users and Computers.



Make sure you follow this guide to set the ACL's for your users. [https://wiki.samba.org/index.php/Setup_and_configure_file_shares](https://wiki.samba.org/index.php/Setup_and_configure_file_shares)

---

### Post by tadewosa on 2014-03-27
thank you for your reply. It is just this guide that I used when I sett up shares. Except "ACL support on member server" I followed exactly as described there.
The only thing that I am not sure with the correctness of my configuration is editing "/etc/fstab".
It seems that I need a good knowledge of editing fstab. My file system is ext4.
Question: Must I add the whole line "/dev/sda3     /srv/samba/Demo     ext4      user_xattr,acl      1 1" to the existing (of course changing /sda3 and /srv/samba/Demo to match my settings)?
I've 8 share folders in /srv/samba/ must I add 8 times "/dev/sda3 /srv/samba/Demo     ext4      user_xattr,acl      1 1" changing /srv/samba/Demo each time to adopt to the given share name?
Is it enough and appropriate to do the above (addin only "/dev/sda3     /srv/samba/Demo     ext4      user_xattr,acl      1 1" for each share) as other steps have been taken earlier?

---

### Post by lingpanda on 2014-03-27
> **tadewosa said:**
> thank you for your reply. It is just this guide that I used when I sett up shares. Except "ACL support on member server" I followed exactly as described there.
The only thing that I am not sure with the correctness of my configuration is editing "/etc/fstab".
It seems that I need a good knowledge of editing fstab. My file system is ext4.
Question: Must I add the whole line "/dev/sda3     /srv/samba/Demo     ext4      user_xattr,acl      1 1" to the existing (of course changing /sda3 and /srv/samba/Demo to match my settings)?
I've 8 share folders in /srv/samba/ must I add 8 times "/dev/sda3 /srv/samba/Demo     ext4      user_xattr,acl      1 1" changing /srv/samba/Demo each time to adopt to the given share name?
Is it enough and appropriate to do the above (addin only "/dev/sda3     /srv/samba/Demo     ext4      user_xattr,acl      1 1" for each share) as other steps have been taken earlier?

No not at all. Post your fstab and I will show you exactly what to enter. Below is taken from the Samba wiki

[h=2]Development libraries and Programs[/h] [h=3]Required :[/h] These packages are required for a successful build of samba 4 
 
[LIST]
[*] Python -- A good portion of Samba is written using python, including the build system itself (waf).
[/LIST]
 [h=3]Recommended optional development libraries and Programs:[/h] In most distributions these libraries will be labeled with a lib*-dev  or lib*-devel, for example for the Debian or Ubuntu acl would be  libacl1-dev, but in Fedora, RHEL, CentOS, and openSUSE its named  libacl-devel.   
 
[LIST]
[*] acl -- Required for a successful AD DC deployment. If this  library is not included, samba will build successfully, however you will  not be able to change ACL's from the windows frontend. You will receive  and error when you provision and if you manually create the smb.conf  with +s3fs, you will get **Access is denied.** from windows on any attempt to change ACL's.
[*] xattr
[*] blkid
[*] gnutls
[*] readline
[*] openldap -- Required to build the Samba3 components with LDAP  support. Lacking this library the build will complete but attempts to  provision (via upgrade) an Active Directory domain from an existing  Samba3 LDAP backend will fail. Also see [samba-tool domain classicupgrade]("https://wiki.samba.org/index.php/Samba4/samba-tool/domain/classicupgrade/HOWTO")
[*] cups -- for printer sharing support
[*] bsd or setproctitle - for process title updating support
[/LIST]
 
[LIST]
[*] xsltproc and docbook XSL stylesheets -- Required for building man pages and other documentation
[/LIST]



I take it you didn't install the libraries attr and acl prior to compile? 

[h=3]Debian or Ubuntu[/h] ```
# apt-get install build-essential libacl1-dev libattr1-dev \
   libblkid-dev libgnutls-dev libreadline-dev python-dev \
   python-dnspython gdb pkg-config libpopt-dev libldap2-dev \
   dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl

```

---

### Post by tadewosa on 2014-03-27
> **lingpanda said:**
> No not at all. Post your fstab and I will show you exactly what to enter. Below is taken from the Samba wiki

**Development libraries and Programs**

 **Required :**

 These packages are required for a successful build of samba 4 
 
[LIST]
[*] Python -- A good portion of Samba is written using python, including the build system itself (waf). 
[/LIST]
 **Recommended optional development libraries and Programs:**

 In most distributions these libraries will be labeled with a lib*-dev  or lib*-devel, for example for the Debian or Ubuntu acl would be  libacl1-dev, but in Fedora, RHEL, CentOS, and openSUSE its named  libacl-devel.   
 
[LIST]
[*] acl -- Required for a successful AD DC deployment. If this  library is not included, samba will build successfully, however you will  not be able to change ACL's from the windows frontend. You will receive  and error when you provision and if you manually create the smb.conf  with +s3fs, you will get **Access is denied.** from windows on any attempt to change ACL's. 
[*] xattr 
[*] blkid 
[*] gnutls 
[*] readline 
[*] openldap -- Required to build the Samba3 components with LDAP  support. Lacking this library the build will complete but attempts to  provision (via upgrade) an Active Directory domain from an existing  Samba3 LDAP backend will fail. Also see [samba-tool domain classicupgrade]("https://wiki.samba.org/index.php/Samba4/samba-tool/domain/classicupgrade/HOWTO") 
[*] cups -- for printer sharing support 
[*] bsd or setproctitle - for process title updating support 
[/LIST]
 
[LIST]
[*] xsltproc and docbook XSL stylesheets -- Required for building man pages and other documentation 
[/LIST]



I take it you didn't install the libraries attr and acl prior to compile? 

**Debian or Ubuntu**

 ```
# apt-get install build-essential libacl1-dev libattr1-dev \
   libblkid-dev libgnutls-dev libreadline-dev python-dev \
   python-dnspython gdb pkg-config libpopt-dev libldap2-dev \
   dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl

```

yes I did. all mentioned libraries have been installed prior to samba installation. It will be great to show me what/how to do. I will post it as soon as I get access to the server.
thank you

---

### Post by lingpanda on 2014-03-27
> **tadewosa said:**
> yes I did. all mentioned libraries have been installed prior to samba installation. It will be great to show me what/how to do. I will post it as soon as I get access to the server.
thank you

That's good you did install prior to compile. You just need to edit your fstab now. Once that its done your file system should support the xttr. You then just use Windows Computer Management to change permissions. You will need to ```
chmod 777
``` each folder share then set the ACL's however. For instance.

```
chmod 777 /srv/myshare
``` Whatever your share name is. Share must be world RWX.

---

### Post by tadewosa on 2014-03-29
> **lingpanda said:**
> No not at all. Post your fstab and I will show you exactly what to enter. Below is taken from the Samba wiki 

hi lingpand,
my fstab file informaiton is as follows:
<file system>                                 <mount point>                                <type>                                      <options>                                                <dump>            <pass>
proc                                          /proc                                               proc                                      node,noexec,nosuid                                           0                   0
# / was on /dev/md1 during installation
UUID=                                            /                                             ext4                                          user_xattr,acl,barrier=1,errors_remount-ro               0                   1
#swap was on /dev/mdo during installation
#UUID=...                                             none                                     swap                                          sw                                                               0                 0
/dev/mappaer/cryptswap1                      none                                  swap                                             sw                                                              0                       0

I have two discs and configured software RAID 1.

There are 8 share folders and 5 groups
eg.
share folder 1 "porject" full permission to group "development" (members usr1, usr2) access denied for other users and groups.
share folder 2 "Documents" full permission to group "freeall" (members usr1, usr2, usr3, usr4, usr5)
share folder 3 "welless" full permission to group "health" (members usr1, usr5) access denied for other users and groups.
The share paths are: 
/usr/local/samba/var/development
/usr/local/samba/var/freeall
/usr/local/samba/var/health

can you show me how to exactly enter in this fstab file?

Thank you

---

### Post by lingpanda on 2014-03-31
> **tadewosa said:**
> hi lingpand,
my fstab file informaiton is as follows:
<file system>                                 <mount point>                                <type>                                      <options>                                                <dump>            <pass>
proc                                          /proc                                               proc                                      node,noexec,nosuid                                           0                   0
# / was on /dev/md1 during installation
UUID=                                            /                                             ext4                                          user_xattr,acl,barrier=1,errors_remount-ro               0                   1
#swap was on /dev/mdo during installation
#UUID=...                                             none                                     swap                                          sw                                                               0                 0
/dev/mappaer/cryptswap1                      none                                  swap                                             sw                                                              0                       0

I have two discs and configured software RAID 1.

There are 8 share folders and 5 groups
eg.
share folder 1 "porject" full permission to group "development" (members usr1, usr2) access denied for other users and groups.
share folder 2 "Documents" full permission to group "freeall" (members usr1, usr2, usr3, usr4, usr5)
share folder 3 "welless" full permission to group "health" (members usr1, usr5) access denied for other users and groups.
The share paths are: 
/usr/local/samba/var/development
/usr/local/samba/var/freeall
/usr/local/samba/var/health

can you show me how to exactly enter in this fstab file?

Thank you

Can you please re post but use code tags? I don't want you to mess up your fstab. Thanks.

---

### Post by tadewosa on 2014-03-31
my fstab file informaiton is as follows:
# / was on /dev/md1 during installation
UUID= / ext4 user_xattr,acl,barrier=1,errors_remount-ro 0 1
#swap was on /dev/mdo during installation
#UUID=... none swap sw 0 0
/dev/mappaer/cryptswap1 none swap sw 0 0


[TABLE="width: 500, align: center"]
[TR]
[TD]file system[/TD]
[TD]mount point[/TD]
[TD]type[/TD]
[TD]options[/TD]
[TD]dump[/TD]
[TD]pass[/TD]
[/TR]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]UUID =...[/TD]
[TD]/[/TD]
[TD]ext4[/TD]
[TD]user_xattr,acl,barrier=1,errors_remount-ro[/TD]
[TD]0[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]UUID = ...[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]

---

### Post by lingpanda on 2014-03-31
> **tadewosa said:**
> my fstab file informaiton is as follows:
# / was on /dev/md1 during installation
UUID= / ext4 user_xattr,acl,barrier=1,errors_remount-ro 0 1
#swap was on /dev/mdo during installation
#UUID=... none swap sw 0 0
/dev/mappaer/cryptswap1 none swap sw 0 0


[TABLE="width: 500, align: center"]
[TR]
[TD]file system[/TD]
[TD]mount point[/TD]
[TD]type[/TD]
[TD]options[/TD]
[TD]dump[/TD]
[TD]pass[/TD]
[/TR]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]UUID =...[/TD]
[TD]/[/TD]
[TD]ext4[/TD]
[TD]user_xattr,acl,barrier=1,errors_remount-ro[/TD]
[TD]0[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]UUID = ...[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


Not exactly code tags but I'll try and make do. Here is mine.


```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/samba4DC-root /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 1       1
# /boot was on /dev/sda1 during installation
UUID=54f12064-e95b-4f55-b500-d950981f7f5d /boot           ext2    defaults        0       2
/dev/mapper/samba4DC-swap_1 none            swap    sw              0       0
```

Without proper codes tags yours would look something like.

[TABLE="align: center"]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0
[/TD]
[/TR]
[TR]
[TD]UUID =...
[/TD]
[TD][SIZE=4][B]/
[/B][/SIZE][/TD]
[TD][SIZE=4][B]ext4
[/B][/SIZE][/TD]
[TD][SIZE=4][B]errors=remount-ro,user_xattr,acl,barrier=1 1       1 
[/B][/SIZE][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]UUID = ...[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]

---

### Post by tadewosa on 2014-03-31
> **lingpanda said:**
> Not exactly code tags but I'll try and make do. Here is mine.


```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/samba4DC-root /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 1       1
# /boot was on /dev/sda1 during installation
UUID=54f12064-e95b-4f55-b500-d950981f7f5d /boot           ext2    defaults        0       2
/dev/mapper/samba4DC-swap_1 none            swap    sw              0       0
```

Without proper codes tags yours would look something like.

[TABLE="align: center"]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]UUID =...[/TD]
[TD][SIZE=4][B]/
[/B][/SIZE][/TD]
[TD][SIZE=4][B]ext4
[/B][/SIZE][/TD]
[TD][SIZE=4][B]errors=remount-ro,user_xattr,acl,barrier=1 1       1 
[/B][/SIZE][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]UUID = ...[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]

In case the UUID is needed I just posted it here. [SIZE=2]user_xattr,acl was not there before. It is me who added it.[/SIZE] Must I change ext4    user_xattr,acl,barrier=1,errors_remount-ro    0    1 to
ext4     errors=remount-ro,user_xattr,acl,barrier=1 1 1 ?
Is there something more to edit or it is all what must to be changed?
[TABLE="align: center"]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]UUID = 3f9a2ca7-21a3-40d6-ad43-06d0334c494a[/TD]
[TD][SIZE=4][B]/
[/B][/SIZE][/TD]
[TD][SIZE=4][B]ext4
[/B][/SIZE][/TD]
[TD][SIZE=4][B]errors=remount-ro,user_xattr,acl,barrier=1 1       1 
[/B][/SIZE][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]UUID = b1f620f6-4763-48c4-a45e-f7ab5698d398[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


Thank you.

---

### Post by lingpanda on 2014-03-31
> **tadewosa said:**
> In case the UUID is needed I just posted it here. [SIZE=2]user_xattr,acl was not there before. It is me who added it.[/SIZE] Must I change ext4    user_xattr,acl,barrier=1,errors_remount-ro    0    1 to
ext4     errors=remount-ro,user_xattr,acl,barrier=1 1 1 ?
Is there something more to edit or it is all what must to be changed?
[TABLE="align: center"]
[TR]
[TD]proc[/TD]
[TD]/proc[/TD]
[TD]proc[/TD]
[TD]node v,noexec,nosuid[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]UUID = 3f9a2ca7-21a3-40d6-ad43-06d0334c494a[/TD]
[TD][SIZE=4][B]/
[/B][/SIZE][/TD]
[TD][SIZE=4][B]ext4
[/B][/SIZE][/TD]
[TD][SIZE=4][B]errors=remount-ro,user_xattr,acl,barrier=1 1       1 
[/B][/SIZE][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]UUID = b1f620f6-4763-48c4-a45e-f7ab5698d398[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]/dev/mapper crypt swap1[/TD]
[TD]none[/TD]
[TD]swap[/TD]
[TD]sw[/TD]
[TD]0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


Thank you.

Yes to your first question and no to your second question.  You will handle all permissions using the windows computer management tool. You can test your file system by correcting your fstab and rebooting. 

**Testing your filesystem**

 To test your filesystem support, install the 'attr' package and run the following 4 commands as root: 
  ```
# touch test.txt
 # setfattr -n user.test -v test test.txt
 # setfattr -n security.test -v test2 test.txt
 # getfattr -d test.txt
 # getfattr -n security.test -d test.txt
```
You should see output like this: 
  ```
# file: test.txt
 user.test="test"
 # file: test.txt
 security.test="test2"
```
For ACL testing do the following as root: 
  ```
# touch test3.txt
 # setfacl -m g:adm:rwx test3.txt
 # getfacl test3.txt
```
and you should get a line like group:adm:rwx in your output. 

If you get any "Operation not supported" errors then it means your kernel is not configured correctly, or your filesystem is not mounted with the right options. 
If you get any "Operation not permitted" errors then it probably means you didn't try the test as root. 
If you are using the posix:eadb option then you don't need to test your filesystem in this manner.

---

### Post by tadewosa on 2014-04-17
I went through all the steps again. Also tried all the steps and checked my file system as indicated above. i get the same outputs for the functioning file system as is written above.
but the problem remains as before. I or other domain users get [COLOR=#ff0000]_occasionally_[/COLOR] access denied messages even for the files that they own, created and saved. Full access permission is also set for this folder, sub folders and files.
The case is for ms office documents, downloaded html and zip files. Folders are accessible. Other files like pdf, imaging audio or video files are until now accessible with out any problem.
I am desperate now.
thank you

---

### Post by lingpanda on 2014-04-18
> **tadewosa said:**
> I went through all the steps again. Also tried all the steps and checked my file system as indicated above. i get the same outputs for the functioning file system as is written above.
but the problem remains as before. I or other domain users get [COLOR=#ff0000]_occasionally_[/COLOR] access denied messages even for the files that they own, created and saved. Full access permission is also set for this folder, sub folders and files.
The case is for ms office documents, downloaded html and zip files. Folders are accessible. Other files like pdf, imaging audio or video files are until now accessible with out any problem.
I am desperate now.
thank you

Did you verify user and group permissions were set correctly using Windows Computer Management Tool? If so you may want to ask your question on the Samba mailing lists. [http://lists.samba.org/](http://lists.samba.org/)

---

