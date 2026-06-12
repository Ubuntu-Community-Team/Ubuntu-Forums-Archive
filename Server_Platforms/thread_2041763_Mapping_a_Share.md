---
title: "Mapping a Share"
date: 2012-08-13
forum: Server Platforms
---

### Post by csiis on 2012-08-13
I'm trying to create a mount point on my Ubuntu 12.04 server to a location on a different servers.

First of all im creating the mnt point - mkdir /mnt/example - which is fine.

Then i attempt to run:

mount -t cifs //servertest/example /mnt/example -o user=test,password=test

after which i get back:

mount: //servertest/example is not a valid block device

thanks

---

### Post by darkod on 2012-08-13
If it doesn't resolve the server name correctly, try using the IP instead of //servertest, something like //192.168.1.10/sharename

---

### Post by SeijiSensei on 2012-08-13
See if you can access the share from the command line with smbclient:

```
smbclient \\\\server\\share -U username
```

The extra slashes are needed to "escape" the backslash which has a defined meaning in the shell.  The server should prompt for your password, then smbclient will display a prompt "smb: \>".  Typing "ls" will list the remote share.

If that doesn't work, you may need to check that you're in the same workgroup or domain.  In smbclient you can try adding "-W" followed by the workgroup or domain.  Recent Windows servers sometimes require usernames of the form "DOMAIN\username".  Try that instead.

Do you have access to the server's logs?  Perhaps you'll find a clue there.

---

### Post by redmk2 on 2012-08-13
> **SeijiSensei said:**
> See if you can access the share from the command line with smbclient:

```
smbclient \\\\server\\share -U username
```

The extra slashes are needed to "escape" the backslash which has a defined meaning in the shell.  The server should prompt for your password, then smbclient will display a prompt "smb: \>".  Typing "ls" will list the remote share.

If that doesn't work, you may need to check that you're in the same workgroup or domain.  In smbclient you can try adding "-W" followed by the workgroup or domain.  Recent Windows servers sometimes require usernames of the form "DOMAIN\username".  Try that instead.

Do you have access to the server's logs?  Perhaps you'll find a clue there.

The correct syntax is ```
smbclient //server/share
```
...no need to escape characters at all.  If you don't use the -U switch it will prompt you for login name,

---

### Post by redmk2 on 2012-08-13
> **csiis said:**
> I'm trying to create a mount point on my Ubuntu 12.04 server to a location on a different servers.

First of all im creating the mnt point - mkdir /mnt/example - which is fine.

Then i attempt to run:

mount -t cifs //servertest/example /mnt/example -o user=test,password=test

after which i get back:

mount: //servertest/example is not a valid block device

thanks
It looks like you have not created a Samba (Windows) share to mount.  Have you created a share?

---

### Post by SeijiSensei on 2012-08-13
> **redmk2 said:**
> The correct syntax is ```
smbclient //server/share
```
...no need to escape characters at all.  If you don't use the -U switch it will prompt you for login name,

That wasn't always true.  If smbclient now accepts the //server/share syntax, that is an improvement over the original smbclient that I started using a dozen years ago.

---

### Post by redmk2 on 2012-08-14
> **SeijiSensei said:**
> That wasn't always true.  If smbclient now accepts the //server/share syntax, that is an improvement over the original smbclient that I started using a dozen years ago.

Nope, it's been that way since at least 1995. Which is 17 years ago by my math.  I suppose you can do it your way but is is confusing.  The \\server\share is the Windows UNC method, not a Samba (SMB/CIFS) method if I'm not mistaken.  We are way OT here anyway.

---

### Post by csiis on 2012-08-14
Thanks all for the info - Ill have a look today and update

---

### Post by csiis on 2012-08-15
Ok so success.

I can access the remote directory and view its contents using:

smbclient //RemoteServer/RemoteDirectory -U UserName

For scripting purposes i really need to be able to access the remote directory via a mount point. Any ideas on how i can get this to work based on the above working?

Thank you

---

### Post by csiis on 2012-08-15
Sorted.

I didnt have the smbfs package installed - DOH!

thanks for everyones input

---

