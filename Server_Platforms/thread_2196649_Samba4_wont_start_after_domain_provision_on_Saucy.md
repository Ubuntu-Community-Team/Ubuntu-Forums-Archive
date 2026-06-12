---
title: "Samba4 wont start after domain provision on Saucy"
date: 2013-12-30
forum: Server Platforms
---

### Post by MikeEvans on 2013-12-30
Problem: The samba4 package appears to be broken or at least lacks support for AD DC hosting.  The samba service will not start after domain provisioning.  After much searching I "think" this is broken due to a bug: [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031]("https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031"). Does that sound right?

Here is a rundown of my testing:

System: Fresh Saucy server running in a vm

I'm following the official wiki instructions for implementing a samba 4 AD DC:  [http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO]("http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO") 

samba is installed via "sudo apt-get install samba4"

```

impadmin@DC1:~$ samba -V
samba: /usr/lib/x86_64-linux-gnu/libwbclient.so.0: no version information available (required by /usr/lib/x86_64-linux-gnu/samba/libauth4.so)
Version 4.0.3
impadmin@DC1:~$ smbclient4 -V
Version 4.0.3

```

I attempt to provision the domain

```

sudo rm -fr /var/lib/samba/private/*
sudo rm /etc/samba/smb.conf
sudo samba-tool domain provision --use-rfc2307 --interactive

```

here is the output for the provisioning command: [http://pastebin.com/raw.php?i=rsufWS2V]("http://pastebin.com/raw.php?i=rsufWS2V")

The first problem occurs during provisioning.  There are lots of errors like this:
```

Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr

```

I tested that acl is working by setting and reading attributes.

This appears to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1091348]("https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1091348")

However it is not clear if this bug stops samba4 from running.

When starting samba directly I get the following:

```

impadmin@DC1:~$ sudo samba
samba: /usr/lib/x86_64-linux-gnu/libwbclient.so.0: no version information available (required by /usr/lib/x86_64-linux-gnu/samba/libauth4.so)

```

This also appears to be a known bug:  [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031]("https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031")

So is this package broken for now?  If so does anyone have a suggestion for running samba4+ as AD DC?  Maybe switching to 13.04?

---

### Post by lingpanda on 2014-01-02
> **MikeEvans said:**
> Problem: The samba4 package appears to be broken or at least lacks support for AD DC hosting.  The samba service will not start after domain provisioning.  After much searching I "think" this is broken due to a bug: [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1244031). Does that sound right?

Here is a rundown of my testing:

System: Fresh Saucy server running in a vm

I'm following the official wiki instructions for implementing a samba 4 AD DC:  [http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO) 

samba is installed via "sudo apt-get install samba4"

```

impadmin@DC1:~$ samba -V
samba: /usr/lib/x86_64-linux-gnu/libwbclient.so.0: no version information available (required by /usr/lib/x86_64-linux-gnu/samba/libauth4.so)
Version 4.0.3
impadmin@DC1:~$ smbclient4 -V
Version 4.0.3

```

I attempt to provision the domain

```

sudo rm -fr /var/lib/samba/private/*
sudo rm /etc/samba/smb.conf
sudo samba-tool domain provision --use-rfc2307 --interactive

```

here is the output for the provisioning command: [http://pastebin.com/raw.php?i=rsufWS2V](http://pastebin.com/raw.php?i=rsufWS2V)

The first problem occurs during provisioning.  There are lots of errors like this:
```

Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr

```

SNIP



Did you make sure to review this [https://wiki.samba.org/index.php/Samba_4/OS_Requirements](https://wiki.samba.org/index.php/Samba_4/OS_Requirements) before provision?

---

### Post by MikeEvans on 2014-01-02
> **lingpanda said:**
> Did you make sure to review this [https://wiki.samba.org/index.php/Samba_4/OS_Requirements](https://wiki.samba.org/index.php/Samba_4/OS_Requirements) before provision?

Yes.  I've gone through it a few times and I don't think I missed anything on the wiki.  I would be interested to know if anyone has this working on Saucy.  

I'm trying some alternative configurations. 4.1 compiles and runs fine.

Thanks for your time.

---

