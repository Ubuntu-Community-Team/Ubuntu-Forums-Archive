---
title: "Samba shares are read only, don't know why"
date: 2015-01-08
forum: Ubuntu Cloud and Juju
---

### Post by Joshua_Borrow on 2015-01-08
Hi,

I've recently set up a samba share on kubuntu 14.10 machine. Here's my smb.conf:[INDENT][FONT=courier new][global]
workgroup = workgroup
netbios name = rigel
security = user
encrypt passwords = true

[share]
path = /home/share
browseable = yes
read only = no
directory mask = 0755
create mask = 0755[/FONT]

[/INDENT]
[FONT=arial]
When I try to connect to it on my macbook, I can connect and read the files. However, trying to write to the drive produces the error 'file system is read-only', even though I have:

          [/FONT][INDENT][FONT=courier new]drwxrwxrwx  2 josh    users   4096 Jan  8 14:42 share[/FONT]
[/INDENT]
 [FONT=arial]
Any help would be much appreciated.
[/FONT]

---

### Post by Samundra_Shrestha on 2015-01-09
Did you try setting the directory mask to 0777 and create mask to 0777. However I will not advise you to do so, but for quick test you can change the directory mask and create mask to 0777 and then restart samba share and then try to access the share. 

If you can access the server then you will need to confirm that the user accessing the share has the right privilege (0777) to write on the share. Try to change the share ownership to the user you tried to access with.

---

### Post by Joshua_Borrow on 2015-01-09
Thanks for your reply.

Yeah, even with everything 777 and the account that owns the share, I still get that it's read only.

---

### Post by Morbius1 on 2015-01-09
I'm not a KDE user since I find it very disturbing but I do have a KDE system in a VBox guest for times like this.

I tried to reproduce your symptoms and have not been very successful so far. What I did was create the same folder and added the same share definition to the default smb.conf. What I did not do is throw away the other 60% of the [global] section as you have done. I have no problem writing to the share from OSX.

I suppose I could also match your [global] section and find out which one of the missing parameters is the cause of this but I did try one other experiment and that was to create a samba share of the exact same folder from dolphin and made it read only. Now I have duplicate shares from two different methods of the same folder but with different parameters. Now it fails.

Run the following command and see if you created a share in dolphin:
```
net userhsare info --long
```

---

### Post by SeijiSensei on 2015-01-09
I assume you can write normally to /home/share from Linux?  If you cannot do that either, then the filesystem holding /home has errors.  Such filesystems are mounted read-only and need to be checked and fixed with fsck.

---

### Post by Joshua_Borrow on 2015-01-09
I can write normally in linux, yes.

Here's my output:

```
info_fn: file /var/lib/samba/usershares/macbook is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[share]
path=/home/share
comment=
usershare_acl=Everyone:R,
guest_ok=n

```

I did try to create one under /home/macbook through dolphin but I deleted it as it wouldn't let me set permissions within the file browser (every time I clicked close it reverted to josh : ----- from josh : all access.

---

### Post by Morbius1 on 2015-01-09
This samba share ( Read Only ):
> [share]
path=/home/share
comment=
usershare_acl=Everyone:R,
guest_ok=n
Conflicts with this samba share ( Writeable ):
> [FONT=courier new][share]
path = /home/share
browseable = yes
read only = no
directory mask = 0755
create mask = 0755[/FONT]
[FONT=arial]
[/FONT]
It's usually anyones guess which one samba will obey but in KDE's case it appears to be the one you created in dolphin. Go back into dolphin and "un-share" it.

---

### Post by Joshua_Borrow on 2015-01-09
I can't find the old folder (that has been shared by dolphin, I must have deleted it in rage) but creating a new one has solved this issue for me. Thanks for your help!

---

